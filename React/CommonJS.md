먼저 자바스크립트의 모듈시스템에 대해 설명하자면

기존에는 html 파일에서 <script> 태그를 이용하여 필요한 자바스크립트 파일들을 불러왔다.

이러한 방식에는 큰 문제가 있었는데

html 파일에서 불러와진 여러 자바스크립트들이 서로 다른 파일임에도 불구하고

서로가 의존적이게 되어버렸다... 부가적으로 파일들을 로드하는 순서도 중요했고...

 

이러한 점을 보완하기 위해 등장한 것이 바로 모듈 시스템이다.

간단히 말하면 외부에서 사용할 수 있게 특정 함수나 오브젝트 등을 모듈화 하고,

해당 모듈을 사용하려는 쪽에서는 필요한 모듈만 불러와서 사용하면 된다.

 

모듈을 정의하기 위한 문법에는 여러가지가 있다. (모듈 포맷)

대표적으로 AMD, CommonJS, ES6 등이 있는데 이 포스팅에서는 CommonJS와 ES6를 비교해보겠다.

 

CommonJS

CommonJS 포맷은 Node.js (서버사이드 자바스크립트) 의 표준이다.

(정확히는 독자적으로 진화시켰지만 기본적으로 CommonJS 방식을 따르고 있다.)

내보내기의 경우 exports 및 module.exports,

가져오기의 경우 require 를 사용한다.

1-1. exports를 통한 내보내기
 <pre>
 <code>

//func.js
function func1 (param) {
	// ...
}

function func2 (param) {
	// ...
}

exports.func1 = func1
exports.func2 = func2
 

1-2. 가져오기
 <pre>
 <code>

const obj = require('./func')

obj.func1(10)
obj.func2(20)
 </code>
 </pre>

다음으로는 module.exports를 통한 내보내기와 가져오기 입니다.

 

2-1. module.exports를 통한 내보내기
 <pre>
 <code>

// func.js
const obj = {
	
    func1: function (num) {
    	// ...
    },
    
    func2: function (num) {
    	// ...
    }
}
 </code>
 </pre>
module.exports = obj
 

2-2. 가져오기
 <pre>
 <code>

const obj = require('./func')

obj.func1(10)
obj.func2(20)
 
 </code>
 </pre>
기본적으로 가져오는 방법에 대해서는 두 방법이 모두 동일하다.

다만, 내보내기를 할 경우

exports를 사용하는 경우에는 여러 property를 내보낼 때,

module.exports를 사용하는 경우에는 여러 property를 내보낼 때 혹은 단일 Object를 내보낼 때 모두 가능하다.

 

추가적으로 exports는 module.exports를 참조하고 있는 객체이다.

즉, exports 에 property를 명시하는 위와같은 방법은 정상적으로 동작하지만,

신규 객체를 할당해버리면 모듈이 동작하지 않는다.

특별한 상황이 아니라면 module.exports를 사용하는 것이 권장된다.

 

 

ES6

CommonJS와 마찬가지로 기본적으로는 원하는 모듈을 내보내고, 가져온다는 것에서는 동일하지만

아직 브라우저들이 es6를 완벽히 지원하지 못하는 상황이므로

webpack 이나 babel 등의 번들러들이 필요한 것이 단점이라면 단점이다.

(사실 최근에는 번들러를 끼고 개발하는 것이 일상이기 때문에 불편한것도 모르겠지만..)

 

기본적으로 내보내기 키워드는 export 및 default.

가져오기 키워드는 import 입니다.

 

1-1. export 를 이용한 내보내기
 <pre>
 <code>

// first_func.js

export function func1 (num) {
	// ...
}

const func2 = function (num) {
	// ...
}

export { func2 }
  </code>
 </pre>

1-2. 가져오기

// 사용하려는 객체만 선택하여 가져오기
 <pre>
 <code>

import { func1 } from './first_func'

func1(10)
 </code>
 </pre>

// 모든 객체를 가져오되 원하는 이름을 붙여서 사용한다.
 <pre>
 <code>

import * as obj from './first_func'

obj.func1(10)
obj.func2(20)
  </code>
 </pre>

2-1. export default 를 이용한 내보내기
 <pre>
 <code>


// second_func.js
const obj = {

    func3: function (num) {
    	// ...
    },
    
    func4: function (num) {
    	// ...
    }
}

export default obj
  </code>
 </pre>

2-2. 가져오기

// default 키워드를 이용하여 내보냈던 쪽에서 사용한 명칭을 그대로 사용할 필요는 없다
 <pre>
 <code>

import testObj from './second_func'

testObj.func3(10)
testObj.func4(20)
  </code>
 </pre>

 

이상으로 CommonJS 와 ES6 의 모듈시스템에 알아보았다.
# 출처
[CommonJS와 ES6의 모듈(module) 시스템](https://jh-7.tistory.com/9)
