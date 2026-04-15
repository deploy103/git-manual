# Git Branch

`git branch`는 branch를 확인, 생성, 삭제할 때 사용한다.  
branch는 작업 내용을 분리해서 관리할 때 사용한다.

---

## 1. 현재 branch 확인

현재 어떤 branch에 있는지 확인한다.

~~~bash
git branch
~~~

### example
~~~bash
git branch
* main
  dev
~~~

### explanation
- `*` 이 붙은 branch가 현재 작업 중인 branch이다.

---

## 2. branch 자세히 확인

최근 commit 정보까지 같이 확인한다.

~~~bash
git branch -v
~~~

### example
~~~bash
git branch -v
* main a1b2c3d INIT: first commit
  dev  e4f5g6h FEAT: add page
~~~

---

## 3. 원격 branch까지 전부 확인

로컬과 원격 branch를 같이 확인한다.

~~~bash
git branch -a
~~~

### example
~~~bash
git branch -a
* main
  dev
  remotes/origin/main
  remotes/origin/dev
~~~

---

## 4. 새 branch 생성

새 branch를 만든다.

~~~bash
git branch <branch name>
~~~

### example
~~~bash
git branch feature/login
~~~

### explanation
이 명령은 branch만 만들고 이동하지는 않는다.

---

## 5. branch 삭제

branch를 삭제한다.

~~~bash
git branch -d <branch name>
~~~

### example
~~~bash
git branch -d feature/login
~~~

### explanation
정상적으로 merge 된 branch만 삭제한다.

---

## 6. branch 강제 삭제

merge 여부와 상관없이 강제로 삭제한다.

~~~bash
git branch -D <branch name>
~~~

### warning
작업 내용이 사라질 수 있으므로 주의해서 사용해야 한다.

---

## 7. 자주 쓰는 방식

~~~bash
git branch
git branch -a
git branch <branch name>
git branch -d <branch name>
~~~