# Git 설치 가이드

Git 공식 설치 페이지는 `git-scm.com/install` 이고, 현재 Git 공식 사이트 기준 최신 버전은 2.53.0이다. Windows용 최신 Git for Windows x64 빌드는 2026-04-14 릴리스로 안내되어 있다. :contentReference[oaicite:0]{index=0}

---

## 1. Windows 설치

Windows에서는 Git 공식 사이트에서 설치 파일을 받거나 `winget`으로 설치할 수 있다. Git 공식 설치 페이지는 Git for Windows 설치 파일과 `winget install --id Git.Git -e --source winget` 명령을 안내한다. :contentReference[oaicite:1]{index=1}

### 방법 1. 설치 파일로 설치

브라우저에서 공식 다운로드 페이지로 들어가서 설치한다.

~~~bash
https://git-scm.com/download/win
~~~

### 방법 2. winget으로 설치

PowerShell 또는 CMD에서 실행한다.

~~~bash
winget install --id Git.Git -e --source winget
~~~

### 설치 확인

~~~bash
git --version
~~~

---

## 2. macOS 설치

공식 문서 기준 macOS에서는 Homebrew로 설치할 수 있고, Git 미설치 상태에서 터미널에 `git --version`을 입력하면 Xcode Command Line Tools 설치 안내가 나올 수 있다. 또한 Git 공식 사이트는 macOS용 다운로드 페이지도 제공한다. :contentReference[oaicite:2]{index=2}

### 방법 1. Homebrew로 설치

~~~bash
brew install git
~~~

### 방법 2. Xcode Command Line Tools 방식

~~~bash
git --version
~~~

### 방법 3. 공식 설치 파일

~~~bash
https://git-scm.com/download/mac
~~~

### 설치 확인

~~~bash
git --version
~~~

---

## 3. Linux 설치

공식 Git 문서는 Linux에서 배포판 패키지 관리자를 통한 설치를 안내한다. 배포판마다 명령은 다르다. :contentReference[oaicite:3]{index=3}

### Ubuntu / Debian

~~~bash
sudo apt update
sudo apt install git -y
~~~

### Fedora

~~~bash
sudo dnf install git -y
~~~

### CentOS / RHEL 계열

~~~bash
sudo yum install git -y
~~~

### Arch Linux

~~~bash
sudo pacman -S git
~~~

### 설치 확인

~~~bash
git --version
~~~

---

## 4. 설치 후 최초 설정

Git 공식 문서는 사용자 이름과 이메일 설정에 `git config`를 사용한다고 안내한다. `--global`을 쓰면 사용자 전역 설정 파일에 기록된다. :contentReference[oaicite:4]{index=4}

### 사용자 이름 설정

~~~bash
git config --global user.name "<name>"
~~~

### 이메일 설정

~~~bash
git config --global user.email "<email>"
~~~

### 기본 branch 이름 main으로 설정

~~~bash
git config --global init.defaultBranch main
~~~

### 설정 확인

~~~bash
git config --list
~~~

---

## 5. 설치 확인용 테스트

Git이 정상 설치됐는지 간단히 확인한다.

~~~bash
git --version
git config --list
~~~

---

## 6. 내가 보통 쓰는 최소 세팅

~~~bash
git --version
git config --global user.name "<name>"
git config --global user.email "<email>"
git config --global init.defaultBranch main
git config --list
~~~