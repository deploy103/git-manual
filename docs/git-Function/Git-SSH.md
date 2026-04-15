# Git SSH란?

Git SSH는 Git과 원격 저장소를 연결할 때 **SSH 방식으로 인증**하는 방법이다.  
주로 GitHub, GitLab 같은 원격 저장소에 `push`, `pull`, `clone` 할 때 사용한다.

---

## 1. SSH가 필요한 이유

Git 원격 저장소에 접근할 때는 내가 해당 저장소에 접근할 수 있는 사용자라는 것을 인증해야 한다.

인증 방식은 보통 두 가지가 있다.

- HTTPS 방식
- SSH 방식

HTTPS 방식은 작업할 때 토큰이나 로그인 정보가 필요할 수 있고,  
SSH 방식은 미리 등록한 SSH 키를 사용해서 인증한다.

즉, Git SSH는  
**비밀번호 대신 SSH 키로 Git 원격 저장소를 인증하는 방식**이라고 보면 된다.

---

## 2. Git SSH의 동작 방식

Git SSH는 공개키 암호화 방식을 사용한다.

구성은 두 가지이다.

- 개인키(Private Key)
- 공개키(Public Key)

### explanation
- 개인키는 내 컴퓨터에 보관한다.
- 공개키는 GitHub 같은 원격 서비스에 등록한다.
- 이후 접속할 때 원격 저장소는 등록된 공개키를 기준으로 사용자를 확인한다.

즉,
내 컴퓨터에 있는 개인키와  
GitHub에 등록된 공개키가 서로 짝이 맞으면 인증이 성공한다.

---

## 3. HTTPS와 SSH의 차이

### HTTPS
- 주소 예시:
~~~bash
https://github.com/username/repo.git
~~~
- 토큰 또는 로그인 정보가 필요할 수 있다.
- 처음 접하는 사람에게는 이해하기 쉬운 편이다.

### SSH
- 주소 예시:
~~~bash
git@github.com:username/repo.git
~~~
- SSH 키를 미리 설정해야 한다.
- 설정이 끝나면 push, pull 할 때 편하다.

---

## 4. Git SSH를 사용하는 장점

### 1) 매번 인증 정보를 덜 입력해도 된다
SSH 키를 등록해두면 비밀번호나 토큰을 반복해서 입력하지 않아도 되는 경우가 많다.

### 2) 원격 작업이 편하다
`push`, `pull`, `clone` 같은 작업을 더 자연스럽게 할 수 있다.

### 3) 여러 저장소 작업에 유리하다
개인 프로젝트, 팀 프로젝트, 서버 작업 등에서 SSH 키 기반 인증이 많이 사용된다.

### 4) 보안적으로 관리가 명확하다
공개키와 개인키를 분리해서 사용하므로 계정 비밀번호를 직접 전송하지 않는다.

---

## 5. Git SSH를 쓰기 위해 필요한 것

Git SSH를 사용하려면 보통 아래 과정이 필요하다.

1. SSH 키 생성
2. 공개키를 GitHub에 등록
3. 원격 저장소 주소를 SSH 형식으로 변경
4. 연결 테스트

---

## 6. SSH 키란?

SSH 키는 원격 시스템에 안전하게 로그인하거나 인증할 때 사용하는 키 파일이다.

보통 아래처럼 생성된다.

~~~bash
id_ed25519
id_ed25519.pub
~~~

### explanation
- `id_ed25519` : 개인키
- `id_ed25519.pub` : 공개키

GitHub에는 `.pub` 파일 내용을 등록한다.  
개인키는 절대 외부에 공개하면 안 된다.

---

## 7. Git SSH를 쓰는 대표 명령

원격 저장소 SSH 주소 예시:

~~~bash
git@github.com:username/repo.git
~~~

현재 remote 확인:

~~~bash
git remote -v
~~~

SSH 주소로 변경:

~~~bash
git remote set-url origin git@github.com:username/repo.git
~~~

연결 테스트:

~~~bash
ssh -T git@github.com
~~~

---

## 8. 언제 SSH를 쓰는가?

보통 아래 상황에서 많이 쓴다.

- GitHub에 자주 push 해야 할 때
- 협업 저장소를 자주 다룰 때
- 서버에서 Git 작업할 때
- HTTPS 인증이 번거로울 때

---

## 9. 주의할 점

### 1) 개인키는 절대 공유하면 안 된다
유출되면 내 계정 인증에 악용될 수 있다.

### 2) GitHub에는 공개키만 등록해야 한다
`.pub` 파일 내용을 등록해야 한다.

### 3) SSH 설정 후에도 remote 주소가 HTTPS면 SSH 인증을 안 쓴다
이 경우 remote URL을 SSH 형식으로 바꿔야 한다.

---

## 10. 한 줄 정리

Git SSH는  
**Git 원격 저장소에 접근할 때 비밀번호 대신 SSH 키로 인증하는 방식**이다.

설정이 끝나면 GitHub 같은 원격 저장소에 더 편하게 `push`, `pull`, `clone` 할 수 있다.