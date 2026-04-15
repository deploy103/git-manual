# Git Clone

`git clone`은 원격 저장소를 내 컴퓨터로 복사할 때 사용한다.

---

## 1. 저장소 복제

원격 저장소를 현재 폴더에 복제한다.

~~~bash
git clone <repository URL>
~~~

### example
~~~bash
git clone https://github.com/example/test.git
~~~

---

## 2. 폴더 이름 지정해서 복제

원하는 폴더 이름으로 저장소를 복제한다.

~~~bash
git clone <repository URL> <directory name>
~~~

### example
~~~bash
git clone https://github.com/example/test.git my-project
~~~

---

## 3. clone 후 확인

복제한 폴더로 이동한다.

~~~bash
cd test
~~~

---

## 4. 자주 쓰는 방식

~~~bash
git clone <repository URL>
cd <repository name>
git branch
git remote -v
~~~