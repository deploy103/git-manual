# Git Push

`git push`는 로컬 commit을 원격 저장소에 업로드할 때 사용한다.

---

## 1. 현재 branch 업로드

현재 branch의 commit을 원격 저장소에 업로드한다.

~~~bash
git push
~~~

### explanation
이미 upstream 설정이 되어 있어야 한다.

---

## 2. 특정 branch 업로드

원하는 branch를 지정해서 업로드한다.

~~~bash
git push origin main
~~~

### example
~~~bash
git push origin main
~~~

---

## 3. 처음 올릴 때 upstream 연결

처음 push 하는 branch는 `-u` 옵션으로 연결해두는 경우가 많다.

~~~bash
git push -u origin main
~~~

### explanation
이후에는 `git push`만 입력해도 같은 branch로 업로드된다.

---

## 4. 새 branch 원격에 올리기

로컬에서 만든 새 branch를 원격에 업로드한다.

~~~bash
git push -u origin feature/login
~~~

---

## 5. tag까지 같이 올리기

tag를 원격 저장소에 업로드한다.

~~~bash
git push origin <tag name>
~~~

### example
~~~bash
git push origin v1.0.0
~~~

---

## 6. 자주 쓰는 방식

~~~bash
git push
git push origin main
git push -u origin <branch name>
~~~