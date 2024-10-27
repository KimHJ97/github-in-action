# git status

git status 명령어는 Git 저장소의 현재 상태를 확인하는 명령어로, 작업 디렉토리와 스테이징 영역의 파일 상태를 보여준다. 어떤 파일이 수정되었고, 스테이징 영역에 추가되었거나 커밋되지 않은 파일이 뭉멋인지 쉽게 알 수 있다.

```bash
git status
git status -s
```

## 주요 출력 정보

 - __Untracked files__: Git이 관리하지 않는 파일들로, 새로 생성되었지만 아직 Git에 추가되지 않은 파일들이다. git add 명령어로 스테이징해야 커밋할 수 있다.
 - __Changes not staged for commit__: Git에서 관리 중이지만 아직 스테이징되지 않은 파일이다. 기존에 Git에 추가된 파일이 수정된 경우 이 목록에 나타나며, git add를 통해 스테이징할 수 있다.
 - __Changes to be committed__: 스테이징 영역에 추가되어 커밋할 준비가 된 파일이다. 이 파일들은 git commit을 실행하면 커밋된다.
 - __Branch information__: 현재 브랜치의 이름과 상태를 보여준다. 만약 새로운 커밋이 없으면 "Your branch is up to date"라고 나타나며, 변경 사항이 있다면 "Your branch is ahead" 또는 "Your branch is behind" 등의 메시지가 표시된다.
```bash
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   file1.txt
        new file:   file2.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
        modified:   file3.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        file4.txt
```
