# Git Log

`git log`는 commit 기록을 확인하는 명령어이다.  
누가 어떤 메시지로 commit 했는지, 이전 작업 내역이 어떻게 쌓였는지 볼 때 사용한다.

---

## 1. 기본 commit 기록 확인

저장된 commit 기록을 자세히 확인한다.

~~~bash
git log
~~~

---

## 2. 한 줄로 간단하게 확인

commit 기록을 짧게 한 줄씩 확인한다.

~~~bash
git log --oneline
~~~

### example
~~~bash
git log --oneline
a1b2c3d FEAT: add login feature
d4e5f6g FIX: update README
~~~

---

## 3. branch 흐름까지 같이 확인

branch가 어떻게 나뉘고 합쳐졌는지 그래프로 확인한다.

~~~bash
git log --oneline --graph --all
~~~

### example
~~~bash
git log --oneline --graph --all
* a1b2c3d FEAT: add login feature
* d4e5f6g FIX: update README
* 1a2b3c4 INIT: first commit
~~~

---

## 4. 최근 commit만 보기

최근 몇 개만 보고 싶을 때 사용한다.

~~~bash
git log --oneline -5
~~~

---

## 5. 자주 쓰는 방식

~~~bash
git log --oneline
git log --oneline --graph --all
~~~