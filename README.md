# HID Prototype Demos

Phi Design School · HID 과제 프로토타입 모음.

## Live Demos

- **W1 · Context Ledger**: https://st4rgaz3rx.github.io/hid-w1-context-ledger/
- **W2 · Goal Strip**: https://st4rgaz3rx.github.io/hid-w1-context-ledger/v2/
- **Final · Loop loop**: https://st4rgaz3rx.github.io/hid-w1-context-ledger/loop-loop/

---

## W1 · Context Ledger

채팅 UX의 인지적 마찰 — **자동 context compaction이 일어났을 때 사용자가 어느 컨텍스트가 살아있고 어느 부분이 압축·드롭됐는지 인지할 수 없는 비대칭** — 을 해결하는 인터랙션 설계.

## 구현된 인터랙션 (행위 → 반응)

| # | 사용자 행위 | 시스템 반응 |
|---|---|---|
| 1 | 첫 turn에 1000줄 스펙 붙여넣기 | `📄 spec v1` 카드 🟢 active 등록 |
| 2 | 자동 compaction | 카드 🟢 → 🟡 + ⚠ 배지 + 토큰 갱신 |
| 3 | 보내기 버튼 hover | "답변에 쓰일 컨텍스트" 칩 묶음 |
| 4 | 🟡 카드 클릭 | 좌우 분할 diff 모달 |
| 5 | 🟡 카드를 입력창으로 드래그 | 원문 인용 자동 삽입 + 🟢↻ 전이 |
| 6 | 드롭된 turn 거터에 hover | 🔴 점 + "드롭됨" 툴팁 |

## 작동 환경

- 단일 HTML 파일 (외부 의존성 없음)
- vanilla HTML/CSS/JS
- 모던 브라우저 (Chrome, Safari, Firefox 모두 OK)

## 시연 시나리오 (6스텝)

1. **컨텍스트 비대칭 인지** — 좌측 ledger의 🟡 카드를 본다
2. **send 직전 미리보기** — 입력 후 보내기 hover, 칩 묶음 확인
3. **diff로 누락 확인** — 🟡 spec v1 클릭, 좌우 분할 모달 보기
4. **드래그 재첨부** — 🟡 카드를 입력창으로 드래그
5. **보내기 → 답변 인용** — 클릭 후 답변이 재첨부 spec 디테일 인용
6. **드롭 마커 확인** — turn 14 거터에 hover

---

작성: 2026-05-08~05-10 (Phi Design School HID 1주차)

---

## W2 · Goal Strip

긴 AI 채팅에서 초반 목표가 대화에 묻혀 모델이 최근 메시지 중심으로 답하는 문제를 다룬다. 상단에 수정 가능한 `Goal Strip`을 두고, 답변마다 목표 관련성을 표시하며, 목표 밖 요청은 답변 전에 분기/업데이트를 선택하게 한다.

### 데모 URL

👉 **https://st4rgaz3rx.github.io/hid-w1-context-ledger/v2/**

### 구현된 인터랙션

| # | 사용자 행위 | 시스템 반응 |
|---|---|---|
| 1 | Goal Strip 확인 | 현재 목표와 기준 chip이 상단 상태값으로 고정 표시 |
| 2 | 목표 관련 요청 보내기 | 답변에 `Goal fit: High` badge 표시 |
| 3 | 목표 밖 요청 보내기 | 답변 전 `Drift Check` modal 표시 |
| 4 | 별도 대화 분기 선택 | 곁가지 요청만 분리하고 현재 목표 보존 |
| 5 | Edit Goal 열기 | 목표와 기준 chip을 drawer에서 수정 |
| 6 | 수정 목표로 재요청 | 업데이트된 목표 기준으로 답변 생성 |

### 작동 환경

- `v2/index.html` 단일 HTML 파일
- vanilla HTML/CSS/JS
- 외부 의존성 없음

---

## Final · Loop loop

loop engineering(자율 코딩 에이전트 루프)을 위한 UIUX. 에이전트가 같은 실패를 반복하며 로그만 바쁘게 흘러도 통과 수가 그대로면 진척이 아니다(**busy ≠ progress**). iteration을 `advanced / stalled / regressed` 진척 상태로 표상하고, 무진척이 3회 쌓이면 다음 iteration이 토큰을 쓰기 전에 `Spin Check`로 멈춰 세워 방향 수정 / 정지 / 계속을 고르게 한다. 미니멀 에디토리얼 테마.

### 데모 URL

👉 **https://st4rgaz3rx.github.io/hid-w1-context-ledger/loop-loop/**

### 사용 방법

진입 시 단계별 가이드 popup이 시나리오를 설명한다. 닫으면 메인 화면에서 직접 루프를 한 회차씩 돌려본다.

| # | 사용자 행위 | 시스템 반응 |
|---|---|---|
| 1 | 가이드 popup 훑고 시작하기 | 5단계 시나리오 확인 후 메인 진입 |
| 2 | `다음 iteration 실행` 3회 | #1–3 advanced, tests 2→16/20, 무진척 0 |
| 3 | 계속 눌러 #4–6까지 | #4–5 stalled, #6 regressed, 무진척 3, budget 경고 |
| 4 | 한 번 더 누름 | `Spin Check` 인터셉트 — ledger dim, 토큰 쓰기 전 정지 |
| 5 | 방향 수정 → 제약 입력 → 적용 | #7 advanced 14→20, 20/20 달성, 무진척 0 |

### 작동 환경

- `loop-loop/index.html` 단일 HTML 파일
- vanilla HTML/CSS/JS (폰트는 Google Fonts CDN, 오프라인 시 시스템 폰트로 graceful fallback)
- 외부 의존성 없음

---

작성: 2026-06-15 (Phi Design School HID 최종 과제)
