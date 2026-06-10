# Workflow

사용자가 기획서를 주면 Codex가 버전별 계획과 브랜치 흐름을 만들고, 기능별 작업을 진행하기 위한 전체 흐름입니다.

## 전체 흐름

```text
기획안 입력
-> docs 확인
-> product_plan 정리
-> 버전 결정
-> 버전 폴더 생성
-> plan/checklist 생성
-> 기준 브랜치 확인
-> version 브랜치 생성
-> feature 브랜치 생성
-> 기능별 구현
-> 기능별 커밋
-> 점검
-> feature를 version에 병합
-> 버전 리뷰
-> PR 초안 작성
-> 다음 버전 준비
```

## 1. 기획안 입력

사용자는 자연어로 기획안을 제공하거나 `planning_brief_template.md` 형식으로 작성한다.

Codex는 기획안을 다음 항목으로 정리한다.

- 목표
- 사용자
- 핵심 기능
- 제외할 일
- 우선순위
- 예상 버전
- 열린 질문

정리한 내용은 `product_plan.md`에 반영한다.

## 2. 버전 결정

첫 작업은 보통 `v0.1`로 시작한다.

버전 예시:

- `v0.1`: 가장 작은 MVP
- `v0.2`: 사용성 개선
- `v0.3`: 안정화
- `v1.0`: 첫 정식 버전

## 3. 버전 폴더 생성

예시:

```text
docs/versions/v0.1/
  plan_v0.1.md
  checklist_v0.1.md
  branch_log_v0.1.md
  commit_log_v0.1.md
  review_v0.1.md
```

생성 규칙:

1. `docs/versions/vX.Y/` 폴더를 만든다.
2. `docs/versions/_template/` 문서를 복사한다.
3. 파일명에서 `template`을 실제 버전명으로 바꾼다.
4. 문서 안의 `vX.Y`를 실제 버전명으로 바꾼다.
5. 사용자가 준 기획안을 `plan_vX.Y.md`에 반영한다.
6. 완료 조건을 `checklist_vX.Y.md`에 반영한다.

예시: `v0.1`

```text
plan_template.md -> plan_v0.1.md
checklist_template.md -> checklist_v0.1.md
branch_log_template.md -> branch_log_v0.1.md
commit_log_template.md -> commit_log_v0.1.md
review_template.md -> review_v0.1.md
```

## 3-1. 패치 버전 처리

작은 버그 수정은 새 기능 버전처럼 큰 계획을 만들지 않는다.

예시:

```text
v0.1에서 발견된 버그
-> v0.1.1 패치
```

패치 버전에서는 다음 문서만 만든다.

```text
docs/versions/v0.1.1/
  patch_v0.1.1.md
  checklist_v0.1.1.md
```

패치 작업 흐름:

1. 버그 내용을 짧게 정리한다.
2. 영향 범위와 재현 방법을 적는다.
3. `fix/v0.1.1-*` 브랜치를 제안한다.
4. 수정한다.
5. 재현 케이스가 해결됐는지 확인한다.
6. `checklist_v0.1.1.md`에 검증 결과를 남긴다.
7. PR 초안을 작성한다.

패치 버전에서 하지 않는 것:

- 새 기능 추가
- 큰 파일 구조 변경
- 새 의존성 추가
- 전체 버전 계획 재작성

## 4. 브랜치 생성

기준 흐름:

```bash
# 기준 브랜치 확인 후 시작
git checkout -b version/v0.1
git checkout -b feature/v0.1-feature-name
```

브랜치 이름:

- `version/v0.1`
- `feature/v0.1-auth`
- `feature/v0.1-layout`
- `fix/v0.1-build`
- `docs/v0.1-operation`

## 5. 기능별 작업

기능 하나를 하나의 feature 브랜치에서 작업한다.

작업 중 확인:

- 관련 plan 항목
- 관련 checklist 항목
- 파일 구조 규칙
- 검증 방법
- 커밋 단위

## 6. 커밋

기능 단위로 커밋한다.

커밋 전 확인:

```bash
git status --short
git diff --stat
```

커밋 후 `commit_log_*.md`에 기록한다.

## 7. 점검

feature 브랜치를 `version/v*`에 병합하기 전에 확인한다.

- 체크리스트 완료 여부
- 실행, 빌드, 테스트 결과
- 문서 갱신 여부
- 관련 없는 변경 포함 여부

## 8. 병합

병합은 사용자 승인 후 진행한다.

흐름:

```text
feature/v0.1-* -> version/v0.1
version/v0.1 -> push
GitHub PR: version/v0.1 -> develop
```

`develop`과 `main` 병합은 사용자가 GitHub PR에서 관리한다.

## 9. 버전 종료

버전이 끝나면 `review_*.md`를 작성한다.

포함할 내용:

- 완료한 일
- 못 한 일
- 다음 버전으로 넘길 일
- 검증 결과
- 배운 점 또는 운영 기준 변경

## 10. 다음 버전 준비

다음 버전을 시작할 때 이전 버전의 review를 먼저 읽는다.

예시:

```text
v0.1 review
-> v0.2 plan
-> v0.2 checklist
-> version/v0.2
-> feature/v0.2-*
```
