# Claude Motion Playbook

**Claude Opus 5.5 做了 233 支动效视频，我们一条条拆完，看动效 prompt 到底该怎么写。**

[prompt-motion.com](https://www.prompt-motion.com/)（策展人 [@p4nthera_](https://x.com/p4nthera_)）收的都是 Claude Opus 5.5 用代码做出来的动效视频，用的有 HTML + GSAP、Remotion、HyperFrames、Three.js、Canvas 等，每条都附上背后的 prompt 或 skill。
我们把 2026-10-09 快照里的 233 条全部过了一遍：每个 prompt 都读了，每支视频都抽了样（6 帧联系表 + `ffprobe`），逐条分类，再跑统计。每份文档发布前都另找了一个审稿人核对过。

这个仓库放的是我们的笔记。**不存视频、不存截帧、不存完整 prompt**，每一条都链回原作者。

[English](README.md)

## 我们发现了什么

- **一句 prompt 撑起半个画廊。**「make a dynamic 15-second motion graphics video … like it's your showreel … go all out」这句一字不差出现了 **33 次，来自 33 个账号**。算上改写和插了品牌名的版本，这一家族占了 **230 条 prompt 里的 102 条（44%）**。→ [prompt 写法](docs/zh/prompt-patterns.md)
- **prompt 写得长，画面并不更好看。** 结构化长 prompt 的视觉冲击均分 3.94，一句话 prompt 3.88（n = 17 对 154，p ≈ 0.87）；只看画面的盲评下是 3.35 对 3.55（p ≈ 0.38）。长 prompt 换来的是**可控**：照它做出来的视频 76% 是产品片或品牌片，一句话 prompt 只有 38%。
- **「go all out」影响的是评分员，不是片子。** 评分员能看到 prompt 时，带加码词的 prompt 平均高 0.33 分（n = 95 对 135，p ≈ 0.001）。我们把 233 支片**盲评**重打了一遍，只看画面、不看 prompt：差距缩到 +0.08（95% 置信区间 −0.11 到 +0.27，p ≈ 0.47），15 个 prompt 特征没有一个还显著。看起来是这句话影响了读到它的评分员，而不是视频本身。→ [盲评重打](docs/zh/prompt-patterns.md#27-盲评重打哪些结论还站得住)
- **同一句 prompt，出来的片子差很多。** 用那句原版 prompt 做出的 31 支不同视频分属 4 个类别，盲评分数从 2 到 5 都有（标准差 0.68，接近全库的 0.73）。既然没有哪种措辞在盲评下还管用，多跑几版、挑最好的，才是你真正能控制的。
- **好的长 prompt 都是一个骨架。** `<inputs>` `<direction>` `<structure>` `<build>` `<gotchas>` `<start>`，6 个账号的 10 条在用。最值钱的部分是 gotchas（踩坑清单）、确定性渲染规则，以及渲染前后的检查关口。→ [模板](templates/saas-launch-film.hyperframes.md)
- **137 招可复用的手法**，分为镜头、转场、文字、UI 演示、3D、数据可视化、粒子、音乐卡点、渲染质检九组，每招都附例子链接。→ [招式库](docs/zh/techniques.md)
- **这是一股浪潮，不止一个网站。** 我们整理了 **100 个**相关项目（画廊、清单、框架官方展示页和 skill 目录），最大的 [Oneshotted](https://oneshotted.io/) 收了 6,164 条。→ [生态地图](docs/zh/ecosystem.md)

## 里面有什么

| | 中文 | English | 内容 |
|---|---|---|---|
| 必看清单 | [top-picks](docs/zh/top-picks.md) | [en](docs/top-picks.md) | 先看 6 条、全库 Top 20、按用途和类别的推荐、数据概览 |
| prompt 写法 | [prompt-patterns](docs/zh/prompt-patterns.md) | [en](docs/prompt-patterns.md) | prompt 怎么写、什么和质量有关，附统计 |
| 招式库 | [techniques](docs/zh/techniques.md) | [en](docs/techniques.md) | 137 招分 9 组，每招附 HTML + GSAP / HyperFrames 实现提示和例子 |
| Skill 评测 | [skills](docs/zh/skills.md) | [en](docs/skills.md) | 画廊里出现的 13 个开源动效 skill |
| 生态地图 | [ecosystem](docs/zh/ecosystem.md) | [en](docs/ecosystem.md) | 100 个同类合集、清单、官方展示页和 skill 目录 |
| 模板 | [saas-launch-film.hyperframes.md](templates/saas-launch-film.hyperframes.md) | （中英合一） | 我们自己写的 45–60 秒 SaaS 发布片 HyperFrames prompt，外加 3 个一句话变体 |
| 数据表 | [catalog.csv](catalog/catalog.csv) · [catalog.json](catalog/catalog.json) | | 233 条的作者、日期、技术栈、时长、画幅、类别、手法、链接 |
| 数据集 | [🤗 PHY041/claude-motion-playbook](https://huggingface.co/datasets/PHY041/claude-motion-playbook) | | 同一份数据表放在 Hugging Face 上：`load_dataset("PHY041/claude-motion-playbook")` |

**没时间？先看这 6 条**（加起来 5 分 44 秒）：[#5](https://www.prompt-motion.com/twoclipping-221cab) · [#8](https://www.prompt-motion.com/lexnlin-038035) · [#126](https://www.prompt-motion.com/ik-builds-b8bdcf) · [#36](https://www.prompt-motion.com/ismailfahmi-557268) · [#64](https://www.prompt-motion.com/sayan-shanky-f850d8) · [#29](https://www.prompt-motion.com/kloss-xyz-fe0c31)。[为什么是这 6 条 →](docs/zh/top-picks.md#1-从这里开始10-分钟看-6-条)

## 方法

- **数据**：prompt-motion.com 截至 2026-10-09 的全部 233 条公开条目，发布于 2026-09-23 到 10-08，来自 216 个账号。文中的 `#N` 都是 catalog 里的 `id`。
- **怎么看片**：每支视频抽一张 6 帧联系表，再用 `ffprobe` 读时长、帧率和有没有声音。这是抽样，不是完整观看；落在抽样帧之间的动作，回到视频里抽查过。
- **怎么打分**：AI 评分员按 1–5 分给视觉冲击和 prompt 质量打分。换一个新评分员按原指令重打 50 条，加权 κ 是 0.74；把 233 条全部盲评重打（只看画面，不给 prompt、标题和作者），和原评分的一致性只有 κ 0.51，平均低 0.33 分，说明看到 prompt 会把分数抬高。所以只公布汇总结果，不公布单条分数；均分差在 0.3 以内的都当噪声看。
- **统计**：置换检验（20,000 次打乱），15 个 prompt 特征做 Bonferroni 校正。文档里每个数都标了样本量 n。
- **核对**：每份文档由另一个审稿人回到原始文件，逐条核对数字、引文和链接，错的当场改掉。
- **局限**：画廊是精选的，有幸存者偏差；大多数 prompt 很短；只有 56 条写明了技术栈。

## 版权与致谢

- 视频和 prompt 版权都归原作者。catalog 每一行都链到作者原帖和 prompt-motion.com 的条目页，看视频、读完整 prompt 请去那里。
- 策展归功于 [@p4nthera_](https://x.com/p4nthera_) 和 [prompt-motion.com](https://www.prompt-motion.com/)。本项目独立制作，和 prompt-motion.com、各位作者、Anthropic、HeyGen 都没有关联。
- 文中引用的 prompt 都是短句（≤ 25 个英文词），注明作者并附链接。
- 如果你是作者，想改描述或撤下自己的条目，请[开 issue](https://github.com/PHY041/claude-motion-playbook/issues)，我们会处理。

## 许可

- 我们写的内容（`docs/`、README）和 `catalog/` 里我们加的分类字段：[CC BY 4.0](LICENSE)。
- `templates/`：[CC0 1.0](templates/LICENSE)，随便抄、随便改，不用署名。
- 视频、prompt 和其他第三方内容**不在**许可范围内，版权仍归各自作者。

---

作者 [Haoyang Pang](https://github.com/PHY041)（[Canlah AI](https://canlah.ai)）。如果帮你省了一个下午，点个 ⭐ 让更多人看到。
