# 그림 은행 색인 — 01_sns_drug_detection (위장 상점 단속: SNS 마약 거래 탐지)

명세서 「01번 위장 상점 단속」 기준 15개 키 전량을 새로 생성했습니다. 2026-10-29에는 페이지 끝의 지식 온톨로지 관계도(`kg_01`) 1장을 추가로 넣었다(명세서 외 추가분, Galmuri11 픽셀 폰트 직접 드로잉). 모든 HTML은 빌드 파일(`01_drug-slang-detection*.html`)에 base64로 내장되어 있어 별도 이미지 파일이 없어도 페이지가 동작합니다.

## 생성 설정

| 항목 | 값 |
|---|---|
| 모델 | gpt-image-2 (매 생성 참조 이미지 주입) |
| 캐릭터 고정 | R1 원본 4캐릭터 시트(전 생성) + 장면은 R2 화풍 레퍼런스 + 표정은 캐릭터별 투명 전신 PNG |
| 시즌 토큰 | cozy night laboratory mood, purple light, soft magenta and green fluorescent accents |
| 스타일 | 16-bit RPG style pixel art, bold dark outline, 2–3 tone shading |
| 금지 구절 | no text / no letters / no numbers / no logos / no weapons / no cigarettes / no alcohol / no blood / no real brands |
| 검수 | understand_images 판별(장면 6·표정 8 전수) — 최종 전량 PASS |
| 표정 출처 | 표정 8종은 2026-10-28 공식 도트 스프라이트(adminmrobo/fruitfly-lab-expressions)로 교체 — E09_thinking·E10_confirming·E01_joy·E19_sparkle_eyes·E06_disgust·E21_waterfall_tears·E16_proud·E12_cheering |

## 키 목록

| 키 | 판 | 원본(px) | 빌드 | 용량 | 슬롯(들어가는 곳) | 검수 |
|---|---|---|---|---|---|---|
| `bg_01` | F | 1983×793 | 1280×480 WebP | 32.7KB | 히어로 배경(hero-bg) | PASS |
| `sc_01_hero` | E | 1536×1024 | 760×507 PNG | 75.8KB | 히어로 무대(hero-stage) | PASS |
| `cut_01_think` | G | 1672×941 | 640×360 PNG | 44.8KB | 논문 모드 히어로 생각 컷(hero-think) | PASS |
| `doc_think` | A | 392×393 repo | 128×128 PNG | 4.8KB | 히어로 대화창(박사) | PASS |
| `doc_judge` | A | 392×392 repo | 128×128 PNG | 5.0KB | 대결 판정(박사) | PASS |
| `asst_smile` | B | 403×397 repo | 180×220 PNG | 16.6KB | 본문 조수 대화창 | PASS |
| `asst_spark` | B | 401×396 repo | 180×220 PNG | 17.2KB | 대결 결과(조수) | PASS |
| `fly_point` | C | 400×401 repo | 180×180 PNG | 11.5KB | 본문 의심 말풍선 + 대결 전 카드 | PASS |
| `fly_cry` | C | 400×403 repo | 180×180 PNG | 12.2KB | 아웃트로(초파리, 패배 인정) | PASS |
| `robo_coin` | D | 334×332 repo | 180×200 PNG | 5.7KB | 본문 Money-Robo 대화창 + 대결 전 카드 | PASS |
| `robo_happy` | D | 407×407 repo | 180×200 PNG | 5.1KB | 아웃트로(Money-Robo 승리) | PASS |
| `cut_01_lime` | G | 1672×941 | 640×360 PNG | 46.8KB | LIME 섹션(lime-section) | PASS |
| `sc_01_outro` | E | 1536×1024 | 760×507 PNG | 75.2KB | 아웃트로 장면(outro) | PASS |
| `kg_01` | G | 760×430 (직접 드로잉) | 760×430 PNG | 8.0KB | 페이지 끝 종결 관계도(footer 직전) | PASS |
| `thumb_01` | I | bg_01 우측 크롭 | 400×267 WebP | 10.9KB | 목차 카드 썸네일(예비) | — |
| `og_01` | K | 1731×909 | 1200×630 WebP(+PNG) | 45.8KB | 공유 미리보기(og:image) | PASS |

