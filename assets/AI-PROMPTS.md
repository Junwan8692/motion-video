# AI 생성 이미지 프롬프트 (Codex built-in image_gen, 2026-09-28)

사용자 결정으로 캐릭터를 AI로 다시 만들었다(BRIEF.md Notes). 공개 전 작가 동의·계약 범위 확인 필요.
참고 이미지: `references/art/` (레진 공식 대표 이미지). 생성 원본은 `~/.codex/generated_images/01a0e706-…/`에 있고, 프로젝트의 인물 3장은 투명 여백을 1% 남기고 잘라 냈다.

| 파일 | 크기(생성 → 프로젝트) | 시도 | 참고 이미지 |
|---|---|---|---|
| assets/characters/HL-pair.png | 1536×1024 → 721×904 | 2 | references/art/hajungjeon-wide.jpg |
| assets/characters/HL-pair-2.png | 1024×1536 → 693×1294 | 2 | references/art/madeye-tall.jpg |
| assets/characters/BL-pair.png | 1536×1024 → 817×901 | 2 | references/art/agony-wide.jpg, agony-tall.jpg |
| assets/props/palace.png | 1536×1024 | 2 | — |
| assets/props/knot.png | 1024×1536 | 2 | — |
| assets/props/coin.png | 1254×1254 → 1024×1024 | 1차본 선택 | — |
| assets/props/brush-1.png | 1536×1024 | 1 | — |
| assets/props/brush-2.png | 1536×1024 | 1 | — |

- 엽전: Codex는 2차본(朝·平·通·寶, 실제 없는 조합)을 골랐지만, 실제 상평통보 글자(常·平·通·寶)가 나온 1차본으로 바꿈. 네 글자의 배치 순서는 실제 동전과 다름.
- `assets/props/tinted/`: 선화·붓터치의 알파는 그대로 두고 팔레트 색만 채운 버전(palace-paper, brush-1-ink/sun, brush-2-ember/ink).

## 프롬프트 원문

1. **HL pair:** "Create a new isolated character cutout using the supplied image strictly as the identity, costume palette, and Korean webtoon style reference. Output 1536x1024 PNG with real transparent alpha. The two full-length Joseon figures should occupy only the central 75% of the canvas height, so there is at least 8% wholly empty transparent space above the highest hair and below both shoes, and at least 8% at left and right. Side by side, standing close, three-quarter toward viewer: elegant narrow-eyed faintly smiling man with very long straight black hair past shoulders, fully closed ivory Joseon hanbok robe and a thin calligraphy brush; large dark-eyed woman with dark brown hair in a single long braid over her shoulder tied with pale pink ribbon, pale pink and white jeogori and chima. Keep the facial features and hair from the reference. Full-color Korean webtoon, clean line art, soft painterly shading. Entire hair, sleeves, hems and feet visible. Clean cutout edges only; absolutely no glow, ground shadow, cast shadow, scenery, floor, backdrop, text, letters, signature, watermark, logo, or border. Tasteful all-ages promo, fully clothed."

2. **HL pair 2:** "Second attempt at a 1024x1536 transparent PNG Korean webtoon cutout using supplied art only as reference for character identities and clothes. Make the people SMALLER: the entire two-person silhouette including crown prince's hat and both sets of shoes must fit between x=100..924 and y=160..1376, leaving broad clear transparent margins. Front court lady has round dark eyes, dark hair in a low bun with small butterfly ornament, light pink jeogori and red chima, hands shyly near face. Crown prince stands behind leaning over her shoulder, narrow eyes, royal blue robe and black winged ikseongwan hat with gold ornament. Full-length feet visible. Match the reference Korean manhwa line art and shading. No glow, halo, cast shadow, floor, backdrop, scenery, text, signature, watermark, logo or border. Fully clothed tasteful all-ages art."

3. **BL pair:** "Second attempt at an isolated 1536x1024 transparent PNG character cutout. Supplied two references establish the same two young men's identities, colors and Korean webtoon style. Make the figures SMALLER so the ENTIRE silhouette including hair, flowing robes, shoes and a thin red thread fits inside x=140..1396 and y=100..924, with clearly empty transparent bands on all four sides. Two full-length men face each other tenderly: delicate black-haired man in a fully closed pale grey-blue layered palace robe; taller very-long-white-silver-haired man in fully closed white and grey layered palace robes, gently touching the other's cheek, thin red thread tied at his finger. Melancholic, tasteful all-ages. Match reference faces and soft painterly manhwa line art. No bare shoulders, background, scenery, rain, glow, ground shadow, text, watermark, signature, logo or frame."

4. **Palace:** "Second attempt at a standalone transparent PNG palace engraving asset, 1536x1024. A symmetric straight-on front elevation of a Korean Joseon palace gate like Gwanghwamun, centered and about 90% of canvas width. Stone base with exactly three arched openings, two stacked roof tiers with upturned eaves and ridge figures. Render the architecture ONLY as fine pure BLACK copperplate etching lines and black cross-hatching on TRANSPARENT alpha. There must be NO white or grey fill, no paper, no opaque pixels inside open arches or empty spaces between roof details. The entire image is line art cut out from a transparent canvas, usable for CSS recoloring. No sky, floor, ground plane, people, letters, signs, labels, watermark, signature, logo or frame."

5. **Knot:** "Second attempt at a standalone 1024x1536 transparent PNG Korean maedeup norigae. ONE red silk cord enters at the exact top edge, leading to two or three traditional decorative red knots including a butterfly and chrysanthemum knot, followed by ONE long red silk tassel ending inside the canvas. Straight-on front view; finely detailed woven red threads; all knots and tassel completely inside with wide empty side margins. Crucial: precise HARD CUTOUT alpha around only the cord, knots and tassel; NO red halo or glow around it, no cast shadow, no colored haze, no backdrop of any kind. No hook, hand, scenery, text, watermark, logo, signature, or frame."

6. **Coin (1차본 사용):** 원래 요청 — "A Joseon sangpyeong tongbo coin seen flat-on: round, raised rim, square hole in the center that is fully transparent, four raised characters around the hole (exact characters not important), polished antique gold metal, soft studio lighting. Coin fills about 85% of the canvas."

7. **Brush stroke:** "Isolated alpha-mask art for a HyperFrames ink wipe. Exactly 1536x1024 transparent PNG. ONE long horizontal dry-brush stroke of PURE BLACK ink spanning approximately 95% of canvas width and only 20% of canvas height, centered vertically. Natural rough dry edges, bristle streaks and irregular feathering at the ends. All other pixels fully transparent. No second stroke, splatters, grey, color, paper, backdrop, shadow, glow, text, signature, watermark, logo or frame."

8. **Ink splash:** "Isolated alpha-mask art for a HyperFrames ink splash. Exactly 1536x1024 transparent PNG. A dynamic cluster of PURE BLACK ink splatters, droplets, and short energetic brush flicks spreading horizontally across the canvas. Intentional varied droplet sizes and crisp irregular edges. All other pixels fully transparent. No long continuous brush stroke, grey, color, paper, backdrop, shadow, glow, text, letters, signature, watermark, logo or frame."
