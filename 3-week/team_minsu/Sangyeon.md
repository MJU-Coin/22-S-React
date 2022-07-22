# 리액트란

### 리액트란?

사용자 인터페이스를 만들기 위한 자바스크립트 라이브러리

페이스북에서 만든 오픈소스 자바스크립트 라이브러리

### 프레임 워크 vs 라이브러리

차이점 : 프로그램에 흐름에 대한 제어권한

프레임 워크 (Angular.js, Vue.js) : 프레임워크가 제어권한 갖고있음

라이브러리(react) : 개발자에게 제어권한이 있음

### Single Page Application (SPA)

SPA는 서버로부터 새로운 페이지를 불러오지 않고 한 페이지를 동적으로 사용하는 어플리케이션이나 웹페이지

React가 이러한 SPA를 쉽게 만들 수 있게 도와준다.

### 리액트의 장점

1. 빠른 업데이트 & 렌더링 속도
- Virtual DOM

DOM : 웹사이트를 정의하는 하나의 객체 즉, 하나의 웹사이트 정보를 모두 담고 있는 하나의 그릇

웹페이지와 실제 DOM 사이에서 중간 매개체 역할

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/552dd8c3-49d8-44d6-954a-70d6fd763e69/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220720%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220720T070619Z&X-Amz-Expires=86400&X-Amz-Signature=8cb0d43fdbacb0a218b9706f1c86b8d81641ee0e72a200c550fb29f510eda1da&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

화면이 업데이트 된다 = DOM이 수정된다.

DOM은 <div>태그 안의 색상을 바꾸기만 해도 전체 노드가 업데이트 되는 Reflow가 나타나서 매우 비효율적임

VIrtual DOM은 실제 DOM처럼 직접 수정하는 것이 아닌, 업데이트 해야할 최소한의 부분만을 찾아서 하나로 그룹화해서 DOM에 전달함

1. Component=Based

React는 컴포넌트들을 조합하여 웹페이지를 만듦

- 재사용성(Reusabliity) <중요함>

재사용성이 좋을 수록 좋은 코드이며, 재사용성을 높이려면 소프트웨어 또는 모듈이 다른 모듈에 의존하지 않고, 호환성 문제가 발생하지 않도록 만들어야 한다

재사용성의 장점 

1) 개발 기간 단축

2) 유지 보수 용이

- 리액트와 재사용성

리액트는 컴포넌트들의 조합으로 웹페이지를 만드는데, 이러한 컴포넌트를 재사용성이 높게 만들면 다른 웹사이트도 쉽고 빠르게 만들 수 있다.

1. Meta라는 스폰서 갖고있음

좋은 스폰서를 갖고 있기에, 계속 업데이트하고 계속 꾸준히 사용될 것임

1. 활발한 지식공유 & 커뮤니티

1. React Native를 이용하여 모바일 앱을 만들 수 있다.

### 리액트의 단점

1. 방대한 학습량

1. 높은 상태관리 복잡도

성능 최적화를 위해 Status를 관리를 잘 해줘야함

규모가 커질 수록 상태 관리 하기가 힘들어져서 Redux, Bo-mex, Recoil 같은 외부 상태관리 라이브러리를 사용하는 경우가 많음

### create-react-app

npx-execute npm package binaries 

react로 웹 애플리케이션을 만들기 위한 모든 설정이 되어있는 상태로 프로젝트를 생성해주는 도구

명령어

- 경로변경 : cd my-app
- 애플리케이션 실행 :  npm start

# JSX

### JSX란?

A syntax extension to JavaScript

 Java Script + XML/HTML으로, javaScript에 XML을 확장한 문법

```jsx
const element = <h1>Hello world!</h1>;
```

 

### JSX 역할

내부적으로 XML/HTML을 JavaScript로 변환시키는 역할

```jsx
React.createElement(
type,
[props],
[...children]
}
```


React 사용시 JSX 사용이 필수는 아니지만 많은 장점이 있기에 사용하는 것을 권장함

### JSX 장점

1. 간결한 코드

```jsx
JSX사용
<div>Hello, {name}</div>

JSX 사용 안함
React.createElement('div', null, `Hello, ${name}`);
```

1. 가독성 향상

      > 버그를 발견하기 쉬움

1. injection Attacks 방어

```jsx
const title=esopnse.potentiallyMaliciousInput;

// 이 코드는 안전합니다.
const element = <h1>{title}</h1>
```

