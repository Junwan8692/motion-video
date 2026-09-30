---
compositionId: hangul-day-40s
duration_s: 40.0
canvas: { w: 1920, h: 1080, fps: 30 }
mode: collaborative
message: "제580돌 한글날, 레진 사극 한마당 — 사극 BL·HL·남성향 주인공과 가·나·다 혜택을 40초에 꽉 채워 알린다"
audience: "레진 사극 장르 독자 (BL·HL·남성향)"
style:
  font: "Pretendard — Black 900 display / Bold 700 copy / SemiBold 600 label (assets/fonts/pretendard). Preset fonts Instrument Serif / Archivo / JetBrains Mono have no Hangul."
  palette: ["#F1EE2E", "#1B2566", "#E26B4A", "#F0DA7C", "#E9E5DB"]
assets: "cutouts assets/characters/{HL-pair,HL-pair-2,BL-pair,M-group}.png (official Lezhin key art, isnet-anime cutouts, native 1200×600 / 600×800); finale covers assets/covers/*-tall.jpg (6 official covers, 600×800); logo pending assets/logo/lezhin.(svg|png) — labelled placeholder until it lands; provenance assets/characters/SOURCES.md"
build_notes:
  - "one paused timeline per frame; no remote assets; seeded noise only (mulberry32)"
  - "frame.md (biennale-yellow) supplies the PALETTE ONLY — ignore its typography and its editorial-calm prose"
  - "ALL text in Pretendard via local @font-face (assets/fonts/pretendard/*.woff2); never let Hangul fall back to a system font"
  - "look = references/ref-01..10: grunge kinetic poster (A) + traditional palace (B); grunge texture mask on display type, halftone dot ground, grain, RGB fringe on type and on B&W character art"
  - "sun #F1EE2E stands in for the reference yellow; ink #1B2566 navy is the dark (the palette has no black); ember #E26B4A is the red; haze #F0DA7C is the gold; paper #E9E5DB is light type on dark"
  - "one accent per section: intro haze, A sections ink on sun, 나 ember, finale haze"
  - "hits are 0ms sets on real onsets; syncopated accents (13.421, 15.116, 17.252, 33.948) are real hits, not grid errors"
  - "rolls[]: the analyzer tagged the whole dense syncopated percussion as one sustained fill (5.619–39.822), so every boundary sits inside it; boundaries follow phrase edges, downbeats, and key_moments instead"
  - "horizontal motion runs left → right, the way a Hangul horizontal stroke is written"
  - "character art looks (B&W, RGB fringe, grain) go through hyperframes media-treatment on the <img> — no CSS filters"
  - "characters: AI-regenerated full-figure cutouts (Codex image_gen) at assets/characters/{HL-pair,HL-pair-2,BL-pair}.png; M-group stays the official art cutout; web cutouts kept as fallback in assets/characters/web/"
  - "props: assets/props/palace.png (black engraving line art → use as a CSS mask filled with paper #E9E5DB), knot.png, coin.png, brush-1.png / brush-2.png (alpha masks filled with the section colour)"
  - "code-native, not images: 천지인 strokes, the ㅡ/ㅣ bars, the ㅡ of 극 stretching into the bar, the gold dot — SVG/DOM so they scale and transition cleanly"
  - "TEXT LEGIBILITY (user rule): characters never cover more than ~15% of any headline glyph, never sit on a glyph's key stroke, and never cover copy lines. When a figure overlaps big type, the figure goes BEHIND the type (type on top) and shows through the gaps. In '역시' the '시' must stay fully readable at every moment of the move."
avoid: ["centered title on a gradient", "everything fading in", "corner labels, frame borders, watermark", "glow on UI chrome", "generic particle bursts", "slideshow — every beat a fresh card", "screensaver motion that says nothing", "the preset's editorial-calm serif look", "tiny unreadable hero text", "work titles on screen"]
---

## Decisions

