# git init

git init 명령어는 새로운 Git 저장소를 생성할 때 사용하는 명령어로, 실행하면 해당 디렉토리에 .git이라는 숨겨진 폴더가 생성되고, 이곳에 Git이 버전 관리를 위한 정보와 데이터를 저장하게 된다.
 - Git 저장소 초기화 라고도 한다.
 - 초기화된 저장소에서 git add, git commit 등의 명령어를 사용하여 파일과 변경 사항을 관리할 수 있다.
```bash
git init
```

## 기본 사용 예시

```bash
git init
echo "Hello Git" >> README.md
git add .
git commit -m "Initial Commit"
```