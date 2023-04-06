## useMemo

const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);

메모이제이션된 값을 반환합니다.

useMemo는 의존성이 변경되었을 때에만 메모이제이션된 값만 다시 계산 한다.   
이 최적화는 모든 렌더링 시의 고비용 계산을 방지하게 해 준다.

useMemo로 전달된 함수는 렌더링 중에 실행된다.   
통상적으로 렌더링 중에는 하지 않는 것을 이 함수 내에서 하지 말것.   
예를 들어, 사이드 이펙트(side effects)는 useEffect에서 하는 일이지 useMemo에서 하는 일이 아님.

배열이 없는 경우 매 렌더링 때마다 새 값을 계산하게 될 것이다.

## useCallback

const cachedFn = useCallback(fn, dependencies)

메모이제이션된 콜백을 반환합니다.
