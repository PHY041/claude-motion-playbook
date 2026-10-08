# Ecosystem: collections like prompt-motion.com

A map of every site and repository we could find that does what [prompt-motion.com](https://www.prompt-motion.com/) does (AI-made motion videos, each paired with the prompt, source or skill behind it), plus the framework showcases, skill directories and inspiration galleries around it. Snapshot of **2026-10-09**. Item counts are what each site stated on the day it was checked; they change daily.

For scale: prompt-motion.com itself, curated by [@p4nthera_](https://x.com/p4nthera_), holds 233 entries (see [top picks](top-picks.md)).

[简体中文版](zh/ecosystem.md)

## TL;DR

- **100 distinct projects.** The verified list had 132 rows, and many were the same project seen twice: EN and ZH pages, a site and its GitHub source, or several pages of one site. We merged them into one row per project. 55 more candidates were checked and dropped.
- **The biggest prompt galleries** (re-checked 2026-10-09): [Oneshotted](https://oneshotted.io/) 6,164 recipes, about 26 times prompt-motion.com · [24fps](https://24fps.dev) 4,607 clips · [JasonZhu.AI](https://jasonzhu.ai/en/prompts/claude-opus-5-5) 1,402 works · [Claude Video](https://claudevideo.org/) 1,276 videos · [Awesome AI Motion](https://guanmo-ai.github.io/awesome-ai-motion/) 581 cases · [Skillry](https://skillry.dev/ai-videos/opus-5-5) 513 Opus 5.5 + 80 Fable 5.5 videos.
- **A full prompt is the exception, not the rule.** Many creators posted the video without the prompt. Items carrying a prompt: 24fps 1,073 of 4,607 (23%); JasonZhu.AI 361 of 1,402 (26%), of which 148 (11%) are full; Claude Video 457 of 1,276 (36%); Awesome AI Motion 83 of 581 (14%) marked "original".
- **The collections overlap heavily** because they draw on the same wave of X posts from late September 2026. All 470 Tellcut posts also appear in WorkSkill. 333 of HiAPIAI's 425 ids are in Skillry's data. TopView's Opus items come from YouMind. 24fps says it draws on 129 GitHub collections.
- **Where to start:** Oneshotted (largest, labels where each prompt came from, has an MCP server), 24fps (states rights per clip, offers MCP/API, shows one prompt run 109 times), Skillry and its MIT dataset (original and remake side by side), JasonZhu.AI (bilingual, prompt status on every card), and the HyperFrames docs (18 prompts rendered unedited, plus 400 blocks with source).
- **Open data with a licence:** [yihui-dev/awesome-opus5-5-videos](https://github.com/yihui-dev/awesome-opus5-5-videos) (MIT, 513 rows, 3,101★), guanmo-ai (MIT for code), Li-Evan (CC-BY-4.0 for the curation) and athemeroy (CC-BY-4.0). Several popular lists have no licence file. No repo licence covers the creators' prompts or videos.
- **Terms differ.** Oneshotted, Swishy, Pexo, AutoAE, 60fps.design and MotionSites forbid scraping in their terms, and several of them offer an MCP server or API instead. See [§7](#7-using-these-collections-responsibly).

## Contents

1. [Scale and where to start](#1-scale-and-where-to-start)
2. [Direct analogs: AI-made motion + prompt per item](#2-direct-analogs-ai-made-motion--prompt-per-item)
3. [Open-source lists and datasets on GitHub](#3-open-source-lists-and-datasets-on-github)
4. [Framework showcases and template libraries](#4-framework-showcases-and-template-libraries)
5. [Skills and skill directories](#5-skills-and-skill-directories)
6. [Web-motion inspiration galleries (no prompts)](#6-web-motion-inspiration-galleries-no-prompts)
7. [Using these collections responsibly](#7-using-these-collections-responsibly)
8. [Method](#8-method)

---

## 1. Scale and where to start

### The largest collections

| Collection | Items (as stated) | With a prompt | Checked |
|---|---|---|---|
| [Oneshotted](https://oneshotted.io/) | 6,164 recipes from 3,716 creators | 3,838 prompts (site's count) | 2026-10-09; 6,144 the day before |
| [24fps](https://24fps.dev) | 4,607 clips, 2,540 creators, 44 models | 1,073 | Counts dated 2026-10-03, unchanged on 10-09 |
| [JasonZhu.AI](https://jasonzhu.ai/en/prompts/claude-opus-5-5) | 1,402 works, 838 creators | 361 (148 full) | 2026-10-09; site updated 10-08 |
| [Claude Video](https://claudevideo.org/) | 1,276 videos, 1,007 creators | 457 with full prompt | 2026-10-09 |
| [Awesome AI Motion](https://guanmo-ai.github.io/awesome-ai-motion/) | 581 cases | 83 original, 118 brief | 2026-10-09; data from 10-06 |
| [Skillry](https://skillry.dev/ai-videos/opus-5-5) | 513 Opus 5.5 + 80 Fable 5.5 | Opus: 279 full, 234 flagged partial | 2026-10-09 |
| [WorkSkill](https://workskill.tools/ai-videos/opus-5-5) | 478 Opus 5.5 + 76 Fable 5.5 | A prompt block per case, length varies | 2026-10-09 |
| [Tellcut](https://tellcut.app/examples) | 470 | 276 full, 194 excerpts | 2026-10-09 |

Larger, but not the same kind of collection: [TopView](https://www.topview.ai/video-prompts) has 12,430 video prompts, mostly for generative-video models. [What Ships](https://whatships.com) has 2,447 launch films made by studios and teams. The [HyperFrames Studio community](https://www.hyperframes.dev/?view=community) has 949 projects, each with its source.

### Where to start

1. **[Oneshotted](https://oneshotted.io/): for range.** It is the largest collection. It separates the creator's own prompt from a reconstruction labelled "rebuilt from the video's frames". It filters by framework (Remotion, HyperFrames, GSAP, Three.js, Motion Canvas, Manim). An MCP server and an agent skill let a coding agent search it within the stated limits.
2. **[24fps](https://24fps.dev): for an agent-friendly index with clear rights.** Every clip says what you may do with it, and 395 clips are open-licensed with source. It offers an MCP server, a JSON API and `llms-full.txt`. Its "one prompt, 109 runs" page shows how much a single brief varies from run to run.
3. **[Skillry](https://skillry.dev/ai-videos/opus-5-5) + [yihui-dev/awesome-opus5-5-videos](https://github.com/yihui-dev/awesome-opus5-5-videos): for clean data.** This is an MIT-licensed JSON of 513 entries that flags partial prompts. The site plays each original next to a live remake.
4. **[JasonZhu.AI](https://jasonzhu.ai/en/prompts/claude-opus-5-5): for sorting by how complete the prompt is.** It is bilingual EN/ZH. Each card shows whether the prompt is full (with a character count), brief or missing, and whether you need your own reference assets.
5. **HyperFrames docs ([prompt examples](https://hyperframes.heygen.com/prompting/examples), [catalog](https://hyperframes.heygen.com/catalog)): for prompt and output you can trust.** 18 videos are each labelled as rendered unedited from the prompt shown. The catalog has 400 blocks and components with source under Apache-2.0.

---

## 2. Direct analogs: AI-made motion + prompt per item

These sites collect motion pieces made by AI coding agents from many creators and attach a prompt (or source) to each item. They are sorted by size. Nearly all of them credit and link the creator's X post.

### 2a. Large galleries (250+ items)

| Collection | Items | What ships | Notes |
|---|---|---|---|
| [Oneshotted](https://oneshotted.io/) | 6,164 recipes, 3,838 prompts, 3,716 creators | The creator's prompt where one was published; a separately labelled reconstruction; MCP server; agent skill | Flags prompts "not yet confirmed on X". About 4,950 items are video types; the rest are web-UI motion or "other". |
| [24fps](https://24fps.dev) | 4,607 clips, 2,540 creators, 44 models | Prompt for 1,073 (in full up to 280 characters, otherwise an excerpt and a link); source for 395 open-licensed clips; MCP, JSON API, `llms-full.txt`, skill; 2,125 editor presets | Says it draws on 129 GitHub collections, creators' posts and the open web. Clips play through X embeds. 55% of clips have no framework recorded. |
| [JasonZhu.AI](https://jasonzhu.ai/en/prompts/claude-opus-5-5) ([中文](https://jasonzhu.ai/zh/prompts/claude-opus-5-5)) | 1,402 works, 838 creators | Prompt for 361, 148 of them full | Bilingual. Prompt status and a "needs your own reference assets" flag on every card. Covers Opus, Sonnet and Fable 5.5, and also includes games (233) and model comparisons (186). Source: [zhuyansen/awesome-opus-5.5-video](https://github.com/zhuyansen/awesome-opus-5.5-video). |
| [Claude Video](https://claudevideo.org/) | 1,276 videos, 1,007 creators | Full prompt for 457; editorial notes and a "make one like this" guide per entry; a directory of 247 skills | Can sort by "has prompt". Publishes `llms.txt` for agents. |
| [Awesome AI Motion](https://guanmo-ai.github.io/awesome-ai-motion/) (guanmo-ai) | 581 cases | Prompt status per case (83 original, 118 brief, 380 unknown); 62 cases link code, demos or tools | Titles and summaries in ZH and EN; everything is in one `cases.json`. Some cases were made with generative-video models (Seedance, Kling, Veo), not code. |
| [Skillry](https://skillry.dev/ai-videos/opus-5-5) ([中文](https://skillry.dev/zh/ai-videos/opus-5-5), [Fable 5.5](https://skillry.dev/ai-videos/fable-5-5)) | 513 Opus 5.5 + 80 Fable 5.5 videos | Opus: a prompt per entry (279 full, 234 flagged partial). Fable: 8 of 80 have one | Plays the original and a live remake side by side and links installable skills. Data: [yihui-dev/awesome-opus5-5-videos](https://github.com/yihui-dev/awesome-opus5-5-videos) and [awesome-fable5-5-videos](https://github.com/yihui-dev/awesome-fable5-5-videos) (MIT). |
| [WorkSkill](https://workskill.tools/ai-videos/opus-5-5) | 478 Opus 5.5 + 76 Fable 5.5 | Prompt block, credit and a self-hosted MP4 per case | Contains all 470 Tellcut posts plus newer ones up to 2026-10-07. Data: [mailes/awesome-claude-5-5-videos](https://github.com/mailes/awesome-claude-5-5-videos) (MIT). Some prompt fields are only a title or one line. |
| [Tellcut examples](https://tellcut.app/examples) (opus6.video redirects here) | 470 | Full prompt for 276, excerpt for 194 | Each card says whether its prompt is full or an excerpt. Videos open on X. The whole set is one `examples.json`. A sibling page, [/effects](https://tellcut.app/effects), has 21 effects with prompts. |
| [YouMind](https://youmind.com/opus-5-5-prompts) ([中文](https://youmind.com/zh-CN/opus-5-5-prompts)) | 340 Opus 5.5 items | Full prompt plus a translation, MP4, credit | About 15 locales, including ja-JP. Many items are interactive Three.js pages. A [web-page prompt hub](https://youmind.com/prompts/webpage) adds 452 GPT 6 Astra and 49 Gemini 3 Pro prompts. |
| [Awesome Opus 5.5 Video Prompts](https://li-evan.github.io/awesome-opus-5.5-video-prompts/) (Li-Evan) | 334 entries, 302 creators | Verbatim prompt plus a Chinese translation, tagged by kind (one-shot 190, brief 77, spec 24, template 23, pipeline 20) | The README says a validator checks that every prompt is a verbatim substring of the creator's post. Includes a director's toolkit (workflow, anatomy, vocabulary). Last updated 2026-09-27. |
| [Skilloop](https://skilloop.dev/ai-video/opus-5-5) ([中文](https://skilloop.dev/zh/ai-video/opus-5-5)) | 278 Opus 5.5 + 45 Fable 5.5 cases | Some prompt for about 161 of 278 (133 full texts come from the yihui-dev list); other pages say the author did not publish one | Source repos: [xianyu110/awesome-claude-opus-5.5](https://github.com/xianyu110/awesome-claude-opus-5.5) (281 curated cases, 144 with a prompt, plus a wider list of 1,019) and [awesome-fable-5.5](https://github.com/xianyu110/awesome-fable-5.5) (54 cases, 16 with a prompt). |
| [Awesome Opus 5.5 Videos](https://img.dsxzai.com/) (chuspeeism) | 300 Opus 5.5 cases (plus 485 image cases) | The creator's prompt for 36; a production note for the rest | Chinese UI with a public JSON API; the repo is MIT. Last updated 2026-09-27. |
| [BeatAPI](https://beatapi.io/opus-5-5-videos) | 302 cases; a [GPT-6 Astra 3D page](https://beatapi.io/gpt-6-astra-3d-prompts) with 306 more | Opus: each card links to the prompt file in the yihui-dev repo. 3D: each prompt is labelled exact (47), creator-stated (163) or source-stated (96) | 282 of the 302 Opus cases are pinned from yihui-dev. 3D data: [BeatAPI/awesome-3d-prompts](https://github.com/BeatAPI/awesome-3d-prompts) (MIT). |
| [TopView video prompts](https://www.topview.ai/video-prompts?q=opus) | 12,430 video prompts, about 261 of them matching "opus" | Prompt, MP4, credit | Mostly prompts for generative-video models (Seedance, Grok). The Opus items are mirrored from YouMind. Its [Abstract VFX](https://www.topview.ai/abstract-vfx-v-subject-video-prompts) category holds many code-made pieces. |

### 2b. Smaller curated galleries

| Collection | Items | What ships | Notes |
|---|---|---|---|
| [Remotion Prompt Showcase](https://www.remotion.dev/prompts) | 25 | Full prompt, plus the tool and model used | Official. Models range from Opus 4.5 to 4.7 plus Kimi K2.5; the newest entry is from about May 2026. Part of Remotion ([§4](#4-framework-showcases-and-template-libraries)). |
| [HyperFrames example prompts](https://hyperframes.heygen.com/prompting/examples) | 18 | Verbatim prompt; each video is labelled as rendered unedited from it | Official docs, with a shared motion preamble. 8 use registry blocks or skills; 10 are freeform. Part of HyperFrames ([§4](#4-framework-showcases-and-template-libraries)). |
| [Searchable gallery](https://eastling.github.io/awesome-opus-5.5-video-prompts/) (eastling) | 90 + starter templates | Full prompt, a one-line "why it works" note and tech tags | Starter templates carry structure notes per film type. All 90 posts also appear in Tellcut; the repo's homepage is opus6.video. The list is CC0. |
| [AI × Leaders](https://ai-x-leaders.com/en/prompt/) | 80 | A prompt status per item (16 complete, 13 verified source, 20 excerpt, 23 unverified, among others) | Separate Claude and OpenAI tabs, export, and a `catalogue.json`. |
| [APIModels](https://apimodels.app/claude-opus-5-5-video-prompts) | 60 case studies | A copyable prompt for about 24; the rest are marked not published | Each case lists toolchain, duration, resolution, cost, pitfalls and "same prompt, other runs". Also has a prompt formula and six workflow templates. |
| [Claude Video Atlas](https://yeadon8888.github.io/claude-video-atlas/) | 53 | The creator's prompt for 5 and MIT source for 4; the rest carry a curator template, labelled as such | Sources beyond X: 小红书, 抖音, YouTube and GitHub. Only 4 of its 44 creators also appear on prompt-motion.com. Last updated 2026-09-26. |
| [AY Automate](https://www.ayautomate.com/resources/claude-opus-5-5-motion-graphics) | 48 posts | The creator's full prompt for 10, copied word for word | Posts pulled 2026-09-28. Filters include showreel, landing pages, and 3D & physics. |
| [AI9app](https://ai9app.io/video-prompts/opus-5-5) | 30 | Free full prompt, X credit and a mirrored video | Many titles are in Traditional Chinese. |
| [mg-styles-15](https://vincentwei1021.github.io/mg-styles-15/) | 15 films | Prompt, source and MP4 for each film, plus a grading rubric | One author covering 15 motion-design styles; MIT. |
| [Opus 5.5 统一效果图鉴](https://github.com/jinhanbuilds/opus-5-5-unified-gallery) (jinhanbuilds) | 122 demos, 15 of them video-type | The original prompt per item; a 75-keyword motion lexicon and prompt builder | Chinese. Most items are interactive pages from MiaAI-Lab's 100-HTML set; the 15 video demos were rebuilt from their prompts. |
| [Made with Motion](https://motion.so/made-with-motion) (Mosaic) | 8 | A one-line prompt, a 4-step workflow and an MP4 | Agent-made launch and explainer films. Last updated 2026-06-18. |
| [Muzli: Opus 5.5 for designers](https://muz.li/blog/claude-opus-5-5-for-designers/) | 3 demos | Full prompt plus standalone HTML for each | One demo is a 12-second kinetic-type title sequence on a single GSAP timeline. Also has a brief template and a sample `CLAUDE.md` design-rules block. |

### 2c. Tool, vendor and single-team galleries

Each item comes with a prompt or source, but everything here was made with one product or by one team.

| Gallery | Items | What ships | Notes |
|---|---|---|---|
| [showtime examples](https://faviovazquez.github.io/showtime/gallery.html) | 32 | The exact request given to the agent, plus full project source | Launch, PR, explainer and trailer examples from one tool; MIT. |
| [Claude Imagine](https://claudeimagine.com/opus-5-5-video) | 30 remakes | Full HyperFrames source per template (MIT); one shared "rebuild from contact sheets" prompt | Re-implementations using fictional brands; each credits the post that inspired it. |
| [ChatCut prompt library](https://chatcut.io/prompt-library) | 133 cards | A prompt entry and preview each; Remotion TSX for about 104 | One vendor's templates. "Try this prompt" opens the ChatCut app. |
| [Swishy](https://www.swishy.ai/) | 143 templates | The prompt a Swishy user wrote, plus the Remotion scene source | Templates are on the homepage and at `/templates/<slug>`. Most are short UI and social snippets. |
| [iArt.ai templates](https://www.iart.ai/templates) | 23 curated, plus a larger community feed | Prompt and multi-clip GSAP/Remotion code, shown in the app's share view | Shows creator names and remix counts. |
| [Hera](https://www.hera.video/templates) | 13 templates + 11 shared projects | Templates have prompts with placeholders; shared projects expose the prompt chain and the GSAP HTML | Shared items date from 2025. The full gallery needs a login. |
| [Pexo gallery](https://pexo.ai/gallery) | 712 videos, about 200 of them motion-related | A structured prompt and MP4 per video | Mostly generative-video output (Seedance, Kling, MiniMax). The prompts are structured briefs (subject, style, camera, lighting). |
| [Motion Face](https://motionface.cc/) | 95 clips | Each clip is bound to a Remotion source repo, unlocked with credits | Chinese. Many clips are Remotion remakes. Also runs a board of paid Opus 5.5 tasks. Playback needs a login. |
| [Leon's demos](https://leons-demos.vercel.app) | 58 cards, 11 of them video | A repo link for 11 and a prompt for 1 | One creator's X posts. Links to the cinetic and claude-launchvideo repos. |
| [PremiereCopilot Vibe Motion](https://www.premierecopilot.com/vibe-motion) | 11 | The exact prompt and an MP4 | Part of the product page for a Premiere Pro plugin. |

### 2d. AI-made work without per-item prompts

| Gallery | Items | What ships | Notes |
|---|---|---|---|
| [Revid: Claude Opus 5.5 motion graphics](https://www.revid.ai/claude-motion-graphics) | 64 videos | MP4, credit and engagement counts; no creator prompts | Ranked by engagement and includes 17 launch films. 40 of its 55 creators are not on prompt-motion.com. Covers posts from 2026-09-23 to 09-27. |
| [Frontier Games](https://theolundqvist.github.io/frontier-games/) | 127 games + 80 films | Playable builds and the creators' footage | Opus 5.5 (65 games) next to GPT-6 Astra (62). No licence file. |

**Copies of prompt-motion.com itself.** We found two copies of prompt-motion.com's own entries: a GitHub repository with 229 prompt files and a separate domain listing 230 entries whose slugs all match. They add no new items, so they are not in the count. Use the original.

---

## 3. Open-source lists and datasets on GitHub

### 3a. GitHub-first lists

| Repository | Items | Licence | Notes |
|---|---|---|---|
| [athemeroy/awesome-claude-5-5-videos](https://github.com/athemeroy/awesome-claude-5-5-videos) | 168 reviewed cases; a corpus of 1,511 candidate posts | CC-BY-4.0 | A research index. Cases are grouped by production path (procedural 2D 52, explainer 27, 3D/real-time 19), with CSVs on prompt overlap, prompt length and style. 134 of its 150 creators are not on prompt-motion.com. 497★. |
| [LeaddeOpenLab/awesome-opus-5-5-video-prompts](https://github.com/LeaddeOpenLab/awesome-opus-5-5-video-prompts) | 398 | None | Each prompt has provenance fields (disclosure, verification status, source text range) and a GIF. About 141 of its posts are not in WorkSkill or Tellcut. |
| [HiAPIAI/awesome-opus-5-5-video-styles](https://github.com/HiAPIAI/awesome-opus-5-5-video-styles) | 425 prompts in 12 styles | CC-BY-4.0 (prompts and media excluded) | A recipe per style, e.g. Product UI promo (80) and kinetic typography (52). Stills only, no video. 333 of its 425 ids are in Skillry's data. |
| [X-RayLuan/awesome-opus-5-5-video-prompts](https://github.com/X-RayLuan/awesome-opus-5-5-video-prompts) | 83 | MIT for docs and tooling; RIGHTS.md for media | EN and 中文. Clips are served through jsDelivr, and prompts are marked verbatim. 64 of its 83 posts are not in WorkSkill. |
| [opusvideo/awesome-claude-video](https://github.com/opusvideo/awesome-claude-video) | 59 | None | About 25 step-by-step implementation guides in EN and ZH. 21 entries have a prompt or brief. Only posts with more than 10K views are included. |
| [joeseesun/opus-video-prompts](https://github.com/joeseesun/opus-video-prompts) | 54 cases, 18 full prompts | None | Organised by 9 technical routes. Covers launch week, 09-22 to 09-25. |
| [real-leo/awesome-opus-videos-aggregate](https://github.com/real-leo/awesome-opus-videos-aggregate) | 846 rows, deduplicated from 4 lists | CC BY 4.0 | A meta-index; a single commit on 2026-09-28. |
| [cindyxu1030/motion-graphics-prompt-bank](https://github.com/cindyxu1030/motion-graphics-prompt-bank) | 57 prompts with GIFs | CC BY-NC-SA 4.0 | One author. HyperFrames prompts with placeholders; 15 launch-trailer scenes were reverse-engineered from AI-product launch films. |
| [maning636/motion-prompts](https://github.com/maning636/motion-prompts) | 379 prompts; the hub has 1,004 templates with previews | Custom, not OSI | Chinese; single-file GSAP HTML. The licence forbids repackaging or re-uploading the prompts. |
| [Markjinli/awesome-hyperframes-prompt](https://github.com/Markjinli/awesome-hyperframes-prompt) | 28 templates | None | `prompt.md` plus `index.html` per template; Chinese. Last push 2026-05-14. |

### 3b. The data behind the websites

Several sites in §2 publish their data. A repository licence covers the repository's own text and code. The prompts and videos remain the creators' work in every case.

| Site | Dataset | Licence | Rows |
|---|---|---|---|
| Skillry | [yihui-dev/awesome-opus5-5-videos](https://github.com/yihui-dev/awesome-opus5-5-videos) `data/videos.json` (+ awesome-fable5-5-videos) | MIT | 513 (+80) |
| WorkSkill | [mailes/awesome-claude-5-5-videos](https://github.com/mailes/awesome-claude-5-5-videos) `data/opus-5-5.json` | MIT | 477 (+76 Fable) |
| JasonZhu.AI | [zhuyansen/awesome-opus-5.5-video](https://github.com/zhuyansen/awesome-opus-5.5-video) `cases.json` | No licence file | 1,402 |
| Skilloop | [xianyu110/awesome-claude-opus-5.5](https://github.com/xianyu110/awesome-claude-opus-5.5) `data/selected.json` | No licence file | 281 (+1,019 in the wider list) |
| Awesome AI Motion | [guanmo-ai/awesome-ai-motion](https://github.com/guanmo-ai/awesome-ai-motion) `data/cases.json` | MIT for code and docs; third-party material excluded | 581 |
| Li-Evan | [Li-Evan/awesome-opus-5.5-video-prompts](https://github.com/Li-Evan/awesome-opus-5.5-video-prompts) `site/data.json` | CC-BY-4.0 for the curation | 334 |
| eastling | [eastling/awesome-opus-5.5-video-prompts](https://github.com/eastling/awesome-opus-5.5-video-prompts) `data/prompts.json` | CC0 for the list | 90 |
| chuspeeism | [chuspeeism/awesome-opus-5-5-videos](https://github.com/chuspeeism/awesome-opus-5-5-videos) `data/cases.json` | MIT for the repo text | 300 |
| Claude Video Atlas | [Yeadon8888/claude-video-atlas](https://github.com/Yeadon8888/claude-video-atlas) `data/cases.json` | MIT for the site code | 53 |
| Tellcut | `tellcut.app/data/examples.json` (no repo) | Not stated | 470 |
| 24fps | `24fps.dev/llms-full.txt` (no repo) | Per-clip rights page | 4,607 |

### 3c. How the collections feed each other

- **yihui-dev → many.** Skillry is built on it. BeatAPI pins 282 of its cases. Skilloop took 133 full prompt texts from it. HiAPIAI says it is partly derived from it. real-leo aggregates it.
- **Tellcut ⊂ WorkSkill, and eastling ⊂ Tellcut.** Every Tellcut post is in WorkSkill, and every eastling post is in Tellcut.
- **YouMind → TopView.** TopView's Opus items carry `source_type: youmind`.
- **24fps** says its counts come from 129 GitHub collections, creators' posts and the open web.
- **guanmo-ai's** `THIRD_PARTY.md` cites joeseesun, athemeroy and Frontier Games.
- **Claude Video's** skills page is built from the [awesome-claude-video-skills](https://github.com/zhuyansen/awesome-claude-video-skills) list (CC0).

The practical upshot: when you need the original prompt, follow the credit to the creator's own post. Most of these collections quote the same posts.

---

## 4. Framework showcases and template libraries

### 4a. HyperFrames (HeyGen)

The framework repo [heygen-com/hyperframes](https://github.com/heygen-com/hyperframes) is Apache-2.0 and had 59,087★ on 2026-10-09. Its official surfaces:

| Surface | Items | What ships | Notes |
|---|---|---|---|
| [Prompt examples](https://hyperframes.heygen.com/prompting/examples) | 18 videos | The verbatim prompt; each video is labelled as rendered unedited | A shared preamble is pasted before every prompt. Also available as `/prompting/examples.md`. |
| [Catalog](https://hyperframes.heygen.com/catalog) | 400 (170 blocks, 222 components, 8 examples) | Preview video, source, and an `npx hyperframes add <name>` command | Every page has a `.md` twin with the composition HTML. |
| [Examples / showcase](https://hyperframes.heygen.com/examples) | About 23 films, plus 2 reference-vs-replica pairs | 11 films include source, held in [hyperframes-launches](https://github.com/heygen-com/hyperframes-launches) (20 project folders with storyboards and briefs) | Bundled media, logos and fonts are excluded from the licence. |
| [30 Days of HyperFrames](https://hyperframes.heygen.com/thirty-days) | 30 lessons | An MP4 and an X post with copy-paste prompts for each | The prompts live in the X posts. |
| [Studio community](https://www.hyperframes.dev/?view=community) | 949 projects from 861 users (34 featured, 86 with a rendered MP4) | Full composition HTML per project | robots.txt disallows `/api/`. |
| [Community skills](https://github.com/heygen-com/hyperframes-community-skills) | 8 skills | `SKILL.md` plus scripts | Apache-2.0. The README asks you to review each skill before installing. |

### 4b. Remotion ecosystem

| Project | Items | What ships | Licence / notes |
|---|---|---|---|
| [Remotion](https://www.remotion.dev/showcase) (official) | [Prompt showcase](https://www.remotion.dev/prompts) 25; [showcase](https://www.remotion.dev/showcase) 80, 3 with source; [elements](https://www.remotion.dev/elements) 42; [resources](https://www.remotion.dev/docs/resources/) about 200 links | Prompts, product videos, components with code, and a link directory | Remotion License: companies above 3 employees need a paid company licence. |
| [Remocn](https://remocn.dev) | 364 registry items; 55 showcase launch videos | Component TSX with copy-prompt buttons; showcase source in remocn-collections | Main repo MIT; remocn-collections has no licence file. |
| [snapcn](https://snapcn.dev) | 46 free + 51 Pro components; 6 workflow skills | A live player, copy-prompt button and choreography notes per component | Free tier MIT; Pro is paid. |
| [RenderComp free templates](https://rendercomp.com/free) | 50 | Source plus an MP4 preview | MIT ([GitHub](https://github.com/RenderComp/free-remotion-templates)). |

### 4c. GSAP and web animation

| Project | Items | What ships | Licence / notes |
|---|---|---|---|
| [GSAP Demo Hub](https://demos.gsap.com/) + [gsap-skills](https://github.com/greensock/gsap-skills) | About 78 demos; 8 official agent skills | CodePen source per demo; skills | GSAP standard licence; skills MIT (16,034★). |
| [Made With GSAP](https://madewithgsap.com/) | 120 effects, 2 of them free | A tutorial, code ZIP and AI prompt per effect | Paid. The licence forbids putting the code in public repos. |
| [Motion examples](https://motion.dev/examples) | 462 | A preview MP4 for each; free source for 152, the other 310 need Motion+ | UI micro-interactions. The library is MIT. |
| [Codrops Creative Hub](https://tympanus.net/codrops/hub/) | 1,000+ demos; 347 GitHub repos | A live demo plus an MIT GitHub repo | robots.txt opts out of AI training and disallows AI crawlers; use the [GitHub repos](https://github.com/codrops). |
| [React Bits](https://reactbits.dev/) | 200+ free components (+230 Pro) | Full source per component as shadcn registry JSON | MIT + Commons Clause. |

### 4d. Other motion tools and template libraries

| Project | Items | What ships | Licence / notes |
|---|---|---|---|
| [Open Design](https://open-design.ai/plugins/templates/hyperframes/) ([video](https://open-design.ai/plugins/templates/video/)) | 25 HyperFrames templates; 49 video entries | `preview.mp4`, full source and `SKILL.md` in [nexu-io/open-design](https://github.com/nexu-io/open-design) | Apache-2.0. About 40 of the video entries are Seedance prompts. |
| [motion-anything](https://github.com/nexu-io/motion-anything) | 77 effects with live previews (218 `preview.html` files); 58 HyperFrames templates | `SKILL.md` plus runnable source | Apache-2.0; runs as a local app. Last push 2026-07-07. |
| [HyperFrames Motion Library](https://nutllwhy.github.io/hyperframes-motion-library/) | 23 templates × 3 presets | Composition source, parameter schema and a sample render | MIT. Data and explainer overlays. |
| [saas-motion-kit](https://tugrawork-creator.github.io/saas-motion-kit/) | 101 theme sheets, 24 transitions, 6 films | Storyboard sheets, seek-safe GSAP recipes, HyperFrames projects and a skill | MIT. |
| [Rive Marketplace](https://rive.app/marketplace) | Tens of thousands of community posts | A `.riv` file plus an MP4 | CC BY 4.0 per Rive's docs; check each file's label. |
| [Jitter templates](https://jitter.video/templates) | 407 | Editable only inside Jitter; no prompts or code | Has a "Jitter AI" category made with Opus 5.5. |
| [AutoAE](https://autoae.online/hooks) | 1,052 templates, 78 of them SaaS or launch | Preview MP4; customising is paid; no prompts or source | The terms forbid automated access. |

### 4e. Web and UI component libraries with prompts

Motion is a subset of each library. The output is web pages and components, not rendered films.

| Library | Items | What ships | Licence / notes |
|---|---|---|---|
| [21st.dev](https://21st.dev/) ([hero animations](https://21st.dev/community/components/explore/hero-animation)) | 12,000+ components; 60 hero animations | An agent prompt plus source per component | Each author's licence applies. robots.txt opts out of AI training. |
| [Aura](https://www.aura.build/) ([animation](https://aura.build/browse/components/animation)) | 2,831 components; 192 skills, about 27 of them motion | Copy-prompt button, HTML code and skills | Some templates are PRO. |
| [Superdesign](https://superdesign.dev/library) | 1,229 prompts, 114 tagged animation | A structured prompt plus a live preview | Community-contributed. |
| [Shaders](https://shaders.com/sections/particle-swarm-hero) | 60 sections; 190+ components | Install prompts (Pro); an MIT shader engine | The licence forbids redistributing sections or presets. |
| [Webthemez](https://www.webthemez.com/) | 158 | A website recreation prompt and a source ZIP (free items) | Newest item 2026-07-03. |
| [MotionSites](https://motionsites.ai/) | Not disclosed | Animated website prompts (paid) | The terms forbid scraping and redistribution. |
| [FreeFrontend](https://freefrontend.com/) | 1,284 pages | Inline HTML/CSS/JS, mostly credited CodePen pens | Check each pen's licence. |

### 4f. Benchmarks that publish prompts

| Benchmark | Items | What ships | Notes |
|---|---|---|---|
| [HeyGen Code2Video Bench](https://www.heygen.com/research/introducing-code2video-benchmark) | 168 briefs; a public Kaggle subset of at least 32 tasks | Each brief comes with a human-made reference video; the page plays model outputs side by side | The Kaggle dataset `heygen/code2video-public` is CC BY 4.0. |
| [XSCT Bench](https://xsct.ai/gallery) | 1,517 cases, about 47 of them motion | System and user prompts, a rubric, and each model's HTML output | Chinese. The site temporarily blocks clients that fetch too fast. |

---

## 5. Skills and skill directories

### 5a. Directories

| Directory | Items | What it records | Notes |
|---|---|---|---|
| [skills.sh](https://skills.sh/heygen-com/hyperframes/motion-graphics) | 20,000 skills; about 865 are motion or video by URL keyword | Install command, full `SKILL.md`, installs and audits | HyperFrames `motion-graphics` showed 382.4K installs. |
| [awesome-claude-video-skills](https://github.com/zhuyansen/awesome-claude-video-skills) ([AgentSkillsHub](https://agentskillshub.top/best/claude-video-skills/)) | 259 repos | Stars, kind, security grade and licence | CC0. Refreshed every 8 hours. |
| [awesome-opus-video-skills](https://github.com/ismoshushi/awesome-opus-video-skills) | 110 skills, 63 of them code-render | Render stack, install command, licence and an Opus 5.5 flag | MIT. |
| [Skillry skills](https://skillry.dev/skills) | 387 skills: 144 video, 42 free | Preview MP4s and installable packages | About 19 are HyperFrames launch-film skills. Installing needs a login. |
| [iart-ai/motion-skills](https://github.com/iart-ai/motion-skills) | 54 skills in 17 packs | `SKILL.md` files with a render → screenshot → verify loop | Mostly MIT; 745★. |
| [Claude Video skills](https://claudevideo.org/) | 247 | Open-source video skills | Built from the awesome-claude-video-skills list. |

The HyperFrames community skills and GSAP's official skills are listed in §4.

### 5b. Skill packs that ship example films

| Skill | Example films / items | Licence | Notes |
|---|---|---|---|
| [video-shotcraft](https://vincentwei1021.github.io/video-shotcraft/) | 157 shot recipes, 214 preview MP4s, 9 community films | Apache-2.0 | Builds Remotion product promos; 10,866★. |
| [video-talkcraft](https://vincentwei1021.github.io/video-talkcraft/) | 108 recipe cards, each with TSX and a live demo | PolyForm Noncommercial | For voiceover and talking-head explainers. |
| [Lemo-Opuscar](https://lemomo-ai.github.io/lemo-opuscar/) | 43 styles and 44 films, all with full source | MIT | Each style has a `STYLE.md` prompt. One studio made everything. Ships as a Claude Code plugin; 1,410★. |
| [hyperframes-student-kit](https://github.com/nateherkai/hyperframes-student-kit) | 15 skills, 406 motion cards, 12+ projects | MIT | Previews have to be rendered locally; 1,221★. |
| [motion-graphics-skills](https://github.com/charlie947/motion-graphics-skills) (charlie947) | 13 skills, 16 effect prompts | MIT | A companion Substack post shows each tile; 2 are public. |
| [Claude Video Skills](https://neelshah1810.github.io/Claude-Video-Skills/) | 11 skills, 11 films with HTML source | MIT | All brands are fictional. |
| [motion-launch-videos](https://github.com/Kimeur/motion-launch-videos) | 11 skills, 12 films with BRIEF.md and DESIGN.md | MIT | v2.1.0. The repo is more current than its [landing page](https://gazouzi.com/en/motion-launch-videos). |
| [product-launch-motion-skill](https://github.com/ouerf-man/product-launch-motion-skill) | 12 launch-film types, each with a GIF and HyperFrames source | MIT | From T01 Teaser to T11 Kinetic Shape Film. |
| [30X Web-to-Video](https://norahe0304-art.github.io/30x-video/) | 12 films; Remotion source for 4 (plus 2 retired) | MIT | Installed with `npx 30x-web-to-video`. |
| [motion-designer](https://designer.ostinos.com/) (kaventro) | 7 films, 4 with full source | MIT | Includes beat-map and music tools. |
| [cinetic](https://github.com/Leonxlnx/cinetic) + [claude-launchvideo](https://github.com/Leonxlnx/claude-launchvideo) | 4 films with their briefs; a 273-technique library; full source for one launch film | MIT | Remotion by default; HyperFrames optional. |
| [onetake](https://github.com/feitangyuan/onetake) ([site](https://onetakemotion.com)) | 10 case films with beat sheets | Free edition PolyForm Noncommercial; paid Pro adds a commercial licence and source | 1,951★. |
| [brag](https://latent-spaces.github.io/brag/) | 8 MP4s | MIT | Each demo project is rendered in a slim mode and a HyperFrames mode; 14,274★. |
| [Adu motion video](https://adunext.github.io/adu-motion-video/examples/gallery/) | 11 styles | MIT | Chinese. Several styles expect your own voiceover footage. |
| [claude-motion-design](https://github.com/howseen-ai/claude-motion-design) | 1 skill and one full example film | MIT | Has a remake mode that renders the original and the copy split-screen. |
| [opus-video-skills](https://github.com/tuzhechen2005/opus-video-skills) | 2 skills, 3 worked examples | MIT | Kinetic reel and painted animation. |
| [motion-design](https://github.com/cth9191/motion-design) (cth9191) | 10 styles, each with its original prompt | None | The films were made with a generative-video model (Higgsfield), not code. |
| [CutDirector](https://github.com/Fangx-AI/cut-director) | 15 prompts with demos | AGPL-3.0 for code; CC BY-SA 4.0 for prompts | Talking-head overlays. Also mirrors ChatCut's 123 references. |
| [AI Motion Director](https://immamdouhaboammar.github.io/motion-graphics-skills/) | 53 skills; about 9 HyperFrames projects | Proprietary | The licence permits viewing in a browser only. |

---

## 6. Web-motion inspiration galleries (no prompts)

These are useful for reference footage. None of them carries prompts or AI-made source.

| Gallery | Items | Notes |
|---|---|---|
| [What Ships](https://whatships.com) | 2,447 launch videos from X | Launch films made by studios and teams. Metadata is available as JSON, an OpenAPI spec and `llms-full.txt`; the site source is MIT. |
| [landing.love](https://www.landing.love/) | 2,163 website recordings | A video sitemap lists every recording. |
| [Recent](https://recent.design/) (formerly Godly) | About 1,117 items | MP4 previews and a Motion category. |
| [60fps.design](https://60fps.design/motion) | 83 brand reels, 67 storyboards | The terms forbid bulk copying. |
| [Awwwards Elements](https://www.awwwards.com/elements/) | Hundreds of short clips | robots.txt disallows `/elements/*`. |

---

## 7. Using these collections responsibly

**General rules**

- **The prompts and videos belong to their creators.** Nearly every collection says so, and none of the repository licences in §3 covers them. Credit the creator and link the original post.
- **A repo without a licence file is all rights reserved by default.** That applies to JasonZhu.AI's source, xianyu110, opusvideo, joeseesun, LeaddeOpenLab, Markjinli, remocn-collections, cth9191, Frontier Games and jinhanbuilds. Read these collections for reference; do not republish them.
- **Use the route the site offers.** Use an MCP server, an API, `llms.txt` or the GitHub data where one exists, and do not crawl pages the site's robots.txt disallows.
- **Hotlinked X media expires.** Many lists point at `video.twimg.com` URLs, which can stop working.
- **prompt-motion.com** sets `Content-Signal: search=yes, ai-train=no, use=reference` and blocks AI training crawlers. That is why this repo publishes only analysis and links.

**Site terms we recorded**

| Site | What its terms or robots.txt say | Offered route |
|---|---|---|
| Oneshotted | Terms §6 forbid copying the library or its prompts in bulk, scraping, getting around rate limits and redistributing prompts | MCP server (free key, 20 calls/min, 200/day) or the agent skill |
| 24fps | Training crawlers are disallowed. 4,212 clips are "© creator, link only"; the 395 open-licensed clips are free with attribution | MCP server, JSON API, `llms-full.txt` |
| Skillry | Terms §8 forbid scraping or bulk-copying paid catalog content without written permission | The MIT data on GitHub |
| Claude Video | AI crawlers are explicitly welcome; videos and prompts belong to the creators, and takedowns are honoured | `llms.txt`, sitemap |
| YouMind, TopView | `/api/` is disallowed; YouMind honours takedown requests | Sitemaps and detail pages |
| Swishy | The terms forbid scraping or bots without written permission, and using the templates to build a competing product | Browse by hand |
| Pexo | The terms forbid automated access that is not expressly authorised | Browse by hand |
| iArt.ai | The app's robots.txt disallows everything; the terms forbid scraping | Open share links one by one |
| AutoAE | The terms forbid automated access; the licence forbids scraping or replicating the library | Browse by hand |
| 60fps.design | The terms forbid bulk download, building a reference library from it and ML use | Paid MCP |
| MotionSites | The terms forbid scraping, bypassing the paywall and redistributing prompts | Paid plans and MCP |
| Made With GSAP | The licence forbids redistributing the code or putting it in public repos | Membership |
| Codrops | robots.txt opts out of AI training and disallows AI crawlers | The MIT GitHub repos |
| HyperFrames Studio | robots.txt disallows `/api/` | Browse the community page |
| Awwwards | robots.txt disallows `/elements/*` | Browse by hand |
| XSCT Bench | The site temporarily blocks clients that fetch too fast | Read slowly, by hand |
| React Bits | MIT + Commons Clause: you may use the components, but not sell or redistribute them | shadcn registry |
| video-talkcraft, onetake (free) | PolyForm Noncommercial | Ask the author for commercial use; onetake sells a commercial licence |
| Motion Prompt Bank | CC BY-NC-SA 4.0 | Attribute; no commercial republishing |
| maning636/motion-prompts | A custom licence forbids repackaging or re-uploading the prompts | Use the outputs, not the prompt text |
| AI Motion Director | Proprietary: viewing in a browser only | — |

---

## 8. Method

**How candidates were found.** We ran AI-assisted web searches from several angles: English, Chinese and Japanese queries; names of models, frameworks and genres; and GitHub repository search for "awesome" lists and skill repos. We then followed citations inside the collections we found: "related lists" sections, `THIRD_PARTY.md` files, the Remotion resources index, `llms.txt` files and sponsor links. 183 candidates were collected. Checking them turned up a few extra leads, which were checked the same way.

**How they were verified.** Each candidate was opened and checked on 2026-10-08/09 by a reviewer whose brief was to disprove the claim made for it:

- Is it live?
- Do the item counts match?
- Does each item really ship a prompt, source or skill?
- What do the licence, robots.txt and terms say?

Where the counts or claims were wrong, the reviewer recorded the observed values. 132 rows were kept and 55 dropped. Dropped rows included single skills with one demo, how-to articles, pages behind a paywall, generic web-design galleries and copies of other collections. No Japanese-language collection made the final list; YouMind offers a ja-JP locale.

**What "similarity" meant (1–5).**

- **5:** the same concept as prompt-motion.com. AI-made motion pieces from many creators, each with a prompt.
- **4:** a curated motion collection with a prompt or source per item, but missing one part (one creator, source instead of prompts, or a vendor's own output).
- **3:** a strong motion collection without prompts or source; a prompt library for web/UI motion; or a skill directory.
- **2:** a single skill, tool or article.
- **1:** unrelated.

Rows were kept if live and scored 3 or higher. A few 3s were dropped because their per-item "prompts" turned out to be generic templates.

**How rows were merged.** These were folded into one project: language versions of the same site, a site and its GitHub source repo, several pages of one site (e.g. Opus 5.5 and Fable 5.5 galleries, or a gallery and its skills store), and the official surfaces of one framework. Products from the same owner that serve different purposes were kept separate. The copies of prompt-motion.com were not counted. That gives 100 distinct projects.

**Our re-check on 2026-10-09.** We re-fetched the headline pages and data files of the largest collections:

| Site | Recorded on 10-08/09 | Our check, 10-09 | Change |
|---|---|---|---|
| Oneshotted | 6,144 recipes / 3,837 prompts / 3,710 creators | 6,164 / 3,838 / 3,716 | +20 recipes in about a day |
| 24fps | 4,607 clips / 1,073 with prompt / 2,540 creators | Same | Counts still dated 2026-10-03 |
| JasonZhu.AI | 1,402 works / 361 with prompt / 148 full | Same | — |
| Claude Video | 1,276 videos / 457 with prompt / 1,007 creators | Same | — |
| Skillry | 513 videos; repo 3,084–3,087★ | 513; repo 3,101★ | Stars only |
| WorkSkill | 478 cases | Same | — |
| Tellcut | 470 / 276 full (`examples.json`) | Same | — |
| Awesome AI Motion | 581 cases / 83 original (`cases.json`) | Same | — |
| Li-Evan | 334 entries, updated 2026-09-27 (`data.json`) | Same | — |
| YouMind | 340 items | Same | — |
| HyperFrames catalog | 400 items (170 / 222 / 8) | Same | — |
| What Ships | 2,552 rows in `search-index.json` (2,447 videos, 94 tools, 11 studios) | Same | — |

**Caveats.**

- Every count is what the site said on the check date. The active collections grow daily, and some had already stopped updating, as their "last updated" dates show.
- A "prompt" means very different things across sites: a verbatim creator prompt, an excerpt, a curator's reconstruction, or a one-line description. Read each site's labels.
- Model attributions are the creators' own claims, and no collection re-ran the prompts to check them, apart from the remake features noted above.
- If we missed a collection, or a count is wrong, please open an issue with a link.
