# git branch

git branch 명령어는 Git에서 브랜치를 관리할 때 사용하는 명령어이다. 브랜치는 Git 저장소 내에서 코드 변경을 독립적으로 관리할 수 있게 해주는 기능으로, 다양한 기능 개발이나 버그 수정을 위해 분기점을 만들고 작업을 할 수 있다.

 - __독립적 작업 환경 제공__: 브랜치를 사용하면 메인 브랜치와 독립적으로 새로운 기능을 개발하거나 버그를 수정할 수 있다.
 - __협업 및 코드 관리__: 각 작업이 독립된 브랜치에서 이루어지므로, 여러 사람이 동시에 작업해도 메인 코드베이스에 영향을 주지 않는다.

## git branch 사용법

```bash
# 브랜치 목록 확인
git branch # 로컬 브랜치 확인
git branch -a

# 새로운 브랜치 생성: 이미 존재하면 에러 발생
git branch {branchName}

# 브랜치 삭제
git branch -d {branchName}
git branch -D {branchName} # 강제 삭제

# 현재 브랜치 이름 변경
git branch -m {newBranchName}
```

 - 원격 저장소 관련 명령어
```bash
# 원격 브랜치 확인
git branch -r

# 로컬 현재 브랜치를 원격 브랜치에 연결
git branch --set-upstream-to={Remote Name}/{Remote Branch}

# 원격 브랜치 연결 확인
git branch -vv
```