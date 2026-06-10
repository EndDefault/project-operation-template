# Docs README

Codex는 새 프로젝트 작업을 시작할 때 이 문서를 먼저 읽습니다.

이 `docs/` 폴더는 프로젝트의 전체 작업 흐름을 제어하는 운영 문서입니다. 사용자가 기획서를 주면 Codex는 이 문서를 기준으로 버전 계획, 체크리스트, 브랜치 흐름, 커밋 단위를 구성합니다.

## 먼저 읽을 문서

1. `product_plan.md`
2. `development_rules.md`
3. `file_structure_rules.md`
4. `workflow.md`
5. 사용자가 제공한 기획안 또는 `planning_brief_template.md`
6. 현재 버전의 `docs/versions/v*/plan_*.md`
7. 현재 버전의 `docs/versions/v*/checklist_*.md`

## 문서 역할

- `product_plan.md`: 전체 기획과 MVP 범위
- `planning_brief_template.md`: 사용자가 처음 제공하는 기획안 양식
- `development_rules.md`: 개발 중 지킬 약속과 자동화 경계
- `file_structure_rules.md`: 파일 분리와 폴더 구조 기준
- `workflow.md`: 기획서 입력부터 버전 종료까지의 전체 흐름
- `version_checklist.md`: 버전별 체크리스트 공통 기준
- `commit_convention.md`: 커밋 메시지와 커밋 단위 기준
- `pr_convention.md`: PR 제목, 본문, 분리 기준
- `change_log.md`: 중요한 방향 변경 기록
- `versions/`: 버전별 계획, 체크리스트, 브랜치 로그, 커밋 로그, 리뷰

## 버전 폴더 규칙

새 버전을 시작하면 다음 구조를 만든다.

```text
docs/
  versions/
    v0.1/
      plan_v0.1.md
      checklist_v0.1.md
      branch_log_v0.1.md
      commit_log_v0.1.md
      review_v0.1.md
```

버전명은 가능한 한 `v0.1`, `v0.2`, `v1.0`처럼 명확하게 작성한다.

## 패치 버전 규칙

아주 작은 버그 수정이나 문서 오타 수정처럼 새 기능 계획이 필요 없는 작업은 패치 버전으로 처리한다.

예시:

```text
v0.1
-> v0.1.1
```

패치 버전에서는 전체 `plan_*.md`를 새로 만들지 않는다. 대신 간단한 패치 노트와 체크리스트만 만든다.

```text
docs/versions/v0.1.1/
  patch_v0.1.1.md
  checklist_v0.1.1.md
```

패치 브랜치 예시:

```text
fix/v0.1.1-bug-name
```

패치 버전 기준:

- 새 기능을 추가하지 않는다.
- 기존 동작의 버그, 오타, 깨진 링크, 작은 UI 깨짐을 고친다.
- 수정 범위가 작고 명확해야 한다.
- 수정 후 체크리스트와 검증 결과를 남긴다.
- 사용자가 원하면 `version/v0.1.1` 브랜치로 묶고, 아니면 `fix/v0.1.1-*` 브랜치만 사용한다.

## 버전 문서 생성 규칙

새 버전을 시작할 때는 `docs/versions/_template/` 안의 파일을 복사해서 실제 버전명에 맞게 이름을 바꾼다.

예시: `v0.1`

```text
docs/versions/_template/plan_template.md
-> docs/versions/v0.1/plan_v0.1.md

docs/versions/_template/checklist_template.md
-> docs/versions/v0.1/checklist_v0.1.md

docs/versions/_template/branch_log_template.md
-> docs/versions/v0.1/branch_log_v0.1.md

docs/versions/_template/commit_log_template.md
-> docs/versions/v0.1/commit_log_v0.1.md

docs/versions/_template/review_template.md
-> docs/versions/v0.1/review_v0.1.md
```

파일을 만든 뒤 문서 안의 placeholder도 실제 버전명으로 바꾼다.

```text
vX.Y -> v0.1
version/vX.Y -> version/v0.1
feature/vX.Y-* -> feature/v0.1-*
```

## 브랜치 규칙

기본 흐름:

```text
main
develop
version/v0.1
feature/v0.1-feature-name
```

- `main`: 안정 버전
- `develop`: 사용자가 최종 관리하고 PR 대상으로 삼는 브랜치
- `version/v*`: 특정 버전 통합 브랜치
- `feature/v*-*`: 기능별 작업 브랜치

## Codex 실행 규칙

사용자가 기획서를 주면 Codex는 다음 순서로 진행한다.

1. `docs/README.md`와 `workflow.md`를 읽는다.
2. 기획안 또는 `planning_brief_template.md` 내용을 분석한다.
3. `product_plan.md`를 정리한다.
4. 목표 버전을 제안한다.
5. 해당 버전 폴더를 만든다.
6. `plan_*.md`와 `checklist_*.md`를 만든다.
7. 필요한 브랜치 흐름을 제안한다.
8. 사용자 승인 후 version/feature 브랜치를 생성한다.
9. 기능별 feature 브랜치에서 작업한다.
10. 기능별 커밋을 만든다.
11. 체크리스트를 점검한다.
12. 사용자 승인 후 feature 브랜치를 version 브랜치에 병합한다.
13. `review_*.md`와 PR 초안을 작성한다.
14. 사용자가 version 브랜치를 push하고 develop 대상 PR을 만든다.
15. 다음 버전 계획을 준비한다.

## 승인 필요 작업

Codex는 다음 작업 전에 사용자 승인을 받는다.

- feature 브랜치 병합
- push
- PR 생성
- 큰 파일 구조 변경
- 새 의존성 추가
