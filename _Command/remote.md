# git remote

git remote 명령어는 Git에서 원격 저장소(remote repository)를 관리할 때 사용하는 명령어이다. 원격 저장소는 GitHub, GitLab, Bitbucket 등의 플랫폼에 위치한 리포지토리로, 팀원들과 코드 변경 사항을 공유하거나 백업 목적으로 사용된다.

 - 원격 저장소 관련 명령어
    - __변경 사항 가져오기__: git fetch, git pull
    - __변경 사항 업로드__: git push
    - __원격 저장소 정보 확인 및 관리__: git remote show, git remote update, git remote prune
    - __원격 브랜치 확인__: git branch -r

## git remote 사용법

```bash
# 원격 저장소 목록 확인
git remote
git remote -v

# 원격 저장소 추가
git remote add {name} {Remote URL}

# 원격 저장소 삭제
git remote remove {name}

# 원격 저장소 이름 변경
git remote rename {currentName} {newName}

# 원격 저장소 정보 확인
git remote show {name}
```
