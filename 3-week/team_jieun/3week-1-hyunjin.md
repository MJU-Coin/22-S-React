## Node.js

- js로 네트워크 애플리케이션을 개발할 수 있게 해주는 환경
- 브라우저에서만 돌아가던 js를 외부 응용 프로그램으로 빼서 브라우저 없이 돌아갈 수 있게 자체 엔진이라고 생각하면 된다.
→ 그렇기 때문에 node.js로 js를 활용해 웹을 벗어나 서버도 만들 수 있고 다양한 것들이 제작 가능하게 됨

## npm(node package manager)

- node.js를 위한 package manager 
- package manager(: 프로젝트를 하면서 필요한 다양한 외부 패키지들의 버전, 의존성을 관리해주는 것)
- node.js를 설치하면 자동으로 설치됨

## react?

- ui를 만들기 위한 js 프레임워크 → 자주 사용되는 기능을 정리해 모아둔 것

## spa(single page application)

: 하나의 페이지만 존재하는 웹사이트/어플 → 사용자가 특정 페이지를 요구했을 때 그 페이지를 보여줌

- react가 spa를 쉽고 빠르게 만들 수 있게 해줌

## react 특징

- 빠른 업데이트(화면전환)을 위해 virtual DOM을 사용 (가상의 DOM)
- component(구성요소) 기반
- 레고를 조립하듯 component들을 모아서 개발
- 재사용성: 계속해서 다시 사용이 가능한 성질
- 소프트웨어를 개발할 때 재사용성이 높게 개발해야 함
- 리액트와 재사용성
- 재사용성이 높은 컴포넌트를 만들어야 함

# <JSX>

: js의 문법을 확장시킨 것 

- js + xml/html

```jsx
ex) JSX 코드
const element = <h1>hi</h1>;
```

- JSX의 역할

 - 내부적으로 XML/HTML 코드를 JS로 변환하는 과정을 거친다. 따라서 실제로 JSX 코드를 작성해도 최종적으로는 JS코드가 나온다.

```jsx
//JSX를 사용한 코드
const element = (
	<h1 className = "greeting">
		hello, world!
	</h1>
)

//JSX를 사용하지 않은 코드
const element = React.createElement(
	'h1',
	{className: "greeting"},
	'hello world!'
)
-> React.createElement()의 결과

const element ={
	type: 'h1', //element의 유형
	props: { //속성들이 들어감
	className: "greeting",
	children: 'hello, world!' //현재 element가 포함한 자식 element
	}
}
```

 - 리액트에서 JSX를 사용하는 것은 필수는 아니지만 생산성, 가독성이 좋고 비교적 간단하기 때문에 편리하다.

- JSX의 장점

 - 간결한 코드

 - 가독성 향상 → 버그를 발견하기 쉬움

 - Injection Attacks 방어

- jsx 사용법

 - {} ← 중괄호 안에는 js코드가 들어간다고 생각하면 됨

 - 자식을 정의하는 방법

```jsx
const element = (
	<div>
		<h1>안녕</h1>
		<h2>잘가</h2>
	</div>
);
```

# <Elements>

: react app을 구성하는 가장 작은 블록들

- 화면에서 보이는 것들을 기술한다.
- react elements는 js 객체 형태로 존재한다.
- 컴포넌트 렌더링을 위해 모든 컴포넌트가 createElement 함수를 통해서 elements로 변환된다.

<aside>
💡 ‘불변성’을 가지고 있음 → 한번 생성된 elements는 변하지 않는다 → elements 생성 후에는 children이나 attributes를 바꿀 수 없다.

- ex) component : 붕어빵 틀, element : 완성된 붕어빵

</aside>

### elements 렌더링하기

```jsx
<div id="root"></div> -> root DOM Node
//모든 리액트 앱에 필수적으로 들어가는 중요한 코드
//div 안에 있는 모든 것이 리액트 DOM에 의해 관리된다.
```

- 리액트 elements가 렌더링되는 과정은 virtual DOM에서 실제 DOM으로 이동하는 과정
- elements를 업데이트하려면?

 - 새롭게 업데이트 된 elements를 기존의 elements하고 바꿔치기한다!