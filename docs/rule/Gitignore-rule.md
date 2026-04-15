# Gitignore Rule

`Gitignore Rule` 은  
Git으로 관리하지 않을 파일과 디렉터리를 정하는 규칙이다.

프로젝트를 진행하다 보면  
환경 파일, 빌드 결과물, 에디터 설정 파일처럼  
저장소에 올리면 안 되거나 굳이 올릴 필요가 없는 파일들이 생긴다.

이런 파일들을 `.gitignore` 로 제외해서  
저장소를 깔끔하게 관리한다.

---

## 1. 왜 필요한가

모든 파일을 Git에 올리면  
불필요한 파일까지 같이 올라가서 저장소가 지저분해질 수 있다.

예를 들어 아래 같은 파일들은 보통 제외한다.

- 개인 환경 설정 파일
- 실행 결과로 만들어진 파일
- 빌드 산출물
- 캐시 파일
- 비밀 정보가 들어 있는 파일

이런 파일들을 그대로 push 하면  
협업에 방해가 되거나 보안 문제가 생길 수 있다.

---

## 2. 기본 원칙

`.gitignore` 에는  
**공유할 필요가 없는 파일** 과  
**자동 생성되는 파일** 을 넣는 것을 추천한다.

대표적으로 아래 항목들을 자주 제외한다.

- `.env`
- `.vscode/`
- `node_modules/`
- `__pycache__/`
- `*.log`
- `*.exe`
- `*.o`

---

## 3. 자주 제외하는 파일과 디렉터리

### 1) 환경 변수 파일
API 키, 비밀번호 같은 민감한 정보가 들어갈 수 있다.

example:
- `.env`
- `.env.local`

### 2) 에디터 설정 파일
개인별 개발 환경 차이가 있으므로 보통 제외한다.

example:
- `.vscode/`
- `.idea/`

### 3) 빌드 결과물
컴파일하거나 실행하면 자동 생성되는 파일들이다.

example:
- `dist/`
- `build/`
- `out/`

### 4) 캐시 파일
실행 중 자동으로 생기는 임시 파일들이다.

example:
- `__pycache__/`
- `*.pyc`

### 5) 운영체제 생성 파일
운영체제가 자동으로 만드는 불필요한 파일이다.

example:
- `.DS_Store`
- `Thumbs.db`

---

## 4. 작성 규칙 추천

### 1) 디렉터리는 끝에 `/` 붙이기
디렉터리라는 것을 명확하게 표시하는 것이 좋다.

좋은 예:
- `.vscode/`
- `node_modules/`

### 2) 확장자 패턴은 `*` 사용
같은 종류의 파일을 한 번에 제외할 수 있다.

example:
- `*.log`
- `*.tmp`
- `*.exe`

### 3) 민감한 파일은 반드시 제외
비밀번호, 토큰, 키 파일은 절대 push 하지 않는 것이 좋다.

example:
- `.env`
- `id_rsa`
- `*.pem`

### 4) 팀 전체에 필요한 설정 파일은 무조건 제외하지 않기
모든 설정 파일을 무조건 `.gitignore` 에 넣으면 안 된다.

예를 들어  
프로젝트 실행에 꼭 필요한 설정 파일이면  
템플릿 파일을 공유하는 방식이 더 좋다.

example:
- `.env.example` 는 포함
- `.env` 는 제외

### 5) 이미 추적 중인 파일은 `.gitignore` 만 써도 바로 사라지지 않음
이미 Git이 추적하고 있는 파일은  
`.gitignore` 에 추가해도 계속 관리된다.

이 경우에는 추적 해제를 해야 한다.

example:
- `git rm -r --cached .vscode`
- `git rm --cached .env`

---

## 5. 대표 예시

### example `.gitignore`

- `.env`
- `.vscode/`
- `__pycache__/`
- `*.log`
- `build/`
- `dist/`

---

## 6. 자주 쓰는 명령어

### `.gitignore` 파일 생성
touch .gitignore

### 이미 추적 중인 파일 추적 해제
git rm -r --cached .vscode

또는

git rm --cached .env

### 변경사항 반영
git add .gitignore
git commit -m "CHORE: update gitignore rule"

---

## 7. 추천 사용 방식

프로젝트 시작할 때  
처음부터 `.gitignore` 를 만들어 두는 것이 좋다.

### recommended flow

1. 프로젝트 시작
2. `.gitignore` 작성
3. 제외할 파일 확인
4. Git add 및 commit 진행

이렇게 하면  
불필요한 파일이 처음부터 저장소에 들어가는 것을 막을 수 있다.

---

## 8. 추천 규칙 예시

개인 프로젝트 또는 팀 프로젝트에서는  
아래 정도를 기본으로 두면 무난하다.

- `.env`
- `.vscode/`
- `.idea/`
- `node_modules/`
- `__pycache__/`
- `*.log`
- `build/`
- `dist/`
- `.DS_Store`
- `Thumbs.db`

---

## 9. 나쁜 예 / 좋은 예

### bad

- 비밀 키가 들어 있는 `.env` 파일 push
- `.vscode/` 같은 개인 설정 폴더 push
- 빌드 결과물까지 전부 commit
- `.gitignore` 없이 작업 시작

### good

- `.env` 는 제외하고 `.env.example` 만 공유
- 개인 설정 폴더는 `.gitignore` 로 제외
- 자동 생성 파일은 commit 하지 않음
- 프로젝트 시작할 때 `.gitignore` 먼저 작성

---

## 10. 한 줄 정리

좋은 `.gitignore` 설정은  
**공유할 필요 없는 파일과 민감한 파일을 저장소에서 제외해서 프로젝트를 깔끔하고 안전하게 관리하는 것**이다.