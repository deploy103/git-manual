# remote origin already exists

`remote origin already exists` 는  
이미 `origin` 이라는 이름의 원격 저장소가 등록되어 있는데 다시 추가하려고 할 때 발생한다.

---

## 1. 대표 예시

~~~bash
git remote add origin https://github.com/user/repo.git
error: remote origin already exists.
~~~

---

## 2. 언제 발생하나

보통 아래 경우이다.

- 이미 remote 연결이 되어 있음
- 다른 저장소 URL로 바꾸려는데 `add` 를 또 실행함
- clone 받은 저장소에 다시 `origin` 을 추가하려고 함

---

## 3. 먼저 확인할 것

### 현재 remote 확인
~~~bash
git remote -v
~~~

---

## 4. 해결 방법 1: URL만 변경

이미 있는 `origin` 의 주소만 바꾸고 싶다면 `set-url` 을 쓴다.

~~~bash
git remote set-url origin <repository URL>
~~~

### example
~~~bash
git remote set-url origin https://github.com/user/new-repo.git
~~~

---

## 5. 해결 방법 2: 기존 origin 삭제 후 다시 추가

~~~bash
git remote remove origin
git remote add origin <repository URL>
~~~

---

## 6. 자주 쓰는 확인 흐름

~~~bash
git remote -v
git remote set-url origin <repository URL>
git remote -v
~~~

---

## 7. 한 줄 정리

이 에러는  
**`origin` 이라는 원격 저장소 이름이 이미 등록되어 있는데 또 추가하려고 해서 발생하는 상태**이다.