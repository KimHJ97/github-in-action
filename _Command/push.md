# git push

git push 명령어는 로컬 Git 저장소의 변경 사항을 원격 저장소(remote repository)로 업로드하는 데 사용됩니다. 이 명령어는 협업 환경에서 팀원들과 코드 변경 사항을 공유하고, 원격 저장소에 업데이트된 버전을 배포하는 데 필수적이다.

 - 로컬 저장소의 변경 사항(커밋 이력)을 원격 저장소에 업로드한다.

## git push 사용법

```bash
# 현재 브랜치를 원격 저장소에 반영
git push

# 로컬 브랜치의 커밋 이력을 원격 저장소에 반영
git push {Remote Name} {Local BranchName}

# -u 옵션: 처음 푸시할 때 해당 옵션을 사용하여 로컬 브랜치와 원격 브랜치를 연결할 수 있다.
# 이후부터는 git push만 입력해도 연결된 브랜치로 쉽게 푸시할 수 있다.
# 원격 저장소에 Local Branch 이름과 동일한 브랜치가 생성되며, 연결된다.
git push -u {Remote Name} {Local BranchName}
```
