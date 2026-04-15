# How Git Works

`How Git Works` 는  
Git 이 내부적으로 어떤 흐름으로 파일을 관리하는지 설명하는 문서이다.

Git 을 제대로 이해하려면  
단순히 명령어만 외우는 것보다  
파일이 어떤 단계를 거쳐 commit 되는지 아는 것이 중요하다.

핵심은  
Git 이 파일을 바로 commit 하는 것이 아니라  
몇 단계를 거쳐서 기록한다는 점이다.

---

## 1. Git 의 기본 흐름

Git 은 보통 아래 순서로 동작한다.

1. 파일을 수정한다.  
2. 수정한 파일을 staging area 에 올린다.  
3. staging 된 내용을 commit 으로 저장한다.  
4. 필요하면 원격 저장소에 push 한다.  

즉, Git 은  
**수정 → 준비 → 기록 → 공유** 흐름으로 관리된다고 보면 된다.

---

## 2. Git 이 관리하는 3가지 영역

Git 을 이해할 때 가장 중요한 개념은  
아래 3가지 영역이다.

- Working Directory
- Staging Area
- Repository

---

## 3. Working Directory 란

`Working Directory` 는  
내가 실제로 파일을 수정하고 있는 현재 작업 공간이다.

예를 들어  
코드를 열어서 내용을 바꾸거나  
문서를 수정하는 곳이 바로 여기에 해당한다.

즉, 지금 눈에 보이는 프로젝트 폴더의 파일 상태라고 보면 된다.

---

## 4. Staging Area 란

`Staging Area` 는  
다음 commit 에 넣을 파일을 미리 골라 두는 공간이다.

Git 은  
수정했다고 바로 commit 하지 않는다.

먼저 `git add` 로  
"이 파일들을 다음 commit 에 포함하겠다" 라고 올려 둔다.

이 준비 공간이 staging area 이다.

즉, staging area 는  
**commit 직전 대기실** 같은 개념이다.

---

## 5. Repository 란

`Repository` 는  
commit 기록이 실제로 저장되는 공간이다.

`git commit` 을 하면  
staging area 에 있던 내용이  
하나의 commit 으로 저장소에 기록된다.

즉, repository 는  
프로젝트의 이력 데이터베이스 같은 역할을 한다.

---

## 6. 한 번에 이해하는 예시

예를 들어 `main.c` 를 수정했다고 하자.

### 1) 파일 수정
이 상태는 `Working Directory` 에만 반영된다.

### 2) `git add main.c`
이제 `main.c` 는 `Staging Area` 로 올라간다.

### 3) `git commit -m "FIX: correct input logic"`
이제 staging 된 `main.c` 상태가 `Repository` 에 commit 으로 저장된다.

즉, 흐름은 아래와 같다.

`Working Directory` → `Staging Area` → `Repository`

---

## 7. 왜 staging area 가 필요한가

처음에는  
왜 그냥 바로 commit 하지 않고  
중간 단계를 두는지 헷갈릴 수 있다.

이유는  
수정한 파일 중에서  
**어떤 것만 commit 할지 직접 고를 수 있어야 하기 때문**이다.

예를 들어 아래처럼 작업했다고 하자.

- `main.c` : 버그 수정
- `README.md` : 문서 정리
- `test.c` : 실험 파일

이때 모든 파일을 한꺼번에 commit 하고 싶지 않을 수 있다.

먼저 필요한 파일만 `git add` 해서  
정확한 commit 을 만들 수 있다.

---

## 8. Git 상태 확인

Git 은 현재 파일이 어느 단계에 있는지  
`git status` 로 보여준다.

보통 아래와 같이 나온다.

- 수정만 된 파일
- staging 된 파일
- 추적되지 않는 새 파일
- commit 할 내용이 없는 상태

즉, `git status` 는  
지금 Git 상태를 보는 가장 기본적인 명령어이다.

---

## 9. tracked 와 untracked

Git 은 파일을  
추적하는 파일과 추적하지 않는 파일로 나눈다.

### tracked
이미 Git 이 알고 있는 파일

### untracked
새로 만들었지만 아직 Git 에 추가하지 않은 파일

예를 들어 새 파일을 만들면  
처음에는 untracked 상태이다.

여기서 `git add` 를 하면  
이제 Git 이 그 파일을 추적하기 시작한다.

---

## 10. commit 은 스냅샷에 가깝다

Git commit 은  
파일 하나만 따로 저장하는 느낌보다  
**그 시점의 프로젝트 상태를 기록하는 스냅샷** 에 가깝다.

즉, commit 을 쌓아 간다는 것은  
프로젝트의 중요한 시점들을 차례대로 저장하는 것이라고 보면 된다.

---

## 11. HEAD 란

`HEAD` 는  
현재 내가 보고 있는 commit 위치를 가리키는 포인터라고 보면 된다.

보통은 현재 branch 의 최신 commit 을 가리킨다.

예를 들어 `main` branch 에 있으면  
HEAD 는 `main` 의 최신 commit 을 가리킨다.

그래서 commit 을 새로 만들면  
HEAD 도 같이 앞으로 이동한다.

---

## 12. branch 는 commit 흐름의 이름표

branch 는 별도의 폴더나 파일 복사본이 아니라  
사실상 **특정 commit 흐름을 가리키는 이름표** 에 가깝다.

예를 들어 `main` 과 `feat/login` 은  
각자 다른 commit 흐름을 가리킬 수 있다.

그래서 branch 를 바꾸면  
Git 이 그 branch 가 가리키는 상태로 작업 파일을 바꿔 준다.

---

## 13. remote 는 별도 저장소이다

Git 은 원래 로컬에서 동작한다.

여기에 GitHub 같은 원격 저장소를 연결하면  
로컬 commit 을 원격으로 올릴 수 있다.

즉,

- 로컬 저장소 : 내 컴퓨터에 있는 Git 저장소
- 원격 저장소 : GitHub 등에 있는 Git 저장소

이 둘은 연결되어 있지만  
같은 것은 아니다.

---

## 14. 자주 보는 흐름

### 파일 수정
Working Directory 변경

### `git add`
Staging Area 로 올림

### `git commit`
Repository 에 기록

### `git push`
원격 저장소로 공유

### `git pull`
원격 저장소 최신 내용을 로컬로 가져옴

---

## 15. 한 줄 정리

Git 은  
**작업 파일을 바로 저장하지 않고, Working Directory → Staging Area → Repository 흐름으로 단계적으로 기록하는 시스템**이다.