# Git Switch and Checkout

`git switch`와 `git checkout`은 branch를 이동할 때 사용한다.  
최근에는 branch 이동에는 `switch`를 더 많이 쓴다.

---

## 1. 기존 branch로 이동

이미 존재하는 branch로 이동한다.

~~~bash
git switch <branch name>
~~~

### example
~~~bash
git switch main
~~~

---

## 2. 새 branch 생성 후 바로 이동

branch를 만들고 바로 이동한다.

~~~bash
git switch -c <branch name>
~~~

### example
~~~bash
git switch -c feature/login
~~~

---

## 3. checkout으로 branch 이동

예전 방식으로 branch를 이동한다.

~~~bash
git checkout <branch name>
~~~

### example
~~~bash
git checkout dev
~~~

---

## 4. checkout으로 branch 생성 후 이동

~~~bash
git checkout -b <branch name>
~~~

### example
~~~bash
git checkout -b feature/login
~~~

---

## 5. 차이점

### explanation
- `git switch` : branch 이동 목적
- `git checkout` : branch 이동 + 파일 복원 등 여러 용도
- 초보자는 branch 이동에는 `switch`가 더 헷갈림이 적다

---

## 6. 자주 쓰는 방식

~~~bash
git switch main
git switch -c <branch name>
git checkout <branch name>
git checkout -b <branch name>
~~~