# Git Status

`git status`는 현재 작업 폴더의 상태를 확인하는 명령어이다.  
어떤 파일이 수정되었는지, 어떤 파일이 staging 되었는지, 아직 commit 안 된 내용이 무엇인지 볼 때 사용한다.

---

## 1. 기본 상태 확인

현재 Git 상태를 자세히 확인한다.

~~~bash
git status
~~~

### example
~~~bash
git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
        modified:   app.py
~~~

---

## 2. 짧은 형식으로 확인

상태를 짧게 한 줄씩 확인한다.

~~~bash
git status -s
~~~

### example
~~~bash
git status -s
M  README.md
 M app.py
?? test.txt
~~~

### meaning
- `M` : modified, 수정됨
- `??` : untracked, 아직 Git이 추적하지 않는 파일
- 앞칸 문자: staging 영역 상태
- 뒷칸 문자: working directory 상태

---

## 3. 자주 쓰는 방식

~~~bash
git status
git status -s
~~~