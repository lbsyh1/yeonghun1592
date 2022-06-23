ESLint will look for configuration files in all parent folders up to the root directory.

env는 사전 정의된 전역 변수 사용을 정의합니다.
자주 사용되는 설정으로는 browser, node가 있습니다.

parserOptions은 ESLint 사용을 위해 지원하려는 Javascript 언어 옵션을 지정할 수 있습니다.

ecmaVersion: 사용할 ECMAScript 버전을 설정
sourceType: parser의 export 형태를 설정
ecmaFeatures: ECMAScript의 언어 확장 기능을 설정
globalReturn: 전역 스코프의 사용 여부 (node, commonjs 환경에서 최상위 스코프는 module)
impliedStric: strict mode 사용 여부
jsx: ECMScript 규격의 JSX 사용 여부


확장 (extends)
extends는 추가한 플러그인에서 사용할 규칙을 설정합니다.
플러그인은 일련의 규칙 집합이며, 플러그인을 추가하여도 규칙은 적용되지 않습니다.
규칙을 적용하기 위해서는 추가한 플러그인 중, 사용할 규칙을 추가해주어야 적용이 됩니다.


여기서 eslint-plugin- 접두사를 생략하고 plugin:를 사용하여 사용할 플러그인을 지정할 수 있습니다. eslint:all과 eslint:recommended는 ESLint에 기본으로 제공되는 확장입니다. ESLint는 eslint:all를 프로덕션 용도로 사용하지 않기를 권장하고 있습니다.

또, 자주 사용되는 Typescript는 @typescript-eslint/eslint-plugin를 사용할 수 있습니다. 이 플러그인은 접미사 eslint-plugin을 생략하고 설정할 수 있습니다.
ESLint에는 프로젝트에서 사용하는 규칙을 수정할 수 있습니다. 규칙을 변경하는 경우, 다음과 같은 방법으로 설정해야 합니다.
-"off" 또는 0: 규칙을 사용하지 않음
-"warn" 또는 1: 규칙을 경고로 사용
-"error" 또는 2: 규칙을 오류로 사용



Print Width
Specify the line length that the printer will wrap on.


Tab Width
Specify the number of spaces per indentation-level.

Tabs
Indent lines with tabs instead of spaces.

Semicolons
Print semicolons at the ends of statements.


Trailing Commas
Default value changed from none to es5 in v2.0.0

Print trailing commas wherever possible in multi-line comma-separated syntactic structures. (A single-line array, for example, never gets trailing commas.)
End of Line
For historical reasons, there exist two common flavors of line endings in text files. That is \n (or LF for Line Feed) and \r\n (or CRLF for Carriage Return + Line Feed). The former is common on Linux and macOS, while the latter is prevalent on Windows. Some details explaining why it is so can be found on Wikipedia.


uotes
Use single quotes instead of double quotes.


editor.defaultFormatter": "vscode.json-language-features". - 위의 값은 기본적으로 포맷의 형태를 어떤 방식으로 설정하는지에 대한 셋팅입니다.
