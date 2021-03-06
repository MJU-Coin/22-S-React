# Hooks

앞서 컴포넌트에는 두가지 종류가 있었다.

함수 컴포넌트와 클래스 컴포넌트인데 클래스 컴포넌트와 같이 생성자에서 state를 정의하고 setState함수를 활용하여 state 수정및 라이프싸이클 메소드를 사용할 수 있는것과 달리 

함수 컴포넌트에서는 state를 사용하지 못하고 라이프싸이클에 따른 기능 구현이 불가능하다.

그래서 이러한 점을 보완하기 위해 Hooks이라는 개념이 생겼다.

훅은 갈고리라는 뜻을 가진것에 걸맞게 state관련 함수 , 라이프싸이클 관련 함수 , 최적화함수 등을

갈고리 처럼 함수컴포넌트에 걸어 원하는 시점에 정해진 함수들이 실행되도록 한다.

→ 이때 실행되는 함수들이 hooks (훅을 사용할땐 앞에 use를 붙인다.)

## 대표적인 hooks

1. useState() → state를 사용하기위한 훅

1. useEffect() → side effect를 수행하기 위한 훅

//사이드 이펙트는 서버에서 데이터를 받아오거나 수동으로 돔을 변경하는 작업을 의미 (효과, 영향)

→ 클래스 컴포넌트에서 제공하는 생명주기함수를 통합해서 제공한다.

1. useMemo() → Memoized value를 리턴하는 훅

//Memoization : 최적화를 위해 사용하는 개념 → 연산량이 많이드는 함수의 호출결과를 저장한뒤 같은 입력값으로 함수를 호출했을때 새로함수를 호출하지않고 이전에 저장한 호출값을 바로 반환하는것 →시간 아낌, 중복 연산x

이 Memoization 의 결과값을 Memoized value라고 부른다.

1. useCallback() → useMemo() 훅과 유사하나 값이 아닌 함수를 반환함

1. useRef() → Reference를 사용하기 위한 훅

//Reference → 특정 컴포넌트에 접근할 수 있는 객체

1. useRef() 훅은 Reference를 반환함 (일반적인 자바스크립트 객체를 리턴함)

→ useRef() 훅은 내부의 데이터가 변경되었을 떄 따로 알리지 않음

### hooks의 규칙

1.훅은 최상위 레벨에서만 호출해야함

→ 최상위 레벨은 리액트 컴포넌트의 최상위 레벨을 의미함, 반복문+조건문+중첩된 함수들안에서 훅을 호출하면 안됨.

2,리액트 함수 컴포넌트에서만 훅을 호출해야한다.

→일반적인 js함수에서 훅을 호출하면 안됨

### Custom Hook만들기

→ 여러 컴포넌트에서 반복적으로 사용되는 로직을 훅으로 만들어 재사용하기 위해 씀