# 캐릭터·표지 이미지 출처

- 수집일: 2026-09-28
- 출처: 레진코믹스 공식 작품 페이지의 대표 이미지(`og:image`, 공식 CDN `ccdn.lezhin.com`)만 사용. 로그인·성인 인증이 필요한 페이지는 쓰지 않음(야화첩, 칼과 꽃 제외).
- 원본 크기 그대로 사용: 가로형 1200×600, 세로형 600×800. CDN의 `?width=` 확대본은 늘린 이미지라 쓰지 않음.
- 배경 제거: rembg `isnet-anime` 모델(웹툰·애니 그림 전용). HyperFrames 기본 `remove-background`(u2net_human_seg)는 그림에서 실패함.
- 작가 원화를 홍보에 쓰는 것은 사내 권리 확인 사항(BRIEF.md Notes). 일부 표지는 노출이 있어(예: 하는 중전) 홍보 적합성은 사용자가 판단.
- 장르·태그는 각 작품 페이지의 공식 데이터(`genres`, `tags`) 그대로.

> 2026-09-28 갱신: 영상에 쓰는 HL-pair, HL-pair-2, BL-pair는 AI로 다시 만든 전신 이미지다(`assets/AI-PROMPTS.md`). 아래 웹 원화 컷아웃 중 HL·BL 3장은 `assets/characters/web/`에 예비로 옮겼고, M-group.png만 그대로 쓴다.

## 웹 원화 컷아웃 (HL·BL 3장은 assets/characters/web/, M-group은 assets/characters/)

| 파일 | 작품 | 공식 장르 · 태그 | 작품 페이지 | 이미지 원본 | 원본 → 결과 |
|---|---|---|---|---|---|
| HL-pair.png | 하는 중전 [개정판] (초야/산홍) | romance · 레진절_다다익선, 동양풍, 다각관계, 신분차이, 순수녀, 로맨스 | https://www.lezhin.com/ko/comic/ha_is_the_queen_15 | https://ccdn.lezhin.com/v2/comics/7011732964492487/images/wide.jpg | 1200×600 → 1187×600 |
| HL-pair-2.png | 광안 [개정판] (육미화/소라/라혜) | romance · 레진절_다다익선, 조선, 동양풍, 궁정물, 시대극, 로맨스 | https://www.lezhin.com/ko/comic/madeye_15 | https://ccdn.lezhin.com/v2/comics/6405062063357952/images/tall.jpg | 600×800 → 600×748 |
| BL-pair.png | 애별리고 [개정판] (레드피치스튜디오/설해송) | bl · 오메가버스, 피폐물, 집착공, 미인수, 동양풍, BL 외 | https://www.lezhin.com/ko/comic/agony_of_separation_all | https://ccdn.lezhin.com/v2/comics/7011735531003791/images/wide.jpg | 1200×600 → 1200×600 |
| M-group.png | 어둠이 스러지는 꽃 (므앵갱) | fantasy · 레진절_금이한냥, 동양풍, 시대극, 판타지 | https://www.lezhin.com/ko/comic/audum_kkot | https://ccdn.lezhin.com/v2/comics/9/images/tall.jpg | 600×800 → 496×671 |

M-group은 "남성향" 자리의 대체 후보. 레진 공식 분류는 판타지 사극이고 남성향 표시는 없음.

## 엔딩 액자용 공식 표지 (assets/covers/, 배경 제거 없이 원본)

| 파일 | 작품 | 공식 장르 · 태그 | 작품 페이지 | 이미지 원본 |
|---|---|---|---|---|
| hajungjeon-tall.jpg | 하는 중전 [개정판] | romance | https://www.lezhin.com/ko/comic/ha_is_the_queen_15 | https://ccdn.lezhin.com/v2/comics/7011732964492487/images/tall.jpg |
| madeye-tall.jpg | 광안 [개정판] | romance · 조선, 시대극 | https://www.lezhin.com/ko/comic/madeye_15 | https://ccdn.lezhin.com/v2/comics/6405062063357952/images/tall.jpg |
| cloud-tall.jpg | 구름을 비추는 새벽 (버프찌/지연/5月 돼지) | romance · 순정녀, 후회남, 조선, 시대극, 로맨스 | https://www.lezhin.com/ko/comic/cloud_lit_dawn | https://ccdn.lezhin.com/v2/comics/6288849046405120/images/tall.jpg |
| agony-tall.jpg | 애별리고 [개정판] | bl · 동양풍, BL | https://www.lezhin.com/ko/comic/agony_of_separation_all | https://ccdn.lezhin.com/v2/comics/7011735531003791/images/tall.jpg |
| yeoksal-tall.jpg | 역살 [개정판] (킨고/당밀) | bl · 혐관, 광공, 집착공, 미인수, 동양풍, BL | https://www.lezhin.com/ko/comic/yeoksal_15 | https://ccdn.lezhin.com/v2/comics/7011758600588694/images/tall.jpg |
| audum-tall.jpg | 어둠이 스러지는 꽃 | fantasy · 동양풍, 시대극, 판타지 | https://www.lezhin.com/ko/comic/audum_kkot | https://ccdn.lezhin.com/v2/comics/9/images/tall.jpg |

모든 표지 원본은 600×800.

## 검토했지만 뺀 것

- 야화첩, 칼과 꽃 — 작품 페이지가 로그인(성인 인증) 필요.
- 역살, 고란이 전, 밤을 여는 달 — 배경 제거 실패(꽃·배경이 인물과 섞임). 역살은 표지로만 사용.
- 반야가인 — 컷아웃은 가능하지만 아이 캐릭터와 저작권 문구가 함께 들어가 보류.
- 봄툰(마녀보감 등) — 공개 이미지가 600×330 한 장뿐이라 해상도 부족. 쓰려면 원본 파일 필요.
