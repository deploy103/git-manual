# Pull Request Rule

`Pull Request Rule` 은  
작업한 branch 내용을 다른 branch 에 합치기 전에  
검토를 요청하는 기준과 작성 방법을 정해두는 규칙이다.

특히 협업에서는  
작업 내용을 바로 merge 하지 않고  
Pull Request 를 통해 변경 내용을 먼저 확인하는 과정이 중요하다.

이 과정을 통해  
무슨 작업이 들어가는지 명확하게 보이고,  
실수나 충돌 가능성도 줄일 수 있다.

---

## 1. 왜 필요한가

Pull Request 없이 바로 merge 하면  
어떤 변경이 들어가는지 확인하기 어렵고,  
협업 중에는 실수로 잘못된 내용이 들어갈 수 있다.

예를 들어 아래 같은 문제가 생길 수 있다.

- 어떤 기능이 추가되었는지 알기 어려움
- 버그 수정 범위가 불명확함
- 문서 수정인지 기능 수정인지 구분이 안 됨
- 리뷰 없이 merge 되어 문제를 놓칠 수 있음

그래서 Pull Request 작성 규칙을 정해두면  
변경 내용을 보기 쉽고, 검토도 편해진다.

---

## 2. 기본 원칙

Pull Request 는  
**무엇을 왜 바꿨는지 짧고 명확하게 보이도록 작성**하는 것이 좋다.

보통 아래 내용을 포함하면 충분하다.

- 제목
- 변경 내용
- 작업 이유
- 확인 사항
- 참고 사항

---

## 3. 제목 작성 규칙

제목은 branch 나 commit 메시지처럼  
짧고 명확하게 쓰는 것을 추천한다.

기본 형식은 아래처럼 맞추면 된다.

TYPE: short summary

### example

- `FEAT: add login page`
- `FIX: correct upload path error`
- `DOCS: update git manual`
- `CHORE: update gitignore`

---

## 4. 본문에 들어가면 좋은 내용

### 1) 무엇을 변경했는지
어떤 파일이나 기능을 수정했는지 적는다.

example:
- 로그인 페이지 추가
- 업로드 경로 오류 수정
- README 정리

### 2) 왜 변경했는지
이 작업이 왜 필요한지 적는다.

example:
- 로그인 기능이 필요해서 추가
- 잘못된 경로 때문에 업로드가 실패해서 수정
- 문서 구조가 복잡해서 정리

### 3) 확인한 내용
직접 확인한 항목을 적는다.

example:
- 실행 확인 완료
- 기본 기능 동작 확인 완료
- 오타 및 링크 확인 완료

### 4) 참고 사항
리뷰할 때 알아야 할 점이 있으면 적는다.

example:
- UI 는 임시 버전
- backend 연결은 아직 안 됨
- 추가 수정 예정

---

## 5. 추천 Pull Request 본문 양식

아래 정도로 작성하면 무난하다.

### template

- Summary
  - 무엇을 했는지 간단히 작성

- Changes
  - 변경한 내용 정리

- Reason
  - 왜 수정했는지 작성

- Check
  - 직접 확인한 내용 작성

- Note
  - 참고 사항 작성

---

## 6. example

### title
`FEAT: add login page`

### body

- Summary
  - 로그인 페이지를 추가했다.

- Changes
  - login.html 추가
  - login.css 추가
  - login 관련 route 연결

- Reason
  - 사용자 로그인 기능이 필요해서 추가했다.

- Check
  - 페이지 실행 확인 완료
  - 기본 입력창 동작 확인 완료

- Note
  - 실제 인증 기능은 아직 연결하지 않았다.

---

## 7. 작성 규칙 추천

### 1) 제목만 보고 작업 종류가 보여야 함
좋은 예:
- `FIX: resolve image loading error`

나쁜 예:
- `update`
- `fix`
- `작업`

### 2) 한 PR 에 한 작업만 넣기
기능 추가, 문서 수정, 설정 변경을 한 PR 에 전부 섞지 않는 것이 좋다.

좋은 예:
- 로그인 기능 추가만 포함
- README 수정만 포함

나쁜 예:
- 로그인 기능 추가 + README 수정 + gitignore 수정 한 번에 포함

### 3) 너무 긴 설명은 피하고 핵심만 적기
PR 본문은 논문처럼 길게 쓰는 것이 아니라  
리뷰하는 사람이 빠르게 이해할 수 있게 쓰는 것이 좋다.

### 4) merge 전에 직접 확인하기
최소한 실행 가능 여부나 기본 동작은 확인하고 올리는 것이 좋다.

### 5) 문서 수정도 PR 제목 규칙 맞추기
문서 작업도 그냥 올리지 말고 구분해서 작성한다.

example:
- `DOCS: add branch rule`

---

## 8. 자주 쓰는 흐름

### 작업 branch 생성
`git switch -c feat/login`

### 작업 후 commit
`git add .`
`git commit -m "FEAT: add login page"`

### 원격 저장소에 push
`git push -u origin feat/login`

### 이후 Pull Request 생성
- base: `main`
- compare: `feat/login`

---

## 9. 나쁜 예 / 좋은 예

### bad

- 제목이 `update`
- 본문 없음
- 여러 작업이 한 PR 에 섞여 있음
- 실행 확인 없이 PR 생성
- 왜 수정했는지 설명 없음

### good

- 제목이 `FEAT`, `FIX`, `DOCS` 등으로 시작함
- 무엇을 바꿨는지 본문에 정리함
- 작업 이유를 적음
- 확인한 내용을 적음
- 한 PR 에 한 작업만 넣음

---

## 10. 추천 규칙 예시

개인 프로젝트 또는 팀 프로젝트에서는  
아래 정도로 통일하면 충분하다.

- 제목은 `TYPE: short summary`
- 본문에는 변경 내용과 이유 작성
- 가능하면 확인 사항 작성
- 한 PR 에 한 작업만 포함
- 리뷰 후 merge 진행

---

## 11. 한 줄 정리

좋은 Pull Request 는  
**무엇을 왜 바꿨는지 쉽게 보이도록 정리해서, merge 전에 검토할 수 있게 만드는 것**이다.