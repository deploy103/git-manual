# Git Remove and Move

`git rm`은 파일 삭제를 Git에 반영할 때 사용하고, `git mv`는 파일 이름 변경이나 이동을 Git에 반영할 때 사용한다.

---

## 1. 파일 삭제

파일을 삭제하고 Git에도 반영한다.

~~~bash
git rm <file name>
~~~

### example
~~~bash
git rm test.txt
~~~

---

## 2. 폴더 삭제

폴더를 Git에서 제거한다.

~~~bash
git rm -r <directory name>
~~~

### example
~~~bash
git rm -r src/
~~~

---

## 3. 파일 이름 변경

파일 이름을 바꾸고 Git에 반영한다.

~~~bash
git mv <old name> <new name>
~~~

### example
~~~bash
git mv app.txt main.txt
~~~

---

## 4. 파일 이동

다른 폴더로 이동할 수도 있다.

~~~bash
git mv app.py src/app.py
~~~

---

## 5. 자주 쓰는 방식

~~~bash
git rm <file name>
git mv <old name> <new name>
git commit -m "CHORE: remove and rename files"
~~~