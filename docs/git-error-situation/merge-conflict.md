# Merge Conflict

`Merge conflict` 는 branch를 합치는 과정에서  
Git이 어느 내용을 남겨야 할지 자동으로 결정하지 못할 때 발생하는 충돌이다.

---

## 1. 언제 발생하나

보통 아래 상황에서 발생한다.

- `git merge`
- `git pull`
- `git pull --rebase`
- 같은 파일의 같은 부분을 서로 다르게 수정했을 때

---

## 2. 대표 예시

~~~bash
git merge feature/login
Auto-merging app.css
CONFLICT (content): Merge conflict in app.css
Automatic merge failed; fix conflicts and then commit the result.
~~~

---

## 3. 확인 방법

~~~bash
git status
~~~

### example
~~~bash
On branch main
You have unmerged paths.

Unmerged paths:
  both modified:   app.css
~~~

---

## 4. 충돌 파일 안에서 보이는 표시

~~~text
<<<<<<< HEAD
button color: blue
=======
button color: red
>>>>>>> feature/login
~~~

### explanation
- `HEAD` : 현재 branch 내용
- 아래쪽 : 합치려는 branch 내용

이 표시를 보고 직접 원하는 내용으로 수정해야 한다.

---

## 5. 해결 방법

### 1) 파일 열어서 직접 수정
~~~text
button color: blue;
~~~

또는 둘 내용을 합쳐서 새로 정리한다.

### 2) 충돌 표시 삭제
아래 표시는 전부 없어져야 한다.

~~~text
<<<<<<<
=======
>>>>>>>
~~~

### 3) 다시 add 후 commit
~~~bash
git add .
git commit -m "MERGE: resolve conflict"
~~~

---

## 6. merge 자체 취소

해결하지 않고 merge 전 상태로 돌아가려면:

~~~bash
git merge --abort
~~~

---

## 7. rebase 중 conflict일 때

~~~bash
git add .
git rebase --continue
~~~

취소하려면:

~~~bash
git rebase --abort
~~~

---

## 8. 한 줄 정리

`Merge conflict` 는  
**같은 부분을 서로 다르게 수정해서 Git이 자동 병합을 못 하는 상태**이고,  
파일을 직접 수정한 뒤 `git add` 후 다시 진행해야 한다.