## Git 올리기

로컬 폴더에서 작업한 파일을 Git 저장소에 올릴 때는 아래 순서대로 진행한다.

### 1. Git 저장소로 만들기
아직 Git 저장소가 아니라면 먼저 초기화한다.

```bash
git init
```

### 2. File Upload
현재 폴더의 파일들을 Git이 추적할 수 있게 추가한다.

```bash
git add .
```

### 3. Commit Create
추가한 파일들의 변경사항을 하나의 기록으로 저장한다.

```bash
git commit -m "<commit message>"

<example>
git commit -m "FETCH:BOF_Fetch"

```

### 4. setting to Basic Branch Name
브랜치 이름을 main 혹은 작업중인 브랜치 이름으로 맞춰준다.

```bash
git branch -M main
```

### 5. Repository Connect
Github Repository Adress를 연결한다.

```bash
git remote add origin <repository URL>

<example>
git remote add origin https://github.com/youghwjdkill1/git-command-manual.git
```

### 6. Upload to Repository 
Upload Local Commit to the remote repository

```bash
git push -u origin main
```

### 7. 짧게 내가 쓰는 방식
```bash
git add .    # 디렉터리에 변경사항을 전부 로컬 커밋한다.
git commit -m "<commit message>"    # 커밋 메세지를 남긴다.
git push origin main     # main branch에 푸시(UPload) 한다.
```
