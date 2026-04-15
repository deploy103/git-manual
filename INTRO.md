# INTRO

이 저장소는 Git을 처음 배우는 사람, 협업 중 Git 때문에 막히는 사람, 그리고 필요한 내용을 빠르게 찾아보고 싶은 사람을 위해 만든 Git 문서 정리 저장소입니다.

처음 Git을 접하면 `add`, `commit`, `push`, `pull`, `merge`, `branch` 같은 기본 명령어도 헷갈리기 쉽고, 작업을 하다 보면 `Everything up-to-date`, `Permission denied (publickey)`, `Detached HEAD`, `Merge Conflict` 같은 오류를 만나면서 더 어렵게 느껴질 수 있습니다.

이 저장소는 그런 과정을 조금 더 쉽게 만들기 위해 정리되었습니다.  
단순히 명령어만 나열하는 것이 아니라, 아래와 같은 흐름으로 필요한 내용을 바로 찾을 수 있게 구성하는 것을 목표로 했습니다.

- 설치가 필요하면 설치 문서로 이동
- 명령어 사용법이 필요하면 usage 문서로 이동
- 오류가 발생하면 error 문서로 이동
- 협업 규칙이 필요하면 rule 문서로 이동
- Git이 실제로 어떻게 동작하는지 이해하고 싶다면 guide 문서로 이동

---

## Why This Repository Exists

Git은 개발에서 거의 기본처럼 사용되지만, 처음 배우는 입장에서는 어렵게 느껴질 수 있습니다.

특히 아래와 같은 부분에서 많이 막힙니다.

- 로컬과 원격 저장소의 차이
- branch를 왜 나누는지
- merge는 어떻게 되는지
- fetch와 pull의 차이
- reset과 revert의 차이
- conflict가 왜 발생하는지
- SSH 설정은 왜 필요한지
- push가 안 될 때 어디부터 확인해야 하는지

이 저장소는 이런 문제를 한 번에 정리해서, 누군가가 나처럼 같은 부분에서 오래 헤매지 않도록 만들었습니다.

---

## Who This Repository Is For

이 저장소는 아래와 같은 사람을 대상으로 합니다.

- Git을 처음 배우는 사람
- 팀 프로젝트를 시작하는 학생
- branch, merge, pull request 흐름이 헷갈리는 사람
- Git 오류가 발생했을 때 빠르게 해결법을 찾고 싶은 사람
- 협업용 Git 규칙을 문서로 정리하고 싶은 사람

---

## What This Repository Contains

이 저장소는 크게 다섯 가지 영역으로 구성되어 있습니다.

### 1. Install
Git 설치와 SSH 설정 방법을 정리한 문서입니다.

Git을 처음 설치하거나, GitHub와 SSH 연결을 해야 할 때 먼저 보면 됩니다.

### 2. Git Function
Git에서 자주 나오는 개념을 설명하는 문서입니다.

예를 들어 SSH가 무엇인지, conflict가 무엇인지처럼 개념 자체를 이해할 때 참고할 수 있습니다.

### 3. Git Usage
실제로 자주 사용하는 Git 명령어들을 문서별로 나누어 정리한 영역입니다.

`init`, `add`, `commit`, `push`, `clone`, `branch`, `merge`, `fetch`, `remote`, `tag` 등 기본 명령어부터 협업 과정에서 자주 쓰는 명령어까지 확인할 수 있습니다.

### 4. Git Error Situation
Git을 사용하면서 자주 만나는 오류 상황과 해결 방향을 정리한 영역입니다.

에러 문장을 보고 바로 해당 문서로 이동해서 원인과 해결 방법을 찾는 용도로 만들었습니다.

### 5. Rule
협업할 때 필요한 규칙들을 정리한 영역입니다.

commit 메시지 규칙, branch 규칙, merge 규칙, pull request 규칙, release 규칙 등을 문서로 분리해 두었습니다.

### 6. Guide
Git이 실제로 어떻게 동작하는지, 로컬과 원격은 어떤 차이가 있는지, 협업은 어떤 흐름으로 진행되는지를 이해하기 위한 가이드 문서입니다.

단순히 명령어를 외우는 것이 아니라, Git의 흐름 자체를 이해하는 데 목적이 있습니다.

---

## What I Wanted To Make

이 저장소를 만들면서 가장 중요하게 생각한 것은 아래 세 가지입니다.

### Easy to Find
필요한 내용을 빠르게 찾을 수 있어야 합니다.

처음 배우는 사람은 긴 설명보다 지금 필요한 문서에 바로 도달하는 것이 더 중요할 때가 많습니다.  
그래서 문서를 사용법, 오류, 규칙, 가이드로 나누어 접근하기 쉽게 구성했습니다.

### Easy to Read
설명은 가능한 한 복잡하지 않게 정리하려고 했습니다.

처음부터 Git의 내부 구조를 깊게 설명하기보다, 먼저 쓰는 방법과 흐름을 이해하고, 그 다음에 원리를 이해할 수 있도록 구성하는 방향을 목표로 했습니다.

### Useful for Collaboration
혼자 쓰는 Git이 아니라, 같이 작업할 때도 도움이 되도록 만들고 싶었습니다.

branch 전략, commit 메시지 규칙, pull request 규칙, merge 규칙처럼 팀 협업에서 실제로 필요한 문서들도 함께 정리한 이유가 여기에 있습니다.

---

## Recommended Way To Use This Repository

이 저장소를 처음 보는 경우에는 아래 순서로 읽는 것을 추천합니다.

1. `README.md` 에서 전체 구조 확인
2. `guide/what-is-git.md` 로 Git의 기본 개념 이해
3. `guide/How-Git-Works.md` 로 Git 동작 방식 이해
4. `install/` 문서로 설치 및 SSH 설정
5. `docs/git-usage/` 문서로 기본 명령어 학습
6. 필요할 때 `docs/git-error-situation/` 에서 오류 해결
7. 팀 프로젝트라면 `docs/rule/` 문서로 협업 규칙 확인

---

## Final Note

이 저장소는 완벽한 Git 사전이라기보다, Git을 배우고 사용하는 과정에서 자주 막히는 지점을 빠르게 해결할 수 있도록 정리한 실용 문서 모음에 가깝습니다.

누군가가 Git 때문에 필요 이상으로 오래 막히지 않고, 필요한 문서를 바로 찾고, 바로 이해하고, 바로 적용할 수 있게 만드는 것이 이 저장소의 목적입니다.