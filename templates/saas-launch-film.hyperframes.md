# SaaS launch film (45–60 s): a HyperFrames prompt template

This is a reusable prompt for a 45–60 second product launch film built in HyperFrames: HTML compositions, each driven by one paused GSAP timeline, rendered deterministically frame by frame. It applies the patterns measured in [`docs/prompt-patterns.md`](../docs/prompt-patterns.md) and was written from scratch. It doesn't reuse any creator's prompt text.

Fill in the `{{PLACEHOLDERS}}`, or leave them blank and let the model ask.

**What the data says this template will and won't do.** In the gallery, long structured specs didn't score higher on visual wow than one-liners (3.94 vs 3.88 with the grader reading the prompt, 3.35 vs 3.55 graded blind from frames only; neither gap is significant). Where they did differ is in how often the result was the film you asked for: 76% of structured-spec outputs were product or brand films, against 38% of one-liners. Use the one-liners at the bottom to find a direction, then use this template to make the real film.

## How to use it

1. **Explore first.** Run one of the [one-liner variants](#three-one-liners-for-quick-exploration) inside your product repo, 2–3 times each. The same prompt can swing a point or two between runs, so don't judge a direction on a single video.
2. **Fill the inputs.** Fill the placeholders below, or paste the prompt as-is and answer the model's questions.
3. **Paste the full prompt** into a coding agent running in the product repo, with the HyperFrames CLI available (`npx hyperframes`).
4. **Approve twice:** once on the cue sheet and stills, and again on the draft before the final render.

| Placeholder | What to put there |
|---|---|
| `{{PRODUCT}}` | Product name and its one-line promise |
| `{{AUDIENCE}}` | Who buys it, described the way they describe themselves |
| `{{PROBLEM}}` | The moment in their day when the pain shows up, in one sentence |
| `{{PROOF}}` | One checkable fact: a sourced metric, a quote you have permission to use, or a before/after inside the product |
| `{{SOURCE}}` | Repo paths, design tokens and URLs holding the real UI, copy, fonts, colours and logo |
| `{{UI_MOMENTS}}` | Three screens or interactions that show the product working |
| `{{CTA}}` | The last line on screen, plus the URL |
| `{{DURATION}}` | 45–60 seconds (default 50) |

## The prompt

```text
You are directing and building a {{DURATION}}-second launch film for {{PRODUCT}} in HyperFrames:
HTML compositions, each driven by one paused GSAP timeline, rendered frame by frame.
The film has one job. A {{AUDIENCE}} who has never heard of {{PRODUCT}} should understand, with the
sound off, what problem it removes and why they should try it.

<inputs>
Ask me for everything below in a single message. For anything I leave blank, use the default in
brackets and list your assumptions before you start.
- PRODUCT: name and one-line promise. [take them from the README or landing page in SOURCE]
- AUDIENCE: who buys it, in their own words. [infer from SOURCE, then ask me to confirm]
- PROBLEM: the moment the pain shows up in their day, in one sentence. [no default; ask]
- PROOF: one fact a sceptic could check: a metric with its source, a customer quote I have
  permission to use, or a before/after inside the product. [none: show the solved state in the UI]
- SOURCE: the repo, design tokens and URLs that hold the real UI, copy, fonts, colours and logo.
  [this repo]
- UI_MOMENTS: three screens or interactions that show the product doing its job. [pick from SOURCE]
- CTA: the closing line and the URL. [the main URL in SOURCE]
- FORMAT: [1920x1080 at 30 fps. A vertical version is laid out again later, never cropped.]
- DURATION: [50 s, within 45–60]
- MUSIC: a track I hold a licence for, or an original score generated in code. [generate one]
- BANNED_WORDS: words the brand never puts on screen. [none]
</inputs>

<direction>
Look: use the brand's own tokens from SOURCE, meaning one background, one ink colour and one accent.
The accent goes only where the viewer's eye should go. Use the typefaces from SOURCE with a system
fallback, set large, with few words per frame.
Through-line: pick one object from the real UI (the cursor, a status chip, a card or the logo mark)
and carry it through every section. Its role changes as the story moves.
Transitions: every change of scene comes from something already on screen. An element grows,
splits, docks or turns into the next scene. Never jump to an unrelated layout.
Reading beats rhythm: headlines are 8 words or fewer, with no more than two text blocks on screen
at once. Each headline stays up as long as it takes to read aloud calmly, plus half a second.
Camera: one deliberate move per shot, never two at once. Each shot starts at the scale where the
previous one ended.
Leave out: corner HUD (timecodes, frame counters, BPM readouts), particle bursts, lens flares,
glitch or RGB split, camera shake, animation jargon on screen, flat screenshots sliding around,
holds over one second (the end card excepted), and any number, logo, customer or feature that
isn't in SOURCE or PROOF.
</direction>

<structure>
The times below are for 50 s; scale them in proportion for 45–60 s. Snap a cut to the nearest beat
only when that doesn't cut a headline short.
1. Hook (0–4 s): the PROBLEM moment, seen from the audience's side and already in motion. No logo yet.
2. Cost (4–12 s): what the problem costs them in time, mistakes or money, shown as something
   happening on screen rather than as a slogan. One line of copy at most.
3. Turn (12–16 s): the through-line object appears inside the problem and the product UI grows out
   of it. The product name appears for the first time here.
4. How it works (16–36 s): the three UI_MOMENTS, one per shot, about 6 s each. Rebuild each from
   SOURCE and drive it with a cursor or real input. End every shot on the result of the action.
5. Proof (36–44 s): state PROOF once. If it's a number, show its source on screen. If there's no
   PROOF, go back to the hook's framing and show the same moment solved.
6. End card (44–50 s): the logo lockup from SOURCE, the one-line promise and the CTA. Hold still
   for at least 2 s.
</structure>

<build>
1. Project: a standalone index.html whose root is
   <div id="root" data-composition-id="launch" data-width="1920" data-height="1080"
        data-duration="{{DURATION}}">
   Put each section in its own sub-composition file in compositions/, wrapped in <template>, and
   mount it from index.html with data-composition-src, data-start, data-duration and class="clip".
2. Timelines: exactly one gsap.timeline({ paused: true }) per composition. Build it after
   document.fonts.ready and register it at window.__timelines["<id>"], where <id> matches that
   composition's data-composition-id. Render length comes from the root's data-duration.
3. Seek-safe: any frame must come out the same no matter what order frames are rendered in.
   - Set start states inside the timeline, with fromTo or a set at time 0.
   - No CSS transitions or keyframe animations, no setTimeout, setInterval or
     requestAnimationFrame loops, no Date.now(), no unseeded Math.random().
   - Never tween display, visibility or autoAlpha on a .clip element; animate a child instead.
   - Never give an element a CSS transform and a GSAP tween on the same property.
4. One source of truth: put every section time and cue point in cues.js, and every on-screen string
   in copy.json, drawn from SOURCE or PROOF. The sections themselves contain no hard-coded times
   or strings.
5. Rebuild, don't paste: recreate the UI as HTML/CSS from SOURCE components and tokens, split into
   parts that can move on their own. No full-screen screenshots.
6. Search before you build: for every named effect, run
   npx hyperframes catalog --query "<the effect in plain words>"
   and use a registry block if one fits.
7. Motion blur: use the registry motion-blur component (data-hf-motion-blur) on two or three fast,
   snapping moves only. Never on text the viewer is reading.
8. Audio:
   - Use <audio id="music" data-timeline-role="music"> and run npx hyperframes beats for the
     beat grid.
   - Give each on-screen event one short, quiet sound, timed so its loudest point (not the start
     of the file) hits the event. Keep silence in between.
   - Log every audio source and its licence in AUDIO.md.
   - Aim for about -14 LUFS integrated, and measure it again after the final encode.
9. Verify before you show me anything:
   a. npx hyperframes check must report 0 findings. Fix lint errors first: while lint fails, the
      layout and contrast audits don't run.
   b. Run npx hyperframes snapshot --at <every cut, every headline midpoint> and review each still:
      one idea, readable on a phone, nothing clipped or overlapping.
   c. Render a draft. Decode frames from the MP4 with ffmpeg, then scan for one-frame jumps,
      frozen stretches (freezedetect) and black gaps (blackdetect). Check the loudness.
   d. Ask a separate reviewer, meaning a new agent or session that didn't write the code, to watch
      the draft against this brief and list problems. Fix them before asking me for approval.
</build>

<gotchas>
- Web fonts change text width, so measure and fit text only after the fonts have loaded. If the
  product name is long, scale the whole lockup rather than letting it wrap.
- When one line of copy replaces another in the same spot, let the old line finish leaving before
  the new one starts arriving.
- A colour wipe that covers the frame should travel past all four corners and take several frames.
  A one-frame swap reads as a glitch.
- A card the same colour as its background vanishes. Give it a hairline border or a soft shadow.
- Opacity or filters on a preserve-3d element flatten it. Fade a wrapper around it instead.
- Don't set will-change on elements the camera zooms; their text renders soft.
- Typing effects: lay out the finished text first and reveal it character by character, so the
  caret never jumps to a new line mid-word.
- An <audio> element without an id is left out of the mix, and the render comes out silent.
- Strong blur can erase thin strokes. Check a still at the blur's peak before you keep it.
</gotchas>

<start>
1. Ask for the inputs in one message, then restate the story in six lines, one per section.
2. Show me the cue sheet: for each section, its time, the on-screen copy, and which element carries
   over into the next section.
3. Show me five stills from snapshot: the hook, the cost, the turn, the middle UI moment and the
   end card.
Wait for my approval before you build all the sections, and wait again before the final render.
</start>
```

### Why each section is there

| Section | What it does | Evidence from the gallery |
|---|---|---|
| `<inputs>` | Makes the prompt reusable, and makes the model say what it assumed | Four long specs ask for inputs and fall back to defaults |
| `<direction>` | Fixes the taste decisions the model would otherwise make for you | One-liner showreels drift to HUD chrome (74% of verbatim videos) and particles (55%) |
| `<structure>` | Problem first, product second, one proof, then a still end card | Short briefs with a written story arc stay on topic; reading time is protected explicitly |
| `<build>` | Deterministic, seekable rendering and one source of truth for timing and copy | 13 prompts require frames that are pure functions of time |
| `<gotchas>` | Failure modes that are cheap to prevent and expensive to find | The most specific, least obvious part of every long spec |
| `<start>` | Approval before the expensive render | 9 specs gate the full build on a beat map, a storyboard or stills |

## Three one-liners for quick exploration

Run each one inside the product repo, 2–3 times, and keep the best take: the spread between runs of one prompt is bigger than any wording effect we could measure.

- **"Go all out" stays, but not because it helps.** It's the gallery's most common closing line and it's harmless. Graders who could read the prompt scored pressure phrases 0.33 higher, but a blind re-grade from frames only found no effect (+0.08, p ≈ 0.47; see [section 2.7](../docs/prompt-patterns.md#27-blind-re-grade-what-survives)). Keep it or cut it; don't expect it to improve the film.
- **No "showreel" framing.** It pulls the model toward HUD-heavy technique montages rather than product films.

**1. Brand slot, in-repo**

```text
Working in this repo, make a 45-second HyperFrames launch film for {{PRODUCT}} (HTML plus one paused, seek-safe GSAP timeline per composition). Study the codebase and the landing page before designing, and build only from the real interface, copy, colours and logo you find there. Open on {{PROBLEM}} and close on {{CTA}}. Go all out.
```

Use it to see what the model makes of your product with almost no direction. Adding a brand slot to the gallery's one-liner cost nothing measurable on the wow score (3.98 vs 4.02 sighted, 3.55 vs 3.62 blind), and 70% of those outputs were product films, against 16% without one.

**2. One object carries the film**

```text
Build a 50-second HyperFrames launch film for {{PRODUCT}} in which one element taken from its real UI ({{THROUGH_LINE}}) is present in every shot and changes its job as the story moves: it marks the problem, turns into the product, carries the proof and lands on the logo. Each transition grows out of something already on screen, and every headline stays up long enough to read. No HUD, no particles, no made-up numbers. Go all out.
```

Use it to test a visual idea quickly. A single continuity rule gives the model most of what a full shot list would.

**3. The whole story in one paragraph**

```text
Make a 60-second launch film for {{PRODUCT}} with HyperFrames, entirely in code. Start by reading {{SOURCE}} for the real copy, colours, fonts and logo. Tell it in six beats: the moment {{AUDIENCE}} runs into {{PROBLEM}}, what that costs them, {{PRODUCT}} stepping in, three real UI moments, {{PROOF}}, and an end card with {{CTA}}. Keep one idea per shot, give every headline time to be read at a calm pace, and play a short sound only when something lands, quiet in between. Before showing me anything, run npx hyperframes check, look at a still from every cut, and fix any overlap, cut-off text or headline that leaves too soon. Go all out.
```

Use it to try a new story structure without writing the full spec. It brings the story arc, the reading pace and a self-check along without any tags.

---

## 中文说明

这是一份可复用的 prompt 模板，用来在 HyperFrames 里做 45–60 秒的 SaaS 产品发布片。HyperFrames 的做法是：用 HTML 搭合成，每个合成由一条暂停的 GSAP 时间线驱动，再逐帧做确定性渲染。模板依据的是 [`docs/zh/prompt-patterns.md`](../docs/zh/prompt-patterns.md) 里的统计结论，由我们从零写成，没有照搬任何作者的 prompt 原文。

填好 prompt 里的 `{{PLACEHOLDERS}}` 占位符，或者留空，让模型来问你。

**数据说明这份模板能做什么、不能做什么。** 在画廊数据里，长的结构化 spec 的视觉冲击分并不比一句话 prompt 高（评分员看得到 prompt 时 3.94 对 3.88，只看画面盲评时 3.35 对 3.55，两个差距都不显著）。差别在于成片是不是你要的那支片子：结构化 spec 的成片有 76% 是产品片或品牌片，一句话只有 38%。所以先用文末的一句话变体找方向，方向定了再用这份模板做正式片。

### 怎么用

1. **先探索。** 在产品仓库里跑[一句话变体](#三个一句话变体)，每个跑 2–3 次。同一条 prompt 两次运行之间能差一两分，只看一支片子不要下结论。
2. **填输入。** 按下表填好占位符，或者原样粘贴，再回答模型的提问。
3. **粘贴运行。** 把完整 prompt 粘贴给一个在产品仓库里运行、能用 HyperFrames CLI（`npx hyperframes`）的 coding agent。
4. **确认两次。** 先确认分镜表和静帧，再确认草稿，然后才做最终渲染。

| 占位符 | 填什么 |
|---|---|
| `{{PRODUCT}}` | 产品名和一句话卖点 |
| `{{AUDIENCE}}` | 谁会买，用他们形容自己的话来写 |
| `{{PROBLEM}}` | 痛点在他们一天里冒出来的那个时刻，一句话 |
| `{{PROOF}}` | 一条能核实的事实：有出处的指标、获准使用的引语，或产品里的前后对比 |
| `{{SOURCE}}` | 存放真实界面、文案、字体、配色和 logo 的仓库路径、设计 token 和网址 |
| `{{UI_MOMENTS}}` | 三个能看出产品在干活的界面或交互 |
| `{{CTA}}` | 屏幕上的最后一句话，加上网址 |
| `{{DURATION}}` | 45–60 秒（默认 50） |

prompt 正文见上方的 [The prompt](#the-prompt)，保持英文原样，直接粘贴即可。

### 每一段为什么这样写

| 段落 | 作用 | 画廊里的依据 |
|---|---|---|
| `<inputs>` | 让 prompt 可以反复套用，并让模型说清自己做了哪些假设 | 4 条长 spec 先问输入，没给的用默认值 |
| `<direction>` | 替模型先把品味上的决定做掉 | 一句话 showreel 容易滑向角落 HUD（逐字原版视频的 74%）和粒子（55%） |
| `<structure>` | 先讲问题，再讲产品，给一个证据，最后是一张静止的尾卡 | 写明故事弧的短 brief 不容易跑题；阅读时间单独写明、受保护 |
| `<build>` | 确定性、可任意跳帧的渲染；时间和文案各只有一个出处 | 13 条 prompt 要求每一帧都是时间的纯函数 |
| `<gotchas>` | 防起来便宜、查起来贵的坑 | 每份长 spec 里最具体、也最不显眼的部分 |
| `<start>` | 花大钱渲染之前先确认 | 9 条 spec 要求先交节拍表、分镜或静帧，确认后才全量制作 |

**英文 prompt 各段要点：**

- **`<inputs>`**
  - 一次问齐所有输入；没给的用默认值，并先列出做了哪些假设。
  - PROOF 只接受能核实的事实；没有的话，就在界面里展示「问题解决之后的样子」，不编数字。
  - 竖版要重新排版，不能直接从横版裁。
- **`<direction>`**
  - 明确排除角落 HUD、粒子、镜头光晕、故障效果等常见套路。
  - 只用一个强调色，并选一个真实界面里的物件贯穿全片。
  - 每次转场都从画面上已有的东西长出来。
  - 标题不超过 8 个词，停留时间够平静地念一遍、再多 0.5 秒。读得完比卡准拍子更重要。
- **`<structure>`**
  - 六段依次是：开场钩子、问题的代价、转折、三个界面时刻、一个证据、静止的尾卡。
  - 时间按 50 秒写，45–60 秒按比例缩放。
  - 切点吸附到节拍上的前提是不缩短标题的阅读时间。
- **`<build>`**（照 HyperFrames 的约定写，不管按什么顺序渲染，每一帧都一样）
  - 每个合成只有一条暂停的时间线，注册的 id 和 `data-composition-id` 一致；初始状态在时间线里设好。
  - 不用 CSS 过渡、计时器和没有种子的随机数；不对 `.clip` 本身做可见性动画。
  - 时间点和文案各放一个文件。
  - 界面用真实组件重建，不贴整屏截图。
  - 先查 registry 再手写效果；运动模糊只加在两三个快速动作上。
  - 音效按最响的那一刻对位，响度在编码后复测。
  - 最后一步是检查：`check` 零问题、关键帧快照、从 MP4 解码出帧扫描跳帧和冻帧，再请一个没写过代码的新 agent 或新会话复审。
- **`<gotchas>`**
  - 字体加载完再量文字，长名字整体缩放。
  - 换字时，旧的先走完、新的再进来。
  - 铺满全屏的色块要越过四角，并且用上几帧时间。
  - 同色卡片加细边；`preserve-3d` 元素改为淡化外层；被镜头缩放的元素不加 `will-change`。
  - 打字效果先排好最终文本再逐字显示；每个 `<audio>` 都要有 id，否则渲染没有声音。
  - 强模糊可能把细线条抹掉，保留之前先看一张模糊最强时的静帧。
- **`<start>`**：先问输入并用六行复述故事，再交分镜表和五张静帧。确认之后才全量制作，草稿确认之后才最终渲染。

### 三个一句话变体

prompt 原文见上方的 [Three one-liners for quick exploration](#three-one-liners-for-quick-exploration)，每个都在产品仓库里跑 2–3 次，留最好的一版：同一句 prompt 多次运行之间的差距，比我们能测到的任何措辞效应都大。

- **保留 "go all out"，但不是因为它管用。** 这是画廊里最常见的结尾，留着无妨。能看到 prompt 的评分员给加码词平均高 0.33 分，但只看画面的盲评重打没有发现任何效果（+0.08，p ≈ 0.47，见[第 2.7 节](../docs/zh/prompt-patterns.md#27-盲评重打哪些结论还站得住)）。留不留都行，别指望它让片子变好。
- **去掉 showreel 体裁。** 它会把模型带向 HUD 堆满的技法蒙太奇，而不是产品片。
- **变体 1（品牌槽 + 在仓库里跑）。** 用最少的指导，看看模型怎么理解你的产品。数据里加品牌槽几乎不降视觉冲击分（明评 3.98 对 4.02，盲评 3.55 对 3.62），产品片占比却从 16% 升到 70%。
- **变体 2（一个物件贯穿全片）。** 适合快速试一个视觉概念。一条连续性规则，就能给模型一整张分镜表能给的大部分东西。
- **变体 3（一段话讲完故事）。** 适合不写完整 spec 就试一种新的叙事结构。不用标签，也带上了故事弧、阅读节奏和自查。