- **Message**: 한글날엔 역시 사극 — 레진 사극 한마당에서 가·나·다 혜택을 누린다.
- **Audience and arc**: 레진 사극 독자(BL·HL·남성향). 어둠 속 한글의 기원(천지인) → 노랑 키네틱으로 폭발 → 주인공 라인업 → 가·나·다 혜택 → 사극 한마당 로고.
- **Format**: 1920×1080 (16:9), 40.0s, 내레이션 없음, 음악 있음(`assets/bgm.mp3`, 92 BPM, 최고조 34–38s), 자막 없음. 90초가 길어서 40초로 줄였으므로 장면 7개를 모두 유지하고 꽉 차게 보여준다.
- **Spine**: 천지인 — ·(하늘) 금빛 점이 엽전이 되고, ㅡ(땅)은 라인업을 가르는 막대가 되고, ㅣ(사람)는 엔딩으로 넘어가는 세로 와이프가 된다. 엽전은 '가'의 "1코인"과 엔딩 로고 옆 점으로 다시 돌아온다.
- **Brand**: `frame.md` = biennale-yellow (자동 파이프라인 프리셋 중 두 레퍼런스에 가장 가까움). sun `#F1EE2E` A의 노랑 바탕 · ink `#1B2566` 어두운 색(인트로·엔딩 바탕, 검정 대신) · ember `#E26B4A` 붉은 포인트(매듭, '나' 바탕) · haze `#F0DA7C` 금색(엽전, 제목 광택) · paper `#E9E5DB` 어두운 바탕 위 글자. 글꼴은 Pretendard 하나(사용자 확정; 프리셋 글꼴에는 한글이 없음).
- **Bans**: frontmatter `avoid` 목록 전체. 특히 모든 요소가 페이드인으로 등장하는 것, 가운데 정렬 제목 + 그라디언트 배경, 흔한 파티클 폭발.
- **Held frame**: Frame 4 g2 — 레진 로고가 38.568s에 들어온 뒤 오디오가 사라지는 39–40s까지 완전히 멈춘다.
- **Characters**: 레진 공식 대표 이미지에서 따낸 컷아웃 4장(짝 단위). HL-pair(하는 중전)는 '가', BL-pair(애별리고)는 '나', M-group(어둠이 스러지는 꽃)은 '다'에 쓰고, 세 장이 Frame 2 라인업에 나란히 선다. HL-pair-2(광안)는 '가'의 흐린 배경 그림. Frame 4 액자는 공식 표지 6장. 작품명은 화면에 넣지 않는다. 출처는 `assets/characters/SOURCES.md`.
- **Copy placeholders**: `[예시]`는 혜택·기간·행사명이다. 렌더 전에 실제 값으로 바꾼다.
- **Every 2–4 s**: 새 변화가 생기는 시각은 0.65 · 3.41 · 4.67 · 5.29 · 7.92 · 9.59 · 10.47 · 12.14 · 13.03 · 13.42 · 15.56 · 17.25 · 18.11 · 20.71 · 23.27 · 25.82 · 28.33 · 31.00 · 33.53 · 33.95 · 34.76 · 36.04 · 38.57. 가장 긴 간격은 2.8s이고, 마지막 멈춤(held frame)만 예외다.
- **Review sheet**: `storyboard.html` v3 (셀 id `frame-NN-gK`, 프레임 앵커 `frame-NN`).

## Changes from v2

- 사용자: "지금 이미지가 전부 정사각형 이잖아. 인물만 크롭하기 힘들면 codex imagen 스킬로 다시 생성해도 되는데" → 선택: "캐릭터도 AI로 다시 생성하고, js로 표현하기 힘든 이미지(한옥 등)는 비율을 계산해 이미지로, 코드 트랜지션에 유리하면 SVG로."
  → Codex image_gen으로 전신 인물 3장(HL-pair, HL-pair-2, BL-pair)과 소품 5장(궁궐 판화 선화, 매듭, 엽전, 붓터치 2종)을 만들어 모든 칸에 반영. 라인업은 네 작품 인물로 늘림. 프롬프트와 크기는 `assets/AI-PROMPTS.md`.

## Changes from v1

