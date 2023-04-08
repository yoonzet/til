### useContext

#### Context API 3가지 주요 개념
```
createContext(initialValue)
```
- context 객체 생성
- createContext 함수 호출 시 Provider와 Consumer 컴포넌트 반환
- initialValue는 Provider를 사용하지 않았을 때 적용될 초기값을 의미

```
Context.Provider
```
- 생성한 context를 하위 컴포넌트에 전달하는 역할

```
Context.Consumer
// useContext 사용 시
const data = useContext(Context);
```
- context의 변화를 감시하는 컴포넌트
- 설정한 상태를 불러올 때 사용
