# Permission denied (publickey)

`Permission denied (publickey)` 는 SSH 인증에 실패했을 때 나오는 에러이다.

즉, GitHub나 원격 저장소가 현재 컴퓨터의 SSH 키를 신뢰하지 않았다는 뜻이다.

---

## 1. 대표 예시

~~~bash
git push origin main
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.
~~~

---

## 2. 언제 발생하나

보통 아래 경우이다.

- GitHub에 공개키를 등록하지 않음
- `ssh-agent` 에 키를 추가하지 않음
- 다른 SSH 키를 잡고 있음
- remote URL은 SSH인데 키 설정이 안 됨
- 권한 없는 저장소에 push 시도함

---

## 3. 먼저 확인할 것

### remote URL 확인
~~~bash
git remote -v
~~~

### SSH 키 목록 확인
~~~bash
ls -al ~/.ssh
~~~

### agent에 올라간 키 확인
~~~bash
ssh-add -l
~~~

### GitHub 연결 테스트
~~~bash
ssh -T git@github.com
~~~

---

## 4. 원인별 해결

### 1) 공개키를 GitHub에 안 올림
공개키 확인:

~~~bash
cat ~/.ssh/id_ed25519.pub
~~~

이 내용을 GitHub `Settings -> SSH and GPG keys` 에 등록한다.

---

### 2) ssh-agent에 키를 안 넣음
~~~bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
~~~

---

### 3) remote URL 확인
SSH 형식이어야 한다.

### SSH 예시
~~~bash
git@github.com:username/repo.git
~~~

### 변경
~~~bash
git remote set-url origin git@github.com:username/repo.git
~~~

---

### 4) 여러 키를 써서 다른 키가 잡힘
`~/.ssh/config` 에 명시한다.

~~~bash
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519
  IdentitiesOnly yes
~~~

---

## 5. 최소 해결 순서

~~~bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
ssh -T git@github.com
git remote -v
~~~

---

## 6. 한 줄 정리

이 에러는  
**SSH 방식으로 인증하려 했는데 원격 저장소가 현재 키를 신뢰하지 않는 상태**이다.