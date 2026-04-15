# Push Rule

`Push Rule` 은  
로컬에서 작업한 내용을 원격 저장소에 올릴 때  
어떤 순서와 기준으로 push 할지 정해두는 규칙이다.

무작정 push 하면  
정리되지 않은 commit 이 올라가거나  
잘못된 branch 에 작업 내용이 올라갈 수 있다.

따라서 push 전에는  
현재 branch, 변경 내용, commit 상태를 먼저 확인하는 습관이 중요하다.

---

## 1. 왜 필요한가

push 는  
내 로컬 작업 내용을 원격 저장소에 반영하는 작업이다.

즉, 한 번 올리면  
협업 중인 다른 사람도 그 내용을 보게 될 수 있다.

그런데 확인 없이 push 하면 아래 같은 문제가 생길 수 있다.

- 잘못된 branch 에 push
- 필요 없는 파일까지 push
- commit 메시지가 정리되지 않은 상태로 push
- 테스트 안 된 코드 push
- 민감한 파일 push

그래서 push 하기 전 확인 규칙을 정해두는 것이 좋다.

---

## 2. 기본 원칙

push 하기 전에는  
아래 내용을 먼저 확인하는 것을 추천한다.

- 현재 branch 가 맞는지 확인
- 변경 파일이 맞는지 확인
- commit 메시지가 정리되었는지 확인
- push 대상 원격 저장소가 맞는지 확인

---

## 3. push 전 확인할 것

### 1) 현재 branch 확인
어느 branch 에 있는지 먼저 확인한다.

example:
`git branch`

현재 작업 branch 에 `*` 표시가 붙는다.

### 2) 변경 상태 확인
수정된 파일과 staging 상태를 확인한다.

example:
`git status`

### 3) commit 기록 확인
어떤 commit 을 push 하게 되는지 확인한다.

example:
`git log --oneline`

### 4) 원격 저장소 확인
어느 원격 저장소로 push 되는지 확인한다.

example:
`git remote -v`

---

## 4. 기본 push 명령어

가장 기본적인 push 는 아래처럼 사용한다.

`git push origin <branch name>`

### example

- `git push origin main`
- `git push origin feat/login`
- `git push origin docs/git-manual`

---

## 5. 처음 push 할 때

새 branch 를 처음 push 할 때는  
upstream 을 같이 연결하는 것이 편하다.

`git push -u origin <branch name>`

### example

`git push -u origin feat/login`

이후에는  
같은 branch 에서 그냥 `git push` 만 써도 된다.

---

## 6. 추천 push 순서

push 는 아래 순서대로 하는 것이 안전하다.

### recommended flow

1. 현재 branch 확인  
2. 변경 파일 확인  
3. add 진행  
4. commit 진행  
5. commit 기록 확인  
6. 원격 저장소 확인  
7. push 진행  

---

## 7. 자주 쓰는 명령어

### 현재 상태 확인
`git status`

### 현재 branch 확인
`git branch`

### commit 기록 확인
`git log --oneline`

### 원격 저장소 확인
`git remote -v`

### push 진행
`git push origin <branch name>`

### 처음 push 할 때 upstream 설정 포함
`git push -u origin <branch name>`

---

## 8. push 할 때 주의할 점

### 1) main 에 바로 push 하지 않기
가능하면 작업용 branch 에 먼저 push 하는 것이 좋다.

좋은 예:
- `feat/login`
- `fix/image-path`
- `docs/gitignore-rule`

### 2) add . 하기 전에 파일 확인하기
불필요한 파일까지 같이 올라갈 수 있으므로  
`git status` 로 먼저 확인하는 것이 좋다.

### 3) `.env` 같은 민감한 파일 확인하기
실수로 push 하면 안 되는 파일은  
반드시 `.gitignore` 로 제외해야 한다.

### 4) commit 없이 push 는 안 됨
push 는 commit 된 내용만 올라간다.  
수정만 해둔 파일은 push 되지 않는다.

### 5) 협업 중이면 push 전에 pull 확인하기
원격 저장소가 더 최신일 수도 있으므로  
충돌 가능성이 있으면 먼저 pull 상태를 확인한다.

---

## 9. 나쁜 예 / 좋은 예

### bad

- branch 확인 없이 바로 push
- `main` 에서 바로 작업 후 push
- `.env` 파일까지 같이 push
- commit 메시지가 `fix`, `update` 같은 상태로 push
- 무슨 파일이 올라가는지 확인 안 하고 push

### good

- `git status` 로 변경 파일 먼저 확인
- `git branch` 로 현재 branch 확인
- 작업용 branch 에 push
- commit 메시지 정리 후 push
- 원격 저장소 확인 후 정확한 branch 로 push

---

## 10. 예시 흐름

### 작업 branch 에 push 할 때

`git status`  
`git branch`  
`git add .`  
`git commit -m "FEAT: add login page"`  
`git push -u origin feat/login`

### 문서 작업 push 할 때

`git status`  
`git add .`  
`git commit -m "DOCS: add push rule"`  
`git push -u origin docs/push-rule`

---

## 11. 한 줄 정리

좋은 push 습관은  
**현재 branch 와 변경 내용을 먼저 확인한 뒤, 정리된 commit 만 올리는 것**이다.