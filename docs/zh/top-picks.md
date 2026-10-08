# 必看清单：先看哪些

这是一份 [prompt-motion.com](https://www.prompt-motion.com/)（由 [@p4nthera_](https://x.com/p4nthera_) 整理）所收 233 支动效视频的观看指南，数据快照日期 2026-10-09。每支视频都是 Claude Opus 5.5 写代码做出来的。每条推荐都链接到作者自己的条目页，在那里可以看视频、读完整 prompt。文中 `#N` 就是 [`catalog/catalog.json`](../../catalog/catalog.json) 里的 `id`。

[English version](../top-picks.md)

## 要点速览

- **233 个条目，228 支不同的视频，216 个发布账号。** 有 5 个条目是转发别人更早发的视频，名单见[下文](#转发)。
- **产品发布片最多：** 233 条里有 70 条（30%），其次是动效作品集（44 条，19%）和讲解片（24 条，10%）。
- **默认就短：** 时长中位数 20.1 秒，84 条落在 14.5–15.6 秒之间。被复制最多的 brief 是「15 秒动效设计师作品集」，87 条 prompt 里有 "go all out" 这句。
- **233 条里 192 条是 16:9，200 条（86%）听得到声音。**
- **233 条里只有 56 条写明了技术栈。** 写明的里面 Remotion（13 条）和 HyperFrames（10 条）最多。评分员看下来，全部条目里约一半（116 条）是普通网页 2D：HTML/CSS/JS、Canvas 或 SVG。
- **没时间？这 6 条加起来不到 6 分钟：** [#5](https://www.prompt-motion.com/twoclipping-221cab)、[#8](https://www.prompt-motion.com/lexnlin-038035)、[#126](https://www.prompt-motion.com/ik-builds-b8bdcf)、[#36](https://www.prompt-motion.com/ismailfahmi-557268)、[#64](https://www.prompt-motion.com/sayan-shanky-f850d8)、[#29](https://www.prompt-motion.com/kloss-xyz-fe0c31)。
- **怎么选出来的：** 先由 AI 评分员过一遍，我们再逐条看约 90 条的 6 帧联系表重新排序。我们不公开单条分数（原因见[方法与局限](#6-方法与局限)）。

## 目录

1. [从这里开始：10 分钟看 6 条](#1-从这里开始10-分钟看-6-条)
2. [数据一览](#2-数据一览)
3. [全库 Top 20](#3-全库-top-20)
4. [按用途挑片](#4-按用途挑片)
5. [每个类别最好的 1–2 条](#5-每个类别最好的-12-条)
6. [方法与局限](#6-方法与局限)

---

## 1. 从这里开始：10 分钟看 6 条

6 条总时长 5 分 44 秒，剩下的时间可以把最喜欢的两条再看一遍。

1. [#5](https://www.prompt-motion.com/twoclipping-221cab) · **Photo print app launch film** · @twoclipping · 29s · 方形 — 工艺标杆。一镜到底，每个场景都从上一个场景里长出来；prompt 是完整的结构化 spec，值得逐行读。
2. [#8](https://www.prompt-motion.com/lexnlin-038035) · **Engraving-style Claude ad** · @LexnLin · 15s · 竖版 — 怎样用一个元素撑起整支片：一颗珊瑚色圆点先后变成问号、笔尖、向日葵花心，最后变成 logo。
3. [#126](https://www.prompt-motion.com/ik-builds-b8bdcf) · **Paper-style product launch film** · @ik_builds · 15s — 一支产品片，prompt 写成了可复用的模板（产品、受众、禁用词都是占位符），用 HyperFrames + GSAP 做。
4. [#36](https://www.prompt-motion.com/ismailfahmi-557268) · **Drone Emprit showreel** · @ismailfahmi · 15s — 全库最好看的数据片：同一套粒子把海量发言变成簇，最后落成一个尖峰。
5. [#64](https://www.prompt-motion.com/sayan-shanky-f850d8) · **AI data centre 3D tour** · @Sayan_shanky · 1:38 — 一句话 prompt 能换来什么：一部 11 章的数据中心 3D 导览。
6. [#29](https://www.prompt-motion.com/kloss-xyz-fe0c31) · **History of AI timeline** · @kloss_xyz · 2:52 — 撑得住的长片：将近 3 分钟，每一章都有专门做的可视化。

---

## 2. 数据一览

以下数字都由 [`catalog/catalog.json`](../../catalog/catalog.json) 和下载下来的视频文件算出（时长、分辨率、帧率、音轨用 `ffprobe` 读取）。

### 基本数据

| 项 | 数 |
|---|---|
| 条目 | 233（Prompt 230 条，Skill 3 条：[#16](https://www.prompt-motion.com/lexnlin-6161a6)、[#23](https://www.prompt-motion.com/anthonyriera-9b1b2a)、[#70](https://www.prompt-motion.com/jake11moran-a269c4)） |
| 不同的视频 | 228（有 5 条是转发更早的视频） |
| 发布账号 | 216 |
| 发布时间 | 2026-09-23 至 2026-10-08（9 月 220 条，10 月 13 条） |
| 总时长 | 155.5 分钟 |
| 附了 skill 仓库的条目 | 4（[#16](https://www.prompt-motion.com/lexnlin-6161a6)、[#23](https://www.prompt-motion.com/anthonyriera-9b1b2a)、[#70](https://www.prompt-motion.com/jake11moran-a269c4)、[#147](https://www.prompt-motion.com/buildfastwithai-53234e)） |

### 按类别

类别由 AI 评分员标注，每条一个。

| 类别 | 条数 | 占比 | 时长中位数 | 有音轨 |
|---|---|---|---|---|
| 产品发布片 `product-launch-film` | 70 | 30% | 19.3 秒 | 64 |
| 动效作品集 `showreel-montage` | 44 | 19% | 15.1 秒 | 43 |
| 讲解 / 数据可视化 `explainer-data-viz` | 24 | 10% | 58.6 秒 | 17 |
| SaaS 界面走查 `saas-ui-walkthrough` | 17 | 7% | 30.0 秒 | 14 |
| 动态字体 `kinetic-typography` | 16 | 7% | 15.1 秒 | 14 |
| 角色 / 故事动画 `character-story-animation` | 16 | 7% | 43.9 秒 | 14 |
| 社媒竖版广告 `social-ad-vertical` | 10 | 4% | 29.1 秒 | 8 |
| 3D 场景 `3d-world-scene` | 8 | 3% | 38.6 秒 | 7 |
| 个人介绍片 `personal-intro-reel` | 8 | 3% | 29.6 秒 | 7 |
| 其他 `other` | 8 | 3% | 22.5 秒 | 2 |
| 生成式抽象 `generative-abstract` | 6 | 3% | 30.5 秒 | 6 |
| Logo / 品牌演绎 `logo-brand-ident` | 4 | 2% | 16.6 秒 | 4 |
| 工具 / Skill 演示 `meta-tool-demo` | 2 | 1% | 50.6 秒 | 2 |

表里算作「有音轨」的，有两条其实是静音（峰值 −91 dB）：[#55](https://www.prompt-motion.com/0xnfrith-5be616) 和 [#123](https://www.prompt-motion.com/buildfastwithai-ed9447)。

### 技术栈：自报 vs 推断

**作者自己写明的**（`stack_stated`）：233 条里只有 56 条（24%），其余 177 条空着。

| 自报的技术栈 | 条数 |
|---|---|
| Remotion（含 1 条 "Remotion, React"） | 13 |
| HyperFrames（含 1 条 "HyperFrames + GSAP"） | 10 |
| HTML | 9 |
| HTML + Playwright 逐帧截图（4 种写法） | 6 |
| Three.js | 5 |
| JavaScript | 5 |
| Python（含 1 条 "Python + ffmpeg"） | 2 |
| 各 1 条：OpenEdit、Manim + edge-tts、SVG/Canvas、WebGL2 + Canvas 2D + Web Audio、Blender、Canvas | 6 |

**评分员推断的**（`stack_inferred`，覆盖全部 233 条）。评分员是看画面和 prompt 猜的，没有逐条核实。我们按关键词把他们的备注归类，命中第一个就停，顺序是：Remotion → HyperFrames → 其他工具 → 逐帧截图管线 → 3D → 网页 2D。

| 推断的技术栈（大类） | 条数 |
|---|---|
| 网页 2D：HTML / CSS / JS、Canvas、SVG、GSAP | 116 |
| Three.js / WebGL / shader（含「Canvas 或 WebGL」这类猜测） | 42 |
| 看不出 | 26 |
| 其他工具：Manim、Python、Blender、OpenEdit、skill 管线、AI 生成的图像 | 15 |
| Remotion | 13 |
| HTML + 确定性逐帧截图（Playwright 和 / 或 `seek(t)`） | 11 |
| HyperFrames | 10 |

### 时长

| 区间 | 条数 |
|---|---|
| ≤ 12 秒 | 10 |
| 12–20 秒 | 103 |
| 20–35 秒 | 54 |
| 35–60 秒 | 38 |
| 1–2 分钟 | 17 |
| > 2 分钟 | 11 |

- 中位数 20.1 秒，平均 40.1 秒。最短 10.0 秒（8 条），最长 7 分 37 秒（[#27 Derivative concept explainer — @LinearUncle](https://www.prompt-motion.com/linearuncle-5d2bae)）。
- 84 条（36%）在 14.5–15.6 秒之间，「15 秒作品集」是最常见的单一题型。
- ≤ 30.0 秒的有 143 条；把跑到 30.5 秒的「30 秒片」也算上是 159 条。

### 画幅与帧率

| 画幅 | 条数 | 说明 |
|---|---|---|
| 16:9 | 192 | 1920×1080 共 149 条，1280×720 共 37 条，另有 6 条是接近 16:9 的尺寸（如 1920×1078、854×480） |
| 9:16 | 16 | 1080×1920 共 11 条，720×1280 共 5 条 |
| 1:1 | 14 | 1080² 共 9 条，1440² 共 4 条，720² 共 1 条 |
| 4:5 | 2 | [#135](https://www.prompt-motion.com/marklaunches-3b9492)、[#219](https://www.prompt-motion.com/anas0ra-e57aea) |
| 比 9:16 更窄 | 1 | [#171](https://www.prompt-motion.com/francoxavier33-d2dfd2)（886×1920） |
| 其他 | 8 | 3 条录屏尺寸（1920×982 / 972），宽银幕 1920×816（[#233](https://www.prompt-motion.com/kamstudiolabs-0b0824)），以及 1920×1292、1408×1080、1280×848、1152×720 |

帧率：60fps 有 131 条（其中 2 条是 59.94），30fps 有 93 条，24fps 有 5 条（其中 1 条是 23.98），另外 12、15、25、53.7fps 各 1 条。

### 声音

- 233 条里 202 条有音轨，31 条没有。
- 有音轨的里面有 2 条是静音（峰值 −91 dB，用 ffmpeg `volumedetect` 实测）。
- **听得到声音的是 200 条（86%）。** 只统计了有没有，没有评声音好坏。

### Prompt 写法

| 写法（评分员标注） | 条数 |
|---|---|
| 一句话 prompt | 154（66%） |
| 短 brief | 56（24%） |
| 结构化 spec（分段、禁用清单、节拍表、QA） | 17（7%） |
| 走 skill | 6（3%） |

87 条 prompt 里有 "go all out" 这句（比如 [#1](https://www.prompt-motion.com/stephanlivera-df17a2)），84 条把视频定位成作品集或简历。各种写法到底换来了什么，见 [prompt-patterns.md](prompt-patterns.md)。

### 转发

有些视频被不止一个账号发过。画廊把每次发布都列成一个条目；我们引用最早的那条。

| 原条目 | 也发成了 | 依据 |
|---|---|---|
| [#1](https://www.prompt-motion.com/stephanlivera-df17a2) | [#62](https://www.prompt-motion.com/roundtablespace-d3a1be) | 视频文件字节完全相同 |
| [#4](https://www.prompt-motion.com/ajith-io-b5626e) | [#129](https://www.prompt-motion.com/mrtanviir-132457)、[#227](https://www.prompt-motion.com/umangratani-57f86a) | 同一支片，联系表一致 |
| [#6](https://www.prompt-motion.com/himanshutwtxs-5f4b43) | [#51](https://www.prompt-motion.com/chatgptastra-0d95c7) | 同一支片 |
| [#64](https://www.prompt-motion.com/sayan-shanky-f850d8) | [#117](https://www.prompt-motion.com/mdaman010-e7226a) | 画面一致，编码不同 |

---

## 3. 全库 Top 20

排序是我们看联系表后定的，不是按评分员的分数排。每一条都值得完整看一遍。

1. [#5](https://www.prompt-motion.com/twoclipping-221cab) · **Photo print app launch film** · @twoclipping · 29s · 方形 — 一镜到底：字标缩进自己的句点，光圈打开一张照片，液态玻璃滑块把它从白天调成黄昏，状态胶囊跟着订单一路变形，最后黑色淹没全屏、收进实拍墙面上挂着的装框照片。prompt 是结构化 spec 的范本。
2. [#13](https://www.prompt-motion.com/twoclipping-6dd14e) · **UGC ad generator promo** · @twoclipping · 20s — 米白色的开场句沉进黑色舞台：18 条真实竖屏广告组成扫描墙，接带地面倒影的 3D 圆柱轮播，再砸出一个带运动模糊重影的数字。prompt 写清了节拍网格、响度目标和逐拍抽帧检查。
3. [#8](https://www.prompt-motion.com/lexnlin-038035) · **Engraving-style Claude ad** · @LexnLin · 15s · 竖版 — 白底上的铜版画抠图，一颗珊瑚色圆点贯穿所有镜头（问号、笔尖、向日葵花心、logo）。编辑设计级的 match cut 示范。
4. [#29](https://www.prompt-motion.com/kloss-xyz-fe0c31) · **History of AI timeline** · @kloss_xyz · 2:52 — 将近 3 分钟，每一章都有专门做的可视化（神经元 Σ、感知机、反向传播、围棋棋盘），章节 HUD 全程统一，节奏一直不散。
5. [#36](https://www.prompt-motion.com/ismailfahmi-557268) · **Drone Emprit showreel** · @ismailfahmi · 15s — 海量发言变成流场粒子丝带，按平台换色，再聚成簇，最后落成情绪曲线上的一个尖峰，角落的计数器一直在涨。
6. [#64](https://www.prompt-motion.com/sayan-shanky-f850d8) · **AI data centre 3D tour** · @Sayan_shanky · 1:38 — 46 个字符的 prompt，换来一部 11 章的白模 3D 导览（电力进站、机柜、芯片爆炸视图、集群、散热），流线按颜色编码，图例常驻。也被发成了 [#117](https://www.prompt-motion.com/mdaman010-e7226a)。
7. [#202](https://www.prompt-motion.com/blueoctopusai-dd17bd) · **First & 10 yellow line explainer** · @blueoctopusai · 2:48 — 搭了一整座低多边形球场，叠上信号链流程图，讲清楚橄榄球转播里那条黄色首攻线是怎么合成的。3D 讲解片的标杆。
8. [#147](https://www.prompt-motion.com/buildfastwithai-53234e) · **Indian civilisation history film** · @BuildFastWithAI · 1:27 — 靛蓝、姜黄、朱红的图版，用一根红线串起五千年，最后收成一条时间轴。做这支片的 skill 连配乐也是用代码合成的。
9. [#83](https://www.prompt-motion.com/hbcoop-de365c) · **Full Stop figure sequence** · @HBCoop_ · 29s — 米色书页上，一个黑点依次变成线、透镜、球、鸟群、地球，下方用打字机打出图注。极简，也极讲究。
10. [#225](https://www.prompt-motion.com/samaote-5e2fc2) · **Synced lyrics motion video** · @samaote · 30s — 歌词按小节对齐，整首歌被演成一个太阳从日出到日食的过程，角落挂着倒计时和小节计数。
11. [#44](https://www.prompt-motion.com/gizakdag-cf4ae6) · **Overthinking motion study** · @gizakdag · 15s · 竖版 — 一个点炸成一圈圈环绕的焦虑问句，配复古拼贴、半调网点和 RGB 色差，最后收在 "breathe."。海报级的画面密度。
12. [#42](https://www.prompt-motion.com/nft-chen-5f8bb0) · **Porco Rosso sunset dogfight** · @NFT_Chen · 14s — 用 Three.js 卡通渲染做的紫色积云和日落海面空战。它不是产品片，但证明了浏览器里的 3D 能做到什么程度。
13. [#158](https://www.prompt-motion.com/rebutonepress-810f78) · **Black hole time story** · @RebutonePress · 5:00 — 带引力透镜的黑洞，左右两栏遥测 HUD 显示母船和探测器的时间越走越开，配中文字幕。prompt 里没写渲染方法。
14. [#155](https://www.prompt-motion.com/faroukzy-9ff23e) · **The Last Light animated short** · @faroukzy · 4:00 — 绘本感的动画短片：灯塔、暴风雨，一个小机器人把胸口的光交给熄灭的灯，字幕标了说话人。prompt 只有一句话，没写技术栈；值得重点看它的叙事和镜头节奏。
15. [#216](https://www.prompt-motion.com/spearwtf-3c1fd1) · **Chain.wtf pitch video** · @SPEARwtf · 30s — 开场是一个客客气气的 "Gamble responsibly" 按钮，光标一点，砸切成 3D 的 DOUBLE IT 街机按钮。反转式开场的教科书，后面是带胶片颗粒和色散的 3D 道具。
16. [#214](https://www.prompt-motion.com/nolkeeg-bf062e) · **What happens in one second** · @nolkeeg · 45s — 粒子聚成 ONE SECOND，接发光的地球和太阳。每一屏是一个大数字加一句斜体衬线说明，底部的进度条本身就代表那一秒。
17. [#81](https://www.prompt-motion.com/samuel-spitz-974923) · **Motion design showreel** · @samuel_spitz · 15s — 一条红线贯穿全片（下划线、铬球轨道、落版签名），中间是 Bauhaus 模块网格、玻璃纵深层和液态铬字。在这道常见的作品集题目里完成度最高。
18. [#89](https://www.prompt-motion.com/zheke-38deff) · **Kinetic type showreel** · @zheke · 15s · 方形 — 「I CAN + 动词」，每个动词用对应的动画原理演出来（SNAP 碎裂，RENDER 变成一团光泽 3D 软球），然后划掉 AFTER EFFECTS，砸出 JUST CODE。
19. [#126](https://www.prompt-motion.com/ik-builds-b8bdcf) · **Paper-style product launch film** · @ik_builds · 15s — 一颗青色小球从散落的笔记出发，变成节点图的中心，再变成增长曲线的头，最后落成 logo；中间有手写批注、明暗硬切，以及碎落成图表的 3D 大字。
20. [#228](https://www.prompt-motion.com/anilraok-eff262) · **Scrabble tile character story** · @Anilraok · 42s · 竖版 — 一块被落在格子外的木质字母牌，最后补上了缺口。暖色主光、浅景深，用 Three.js 做出接近动画长片的角色质感。

**也值得看**

- [#3](https://www.prompt-motion.com/shneural-2abdfa) · **Bold kinetic type showreel** · @shneural · 32s — 六个编号章节，每章一句两行的大字主张，配一个旋转的铬或玻璃 3D 物体。
- [#15](https://www.prompt-motion.com/emollick-8661a8) · **Recursion explained in genres** · @emollick · 1:15 — 讲递归：每深入一层就换一种电影类型，最后一层层退回来，把开头那句话说完。
- [#17](https://www.prompt-motion.com/steventey-0d20e4) · **Dub promo video** · @steventey · 15s — 一长串 UTM 链接压缩成短链胶囊，接深色点阵地球和 3D 倾斜的实时仪表盘。
- [#71](https://www.prompt-motion.com/arjunsh1607-93005d) · **Pixelup Labs studio showreel** · @arjunsh1607 · 15s — 工作室作品集，结尾的「证明页」做得好：标题、高亮关键词、数字滚动。
- [#112](https://www.prompt-motion.com/jesscaroline7-1ff7cb) · **Ondefica app motion reel** · @jesscaroline7 · 1:00 · 竖版 — 用 HyperFrames 做的竖版：一个点代表一个地点的点阵地图加计数器，讲一个 App。
- [#136](https://www.prompt-motion.com/web3wesley-7bb108) · **Type, form, space showreel** · @Web3Wesley · 15s — 一张简历卡开场又收场，卡上的技能清单同时就是章节目录。
- [#143](https://www.prompt-motion.com/adamdesgns-478d6d) · **Fitters Bible app promo** · @Adamdesgns · 15s — 沿管道路径的焊接火花、工程 HUD 标注、一个点代表一条记录的计数器。
- [#176](https://www.prompt-motion.com/madebyjmayala-b9204d) · **Gene Spectra promo** · @madebyjmayala · 15s — 问题句压在原始基因数据上，接一条扫描线把数据扇出成带标签的光谱。
- [#185](https://www.prompt-motion.com/robvjourney-ce3e1a) · **Nohandslabs brand promo** · @robvjourney · 15s — 从终端开机一路长成点阵风的品牌世界。
- [#193](https://www.prompt-motion.com/marouanegazouzi-6071d5) · **Crux motion design showreel** · @marouanegazouzi · 15s — 给一个真实产品做的分章 HUD 作品集：动态字体、钟形曲线图、产品界面、雷达、翻牌字蒙太奇。
- [#196](https://www.prompt-motion.com/sahildesigner23-ee3155) · **3D motion design showreel** · @sahildesigner23 · 15s — 动态字体、铬金属软球，以及一部 3D 倾斜手机里的渲染进度一路跑到 100%。
- [#233](https://www.prompt-motion.com/kamstudiolabs-0b0824) · **Lighthouse keeper silent short** · @KamStudioLabs · 46s · 宽银幕 — 剪影风的无对白灯塔守护人短片，靠光、雾和雨讲故事。

---

## 4. 按用途挑片

手上有具体的片子要做时，先看哪几条、借什么。

### SaaS 发布片

- [#134](https://www.prompt-motion.com/aschapmann-131210) · **SaaS launch video** · @aschapmann · 30s — 四个短场景讲一个故事：Reddit 为什么重要、为什么难做、产品怎么解决、从第 1 天到第 3 个月以后你能得到什么。**借：** 这套四幕结构，以及让模型动手前先 "first read my landing page and codebase to pull the real story"（[prompt](https://www.prompt-motion.com/aschapmann-131210)）的写法。用 Remotion 做。
- [#126](https://www.prompt-motion.com/ik-builds-b8bdcf) · **Paper-style product launch film** · @ik_builds · 15s — **借：** 把 brief 写成填空模板，用 `{{PRODUCT}}`、`{{AUDIENCE}}`、`{{BANNED_WORDS}}` 这类占位符，再加一条硬规则："No invented results: no %, multipliers, customer names or figures."（[prompt](https://www.prompt-motion.com/ik-builds-b8bdcf)）
- [#209](https://www.prompt-motion.com/ceowinkz-7c776b) · **Amazon wholesale pitch video** · @ceowinkz · 15s — 痛点段用红色（"TOO MANY SELLERS."），方案段用蓝色。**借：** 一道竖向光条扫过，把商品页变成 AFTER 状态；一个品牌节点用曲线扇出到三张渠道卡。
- [#188](https://www.prompt-motion.com/amol909s-27533e) · **Commotion app showreel** · @Amol909S · 20s — **借：** logo 的 2×2 方块展开成一格格同时在干活的工作窗格，再用一张路由图表现请求被派给合适的模型。表现「多个 agent 并行」的干净做法。
- 另见 [Top 20](#3-全库-top-20) 里的 [#5](https://www.prompt-motion.com/twoclipping-221cab) 和 [#13](https://www.prompt-motion.com/twoclipping-6dd14e)。

### 产品界面演示

- [#2](https://www.prompt-motion.com/twoclipping-5cba86) · **Shape morphing through UI states** · @twoclipping · 14s · 方形 — 一个黑色形状，不切镜头，连续变成十来种 UI 状态（按钮、加载、对勾、灵动岛、播放器、滑块、开关、标签页、图表、⌘K、toast），最后无缝循环。**借：** 「一个元素、永不切镜」作为 UI 片的总规则；以及 prompt 里让标签指示条前后两条边走不同弹簧、前沿先被拉长的小技巧。
- [#178](https://www.prompt-motion.com/antonio-kodheli-490109) · **Prompt Motion site promo** · @antonio_kodheli · 23s — 给这个画廊自己做的宣传片，只用网站上真实存在的东西：镜头在全屏视频和它在网格里的小卡片之间来回，打开一个条目和它的 prompt，最后落在网址按钮上。**借：** prompt 里「只展示产品真有的东西」这条规则（明令禁止编造功能和数字），以及把时间表和文案拆成两个文件的做法。
- [#34](https://www.prompt-motion.com/notdwd-7de38a) · **Frame by Frame launch video** · @notdwd · 12s · 方形 — 菜单栏图标弹出一个磨砂玻璃输入框，逐字打出一句请求，镜头甩上去进入结果页。**借：** prompt 的精度：坐标精确到帧号，每个切点都由节拍公式算出。[#10](https://www.prompt-motion.com/notdwd-c2037d) 是同一作者用几乎同一份 prompt 做的复刻对照。
- [#104](https://www.prompt-motion.com/daniel-haida-8691d4) · **Taxtello bookkeeping app film** · @daniel_haida · 14s — 深蓝底上 3D 倾斜的真实记账仪表盘，金色是唯一点缀色，健康分圆环一路数上去，再引出字标。**借：** 用同一个点缀元素把镜头带进下一个场景；prompt 里编了号的禁用效果清单，以及 CHAOS → CONTROL → CLARITY 的情绪弧。
- [#17](https://www.prompt-motion.com/steventey-0d20e4) · **Dub promo video** · @steventey · 15s — **借：** 把产品的核心动作演成一次变形（长链接压缩成短链接），再接 3D 倾斜的仪表盘和实时事件通知。

### 讲解 / 数据故事

- [#198](https://www.prompt-motion.com/palashbagchi11-0a4b6b) · **Backlink audit data promo** · @PalashBagchi11 · 30s — 先从观众的处境开场（"You paid for 173 backlinks."），然后一屏一个发现：一个大数字配一张点阵图，一个点代表一条 URL，最后是一句被划掉的判词和一个 CTA。**借：** 「一屏一个发现」的审计片结构。（画廊里这条的 prompt 只涉及配乐和出横竖两版。）
- [#36](https://www.prompt-motion.com/ismailfahmi-557268) · **Drone Emprit showreel** · @ismailfahmi · 15s — **借：** 同一套粒子贯穿所有场景，让观众看着数据从「量」变成「类」，再变成「一个事件」。
- [#214](https://www.prompt-motion.com/nolkeeg-bf062e) · **What happens in one second** · @nolkeeg · 45s — **借：** 固定的数字版式（大数字、斜体衬线说明、小号等宽字），以及一条本身就是主题的进度条。
- [#176](https://www.prompt-motion.com/madebyjmayala-b9204d) · **Gene Spectra promo** · @madebyjmayala · 15s — **借：** 「扫描线 → 光谱」这个动作，适合任何「把原始的 X 变成看得懂的 Y」的故事。
- [#55](https://www.prompt-motion.com/0xnfrith-5be616) · **Celld job ownership explainer** · @0xnfrith · 53s — **借：** 带标签的章节胶囊（THE SETUP、THE FAILURE、THE IDEA、STEP 1–3、THE TRADE-OFF），让一段工程论证很容易跟上。
- 长片请看 [Top 20](#3-全库-top-20) 里的 [#29](https://www.prompt-motion.com/kloss-xyz-fe0c31) 和 [#202](https://www.prompt-motion.com/blueoctopusai-dd17bd)。

### 品牌 / Logo 演绎

- [#20](https://www.prompt-motion.com/tdinh-me-815acb) · **TypingMind logo reveal** · @tdinh_me · 21s — 线框节点组成的大脑一面一面填上颜色，变成 App 图标，再打出字标。**借：** 让标志从它自己的结构线里长出来。
- [#185](https://www.prompt-motion.com/robvjourney-ce3e1a) · **Nohandslabs brand promo** · @robvjourney · 15s — 终端开机（`[ ok ] agent.intake … online`）、点阵手、一个大数字、警戒胶带标语，最后是 logo。**借：** 用开机序列给技术品牌做演绎。
- [#122](https://www.prompt-motion.com/madhav-xo-f97f20) · **Personal research intro reel** · @Madhav_XO · 10s — 10 秒：一行终端编译命令、粒子神经网络、两张成绩卡，最后是名字落版。**借：** 一套 10 秒就讲完的个人演绎结构。
- 一个点变成标志的做法，见 [Top 20](#3-全库-top-20) 里的 [#8](https://www.prompt-motion.com/lexnlin-038035) 和 [#83](https://www.prompt-motion.com/hbcoop-de365c)。

### 动态字体

- [#89](https://www.prompt-motion.com/zheke-38deff) · **Kinetic type showreel** · @zheke · 15s · 方形 — **借：** 让每个词把自己的意思演出来。
- [#225](https://www.prompt-motion.com/samaote-5e2fc2) · **Synced lyrics motion video** · @samaote · 30s — **借：** 字对齐小节，整首歌用一条视觉弧线贯穿。
- [#100](https://www.prompt-motion.com/gdgtify-287ddf) · **Speech built as architecture** · @Gdgtify · 20s · 方形 — 词变成了结构件：WAIT、WAITING、VOICE 挂在一根金色横梁上，像一栋楼按提示点一段段搭起来。**借：** 把字当建筑来搭；prompt 是结构化 spec。
- [#44](https://www.prompt-motion.com/gizakdag-cf4ae6) · **Overthinking motion study** · @gizakdag · 15s · 竖版 — **借：** 先让密度一路往上堆，再收成一个安静的词。
- [#3](https://www.prompt-motion.com/shneural-2abdfa) · **Bold kinetic type showreel** · @shneural · 32s — **借：** 「一句大字主张 + 一个 3D 物体」的章节模板。

---

## 5. 每个类别最好的 1–2 条

### 产品发布片（70 条）
- [#5](https://www.prompt-motion.com/twoclipping-221cab) · **Photo print app launch film** · @twoclipping · 29s · 方形 — 一镜到底、光标驱动，全库工艺最好。
- [#126](https://www.prompt-motion.com/ik-builds-b8bdcf) · **Paper-style product launch film** · @ik_builds · 15s — 叙事和 prompt 都能直接复用。

### 动效作品集（44 条）
- [#81](https://www.prompt-motion.com/samuel-spitz-974923) · **Motion design showreel** · @samuel_spitz · 15s — 一条红线贯穿全片，章节外框始终统一。
- [#136](https://www.prompt-motion.com/web3wesley-7bb108) · **Type, form, space showreel** · @Web3Wesley · 15s — 结构最清楚：简历卡列出 Type / Form / Space / Time，逐章演示，最后回到简历卡。

### 讲解 / 数据可视化（24 条）
- [#29](https://www.prompt-motion.com/kloss-xyz-fe0c31) · **History of AI timeline** · @kloss_xyz · 2:52 — 每章一种专门的可视化，章节 HUD 统一。
- [#202](https://www.prompt-motion.com/blueoctopusai-dd17bd) · **First & 10 yellow line explainer** · @blueoctopusai · 2:48 — 一个 3D 世界加一张信号链流程图，把一个技术原理讲透。
- 另见 [#36](https://www.prompt-motion.com/ismailfahmi-557268)、[#147](https://www.prompt-motion.com/buildfastwithai-53234e)。

### SaaS 界面走查（17 条）
- [#2](https://www.prompt-motion.com/twoclipping-5cba86) · **Shape morphing through UI states** · @twoclipping · 14s · 方形 — 一个不切镜的形状走完十来种 UI 状态，无缝循环。
- [#178](https://www.prompt-motion.com/antonio-kodheli-490109) · **Prompt Motion site promo** · @antonio_kodheli · 23s — 全屏视频和网格小卡片之间精确互切，"Copied" 胶囊升起后变成网址按钮。
- 另见 [#231](https://www.prompt-motion.com/charlesmendez-73b6e4)、[#188](https://www.prompt-motion.com/amol909s-27533e)。

### 动态字体（16 条）
- [#225](https://www.prompt-motion.com/samaote-5e2fc2) · **Synced lyrics motion video** · @samaote · 30s — 歌词对齐小节，一个太阳贯穿整首歌。
- [#44](https://www.prompt-motion.com/gizakdag-cf4ae6) · **Overthinking motion study** · @gizakdag · 15s · 竖版 — 海报级拼贴，节奏从混乱收回到平静。
- 另见 [#89](https://www.prompt-motion.com/zheke-38deff)、[#100](https://www.prompt-motion.com/gdgtify-287ddf)。

### 角色 / 故事动画（16 条）
- [#155](https://www.prompt-motion.com/faroukzy-9ff23e) · **The Last Light animated short** · @faroukzy · 4:00 — 叙事最完整，画面最美。
- [#228](https://www.prompt-motion.com/anilraok-eff262) · **Scrabble tile character story** · @Anilraok · 42s · 竖版 — Three.js 做出接近动画长片的质感，「缺的那一块」这个故事简单有力。
- 另见 [#70](https://www.prompt-motion.com/jake11moran-a269c4)（一个把真实 agent 会话拍成水彩卡通的 skill）、[#233](https://www.prompt-motion.com/kamstudiolabs-0b0824)。

### 社媒竖版广告（10 条）
- [#8](https://www.prompt-motion.com/lexnlin-038035) · **Engraving-style Claude ad** · @LexnLin · 15s · 竖版 — 一个圆点完成所有转场。
- [#112](https://www.prompt-motion.com/jesscaroline7-1ff7cb) · **Ondefica app motion reel** · @jesscaroline7 · 1:00 · 竖版 — HyperFrames 做的竖版，一个点代表一个地点的点阵地图，加计数器。
- 这个类别里还有 [#216](https://www.prompt-motion.com/spearwtf-3c1fd1)（16:9）。

### 3D 场景（8 条）
- [#64](https://www.prompt-motion.com/sayan-shanky-f850d8) · **AI data centre 3D tour** · @Sayan_shanky · 1:38 — 一句话 prompt，出来 11 章 3D 导览。
- [#158](https://www.prompt-motion.com/rebutonepress-810f78) · **Black hole time story** · @RebutonePress · 5:00 — 引力透镜黑洞，加双栏遥测对比。
- 另见 [#42](https://www.prompt-motion.com/nft-chen-5f8bb0)。

### 个人介绍片（8 条）
- [#223](https://www.prompt-motion.com/rneayan-474bcf) · **Risograph studio intro** · @rneayan · 1:09 — 通篇孔版印刷质感；标着「企划、导演、AI、剪辑」的调音台推子，一张图就说清了「人在掌控 AI」。
- [#122](https://www.prompt-motion.com/madhav-xo-f97f20) · **Personal research intro reel** · @Madhav_XO · 10s — 深色粒子网络配终端编译开场，10 秒讲完。

### 生成式抽象（6 条）
- [#83](https://www.prompt-motion.com/hbcoop-de365c) · **Full Stop figure sequence** · @HBCoop_ · 29s — 一个点讲完整个故事。
- [#53](https://www.prompt-motion.com/monokern-ade5b6) · **Psychedelic hypnotic eye showreel** · @monokern · 20s — shader 级的迷幻效果，用来看上限。

### Logo / 品牌演绎（4 条）
- [#185](https://www.prompt-motion.com/robvjourney-ce3e1a) · **Nohandslabs brand promo** · @robvjourney · 15s — 从终端开机进入品牌世界。
- [#20](https://www.prompt-motion.com/tdinh-me-815acb) · **TypingMind logo reveal** · @tdinh_me · 21s — 先画线框，再逐面填色，最后收成 App 图标。

### 工具 / Skill 演示（2 条）
- [#16](https://www.prompt-motion.com/lexnlin-6161a6) · **Cinetic skill launch film** · @LexnLin · 30s — 一个开源 skill 的发布片，skill 带 273 条技法库，结尾在终端里打出安装命令。

### 其他（8 条）
- [#26](https://www.prompt-motion.com/itsolelehmann-e47532) · **Four seasons train window** · @itsolelehmann · 30s — 前景纹丝不动，窗外四季在变，中间穿过隧道黑场。任何「前后对比」的故事都能借这个手法。

---

## 6. 方法与局限

**推荐是怎么选出来的**

1. **评分。** 233 条由 AI 评分员分 24 批打分，每批最多 10 条。评分员看的是每支视频的 6 帧联系表、prompt 和元数据，标出类别、标签、推断技术栈、视觉冲击分（1–5）、prompt 结构分（1–5），以及它对 SaaS 和产品片有多大参考价值（1–5）。
2. **初筛。** 取视觉冲击满分的 43 条，加上评分员认为对 SaaS 和产品片最有参考价值的条目，再加各类别的有力候选，共约 90 条。
3. **重排。** 逐条看初筛条目的联系表，按工艺、结构是否清楚、读者能借走多少重新排序。我们的判断和评分员不一致时，以我们的为准。

**为什么不公开单条分数**

- **评分员之间差 1 分左右。** 同一支片被发了三次（[#4](https://www.prompt-motion.com/ajith-io-b5626e)、[#129](https://www.prompt-motion.com/mrtanviir-132457)、[#227](https://www.prompt-motion.com/umangratani-57f86a)），视觉冲击分相差 1 分；另外两组转发（[#64](https://www.prompt-motion.com/sayan-shanky-f850d8) / [#117](https://www.prompt-motion.com/mdaman010-e7226a)、[#6](https://www.prompt-motion.com/himanshutwtxs-5f4b43) / [#51](https://www.prompt-motion.com/chatgptastra-0d95c7)）各自被分进了两个不同的类别。5 分制上 ±1 的误差，不足以给单条排名。
- **汇总数字更稳。** 全部 233 条的视觉冲击分：2 分 5 条，3 分 65 条，4 分 120 条，5 分 43 条（没有 1 分）。按 prompt 写法分组的平均视觉冲击分：一句话 3.88（n = 154），短 brief 3.80（n = 56），结构化 spec 3.94（n = 17），走 skill 3.83（n = 6）。这些差距都远小于评分误差，所以在这批数据里，写长 prompt 并没有换来明显更高的分；它换来的是可控和可复现（见 [prompt-patterns.md](prompt-patterns.md)）。

**我们没有核实的**

- **看的是联系表，不是完整播放。** 每支片只看了 6 帧，没有逐条从头看到尾。靠连续运动取胜的片子（比如 [#2](https://www.prompt-motion.com/twoclipping-5cba86)），静帧看起来会比实际朴素。
- **声音**只统计了有、静音、没有三种，没有评好坏。
- **推断的技术栈**来自评分员，没有对照源码核实。
- **推荐是一种判断。** 偏好工艺、清楚的结构和能复用的想法。清单之外还有很多值得看的条目，完整名单在 [`catalog/catalog.json`](../../catalog/catalog.json)。

**版权。** 视频和 prompt 归原作者所有。本仓库只链接到每个条目和原帖，不转存视频、画面或完整 prompt。
