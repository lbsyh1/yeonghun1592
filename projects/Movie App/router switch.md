Route exact와 Switch의 간단 정리

```

<Route path="/" component= { Main } />
<Route path="/water" component= { Water } />
<Route path="/juice" component= { Juice } />

```

위의 소스코드를 바탕으로 경로를 / 로 이동할 경우 Main, Water, Juice 컴포넌트 3개가 전부 렌더링된다. Route는 경로가 부분적으로 일치하는 컴포넌트도 렌더링하는 특성을 가지고 있기 때문이다. 의도치 않은 렌더링을 위해 exact를 사용한다.

 ```

<Route path="/" exact component= { Main } />
<Route path="/water" exact component= { Water } />
<Route path="/juice" exact component= { Juice } />

```

/ 경로로 이동할 경우 Main컴포넌트만, /water 경로로 이동할 경우 Water 컴포넌트만, /juice 경로로 이동할 경우 Juice 컴포넌트만 렌더링되게 된다. 즉, 경로가 완벽히 일치하는 컴포넌트만 렌더링 하게된다.

 

 ```

<Switch>
  <Route path="/" component= { Main } />
  <Route path="/water" exact component= { Water } />
  <Route path="/juice" exact component= { Juice } />
</ Switch

```

Switch 태그를 사용하여 감쌀 경우, 경로와 일치하는 컴포넌트를 하나만 렌더링하게 된다. 경로의 일치 검사는 / water juice 순으로 위에서 아래로 순차적으로 진행하게 된다. 그렇기 때문에 Switch 태그를 사용할 경우에는 Route의 순서에 유의하여 사용하여야 한다.

 

 

이렇게 보면 exact와 Switch의 차이점은 경로의 일치 유무에 따라 컴포넌트를 여러개 또는 단 하나만 렌더링 한다는 작은 차이점 밖에 없는 것으로 보인다. 이로인해 Switch태그를 사용하는 것보다 exact를 통해 컴포넌트 렌더링을 제어하면 된다는 생각이 들 것 이고, Switch태그가 전혀 필요없을 것 처럼 보일 수 있다.

하지만 다음의 경우를 살펴보면 생각이 바뀌게 될 것이다.

만약 사용자가 존재하지 않은 URL로 이동한다는 예를 들어보자.

```

<Route path="/" exact component= { Main } />
<Route path="/water" exact component= { Water } />
<Route path="/juice" exact component= { Juice } />

```

라우트 컴포넌트가 위와 같을 경우, 사용자가 /melon이라는 없는 경로로 페이지를 이동할 경우, 사용자는 아무것도 없는 빈 페이지를 보게 된다. 이러한 경우를 방지하고자, 와일드 카드를 활용하여 없는 페이지일 경우, 간단한 안내 문구를 나타내도록 수정할 수 있다.

 

<Route path="*" component= { NonPage } />
와일드 카드 *가 의미하는 것은 이 곳에 어떤 텍스트가 들어가도 상관없다는 뜻이다.

 

 

이를 통해 안내 문구를 추가하였다고 생각한 후, / 경로로 이동하게 되면, Main과 NonPage 컴포넌트 2개가 렌더링되는 것을 확인할 수 있다. 분명 없는 페이지에서만 NonPage 컴포넌트를 보여주려고 하였으나, 오히려 모든 경로에서 보여지도록 바뀌게 되었다. 이러한 오류를 해결하기 위해 Switch 태그를 사용할 수 있다.

 ```

<Switch>
  <Route path="/" exact component= { Main } />
  <Route path="/water" exact component= { Water } />
  <Route path="/juice" exact component= { Juice } />
  <Route path="*" component= { NonPage } />
</ Switch>

```

Switch태그는 일치하는 단 하나의 컴포넌트만 렌더링한다. 위와 같을 경우 사용자가 없는 경로인 /melon으로 이동할 경우, 가장 마지막 부분에 있는 path="*"로 인해 NonPage 컴포넌트 단 하나만 렌더링되게 된다.

 

불필요한 렌더링 없이 단 하나의 컴포넌트만 렌더링하여 사용해야 할 경우, Switch태그를 통해 유용하게 라우팅을 구현할 수 있다.
