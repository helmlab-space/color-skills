# color-skills

**Agent skills for color work: which color space to use for which task, and how to use the helmlab library.**

[![install](https://img.shields.io/badge/install-npx%20skills%20add-34d399)](https://www.npmjs.com/package/skills)
[![license](https://img.shields.io/badge/license-MIT-blue)](LICENSE)

```bash
npx skills add helmlab-space/color-skills
```

Installs into Claude Code, Codex, Gemini CLI, Cline and friends. Plain markdown — paste into `.cursorrules` or any system prompt if you prefer.

## Why this exists

No color space suits every task. The right move is *routing* — picking the space per task — and AI assistants often get it wrong: they compute ΔE in OKLab, blur images in gamma space, and hallucinate library APIs.

## The skills

### `color-space-routing`

Task → space routing. Vendor-neutral: routes to OKLab, CIELAB, CAM16, Jzazbz, linear sRGB, okhsl or Helmlab, depending on the task.

- **Routing table**: gradients, palettes, ΔE, gamut mapping, CVD-safe palettes, HDR/PQ, color pickers, video pipelines, physical light ops, CSS-only
- **Form rules**: when to use rectangular (Lab) vs cylindrical (LCh) coordinates — mixing and distance vs hue rotation and chroma clipping
- **Testing checklist**: sanity anchors (ΔE00(red,green)=86.6), gray-axis/endpoint checks, boundary round-trips, ΔE-tolerance snapshots instead of brittle hex asserts
- **Graveyard**: approaches we tried and dropped, so your assistant stops re-proposing them
- **11 pitfalls**, every one a bug observed in real code

### `helmlab`

Correct API usage of the [helmlab](https://github.com/helmlab-space/helmlab) library (npm + PyPI). Two-space mental model (GenSpace for generation, MetricSpace for measurement), verified example outputs, and the gotchas that break generated code — exporter input space, per-language `distance()` contracts, 0–1 L scale, hallucinated methods.

## Evaluation

In July 2026 both skills were evaluated on auto-verifiable tasks, solved in fresh headless sessions with and without the skill. Those results describe the skill versions of that time. On 2026-11-12 the skills changed (performance figures removed, see below) and they have not been evaluated again. Harness, tasks and raw answers: [helmlab/skills/…/eval](https://github.com/helmlab-space/helmlab/tree/main/skills/color-space-routing/eval).

The same evaluation compared a split layout (thin core + reference files) with single files; the split layout did worse, so the skills ship as single files.

## Evidence

The skills give no performance figures. Figures will be published on one evidence page at [helmlab.space](https://helmlab.space), where each figure names its dataset, its size (n), and whether that data was used to fit, tune or design the model.

## Updating

```bash
npx skills update
```

Source of truth lives in [helmlab-space/helmlab/skills](https://github.com/helmlab-space/helmlab/tree/main/skills); this repo is the install mirror.

## License

MIT © [Görkem Yıldız](https://github.com/Grkmyldz148)
