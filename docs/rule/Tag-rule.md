# Tag Rule

`Tag Rule` 은  
특정 commit 에 버전이나 중요한 기준점을 표시할 때  
어떤 형식으로 tag 를 만들지 정해두는 규칙이다.

tag 는 주로  
배포 버전, 릴리스 시점, 중요한 완료 지점을 표시할 때 사용한다.

branch 는 계속 움직이지만  
tag 는 특정 commit 을 고정해서 가리키므로  
버전 관리에 유용하다.

---

## 1. 왜 필요한가

tag 없이 버전을 관리하면  
어느 commit 이 어떤 배포 버전인지 찾기 어려울 수 있다.

예를 들어 아래 같은 문제가 생길 수 있다.

- 어느 시점이 v1.0 인지 모름
- 배포 기준 commit 을 찾기 어려움
- 이전 안정 버전으로 돌아가기 어려움
- 기록은 있는데 릴리스 기준점이 없음

그래서 중요한 시점에는 tag 를 붙여 두는 것이 좋다.

---

## 2. 기본 원칙

tag 는  
**배포 가능하거나 의미 있는 완료 시점에만 붙이는 것**을 추천한다.

보통 아래에 사용한다.

- 정식 배포 버전
- 중간 점검 버전
- 발표 버전
- 중요한 완료 시점

---

## 3. tag 이름 규칙

가장 많이 쓰는 방식은 아래와 같다.

vMajor.Minor.Patch

### example

- `v1.0.0`
- `v1.1.0`
- `v1.1.1`

---

## 4. 버전 번호 의미 추천

### Major
큰 변경  
이전 버전과 크게 달라질 때 올린다.

example:
- `v1.0.0` → `v2.0.0`

### Minor
기능 추가  
기존 기능은 유지하면서 새 기능이 추가될 때 올린다.

example:
- `v1.0.0` → `v1.1.0`

### Patch
버그 수정  
작은 수정이나 오류 수정일 때 올린다.

example:
- `v1.1.0` → `v1.1.1`

---

## 5. 기본 tag 명령어

### tag 생성
`git tag v1.0.0`

### 주석이 있는 tag 생성
`git tag -a v1.0.0 -m "Release version 1.0.0"`

### tag 목록 확인
`git tag`

### 특정 tag push
`git push origin v1.0.0`

### 모든 tag push
`git push origin --tags`

---

## 6. 작성 규칙 추천

### 1) 의미 없는 commit 에 tag 붙이지 않기
중간 저장용 commit 에는 tag 를 붙이지 않는 것이 좋다.

### 2) 버전 형식 통일
`v1`, `ver1`, `release1` 처럼 섞지 말고  
하나의 형식으로 통일하는 것이 좋다.

좋은 예:
- `v1.0.0`

나쁜 예:
- `version1`
- `release-final`
- `test-tag`

### 3) 가능하면 주석 tag 사용
나중에 무엇을 위한 tag 인지 보기 쉽다.

example:
`git tag -a v1.0.0 -m "First stable release"`

### 4) 정식 배포 기준으로 tag 붙이기
실행 가능하고 기준점이 되는 상태에 붙이는 것이 좋다.

### 5) tag 는 수정보다 새로 만드는 방식 권장
한 번 공개된 tag 를 자주 바꾸는 것은 좋지 않다.

---

## 7. 자주 쓰는 흐름

### 첫 릴리스

`git switch main`  
`git pull origin main`  
`git tag -a v1.0.0 -m "First release"`  
`git push origin main`  
`git push origin v1.0.0`

### 버그 수정 후 패치 버전

`git tag -a v1.0.1 -m "Bug fix release"`  
`git push origin v1.0.1`

---

## 8. 나쁜 예 / 좋은 예

### bad

- 의미 없는 commit 에 tag 생성
- tag 이름 형식이 제각각임
- 어떤 버전인지 설명 없음
- 테스트용 tag 를 그대로 push
- 배포 기준이 아닌 상태에 tag 생성

### good

- 릴리스 기준 commit 에 tag 생성
- `v1.0.0` 형식 사용
- 필요하면 주석 tag 사용
- 버전 증가 기준을 통일
- 공개된 tag 는 신중하게 관리

---

## 9. 한 줄 정리

좋은 tag 규칙은  
**중요한 버전이나 기준점을 일정한 형식으로 표시해서 나중에도 쉽게 찾을 수 있게 만드는 것**이다.