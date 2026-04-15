# Merge Rule

`Merge Rule` 은  
작업이 끝난 branch 를 다른 branch 에 합칠 때  
어떤 기준으로 merge 할지 정해두는 규칙이다.

merge 는 단순히 branch 를 합치는 작업이지만  
기준 없이 진행하면  
불필요한 commit 이 섞이거나,  
안정적이지 않은 코드가 `main` 에 들어갈 수 있다.

따라서 merge 전 확인 기준을 정해두는 것이 좋다.

---

## 1. 왜 필요한가

merge 를 아무 기준 없이 하면  
아래 같은 문제가 생길 수 있다.

- 작업이 끝나지 않은 branch 가 합쳐짐
- commit 기록이 지저분해짐
- 충돌을 제대로 해결하지 않고 merge 함
- 검토되지 않은 내용이 `main` 에 들어감
- 여러 작업이 한꺼번에 섞여 들어감

그래서 merge 전 확인 규칙을 정하면  
저장소를 더 안정적으로 관리할 수 있다.

---

## 2. 기본 원칙

merge 는  
**작업이 끝났고, 내용이 확인된 branch 만 진행**하는 것이 좋다.

보통 아래를 먼저 확인한다.

- 작업이 완료되었는지
- commit 이 정리되었는지
- 불필요한 파일이 없는지
- 충돌이 해결되었는지
- merge 대상 branch 가 맞는지

---

## 3. merge 전 확인할 것

### 1) 현재 branch 확인
merge 하기 전에  
어느 branch 에 있는지 먼저 확인한다.

example:
`git branch`

### 2) 작업 내용 확인
변경 파일과 commit 내용을 확인한다.

example:
`git status`  
`git log --oneline`

### 3) 원격 branch 최신 상태 확인
merge 전에 최신 내용을 먼저 반영하는 것이 좋다.

example:
`git pull origin main`

### 4) Pull Request 또는 리뷰 여부 확인
협업이면 가능하면  
리뷰 후 merge 하는 것이 좋다.

---

## 4. 기본 merge 명령어

가장 기본적인 merge 는 아래처럼 사용한다.

`git merge <branch name>`

### example

`git merge feat/login`

이 명령은  
현재 branch 에 `feat/login` 내용을 합친다.

즉, 보통 `main` 에서 아래처럼 사용한다.

`git switch main`  
`git merge feat/login`

---

## 5. 추천 merge 방식

### 1) 일반 merge
branch 기록을 그대로 유지하면서 합친다.

example:
`git merge feat/login`

### 2) squash merge
작업 branch 의 여러 commit 을  
하나의 commit 으로 합치고 싶을 때 사용한다.

example:
`git merge --squash feat/login`

문서 수정이나 작은 작업은  
squash merge 도 괜찮다.

---

## 6. 작성 규칙 추천

### 1) 작업이 끝난 branch 만 merge
미완성 기능은 merge 하지 않는 것이 좋다.

### 2) 한 branch 는 한 작업만 포함
여러 작업이 섞여 있으면  
merge 후 관리가 어려워진다.

### 3) 가능하면 `main` 에 직접 작업하지 않기
작업은 별도 branch 에서 하고  
검토 후 `main` 에 merge 하는 흐름이 좋다.

### 4) 충돌은 확인 후 직접 해결
충돌이 났을 때는  
기계적으로 처리하지 말고  
어떤 코드가 남아야 하는지 확인해야 한다.

### 5) merge 후 불필요한 작업 branch 정리
작업이 끝난 branch 는 삭제해서  
저장소를 깔끔하게 유지하는 것이 좋다.

---

## 7. 자주 쓰는 흐름

### 작업 branch 를 main 에 합칠 때

`git switch main`  
`git pull origin main`  
`git merge feat/login`  
`git push origin main`

### squash merge 할 때

`git switch main`  
`git pull origin main`  
`git merge --squash docs/git-manual`  
`git commit -m "DOCS: merge git manual update"`  
`git push origin main`

---

## 8. merge 후 branch 정리

로컬 branch 삭제:

`git branch -d feat/login`

원격 branch 삭제:

`git push origin --delete feat/login`

---

## 9. 나쁜 예 / 좋은 예

### bad

- 작업 중인 branch 를 바로 merge
- 확인 없이 `main` 에 merge
- 충돌을 대충 해결하고 merge
- 기능 추가와 문서 수정이 섞인 branch 를 merge
- merge 후 오래된 branch 를 그대로 방치

### good

- 작업 완료 후 merge
- merge 전 status 와 log 확인
- 필요하면 리뷰 후 merge
- 한 branch 에 한 작업만 담기
- merge 후 작업 branch 정리

---

## 10. 한 줄 정리

좋은 merge 규칙은  
**작업이 완료되고 확인된 branch 만 안전하게 합쳐서 `main` 을 안정적으로 유지하는 것**이다.