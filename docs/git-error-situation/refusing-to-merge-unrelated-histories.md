# refusing to merge unrelated histories

`refusing to merge unrelated histories` 는  
서로 관련 없는 Git 기록 두 개를 합치려고 할 때 발생하는 에러이다.

즉, Git이 보기에 두 저장소의 시작점이 완전히 다르다는 뜻이다.

---

## 1. 대표 예시

~~~bash
git pull origin main
fatal: refusing to merge unrelated histories
~~~

---

## 2. 언제 발생하나

보통 아래 경우이다.

- 로컬에서 `git init` 후 작업했고, 원격 저장소에도 별도 commit이 이미 있음
- GitHub에서 README를 만들어둔 저장소에 로컬 프로젝트를 나중에 연결함
- 서로 다른 두 저장소를 억지로 합치려 함

---

## 3. 왜 발생하나

Git은 보통 같은 뿌리에서 갈라진 commit 기록만 자연스럽게 합친다.  
그런데 로컬과 원격이 처음부터 완전히 다른 이력이라면 자동 merge를 거부한다.

---

## 4. 먼저 확인할 것

~~~bash
git log --oneline --graph --all
git remote -v
~~~

---

## 5. 해결 방법

서로 관련 없는 기록이지만 정말 합쳐야 한다면 아래 옵션을 사용한다.

~~~bash
git pull origin main --allow-unrelated-histories
~~~

### explanation
이 옵션은 관련 없는 두 이력을 강제로 merge 하도록 허용한다.

---

## 6. 충돌이 날 수 있음

강제로 합치는 과정에서 같은 파일 이름 등이 겹치면 conflict가 날 수 있다.

### 해결 흐름
~~~bash
git pull origin main --allow-unrelated-histories
git status
git add .
git commit -m "MERGE: combine unrelated histories"
~~~

---

## 7. 주의할 점

이 에러가 났다고 무조건 강제로 합치면 안 된다.  
정말 같은 프로젝트를 합치는 상황인지 먼저 확인해야 한다.

특히 잘못된 저장소 URL을 연결한 경우도 있으므로 `git remote -v` 확인이 먼저다.

---

## 8. 한 줄 정리

이 에러는  
**공통 조상이 없는 서로 다른 Git 이력을 합치려 해서 Git이 merge를 거부한 상태**이다.