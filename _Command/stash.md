# git stash

git stash 명령어는 현재 작업 중인 변경 사항을 임시로 저장하여 작업 디렉토리를 깨끗하게 비우고 다른 작업을 할 수 있도록 도와주는 명령어이다.

 - 커밋하지 않은 변경 사항을 스택(Stack) 형태로 저장해 두었다가, 나중에 다시 적용할 수 있다.
 - 스테이징이 올라간 파일이나, Modified 상태로 작업 디렉토리에 있는 파일들을 저장소에 보관한다.

## git stash 사용법

```bash
# 스테이징 된 변경 사항과 함께 스택에 저장
git stash

# 스테이징 하지 않은 변경 사항만 스택에 저장 (-u 옵션)
# 스테이징하지 않은 파일과 untracked 파일까지 모두 stash에 저장
git stash -u

# 스택에 이름 붙여 저장
git stash save "이름"

# 임시 저장된 작업 확인
git stash list

# 저장된 작업 적용: 가장 최근의 stash를 적용하여 저장했던 변경 사항을 가져온다.
git stash apply

# 저장된 작업 적용 후 제거
git stash pop

# 특정 stash 적용
git stash apply stash@{n}

# 특정 stash 제거
git stash drop stash@{n}

# 모든 stash 제거
git stash clear
```
