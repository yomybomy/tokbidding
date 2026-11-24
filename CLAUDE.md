# 톡톡 비딩 · 작업 메모

브리지 공부·게임 중에 비딩이 헷갈릴 때 바로 여는 빠른 참조 웹앱. 만든 사람: yoon (GitHub `yomybomy`).
이 파일은 새 PC나 새 세션에서 이어서 작업할 때 먼저 읽는 메모예요. 정한 내용이 바뀌면 여기도 고쳐 주세요.

## 파일
- `index.html` — 사이트 전체 (카드 데이터 `const C = [...]`, 검색·필터, SAYC/2/1 전환, 내 핸드로 찾기)
- `manifest.webmanifest`, `sw.js`, `icons/` — 웹앱(홈 화면 설치·오프라인)
- 사이트를 고친 뒤에는 `sw.js`의 `VERSION`(예: `tok-v1` → `tok-v2`)을 올려야 설치한 사람에게 새 버전이 반영돼요.
- 배포: GitHub Pages (`https://yomybomy.github.io/tokbidding/`). `main`에 push하면 반영.
- 예전 Claude 아티팩트 주소(https://claude.ai/artifact/5bsiv9uH7TZ5Dyt2xFGDHf)는 웹앱 이전의 버전이에요.

## 카드 데이터 형식
- 카드: `{ id, cat, t(1 자주 쓰임 · 2 알아두면 좋음 · 3 선택 심화), face, name, when, auc, title, rows, cols?, chk?, sys? }`
- 행: `"점수|장수·조건|비드|메모"`, `#`로 시작하면 구분 제목. `auc`의 `[[...]]`는 강조.
- `sys: { sayc: {...}, gf: {...} }` 은 시스템별로 바뀌는 부분만 덮어써요.

## 기준 (사용자 학습지가 정답)
- 점수·장수 기준은 Canva에서 제목이 **[윤윤]** 으로 시작하는 학습지를 따른다. 학습지끼리 다르면 사용자에게 물어서 정한다.
- 기본 시스템 SAYC, 2/1 GF 전환 제공.
- 1NT 오픈 15–17. 2NT 20–21. 2♣ 후 2NT 22–23, 3NT 오픈 24–25, 2♣ 후 3NT 26–27, 2♣ 후 4NT 28+.
- 2/1 GF **12+**, 1NT 포싱 6–11, 2/1 뒤 3장 리밋 10–11, 패스트 어라이벌 12–14.
- SAYC 1M–1NT 6–10, 마이너 뒤 1NT 6–10 / 2NT 11–12 초대 / 3NT 13–15.
- 15–17 밸런스 + 5장 메이저 → 1NT.
- 단순 레이즈 6–9 (support points), Bergen 7–9 / 10–12, Splinter 13–16, Drury 10+ support points.
- Weak Two 5–10, Preempt 4–9, Strong 2♣ 언밸런스 21+.
- 4SF = 게임 포싱(양 시스템). Reverse 뒤 응답자 자기 수트 반복 NF. Ingberman = 릴레이형(오프너 3♣), 약함 5–7.
- NMF는 약속했을 때만, 약속 없으면 실제 수트 NF. 2/1에서도 점프 시프트 기본은 Strong.
- Transfer Walsh: 3–4장은 1레벨 수락, 2♥ = 17–19 Superaccept. Landy 5–4 이상. Cappelletti 2NT = 두 마이너.
- Michaels · 언유주얼 2NT: 6–10 또는 17+, 11–16은 일반 오버콜로 시작.
- 1NT 오버콜 15–17, 2레벨 오버콜 10–16.
- 수비 쪽 (2026-11-24 결정, 경쟁 학습지 10개 비교):
  - 테이크아웃 X 12–17, 강한 X 18+
  - 오버콜 뒤 단순 레이즈 7–10, 어드밴서 2NT 12–14 / 3NT 15+, 어드밴서 점프 시프트 15+
  - 오버콜러 강도 8–12 / 13–14 / 15–16
  - 샌드위치: 패스 안 한 손 1NT 16–18, 패스한 손 1NT 두 수트 6–10
  - 밸런싱 1NT 12–15, 점프 2NT 18–19
  - BROMAD는 One-under, 더블 뒤 트랜스퍼 응답과 둘 중 하나만
  - Jordan 2NT 4장 이상, 서포트 더블은 2♠까지
  - 오버콜 뒤 응답자 새 수트는 포싱 기본(NFB는 선택 심화)
  - 위크 투·Preempt·레이즈 뒤 밸런싱 수비는 학습지가 없어 표준 숫자 + 약속 확인 표시
- 경쟁 학습지: 오버콜 통합 01 `DAHbN_J10sE` · 02 `DAHbNj5QYQs` · 03 `DAHad__Mmyo` · 수트 오버콜 뒤 비딩 `DAHWiD32e14` · Cue-bid 지지형 `DAHU3bt_Pe4` · 4차시 Overcaller·Advancer Rebid `DAHbtdTEotA` · Takeout Double·Responsive `DAHbJkd-Z00` · Redouble·상대 X 뒤 `DAHbr0ip9gw` · Negative·Reopening·Support `DAHbr68R0ps` · 상대 1NT 방어 `DAHawcz2QDQ`

## 용어·표현 원칙
- "경매"가 아니라 **"비딩"**.
- 공식 용어 기준. 자연스러운 한국어는 써도 되지만 번역체면 영어 그대로 (Preempt, Superaccept, Pass or Correct, Quantitative, Rule of 20 등).
- "슈트" 아니고 **"수트"**.
- **"자연"이라는 표현 금지** (자연 3NT, 자연 오버콜 등) → "실제 수트", "일반 오버콜"처럼.
- 특정 오프닝 비드는 "3NT 오픈", "2NT 오픈"처럼 **"오픈"** 선호.

## 디자인
- 스티커 스타일: 굵은 남색 테두리 + 딱 떨어지는 그림자, 주아(제목·비드) + 고운돋움(본문), 노란 형광펜, 점수표 줄무늬 배경.
- 항상 밝은 테마(다크 모드 없음). ♥♦ 빨강, 더블 카드도 일반 카드와 같은 색.
- 휴대폰: 카드 표는 줄마다 작은 카드(비드가 맨 위), 고정 메뉴는 검색 + 필터 버튼 + 탭.
- 사이트 이름 "톡톡 비딩"(임시, 바뀔 수 있음). 스티커 "yoon의 비딩 노트", 맨 아래 "made by yoon".

## 일하는 방식
- 고치기 전에 문제와 대안을 먼저 보여주고 함께 정한 뒤 수정한다.
- 선택지는 팝업 질문 창보다 글로 정리해서 묻는다.

## 참고한 [윤윤] 학습지 (Canva 디자인 id)
2026-11-23에 아래 학습지와 사이트를 비교해서 A그룹(분명한 차이)과 B그룹(학습지끼리 다른 것, 위 기준에 결정 반영)을 고쳤다. 학습지가 바뀌면 해당 카드만 다시 비교한다.
- 오프닝·NT: 1NT 자연 응답·Stayman `DAHbU1QISwc` · 1NT Transfer·Texas·Smolen·마이너 Transfer `DAHbU6p-9no` · 2NT 오프닝 `DAHbQSUW6SA` · Strong 2♣·Waiting·Second Negative·Kokish `DAHbJpg7Ti8` · Weak Two·Ogust·Feature Ask `DAHbQXTxZms` · Preempt `DAHbbRV5zZ4`
- 응답·레이즈: SAYC 1수트 오픈 뒤 자연 응답 `DAHbbqEDwIk` · 1레벨 오픈과 응답 복습 `DAHT_wNH8D4` · 메이저 Raise `DAHboJ7NfEA` · Bergen·Jacoby·Splinter `DAHboIfI-2k` · Passed-hand·Drury `DAHboHjGkGU` · 마이너 Raise·Inverted `DAHbpIiFRg0`
- 리비드·2/1: 오프너 리비드 `DAHbbihuOsc` · 응답자 리비드 `DAHbjJgD0-8` · Reverse·Jump Shift·Ingberman `DAHbplLIvY4` · 2/1 첫 응답 `DAHbjlUpLG4` · 2/1 이후 `DAHbjhZ6PI8` · SAYC·2/1 실전 비교 `DAHbpsu77Os` · Game Try·Partscore `DAHboPO--ZY`
- 경쟁·확장·평가: 상대 1NT 방어 `DAHawcz2QDQ`(사본 여럿 중 최신) · 오버콜 통합 03 `DAHad__Mmyo` · 3차시 Overcall과 Advancer `DAHbjNyHY5U` · BART·Wolff `DAHbpZCC6qA` · Gazzilli·Transfer Walsh `DAHbpjIAuQA` · 핸드 평가 `DAHbOuB32Po`
- 비딩 기준이 아니라 제외: 미니브리지, 풍속도 수업자료, BRIDGE CLASS 플레이 실습.

## 남은 일
### C그룹: 학습지에 있지만 사이트에 없는 기준 (추가 후보)
- 메이저 오프닝: 1M–3NT = 15–17 밸런스·2장 지지(선택), 직접 4M은 5장 이상 지지 + 짧은 수트(13+는 4M 안 씀), 새 수트 순서(긴 수트 먼저, 4–4는 싼 수트, 5–5는 높은 수트).
- 레이즈: support points 3–2–1(보이드 3·싱글톤 2·더블톤 1, 5–3–1은 선택). 4-3-3-3·9 이하면 Bergen 대신 2M 가능. Bergen은 1·2번째 자리·비경쟁·unpassed에서만. Jacoby 2NT 답 순서는 좋은 5장 사이드 → shortness → 강도. Passed hand는 Jacoby 2NT 대신 Drury.
- Drury 세부: 2♦* 뒤 응답자 2M 최저 NF / 3M 상한 INV / 4M, 경쟁 중 off, passed hand 1NT 6–11 NF. Two-way: 2♣* = 정확히 3장 10–11, 2♦* = 4장 이상 9–11.
- 마이너: 1♦ 레이즈(♦4장이면 2♦ 6–9 / 3♦ 10–12), 2♣ 레이즈는 ♣5장. Inverted는 X·오버콜 뒤 off, passed hand에서 on, 2NT·3m에서 멈출 수 있음.
- 1NT 뒤: SAYC 2♠* 마이너 사인오프와 3♣/3♦ 직접 초대. Stayman 2♥ 뒤 응답자가 ♠4장만 있으면 NT로 후속. Jacoby ♥ 트랜스퍼 뒤 2♠ = ♥5·♠4 8–9 INV(선택). Texas 대신 약한 슬램 관심이면 Jacoby 뒤 4M.
- 2NT 오픈 뒤: 13–15 → 6NT, 16 → 5NT, 17+ → 7NT. 5–4는 Stayman 뒤 Smolen, 5–5는 트랜스퍼 뒤 다른 메이저 GF. 2NT 뒤 Quantitative 4NT = 11–12, 5NT = 16.
- Strong 2♣: Positive 수트 질(5장 AKQ 중 2장 / 6장 AKQJ10 중 3장), 2♣–2♦–2NT 뒤 응답자 0–1 패스 / 3+ 3NT / 9–10 4NT / 11–12 6NT. 오프너 3♣ 리비드 뒤 Second Negative는 3♦.
- Weak Two·Preempt: Rule of 17, 4번째 자리 위크 투 ≈ 10–14, Rule of 2·3·4, 다른 4장 메이저가 있으면 Preempt 피하기.
- 2/1 세부: 1♠–2♥는 ♥5장 이상, 3레벨 새 수트 4장+·보통 14+, 3M 점프 반복 6장+·15+, 4♣·4♦는 게임 아님. 1NT 포싱 뒤 응답자 2NT/3♣ = 10–11 INV, 3M 점프 = 좋은 6장 INV.
- Reverse 세부: 응답자 3♠ 점프 = 6장·8+, 1NT 응답 뒤 높은 새 수트도 Reverse, 2/1 GF 뒤의 높은 새 수트는 Reverse 점수 불필요.
- 경쟁: 1NT 방어 공통 길이(한 수트 6장, 두 수트 5–4), Meckwell X–2♣ 뒤 답(패스 ♣ / 2♦ ♦ / 2♥ 양 메이저), Multi-Landy 2NT = 두 마이너 5–5, 어드밴서의 Fit-showing Jump, 오버콜 뒤 어드밴서 새 수트는 NF, 상대 위크 투 뒤 2NT = 강한 밸런스 + 스토퍼.
- 핸드 평가: 장수점수(5장 +1 · 6장 +2 · 7장 +3), 지지점수, 짧은 수트 아너 감점, 퀵트릭 AKQ = 2.
- 내 핸드로 찾기: 6장 마이너(SAYC 2♠* 사인오프, 8–9는 3m 직접 초대), 5–5 메이저(초대는 ♥ 트랜스퍼 뒤 2♠, 게임은 ♠ 트랜스퍼 뒤 3♥), ♠5·♥4 초대(Stayman 뒤 2♠), 슬램 관심 있는 6장 메이저.

### 학습지 완성 뒤 다시 맞출 카드 (사용자와 2026-11-24 합의)
학습지가 아직 없어 표준 숫자 + `chk: true`로 넣은 카드. 사용자가 학습지를 완성하면 점수·장수를 학습지대로 고치고 부족한 행을 추가한다.
- 1단계로 추가: `vsresp`(상대 응답 뒤 개입), `vsstay`(상대 Stayman·Transfer에 개입), `vsweaknt`(상대 Weak NT 방어), `delayed`(늦은 개입), `vsart`(상대 인위적 비드에 X)
- 이전에 추가: `vsweak2`, `vspre34`, `balraise` (대부분 표준 숫자)
- 2단계(아직 안 함, 선택 심화 후보): 상대 Strong 1♣(Precision 등) 방어, 상대 2NT 오픈·Gambling 3NT 방어, 상대 특수 오프닝(Flannery·Muiderberg·Namyats) 방어

### 그 밖에
- 학습지가 아직 없는 카드: NMF·XYZ·Checkback, Serious 3NT, LTC, Rule of 20.
- 개선 후보: 같은 비드 카드 구분(이름 크게), 알아두면/심화 구역 접기, 분류 이름 정리("상대 오프닝에 개입" vs "상대가 개입했을 때"), 검색 정확도(비드·이름 일치 우선), 표의 빈 점수 칸 처리.

## 새 PC로 옮길 때
1. Claude 데스크톱 앱 설치, 같은 계정으로 로그인.
2. "GitHub의 yomybomy/tokbidding을 문서 폴더에 내려받고, CLAUDE.md를 먼저 읽은 다음 이어서 하자"라고 요청.
3. Git·GitHub CLI 설치(winget `Git.Git`, `GitHub.cli`), `gh auth login --web`으로 로그인.
4. 학습지 비교가 필요하면 Canva 연결 확인.
