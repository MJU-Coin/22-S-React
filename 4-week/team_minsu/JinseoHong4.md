컴포넌트는 두가지로 나뉘어진다.

Function Component

- state 사용 불가
- Lifecycle에 따른 기능 구현 불가.
- hook 으로 이러한 한계 극복

Class Component

- 생성자에서 state 정의
- setState() 함수를 통해 state 업데이트
- Lifecycle methods 제공

# hook

리액트 state와 생명주기 기능에 갈고리를 걸어 원하는 시점에 정해진 함수를 실행되도록 만들때 그 함수.

이름 앞에 use 를 붙여 훅인 것을 알려줘야함

### useState() - state를 사용하기 위한 hook

```jsx
const [변수명, set함수명] = useState(초기값);
```

useState() 를 호출할 때에는 파라미터로 선언할 state의 초기값 들어감.

리턴값으로 배열 반환,

```jsx
import React, { useState } from "react";

function Counter(props) {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>총 {count}번 클릭했습니다.</p>
      <button onClick={() => setCount(count + 1)}>클릭</button>
    </div>
  );
}
```

클래스 컴포넌트는 setState 로 모든 state 조정 가능

useState는 변수 각각에 대해 set 함수가 따로 존재.

### useEffect() - side effect를 수행하기 위한 hook.

리액트에서 side effect = 효과, 영향

서버에서 데이터 받아옴, 수동으로 돔 변경 등의 작업 → 다른 컴포넌트에 영향을 미칠 수 있으며, 렌더링 중에는 작업이 완료될 수 없음.

이러한 작업을 사이드에서 함.

생명주기 함수와 동일한 기능을 제공하는 함수.

```jsx
useEffect(이펙트 함수, 의존성 배열);
```

의존성 배열: 이 함수가 의존하고 있는 배열. 배열 안의 값이 변경되면 이펙트 함수 실행

이펙트 함수는 처음 렌더링된 이후와 업데이트로 인한 재렌더링에 실행

### useMemo

Memoized value를 리턴하는 hook

Memoization - 최적화를 위해 사용하는 개념

비용이 높은 함수의 호출결과를 저장, 같은 입력값으로 함수를 호출하면 전에 저장해놨던 결과를 출력.

```jsx
const memoizedValue = useMemo(
	() => {
		//연산량이 높은 작업을 수행하여 결과를 반환
		return computeExpnsiveValue(의존성 변수1, 의존성 변수2);
	},
	[의존성 변수1, 의존성 변수2]
);
```

의존성 배열의 변수가 변했을 때에만 함수를 호출, 그렇지 않으면 기존함수의 결과 그대로 반환

빠른 렌더링 가능.

렌더링이 일어나는동안 실행. 따라서 사이드 이펙트같은 렌더링이 일어나는 동안 실행되면 안되는 기능들은 넣으면 안됨.

의존성 배열을 넣지 않을 경우, 매 렌더링마다 함수가 실행됨.

빈 배열일 경우, 컴포넌트 마운트 시에만 호출됨. 변경 X
