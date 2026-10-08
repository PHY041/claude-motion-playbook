# Skills: the open-source agent skills behind the gallery

A read-through of the agent skills linked from the 233 videos on [prompt-motion.com](https://www.prompt-motion.com/) (curated by [@p4nthera_](https://x.com/p4nthera_)), snapshot of 2026-10-09. A skill is a folder of instructions, references and scripts (`SKILL.md` plus helpers) that a coding agent loads to do one kind of job. Here the job is turning a brief into a rendered video. `#N` is the entry's `id` in [`catalog/catalog.json`](../catalog/catalog.json).

[简体中文版](zh/skills.md)

## TL;DR

- **4 of 233 entries link a skill repo; the other 229 are prompts.** The four are [#16 Cinetic skill launch film — @LexnLin](https://www.prompt-motion.com/lexnlin-6161a6), [#23 Reddit marketing tool launch video — @anthonyriera](https://www.prompt-motion.com/anthonyriera-9b1b2a), [#70 Animated agent session story — @jake11moran](https://www.prompt-motion.com/jake11moran-a269c4) and [#147 Indian civilisation history film — @BuildFastWithAI](https://www.prompt-motion.com/buildfastwithai-53234e). Their repos hold 13 motion skills, and this page reviews all of them.
- **[cinetic](#1-cinetic) has the most complete pipeline.** It runs 9 steps from `BRIEF.md` to delivery, and every step ends in a gate the agent actually runs, most of them scripts. It draws techniques at random from a 273-entry library and won't ship until a film passes an 11-dimension rubric. By the author's own measurement it costs about 3× the time and tokens of a baseline run without it.
- **[product-film](#2-product-film) stays closest to the product.** It reads your design system, interviews you using your real feature names, and builds the film in Remotion from your own components. Before delivery it decodes the finished files to check that the colours came through intact.
- **The HyperFrames community repo holds 8 skills.** The two standouts are [session-story](#3-session-story), a personal film built from your agent transcripts behind an explicit privacy gate, and [vox-explainer](#4-vox-explainer), which keeps a seam ledger and checks every cut automatically in headless Chrome.
- **buildfast-skills spans three output types.** [generative-film](#6-generative-film) draws every frame with pycairo and needs no browser. [motion-studio](#5-motion-studio) combines 51 visual styles, 10 motion languages and 13 video templates, then runs a 16-check QC. [canvas-documentary](#7-canvas-documentary-html-animation-skill) outputs an interactive HTML page instead of an MP4.
- **The ideas recur across repos.** One beat grid drives picture, sound and QA. Each build ends in a render → measure → critique loop, and pass/fail thresholds are explicit numbers. See [Ideas worth borrowing](#9-ideas-worth-borrowing-whatever-engine-you-use).
- **Every repo is MIT or Apache-2.0, but the engines and libraries have their own licences.** Remotion has its own licence; p5 is LGPL-2.1; Strudel is AGPL-3.0. Check them before commercial use.

## Contents

1. [The repos at a glance](#the-repos-at-a-glance)
2. [Comparison](#comparison)
3. Reviews: [cinetic](#1-cinetic) · [product-film](#2-product-film) · [session-story](#3-session-story) · [vox-explainer](#4-vox-explainer) · [motion-studio](#5-motion-studio) · [generative-film](#6-generative-film) · [canvas-documentary](#7-canvas-documentary-html-animation-skill) · [the other community skills](#8-the-other-hyperframes-community-skills)
4. [Ideas worth borrowing](#9-ideas-worth-borrowing-whatever-engine-you-use)
5. [Which one to pick](#10-which-one-to-pick)
6. [Method & caveats](#11-method--caveats)

---

## The repos at a glance

All four repos were read at the commit below. File links in this page point to the default branch, so a file may have moved since then.

| Repo | Snapshot commit | Licence | Gallery entry |
|---|---|---|---|
| [Leonxlnx/cinetic](https://github.com/Leonxlnx/cinetic) | [`bee5d78`](https://github.com/Leonxlnx/cinetic/commit/bee5d7807205d5543472c38312507f9bf366cbbf), 2026-10-04 (v1.0.0) | MIT | [#16 Cinetic skill launch film — @LexnLin](https://www.prompt-motion.com/lexnlin-6161a6) |
| [Rieranthony/product-film-skill](https://github.com/Rieranthony/product-film-skill) | [`fe11efc`](https://github.com/Rieranthony/product-film-skill/commit/fe11efc429d5903e37274d0b294e1b95745b2881), 2026-09-26 (v1.1.0) | MIT | [#23 Reddit marketing tool launch video — @anthonyriera](https://www.prompt-motion.com/anthonyriera-9b1b2a) |
| [heygen-com/hyperframes-community-skills](https://github.com/heygen-com/hyperframes-community-skills) | [`ba7a0bb`](https://github.com/heygen-com/hyperframes-community-skills/commit/ba7a0bb6d3567d124c51f6074625043bfe0b32eb), 2026-09-24 | Apache-2.0 | [#70 Animated agent session story — @jake11moran](https://www.prompt-motion.com/jake11moran-a269c4) (session-story) |
| [buildfastwithai/buildfast-skills](https://github.com/buildfastwithai/buildfast-skills) | [`c91416c`](https://github.com/buildfastwithai/buildfast-skills/commit/c91416cf7473ccd485d5fcc739a54314a4f8b1bc), 2026-10-08 | MIT | [#147 Indian civilisation history film — @BuildFastWithAI](https://www.prompt-motion.com/buildfastwithai-53234e) (generative-film) |

Some context from the catalog: 56 of the 233 entries state their stack. Of those, Remotion appears in 13 and HyperFrames in 10. Most of the 13 skills target the same two engines. Two bring their own renderer (motion-studio and generative-film), canvas-documentary outputs an interactive page, and p5-paint-animation renders with Puppeteer and ffmpeg.

---

## Comparison

| Skill | Output | Render stack | Licence notes | Best for |
|---|---|---|---|---|
| [cinetic](#1-cinetic) | 3–90 s films, loops and stings; MP4, plus WebM/GIF/ProRes alpha where the format calls for them | Remotion 4.0.529 (default) or HyperFrames 0.8.79 | MIT; Remotion's licence applies to the default engine | Launch films and logo stings where finish and sync have to be checkable |
| [product-film](#2-product-film) | 20–90 s launch film or muted landing-page loop, plus WebM and poster | Remotion, Bun, uv | MIT; Remotion's licence; music you have rights to | Product teams with a codebase and a design system |
| [session-story](#3-session-story) | 40–70 s watercolour film at 24 fps with its own score | HyperFrames 0.8.71 + p5.brush | Apache-2.0; p5 is LGPL-2.1 | A personal film of how you work with your agent |
| [vox-explainer](#4-vox-explainer) | 60–90 s collage-style explainer | HyperFrames + GSAP; Node seam scripts | Apache-2.0 | Explainers built from a topic, report or document |
| [motion-studio](#5-motion-studio) | Motion-graphics MP4 in any aspect ratio, 13 video types | Its own HTML engine + Playwright + ffmpeg | MIT; bundled fonts carry their own (OFL) licence files | Trying many looks on one storyboard; model benchmarks |
| [generative-film](#6-generative-film) | 45–120 s, 1920×1080, 30 fps MP4 | Python: pycairo, Pillow, numpy/scipy, ffmpeg | MIT | Graphic history and science shorts, no browser needed |
| [canvas-documentary](#7-canvas-documentary-html-animation-skill) | One self-contained interactive HTML file, about 2 min | Canvas 2D + Web Audio | MIT | Interactive story pieces for the web |

---

## 1. cinetic

**What it does:** the coding agent acts as director. It writes the concept, invents or applies a brand, sets a beat grid, synthesizes the score, renders, then measures and critiques the result before shipping. The gallery entry, [#16 Cinetic skill launch film — @LexnLin](https://www.prompt-motion.com/lexnlin-6161a6), is the skill's own 30-second launch film.

**Pipeline, brief to MP4.** Each step writes a file and ends at a check the agent runs ([SKILL.md §3](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/SKILL.md)):

| Step | Writes | Gate |
|---|---|---|
| 0 Intake | `BRIEF.md`: spec line, hard bans, brand exceptions | A spec line such as `1920x1080@60, 30s, 120BPM` |
| 1 Concept | `TREATMENT.md`: 3 concepts, drawn techniques, beat sheet | Logline ≤ 15 words; specificity test answered; copy within the word budget |
| 2 Brand | `src/brand/`: tokens, mark, lockup | `lint-film.mjs` finds no placeholders and no off-token colour or font |
| 3 Timeline | `timeline.ts`: every frame from `b(bar, beat, sub)` | `grid-check.ts`: cues on the 16th-note grid, text held long enough, no gap without an event longer than 48 f |
| 4 Build | Act code plus a contact sheet per act | 0 safe-area or overlap violations; readable text moves ≤ 20 px/f |
| 5 Sound | Cues exported from the picture code, then a synthesized score | −14 LUFS ±0.5, true peak ≤ −1.5 dBTP |
| 6 Render | Preview, then master (with motion blur above 12 px/f) | `probe.py` spec check; `check-sync.py` lag ≤ 48 samples |
| 7 Review | Sheets, pixel forensics, A/V audit, critic passes | Every one of 11 rubric dimensions ≥ 3, Finish and Sync = 5, mean ≥ 4.2, no open P0 |
| 8 Deliver | Master, poster, 9:16 and 1:1 re-layouts, brand kit | Every deliverable passes `probe.py` |

Stings, loops and short clips take a scaled-down path: a one-page treatment, one or two acts and one review round.

**Render stack, dependencies, licence.** Remotion 4.0.529 is the default engine. HyperFrames 0.8.79 is the alternative, scaffolded with `new-film.sh --engine hyperframes` from [`assets/hyperframes-starter/`](https://github.com/Leonxlnx/cinetic/tree/main/skills/cinetic/assets/hyperframes-starter). Requirements are Node 22+, ffmpeg 6+ with libx264, and a headless Chromium. You also need Python 3.11+ with numpy, scipy, soundfile, pyloudnorm, opencv-python and librosa, plus fonttools, brotli, uharfbuzz and pillow for logos and gradients. The skill is MIT. The README notes that Remotion is free for individuals and companies of up to 3 people, and that a company licence is needed from 4. HyperFrames is Apache-2.0.

**What's genuinely clever**

- **Techniques are drawn, not chosen.** [`scripts/pick.py`](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/scripts/pick.py) draws from [`assets/library/techniques.json`](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/assets/library/techniques.json), which holds 273 techniques in 14 categories. The draw is weighted by format and energy, yields roughly one technique per 2.5 s of film, and is seeded so it can be reproduced. The author's reasoning: an agent that picks by hand converges on the same fade-up, push-in and end card every time. `pick.py` uses only the Python standard library, so it works with any engine.
- **Sound is computed from motion.** Sync frames come from the same easing curves and springs the picture uses: contact frames for impacts, the 97% frame for settles, velocity peaks for whooshes. In the HyperFrames starter this is `FILM.cues()` in [`timeline.js`](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/assets/hyperframes-starter/timeline.js). The author reports that hand-typed sync points landed 8–11 frames off.
- **Pixel forensics on the rendered file.** [`scripts/forensics.py`](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/scripts/forensics.py) checks any MP4 for one-frame pops, stalls, dead holds, ghost frames, border slivers, judder, banding, compression smear and loop seams. [`scripts/sheet.py`](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/scripts/sheet.py) makes contact sheets labelled with frame numbers and times. Neither depends on the engine.
- **Banding is handled with a number.** [`references/finishing.md` §3](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/references/finishing.md) gives a rule of thumb: a CSS gradient whose channels change by fewer than about 30 code values across the frame will band. Gradients ship as dithered PNGs from [`dither-gradient.py`](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/scripts/dither-gradient.py). On HyperFrames, [`hf-finish.sh`](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/scripts/hf-finish.sh) renders a PNG sequence and encodes once, with x264 at CRF 14, tagged BT.709. That avoids compressing twice.
- **A table of HyperFrames traps the linter misses.** [`references/hyperframes-engine.md` §10](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/references/hyperframes-engine.md) lists them. PNG capture drops the `html`/`body` background, so the master turns black. Mismatched composition ids cause a 45 s stall and then a frozen act. A lint error disables the layout audit, so `check` reports a clean-looking "0 samples".
- **Critics plus a verifier.** Five prompts in [`assets/critics/`](https://github.com/Leonxlnx/cinetic/tree/main/skills/cinetic/assets/critics) cover director, art/copy/UI, sound-sync and forensics, plus a verifier that tries to refute every P0 and P1 before anyone fixes it. They score against the 11-dimension rubric and ship gate in [`references/review-loop.md` §9–10](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/references/review-loop.md).
- **Craft rules backed by measurements.** [`references/craft-rules.md` §9](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/references/craft-rules.md) lists 15 differences between top-tier and good films. Two examples: exits accelerate into the cut and the next shot opens already moving; a film spends stillness once (a 60–96 f hold on the key claim) and follows it with its biggest move.
- **Tests that kill weak ideas early.** [`references/concept-and-story.md` §4](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/references/concept-and-story.md) runs 10 tests, among them ownership, deletion, muted and specificity. It also lists generic props, such as the glowing orb for "AI". The pause test in [`references/product-ui.md` §8](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/references/product-ui.md) requires every paused frame to make sense: counts agree, state changes on the frame of its cause, and UI text is ≥ 22 px.
- **An honest evaluation.** [`docs/evaluation.md`](https://github.com/Leonxlnx/cinetic/blob/main/docs/evaluation.md) reports that cinetic met more written expectations than the baseline in every round (54/56 vs 41/56 in round 7). It also reports that the neutral blind judge was split, preferring cinetic in 7 of 23 comparisons over six rounds. The author adds that the expectations were written alongside the skill and should be read as an upper bound.

**Limitations**

- **Cost.** Round 7 averaged 95 minutes and 626k tokens per film, against 33 minutes and 231k tokens for the baseline. That is roughly 3×, by the author's measurement.
- **Opinionated taste.** When the agent invents the look, hard bans apply: no serif or italic type; no orange, cream or purple; no glow, particles or multi-hue gradients. A brand you supply overrides them, but each exception has to be declared in `BRIEF.md` and marked in code.
- **The HyperFrames path is the secondary one.** Its motion blur is capped near 18 px/f, and the docs advise building faster films in Remotion. The published evaluation compares against a Remotion baseline and does not report HyperFrames runs separately.
- **Pinned engine versions.** The skill pins Remotion 4.0.529 and HyperFrames 0.8.79, so a newer CLI may behave differently.
- **Heavy setup.** The Python dependencies are substantial. The scripts were developed on Linux; the README says macOS is less tested and Windows is untested.
- **A dense default pace.** The density target is 45–60 discrete events per 30 s. The author says every number is a default you can move away from with a stated reason.

**Who should use it:** people making launch films, teasers, logo stings or landing-page loops who have the time and token budget for a measured process. It also suits teams who want to lift individual gates (forensics, contact sheets, the rubric) into their own pipeline.

**Best for:** short films where finish and audio sync have to be verifiable, not just eyeballed.

---

## 2. product-film

**What it does:** learns your product's design system and asks what the film should include. It then builds and renders a launch video or landing-page loop in Remotion from your real components, logo and music. The gallery lists [#23 Reddit marketing tool launch video — @anthonyriera](https://www.prompt-motion.com/anthonyriera-9b1b2a) with this skill, stack Remotion.

**Pipeline, brief to MP4** ([SKILL.md](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/SKILL.md)):

1. **Discovery.** Parallel read-only sweeps of rules files, tokens, components, logo, claims and the live site ([`reference/discovery.md`](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/reference/discovery.md)).
2. **Interview.** Two rounds of multiple-choice questions: first the brief, then the ingredients.
3. **Brand and story.** The answers become `videos/BRAND.md`, which overrides the skill's defaults, plus a film prompt and beat sheet. There is a checkpoint with 3 style frames before anything is built.
4. **Music.** `beats.py` measures the song's beat grid and `audio-edit.py` cuts it on bar lines. Sound effects sit on measured peaks.
5. **Build.** One Remotion composition with every frame a pure function of time. A small kit covers time, springs, camera, cursors, magic moves and punchlines.
6. **Review.** Stills at every handoff, contact and handoff sheets, then a half-resolution draft.
7. **Render and verify.** A 240 fps PNG master is averaged by ffmpeg (`tmix`, 4 sub-frames) into 60 fps with motion blur, with the colour conversion done once. Deliverables are a muted loop, a version with music, a WebM and a poster. `verify.py` checks them all ([`reference/render.md`](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/reference/render.md)).

**Render stack, dependencies, licence.** Remotion (added to your project by the skill), Node.js, [Bun](https://bun.sh) and [uv](https://docs.astral.sh/uv/). The Python scripts pull numpy and a full ffmpeg (imageio-ffmpeg) on demand, so nothing is installed system-wide. It needs Claude Code, because it runs your local toolchain and its interview step uses Claude Code's question tool. The skill is MIT. Its README notes that Remotion carries its own licence, under which larger companies need a company licence.

**What's genuinely clever**

- **It asks only what the code can't answer.** [`reference/interview.md`](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/reference/interview.md) names options after your real features and components and lists the recommendation first. It never asks about colours, fonts or radii, which the code already answers. Taste questions get 3 style frames instead, because people react to pictures faster than to questions.
- **Proof moments and magic moves.** [`reference/ingredients.md`](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/reference/ingredients.md) gives a search result, an AI answer, a metric or a quote its own scene, "lo-fi but faithful". The same file has a pairing table for magic moves, where one element travels into the next scene: avatars in a diagram become rows in a list, a clicked row's title becomes the detail view's header.
- **Punchlines that don't re-centre.** In [`templates/kit/punchlines.tsx`](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/templates/kit/punchlines.tsx), every word holds its slot from the start, so a centred line never shifts while it builds.
- **Decode-and-check verification.** [`scripts/verify.py`](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/scripts/verify.py) decodes frame 0 of every deliverable and checks the background within ±2. For loops, it checks that the last frame matches the first. It exists to catch one specific trap: a limited-range master read as full range turns `#0a0a0a` into `#171717`, a grey box on a dark page.
- **The story follows the song's structure.** [`reference/music.md`](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/reference/music.md) prints each stem's loudness per bar and maps the story onto it. The first punchlines arrive where the drums come in, the strongest moment lands on the drop, and the headline sits where the bass drops out.
- **A short list of Remotion traps.** The list in SKILL.md is practical. Stills don't forward console logs, so [`templates/kit/debug.tsx`](https://github.com/Rieranthony/product-film-skill/blob/main/plugins/product-film/skills/product-film/templates/kit/debug.tsx) prints measurements into the frame. Remotion's bundled ffmpeg has no `tmix`, `select` or `tile`. `interpolateColors` cannot parse `color-mix()`.

**Limitations**

- **Remotion only.** Larger companies need Remotion's company licence.
- **Claude Code only.** It does not run in the chat apps.
- **It needs a product to read.** It works best inside a product repo with tokens and components; without one there is little to discover.
- **It brings no music.** You supply a licensed track or a royalty-free one, or go silent. Sound effects are synthesized or licensed.
- **Slow final render.** The author's figure is about 10 minutes for a 50 s film at 240 fps on a laptop.
- **No published evaluation** comparable to cinetic's.

**Who should use it:** SaaS and app teams who want the film to look like the product made it, with the same surfaces, type, components and claims.

**Best for:** landing-page loops and launch videos built from a real codebase.

---

## 3. session-story

**What it does:** your agent reads its local history with you, picks one typical session and films it start to finish as a 40–70 s watercolour animation, with an orchestral score it composes itself. Your messages arrive as paper planes. Corrections arrive as a cartoon mallet and praise as a butterfly towing a ribbon of words. The gallery entry is [#70 Animated agent session story — @jake11moran](https://www.prompt-motion.com/jake11moran-a269c4).

**Pipeline, brief to MP4** ([SKILL.md](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/session-story/SKILL.md)):

1. Setup once (`npm ci` from the committed lockfile).
2. Ask the user for permission before reading any history.
3. `harvest.py` reads the agent's local transcripts (Claude Code or Codex) for the current project and ranks sessions by how typical they are.
4. The agent writes `story.json` beat by beat with verbatim quotes and real times, and `schedule.mjs` checks it after every edit.
5. It decorates the room from what it knows about the user.
6. **Privacy gate:** the user sees a table of every on-screen line with its source and approves or edits it. Until approval, every frame carries a DRAFT stamp.
7. Design pass: snapshot frames and a contact sheet.
8. Score: `score.py`, then `build.sh` (normalized to −16 LUFS).
9. Render with `hyperframes@0.8.71 render --fps 24 --crf 12`, then check the length and the key frames.

**Render stack, dependencies, licence.** HyperFrames 0.8.71 with p5 2.3.3 (LGPL-2.1), p5.brush 2.2.3 (MIT) watercolour on WebGL, and the Permanent Marker font (Apache-2.0). It needs Node 22+, Python 3.9+ (standard library only) and ffmpeg. The score renders through `swift` and Apple's built-in General MIDI bank on macOS, or through `fluidsynth` with a soundfont elsewhere. The repo is Apache-2.0. Part of the engine kit is adapted from ClaudeAnimationBase (MIT), as documented in [`assets/engine/NOTICE.md`](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/session-story/assets/engine/NOTICE.md).

**What's genuinely clever**

- **One story file feeds both picture and music.** [`scripts/schedule.mjs`](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/session-story/scripts/schedule.mjs) compiles `story.json` with the same `scenes/compile.js` the film runs. From it, it writes `story.js` for the picture and `score/timeline.json` for the music, so one edit re-times both.
- **Privacy is part of the design.** The skill asks for consent, then runs the approval table and DRAFT stamp described above. It also tells the agent to pass `--describe false` to every snapshot, because with a `GEMINI_API_KEY` set the snapshot command would otherwise send frames (containing the user's words) to Gemini. `schedule.mjs` refuses to build the bundled example story without `--example`, so the example can't stand in for your user's story.
- **Physical motion rules.** [`references/motion.md`](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/session-story/references/motion.md) sets three rules: no idle motion, a reaction starts on the frame of its cause, and a heavy moment gets a beat of stillness before it. The paper plane glides at about 3:1, porpoises, flares and slides to a stop.
- **Dead air fails the build.** [`scripts/score/qc.py`](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/session-story/scripts/score/qc.py) fails the score on any stretch quieter than −45 dBFS for more than 1.2 s, which usually means a beat with no cue.

**Limitations:** it needs real history, either local transcripts or messages the user pastes in. The visual world is fixed (a watercolour room, paper planes, a mallet, butterflies): you change the story, room and score, not the style. Score rendering needs `swift` on macOS or `fluidsynth` plus a soundfont. The film renders at 24 fps on a pinned HyperFrames 0.8.71. The project folder holds the user's own words, so the skill says never to commit or share it.

**Who should use it:** individual users who want a warm, shareable film of what working with their agent looks like.

**Best for:** personal storytelling from real transcripts, with the user approving every word.

---

## 4. vox-explainer

**What it does:** builds a 60–90 s collage-style explainer from a topic, or from documents and links you supply, with numeric gates on cuts and pacing. It lives in the same community repo as session-story ([#70 Animated agent session story — @jake11moran](https://www.prompt-motion.com/jake11moran-a269c4)).

**Pipeline, brief to MP4** ([SKILL.md](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/vox-explainer/SKILL.md)):

1. **Route the request.** In topic mode, a four-part filter guides ideation. In source mode, a "storyline mine" pulls five things from the material: what the audience already knows, the tension, the turn, a mechanism the viewer can verify on screen, and receipts. Any beat the source can't fill honestly is cut, not faked.
2. **Script.** Voice-over plus a beat map; every line has to pass a deletion test.
3. **Design pass.** A contact sheet of real assets, one frame per beat, delivered before any composition is built.
4. **Voice-over.** Record it or use TTS (`npx hyperframes tts` first; any TTS API only after the user approves the provider and cost). Transcribe for word timestamps; the audio is the clock.
5. **Build.** One HyperFrames composition, one clip group per beat.
6. **QC gates.** Lint and check at 0 errors. Any still run over 3 s in the render is a planning bug. Measured seams, event gaps ≤ 3 s per beat, and a keyframe sheet audit.

**Render stack, dependencies, licence.** HyperFrames + GSAP, Node 22+ and a local Chrome. The seam scripts have no npm dependencies. `seam-gate.mjs --project` runs a HyperFrames version pinned in the script (0.8.14) through `npx`; `--url` points it at a preview server you started yourself instead. Apache-2.0.

**What's genuinely clever**

- **A motion law for cuts.** [`references/motion-continuity.md`](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/vox-explainer/references/motion-continuity.md) says scene B enters the way scene A exits: same axis, same direction, matched speed, with both sides moving at the cut. Each film picks one dominant direction (left by default), and the other directions are reserved for meaning. Up is a conclusion, pushing forward on Z goes deeper, pulling back on Z is an arrival. Consecutive seams in opposite directions are banned as "ping-pong".
- **A seam ledger that gets verified.** `ledger.json` holds one row per cut. [`scripts/seam-stamp.mjs`](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/vox-explainer/scripts/seam-stamp.mjs) writes the transition tweens from it. [`scripts/seam-gate.mjs`](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/vox-explainer/scripts/seam-gate.mjs) then measures each cut in headless Chrome. It checks that exits are still moving, entries don't start from rest, directions match the ledger, the two sides never overlap, and the carrier stays continuous within 12 px and 5% ([`references/seam-gate.md`](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/vox-explainer/references/seam-gate.md)). A speed mismatch only raises a warning.
- **A technique floor against slideshows.** Each beat declares its layout recipe and motion treatment up front. Static cards and side-by-sides are capped at a third of the beats, and no two consecutive beats share a recipe. A "zoom-in contract" adds one more rule: a push into a photograph must pay off, either by lifting the subject off the plate or by holding full-frame while callouts draw on it.
- **Honesty about sources.** In source mode, a dead citation is verified independently on the open web or cut.

**Limitations:** the built-in look is a Vox-inspired collage, with a measured palette, Archivo Black headlines and a yellow circle as the recurring carrier. The skill itself states that this implies no affiliation with Vox and that Vox logos must not be used. A brand skin is an explicit opt-in. The format is narration-driven and runs at 30 fps by default. Assets come from public-domain archives. The `--project` mode downloads an older pinned HyperFrames unless you use `--url`.

**Who should use it:** anyone turning a report, memo, paper or topic into a short explainer, especially where continuity between shots matters.

**Best for:** document-to-explainer films with checked pacing and cuts.

---

## 5. motion-studio

**What it does:** works as a small motion-design studio. It splits a brief into three layers, video type (structure) × visual style (look) × motion language (movement), and renders through its own deterministic HTML engine.

**Pipeline, brief to MP4** ([SKILL.md](https://github.com/buildfastwithai/buildfast-skills/blob/main/motion-studio-skill/SKILL.md)):

1. `detect_env.py` checks the machine for Chromium and ffmpeg.
2. `plan.py` resolves the brief into a template, style, motion, format, duration, fps and audio, and lists the defaults it applied.
3. The agent writes a concept and a storyboard. Each scene gets time, purpose, visual, camera, animation, typography, transition and audio.
4. `plan.py --scaffold` writes `spec.json`, `storyboard.md` and a starter `composition.html`.
5. The agent builds the design with the engine.
6. `render.py --stills` produces a contact sheet, `--preview` a half-resolution timing check, and the final render frames → H.264 with generated music and SFX, then 16 QC checks.
7. Fix and re-render, about 3 loops at most.

**Render stack, dependencies, licence.** The engine is [`engine/ms.js`](https://github.com/buildfastwithai/buildfast-skills/blob/main/motion-studio-skill/engine/ms.js). Playwright drives Chromium, calls `window.__ms.render(t)` for each frame and captures it over CDP for ffmpeg. It needs Python 3.9+ with playwright, numpy, scipy and pillow, plus ffmpeg/ffprobe. Three.js and Blender are optional. MIT; the bundled fonts ship with their own OFL licence files.

**What's genuinely clever**

- **A 16-check automated QC.** [`reference/qc.md`](https://github.com/buildfastwithai/buildfast-skills/blob/main/motion-studio-skill/reference/qc.md) uses ffmpeg's `blackdetect`, `freezedetect` and `scdet`. It also audits text against the safe area, caps reading speed at 4.5 words/s with scenes ≥ 0.4 s, and checks that transitions aren't all fades. Every percussive cue needs a distinct attack within 30 ms, and the A/V offset must be ≤ 1 frame.
- **Variants and style-cuts.** `render.py --variants` renders one frozen timeline in several styles and adds a side-by-side comparison video. `stylecut.py` cuts one scene through many styles on the beat.
- **A benchmark mode built for comparing models.** [`reference/benchmark.md`](https://github.com/buildfastwithai/buildfast-skills/blob/main/motion-studio-skill/reference/benchmark.md) freezes the brief, timings, seed and required text, then scores QC hygiene. A variant loses 20 points if two fresh renders differ. The doc says plainly that the score measures hygiene, not craft.
- **Token-driven compositions**, so a restyle changes the spec, not the scenes.

**Limitations:** it is another engine to learn rather than Remotion or HyperFrames. Its breadth (51 styles in 7 families, from minimal to VHS and pixel) means many looks are genre presets. No TTS is bundled, so voice-over needs a recorded file. At this snapshot the repo README's skill table lists five other skills, so the motion skills are easy to miss in the folder list.

**Who should use it:** people who want to see the same storyboard in several looks quickly, or to benchmark coding models on a fixed motion task.

**Best for:** style exploration and reproducible model comparisons.

---

## 6. generative-film

**What it does:** produces a 45–120 s, 1920×1080, 30 fps MP4 in which every frame is drawn in code with pycairo and Pillow and every note is synthesized with numpy and scipy. The skill's reference film, *SŪTRA* (Indian civilisation, 87 s), matches gallery entry [#147 Indian civilisation history film — @BuildFastWithAI](https://www.prompt-motion.com/buildfastwithai-53234e). Its prompt was a single 13-word line asking for "a creative mp4 video on indian civilisation" with music and sound effects ([post](https://x.com/BuildFastWithAI/status/2104451249269780900)). The gallery lists the entry as one-shot.

**Pipeline, brief to MP4** ([SKILL.md](https://github.com/buildfastwithai/buildfast-skills/blob/main/generative-film-skill/SKILL.md)):

1. Setup: pycairo and fonttools, plus a check that Pillow has Raqm for complex scripts.
2. Concept: research every fact that appears on screen, pick a through-line object, a one-word title with a dictionary-style gloss, and 6–10 chapters.
3. Timeline in beats, at 90–110 BPM.
4. Music first, with `audio_kit.py`, targeting about −16 to −14 LUFS.
5. Scenes with `engine.py`.
6. Test frames and a contact sheet, usually 2–3 rounds.
7. Parallel chunked render across all cores, then concat and mux.
8. QA: frame count, a tiled sheet of the final file, spot checks.

**Render stack, dependencies, licence.** Python with pycairo, Pillow (with Raqm), numpy, scipy and fonttools, plus ffmpeg. No browser is involved. Fonts download from the google/fonts GitHub repo on first use. MIT.

**What's genuinely clever**

- **"An idea per chapter, not a picture per chapter."** Each scene has to show a mechanism, such as a city grid being walked or a fractal growing, rather than illustrate a noun. If a chapter could be replaced by a stock photo, it gets rethought.
- **Music is written first.** Everything is timed in beats, so every cut, pop and flash lands on a musical event.
- **Multilingual type that holds up.** Raqm shaping covers Devanagari, Arabic and Tamil, and a `missing_glyphs(font, string)` check catches tofu before render.
- **Self-contained.** The full [`engine.py`](https://github.com/buildfastwithai/buildfast-skills/blob/main/generative-film-skill/scripts/engine.py) and [`audio_kit.py`](https://github.com/buildfastwithai/buildfast-skills/blob/main/generative-film-skill/scripts/audio_kit.py) are also printed as appendices in SKILL.md. The [`examples/sutra/`](https://github.com/buildfastwithai/buildfast-skills/tree/main/generative-film-skill/examples/sutra) folder holds the reference film's source.

**Limitations:** the setup line uses `pip install --break-system-packages`, which writes into the system Python; a virtual environment is the safer route. Fonts are fetched from GitHub at run time. The built-in art direction is strong (risograph print proof, mis-registered inks, glitch stutters, a white flash on the drop), which is less suited to brand-strict work. The delivery steps are written for a hosted sandbox (a 30 MB chat upload limit and file-send tools), so local agents need to adapt them. By the author's figure, SŪTRA took about 20 minutes to render on 2 cores.

**Who should use it:** creators making cultural, history or science shorts who want a distinctive graphic look without a browser in the loop.

**Best for:** code-drawn documentary shorts with a synthesized, beat-synced score.

---

## 7. canvas-documentary (html-animation-skill)

**What it does:** builds a cinematic story in chapters, with camera work, procedural art, generated sound and playback controls, as a single self-contained HTML canvas file. The output is an interactive page, not an MP4.

**Pipeline** ([`html-animation-skill.md`](https://github.com/buildfastwithai/buildfast-skills/blob/main/html-animation-skill/html-animation-skill.md)):

1. Script first: 6–10 chapters of 12–20 s each (about 2 min), with timed captions.
2. A fixed architecture in which every scene is a pure function of its local time.
3. Web Audio sound.
4. A transport bar with keyboard shortcuts.
5. Write the file in parts and check the syntax with `node --check`.
6. Watch it in headless Playwright: screenshot every named story beat, then sweep the runtime in 2 s steps at desktop and phone sizes.

**Render stack, dependencies, licence.** Plain HTML with Canvas 2D and Web Audio, no libraries and no network at runtime. Playwright is used only for verification. MIT.

**What's genuinely clever:** because every scene is deterministic in its local time, seeking is free, for the scrubber and for automated screenshots alike. A single Hermite spline drives every motion path, and facing direction is derived from velocity. The narration rule is "states facts, never describes the picture". Interaction is diegetic: the subject banks away from the cursor. There is also a short list of failures the verification pass "catches every time".

**Limitations:** to get a video you have to capture the page yourself. The skill is a single file named `html-animation-skill.md` whose front matter is `name: canvas-documentary`, not a `SKILL.md`, so installers that look for `SKILL.md` may not find it; copy it in by hand. The verification step assumes a preinstalled headless Chromium.

**Who should use it:** people making interactive nature or science stories for the web, where viewers scrub, pause and click.

**Best for:** interactive story pages rather than rendered video.

---

## 8. The other HyperFrames community skills

The same repo holds six more video skills. Its README warns that community skills sit outside the curated HyperFrames set and should be reviewed before use. Each folder documents its network access and side effects.

| Skill | What it makes | Stack and notable dependencies | Best for |
|---|---|---|---|
| [duo](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/duo/SKILL.md) | Two HTML screens composited into a fixed photo of hands holding an open foldable phone, 1448×1086 at 30 fps | HyperFrames `@latest` (unpinned); GSAP 3.14.2 from jsDelivr at render time | Side-by-side comparison and meme clips |
| [camera-3d-captions](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/camera-3d-captions/SKILL.md) | Captions placed in 3D around a static-camera talking head: depth groups, words behind the speaker via an alpha matte, a ring of words; 5–20 s pieces | HyperFrames 0.8.62; local `remove-background` model (about 170 MB, first run); Python fonttools, numpy, pillow | Talking-head and avatar clips that need depth captions |
| [x-posting-license](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/x-posting-license/SKILL.md) | A 10.35 s, 1920×1080, 60 fps "posting license" card for an X profile from a locked template; `build.mjs` validates and HTML-escapes every input | HyperFrames; reads public profile data; styled in X's branding | Novelty profile cards; check X's brand terms before publishing |
| [day-in-my-life](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/day-in-my-life/SKILL.md) | A 60–75 s hand-drawn ink film of one average session, with a string score; needs at least 10 local sessions over 5 days | HyperFrames 0.8.70; p5 2.3.2 (LGPL-2.1), p5.brush, puppeteer; numpy and scipy for the score | Personal session films in an ink style |
| [prod-by-claude](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/prod-by-claude/SKILL.md) | A 1080×1080 video of a Strudel live-coding track in which every code token lights up on the note it plays | HyperFrames 0.8.70; `@strudel/web` 1.3.0 (AGPL-3.0, installed from npm); puppeteer-core; Chrome for Testing | Musicians and live coders |
| [p5-paint-animation](https://github.com/heygen-com/hyperframes-community-skills/blob/master/skills/p5-paint-animation/SKILL.md) | Handwriting that writes itself, photos repainted as brushstrokes, short clips repainted frame by frame | Puppeteer + ffmpeg (HyperFrames only for optional matting); p5 2.3.2, p5.brush 2.2.1; about 5–20 s per frame | Hand-made textures and write-on effects (not crisp brand type) |

HyperFrames pins differ across this repo: 0.8.14 in the vox-explainer seam gate, then 0.8.62, 0.8.70 and 0.8.71, with `@latest` in duo and x-posting-license. Pair each skill with the version it was tested on.

---

## 9. Ideas worth borrowing, whatever engine you use

These ideas work outside the skill they come from, and most need nothing installed.

| Idea | Where it comes from | Why it helps |
|---|---|---|
| One beat grid drives picture, sound and checks | cinetic `timeline.ts`; product-film `cues.ts`; generative-film's beats | Picture and sound can't drift apart, and checks read the same numbers |
| Compute sound cues from the motion curves | cinetic `sync.ts` / `FILM.cues()` | The author measured hand-typed cues landing 8–11 frames off |
| Draw techniques at random from a library | cinetic `pick.py` | Breaks the habit of the same fade-up, push-in and end card |
| Keep a seam ledger and verify it | vox-explainer `ledger.json` + `seam-gate.mjs` | Catches cuts that start from rest, settled exits and direction ping-pong |
| Compile one story file into both picture and score | session-story `schedule.mjs` | One edit re-times both tracks |
| Decode the delivered file and check the colours | product-film `verify.py` | Catches colour-range shifts the editor never shows |
| Render PNGs, encode once, dither gradients | cinetic `hf-finish.sh`, `dither-gradient.py` | Avoids double compression and banding on dark gradients |
| Run pixel forensics on the final MP4 | cinetic `forensics.py`; motion-studio `qc.py` | Finds pops, freezes, black frames and unexpected cuts |
| Set hard reading limits | cinetic: 36 f + 6 f per word at 60 fps; motion-studio: ≤ 4.5 words/s | Text stays on screen long enough to read |
| Fail on dead air; gate real quotes | session-story `score/qc.py` and its approval table | Silence becomes a bug report; nobody sees words they didn't approve |

**A zero-install first step.** Take a film you've already made and export a contact sheet with any ffmpeg tile filter. Score it against cinetic's 11-dimension rubric in [`references/review-loop.md` §9](https://github.com/Leonxlnx/cinetic/blob/main/skills/cinetic/references/review-loop.md). Finish and Sync need its scripts, so leave those two for later. Then write a `ledger.json` for the same film's cuts in vox-explainer's format. Writing the table alone often shows direction flips and cuts that start from rest.

---

## 10. Which one to pick

| If you want… | Start with |
|---|---|
| A launch film, sting or loop with measured QA, and you can afford a long run | cinetic |
| A film that looks exactly like your product, built from your own components | product-film (budget for Remotion's licence if it applies) |
| To stay in HyperFrames | cinetic with `--engine hyperframes`, or vox-explainer |
| An explainer from a document or topic | vox-explainer |
| The same storyboard in several looks, or a model benchmark | motion-studio |
| A graphic documentary short without a browser | generative-film |
| An interactive story page | canvas-documentary |
| A personal film of your agent sessions | session-story (watercolour) or day-in-my-life (ink) |

All of these skills can run commands, read files and, in places, call network services. Read the `SKILL.md` and the scripts before installing one, as the HyperFrames community README itself advises.

---

## 11. Method & caveats

- **Read-only.** We read each repo at the snapshot commit listed [above](#the-repos-at-a-glance): `SKILL.md`, references and script headers. We did not install or run anything.
- **Numbers from the repos are the authors' figures**, and the text attributes them that way. That covers render times, token costs, evaluation results and measured offsets. We have not reproduced them.
- **Counts we computed ourselves:** the 273 techniques and 14 categories in cinetic's library, motion-studio's 51 styles, 10 motion languages and 13 templates, and the 4-of-233 and stack figures from `catalog.json`.
- **Licences** come from each repo's `LICENSE` file and the third-party notices inside the skills. Engine and library licences (Remotion, p5, Strudel) are summarized as the repos state them; read the originals before commercial use.
- **This page uses no quality scores.** Gallery entries are cited only to show what each skill produced, not to rank the videos.
- **Snapshots age.** Skills in this space are changing weekly. Check the repo's changelog or commit history for anything newer than the commits listed here.