- 사용자: "너가 웹에 있는 데이터 중에서 레진/봄툰의 사극 이미지 중 해상도 높은거 골라서 배경 없애서 넣어줘."
  → 레진 공식 대표 이미지로 컷아웃 4장과 표지 6장을 넣음. 캐릭터 자리를 한 명 단위(HL-1…M-2)에서 짝 단위(HL-pair, BL-pair, M-group)로 바꿈(원화가 두 사람이 겹친 구도라 한 명씩 분리 불가).
- 사용자: "지금 판화 궁궐 같은건 저게 최종 디자인임?" → 아니요. 시트의 궁궐은 자리표시이고, 최종은 궁궐 사진에 `engraving` 효과(레퍼런스 8번 느낌), 사진이 없으면 SVG 선화.
- 4번 칸: '사'가 잘려 "ㅏ극"으로 읽히던 것을 '극'만 보이게 고치고 막대를 ㅡ 획 높이에 맞춤.

## Changes from v3 (build, 2026-09-28)

- '나'(03 g2) 글자·카피 색을 paper → ink로 변경 — 주홍 바탕 대비 2.54:1 → 약 4.3:1. 카피 크기 67 → 58px('예시' 표시가 패널에 가려지지 않게).
- 인트로(01) 궁궐 첫 화면 투명도 8% → 20%, 궁궐 그리기·매듭 등장을 0.65s → 0.1 / 0.2 / 0.3s로 앞당김(첫 2초 훅).
- 색번짐·광택·외곽선 복제 글자와 촘촘한 제목 줄에 `data-layout-allow-overlap` 표시(의도한 겹침).
- 제작 에이전트 판단: 엔딩 제목 "사극 한마당"에는 '예시' 표시 없음, 엔딩 엽전은 37.314s에 등장, "→"는 SVG 선으로 그림, 필름 노이즈는 타임라인 단계 움직임.
- 프레임 구간(span)은 그대로라 타이밍 표는 변경 없음. 이제 기준은 `compositions/frames/*.html`.

## Locked

- 사용자 승인 (2026-09-28): "좋아 좋은데, 실제로 캐릭터가 글자를 너무 가리진 않도록 모션 그래픽 잡을때 신경 써줘. 특히 "역시" 쪽에서 "시"를 많이 가릴거 같아서 혹시나 해서."
- 잠긴 것: 장면 10개의 배치·계층·카피(storyboard.html v3), 40초 음악 타이밍, 팔레트(biennale-yellow)와 Pretendard, 에셋(assets/characters, assets/props, assets/covers).
- 추가 규칙: 인물이 제목 글자를 가리지 않는다(build_notes의 TEXT LEGIBILITY). '역시' 칸은 인물을 글자 뒤로 보냄.

## Still open

- 레진 로고 파일 (`assets/logo/lezhin.svg` 또는 `.png`) — 대기.
- AI로 다시 만든 캐릭터 3장 — 공개 전 작가 동의·계약 범위 사내 확인.
- 남성향 자리: 레진 공식 분류에서 남성향 사극을 확인하지 못해 판타지 사극(어둠이 스러지는 꽃)으로 대체. 원하는 작품이 있으면 교체.
- 봄툰 작품: 공개 이미지가 600×330이라 원본 파일이 있어야 씀.
- `[예시]` 값: 혜택 3개, 기간, 행사명.

## Frame 1 — 01-intro

- src: compositions/frames/01-intro.html
- duration: 13.026s
- span_sec: [0.0, 13.026]
- pacing: beat_cut
- mood: [dark, cinematic]
- feel: near-silent opening (0–4 VOID) swelling into a warm, dense syncopated groove; energy climbs step by step toward the first HIGH hit at 13
- status: animated

### Groups

- **g1** — free_design
  - span_sec: [0.0, 5.294]
  - free_design: { dominant_system: "ink ground; a gold dot becomes a coin while an engraved palace draws in", primitives: ["mask-reveal", "spotlight-sweep", "negative-space-hold"], density_topology: "accumulate" }
  - anchors: [0.65, 3.413, 4.667, 5.294]
  - on screen: ink ground with halftone dots and grain alive from the first frame. At 0.65 a gold · (haze) drops to center and two ember knot ornaments swing in from the top corners (pendulum). An engraved palace roofline draws in behind with a mask reveal (engraving treatment on a palace image, or SVG line art until one is supplied). At 3.413 the dot flares; by 4.667 it has become a square-holed 엽전.
  - copy: none
