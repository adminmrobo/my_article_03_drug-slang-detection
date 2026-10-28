# AI LAB Explainer — 01. SNS 은어와 이상탐지 (위장 거래 탐지)

**[한국어](#ko) · [English](#en) · [中文](#zh) · [日本語](#ja) · [Oʻzbekcha](#uz) · [Русский](#ru) · [Tiếng Việt](#vi)**

---

<a id="ko"></a>
## 한국어

SNS에서 일상 언어로 위장한 불법 마약 거래를 AI가 어떻게 잡아내는지 다루는 인터랙티브 해설 페이지입니다. 논문 「SNS 텍스트 기반 마약 의심 거래 탐지 알고리즘에 대한 연구」(안상선, 미래사회 16(1), 2025)의 통계를 기준으로, 전처리 파이프라인 → 원-핫 인코딩의 한계와 워드 임베딩 → 4대 은어 패턴 → 분류 모델 비교 → XAI(LIME·SHAP)까지 브라우저에서 직접 만져 보며 학습합니다. 그림·데이터·스크립트를 전부 한 파일에 담아(base64) 그대로 열기만 하면 동작합니다.

- **바로 보기**: `https://adminmrobo.github.io/my_article_03_drug-slang-detection/` — 루트 주소는 `index.html`이 한국어 본편으로 이동시킵니다. 본편 주소: `…/01_drug-slang-detection.html`
- **저자**: 안상선 ((주)M-Robo 대표)
- **라이선스**: CC BY-NC 4.0 (아래 「라이선스」 절)

### 언어

| 언어 | 파일 이름 | 바로 보기 |
|---|---|---|
| 한국어 (원본) | `01_drug-slang-detection.html` | 546 KB|
| English | `01_drug-slang-detection.en.html` | 545 KB|
| 中文 (简体) | `01_drug-slang-detection.zh.html` | 543 KB|
| 日本語 | `01_drug-slang-detection.ja.html` | 548 KB|
| Oʻzbekcha | `01_drug-slang-detection.uz.html` | 547 KB|
| Русский | `01_drug-slang-detection.ru.html` | 558 KB|
| Tiếng Việt | `01_drug-slang-detection.vi.html` | 550 KB|

- 전환 방법: ① 최상단 메뉴의 🌐 선택 상자 ② 오른쪽 아래 🌐 배너. 고른 언어는 브라우저(`localStorage`)에 기억됩니다.
- 한국어 페이지에서만 자동 전환합니다. 브라우저 언어가 지원 언어이고 그 번역 파일이 실제로 있을 때만 이동하며(이동 전 `HEAD` 확인), 없으면 한국어로 머뭅니다.
- `?lang=vi`처럼 주소 뒤에 붙이면 해당 언어로 열립니다. 번역판 주소로 들어온 경우 자동 전환하지 않습니다.
- 그림 속 글자(은어 예시, 워드클라우드 단어, 논문 인용)는 원문 연구 대상인 한국어 그대로이며, 모든 번역판에서 첫 등장에 뜻을 괄호로 덧붙였습니다.

### 페이지 구성

| 구성 | 내용 | 난이도 |
|---|---|---|
| ⓪ 전처리 파이프라인 | 수집→형태소 분석→정규화→DTM→원-핫→Word2Vec 6단계, 원-핫 vs 밀집 벡터 실습 | ★★ |
| ① 4대 은어 패턴 | 대유·비유·쌍관·묘사 변환 시뮬레이터, 퀴즈 1 | ★★ |
| ② 워드클라우드 & PCA | 논문 그림 6·7 재현, Word2Vec PCA 45도선 군집 실습, 퀴즈 2 | ★★★ |
| ③ 분류기 삼국지 | 로지스틱 99.89% vs KNN vs 의사결정나무 결정 경계와 지표 표 | ★★★ |
| ④ XAI | LIME 독감 진단 비유, 피처 기여도(부재의 증거), SHAP 전역 기여 | ★★★★ |
| 대결 (Duel) | 키워드 필터 62.0%(오탐 38%) vs 머신러닝 99.89% 판정 시뮬레이션 | — |
| 지식 색인 · 꾸러미 | 개념 검색과 관계 그래프, 온톨로지/서지 데이터 ZIP·BibTeX 내보내기 | — |

### 핵심 숫자와 출처

| 숫자 | 의미 | 출처 |
|---|---|---|
| 27,611명 (+50.1%) | 2023년 마약사범, 전년비 증가 | 논문 서술 [1] |
| +207% | 10대 마약사범 증가율(SNS 비대면 유통) | 논문 서술 [1] |
| 99.89% / 99.68% / 98.61% | 로지스틱 회귀 / KNN / 의사결정나무 정확도 | 논문 실험 표 |
| 정밀도 100% | 로지스틱 회귀의 정상 게시글 오탐 0 | 논문 실험 표 |
| 3,120건 | 실험 데이터셋(정상 : 마약의심 = 1:1) | 논문 실험 조건 |

**설명용 모형인 것**: 대결 바(62.0%·오탐 38%), PCA 산점 좌표, XAI 기여도 막대의 값은 논문 수치와 결론을 기준으로 화면용으로 구현한 것으로, 논문의 원본 계산값을 그대로 옮긴 것이 아닙니다. 지표 표의 수치는 논문 보고값입니다.

### 파일

```
01_drug-slang-detection.html        한국어 본편 (그림 base64 내장)
01_drug-slang-detection.en.html     영어판
01_drug-slang-detection.zh.html     중국어(간체)판
01_drug-slang-detection.ja.html     일본어판
01_drug-slang-detection.uz.html     우즈베크어판
01_drug-slang-detection.ru.html     러시아어판
01_drug-slang-detection.vi.html     베트남어판
index.html                          루트 주소 진입(한국어 본편으로 이동)
og_01.png                           공유 미리보기(og:image)
INDEX.md                            그림 은행 색인(키·판형·용처·검수 기록)
README.md
```

| 파일 | 크기 |
|---|---|
| `01_drug-slang-detection.html` | 546 KB|
| `01_drug-slang-detection.en.html` | 545 KB|
| `01_drug-slang-detection.zh.html` | 543 KB|
| `01_drug-slang-detection.ja.html` | 548 KB|
| `01_drug-slang-detection.uz.html` | 547 KB|
| `01_drug-slang-detection.ru.html` | 558 KB|
| `01_drug-slang-detection.vi.html` | 550 KB|
| `index.html` | 0.4 KB |
| `og_01.png` | 445 KB|

### 데이터와 이미지

- 그림은 16비트 RPG풍 픽셀아트 15종(배경 1·장면 3·컷 2·표정 8·썸네일/OG 2)을 `data-img` 키로 관리하고 base64로 파일 안에 내장했습니다. 키별 용처는 `INDEX.md`를 참고하세요.
- 캔버스 실습(파이프라인·은어 패턴·PCA·결정 경계·기여도·지식 그래프)은 페이지 안 JavaScript로 그립니다. 대화창의 캐릭터 얼굴은 공식 도트 표정 스프라이트([fruitfly-lab-expressions](https://github.com/adminmrobo/fruitfly-lab-expressions))를 씁니다.
- 워드클라우드 2장은 논문 그림 6·7의 재현이고, 은어 예시(작대기, 크리스탈, 떨, 샤키 등)는 연구 대상 데이터라 번역하지 않습니다.

### 용어 표기

- **위장 거래**: 일상 상거래 문맥으로 위장한 마약 거래 게시물.
- **대유·비유·쌍관·묘사**: 논문이 분류한 4대 은어 패턴 명칭(페이지 전체에서 이 표기를 유지).
- **부재의 증거**: 정상 상거래 필수 단어가 없다는 것 자체가 탐지 근거가 되는 LIME·SHAP 발견.
- **설명용 모형**: 논문 수치를 기반으로 화면용으로 구현한 시뮬레이션 값.

### 라이선스

이 시리즈는 크리에이티브 커먼즈 저작자표시-비영리 4.0 국제 라이선스([CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.ko))로 제공됩니다.

출처 표기 예: 안상선 (2025). SNS 텍스트 기반 마약 의심 거래 탐지 알고리즘에 대한 연구: 패턴 및 맥락 분석을 중심으로. *미래사회*, 16(1), 172-191. DOI: 10.22987/jifso.2025.16.1.172

---

<a id="en"></a>
## English

**SNS Slang and Anomaly Detection — How Does AI See Through Disguised Deals?** An interactive explainer based on the paper *A Study on the Algorithm for Detecting Suspected Drug Transactions in SNS Text* (Ahn Sang-Sun, *Mirae Sahoe* 16(1), 2025): from the preprocessing pipeline, the limits of one-hot encoding and word embeddings, and the four slang patterns, to the three-classifier showdown (logistic regression, most accurate at 99.89%) and XAI (LIME·SHAP). All images, data and scripts are embedded (base64) in one self-contained HTML file — just open it.

- **View**: `https://adminmrobo.github.io/my_article_03_drug-slang-detection/01_drug-slang-detection.en.html`
- **Author**: Ahn Sang-Sun (CEO, M-Robo Co., Ltd.) · **License**: [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en)
- The Korean slang words inside the artwork (작대기, 크리스탈, 떨, 샤키…) are the research data itself and stay in Korean; each is glossed in parentheses at first appearance.
- The English version is machine-translated and **not yet proofread by a native speaker**.

---

<a id="zh"></a>
## 中文

**SNS 黑话与异常检测 — AI 如何识破伪装交易？** 基于论文《SNS 文本基础毒品可疑交易检测算法研究》(Ahn Sang-Sun，《未来社会》16(1)，2025) 的互动解说页：从预处理流水线、独热编码的局限与词向量、四大黑话模式，到三种分类模型对比（逻辑回归准确率最高，达 99.89%）与可解释 AI（LIME·SHAP）。全部图片、数据与脚本以 base64 内嵌于单一 HTML 文件，打开即可运行。

- **直接查看**： `https://adminmrobo.github.io/my_article_03_drug-slang-detection/01_drug-slang-detection.zh.html`
- **作者**： Ahn Sang-Sun（M-Robo 株式会社代表） · **许可证**： [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.zh-hans)
- 图中的韩国黑话词汇（작대기、크리스탈、떨、샤키 等）是研究数据，保留韩文，首次出现时以括号注明含义。
- 中文版为机器翻译，**尚未经母语者校对**。

---

<a id="ja"></a>
## 日本語

**SNS隠語と異常検知 — AIは偽装取引をどう見破るのか？** 論文 *SNSテキストに基づく薬物疑い取引検出アルゴリズムの研究*(アン・サンソン、*未来社会* 16(1)、2025)に基づくインタラクティブ解説ページです。前処理パイプライン、one-hot符号化の限界と単語ベクトル、4大隠語パターンから、3分類モデルの対決(ロジスティック回帰が99.89%で最高精度)、XAI(LIME・SHAP)まで、ブラウザ上で直接操作しながら学べます。画像・データ・スクリプトをすべて1つのHTMLファイルに(base64で)内蔵しており、開くだけで動作します。

- **直接見る**: `https://adminmrobo.github.io/my_article_03_drug-slang-detection/01_drug-slang-detection.ja.html`
- **著者**: アン・サンソン(株式会社M-Robo代表) · **ライセンス**: [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.ja)
- 画像内の韓国語スラング(작대기、크리스탈、떨、샤키 など)は研究データのため韓国語のままとし、初出時に括弧で意味を添えています。
- 日本語版は機械翻訳で、**母語話者の校正はまだ行われていません**。

---

<a id="uz"></a>
## Oʻzbekcha

**Ijtimoiy tarmoq jargoni va anomaliyani aniqlash — AI yashirin bitimlarni qanday fosh qiladi?** *SNS matni asosida giyohvandlik shubhali bitimlarni aniqlash algoritmi tadqiqoti* (Ahn Sang-Sun, *Mirae Sahoe* 16(1), 2025) maqolasiga asoslangan interaktiv tushuntirish sahifasi: oldindan qayta ishlash bosqichi, one-hot kodlashning cheklovlari va soʻz vektorlari, toʻrtta jargon naqshi, uch tasniflagich musobaqasi (eng aniq — logistik regressiya, 99,89%) va tushuntiriladigan AI (LIME·SHAP). Barcha rasmlar, maʼlumot va skriptlar bitta HTML faylga (base64) joylashtirilgan — faqat ochish yetarli.

- **Toʻgʻridan-toʻgʻri koʻrish**: `https://adminmrobo.github.io/my_article_03_drug-slang-detection/01_drug-slang-detection.uz.html`
- **Muallif**: Ahn Sang-Sun (M-Robo kompaniyasi rahbari) · **Litsenziya**: [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en)
- Rasmlardagi koreys jargon soʻzlari (작대기, 크리스탈, 떨, 샤키…) tadqiqot maʼlumoti boʻlgani uchun koreyscha qoladi, birinchi uchrashda qavs ichida izohlanadi.
- Oʻzbekcha nusxa mashina tarjimasi boʻlib, **hali ona tili mutaxassisi tomonidan tahrirlanmagan**.

---

<a id="ru"></a>
## Русский

**Сленг в соцсетях и обнаружение аномалий — как ИИ распознаёт замаскированные сделки?** Интерактивный разбор по статье *Исследование алгоритма обнаружения подозрительных наркосделок в текстах SNS* (Ан Сансон, *Mirae Sahoe* 16(1), 2025): от конвейера предобработки, ограничений one-hot кодирования и векторных представлений слов и четырёх шаблонов сленга — до состязания трёх классификаторов (лучший — логистическая регрессия, точность 99,89%) и объяснимого ИИ (LIME·SHAP). Все изображения, данные и скрипты встроены (base64) в один HTML-файл — достаточно открыть его.

- **Смотреть**: `https://adminmrobo.github.io/my_article_03_drug-slang-detection/01_drug-slang-detection.ru.html`
- **Автор**: Ан Сансон (генеральный директор M-Robo Co., Ltd.) · **Лицензия**: [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.ru)
- Корейские слова-сленг на картинках (작대기, 크리스탈, 떨, 샤키…) — данные исследования, поэтому оставлены по-корейски с пояснением в скобках при первом появлении.
- Русская версия переведена автоматически и **пока не вычитана носителем языка**.

---

<a id="vi"></a>
## Tiếng Việt

**Tiếng lóng trên mạng xã hội và phát hiện bất thường — AI nhìn thấu giao dịch ngụy trang như thế nào?** Trang giải thích tương tác dựa trên bài báo *Nghiên cứu thuật toán phát hiện giao dịch nghi ngờ ma túy dựa trên văn bản SNS* (Ahn Sang-Sun, *Mirae Sahoe* 16(1), 2025): từ quy trình tiền xử lý, giới hạn của one-hot và word embedding, 4 mẫu tiếng lóng, so sánh ba mô hình phân loại (hồi quy logistic 99.89% chính xác nhất) đến XAI (LIME·SHAP). Toàn bộ hình ảnh, dữ liệu và mã nhúng trong một tệp HTML duy nhất.

- **Xem trực tiếp**: `https://adminmrobo.github.io/my_article_03_drug-slang-detection/01_drug-slang-detection.vi.html`
- **Tác giả**: Ahn Sang-Sun (Giám đốc điều hành, M-Robo Co., Ltd.) · **Giấy phép**: [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.vi)
- Các từ tiếng lóng Hàn Quốc trong hình (작대기, 크리스탈, 떨, 샤키…) là dữ liệu nghiên cứu nên giữ nguyên tiếng Hàn, lần đầu xuất hiện sẽ có chú thích trong ngoặc.
- Phần tiếng Việt là bản dịch tự động và **chưa qua hiệu đính bởi người bản xứ**.
