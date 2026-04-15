# Git Command Manual

Git 설치, 기본 사용법, 협업 흐름, 규칙, 자주 발생하는 오류 상황을 빠르게 찾기 위한 문서 모음입니다.

## Table of Contents

- [Directory Structure](#directory-structure)
- [1. Install](#1-install)
- [2. Git Function](#2-git-function)
- [3. Git Usage](#3-git-usage)
- [4. Git Error Situation](#4-git-error-situation)
- [5. Rules](#5-rules)
- [6. Guide](#6-guide)
- [7. Recommended Reading Order](#7-recommended-reading-order)
- [8. Quick Start](#8-quick-start)
- [9. Quick Links](#9-quick-links)
- [10. Notes](#10-notes)

---

## Directory Structure

- `install/` : Git 설치 및 SSH 설정
- `docs/git-Function/` : Git 핵심 개념 설명
- `docs/git-usage/` : Git 명령어별 사용법
- `docs/git-error-situation/` : 자주 발생하는 오류와 해결 방법
- `docs/rule/` : 협업 및 저장소 운영 규칙
- `guide/` : Git 동작 방식과 협업 흐름 가이드

---

## 1. Install

- [Git 설치 가이드](./install/Git-install.md)
- [Git SSH 설정](./install/Git-ssh.md)

---

## 2. Git Function

- [Git SSH](./docs/git-Function/Git-SSH.md)
- [Git Conflict](./docs/git-Function/Git-conflict.md)

---

## 3. Git Usage

### Basic

- [Init](./docs/git-usage/init.md)
- [Clone](./docs/git-usage/clone.md)
- [Add](./docs/git-usage/add.md)
- [Commit](./docs/git-usage/commit.md)
- [Push](./docs/git-usage/push.md)
- [Upload](./docs/git-usage/Upload.md)
- [Pull Request](./docs/git-usage/Pull-Request.md)

### Check

- [Status](./docs/git-usage/Status.md)
- [Log](./docs/git-usage/Log.md)
- [Diff](./docs/git-usage/diff.md)

### Branch / Remote

- [Branch](./docs/git-usage/Branch.md)
- [Switch / Checkout](./docs/git-usage/switch-checkout.md)
- [Merge](./docs/git-usage/merge.md)
- [Fetch](./docs/git-usage/fetch.md)
- [Remote](./docs/git-usage/remote.md)
- [Tag](./docs/git-usage/tag.md)

### Config / Repository

- [Config](./docs/git-usage/config.md)
- [Repository Create](./docs/git-usage/repo-create.md)
- [Ignore](./docs/git-usage/ignore.md)

### Recovery / Cleanup

- [Restore](./docs/git-usage/restore.md)
- [Reset / Revert](./docs/git-usage/reset-revert.md)
- [Stash](./docs/git-usage/stash.md)
- [Remove / Move](./docs/git-usage/rm-mv.md)

---

## 4. Git Error Situation

### Push / Branch

- [Everything up-to-date](./docs/git-error-situation/Everything-up-to-date.md)
- [src refspec main does not match any](./docs/git-error-situation/src-refspec-main-does-not-match-any.md)
- [failed to push some refs / non-fast-forward](./docs/git-error-situation/failed-to-push-non-fast-forward.md)
- [remote origin already exists](./docs/git-error-situation/remote-origin-already-exists.md)

### SSH / Remote

- [Permission denied (publickey)](./docs/git-error-situation/permission-denied-publickey.md)

### Repository / History

- [fatal: not a git repository](./docs/git-error-situation/fatal-not-a-git-repository.md)
- [Detached HEAD](./docs/git-error-situation/detached-head.md)
- [refusing to merge unrelated histories](./docs/git-error-situation/refusing-to-merge-unrelated-histories.md)

### Conflict / Line Ending

- [Merge Conflict](./docs/git-error-situation/merge-conflict.md)
- [LF will be replaced by CRLF](./docs/git-error-situation/lf-will-be-replaced-by-crlf.md)

---

## 5. Rules

- [Branch Rule](./docs/rule/Branch-rule.md)
- [Code Review Rule](./docs/rule/Code-Review-rule.md)
- [Conflict Rule](./docs/rule/Conflict-rule.md)
- [Gitignore Rule](./docs/rule/Gitignore-rule.md)
- [Issue Rule](./docs/rule/Issue-rule.md)
- [Merge Rule](./docs/rule/Merge-rule.md)
- [Pull Request Rule](./docs/rule/Pull-Request-rule.md)
- [Pull Rule](./docs/rule/Pull-rule.md)
- [Push Rule](./docs/rule/Push-Rule.md)
- [Release Rule](./docs/rule/Release-rule.md)
- [Repository Rule](./docs/rule/Repository-rule.md)
- [Tag Rule](./docs/rule/Tag-rule.md)
- [Commit Rule](./docs/rule/commit-rule.md)

---

## 6. Guide

- [What is Git](./guide/what-is-git.md)
- [How Git Works](./guide/How-Git-Works.md)
- [Remote and Local](./guide/Remote-and-Local.md)
- [Git Workflow](./guide/Git-Workflow.md)
- [Branch and Merge](./guide/Branch-and-Merge.md)
- [Collaboration Flow](./guide/Collaboration-Flow.md)

---

## 7. Recommended Reading Order

### For Beginners

1. [What is Git](./guide/what-is-git.md)
2. [How Git Works](./guide/How-Git-Works.md)
3. [Git 설치 가이드](./install/Git-install.md)
4. [Git SSH 설정](./install/Git-ssh.md)
5. [Init](./docs/git-usage/init.md)
6. [Add](./docs/git-usage/add.md)
7. [Commit](./docs/git-usage/commit.md)
8. [Push](./docs/git-usage/push.md)

### For Collaboration

1. [Branch](./docs/git-usage/Branch.md)
2. [Switch / Checkout](./docs/git-usage/switch-checkout.md)
3. [Merge](./docs/git-usage/merge.md)
4. [Pull Request](./docs/git-usage/Pull-Request.md)
5. [Collaboration Flow](./guide/Collaboration-Flow.md)
6. [Git Workflow](./guide/Git-Workflow.md)

### For Rules

1. [Commit Rule](./docs/rule/commit-rule.md)
2. [Branch Rule](./docs/rule/Branch-rule.md)
3. [Push Rule](./docs/rule/Push-Rule.md)
4. [Pull Request Rule](./docs/rule/Pull-Request-rule.md)
5. [Merge Rule](./docs/rule/Merge-rule.md)
6. [Code Review Rule](./docs/rule/Code-Review-rule.md)

### For Troubleshooting

1. [Everything up-to-date](./docs/git-error-situation/Everything-up-to-date.md)
2. [Permission denied (publickey)](./docs/git-error-situation/permission-denied-publickey.md)
3. [Merge Conflict](./docs/git-error-situation/merge-conflict.md)
4. [Detached HEAD](./docs/git-error-situation/detached-head.md)
5. [fatal: not a git repository](./docs/git-error-situation/fatal-not-a-git-repository.md)

---

## 8. Quick Start

처음부터 Git을 사용하는 경우 아래 순서대로 보면 됩니다.

1. [Git 설치 가이드](./install/Git-install.md)
2. [Git SSH 설정](./install/Git-ssh.md)
3. [What is Git](./guide/what-is-git.md)
4. [Init](./docs/git-usage/init.md)
5. [Add](./docs/git-usage/add.md)
6. [Commit](./docs/git-usage/commit.md)
7. [Push](./docs/git-usage/push.md)

---

## 9. Quick Links

- 저장소 처음 만들기 → [Init](./docs/git-usage/init.md)
- 원격 저장소 연결 → [Remote](./docs/git-usage/remote.md)
- 파일 올리기 → [Add](./docs/git-usage/add.md), [Commit](./docs/git-usage/commit.md), [Push](./docs/git-usage/push.md)
- 브랜치 작업 → [Branch](./docs/git-usage/Branch.md), [Switch / Checkout](./docs/git-usage/switch-checkout.md)
- 협업 흐름 → [Collaboration Flow](./guide/Collaboration-Flow.md)
- 충돌 해결 → [Git Conflict](./docs/git-Function/Git-conflict.md), [Merge Conflict](./docs/git-error-situation/merge-conflict.md)
- SSH 문제 → [Git SSH 설정](./install/Git-ssh.md), [Permission denied (publickey)](./docs/git-error-situation/permission-denied-publickey.md)

---

## 10. Notes

이 문서는 아래 목적에 맞게 분리되어 있습니다.

- 명령어를 빠르게 찾고 싶을 때 → `docs/git-usage/`
- 오류 해결법을 찾고 싶을 때 → `docs/git-error-situation/`
- 팀 규칙을 확인하고 싶을 때 → `docs/rule/`
- Git이 실제로 어떻게 동작하는지 이해하고 싶을 때 → `guide/`