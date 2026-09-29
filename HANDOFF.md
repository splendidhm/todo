# 작업 인수인계

## 프로젝트
- 경로: `C:\Users\tomi2\projects\todo`
- `index.html` 하나에 HTML/CSS/JavaScript를 담은 개인용 할 일 달력.
- GitHub: https://github.com/splendidhm/todo, 브랜치 `main`.

## 다음 버전 결정 사항 (2026-09-20)
- 다음 버전 코드네임: **고슴도치**.
- 마감 알림은 **마감일 3일 전부터** 표시한다.
- 사용자가 확정한 요구사항이며, 아직 코드에는 구현하지 않음.

## 지금까지 한 일
- 날짜별 할 일 추가, 완료 체크·해제, 개별·월별 완료 항목 삭제, 월 이동, 완료 개수 표시.
- 오른쪽 상단 고정 다크모드 토글과 모드 저장 구현. 마지막 기존 커밋은 `1dd4d6f` (`다크모드 업그레이드`).
- 이전 버전 백업 `index.backup.html`과 기여 가이드 `AGENTS.md` 작성.
- 이번 작업: 새 할 일 입력 폼에 선택 사항인 마감일 날짜 입력 추가.
- 각 기존 항목 아래에도 마감일 입력을 표시하여 추가·수정·비우기 가능.
- 할 일에 `dueDate` 필드 추가: `YYYY-MM-DD` 문자열, 미지정은 빈 문자열.
- `todo-calendar-v1` 저장 키 유지. 기존 항목에 마감일이 없거나 잘못된 날짜가 저장되어 있으면 빈 값으로 읽음.
- `normalizeDueDate()`는 실제 날짜를 검증하고, `dueDateField()`는 라벨과 날짜 입력을 생성함.
- 항목이 배치된 달력 날짜와 마감일은 독립적이며, 마감일을 바꿔도 항목의 달력 위치는 이동하지 않음.
- 기존 자기소개 링크와 백업 파일을 보존함. 이번 변경은 커밋·푸시하지 않음.

## 검증
- Node의 VM과 간단한 DOM/localStorage 모형으로 실제 스크립트를 실행하여 검사 통과:
  기존 데이터 호환, 마감일 등록·복원·수정·비우기, 잘못된 날짜/윤년 검증, 완료 체크, 월별 완료 삭제, 월 이동.
- JavaScript 문법 검사 및 `git diff --check` 통과.
- 자동 검사 코드는 터미널에서 일회 실행했으며 저장된 테스트 파일은 없음.
- 연결된 브라우저가 없어 실제 화면, 네이티브 날짜 선택기, 키보드·한글 입력, 모바일 배치, 양쪽 테마의 수동 검증은 미완료.

## Latest implementation (2026-09-20)
- Implemented overdue styling for incomplete tasks with a due date before the current local date. Tasks due today and completed tasks are excluded.
- Added red task text, a red left border, and a Korean overdue notice, with separate light/dark theme colors.
- Deadline edits update the existing task element immediately and preserve input focus.
- Refresh at local midnight and on window focus / document visibility restoration; today's calendar highlight also updates without rebuilding inputs.
- Existing storage keys, task placement, backup, and about link are preserved. No commit or push performed.

## Verification in this session
- Passed JavaScript syntax checks and git diff --check.
- Executed the actual application script in Node VM with DOM/storage stubs: yesterday/today/tomorrow, no deadline, completed tasks, year/month/leap-day boundaries, completion toggle, deadline edit/clear, focus preservation, storage writes, and midnight timer callback.
- Browser rendering, native date picker, actual overnight/sleep behavior, keyboard/IME input, mobile scrolling, and visual contrast in both themes still require manual verification.

## Next steps
- Run the browser checks above using disposable tasks; also verify reload persistence and individual/monthly deletion.
- Implement the confirmed next-version requirement above: show deadline reminders starting 3 days before the due date (codename: 고슴도치).

## 날짜별 메모 및 커밋 준비 (2026-09-29)
- 기존 달력 위에 날짜 선택과 하루 한 편의 본문 입력 영역을 추가함. 처음 열 때는 오늘 날짜를 선택하며 달력 월 이동과 독립적으로 동작함.
- `todo-diary-v1`에 날짜별 본문을 입력 즉시 저장함. 줄바꿈과 공백을 보존하고 본문을 비우면 해당 날짜의 기록을 삭제함.
- 메모 저장 상태와 오류를 별도로 표시함. 저장 실패 시 창 안의 입력은 유지하며, 불러오기 실패 시 기존 저장값 보호를 위해 자동 저장을 중지함.
- 모바일 너비 및 라이트/다크 테마 스타일을 추가함. 새 달력, 검색, 로그인, 동기화, 백업 기능은 추가하지 않음.
- 구현 시 Node VM 검증 통과: 재실행 복원, 날짜별 분리, 수정·삭제, 한글·이모지·여러 줄, 윤년 날짜, 조합 완료 이벤트, 저장 실패와 복구, 손상 데이터 보호.
- 실제 브라우저 렌더링, 모바일 화면, 키보드 및 한글 IME 조작은 미검증. 앱 파일을 기본 브라우저로 여는 동작은 수행함.
- 이번 커밋 대상은 `index.html`, `AGENTS.md`, `HANDOFF.md`. 위의 미커밋 기록은 당시 작업 상태를 뜻함.
