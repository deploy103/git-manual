# Git Workflow

`Git Workflow` 는  
Git 을 사용할 때 보통 어떤 순서로 작업이 진행되는지 설명하는 문서이다.

Git 명령어는 많지만  
실제로 자주 쓰는 흐름은 어느 정도 정해져 있다.

핵심은  
파일을 수정하고, 필요한 것만 기록하고,  
필요하면 원격 저장소에 공유하는 순서를 이해하는 것이다.

---

## 1. 가장 기본적인 흐름

가장 기본적인 Git 작업 흐름은 아래와 같다.

1. 파일 수정  
2. 상태 확인  
3. add  
4. commit  
5. push  

즉, 보통은 아래 순서로 생각하면 된다.

`edit → status → add → commit → push`

---

## 2. 단계별 설명

### 1) 파일 수정
코드나 문서를 수정한다.

예:
- 버그 수정
- 기능 추가
- README 정리

### 2) 상태 확인
무슨 파일이 바뀌었는지 확인한다.

example:
`git status`

### 3) add
다음 commit 에 넣을 파일을 고른다.

example:
`git add .`

또는

`git add main.c`

### 4) commit
변경 사항을 기록으로 남긴다.

example:
`git commit -m "FIX: correct input logic"`

### 5) push
로컬 commit 을 원격 저장소에 올린다.

example:
`git push origin main`

---

## 3. 왜 status 를 자주 봐야 하나

Git 을 쓸 때  
`git status` 는 거의 습관처럼 자주 보는 것이 좋다.

이유는 아래와 같다.

- 어떤 파일이 수정되었는지 확인 가능
- staging 된 파일 확인 가능
- 실수로 포함된 파일 확인 가능
- 현재 branch 상태 확인 가능

즉, status 는  
지금 Git 상황을 빠르게 보여 주는 기본 명령어이다.

---

## 4. add 의 역할

`git add` 는  
"이 파일을 다음 commit 에 포함하겠다" 라는 의미이다.

처음에는 add 와 commit 이 비슷해 보이지만 다르다.

- `git add` : commit 에 넣을 준비
- `git commit` : 실제 기록 저장

즉, add 는 준비이고  
commit 은 저장이다.

---

## 5. commit 의 역할

`git commit` 은  
현재 staging area 에 있는 내용을  
하나의 기록으로 저장하는 작업이다.

좋은 commit 은  
한 작업 단위로 묶여 있어야 보기 좋다.

예를 들어

- 로그인 기능 추가
- 이미지 경로 오류 수정
- README 문서 정리

이런 식으로 작업 단위별 commit 이 좋다.

---

## 6. push 의 역할

`git push` 는  
내 로컬 저장소에 있는 commit 을  
원격 저장소에 올리는 명령어이다.

즉, commit 까지는 내 컴퓨터 안에서 끝나고  
push 를 해야 GitHub 같은 곳에 반영된다.

---

## 7. 기본 예시 흐름

예를 들어 로그인 페이지를 추가한다고 하자.

### 1) 파일 수정
- `login.html`
- `login.css`

### 2) 상태 확인
`git status`

### 3) add
`git add .`

### 4) commit
`git commit -m "FEAT: add login page"`

### 5) push
`git push origin feat/login`

이렇게 하면  
작업이 Git 기록과 원격 저장소에 반영된다.

---

## 8. 작업 시작 전 자주 하는 흐름

작업을 시작하기 전에는  
최신 상태를 먼저 받는 것이 좋다.

보통 아래처럼 한다.

`git switch main`  
`git pull origin main`

그 다음 작업용 branch 를 만든다.

`git switch -c feat/login`

즉, 협업에서는  
작업 전에 최신 상태를 맞추는 것이 중요하다.

---

## 9. 작업 중 자주 반복되는 흐름

실제로 작업 중에는  
아래 흐름이 반복된다.

1. 파일 수정  
2. `git status`  
3. `git add`  
4. `git commit`  

필요할 때만 `git push` 를 한다.

즉, Git 작업은  
작은 수정과 commit 이 계속 이어지는 구조이다.

---

## 10. 작업 완료 후 흐름

작업이 끝나면  
보통 아래처럼 마무리한다.

1. commit 정리  
2. 원격 저장소에 push  
3. Pull Request 생성  
4. merge  
5. 작업 branch 삭제  

개인 프로젝트면 PR 없이 바로 merge 할 수도 있지만  
협업에서는 PR 흐름이 일반적이다.

---

## 11. 잘못된 흐름 예시

아래 같은 흐름은 좋지 않다.

- 수정만 잔뜩 하고 commit 안 함
- 무슨 파일이 바뀌었는지 확인 안 함
- 의미 없는 commit 메시지 사용
- `main` 에서 바로 작업 후 push
- 여러 작업을 한 commit 에 몰아넣음

이렇게 하면  
기록이 지저분해지고 관리가 어려워진다.

---

## 12. 좋은 흐름 예시

아래처럼 하면 깔끔하다.

- 작업 전에 최신 상태 pull
- 새 작업은 branch 생성 후 진행
- 한 작업 단위로 commit
- push 전에 status 확인
- 작업 완료 후 merge

---

## 13. 협업 기준 기본 흐름

협업에서는 보통 이렇게 간다.

1. 최신 `main` 받기  
2. 새 branch 생성  
3. 작업  
4. commit  
5. push  
6. Pull Request  
7. 리뷰  
8. merge  

즉, 로컬 작업만 잘하는 것이 아니라  
다른 사람과 연결되는 흐름까지 포함해서 보는 것이 중요하다.

---

## 14. 한 줄 정리

Git workflow 는  
**파일 수정 후 상태를 확인하고, 필요한 내용만 add 해서 commit 하고, 최종적으로 원격 저장소에 공유하는 반복 작업 흐름**이다.