* npm init :package.json을 만드는 명령어

* npm init -y : -y라는 속성을 이용하면 default값으로 설정된 package.json을 만들겠다라는 의미다

* npm i react react-dom : react와 react-dom이라는 패키지를 설치한다

* react-dom package는 앱의 최상위 레벨에서 사용할 수 있는 DOM에 특화된 메서드와 필요한 경우 React 모델 외부로 나갈 수 있는 해결책을 제공한다.

* $node_modules/.bin/tsc --init :

1.node_modules : package.json에는 프로젝트가 의존하고 있는 모듈들에 대한 정보가 나와있고, node_modules 디렉토리에는 package.json에 있는 모듈 뿐만 아니라, package.json에 있는 모듈이 의존하고 있는 모듈 전부를 포함하고 있다. 그래서 node_modules 디렉토리안에는 정말 많은 모듈들이 들어가 있다. npm으로 새로운 모듈(패키지)를 설치하게 되면, package.json과 node_modules에 추가된다.

2.node_modules/.bin : 이 폴더는 이름에서도 유추할수있다시피 바이너리 파일들이 저장되는 곳이다. (바이너리 파일이란 1과 0으로만 이루어진 파일이다.

3.tsc --init : tsconfig.json 파일을 생성한다
## tsconfig.json
<pre>
<code>

{
  "compilerOptions": {
    "sourceMap": true,
    "target": "es5",
    "lib": ["dom", "ES2015", "ES2016", "ES2017", "ES2018", "ES2019", "ES2020"],
    "allowJs": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "esModuleInterop": true,
    "module": "commonjs",
    "isolatedModules": true,
    "jsx": "preserve",
    "allowSyntheticDefaultImports": true,
    "baseUrl": "./",
    "outDir": "./dist",
    "moduleResolution": "node"
  },
  "exclude": ["node_modules"],
  "include": ["**/*.ts", "**/*.tsx"]
}
</code>
</pre>
* sourceMap": true : Soucemap을 설정하면, 코드상의 위치를 기억하고 알려주기 때문에 빌드 전 어떤 파일, 라인에서 오류가 났는지 확인할 수 있다.
"target": "es5" : tsconfig.json 에 등장하는 중간에 lib의 내용을 보면 배열형태로 사용할 라이브러리들을 정의하고 있습니다. 만약 lib 항목을 정의하지 않았다면 target 항목에서 지정한 ECMAScript의 버전에 따라 기본값이 정의됩니다.

ES5의 기본 값: dom, es5, scripthost

ES6의 기본 값: dom, dom.iterable, es6, scripthost

* "lib": ["dom", "ES2015", "ES2016", "ES2017", "ES2018", "ES2019", "ES2020"], : 위의 기본 값 대신에 커스텀하게 라이브러리를 쓰려고 할 때, lib을 정의하여 사용합니다.

* "allowJs": true, : 1.allowJS js파일 사용 허용하는 옵션 타입스크립트는 .js확장자를 허용하지 않는다. 따라서 .js파일을 컴파일하는데, 이때 자바스크립트를 타입스크립트로 바꾸는 프로젝트가 진행중이라면 곤란함을 겪을 것이다. 점진적 도입을 위한 옵션이있는데, allowJS 옵션이다. true일 경우 .js파일을 사용할 수 있다고 한다.

* "strict": true, strict 모드는 문법과 런타임 동작을 모두 검사하여, 실수를 에러로 변환하고, 변수 사용을 단순화(Simplifying) 시켜줍니다.

## 실수를 에러로 변환(Converting mistakes into errors)

자바스크립트는 오류를 어느정도 무시하고 넘어갈 수 있습니다. 이것이 편하게 코딩을 할 수 있게 하지만, 때로는 심각한 버그를 만들게 됩니다. strict 모드는 이러한 실수를 에러로 변환하여 즉시 수정할 수 있게 합니다.

* "forceConsistentCasingInFileNames": true, : 같은 파일에 대한 일관되지 않은 참조를 허용하지 않을지 여부

*  "esModuleInterop": true, : esModuleInterop 키
 
오픈소스 자바스크립트 라이브러리 중에는 웹 브라우저에서 동작한다는 가정으로 만들어 진 것들이 있다(위 소스에선 chance 라이브러리)

이들은 CommonJS 방식으로 동작하는 TS 코드에 혼란을 줄 수 있으므로 이를 정상적으로 동작하게 하기 위해 true로 설정

* "isolatedModules": true, : isolatedModules

각 파일을 분리된 모듈로 트랜스파일(트랜스파일(transpile)이란 어떤 특정 언어로 작성된 소스 코드를 다른 소스 코드로 변환하는 것을 말합니다)

* "jsx": "preserve",

TypeScript는 다음 세 가지의 JSX 모드를 제공합니다: preserve, react, react-native. 이 모드는 출력 단계에만 영향을 미치며 타입 검사에는 영향을 미치지 않습니다. preserve 모드는 JSX를 출력 일부로 유지하여 이를 다른 변환 단계(예: Babel)에서 추가로 사용합니다. 또한 출력 파일 확장자는 .jsx입니다. react 모드는 React.createElement를 출력하고 사용하기 전 JSX 변환을 거칠 필요가 없으며 출력 파일 확장자는 .js입니다. react-native 모드는 모든 JSX를 유지한다는 점에서 preserve 모드와 유사하나, 출력 파일 확장자가 .js라는 차이가 있습니다.

* "allowSyntheticDefaultImports": true, allowSyntheticDefaultImports

default export를 쓰지 않은 모듈도 default import가 가능하게 할건지 여부

*  "outDir": "./dist", : outDir : 컴파일 후 생성되는 js파일이 생성될 폴더명
 
*  "moduleResolution": "node" : moduleResolution 은 module을 import하거나 export할 때, 어떤 방식으로 처리할 것인가에 대한 설정입니다.(이 해석 전략은 런타임에 Node.js의 모듈 해석 메커니즘을 모방하려고 시도합니다.)
 
*  "exclude": ["node_modules"], :  exclude: 컴파일하지 않을 폴더나 파일을 제외
* "include": ["**/*.ts", "**/*.tsx"] : include: 컴파일할 폴더나 파일을 별도 지정

# (2) 바벨(Babel) 설정
---

* npm i -D babel-loader : babel-loader: 웹팩과 바벨을 연동시키도록 해준다.
<pre>
<code>
module.exports = {
  presets: ['@babel/preset-react', '@babel/preset-env', '@babel/preset-typescript'],
};
</code>
</pre>
* 아래의 것들은 플러그인이지만 babel-loader과 같이 쓰이기 때문에 간략하게 소개하면 아래와 같다.

@babel/cli : 터미널에서 바벨 명령어를 사용할 수 있게 도와준다.

@babel/core : 바벨의 핵심 기능을 포함한다.

@babel/preset-env : es6의 문법을 es5의 문법으로 사용할 수 있게끔 es6의 문법을 트랜스파일링을 해주는 플러그인이다.

* -D : -D 와 같은 접미어를 “플래그” 라고 부르는데, 주로 사용되는 플래그는 다음과 같습니다.

플래그	효과
-P	패키지를 설치하고 프로젝트의 dependencies 목록에 추가한다.

—save-prod	패키지를 설치하고 프로젝트의 dependencies 목록에 추가한다.

-D	패키지를 설치하고 프로젝트의 devDependencies 목록에 추가한다.

—save-dev	패키지를 설치하고 프로젝트의 devDependencies 목록에 추가한다.

-g	패키지를 프로젝트가 아닌 시스템의 node_modules 폴더에 설치한다.

* @babel/preset-react

JSX로 작성된 코드들을 createElement 함수를 이용한 코드로 변환해 주는 바벨 플러그인이 내장되어 있다.
리액트 애플리케이션을 만들 때 필요한 플러그인들의 집합
preset

바벨은 js 파일을 입력받아 변환하여 결과물 js파일을 출력한다.

자바스크립트 파일을 변환해 주는 작업은 플러그인(plugin) 단위로 이루어진다.

하나의 결과물을 위해 여러개의 플러그인을 활용하여 여러번의 변환과정을 거친다.

이러한 플러그인들의 집합을 preset 이라 칭한다. (ex. 압축관련 플러그인 집합: babel-preset-minify)

* 플러그인 :  

플러그인의 본래 의미는 콘센트에 플러그를 꼽는다는 뜻이다. 하지만 인터넷이 발달하고 웹브라우저가 담당해야 할 부분이 증가하면서 메인프로그램인 웹브라우저가 처리하지 못하는 부분을 처리해 주는 작은 프로그램들을 플러그인이라고 부르기 시작하였다.

# (3) 웹팩(Webpack) 설정
---

* $npm i -D webpack webpack-cli  webpack은 웹팩의 핵심 패키지이며 webpack-cli는 터미널에서 webpack 커맨드를 실행할 수 있게 해주는 커맨드라인 도구입니다.

두 개의 패키지 모두 개발할 때만 필요한 의존성이기 때문에 -D 옵션을 사용하였습니다.

웹팩 데브 서버는 웹 애플리케이션을 개발하는 과정에서 유용하게 쓰이는 도구입니다. 웹팩의 빌드 대상 파일이 변경 되었을 때 매번 웹팩 명령어를 실행하지 않아도 코드만 변경하고 저장하면 웹팩으로 빌드한 후 브라우저를 새로고침 해줍니다.

* $npm i -D html-webpack-plugin HtmlWebpackPlugin은 webpack 번들을 제공하는 HTML 파일 생성을 단순화합니다.
이 플러그인은 매번 컴파일에 변경되는 해시로 된 파일 이름을 가진 webpack 번들에 특히 유용합니다. 
플러그인이 HTML 파일을 생성하도록 하거나 lodash 템플릿을 사용하여 나만의 템플릿을 제공하거나 나만의 로더를 사용할 수 있습니다
## .webpack.config.js
<pre>
<code>

const HtmlWebpackPlugin = require('html-webpack-plugin');
const path = require('path');
const webpack = require('webpack');
const prod = process.env.NODE_ENV === 'production';

module.exports = {
  mode: prod ? 'production' : 'development',
  devtool: prod ? 'hidden-source-map' : 'eval',
  entry: './src/index.tsx',
  resolve: {
    extensions: ['.js', '.jsx', '.ts', '.tsx'],
  },
  
  module: {
    rules: [
      {
        test: /\.tsx?$/,
        use: ['babel-loader', 'ts-loader'],
      },
    ],
  },
  
  output: {
    path: path.join(__dirname, '/dist'),
    filename: 'bundle.js',
  },

  plugins: [
	new webpack.ProvidePlugin({
      React: 'react',
    }),
    new HtmlWebpackPlugin({
      template: './src/index.html',
    }),
  ],
};
</code>
</pre>

const HtmlWebpackPlugin = require('html-webpack-plugin');

* require() 함수는 어떻게 쓰는 것일까요?

Node.JS 에서는 require 메서드를 통해 외부 모듈을 가져올 수 있습니다. require 메서드는 node가 local object에 추가한 메서드로서 다음과 같이 파라미터로 추가할 모듈의 파일 경로값을 받습니다.

const foo = require('파일 경로');


* devtool: prod ? 'hidden-source-map' : 'eval',
소스맵
소스맵은 원본 소스와 난독화된 소스를 매핑해주는 방법 중 하나이다.
*.map 파일을 통해 제공되고, json 형태로 돼있다.
웹팩에서 devtool 옵션은 개발을 용이하게 하기 위해 소스맵을 제공하는 옵션이다.
mode: prod ? 'production' : 'development',

* Webpack 모드
mode 매개 변수는 다음 3가지 값 중 하나를 사용할 수 있습니다. 
mode 값
설명
development
개발 모드
production
배포 모드 (기본 값)

webpack.config.js라는 파일과 자주 마주치게 됩니다. 바로 웹팩 설정 파일인데요


* Entry
entry 속성은 웹팩에서 웹 자원을 변환하기 위해 필요한 최초 진입점이자 자바스크립트 파일 경로입니다.
<pre>
<code>
// webpack.config.js
module.exports = {
  entry: './src/index.js'
}
</code>
</pre>
위 코드는 웹팩을 실행했을 때 src 폴더 밑의 index.js 을 대상으로 웹팩이 빌드를 수행하는 코드입니다.

*  Entry 파일에는 어떤 내용이 들어가야 하나?
entry 속성에 지정된 파일에는 웹 애플리케이션의 전반적인 구조와 내용이 담겨져 있어야 합니다. 웹팩이 해당 파일을 가지고 웹 애플리케이션에서 사용되는 모듈들의 연관 관계를 이해하고 분석하기 때문에 애플리케이션을 동작시킬 수 있는 내용들이 담겨져 있어야 합니다.
none
기본 최적화 옵션 설정 해제

<pre>
<code>

resolve: {
    extensions: ['.js', '.jsx', '.ts', '.tsx'],
  },
  </code>
</pre>
* Resolve 옵션은 module이 resolve 되는 방식을 변경시킨다. 예컨대 import 'lodash' 호출시, resolve 옵션은 웹팩이 lodash를 찾는 방법을 변경시킬 수 있다.

resolve.extensions
자동으로 특정 확장자만 resolve한다.
<pre>
<code>
module.exports = {
  //...
  resolve: {
    modules: [path.resolve(__dirname, 'src'), 'node_modules']
    extensions: ['.js', '.jsx']// , .scss ,.css]
  }
};

module: {
    rules: [
      {
        test: /\.tsx?$/,
        use: ['babel-loader', 'ts-loader'],
      },
    ],
  },
  
  </code>
</pre>
* module
module 프로퍼티는 프로젝트 내의 여러 유형의 모듈들을 처리할 방법을 결정
module.rules : 모듈이 생성 될 때 요청과 일치하는 규칙 의 배열
module.rules.test : loader를 적용시킬 파일들을 정규식으로 명시
module.rules.loader : 사용할 loader 명시



* output
 
번들링한 결과물을 어디 경로에 놓을 것인지를 결정합니다.

파일이름과 path를 정해놓으면 그곳에 정의해둡니다.
<pre>
<code>
output: {
  path: path.join(__dirname, "static"),
  filename: "[name].js",
},

plugins: [
	new webpack.ProvidePlugin({
      React: 'react',
    }),
    new HtmlWebpackPlugin({
      template: './src/index.html',
    }),
  ],
  </code>
</pre>
* ProvidePlugin
모듈을 import 또는 require 할 필요 없이 자동으로 로드합니다.
html-webpack-plugin
웹팩에서 실행해서 나오는 결과물을 확인하기 위해서는 이전처럼([front-backend 분리] 로더 사용하기) 직접 html 파일을 수동으로 작성해야 한다. 
위에서 chunkhash 옵션을 설정했기 때문에 파일의 내용이 변경될 때마다 html 파일의 내용도 수정해야한다. 
이러한 작업을 자동으로 하는 플로그인이 'html-webpack-plugin' 이다.
<pre>
<code>

module.exports = {...
  devServer: {
    historyApiFallback: true,
    inline: true,
    port: 3000,
    hot: true,
    publicPath: '/',
  },
    </code>
</pre>
* historyAPI란 브라우저의 세션 기록에 대한 property와 접근 method를 제공하는 객체이다. (여기를 참고)


* 세션 기록이란 쉽게 생각해서 우리가 뒤로가기 앞으로가기 할 때 뒤로(앞으로)갈 페이지에 대한 정보를 저장해두는 것이다.
historyApiFallback
History API 또는 react-router 등을 사용하는 경우 새로고침 시 404 에러를 해결해주는 option

* Inline 모드 : 작은 웹팩개발서버 클라이언트엔트리가 번들에 추가가 되어서 바뀔때마다 페이지를 갱신합니다.

* Hot Module Replacement(또는 HMR)는 webpack에서 제공하는 가장 유용한 기능 중 하나입니다. 
모든 종류의 모듈을 새로고침 할 필요 없이 런타임에 업데이트 할 수 있습니다.

* publicPath를 사용하여 webpack-dev-server가 “가상”파일을 제공 할 위치를 가리킬 수 있습니다. 
publicPath 옵션은 webpack-dev-server에 대한 content-build 옵션의 위치와 같습니다. 
* webpack-dev-server 는 시작할 때 사용할 가상 파일을 만듭니다. 이 가상 파일은 웹팩에서 생성 한 실제 번들 파일과 유사합니다. 
기본적으로 –content-base 옵션이 index.html이있는 디렉토리를 가리 키도록합니다. 
<pre>
<code>

plugins: [
    ...,
    new webpack.HotModuleReplacementPlugin(),
    ...,
  ],
  </code>
  </pre>

* 핫 모듈 리플레이스먼트(Hot Module Replacement - HMR)는 웹팩이 제공하는 가장 유용한 기능 중 하나입니다. 
전체 새로고침 없이 모든 종류의 모듈들을 런타임 시점에 업데이트 되게 해줍니다


: package.json 파일의 scripts 항목에 다양한 명령어를 설정해두고 콘솔에서 실행할 수 있다.

* npm run build 해당 빌드를 실행하면 프로젝트에 전에 없던 build라는 폴더가 생성됩니다
해당 빌드를 실행하면 프로젝트에 전에 없던 build라는 폴더가 생성됩니다.
이는 말 그대로 빌드된 파일들을 저장하는 폴더입니다. 
npm run build 은의 별칭


* ReactDOM.render(element, container[, callback])
react-dom package는 앱의 최상위 레벨에서 사용할 수 있는 DOM에 특화된 메서드와 필요한 경우 React 모델 외부로 나갈 수 있는 해결책을 제공합니다.
대다수 컴포넌트는 이 모듈을 사용할 필요가 없습니다.

React 엘리먼트를 container DOM에 렌더링하고 컴포넌트에 대한 참조를 반환합니다(무상태 컴포넌트는 null을 반환합니다).

React 엘리먼트가 이전에 container 내부에 렌더링 되었다면 해당 엘리먼트는 업데이트하고 최신의 React 엘리먼트를 반영하는 데 필요한 DOM만 변경합니다.

추가적인 콜백이 제공된다면 컴포넌트가 렌더링되거나 업데이트된 후 실행됩니다.
