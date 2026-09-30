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
frame_id: 03-ganada
Your block: the `## Frame 3 — 03-ganada` block in PROJECT_DIR/STORYBOARD.md
audiomap: PROJECT_DIR/audiomap.json
frame.md: PROJECT_DIR/frame.md
Materials: for each group, <SKILL_DIR>/references/templates/<id>/index.html (templates) and <SKILL_DIR>/references/motion-primitives/<id>/ (free); staged assets/ (asset groups)
Contracts: ../hyperframes-core/references/sub-compositions.md + determinism-rules.md
Canvas: 1920×1080   Pacing: beat_cut
Write to: PROJECT_DIR/compositions/frames/03-ganada.html
```

This frame has a **confirmed sketch** at `storyboard.html#frame-03`: build dresses that layout, never redraws it.

**Read first:** `D:/code/motion-video/.hyperframes/frame-packets/_project-notes.md` (resolved questions, absolute skill paths, studio rules, the user's text-legibility rule, fonts, assets, image hooks, components, lint traps — it overrides defaults), then the `build_notes` / `avoid` / `## Decisions` of STORYBOARD.md.

Frame-specific notes (03-ganada, track 25.821–33.483; frame-local = track − 25.821). Three one-bar blocks, each a hard 0ms cut:
- g1 '가' (25.821–28.352): sun ground + halftone; `assets/characters/HL-pair-2.png` ghosted large behind (id `f03-g1-hlpair2`, `treat-color`, opacity ≈ 0.16); `assets/props/tinted/brush-1-ink.png` wipes in on a diagonal (clip-path reveal); "가" (900, ink, grunge + RGB fringe) slams at 25.821 on the left; the HL pair (`assets/characters/HL-pair.png`, id `f03-g1-hlpair`, `treat-color`) enters on the right; `assets/props/coin.png` returns beside "가볍게, 단 1코인".
- g2 '나' (28.352–30.906): palette flip to ember at 28.328; two ink panels; the BL pair (`assets/characters/BL-pair.png`, id `f03-g2-blpair`, `treat-color`) breaks out over the panel tops; "나" (900, paper) huge on the left; copy "나눠 드려요, 100% 코인백" below.
- g3 '다' (30.906–33.483): inversion to ink at 30.999; "다" in sun; the M-group (`assets/characters/M-group.png`, id `f03-g3-mgroup`, `treat-color`) on the right; `brush-2-ember.png` splash + `brush-1-sun.png` flick. Copy "다 풀었다, 특별편 OPEN" below. End clean (the riser at 33.530 belongs to the next frame).
- Copy lines are example values: render as written plus a small outlined "예시" tag (class `ex-tag`) after each. Keep copy lines and big syllables clear of figures.
- Something new every 2–4 s; one accent per block.

When done, reply with: the file path, the frame-local anchor times you used, and anything you could not realize.
