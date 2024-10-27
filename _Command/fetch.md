# git fetch

git fetch 명령어는 원격 저장소의 변경 사항을 가져와 로컬 저장소에 업데이트하는 명령어이다. git fetch는 원격의 최신 커밋들을 로컬 저장소에 복사해오지만, 로컬 브랜치에는 병합하지 않으므로 커밋 히스토리를 안전하게 유지할 수 있다. 이후 필요에 따라 변경 사항을 로컬 브랜치에 병합(git merge)하거나, 새로운 브랜치로 확인할 수 있다.

## git fetch 사용법

```bash
# 원격 저장소 최신 변경 사항 가져오기
git fetch {Remote Name}

# 원격 저장소 특정 브랜치의 최신 변경 사항 가져오기
git fetch {Remote Name} {Remote BranchName}

# 원격 저장소에 삭제된 브랜치를 로컬에 반영
git fetch --prune
```

## git fetch 사용 예시

```bash
# 원격 저장소 변경 사항 가져오기
git fetch origin main

# 로컬 브랜치에 변경 사항 병합
git switch main
git merge origin/main
```
