# Git Hooks

Git Hooks는 특정 Git 이벤트가 발생할 때 자동으로 실행되는 스크립트를 말한다. 이를 통해 코드 품질 관리, 커밋 메시지 스타일 검사, 자동 테스트 실행 등을 쉽게 자동화할 수 있어 개발 효율을 높이고 팀 내 코드 품질을 유지할 수 있다.

Git은 로컬 리포지토리의 .git/hooks 디렉토리에 다양한 훅 스크립트를 제공하며, 파일명을 변경하거나 실행 가능한 상태로 만들면 활성화된다.

 - __코드 스타일 검사__: pre-commit 훅에서 ESLint나 Prettier와 같은 도구를 실행하여 코드 스타일을 맞추고, 오류가 있으면 커밋을 중단할 수 있습니다.
 - __커밋 메시지 규칙 적용__: commit-msg 훅에서 커밋 메시지가 특정 형식([TYPE]: 설명)을 따르도록 검증하고, 형식에 맞지 않으면 경고를 출력하도록 설정할 수 있습니다.
 - __자동화 테스트__: pre-push 훅에서 테스트를 실행하여 모든 테스트가 통과된 경우에만 푸시하도록 할 수 있습니다.

## Client-Side Hooks

 - __Commit Workflow Hooks__
    - __pre-commit__
        - 커밋하기 전에 실행됩니다.
        - 주로 코드 스타일 검사, 코드 품질 분석, 자동 포맷팅 등을 수행하여 코드 품질을 관리합니다.
    - __prepare-commit-msg__
        - 커밋 메시지를 작성하기 전에 실행됩니다.
        - 커밋 메시지 템플릿이나 기본값을 자동으로 추가하거나, 특정 커밋 메시지 형식을 요구하는 경우 유용합니다.
    - __commit-msg__
        - 커밋 메시지가 입력된 후에 실행됩니다.
        - 커밋 메시지 규칙을 검증하여, 올바른 형식을 따르지 않으면 커밋을 중단할 수 있습니다.
    - __post-commit__
        - 커밋이 완료된 후 실행됩니다.
        - 커밋 이후 후속 작업을 수행하는 데 사용되며, 로그를 기록하거나 Slack과 같은 외부 서비스로 알림을 보낼 때 유용합니다.
 - __Email Workflow Hooks__
    - __applypatch-msg__
        - git am 명령어 실행 시 가장 먼저 실행됩니다.
    - __pre-applypatch__
        - patch 파일을 적용한 후 실행됨, patch 반영 또한 중단시킬 수 있습니다.
    - __post-applypatch__
        - patch 파일이 commit으로 반영되기 직전에 수행되며, patch 반영은 중단시킬 수 없습니다.
 - __Other Hooks__
    - __pre-rebase__
        - 리베이스를 시작하기 전에 실행됩니다.
        - 리베이스 도중 충돌 가능성을 사전 점검하거나 백업을 생성하는 등 리베이스의 안전성을 높이는 데 사용됩니다.
    - __post-rewrite__
        - git commit --amend 또는 git rebase와 같이 커밋이 변경된 후에 실행됩니다.
        - 이 훅은 커밋이 수정되거나 새롭게 작성된 이후에 후속 작업을 수행하는 데 유용합니다. 예를 들어, 변경 이력을 로그에 남기거나 알림을 보내는 작업을 할 수 있습니다.
    - __pre-merge-commit__
        - git merge를 실행하여 병합 커밋을 만들기 전에 실행됩니다.
        - 병합 시 발생할 수 있는 문제를 사전에 검토하거나 병합 전에 특정 검증 작업을 추가할 때 사용됩니다.
    - __pre-push__
        - 푸시하기 전에 실행됩니다.
        - 푸시 전 테스트를 실행하거나 코드 스캔을 수행하여, 오류가 발생하면 푸시를 중단하도록 할 수 있습니다.
    - __post-checkout__
        - 체크아웃 후, 즉 브랜치를 변경하거나 특정 커밋으로 이동한 직후 실행됩니다.
        - 특정 브랜치 전환 시 후속 작업이 필요할 때, 예를 들어 환경 설정 파일을 변경하거나 디버그 모드를 켜는 등의 작업을 수행할 수 있습니다.
    - __post-merge__
        - 병합 후 실행됩니다.
        - 병합 후에 자동 빌드, 테스트 실행, 또는 특정 파일 재설정 작업 등을 수행할 수 있습니다.

## Git Hooks 사용법

Git Hooks 는 .git/hooks 디렉토리 안에 저장한다. hook 은 실행가능한 스크립트이며, 설정하고자 하는 훅 이름을 확장자 없이 파일명으로 지정하면 Git Hooks 를 적용할 수 있다.

 - `.git/hooks/pre-commit`
    - Exit 코드가 0이 아니면 커밋이 취소된다.
