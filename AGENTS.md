# EduHelper 개인정보 처리방침 저장소 규칙

## 프로젝트와 배포 경계

- 이 저장소는 공개용 EduHelper 개인정보 처리방침 단일 페이지 `privacy-policy.html`을 게시한다.
- GitHub Pages는 `main` branch의 저장소 root를 사용한다. `main` 통합·push는 법적 사용자 문구의 실제 운영 게시로 이어질 수 있으므로 일반 문서 변경과 같은 것으로 취급하지 않는다.
- 공개 페이지와 EduHelper 저장소의 `tools/store/privacy-policy.html`은 의도적으로 동기화된 문서다. 방침을 바꾸는 작업은 두 후보의 byte 단위 일치 또는 의도적인 차이와 그 근거를 검증한다.

## 내용 보존 원칙

- 시행일, 최종 수정일, 배포 문서 version, 연락처, 처리 항목·목적·위치·보유기간, 제3자·위탁·국외 처리, 권리행사·삭제 절차를 검증된 근거 없이 바꾸지 않는다.
- heading, anchor, link, UTF-8 encoding과 반응형·dark mode 렌더링을 보존한다.
- 법률·제품 동작·외부 서비스에 관한 사실은 현재 구현 및 확인 가능한 권위 자료와 맞춰 검토한다. 확인하지 못한 내용을 확정 문구로 추가하지 않는다.
- 학생자료, 계정자료, 비공개 연락처, token, secret과 로컬 전용 파일을 공개 페이지·로그·PR에 넣지 않는다. 이 저장소의 공개 PR에는 기기 고유명과 사용자 홈 절대경로를 기록하지 않고, 기기 역할·canonical 상대경로·branch·Worktree slug로 실행 위치를 식별한다. 정확한 로컬 경로는 공개되지 않는 검증 기록에서만 대조한다.

## 작업과 승인 경계

- 새 작업과 다른 기기의 작업 이어받기는 registry와 device policy에 따른 `development-ecosystem` start/resume 절차로 exact canonical default branch와 HEAD를 확인해 `codex/*` 전용 Worktree를 준비한다. 읽기 전용 조사·리뷰·렌더링 확인만으로는 새 PR을 만들지 않는다.
- 승인된 구현 범위의 로컬 수정·검증·topic commit까지만 자동 진행한다. Non-force topic push, local `main` 통합, GitHub `main` push와 Pages 자동 게시, 기타 외부 게시와 삭제는 각 action마다 같은 작업의 direct exact approval이 있어야 한다. 승인된 topic push와 Draft PR 생성·본문 재확인까지 끝나야 `검토 대기 완료`라고 표시한다.
- 기존 사용자 변경의 stash·삭제·이동은 수행하지 않는다. Force/history rewrite, 파괴적 migration, 영구 삭제와 복구 근거 삭제는 별도 device-bound local exact 절차 없이는 수행하지 않는다.
- PR에는 변경한 조항, 정책 version·날짜 영향, EduHelper 동기본 비교, 로컬 렌더링 결과와 실제 게시 위험을 기록한다.
- 실제 provider가 제공한 PR Preview가 없으면 `Preview 없음`이라고 쓰고 로컬 URL을 제공한다. `https://cuff8502.github.io/privacy-policy/privacy-policy.html`은 운영 URL이며 Preview가 아니다.

## 실행과 검증

- package manager와 프로젝트 전용 test suite는 없다. 존재하지 않는 설치·테스트 명령을 추정하지 않는다.
- `git diff --check`와 HTML parser 검사를 실행하고, 현재 Worktree를 로컬 HTTP server로 열어 `privacy-policy.html`의 HTTP 200 응답을 확인한다.
- `privacy-policy.html` 변경이 있으면 제목·section heading·table·링크·시행일·version을 브라우저에서 확인하고 EduHelper 동기본과 전체 내용을 비교한다. 운영 규칙만 바꾸고 HTML blob이 base와 동일한 경우에는 byte 동일 근거와 브라우저 확인이 해당 없음을 기록한다.
- production 페이지가 바뀌었다고 말하려면 별도 승인된 게시 후 실제 Pages 결과를 확인해야 한다.
