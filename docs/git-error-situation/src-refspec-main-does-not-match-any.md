# src refspec main does not match any

`error: src refspec main does not match any` 는  
보통 push 하려는 branch 이름이 실제로 존재하지 않거나, 아직 commit이 하나도 없을 때 발생한다.

---

## 1. 대표 예시

~~~bash
git push -u origin main
error: src refspec main does not match any
~~~

---

## 2. 언제 발생하나

보통 아래 경우이다.

- 아직 첫 commit을 안 한 상태
- 현재 branch 이름이 `main` 이 아닌데 `main` 으로 push 한 경우
- branch 이름을 잘못 입력한 경우

---

## 3. 먼저 확인할 것

### 현재 branch 확인
~~~bash
git branch
~~~

### commit 존재 여부 확인
~~~bash
git log --oneline
~~~

### 상태 확인
~~~bash
git status
~~~

---

## 4. 가장 흔한 원인 1: commit이 없음

Git은 commit이 하나도 없으면 push 할 branch 기록 자체가 없다.

### 해결
~~~bash
git add .
git commit -m "INIT: first commit"
git branch -M main
git push -u origin main
~~~

---

## 5. 가장 흔한 원인 2: branch 이름이 다름

예를 들어 현재 branch가 `master` 인데 `main` 으로 push 하면 에러가 난다.

### 확인
~~~bash
git branch
~~~

### 해결 방법 1. 현재 branch 이름에 맞춰 push
~~~bash
git push -u origin master
~~~

### 해결 방법 2. branch 이름을 main으로 변경
~~~bash
git branch -M main
git push -u origin main
~~~

---

## 6. 자주 쓰는 해결 흐름

~~~bash
git status
git branch
git add .
git commit -m "INIT: first commit"
git branch -M main
git push -u origin main
~~~

---

## 7. 한 줄 정리

이 에러는  
**push 하려는 branch가 실제로 없거나, 아직 commit이 없어서 Git이 올릴 대상을 못 찾는 상태**이다.