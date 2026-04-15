# Pull Rule

`Pull Rule` 은  
원격 저장소의 변경 내용을 로컬 저장소로 가져올 때  
어떤 기준으로 pull 할지 정해두는 규칙이다.

`git pull` 은 자주 쓰는 명령어지만  
작업 중인 파일이 있는 상태에서 무작정 실행하면  
충돌이 나거나 작업 흐름이 꼬일 수 있다.

그래서 pull 전 확인 습관이 중요하다.

---

## 1. 왜 필요한가

pull 은  
원격 저장소의 최신 내용을 내 로컬에 반영하는 작업이다.

그런데 아무 때나 pull 하면  
아래 같은 문제가 생길 수 있다.

- 작업 중인 파일과 충돌 발생
- 아직 commit 안 한 변경 내용이 꼬임
- 어떤 branch 를 pull 했는지 헷갈림
- 필요 없는 merge commit 생성
- 로컬 작업이 정리되지 않은 상태로 섞임

그래서 pull 전에 상태를 먼저 확인하는 것이 좋다.

---

## 2. 기본 원칙

pull 하기 전에는  
아래 내용을 먼저 확인하는 것을 추천한다.

- 현재 branch 가 맞는지 확인
- 작업 중인 변경 파일이 있는지 확인
- commit 이 필요한 상태인지 확인
- pull 대상 원격 branch 가 맞는지 확인

---

## 3. pull 전 확인할 것

### 1) 현재 branch 확인
example:
`git branch`

### 2) 변경 상태 확인
example:
`git status`

### 3) commit 여부 확인
작업 중인 내용이 있으면  
먼저 commit 하거나 stash 하는 것이 좋다.

example:
`git log --oneline`

### 4) 원격 저장소 확인
example:
`git remote -v`

---

## 4. 기본 pull 명령어

가장 기본적인 pull 은 아래처럼 사용한다.

`git pull origin <branch name>`

### example

- `git pull origin main`
- `git pull origin develop`

upstream 이 연결되어 있으면  
그냥 아래처럼 써도 된다.

`git pull`

---

## 5. 추천 pull 방식

### 1) 작업 중인 파일이 없을 때 pull
가장 안전하다.

### 2) 작업 중이면 먼저 commit 후 pull
로컬 변경 내용을 먼저 정리하고 pull 하는 것이 좋다.

example:
`git add .`  
`git commit -m "WIP: save current work"`  
`git pull origin main`

### 3) 잠깐 치워둘 때 stash 사용
아직 commit 하기 애매하면 stash 를 쓸 수 있다.

example:
`git stash`  
`git pull origin main`  
`git stash pop`

---

## 6. 작성 규칙 추천

### 1) 작업 중인데 무작정 pull 하지 않기
변경 파일이 있으면  
먼저 `git status` 로 확인한다.

### 2) 현재 branch 확인 후 pull
`main` 인 줄 알았는데 다른 branch 인 경우가 있다.

### 3) 가능하면 자주 pull 해서 차이를 줄이기
오랫동안 pull 안 하면  
충돌 가능성이 커진다.

### 4) 협업 중이면 작업 시작 전 pull
작업 시작 전에 최신 상태를 받아 두는 것이 좋다.

### 5) 충돌이 나면 직접 확인 후 해결
충돌 메시지가 뜨면  
파일을 열어서 어떤 내용을 남길지 확인해야 한다.

---

## 7. 자주 쓰는 흐름

### 작업 시작 전에 최신 내용 받기

`git switch main`  
`git pull origin main`

### 작업 branch 에 최신 main 반영하기

`git switch main`  
`git pull origin main`  
`git switch feat/login`  
`git merge main`

### 작업 중 stash 후 pull 하기

`git stash`  
`git pull origin main`  
`git stash pop`

---

## 8. 충돌이 났을 때

충돌이 나면  
해당 파일을 직접 수정해서 정리한 뒤  
다시 add 와 commit 을 진행한다.

기본 흐름:

`git status`  
충돌 파일 수정  
`git add .`  
`git commit`

---

## 9. 나쁜 예 / 좋은 예

### bad

- 수정 중인데 바로 pull
- 현재 branch 확인 없이 pull
- 충돌 내용을 확인 안 하고 넘김
- 너무 오래 pull 안 해서 한꺼번에 반영
- 무엇을 pull 했는지 모르고 진행

### good

- pull 전에 `git status` 확인
- 작업 시작 전에 최신 내용 pull
- 작업 중이면 commit 또는 stash 후 pull
- 충돌 시 직접 확인 후 해결
- branch 확인 후 정확히 pull

---

## 10. 한 줄 정리

좋은 pull 습관은  
**현재 상태를 먼저 확인하고, 로컬 작업을 정리한 뒤 최신 내용을 안전하게 반영하는 것**이다.