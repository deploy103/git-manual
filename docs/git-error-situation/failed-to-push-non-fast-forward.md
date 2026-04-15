# failed to push some refs / non-fast-forward

`failed to push some refs` 와 `non-fast-forward` 는  
원격 저장소 쪽이 내 로컬보다 앞서 있어서 그대로 push 할 수 없을 때 발생한다.

즉, 다른 사람이 먼저 push 했거나, GitHub에서 직접 수정된 commit이 있어서 내 기록만 바로 올릴 수 없는 상태이다.

---

## 1. 대표 예시

~~~bash
git push origin main
To github.com:user/repo.git
 ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'git@github.com:user/repo.git'
hint: Updates were rejected because the tip of your current branch is behind
~~~

---

## 2. 언제 발생하나

보통 아래 경우이다.

- 다른 사람이 먼저 push 함
- GitHub 웹에서 README 등을 수정함
- 다른 PC에서 작업 후 이미 push 함
- 로컬 branch가 원격보다 뒤처짐

---

## 3. 먼저 확인할 것

### 원격 내용 가져오기
~~~bash
git fetch
~~~

### 차이 확인
~~~bash
git log --oneline --graph --all
~~~

### 현재 상태 확인
~~~bash
git status
~~~

---

## 4. 가장 일반적인 해결

원격 내용을 먼저 반영한 뒤 다시 push 한다.

~~~bash
git pull origin main
git push origin main
~~~

---

## 5. 충돌이 나는 경우

`git pull` 과정에서 conflict가 나면 직접 해결해야 한다.

~~~bash
git status
git add .
git commit -m "MERGE: resolve conflict"
git push origin main
~~~

---

## 6. rebase 방식으로 정리해서 반영

히스토리를 깔끔하게 이어붙이고 싶으면 rebase 방식도 쓴다.

~~~bash
git pull --rebase origin main
git push origin main
~~~

### conflict 발생 시
~~~bash
git add .
git rebase --continue
~~~

---

## 7. 강제 push는 주의

~~~bash
git push --force origin main
~~~

### warning
이 명령은 원격 기록을 덮어쓸 수 있으므로 협업 중에는 매우 조심해야 한다.

---

## 8. 한 줄 정리

이 에러는  
**원격 저장소에 내 로컬에 없는 최신 commit이 있어서 바로 push 할 수 없는 상태**이다.