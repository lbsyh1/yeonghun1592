BrowserRouter ,Route, Switch를 import

```

<BrowserRouter>
  <div>
    <Header>
    <Switch>
      <Router exact path="/"><Day><Router>
      <Router>
      <Router>
     </Switch>
     <Footer>
   <div>
 
 ```
 
 Router사이에 끼인 컴포넌트로 이동시킨다
 
 html은 a href를 사용하지만 리액트에서는 link to
 
 ```
 
 <Link to=`/day/${day.day}`>{day.day}</Link>
 Router는 특정 url에 특정 컴포넌트가 위치하게
 Link는 말그대로 특정 url로 이동하는 버튼을 만든다
 
 ```
 
 url에 asdasdasdasd를 입력하고
 <Route path="/day/:day">로 해놓고
  const params=useParams().day로 하면 params에 asdasdasd가 저장된다
  useParams는 url에서 값을 받아오는데 사용한다
  
  URL이 "/calendar/:year/:month/:day"인 경우, useParams는 다음과 같은 객체를 반환할 수 있습니다.

```
  
{
  year: "2023",
  month: "03",
  day: "08"
}
 
  
const person = { name: 'John', age: 30 };
const { name, age } = person;
  
const name=person.name;
const age=person.age;를 축약한것
 
변수와 객체의 프로퍼티 이름이 같을 때 축약문법을 사용할 수 있다

```
  
```
 
{days.map(day=>
  <li>
    <Link to=`/day/${day.day}`>{day.day}</Link>
  </li>
  
  해당날짜에 해당하는 url로 이동하고 링크 버튼은 해당날짜이다
  
```
  
  
  
  
