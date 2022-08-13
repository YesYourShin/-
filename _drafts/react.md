---
layout: post
title: react
---

## 리액트 시작

```powershell
npx create-react-app my-app
cd my-app
npm start
```

## 서버 키는 법

```powershell
npm start
```

## return

return을 할 때 태그들은 하나의 태그 안에 있어야 됨
태그는 <></> 이런 식으로 해도 됨

## state(상태)란

계속해서 동적으로 변화하는 특정 상태  
상태에 따라 각각 다른 동작을 함

값이 바뀌면 리렌더링됨

예시 코드

```javascript
const [count, setCount] = useState(0);

const onIncrease = () => {
  setCount(count + 1);
};

const onDecrease = () => {
  setCount(count - 1);
};

return (
  <div>
    <h2>{count}</h2>
    <button onClick={onIncrease}>+</button>
    <button onClick={onDecrease}>-</button>
  </div>
);
```

useState를 사용할 때는 상태의 기본값을 파라미터로 넣어서 호출해줌  
이 함수를 호출하면 배열이 반환되는데 첫 번째 파라미터로는 현재 상태, 두 번째 파라미터로는 Setter 함수를 반환함  
배열 비구조화 할당을 통하여 각 파라미터를 추출해준 것  
Setter 함수는 파라미터로 전달 받은 값을 최신 상태로 설정해줌  
https://react.vlpt.us/basic/07-useState.html

## props

컴포넌트에서 값을 다른 컴포넌트로 전달할 수 있음

예시

```javascript
// App.js
import Counter from "./Counter";
function App() {
  const number = 5;

  return (
    <div className="App">
      <Counter initialValue={number} />
    </div>
  );
}

export default App;

// Counter.js
import React, { useState } from 'react';
const Counter = props => {

    return (
    );
};

export default Counter;

```

props는 객체로 전달됨

props받아서 쓸 때는 점표기법으로 하면 됨

```javascript
const [count, setCount] = useState(props.initialValue);
```

여러 개 전달 하고 싶을 때 스프레드 연산자 쓰기

```javascript
const counterProps = {
  a: 1,
  b: 2,
  c: 3,
  d: 4,
  e: 5,
  initialValue: number,
};
return (
  <div className="App">
    <MyHeader />
    <Counter {...counterProps} />
  </div>
);
```

객체 중 하나만 받을 수도 있음

```javascript
const Counter = ({ initialValue }) => {};
```

만약 props를 받았는데 거기서 써야될 key가 없다면 해당 컴포넌트에서 디폴트값을 설정해 줄 수도 있음

```javascript
Counter.defaultProps = {
  initialValue: 0,
};
```

useState의 파라미터도 props 가능

컴포넌트의 자식으로 배치된 요소들을 props로 전달하는 것도 가능

```javascript
// App.js
return (
  <Container>
    <div className="App">
      <MyHeader />
      <Counter {...counterProps} />
    </div>
  </Container>
);

// Container.js
const Container = ({ children }) => {
  return (
    <div style={{ margin: 20, padding: 20, border: "1px solid gray" }}>
      {children}
    </div>
  );
};

export default Container;
```
