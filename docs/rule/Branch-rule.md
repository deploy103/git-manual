# Branch Rule

`Branch Rule` 은  
Git branch를 어떤 기준으로 만들고, 어떤 이름으로 관리할지 정해두는 규칙이다.

branch 이름과 사용 목적을 통일하면  
현재 어떤 작업을 하고 있는지 바로 파악할 수 있고,  
협업할 때도 작업 구분이 훨씬 쉬워진다.

---

## 1. 왜 필요한가

branch를 아무 이름으로 만들면  
무슨 작업용 branch인지 알아보기 어렵다.

예를 들어 아래와 같은 이름은 좋지 않다.

- test
- aaa
- branch1
- qwe

이런 이름은 나중에 봤을 때  
무슨 작업을 위한 branch였는지 알기 어렵다.

반대로 규칙을 정하면  
기능 추가, 버그 수정, 문서 수정 같은 작업을 branch 이름만 보고도 구분할 수 있다.

---

## 2. 기본 원칙

branch 이름은  
**작업 종류 + 작업 내용** 형태로 만드는 것을 추천한다.

기본 형식은 아래와 같다.

type/short-name

### example

- feat/login
- fix/upload-path
- docs/git-manual
- refactor/input-handler
- chore/vscode-ignore

---

## 3. 자주 사용하는 branch type

### feat
새로운 기능 추가

example: `feat/login`

### fix
버그 수정

example: `fix/file-upload-error`

### docs
문서 수정

example: `docs/git-manual`

### refactor
기능 변화 없이 코드 구조 개선

example: `refactor/input-handler`

### chore
설정, 패키지, 기타 작업

example: `chore/gitignore-update`

### test
테스트 코드 추가 또는 수정

example: `test/login-check`

### hotfix
급한 버그 수정  
보통 운영 중인 중요한 문제를 빠르게 고칠 때 사용한다.

example: `hotfix/login-error`

---

## 4. branch 이름 작성 규칙

### 1) 소문자만 사용
branch 이름은 소문자로 통일하는 것이 좋다.

좋은 예:
- `feat/login-page`

나쁜 예:
- `Feat/LoginPage`

### 2) 공백 사용 금지
branch 이름에 공백은 넣지 않는다.

좋은 예:
- `docs/readme-update`

나쁜 예:
- `docs/readme update`

### 3) 단어 구분은 하이픈(-) 사용
여러 단어가 들어가면 하이픈으로 구분한다.

좋은 예:
- `fix/image-path-error`

나쁜 예:
- `fix/image_path_error`

### 4) 너무 길게 쓰지 않기
branch 이름은 짧고 어떤 작업인지 보일 정도면 충분하다.

좋은 예:
- `refactor/input-logic`

나쁜 예:
- `refactor/change-the-entire-input-processing-function-for-better-readability`

### 5) 작업 하나당 branch 하나 사용
여러 작업을 하나의 branch에 몰아서 하지 않는 것이 좋다.

예:
- 로그인 기능 추가 → `feat/login`
- README 수정 → `docs/readme-update`

---

## 5. 추천 branch 예시

### 기능 추가
- `feat/login`
- `feat/file-upload`
- `feat/dark-mode`

### 버그 수정
- `fix/null-error`
- `fix/image-path`
- `fix/login-redirect`

### 문서 수정
- `docs/readme`
- `docs/git-manual`
- `docs/branch-rule`

### 코드 정리
- `refactor/main-logic`
- `refactor/input-handler`

### 설정 작업
- `chore/gitignore`
- `chore/vscode-setting`

### 긴급 수정
- `hotfix/server-error`

---

## 6. branch 생성 예시

새 branch를 만들 때는 아래처럼 사용한다.

git switch -c feat/login

또는

git checkout -b feat/login

---

## 7. main branch 사용 규칙 추천

`main` branch는  
최종적으로 정리된 안정적인 내용만 두는 것을 추천한다.

즉, 바로 `main` 에서 작업하지 말고  
작업용 branch를 만든 뒤 작업을 끝내고 합치는 방식이 좋다.

### recommended flow

1. `main` 에서 새 branch 생성
2. 작업 진행
3. commit 정리
4. `main` 으로 merge

---

## 8. 추천 규칙 예시

개인 프로젝트 또는 팀 프로젝트에서는 아래 정도로 통일하면 충분하다.

- `main`      : 최종본, 안정적인 branch
- `feat/*`    : 기능 추가
- `fix/*`     : 버그 수정
- `docs/*`    : 문서 수정
- `refactor/*`: 리팩토링
- `chore/*`   : 설정, 기타 작업
- `test/*`    : 테스트 작업
- `hotfix/*`  : 긴급 수정

---

## 9. 나쁜 예 / 좋은 예

### bad

- `test`
- `aaa`
- `mybranch`
- `branch1`

### good

- `feat/login`
- `fix/upload-error`
- `docs/git-manual`
- `chore/gitignore-update`

---

## 10. 한 줄 정리

좋은 branch 이름은  
**무슨 작업 branch인지 이름만 보고 바로 알 수 있게 만드는 것**이다.