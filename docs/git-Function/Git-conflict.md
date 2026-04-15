# Git Conflict

Git conflict는 branch를 합치거나 pull 하는 과정에서  
Git이 어떤 내용을 기준으로 합쳐야 할지 스스로 결정하지 못할 때 발생하는 충돌이다.

보통 같은 파일의 같은 부분을 서로 다르게 수정했을 때 발생한다.

---

## 1. conflict가 발생하는 대표 상황

보통 아래 상황에서 많이 발생한다.

- `git merge` 할 때
- `git pull` 할 때
- `git rebase` 할 때
- 같은 파일의 같은 줄 근처를 서로 다르게 수정했을 때

---

## 2. conflict가 나는 예시

예를 들어 `main` branch와 `feature/login` branch가 있다고 가정한다.

`main`에서는 아래처럼 수정했다.

~~~text
button color: blue
~~~

`feature/login`에서는 같은 부분을 아래처럼 수정했다.

~~~text
button color: red
~~~

이 상태에서 branch를 merge 하면  
Git은 어느 내용을 남겨야 할지 자동으로 판단하지 못할 수 있다.

이럴 때 conflict가 발생한다.

---

## 3. conflict 발생 예시 명령

현재 `main` branch에서 다른 branch를 merge 할 때 발생할 수 있다.

~~~bash
git switch main
git merge feature/login
~~~

### example
~~~bash
Auto-merging app.css
CONFLICT (content): Merge conflict in app.css
Automatic merge failed; fix conflicts and then commit the result.
~~~

---

## 4. conflict가 난 파일 확인

충돌이 발생한 파일은 `git status`로 확인한다.

~~~bash
git status
~~~

### example
~~~bash
On branch main
You have unmerged paths.
  (fix conflicts and run "git commit")

Unmerged paths:
  both modified:   app.css
~~~

---

## 5. conflict 파일 안에서 보이는 표시

충돌이 난 파일을 열면 보통 아래처럼 표시된다.

~~~text
<<<<<<< HEAD
button color: blue
=======
button color: red
>>>>>>> feature/login
~~~

### explanation
- `<<<<<<< HEAD`
  - 현재 branch 내용
- `=======`
  - 내용 구분선
- `>>>>>>> feature/login`
  - 합치려는 branch 내용

즉, 둘 중 무엇을 남길지 직접 정해야 한다.

---

## 6. conflict 해결 방법

충돌 파일을 열고 원하는 내용만 남기도록 직접 수정한다.

### example 1. 현재 branch 내용만 남기기
~~~text
button color: blue
~~~

### example 2. 다른 branch 내용만 남기기
~~~text
button color: red
~~~

### example 3. 둘을 적절히 합쳐서 남기기
~~~text
button color: blue;
hover color: red;
~~~

중요한 점은 아래 표시를 전부 지워야 한다는 것이다.

~~~text
<<<<<<<
=======
>>>>>>>
~~~

---

## 7. conflict 해결 후 해야 하는 일

파일을 직접 수정한 뒤에는 다시 staging 하고 commit 해야 한다.

~~~bash
git add .
git commit -m "MERGE: resolve conflict"
~~~

---

## 8. merge conflict 전체 흐름

~~~bash
git switch main
git merge feature/login
git status
~~~

충돌 파일 수정 후:

~~~bash
git add .
git commit -m "MERGE: resolve conflict"
~~~

---

## 9. pull 하다가 conflict 나는 경우

원격 저장소 내용을 가져오면서 merge 될 때도 conflict가 날 수 있다.

~~~bash
git pull origin main
~~~

이 경우도 해결 방식은 같다.

1. `git status`로 충돌 파일 확인
2. 파일 열어서 직접 수정
3. `git add`
4. `git commit`

---

## 10. rebase 중 conflict 나는 경우

`rebase` 도 conflict가 날 수 있다.

~~~bash
git rebase main
~~~

충돌 해결 후에는 아래처럼 진행한다.

~~~bash
git add .
git rebase --continue
~~~

### 중단하고 원래 상태로 돌아가기
~~~bash
git rebase --abort
~~~

---

## 11. merge 취소하기

conflict가 난 merge 자체를 취소하고 싶으면 아래 명령을 쓴다.

~~~bash
git merge --abort
~~~

### explanation
merge 도중 충돌이 났을 때, 해결하지 않고 merge 전 상태로 돌아간다.

---

## 12. conflict를 줄이는 방법

### 1) 자주 pull 하기
오래 안 가져오면 서로 작업 차이가 커져서 conflict 확률이 올라간다.

~~~bash
git pull origin main
~~~

### 2) 같은 파일을 여러 명이 동시에 크게 수정하지 않기
특히 같은 함수, 같은 CSS, 같은 설정 파일은 충돌이 자주 난다.

### 3) 작업을 너무 오래 끌지 않기
branch를 오래 들고 있으면 merge 시 충돌이 많아진다.

### 4) merge 전에 최신 main 반영하기
~~~bash
git switch main
git pull origin main
git switch feature/login
git merge main
~~~

---

## 13. conflict 났을 때 많이 쓰는 명령

현재 상태 확인:

~~~bash
git status
~~~

충돌 해결 후 staging:

~~~bash
git add .
~~~

merge 완료:

~~~bash
git commit -m "MERGE: resolve conflict"
~~~

merge 취소:

~~~bash
git merge --abort
~~~

rebase 계속:

~~~bash
git rebase --continue
~~~

rebase 취소:

~~~bash
git rebase --abort
~~~

---

## 14. 내가 짧게 쓰는 방식

### merge conflict 해결
~~~bash
git status
git add .
git commit -m "MERGE: resolve conflict"
~~~

### merge 취소
~~~bash
git merge --abort
~~~

### rebase conflict 해결
~~~bash
git add .
git rebase --continue
~~~

---

## 15. 한 줄 정리

Git conflict는  
**같은 부분을 서로 다르게 수정해서 Git이 자동으로 합치지 못하는 상태**이다.

이 경우 파일을 직접 수정하고 `git add` 후 다시 commit 하거나,  
rebase 중이면 `git rebase --continue` 하면 된다.