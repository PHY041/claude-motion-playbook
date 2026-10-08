# prompt 写法：233 条 prompt 是怎么写的，出片好坏到底跟什么有关

这是 [prompt-motion.com](https://www.prompt-motion.com/)（由 [@p4nthera_](https://x.com/p4nthera_) 整理）在 2026-10-09 的快照，共 233 条：230 条带 prompt，另外 3 条是 skill，只有安装命令。文中的 `#N` 对应 [`catalog/catalog.json`](../../catalog/catalog.json) 里的 `id`。下面每个数字都是用 prompt 原文、catalog 和评分记录重新算出来的。方法和局限见[第 2.1 节](#21-方法先看这一节)。

[English version](../prompt-patterns.md)

## 要点速览

- **一条 prompt 占了半壁江山。** 那句 "showreel" 爆款一句话**原样出现了 33 次，来自 33 个不同账号**（其中 22 份逐字节完全相同）。加上改写、翻译和插品牌的版本，整个家族一共 **102 条，占 230 条 prompt 的 44%**。另有 12 条只保留了它的骨架，合计 114 条（50%）。全库 prompt 长度的中位数是 151 个字符，正好就是这句话的长度。
- **写得更多，画面不会更出彩。** 评分员按 1–5 分打视觉冲击分：结构化 spec 平均 3.94，一句话 3.88（n = 17 对 154，置换检验 p ≈ 0.87）。评分员还单独给 prompt 质量打了分，这个分和视觉冲击分几乎不相关（Spearman ρ = 0.06，p ≈ 0.40）。
- **长 spec 换来的是可控。** 结构化 spec 的成片有 76% 是产品片或品牌片，一句话只有 38%。写了单一时长的 136 条 prompt 里，131 条成片时长落在要求的 0.8–1.25 倍之内。
- **"go all out" 这类加码词是和视觉冲击分关联最强的单项写法。** 测了 15 项写法，只有它扛得住多重比较校正：4.05 对 3.73（带加码词的 95 条对不带的 135 条，p ≈ 0.001；"go all out" 本身出现在 87 条里）。但它和 showreel 模板绑在一起出现，把「是否属于模板家族」固定住之后，差距是 +0.31（p ≈ 0.04）。
- **往模板里塞品牌，几乎没有代价。** 在家族内部，点名产品或人物的 44 条平均 3.98，纯自我 showreel 的 58 条平均 4.02（p ≈ 0.89）。产品片或品牌片的占比却从 16% 升到了 70%。
- **同一句 prompt，出来的片子不一样。** 逐字原版产出的 31 支不同视频，分数从 3 到 5 都有，分属 4 个类别，时长从 14.9 秒到 45.1 秒。
- **长 spec 有一套共同的结构。** 六段 XML（`<inputs>` `<direction>` `<structure>` `<build>` `<gotchas>` `<start>`）出现在 10 条里，来自 6 个账号，时间跨度从 09-23 到 10-08。它的价值主要在三处：踩坑清单、确定性渲染规则、开工前和渲完后的检查关口。
- **评分噪声大约 ±1 分。** 所以 0.3 分以下的差距都在噪声范围内。我们只公布汇总数字，不公布单条分数。

---

## 1. 爆款一句话家族

### 1.1 原句

画廊里最早的一份是 [#3 Bold kinetic type showreel — @shneural](https://www.prompt-motion.com/shneural-2abdfa)，发布于 2026-09-24。画廊没有记录这句话最初是谁写的。

开头是 "make a dynamic 15-second motion graphics video that shows what an incredible motion designer you are …"，结尾是 "go all out."。整条 prompt 只有两句话、151 个字符，全文请看[条目页](https://www.prompt-motion.com/shneural-2abdfa)。

| 片段 | 起的作用 |
|---|---|
| 格式与时长（15 秒的 motion graphics 视频） | 定格式、定时长。时长基本会被遵守：写了单一时长的一句话有 100 条，其中 96 条成片落在要求的 0.8–1.25 倍之内。 |
| 自证（让模型当一个 incredible motion designer） | 把「做个视频」变成「证明你自己」，模型会把会的技法尽量都摆出来。 |
| 体裁（a showreel for a résumé） | 指定体裁：技法蒙太奇 + 章节编号 + 落版。所以这一族的成片长得很像。 |
| 加码（"go all out"） | 加码。加码词是和视觉冲击分关联最强的写法（见第 2.3 节）。 |

### 1.2 变体

114 条全部人工读过、归了类，完整名单见[附录 A](#附录-a家族成员)。「产品片或品牌片」指 catalog 的 `category` 是 `product-launch-film`、`saas-ui-walkthrough`、`social-ad-vertical` 或 `logo-brand-ident`。

| 变体 | 条数 | 例子 | 平均视觉冲击分 | 产品片或品牌片 |
|---|---|---|---|---|
| A 逐字原版（忽略大小写、重音、标点） | 33 | 上面的 #3 | 3.97 | 18% |
| B 原版后面追加一句 | 8 | [#17 Dub promo video — @steventey](https://www.prompt-motion.com/steventey-0d20e4)，追加一句指向产品网址的发布片要求 | 4.38 | 62% |
| C 只改时长、画幅或主题 | 14 | [#48 Jev engineering showreel — @polydao](https://www.prompt-motion.com/polydao-7a572b)，改成带 `[24]` / `[TOPIC]` / `[BRAND COLORS]` 的模板 | 3.93 | 36% |
| D 插入品牌槽（for / on / about X） | 21 | [#12 Distilbook product video — @ajith_io](https://www.prompt-motion.com/ajith-io-c52e09)，开头先让模型调研："Research Distilbook." | 3.95 | 86% |
| E 品牌当主语（what an incredible X is） | 4 | [#36 Drone Emprit showreel — @ismailfahmi](https://www.prompt-motion.com/ismailfahmi-557268) | 4.00 | 50% |
| G 英文改写 | 16 | [#137 Reflex brand motion reel — @reflex_cloud](https://www.prompt-motion.com/reflex-cloud-72ffe5) | 4.06 | 12% |
| H 翻译版（中、日、土耳其语） | 6 | [#59 Lism CSS 1.0 release video — @ddryo_loos](https://www.prompt-motion.com/ddryo-loos-300829) | 3.83 | 33% |
| F 只剩骨架（没有 designer，也没有 showreel） | 12 | [#31 SuperX feature release teaser — @robj3d3](https://www.prompt-motion.com/robj3d3-b18fad) | 3.75 | 83% |

- **核心家族**（A–E、G、H）共 102 条，来自 98 个账号，有 69 种不同的文本。算上 F 是 114 条、110 个账号、80 种文本。
- **家族整体比其他 prompt 高，但差距全来自加码词。** 核心家族平均 4.00，其余 prompt 3.75（n = 102 对 128，p ≈ 0.011）。去掉转发之后是 4.02 对 3.74（p ≈ 0.003）。把加码词固定住之后，差距只剩 +0.02（分层置换检验 p ≈ 0.89）。
- **逐字原版单拿出来并不特别：** 3.97 对其余的 3.84（p ≈ 0.37）。
- **时间分布。** 逐字原版的发布日期：09-24 有 1 条，09-25 有 21 条，09-26 有 10 条，09-27 有 1 条。09-25 和 09-26 也是全库发帖最多的两天，分别 82 条和 68 条。
- **转发。** [#129 Claude motion designer showreel — @mrtanviir](https://www.prompt-motion.com/mrtanviir-132457) 和 [#227 Shape and dot motion showreel — @umangratani](https://www.prompt-motion.com/umangratani-57f86a) 转发的是同一支视频（重新压成了 720p），原片是 [#4 Abstract motion design reel — @ajith_io](https://www.prompt-motion.com/ajith-io-b5626e)，#4 是最早的那条。所以 33 条逐字原版实际对应 31 支不同的视频。
- **常见的小改法：**
  - 开头先加一步调研（#12）；
  - 让模型用品牌自家的 API 生成素材（[#102 fal motion design showreel — @influencer_seo](https://www.prompt-motion.com/influencer-seo-ce8c33)）；
  - 结尾加一句命令，比如 "dont ask just make"（[#166 Swiss-style motion showreel — @levabashidze](https://www.prompt-motion.com/levabashidze-2d713a)）。

### 1.3 这个模板容易产出什么

这一节只做描述，依据是 catalog 里的标签和技法记录，不是分数。

- **HUD 装饰**（时间码、取景框角标、节拍计数）出现在 **31 支逐字原版视频中的 23 支（74%）**。其他视频里是 22%，17 支结构化 spec 成片里一支都没有。
- **粒子**出现在 31 支中的 17 支（55%），其他视频 16%，结构化 spec 成片同样一支没有。
- **已经有 prompt 明着禁这种风格。** [#63 Claude self-intro motion graphic — @1littlecoder](https://www.prompt-motion.com/1littlecoder-9fef89) 写的是 "Avoid the frames and texts on the corners which are typical ai made giveaways!"。同一句 prompt 也被另一个账号发成了 [#215 Kinetic type self-portrait — @souravbhar871](https://www.prompt-motion.com/souravbhar871-61f424)。第 3 节里还有两条长 spec 也禁了时间轴类装饰。

### 1.4 看得见的 prompt 不是全部输入

31 支逐字原版视频里有 6 支是产品片，但 prompt 里一个产品名都没有：

- [#7 Enxovaly baby app promo — @gabrielbuzziv](https://www.prompt-motion.com/gabrielbuzziv-4ff0c6)
- [#11 Travel visa service promo — @thismacapital](https://www.prompt-motion.com/thismacapital-dfba20)
- [#21 AjustaCV Pro pricing promo — @thayto_dev](https://www.prompt-motion.com/thayto-dev-44b911)
- [#115 LiteLLM promo reel — @MisbahSy](https://www.prompt-motion.com/misbahsy-80eaec)
- [#193 Crux motion design showreel — @marouanegazouzi](https://www.prompt-motion.com/marouanegazouzi-6071d5)
- [#222 Lead Notifi product ad — @leadnotifi](https://www.prompt-motion.com/leadnotifi-e83f94)

模型显然拿到了画廊里看不到的上下文，比如代码仓库、项目文件或之前的对话。别的条目大概也有类似情况，所以读下面「prompt 和质量」的数字时，要把这一点放在心里。

---

## 2. 哪些写法和画面质量相关，哪些不相关

### 2.1 方法（先看这一节）

- **分数。** 「视觉冲击分」是 AI 评分员打的 1–5 分，评分时看的是视频的 6 帧联系表，加上 prompt。不同评分员之间通常差 ±1 分左右。
  - 验证：有 5 条是对库里已有视频的转发。5 次里有 4 次转发和原条分数相同，1 次差 1 分。
  - 正因为有这个噪声，**不公布单条分数**。
- **分数分布。** 230 条 prompt 里，2 分 5 条、3 分 65 条、4 分 117 条、5 分 43 条，没有 1 分。均值 3.86，标准差 0.73。几乎都挤在 3、4 分，所以 0.3 分的差距已经算大了。
- **写法特征**用正则表达式从 prompt 原文里识别；第 1 节的变体家族是人工归类的。
- **检验。** p 值来自对均值差的双侧置换检验（固定随机种子，打乱 20,000 次标签）；Spearman 的 p 值也用置换检验。一共测了 15 项写法，Bonferroni 校正后的阈值是 0.05 / 15 ≈ 0.0033。
- **「产品片或品牌片」**用的是 catalog 的 `category`，由同一批评分员标注。它是分类标签，不是分数。

### 2.2 单项写法与视觉冲击分（230 条 prompt）

| prompt 里有这项写法 | 有的条数 | 平均视觉冲击分（有 / 没有） | 差 | p |
|---|---|---|---|---|
| 加码词（"go all out" 出现在 87 条里，另加 "go crazy"、全力……） | 95 | 4.05 / 3.73 | **+0.33** | **0.001** |
| showreel / résumé / portfolio 体裁 | 92 | 4.02 / 3.75 | +0.27 | 0.007 |
| 写了网址、@账号或占位符 | 33 | 4.03 / 3.83 | +0.20 | 0.15 |
| 写了时长 | 148 | 3.93 / 3.74 | +0.18 | 0.07 |
| 禁用 / 避免清单 | 17 | 4.00 / 3.85 | +0.15 | 0.50 |
| 全量制作前先确认 | 10 | 4.00 / 3.85 | +0.15 | 0.66 |
| BPM / 节拍网格 | 18 | 3.89 / 3.86 | +0.03 | 0.87 |
| 要音乐、音效或配音 | 44 | 3.89 / 3.85 | +0.03 | 0.82 |
| 渲完自查 | 12 | 3.83 / 3.86 | −0.03 | 1.00 |
| 用真素材（仓库、官网、截图） | 31 | 3.81 / 3.87 | −0.06 | 0.69 |
| 先调研 / 先读资料 | 20 | 3.80 / 3.87 | −0.07 | 0.75 |
| 角色设定（"you are a … designer"） | 9 | 3.78 / 3.86 | −0.09 | 0.82 |
| 确定性渲染（seek(t)、时间的纯函数） | 13 | 3.77 / 3.87 | −0.10 | 0.70 |
| 写了 hex 色值 | 8 | 3.75 / 3.86 | −0.11 | 0.81 |
| 点名技术栈 | 37 | 3.70 / 3.89 | −0.19 | 0.18 |

只有第一行过了校正后的阈值。差值为负的几行都在噪声范围内（p ≥ 0.18），不能据此说 hex 色值或角色设定会拉低质量。

### 2.3 把加码词单独拆出来看

加码词和 showreel 体裁通常一起出现，所以拆成四格：

| | 有 showreel 体裁 | 没有 showreel 体裁 |
|---|---|---|
| **有加码词** | 4.06（n = 81） | 4.00（n = 14） |
| **没有加码词** | 3.73（n = 11） | 3.73（n = 124） |

- **只有 showreel 体裁、没有加码词时，分数和基线一样。** 把加码词固定住，体裁只多 +0.03（分层置换 p ≈ 0.88）。
- **加码词在两种分层下都保持差距。** 固定「是否属于家族」时差 +0.31（p ≈ 0.04），固定「是否有 showreel 体裁」时差 +0.30（p ≈ 0.06）。
- **带加码词的 prompt，翻车也更少：** 3 分及以下占 18%，其余 prompt 是 39%。
- **这是相关，不能证明因果。** 有两格样本很小，只有 14 条和 11 条。
- **口径放宽，差距更大。** 我们自己挑了一份更宽的「强烈措辞」清单（n = 118 对 112），差距是 +0.42（p < 0.001）。但那份清单本身是主观判断。

### 2.4 长 spec 对一句话

| prompt 类型（catalog） | 条数 | 平均视觉冲击分 | 3 分及以下 | 产品片或品牌片 |
|---|---|---|---|---|
| 一句话 | 154 | 3.88 | 31% | 38% |
| 短 brief | 56 | 3.80 | 29% | 48% |
| 结构化 spec | 17 | 3.94 | 24% | 76% |
| 走 skill | 6 | 3.83 | 33% | 33% |

- **视觉冲击分：没有实质差别。** 结构化 spec 对一句话 +0.06（p ≈ 0.87）；超过 500 字符的对其余的 +0.15（n = 23 对 207，p ≈ 0.37）。
- **长度和视觉冲击分有很弱的正向等级相关**（ρ = 0.14，p ≈ 0.04），主要是最短的那批拉低的：
  - 100 字符及以下：均值 3.70，42% 在 3 分及以下；
  - 101–200 字符（一句话家族所在的区间）：均值 3.95，25% 在 3 分及以下。
- **prompt 写得好，不等于画面出彩。** 评分员给的 prompt 质量分和长度强相关（ρ = 0.68），和视觉冲击分几乎不相关（ρ = 0.06，p ≈ 0.40）。质量 5 分的 15 条平均视觉冲击分 4.00，质量 1 分的 47 条平均 3.72。
- **长 spec 改变的是「拿到什么」：**
  - 产品片，而不是技法蒙太奇（76% 对 38%）；
  - 要求的格式和文案；
  - 可能更少翻车（3 分及以下 24% 对 31%）。最后这一点是我们的解读，n = 17 的数据只能弱支持。

### 2.5 插入品牌

只看核心家族：

| | 条数 | 平均视觉冲击分 | 产品片或品牌片 |
|---|---|---|---|
| 点名产品、品牌、项目或人物 | 44 | 3.98 | 70% |
| 纯自我 showreel | 58 | 4.02 | 16% |

视觉冲击分差 −0.04（p ≈ 0.89），可以视为零。**加一个品牌槽，大多数成片就变成了产品片，视觉冲击分没有可测量的损失。** 纯自我那一组也包括了那 6 条没写产品名、却照样出了产品片的逐字原版（第 1.4 节）。

### 2.6 同一句 prompt，结果差多少

- **逐字原版。** 它的 31 支不同视频，3 分、4 分、5 分分别是 7、17、7 支，分属 4 个 catalog 类别，时长 14.9–45.1 秒。
- **另外还有 4 句 prompt，各被发过两次、对应两支不同的视频：**
  - [#2 Shape morphing through UI states — @twoclipping](https://www.prompt-motion.com/twoclipping-5cba86) 和 [#97 Morphing UI states loop — @demonugc](https://www.prompt-motion.com/demonugc-4c5753)，用的是同一份 2,711 字符的 spec；
  - [#12 Distilbook product video — @ajith_io](https://www.prompt-motion.com/ajith-io-c52e09) 和 [#33 Distilbook motion showreel — @itisRazak](https://www.prompt-motion.com/itisrazak-3ad902)；
  - [#63 Claude self-intro motion graphic — @1littlecoder](https://www.prompt-motion.com/1littlecoder-9fef89) 和 [#215 Kinetic type self-portrait — @souravbhar871](https://www.prompt-motion.com/souravbhar871-61f424)；
  - [#160 DistilBook product explainer — @sudo_kiran](https://www.prompt-motion.com/sudo-kiran-4f8b59) 和 [#68 DistilBook motion explainer — @sudo_kiran](https://www.prompt-motion.com/sudo-kiran-b055de)。这是全库唯一一例同一个账号把自己的 prompt 又跑了一遍。

  四对里，每对两支视频都差 1 分。
- **坦白说：** 1 分也正好是评分噪声的大小，所以分不清这里面多少是模型的波动、多少是评分的波动。
- **但两次运行确实不一样。** 不靠分数的证据有：同一句 prompt 落进了不同类别、不同时长；#2/#97 这一对，一支带配乐发布，另一支没有。
- **实际含义：** 拿一两支片子比较，说明不了哪种写法更好。同一句 prompt 内部的波动（最多 2 分），比第 2.2 节里任何一项写法带来的平均差距（最多 0.33 分）还大。

### 2.7 能说的和不能说的

- **能说：**
  - 加码词和更高的视觉冲击分相关。
  - 长 spec、点名品牌和「切题的产品片」相关。
  - 写法只能解释视觉冲击分差异里很小的一部分。
- **不能说：**
  - 「写得越细，画面越出彩」：数据不支持。
  - 「hex 色值、角色设定、点名技术栈会拉低质量」：这几项各只有 8–37 条，差距在噪声级别。
  - 从 `effort` 元数据得出任何结论：只有 36 条标了（Max 22 条 4.09，High 7 条 4.29，Medium 7 条 3.57）。
- **幸存者偏差。** 画廊里只有作者愿意发出来的片子。一句话的高分里，可能有一部分来自「跑了好几次，挑最好的发」，被丢掉的版本看不到。
- **评分可能有偏向（推测，未核实）。** 评分员看片时也看到了 prompt，而视觉冲击分可能更偏爱技法密度（3D、粒子、风格跳切），很多长 spec 恰恰是有意禁掉这些的。
- **样本不独立。** 模板会被照抄：一份长 spec 被逐字复用，另一份相似度 99.5%（见第 3.1 节）；另有 5 支视频被其他账号转发。

---

## 3. 长结构化 spec 的解剖

### 3.1 写法

**六段 XML**（`<inputs>` `<direction>` `<structure>` `<build>` `<gotchas>` `<start>`）：10 条，来自 6 个账号。

- **谁在用。** 按发布顺序：
  - [#13 UGC ad generator promo — @twoclipping](https://www.prompt-motion.com/twoclipping-6dd14e)，最早，09-23；
  - [#2 Shape morphing through UI states — @twoclipping](https://www.prompt-motion.com/twoclipping-5cba86)（同一账号）；
  - [#97 Morphing UI states loop — @demonugc](https://www.prompt-motion.com/demonugc-4c5753)，逐字复用 #2；
  - [#5 Photo print app launch film — @twoclipping](https://www.prompt-motion.com/twoclipping-221cab)；
  - [#34 Frame by Frame launch video — @notdwd](https://www.prompt-motion.com/notdwd-7de38a)；
  - [#10 Launch video remake comparison — @notdwd](https://www.prompt-motion.com/notdwd-c2037d)，和 #34 有 99.5% 相同，只多了品牌色的处理；
  - [#25 Orange dot motion system — @ultimaxbt](https://www.prompt-motion.com/ultimaxbt-bbebf5)；
  - [#178 Prompt Motion site promo — @antonio_kodheli](https://www.prompt-motion.com/antonio-kodheli-490109)，去掉了 `<start>`；
  - [#38 Ora 2 image model launch film — @rossaxbt](https://www.prompt-motion.com/rossaxbt-3085b7)，加了 `<script>` `<voice>` `<sound>`；
  - [#52 Food craving launch film — @ultimaxbt](https://www.prompt-motion.com/ultimaxbt-2ddf1e)，最晚，10-08。
- **为什么值得注意：** 这是一个会在账号之间传播的模板。

| 其他写法 | 条目 | 说明 |
|---|---|---|
| 自定标签的 XML | [#66 Spotify product film — @brainextends](https://www.prompt-motion.com/brainextends-e19ac3) | 交付物、美术方向、时间线、常驻播放器、运动质量、音频、验证 |
| 横线分节的 brief | [#104 Taxtello bookkeeping app film — @daniel_haida](https://www.prompt-motion.com/daniel-haida-8691d4) | 15,306 字符，全库最长；16 个标题，从「事实来源」到「质量标准」，最后是「最终交付物」 |
| 大写小标题挤在一段 | [#100 Speech built as architecture — @Gdgtify](https://www.prompt-motion.com/gdgtify-287ddf) | 美术方向、逐字演讲稿、分镜、编排、工程、质量关口 |
| 带占位符的可复用模板 | [#126 Paper-style product launch film — @ik_builds](https://www.prompt-motion.com/ik-builds-b8bdcf) | `{{PRODUCT}}`、`{{POSITIONING_DOCS}}`、`{{BANNED_WORDS}}`……；全库唯一一条 HyperFrames 长 spec |
| 列表 brief 或一大段话 | 9 条 | 500–1,006 字符，见[附录 B](#附录-b超过-500-字符的-23-条-prompt) |

### 3.2 逐段拆解

**`<inputs>`：先问，问不到就用默认值。** 这一段让 prompt 可以反复套用。

- **问什么：** 模型先要产品名、logo、要展示的界面时刻、实拍素材和音乐。
- **默认值。** 有 4 条（#10、#34、#38、#52）给出了用户没提供时用什么，#10 的说法是 "If I skip any, use the defaults"。
- **授权。** 凡是点名了音乐来源的长 spec，点的都是可免费商用的来源，Mixkit 在 9 条 prompt 里出现。#104 禁止从网上抓有版权的音频，#126 只允许 CC0 或自己生成的声音。

**`<direction>`：一种画风、一条运动规则、一张禁用清单。**

- **连续性写成硬规则。** 有 5 条（#2、#5、#25、#52、#97）要求一镜到底，或者用一个物件串起每一场。例如 "One shape, never cut"（#2）、"The orange dot connects every scene"（#25）。
- **镜头规则写成约束，而不是愿望。** #52 要求每场只做一次缓动运镜，不能连着推近又拉远；#178 不允许两个运镜同时发生。
- **把克制写成目标。** #104 宁要几个出彩的瞬间，也不要一堆平平无奇的。

**禁用清单表达的是品味，不是行业规矩。** 只在 prompt 明确「禁」某项时才计数：

| 被禁项 | 禁它的条数 | 反而点名要它的 |
|---|---|---|
| 空镜、长停顿、冻帧 | 9 | — |
| 粒子 | 8 | 2 条：[#41 Motion techniques showreel — @lukasersil](https://www.prompt-motion.com/lukasersil-0ed38e)、[#105 Badge unlock screen animation — @BThreeAgency](https://www.prompt-motion.com/bthreeagency-b9b8d9) |
| 看起来像模板 | 8 | — |
| 光晕（glow） | 7 | 3 条：#38、#52、[#134 SaaS launch video — @aschapmann](https://www.prompt-motion.com/aschapmann-131210) |
| 弹跳缓动 | 7 | — |
| 交叉淡化，或把淡入淡出当默认转场 | 7 | — |
| 渐变 | 5 | 好几条，用作配色或光晕 |
| 角落 HUD / 时间轴装饰 | 4 | — |
| 编造数字或功能 | 3（#104、#126、#178） | — |

**`<structure>`：节拍表，时间单位有三种。**

- **按音乐拍子**，最常见："120 BPM, 7 bars, something happens on every beat"（#2），每个动作都钉在小节号或拍号上。
- **按帧号。** #10 把每个镜头精确到帧号和像素坐标，硬切点放在拍点前面一点。
- **按语句。** #100 明确拒绝卡拍："Do not force the speech onto a dance beat."；#38 则跟着配音的句首切镜头。
- **只给方向。** 精度的另一头是 #104，它把自己的分镜称为 "a strong starting point, not a rigid template"。

**`<build>`：让渲染确定、可复现。**

- **每一帧都是时间的纯函数。** 13 条 prompt 要求 seek(t) 式渲染：不用 CSS 过渡，不用计时器，帧和帧之间不带状态。其中两条是短 prompt（[#161 SaaS product launch video — @xelandre__](https://www.prompt-motion.com/xelandre-363f00)、[#230 Token bucket rate limiter — @ParkerRex](https://www.prompt-motion.com/parkerrex-1a54fe)）。弹簧写成闭式解，这样也能任意跳帧。
- **用子帧叠出运动模糊。** 7 条 prompt 每帧渲 3 到 8 个子帧，大多用 ffmpeg 的 `tmix` 混合。#52 的经验来之不易："Four subframes leave ghost copies on fast moves, so render 8 and slow the move down."
- **音效按实测峰值对位。** 让音效最响的那一刻、"not its file start"，落在事件上（#13）。7 条这样做，8 条把响度统一到 −14 LUFS。
- **镜头和交接：**
  - 整个世界层只有一个变换，缩放在对数空间里插值（#52、#178）；
  - "Make every handoff a shared element"（#52）。
- **先抓真素材，什么都不编：**
  - #178 先抓取网站，并要求 "Quote all of it verbatim."；
  - #104 先看产品仓库，再开始设计；
  - 配套的工程习惯是：所有时间点放一个文件，所有文案放另一个文件。

**`<gotchas>`：只有真做过才知道的坑。** 这一段最难凭空写出来，也最值钱。

- **铺满全屏的色块。** 要越过四个角，并且用上几帧的时间铺开，否则半个画面会在一帧之内突变（#5，#52 和 #25 也有同样的规则）。
- **3D。** 给 `preserve-3d` 元素设透明度或滤镜，它会被压平，要改成淡化它的外层（#13）。
- **字体。** 等字体加载完再量文字；长名字放不下时，整个标志组合一起缩放（#10）。
- **缩放的文字。** 被镜头缩放的元素如果带着 `will-change`，文字会发糊（#2）。
- **同色消失。** 和页面同色的卡片要加 1 px 细边，否则会看不见（#178、#10）。
- **太短的淡入。** "A 0.05s fade looks like an instant pop-in."（#38）
- **换字。** 在移动的形状里换字，出场和入场要分开计时（#2、#25、#66）。

**`<start>`：花大钱之前的确认关口。** 9 条 spec 以 `<start>` 结尾，内容都是三步：

1. 先问输入；
2. 交出节拍表、分镜或 4–8 张静帧；
3. 确认之后才做完整的片子。

#178 用散文写了同样的要求。

**渲完以后的 QA。**

- **逐帧检查。** 4 条每拍出一帧检查（#2、#5、#25、#97）；有 4 条（#5、#38、#52、#178）扫描全片，找单帧跳变。#5 的标准是 "frame-difference spikes 3x their neighbours"。
- **换人复审。** #178 要求 "have a fresh critic who didn't build it review the render, and fix what it finds."
- **看真实成片。** #104 检查的是从最终 MP4 里解码出来的帧，不是浏览器截图，最后写道："Do not declare success because the code compiles. The deliverable is the FILM."
- **短 prompt 也能带自查。** #134 要求 "render it, check the frames yourself and fix anything that overlaps, clips or feels rushed before showing me the result"。

### 3.3 短 brief 里的好招

- **把真素材拆开做动画，而不是贴截图。** [#32 mdfor.dev product intro video — @HO_BA](https://www.prompt-motion.com/ho-ba-f3f0e9)："break them down into components/icons so we can animate those too."
- **事实只取自来源。** "Use only facts and numbers that are on the site."（[#127 Developer portfolio site showreel — @wani_shola](https://www.prompt-motion.com/wani-shola-16ca7a)）；#126 直接禁止编造结果。
- **把故事弧写出来：**
  - #134 是市场 → 痛点 → 解法 → 收获；
  - [#18 Animated business explainer — @alex_prompter](https://www.prompt-motion.com/alex-prompter-1ea044) 是问题 → 我做什么 → 三步 → 一个证据 → 名字。
- **一条规则撑起全片。** "every note comes from a visible collision"（[#200 Collision-driven music machine — @KamStudioLabs](https://www.prompt-motion.com/kamstudiolabs-447565)）；或者一个物件穿过每一场（#25、#126）。
- **散文分镜也行。** [#77 Sahi trading terminal reveal — @dale_vaz](https://www.prompt-motion.com/dale-vaz-cc612a) 一个标签都没用，写的是镜头从一个点一路拉到整个桌面、再推回来的过程。

---

## 4. 用在 SaaS 发布片上

1. **先用一句话探索。** 用插品牌槽的变体，在产品仓库里跑，每个版本跑 2–3 次再下判断。同一句 prompt 能差一两分（第 2.6 节），仓库上下文也会明显改变成片（第 1.4 节）。
2. **想要产品片，就留下加码词、去掉 showreel 体裁。** 有了加码词之后，体裁带不来可测量的提升（第 2.3 节），反而会把片子带向 HUD 堆满的技法蒙太奇（第 1.3 节）。
3. **方向定了，再换成结构化 spec。** 它不会让片子更出彩，但会让片子讲的是你的产品、用你要的格式、用真实界面和真实事实来做，并且在花大钱渲染之前先过一道确认。
4. **先借用踩坑清单和检查关口。** 这是 spec 里最不显眼的部分，写进去几乎没有成本。

我们从零写了一份 HyperFrames 模板：[`templates/saas-launch-film.hyperframes.md`](../../templates/saas-launch-film.hyperframes.md)。

---

## 附录 A：家族成员

A 逐字原版（33）：[#1 @stephanlivera](https://www.prompt-motion.com/stephanlivera-df17a2)、[#3 @shneural](https://www.prompt-motion.com/shneural-2abdfa)、[#4 @ajith_io](https://www.prompt-motion.com/ajith-io-b5626e)、[#6 @himanshutwtxs](https://www.prompt-motion.com/himanshutwtxs-5f4b43)、[#7 @gabrielbuzziv](https://www.prompt-motion.com/gabrielbuzziv-4ff0c6)、[#11 @thismacapital](https://www.prompt-motion.com/thismacapital-dfba20)、[#21 @thayto_dev](https://www.prompt-motion.com/thayto-dev-44b911)、[#30 @jasonzhou1993](https://www.prompt-motion.com/jasonzhou1993-8595e0)、[#39 @tequilafunks](https://www.prompt-motion.com/tequilafunks-97f6c9)、[#50 @ayushunleashed](https://www.prompt-motion.com/ayushunleashed-ece3e3)、[#60 @eyishazyer](https://www.prompt-motion.com/eyishazyer-af035b)、[#61 @blue_clarity](https://www.prompt-motion.com/blue-clarity-ef56d0)、[#69 @RaphaelAubryy](https://www.prompt-motion.com/raphaelaubryy-4b137e)、[#72 @codeSTACKr](https://www.prompt-motion.com/codestackr-c071bf)、[#115 @MisbahSy](https://www.prompt-motion.com/misbahsy-80eaec)、[#118 @motiondsgnr](https://www.prompt-motion.com/motiondsgnr-9dcfa6)、[#129 @mrtanviir](https://www.prompt-motion.com/mrtanviir-132457)、[#136 @Web3Wesley](https://www.prompt-motion.com/web3wesley-7bb108)、[#156 @m1n9_k7](https://www.prompt-motion.com/m1n9-k7-ff9ab9)、[#168 @zaqailo](https://www.prompt-motion.com/zaqailo-212ad3)、[#169 @CrazyAlphaaa](https://www.prompt-motion.com/crazyalphaaa-bc7e75)、[#170 @fionntobin](https://www.prompt-motion.com/fionntobin-97b7af)、[#172 @itsuki_dev](https://www.prompt-motion.com/itsuki-dev-10942d)、[#177 @tolgayhickiran](https://www.prompt-motion.com/tolgayhickiran-e90799)、[#187 @3xtihor](https://www.prompt-motion.com/3xtihor-0f6911)、[#192 @LeonKohli](https://www.prompt-motion.com/leonkohli-6dc01b)、[#193 @marouanegazouzi](https://www.prompt-motion.com/marouanegazouzi-6071d5)、[#195 @safarkhanshuvo](https://www.prompt-motion.com/safarkhanshuvo-ffd52d)、[#196 @sahildesigner23](https://www.prompt-motion.com/sahildesigner23-ee3155)、[#217 @TeslaChartz](https://www.prompt-motion.com/teslachartz-c58b32)、[#222 @leadnotifi](https://www.prompt-motion.com/leadnotifi-e83f94)、[#226 @Shinskinakamoto](https://www.prompt-motion.com/shinskinakamoto-20190b)、[#227 @umangratani](https://www.prompt-motion.com/umangratani-57f86a)

B 原版 + 追加一句（8）：[#14 @samuel_yostt](https://www.prompt-motion.com/samuel-yostt-891f87)、[#17 @steventey](https://www.prompt-motion.com/steventey-0d20e4)、[#143 @Adamdesgns](https://www.prompt-motion.com/adamdesgns-478d6d)、[#152 @Sudiyasa_](https://www.prompt-motion.com/sudiyasa-f48ac9)、[#166 @levabashidze](https://www.prompt-motion.com/levabashidze-2d713a)、[#174 @kyonax_on_tech](https://www.prompt-motion.com/kyonax-on-tech-aabc1d)、[#181 @danilowm](https://www.prompt-motion.com/danilowm-d3720d)、[#191 @johnsavage_ai](https://www.prompt-motion.com/johnsavage-ai-b091c0)

C 只改时长、画幅或主题（14）：[#28 @jacksonfall](https://www.prompt-motion.com/jacksonfall-54b2ac)、[#32 @HO_BA](https://www.prompt-motion.com/ho-ba-f3f0e9)、[#44 @gizakdag](https://www.prompt-motion.com/gizakdag-cf4ae6)、[#48 @polydao](https://www.prompt-motion.com/polydao-7a572b)、[#53 @monokern](https://www.prompt-motion.com/monokern-ade5b6)、[#56 @Math_files](https://www.prompt-motion.com/math-files-39c9d0)、[#107 @ndhabarde11](https://www.prompt-motion.com/ndhabarde11-f155b4)、[#109 @rendesr](https://www.prompt-motion.com/rendesr-86be44)、[#112 @jesscaroline7](https://www.prompt-motion.com/jesscaroline7-1ff7cb)、[#142 @elliot_garreffa](https://www.prompt-motion.com/elliot-garreffa-f334bc)、[#175 @loicRambo](https://www.prompt-motion.com/loicrambo-ad6830)、[#186 @VanshWTFFF](https://www.prompt-motion.com/vanshwtfff-db0466)、[#206 @thilina_a](https://www.prompt-motion.com/thilina-a-891c09)、[#210 @ibrahimwasim240](https://www.prompt-motion.com/ibrahimwasim240-809370)

D 插入品牌槽（21）：[#12 @ajith_io](https://www.prompt-motion.com/ajith-io-c52e09)、[#33 @itisRazak](https://www.prompt-motion.com/itisrazak-3ad902)、[#37 @melvynx](https://www.prompt-motion.com/melvynx-6cde6c)、[#47 @ajith_io](https://www.prompt-motion.com/ajith-io-4c248f)、[#49 @ajith_io](https://www.prompt-motion.com/ajith-io-ea7f2d)、[#76 @prasad_pilla](https://www.prompt-motion.com/prasad-pilla-2c0cba)、[#91 @sudeepsd_](https://www.prompt-motion.com/sudeepsd-1a3485)、[#102 @influencer_seo](https://www.prompt-motion.com/influencer-seo-ce8c33)、[#103 @agonaliu_](https://www.prompt-motion.com/agonaliu-466a8f)、[#111 @en______ra](https://www.prompt-motion.com/en-ra-81c6dd)、[#113 @TheViableEdge](https://www.prompt-motion.com/theviableedge-9065be)、[#116 @reyzostyle](https://www.prompt-motion.com/reyzostyle-b55864)、[#128 @manuelogomigo](https://www.prompt-motion.com/manuelogomigo-f33ca9)、[#132 @JayScambler](https://www.prompt-motion.com/jayscambler-3f8889)、[#133 @utopyaszx](https://www.prompt-motion.com/utopyaszx-1b2f94)、[#141 @Devius_Maximus](https://www.prompt-motion.com/devius-maximus-beab45)、[#150 @bizibeast](https://www.prompt-motion.com/bizibeast-10f264)、[#157 @quickdesignio](https://www.prompt-motion.com/quickdesignio-dd93d0)、[#167 @miskinho_](https://www.prompt-motion.com/miskinho-443898)、[#173 @KangarooHere](https://www.prompt-motion.com/kangaroohere-b10f8d)、[#188 @Amol909S](https://www.prompt-motion.com/amol909s-27533e)

E 品牌当主语（4）：[#36 @ismailfahmi](https://www.prompt-motion.com/ismailfahmi-557268)、[#119 @Astrodevil_](https://www.prompt-motion.com/astrodevil-3f2054)、[#182 @KmAsiff](https://www.prompt-motion.com/kmasiff-cc72cb)、[#184 @rammanq](https://www.prompt-motion.com/rammanq-f5a90f)

G 英文改写（16）：[#41 @lukasersil](https://www.prompt-motion.com/lukasersil-0ed38e)、[#57 @hanifproduktif](https://www.prompt-motion.com/hanifproduktif-54bdee)、[#62 @RoundtableSpace](https://www.prompt-motion.com/roundtablespace-d3a1be)、[#71 @arjunsh1607](https://www.prompt-motion.com/arjunsh1607-93005d)、[#81 @samuel_spitz](https://www.prompt-motion.com/samuel-spitz-974923)、[#84 @AIStockSavvy](https://www.prompt-motion.com/aistocksavvy-3fb9f5)、[#89 @zheke](https://www.prompt-motion.com/zheke-38deff)、[#110 @BogdanDragomir](https://www.prompt-motion.com/bogdandragomir-35e024)、[#127 @wani_shola](https://www.prompt-motion.com/wani-shola-16ca7a)、[#137 @reflex_cloud](https://www.prompt-motion.com/reflex-cloud-72ffe5)、[#144 @andginja](https://www.prompt-motion.com/andginja-333d32)、[#151 @heyiammallik](https://www.prompt-motion.com/heyiammallik-e72d17)、[#163 @HenkPoley](https://www.prompt-motion.com/henkpoley-3d3407)、[#190 @ghinaiya_nirmal](https://www.prompt-motion.com/ghinaiya-nirmal-5d8fec)、[#208 @blushpetal795](https://www.prompt-motion.com/blushpetal795-0c85c2)、[#225 @samaote](https://www.prompt-motion.com/samaote-5e2fc2)

H 翻译版（6）：[#51 @ChatGptAstra](https://www.prompt-motion.com/chatgptastra-0d95c7)、[#59 @ddryo_loos](https://www.prompt-motion.com/ddryo-loos-300829)、[#108 @_topi_003](https://www.prompt-motion.com/topi-003-9ca6b5)、[#125 @_topi_003](https://www.prompt-motion.com/topi-003-b0e12c)、[#189 @cansincengiz_me](https://www.prompt-motion.com/cansincengiz-me-cf68dd)、[#201 @Grace_sunnyy](https://www.prompt-motion.com/grace-sunnyy-29bc61)

F 只剩骨架（12）：[#31 @robj3d3](https://www.prompt-motion.com/robj3d3-b18fad)、[#63 @1littlecoder](https://www.prompt-motion.com/1littlecoder-9fef89)、[#73 @hqmank](https://www.prompt-motion.com/hqmank-7c61f1)、[#94 @paulo_kombucha](https://www.prompt-motion.com/paulo-kombucha-96431c)、[#114 @0xfemyn](https://www.prompt-motion.com/0xfemyn-e114d3)、[#121 @macrohou](https://www.prompt-motion.com/macrohou-33959d)、[#164 @FractaDev](https://www.prompt-motion.com/fractadev-149adc)、[#176 @madebyjmayala](https://www.prompt-motion.com/madebyjmayala-b9204d)、[#204 @deebeeeff](https://www.prompt-motion.com/deebeeeff-50fcd0)、[#209 @ceowinkz](https://www.prompt-motion.com/ceowinkz-7c776b)、[#211 @Jazzen_Chen](https://www.prompt-motion.com/jazzen-chen-4542ae)、[#215 @souravbhar871](https://www.prompt-motion.com/souravbhar871-61f424)

## 附录 B：超过 500 字符的 23 条 prompt

| 条目 | 字符数 | 写法 | 声明的技术栈 |
|---|---|---|---|
| [#104 Taxtello bookkeeping app film — @daniel_haida](https://www.prompt-motion.com/daniel-haida-8691d4) | 15,306 | 分节 brief（16 个横线标题） | Remotion |
| [#10 Launch video remake comparison — @notdwd](https://www.prompt-motion.com/notdwd-c2037d) | 10,419 | 六段 XML（精确到帧） | — |
| [#34 Frame by Frame launch video — @notdwd](https://www.prompt-motion.com/notdwd-7de38a) | 10,311 | 六段 XML（和 #10 几乎相同） | — |
| [#66 Spotify product film — @brainextends](https://www.prompt-motion.com/brainextends-e19ac3) | 8,142 | XML，自定 8 个标签 | — |
| [#38 Ora 2 image model launch film — @rossaxbt](https://www.prompt-motion.com/rossaxbt-3085b7) | 5,800 | 六段 XML + 脚本 / 配音 / 声音 | HTML canvas + Playwright + ffmpeg |
| [#5 Photo print app launch film — @twoclipping](https://www.prompt-motion.com/twoclipping-221cab) | 5,222 | 六段 XML | HTML + Playwright |
| [#52 Food craving launch film — @ultimaxbt](https://www.prompt-motion.com/ultimaxbt-2ddf1e) | 4,667 | 六段 XML | HTML |
| [#100 Speech built as architecture — @Gdgtify](https://www.prompt-motion.com/gdgtify-287ddf) | 4,373 | 大写小标题挤在一段 | SVG/Canvas |
| [#178 Prompt Motion site promo — @antonio_kodheli](https://www.prompt-motion.com/antonio-kodheli-490109) | 4,024 | 五段 XML（没有 start） | Remotion |
| [#25 Orange dot motion system — @ultimaxbt](https://www.prompt-motion.com/ultimaxbt-bbebf5) | 3,367 | 六段 XML | HTML |
| [#2 Shape morphing through UI states — @twoclipping](https://www.prompt-motion.com/twoclipping-5cba86) | 2,711 | 六段 XML | HTML + Playwright |
| [#97 Morphing UI states loop — @demonugc](https://www.prompt-motion.com/demonugc-4c5753) | 2,711 | 六段 XML（和 #2 逐字相同） | HTML, Playwright |
| [#13 UGC ad generator promo — @twoclipping](https://www.prompt-motion.com/twoclipping-6dd14e) | 2,515 | 六段 XML（最早，09-23） | HTML + Playwright |
| [#126 Paper-style product launch film — @ik_builds](https://www.prompt-motion.com/ik-builds-b8bdcf) | 1,528 | 占位符模板 | HyperFrames + GSAP |
| [#127 Developer portfolio site showreel — @wani_shola](https://www.prompt-motion.com/wani-shola-16ca7a) | 1,006 | 列表 brief | Remotion |
| [#134 SaaS launch video — @aschapmann](https://www.prompt-motion.com/aschapmann-131210) | 996 | 一整句长句 | Remotion |
| [#8 Engraving-style Claude ad — @LexnLin](https://www.prompt-motion.com/lexnlin-038035) | 994 | 编号 brief + 参考视频 | — |
| [#41 Motion techniques showreel — @lukasersil](https://www.prompt-motion.com/lukasersil-0ed38e) | 744 | 一段话（技法清单） | — |
| [#77 Sahi trading terminal reveal — @dale_vaz](https://www.prompt-motion.com/dale-vaz-cc612a) | 631 | 散文分镜 | JavaScript |
| [#32 mdfor.dev product intro video — @HO_BA](https://www.prompt-motion.com/ho-ba-f3f0e9) | 597 | 一句话 + 追加要求 | — |
| [#137 Reflex brand motion reel — @reflex_cloud](https://www.prompt-motion.com/reflex-cloud-72ffe5) | 544 | 一段话 | — |
| [#85 Visual guides library launch — @techyoutbe](https://www.prompt-motion.com/techyoutbe-945b56) | 519 | 一段话 | — |
| [#197 Sketchbook animals come alive — @abderrahmen_g](https://www.prompt-motion.com/abderrahmen-g-9e8ed0) | 502 | 一段话 + 素材目录 | JavaScript |
