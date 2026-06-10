
# File Structure Rules

이 문서는 파일 하나에 모든 기능을 몰아넣지 않기 위한 기준입니다.

## 기본 원칙

- 한 파일은 하나의 명확한 책임을 가진다.
- 화면, 상태, API 호출, 비즈니스 로직, 타입, 상수는 필요하면 분리한다.
- 기존 프로젝트의 폴더 구조와 네이밍을 우선한다.
- 새 구조를 만들면 이유를 버전 문서나 변경 기록에 남긴다.

## 분리 기준

다음 상황이면 파일 분리를 검토한다.

- 파일이 250줄을 넘고 여러 책임이 섞여 있다.
- 같은 로직이 두 번 이상 반복된다.
- 화면 파일 안에 데이터 요청, 데이터 변환, 검증, UI가 모두 들어 있다.
- 특정 로직을 따로 테스트하기 어렵다.
- 파일 이름만 보고 역할을 이해하기 어렵다.

## 권장 구조 예시

프론트엔드 프로젝트:

```text
src/
  app/
  pages/
  features/
    feature-name/
      components/
      hooks/
      api/
      utils/
      types.ts
      constants.ts
  shared/
    components/
    hooks/
    lib/
    utils/
```

백엔드 또는 스크립트 프로젝트:

```text
src/
  modules/
    module-name/
      service.*
      repository.*
      schema.*
      types.*
  shared/
  config/
tests/
```

## 새 파일 생성 체크

- 이 파일의 책임을 한 문장으로 설명할 수 있는가?
- 기존 폴더 중 더 알맞은 위치가 있는가?
- 이름만 보고 역할을 알 수 있는가?
- 같은 책임의 파일들이 이미 있는가?
- 문서의 구조 규칙과 충돌하지 않는가?
