## useId

useId는 클라이언트와 서버간의 hydration의 mismatch를 피하면서 유니크 아이디를 생성할 수 있는 새로운 훅이다. 이는 주로 고유한 id가 필요한 접근성 API와 사용되는 컴포넌트에 유용할 것으로 기대된다. 이렇게 하면 React 17 이하에서 이미 존재하고 있는 문제를 해결할 수 있다. 그리고 이는 리액트 18에서 더 중요한데, 그 이유는 새로운 스트리밍 렌더러가 HTML을 순서에 어긋나지 않게 전달해 줄 수 있기 때문이다.

아이디 생성 알고리즘은 여기에서 살펴볼 수 있다. 아이디는 기본적으로 트리 내부의 노드의 위치를 나타내는 base 32 문자열이다. 트리가 여러 children으로 분기 될때 마다, 현재 레벨에서 자식 수준을 나타내는 비트를 시퀀스 왼쪽에 추가하게 된다.

```
    const id = useId();
    const id2 = useId();

    useEffect(() => {
        const myComponentDOMElement1 = document.querySelector(`[id="email-${id}"]`); // this will work
        const myComponentDOMElement2 = document.querySelector(`[id="password-${id}"]`); // this will work
        console.log(myComponentDOMElement1);
        console.log(myComponentDOMElement2);
        const myComponentDOMElement3 = document.querySelector(`[id="email-${id2}"]`); // this will work
        const myComponentDOMElement4 = document.querySelector(`[id="password-${id2}"]`); // this will work
        console.log(myComponentDOMElement3);
        console.log(myComponentDOMElement4);
    }, []);
    
        return (
        <>
            <React.Fragment>
                <label htmlFor={`email-${id}`}>Email</label>
                <input type="text" id={`email-${id}`} name="email" />

                <label htmlFor={`password-${id}`}>Password</label>
                <input type="password" id={`password-${id}`} name="password" />
            </React.Fragment>
            <React.Fragment>
                <label htmlFor={`email-${id2}`}>Email</label>
                <input type="text" id={`email-${id2}`} name="email" />

                <label htmlFor={`password-${id2}`}>Password</label>
                <input type="password" id={`password-${id2}`} name="password" />
            </React.Fragment>
        </>
    )
    ```