React Dom은 기본적으로 렌더링하기 전에 임베딩된 값을 모두 문자열로 변환하기 때문에 명시적으로 선언되지 않은 값은 괄호 사이에 들어갈 수 없어서 XSS(Cross Site Scripting)을 방어할 수 있음

### JSX 사용법

모든 JavaScript 문법 사용 가능

 XML/HTML 문법 사용하다가 JS 사용하고 싶으면 중괄호{} 를 쓰고 안에 사용하면 됨
 ```jsx
태그의 속성에 값을 넣는 방법
// 큰따옴표 사이에 문자열 넣기
const element= <div tabIndex="0"></div>

// 중괄호 사이에 자바스크립트 코드를 넣기
const element = <img src={user.avatarUrl}></img>
```

```jsx
자식을 정의하는 방법
const elemnt={
<div>
		<h1>안녕하세요</h1>
</div>
```
# Rendering Elements

### Elements란

the smallest building Blocks of React apps

리액트 앱을 구성하는 가장 작은 블록들

### React Elements

- Virtual DOM에 존재하는 것 : React Elements
- Browser DOM에 존재하는 것 : Dom Elements

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8ab7dfd0-508c-4fbb-9c42-7744898a09c5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220720%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220720T070641Z&X-Amz-Expires=86400&X-Amz-Signature=db81bf29f38036d9912472b6ef8c04f155b3229c6fe3fec500757d9fafc2baf7&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

React Element는 DOM Elements의 가상의 Element

React Elements는 자바스크립트 객체 형태로 존재

화면에서 보이는 것들을 기술

### React Elements 특징

- 불변성

Elements 생성 후에는 children이나 attributes를 바꿀 수 없다.

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/31133728-d0c1-4746-b4c2-de698958c34c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220720%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220720T070706Z&X-Amz-Expires=86400&X-Amz-Signature=93171547bc238b504aa638fba7ca5f602853861d7095121cf5cabb06bda414c2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

Elements를 바꾸려면 새로운 Elements를 생성해서 기존의 Elements와 바꿔주어야 한다.
<br>



```jsx
funtion tick(){ 
	const element = (
		<div>
				<h1>안녕, 리액트!</h1>
				<h2>현재 시간 : {new Date().toLocaleTimeString()}</h2>
		</div>
);

	ReactDOM.render(elemnet, document.getElementById('root'));
}

setInterval(tick, 1000); // 1초만 tick함수 호출
```

기존 element를 바꿔서 시간을 계속 업데이트 하는 것이 아닌, 새로운 element를 만들어서 기존의 element와 교체하는 것이다.


# Components 와 Props

리액트는 컴포넌트 기반으로, 레고 블럭을 조립하듯 컴포넌트들을 모아서 개발

### React component의 입출력

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8e6175fd-a4ee-44c9-ad10-d7c81730018d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220722%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220722T114014Z&X-Amz-Expires=86400&X-Amz-Signature=917faace7084f02b71b2eb772a519181fa579d250af4c31c95f120816b3be004&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

React component 입력 : Props

React component 출력 : React element

React component는 속성을 받아 React element로 변환 시켜주는 것

### Component와 Element

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a4edd406-89f9-4e12-a852-f8bb5c599bdf/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220722%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220722T114037Z&X-Amz-Expires=86400&X-Amz-Signature=033dced07464954165522f49f2204a3c20ca153f264adb34fadaa4d58c6bfdfd&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

Component와 Element는 Class와 instance의 관계와 비슷하다. 붕어빵 틀 처럼 Component를 계속 찍어내는 것 처럼 Element를 찍어내는 것이다.

### Props란

Property의 줄인말, Component의 속성을 말함.

위의 그림을 보면 붕어빵에 들어가는 속 재료를 Props로 나타낼 수 있다.

컴포넌트에 전달할 다양한 정보를 담고 있는 자바스크립트 객체

### Props의 특징

1. Read-Only

읽을 수만 있다 = 값을 변경 할 수 없다

즉, 새로운 컴포넌트에 새로운 Props를 전달하여 새로운 element를 만들어서 변경해야 함

1. 모든 리액트 컴포넌트는 그들의 Props에 관해서는 Pure 함수같은 역할을 해야 한다.

즉, 모든 리액트 컴포넌트는 Props를 직접 바꿀 수 없고, **같은 Props에 대해서는 항상 같은 결과**를 보여준다

자바스크립트 특징(Pure, Unpure)

- Pure

