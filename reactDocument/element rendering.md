브라우저 DOM 엘리먼트와 달리 React 엘리먼트는 일반 객체
 React DOM은 React 엘리먼트와 일치하도록 DOM을 업데이트
 
 <div id="root"></div>
이 안에 들어가는 모든 엘리먼트를 React DOM에서 관리하기 때문에 이것을 “루트(root)” DOM 노드라고 부릅니다.

React로 구현된 애플리케이션은 일반적으로 하나의 루트 DOM 노드가 있습니다. 

React 엘리먼트를 렌더링 하기 위해서는 우선 DOM 엘리먼트를 ReactDOM.createRoot()에 전달한 다음, React 엘리먼트를 root.render()에 전달해야 합니다.

```

 <div id="apple"></div>//react엘레먼트
 
const banana = ReactDOM.createRoot(
  document.getElementById('apple')
);
//apple을 root로 만든다
//element를 render함수로 root인 banana에 추가한다
const element = <h1>Hello, world</h1>;
banana.render(element);

```

중단
1.dom
2.date생성자

DOM이란 무엇인가?

DOM을 조금 풀어서 써 볼까요? DOM은 Document Object Model의 약자입니다. 

Document는 문서이고 Object는 객체로 번역이 되죠. 
그리고 Model은 그냥 모델로 많이 쓰죠. 문서 객체 모델로 번역을 할 수 있겠네요. 
번역을 해도 아직 통 감이 오지 않네요. 



도대체 이 문서 객체란 것이 무엇일까요? 
문서 객체란 <html>이나 <body> 같은 html문서의 태그들을 JavaScript가 이용할 수 있는 객체(object)로 만들면 그것을 문서 객체라고 합니다. 
  
이제 조금 더 명확하게 DOM을 정의해보겠습니다. DOM은 넓은 의미로 웹 브라우저가 HTML 페이지를 인식하는 방식을 의미합니다. 
  조금 좁은 의미로 본다면 document 객체와 관련된 객체의 집합을 의미할 수도 있습니다.   
  
  new 키워드는 객체를 생성하는 방법 중, 생성자 함수(Constructor) 를 사용하여 객체를 만들 때 함께 쓰는 키워드이다.
new 생성자함수명() 의 형식을 통해 자바스크립트에서 동일한 구성을 가진 객체를 여러 개 만들어 낼 수 있다.
  
  new Date()를 호출하면 새로운 Date 객체가 만들어지는데, new Date()는 다음과 같은 형태로 호출할 수 있습니다.

new Date()
인수 없이 호출하면 현재 날짜와 시간이 저장된 Date 객체가 반환됩니다.
  
  
  
