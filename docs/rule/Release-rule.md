# Release Rule

`Release Rule` 은  
프로젝트를 배포하거나 버전을 공개할 때  
어떤 기준으로 release 할지 정해두는 규칙이다.

release 는 단순히 파일을 올리는 것이 아니라  
**현재 버전을 공식적으로 내보내는 기준점**을 만드는 작업이다.

그래서 release 전 확인할 것과  
버전 관리 기준을 정해두는 것이 좋다.

---

## 1. 왜 필요한가

release 규칙이 없으면  
어느 시점이 정식 버전인지 헷갈릴 수 있다.

예를 들어 아래 같은 문제가 생길 수 있다.

- 테스트 안 된 버전이 배포됨
- 어떤 commit 이 release 기준인지 모름
- 버전 번호가 제각각임
- 수정 사항이 정리되지 않음
- 이전 버전으로 돌아가기 어려움

그래서 release 전에 확인 기준을 정해두는 것이 좋다.

---

## 2. 기본 원칙

release 는  
**실행 가능하고, 기준점으로 삼을 수 있는 상태에서만 진행**하는 것이 좋다.

보통 아래를 먼저 확인한다.

- 기능이 정상 동작하는지
- 치명적인 버그가 없는지
- 문서가 필요한 만큼 정리되었는지
- 버전 번호가 맞는지
- tag 를 붙일 준비가 되었는지

---

## 3. 버전 규칙 추천

release 버전은 아래 형식을 추천한다.

vMajor.Minor.Patch

### example

- `v1.0.0`
- `v1.1.0`
- `v1.1.1`

### 의미

- `Major` : 큰 변경
- `Minor` : 기능 추가
- `Patch` : 버그 수정

---

## 4. release 전 확인할 것

### 1) 현재 branch 확인
보통 release 는 `main` 기준으로 진행한다.

example:
`git branch`

### 2) 최신 상태 반영
원격 저장소 최신 내용을 먼저 반영한다.

example:
`git pull origin main`

### 3) 변경 내용 확인
example:
`git status`  
`git log --oneline`

### 4) 실행 확인
최소한 기본 실행 여부는 확인하는 것이 좋다.

### 5) 문서 확인
필요하면 아래도 확인한다.

- `README.md`
- 변경 사항 문서
- 사용 방법 문서

---

## 5. 기본 release 흐름

### recommended flow

1. `main` 최신화  
2. 실행 및 기본 동작 확인  
3. 버전 번호 결정  
4. tag 생성  
5. 원격 저장소에 push  
6. 필요하면 Release Note 작성  

---

## 6. 자주 쓰는 명령어

### main 최신화
`git switch main`  
`git pull origin main`

### tag 생성
`git tag -a v1.0.0 -m "Release version 1.0.0"`

### tag push
`git push origin v1.0.0`

### 모든 tag push
`git push origin --tags`

---

## 7. Release Note 추천 항목

release 할 때는  
무엇이 바뀌었는지 간단히 정리해 두는 것이 좋다.

### example

- Added
  - 로그인 기능 추가

- Fixed
  - 이미지 경로 오류 수정

- Docs
  - README 정리

이렇게 적어두면  
나중에 버전별 변경 사항을 보기 쉽다.

---

## 8. 작성 규칙 추천

### 1) 테스트 안 된 상태로 release 하지 않기
최소한 기본 실행과 핵심 기능은 확인하는 것이 좋다.

### 2) release 는 의미 있는 시점에만 진행
중간 저장용 상태에는 release 를 만들지 않는 것이 좋다.

### 3) tag 와 version 형식 통일
`v1.0.0` 형식으로 통일하는 것이 보기 좋다.

### 4) release 전에 불필요한 파일 확인
로그 파일, 임시 파일, 민감한 파일이 포함되지 않게 확인한다.

### 5) 변경 사항을 간단히 기록
Release Note 나 태그 메시지라도 남기는 것이 좋다.

---

## 9. 나쁜 예 / 좋은 예

### bad

- 테스트 없이 바로 release
- 버전 번호 형식이 일정하지 않음
- 무엇이 바뀌었는지 기록 없음
- 중간 작업 상태를 release 로 공개
- tag 없이 release 기준만 말로 정함

### good

- `main` 최신 상태 확인 후 release
- 기본 동작 확인 후 진행
- `v1.0.0` 형식 사용
- tag 생성 후 push
- 변경 사항 간단히 정리

---

## 10. 한 줄 정리

좋은 release 규칙은  
**배포 가능한 기준점을 일정한 버전 형식과 절차로 관리해서, 언제든 다시 확인할 수 있게 만드는 것**이다.