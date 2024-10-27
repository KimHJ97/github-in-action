# git switch

git switch 명령어는 Git에서 브랜치를 전환할 때 사용하는 명령어이다. 이 명령어는 브랜치 이동에 집중된 git checkout의 대체 명령어로, 브랜치를 전환하거나 새 브랜치를 생성하면서 자동으로 이동할 수 있다.

## git switch 사용법

```bash
# 브랜치 변경: 브랜치가 없는 경우 에러 발생
git switch {branchName}

# 새로운 브랜치 생성 및 전환: 브랜치가 존재하는 경우 에러 발생
git switch -c {branchName}

# 이전 브랜치로 전환: 마지막에 체크아웃한 브랜치로 전환
git switch -
```
