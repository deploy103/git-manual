# Git Merge

`git merge`는 다른 branch의 작업 내용을 현재 branch에 합칠 때 사용한다.

---

## 1. branch 합치기

현재 branch에서 다른 branch의 내용을 합친다.

~~~bash
git merge <branch name>
~~~

### example
~~~bash
git merge feature/login
~~~

### explanation
- 현재 내가 `main` branch에 있다면
- `feature/login`의 작업 내용을 `main`에 합침

---

## 2. merge 전 확인

어느 branch에 있는지 먼저 확인하는 것이 좋다.

~~~bash
git branch
~~~

---

## 3. 충돌이 나는 경우

같은 파일의 같은 부분을 서로 다르게 수정했다면 conflict가 날 수 있다.

~~~bash
git merge feature/login
~~~

### explanation
- conflict가 나면 파일을 직접 수정해야 함
- 수정 후 다시 add 하고 commit 하면 됨

~~~bash
git add .
git commit -m "MERGE: resolve conflict"
~~~

---

## 4. 자주 쓰는 흐름

~~~bash
git switch main
git pull origin main
git merge feature/login
git push origin main
~~~