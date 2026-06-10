# Project Operation Template

프로젝트를 시작하기 전에 기획, 버전 계획, 브랜치 흐름, 체크리스트, 커밋 기준을 정리하기 위한 운영 문서 템플릿입니다.

이 저장소는 코드 템플릿이 아니라 프로젝트 진행 방식 템플릿입니다. 사용자가 기획안을 주면 Codex는 `docs/README.md`와 `docs/workflow.md`를 기준으로 버전별 계획 문서와 체크리스트를 만들고, 기능별 작업 흐름을 구성합니다.

## 사용 방법

1. 새 프로젝트에 이 저장소의 `docs/` 폴더를 복사합니다.
2. 사용자는 `docs/planning_brief_template.md` 형식으로 기획안을 작성합니다.
3. Codex는 `docs/README.md`를 먼저 읽고 전체 작업 흐름을 확인합니다.
4. Codex는 기획안을 바탕으로 `docs/product_plan.md`를 정리합니다.
5. Codex는 첫 버전 폴더를 만듭니다. 예: `docs/versions/v0.1/`
6. Codex는 버전별 `plan`, `checklist`, `branch_log`, `commit_log`, `review` 문서를 생성합니다.
7. 기능별 작업은 `feature/v*` 브랜치에서 진행하고, 버전 작업은 `version/v*` 브랜치에 정리합니다.
8. 사용자는 `version/v*` 브랜치를 push한 뒤 GitHub에서 `develop` 대상 PR을 만듭니다.

## 문서 시작점

Codex는 작업을 시작할 때 아래 문서를 먼저 읽습니다.

- `docs/README.md`
- `docs/workflow.md`
- `docs/development_rules.md`
- `docs/file_structure_rules.md`
- 현재 버전의 `docs/versions/v*/plan_*.md`
- 현재 버전의 `docs/versions/v*/checklist_*.md`

## 주요 문서

- `docs/planning_brief_template.md`: 사용자가 처음 제공하는 기획안 양식
- `docs/product_plan.md`: 프로젝트 전체 기획과 MVP 범위
- `docs/development_rules.md`: Codex와 사람이 지킬 개발 규칙
- `docs/file_structure_rules.md`: 파일 분리와 폴더 구조 기준
- `docs/workflow.md`: 기획안 입력부터 PR 초안까지의 전체 흐름
- `docs/version_checklist.md`: 버전별 체크리스트 공통 기준
- `docs/versions/_template/`: 버전별 문서 생성 템플릿
- `docs/commit_convention.md`: 커밋 메시지와 커밋 단위 기준
- `docs/pr_convention.md`: PR 제목과 본문 작성 기준
- `docs/change_log.md`: 중요한 운영 기준 변경 기록

## 기본 브랜치 흐름

```text
main
develop
version/v0.1
feature/v0.1-feature-name
```

- `main`: 안정 버전
- `develop`: 사용자가 최종 관리하고 PR 대상으로 삼는 브랜치
- `version/v*`: 특정 버전의 작업을 모으는 브랜치
- `feature/v*-*`: 기능별 작업 브랜치

Codex는 `develop`이나 `main`에 직접 병합하지 않습니다. Codex는 버전 작업을 정리하고 PR 초안을 만들며, 사용자가 GitHub에서 PR을 만들고 병합을 관리합니다.
