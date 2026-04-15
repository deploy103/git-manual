# Git Commit

`git commit`은 staging 된 변경사항을 하나의 기록으로 저장할 때 사용한다.

---

## 1. commit 만들기

staging 된 파일들을 commit 한다.

~~~bash
git commit -m "<commit message>"
~~~

### example
~~~bash
git commit -m "FEAT: add login page"
~~~

---

## 2. add와 commit 한 번에 하기

이미 Git이 추적 중인 파일의 수정사항은 `-a` 옵션으로 바로 commit 할 수 있다.

~~~bash
git commit -am "<commit message>"
~~~

### example
~~~bash
git commit -am "FIX: update button style"
~~~

### explanation
새 파일은 `git add`를 먼저 해야 한다.

---

## 3. 마지막 commit 메시지 수정

직전 commit 메시지만 바꾸고 싶을 때 사용한다.

~~~bash
git commit --amend -m "<new message>"
~~~

### example
~~~bash
git commit --amend -m "FEAT: add login API"
~~~

---

## 4. commit만 하고 push 안 된 상태 확인

보통 `git log --oneline`으로 확인한다.

~~~bash
git log --oneline
~~~

---

## 5. 자주 쓰는 방식

~~~bash
git add .
git commit -m "<commit message>"
~~~