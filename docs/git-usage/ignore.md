# Git Ignore

`.gitignore`는 Git이 추적하지 않아야 하는 파일이나 폴더를 지정할 때 사용한다.  
보통 캐시 파일, 빌드 결과물, 환경설정 파일 등을 제외할 때 사용한다.

---

## 1. 기본 예시

~~~gitignore
.env
node_modules/
dist/
__pycache__/
*.log
~~~

### explanation
- `.env` : 환경 변수 파일 무시
- `node_modules/` : 패키지 폴더 무시
- `dist/` : 빌드 결과물 무시
- `__pycache__/` : Python 캐시 무시
- `*.log` : 로그 파일 무시

---

## 2. 주의할 점

`.gitignore`에 적어도 이미 commit 된 파일은 계속 추적된다.

### example
이미 올라간 `.env` 파일을 무시하고 싶다면 먼저 Git 추적에서 제거해야 한다.

~~~bash
git rm --cached .env
git commit -m "CHORE: stop tracking .env"
~~~

---

## 3. `.gitignore` 확인 후 상태 보기

~~~bash
git status
~~~

---

## 4. 자주 쓰는 방식

### `.gitignore` 작성
~~~gitignore
.env
.vscode/
node_modules/
dist/
~~~

### 이미 추적 중인 파일 제거
~~~bash
git rm --cached <file name>
~~~