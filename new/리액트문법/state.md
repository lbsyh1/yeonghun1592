1.ui를 자동으로 업데이트

2.

바닐라 자바스크립트로 했을때 

```

let name='mike'
function nameChange(){
name=name==='mike'?'jordan':'minsu';
document.getElementById('name').innerText=name;//dom을 업데이트 하는 코드
}
return(
<div>
  <p id="name">{name}</p>
<button onClick={nameChange}

```

```

let [name,setName]=useState('mike');
function nameChange(){
setName(name==='mike'?'jordan':'minsu'); //여기서 콜백함수를 사용하는것이 더 좋다
}
return(
<div>
<p>{name}</p>
<button onClick={nameChange}

```

state로 해야 변경된 dom에 따라 ui업데이트를 한다

useState를 사용할 때 변수의 선언 방식에 대해서는 일반적으로 const를 사용하는 것이 권장됩니다.

이유는 useState를 사용하여 상태를 관리하는 변수는 컴포넌트 내에서 변경 가능하며, 변수의 값이 변경되면 컴포넌트가 다시 렌더링됩니다. 따라서 let을 사용하여 변수를 선언하면 이후에 변수의 값이 변경될 수 있으므로, 컴포넌트의 상태 변화를 추적하기 어려워집니다.

반면, const를 사용하여 변수를 선언하면 변수의 값이 변경될 수 없으므로, 컴포넌트의 상태 변화를 추적하기 쉬워집니다. 또한, const를 사용하여 변수를 선언하면 변수의 스코프가 블록 레벨(block-level)로 제한되므로, 변수의 재할당이 불가능합니다.

따라서, useState를 사용하여 상태를 관리할 때에는 일반적으로 const를 사용하여 변수를 선언하는 것이 좋습니다. 다만, 특별한 상황에서 변수의 값을 변경해야 하는 경우에는 let을 사용할 수도 있습니다. 이 경우에는 변수의 값을 변경할 때마다 컴포넌트가 다시 렌더링되므로, 상태 변화를 추적하기 쉬워집니다.
