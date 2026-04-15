# Git Diff

`git diff`는 파일이 어떻게 바뀌었는지 비교할 때 사용한다.

---

## 1. 수정된 내용 확인

아직 staging 하지 않은 변경사항을 확인한다.

~~~bash
git diff
~~~

---

## 2. staging 된 내용 확인

`git add`까지 한 변경사항을 확인한다.

~~~bash
git diff --staged
~~~

---

## 3. 특정 파일만 확인

원하는 파일만 비교해서 볼 수 있다.

~~~bash
git diff README.md
~~~

---

## 4. branch 간 비교

서로 다른 branch의 차이를 확인한다.

~~~bash
git diff main feature/login
~~~

---

## 5. 자주 쓰는 방식

~~~bash
git diff
git diff --staged
~~~