# git add

git add 명령어는 Git 저장소에서 변경된 파일들을 스테이징(staging) 영역에 추가하는 명령어로 스테이징 영역에 있는 파일들은 다음 커밋에 포함될 준비가 된 상태가 되며, 이후 git commit 명령어로 실제 저장소 히스토리에 기록된다.

## git add 명령어 사용법

```bash
# 기본 사용법
git add {fileName}

# 여러 파일 추가
git add {file1} {file2}

# 모든 변경 사항 추가
git add .

# 특정 디렉토리 내 모든 파일 추가
git add {디렉토리명}/

# Tracked 파일의 변경 사항만 추가(이미 Git에 등록된 파일의 변경 사항만)
git add -u
```
