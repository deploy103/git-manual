# Git 저장소 생성

## 1. Git 저장소(Repository)란
Git 저장소는 프로젝트의 파일 변경 내역을 기록하고 관리하는 공간이다.
코드 수정 이력 추적, 협업, 복구 작업을 위해 사용한다.

## 2. 새 프로젝트를 Git 저장소로 만드는 방법

### 방법 1. 현재 폴더에서 Git 시작
아래 명령어를 입력하면 현재 디렉터리가 Git 저장소로 초기화된다.

```bash
git init
```

### 방법 2. 기본 Repository Clone 하기
이미 Github에 저장소가 존재한다면 `clone`해서 가져올 수 있다.
또한 이 명령어를 사요하면 원격 저장소의 파일과 기록까지 함께 내려받을 수 있다.
```bash
git clone <저장소주소>

<example>
git clone https://github.com/youghwjdkill2/OcenSurvival.git
d
```