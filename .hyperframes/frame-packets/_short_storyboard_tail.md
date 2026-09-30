
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
- status: built

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
- status: built

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
- status: built

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
- status: built

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
