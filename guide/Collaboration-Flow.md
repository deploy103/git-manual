# Collaboration Flow

`Collaboration Flow` 는  
여러 사람이 하나의 Git 저장소에서  
어떤 순서로 함께 작업하는지 설명하는 문서이다.

혼자 하는 Git 과 협업용 Git 의 가장 큰 차이는  
다른 사람의 작업과 내 작업이 서로 영향을 준다는 점이다.

그래서 협업에서는  
작업을 분리하고, 확인하고, 합치는 흐름이 중요하다.

---

## 1. 협업에서 중요한 이유

협업에서는  
한 사람이 `main` 을 막 바꾸기 시작하면  
전체 프로젝트가 금방 꼬일 수 있다.

예를 들어 아래 같은 문제가 생길 수 있다.

- 같은 파일을 동시에 수정함
- 서로 다른 기능이 섞임
- 누가 어떤 작업을 했는지 모름
- 오류가 있는 코드가 바로 main 에 들어감
- 충돌이 자주 발생함

그래서 협업에서는  
작업 흐름을 나누고 정리하는 규칙이 필요하다.

---

## 2. 협업의 기본 원칙

협업에서는 보통 아래 원칙을 따른다.

- `main` 은 안정적으로 유지
- 작업은 별도 branch 에서 진행
- 작업 완료 후 원격 저장소에 push
- Pull Request 로 변경 내용 검토
- 리뷰 후 merge

즉,  
**바로 합치지 말고, 나눠서 작업한 뒤 확인 후 합친다** 가 핵심이다.

---

## 3. 협업 기본 흐름

보통 협업은 아래 순서로 진행된다.

1. 최신 `main` 을 받는다.  
2. 새 작업용 branch 를 만든다.  
3. 각자 작업한다.  
4. commit 한다.  
5. 원격 저장소에 push 한다.  
6. Pull Request 를 만든다.  
7. 리뷰를 받는다.  
8. 문제 없으면 merge 한다.  

---

## 4. 단계별 설명

### 1) 최신 main 받기
작업 시작 전  
기준이 되는 최신 상태를 먼저 가져온다.

example:
`git switch main`  
`git pull origin main`

### 2) 작업용 branch 생성
기능이나 버그 수정별로 branch 를 만든다.

example:
`git switch -c feat/login`

### 3) 작업 진행
각자 자기 branch 에서만 수정한다.

### 4) commit
작업 단위로 기록을 남긴다.

example:
`git commit -m "FEAT: add login page"`

### 5) push
원격 저장소에 branch 를 올린다.

example:
`git push -u origin feat/login`

### 6) Pull Request 생성
`feat/login` 을 `main` 에 합치기 전에  
검토 요청을 보낸다.

### 7) 리뷰
다른 사람이 변경 내용을 확인한다.

### 8) merge
문제가 없으면 `main` 으로 합친다.

---

## 5. 왜 branch 를 따로 만들어야 하나

협업에서는  
한 저장소를 여러 사람이 동시에 만지기 때문에  
작업을 분리할 수 있어야 한다.

branch 를 따로 만들면 아래 장점이 있다.

- 메인 버전을 안 건드리고 작업 가능
- 기능별로 작업을 분리 가능
- 문제가 생겨도 main 은 안전함
- 리뷰 전에 작업 내용을 독립적으로 볼 수 있음

즉, branch 는  
협업에서 작업 공간을 나누는 기본 장치이다.

---

## 6. Pull Request 가 왜 필요한가

Pull Request 는  
"이 작업을 main 에 합쳐도 되는지 봐 달라" 는 요청이다.

이 과정이 있으면 아래가 가능하다.

- 변경 내용 확인
- 실수 찾기
- 구조나 이름 점검
- 리뷰 의견 교환
- merge 전 마지막 검토

즉, PR 은  
단순한 버튼이 아니라  
협업에서 검토 단계 역할을 한다.

---

## 7. 협업 중 자주 생기는 상황

### 1) 같은 파일을 동시에 수정
충돌이 날 수 있다.

### 2) main 이 먼저 바뀜
내 branch 가 오래되면  
merge 전에 최신 main 을 반영해야 한다.

### 3) 리뷰에서 수정 요청
추가 commit 후 같은 PR 에 반영한다.

### 4) 작업이 커짐
한 branch 에 너무 많이 담지 말고  
작업을 나누는 것이 좋다.

---

## 8. 협업에서 자주 쓰는 흐름 예시

### A 가 작업 시작

`git switch main`  
`git pull origin main`  
`git switch -c feat/login`

### A 가 작업 후 push

`git add .`  
`git commit -m "FEAT: add login page"`  
`git push -u origin feat/login`

### GitHub 에서 PR 생성
- base: `main`
- compare: `feat/login`

### B 가 리뷰
- 코드 확인
- 수정 요청 또는 승인

### 승인 후 merge
- `feat/login` 이 `main` 에 합쳐짐

---

## 9. 협업에서 main 은 어떤 의미인가

보통 `main` 은  
현재 팀이 기준으로 삼는 안정 상태이다.

그래서 협업에서는  
아무 작업이나 바로 main 에 올리지 않는다.

즉, main 은  
"지금 기준 버전" 이고  
작업 branch 는 "변경 중인 버전" 이라고 보면 된다.

---

## 10. 협업할 때 좋은 습관

- 작업 전에 최신 main 받기
- branch 이름 규칙 맞추기
- 한 branch 에 한 작업만 담기
- commit 메시지 정리하기
- PR 제목과 설명 적기
- 리뷰 받고 merge 하기
- merge 후 branch 정리하기

---

## 11. 협업에서 안 좋은 습관

- main 에서 직접 작업
- 여러 기능을 한 branch 에 몰아넣기
- PR 없이 바로 merge
- 작업 오래 끌고 pull 안 하기
- 충돌 확인 없이 넘기기
- 의미 없는 commit 메시지 사용

---

## 12. 한 줄 정리

Git 협업 흐름은  
**최신 기준에서 branch 를 나눠 작업하고, commit 과 push 후 Pull Request 와 리뷰를 거쳐 main 에 합치는 구조**이다.