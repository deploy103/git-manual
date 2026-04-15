# Git Reset and Revert

`git reset`과 `git revert`는 commit을 되돌릴 때 사용한다.  
둘은 동작 방식이 다르므로 구분해서 써야 한다.

---

## 1. reset --soft

최근 commit만 취소하고, 변경 내용은 staging 상태로 남긴다.

~~~bash
git reset --soft HEAD~1
~~~

### explanation
- commit만 취소
- 파일 수정 내용은 그대로 남음
- 다시 commit 메시지 바꿔서 commit 할 때 자주 사용

---

## 2. reset --mixed

최근 commit을 취소하고, 변경 내용은 working directory에 남긴다.

~~~bash
git reset HEAD~1
~~~

### explanation
- 기본 reset 방식
- add 상태도 같이 풀림

---

## 3. reset --hard

최근 commit과 수정 내용까지 전부 되돌린다.

~~~bash
git reset --hard HEAD~1
~~~

### warning
이 명령은 작업 내용을 날릴 수 있으므로 주의해서 사용해야 한다.

---

## 4. revert

특정 commit을 취소하는 새로운 commit을 만든다.

~~~bash
git revert <commit hash>
~~~

### example
~~~bash
git revert a1b2c3d
~~~

### explanation
- 기존 기록을 지우지 않음
- 협업 중에는 `reset`보다 `revert`가 더 안전한 경우가 많음

---

## 5. 자주 쓰는 방식

### 마지막 commit 메시지만 잘못 넣었을 때
~~~bash
git reset --soft HEAD~1
git commit -m "new message"
~~~

### 이미 push한 commit을 안전하게 취소할 때
~~~bash
git revert <commit hash>
~~~