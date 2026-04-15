# GitHub Username 변경 후 체크리스트

GitHub username을 변경하면  
기존 저장소 링크는 대부분 새 username으로 리다이렉트되지만,  
문서나 설정 파일 안에 직접 적어 둔 계정명과 URL은 따로 점검하는 것이 좋다.

이 문서는 GitHub username 변경 후 확인해야 할 항목을 정리한 것이다.

---

## 1. 현재 remote 확인

현재 로컬 저장소가 어떤 주소를 바라보고 있는지 먼저 확인한다.

```bash
git remote -v
```

---

## 2. HTTPS 사용 시 remote URL 변경

기존 username이 포함된 주소를 새 username 기준으로 변경한다.

```bash
git remote set-url origin https://github.com/deploy103/<repository-name>.git
```

예시:

```bash
git remote set-url origin https://github.com/deploy103/git-command-manual.git
```

---

## 3. SSH 사용 시 remote URL 변경

SSH 방식으로 연결 중이라면 아래처럼 변경한다.

```bash
git remote set-url origin git@github.com:deploy103/<repository-name>.git
```

예시:

```bash
git remote set-url origin git@github.com:deploy103/git-command-manual.git
```

---

## 4. 변경 확인

remote 주소가 정상적으로 변경되었는지 다시 확인한다.

```bash
git remote -v
```

---

## 5. README / 문서 / 블로그 / 노션 링크 수정

문서 안에 예전 GitHub 프로필 링크가 들어가 있다면 새 username으로 수정한다.

### before

```text
https://github.com/youghwjdkill1
```

### after

```text
https://github.com/deploy103
```

저장소 링크는 리다이렉트될 수 있어도,  
프로필 링크나 직접 적어 둔 주소는 수동 점검이 필요하다.

---

## 6. 문서 안의 계정 멘션 수정

문서, 협업 가이드, 설명 파일 안에 예전 username이 적혀 있다면 함께 수정한다.

### before

```text
@youghwjdkill1
```

### after

```text
@deploy103
```

---

## 7. CODEOWNERS 파일 확인

`CODEOWNERS` 파일 안에 예전 username이 들어 있으면 직접 수정해야 한다.

### example

```text
* @deploy103
```

---

## 8. GitHub Actions / 배포 설정 / 스크립트 점검

workflow 파일, 배포 스크립트, 설명 문서 안에 예전 username이 남아 있을 수 있다.

현재 디렉터리에서 한 번에 찾으려면:

```bash
grep -R "youghwjdkill1" .
```

---

## 9. 여러 저장소를 쓰는 경우

현재 상위 폴더 아래에 Git 저장소가 어디 있는지 확인하려면:

```bash
find . -name ".git" -type d -prune
```

각 저장소마다 들어가서 `git remote -v`를 확인하고 필요한 경우 수정한다.

---

## 10. 정리

GitHub username을 변경했다고 해서 모든 설정이 즉시 깨지는 것은 아니다.  
하지만 아래 항목은 직접 점검하는 것이 안전하다.

- remote URL
- README 및 문서 링크
- 프로필 링크
- 계정 멘션
- CODEOWNERS
- workflow / deploy 스크립트
- clone 안내문

즉,  
**"당장 동작은 할 수 있어도, 문서와 설정은 새 username 기준으로 정리하는 것이 좋다."**