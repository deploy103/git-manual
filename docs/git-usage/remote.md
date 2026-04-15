# Git Remote

`git remote`는 현재 로컬 저장소가 어떤 원격 저장소와 연결되어 있는지 확인하거나 변경할 때 사용한다.

---

## 1. 원격 저장소 확인

현재 연결된 원격 저장소 이름을 확인한다.

~~~bash
git remote
~~~

---

## 2. 원격 저장소 주소까지 확인

원격 저장소 이름과 URL을 같이 확인한다.

~~~bash
git remote -v
~~~

### example
~~~bash
git remote -v
origin  https://github.com/example/test.git (fetch)
origin  https://github.com/example/test.git (push)
~~~

---

## 3. 원격 저장소 연결

원격 저장소를 새로 연결한다.

~~~bash
git remote add origin <repository URL>
~~~

### example
~~~bash
git remote add origin https://github.com/example/test.git
~~~

---

## 4. 원격 저장소 주소 변경

이미 연결된 원격 저장소 주소를 바꾼다.

~~~bash
git remote set-url origin <repository URL>
~~~

### example
~~~bash
git remote set-url origin https://github.com/example/new-test.git
~~~

---

## 5. 원격 저장소 삭제

연결된 원격 저장소를 제거한다.

~~~bash
git remote remove origin
~~~

---

## 6. 자주 쓰는 방식

~~~bash
git remote -v
git remote add origin <repository URL>
git remote set-url origin <repository URL>
~~~