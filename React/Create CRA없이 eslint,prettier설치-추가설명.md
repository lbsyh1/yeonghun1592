
<pre>
<code>
module.exports = {
    root: true,
    env: {
        browser: true,
        es6: true,
    },
    extends: [
        "plugin:@typescript-eslint/recommended",
         // typescript 표준 규칙 모음
        "plugin:import/errors",
        "plugin:import/warnings",
        "plugin:import/typescript",
        // import 관련 규칙 모음

        "plugin:prettier/recommended",
        "prettier/@typescript-eslint",
        "prettier/react",
         // prettier 관련 규칙 모음
    ],
    parserOptions: {
        ecmaVersion: 2018,
        project: ["./tsconfig.json"],
        // tsconfig 파일의 경로를 참조 해줍니다. 
        // 기준은 root 입니다.
    },
    rules: {
            // 추가하고 싶은 rule을 더 추가해줍니다.
        }
        </code>
        </pre>
* env는 사전 정의된 전역 변수 사용을 정의합니다.
자주 사용되는 설정으로는 browser, node가 있습니다.

* parserOptions은 ESLint 사용을 위해 지원하려는 Javascript 언어 옵션을 지정할 수 있습니다.

* ecmaVersion: 사용할 ECMAScript 버전을 설정
*
* sourceType: parser의 export 형태를 설정

* ecmaFeatures: ECMAScript의 언어 확장 기능을 설정

* globalReturn: 전역 스코프의 사용 여부 (node, commonjs 환경에서 최상위 스코프는 module)

* impliedStric: strict mode 사용 여부

* jsx: ECMScript 규격의 JSX 사용 여부


* 확장 (extends)
extends는 추가한 플러그인에서 사용할 규칙을 설정합니다.
플러그인은 일련의 규칙 집합이며, 플러그인을 추가하여도 규칙은 적용되지 않습니다.
규칙을 적용하기 위해서는 추가한 플러그인 중, 사용할 규칙을 추가해주어야 적용이 됩니다.


* 여기서 eslint-plugin- 접두사를 생략하고 plugin:를 사용하여 사용할 플러그인을 지정할 수 있습니다. eslint:all과 eslint:recommended는 ESLint에 기본으로 제공되는 확장입니다. ESLint는 eslint:all를 프로덕션 용도로 사용하지 않기를 권장하고 있습니다.

* 또, 자주 사용되는 Typescript는 @typescript-eslint/eslint-plugin를 사용할 수 있습니다. 이 플러그인은 접미사 eslint-plugin을 생략하고 설정할 수 있습니다.
ESLint에는 프로젝트에서 사용하는 규칙을 수정할 수 있습니다. 규칙을 변경하는 경우, 다음과 같은 방법으로 설정해야 합니다.
-"off" 또는 0: 규칙을 사용하지 않음
-"warn" 또는 1: 규칙을 경고로 사용
-"error" 또는 2: 규칙을 오류로 사용
<pre>
<code>
module.exports = {
    endOfLine: "lf",
    tabWidth: 4,
    semi: true,
    singleQuote: false,
    trailingComma: "all",
    printWidth: 120,
};
</code>
        </pre>

* Print Width 
프린터가 줄 바꿈할 줄 길이를 지정합니다



* Tab Width 들여쓰기 수준당 공백 수를 지정합니다.


* Tabs 공백 대신 탭을 사용하여 줄을 들여씁니다.


* Semicolons 명령문의 끝에 세미콜론을 추가합니다.



* Trailing Commas v2.0.0에서 기본값이 없음에서 es5로 변경됨

여러 줄 쉼표로 구분된 구문 구조에서 가능한 한 후행 쉼표를 인쇄합니다. (예를 들어, 단일 행 배열은 후행 쉼표를 가져오지 않습니다.)
줄 끝
역사적 이유로 텍스트 파일의 줄 끝에는 두 가지 일반적인 특징이 있습니다. 그것은 \n(또는 줄 바꿈의 경우 LF) 및 \r\n(또는 캐리지 리턴 + 줄 바꿈의 경우 CRLF)입니다. 전자는 

* quotes 
큰따옴표 대신 작은따옴표를 사용한다

<pre>
<code>

{
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "[typescriptreact]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[typescript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "editor.formatOnSave": true
}
</code>
        </pre>
* editor.defaultFormatter": "vscode.json-language-features". - 위의 값은 기본적으로 포맷의 형태를 어떤 방식으로 설정하는지에 대한 셋팅입니다.