- **g2** — free_design
  - span_sec: [5.294, 13.026]
  - free_design: { dominant_system: "천지인 strokes lock around the coin, then the title builds", primitives: ["directional-fill", "kinetic-letter-in", "chrome-sweep"], density_topology: "accumulate" }
  - anchors: [5.294, 7.918, 9.590, 10.472, 12.144]
  - on screen: on 5.294 a paper ㅡ bar cuts left → right through the coin; on 7.918 a ㅣ bar drops through it (· ㅡ ㅣ = 천지인). At 9.590 "1446 → 2026" lands (Bold, haze). At 10.472 "제580돌 한글날" lands large, left-aligned in the lower half (Black, paper) with a haze chrome sweep. The perc hit at 12.144 flares the coin as the pre-drop tension.
  - copy: ["1446 → 2026", "제580돌 한글날"]

## Frame 2 — 02-hook

- src: compositions/frames/02-hook.html
- duration: 12.795s
- span_sec: [13.026, 25.821]
- pacing: beat_cut
- mood: [hype, aggressive]
- feel: first HIGH hit at 13, syncopated snare accents about every 1.7–2 s (13.421, 15.557, 17.252) into the SURGE at 18.112, then a heavy groove easing to LOW by 23–25
- status: animated

### Groups

- **g1** — free_design
  - span_sec: [13.026, 18.158]
  - free_design: { dominant_system: "one giant word per hit on grunge yellow", primitives: ["system-replace", "braam-punch", "chromatic-split", "screen-shake"], density_topology: "replace" }
  - anchors: [13.026, 13.421, 15.557, 17.252]
  - on screen: 13.026 system-replace from the dark intro to a sun ground with halftone and grain. 13.421 "한글날엔" slams full width (Black, ink, grunge texture mask, RGB fringe). 15.557 "역시" replaces it; the HL pair (B&W, `HL-pair.png`) stands BEHIND the type and peeks through the gap between '역' and '시' (ref-02 feel, but the type stays on top — '시' is never covered). 17.252 "사극" slams, with the ㅡ of '극' primed to stretch.
  - copy: ["한글날엔", "역시", "사극"]
- **g2** — free_design
  - span_sec: [18.158, 20.712]
  - free_design: { dominant_system: "the ㅡ of 극 stretches into a bar that sweeps the lineup in", primitives: ["directional-fill", "mask-reveal", "screen-shake"], density_topology: "replace" }
  - anchors: [18.112, 19.064, 20.062]
  - on screen: on the SURGE (18.112) the ㅡ stroke of '극' stretches into a full-width ink bar while the view pans left → right (ref-03). The three casts — `HL-pair`, `BL-pair`, `M-group` — B&W with RGB fringe, stand along the bar, some in front of it and some behind. The 19.064 snare gives a short shake.
  - copy: none
- **g3** — free_design
  - span_sec: [20.712, 25.821]
  - free_design: { dominant_system: "held lineup; a two-line statement lands on downbeats", primitives: ["kinetic-letter-in", "chromatic-split", "negative-space-hold"], density_topology: "accumulate" }
  - anchors: [20.712, 23.266, 25.17]
  - on screen: the lineup keeps a slow drift. "스물여덟 자에 새긴" lands on the bar at 20.712 (Bold, sun on ink). "연모와 칼끝" lands at 23.266 (Black, ink, large, lower left). The LOW stretch 23–25 holds it; 25.17 primes the cut.
  - copy: ["스물여덟 자에 새긴", "연모와 칼끝"]

## Frame 3 — 03-ganada

- src: compositions/frames/03-ganada.html
- duration: 7.662s
- span_sec: [25.821, 33.483]
- pacing: beat_cut
- mood: [hype, playful]
- feel: three one-bar blocks: medium groove from 25.8, SURGE 28 (strong snare 28.328), DROP 30 then SURGE 31, DROP 32, LOW 33 with a riser at 33.53
- status: animated

