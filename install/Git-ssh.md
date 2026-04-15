# Git SSH 설정법

GitHub는 SSH로 연결하면 매번 아이디/토큰을 입력하지 않고 push, pull 할 수 있다. GitHub 공식 문서는 SSH 연결 절차를 `기존 키 확인 → 새 키 생성 → GitHub 계정에 공개키 등록 → 연결 테스트` 순서로 안내한다. 또한 기본 권장 알고리즘으로 Ed25519를 사용하며, Ed25519를 지원하지 않는 레거시 환경에서는 RSA 4096을 대안으로 안내한다. :contentReference[oaicite:0]{index=0}

---

## 1. 기존 SSH 키 확인

먼저 기존 키가 있는지 확인한다.

~~~bash
ls -al ~/.ssh
~~~

### explanation
보통 아래 같은 파일이 있으면 기존 SSH 키가 있는 것이다.

~~~bash
id_ed25519
id_ed25519.pub
id_rsa
id_rsa.pub
~~~

---

## 2. 새 SSH 키 생성

GitHub 공식 문서 기준 권장 방식은 Ed25519이다. :contentReference[oaicite:1]{index=1}

~~~bash
ssh-keygen -t ed25519 -C "your_email@example.com"
~~~

### example
~~~bash
ssh-keygen -t ed25519 -C "example@gmail.com"
~~~

### explanation
명령 실행 후 보통 아래를 물어본다.

- 저장 위치
- passphrase 설정 여부

그냥 기본 경로를 쓸 거면 Enter 누르면 된다.

기본 경로 예시:

~~~bash
/home/user/.ssh/id_ed25519
~~~

### legacy system
Ed25519를 지원하지 않는 환경이면 RSA 4096을 사용할 수 있다. :contentReference[oaicite:2]{index=2}

~~~bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
~~~

---

## 3. ssh-agent 실행 및 키 등록

GitHub 공식 문서는 생성한 키를 ssh-agent에 추가하는 절차를 안내한다. :contentReference[oaicite:3]{index=3}

### Linux / macOS
~~~bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
~~~

### Windows Git Bash
~~~bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
~~~

### explanation
passphrase를 설정했다면 여기서 한 번 입력할 수 있다.

---

## 4. 공개키 내용 출력

GitHub에는 `.pub` 파일 내용을 등록해야 한다. GitHub 공식 문서는 공개키를 GitHub 계정에 추가해야 SSH 접근이 가능하다고 안내한다. :contentReference[oaicite:4]{index=4}

### Linux / macOS
~~~bash
cat ~/.ssh/id_ed25519.pub
~~~

### Windows PowerShell
~~~bash
type $env:USERPROFILE\.ssh\id_ed25519.pub
~~~

### Git Bash
~~~bash
cat ~/.ssh/id_ed25519.pub
~~~

출력된 한 줄 전체를 복사한다.

---

## 5. GitHub에 SSH 키 등록

GitHub 웹에서 아래 순서로 들어간다. GitHub 공식 문서의 계정 설정 흐름이다. :contentReference[oaicite:5]{index=5}

1. GitHub 로그인
2. `Settings`
3. `SSH and GPG keys`
4. `New SSH key` 또는 `Add SSH key`
5. Title 입력
6. Key 칸에 방금 복사한 공개키 붙여넣기
7. 저장

### explanation
- `Title` 은 장치 구분용 이름이다.
- 예: `My Desktop`, `Windows Laptop`, `WSL-Kali`

---

## 6. SSH 연결 테스트

GitHub 공식 문서는 아래 명령으로 연결 테스트를 안내한다. 처음 연결하면 호스트 신뢰 여부를 물을 수 있다. :contentReference[oaicite:6]{index=6}

~~~bash
ssh -T git@github.com
~~~

### example
~~~bash
ssh -T git@github.com
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
~~~

### explanation
저 문구가 나오면 정상이다.

---

## 7. 원격 저장소 URL을 SSH 방식으로 변경

HTTPS로 연결된 저장소라면 SSH URL로 바꿔야 한다.

현재 remote 확인:

~~~bash
git remote -v
~~~

### HTTPS 예시
~~~bash
origin  https://github.com/username/repo.git (fetch)
origin  https://github.com/username/repo.git (push)
~~~

SSH로 변경:

~~~bash
git remote set-url origin git@github.com:username/repo.git
~~~

다시 확인:

~~~bash
git remote -v
~~~

### SSH 예시
~~~bash
origin  git@github.com:username/repo.git (fetch)
origin  git@github.com:username/repo.git (push)
~~~

---

## 8. push 테스트

~~~bash
git push origin main
~~~

### explanation
정상 설정이면 비밀번호 대신 SSH 키로 인증된다.

---

## 9. 여러 SSH 키를 쓰는 경우

개인 계정, 학교 계정, 서버용 키를 따로 쓰면 `~/.ssh/config`를 설정하는 편이 편하다.

~~~bash
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519
  IdentitiesOnly yes
~~~

### 다른 키를 별도로 쓰는 예시
~~~bash
Host github-personal
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_personal
  IdentitiesOnly yes

Host github-school
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_school
  IdentitiesOnly yes
~~~

그 경우 remote도 별칭으로 잡는다.

~~~bash
git remote set-url origin git@github-personal:username/repo.git
~~~

---

## 10. 자주 나는 문제

### 1) Permission denied (publickey)
보통 아래 중 하나다.

- 공개키를 GitHub에 안 올림
- `ssh-agent`에 키를 안 넣음
- 다른 키를 잡고 있음
- remote URL이 아직 HTTPS임

확인 명령:

~~~bash
ssh -T git@github.com
git remote -v
ssh-add -l
~~~

### 2) 이미 다른 키가 있는데 새 키가 우선으로 잡힘
이 경우 `~/.ssh/config`에서 `IdentityFile`과 `IdentitiesOnly yes`를 명시하는 게 가장 깔끔하다.

### 3) 공개키 말고 개인키를 붙여넣음
GitHub에는 반드시 `.pub` 파일 내용을 넣어야 한다. GitHub는 OpenSSH 공개키 형식을 요구한다. :contentReference[oaicite:7]{index=7}

---

## 11. 내가 보통 쓰는 최소 명령

~~~bash
ssh-keygen -t ed25519 -C "your_email@example.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub
ssh -T git@github.com
git remote set-url origin git@github.com:username/repo.git
~~~