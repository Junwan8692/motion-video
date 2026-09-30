---
compositionId: hangul-day-18s
duration_s: 18.47
canvas: { w: 1920, h: 1080, fps: 30 }
mode: collaborative
message: "제580돌 한글날, 레진 사극 한마당 — 사극 BL·HL·남성향 주인공과 가·나·다 혜택을 18초에 속도감 있게 알린다"
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
  - "hits are 0ms sets on real onsets and beats of the 185 BPM grid (strong onsets 11.471, 14.141, 15.418, 16.533)"
  - "SHORT VERSION PACE (user: 짧고 타이트하게, 속도감): something new about every 1 s; eases ≤ 0.35 s; hard cuts on beats; no slow drifts or long holds except the two musical breaks (7.987–10.24 copy hold, 12.0–12.794 triptych hold) and the final freeze 17.0–18.47"
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
- **Format**: 1920×1080 (16:9), 18.47s, 내레이션 없음, 음악 `assets/bgm.mp3` = 원곡 2:15.9–2:34.4(185 BPM, 강타 3.18 · 7.0 · 10.24 · 13.0, 정적 12.0–12.8, 17.0 이후 끝). 사용자 요청으로 20초 이하·속도감 버전. 장면 7개 유지. 40초 버전은 `versions/40s/`.
- **Spine**: 천지인 — ·(하늘) 금빛 점이 엽전이 되고, ㅡ(땅)은 라인업을 가르는 막대가 되고, ㅣ(사람)는 엔딩으로 넘어가는 세로 와이프가 된다. 엽전은 '가'의 "1코인"과 엔딩 로고 옆 점으로 다시 돌아온다.
- **Brand**: `frame.md` = biennale-yellow (자동 파이프라인 프리셋 중 두 레퍼런스에 가장 가까움). sun `#F1EE2E` A의 노랑 바탕 · ink `#1B2566` 어두운 색(인트로·엔딩 바탕, 검정 대신) · ember `#E26B4A` 붉은 포인트(매듭, '나' 바탕) · haze `#F0DA7C` 금색(엽전, 제목 광택) · paper `#E9E5DB` 어두운 바탕 위 글자. 글꼴은 Pretendard 하나(사용자 확정; 프리셋 글꼴에는 한글이 없음).
- **Bans**: frontmatter `avoid` 목록 전체. 특히 모든 요소가 페이드인으로 등장하는 것, 가운데 정렬 제목 + 그라디언트 배경, 흔한 파티클 폭발.
- **Held frame**: Frame 4 g2 — 16.533s 로고 착지, 17.0 마지막 타격 뒤 18.47까지 완전히 멈춘다.
- **Characters**: 레진 공식 대표 이미지에서 따낸 컷아웃 4장(짝 단위). HL-pair(하는 중전)는 '가', BL-pair(애별리고)는 '나', M-group(어둠이 스러지는 꽃)은 '다'에 쓰고, 세 장이 Frame 2 라인업에 나란히 선다. HL-pair-2(광안)는 '가'의 흐린 배경 그림. Frame 4 액자는 공식 표지 6장. 작품명은 화면에 넣지 않는다. 출처는 `assets/characters/SOURCES.md`.
- **Copy placeholders**: `[예시]`는 혜택·기간·행사명이다. 렌더 전에 실제 값으로 바꾼다.
- **Every ~1 s**: 새 변화 시각 0.0 · 0.63 · 1.28 · 1.90 · 2.53 · 3.18 · 4.16 · 5.11 · 6.39 · 7.04 · 7.99 · 8.94 · 10.24 · 10.87 · 11.47 · 12.79 · 13.10 · 14.14 · 14.70 · 15.42 · 16.53 · 17.0(정지).
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

## Short version (2026-09-29)

- 사용자: "확실히 좀 느릿~느릿... 하네 ㅋㅋㅋ 지금 이걸 좀더 짧고 타이트 하게 20초 언더로 속도감 있는 버전으로 수정 가능한지?" → "where is 18s ver HTML?"
- 음악을 원곡의 가장 센 마지막 구간(2:15.9–2:34.4, 18.47s)으로 교체하고, 같은 장면 7개를 새 박에 맞춰 압축. 가·나·다는 한 장면씩 교체하면 문구를 읽을 수 없어 세 칸 누적(레퍼런스 9번)으로 바꿈. 카피는 핵심어로 줄임(단 1코인 / 100% 코인백 / 특별편 OPEN).
- 40초 버전 보관: `versions/40s/`.

## Frame 1 — 01-intro

- src: compositions/frames/01-intro.html
- duration: 3.181s
- span_sec: [0.0, 3.181]
- pacing: beat_cut
- mood: [dark, cinematic]
- feel: near-silent first second rising into a low build (1–3 s); the first real hit lands at 3.181
- status: animated

### Groups

- **g1** — free_design
  - span_sec: [0.0, 1.277]
  - free_design: { dominant_system: "ink ground; the palace draws in fast, knots swing in, the gold dot becomes the coin", primitives: ["mask-reveal", "negative-space-hold"], density_topology: "accumulate" }
  - anchors: [0.0, 0.325, 0.627, 0.952]
  - on screen: the engraved palace is visible from frame 1 and wipes in left → right over 0.0–0.9; both knots swing in from the top corners by 0.325; the gold dot drops and becomes the coin on 0.627; a coin pulse on 0.952.
  - copy: none