### Groups

- **g1** — free_design
  - span_sec: [25.821, 28.352]
  - free_design: { dominant_system: "giant syllable 가 with two colour cutouts and an ink brush stroke", primitives: ["braam-punch", "mask-reveal", "content-swap"], density_topology: "accumulate" }
  - anchors: [25.821, 26.448, 27.562]
  - on screen: sun ground with `HL-pair-2` ghosted and enlarged behind at low opacity; an ink brush stroke wipes in on a diagonal (ref-04). "가" (Black, ink) slams at 25.821 on the left; the `HL-pair` colour cutout enters on the right. The intro coin returns beside "단 1코인" (callback to Frame 1).
  - copy: ["가", "가볍게, 단 1코인 [예시]"]
- **g2** — free_design
  - span_sec: [28.352, 30.906]
  - free_design: { dominant_system: "palette flip to ember with ink panels; characters break out of the panels", primitives: ["palette-flip", "braam-punch", "3d-card-flip"], density_topology: "replace" }
  - anchors: [28.328, 29.002, 29.652]
  - on screen: at 28.328 the palette flips to an ember ground with two ink panels (ref-09). The `BL-pair` breaks out over the top of the panels. "나" (Black, paper) is huge; the copy line sits below.
  - copy: ["나", "나눠 드려요, 100% 코인백 [예시]"]
- **g3** — free_design
  - span_sec: [30.906, 33.483]
  - free_design: { dominant_system: "inversion to ink ground with sun type; line-art plus colour characters", primitives: ["system-replace", "braam-punch", "chromatic-split"], density_topology: "replace" }
  - anchors: [30.906, 30.999, 31.509, 32.206]
  - on screen: at 30.999 the frame inverts to an ink ground; "다" in sun (ref-06). The `M-group` stands in colour on the right; ember and sun brush splashes. The copy line sits below.
  - copy: ["다", "다 풀었다, 특별편 OPEN [예시]"]

## Frame 4 — 04-finale

- src: compositions/frames/04-finale.html
- duration: 6.517s
- span_sec: [33.483, 40.0]
- pacing: beat_cut
- mood: [cinematic, hype]
- feel: riser at 33.53 into the biggest SURGE of the track (34–38 HIGH, energy 0.91), hard stop and DROP at 38, fading to silence 39–40
- status: animated

### Groups

- **g1** — free_design
  - span_sec: [33.483, 36.037]
  - free_design: { dominant_system: "ㅣ wipe to a rippled ink ground; title slam on the SURGE; framed portraits rise in perspective", primitives: ["system-replace", "braam-punch", "chromatic-split", "screen-shake"], density_topology: "replace" }
  - anchors: [33.530, 33.948, 34.760, 35.387]
  - on screen: on the 33.530 riser a ㅣ vertical wipe (천지인 callback) opens an ink ground with a subtle ripple and halftone texture (ref-10). "사극 한마당 [예시]" slams on 33.948 (Black, paper) under "2026 한글날" (SemiBold, haze). On 34.760 and 35.387 a row of six framed official covers (`assets/covers/*-tall.jpg`, ember frames) rises from the bottom in perspective.
  - copy: ["2026 한글날", "사극 한마당 [예시]"]
- **g2** — free_design
  - span_sec: [36.037, 40.0]
  - free_design: { dominant_system: "dates and logo land, then everything holds still", primitives: ["staggered-reveal", "freeze-hold", "negative-space-hold"], density_topology: "accumulate then hold" }
  - anchors: [36.037, 38.0, 38.568]
  - on screen: "10.09(금) – 10.11(일) [예시]" lands under the title on 36.037 (Bold, sun). The gold dot returns next to the logo. After the 38.0 hard stop, the 레진 logo lands on 38.568 and the whole frame freezes through the audio fade (39–40). No watermark.
  - copy: ["10.09(금) – 10.11(일) [예시]", "레진 로고"]
