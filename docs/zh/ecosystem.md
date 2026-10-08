# 生态地图：和 prompt-motion.com 同类的站点与仓库

这份文档收录我们能找到的、和 [prompt-motion.com](https://www.prompt-motion.com/) 做同一件事的站点和仓库，也就是收集 AI 做的动效视频，每条配上背后的 prompt、源码或 skill。周边的框架官方展示页、skill 目录和动效灵感站也一并列出。快照日期 **2026-10-09**。条目数一律采用各站在核查当天自己公布的数字，每天都在变。

做个参照：prompt-motion.com（由 [@p4nthera_](https://x.com/p4nthera_) 整理）本身有 233 条（见[必看清单](top-picks.md)）。

[English version](../ecosystem.md)

## 要点速览

- **共 100 个独立项目。**核实后的清单有 132 行，其中很多是同一个项目出现了两次：中英文两个页面、网站和它的 GitHub 源仓库、同一个站的不同页面。我们把这些合并成每个项目一行。另有 55 个候选核查后剔除。
- **最大的几个 prompt 库**（2026-10-09 复核）：[Oneshotted](https://oneshotted.io/) 6,164 条，约为 prompt-motion.com 的 26 倍；[24fps](https://24fps.dev) 4,607 条；[JasonZhu.AI](https://jasonzhu.ai/zh/prompts/claude-opus-5-5) 1,402 条；[Claude Video](https://claudevideo.org/) 1,276 条；[Awesome AI Motion](https://guanmo-ai.github.io/awesome-ai-motion/) 581 条；[Skillry](https://skillry.dev/zh/ai-videos/opus-5-5) 513 条 Opus 5.5，另有 80 条 Fable 5.5。
- **带完整 prompt 的反而是少数。**很多作者只发了视频，没有公开 prompt。带 prompt 的比例：24fps 是 4,607 条里有 1,073 条（23%）；JasonZhu.AI 是 1,402 条里有 361 条（26%），其中完整的 148 条（11%）；Claude Video 是 1,276 条里有 457 条（36%）；Awesome AI Motion 是 581 条里 83 条（14%）标为「原文」。
- **各家重叠很多。**它们抓的是 2026 年 9 月下旬起同一波 X 帖子。Tellcut 的 470 条全部也在 WorkSkill 里；HiAPIAI 的 425 条里有 333 条出现在 Skillry 的数据中；TopView 的 Opus 条目来自 YouMind；24fps 自称数据来自 129 个 GitHub 合集。
- **从哪里开始看：**Oneshotted（规模最大，标明每条 prompt 的来源，有 MCP）；24fps（每条都写清使用权限，有 MCP/API，还把同一个 prompt 跑了 109 次）；Skillry 和它的 MIT 数据集（原片和复刻并排播放）；JasonZhu.AI（中英双语，每张卡片标明 prompt 完整度）；HyperFrames 官方文档（18 条原样渲染的 prompt，加 400 个带源码的 block）。
- **带许可证的开放数据：**[yihui-dev/awesome-opus5-5-videos](https://github.com/yihui-dev/awesome-opus5-5-videos)（MIT，513 行，3,101★）、guanmo-ai（代码 MIT）、Li-Evan（整理内容 CC-BY-4.0）、athemeroy（CC-BY-4.0）。好几个热门清单没有许可证文件。作者的 prompt 和视频都不在任何仓库许可证的覆盖范围内。
- **各站条款差别很大。**Oneshotted、Swishy、Pexo、AutoAE、60fps.design 和 MotionSites 的条款禁止爬取，其中好几家提供 MCP 或 API 作为替代。详见[第 7 节](#7-怎样合规地使用)。

## 目录

1. [规模与入门推荐](#1-规模与入门推荐)
2. [直接同类：AI 做的动效，每条配 prompt](#2-直接同类ai-做的动效每条配-prompt)
3. [GitHub 上的开源清单与数据集](#3-github-上的开源清单与数据集)
4. [框架官方展示与模板库](#4-框架官方展示与模板库)
5. [Skill 与 skill 目录](#5-skill-与-skill-目录)
6. [网页动效灵感站（不带 prompt）](#6-网页动效灵感站不带-prompt)
7. [怎样合规地使用](#7-怎样合规地使用)
8. [方法](#8-方法)

---

## 1. 规模与入门推荐

### 最大的几个合集

| 合集 | 条目数（站方公布） | 带 prompt 的 | 核查日期 |
|---|---|---|---|
| [Oneshotted](https://oneshotted.io/) | 6,164 条，3,716 位作者 | 3,838 条 prompt（站方口径） | 2026-10-09；前一天是 6,144 |
| [24fps](https://24fps.dev) | 4,607 条，2,540 位作者，44 个模型 | 1,073 | 计数标注为 2026-10-03，10-09 未变 |
| [JasonZhu.AI](https://jasonzhu.ai/zh/prompts/claude-opus-5-5) | 1,402 条，838 位作者 | 361（完整 148） | 2026-10-09；站点 10-08 更新 |
| [Claude Video](https://claudevideo.org/) | 1,276 条，1,007 位作者 | 457 条带完整 prompt | 2026-10-09 |
| [Awesome AI Motion](https://guanmo-ai.github.io/awesome-ai-motion/) | 581 条 | 原文 83，简述 118 | 2026-10-09；数据截至 10-06 |
| [Skillry](https://skillry.dev/zh/ai-videos/opus-5-5) | Opus 5.5 513 条 + Fable 5.5 80 条 | Opus：完整 279，标为「部分」234 | 2026-10-09 |
| [WorkSkill](https://workskill.tools/ai-videos/opus-5-5) | Opus 5.5 478 条 + Fable 5.5 76 条 | 每条都有 prompt 区块，长短不一 | 2026-10-09 |
| [Tellcut](https://tellcut.app/examples) | 470 条 | 完整 276，节选 194 | 2026-10-09 |

规模更大、但不是同一类的合集：[TopView](https://www.topview.ai/video-prompts) 有 12,430 条视频 prompt，大多是给生成式视频模型用的；[What Ships](https://whatships.com) 收了 2,447 支由工作室和团队做的发布片；[HyperFrames Studio 社区](https://www.hyperframes.dev/?view=community) 有 949 个项目，每个都带源码。

### 从哪里开始看

1. **[Oneshotted](https://oneshotted.io/)：看广度。**它是规模最大的一个。作者本人的 prompt 和站方「从视频画面反推」的版本分开标注。可以按框架筛选（Remotion、HyperFrames、GSAP、Three.js、Motion Canvas、Manim）。有 MCP 和 agent skill，coding agent 可以在站方限额内直接检索。
2. **[24fps](https://24fps.dev)：给 agent 用、版权写得清楚的索引。**每条都写明能怎么用，其中 395 条是开源许可、附源码。提供 MCP、JSON API 和 `llms-full.txt`。「一个 prompt，109 次运行」页面直观展示同一份 brief 每次跑出来能差多少。
3. **[Skillry](https://skillry.dev/zh/ai-videos/opus-5-5) + [yihui-dev/awesome-opus5-5-videos](https://github.com/yihui-dev/awesome-opus5-5-videos)：要干净的数据就看这个。**513 条 MIT 许可的 JSON，只公开了部分 prompt 的条目会单独标出。网站上原片和实时复刻并排播放。
4. **[JasonZhu.AI](https://jasonzhu.ai/zh/prompts/claude-opus-5-5)：按 prompt 完整度筛选。**中英双语。每张卡片标明 prompt 是完整（附字数）、简述还是没有，以及需不需要你自己准备参考素材。
5. **HyperFrames 官方文档（[prompt 示例](https://hyperframes.heygen.com/prompting/examples)、[catalog](https://hyperframes.heygen.com/catalog)）：prompt 和成片能一一对上。**18 支视频都标明是用所示 prompt 原样渲染、未经剪辑；catalog 有 400 个 block 和组件，源码为 Apache-2.0。

---

## 2. 直接同类：AI 做的动效，每条配 prompt

这些站收集多位作者用 AI coding agent 做的动效作品，每条附 prompt（或源码），按规模排序。几乎每家都标注并链接作者的 X 原帖。

### 2a. 大型合集（250 条以上）

| 合集 | 条目数 | 每条附带 | 备注 |
|---|---|---|---|
| [Oneshotted](https://oneshotted.io/) | 6,164 条，3,838 条 prompt，3,716 位作者 | 作者公开了 prompt 的就用作者原文；另附单独标注的站方反推版本；有 MCP 和 agent skill | 会标出「尚未在 X 上确认」的 prompt。约 4,950 条是视频类，其余是网页 UI 动效或「其他」。 |
| [24fps](https://24fps.dev) | 4,607 条，2,540 位作者，44 个模型 | 1,073 条带 prompt（280 字符以内全文展示，更长的给节选加链接）；395 条开源许可的附源码；有 MCP、JSON API、`llms-full.txt` 和 skill；另有 2,125 个编辑器预设 | 自称数据来自 129 个 GitHub 合集、作者原帖和公开网页。视频通过 X 嵌入播放。55% 的条目没有记录框架。 |
| [JasonZhu.AI](https://jasonzhu.ai/zh/prompts/claude-opus-5-5)（[English](https://jasonzhu.ai/en/prompts/claude-opus-5-5)） | 1,402 条，838 位作者 | 361 条带 prompt，其中完整的 148 条 | 中英双语。每张卡片标 prompt 状态，以及「需要自备参考素材」。覆盖 Opus、Sonnet、Fable 5.5，也收游戏（233）和模型对比（186）。源仓库：[zhuyansen/awesome-opus-5.5-video](https://github.com/zhuyansen/awesome-opus-5.5-video)。 |
| [Claude Video](https://claudevideo.org/) | 1,276 条，1,007 位作者 | 457 条带完整 prompt；每条有编辑点评和「照着做一个」指南；附 247 个 skill 的目录 | 可按「有 prompt」排序。为 agent 提供 `llms.txt`。 |
| [Awesome AI Motion](https://guanmo-ai.github.io/awesome-ai-motion/)（guanmo-ai） | 581 条 | 每条标 prompt 状态（原文 83、简述 118、未知 380）；62 条附代码、demo 或工具链接 | 标题和摘要中英双语，全部数据在一个 `cases.json` 里。有些是生成式视频（Seedance、Kling、Veo），不是代码做的。 |
| [Skillry](https://skillry.dev/zh/ai-videos/opus-5-5)（[English](https://skillry.dev/ai-videos/opus-5-5)，[Fable 5.5](https://skillry.dev/ai-videos/fable-5-5)） | Opus 5.5 513 条 + Fable 5.5 80 条 | Opus 每条都有 prompt（完整 279，标为「部分」234）；Fable 80 条里 8 条有 | 原片和实时复刻并排播放，并链接可安装的 skill。数据：[yihui-dev/awesome-opus5-5-videos](https://github.com/yihui-dev/awesome-opus5-5-videos) 和 [awesome-fable5-5-videos](https://github.com/yihui-dev/awesome-fable5-5-videos)（MIT）。 |
| [WorkSkill](https://workskill.tools/ai-videos/opus-5-5) | Opus 5.5 478 条 + Fable 5.5 76 条 | 每条有 prompt 区块、作者署名和站内托管的 MP4 | 包含 Tellcut 的全部 470 条，另有截至 2026-10-07 的更新帖子。数据：[mailes/awesome-claude-5-5-videos](https://github.com/mailes/awesome-claude-5-5-videos)（MIT）。有些 prompt 字段只有标题或一句话。 |
| [Tellcut examples](https://tellcut.app/examples)（opus6.video 会跳转到这里） | 470 条 | 完整 prompt 276 条，节选 194 条 | 每张卡片标明 prompt 是完整还是节选。视频要跳到 X 上看。整套数据是一个 `examples.json`。姊妹页 [/effects](https://tellcut.app/effects) 有 21 个动效及其 prompt。 |
| [YouMind](https://youmind.com/zh-CN/opus-5-5-prompts)（[English](https://youmind.com/opus-5-5-prompts)） | Opus 5.5 340 条 | 完整 prompt 加译文、MP4、作者署名 | 约 15 种语言界面，含日语。很多条目是可交互的 Three.js 页面。另有一个[网页 prompt 总站](https://youmind.com/prompts/webpage)，加收 452 条 GPT 6 Astra 和 49 条 Gemini 3 Pro 的 prompt。 |
| [Awesome Opus 5.5 Video Prompts](https://li-evan.github.io/awesome-opus-5.5-video-prompts/)（Li-Evan） | 334 条，302 位作者 | 逐字原文 prompt 加中文翻译，按类型标注（一句话型 190、简述 77、规格书 24、模板 23、流水线 20） | README 说有校验程序逐条确认 prompt 是作者原帖里的原文。附「导演工具箱」（流程、结构拆解、术语表）。最后更新 2026-09-27。 |
| [Skilloop](https://skilloop.dev/zh/ai-video/opus-5-5)（[English](https://skilloop.dev/ai-video/opus-5-5)） | Opus 5.5 278 条 + Fable 5.5 45 条 | 278 条里约 161 条有某种 prompt（其中 133 条全文来自 yihui-dev 清单）；其余页面写着「作者未公开提示词」 | 源仓库：[xianyu110/awesome-claude-opus-5.5](https://github.com/xianyu110/awesome-claude-opus-5.5)（精选 281 条，144 条带 prompt，另有 1,019 条的大名单）和 [awesome-fable-5.5](https://github.com/xianyu110/awesome-fable-5.5)（54 条，16 条带 prompt）。 |
| [生成提示词案例库](https://img.dsxzai.com/)（chuspeeism） | Opus 5.5 300 条（另有 485 条图片 prompt） | 36 条带作者原 prompt，其余附制作说明 | 中文界面，有公开的 JSON API；仓库为 MIT。最后更新 2026-09-27。 |
| [BeatAPI](https://beatapi.io/opus-5-5-videos) | 302 条；[GPT-6 Astra 3D 页](https://beatapi.io/gpt-6-astra-3d-prompts)另有 306 条 | Opus 页每张卡片链接到 yihui-dev 仓库里的 prompt 文件；3D 页标注 prompt 可信度（逐字 47、作者自述 163、来源转述 96） | 302 条里有 282 条固定引用 yihui-dev。3D 数据：[BeatAPI/awesome-3d-prompts](https://github.com/BeatAPI/awesome-3d-prompts)（MIT）。 |
| [TopView 视频 prompt 库](https://www.topview.ai/video-prompts?q=opus) | 共 12,430 条，搜「opus」约 261 条 | prompt、MP4、作者署名 | 大部分是生成式视频模型（Seedance、Grok）的 prompt，Opus 条目转自 YouMind。[Abstract VFX](https://www.topview.ai/abstract-vfx-v-subject-video-prompts) 分类里有不少代码做的作品。 |

### 2b. 小型精选合集

| 合集 | 条目数 | 每条附带 | 备注 |
|---|---|---|---|
| [Remotion Prompt Showcase](https://www.remotion.dev/prompts) | 25 条 | 完整 prompt，以及所用工具和模型 | 官方。模型从 Opus 4.5 到 4.7，另有 Kimi K2.5；最新一条约在 2026 年 5 月。归入 Remotion（见[第 4 节](#4-框架官方展示与模板库)）。 |
| [HyperFrames 示例 prompt](https://hyperframes.heygen.com/prompting/examples) | 18 条 | 逐字 prompt；每支视频都标明由该 prompt 原样渲染、未经剪辑 | 官方文档，附一段共用的动效前言。8 条用到 registry block 或 skill，10 条是自由发挥。归入 HyperFrames（见[第 4 节](#4-框架官方展示与模板库)）。 |
| [可搜索合集](https://eastling.github.io/awesome-opus-5.5-video-prompts/)（eastling） | 90 条 + 入门模板 | 完整 prompt、一句「为什么有效」点评、技术标签 | 入门模板按片型写了结构要点。90 条帖子都在 Tellcut 里也有；仓库主页指向 opus6.video。清单本身为 CC0。 |
| [AI × Leaders](https://ai-x-leaders.com/en/prompt/) | 80 条 | 每条标 prompt 状态（完整 16、已核实来源 13、节选 20、未核实 23 等） | Claude 和 OpenAI 分两个标签页，可导出，有 `catalogue.json`。 |
| [APIModels](https://apimodels.app/claude-opus-5-5-video-prompts) | 60 个案例 | 约 24 条可复制 prompt，其余标为未公开 | 每个案例写了工具链、时长、分辨率、成本、踩坑点，以及「同一个 prompt 的其他运行结果」。另附 prompt 公式和 6 个工作流模板。 |
| [Claude Video Atlas](https://yeadon8888.github.io/claude-video-atlas/) | 53 条 | 5 条带作者 prompt，4 条带 MIT 源码；其余附整理者自写的模板，页面上有标明 | 来源不止 X，还有小红书、抖音、YouTube 和 GitHub。44 位作者里只有 4 位也出现在 prompt-motion.com。最后更新 2026-09-26。 |
| [AY Automate](https://www.ayautomate.com/resources/claude-opus-5-5-motion-graphics) | 48 条帖子 | 10 条附作者完整 prompt，逐字照录 | 帖子抓取于 2026-09-28。分类包括作品集、落地页、3D 与物理等。 |
| [AI9app](https://ai9app.io/video-prompts/opus-5-5) | 30 条 | 免费完整 prompt、X 署名、镜像视频 | 很多标题是繁体中文。 |
| [mg-styles-15](https://vincentwei1021.github.io/mg-styles-15/) | 15 支片 | 每支都有 prompt、源码和 MP4，另附评分标准 | 一位作者做的 15 种动效设计风格；MIT。 |
| [Opus 5.5 统一效果图鉴](https://github.com/jinhanbuilds/opus-5-5-unified-gallery)（jinhanbuilds） | 122 个 demo，其中 15 个是视频类 | 每条附原 prompt；另有 75 个关键词的「动效词典」和 prompt 生成器 | 中文。大部分条目是 MiaAI-Lab「100 个 HTML」里的交互页面；15 个视频 demo 是按 prompt 重新生成的。 |
| [Made with Motion](https://motion.so/made-with-motion)（Mosaic） | 8 条 | 一句话 prompt、4 步流程和 MP4 | agent 做的发布片和讲解片。最后更新 2026-06-18。 |
| [Muzli：设计师用 Opus 5.5](https://muz.li/blog/claude-opus-5-5-for-designers/) | 3 个 demo | 每个附完整 prompt 和独立 HTML | 其中一个是 12 秒的动态字体片头，整片只用一条 GSAP 时间轴。另附 brief 模板和一段 `CLAUDE.md` 设计规则示例。 |

### 2c. 工具、厂商与单一团队的作品集

每条都附 prompt 或源码，但都是用同一个产品做的，或出自同一个团队。

| 作品集 | 条目数 | 每条附带 | 备注 |
|---|---|---|---|
| [showtime examples](https://faviovazquez.github.io/showtime/gallery.html) | 32 条 | 发给 agent 的原始请求，加完整项目源码 | 一个工具的示例集，有发布片、PR 视频、讲解片、预告片；MIT。 |
| [Claude Imagine](https://claudeimagine.com/opus-5-5-video) | 30 个复刻 | 每个模板附完整 HyperFrames 源码（MIT）；共用一条「按联系表重建」的 prompt | 用虚构品牌重新实现，每条都标注灵感来源的帖子。 |
| [ChatCut prompt library](https://chatcut.io/prompt-library) | 133 张卡片 | 每张有 prompt 入口和预览；约 104 张附 Remotion TSX | 单一厂商的模板。「Try this prompt」会打开 ChatCut 应用。 |
| [Swishy](https://www.swishy.ai/) | 143 个模板 | 用户 prompt 加 Remotion 场景源码 | 模板在首页和 `/templates/<slug>` 上，多数是简短的 UI 和社媒片段。 |
| [iArt.ai templates](https://www.iart.ai/templates) | 精选 23 个，社区流更多 | prompt 和多段 GSAP/Remotion 代码，在应用的分享页里查看 | 显示作者名和被 remix 的次数。 |
| [Hera](https://www.hera.video/templates) | 13 个模板 + 11 个公开分享项目 | 模板 prompt 带占位符；分享项目公开 prompt 修改链和 GSAP HTML | 分享的作品出自 2025 年。完整模板库需要登录。 |
| [Pexo gallery](https://pexo.ai/gallery) | 712 支，其中约 200 支和动效相关 | 每支有结构化 prompt 和 MP4 | 大部分是生成式视频（Seedance、Kling、MiniMax）。prompt 是结构化 brief（主体、风格、镜头、光线）。 |
| [Motion Face](https://motionface.cc/) | 95 段 | 每段绑定一个 Remotion 源码仓库，用积分解锁 | 中文站，很多是 Remotion 复刻。还有一个 Opus 5.5 付费任务板。播放需要登录。 |
| [Leon's demos](https://leons-demos.vercel.app) | 58 张卡片，11 张是视频 | 11 张附仓库链接，1 张附 prompt | 一位作者的 X 作品集，链接到 cinetic 和 claude-launchvideo 仓库。 |
| [PremiereCopilot Vibe Motion](https://www.premierecopilot.com/vibe-motion) | 11 条 | 原始 prompt 和 MP4 | Premiere Pro 插件产品页上的一个板块。 |

### 2d. AI 做的作品，但不附 prompt

| 作品集 | 条目数 | 附带 | 备注 |
|---|---|---|---|
| [Revid：Claude Opus 5.5 动效](https://www.revid.ai/claude-motion-graphics) | 64 支 | MP4、署名和互动数据；没有作者 prompt | 按互动排名，含 17 支发布片。55 位作者里有 40 位不在 prompt-motion.com 上。收录 2026-09-23 到 09-27 的帖子。 |
| [Frontier Games](https://theolundqvist.github.io/frontier-games/) | 127 个游戏 + 80 支片 | 可玩的构建版本和作者录屏 | Opus 5.5（65 个游戏）与 GPT-6 Astra（62 个）并列展示。没有许可证文件。 |

**prompt-motion.com 自身的副本。**我们发现了两份 prompt-motion.com 条目的副本：一个 GitHub 仓库有 229 个 prompt 文件，另一个独立域名列出 230 条，slug 全部一致。它们没有新增条目，所以不计入总数。请直接看原站。

---

## 3. GitHub 上的开源清单与数据集

### 3a. 以 GitHub 为主的清单

| 仓库 | 条目数 | 许可证 | 备注 |
|---|---|---|---|
| [athemeroy/awesome-claude-5-5-videos](https://github.com/athemeroy/awesome-claude-5-5-videos) | 精读 168 条；统计语料 1,511 条候选帖子 | CC-BY-4.0 | 研究型索引。案例按制作路线分组（程序化 2D 52、讲解 27、3D/实时 19），附 prompt 重叠、prompt 长度、风格等 CSV。150 位作者里有 134 位不在 prompt-motion.com 上。497★。 |
| [LeaddeOpenLab/awesome-opus-5-5-video-prompts](https://github.com/LeaddeOpenLab/awesome-opus-5-5-video-prompts) | 398 条 | 无 | 每条 prompt 都有出处字段（公开程度、核实状态、原文范围）和 GIF。约 141 条不在 WorkSkill 或 Tellcut 里。 |
| [HiAPIAI/awesome-opus-5-5-video-styles](https://github.com/HiAPIAI/awesome-opus-5-5-video-styles) | 425 条 prompt，分 12 种风格 | CC-BY-4.0（prompt 和媒体除外） | 每种风格一份配方，比如产品 UI 宣传（80）、动态字体（52）。只有静帧，没有视频。425 条里有 333 条在 Skillry 的数据中。 |
| [X-RayLuan/awesome-opus-5-5-video-prompts](https://github.com/X-RayLuan/awesome-opus-5-5-video-prompts) | 83 条 | 文档和工具 MIT；媒体见 RIGHTS.md | 中英双语。视频片段经 jsDelivr 分发，prompt 标明逐字照录。83 条里有 64 条不在 WorkSkill 里。 |
| [opusvideo/awesome-claude-video](https://github.com/opusvideo/awesome-claude-video) | 59 条 | 无 | 约 25 篇中英文分步实现指南。21 条有 prompt 或 brief。只收浏览量超过 1 万的帖子。 |
| [joeseesun/opus-video-prompts](https://github.com/joeseesun/opus-video-prompts) | 54 个案例，18 条完整 prompt | 无 | 按 9 条技术路线整理，覆盖发布当周 09-22 到 09-25。 |
| [real-leo/awesome-opus-videos-aggregate](https://github.com/real-leo/awesome-opus-videos-aggregate) | 4 个清单去重后 846 行 | CC BY 4.0 | 元索引，只有 2026-09-28 一次提交。 |
| [cindyxu1030/motion-graphics-prompt-bank](https://github.com/cindyxu1030/motion-graphics-prompt-bank) | 57 条 prompt 加 GIF | CC BY-NC-SA 4.0 | 一位作者自制。HyperFrames prompt 带占位符；其中 15 个发布预告场景是从 AI 产品发布片里反推出来的。 |
| [maning636/motion-prompts](https://github.com/maning636/motion-prompts) | 379 条 prompt；配套站点有 1,004 个带预览的模板 | 自定义许可，非 OSI | 中文，单文件 GSAP HTML。许可证禁止把 prompt 重新打包或转传。 |
| [Markjinli/awesome-hyperframes-prompt](https://github.com/Markjinli/awesome-hyperframes-prompt) | 28 个模板 | 无 | 每个模板有 `prompt.md` 和 `index.html`；中文。最后推送 2026-05-14。 |

### 3b. 各网站背后的数据

第 2 节里好几个站公开了数据。仓库许可证只覆盖仓库自己的文字和代码，prompt 和视频在任何情况下都仍归原作者。

| 站点 | 数据集 | 许可证 | 行数 |
|---|---|---|---|
| Skillry | [yihui-dev/awesome-opus5-5-videos](https://github.com/yihui-dev/awesome-opus5-5-videos) `data/videos.json`（另有 awesome-fable5-5-videos） | MIT | 513（+80） |
| WorkSkill | [mailes/awesome-claude-5-5-videos](https://github.com/mailes/awesome-claude-5-5-videos) `data/opus-5-5.json` | MIT | 477（+76 Fable） |
| JasonZhu.AI | [zhuyansen/awesome-opus-5.5-video](https://github.com/zhuyansen/awesome-opus-5.5-video) `cases.json` | 无许可证文件 | 1,402 |
| Skilloop | [xianyu110/awesome-claude-opus-5.5](https://github.com/xianyu110/awesome-claude-opus-5.5) `data/selected.json` | 无许可证文件 | 281（大名单 1,019） |
| Awesome AI Motion | [guanmo-ai/awesome-ai-motion](https://github.com/guanmo-ai/awesome-ai-motion) `data/cases.json` | 代码和文档 MIT，第三方内容除外 | 581 |
| Li-Evan | [Li-Evan/awesome-opus-5.5-video-prompts](https://github.com/Li-Evan/awesome-opus-5.5-video-prompts) `site/data.json` | 整理内容 CC-BY-4.0 | 334 |
| eastling | [eastling/awesome-opus-5.5-video-prompts](https://github.com/eastling/awesome-opus-5.5-video-prompts) `data/prompts.json` | 清单 CC0 | 90 |
| chuspeeism | [chuspeeism/awesome-opus-5-5-videos](https://github.com/chuspeeism/awesome-opus-5-5-videos) `data/cases.json` | 仓库文字 MIT | 300 |
| Claude Video Atlas | [Yeadon8888/claude-video-atlas](https://github.com/Yeadon8888/claude-video-atlas) `data/cases.json` | 站点代码 MIT | 53 |
| Tellcut | `tellcut.app/data/examples.json`（无仓库） | 未说明 | 470 |
| 24fps | `24fps.dev/llms-full.txt`（无仓库） | 见逐条版权页 | 4,607 |

### 3c. 各家的数据从哪来

- **yihui-dev 是很多家的上游。**Skillry 建在它之上；BeatAPI 固定引用其中 282 条；Skilloop 从中取了 133 条完整 prompt；HiAPIAI 自述部分源自它；real-leo 把它合并进总表。
- **Tellcut 包含于 WorkSkill，eastling 包含于 Tellcut。**Tellcut 的每条帖子 WorkSkill 都有，eastling 的每条帖子 Tellcut 都有。
- **YouMind → TopView。**TopView 的 Opus 条目都带 `source_type: youmind`。
- **24fps** 自称计数来自 129 个 GitHub 合集、作者原帖和公开网页。
- **guanmo-ai** 的 `THIRD_PARTY.md` 引用了 joeseesun、athemeroy 和 Frontier Games。
- **Claude Video** 的 skill 页面是根据 [awesome-claude-video-skills](https://github.com/zhuyansen/awesome-claude-video-skills) 清单（CC0）做的。

实际意义：想看原始 prompt，就顺着署名找到作者本人的帖子。这些合集引用的大多是同一批帖子。

---

## 4. 框架官方展示与模板库

### 4a. HyperFrames（HeyGen）

框架仓库 [heygen-com/hyperframes](https://github.com/heygen-com/hyperframes) 为 Apache-2.0，2026-10-09 有 59,087★。官方各页面：

| 页面 | 条目数 | 每条附带 | 备注 |
|---|---|---|---|
| [Prompt 示例](https://hyperframes.heygen.com/prompting/examples) | 18 支视频 | 逐字 prompt；每支视频都标明原样渲染、未经剪辑 | 每条 prompt 前要先贴一段共用前言。也有 `/prompting/examples.md` 版本。 |
| [Catalog](https://hyperframes.heygen.com/catalog) | 400 个（170 个 block、222 个组件、8 个示例） | 预览视频、源码，以及 `npx hyperframes add <name>` 安装命令 | 每页都有对应的 `.md` 版本，内含 composition HTML。 |
| [Examples / showcase](https://hyperframes.heygen.com/examples) | 约 23 支片，另有 2 组「参考片 vs 复刻」对照 | 11 支附源码，放在 [hyperframes-launches](https://github.com/heygen-com/hyperframes-launches)（20 个项目文件夹，含分镜和 brief） | 内含的媒体、logo、字体不在许可证范围内。 |
| [30 Days of HyperFrames](https://hyperframes.heygen.com/thirty-days) | 30 课 | 每课一个 MP4 和一条附可复制 prompt 的 X 帖子 | prompt 在 X 帖子里。 |
| [Studio 社区](https://www.hyperframes.dev/?view=community) | 949 个项目，来自 861 位用户（34 个精选，86 个有渲染好的 MP4） | 每个项目的完整 composition HTML | robots.txt 禁止访问 `/api/`。 |
| [社区 skill](https://github.com/heygen-com/hyperframes-community-skills) | 8 个 skill | `SKILL.md` 和脚本 | Apache-2.0。README 提醒安装前逐个审查。 |

### 4b. Remotion 生态

| 项目 | 条目数 | 附带 | 许可证 / 备注 |
|---|---|---|---|
| [Remotion](https://www.remotion.dev/showcase)（官方） | [Prompt showcase](https://www.remotion.dev/prompts) 25 条；[showcase](https://www.remotion.dev/showcase) 80 支，3 支附源码；[elements](https://www.remotion.dev/elements) 42 个；[资源索引](https://www.remotion.dev/docs/resources/) 约 200 个链接 | prompt、产品视频、带代码的组件和链接目录 | Remotion License：员工超过 3 人的公司需要购买公司授权。 |
| [Remocn](https://remocn.dev) | 364 个 registry 条目；55 支 showcase 发布片 | 组件 TSX 附「复制 prompt」按钮；showcase 源码在 remocn-collections | 主仓库 MIT；remocn-collections 没有许可证文件。 |
| [snapcn](https://snapcn.dev) | 免费 46 个 + Pro 51 个组件；6 个工作流 skill | 每个组件有实时播放器、「复制 prompt」按钮和编排说明 | 免费部分 MIT，Pro 付费。 |
| [RenderComp 免费模板](https://rendercomp.com/free) | 50 个 | 源码加 MP4 预览 | MIT（[GitHub](https://github.com/RenderComp/free-remotion-templates)）。 |

### 4c. GSAP 与网页动画

| 项目 | 条目数 | 附带 | 许可证 / 备注 |
|---|---|---|---|
| [GSAP Demo Hub](https://demos.gsap.com/) + [gsap-skills](https://github.com/greensock/gsap-skills) | 约 78 个 demo；8 个官方 agent skill | 每个 demo 附 CodePen 源码；skill | GSAP 标准许可；skill 为 MIT（16,034★）。 |
| [Made With GSAP](https://madewithgsap.com/) | 120 个效果，其中 2 个免费 | 每个效果附教程、代码 ZIP 和 AI prompt | 付费。许可证禁止把代码放进公开仓库。 |
| [Motion examples](https://motion.dev/examples) | 462 个 | 每个都有预览 MP4；152 个免费附源码，另外 310 个需要 Motion+ | UI 微交互。库本身 MIT。 |
| [Codrops Creative Hub](https://tympanus.net/codrops/hub/) | 1,000+ 个 demo；347 个 GitHub 仓库 | 在线 demo 加 MIT 的 GitHub 仓库 | robots.txt 声明不许用于 AI 训练，并屏蔽 AI 爬虫；请用 [GitHub 仓库](https://github.com/codrops)。 |
| [React Bits](https://reactbits.dev/) | 200+ 个免费组件（另有 230 个 Pro） | 每个组件的完整源码，以 shadcn registry JSON 提供 | MIT + Commons Clause。 |

### 4d. 其他动效工具与模板库

| 项目 | 条目数 | 附带 | 许可证 / 备注 |
|---|---|---|---|
| [Open Design](https://open-design.ai/plugins/templates/hyperframes/)（[视频](https://open-design.ai/plugins/templates/video/)） | 25 个 HyperFrames 模板；49 条视频模板 | [nexu-io/open-design](https://github.com/nexu-io/open-design) 里有 `preview.mp4`、完整源码和 `SKILL.md` | Apache-2.0。视频模板里约 40 条是 Seedance prompt。 |
| [motion-anything](https://github.com/nexu-io/motion-anything) | 77 个有实时预览的效果（218 个 `preview.html`）；58 个 HyperFrames 模板 | `SKILL.md` 加可运行源码 | Apache-2.0；以本地应用形式运行。最后推送 2026-07-07。 |
| [HyperFrames Motion Library](https://nutllwhy.github.io/hyperframes-motion-library/)（栗噔噔） | 23 个模板 × 3 套预设 | composition 源码、参数 schema 和示例渲染 | MIT。数据和讲解类叠加层。 |
| [saas-motion-kit](https://tugrawork-creator.github.io/saas-motion-kit/) | 101 张主题分镜表、24 个转场、6 支片 | 分镜表、可任意跳帧的 GSAP 配方、HyperFrames 项目和 skill | MIT。 |
| [Rive Marketplace](https://rive.app/marketplace) | 数万条社区作品 | `.riv` 文件加 MP4 | 按 Rive 文档为 CC BY 4.0，具体看每个文件的标注。 |
| [Jitter templates](https://jitter.video/templates) | 407 个 | 只能在 Jitter 里编辑，没有 prompt 或代码 | 有一个用 Opus 5.5 做的「Jitter AI」分类。 |
| [AutoAE](https://autoae.online/hooks) | 1,052 个模板，其中 78 个是 SaaS 或发布类 | 预览 MP4；定制要付费；没有 prompt 或源码 | 条款禁止自动化访问。 |

### 4e. 带 prompt 的网页与 UI 组件库

动效只是这些库的一部分，产出是网页和组件，不是渲染好的视频。

| 组件库 | 条目数 | 附带 | 许可证 / 备注 |
|---|---|---|---|
| [21st.dev](https://21st.dev/)（[hero 动画](https://21st.dev/community/components/explore/hero-animation)） | 12,000+ 个组件；hero 动画 60 个 | 每个组件附 agent prompt 和源码 | 各作者自定许可证。robots.txt 声明不许用于 AI 训练。 |
| [Aura](https://www.aura.build/)（[动画](https://aura.build/browse/components/animation)） | 2,831 个组件；192 个 skill，约 27 个与动效有关 | 「复制 prompt」按钮、HTML 代码和 skill | 部分模板为 PRO。 |
| [Superdesign](https://superdesign.dev/library) | 1,229 条 prompt，114 条标了 animation | 结构化 prompt 加实时预览 | 社区贡献。 |
| [Shaders](https://shaders.com/sections/particle-swarm-hero) | 60 个区块；190+ 个组件 | 安装 prompt（Pro）；MIT 的 shader 引擎 | 许可证禁止转发区块或预设。 |
| [Webthemez](https://www.webthemez.com/) | 158 个 | 网站复刻 prompt 和源码 ZIP（免费条目） | 最新一条 2026-07-03。 |
| [MotionSites](https://motionsites.ai/) | 未公开 | 动画网站 prompt（付费） | 条款禁止爬取和转发。 |
| [FreeFrontend](https://freefrontend.com/) | 1,284 个页面 | 内嵌 HTML/CSS/JS，多为署名的 CodePen 作品 | 每个 pen 的许可证要单独确认。 |

### 4f. 公开 prompt 的评测基准

| 基准 | 条目数 | 附带 | 备注 |
|---|---|---|---|
| [HeyGen Code2Video Bench](https://www.heygen.com/research/introducing-code2video-benchmark) | 168 份 brief；Kaggle 公开子集至少 32 个任务 | 每份 brief 配一支人工制作的参考视频；页面上可并排播放各模型的结果 | Kaggle 数据集 `heygen/code2video-public` 为 CC BY 4.0。 |
| [XSCT Bench（小山出题）](https://xsct.ai/gallery) | 1,517 个用例，约 47 个是动效 | system prompt、user prompt、评分标准和各模型的 HTML 输出 | 中文。抓取太快会被临时封 IP。 |

---

## 5. Skill 与 skill 目录

### 5a. 目录

| 目录 | 条目数 | 记录了什么 | 备注 |
|---|---|---|---|
| [skills.sh](https://skills.sh/heygen-com/hyperframes/motion-graphics) | 20,000 个 skill；按 URL 关键词约 865 个与动效或视频有关 | 安装命令、完整 `SKILL.md`、安装量和安全审计 | HyperFrames 的 `motion-graphics` 显示 38.24 万次安装。 |
| [awesome-claude-video-skills](https://github.com/zhuyansen/awesome-claude-video-skills)（[AgentSkillsHub](https://agentskillshub.top/best/claude-video-skills/)） | 259 个仓库 | star 数、类型、安全评级、许可证 | CC0。每 8 小时刷新一次。 |
| [awesome-opus-video-skills](https://github.com/ismoshushi/awesome-opus-video-skills) | 110 个 skill，63 个属于代码渲染类 | 渲染栈、安装命令、许可证和 Opus 5.5 标记 | MIT。 |
| [Skillry skills](https://skillry.dev/skills) | 387 个 skill：视频类 144 个，免费 42 个 | 预览 MP4 和可安装的包 | 约 19 个是 HyperFrames 发布片 skill。安装需要登录。 |
| [iart-ai/motion-skills](https://github.com/iart-ai/motion-skills) | 17 个包，共 54 个 skill | `SKILL.md` 内置「渲染 → 截图 → 校验」循环 | 大多 MIT；745★。 |
| [Claude Video skills](https://claudevideo.org/) | 247 个 | 开源视频 skill | 根据 awesome-claude-video-skills 清单整理。 |

HyperFrames 社区 skill 和 GSAP 官方 skill 见第 4 节。

### 5b. 附示例成片的 skill 包

| Skill | 示例成片 / 条目 | 许可证 | 备注 |
|---|---|---|---|
| [video-shotcraft](https://vincentwei1021.github.io/video-shotcraft/) | 157 张镜头配方卡、214 个预览 MP4、9 支社区作品 | Apache-2.0 | 用来做 Remotion 产品宣传片；10,866★。 |
| [video-talkcraft](https://vincentwei1021.github.io/video-talkcraft/) | 108 张配方卡，每张有 TSX 和在线 demo | PolyForm Noncommercial | 面向口播和配音讲解片。 |
| [Lemo-Opuscar](https://lemomo-ai.github.io/lemo-opuscar/) | 43 种风格、44 支片，全部附完整源码 | MIT | 每种风格一个 `STYLE.md` prompt。全部出自同一个工作室。以 Claude Code 插件形式发布；1,410★。 |
| [hyperframes-student-kit](https://github.com/nateherkai/hyperframes-student-kit) | 15 个 skill、406 张动效卡片、12 个以上项目 | MIT | 预览要在本地渲染；1,221★。 |
| [motion-graphics-skills](https://github.com/charlie947/motion-graphics-skills)（charlie947） | 13 个 skill，16 条效果 prompt | MIT | 配套的 Substack 文章展示每个效果，2 个公开。 |
| [Claude Video Skills](https://neelshah1810.github.io/Claude-Video-Skills/) | 11 个 skill，11 支附 HTML 源码的片子 | MIT | 品牌都是虚构的。 |
| [motion-launch-videos](https://github.com/Kimeur/motion-launch-videos) | 11 个 skill，12 支片，附 BRIEF.md 和 DESIGN.md | MIT | v2.1.0。仓库比它的[介绍页](https://gazouzi.com/en/motion-launch-videos)更新。 |
| [product-launch-motion-skill](https://github.com/ouerf-man/product-launch-motion-skill) | 12 种发布片类型，每种附 GIF 和 HyperFrames 源码 | MIT | 从 T01 预告到 T11 动态几何片。 |
| [30X Web-to-Video](https://norahe0304-art.github.io/30x-video/) | 12 支片；4 支附 Remotion 源码（另有 2 支已下架） | MIT | 用 `npx 30x-web-to-video` 安装。 |
| [motion-designer](https://designer.ostinos.com/)（kaventro） | 7 支片，4 支附完整源码 | MIT | 附节拍图和配乐工具。 |
| [cinetic](https://github.com/Leonxlnx/cinetic) + [claude-launchvideo](https://github.com/Leonxlnx/claude-launchvideo) | 4 支片，各附生成它的 brief；273 条技法库；一支发布片的完整源码 | MIT | 默认 Remotion，也可选 HyperFrames。 |
| [onetake](https://github.com/feitangyuan/onetake)（[官网](https://onetakemotion.com)） | 10 支案例片，附节拍表 | 免费版 PolyForm Noncommercial；付费 Pro 版附商用授权和源码 | 1,951★。 |
| [brag](https://latent-spaces.github.io/brag/) | 8 个 MP4 | MIT | 每个演示项目分别用精简模式和 HyperFrames 模式渲染；14,274★。 |
| [阿杜动画模板](https://adunext.github.io/adu-motion-video/examples/gallery/) | 11 种风格 | MIT | 中文。好几种风格需要你自己的口播素材。 |
| [claude-motion-design](https://github.com/howseen-ai/claude-motion-design) | 1 个 skill 加一支完整示例片 | MIT | 有复刻模式，把原片和复刻版左右分屏渲染。 |
| [opus-video-skills](https://github.com/tuzhechen2005/opus-video-skills) | 2 个 skill，3 个完整示例 | MIT | 动态作品集和手绘动画两种风格。 |
| [motion-design](https://github.com/cth9191/motion-design)（cth9191） | 10 种风格，各附原 prompt | 无 | 片子是生成式视频模型（Higgsfield）做的，不是代码。 |
| [CutDirector](https://github.com/Fangx-AI/cut-director) | 15 条 prompt，附 demo | 代码 AGPL-3.0；prompt CC BY-SA 4.0 | 口播叠加效果。另镜像了 ChatCut 的 123 个官方参考。 |
| [AI Motion Director](https://immamdouhaboammar.github.io/motion-graphics-skills/) | 53 个 skill；约 9 个 HyperFrames 项目 | 专有许可 | 许可证只允许在浏览器里查看。 |

---

## 6. 网页动效灵感站（不带 prompt）

这些站适合找参考画面，都不附 prompt，也没有 AI 做的源码。

| 站点 | 条目数 | 备注 |
|---|---|---|
| [What Ships](https://whatships.com) | 2,447 支来自 X 的发布片 | 由工作室和团队制作。元数据有 JSON、OpenAPI 和 `llms-full.txt`；站点源码 MIT。 |
| [landing.love](https://www.landing.love/) | 2,163 段网站录屏 | 视频 sitemap 列出全部录屏。 |
| [Recent](https://recent.design/)（原 Godly） | 约 1,117 条 | MP4 预览，有 Motion 分类。 |
| [60fps.design](https://60fps.design/motion) | 83 支品牌片、67 份分镜 | 条款禁止批量复制。 |
| [Awwwards Elements](https://www.awwwards.com/elements/) | 数百段短片 | robots.txt 禁止访问 `/elements/*`。 |

---

## 7. 怎样合规地使用

**通用原则**

- **prompt 和视频属于原作者。**几乎每个合集都这样声明，第 3 节里的仓库许可证也都不覆盖它们。注明作者，并链接原帖。
- **没有许可证文件的仓库，默认保留全部权利。**JasonZhu.AI 的源仓库、xianyu110、opusvideo、joeseesun、LeaddeOpenLab、Markjinli、remocn-collections、cth9191、Frontier Games 和 jinhanbuilds 都是这种情况。只作参考阅读，不要转发。
- **走站方提供的通道。**有 MCP、API、`llms.txt` 或 GitHub 数据的就用它们，不要抓 robots.txt 禁止的页面。
- **热链的 X 媒体会失效。**很多清单直接引用 `video.twimg.com` 的地址，这些地址可能会失效。
- **prompt-motion.com** 声明了 `Content-Signal: search=yes, ai-train=no, use=reference`，并屏蔽 AI 训练爬虫。所以本仓库只发布分析和链接。

**我们记录到的各站条款**

| 站点 | 条款或 robots.txt 的规定 | 站方提供的通道 |
|---|---|---|
| Oneshotted | 条款第 6 条禁止批量复制合集或 prompt、爬取、绕过频率限制和转发 prompt | MCP（免费 key，每分钟 20 次、每天 200 次）或 agent skill |
| 24fps | 屏蔽训练爬虫。4,212 条为「© 原作者，仅链接」；395 条开源许可的，注明出处即可使用 | MCP、JSON API、`llms-full.txt` |
| Skillry | 条款第 8 条禁止未经书面许可爬取或批量复制付费内容 | GitHub 上的 MIT 数据 |
| Claude Video | 明确欢迎 AI 爬虫；视频和 prompt 属于原作者，接受下架请求 | `llms.txt`、sitemap |
| YouMind、TopView | 禁止访问 `/api/`；YouMind 接受作者的下架请求 | sitemap 和详情页 |
| Swishy | 条款禁止未经书面许可爬取或使用机器人，也禁止用其模板做竞品 | 手动浏览 |
| Pexo | 条款禁止未经明确授权的自动化访问 | 手动浏览 |
| iArt.ai | 应用的 robots.txt 禁止访问所有页面；条款禁止爬取 | 逐个打开分享链接 |
| AutoAE | 条款禁止自动化访问；许可证禁止爬取或复制模板库 | 手动浏览 |
| 60fps.design | 条款禁止批量下载、据此建参考库以及用于机器学习 | 付费 MCP |
| MotionSites | 条款禁止爬取、绕过付费墙和转发 prompt | 付费套餐和 MCP |
| Made With GSAP | 许可证禁止转发代码或放进公开仓库 | 会员 |
| Codrops | robots.txt 声明不许用于 AI 训练，并屏蔽 AI 爬虫 | MIT 的 GitHub 仓库 |
| HyperFrames Studio | robots.txt 禁止访问 `/api/` | 浏览社区页面 |
| Awwwards | robots.txt 禁止访问 `/elements/*` | 手动浏览 |
| XSCT Bench | 抓取太快会被临时封 IP | 慢速手动阅读 |
| React Bits | MIT + Commons Clause：可以使用组件，但不能出售或转发组件本身 | shadcn registry |
| video-talkcraft、onetake（免费版） | PolyForm Noncommercial | 商用需征得作者同意；onetake 单独出售商用授权 |
| Motion Prompt Bank | CC BY-NC-SA 4.0 | 注明出处，不得商业转发 |
| maning636/motion-prompts | 自定义许可证禁止重新打包或转传 prompt | 可使用产出，不能转发 prompt 原文 |
| AI Motion Director | 专有许可，只能在浏览器里查看 | — |

---

## 8. 方法

**候选怎么找的。**我们用 AI 辅助从多个角度做网页搜索：英文、中文和日文关键词；模型名、框架名和片型；再在 GitHub 上搜「awesome」清单和 skill 仓库。之后顺着已找到合集里的引用继续追：「相关清单」板块、`THIRD_PARTY.md` 文件、Remotion 资源索引、`llms.txt` 文件和赞助位链接。一共收集到 183 个候选。核查过程中又发现几条额外线索，按同样标准核查。

**怎么核实的。**2026-10-08/09，每个候选都打开逐一核查。核查人的任务是尽量推翻对它的描述：

- 网站还在吗？
- 条目数对得上吗？
- 每条是不是真的附 prompt、源码或 skill？
- 许可证、robots.txt 和条款怎么写？

数字或说法不对的，记录核查时看到的实际情况。最终保留 132 行，剔除 55 个。剔除的包括：只带一个 demo 的单个 skill、教程文章、内容在付费墙后的页面、泛网页设计灵感站，以及其他合集的副本。最终名单里没有日文合集；YouMind 提供日语界面。

**「相似度」怎么定的（1–5 分）。**

- **5 分：**和 prompt-motion.com 同一个概念。多位作者的 AI 动效作品，每条配 prompt。
- **4 分：**精选动效合集，每条附 prompt 或源码，但缺一项（只有一位作者、给源码而不是 prompt，或是厂商自己的作品）。
- **3 分：**不附 prompt 或源码的优质动效合集、网页/UI 动效的 prompt 库，或 skill 目录。
- **2 分：**单个 skill、工具或文章。
- **1 分：**无关。

网站在线且 3 分及以上的保留。有几个 3 分的被剔除，因为它们每条所谓的「prompt」其实是通用模板。

**怎么合并的。**以下情况算同一个项目：同一网站的不同语言版本、网站和它的 GitHub 源仓库、同一网站的多个页面（比如 Opus 5.5 和 Fable 5.5 两个合集页，或合集和它的 skill 商店），以及同一框架的各个官方页面。同一主体但用途不同的产品分开计算。prompt-motion.com 的副本不计入。合并后共 100 个独立项目。

**我们在 2026-10-09 的复核。**重新抓取了最大几个合集的首页数字和数据文件：

| 站点 | 10-08/09 核查记录 | 10-09 复核 | 变化 |
|---|---|---|---|
| Oneshotted | 6,144 条 / 3,837 条 prompt / 3,710 位作者 | 6,164 / 3,838 / 3,716 | 约一天内新增 20 条 |
| 24fps | 4,607 条 / 1,073 条带 prompt / 2,540 位作者 | 相同 | 计数仍标注为 2026-10-03 |
| JasonZhu.AI | 1,402 条 / 361 条带 prompt / 148 条完整 | 相同 | — |
| Claude Video | 1,276 条 / 457 条带 prompt / 1,007 位作者 | 相同 | — |
| Skillry | 513 条；仓库 3,084–3,087★ | 513；仓库 3,101★ | 只有 star 数变化 |
| WorkSkill | 478 条 | 相同 | — |
| Tellcut | 470 / 完整 276（`examples.json`） | 相同 | — |
| Awesome AI Motion | 581 条 / 原文 83（`cases.json`） | 相同 | — |
| Li-Evan | 334 条，更新于 2026-09-27（`data.json`） | 相同 | — |
| YouMind | 340 条 | 相同 | — |
| HyperFrames catalog | 400 个（170 / 222 / 8） | 相同 | — |
| What Ships | `search-index.json` 2,552 行（视频 2,447、工具 94、工作室 11） | 相同 | — |

**局限。**

- 所有数字都是各站在核查当天公布的。活跃的合集每天都在增长，也有一些已经停更，看各自的「最后更新」日期就知道。
- 各站说的「prompt」含义差别很大：可能是作者逐字原文、节选、整理者的反推版本，也可能只是一句描述。请看各站自己的标注。
- 模型归属是作者自己的说法。除了上文提到的复刻功能，没有哪个合集重新跑过 prompt 来核对。
- 如果我们漏掉了某个合集，或数字有误，欢迎带上链接提 issue。
