# Git Add

`git add`는 파일의 변경사항을 staging area에 올릴 때 사용한다.  
commit 하기 전에 먼저 add 해야 한다.

---

## 1. 특정 파일 add

원하는 파일 하나만 staging 한다.

~~~bash
git add <file name>
~~~

### example
~~~bash
git add README.md
~~~

---

## 2. 현재 폴더 전체 add

현재 폴더 기준으로 변경사항을 전부 staging 한다.

~~~bash
git add .
~~~

---

## 3. 모든 변경사항 add

삭제된 파일까지 포함해서 전부 staging 한다.

~~~bash
git add -A
~~~

### explanation
- 수정
- 새 파일
- 삭제된 파일  
전부 포함한다.

---

## 4. staging 확인

어떤 파일이 add 되었는지 확인한다.

~~~bash
git status
~~~

---

## 5. 자주 쓰는 방식

~~~bash
git add .
git status
git commit -m "<commit message>"
~~~