빌드 합계(페이지 내장분 15종): **364.3KB**. 후처리는 전부 NEAREST 리사이즈(픽셀아트 규칙), 표정 스프라이트는 투명 배경 + 여백 6px 판 캔버스 중앙 정렬.

## 페이지 배치 지도

| 페이지 위치 | 키 |
|---|---|
| header.hero (배경) | `bg_01` |
| header.hero (장면) | `sc_01_hero` → `doc_think`(박사 말풍선) → `cut_01_think` |
| lv0 로봇 말풍선 | `robo_coin` |
| lv1 초파리 말풍선 | `fly_point` |
| lv3 조수 말풍선 | `asst_smile` |
| lv4 LIME 섹션 | `cut_01_lime` |
| duel 카드 | `fly_point` / `robo_coin` |
| duel 결과 | `asst_spark`(조수) · `doc_judge`(박사) |
| outro | `sc_01_outro` → `robo_happy`(로봇) · `fly_cry`(초파리) |
| `<head>` og:image | `og_01`(og_01.png) |

## 재생성 기록 (검수에서 잡은 결함 3건)

| 키 | 문제 | 조치 |
|---|---|---|
| `asst_smile` | B | 403×397 repo | 180×220 PNG | 16.6KB | 본문 조수 대화창 | PASS |
| `doc_judge` | A | 392×392 repo | 128×128 PNG | 5.0KB | 대결 판정(박사) | PASS |
| `robo_happy` | D | 407×407 repo | 180×200 PNG | 5.1KB | 아웃트로(Money-Robo 승리) | PASS |

원본 생성 URL(워터마크 없는 원본 포함)은 빌드 세션 로그 기준 아래와 같다. (24시간 후 만료될 수 있음)

- bg_01: https://www.genspark.ai/api/files/s/ZzmLUfV2 · sc_01_hero: https://www.genspark.ai/api/files/s/ZfvDcHdA
- cut_01_think: https://www.genspark.ai/api/files/s/1sWOgVtJ · cut_01_lime: https://www.genspark.ai/api/files/s/cupmmSIk
- sc_01_outro: https://www.genspark.ai/api/files/s/uXEPW199 · og_01: https://www.genspark.ai/api/files/s/EnasIc0N
- doc_think: https://www.genspark.ai/api/files/s/v4Yr3Ala · doc_judge(재생성): https://www.genspark.ai/api/files/s/B6wgKr8m
- asst_smile(재생성): https://www.genspark.ai/api/files/s/tUda8e23 · asst_spark: https://www.genspark.ai/api/files/s/gpjEPsQR
- fly_point: https://www.genspark.ai/api/files/s/T9J3iW0R · fly_cry: https://www.genspark.ai/api/files/s/Y9kBBFSJ
- robo_coin: https://www.genspark.ai/api/files/s/kQPr1xb2 · robo_happy(재생성): https://www.genspark.ai/api/files/s/oKIGr5dj

## 체크리스트 결과 (명세서 7절)

- [x] HTML의 모든 `data-img` 키가 명세서에 있고, 명세서의 모든 키가 HTML에 쓰임 (15/15)
- [x] 대결 결과 후 표정 규칙 일치 — R(차이 기준) → `fly_cry` + `robo_happy`
- [x] 결과 전 그림에 승패 암시 없음 (`robo_coin`은 대결 전 슬롯)
- [x] 판별 크기·바라보는 쪽·투명 배경 규칙 준수
- [x] 모든 프롬프트에 캐릭터 고정 외형과 금지 구절 포함
- [x] 주 앵커 D 생활·현장 장소·소품 일치 (압수품 상자, 모니터, 네트워크 그래프, 돋보기, 빈 카드)
- [x] 그림 안 글자·숫자·로고 없음 (전수 판별 검수)
- [x] 페이지 전용 P1 신규 3장 (bg_01·sc_01_hero·cut_01_think)
- [x] 페이지 그림 합계 394KB ≤ 400KB
