# Commit Message Rule

`Commit Message Rule` 은  
Git commit 메시지를 어떤 형식으로 작성할지 정해두는 규칙이다.

일관된 commit 메시지를 사용하면  
무슨 작업을 했는지 한눈에 보기 쉽고, 협업할 때도 변경 내용을 빠르게 파악할 수 있다.

---

## 1. 왜 필요한가

commit 메시지를 아무렇게나 쓰면  
나중에 기록을 봤을 때 어떤 변경인지 알아보기 어렵다.

예를 들어 아래 같은 메시지는 좋지 않다.

- asdf
- fix
- 수정
- gg

이런 메시지는 무엇을 수정했는지 알기 어렵다.

반대로 규칙을 정하면  
기록이 정리되고, 작업 목적을 바로 확인할 수 있다.

---

## 2. 기본 형식

보통 아래 형식으로 많이 사용한다.

TYPE: short summary

### example

- FEAT: add login function
- FIX: correct file upload path
- DOCS: update README
- STYLE: format code
- REFACTOR: simplify input logic

---

## 3. 자주 사용하는 TYPE

### FEAT
새로운 기능 추가

example: `FEAT: add user login feature`

### FIX
버그 수정

example: `FIX: correct wrong redirect URL`

### DOCS
문서 수정

example: `DOCS: update git manual`

### STYLE
코드 의미 변화 없이 스타일만 수정  
예: 공백, 줄 정렬, 세미콜론 정리 등

example: `STYLE: format main.c`

### REFACTOR
기능 변화 없이 코드 구조 개선

example: `REFACTOR: simplify file parsing logic`

### CHORE
빌드, 설정, 패키지, 잡다한 작업

example: `CHORE: add .vscode to gitignore`

### TEST
테스트 코드 추가 또는 수정

example: `TEST: add login validation test`

### INIT
초기 세팅

example: `INIT: create project structure`

---

## 4. 작성 규칙 추천

### 1) 첫 단어는 TYPE으로 시작
example: `FEAT: add dark mode toggle`

### 2) 한 줄로 짧고 명확하게 작성
무엇을 했는지 바로 보이게 쓴다.

좋은 예: `FIX: resolve image path error`  
나쁜 예: `FIX: fix something`

### 3) 너무 긴 문장은 피하기
commit 메시지는 설명문이 아니라 작업 요약이다.

### 4) 한 commit에는 한 작업만 담기
기능 추가와 버그 수정을 한 commit에 같이 넣지 않는 것이 좋다.

### 5) 문서 작업은 DOCS, 설정 작업은 CHORE로 구분
README 수정인데 FEAT로 쓰지 않도록 구분한다.

---

## 5. 추천 메시지 예시

### 기능 추가
`FEAT: add multi file upload support`

### 버그 수정
`FIX: prevent null pointer error`

### 문서 수정
`DOCS: add detached head explanation`

### 환경 설정
`CHORE: create .env.example`

### 코드 정리
`REFACTOR: split input handler function`

### 코드 스타일 정리
`STYLE: reformat README headings`

---

## 6. 나쁜 예 / 좋은 예

### bad

- `git commit -m "update"`
- `git commit -m "fix"`
- `git commit -m "123"`
- `git commit -m "수정"`

### good

- `git commit -m "DOCS: add commit message rule"`
- `git commit -m "FIX: correct login redirect bug"`
- `git commit -m "CHORE: add .vscode to gitignore"`

---

## 7. 추천 규칙 예시

팀 또는 개인 프로젝트에서는 아래 정도로 통일하면 충분하다.

- `INIT`     : 초기 세팅
- `FEAT`     : 기능 추가
- `FIX`      : 버그 수정
- `DOCS`     : 문서 수정
- `STYLE`    : 코드 스타일 정리
- `REFACTOR` : 리팩토링
- `TEST`     : 테스트 관련 작업
- `CHORE`    : 설정, 기타 작업

---

## 8. 한 줄 정리

좋은 commit 메시지는  
**무슨 작업을 했는지 짧고 명확하게 바로 보이도록 작성하는 것**이다.