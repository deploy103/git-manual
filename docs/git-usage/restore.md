# Git Restore

`git restore`는 수정한 파일을 되돌리거나 staging 된 파일을 해제할 때 사용한다.

---

## 1. working directory 파일 되돌리기

수정했지만 아직 add 하지 않은 파일을 마지막 commit 상태로 되돌린다.

~~~bash
git restore <file name>
~~~

### example
~~~bash
git restore README.md
~~~

### warning
수정 내용이 사라질 수 있다.

---

## 2. staging 해제

`git add` 한 파일을 staging 에서 내린다.

~~~bash
git restore --staged <file name>
~~~

### example
~~~bash
git restore --staged README.md
~~~

---

## 3. 전체 staging 해제

전부 staging 해제한다.

~~~bash
git restore --staged .
~~~

---

## 4. 자주 쓰는 방식

~~~bash
git restore <file name>
git restore --staged <file name>
git restore --staged .
~~~