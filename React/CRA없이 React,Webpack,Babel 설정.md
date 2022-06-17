# 1. CRA(Create-React-App)
CRA는 리액트 프로젝트를 시작하는데 필요한 개발 환경을 세팅 해주는 도구 이다. 또한 프로덕션 용도의 애플리케이션을 개발할 수 있는 환경을 가장 쉽게 셋팅하는 방법 중 하나이다. 초기에 복잡한 Webpack과 Babel, TypeScript등의 설정 필요 없이 명령어 하나로 개발에 필요한 최소한의 환경을 셋팅해준다.

CRA를 사용하면 손 쉽게 리액트 환경을 구축 할 수 있는데 Webpack, Babel에 추가적인 설정을 해야 할 때 어려움이 발생할 수 있다. 그래서 CRA 없이 환경을 구축해 보았다.


# 2. 개발환경 구축
## (1) 리액트 및 타입스크립트 설정
$npm init -y
$npm i react react-dom
$npm i -D typescript @types/react @types/react-dom
여기까지 진행 했을 때 타입스크립트에 대한 설정파일을 만들어야 한다. 타입스크립트가 전역으로 설치되어 있다면 바로 tsc —init을 호출해도 되지만 해당 프로젝트에만 설치되어있을 경우에는 경로를 직접 명시해 tsc를 호출해야 한다.

$node_modules/.bin/tsc --init
최상위 경로에 tsconfig.json 파일이 생성 되는데 필요 없는 부분은 제거하고 프로젝트에 맞게 설정을 진행한다.

tsconfig.json

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

## (2) 바벨(Babel) 설정
$npm i -D babel-loader @babel/core @babel/preset-env
$npm i -D @babel/preset-react @babel/preset-typescript
Typescript 자체 기능 내에 ES6의 새로운 기능들을 사용하기 위해 Babel과 같은 별도 트랜스파일러를 사용하지 않아도 되지만 추가적으로 필요한 경우가 있어서 설치한다. 이후 아래와 같이 Babel 설정파일을 생성 후 작성한다.

babel.config.js

<pre>
<code>
module.exports = {
  presets: ['@babel/preset-react', '@babel/preset-env', '@babel/preset-typescript'],
};
</code>
</pre>
@babel/preset-react : JSX로 작성된 코드들을 createElement 함수를 이용한 코드로 변환해 주는 바벨 플러그인이 내장(리액트를 변환하기 위한 프리셋)
@babel/preset-typescript : 타입스크립트를 변환하기 위한 프리셋
@babel/preset-env : preset-env는 ECMAScript2015+를 변환할 때 사용한다. 바벨 7 이전 버전에는 연도별로 각 프리셋을 제공했지만(babel-reset-es2015, babel-reset-es2016, babel-reset-es2017, babel-reset-latest) 지금은 env 하나로 합쳐졌다. IE 지원을 위한 프리셋

## (3) 웹팩(Webpack) 설정
$npm i -D webpack webpack-cli webpack-dev-server
$npm i -D html-webpack-plugin ts-loader
기본적으로 webpack webpack-cli가 필요하다. 생성된 html파일에 필요한 플러그인인 html-webpack-plugin과 개발 도중 변경사항을 확인할 수 있는 webpack-dev-server, 그리고 타입스크립트 코드를 자바스크립트 코드로 변환해주는 ts-loader를 설치한다.

이후 아래 Webpack 설정파일을 생성 후 작성한다.

webpack.config.js

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
mode : 프로덕션 모드인지 개발 모드인지 확인하는 옵션이다.
devtool : 프로덕션 모드인 경우엔 hidden-source-map을 권장한다. (외부에서 리액트 구조를 확인할 수 없다.)
resolve : 확장자나 경로를 알아서 처리할 수 있도록 설정하는 옵션이다.
module : 이 옵션에 설치한 ts-loader와 babel-loader를 설정하면 된다. loader들은 오른쪽에서 왼쪽 방향으로 적용되기 때문에 ts-loader를 babel-loader보다 오른쪽에 위치시켜야 한다.
output : 번들화 된 파일을 export할 경로와 파일명을 설정한다.
plugins : 설치한 플러그인을 적용하는 옵션이다

(4) Webpack-dev-server 추가설정
webpack-dev-server는 빠른 실시간 리로드 기능을 갖춘 개발 서버로 개발하는 과정에서 코드가 정확히 수정이 일어났는지 바로바로 확인할 수 있어서 유용하다. 또한 프록시 설정기능을 제공하여 CORS문제 등 브라우저 및 서버에러를 처리할 수 있다.

<pre>
<code>
const webpack = require('webpack');

...
module.exports = {...
  devServer: {
    historyApiFallback: true,
    inline: true,
    port: 3000,
    hot: true,
    publicPath: '/',
  },

  plugins: [
    ...,
    new webpack.HotModuleReplacementPlugin(),
    ...,
  ],
...
}
</code>
</pre>
historyApiFallback : 히스토리 API를 사용하는 SPA 개발 시 설정하며 404에러가 발생하면 index.html로 리다이렉트 한다.
inline : inline모드를 활성화 해준다.
port : 접속 포트를 설정한다.
hot : webpack의 HMR기능을 활성화 한다. (리로드 기능)
publicPath : 브라우저를 통해 접근하는 기본 주소값을 설정한다.

(5) package.json 변경설정

<pre>
<code>
...,
"scripts": {
    "dev": "webpack serve --mode development --open --hot",
    "build": "webpack --mode production",
    "prestart": "npm build",
    "start": "webpack --mode development"
  },
...
</code>
</pre>
예전에는 webpack-dev-server 명령어로 실행했는데 webpack serve로 바뀌었다(webpack-cli는 4버전이랑 같이 써야 오류가 안난다.)
dev 명령어는 webpack serve를 실행하는 명령어고 start는 리액트 프로젝트를 빌드해 dist폴더 안에 번들링 된 파일을 추출시켜 준다.

(6) react 엔트리파일 설정
src/index.tsx

<pre>
<code>
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

const rootElement = document.getElementById('root');
ReactDOM.render(<App />, rootElement);
</code>
</pre>
src/App.tsx
<pre>
<code>
import React from 'react';

const App = () => <>Test</>;

export default App;
</code>
</pre>
src/index.html

<pre>
<code>

<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <div id="root"></div>
  </body>
</html>

</code>
</pre>

# 출처
[https://velog.io/@kmlee95/CRA%EC%97%86%EC%9D%B4-React%ED%99%98%EA%B2%BD-%EA%B5%AC%EC%B6%95%ED%95%98%EA%B8%B0](https://velog.io/@kmlee95/CRA%EC%97%86%EC%9D%B4-React%ED%99%98%EA%B2%BD-%EA%B5%AC%EC%B6%95%ED%95%98%EA%B8%B0)
