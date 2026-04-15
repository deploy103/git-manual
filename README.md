# Git Command Manual

Git 사용법, 설치법, 기능 설명, 오류 상황을 빠르게 찾기 위한 문서 모음입니다.

---

## 1. Install

- [Git 설치 가이드](./install/Git-install.md)
- [Git SSH 설정법](./install/Git-ssh.md)

---

## 2. Git Function

- [Git SSH란?](./docs/git-Function/Git-SSH.md)
- [Git Conflict란?](./docs/git-Function/Git-confilct.md)

---

## 3. Git Usage

### 기본 사용
- [Init](./docs/git-usage/init.md)
- [Add](./docs/git-usage/add.md)
- [Commit](./docs/git-usage/commit.md)
- [Push](./docs/git-usage/push.md)
- [Upload](./docs/git-usage/Upload.md)
- [Clone](./docs/git-usage/clone.md)
- [Remote](./docs/git-usage/remote.md)
- [Config](./docs/git-usage/config.md)
- [Repository Create](./docs/git-usage/repo-create.md)

### 확인
- [Status](./docs/git-usage/Status.md)
- [Log](./docs/git-usage/Log.md)
- [Diff](./docs/git-usage/diff.md)

### 브랜치 / 협업
- [Branch](./docs/git-usage/Branch.md)
- [Switch / Checkout](./docs/git-usage/switch-checkout.md)
- [Merge](./docs/git-usage/merge.md)
- [Fetch](./docs/git-usage/fetch.md)
- [Pull Request](./docs/git-usage/Pull-Request.md)

### 복구 / 정리
- [Restore](./docs/git-usage/restore.md)
- [Reset / Revert](./docs/git-usage/reset-revert.md)
- [Stash](./docs/git-usage/stash.md)
- [Remove / Move](./docs/git-usage/rm-mv.md)
- [Ignore](./docs/git-usage/ignore.md)

### 기타
- [Tag](./docs/git-usage/teg.md)

---

## 4. Git Error Situation

### push / branch 관련
- [Everything up-to-date](./docs/git-error-situation/Everything-up-to-date.md)
- [src refspec main does not match any](./docs/git-error-situation/src-refspec-main-does-not-match-any.md)
- [failed to push some refs / non-fast-forward](./docs/git-error-situation/failed-to-push-non-fast-forward.md)
- [remote origin already exists](./docs/git-error-situation/remote-origin-already-exists.md)

### SSH / remote 관련
- [Permission denied (publickey)](./docs/git-error-situation/permission-denied-publickey.md)

### repository / history 관련
- [fatal: not a git repository](./docs/git-error-situation/fetal-not-a-git-repository.md)
- [Detached HEAD](./docs/git-error-situation/detached-head.md)
- [refusing to merge unrelated histories](./docs/git-error-situation/refusing-to-merge-unrelated-histories.md)

### conflict / line ending 관련
- [Merge Conflict](./docs/git-error-situation/merge-conflict.md)
- [LF will be replaced by CRLF](./docs/git-error-situation/lf-will-be-replaced-by-crlf.md)

---

## 5. 빠르게 찾기

### 처음 Git 쓰는 경우
1. [Git 설치](./install/Git-install.md)
2. [Git SSH 설정](./install/Git-ssh.md)
3. [Init](./docs/git-usage/init.md)
4. [Add](./docs/git-usage/add.md)
5. [Commit](./docs/git-usage/commit.md)
6. [Push](./docs/git-usage/push.md)

### 브랜치 작업할 때
1. [Branch](./docs/git-usage/Branch.md)
2. [Switch / Checkout](./docs/git-usage/switch-checkout.md)
3. [Merge](./docs/git-usage/merge.md)
4. [Pull Request](./docs/git-usage/Pull-Request.md)

### 에러가 났을 때
- push가 안 될 때 → [Everything up-to-date](./docs/git-error-situation/Everything-up-to-date.md), [failed to push some refs / non-fast-forward](./docs/git-error-situation/failed-to-push-non-fast-forward.md)
- SSH 문제일 때 → [Git SSH 설정법](./install/Git-ssh.md), [Permission denied (publickey)](./docs/git-error-situation/permission-denied-publickey.md)
- merge 충돌일 때 → [Git Conflict란?](./docs/git-Function/Git-confilct.md), [Merge Conflict](./docs/git-error-situation/merge-conflict.md)
- 저장소 인식이 안 될 때 → [fatal: not a git repository](./docs/git-error-situation/fetal-not-a-git-repository.md)

---

## 6. 추천 문서 읽는 순서

1. [Git 설치 가이드](./install/Git-install.md)
2. [Git SSH 설정법](./install/Git-ssh.md)
3. [Git SSH란?](./docs/git-Function/Git-SSH.md)
4. [Init](./docs/git-usage/init.md)
5. [Add](./docs/git-usage/add.md)
6. [Commit](./docs/git-usage/commit.md)
7. [Push](./docs/git-usage/push.md)
8. [Branch](./docs/git-usage/Branch.md)
9. [Pull Request](./docs/git-usage/Pull-Request.md)
10. [Git Conflict란?](./docs/git-Function/Git-confilct.md)

---

## 7. 참고

현재 링크는 **지금 네 디렉터리 구조 그대로** 맞춘 상태다.  
