# Git Init

`git init`은 현재 폴더를 Git 저장소로 만들 때 사용한다.

---

## 1. Git 저장소 초기화

현재 폴더를 Git repository로 만든다.

~~~bash
git init
~~~

### example
~~~bash
git init
Initialized empty Git repository in /home/user/project/.git/
~~~

---

## 2. 기본 branch 이름 지정

초기화 후 기본 branch 이름을 `main`으로 맞춘다.

~~~bash
git branch -M main
~~~

---

## 3. 저장소 초기화 후 첫 업로드 흐름

~~~bash
git init
git add .
git commit -m "INIT: first commit"
git branch -M main
git remote add origin <repository URL>
git push -u origin main
~~~

---

## 4. 자주 쓰는 방식

~~~bash
git init
git branch -M main
~~~