```bash
#!/bin/sh
​
echo 'Hello World!'
​
exit 0
```

 - `.git/hooks/pre-push`
    - main 브랜치에 직접 푸시하는 경우 푸시를 중단시킨다.
```bash
#!/bin/sh
​
FORBIDDEN_HTTPS_URL="Remote URL" # insert your remote url (https)
FORBIDDEN_SSH_URL="Remote URL SSH" # insert your remote url (ssh)
FORBIDDEN_REF="refs/heads/main" # insert branch ref
​
remote="$1"
url="$2"
​
if [ "$url" != "$FORBIDDEN_HTTPS_URL" -a "$url" != "$FORBIDDEN_SSH_URL" ]
then
    exit 0 # Forked Project 에서는 제한하지 않음
fi
​
if read local_ref local_sha remote_ref remote_sha
then
    if [ "$remote_ref" == "$FORBIDDEN_REF" ]
    then
        echo "DO NOT PUSH it main"
        exit 1 # 금지된 ref 로 push 를 실행하면 에러
    fi
fi
​
exit 0
```

## Git Hooks 공유하기

__Git Hooks__ 는 .git 디렉토리에 저장한다. 그런데 .git 디렉토리는 버전 관리 대상이 아니므로 Repositories 에 올라가지 않는다. 기본적인 Git 체계 하에서는 Git Hooks 를 공유할 수 없다는 뜻이다.

 - Git Hooks 를 설정하는 스크립트 공유
 - Git Template 을 활용
 - husky 사용

### 1. Git Hooks 를 설정하는 스크립트 공유

Git Hooks를 별도 디렉토리에 넣어 버전 관리를 하고, 이 훅을 .git/hooks로 복사하는 스크립트를 함께 공유한다.

이 방법을 사용하면 프로젝트 별로 hooks를 관리하고 고융할 수 있다. 하지만, 작업자는 git clone 후에 반드시 ./setup_hooks.sh를 실행해야 한다. 만약 실수로 설정 스크립트를 실행하지 않으면 훅을 적용할 수 없다.

 - `폴더 구조`
    - 루트 디렉토리에 Git Hooks가 있는 폴더와 .git 폴더로 이동시키는 스크립트 파일을 위치시킨다.
```
./githooks/pre-commit
./githooks/pre-push
./setup_hooks.sh
```

 - `./setup_hooks.sh`
    - githooks 디렉토리에 있는 파일을 .git/hooks 디렉토리로 복사한다.
```sh
#!/bin/sh
​
cp githoooks/* .git/hooks
```

### 2. Git Template을 활용

Git Template 을 활용 은 git clone 시 --template 옵션을 통해 .git 디렉토리를 초기화할 수 있다는 점을 활용한다.

Git Hooks를 별도의 경로나 Repository에서 관리하고자 할 때 사용할 수 있다. 하지만, Template를 미리 공유해야 하며, --template 옵션을 누락하는 경우 훅을 적용할 수 없다.

 - `Template 디렉토리`
    - 프로젝트와 독립된 경로에 Template 디렉토리를 구성하고 Git Hooks를 넣어둔다.
```
./git_templates/hooks/pre-commit
./git_templates/hooks/pre-push
```

 - `Clone시에 Template 옵션 설정`
```bash
$ git clone --template=./git_templates {Remote URL}
```

### 3. husky를 활용

스크립트 공유와 Git Template는 모두 실수로 Git Hooks를 적용하지 않을 가능성이 크다. 이러한 경우 husky를 이용할 수 있다.

husky는 Git Hooks를 보다 쉽게 적용할 수 있는 npm 모듈이다.

#### Husky 적용하기

 - `1. Husky 라이브러리 설치`
```bash
# Husky 설치
npm install husky --save-dev

# husky 초기화
npx husky install
```

 - `2. pre-commit Hook 설정`
    - '.husky/' 폴더안에 pre-commit 파일을 만든다.
```bash
#!/bin/sh

# npx eslint를 사용하여 코드 린팅을 수행합니다.
npx eslint . --fix

# # npx prettier를 사용하여 코드 포맷팅을 수행합니다.
# npx prettier --write .

# # TypeScript 타입 체크를 수행합니다.
# npx tsc --noEmit

# # npm test를 사용하여 테스트를 실행합니다.
# npm test
```


 - `3. package.json 파일 변경`
    - npm install 시에 husky를 초기화할 수 있도록 한다. npm install 시에 husky install 스크립트가 실행된다.
    - 초기 프로젝트를 받은 구성원이 npm install 시에 husky 설정도 초기화된다.
```json
{
  "scripts": {
    ..
    "postinstall": "husky install",
  },
}
```
