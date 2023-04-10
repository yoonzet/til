### useReducer
 - useState를 대체할 수 있는 함수이다.

 - React에서 컴포넌트의 상태 관리를 위해 기본적으로 가장 많이 쓰이는 hook은 state이다.

 - 좀 더 복잡한 상태 관리가 필요한 경우 reducer를 사용할 수 있다.
   ( 콜백대신 dispatch를 전달할 수 있기 때문이라고 볼 수 있는데, 이 부분은 이후 확인해 보자. )

 - reducer는 이전 상태와 Action을 합쳐, 새로운 state를 만드는 조작을 말한다.
  ```
import React, { useReducer } from "react";
const [state, dispatch] = useReducer(reducer, initialState, init);
```
1. state

 - 컴포넌트에서 사용할 상태

2. dispatch 함수

 - 첫번째 인자인 reducer 함수를 실행시킨다.

 - 컴포넌트 내에서 state의 업데이트를 일으키키 위해 사용하는 함수

3. reducer 함수

 - 컴포넌트 외부에서 state를 업데이트 하는 함수

 - 현재state, action 객체를 인자로 받아, 기존의 state를 대체하여 새로운 state를 반환하는 함수

4. initialState

 - 초기 state

5. init

 - 초기 함수 (초기 state를 조금 지연해서 생성하기 위해 사용)
