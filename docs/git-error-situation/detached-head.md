# Detached HEAD

`Detached HEAD` 는 현재 branch 위에 있는 것이 아니라  
특정 commit 자체를 직접 보고 있는 상태를 말한다.

즉, branch 이름이 아니라 commit hash 기준으로 이동한 상태이다.

---

## 1. 언제 발생하나

보통 아래 경우이다.

- 특정 commit으로 직접 checkout 했을 때
- tag를 checkout 했을 때
- 이전 commit 상태를 잠깐 확인하려고 이동했을 때

---

## 2. 대표 예시

~~~bash
git checkout a1b2c3d
~~~

### example message
~~~bash
Note: switching to 'a1b2c3d'.

You are in 'detached HEAD' state.
~~~

---

## 3. 왜 문제가 될 수 있나

이 상태에서도 파일 수정과 commit은 가능하다.  
하지만 branch에 연결된 commit이 아니므로, 나중에 branch로 돌아가면  
방금 만든 commit을 잃어버릴 수 있다.

즉, 작업을 계속할 거면 새 branch를 만들어야 한다.

---

## 4. 현재 상태 확인

~~~bash
git status
git branch
~~~

### example
~~~bash
HEAD detached at a1b2c3d
nothing to commit, working tree clean
~~~

---

## 5. 해결 방법 1: 원래 branch로 돌아가기

잠깐 확인만 한 거라면 원래 branch로 돌아가면 된다.

~~~bash
git switch main
~~~

또는

~~~bash
git checkout main
~~~

---

## 6. 해결 방법 2: 현재 상태에서 새 branch 만들기

이 상태에서 작업을 이어갈 거면 새 branch를 만든다.

~~~bash
git switch -c <branch name>
~~~

### example
~~~bash
git switch -c fix/old-version
~~~

### explanation
현재 commit 위치를 기준으로 새 branch를 만들어서 작업 내용을 안전하게 보관한다.

---

## 7. 자주 쓰는 흐름

### 특정 commit 확인만 할 때
~~~bash
git checkout <commit hash>
git switch main
~~~

### 특정 commit에서 작업 이어갈 때
~~~bash
git checkout <commit hash>
git switch -c <new branch name>
~~~

---

## 8. 한 줄 정리

`Detached HEAD` 는  
**branch가 아니라 특정 commit 위에 직접 올라가 있는 상태**이고,  
작업을 이어갈 거면 새 branch를 만들어야 안전하다.