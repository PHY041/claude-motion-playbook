# Claude Motion Playbook

**What 233 motion videos made by Claude Opus 5.5 teach about prompting motion design.**

[prompt-motion.com](https://www.prompt-motion.com/), curated by [@p4nthera_](https://x.com/p4nthera_), collects motion videos that Claude Opus 5.5 built in code (HTML + GSAP, Remotion, HyperFrames, Three.js, Canvas…), each one with the prompt or skill behind it.
We studied all 233 entries in the 2026-10-09 snapshot. We read every prompt, sampled every video (a 6-frame contact sheet plus `ffprobe`), classified each entry, and ran the statistics. Each doc was fact-checked by a separate reviewer before publishing.

This repo is our notes. **It stores no videos, no frames and no full prompts.** Every entry links back to its creator.

[简体中文](README.zh-CN.md)

## What we found

- **One prompt runs the gallery.** The "make a dynamic 15-second motion graphics video … like it's your showreel … go all out" one-liner appears **33 times word for word, from 33 accounts**. With its rewrites and brand-slot versions, that family covers **102 of 230 prompts (44%)**. → [prompt patterns](docs/prompt-patterns.md)
- **Longer prompts don't look better.** Structured specs average 3.94 on visual impact and one-liners 3.88 (n = 17 vs 154, p ≈ 0.87); graded blind from frames only, it's 3.35 vs 3.55 (p ≈ 0.38). What long specs buy is **control**: 76% of spec-driven videos are product or brand films, against 38% for one-liners.
- **"Go all out" sways the grader, not the film.** With the prompt in view, AI graders scored prompts containing pressure phrases 0.33 higher (n = 95 vs 135, p ≈ 0.001). We then re-graded all 233 videos **blind**, from frames only: the gap fell to +0.08 (95% CI −0.11 to +0.27, p ≈ 0.47), and none of the 15 prompt features stayed significant. The phrase seems to move the judge who reads it, not the video. → [blind re-grade](docs/prompt-patterns.md#27-blind-re-grade-what-survives)
- **The same prompt gives different films.** The 31 distinct videos made from the verbatim one-liner land in 4 categories and span 2 to 5 on the blind grade (SD 0.68, close to the 0.73 of the whole corpus). With no wording feature surviving blind grading, generating a few takes and keeping the best is the lever you actually control.
- **The best specs share one anatomy.** `<inputs>` `<direction>` `<structure>` `<build>` `<gotchas>` `<start>`: 10 entries from 6 accounts use it. Most of the value sits in the gotchas, deterministic rendering and QA gates. → [template](templates/saas-launch-film.hyperframes.md)
- **137 reusable techniques** across camera, cuts, type, UI demos, 3D, data viz, particles, music sync and render QA, each with linked examples. → [techniques](docs/techniques.md)
- **This is a wave, not one site.** We mapped **100 related projects**: galleries, lists, framework showcases and skill directories. The largest, [Oneshotted](https://oneshotted.io/), lists 6,164 recipes. → [ecosystem](docs/ecosystem.md)

## What's inside

| | English | 中文 | What it is |
|---|---|---|---|
| Top picks | [top-picks.md](docs/top-picks.md) | [zh](docs/zh/top-picks.md) | 6 videos to start with, a Top 20, the best by use case and by category, and the dataset at a glance |
| Prompt patterns | [prompt-patterns.md](docs/prompt-patterns.md) | [zh](docs/zh/prompt-patterns.md) | How the prompts are written and what correlates with quality, with stats |
| Techniques | [techniques.md](docs/techniques.md) | [zh](docs/zh/techniques.md) | 137 moves in 9 groups, each with an HTML + GSAP / HyperFrames hint and examples |
| Skills | [skills.md](docs/skills.md) | [zh](docs/zh/skills.md) | Review of the 13 open-source motion skills featured in the gallery |
| Ecosystem | [ecosystem.md](docs/ecosystem.md) | [zh](docs/zh/ecosystem.md) | 100 collections, lists, showcases and skill directories like this one |
| Template | [saas-launch-film.hyperframes.md](templates/saas-launch-film.hyperframes.md) | (bilingual) | Our own 45–60 s SaaS launch-film prompt for HyperFrames, plus 3 one-liners |
| Catalog | [catalog.csv](catalog/catalog.csv) · [catalog.json](catalog/catalog.json) | | All 233 entries: creator, date, stack, length, aspect ratio, category, techniques, links |
| Dataset | [🤗 PHY041/claude-motion-playbook](https://huggingface.co/datasets/PHY041/claude-motion-playbook) | | The same catalog on Hugging Face: `load_dataset("PHY041/claude-motion-playbook")` |

**No time?** Watch these six first (5 min 44 s in total): [#5](https://www.prompt-motion.com/twoclipping-221cab) · [#8](https://www.prompt-motion.com/lexnlin-038035) · [#126](https://www.prompt-motion.com/ik-builds-b8bdcf) · [#36](https://www.prompt-motion.com/ismailfahmi-557268) · [#64](https://www.prompt-motion.com/sayan-shanky-f850d8) · [#29](https://www.prompt-motion.com/kloss-xyz-fe0c31). [Why these →](docs/top-picks.md#1-start-here-6-videos-in-10-minutes)

## Method, briefly

- **Source.** All 233 public entries on prompt-motion.com as of 2026-10-09 (posted 2026-09-23 → 2026-10-08, 216 accounts). `#N` everywhere is the `id` in the catalog.
- **Looking.** For each video: a 6-frame contact sheet, plus duration, frame rate and audio from `ffprobe`. These are samples, not full viewings. Moves that fall between sampled frames were spot-checked against the video.
- **Scoring.** AI graders rated visual impact and prompt quality on a 1–5 scale. A fresh grader repeating the original instructions on 50 entries agreed at weighted κ 0.74. A blind re-grade of all 233 (frames only, no prompt, title or creator) agreed with the original at only κ 0.51 and came out 0.33 lower, so seeing the prompt inflates scores. We publish aggregates only, never per-entry scores, and treat gaps under ~0.3 as noise.
- **Stats.** Permutation tests (20,000 shuffles) with a Bonferroni correction across 15 prompt features. Each number in the docs comes with its n.
- **Checking.** A separate reviewer re-opened the cited files to check every doc's numbers, quotes and links against the source files, and fixed what was wrong.
- **Limits.** The gallery is curated (survivorship bias). Most prompts are short. Stated stacks exist for only 56 entries.

## Credits & content policy

- Every video and prompt belongs to its creator. Each catalog row links to the creator's post and to the prompt-motion.com entry page. Watch the videos and read the full prompts there.
- Curation credit goes to [@p4nthera_](https://x.com/p4nthera_) and [prompt-motion.com](https://www.prompt-motion.com/). This project is independent and not affiliated with prompt-motion.com, the creators, Anthropic or HeyGen.
- Prompt quotes here are short (≤ 25 words), attributed and linked.
- If you are a creator and want your entry described differently or removed, [open an issue](https://github.com/PHY041/claude-motion-playbook/issues) and we'll take care of it.

## License

- Our writing (`docs/`, this README) and our classification fields in `catalog/`: [CC BY 4.0](LICENSE).
- `templates/`: [CC0 1.0](templates/LICENSE). Copy it, change it, no attribution needed.
- Videos, prompts and other third-party material are **not** covered. They stay with their owners.

---

Made by [Haoyang Pang](https://github.com/PHY041) ([Canlah AI](https://canlah.ai)). If this saved you an afternoon, a ⭐ helps others find it.
