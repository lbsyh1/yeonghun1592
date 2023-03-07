ReactDOM react컴포넌트를 html과 연결해준다

ReactDOM.render(인수1,인수2)
인수1(리엑트 엘레먼트)을 인수2안으로 넣어서 화면에 표시한다

ReactDOM은 React엘레먼트와 일치하도록 DOM을 업데이트

index.js는 app.js와 index.html을 연결한다 여기서 조합된다
app.js를 index.html의 DOM안에 집어넣는 역할을 한다
createRoot 주어진 html요소를 root로 만든다 root로 만들면 render함수를 사용해서 dom에 추가할 수 있다

createRoot(container[, options]);
주어진 container에 대해 React 루트를 만들고 해당 루트를 반환합니다. 반환된 루트로 render를 통해 React 엘리먼트를 DOM으로 렌더링할 수 있습니다.

const root = createRoot(container);

root.render(element);
container를 root로 만들고 반환한다 그럼 root에 그 container가 저장된다
그 container(root)에 엘레먼트를 넣고 render할 수 있다
