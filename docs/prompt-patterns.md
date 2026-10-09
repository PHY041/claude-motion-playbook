# Prompt patterns: how the 233 prompts are written, and what actually tracks quality

This is a snapshot of [prompt-motion.com](https://www.prompt-motion.com/) (curated by [@p4nthera_](https://x.com/p4nthera_)) taken on 2026-10-09. It covers 233 entries. 230 of them have a prompt; the other 3 are skills that come with only an install command. `#N` is the `id` in [`catalog/catalog.json`](../catalog/catalog.json). Every number below was recomputed from the prompt texts, the catalog and the grader records. Method and caveats are in [section 2.1](#21-method-read-this-before-the-numbers); the blind re-grade that corrects our earlier pressure-phrase finding is in [section 2.7](#27-blind-re-grade-what-survives).

[简体中文版](zh/prompt-patterns.md)

## TL;DR

- **One prompt dominates.** The "showreel" one-liner appears **33 times verbatim, from 33 different accounts** (22 of those copies are byte-identical). Rewrites, translations and brand-slot versions bring the family to **102 prompts, 44% of the 230**. Another 12 keep only its skeleton, for 114 in all (50%). The median prompt in the gallery is 151 characters long, which is exactly the length of that one-liner.
- **Writing more doesn't buy more wow.** On the graders' 1–5 visual-wow scale, structured specs average 3.94 and one-liners 3.88 (n = 17 vs 154, permutation p ≈ 0.87). Graded blind from frames only, it's 3.35 vs 3.55 (p ≈ 0.38): still no real difference. The graders also scored prompt quality, and that score barely tracks visual wow (Spearman ρ = 0.06, p ≈ 0.40).
- **What long specs buy is control.** 76% of the videos made from structured specs are product or brand films. For one-liners it's 38%. And 131 of the 136 prompts that state a single duration got a video within 0.8–1.25× of it.
- **"Go all out" moves the grader, not the film.** Graders who could read the prompt scored prompts with a pressure phrase 0.33 higher (4.05 vs 3.73, n = 95 vs 135, p ≈ 0.001; "go all out" itself appears in 87). Re-graded blind, from frames only, the gap is +0.08 (95% CI −0.11 to +0.27, p ≈ 0.47), and none of the 15 prompt features we tested predicts the blind score. Details in [section 2.7](#27-blind-re-grade-what-survives).
- **Adding a brand slot costs nothing measurable.** Inside the family, prompts that name a product or person score 3.98 and pure self-showreels 4.02 (n = 44 vs 58, p ≈ 0.89); blind, 3.55 vs 3.62 (p ≈ 0.68). Meanwhile the share of product or brand films rises from 16% to 70%.
- **The same prompt gives different films.** The 31 distinct videos made from the verbatim one-liner span 2 to 5 on the blind grade (SD 0.68, close to the 0.73 of the whole gallery). They fall into 4 categories and run from 14.9 s to 45.1 s. Generating a few takes and keeping the best is the lever you actually control.
- **Long specs share one anatomy.** A six-tag XML layout (`<inputs>` `<direction>` `<structure>` `<build>` `<gotchas>` `<start>`) appears in 10 entries from 6 accounts, posted between 09-23 and 10-08. Most of its value is in the gotchas, the deterministic rendering rules and the approval and QA gates.
- **Grader noise is about ±1 point.** A fresh grader with the original instructions agreed at weighted κ 0.74; a blind grader agreed at κ 0.51 and scored 0.33 lower. Any gap below roughly 0.3 is noise-level, so we publish aggregates only, never per-entry scores.

---

## 1. The viral one-liner family

### 1.1 The text

The earliest copy in the gallery is [#3 Bold kinetic type showreel — @shneural](https://www.prompt-motion.com/shneural-2abdfa), posted 2026-09-24. The gallery doesn't say who wrote the line first.

It opens "make a dynamic 15-second motion graphics video that shows what an incredible motion designer you are …" and ends "go all out." The whole prompt is two sentences and 151 characters; read it in full on the [entry page](https://www.prompt-motion.com/shneural-2abdfa).

| Clause | What it does |
|---|---|
| Format and length (a 15-second motion graphics video) | Sets the format and the length. The length is mostly respected: 96 of the 100 one-liners that state one duration landed within 0.8–1.25× of it. |
| Self-proof (the model as an incredible motion designer) | Turns "make a video" into "prove yourself", so the model shows every technique it knows. |
| Genre (a showreel for a résumé) | Picks the genre: a technique montage with chapter numbers and a closing lockup. That's why these films look alike. |
| Pressure ("go all out") | Asks for maximum effort. Graders who could read the prompt scored such prompts higher, but graders who saw only the frames found no difference ([section 2.7](#27-blind-re-grade-what-survives)). It sways the reader, not the film. |

### 1.2 Variants

We read all 114 prompts and sorted them by hand. Every member is listed in [Appendix A](#appendix-a-family-membership). "Product/brand film" means the catalog `category` is `product-launch-film`, `saas-ui-walkthrough`, `social-ad-vertical` or `logo-brand-ident`.

| Variant | n | Example | Mean wow (sighted) | Product/brand film |
|---|---|---|---|---|
| A. Verbatim (ignoring case, accents, punctuation) | 33 | #3 above | 3.97 | 18% |
| B. Verbatim + one appended sentence | 8 | [#17 Dub promo video — @steventey](https://www.prompt-motion.com/steventey-0d20e4) adds a launch-video line pointing at the product URL | 4.38 | 62% |
| C. Only duration, aspect or theme changed | 14 | [#48 Jev engineering showreel — @polydao](https://www.prompt-motion.com/polydao-7a572b) turns it into a `[24]` / `[TOPIC]` / `[BRAND COLORS]` template | 3.93 | 36% |
| D. Brand slot ("for / on / about X") | 21 | [#12 Distilbook product video — @ajith_io](https://www.prompt-motion.com/ajith-io-c52e09) opens with a research step: "Research Distilbook." | 3.95 | 86% |
| E. Brand becomes the subject ("what an incredible X is") | 4 | [#36 Drone Emprit showreel — @ismailfahmi](https://www.prompt-motion.com/ismailfahmi-557268) | 4.00 | 50% |
| G. English rewrite | 16 | [#137 Reflex brand motion reel — @reflex_cloud](https://www.prompt-motion.com/reflex-cloud-72ffe5) | 4.06 | 12% |
| H. Translation (zh, ja, tr) | 6 | [#59 Lism CSS 1.0 release video — @ddryo_loos](https://www.prompt-motion.com/ddryo-loos-300829) | 3.83 | 33% |
| F. Skeleton only (no designer, no showreel) | 12 | [#31 SuperX feature release teaser — @robj3d3](https://www.prompt-motion.com/robj3d3-b18fad) | 3.75 | 83% |

- **The core family** (A–E, G, H) is 102 prompts from 98 accounts, using 69 distinct texts. Adding F gives 114 prompts, 110 accounts and 80 distinct texts.
- **The family scored higher only with the prompt in view.** On the sighted grade, the core family averages 4.00 against 3.75 for every other prompt (n = 102 vs 128, p ≈ 0.011; 4.02 vs 3.74 with reposts removed, p ≈ 0.003), and the whole gap sits on its pressure words: holding them constant, it falls to +0.02 (stratified permutation p ≈ 0.89). Graded blind, the family is +0.10 over the rest (p ≈ 0.37), which is noise-level. The pressure words themselves don't predict the blind score ([section 2.7](#27-blind-re-grade-what-survives)).
- **The verbatim copies on their own are not special:** 3.97 vs 3.84 for everything else on the sighted grade (p ≈ 0.37).
- **Timing.** The verbatim copies were posted on 09-24 (1), 09-25 (21), 09-26 (10) and 09-27 (1). 09-25 and 09-26 were also the gallery's busiest days, with 82 and 68 entries.
- **Reposts.** [#129 Claude motion designer showreel — @mrtanviir](https://www.prompt-motion.com/mrtanviir-132457) and [#227 Shape and dot motion showreel — @umangratani](https://www.prompt-motion.com/umangratani-57f86a) repost the same video (re-encoded at 720p) as [#4 Abstract motion design reel — @ajith_io](https://www.prompt-motion.com/ajith-io-b5626e), the earliest post of that video. So the 33 verbatim prompts produced 31 distinct videos.
- **Common small tweaks:**
  - a research step up front (#12);
  - telling the model to use the brand's own API for assets ([#102 fal motion design showreel — @influencer_seo](https://www.prompt-motion.com/influencer-seo-ce8c33));
  - a closing order such as "dont ask just make" ([#166 Swiss-style motion showreel — @levabashidze](https://www.prompt-motion.com/levabashidze-2d713a)).

### 1.3 What the template tends to produce

This part is descriptive. It comes from the catalog's tags and technique notes, not from scores.

- **HUD chrome** (timecodes, frame brackets, beat counters) is noted in **23 of the 31 distinct verbatim videos (74%)**. Elsewhere in the gallery it's 22%, and none of the 17 structured-spec videos has it.
- **Particles** show up in 17 of the 31 (55%), against 16% elsewhere and none of the structured-spec videos.
- **Some prompts now ban that look outright.** [#63 Claude self-intro motion graphic — @1littlecoder](https://www.prompt-motion.com/1littlecoder-9fef89) says: "Avoid the frames and texts on the corners which are typical ai made giveaways!" The same prompt was also posted by another account as [#215 Kinetic type self-portrait — @souravbhar871](https://www.prompt-motion.com/souravbhar871-61f424). Two of the long specs in section 3 also rule out timeline chrome.

### 1.4 The visible prompt is not the whole input

Six of the 31 verbatim videos are product films, even though the prompt names no product:

- [#7 Enxovaly baby app promo — @gabrielbuzziv](https://www.prompt-motion.com/gabrielbuzziv-4ff0c6)
- [#11 Travel visa service promo — @thismacapital](https://www.prompt-motion.com/thismacapital-dfba20)
- [#21 AjustaCV Pro pricing promo — @thayto_dev](https://www.prompt-motion.com/thayto-dev-44b911)
- [#115 LiteLLM promo reel — @MisbahSy](https://www.prompt-motion.com/misbahsy-80eaec)
- [#193 Crux motion design showreel — @marouanegazouzi](https://www.prompt-motion.com/marouanegazouzi-6071d5)
- [#222 Lead Notifi product ad — @leadnotifi](https://www.prompt-motion.com/leadnotifi-e83f94)

The model clearly had context the gallery doesn't show, such as a repo, project files or earlier turns. The same probably happens elsewhere in the gallery, so read every prompt-vs-quality number below with that in mind.

---

## 2. What correlates with visual quality, and what doesn't

### 2.1 Method (read this before the numbers)

- **Score.** "Visual wow" is a 1–5 score from AI graders. Each grader saw a 6-frame contact sheet of the video plus its prompt. Two graders typically differ by about ±1 point.
  - Sanity check: 5 entries are reposts of a video that's already in the gallery. In 4 of those 5 cases the repost got the same score as the original, and in 1 it was a point off.
  - Because of this noise, **per-entry scores are not published.**
- **Sighted vs blind.** Sections 2.2–2.6 report these original grades, which we call *sighted* because the grader could read the prompt. [Section 2.7](#27-blind-re-grade-what-survives) re-grades all 233 videos *blind*, from frames only, and re-tests the main findings. Where the two disagree, go with the blind result. The pressure-phrase finding is the one that didn't survive.
- **Distribution.** Across the 230 prompts, 5 videos scored 2, 65 scored 3, 117 scored 4 and 43 scored 5. Nothing scored 1. The mean is 3.86 (SD 0.73). With almost everything sitting at 3 or 4, a 0.3-point gap is already large.
- **Prompt features** were detected with regular expressions on the prompt text. The variant families in section 1 were sorted by hand.
- **Tests.** p-values come from two-sided permutation tests on the difference of means (20,000 seeded label shuffles). Spearman p-values are permutation tests too. With 15 features tested, the Bonferroni threshold is 0.05 / 15 ≈ 0.0033.
- **"Product/brand film"** uses the catalog `category`, which the same graders assigned. It's a label, not a score.

### 2.2 Single features vs visual wow (230 prompts, sighted grader)

> **Superseded by the blind re-grade.** This table uses the original sighted grades. Graded blind, the top two rows shrink to +0.08 (p ≈ 0.47) and +0.11 (p ≈ 0.31), and no row is significant. The side-by-side table is in [section 2.7](#27-blind-re-grade-what-survives).

| Feature in the prompt | n with | Mean wow with / without | Diff | p |
|---|---|---|---|---|
| Pressure words ("go all out" in 87 prompts, plus "go crazy", 全力, …) | 95 | 4.05 / 3.73 | +0.33 | 0.001 |
| Showreel / résumé / portfolio framing | 92 | 4.02 / 3.75 | +0.27 | 0.007 |
| Names a URL, @handle or placeholder | 33 | 4.03 / 3.83 | +0.20 | 0.15 |
| States a duration | 148 | 3.93 / 3.74 | +0.18 | 0.07 |
| Banned / avoid list | 17 | 4.00 / 3.85 | +0.15 | 0.50 |
| Approval gate before the full build | 10 | 4.00 / 3.85 | +0.15 | 0.66 |
| BPM / beat grid | 18 | 3.89 / 3.86 | +0.03 | 0.87 |
| Asks for music, sound or voice | 44 | 3.89 / 3.85 | +0.03 | 0.82 |
| Self-QA after render | 12 | 3.83 / 3.86 | −0.03 | 1.00 |
| Real assets (repo, site, screenshots) | 31 | 3.81 / 3.87 | −0.06 | 0.69 |
| Research / read sources first | 20 | 3.80 / 3.87 | −0.07 | 0.75 |
| Role line ("you are a … designer") | 9 | 3.78 / 3.86 | −0.09 | 0.82 |
| Deterministic render (seek(t), pure function of time) | 13 | 3.77 / 3.87 | −0.10 | 0.70 |
| Hex colour values | 8 | 3.75 / 3.86 | −0.11 | 0.81 |
| Names a tech stack | 37 | 3.70 / 3.89 | −0.19 | 0.18 |

On the sighted grade, only the first row cleared the corrected threshold; on the blind grade, none does. The negative rows here are all noise-level (p ≥ 0.18), so they don't show that hex colours or role lines hurt.

### 2.3 Pressure words, untangled

Pressure words and the showreel framing usually arrive together, so we split them. Each cell gives the sighted mean, then the blind mean from [section 2.7](#27-blind-re-grade-what-survives):

| Mean wow, sighted / blind | Showreel framing | No showreel framing |
|---|---|---|
| **Pressure words** | 4.06 / 3.64 (n = 81) | 4.00 / 3.21 (n = 14) |
| **No pressure words** | 3.73 / 3.27 (n = 11) | 3.73 / 3.52 (n = 124) |

- **On the sighted grade, pressure words kept their gap in both strata.** Holding family membership constant, the gap was +0.31 (p ≈ 0.04); holding showreel framing constant, +0.30 (p ≈ 0.06). The framing itself added +0.03 once pressure words were held constant (stratified permutation p ≈ 0.88).
- **On the blind grade, the gap is gone.** Holding family membership constant it's +0.01, and holding showreel framing constant −0.01 (both p ≈ 1.0). The framing adds +0.12 with pressure words held constant (p ≈ 0.46).
- **The gap came from the grader.** For pressure prompts the sighted grade sits 0.47 above the blind grade; for the rest, 0.22. That difference of +0.25 (95% CI 0.07 to 0.43, p ≈ 0.007) is the phrase priming the grader that reads it.
- **Fewer weak results? Only on the sighted grade:** 18% of pressure prompts scored 3 or below, against 39% of the rest. Blind, it's 46% vs 53%.
- **A looser definition doesn't rescue it.** Our own hand-picked list of intensity phrases (n = 118 vs 112) showed +0.42 on the sighted grade (p < 0.001) and +0.10 blind (p ≈ 0.32).

### 2.4 Long specs vs one-liners

| Prompt type (catalog) | n | Mean wow, sighted / blind | Scored 3 or below, sighted / blind | Product/brand film |
|---|---|---|---|---|
| One-liner | 154 | 3.88 / 3.55 | 31% / 48% | 38% |
| Short brief | 56 | 3.80 / 3.55 | 29% / 52% | 48% |
| Structured spec | 17 | 3.94 / 3.35 | 24% / 59% | 76% |
| Skill-driven | 6 | 3.83 / 3.50 | 33% / 67% | 33% |

- **Wow: no real difference.** Structured specs vs one-liners: +0.06 on the sighted grade (p ≈ 0.87) and −0.19 blind (p ≈ 0.38). Prompts over 500 characters vs the rest: +0.15 sighted (n = 23 vs 207, p ≈ 0.37) and −0.06 blind (p ≈ 0.77).
- **Length had a weak positive rank correlation with sighted wow** (ρ = 0.14, p ≈ 0.04), driven by the very shortest prompts:
  - 100 characters or less: mean 3.70, and 42% scored 3 or below;
  - 101–200 characters, where the one-liner family sits: mean 3.95, and 25% scored 3 or below.

  On the blind grade it disappears (ρ ≈ 0.00, p ≈ 0.97; 3.50 vs 3.57 for the two bands).
- **Prompt craft is not visual wow.** The graders' prompt-quality score correlates strongly with length (ρ = 0.68) but hardly at all with wow (ρ = 0.06 sighted, p ≈ 0.40; −0.07 blind, p ≈ 0.26). The 15 prompts rated 5 for craft average 4.00 sighted wow; the 47 rated 1 average 3.72.
- **What long specs change is what you get:**
  - a product film rather than a technique montage (76% vs 38%);
  - the requested format and copy.

  The sighted grades hinted at fewer misses for specs (24% vs 31% scored 3 or below). The blind grades don't support that (59% vs 48%, on only 17 specs), so we no longer make that claim. The product-film share is a category label, not a quality score, and it holds up ([section 2.7](#27-blind-re-grade-what-survives)).

### 2.5 Brand insertion

Inside the core family:

| | n | Mean wow, sighted / blind | Product/brand film |
|---|---|---|---|
| Names a product, brand, project or person | 44 | 3.98 / 3.55 | 70% |
| Pure self-showreel | 58 | 4.02 / 3.62 | 16% |

The wow difference is −0.04 on the sighted grade (p ≈ 0.89) and −0.08 blind (p ≈ 0.68), effectively zero both ways. **A brand slot turns most outputs into product films with no measurable loss of wow.** The pure group includes the 6 verbatim prompts that produced product films anyway (section 1.4).

### 2.6 Same prompt, different results

- **The verbatim one-liner.** On the sighted grade, its 31 distinct videos split 7 / 17 / 7 across scores 3 / 4 / 5. On the blind grade they split 1 / 14 / 14 / 2 across 2 / 3 / 4 / 5, with an SD of 0.68 against 0.73 for all 230 prompts: one fixed prompt spreads almost as widely as the whole gallery. They fall into 4 catalog categories and run from 14.9 s to 45.1 s.
- **Four other prompts were each posted twice with different videos:**
  - [#2 Shape morphing through UI states — @twoclipping](https://www.prompt-motion.com/twoclipping-5cba86) and [#97 Morphing UI states loop — @demonugc](https://www.prompt-motion.com/demonugc-4c5753), which use the same 2,711-character spec;
  - [#12 Distilbook product video — @ajith_io](https://www.prompt-motion.com/ajith-io-c52e09) and [#33 Distilbook motion showreel — @itisRazak](https://www.prompt-motion.com/itisrazak-3ad902);
  - [#63 Claude self-intro motion graphic — @1littlecoder](https://www.prompt-motion.com/1littlecoder-9fef89) and [#215 Kinetic type self-portrait — @souravbhar871](https://www.prompt-motion.com/souravbhar871-61f424);
  - [#160 DistilBook product explainer — @sudo_kiran](https://www.prompt-motion.com/sudo-kiran-4f8b59) and [#68 DistilBook motion explainer — @sudo_kiran](https://www.prompt-motion.com/sudo-kiran-b055de). This is the gallery's only case of one account re-running its own prompt.

  On the sighted grade, the two videos in each pair are one point apart. On the blind grade the gaps are 0, 1, 1 and 2 points.
- **Honest limit.** One point is also the size of the grader noise, so we can't separate run-to-run variation from grading noise.
- **The runs really do differ, though.** The evidence that doesn't rely on scores: the same prompt lands in different categories and lengths, and one of the #2/#97 pair was posted with a soundtrack and the other without.
- **Practical takeaway:** one or two videos can't tell you which way of prompting is better. A single prompt spans 2 to 5 on the blind grade, while no average gap between prompt features survives blind grading ([section 2.7](#27-blind-re-grade-what-survives)). Generating a few takes and keeping the best is the lever you actually control.

### 2.7 Blind re-grade: what survives

**Why we did it.** The original graders read each prompt next to its frames. A prompt that says "go all out" or "showreel" could tilt the grade before the grader looks at a single frame. Our first version listed this as an unchecked guess. Since pressure phrases were our headline finding, we checked it.

**Method.**

- **Blind re-grade.** Fresh Claude Opus 5.5 graders scored all 233 videos on the same 1–5 visual-wow scale. They saw only the 6-frame contact sheet, with the option to pull extra frames when a sheet was unclear (used for 6 entries). They got no prompt, title, creator, metadata or earlier score. The work ran in 4 interleaved batches, and the batches don't differ (permutation p ≈ 0.87).
- **Retest.** A separate fresh grader re-scored 50 entries with the original sighted instructions, to measure ordinary drift between graders.
- **Same tests.** The same 15 regex features, permutation tests (20,000 shuffles) and Bonferroni threshold (0.0033) as section 2.2.

**Reliability.**

| Comparison | n | Weighted κ (95% CI) | Exact / within 1 point | Mean shift |
|---|---|---|---|---|
| Fresh sighted grader vs original | 50 | 0.74 (0.60–0.84) | 58% / 100% | −0.26 |
| Blind grader vs original | 233 | 0.51 (0.42–0.59) | 52% / 97% | −0.33 |
| Blind grader vs fresh sighted grader | 50 | 0.82 (0.68–0.91) | 76% / 100% | −0.20 (p ≈ 0.007) |

- κ is quadratic-weighted. The new graders are stricter than the original ones, and hiding the prompt lowers scores by a further 0.20 on the same 50 entries.
- Repost check: only 1 of the 5 repost pairs got matching blind scores (3 pairs were a point apart, 1 was two apart). On the sighted grade it was 4 of 5. A single grade is noisy either way.

**Feature by feature, sighted vs blind (230 prompts).**

| Feature in the prompt | n with | Sighted diff (p) | Blind mean with / without | Blind diff (p) |
|---|---|---|---|---|
| Pressure words ("go all out", "go crazy", 全力, …) | 95 | +0.33 (0.001) | 3.58 / 3.50 | +0.08 (0.47) |
| Showreel / résumé / portfolio framing | 92 | +0.27 (0.007) | 3.60 / 3.49 | +0.11 (0.31) |
| Names a URL, @handle or placeholder | 33 | +0.20 (0.15) | 3.64 / 3.52 | +0.12 (0.44) |
| States a duration | 148 | +0.18 (0.07) | 3.51 / 3.59 | −0.08 (0.45) |
| Banned / avoid list | 17 | +0.15 (0.50) | 3.35 / 3.55 | −0.20 (0.31) |
| Approval gate before the full build | 10 | +0.15 (0.66) | 3.30 / 3.55 | −0.25 (0.38) |
| BPM / beat grid | 18 | +0.03 (0.87) | 3.28 / 3.56 | −0.28 (0.13) |
| Asks for music, sound or voice | 44 | +0.03 (0.82) | 3.50 / 3.54 | −0.04 (0.73) |
| Self-QA after render | 12 | −0.03 (1.00) | 3.25 / 3.55 | −0.30 (0.22) |
| Real assets (repo, site, screenshots) | 31 | −0.06 (0.69) | 3.32 / 3.57 | −0.25 (0.09) |
| Research / read sources first | 20 | −0.07 (0.75) | 3.25 / 3.56 | −0.31 (0.07) |
| Role line ("you are a … designer") | 9 | −0.09 (0.82) | 3.44 / 3.54 | −0.09 (0.81) |
| Deterministic render (seek(t), pure function of time) | 13 | −0.10 (0.70) | 3.15 / 3.56 | −0.40 (0.08) |
| Hex colour values | 8 | −0.11 (0.81) | 3.12 / 3.55 | −0.42 (0.14) |
| Names a tech stack | 37 | −0.19 (0.18) | 3.38 / 3.56 | −0.19 (0.18) |

- **No feature predicts the blind score.** The smallest uncorrected p is 0.07, far from the 0.0033 threshold, and after correction every feature sits at p = 1.0. All 15 together explain 6% of the variance in blind scores (adjusted R² ≈ 0).
- **The pressure-phrase gap was grader priming.** Blind, it's +0.08 (95% CI −0.11 to +0.27, p ≈ 0.47), and about zero once family or showreel framing is held constant (+0.01 and −0.01). The sighted grade sits 0.47 above the blind grade for pressure prompts and 0.22 above it for the rest. That extra +0.25 (95% CI 0.07 to 0.43, p ≈ 0.007) is the phrase lifting the score of the grader who reads it.
- **Spec-style features lean negative blind** (deterministic render, research first, real assets, self-QA, beat grid, hex colours: −0.25 to −0.42 on 8–31 prompts), but none is significant even before correction. One possible reading is that these specs ban the dense, flashy looks a frames-only judge rewards (section 3.2). We don't read it as harm.

**What survives and what doesn't.**

| Finding | Sighted grade | Blind grade | Verdict |
|---|---|---|---|
| Pressure words go with higher wow | +0.33 (p ≈ 0.001) | +0.08 (p ≈ 0.47) | Corrected: grader priming |
| The core family beats the rest | +0.25 (p ≈ 0.011) | +0.10 (p ≈ 0.37) | Doesn't survive |
| Longer prompts score slightly higher | ρ = 0.14 (p ≈ 0.04) | ρ ≈ 0.00 (p ≈ 0.97) | Doesn't survive |
| Specs miss less often (scored 3 or below) | 24% vs 31% | 59% vs 48% | Doesn't survive |
| Specs look no better than one-liners | 3.94 vs 3.88 (p ≈ 0.87) | 3.35 vs 3.55 (p ≈ 0.38) | Survives |
| A brand slot costs no wow | −0.04 (p ≈ 0.89) | −0.08 (p ≈ 0.68) | Survives |
| One prompt gives a wide spread | 3 to 5 | 2 to 5 (SD 0.68 vs 0.73 overall) | Survives |

**Control still stands.** "76% of spec-driven videos are product or brand films, against 38% of one-liners" rests on catalog category labels, not on quality scores. The labels hold up too: on the 50 retest entries, the fresh grader agreed on product/brand film or not for 47 (94%, κ 0.88) and on the exact category for 44 (88%).

### 2.8 What we can and can't say

- **Can say:**
  - Long specs and named brands go with on-brief product films.
  - How a prompt is written explains little of the variance in wow. On the blind grade, all 15 features together explain about none of it.
  - A grader who reads the prompt is swayed by it. Pressure phrases widen the sighted-minus-blind gap by 0.25 points (p ≈ 0.007).
- **Can't say:**
  - "Pressure words like 'go all out' make better videos." The blind re-grade finds no effect (+0.08, p ≈ 0.47).
  - "More detail makes it more impressive." Neither grade supports this.
  - "Hex colours, deterministic-render rules or research steps hurt." Their blind gaps lean negative, but none is significant (p ≥ 0.07, n = 8–31).
  - Anything from the `effort` metadata. Only 36 prompts carry it (sighted grade: Max 22 prompts, 4.09; High 7, 4.29; Medium 7, 3.57).
- **Survivorship.** The gallery only holds videos people chose to post. Part of what any group scores may come from "ran it several times, posted the best one", and the discarded runs are invisible.
- **Grader bias, now checked.** The original graders saw the prompt as well as the frames, and section 2.7 shows that this lifts scores, more so for pressure prompts. Blind "wow" may still reward technique density (3D, particles, style jumps), which many long specs ban on purpose. That part we haven't tested.
- **Not independent.** Templates get copied: one long spec was reused word for word and another at 99.5% (section 3.1). And 5 videos were reposted under other accounts.

---

## 3. Anatomy of the long structured specs

### 3.1 Formats

**Six-tag XML** (`<inputs>` `<direction>` `<structure>` `<build>` `<gotchas>` `<start>`): 10 entries from 6 accounts.

- **Who used it.** In posting order:
  - [#13 UGC ad generator promo — @twoclipping](https://www.prompt-motion.com/twoclipping-6dd14e), the first, on 09-23;
  - [#2 Shape morphing through UI states — @twoclipping](https://www.prompt-motion.com/twoclipping-5cba86) (same account);
  - [#97 Morphing UI states loop — @demonugc](https://www.prompt-motion.com/demonugc-4c5753), which reuses #2's text word for word;
  - [#5 Photo print app launch film — @twoclipping](https://www.prompt-motion.com/twoclipping-221cab);
  - [#34 Frame by Frame launch video — @notdwd](https://www.prompt-motion.com/notdwd-7de38a);
  - [#10 Launch video remake comparison — @notdwd](https://www.prompt-motion.com/notdwd-c2037d), 99.5% identical to #34 apart from added brand-colour handling;
  - [#25 Orange dot motion system — @ultimaxbt](https://www.prompt-motion.com/ultimaxbt-bbebf5);
  - [#178 Prompt Motion site promo — @antonio_kodheli](https://www.prompt-motion.com/antonio-kodheli-490109), which drops `<start>`;
  - [#38 Ora 2 image model launch film — @rossaxbt](https://www.prompt-motion.com/rossaxbt-3085b7), which adds `<script>` `<voice>` `<sound>`;
  - [#52 Food craving launch film — @ultimaxbt](https://www.prompt-motion.com/ultimaxbt-2ddf1e), the latest, on 10-08.
- **Why it matters:** it's a template that travels between accounts.

| Other format | Entry | Notes |
|---|---|---|
| XML with its own tags | [#66 Spotify product film — @brainextends](https://www.prompt-motion.com/brainextends-e19ac3) | Deliverables, art direction, timeline, a persistent player, motion quality, audio, validation |
| Sectioned brief with ruled headings | [#104 Taxtello bookkeeping app film — @daniel_haida](https://www.prompt-motion.com/daniel-haida-8691d4) | 15,306 characters, the longest prompt in the gallery; 16 headings, from source of truth through a quality bar to final deliverables |
| Caps headings in one block | [#100 Speech built as architecture — @Gdgtify](https://www.prompt-motion.com/gdgtify-287ddf) | Art direction, exact speech, storyboard, choreography, engineering, quality gate |
| Reusable placeholder template | [#126 Paper-style product launch film — @ik_builds](https://www.prompt-motion.com/ik-builds-b8bdcf) | `{{PRODUCT}}`, `{{POSITIONING_DOCS}}`, `{{BANNED_WORDS}}`…; the gallery's only HyperFrames long spec |
| Bulleted brief or one long paragraph | 9 entries | 500–1,006 characters; see [Appendix B](#appendix-b-the-23-prompts-over-500-characters) |

### 3.2 Section by section

**`<inputs>`: ask first, fall back to defaults.** This is what makes a prompt reusable.

- **What the model asks for:** product name, logo, the UI moments to show, footage and a track.
- **Defaults when the user skips something.** Four specs (#10, #34, #38, #52) supply them; #10 puts it as "If I skip any, use the defaults".
- **Licensing.** Every long spec that names a music source names one that's free for commercial use. Mixkit appears in 9 prompts. #104 forbids pulling copyrighted audio from the internet, and #126 limits sound to CC0 or self-generated.

**`<direction>`: one look, one motion rule, one banned list.**

- **Continuity is written as a hard rule.** Five specs (#2, #5, #25, #52, #97) demand one continuous take, or one object that links every scene. Two examples: "One shape, never cut" (#2) and "The orange dot connects every scene" (#25).
- **Camera rules are constraints, not wishes.** #52 asks for one eased move per scene and no zooming in and out back to back. #178 never allows two camera moves at once.
- **Restraint is the stated goal.** #104 would rather have a few extraordinary moments than many average ones.

**Banned lists are taste, not industry rules.** We counted an item only where the prompt forbids it:

| Banned item | Banned in | Asked for in |
|---|---|---|
| Dead time, long holds, frozen frames | 9 | — |
| Particles | 8 | 2: [#41 Motion techniques showreel — @lukasersil](https://www.prompt-motion.com/lukasersil-0ed38e), [#105 Badge unlock screen animation — @BThreeAgency](https://www.prompt-motion.com/bthreeagency-b9b8d9) |
| A look that reads as a template | 8 | — |
| Glow | 7 | 3: #38, #52, [#134 SaaS launch video — @aschapmann](https://www.prompt-motion.com/aschapmann-131210) |
| Bouncy easing | 7 | — |
| Crossfades, or fades as the default transition | 7 | — |
| Gradients | 5 | several, as a palette or a glow |
| Corner HUD / timeline chrome | 4 | — |
| Invented numbers or features | 3 (#104, #126, #178) | — |

**`<structure>`: a beat sheet, measured in one of three units.**

- **Musical beats** are the most common: "120 BPM, 7 bars, something happens on every beat" (#2), with each action pinned to a bar or beat number.
- **Frames.** #10 times every shot to a frame number and pixel coordinates, and lands its hard cuts just before a beat.
- **Phrases.** #100 refuses to beat-lock: "Do not force the speech onto a dance beat." #38 cuts on the starts of voice-over phrases instead.
- **Loose framing.** At the other end of the precision scale, #104 offers its storyboard as "a strong starting point, not a rigid template".

**`<build>`: make the render deterministic and repeatable.**

- **Frames depend on the timestamp and nothing else.** Thirteen prompts require seek(t)-style rendering, which rules out CSS transitions, timers and any state that survives from one frame to the next. Two of them are short prompts ([#161 SaaS product launch video — @xelandre__](https://www.prompt-motion.com/xelandre-363f00), [#230 Token bucket rate limiter — @ParkerRex](https://www.prompt-motion.com/parkerrex-1a54fe)). Springs are written as closed-form functions so they stay seekable.
- **Motion blur from subframes.** Seven prompts render 3 to 8 subframes per frame, usually blended with ffmpeg's `tmix`. #52 learned the right count the hard way: "Four subframes leave ghost copies on fast moves, so render 8 and slow the move down."
- **Audio is placed by its measured peak.** Each sound effect is aligned so that its loudest point, "not its file start", lands on the event (#13). Seven prompts do this, and eight master to −14 LUFS.
- **Camera and handoffs.**
  - One transform on a world container, with zoom interpolated in log space (#52, #178).
  - "Make every handoff a shared element" (#52).
- **Scrape the real thing first, and invent nothing.**
  - #178 scrapes the site and says "Quote all of it verbatim."
  - #104 inspects the product repos before designing anything.
  - Engineering hygiene comes with it: all cue times live in one file and all strings in another.

**`<gotchas>`: lessons you only learn by shipping.** This is the hardest section to write from scratch and the most valuable one.

- **Full-frame fills.** A shape that floods the frame must overshoot every corner and take a few frames. Otherwise half the screen changes in a single frame (#5, with #52 and #25 making the same point).
- **3D.** Fading or filtering a `preserve-3d` element flattens it, so fade its wrapper instead (#13).
- **Fonts.** Measure text only after fonts load, and scale the whole lockup when a long name doesn't fit (#10).
- **Scaled text.** Text the camera scales renders blurry if it carries `will-change` (#2).
- **Same-colour tiles.** A tile that matches the page colour disappears unless it has a 1 px hairline (#178, #10).
- **Fades.** "A 0.05s fade looks like an instant pop-in." (#38)
- **Text swaps.** Text that changes inside a moving shape needs separate exit and entry timing (#2, #25, #66).

**`<start>`: an approval gate before the expensive part.** Nine specs end with a `<start>` that says three things:

1. ask for the inputs;
2. show a beat map, a storyboard or 4–8 stills;
3. build the full film only after approval.

#178 does the same in prose.

**QA after render.**

- **Frame checks.** Four prompts render one frame per beat (#2, #5, #25, #97). Four (#5, #38, #52, #178) scan the whole render for single-frame jumps. #5 flags "frame-difference spikes 3x their neighbours".
- **A fresh reviewer.** #178 asks to "have a fresh critic who didn't build it review the render, and fix what it finds."
- **Judge the real output.** #104 inspects frames decoded from the final MP4, not browser screenshots, and closes with: "Do not declare success because the code compiles. The deliverable is the FILM."
- **Short prompts can carry QA too.** #134 asks the model to "render it, check the frames yourself and fix anything that overlaps, clips or feels rushed before showing me the result".

### 3.3 Good moves from shorter briefs

- **Animate real assets, not screenshots.** [#32 mdfor.dev product intro video — @HO_BA](https://www.prompt-motion.com/ho-ba-f3f0e9) asks to "break them down into components/icons so we can animate those too."
- **Use only facts from the source.** "Use only facts and numbers that are on the site." ([#127 Developer portfolio site showreel — @wani_shola](https://www.prompt-motion.com/wani-shola-16ca7a)). #126 bans invented results outright.
- **Write the story arc down.**
  - #134 goes market → pain → fix → payoff.
  - [#18 Animated business explainer — @alex_prompter](https://www.prompt-motion.com/alex-prompter-1ea044) goes problem → what I do → three steps → one proof → name.
- **Let one rule carry the film.** "every note comes from a visible collision" ([#200 Collision-driven music machine — @KamStudioLabs](https://www.prompt-motion.com/kamstudiolabs-447565)). Or a single object travels through every scene (#25, #126).
- **A prose shot list works too.** [#77 Sahi trading terminal reveal — @dale_vaz](https://www.prompt-motion.com/dale-vaz-cc612a) describes a camera journey from a single dot out to a full desktop and back, without any tags.

---

## 4. Applying this to SaaS launch films

1. **Explore with a one-liner.** Use the brand-slot variant and run it inside the product repo. Run each version 2–3 times before you judge it: the same prompt swings by a point or two (section 2.6), and repo context visibly changes the output (section 1.4). Picking the best of several takes is the lever you actually control.
2. **Drop the showreel framing** if you want a product film. It pulls toward HUD-heavy technique montages (section 1.3) and doesn't raise the blind score (+0.11, p ≈ 0.31). "Go all out" is harmless to keep, but don't expect it to improve the film: the blind re-grade found no effect ([section 2.7](#27-blind-re-grade-what-survives)).
3. **Switch to a structured spec once you have a direction.** It won't make the film more impressive. It will make it about your product, in your format, built from real UI and real facts, with an approval gate before the expensive render.
4. **Borrow the gotchas and the QA gates first.** They're the least obvious part of a spec, and they cost nothing to include.

We wrote our own template from scratch for HyperFrames: [`templates/saas-launch-film.hyperframes.md`](../templates/saas-launch-film.hyperframes.md).

---

## Appendix A: family membership

A, verbatim (33): [#1 @stephanlivera](https://www.prompt-motion.com/stephanlivera-df17a2), [#3 @shneural](https://www.prompt-motion.com/shneural-2abdfa), [#4 @ajith_io](https://www.prompt-motion.com/ajith-io-b5626e), [#6 @himanshutwtxs](https://www.prompt-motion.com/himanshutwtxs-5f4b43), [#7 @gabrielbuzziv](https://www.prompt-motion.com/gabrielbuzziv-4ff0c6), [#11 @thismacapital](https://www.prompt-motion.com/thismacapital-dfba20), [#21 @thayto_dev](https://www.prompt-motion.com/thayto-dev-44b911), [#30 @jasonzhou1993](https://www.prompt-motion.com/jasonzhou1993-8595e0), [#39 @tequilafunks](https://www.prompt-motion.com/tequilafunks-97f6c9), [#50 @ayushunleashed](https://www.prompt-motion.com/ayushunleashed-ece3e3), [#60 @eyishazyer](https://www.prompt-motion.com/eyishazyer-af035b), [#61 @blue_clarity](https://www.prompt-motion.com/blue-clarity-ef56d0), [#69 @RaphaelAubryy](https://www.prompt-motion.com/raphaelaubryy-4b137e), [#72 @codeSTACKr](https://www.prompt-motion.com/codestackr-c071bf), [#115 @MisbahSy](https://www.prompt-motion.com/misbahsy-80eaec), [#118 @motiondsgnr](https://www.prompt-motion.com/motiondsgnr-9dcfa6), [#129 @mrtanviir](https://www.prompt-motion.com/mrtanviir-132457), [#136 @Web3Wesley](https://www.prompt-motion.com/web3wesley-7bb108), [#156 @m1n9_k7](https://www.prompt-motion.com/m1n9-k7-ff9ab9), [#168 @zaqailo](https://www.prompt-motion.com/zaqailo-212ad3), [#169 @CrazyAlphaaa](https://www.prompt-motion.com/crazyalphaaa-bc7e75), [#170 @fionntobin](https://www.prompt-motion.com/fionntobin-97b7af), [#172 @itsuki_dev](https://www.prompt-motion.com/itsuki-dev-10942d), [#177 @tolgayhickiran](https://www.prompt-motion.com/tolgayhickiran-e90799), [#187 @3xtihor](https://www.prompt-motion.com/3xtihor-0f6911), [#192 @LeonKohli](https://www.prompt-motion.com/leonkohli-6dc01b), [#193 @marouanegazouzi](https://www.prompt-motion.com/marouanegazouzi-6071d5), [#195 @safarkhanshuvo](https://www.prompt-motion.com/safarkhanshuvo-ffd52d), [#196 @sahildesigner23](https://www.prompt-motion.com/sahildesigner23-ee3155), [#217 @TeslaChartz](https://www.prompt-motion.com/teslachartz-c58b32), [#222 @leadnotifi](https://www.prompt-motion.com/leadnotifi-e83f94), [#226 @Shinskinakamoto](https://www.prompt-motion.com/shinskinakamoto-20190b), [#227 @umangratani](https://www.prompt-motion.com/umangratani-57f86a)

B, verbatim + appended sentence (8): [#14 @samuel_yostt](https://www.prompt-motion.com/samuel-yostt-891f87), [#17 @steventey](https://www.prompt-motion.com/steventey-0d20e4), [#143 @Adamdesgns](https://www.prompt-motion.com/adamdesgns-478d6d), [#152 @Sudiyasa_](https://www.prompt-motion.com/sudiyasa-f48ac9), [#166 @levabashidze](https://www.prompt-motion.com/levabashidze-2d713a), [#174 @kyonax_on_tech](https://www.prompt-motion.com/kyonax-on-tech-aabc1d), [#181 @danilowm](https://www.prompt-motion.com/danilowm-d3720d), [#191 @johnsavage_ai](https://www.prompt-motion.com/johnsavage-ai-b091c0)

C, duration / aspect / theme changed (14): [#28 @jacksonfall](https://www.prompt-motion.com/jacksonfall-54b2ac), [#32 @HO_BA](https://www.prompt-motion.com/ho-ba-f3f0e9), [#44 @gizakdag](https://www.prompt-motion.com/gizakdag-cf4ae6), [#48 @polydao](https://www.prompt-motion.com/polydao-7a572b), [#53 @monokern](https://www.prompt-motion.com/monokern-ade5b6), [#56 @Math_files](https://www.prompt-motion.com/math-files-39c9d0), [#107 @ndhabarde11](https://www.prompt-motion.com/ndhabarde11-f155b4), [#109 @rendesr](https://www.prompt-motion.com/rendesr-86be44), [#112 @jesscaroline7](https://www.prompt-motion.com/jesscaroline7-1ff7cb), [#142 @elliot_garreffa](https://www.prompt-motion.com/elliot-garreffa-f334bc), [#175 @loicRambo](https://www.prompt-motion.com/loicrambo-ad6830), [#186 @VanshWTFFF](https://www.prompt-motion.com/vanshwtfff-db0466), [#206 @thilina_a](https://www.prompt-motion.com/thilina-a-891c09), [#210 @ibrahimwasim240](https://www.prompt-motion.com/ibrahimwasim240-809370)

D, brand slot (21): [#12 @ajith_io](https://www.prompt-motion.com/ajith-io-c52e09), [#33 @itisRazak](https://www.prompt-motion.com/itisrazak-3ad902), [#37 @melvynx](https://www.prompt-motion.com/melvynx-6cde6c), [#47 @ajith_io](https://www.prompt-motion.com/ajith-io-4c248f), [#49 @ajith_io](https://www.prompt-motion.com/ajith-io-ea7f2d), [#76 @prasad_pilla](https://www.prompt-motion.com/prasad-pilla-2c0cba), [#91 @sudeepsd_](https://www.prompt-motion.com/sudeepsd-1a3485), [#102 @influencer_seo](https://www.prompt-motion.com/influencer-seo-ce8c33), [#103 @agonaliu_](https://www.prompt-motion.com/agonaliu-466a8f), [#111 @en______ra](https://www.prompt-motion.com/en-ra-81c6dd), [#113 @TheViableEdge](https://www.prompt-motion.com/theviableedge-9065be), [#116 @reyzostyle](https://www.prompt-motion.com/reyzostyle-b55864), [#128 @manuelogomigo](https://www.prompt-motion.com/manuelogomigo-f33ca9), [#132 @JayScambler](https://www.prompt-motion.com/jayscambler-3f8889), [#133 @utopyaszx](https://www.prompt-motion.com/utopyaszx-1b2f94), [#141 @Devius_Maximus](https://www.prompt-motion.com/devius-maximus-beab45), [#150 @bizibeast](https://www.prompt-motion.com/bizibeast-10f264), [#157 @quickdesignio](https://www.prompt-motion.com/quickdesignio-dd93d0), [#167 @miskinho_](https://www.prompt-motion.com/miskinho-443898), [#173 @KangarooHere](https://www.prompt-motion.com/kangaroohere-b10f8d), [#188 @Amol909S](https://www.prompt-motion.com/amol909s-27533e)

E, brand as subject (4): [#36 @ismailfahmi](https://www.prompt-motion.com/ismailfahmi-557268), [#119 @Astrodevil_](https://www.prompt-motion.com/astrodevil-3f2054), [#182 @KmAsiff](https://www.prompt-motion.com/kmasiff-cc72cb), [#184 @rammanq](https://www.prompt-motion.com/rammanq-f5a90f)

G, English rewrite (16): [#41 @lukasersil](https://www.prompt-motion.com/lukasersil-0ed38e), [#57 @hanifproduktif](https://www.prompt-motion.com/hanifproduktif-54bdee), [#62 @RoundtableSpace](https://www.prompt-motion.com/roundtablespace-d3a1be), [#71 @arjunsh1607](https://www.prompt-motion.com/arjunsh1607-93005d), [#81 @samuel_spitz](https://www.prompt-motion.com/samuel-spitz-974923), [#84 @AIStockSavvy](https://www.prompt-motion.com/aistocksavvy-3fb9f5), [#89 @zheke](https://www.prompt-motion.com/zheke-38deff), [#110 @BogdanDragomir](https://www.prompt-motion.com/bogdandragomir-35e024), [#127 @wani_shola](https://www.prompt-motion.com/wani-shola-16ca7a), [#137 @reflex_cloud](https://www.prompt-motion.com/reflex-cloud-72ffe5), [#144 @andginja](https://www.prompt-motion.com/andginja-333d32), [#151 @heyiammallik](https://www.prompt-motion.com/heyiammallik-e72d17), [#163 @HenkPoley](https://www.prompt-motion.com/henkpoley-3d3407), [#190 @ghinaiya_nirmal](https://www.prompt-motion.com/ghinaiya-nirmal-5d8fec), [#208 @blushpetal795](https://www.prompt-motion.com/blushpetal795-0c85c2), [#225 @samaote](https://www.prompt-motion.com/samaote-5e2fc2)

H, translation (6): [#51 @ChatGptAstra](https://www.prompt-motion.com/chatgptastra-0d95c7), [#59 @ddryo_loos](https://www.prompt-motion.com/ddryo-loos-300829), [#108 @_topi_003](https://www.prompt-motion.com/topi-003-9ca6b5), [#125 @_topi_003](https://www.prompt-motion.com/topi-003-b0e12c), [#189 @cansincengiz_me](https://www.prompt-motion.com/cansincengiz-me-cf68dd), [#201 @Grace_sunnyy](https://www.prompt-motion.com/grace-sunnyy-29bc61)

F, skeleton only (12): [#31 @robj3d3](https://www.prompt-motion.com/robj3d3-b18fad), [#63 @1littlecoder](https://www.prompt-motion.com/1littlecoder-9fef89), [#73 @hqmank](https://www.prompt-motion.com/hqmank-7c61f1), [#94 @paulo_kombucha](https://www.prompt-motion.com/paulo-kombucha-96431c), [#114 @0xfemyn](https://www.prompt-motion.com/0xfemyn-e114d3), [#121 @macrohou](https://www.prompt-motion.com/macrohou-33959d), [#164 @FractaDev](https://www.prompt-motion.com/fractadev-149adc), [#176 @madebyjmayala](https://www.prompt-motion.com/madebyjmayala-b9204d), [#204 @deebeeeff](https://www.prompt-motion.com/deebeeeff-50fcd0), [#209 @ceowinkz](https://www.prompt-motion.com/ceowinkz-7c776b), [#211 @Jazzen_Chen](https://www.prompt-motion.com/jazzen-chen-4542ae), [#215 @souravbhar871](https://www.prompt-motion.com/souravbhar871-61f424)

## Appendix B: the 23 prompts over 500 characters

| Entry | Characters | Format | Stack stated |
|---|---|---|---|
| [#104 Taxtello bookkeeping app film — @daniel_haida](https://www.prompt-motion.com/daniel-haida-8691d4) | 15,306 | Sectioned brief (16 ruled headings) | Remotion |
| [#10 Launch video remake comparison — @notdwd](https://www.prompt-motion.com/notdwd-c2037d) | 10,419 | Six-tag XML (frame-exact) | — |
| [#34 Frame by Frame launch video — @notdwd](https://www.prompt-motion.com/notdwd-7de38a) | 10,311 | Six-tag XML (near-identical to #10) | — |
| [#66 Spotify product film — @brainextends](https://www.prompt-motion.com/brainextends-e19ac3) | 8,142 | XML, own tag set (8 tags) | — |
| [#38 Ora 2 image model launch film — @rossaxbt](https://www.prompt-motion.com/rossaxbt-3085b7) | 5,800 | Six-tag XML + script / voice / sound | HTML canvas + Playwright + ffmpeg |
| [#5 Photo print app launch film — @twoclipping](https://www.prompt-motion.com/twoclipping-221cab) | 5,222 | Six-tag XML | HTML + Playwright |
| [#52 Food craving launch film — @ultimaxbt](https://www.prompt-motion.com/ultimaxbt-2ddf1e) | 4,667 | Six-tag XML | HTML |
| [#100 Speech built as architecture — @Gdgtify](https://www.prompt-motion.com/gdgtify-287ddf) | 4,373 | Caps headings in one block | SVG/Canvas |
| [#178 Prompt Motion site promo — @antonio_kodheli](https://www.prompt-motion.com/antonio-kodheli-490109) | 4,024 | Five-tag XML (no start tag) | Remotion |
| [#25 Orange dot motion system — @ultimaxbt](https://www.prompt-motion.com/ultimaxbt-bbebf5) | 3,367 | Six-tag XML | HTML |
| [#2 Shape morphing through UI states — @twoclipping](https://www.prompt-motion.com/twoclipping-5cba86) | 2,711 | Six-tag XML | HTML + Playwright |
| [#97 Morphing UI states loop — @demonugc](https://www.prompt-motion.com/demonugc-4c5753) | 2,711 | Six-tag XML (same text as #2) | HTML, Playwright |
| [#13 UGC ad generator promo — @twoclipping](https://www.prompt-motion.com/twoclipping-6dd14e) | 2,515 | Six-tag XML (earliest, 09-23) | HTML + Playwright |
| [#126 Paper-style product launch film — @ik_builds](https://www.prompt-motion.com/ik-builds-b8bdcf) | 1,528 | Placeholder template | HyperFrames + GSAP |
| [#127 Developer portfolio site showreel — @wani_shola](https://www.prompt-motion.com/wani-shola-16ca7a) | 1,006 | Bulleted brief | Remotion |
| [#134 SaaS launch video — @aschapmann](https://www.prompt-motion.com/aschapmann-131210) | 996 | One long sentence | Remotion |
| [#8 Engraving-style Claude ad — @LexnLin](https://www.prompt-motion.com/lexnlin-038035) | 994 | Numbered brief + reference video | — |
| [#41 Motion techniques showreel — @lukasersil](https://www.prompt-motion.com/lukasersil-0ed38e) | 744 | Paragraph (technique list) | — |
| [#77 Sahi trading terminal reveal — @dale_vaz](https://www.prompt-motion.com/dale-vaz-cc612a) | 631 | Prose shot list | JavaScript |
| [#32 mdfor.dev product intro video — @HO_BA](https://www.prompt-motion.com/ho-ba-f3f0e9) | 597 | One-liner + extra requirements | — |
| [#137 Reflex brand motion reel — @reflex_cloud](https://www.prompt-motion.com/reflex-cloud-72ffe5) | 544 | Paragraph | — |
| [#85 Visual guides library launch — @techyoutbe](https://www.prompt-motion.com/techyoutbe-945b56) | 519 | Paragraph | — |
| [#197 Sketchbook animals come alive — @abderrahmen_g](https://www.prompt-motion.com/abderrahmen-g-9e8ed0) | 502 | Paragraph + asset folder | JavaScript |

## Changelog

- 2026-10-09: added blind re-grade; corrected the pressure-phrase finding.
