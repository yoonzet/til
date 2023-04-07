### React.memo

const MemoizedComponent = memo(SomeComponent, arePropsEqual?)

React.memo는 Memoization(메모이제이션) 기법으로 동작하며, 고차 컴포넌트(Higher Order Component, HOC)이다.

컴포넌트가 props로 동일한 결과를 렌더링하면, React.memo를 호출하고 결과를 메모이징(Memoizaing) 하도록 래핑하여 경우에 따라 성능 향상을 할 수 있다.
즉, React는 컴포넌트를 재렌더링하지 않고 마지막으로 렌더링된 결과를 재사용한다.

컴포넌트가 변경되지 않는경우 리렌더링을 건너뛸 수 있다.
렌더링 최적화를 하지 않을 컴포넌트에 React.memo 를 사용하는것은, 불필요한 props 비교만 하는 것이기 때문에 실제로 렌더링을 방지할수있는 상황이 있는 경우에만 사용하는것이 좋다.


```

import React, { useEffect, useMemo, useState } from 'react';

const TextView = ({ text }) => {
  useEffect(() => {
    console.log('text 변경됨');
  });
  return <div>{text}</div>;
};

const CountView = ({ count }) => {
  useEffect(() => {
    console.log('count가 변경됨');
  });
  return <div>{count}</div>;
};

function App() {
  const [count, setCount] = useState(0);
  const [text, setText] = useState('a');

  return (
    <div className="App">
      <TextView text={text} />
      <input value={text} onChange={(e) => setText(e.target.value)} />
      <br />
      <CountView count={count} />
      <button onClick={() => setCount(count + 1)}>count 1 증가</button>
    </div>
  );
}

export default App;

```
