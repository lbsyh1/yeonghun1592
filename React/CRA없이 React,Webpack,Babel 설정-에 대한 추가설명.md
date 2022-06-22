npm init :package.json을 만드는 명령어
npm init -y : -y라는 속성을 이용하면 default값으로 설정된 package.json을 만들겠다라는 의미다
npm i react react-dom : react와 react-dom이라는 패키지를 설치한다
react-dom package는 앱의 최상위 레벨에서 사용할 수 있는 DOM에 특화된 메서드와 필요한 경우 React 모델 외부로 나갈 수 있는 해결책을 제공한다.
$node_modules/.bin/tsc --init :
1.node_modules : package.json에는 프로젝트가 의존하고 있는 모듈들에 대한 정보가 나와있고, node_modules 디렉토리에는 package.json에 있는 모듈 뿐만 아니라, package.json에 있는 모듈이 의존하고 있는 모듈 전부를 포함하고 있다. 그래서 node_modules 디렉토리안에는 정말 많은 모듈들이 들어가 있다. npm으로 새로운 모듈(패키지)를 설치하게 되면, package.json과 node_modules에 추가된다.
2.node_modules/.bin : 이 폴더는 이름에서도 유추할수있다시피 바이너리 파일들이 저장되는 곳이다. (바이너리 파일이란 1과 0으로만 이루어진 파일이다.
3.tsc --init : tsconfig.json 파일을 생성한다
sourceMap": true : Soucemap을 설정하면, 코드상의 위치를 기억하고 알려주기 때문에 빌드 전 어떤 파일, 라인에서 오류가 났는지 확인할 수 있다.
"target": "es5" : tsconfig.json 에 등장하는 중간에 lib의 내용을 보면 배열형태로 사용할 라이브러리들을 정의하고 있습니다. 만약 lib 항목을 정의하지 않았다면 target 항목에서 지정한 ECMAScript의 버전에 따라 기본값이 정의됩니다.
ES5의 기본 값: dom, es5, scripthost
ES6의 기본 값: dom, dom.iterable, es6, scripthost
"lib": ["dom", "ES2015", "ES2016", "ES2017", "ES2018", "ES2019", "ES2020"], : 위의 기본 값 대신에 커스텀하게 라이브러리를 쓰려고 할 때, lib을 정의하여 사용합니다.
"allowJs": true, : 1.allowJS js파일 사용 허용하는 옵션 타입스크립트는 .js확장자를 허용하지 않는다. 따라서 .js파일을 컴파일하는데, 이때 자바스크립트를 타입스크립트로 바꾸는 프로젝트가 진행중이라면 곤란함을 겪을 것이다. 점진적 도입을 위한 옵션이있는데, allowJS 옵션이다. true일 경우 .js파일을 사용할 수 있다고 한다.
"strict": true, strict 모드는 문법과 런타임 동작을 모두 검사하여, 실수를 에러로 변환하고, 변수 사용을 단순화(Simplifying) 시켜줍니다.
실수를 에러로 변환(Converting mistakes into errors)
자바스크립트는 오류를 어느정도 무시하고 넘어갈 수 있습니다. 이것이 편하게 코딩을 할 수 있게 하지만, 때로는 심각한 버그를 만들게 됩니다. strict 모드는 이러한 실수를 에러로 변환하여 즉시 수정할 수 있게 합니다.
"forceConsistentCasingInFileNames": true, : 같은 파일에 대한 일관되지 않은 참조를 허용하지 않을지 여부
 "esModuleInterop": true, : esModuleInterop 키
오픈소스 자바스크립트 라이브러리 중에는 웹 브라우저에서 동작한다는 가정으로 만들어 진 것들이 있다(위 소스에선 chance 라이브러리)

이들은 CommonJS 방식으로 동작하는 TS 코드에 혼란을 줄 수 있으므로 이를 정상적으로 동작하게 하기 위해 true로 설정

"isolatedModules": true, : isolatedModules

각 파일을 분리된 모듈로 트랜스파일(트랜스파일(transpile)이란 어떤 특정 언어로 작성된 소스 코드를 다른 소스 코드로 변환하는 것을 말합니다)
"jsx": "preserve",
TypeScript는 다음 세 가지의 JSX 모드를 제공합니다: preserve, react, react-native. 이 모드는 출력 단계에만 영향을 미치며 타입 검사에는 영향을 미치지 않습니다. preserve 모드는 JSX를 출력 일부로 유지하여 이를 다른 변환 단계(예: Babel)에서 추가로 사용합니다. 또한 출력 파일 확장자는 .jsx입니다. react 모드는 React.createElement를 출력하고 사용하기 전 JSX 변환을 거칠 필요가 없으며 출력 파일 확장자는 .js입니다. react-native 모드는 모든 JSX를 유지한다는 점에서 preserve 모드와 유사하나, 출력 파일 확장자가 .js라는 차이가 있습니다.

"allowSyntheticDefaultImports": true, allowSyntheticDefaultImports

default export를 쓰지 않은 모듈도 default import가 가능하게 할건지 여부

