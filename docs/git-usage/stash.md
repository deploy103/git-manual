 # Git Stash

`git stash`는 현재 작업 중이던 내용을 잠깐 치워두고 다른 작업을 해야 할 때 사용한다.

---

## 1. 현재 작업 임시 저장

수정 중인 내용을 stash에 저장한다.

~~~bash
git stash
~~~

---

## 2. stash 목록 확인

저장된 stash 목록을 확인한다.

~~~bash
git stash list
~~~

### example
~~~bash
git stash list
stash@{0}: WIP on main: a1b2c3d update README
~~~

---

## 3. 최근 stash 다시 적용

가장 최근 stash를 적용하고 stash 목록에서 제거한다.

~~~bash
git stash pop
~~~

---

## 4. stash 적용만 하기

적용만 하고 목록에서는 지우지 않는다.

~~~bash
git stash apply
~~~

---

## 5. stash 삭제

특정 stash를 삭제한다.

~~~bash
git stash drop stash@{0}
~~~

---

## 6. 자주 쓰는 방식

~~~bash
git stash
git switch main
git stash pop
~~~