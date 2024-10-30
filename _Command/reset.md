# git reset

it reset 명령어는 Git에서 커밋, 스테이징, 작업 디렉토리의 상태를 이전 상태로 되돌릴 때 사용하는 강력한 명령어이다. 주로 특정 커밋으로 이동하거나, 특정 파일의 스테이징 상태를 해제할 때 사용된다.

 - git reset은 되돌리는 범위에 따라 --soft, --mixed, --hard 옵션을 통해 세 가지 방식으로 사용할 수 있다.
 - --soft 옵션: 커밋의 변경 사항을 스테이징 영역에 유지한다.
 - --mixed 옵션(default): 커밋의 변경 사항을 작업 디렉토리에 남겨둔다.
 - --hard 옵션: 커밋의 변경 사항을 스테이징과 작업 디렉토리 모두에서 삭제한다.

## git reset 사용법

```bash
# 마지막 커밋 되돌리기
git reset --soft HEAD~1
git reset HEAD~1 # 스테이징 해제
git reset --hard HEAD~1 # 완전히 삭제

# 특정 파일 스테이징 해제
git reset {fileName}
```
