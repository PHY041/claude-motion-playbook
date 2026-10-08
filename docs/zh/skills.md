# Skill 评测：画廊背后的开源 agent skill

本文逐个阅读 [prompt-motion.com](https://www.prompt-motion.com/)（由 [@p4nthera_](https://x.com/p4nthera_) 整理）233 支视频里链接到的 agent skill，快照日期 2026-10-09。所谓 skill，是一个装着说明、参考文档和脚本的文件夹（`SKILL.md` 加辅助文件），coding agent 加载它来完成某一类工作。这里的工作，是把一段需求变成渲染好的视频。`#N` 指 [`catalog/catalog.json`](../../catalog/catalog.json) 里条目的 `id`。

[English version](../skills.md)

## 要点速览

- **233 条里只有 4 条链接了 skill 仓库，其余 229 条都是 prompt。** 这 4 条是 [#16 Cinetic skill launch film — @LexnLin](https://www.prompt-motion.com/lexnlin-6161a6)、[#23 Reddit marketing tool launch video — @anthonyriera](https://www.prompt-motion.com/anthonyriera-9b1b2a)、[#70 Animated agent session story — @jake11moran](https://www.prompt-motion.com/jake11moran-a269c4) 和 [#147 Indian civilisation history film — @BuildFastWithAI](https://www.prompt-motion.com/buildfastwithai-53234e)。它们背后的仓库里一共有 13 个做视频的 skill，本文全部拆解。
- **[cinetic](#1-cinetic) 的流程最完整。** 从 `BRIEF.md` 到交付共 9 步，每一步都以一道真正要执行的检查收尾，多数是脚本。技法从 273 条的技法库里随机抽取，成片要过 11 维评分表才能出片。作者自己实测，耗时和 token 约为不用它的基线的 3 倍。
- **[product-film](#2-product-film) 最贴近产品本身。** 它先读你的设计系统，用你产品里真实的功能名来提问，再在 Remotion 里用你自己的组件搭片。交付前会解码成片，核对颜色有没有走样。
- **HyperFrames 社区仓库有 8 个 skill，最突出的是两个。** [session-story](#3-session-story) 从你和 agent 的聊天记录做一支个人短片，全程有明确的隐私关；[vox-explainer](#4-vox-explainer) 用一份转场账本记录每个切点，再在无头 Chrome 里逐个自动核验。
- **buildfast-skills 覆盖三种产出。** [generative-film](#6-generative-film) 用 pycairo 逐帧画，不需要浏览器；[motion-studio](#5-motion-studio) 用 51 种画风、10 种动作语言、13 种片型组合，再跑 16 项自动质检；[canvas-documentary](#7-canvas-documentaryhtml-animation-skill) 产出的是可交互的 HTML 页面，不是 MP4。
- **几个做法在多个仓库里反复出现。** 一套节拍网格同时驱动画面、声音和质检；每轮构建都以「渲染 → 测量 → 评审」的循环收尾；通过与否的门槛都写成明确的数字。见[值得借鉴的做法](#9-值得借鉴的做法不分引擎)。
- **四个仓库都是 MIT 或 Apache-2.0，但引擎和依赖库有各自的许可。** Remotion 有自己的授权条款，p5 是 LGPL-2.1，Strudel 是 AGPL-3.0。商用前请先核对。

## 目录

1. [四个仓库一览](#四个仓库一览)
2. [横向对比](#横向对比)
3. 逐个拆解：[cinetic](#1-cinetic) · [product-film](#2-product-film) · [session-story](#3-session-story) · [vox-explainer](#4-vox-explainer) · [motion-studio](#5-motion-studio) · [generative-film](#6-generative-film) · [canvas-documentary](#7-canvas-documentaryhtml-animation-skill) · [其余社区 skill](#8-其余-hyperframes-社区-skill)
4. [值得借鉴的做法](#9-值得借鉴的做法不分引擎)
5. [怎么选](#10-怎么选)
6. [方法与局限](#11-方法与局限)

---

## 四个仓库一览

四个仓库都按下表的 commit 阅读。文中的文件链接指向默认分支，快照之后文件可能已经挪过位置。

| 仓库 | 快照 commit | 许可 | 画廊条目 |
|---|---|---|---|
| [Leonxlnx/cinetic](https://github.com/Leonxlnx/cinetic) | [`bee5d78`](https://github.com/Leonxlnx/cinetic/commit/bee5d7807205d5543472c38312507f9bf366cbbf)，2026-10-04（v1.0.0） | MIT | [#16 Cinetic skill launch film — @LexnLin](https://www.prompt-motion.com/lexnlin-6161a6) |
| [Rieranthony/product-film-skill](https://github.com/Rieranthony/product-film-skill) | [`fe11efc`](https://github.com/Rieranthony/product-film-skill/commit/fe11efc429d5903e37274d0b294e1b95745b2881)，2026-09-26（v1.1.0） | MIT | [#23 Reddit marketing tool launch video — @anthonyriera](https://www.prompt-motion.com/anthonyriera-9b1b2a) |
| [heygen-com/hyperframes-community-skills](https://github.com/heygen-com/hyperframes-community-skills) | [`ba7a0bb`](https://github.com/heygen-com/hyperframes-community-skills/commit/ba7a0bb6d3567d124c51f6074625043bfe0b32eb)，2026-09-24 | Apache-2.0 | [#70 Animated agent session story — @jake11moran](https://www.prompt-motion.com/jake11moran-a269c4)（session-story） |
| [buildfastwithai/buildfast-skills](https://github.com/buildfastwithai/buildfast-skills) | [`c91416c`](https://github.com/buildfastwithai/buildfast-skills/commit/c91416cf7473ccd485d5fcc739a54314a4f8b1bc)，2026-10-08 | MIT | [#147 Indian civilisation history film — @BuildFastWithAI](https://www.prompt-motion.com/buildfastwithai-53234e)（generative-film） |

catalog 里的背景数据：233 条中有 56 条写明了技术栈，其中提到 Remotion 的 13 条，提到 HyperFrames 的 10 条。13 个 skill 里大多数瞄准的也正是这两个引擎；motion-studio 和 generative-film 自带渲染器，canvas-documentary 输出的是交互网页，p5-paint-animation 用 Puppeteer 加 ffmpeg 渲染。

---

## 横向对比

| Skill | 产出 | 渲染栈 | 许可要点 | 最适合 |
|---|---|---|---|---|
| [cinetic](#1-cinetic) | 3–90 秒的短片、循环片和 logo 片头；MP4，格式需要时另出 WebM/GIF/ProRes 透明版 | Remotion 4.0.529（默认）或 HyperFrames 0.8.79 | MIT；默认引擎受 Remotion 授权约束 | 发布片和 logo 片头，成品质量和音画同步都要能量化核验 |
| [product-film](#2-product-film) | 20–90 秒的发布片或静音落地页循环片，另出 WebM 和海报 | Remotion、Bun、uv | MIT；Remotion 授权；配乐需有使用权 | 有代码库和设计系统的产品团队 |
| [session-story](#3-session-story) | 40–70 秒水彩动画，24fps，自带配乐 | HyperFrames 0.8.71 + p5.brush | Apache-2.0；p5 为 LGPL-2.1 | 一支记录你和 agent 怎么合作的个人短片 |
| [vox-explainer](#4-vox-explainer) | 60–90 秒拼贴风解说片 | HyperFrames + GSAP；Node 转场脚本 | Apache-2.0 | 从话题、报告或文档做解说片 |
| [motion-studio](#5-motion-studio) | 任意画幅的动效 MP4，13 种片型 | 自带 HTML 引擎 + Playwright + ffmpeg | MIT；内置字体各附 OFL 许可文件 | 同一分镜试多种画风；给模型做基准测试 |
| [generative-film](#6-generative-film) | 45–120 秒，1920×1080，30fps MP4 | Python：pycairo、Pillow、numpy/scipy、ffmpeg | MIT | 图形感强的历史、科普短片，不需要浏览器 |
| [canvas-documentary](#7-canvas-documentaryhtml-animation-skill) | 单个自包含的交互式 HTML 文件，约 2 分钟 | Canvas 2D + Web Audio | MIT | 网页上的交互式叙事 |

---

## 1. cinetic

**一句话：** 让写代码的 agent 当导演。它先写创意，再套用或发明一套品牌，定好节拍网格，合成配乐，然后渲染、量化测量、评审，最后才出片。画廊条目 [#16 Cinetic skill launch film — @LexnLin](https://www.prompt-motion.com/lexnlin-6161a6) 就是这个 skill 自己 30 秒的发布片。

**从需求到 MP4 的流程。** 每一步写一个文件，以一道 agent 实际运行的检查收尾（[SKILL.md §3](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/SKILL.md)）：

| 步骤 | 产出 | 关卡 |
|---|---|---|
| 0 需求 | `BRIEF.md`：规格行、硬禁令、品牌例外 | 有规格行，如 `1920x1080@60, 30s, 120BPM` |
| 1 创意 | `TREATMENT.md`：3 个创意、抽到的技法、节拍表 | 一句话梗概 ≤ 15 词；具体性测试有书面答案；文案在字数预算内 |
| 2 品牌 | `src/brand/`：token、标志、组合 | `lint-film.mjs` 查不到占位符，也查不到 token 以外的颜色或字体 |
| 3 时间线 | `timeline.ts`：所有帧号都由 `b(bar, beat, sub)` 算出 | `grid-check.ts`：提示点落在 16 分音符网格上，文字停留够长，没有超过 48 帧的无事件空档 |
| 4 搭建 | 分幕代码，每幕一张联系表 | 安全区和遮挡违规为 0；可读文字移动 ≤ 20 px/帧 |
| 5 声音 | 从画面代码导出提示点，再合成配乐 | −14 LUFS ±0.5，真峰值 ≤ −1.5 dBTP |
| 6 渲染 | 先出预览，再出母版（速度超过 12 px/帧的部分加运动模糊） | `probe.py` 规格检查；`check-sync.py` 延迟 ≤ 48 采样点 |
| 7 评审 | 联系表、像素法医、音画审计、评审视角 | 11 维评分每维 ≥ 3，成品质量和音画同步两维 = 5，均分 ≥ 4.2，没有未关闭的 P0 |
| 8 交付 | 母版、海报、9:16 和 1:1 重新排版、品牌套件 | 每个交付物都过 `probe.py` |

片头、循环片和短片段走精简路线：一页纸的创意稿，一到两幕，一轮评审。

**渲染栈、依赖、许可。** 默认引擎是 Remotion 4.0.529。HyperFrames 0.8.79 是备选，用 `new-film.sh --engine hyperframes` 从 [`assets/hyperframes-starter/`](https://github.com/Leonxlnx/cinetic/tree/main/skills/cinetic/assets/hyperframes-starter) 搭项目。需要 Node 22+、带 libx264 的 ffmpeg 6+ 和一个无头 Chromium。还需要 Python 3.11+，装 numpy、scipy、soundfile、pyloudnorm、opencv-python 和 librosa；做标志和渐变另需 fonttools、brotli、uharfbuzz 和 pillow。skill 本身是 MIT。README 说明，Remotion 对个人和 3 人以内的公司免费，4 人起要买公司授权。HyperFrames 是 Apache-2.0。

**真正聪明的地方**

- **技法靠抽签，不靠挑。** [`scripts/pick.py`](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/scripts/pick.py) 从 [`assets/library/techniques.json`](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/assets/library/techniques.json) 里抽，库里有 273 个技法，分 14 类。抽签按片型和能量加权，大约每 2.5 秒片长抽一个，带种子，可以复现。作者的理由是：让 agent 自己挑，每次都会挑到同样的淡入、推近和片尾卡。`pick.py` 只用 Python 标准库，跟引擎无关。
- **音效点从动作曲线算出来。** 同步帧用的是和画面同一套缓动和弹簧：撞击取接触帧，落定取 97% 帧，嗖声取速度峰值帧。在 HyperFrames starter 里，这一步是 [`timeline.js`](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/assets/hyperframes-starter/timeline.js) 里的 `FILM.cues()`。作者实测，手敲的同步点会偏 8–11 帧。
- **对成片做像素法医。** [`scripts/forensics.py`](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/scripts/forensics.py) 对任何 MP4 查单帧跳变、卡帧、死停、重影帧、边缘细缝、抖动、色带、压缩涂抹和循环接缝。[`scripts/sheet.py`](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/scripts/sheet.py) 出标了帧号和时间的联系表。两个脚本都不挑引擎。
- **色带有一条量化判据。** [`references/finishing.md` §3](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/references/finishing.md) 给的经验法则是：整幅画面通道值变化不到约 30 个码值的 CSS 渐变就会出色带。渐变改用 [`dither-gradient.py`](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/scripts/dither-gradient.py) 生成加了抖动的 PNG。HyperFrames 路线下，[`hf-finish.sh`](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/scripts/hf-finish.sh) 先出 PNG 序列，再用 x264 一次性编码（CRF 14，标 BT.709），避免两道有损压缩。
- **一张 HyperFrames lint 查不出的坑表。** 见 [`references/hyperframes-engine.md` §10](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/references/hyperframes-engine.md)。PNG 抓帧会丢掉 `html`/`body` 的背景，母版因此变成黑底。合成 id 对不上，会先卡 45 秒，然后整幕冻住。lint 有错时布局审计被关掉，`check` 会报一个看似干净的 "0 samples"。
- **评审之外还有复核。** [`assets/critics/`](https://github.com/Leonxlnx/cinetic/tree/main/skills/cinetic/assets/critics) 里有 5 份 prompt：导演、美术/文案/UI、声音同步、法医，外加一个复核者，在动手修之前先尝试推翻每一条 P0 和 P1。它们按 [`references/review-loop.md` §9–10](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/references/review-loop.md) 的 11 维评分表和出片门槛打分。
- **有测量撑腰的工艺规则。** [`references/craft-rules.md` §9](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/references/craft-rules.md) 列了顶级片和一般好片的 15 条差别。举两条：离场加速冲进切点，下一镜一开始就在运动；全片只花一次静止（在核心主张上停 60–96 帧），之后紧接全片最大的动作。
- **尽早淘汰弱创意的测试。** [`references/concept-and-story.md` §4](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/references/concept-and-story.md) 有 10 项测试，包括所有权、删除、静音和具体性，并列出了一串通用道具，比如代表 AI 的发光球。[`references/product-ui.md` §8](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/references/product-ui.md) 的暂停测试要求任意一帧暂停下来都说得通：数字对得上，状态在起因那一帧就变，UI 文字 ≥ 22px。
- **评测写得坦诚。** [`docs/evaluation.md`](https://github.com/Leonxlnx/cinetic/blob/main/docs/evaluation.md) 报告说，cinetic 每一轮满足的书面要求都比基线多（第 7 轮 54/56 对 41/56）。它也照实写了：中立盲评意见分裂，六轮共 23 次对比里只有 7 次选了 cinetic。作者还补充说明，这些要求是和 skill 一起写的，应当视作上限来读。

**局限**

- **成本高。** 第 7 轮平均每支片 95 分钟、62.6 万 token，基线是 33 分钟、23.1 万 token，约 3 倍（作者实测）。
- **审美立场鲜明。** 由 agent 发明画风时适用硬禁令：不用衬线体和斜体；不用橙色、米色和紫色；不用发光、粒子和多色渐变。你自带的品牌可以覆盖这些禁令，但每一项例外都要在 `BRIEF.md` 里声明，并在代码里标注。
- **HyperFrames 是次要路线。** 它的运动模糊上限约 18 px/帧，文档建议更快的片子改用 Remotion。公开评测以 Remotion 为基线，没有单独报告 HyperFrames 路线的结果。
- **引擎版本钉死。** 这个 skill 钉的是 Remotion 4.0.529 和 HyperFrames 0.8.79，换新版 CLI 行为可能不同。
- **安装较重。** Python 依赖不少。脚本在 Linux 上开发，README 说 macOS 测得较少，Windows 没测过。
- **默认节奏偏密。** 密度目标是每 30 秒 45–60 个离散事件。作者说明，所有数字都是默认值，有书面理由就可以偏离。

**谁该用：** 做发布片、预告、logo 片头或落地页循环片，并且有时间和 token 预算走完整量化流程的人。也适合想把其中某几道关卡（法医脚本、联系表、评分表）单独搬进自己流程的团队。

**最适合：** 成品质量和音画同步需要能核验、而不只是凭肉眼判断的短片。

---

## 2. product-film

**一句话：** 先读懂你产品的设计系统，再问你片子里要放什么，最后用你真实的组件、logo 和音乐在 Remotion 里搭建并渲染发布片或落地页循环片。画廊把 [#23 Reddit marketing tool launch video — @anthonyriera](https://www.prompt-motion.com/anthonyriera-9b1b2a) 列在这个 skill 下，技术栈为 Remotion。

**从需求到 MP4 的流程**（[SKILL.md](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/SKILL.md)）：

1. **摸底。** 并行做几轮只读扫描：规则文件、token、组件、logo、宣传口径，再逛一遍线上网站（[`reference/discovery.md`](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/reference/discovery.md)）。
2. **访谈。** 两轮选择题，先问需求，再问用料。
3. **品牌与故事。** 回答写进 `videos/BRAND.md`，它的优先级高于 skill 的默认值；再写出片子的 prompt 和节拍表。动手搭建前先拿 3 张风格帧和你确认一次。
4. **音乐。** `beats.py` 测出歌曲的节拍网格，`audio-edit.py` 按小节剪歌，音效放在实测的峰值上。
5. **搭建。** 一个 Remotion 合成，每一帧都是时间的纯函数。配一套小工具包，管时间、弹簧、镜头、光标、magic move 和金句。
6. **评审。** 每个转接点出静帧，再出联系表和转接拼图，然后渲一版半分辨率草稿。
7. **渲染与核验。** 先渲 240fps 的 PNG 母版，用 ffmpeg（`tmix`，每 4 个子帧）平均成带运动模糊的 60fps，颜色转换只做一次。交付物有静音循环版、带音乐版、WebM 和海报，`verify.py` 逐个核验（[`reference/render.md`](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/reference/render.md)）。

**渲染栈、依赖、许可。** Remotion（由 skill 加进你的项目）、Node.js、[Bun](https://bun.sh) 和 [uv](https://docs.astral.sh/uv/)。Python 脚本按需拉取 numpy 和完整版 ffmpeg（imageio-ffmpeg），不往系统里装任何东西。它需要 Claude Code：要调用你本地的工具链，访谈一步也用到 Claude Code 的提问工具。skill 本身是 MIT。README 提醒，Remotion 有自己的授权，规模较大的公司需要购买公司授权。

**真正聪明的地方**

- **只问代码回答不了的问题。** [`reference/interview.md`](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/reference/interview.md) 的选项用你产品真实的功能名和组件名，推荐项放第一个。颜色、字体、圆角这些代码里查得到的，一律不问。审美问题改为出 3 张风格帧让你挑，因为人对图的反应比对问题快。
- **证据镜头和 magic move。** [`reference/ingredients.md`](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/reference/ingredients.md) 让一条搜索结果、一个 AI 回答、一个指标或一句引语各自单独成镜，要求"lo-fi but faithful"（粗糙但忠实）。同一文件还有一张 magic move 搭配表，即一个元素直接飞进下一镜：图里的头像变成列表里的行，被点开那一行的标题变成详情页的页头。
- **金句不会边出边重新居中。** 在 [`templates/kit/punchlines.tsx`](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/templates/kit/punchlines.tsx) 里，每个词从一开始就占好位置，居中的一行在逐词出现时不会挪动。
- **解码核验。** [`scripts/verify.py`](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/scripts/verify.py) 解码每个交付物的第一帧，核对底色误差在 ±2 以内；循环片还要核对末帧和首帧一致。它专门防一个坑：把 limited range 的母版当 full range 读，`#0a0a0a` 会变成 `#171717`，在深色页面上成了一个灰框。
- **故事贴着歌曲结构走。** [`reference/music.md`](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/reference/music.md) 逐小节打印每条分轨的响度，再把故事对上去：鼓进来时出第一批金句，drop 时出最强的画面，贝斯退出时出标题。
- **一张短小的 Remotion 坑表。** SKILL.md 里这张表很实用。静帧不转发 console 日志，所以用 [`templates/kit/debug.tsx`](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/templates/kit/debug.tsx) 把测量值直接打印进画面；Remotion 自带的 ffmpeg 没有 `tmix`、`select` 和 `tile`；`interpolateColors` 解析不了 `color-mix()`。

**局限**

- **只支持 Remotion。** 规模较大的公司需要 Remotion 的公司授权。
- **只能在 Claude Code 里用。** 聊天类应用里跑不了。
- **需要有产品可读。** 在带 token 和组件的产品仓库里效果最好；没有这些，摸底能找到的东西就很少。
- **不带音乐。** 要你提供有授权的曲子或免版税曲，也可以做静音版；音效需要合成或购买授权。
- **终渲慢。** 作者的数字是：50 秒的片子在笔记本上按 240fps 渲染约 10 分钟。
- **没有像 cinetic 那样公开的评测。**

**谁该用：** 希望片子看起来像「产品自己做的」SaaS 和 App 团队，界面、字体、组件和宣传口径都与产品一致。

**最适合：** 用真实代码库做落地页循环片和发布片。

---

## 3. session-story

**一句话：** 你的 agent 读它和你的本地聊天记录，挑出一次典型会话，从头到尾拍成 40–70 秒的水彩动画，并自己作曲配乐。你发的消息化作纸飞机飞进来，纠正化作一把卡通木槌，表扬化作一只拖着文字丝带的蝴蝶。画廊条目是 [#70 Animated agent session story — @jake11moran](https://www.prompt-motion.com/jake11moran-a269c4)。

**从需求到 MP4 的流程**（[SKILL.md](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/session-story/SKILL.md)）：

1. 一次性安装（按已提交的锁文件 `npm ci`）。
2. 读任何记录之前，先征得用户同意。
3. `harvest.py` 读取 agent 在当前项目下的本地会话记录（Claude Code 或 Codex），按典型程度给会话排序。
4. agent 逐个节拍写 `story.json`，用户原话逐字引用，并标上真实时间；每改一次都跑 `schedule.mjs` 检查。
5. 根据它对用户的了解布置房间道具。
6. **隐私关：** 把每一句上屏文字连同出处列成一张表给用户看，由用户确认或修改。确认之前，每一帧都打着 DRAFT 水印。
7. 设计稿：抽帧并出联系表。
8. 配乐：`score.py`，再跑 `build.sh`（响度归一到 −16 LUFS）。
9. 用 `hyperframes@0.8.71 render --fps 24 --crf 12` 渲染，再核对时长和关键帧。

**渲染栈、依赖、许可。** HyperFrames 0.8.71，配 p5 2.3.3（LGPL-2.1）、p5.brush 2.2.3（MIT）做 WebGL 水彩，字体是 Permanent Marker（Apache-2.0）。需要 Node 22+、Python 3.9+（只用标准库）和 ffmpeg。配乐在 macOS 上用 `swift` 调苹果内置的 General MIDI 音色，其他系统用 `fluidsynth` 加音色库。仓库是 Apache-2.0。引擎工具包有一部分改编自 ClaudeAnimationBase（MIT），见 [`assets/engine/NOTICE.md`](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/session-story/assets/engine/NOTICE.md)。

**真正聪明的地方**

- **一个故事文件同时喂给画面和音乐。** [`scripts/schedule.mjs`](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/session-story/scripts/schedule.mjs) 用影片运行时同一份 `scenes/compile.js` 编译 `story.json`，产出给画面用的 `story.js` 和给配乐用的 `score/timeline.json`。改一处，画面和音乐的时间一起更新。
- **隐私是设计出来的。** 先征得同意，再走上面说的确认表和 DRAFT 水印。这个 skill 还要求每次抽帧都加 `--describe false`：环境里设了 `GEMINI_API_KEY` 时，抽帧命令默认会把画面（里面有用户原话）发给 Gemini。不加 `--example` 时，`schedule.mjs` 拒绝编译自带的示例故事，示例因此无法冒充你用户的故事。
- **符合物理的动作规则。** [`references/motion.md`](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/session-story/references/motion.md) 定了三条规矩：没有闲置动作；反应从起因那一帧开始；重的动作之前先停一拍。纸飞机按约 3:1 的滑翔比飞，会上下起伏、拉平、滑行后停下。
- **冷场直接判失败。** [`scripts/score/qc.py`](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/session-story/scripts/score/qc.py) 只要发现低于 −45 dBFS、超过 1.2 秒的片段就判失败，这种片段通常意味着某个节拍漏了提示点。

**局限：** 需要真实的会话记录，本地记录或用户粘贴的消息都行。视觉世界是固定的（水彩房间、纸飞机、木槌、蝴蝶），能改的是故事、房间和配乐，画风改不了。配乐渲染在 macOS 上需要 `swift`，其他系统需要 `fluidsynth` 加音色库。成片 24fps，HyperFrames 钉在 0.8.71。项目文件夹里存着用户原话，skill 明确要求不要提交或分享。

**谁该用：** 想要一支温暖、可分享的短片，记录自己和 agent 如何合作的个人用户。

**最适合：** 用真实会话记录讲个人故事，每一个字都经用户确认。

---

## 4. vox-explainer

**一句话：** 根据一个话题，或你提供的文档和链接，做 60–90 秒的拼贴风解说片，转场和节奏都有数字关卡。它和 session-story（[#70 Animated agent session story — @jake11moran](https://www.prompt-motion.com/jake11moran-a269c4)）在同一个社区仓库里。

**从需求到 MP4 的流程**（[SKILL.md](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/vox-explainer/SKILL.md)）：

1. **分流。** 话题模式下，用一个四项筛子帮助选题。材料模式下，从材料里挖出五样东西：观众已有的认知、反差、转折、观众能在屏幕上自己验证的机制、证据。材料撑不起来的节拍直接删掉，不硬编。
2. **脚本。** 写旁白和节拍图，每一句都要过删除测试。
3. **设计稿。** 用真实素材出联系表，每个节拍一帧，在搭任何合成之前先交出去。
4. **旁白。** 自己录或用 TTS（先用 `npx hyperframes tts`；用任何 TTS API 之前，都要先让用户确认服务商和费用）。转写出每个词的时间，以音频为时钟。
5. **搭建。** 一个 HyperFrames 合成，每个节拍一组片段。
6. **质检关卡。** lint 和 check 0 错误；成片里任何超过 3 秒的静止都算规划错误；实测切点；每个节拍内事件间隔 ≤ 3 秒；最后审一遍关键帧拼图。

**渲染栈、依赖、许可。** HyperFrames + GSAP，Node 22+ 和本地安装的 Chrome。转场脚本没有 npm 依赖。`seam-gate.mjs --project` 会通过 `npx` 运行脚本里钉死的 HyperFrames 版本（0.8.14）；用 `--url` 就可以改为指向你自己起的预览服务。Apache-2.0。

**真正聪明的地方**

- **一条管切点的运动定律。** [`references/motion-continuity.md`](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/vox-explainer/references/motion-continuity.md) 规定：A 镜怎么离场，B 镜就怎么入场，同一轴、同一方向、同样速度，切点两边都在运动。每支片只选一个主方向（默认向左），其他方向留作有含义的特殊用途：向上表示结论，沿 Z 轴向前推表示深入，向后拉表示登场。相邻切点方向来回反转算「乒乓」，明令禁止。
- **转场账本，而且会被核验。** 项目根目录的 `ledger.json` 每个切点占一行。[`scripts/seam-stamp.mjs`](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/vox-explainer/scripts/seam-stamp.mjs) 按账本生成转场补间，[`scripts/seam-gate.mjs`](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/vox-explainer/scripts/seam-gate.mjs) 再在无头 Chrome 里逐个实测切点。它检查离场在切点时还在动、入场不从静止起步、实测方向与账本一致、两边画面从不重叠、承接物前后连续（误差 12px / 5% 以内）（[`references/seam-gate.md`](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/vox-explainer/references/seam-gate.md)）。速度不匹配只报警告。
- **防幻灯片的技法底线。** 每个节拍都要事先声明版式和动作手法。静态卡片和左右对比最多占三分之一，相邻两个节拍不能用同一种版式。另有一条「推进约定」：推进一张照片，就必须兑现，要么把主体从底图上抠出来继续用，要么停在满屏上在画面里做标注。
- **对材料来源较真。** 材料模式下，失效的引用要在公开网络上独立核实，核实不了就删。

**局限：** 自带画风是仿 Vox 的拼贴风：实测配色、Archivo Black 标题字、一个反复出现的黄圈。这个 skill 自己写明，这不代表与 Vox 有任何关系，也不得使用 Vox 的 logo。换成品牌皮肤需要用户明确选择。片型以旁白驱动，默认 30fps，素材取自公有领域档案。`--project` 模式会下载一个较旧的钉死版本 HyperFrames，用 `--url` 可以避开。

**谁该用：** 要把报告、备忘录、论文或某个话题做成短解说片的人，尤其看重镜头之间连贯性的场景。

**最适合：** 从文档到解说片，节奏和切点都经过核验。

---

## 5. motion-studio

**一句话：** 一个「小型动效工作室」。它把需求拆成三层：片型（结构）× 画风（外观）× 动作语言（怎么动），再用自带的确定性 HTML 引擎渲染。

**从需求到 MP4 的流程**（[SKILL.md](https://github.com/buildfastwithai/buildfast-skills/blob/main/motion-studio-skill/SKILL.md)）：

1. `detect_env.py` 检查机器上有没有 Chromium 和 ffmpeg。
2. `plan.py` 把需求拆成片型模板、画风、动作、画幅、时长、帧率和音频，并列出自动补上的默认值。
3. agent 写创意和分镜，每镜写明时间、用途、画面、镜头、动画、字体、转场和声音。
4. `plan.py --scaffold` 生成 `spec.json`、`storyboard.md` 和起步用的 `composition.html`。
5. agent 用引擎做出设计。
6. `render.py --stills` 出联系表，`--preview` 出半分辨率的节奏预览；正式渲染逐帧出图转 H.264，配上生成的音乐和音效，再跑 16 项质检。
7. 修改后重渲，最多约 3 轮。

**渲染栈、依赖、许可。** 引擎是 [`engine/ms.js`](https://github.com/buildfastwithai/buildfast-skills/blob/main/motion-studio-skill/engine/ms.js)。Playwright 驱动 Chromium，每帧调用一次 `window.__ms.render(t)`，经 CDP 截图后交给 ffmpeg。需要 Python 3.9+，装 playwright、numpy、scipy、pillow，另需 ffmpeg/ffprobe；Three.js 和 Blender 可选。MIT；内置字体各附 OFL 许可文件。

**真正聪明的地方**

- **16 项自动质检。** [`reference/qc.md`](https://github.com/buildfastwithai/buildfast-skills/blob/main/motion-studio-skill/reference/qc.md) 用 ffmpeg 的 `blackdetect`、`freezedetect` 和 `scdet` 查黑帧、冻帧和意外跳变；它还审计文字是否在安全区内，阅读速度 ≤ 4.5 词/秒，镜头 ≥ 0.4 秒，转场不能全是淡入淡出。每个打击类提示点都要在 30 毫秒内有清晰的起音，音画偏差 ≤ 1 帧。
- **多版本和风格混剪。** `render.py --variants` 用同一条冻结的时间线渲出多种画风，外加一支并排对比片。`stylecut.py` 把同一个镜头放进多种画风，按节拍剪在一起。
- **专为比较模型设计的基准模式。** [`reference/benchmark.md`](https://github.com/buildfastwithai/buildfast-skills/blob/main/motion-studio-skill/reference/benchmark.md) 冻结需求、时间、种子和必须出现的文字，再按质检卫生度打分；同一版本两次重渲结果不一致就扣 20 分。文档明说，这个分数衡量的是卫生度，不是工艺。
- **合成全部由 token 驱动**，换画风只改规格文件，不改镜头。

**局限：** 又是一套要学的引擎，不是 Remotion 也不是 HyperFrames。覆盖面广（7 个家族共 51 种画风，从极简到 VHS 和像素风），意味着很多画风是类型化的预设。不带 TTS，旁白需要现成的录音文件。在这个快照里，仓库 README 的 skill 表列的是另外五个 skill，做视频的这几个 skill 在文件夹列表里容易被漏看。

**谁该用：** 想快速看到同一分镜在多种画风下的效果，或想在固定动效任务上给 coding 模型做基准测试的人。

**最适合：** 画风探索和可复现的模型对比。

---

## 6. generative-film

**一句话：** 产出 45–120 秒、1920×1080、30fps 的 MP4，每一帧都用 pycairo 和 Pillow 在代码里画出来，每一个音都用 numpy 和 scipy 合成。这个 skill 的参考片 *SŪTRA*（印度文明，87 秒）对应画廊条目 [#147 Indian civilisation history film — @BuildFastWithAI](https://www.prompt-motion.com/buildfastwithai-53234e)。它的 prompt 只有一行、13 个英文词，要的是 "a creative mp4 video on indian civilisation"，外加配乐和音效（[原帖](https://x.com/BuildFastWithAI/status/2104451249269780900)）。画廊标注它是一次成片。

**从需求到 MP4 的流程**（[SKILL.md](https://github.com/buildfastwithai/buildfast-skills/blob/main/generative-film-skill/SKILL.md)）：

1. 安装：pycairo 和 fonttools，并检查 Pillow 是否带 Raqm（复杂文字排版要用）。
2. 创意：上屏的每个事实都要查证；定一个贯穿全片的物件；片名用一个词，配一行词典式释义；分 6–10 章。
3. 以拍为单位排时间线，90–110 BPM。
4. 先写音乐，用 `audio_kit.py`，响度目标约 −16 到 −14 LUFS。
5. 用 `engine.py` 写画面。
6. 出测试帧和联系表，通常改 2–3 轮。
7. 按 CPU 核数分块并行渲染，再拼接、混音。
8. 质检：核对帧数，给成片出一张平铺拼图，抽查几帧。

**渲染栈、依赖、许可。** Python，配 pycairo、Pillow（带 Raqm）、numpy、scipy、fonttools，再加 ffmpeg，全程不用浏览器。字体在首次使用时从 google/fonts 的 GitHub 仓库下载。MIT。

**真正聪明的地方**

- **「每章一个想法，而不是每章一张图。」** 每个场景都要展示一个机制，比如一张城市网格被走一遍，或一个分形长出来，而不是给一个名词配插图。能用一张图库照片替代的章节，就要重想。
- **先写音乐。** 一切以拍为单位，每个切点、弹出和闪白都落在音乐事件上。
- **多语言字体靠得住。** Raqm 负责天城文、阿拉伯文、泰米尔文等文字的排版，`missing_glyphs(font, string)` 在渲染前先查出缺字（显示成方块的字）。
- **自给自足。** 完整的 [`engine.py`](https://github.com/buildfastwithai/buildfast-skills/blob/main/generative-film-skill/scripts/engine.py) 和 [`audio_kit.py`](https://github.com/buildfastwithai/buildfast-skills/blob/main/generative-film-skill/scripts/audio_kit.py) 也作为附录印在 SKILL.md 里，[`examples/sutra/`](https://github.com/buildfastwithai/buildfast-skills/tree/main/generative-film-skill/examples/sutra) 放着参考片的源码。

**局限：** 安装命令用的是 `pip install --break-system-packages`，会写进系统 Python，用虚拟环境更稳妥。字体在运行时从 GitHub 下载。自带的美术风格很强（丝网印刷校样感、错版套色、故障闪切、drop 时闪白），不太适合品牌要求严格的项目。交付步骤是为托管沙盒写的（30MB 的聊天上传上限、发文件的工具），在本地 agent 上用要自己改一改。按作者的数字，SŪTRA 在 2 核上渲染约 20 分钟。

**谁该用：** 做文化、历史或科普短片，想要鲜明的图形风格、又不想把浏览器拉进流程的创作者。

**最适合：** 代码绘制的纪录短片，配合成的、卡节拍的配乐。

---

## 7. canvas-documentary（html-animation-skill）

**一句话：** 把一个分章节的故事做成单个自包含的 HTML canvas 文件，带镜头运动、程序化美术、生成音效和播放控件。产出是可交互的网页，不是 MP4。

**流程**（[`html-animation-skill.md`](https://github.com/buildfastwithai/buildfast-skills/blob/main/html-animation-skill/html-animation-skill.md)）：

1. 先写脚本：6–10 章，每章 12–20 秒（全片约 2 分钟），配带时间点的字幕。
2. 采用固定架构，每个场景都是自身局部时间的纯函数。
3. 用 Web Audio 做声音。
4. 做一条带键盘快捷键的播放控制栏。
5. 分段写文件，用 `node --check` 检查语法。
6. 在无头 Playwright 里实际观看：给每个具名的故事节拍截图，再在桌面和手机尺寸下每 2 秒扫一遍全片。

**渲染栈、依赖、许可。** 纯 HTML，Canvas 2D 加 Web Audio，不用任何库，运行时不联网。Playwright 只用于核验。MIT。

**真正聪明的地方：** 每个场景对局部时间是确定的，所以任意跳转几乎不花成本，播放条拖动和自动截图都受益。一条 Hermite 样条驱动所有运动路径，朝向由速度推出。旁白的规矩是「陈述事实，不描述画面」。交互是故事内的：主角会躲开鼠标。文末还有一张清单，列出核验环节「每次都能抓到」的问题。

**局限：** 要视频得自己录屏。这个 skill 只是一个名为 `html-animation-skill.md` 的文件，front matter 写的是 `name: canvas-documentary`，而不是 `SKILL.md`，按 `SKILL.md` 查找的安装器可能发现不了它，需要手动复制。核验步骤假设机器上已装好无头 Chromium。

**谁该用：** 做网页端交互式自然或科普故事、希望观众能拖动、暂停、点击的人。

**最适合：** 交互式叙事页面，而不是渲染出来的视频。

---

## 8. 其余 HyperFrames 社区 skill

同一仓库里还有六个做视频的 skill。仓库 README 提醒，社区 skill 不属于官方精选集，使用前应先审阅。每个 skill 都写明了自己的网络访问和副作用。

| Skill | 做什么 | 技术栈与主要依赖 | 最适合 |
|---|---|---|---|
| [duo](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/duo/SKILL.md) | 把两块 HTML 屏合成进一张固定照片：两只手拿着一部打开的折叠屏手机，1448×1086，30fps | HyperFrames `@latest`（不钉版本）；渲染时从 jsDelivr 加载 GSAP 3.14.2 | 左右对比和梗图类短片 |
| [camera-3d-captions](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/camera-3d-captions/SKILL.md) | 在固定机位的口播人物周围做 3D 字幕：分层景深、借 alpha 蒙版藏到人物身后的词、绕人物转的一圈文字；每段 5–20 秒 | HyperFrames 0.8.62；本地 `remove-background` 模型（首次运行约 170MB）；Python fonttools、numpy、pillow | 需要景深字幕的口播片（真人或数字人） |
| [x-posting-license](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/x-posting-license/SKILL.md) | 用锁死的模板给一个 X 账号做 10.35 秒、1920×1080、60fps 的「发帖驾照」卡片片；`build.mjs` 对所有输入做校验和 HTML 转义 | HyperFrames；读取公开的账号资料；采用 X 的品牌样式 | 趣味账号卡片；发布前请核对 X 的品牌使用条款 |
| [day-in-my-life](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/day-in-my-life/SKILL.md) | 把一次普通会话做成 60–75 秒的手绘墨线短片，配弦乐；需要 5 天内至少 10 次本地会话 | HyperFrames 0.8.70；p5 2.3.2（LGPL-2.1）、p5.brush、puppeteer；配乐用 numpy 和 scipy | 墨线画风的个人会话短片 |
| [prod-by-claude](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/prod-by-claude/SKILL.md) | 1080×1080 的 Strudel 现场编程音乐视频，每个代码 token 在它演奏的那个音上亮起 | HyperFrames 0.8.70；`@strudel/web` 1.3.0（AGPL-3.0，从 npm 安装）；puppeteer-core；Chrome for Testing | 音乐人和现场编程者 |
| [p5-paint-animation](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/p5-paint-animation/SKILL.md) | 自己书写的手写字、重绘成笔触的照片、逐帧重绘的短视频 | Puppeteer + ffmpeg（只有可选的抠像才用 HyperFrames）；p5 2.3.2、p5.brush 2.2.1；每帧约 5–20 秒 | 手作质感和书写效果（不适合精确的品牌字体） |

这个仓库里各 skill 钉的 HyperFrames 版本不一：vox-explainer 的 seam gate 钉 0.8.14，其余依次有 0.8.62、0.8.70、0.8.71，duo 和 x-posting-license 用 `@latest`。用哪个 skill，就配它测试过的那个版本。

---

## 9. 值得借鉴的做法（不分引擎）

下面这些做法离开原来的 skill 也能用，大多不需要安装任何东西。

| 做法 | 出处 | 好处 |
|---|---|---|
| 一套节拍网格同时驱动画面、声音和质检 | cinetic `timeline.ts`；product-film `cues.ts`；generative-film 的拍子 | 音画不会错位，质检读的也是同一组数字 |
| 音效点从动作曲线算出来 | cinetic `sync.ts` / `FILM.cues()` | 作者实测手敲的提示点会偏 8–11 帧 |
| 从技法库里随机抽技法 | cinetic `pick.py` | 打破「淡入、推近、片尾卡」的惯性 |
| 写转场账本并自动核验 | vox-explainer `ledger.json` + `seam-gate.mjs` | 抓出从静止起步的切点、停住的离场和方向乒乓 |
| 一个故事文件同时编译出画面和配乐时间线 | session-story `schedule.mjs` | 改一处，两条轨道一起更新 |
| 解码交付文件，核对颜色 | product-film `verify.py` | 抓出编辑器里看不到的色彩范围偏移 |
| 先出 PNG，只编码一次；渐变加抖动 | cinetic `hf-finish.sh`、`dither-gradient.py` | 避免两道压缩和深色渐变上的色带 |
| 对成片 MP4 做像素法医 | cinetic `forensics.py`；motion-studio `qc.py` | 抓出跳帧、冻帧、黑帧和意外跳变 |
| 给阅读时间定硬数字 | cinetic：60fps 下 36 帧 + 每词 6 帧；motion-studio：≤ 4.5 词/秒 | 文字在屏幕上停得够久，读得完 |
| 冷场判失败；真实引语要过确认关 | session-story `score/qc.py` 和它的确认表 | 静音变成可报的错误；没人会看到自己没同意的话 |

**零安装的第一步。** 拿一支你已经做好的片子，用任意 ffmpeg tile 滤镜导出一张联系表，按 cinetic [`references/review-loop.md` §9](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/references/review-loop.md) 的 11 维评分表打分。成品质量和音画同步两项需要它的脚本，先留空。再按 vox-explainer 的格式给同一支片的切点写一份 `ledger.json`。光是把这张表写出来，方向来回反转和从静止起步的切点往往就看得出来。

---

## 10. 怎么选

| 如果你想要…… | 先看 |
|---|---|
| 一支带量化质检的发布片、片头或循环片，并且能接受较长的运行时间 | cinetic |
| 一支和你的产品一模一样、用你自己的组件搭的片子 | product-film（如果适用，预留 Remotion 授权的预算） |
| 留在 HyperFrames 生态里 | cinetic 加 `--engine hyperframes`，或 vox-explainer |
| 从文档或话题做解说片 | vox-explainer |
| 同一分镜试多种画风，或给模型做基准测试 | motion-studio |
| 不用浏览器做图形纪录短片 | generative-film |
| 交互式叙事页面 | canvas-documentary |
| 一支记录你和 agent 会话的个人短片 | session-story（水彩）或 day-in-my-life（墨线） |

这些 skill 都能执行命令、读文件，有些还会访问网络服务。安装前先读一遍 `SKILL.md` 和脚本，这也是 HyperFrames 社区仓库 README 自己的建议。

---

## 11. 方法与局限

- **只读。** 每个仓库都按[上面](#四个仓库一览)列出的快照 commit 阅读，包括 `SKILL.md`、参考文档和脚本头部说明。我们没有安装或运行任何东西。
- **仓库里的数字都是作者自己的数字**，文中都注明了出处，包括渲染时间、token 成本、评测结果和实测偏差。我们没有复现这些数字。
- **我们自己算的数字：** cinetic 技法库的 273 个技法和 14 个类别，motion-studio 的 51 种画风、10 种动作语言和 13 种片型模板，以及来自 `catalog.json` 的「233 条中 4 条」和技术栈统计。
- **许可信息**取自各仓库的 `LICENSE` 文件和 skill 内的第三方声明。引擎和库的许可（Remotion、p5、Strudel）按仓库的说法转述，商用前请读原文。
- **本文不使用任何质量评分。** 画廊条目只用来说明各 skill 做出了什么，不用来给视频排名。
- **快照会过时。** 这个领域的 skill 每周都在变，快照之后的变化请看各仓库的更新日志或提交历史。
