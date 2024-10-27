# git checkout

git checkout 명령어는 Git에서 브랜치나 특정 커밋으로 이동하거나, 특정 파일의 상태를 이전 버전으로 되돌릴 때 사용한다. 이 명령어는 주로 브랜치를 전환하거나 특정 커밋을 체크아웃할 때 많이 사용되며, 최근에는 브랜치 전환 목적으로 git switch 명령어가 권장되기도 한다.

 - 브랜치 전환시 git switch 명령어 사용이 권장된다. git checkout에는 여러 기능이 포함된다.
 - git checkout 기능
    - 브랜치 전환: 작업 브랜치를 이동하거나 새 브랜치를 생성하면서 이동할 때 사용한다.
    - 특정 커밋 상태로 이동: 특정 커밋 시점으로 코드를 확인하고자 할 때 유용하다.
    - 파일 복원: 지정된 파일을 이전 상태로 되돌릴 때 사용한다.

## git checkout 사용법

```bash
# 브랜치 변경: 브랜치가 존재하는 경우에 이동된다.
git checkout {branchName}

# 브랜치 생성 및 변경: 이미 존재하는 경우 에러 발생
git checkout -b {branchName}

# 특정 커밋으로 체크아웃
# "detached HEAD" 상태가 되며, 브랜치가 아닌 특정 커밋 시점으로 이동한다.
# 기존 브랜치와 연결되지 않은 새로운 히스토리 상태이다.
git checkout {Commit ID}

# 파일 되돌리기: 특정 파일을 지정한 브랜치 버전으로 되돌린다.
git checkout {branchName} -- {fileName}
```

## git checkout 사용 예시

```bash
# develop 브랜치로 전환
git checkout develop

# 새로운 브랜치 feature/signup을 생성하고, 해당 브랜치로 이동
git checkout -b feature/signup

# app.js 파일을 현재 브랜치의 바로 이전 커밋(HEAD~1) 상태로 되돌린다.
git checkout HEAD~1 -- app.js

# a1b2c3d 커밋 해시를 체크아웃하여, 그 시점으로 이동
git checkout a1b2c3d
```
