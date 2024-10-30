# Git 다양한 설정 파일

Git에서는 .gitignore나 .gitattributes 외에도 여러 설정 파일을 통해 다양한 환경과 설정을 관리할 수 있습니다.

 - __.gitconfig__
    - Git의 전역 또는 로컬 설정을 관리하는 파일입니다. 사용자 정보, alias, 자동 줄 끝 변환, diff/merge 도구 설정 등을 정의할 수 있습니다.
    - 전역 설정은 사용자 홈 디렉터리에 위치한 ~/.gitconfig에서, 로컬 설정은 특정 Git 저장소의 .git/config 파일에서 관리됩니다.
```
[user]
  name = Your Name
  email = you@example.com
[core]
  editor = code
  autocrlf = input
```

 - __.gitmodules__
    - 서브모듈(Submodule) 설정을 관리하는 파일로, 특정 Git 저장소 내에 다른 Git 저장소를 포함하는 경우 사용합니다.
    - 프로젝트 루트에 위치하며, 서브모듈의 URL과 경로 등을 정의하여 서브모듈의 동기화 및 업데이트를 관리할 수 있습니다.
```
[submodule "libs/my-submodule"]
  path = libs/my-submodule
  url = https://github.com/user/my-submodule.git
```

 - __.mailmap__
    - 여러 이메일이나 이름을 사용하는 커밋 히스토리를 정리하여, 동일한 사람으로 인식하게 만드는 파일입니다.
    - 예를 들어, john@example.com과 john.doe@example.com이 모두 동일 인물로 표시되도록 정리할 수 있습니다.
```
John Doe <john@example.com> <john.doe@example.com>
```

 - __.git/hooks/__
    - Git은 특정 이벤트 발생 시 자동으로 실행되는 스크립트를 hooks 디렉토리에 저장합니다. 예를 들어, 커밋 전후, 푸시 전후에 실행되는 스크립트를 통해 코드 스타일 검사, 테스트 실행 등 자동화를 설정할 수 있습니다.
    - Git은 이 폴더에 pre-commit, post-commit, pre-push 등의 예시 훅 파일을 제공하며, 사용자는 이 파일에 직접 명령어를 추가해 설정할 수 있습니다.
    - pre-commit 훅은 커밋을 하기 전 실행됩니다. 커밋하기 전에 코드 스타일 검사, 테스트 실행, 파일 포맷팅 등을 자동으로 수행하는 데 유용합니다.
    - prepare-commit-msg 훅은 커밋 메시지가 편집되기 전에 실행되며, 자동으로 메시지에 정보를 추가할 때 유용합니다.
    - commit-msg 훅은 커밋 메시지를 검증하여 규칙에 맞지 않으면 커밋을 막는 데 사용합니다.
    - pre-push 훅은 푸시하기 전에 실행되며, 푸시 전에 테스트를 실행하거나 코드를 검토할 수 있습니다.
    - post-checkout 훅은 브랜치 변경, git checkout을 통해 파일을 체크아웃한 후 실행됩니다. 특정 브랜치 체크아웃 시 환경 설정을 변경하는 데 유용합니다.
```sh
#!/bin/sh
# .git/hooks/pre-commit

# JavaScript 파일에 대해 ESLint 검사
echo "Running ESLint check..."
eslint . --ext .js,.jsx,.ts,.tsx
if [ $? -ne 0 ]; then
  echo "ESLint check failed. Fix issues before committing."
  exit 1
fi

echo "ESLint check passed!"


#!/bin/sh
# .git/hooks/prepare-commit-msg

BRANCH_NAME=$(git rev-parse --abbrev-ref HEAD)
COMMIT_MSG_FILE=$1

# 브랜치 이름을 메시지 앞에 추가
echo "[$BRANCH_NAME] $(cat $COMMIT_MSG_FILE)" > $COMMIT_MSG_FILE


#!/bin/sh
# .git/hooks/commit-msg

COMMIT_MSG=$(cat "$1")
PREFIXES="feat:|fix:|docs:|style:|refactor:|test:|chore:"

if ! echo "$COMMIT_MSG" | grep -qE "^($PREFIXES) "; then
  echo "Commit message must start with one of the following: feat:, fix:, docs:, style:, refactor:, test:, chore:"
  exit 1
fi


#!/bin/sh
# .git/hooks/pre-push

echo "Running tests before push..."
npm test
if [ $? -ne 0 ]; then
  echo "Tests failed. Fix issues before pushing."
  exit 1
fi

echo "All tests passed! Proceeding with push."


#!/bin/sh
# .git/hooks/post-checkout

BRANCH_NAME=$(git rev-parse --abbrev-ref HEAD)

if [ "$BRANCH_NAME" = "production" ]; then
  cp .env.production .env
  echo "Switched to production environment."
else
  cp .env.development .env
  echo "Switched to development environment."
fi
```

 - __.gitattributes와 함께 사용하는 .git/info/attributes__
    - .gitattributes와 동일한 역할을 하지만, 로컬 저장소에서만 적용되는 속성 설정입니다. 프로젝트 내에 포함되지 않고, 로컬에서만 적용되는 특수한 속성 정의가 필요할 때 사용됩니다.
 - __.git/info/exclude__
    - .gitignore와 유사하지만, 해당 파일을 프로젝트에 포함하지 않고 로컬에서만 특정 파일을 무시할 때 사용됩니다. .gitignore처럼 무시할 파일 패턴을 정의하지만, 프로젝트에 커밋되지 않으므로 개인 설정에 유용합니다.

