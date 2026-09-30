# Project notes for frame workers (read before building — these override defaults)

## Resolved questions — do not re-investigate (saves your budget)

- `id="stage"` in every frame file is correct per the contract: the compiler scopes each frame's CSS to `[data-composition-id="<frame_id>"]` and wraps its script (`packages/core/src/compiler/compositionScoping.ts`). Still prefix every OTHER id with your frame tag (`f01-`, `f02-`, …) so ids are unique project-wide, and prefer element references over global string selectors in GSAP where convenient.
- Asset paths: project-root-relative `assets/...` works as-is inside `compositions/frames/*.html` (`packages/parsers/src/rewriteSubCompPaths.ts`), for `src` and for CSS `url()`.
- `hyperframes media-treatment` finds an `<img>` inside a `<template>` by id — verified. Just give the hooks (id + `treat-bw` / `treat-color`).
- Pretendard woff2 files contain full modern Hangul — no need to check glyph coverage (no fontkit / fontTools work).
- GSAP may tween `clip-path` (keep the same number of points / same `inset()` form at both ends), CSS custom properties, and transforms. No plugins beyond core gsap are loaded.
- The ㅡ-of-극 measurement is given in the frame-02 dispatch; do not measure glyphs with tools.
- A previous attempt at every frame was cut off by a rate limit before any file was written. Start fresh, keep investigation minimal, and write the file.

## Plugin paths (absolute — skills are plugin-installed)

- `SKILL_DIR` (music-to-video) = `C:/Users/User/.claude/plugins/cache/hyperframes/hyperframes/0.8.81/skills/music-to-video`
- Core contracts: `C:/Users/User/.claude/plugins/cache/hyperframes/hyperframes/0.8.81/skills/hyperframes-core/references/sub-compositions.md`, `determinism-rules.md`, `data-attributes.md`, plus the section "First-pass lint gotchas" in `C:/Users/User/.claude/plugins/cache/hyperframes/hyperframes/0.8.81/skills/hyperframes-core/SKILL.md`.
- Motion primitives: `SKILL_DIR/references/motion-primitives/<id>/scene.html` (+ `index.html`); catalog: `SKILL_DIR/references/motion-primitive-catalog.md`. Primitives named in the storyboard without a folder (system-replace, palette-flip, content-swap, freeze-hold, negative-space-hold, staggered-reveal) are described in the catalog table — implement them directly.
- Never run the `hyperframes` CLI, `npx`, or `skills update`. Write only your own frame file.

## Studio rules (from CLAUDE.md)

- Deterministic: no `Math.random` (seed a mulberry32 PRNG), no `Date.now`, no CSS transitions, no `setTimeout` / `setInterval` / `requestAnimationFrame`, no state carried between frames. Everything is driven by the one paused GSAP timeline.
- Banned: centered title on a gradient, everything fading in, corner labels / frame borders / watermark, glow on UI chrome, generic particle bursts.
- Something new happens on screen every 2–4 s.
- One accent colour per section.

## TEXT LEGIBILITY — user rule

User (verbatim): "실제로 캐릭터가 글자를 너무 가리진 않도록 모션 그래픽 잡을때 신경 써줘. 특히 "역시" 쪽에서 "시"를 많이 가릴거 같아서 혹시나 해서."

- A figure never covers more than ~15% of any headline glyph, never sits on a glyph's key stroke, and never covers a copy line — at any moment of the motion, not just the rest pose.
- When a figure overlaps big type, the figure goes BEHIND the type (type has the higher z-index) and shows through the gaps.
- Frame 02, '역시': the HL pair stands behind the type with both faces in the gap between '역' and '시'; '시' fully readable throughout.

## Brand

- `frame.md` (biennale-yellow) = palette hex ONLY: sun `#F1EE2E`, ink `#1B2566`, ember `#E26B4A`, haze `#F0DA7C`, paper `#E9E5DB`. Ignore its typography and its editorial-calm prose.
- All text is Pretendard. Put an in-file `@font-face` (inside your `<template>`'s `<style>`) for every weight you use, family name `"Pretendard"`:
  - 900 → `assets/fonts/pretendard/Pretendard-Black.woff2`
  - 800 → `assets/fonts/pretendard/Pretendard-ExtraBold.woff2`
  - 700 → `assets/fonts/pretendard/Pretendard-Bold.woff2`
  - 600 → `assets/fonts/pretendard/Pretendard-SemiBold.woff2`
  Use these project-root-relative paths exactly; the compiler keeps them as written.
- Look: grunge kinetic poster (A) + traditional palace (B), see `references/ref-01..10.png`. Halftone dot ground (CSS radial-gradient pattern), grain, RGB fringe on display type, grunge texture on display type.

## Confirmed sketch = layout contract

`storyboard.html` (project root) has one cell per group: ids `frame-NN-gK`, anchor `frame-NN`. Read the cell markup: positions and sizes are in `cqw` of a 16:9 frame (1cqw = 19.2px on the 1920 canvas). Your build dresses that layout (real assets, texture, motion) and never redraws it.
Sheet-only CSS — do NOT copy: `.art.bw` / `.art.fr` / `.art.ghost` filters, `.ph` labels, `.meta` / `.note` / `.chip`, the `.grunge` mask (use the real component instead), `.row3d`'s static transforms are fine as a layout reference.

## Assets (project-root-relative paths)

- Characters (transparent, trimmed PNG): `assets/characters/HL-pair.png` 721×904 · `assets/characters/HL-pair-2.png` 693×1294 · `assets/characters/BL-pair.png` 817×901 · `assets/characters/M-group.png` 496×671.
- Props: `assets/props/coin.png` 1024×1024 (gold coin, transparent square hole) · `assets/props/knot.png` 1024×1536 (red knot; the cord starts at the top edge) · tinted, 1536×1024, transparent: `assets/props/tinted/palace-paper.png` (paper-coloured engraving lines), `brush-1-ink.png`, `brush-1-sun.png` (long dry brush stroke), `brush-2-ember.png`, `brush-2-ink.png` (ink splatter). Use them as plain `<img>`; no CSS `mask-image`.
- Finale covers (600×800): `assets/covers/{hajungjeon,agony,cloud,audum,yeoksal,madeye}-tall.jpg`.
- Character image hooks: every character `<img>` gets a unique id `fNN-gK-name` (e.g. `f02-g1-hlpair`) and class `treat-bw` (B&W + RGB fringe, A-style scenes) or `treat-color` (colour + light fringe). NO CSS `filter` on any `<img>` and do not animate `filter` — the orchestrator applies the look afterwards with `hyperframes media-treatment` on those ids.
- Logo: file pending. Use a placeholder box with id `f04-logo` containing the text "레진 로고".
- Installed registry components (inline them per each file's comment block): `compositions/components/texture-mask-text/texture-mask-text.html` (masks in `assets/texture-mask-text/masks/`), `compositions/components/grain-overlay.html`, `compositions/components/rgb-glitch-text.html`.

## Lint traps

- Group containers are plain `<div>`s: no `class="clip"`, no `data-start` — you show/hide them with `tl.set(autoAlpha)`.
- Never give an element a CSS `transform` that GSAP also tweens; set initial states with `gsap.set` / `fromTo`.
- Never tween a `.clip` with `autoAlpha` / `visibility`.
- Sub-composition root uses `width/height: 100%` (or `inset: 0`), never hardcoded 1920/1080; the canvas size lives in `data-width` / `data-height`.
