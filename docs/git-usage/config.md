# Git Config

`git config`는 Git 사용자 이름, 이메일, 기본 설정 등을 관리할 때 사용한다.

---

## 1. 전역 사용자 이름 설정

현재 PC 전체에서 사용할 Git 사용자 이름을 설정한다.

~~~bash
git config --global user.name "<name>"
~~~

### example
~~~bash
git config --global user.name "dolahi"
~~~

---

## 2. 전역 이메일 설정

현재 PC 전체에서 사용할 Git 이메일을 설정한다.

~~~bash
git config --global user.email "<email>"
~~~

### example
~~~bash
git config --global user.email "example@gmail.com"
~~~

---

## 3. 설정 확인

현재 설정된 값을 확인한다.

~~~bash
git config --list
~~~

---

## 4. 특정 값만 확인

원하는 설정만 따로 확인한다.

~~~bash
git config user.name
git config user.email
~~~

---

## 5. 현재 저장소에서만 따로 설정

전역이 아니라 현재 repository에서만 따로 설정할 수 있다.

~~~bash
git config user.name "<name>"
git config user.email "<email>"
~~~

### explanation
`--global`을 빼면 현재 repository에만 적용된다.

---

## 6. 기본 branch 이름 설정

새 repo 생성 시 기본 branch 이름을 `main`으로 설정할 수 있다.

~~~bash
git config --global init.defaultBranch main
~~~

---

## 7. 자주 쓰는 방식

~~~bash
git config --global user.name "<name>"
git config --global user.email "<email>"
git config --global init.defaultBranch main
git config --list
~~~