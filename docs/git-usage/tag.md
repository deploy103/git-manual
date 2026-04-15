# Git Tag

`git tag`는 특정 commit에 버전 이름을 붙일 때 사용한다.  
주로 릴리즈 버전 관리에 사용한다.

---

## 1. tag 목록 확인

현재 tag 목록을 확인한다.

~~~bash
git tag
~~~

---

## 2. tag 생성

현재 commit에 tag를 붙인다.

~~~bash
git tag v1.0.0
~~~

---

## 3. 특정 commit에 tag 생성

원하는 commit에 tag를 붙일 수 있다.

~~~bash
git tag v1.0.0 <commit hash>
~~~

---

## 4. tag 업로드

생성한 tag를 원격 저장소에 업로드한다.

~~~bash
git push origin v1.0.0
~~~

---

## 5. 모든 tag 업로드

로컬의 tag를 전부 원격 저장소에 올린다.

~~~bash
git push --tags
~~~

---

## 6. 자주 쓰는 방식

~~~bash
git tag
git tag v1.0.0
git push origin v1.0.0
~~~s