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

## useRef

import 해줘야 함

```javascript
import { useRef } from "react";
```

useRef(); 를 변수에 담아주면 변수에 React.MutableRefObject 라는 게 저장이 된다.

MutableRefObject는 HTML의 요소를 접근할 수 있는 기능을 함

접근할 요소에 ref={해당변수}를 입력하면 접근을 할 수 있게 된다.

해당 요소를 포커스 시키고 싶다면 해당변수.current.focus()를 하면 된다.

레퍼런스 객체는 현재 가르키는 값을 current라는 값으로 불러올 수 있음

## 오류?

console.log()로 테스트를 하던 도중 한 번만 실행되야 할 console.log가 두 번 실행되는 것을 발견하였다.

왜 그런가 찾아보니 index.js에 StrictMode가 있어서 그런 것이었음

https://velog.io/@hyes-y-tag/React-useEffect%EA%B0%80-%EB%91%90%EB%B2%88-%EC%8B%A4%ED%96%89%EB%90%9C%EB%8B%A4%EA%B3%A0

## 에러

[Warning: Each child in a list should have a unique "key" prop.] 에러

map을 이용할 때는 자식 컴포넌트마다 독립적인 key 값을 넣어줘야 한다.

예

```javascript
{
  ["AAA", "BBB", "CCC"].map((item) => <div key="{item}">{item}</div>);
}
```

https://crong-dev.tistory.com/47

## 단방향 데이터

react는 같은 레벨의 컴포넌트에서는 데이터를 바로 보낼 수 없다.
항상 위에서 아래로만 보낼 수 있음
state 끌어올리기

## Lifecycle

탄생 -> 변화 -> 죽음 순  
탄생(Mount) 화면에 나타나는 것, ex) 초기화 작업  
변화(Update) 업데이트(리렌더), ex) 예외 처리 작업  
죽음(UnMount) 화면에서 사라짐, ex) 메모리 정리 작업

React Component Lifecycle Methods  
클래스형 컴포넌트에서만 사용가능
Mount: ComponentDidMount
Update: ComponentDidUpdate
UnMount: ComponentWillUnmount

use키워드를 붙여서 클래스 컴포넌트가 가지고 있는 근본적인 기능을 함수형 컴포넌트에서 hooking 해서 쓸 수 있는 기능을 React Hooks 라고 함

useEffect 뒤에 디펜덴시 어레이를 전달하면 Mount

```javascript
useEffect(() => {
  console.log("Mount");
}, []);
```

디펜덴시 어레이을 전달하지 않으면 Update

```javascript
useEffect(() => {
  console.log("Update");
});
```

디펜덴시 어레이의 값이 변하면 콜백함수가 작동함

```javascript

```

## Memoization

이미 계산 해 본 연산 결과를 기억 해 두었다가 동일한 계산을 시키면, 다시 연산하지 않고 기억 해 두었던 데이터를 반환 시키게 하는 방법

## useMemo

Memoization하고 싶은 함수를 useMemo로 감싸고, 뒤에 디펜던시 어레이를 주면 사용가능
디펜던시 어레이 안에 있는 것이 변화하지 않으면 똑같은 리턴을 반환함

## React.memo
