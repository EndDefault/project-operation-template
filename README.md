# project-operation-template

새 프로젝트를 시작할 때 사용하는 프로젝트 운영 문서 템플릿입니다.

이 템플릿은 README를 현재 savepoint로 사용하고, `docs/` 문서로 기획, 개발 규칙, 파일 구조, 버전 체크리스트, 변경 기록, 커밋 규칙을 관리합니다.

## 사용 방법

1. 이 리포지토리에서 `Use this template`을 눌러 새 프로젝트를 생성한다.
2. 새 프로젝트의 `README.md`에서 프로젝트명, 설명, 현재 목표 버전을 수정한다.
3. `docs/product_plan.md`에 프로젝트 기획을 작성한다.
4. `docs/version_checklist.md`에서 `v0.1.0` 목표를 프로젝트에 맞게 수정한다.
5. `docs/file_structure_rules.md`에서 사용할 폴더 구조를 정한다.
6. 큰 방향 변경이 생기면 `docs/change_log.md`에 기록한다.
7. 커밋은 `docs/commit_convention.md` 규칙을 따른다.

## 문서 구성

- `README.md`: 프로젝트 index + 현재 savepoint
- `docs/product_plan.md`: 제품 기획과 방향성
- `docs/development_rules.md`: 개발 방향 및 규칙
- `docs/file_structure_rules.md`: 파일 구조와 분리 규칙
- `docs/version_checklist.md`: 버전별 구현 체크리스트
- `docs/change_log.md`: 큰 방향 변경 기록
- `docs/commit_convention.md`: Gitmoji 커밋 규칙

## README 운영 방식

새 프로젝트의 README는 긴 설명서가 아니라 현재 상태를 보여주는 입구로 사용합니다.

README에는 다음 내용을 유지합니다.

- 현재 단계
- 현재 목표 버전
- 다음 작업
- 현재 진행도
- 주요 문서 링크
- 실행 방법

## 체크리스트 운영 방식

`docs/version_checklist.md`는 이번 버전에서 구현할 일을 관리합니다.

완료한 항목은 `[x]`로 표시하고, 아직 하지 않은 항목은 `[ ]`로 둡니다.

## 변경 기록 운영 방식

`docs/change_log.md`는 진행 상황을 적는 문서가 아닙니다.

다음과 같은 큰 변경이 있을 때만 기록합니다.

- 프로젝트 방향 변경
- MVP 범위 변경
- 폴더 구조 변경
- 기술 스택 변경
- 버전 계획 변경
- 기존 문서 기준을 덮어쓰는 결정

## 새 프로젝트에서 먼저 수정할 것

- 프로젝트 이름
- 프로젝트 한 줄 설명
- 현재 목표 버전
- MVP 목표
- 기술 스택
- 파일 구조 규칙
- `v0.1.0` 체크리스트
