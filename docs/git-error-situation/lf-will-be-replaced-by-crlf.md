# LF will be replaced by CRLF

`LF will be replaced by CRLF` 는  
줄바꿈 문자 형식이 바뀔 수 있다고 Git이 경고하는 메시지이다.

에러라기보다 줄바꿈 처리 관련 경고에 가깝다.

---

## 1. 대표 예시

~~~bash
warning: LF will be replaced by CRLF in README.md
~~~

---

## 2. LF와 CRLF가 뭔가

텍스트 파일의 줄바꿈 방식이다.

- `LF` : 주로 Linux, macOS에서 사용
- `CRLF` : 주로 Windows에서 사용

---

## 3. 언제 발생하나

보통 아래 경우이다.

- Windows 환경에서 Git 작업할 때
- 다른 운영체제에서 만든 파일을 수정했을 때
- `core.autocrlf` 설정 영향으로 줄바꿈을 자동 변환할 때

---

## 4. 왜 뜨는가

Git이 파일을 checkout 하거나 add 하는 과정에서  
운영체제 환경에 맞게 줄바꿈을 바꾸려 할 수 있다.

그때 원래 `LF` 였던 파일이 `CRLF` 로 바뀔 수 있다고 알려주는 것이다.

---

## 5. 현재 설정 확인

~~~bash
git config --global core.autocrlf
git config --system core.autocrlf
git config --list
~~~

---

## 6. 자주 쓰는 설정

### Windows에서 보통 많이 쓰는 설정
~~~bash
git config --global core.autocrlf true
~~~

### 줄바꿈 변환을 끄고 싶을 때
~~~bash
git config --global core.autocrlf false
~~~

### commit 시 LF 정규화만 하고 checkout 시는 유지
~~~bash
git config --global core.autocrlf input
~~~

---

## 7. 프로젝트에서 줄바꿈 통일하기

`.gitattributes` 파일로 줄바꿈 정책을 통일할 수 있다.

### example
~~~text
* text=auto
~~~

또는 특정 파일을 LF로 고정:

~~~text
*.sh text eol=lf
*.bat text eol=crlf
~~~

---

## 8. 이 경고가 꼭 문제인가

대부분은 즉시 큰 문제는 아니다.  
다만 팀 프로젝트에서 운영체제가 섞여 있으면  
불필요한 diff가 많이 생길 수 있어서 줄바꿈 정책을 맞추는 게 좋다.

---

## 9. 한 줄 정리

이 메시지는  
**파일 줄바꿈 형식이 LF에서 CRLF로 바뀔 수 있다고 Git이 알려주는 경고**이다.