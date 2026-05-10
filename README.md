# HID W1 — Context Ledger Prototype

Phi Design School · HID 1주차 과제 프로토타입.

채팅 UX의 인지적 마찰 — **자동 context compaction이 일어났을 때 사용자가 어느 컨텍스트가 살아있고 어느 부분이 압축·드롭됐는지 인지할 수 없는 비대칭** — 을 해결하는 인터랙션 설계.

## Live Demo

👉 **https://st4rgaz3rx.github.io/hid-w1-context-ledger/**

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
