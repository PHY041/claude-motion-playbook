# Top picks: what to watch first

A guided path through the 233 motion videos collected on [prompt-motion.com](https://www.prompt-motion.com/) (curated by [@p4nthera_](https://x.com/p4nthera_)), snapshot of 2026-10-09. Every video was made by Claude Opus 5.5 writing code. Each pick links to the creator's own entry page, where you can watch the video and read the full prompt. `#N` is the entry's `id` in [`catalog/catalog.json`](../catalog/catalog.json).

[简体中文版](zh/top-picks.md)

## TL;DR

- **233 entries, 228 distinct videos, 216 posting accounts.** Five entries are reposts of an earlier video; they are listed [below](#reposts).
- **Product launch films dominate:** 70 of 233 entries (30%), followed by showreels (44, 19%) and explainers (24, 10%).
- **Short by default:** median length 20.1 s, and 84 entries run 14.5–15.6 s. The "15-second motion designer showreel" is the most copied brief; 87 prompts contain the phrase "go all out".
- **192 of 233 are 16:9, and 200 (86%) have audible sound.**
- **Only 56 of 233 entries state their stack.** Among those, Remotion (13) and HyperFrames (10) lead. Graders read about half of all entries (116) as plain web 2D: HTML/CSS/JS, Canvas or SVG.
- **No time? Six videos, under 6 minutes of runtime:** [#5](https://www.prompt-motion.com/twoclipping-221cab), [#8](https://www.prompt-motion.com/lexnlin-038035), [#126](https://www.prompt-motion.com/ik-builds-b8bdcf), [#36](https://www.prompt-motion.com/ismailfahmi-557268), [#64](https://www.prompt-motion.com/sayan-shanky-f850d8), [#29](https://www.prompt-motion.com/kloss-xyz-fe0c31).
- **How the picks were made:** AI graders gave a first pass, then we re-ranked about 90 entries by viewing their 6-frame contact sheets. We do not publish per-entry scores (see [Method & caveats](#6-method--caveats)).

## Contents

1. [Start here: 6 videos in 10 minutes](#1-start-here-6-videos-in-10-minutes)
2. [The dataset at a glance](#2-the-dataset-at-a-glance)
3. [Top 20 overall](#3-top-20-overall)
4. [Best picks by use case](#4-best-picks-by-use-case)
5. [Best 1–2 per category](#5-best-12-per-category)
6. [Method & caveats](#6-method--caveats)

---

## 1. Start here: 6 videos in 10 minutes

Total runtime is 5 min 44 s, which leaves time to rewatch the two you like most.

1. [#5](https://www.prompt-motion.com/twoclipping-221cab) · **Photo print app launch film** · @twoclipping · 29s · square — The craft benchmark. Every scene is built out of the previous one in a single take, from a fully structured prompt you can study line by line.
2. [#8](https://www.prompt-motion.com/lexnlin-038035) · **Engraving-style Claude ad** · @LexnLin · 15s · vertical — How to carry a film with one element: a coral dot becomes the question mark, the pen tip, the sunflower centre and finally the logo.
3. [#126](https://www.prompt-motion.com/ik-builds-b8bdcf) · **Paper-style product launch film** · @ik_builds · 15s — A product film whose prompt is written as a reusable template (placeholders for product, audience and banned words), built with HyperFrames + GSAP.
4. [#36](https://www.prompt-motion.com/ismailfahmi-557268) · **Drone Emprit showreel** · @ismailfahmi · 15s — The best-looking data piece in the set: one particle system turns millions of mentions into clusters and a single spike.
5. [#64](https://www.prompt-motion.com/sayan-shanky-f850d8) · **AI data centre 3D tour** · @Sayan_shanky · 1:38 — What a one-sentence prompt can return: an 11-chapter 3D tour of a data centre.
6. [#29](https://www.prompt-motion.com/kloss-xyz-fe0c31) · **History of AI timeline** · @kloss_xyz · 2:52 — Long form that holds: almost three minutes, with a purpose-built visual for every chapter.

---

## 2. The dataset at a glance

All numbers are computed from [`catalog/catalog.json`](../catalog/catalog.json) and the downloaded video files (duration, resolution, frame rate and audio come from `ffprobe`).

### Basics

| Item | Count |
|---|---|
| Entries | 233 (230 prompt entries, 3 skill entries: [#16](https://www.prompt-motion.com/lexnlin-6161a6), [#23](https://www.prompt-motion.com/anthonyriera-9b1b2a), [#70](https://www.prompt-motion.com/jake11moran-a269c4)) |
| Distinct videos | 228 (5 entries repost an earlier video) |
| Posting accounts | 216 |
| Posted | 2026-09-23 to 2026-10-08 (220 in September, 13 in October) |
| Total runtime | 155.5 minutes |
| Entries linking a skill repo | 4 ([#16](https://www.prompt-motion.com/lexnlin-6161a6), [#23](https://www.prompt-motion.com/anthonyriera-9b1b2a), [#70](https://www.prompt-motion.com/jake11moran-a269c4), [#147](https://www.prompt-motion.com/buildfastwithai-53234e)) |

### By category

Categories were assigned by the AI graders, one per entry.

| Category | Entries | Share | Median length | With audio track |
|---|---|---|---|---|
| Product launch film `product-launch-film` | 70 | 30% | 19.3 s | 64 |
| Showreel / montage `showreel-montage` | 44 | 19% | 15.1 s | 43 |
| Explainer / data viz `explainer-data-viz` | 24 | 10% | 58.6 s | 17 |
| SaaS UI walkthrough `saas-ui-walkthrough` | 17 | 7% | 30.0 s | 14 |
| Kinetic typography `kinetic-typography` | 16 | 7% | 15.1 s | 14 |
| Character / story animation `character-story-animation` | 16 | 7% | 43.9 s | 14 |
| Vertical social ad `social-ad-vertical` | 10 | 4% | 29.1 s | 8 |
| 3D world / scene `3d-world-scene` | 8 | 3% | 38.6 s | 7 |
| Personal intro reel `personal-intro-reel` | 8 | 3% | 29.6 s | 7 |
| Other `other` | 8 | 3% | 22.5 s | 2 |
| Generative / abstract `generative-abstract` | 6 | 3% | 30.5 s | 6 |
| Logo / brand ident `logo-brand-ident` | 4 | 2% | 16.6 s | 4 |
| Tool / skill demo `meta-tool-demo` | 2 | 1% | 50.6 s | 2 |

Two of the audio tracks counted here are silent (peak −91 dB): [#55](https://www.prompt-motion.com/0xnfrith-5be616) and [#123](https://www.prompt-motion.com/buildfastwithai-ed9447).

### Stack: stated vs inferred

**Stated by the creator** (`stack_stated`): 56 of 233 entries (24%). The other 177 leave it blank.

| Stated stack | Entries |
|---|---|
| Remotion (incl. 1 "Remotion, React") | 13 |
| HyperFrames (incl. 1 "HyperFrames + GSAP") | 10 |
| HTML | 9 |
| HTML + Playwright frame capture (4 spellings) | 6 |
| Three.js | 5 |
| JavaScript | 5 |
| Python (incl. 1 "Python + ffmpeg") | 2 |
| One each: OpenEdit, Manim + edge-tts, SVG/Canvas, WebGL2 + Canvas 2D + Web Audio, Blender, Canvas | 6 |

**Inferred by the graders** (`stack_inferred`, all 233). Graders guessed from the frames and the prompt; none of these were verified. We bucketed their notes by keyword, first match wins, in this order: Remotion → HyperFrames → other tools → frame capture → 3D → web 2D.

| Inferred stack family | Entries |
|---|---|
| Web 2D: HTML / CSS / JS, Canvas, SVG, GSAP | 116 |
| Three.js / WebGL / shaders (incl. "Canvas or WebGL" guesses) | 42 |
| No usable signal | 26 |
| Other tools: Manim, Python, Blender, OpenEdit, skill pipelines, AI-generated imagery | 15 |
| Remotion | 13 |
| HTML + deterministic frame capture (Playwright and/or `seek(t)`) | 11 |
| HyperFrames | 10 |

### Duration

| Length | Entries |
|---|---|
| ≤ 12 s | 10 |
| 12–20 s | 103 |
| 20–35 s | 54 |
| 35–60 s | 38 |
| 1–2 min | 17 |
| > 2 min | 11 |

- Median 20.1 s, mean 40.1 s. Shortest 10.0 s (8 entries); longest 7:37 ([#27 Derivative concept explainer — @LinearUncle](https://www.prompt-motion.com/linearuncle-5d2bae)).
- 84 entries (36%) run 14.5–15.6 s. The 15-second showreel is the single most common format.
- 143 entries run 30.0 s or less; 159 if you include the "30-second" videos that run to 30.5 s.

### Aspect ratio and frame rate

| Aspect | Entries | Detail |
|---|---|---|
| 16:9 | 192 | 149 at 1920×1080, 37 at 1280×720, 6 at near-16:9 sizes (e.g. 1920×1078, 854×480) |
| 9:16 | 16 | 11 at 1080×1920, 5 at 720×1280 |
| 1:1 | 14 | 9 at 1080², 4 at 1440², 1 at 720² |
| 4:5 | 2 | [#135](https://www.prompt-motion.com/marklaunches-3b9492), [#219](https://www.prompt-motion.com/anas0ra-e57aea) |
| Taller than 9:16 | 1 | [#171](https://www.prompt-motion.com/francoxavier33-d2dfd2) (886×1920) |
| Other | 8 | 3 screen-recording sizes (1920×982 / 972), cinemascope 1920×816 ([#233](https://www.prompt-motion.com/kamstudiolabs-0b0824)), 1920×1292, 1408×1080, 1280×848, 1152×720 |

Frame rate: 131 at 60 fps (2 of them 59.94), 93 at 30 fps, 5 at 24 fps (1 of them 23.98), and one each at 12, 15, 25 and 53.7 fps.

### Sound

- 202 of 233 videos have an audio track; 31 have none.
- Two of those tracks are silent (peak −91 dB, measured with ffmpeg `volumedetect`).
- **200 videos (86%) have audible sound.** We counted presence only and did not rate the sound.

### Prompt style

| Prompt style (grader label) | Entries |
|---|---|
| One-liner | 154 (66%) |
| Short brief | 56 (24%) |
| Structured spec (sections, banned list, beat map, QA) | 17 (7%) |
| Skill-driven | 6 (3%) |

87 prompts contain the phrase "go all out" (for example [#1](https://www.prompt-motion.com/stephanlivera-df17a2)), and 84 frame the video as a showreel or résumé. For what these styles actually buy you, see [prompt-patterns.md](prompt-patterns.md).

### Reposts

Some videos were posted by more than one account. The gallery lists each post as its own entry; we cite the earliest one.

| Original | Also posted as | How we know |
|---|---|---|
| [#1](https://www.prompt-motion.com/stephanlivera-df17a2) | [#62](https://www.prompt-motion.com/roundtablespace-d3a1be) | Byte-identical video file |
| [#4](https://www.prompt-motion.com/ajith-io-b5626e) | [#129](https://www.prompt-motion.com/mrtanviir-132457), [#227](https://www.prompt-motion.com/umangratani-57f86a) | Same video, matching contact sheets |
| [#6](https://www.prompt-motion.com/himanshutwtxs-5f4b43) | [#51](https://www.prompt-motion.com/chatgptastra-0d95c7) | Same video |
| [#64](https://www.prompt-motion.com/sayan-shanky-f850d8) | [#117](https://www.prompt-motion.com/mdaman010-e7226a) | Same frames, different encode |

---

## 3. Top 20 overall

We ordered these by viewing contact sheets, not by sorting grader scores. Each one is worth watching in full.

1. [#5](https://www.prompt-motion.com/twoclipping-221cab) · **Photo print app launch film** · @twoclipping · 29s · square — One continuous take: the wordmark squeezes into its own period, an iris opens onto a photo, a liquid-glass slider relights it from day to golden hour, a status pill morphs through the order, and a black flood contracts onto a framed print on real wall footage. The prompt is a model of a structured spec.
2. [#13](https://www.prompt-motion.com/twoclipping-6dd14e) · **UGC ad generator promo** · @twoclipping · 20s — An off-white hook sinks into a dark stage: a scan wall of 18 real vertical ads, a 3D carousel with floor reflections, then a stat slam with ghosted motion-blur echoes. The prompt documents its beat grid, loudness target and per-beat frame checks.
3. [#8](https://www.prompt-motion.com/lexnlin-038035) · **Engraving-style Claude ad** · @LexnLin · 15s · vertical — Engraved cut-outs on white, with one coral dot carrying every cut (question mark, pen tip, sunflower centre, logo). An editorial-grade lesson in match cuts.
4. [#29](https://www.prompt-motion.com/kloss-xyz-fe0c31) · **History of AI timeline** · @kloss_xyz · 2:52 — Almost three minutes with a purpose-built visual for every chapter (neuron Σ, perceptron, backprop, a Go board) under one consistent chapter HUD. The pacing holds the whole way.
5. [#36](https://www.prompt-motion.com/ismailfahmi-557268) · **Drone Emprit showreel** · @ismailfahmi · 15s — Millions of mentions become flow-field particle ribbons that recolour by platform, regroup into clusters and fall into a sentiment spike, while a counter ticks in the corner.
6. [#64](https://www.prompt-motion.com/sayan-shanky-f850d8) · **AI data centre 3D tour** · @Sayan_shanky · 1:38 — A 46-character prompt returned an 11-chapter clay-render 3D tour (power intake, racks, an exploded chip, the cluster, cooling) with colour-coded flow lines and a persistent legend. Also posted as [#117](https://www.prompt-motion.com/mdaman010-e7226a).
7. [#202](https://www.prompt-motion.com/blueoctopusai-dd17bd) · **First & 10 yellow line explainer** · @blueoctopusai · 2:48 — A whole low-poly stadium plus a signal-chain diagram explains how the broadcast yellow first-down line is composited. A benchmark for 3D explainers.
8. [#147](https://www.prompt-motion.com/buildfastwithai-53234e) · **Indian civilisation history film** · @BuildFastWithAI · 1:27 — Indigo, turmeric and vermilion plates strung on one red thread across five thousand years, closing as a timeline. The skill that made it also synthesises the soundtrack in code.
9. [#83](https://www.prompt-motion.com/hbcoop-de365c) · **Full Stop figure sequence** · @HBCoop_ · 29s — On a beige page, one black dot becomes a line, a lens, a ball, a flock and a world, with typewriter figure captions underneath. Minimal and very refined.
10. [#225](https://www.prompt-motion.com/samaote-5e2fc2) · **Synced lyrics motion video** · @samaote · 30s — Lyrics lock to the bar while the whole song plays out as a single sun, from sunrise to eclipse, with a countdown and bar counter in the corners.
11. [#44](https://www.prompt-motion.com/gizakdag-cf4ae6) · **Overthinking motion study** · @gizakdag · 15s · vertical — A dot bursts into orbiting rings of anxious questions over retro collage, halftone and RGB split, then resolves on "breathe." Poster-level density.
12. [#42](https://www.prompt-motion.com/nft-chen-5f8bb0) · **Porco Rosso sunset dogfight** · @NFT_Chen · 14s — Toon-shaded purple clouds and a sunset dogfight over the sea in Three.js. Not a product film, but proof of how far browser 3D can go.
13. [#158](https://www.prompt-motion.com/rebutonepress-810f78) · **Black hole time story** · @RebutonePress · 5:00 — A black hole with gravitational lensing and a two-column telemetry HUD that shows the mothership's and the probe's clocks drifting apart, with Chinese subtitles. The rendering method isn't stated in the prompt.
14. [#155](https://www.prompt-motion.com/faroukzy-9ff23e) · **The Last Light animated short** · @faroukzy · 4:00 — A storybook-style short: a lighthouse, a storm, and a small robot who gives its own chest light to the dark lamp, with speaker-labelled subtitles. The prompt is a single sentence that names no stack; watch it for the storytelling and the shot rhythm.
15. [#216](https://www.prompt-motion.com/spearwtf-3c1fd1) · **Chain.wtf pitch video** · @SPEARwtf · 30s — Opens on a polite "Gamble responsibly" button, a cursor clicks, and it smash-cuts to a 3D DOUBLE IT arcade button. A textbook fake-out cold open, followed by 3D props under grain and chromatic aberration.
16. [#214](https://www.prompt-motion.com/nolkeeg-bf062e) · **What happens in one second** · @nolkeeg · 45s — Particles condense into ONE SECOND, then a glowing globe and sun. Each screen is one big number with an italic serif line, over a progress bar that stands for the second itself.
17. [#81](https://www.prompt-motion.com/samuel-spitz-974923) · **Motion design showreel** · @samuel_spitz · 15s — One red line runs the whole reel (underline, chrome-orb orbit, signature) through Bauhaus module grids, layered glass depth and liquid-chrome type. The most polished take on the common showreel brief.
18. [#89](https://www.prompt-motion.com/zheke-38deff) · **Kinetic type showreel** · @zheke · 15s · square — "I CAN + verb", each verb acted out by its own principle (SNAP shatters, RENDER becomes a glossy 3D blob), then AFTER EFFECTS is struck out for JUST CODE.
19. [#126](https://www.prompt-motion.com/ik-builds-b8bdcf) · **Paper-style product launch film** · @ik_builds · 15s — A teal ball travels from scattered notes to the hub of a node graph to the head of a growth curve and lands as the logo, with hand-drawn marker notes, hard light/dark switches and 3D type that shatters into a chart.
20. [#228](https://www.prompt-motion.com/anilraok-eff262) · **Scrabble tile character story** · @Anilraok · 42s · vertical — A wooden letter tile left outside the grid finally fills the gap. Warm key light, shallow depth of field and near-feature-animation character work in Three.js.

**Also worth watching**

- [#3](https://www.prompt-motion.com/shneural-2abdfa) · **Bold kinetic type showreel** · @shneural · 32s — Six numbered chapters, each a huge two-line claim plus one rotating chrome or glass 3D object.
- [#15](https://www.prompt-motion.com/emollick-8661a8) · **Recursion explained in genres** · @emollick · 1:15 — Every level of recursion drops into a new film genre, then the film unwinds back out to finish its sentence.
- [#17](https://www.prompt-motion.com/steventey-0d20e4) · **Dub promo video** · @steventey · 15s — A long UTM link compresses into a short-link pill, then a dark dot-matrix globe and a 3D-tilted live dashboard.
- [#71](https://www.prompt-motion.com/arjunsh1607-93005d) · **Pixelup Labs studio showreel** · @arjunsh1607 · 15s — A studio reel that ends on a well-built proof beat: headline, highlighted key word, stat count-ups.
- [#112](https://www.prompt-motion.com/jesscaroline7-1ff7cb) · **Ondefica app motion reel** · @jesscaroline7 · 1:00 · vertical — A vertical reel built with HyperFrames: a dot-per-location map and counters tell the app's story.
- [#136](https://www.prompt-motion.com/web3wesley-7bb108) · **Type, form, space showreel** · @Web3Wesley · 15s — A résumé card opens and closes the reel, and its skills list doubles as the chapter index.
- [#143](https://www.prompt-motion.com/adamdesgns-478d6d) · **Fitters Bible app promo** · @Adamdesgns · 15s — Welding sparks along a pipe path, engineering HUD callouts and a dot-per-record counter.
- [#176](https://www.prompt-motion.com/madebyjmayala-b9204d) · **Gene Spectra promo** · @madebyjmayala · 15s — A problem line over raw genome text, then a scan line that fans the data into a labelled spectrum.
- [#185](https://www.prompt-motion.com/robvjourney-ce3e1a) · **Nohandslabs brand promo** · @robvjourney · 15s — A terminal boot sequence that turns into a dot-matrix brand world.
- [#193](https://www.prompt-motion.com/marouanegazouzi-6071d5) · **Crux motion design showreel** · @marouanegazouzi · 15s — A chaptered HUD reel for a real product: kinetic type, a bell-curve chart, product UI, a radar and a split-flap type montage.
- [#196](https://www.prompt-motion.com/sahildesigner23-ee3155) · **3D motion design showreel** · @sahildesigner23 · 15s — Kinetic type, a chrome blob and a 3D-tilted phone whose render bar climbs to 100%.
- [#233](https://www.prompt-motion.com/kamstudiolabs-0b0824) · **Lighthouse keeper silent short** · @KamStudioLabs · 46s · cinemascope — A wordless silhouette short about a lighthouse keeper, told through light, fog and rain.

---

## 4. Best picks by use case

What to watch, and what to borrow, when you have a specific video to make.

### SaaS launch film

- [#134](https://www.prompt-motion.com/aschapmann-131210) · **SaaS launch video** · @aschapmann · 30s — Four short scenes, one story: why Reddit matters, why it's hard, how the product fixes it, and what you get from Day 1 to Month 3+. **Borrow:** the four-act arc, and a prompt that tells the model to "first read my landing page and codebase to pull the real story" ([prompt](https://www.prompt-motion.com/aschapmann-131210)) before animating anything. Built in Remotion.
- [#126](https://www.prompt-motion.com/ik-builds-b8bdcf) · **Paper-style product launch film** · @ik_builds · 15s — **Borrow:** the brief as a fill-in template, with placeholders such as `{{PRODUCT}}`, `{{AUDIENCE}}` and `{{BANNED_WORDS}}`, and a hard rule: "No invented results: no %, multipliers, customer names or figures." ([prompt](https://www.prompt-motion.com/ik-builds-b8bdcf))
- [#209](https://www.prompt-motion.com/ceowinkz-7c776b) · **Amazon wholesale pitch video** · @ceowinkz · 15s — Problem beats in red ("TOO MANY SELLERS."), solution beats in blue. **Borrow:** a vertical light bar that wipes a product listing into its AFTER state, and one brand node fanning out to three channel cards.
- [#188](https://www.prompt-motion.com/amol909s-27533e) · **Commotion app showreel** · @Amol909S · 20s — **Borrow:** the logo's 2×2 squares open into a grid of live work panes, then a routing diagram shows a request being sent to the right model. A clean way to show parallel agents.
- See also [#5](https://www.prompt-motion.com/twoclipping-221cab) and [#13](https://www.prompt-motion.com/twoclipping-6dd14e) in the [Top 20](#3-top-20-overall).

### Product UI demo

- [#2](https://www.prompt-motion.com/twoclipping-5cba86) · **Shape morphing through UI states** · @twoclipping · 14s · square — One black shape, never cut, morphs through a dozen UI states (button, loader, check, Dynamic Island, player, slider, toggle, tabs, chart, ⌘K, toast) and loops. **Borrow:** "one element, never cut" as the rule for a UI reel, and the prompt's trick of putting a tab indicator's two edges on different springs so the leading edge stretches.
- [#178](https://www.prompt-motion.com/antonio-kodheli-490109) · **Prompt Motion site promo** · @antonio_kodheli · 23s — A promo for the gallery itself, built only from the real site: the camera moves between a full-bleed reel and its card in the grid, opens an entry and its prompt, and lands on the URL pill. **Borrow:** the prompt's rule to show only what the product really has (it bans invented features and numbers) and its split of timing and copy into separate files.
- [#34](https://www.prompt-motion.com/notdwd-7de38a) · **Frame by Frame launch video** · @notdwd · 12s · square — A menu-bar icon springs a frosted-glass prompt box that types a request, then whip-tilts up into the result page. **Borrow:** the prompt's precision: coordinates pinned to frame numbers and every cut placed by a beat formula. [#10](https://www.prompt-motion.com/notdwd-c2037d) is the same creator's remake study with a near-identical prompt.
- [#104](https://www.prompt-motion.com/daniel-haida-8691d4) · **Taxtello bookkeeping app film** · @daniel_haida · 14s — A real bookkeeping dashboard tilted in 3D on dark blue with gold as the only accent; a health-score ring counts up before the wordmark. **Borrow:** one accent element that carries you into each next scene, plus the prompt's numbered list of banned effects and its CHAOS → CONTROL → CLARITY arc.
- [#17](https://www.prompt-motion.com/steventey-0d20e4) · **Dub promo video** · @steventey · 15s — **Borrow:** the product's core action shown as one transformation (a long link compressing into a short one), then a 3D-tilted dashboard with live event toasts.

### Explainer / data story

- [#198](https://www.prompt-motion.com/palashbagchi11-0a4b6b) · **Backlink audit data promo** · @PalashBagchi11 · 30s — Opens on the viewer's situation ("You paid for 173 backlinks."), then one finding per screen: a big number beside a dot grid where each dot is one URL, a struck-through verdict, a CTA. **Borrow:** the one-finding-per-screen audit structure. (The prompt in the gallery covers the music and format pass only.)
- [#36](https://www.prompt-motion.com/ismailfahmi-557268) · **Drone Emprit showreel** · @ismailfahmi · 15s — **Borrow:** one particle system that persists through every scene, so the data visibly turns from volume into categories into one event.
- [#214](https://www.prompt-motion.com/nolkeeg-bf062e) · **What happens in one second** · @nolkeeg · 45s — **Borrow:** a fixed stat lockup (big number, italic serif kicker, small mono line) and a progress bar that is the subject itself.
- [#176](https://www.prompt-motion.com/madebyjmayala-b9204d) · **Gene Spectra promo** · @madebyjmayala · 15s — **Borrow:** the scan-line-to-spectrum move for any "we turn raw X into readable Y" story.
- [#55](https://www.prompt-motion.com/0xnfrith-5be616) · **Celld job ownership explainer** · @0xnfrith · 53s — **Borrow:** labelled chapter pills (THE SETUP, THE FAILURE, THE IDEA, STEP 1–3, THE TRADE-OFF) that make an engineering argument easy to follow.
- For long form, see [#29](https://www.prompt-motion.com/kloss-xyz-fe0c31) and [#202](https://www.prompt-motion.com/blueoctopusai-dd17bd) in the [Top 20](#3-top-20-overall).

### Brand ident / logo

- [#20](https://www.prompt-motion.com/tdinh-me-815acb) · **TypingMind logo reveal** · @tdinh_me · 21s — A wireframe node-net brain fills in facet by facet, becomes the app icon, then the wordmark types on. **Borrow:** build the mark from its own construction lines.
- [#185](https://www.prompt-motion.com/robvjourney-ce3e1a) · **Nohandslabs brand promo** · @robvjourney · 15s — A terminal boot (`[ ok ] agent.intake … online`), a dot-matrix hand, one big stat, caution-tape slogans, then the logo. **Borrow:** a boot sequence as the ident for a technical brand.
- [#122](https://www.prompt-motion.com/madhav-xo-f97f20) · **Personal research intro reel** · @Madhav_XO · 10s — Ten seconds: a terminal compile line, a particle neural network, two proof cards, then the name lockup. **Borrow:** a complete personal ident structure in 10 s.
- For a single dot becoming the mark, see [#8](https://www.prompt-motion.com/lexnlin-038035) and [#83](https://www.prompt-motion.com/hbcoop-de365c) in the [Top 20](#3-top-20-overall).

### Kinetic type

- [#89](https://www.prompt-motion.com/zheke-38deff) · **Kinetic type showreel** · @zheke · 15s · square — **Borrow:** make every word perform its own meaning.
- [#225](https://www.prompt-motion.com/samaote-5e2fc2) · **Synced lyrics motion video** · @samaote · 30s — **Borrow:** lock words to bars and map the whole song to one visual arc.
- [#100](https://www.prompt-motion.com/gdgtify-287ddf) · **Speech built as architecture** · @Gdgtify · 20s · square — Words become structural members: WAIT, WAITING and VOICE hang from a gold rule like a building going up, one cue at a time. **Borrow:** type as architecture, from a structured-spec prompt.
- [#44](https://www.prompt-motion.com/gizakdag-cf4ae6) · **Overthinking motion study** · @gizakdag · 15s · vertical — **Borrow:** let the density climb, then collapse to one calm word.
- [#3](https://www.prompt-motion.com/shneural-2abdfa) · **Bold kinetic type showreel** · @shneural · 32s — **Borrow:** the chapter template of one huge claim plus one 3D object.

---

## 5. Best 1–2 per category

### Product launch film (70)
- [#5](https://www.prompt-motion.com/twoclipping-221cab) · **Photo print app launch film** · @twoclipping · 29s · square — One take, cursor-driven, the highest craft in the set.
- [#126](https://www.prompt-motion.com/ik-builds-b8bdcf) · **Paper-style product launch film** · @ik_builds · 15s — Story and prompt are both reusable as-is.

### Showreel / montage (44)
- [#81](https://www.prompt-motion.com/samuel-spitz-974923) · **Motion design showreel** · @samuel_spitz · 15s — One red line through the whole reel and a consistent chapter frame.
- [#136](https://www.prompt-motion.com/web3wesley-7bb108) · **Type, form, space showreel** · @Web3Wesley · 15s — The clearest structure: a résumé card lists Type / Form / Space / Time, each gets a chapter, and the card closes the reel.

### Explainer / data viz (24)
- [#29](https://www.prompt-motion.com/kloss-xyz-fe0c31) · **History of AI timeline** · @kloss_xyz · 2:52 — A purpose-built visual per chapter under one chapter HUD.
- [#202](https://www.prompt-motion.com/blueoctopusai-dd17bd) · **First & 10 yellow line explainer** · @blueoctopusai · 2:48 — One 3D world plus a signal-chain diagram explains one technical idea completely.
- Also: [#36](https://www.prompt-motion.com/ismailfahmi-557268), [#147](https://www.prompt-motion.com/buildfastwithai-53234e).

### SaaS UI walkthrough (17)
- [#2](https://www.prompt-motion.com/twoclipping-5cba86) · **Shape morphing through UI states** · @twoclipping · 14s · square — A dozen UI states from one uncut shape, looping seamlessly.
- [#178](https://www.prompt-motion.com/antonio-kodheli-490109) · **Prompt Motion site promo** · @antonio_kodheli · 23s — Exact cuts between full-bleed video and the small card in the grid; a "Copied" pill rises and becomes the URL button.
- Also: [#231](https://www.prompt-motion.com/charlesmendez-73b6e4), [#188](https://www.prompt-motion.com/amol909s-27533e).

### Kinetic typography (16)
- [#225](https://www.prompt-motion.com/samaote-5e2fc2) · **Synced lyrics motion video** · @samaote · 30s — Lyrics locked to the bar, one sun through the whole song.
- [#44](https://www.prompt-motion.com/gizakdag-cf4ae6) · **Overthinking motion study** · @gizakdag · 15s · vertical — Poster-grade collage whose rhythm moves from chaos back to calm.
- Also: [#89](https://www.prompt-motion.com/zheke-38deff), [#100](https://www.prompt-motion.com/gdgtify-287ddf).

### Character / story animation (16)
- [#155](https://www.prompt-motion.com/faroukzy-9ff23e) · **The Last Light animated short** · @faroukzy · 4:00 — The most complete story and the most beautiful frames.
- [#228](https://www.prompt-motion.com/anilraok-eff262) · **Scrabble tile character story** · @Anilraok · 42s · vertical — Near-feature-animation polish in Three.js, and a simple "the missing piece" story.
- Also: [#70](https://www.prompt-motion.com/jake11moran-a269c4) (a skill that turns a real agent session into a watercolour cartoon), [#233](https://www.prompt-motion.com/kamstudiolabs-0b0824).

### Vertical social ad (10)
- [#8](https://www.prompt-motion.com/lexnlin-038035) · **Engraving-style Claude ad** · @LexnLin · 15s · vertical — One dot does every transition.
- [#112](https://www.prompt-motion.com/jesscaroline7-1ff7cb) · **Ondefica app motion reel** · @jesscaroline7 · 1:00 · vertical — A HyperFrames vertical with a dot-per-location map and counters.
- Also in this category: [#216](https://www.prompt-motion.com/spearwtf-3c1fd1) (16:9).

### 3D world / scene (8)
- [#64](https://www.prompt-motion.com/sayan-shanky-f850d8) · **AI data centre 3D tour** · @Sayan_shanky · 1:38 — An 11-chapter 3D tour from a one-sentence prompt.
- [#158](https://www.prompt-motion.com/rebutonepress-810f78) · **Black hole time story** · @RebutonePress · 5:00 — A lensing black hole with two-column telemetry.
- Also: [#42](https://www.prompt-motion.com/nft-chen-5f8bb0).

### Personal intro reel (8)
- [#223](https://www.prompt-motion.com/rneayan-474bcf) · **Risograph studio intro** · @rneayan · 1:09 — Risograph texture throughout; faders labelled planning, directing, AI and editing say "a human directs the AI" in one image.
- [#122](https://www.prompt-motion.com/madhav-xo-f97f20) · **Personal research intro reel** · @Madhav_XO · 10s — A dark particle network and a terminal compile opening, complete in 10 s.

### Generative / abstract (6)
- [#83](https://www.prompt-motion.com/hbcoop-de365c) · **Full Stop figure sequence** · @HBCoop_ · 29s — One dot tells the whole story.
- [#53](https://www.prompt-motion.com/monokern-ade5b6) · **Psychedelic hypnotic eye showreel** · @monokern · 20s — Shader-level psychedelia; watch it to see the ceiling.

### Logo / brand ident (4)
- [#185](https://www.prompt-motion.com/robvjourney-ce3e1a) · **Nohandslabs brand promo** · @robvjourney · 15s — Terminal boot into a brand world.
- [#20](https://www.prompt-motion.com/tdinh-me-815acb) · **TypingMind logo reveal** · @tdinh_me · 21s — Wireframe, then faceted fill, then the app icon.

### Tool / skill demo (2)
- [#16](https://www.prompt-motion.com/lexnlin-6161a6) · **Cinetic skill launch film** · @LexnLin · 30s — Launch film for an open-source skill with a library of 273 techniques, ending on the install command typed in a terminal.

### Other (8)
- [#26](https://www.prompt-motion.com/itsolelehmann-e47532) · **Four seasons train window** · @itsolelehmann · 30s — The foreground never moves while the seasons change outside the window, with a tunnel blackout in between. A lovely device for any before/after story.

---

## 6. Method & caveats

**How the picks were made**

1. **Grading.** All 233 entries were graded by AI graders in 24 batches of up to 10 entries. Each grader saw a 6-frame contact sheet of the video, the prompt and the metadata, and assigned a category, tags, an inferred stack, a visual-impact score (1–5), a prompt-structure score (1–5) and a 1–5 rating of how useful the entry is as a reference for SaaS and product films.
2. **Shortlist.** We took the 43 entries with the top visual-impact score, the entries graders rated most useful as references for SaaS and product films, and strong candidates from every category: about 90 entries in all.
3. **Re-ranking.** We viewed each shortlisted contact sheet and re-ordered by craft, clarity of structure and how much a reader can borrow. Where our reading differed from the grader's, ours decided the order.

**Why there are no per-entry scores**

- **The graders disagree by about one point.** The same video posted three times ([#4](https://www.prompt-motion.com/ajith-io-b5626e), [#129](https://www.prompt-motion.com/mrtanviir-132457), [#227](https://www.prompt-motion.com/umangratani-57f86a)) got visual-impact scores one point apart, and two other repost pairs ([#64](https://www.prompt-motion.com/sayan-shanky-f850d8) / [#117](https://www.prompt-motion.com/mdaman010-e7226a), [#6](https://www.prompt-motion.com/himanshutwtxs-5f4b43) / [#51](https://www.prompt-motion.com/chatgptastra-0d95c7)) each landed in two different categories. A ±1 spread on a 5-point scale is too wide to rank individual entries.
- **Aggregates are steadier.** Visual-impact scores across all 233: 5 entries at 2, 65 at 3, 120 at 4, 43 at 5 (none at 1). Average visual impact by prompt style is 3.88 for one-liners (n = 154), 3.80 for short briefs (n = 56), 3.94 for structured specs (n = 17) and 3.83 for skill-driven prompts (n = 6). Those gaps sit well inside the grader noise, so in this data a longer prompt did not buy a visibly higher score. What it buys is control and repeatability (see [prompt-patterns.md](prompt-patterns.md)).

**What we did not check**

- **Contact sheets, not full playback.** We viewed six frames per video, not every video end to end. Pieces whose strength is continuous motion (for example [#2](https://www.prompt-motion.com/twoclipping-5cba86)) can look plainer in stills than they are.
- **Sound** was counted (present, silent or absent), not rated.
- **Inferred stacks** come from the graders and were not verified against source code.
- **Picks are a judgement.** They favour craft, a clear structure and ideas you can reuse. Many entries outside these lists are worth your time; the full set is in [`catalog/catalog.json`](../catalog/catalog.json).

**Rights.** Videos and prompts belong to their creators. This repo links to each entry and post and does not re-host videos, frames or full prompts.
