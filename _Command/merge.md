# git merge

git merge 명령어는 다른 브랜치의 변경 사항을 현재 브랜치에 병합하여 하나의 커밋 히스토리로 만드는 명령어이다.

## git merge 사용법

```bash
# 현재 브랜치에 다른 브랜치에 커밋 이력 병합
git merge {branchName}

# --no-ff (No fast-forward 병합)
# Fast-forward 병합을 방지하고, 강제로 병합 커밋을 생성한다.
git merge --no-ff {branchName}

# --squash (커밋 압축)
# 병합하는 브랜치의 모든 커밋을 하나의 커밋으로 압축하여 병합한다.
git merge --squash {branchName}

# --abort (병합 중단)
# 병합 중 충돌이 발생한 경우, 병합을 중단하고 병합 전 상태로 되돌린다.
git merge --abort
```

## 병합시 충돌 해결 과정

```bash
# 1. 병합 시도 -> 충돌
git merge {branchName}

# 2. 충돌 파일 확인
git status

# 3. 충돌 파일을 열면 아래와 같은 형식으로 충돌 코드가 표시된다.
<<<<<<< HEAD
// 현재 브랜치의 코드
=======
// 병합하려는 브랜치의 코드
>>>>>>> <브랜치_이름>

# 4. 충돌 파일을 수정하고, 수정된 파일 스테이징
git add {fileName}

# 5. 병합 완료
git commit
```
