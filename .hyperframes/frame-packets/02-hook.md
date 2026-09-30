# Frame worker — per-frame composition author (music-to-video)

You build one frame's composition file: `compositions/frames/<frame_id>.html`. Siblings build the other frames in parallel. The generic HyperFrames law — sub-composition shape, timeline registration, determinism, layout — lives in `hyperframes-core` (`references/sub-compositions.md`

- `determinism-rules.md` + `data-attributes.md`); read it first. This file covers the music-specific part.

Your job: **follow the manual, fetch the materials, assemble.** The storyboard tells you WHAT (the frame's groups, each group's template / primitives, content, brand, real beat-anchor seconds). You decide HOW (fetch the materials, bind them to this frame's audio seconds, micro-timing, layout, namespacing).

## Inputs (your dispatch context)

- `PROJECT_DIR` — project root; all paths relative to it.
- `frame_id` — the frame file's stem, e.g. `02-f2`. Use it verbatim as the composition id, the `window.__timelines` key, and the filename `compositions/frames/<frame_id>.html` (the assembler matches on it).
- Your **`## Frame N` block** in `STORYBOARD.md` — its `span_sec`, `pacing`, `mood`, `feel`, and its **`### Groups`** list. Each group is one of:
  - **template** — `template:<id>` + `params` + `role_bindings` (real audiomap anchor seconds) + `copy`.
  - **free_design** — `free_design:{dominant_system, primitives, density_topology}` + `anchors[]` + `copy`.
  - **asset** — `asset:{treatment, clips, anchors?, overlay_copy?}` (see `montage.md`).
- `audiomap.json` — timing truth; use the seconds you're given.
- `frame.md` — the brand (palette + type). Pull every visual token from here.
- **Materials** — `references/templates/<id>/index.html` (its `data-composition-variables` give the param semantics) for template groups; `references/motion-primitives/<id>/scene.html` (the sub-composition; `index.html` only mounts it and holds the page background and font) for free groups; staged `assets/…` for asset groups.
- Canvas `<width>×<height>` and the frame's `pacing`.

If your dispatch carries `lint` / `check` feedback from a prior pass, address each finding.

## What comes fixed — realize it as given

- **No plan = stop.** If your `### Groups` is `TBD`/empty (Step 3 was skipped), report back and write nothing — never invent groups, templates, or copy.
- **The plan** is set in your `## Frame` block: the groups, templates / primitives, copy, brand, and anchors. Build it as written. If a plan is genuinely wrong (wrong template or copy), stop and report — the orchestrator re-plans at Step 3.
- **Transitions** are the assembler's: it hard-cuts between frames. You author the frame's **internal** group→group cuts only.
- **Audio** lives on the root `index.html`; your frame is silent.
- **GSAP** is loaded by the host; use the global `gsap` (your frame carries no gsap `<script>`).
- **Duration** is the frame span length; build your timeline to run `0 … span_len`.

## Build

1. **Read** your `## Frame` block, `frame.md`, and the body of every template / primitive it cites. Reproduce those recipes.
2. **Work in frame-local time.** Subtract the frame start from every anchor: `local_t = track_t − span_sec[0]`.
3. **Author** `compositions/frames/<frame_id>.html`: a `<template>` wrapping `#stage` (`data-composition-id="<frame_id>"`), with all `<style>` / `<script>` inside it, and one paused `gsap.timeline({paused:true})` registered at `window.__timelines["<frame_id>"]`, built synchronously, ending in `tl.seek(0)`. Give each group its own container; show it across its frame-local span with `tl.set("#g1",{autoAlpha:1}, start)` / `tl.set("#g1",{autoAlpha:0}, end)` (this 0ms swap is the group→group cut); namespace each group's ids and shader uniforms `g1_` / `g2_`. When forking a template, inline its DOM / CSS / tweens and use the host's global `gsap`. On a `phrase_flow` frame, pace by phrase / energy.
4. **Self-check and finish.** Run the checklist and fix in place. Writing the file is your terminal action; the orchestrator runs `lint` / `check` and snapshots after assembly (Step 6) and re-dispatches you with any finding.

## Self-check

- `<template>`-wrapped `#stage`; `data-composition-id` == timeline key == filename stem == `<frame_id>`; all `<style>` / `<script>` inside `<template>`; uses the host's global `gsap`.
- One paused timeline, registered, ending in `tl.seek(0)`; `data-duration` == frame span length; silent.
- Each group shows across its frame-local span and hides outside it; `t=0` renders; group→group cuts are 0ms; ids / uniforms namespaced.
- Each group's text / palette match its block's `params` / `copy`, drawn from `frame.md`.
- `phrase_flow` frames pace by phrase / energy.
- Seek-safe per `hyperframes-core/determinism-rules.md` (derive variation from indices; swap text / numbers with `tl.set`).
- Asset clips: muted `<video>`, direct children of `#stage`, with `data-start` / `data-duration` / `data-track-index`. Crossfade outgoing clips to `opacity:0` ending at the next anchor.
- Final frame is intentional; hero text is readable and clear of the edges.

## Dispatch context

```text
PROJECT_DIR: D:/code/motion-video
frame_id: 02-hook
Your block: the `## Frame 2 — 02-hook` block in PROJECT_DIR/STORYBOARD.md
audiomap: PROJECT_DIR/audiomap.json
frame.md: PROJECT_DIR/frame.md
Materials: for each group, <SKILL_DIR>/references/templates/<id>/index.html (templates) and <SKILL_DIR>/references/motion-primitives/<id>/ (free); staged assets/ (asset groups)
Contracts: ../hyperframes-core/references/sub-compositions.md + determinism-rules.md
Canvas: 1920×1080   Pacing: beat_cut
Write to: PROJECT_DIR/compositions/frames/02-hook.html
```

This frame has a **confirmed sketch** at `storyboard.html#frame-02`: build dresses that layout, never redraws it.

**Read first:** `D:/code/motion-video/.hyperframes/frame-packets/_project-notes.md` (resolved questions, absolute skill paths, studio rules, the user's text-legibility rule, fonts, assets, image hooks, components, lint traps — it overrides defaults), then the `build_notes` / `avoid` / `## Decisions` of STORYBOARD.md.

Frame-specific notes (02-hook, track 13.026–25.821; frame-local = track − 13.026):
- g1: frame-local 0 is the system-replace from the dark intro to a sun ground (halftone + grain). One giant word per hit: "한글날엔" at track 13.421, "역시" at 15.557, "사극" at 17.252 (900, ink, grunge texture via the texture-mask-text component, RGB fringe). **User rule for '역시' (critical):** match sketch cell `frame-02-g1` — the HL pair (`assets/characters/HL-pair.png`, id `f02-g1-hlpair`, class `treat-bw`) sits BEHIND the type (type has the higher z-index) with both faces in the gap between '역' and '시'. '시' fully readable at every moment of its entrance and hold; the figure may slide in behind, never across the strokes.
- g2: on the SURGE (track 18.112) the ㅡ of '극' stretches into a full-width ink bar while the view pans left→right (ref-03). Measurement from the sketch (line-height .86, font-size 40cqw, top 5cqw): the ㅡ of 극 spans y ≈ 18.4–23.2cqw; the bar starts inside the stroke at x ≈ 30cqw so the seam hides; scaleX from its left edge. If you change glyph size/position, re-derive: ㅡ top ≈ top + 0.335×font-size, thickness ≈ 0.12×font-size. Lineup per sketch cell `frame-02-g2`: HL-pair behind the bar, M-group behind, BL-pair in front (all `treat-bw`, ids `f02-g2-…`). Short shake at 19.064.
- g3: per sketch cell `frame-02-g3`: four casts (HL-pair, HL-pair-2, BL-pair, M-group; `treat-bw`; ids `f02-g3-…`) with feet behind the bar; "스물여덟 자에 새긴" lands on the bar at 20.712 (700, sun on ink); "연모와 칼끝" at 23.266 (900, ink, large, lower left). Slow drift of the lineup; LOW stretch 23–25 holds; 25.17 primes the cut. Copy lines clear of every figure.
- Something new every 2–4 s.

When done, reply with: the file path, the frame-local anchor times you used, and anything you could not realize.
