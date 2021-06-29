# 프로젝트 코드 스타일 일관성 유지 테스트

husky 와 lint-staged을 활용하여 커밋시 코드 스타일 점검

## 설치 순서

1. yarn add --dev --exact prettier
2. yarn add --dev husky lint-staged
3. npx husky install
4. node 스크립트 추가
    ```json
    // package.json
    {
        "scripts": {
            "prepare": "husky install"
        }
    }
    ```
5. npx husky add .husky/pre-commit "npx lint-staged"
6. git staged 단계에서 수행할 파일과 명령어
    ```json
    // package.json
    {
        "lint-staged": {
            "**/*": "prettier --write --ignore-unknown"
        }
    }
    ```

## Prettier 설정

| 파일             | 용도             | 위치 |
| ---------------- | ---------------- | ---- |
| .prettierrc.json | 코드 스타일 설정 | root |
| .prettierignore  | 예외할 파일 목록 | root |

커맨드 라인에서 `yarn prettier --write .`로 모든 파일에 대한 코딩 스타일 맞춤(파일 변경됨)
커맨드 라인에서 `yarn prettier --check .`로 모든 파일에 대한 코딩 스타일 체크(코딩 스타일 맞지 않는 목록을 보여줌)

#### 참고 문서

-   [Prettier Git hooks](https://prettier.io/docs/en/install.html#git-hooks)
-
