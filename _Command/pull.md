# git pull

git pull 명령어는 원격 저장소에서 최신 변경 사항을 가져와 로컬 브랜치에 병합하는 명령어이다. git fetch와 git merge를 한 번에 수행하며, 팀원들이 업데이트한 코드를 로컬에 반영하여 최신 상태로 유지할 수 있게 한다.

 - fetch: 원격 저장소의 변경 사항을 로컬에 가져온다.
 - merge: 가져온 변경 사항을 현재 로컬 브랜치에 병합한다.

## git pull 사용법

```bash
# 현재 브랜치와 연결된 기본 원격 브랜치에서 최신 변경 사항을 가져와 병합
git pull

# 원격 저장소의 브랜치 내용을 현재 브랜치에 병합
git pull {Remote Name} {Remote BranchName}

# Rebase와 함꼐 pull
# 병합 대신 리베이스를 수행하여 히스토리를 깔끔하게 유지
git pull --rebase {Remote Name} {Remote BranchName}
```
