# Branch and Merge

`Branch and Merge` 는  
Git 에서 branch 가 왜 필요한지,  
그리고 나뉜 작업을 어떻게 다시 합치는지 설명하는 문서이다.

Git 을 이해할 때  
branch 와 merge 는 가장 중요한 개념 중 하나이다.

이걸 이해하면  
왜 협업할 때 branch 를 따고  
왜 마지막에 merge 하는지 자연스럽게 보인다.

---

## 1. branch 란 무엇인가

`branch` 는  
하나의 프로젝트에서 작업 흐름을 나누는 가지이다.

쉽게 말하면  
기본 줄기에서 옆으로 새 작업선을 하나 더 만드는 것이라고 보면 된다.

예를 들어

- `main` : 현재 안정적인 기본 버전
- `feat/login` : 로그인 기능 개발
- `fix/upload-error` : 업로드 오류 수정

이런 식으로 branch 를 나눌 수 있다.

---

## 2. 왜 branch 가 필요한가

프로젝트에서 새 기능을 만들거나  
버그를 수정할 때  
기존 안정 버전을 바로 건드리면 위험하다.

예를 들어 로그인 기능을 만들다가  
중간에 코드가 깨질 수도 있다.

이때 branch 가 있으면  
`main` 은 그대로 두고  
별도 branch 에서만 작업할 수 있다.

즉, branch 는  
**안전하게 실험하고 작업을 분리하기 위한 공간**이다.

---

## 3. branch 를 안 나누면 생기는 문제

branch 없이 전부 `main` 에서만 작업하면  
아래 같은 문제가 생긴다.

- 미완성 코드가 main 에 들어감
- 여러 작업이 한꺼번에 섞임
- 협업 시 충돌이 많아짐
- 어떤 작업이 어떤 변경인지 구분 어려움
- rollback 이 복잡해짐

그래서 branch 는  
Git 사용에서 거의 기본이라고 보면 된다.

---

## 4. branch 는 복사본 폴더가 아니다

처음에는 branch 를  
프로젝트 폴더를 통째로 복사한 것처럼 느낄 수 있다.

하지만 Git 에서 branch 는  
실제로는 **특정 commit 흐름을 가리키는 이름표** 에 가깝다.

즉, branch 는  
파일을 통째로 새로 복제하는 개념이 아니라  
작업 이력이 갈라지는 흐름이라고 이해하는 것이 맞다.

---

## 5. branch 생성 예시

새 branch 를 만들 때는 보통 아래처럼 한다.

`git switch -c feat/login`

이 명령은  
현재 위치를 기준으로  
`feat/login` 이라는 새 branch 를 만들고 그 branch 로 이동한다.

즉, 이제부터 commit 은  
`feat/login` 쪽에 쌓이게 된다.

---

## 6. branch 에서 작업하면 어떻게 되나

예를 들어 `main` 에서 `feat/login` 을 만들었다고 하자.

이후 `feat/login` 에서 작업하고 commit 하면  
그 commit 들은 `feat/login` 에 쌓인다.

이 상태에서는  
`main` 은 아직 그대로이다.

즉, branch 를 나눴다는 것은  
작업 이력을 분리했다는 뜻이다.

---

## 7. merge 란 무엇인가

`merge` 는  
따로 작업하던 branch 내용을  
현재 branch 로 가져와 합치는 작업이다.

예를 들어 `feat/login` 에서 로그인 기능 작업을 마쳤다면  
이제 `main` 으로 돌아가서 그 내용을 합칠 수 있다.

example:
`git switch main`  
`git merge feat/login`

이렇게 하면  
`feat/login` 의 작업 결과가 `main` 에 반영된다.

---

## 8. merge 가 필요한 이유

branch 를 계속 나누기만 하면  
작업이 서로 따로 놀게 된다.

결국 완료된 작업은  
기준 branch 에 반영되어야 한다.

즉, branch 는 작업 분리용이고  
merge 는 작업 반영용이다.

둘은 같이 움직이는 개념이다.

---

## 9. merge 할 때 일어나는 일

Git 은 두 branch 의 commit 흐름을 보고  
어떻게 합칠지 계산한다.

보통은 자동으로 잘 합쳐진다.

하지만 같은 파일의 같은 부분을  
서로 다르게 수정했다면 충돌이 날 수 있다.

즉, merge 는  
자동으로 합쳐질 수도 있고  
사람이 직접 정리해야 할 수도 있다.

---

## 10. fast-forward 와 merge commit

작업이 단순하면  
Git 이 그냥 branch 포인터만 앞으로 움직이는 경우가 있다.

이걸 `fast-forward` 라고 한다.

반면 branch 흐름이 갈라져 있으면  
합친 기록을 남기는 별도 merge commit 이 생길 수 있다.

처음에는 여기까지 깊게 몰라도 되지만  
중요한 점은  
merge 결과가 항상 같은 모양은 아니라는 것이다.

---

## 11. 충돌은 왜 생기나

충돌은  
서로 같은 부분을 다르게 수정했을 때 생긴다.

예를 들어

- A 는 `main.c` 의 10번째 줄 수정
- B 도 같은 줄 수정

이런 경우 Git 이  
어느 내용을 남겨야 할지 자동으로 결정하기 어렵다.

그래서 충돌이 나면  
사람이 직접 확인해서 정리해야 한다.

---

## 12. merge 후에는 어떻게 되나

merge 가 끝나면  
작업 내용이 기준 branch 에 반영된다.

그 후에는 보통 아래처럼 정리한다.

- 원격 저장소에 push
- Pull Request 닫힘 또는 merge 완료
- 작업 끝난 branch 삭제

즉, merge 는  
작업 흐름의 끝부분에 해당한다.

---

## 13. branch 와 merge 의 가장 흔한 흐름

1. `main` 최신 상태 받기  
2. 새 branch 생성  
3. 작업  
4. commit  
5. push  
6. Pull Request  
7. merge  
8. 작업 branch 삭제  

이 흐름이 협업에서 가장 흔하다.

---

## 14. branch 전략을 왜 정하나

협업에서는 branch 를 아무 이름이나 쓰고  
아무 때나 merge 하면 관리가 어려워진다.

그래서 보통 아래를 정한다.

- branch 이름 규칙
- main 직접 push 여부
- PR 필수 여부
- merge 방식
- merge 후 branch 삭제 여부

즉, branch 와 merge 는  
기술 개념이면서 동시에 협업 규칙의 핵심이다.

---

## 15. 한 줄 정리

branch 는  
**작업을 안전하게 분리하는 가지**이고,  
merge 는  
**그 가지에서 끝낸 작업을 기준 branch 로 다시 합치는 과정**이다.