입력 값을 변경하지 않으며, 같은 입력값에 대해서는 항상 같은 출력값을 리턴

```jsx
function sum(a,b){
	return a+b;
}
```

- Unpure

입력 값을 변경

```jsx
functino withdraw(account, amount){
	account.total -= amount;
}
```

### Props 사용법

```jsx
function App(props){
	return(
			<Profile
						name="상연"
						intrioduction="안녕하세요, 상연입니다."
						viewCount={1500}
				/>
		);
}
```

### Component

- Class Component

ES6문법 중 Class를 이용하여 만든 Component

React.Component를 상속받아서 만듦

```jsx
class Welcome extends React.Component{
		render(){
				return <h1>안녕, {this.props.name}</h1>;
	}
}
```

- Function Component

```jsx
function Welcome(props){
		return <h1>안녕, {props.name}</h1>;
}
```

### Component 이름

Component 이름은 항상 대문자로 시작해야 한다.

소문자로 쓰면 DOM태그로 인식함

### Component 렌더링

```jsx
function Welcome(props){
	return <h1>안녕, {props.name}</h1>;
}

const element = <Welcome name="인제"/>;
ReactDOM.render(
	element,
	document.getElementById('root')
);
```

### Component 합성

Component 안에 또 다른 Component를 쓸 수 있다.

복잡한 화면을 여러 개의 Component로 나누어서 구현 가능하다.

```jsx
function Welcome(props){
	return <h1>Hello, {props.name}</h1>;
}

function App(props) {
	return(
			<div>
					<Welcome name="Mike" />
					<Welcome name="Steve" />
					<Welcome name="Jane" />
			</div>
	)
}

ReactDOM.render(
	<App />,
	document.getElementById('root')
);
```

### Component 추출

큰 컴포넌트를 산사조각내면 재사용성이 높아지고 개발 속도가 향상됨

```jsx
function Comment(props) {
  return(
    <div className="comment">
      <div className="user-info">
        <img className="avatar"
          src={props.author.avatarUrl}
          alt={props.author.name}
          />
          <div className="user-info-name">
            {props.author.name}
            </div>
      </div>
    </div>

    <div className="comment-text">
      {props.text}
    </div>

    <div className="comment-date">
      {formatDate(props.date)}
    </div>
  );
}
```

1. Avatar 추출

```jsx
function Avatar(props){
	return (
		<img className="avatar"
				src={props.user.avatarUrl}
				alt={props.user.name}
			/>
	);
}
```

```jsx
function Comment(props) {
  return(
    <div className="comment">
      <div className="user-info">
        <Avatar user={props.author} />
          <div className="user-info-name">
            {props.author.name}
            </div>
      </div>
    </div>

    <div className="comment-text">
      {props.text}
    </div>

    <div className="comment-date">
      {formatDate(props.date)}
    </div>
  );
}
```

# State and Lifecycle

### State란

리액트 Component의 변경 가능한 데이터

state는 개발자가 정의함

렌더링이나 데이터 흐름에 사용되는 값만 state에 포함시켜야함

자바스크립트 객체

```jsx
class LikeButton extends React.Component {
	constructor(props){           // 생성자
		super(props);

		this.state = {             //State 정의
				liked : false
		};
	}
	...
}
```

state는 직접 수정하면 안된다

```jsx
// state를 직접 수정 (잘못된 예시)
this.state = {
	name.'Inje'
};

// setState 함수를 통한 수정 (옳바른 예시)
this.setState({
		name:'Inje'
});
```

### Life Cylce

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/982c770e-2e9c-4f7f-b166-737b136c3e4c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220722%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220722T114101Z&X-Amz-Expires=86400&X-Amz-Signature=27f184d715fefe8c5914e0bc702a4f2ce07aef2db8aa2d2a0ae9609757280aa2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

- 출생 (Mounting)
1. constructor 실행 ( 컴포넌트의 state 정의)
2. Component 렌더링
3. componentDidMount 호출

- 인생(Updating)
1. New props, setState(), forceUpdate()로 업데이트 됨
2. componentDidUpdate 호출

- 사망(Ummounting)

/상위 컴퍼넌트에서 현재 컴퍼넌트를 더이상 화면에 표시하지 않을 때 사망함.

사망하기 직전에 componentWillUnmount 함수 호출

컴포넌트가 계속 존재하는 것이 아니라, 시간의 흐름에 따라 생성되고 업데이트 되다가 사라짐