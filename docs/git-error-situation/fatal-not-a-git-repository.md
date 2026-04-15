# fatal: not a git repository

`fatal: not a git repository` 는  
현재 폴더가 Git 저장소가 아니거나, `.git` 디렉터리를 찾지 못할 때 발생한다.

---

## 1. 대표 예시

~~~bash
git status
fatal: not a git repository (or any of the parent directories): .git
~~~

---

## 2. 언제 발생하나

보통 아래 경우이다.

- Git 저장소 바깥 폴더에서 명령 실행
- `cd` 를 잘못해서 다른 폴더에 들어감
- `.git` 폴더가 삭제됨
- 압축 해제만 하고 clone 안 한 폴더에서 Git 명령 실행

---

## 3. 먼저 확인할 것

### 현재 위치 확인
~~~bash
pwd
~~~

### 파일 목록 확인
~~~bash
ls -al
~~~

### `.git` 존재 확인
~~~bash
ls -al .git
~~~

---

## 4. 해결 방법

### 1) 올바른 저장소 폴더로 이동
~~~bash
cd <repository directory>
git status
~~~

### 2) 아직 Git 저장소가 아니면 초기화
~~~bash
git init
~~~

### 3) 원격 저장소를 받아와야 하는 경우 clone
~~~bash
git clone <repository URL>
cd <repository name>
~~~

---

## 5. `.git` 폴더를 지운 경우

`.git` 을 지우면 Git 기록이 날아간다.  
그 경우 보통 다시 clone 하거나, 새로 `git init` 해서 다시 연결해야 한다.

---

## 6. 한 줄 정리

이 에러는  
**지금 있는 폴더가 Git 저장소가 아니어서 Git 명령을 처리할 수 없는 상태**이다.