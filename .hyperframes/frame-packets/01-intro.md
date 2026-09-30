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
frame_id: 01-intro
Your block: the `## Frame 1 — 01-intro` block in PROJECT_DIR/STORYBOARD.md
audiomap: PROJECT_DIR/audiomap.json
frame.md: PROJECT_DIR/frame.md
Materials: for each group, <SKILL_DIR>/references/templates/<id>/index.html (templates) and <SKILL_DIR>/references/motion-primitives/<id>/ (free); staged assets/ (asset groups)
Contracts: ../hyperframes-core/references/sub-compositions.md + determinism-rules.md
Canvas: 1920×1080   Pacing: beat_cut
Write to: PROJECT_DIR/compositions/frames/01-intro.html
```

This frame has a **confirmed sketch** at `storyboard.html#frame-01`: build dresses that layout, never redraws it.

**Read first:** `D:/code/motion-video/.hyperframes/frame-packets/_project-notes.md` (resolved questions, absolute skill paths, studio rules, the user's text-legibility rule, fonts, assets, image hooks, components, lint traps — it overrides defaults), then the `build_notes` / `avoid` / `## Decisions` of STORYBOARD.md.

Frame-specific notes (01-intro, track 0.0–13.026; frame-local = track seconds):
- g1: ink ground with halftone dots + grain from the first frame. At 0.65 a small gold dot (DOM/SVG circle, haze) drops to centre; two knots (`assets/props/knot.png`) swing in from the top corners — pendulum around the top centre (transform-origin 50% 0), finite timeline tweens only. The engraved palace (`assets/props/tinted/palace-paper.png`) reveals with a clip-path wipe from about 0.65 to 3.4. At 3.413 the dot flares; by 4.667 it has become the coin (`assets/props/coin.png`, crossfade/scale from the dot).
- g2: at 5.294 a paper ㅡ bar sweeps left→right through the coin (scaleX from left); at 7.918 a paper ㅣ bar drops top→bottom (scaleY from top). At 9.590 "1446 → 2026" (700, haze); at 10.472 "제580돌 한글날" (900, paper, lower-left, two lines) with a haze sheen sweep (chrome-sweep primitive). At 12.144 the coin flares. Keep the knots' sway alive through g2.
- Something new every 2–4 s; palace/knots/coin keep subtle motion between anchors.

When done, reply with: the file path, the frame-local anchor times you used, and anything you could not realize.
