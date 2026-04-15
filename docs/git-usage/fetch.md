# Git Pull and Fetch

`git fetch`와 `git pull`은 원격 저장소의 변경사항을 가져올 때 사용한다.  
둘의 차이를 아는 것이 중요하다.

---

## 1. fetch

원격 저장소의 최신 내용을 가져오기만 한다.  
자동으로 merge 하지는 않는다.

~~~bash
git fetch
~~~

### explanation
- 원격 저장소 내용을 업데이트해서 받아옴
- 내 작업 파일은 바로 바뀌지 않음
- 먼저 확인하고 직접 merge 하고 싶을 때 사용

---

## 2. pull

원격 저장소 내용을 가져오고 바로 merge 한다.

~~~bash
git pull origin main
~~~

### explanation
- `fetch + merge`를 한 번에 수행
- 바로 내 branch에 반영됨

---

## 3. fetch 후 직접 비교

가져온 뒤 차이를 보고 싶을 때 사용한다.

~~~bash
git fetch
git log --oneline HEAD..origin/main
~~~

---

## 4. 자주 쓰는 방식

### 그냥 최신 내용 바로 반영
~~~bash
git pull origin main
~~~

### 먼저 가져오고 확인 후 반영
~~~bash
git fetch
git merge origin/main
~~~