props는 컴포넌트 사용처에서 컴포넌트 정의한곳으로 값을 보낼 수 있다 값을 보내고 그 결과를 다시 가져와 사용한다

<Hello age={10}/>

export default function Hello(props){
return(
console.log(props)
<h2>{props.age}</h2>
}

결과={age:10}
10
