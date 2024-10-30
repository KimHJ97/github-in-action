# git rebase

git rebase 명령어는 한 브랜치의 변경 사항을 다른 브랜치 위로 옮겨서 커밋 히스토리를 깔끔하게 정리하는 데 사용된다. 특히 기능 개발 브랜치를 메인 브랜치 위에 다시 쌓아 정리할 때 유용하며, merge와 달리 병합 커밋을 생성하지 않아서 히스토리가 간결해진다.

## git rebase 사용법

 - Interactive Rebase (-i 옵션)
    - 커밋을 정리할 때 -i 옵션을 사용하여 커밋 순서를 재정렬하거나, 커밋 메시지를 수정하거나, 여러 커밋을 하나로 합칠 수 있다.
    - pick, squash, edit 등의 명령어를 통해 원하는 대로 조작할 수 있다.
```bash
git rebase -i {branchName}
```

 - Continue (--continue 옵션)
    - 리베이스 도중 충돌이 발생한 후 충돌을 해결하고 나서, 리베이스를 계속 진행할 때 사용한다.
```bash
git rebase --continue
```

 - Abort (--abort 옵션)
    - 리베이스 중 충돌을 해결하지 않고 리베이스를 중단하고 싶을 때 사용한다.
```bash
git rebase --abort
```

 - Skip (--skip 옵션)
    - 충돌이 발생한 커밋을 건너뛰고 다음 커밋으로 넘어가 리베이스를 진행할 때 사용한다.
```bash
git rebase --skip
```