- **g2** — free_design
  - span_sec: [1.277, 3.181]
  - free_design: { dominant_system: "천지인 bars cut through the coin, then the title slams", primitives: ["directional-fill", "braam-punch", "chrome-sweep"], density_topology: "accumulate" }
  - anchors: [1.277, 1.904, 2.531, 2.856]
  - on screen: 1.277 a paper ㅡ bar cuts left → right through the coin; 1.904 the ㅣ bar drops; 2.531 "1446 → 2026" and "제580돌 한글날" slam in together, lower left; 2.856 haze sheen sweep; hold to the cut.
  - copy: ["1446 → 2026", "제580돌 한글날"]

## Frame 2 — 02-hook

- src: compositions/frames/02-hook.html
- duration: 7.059s
- span_sec: [3.181, 10.24]
- pacing: beat_cut
- mood: [hype, aggressive]
- feel: first hit at 3.181 into a dense 185 BPM groove, SURGE into HIGH at 7.0, a low breath 8–10 before the next surge at 10.24
- status: animated

### Groups

- **g1** — free_design
  - span_sec: [3.181, 6.385]
  - free_design: { dominant_system: "one giant word per hit on grunge yellow", primitives: ["system-replace", "braam-punch", "chromatic-split", "screen-shake"], density_topology: "replace" }
  - anchors: [3.181, 4.156, 5.108, 5.735]
  - on screen: 3.181 system-replace to the sun ground + "한글날엔" slams; 4.156 "역시" — the HL pair (B&W) stands BEHIND the type with both faces in the gap between '역' and '시' ('시' readable at every moment); 5.108 "사극" slams; 5.735 the ㅡ of '극' primes.
  - copy: ["한글날엔", "역시", "사극"]
- **g2** — free_design
  - span_sec: [6.385, 7.987]
  - free_design: { dominant_system: "the ㅡ of 극 stretches into a bar that sweeps the lineup in", primitives: ["directional-fill", "mask-reveal", "screen-shake"], density_topology: "replace" }
  - anchors: [6.385, 7.035, 7.662]
  - on screen: 6.385 the ㅡ stretches into the full-width ink bar while the view pans left → right; HL-pair and M-group behind the bar, BL-pair in front (all B&W); 7.035 SURGE shake; 7.662 accent.
  - copy: none
- **g3** — free_design
  - span_sec: [7.987, 10.24]
  - free_design: { dominant_system: "lineup holds on the bar; the two-line statement lands in the breath", primitives: ["kinetic-letter-in", "chromatic-split", "negative-space-hold"], density_topology: "accumulate" }
  - anchors: [7.987, 8.939, 9.915]
  - on screen: 7.987 "스물여덟 자에 새긴" lands on the bar (four casts standing on it); 8.939 "연모와 칼끝" slams large, lower left; the breath holds it readable; 9.915 primes the cut.
  - copy: ["스물여덟 자에 새긴", "연모와 칼끝"]

## Frame 3 — 03-ganada

- src: compositions/frames/03-ganada.html
- duration: 2.554s
- span_sec: [10.24, 12.794]
- pacing: beat_cut
- mood: [hype, playful]
- feel: surge at 10.24 with hits on 10.867 and 11.471 (strong snare), then a full stop — silence 12.0–12.794
- status: animated

### Groups

- **g1** — free_design
  - span_sec: [10.24, 12.794]
  - free_design: { dominant_system: "three-panel accumulate: 가 · 나 · 다 columns fill left → right, one per hit (ref-09 multi-panel)", primitives: ["system-replace", "braam-punch", "staggered-reveal", "freeze-hold"], density_topology: "accumulate then hold" }
  - anchors: [10.24, 10.867, 11.471, 12.0]
  - on screen: three vertical panels across the frame. 10.24 the left panel (sun) slams in with "가" (ink) + the HL pair (colour) + the coin + "단 1코인"; 10.867 the middle panel (ember) with "나" (ink) + the BL pair + "100% 코인백"; 11.471 the right panel (ink) with "다" (sun) + the M-group + "특별편 OPEN" (paper). From 12.0 (silence) everything freezes so all three benefits read together. Figures never cover the syllables or the copy.
  - copy: ["가", "단 1코인 [예시]", "나", "100% 코인백 [예시]", "다", "특별편 OPEN [예시]"]

## Frame 4 — 04-finale

- src: compositions/frames/04-finale.html
- duration: 5.676s
- span_sec: [12.794, 18.47]
- pacing: beat_cut
- mood: [cinematic, hype]
- feel: the silence breaks at 12.794 / 13.0 into the loudest climax (13–17), hard stop at 17.0, silence to the end
- status: animated

### Groups

- **g1** — free_design
  - span_sec: [12.794, 15.325]
  - free_design: { dominant_system: "ㅣ wipe to a rippled ink ground; title slam on the SURGE; framed covers rise in perspective", primitives: ["system-replace", "braam-punch", "chromatic-split", "screen-shake"], density_topology: "replace" }
  - anchors: [12.794, 13.096, 14.141, 14.698]
  - on screen: 12.794 the ㅣ wipe opens the ink ripple ground; 13.096 "사극 한마당" slams under "2026 한글날"; 14.141 covers 1–3 rise (strong kick); 14.698 covers 4–6.
  - copy: ["2026 한글날", "사극 한마당 [예시]"]
- **g2** — free_design
  - span_sec: [15.325, 18.47]
  - free_design: { dominant_system: "date and logo land on the last hits, then everything holds still", primitives: ["staggered-reveal", "freeze-hold", "negative-space-hold"], density_topology: "accumulate then hold" }
  - anchors: [15.418, 16.533, 17.0]
  - on screen: 15.418 "10.09(금) – 10.11(일)" lands (strong perc); 16.533 the logo placeholder and the coin land (strong snare); 17.0 hard stop — the frame freezes to 18.47. No watermark.
  - copy: ["10.09(금) – 10.11(일) [예시]", "레진 로고"]
