# 4-week-soyun-1

<aside>
๐ก 7๊ฐ 1,2๋ฃ๊ธฐ / useState, useEffect, useRef ์กฐ์ฌ

</aside>

- Self Closing
    
    `<ํ๊ทธ />` 
    
    ํ๊ทธ์ ํ๊ทธ ์ฌ์ด์ ์๋ฌด ๋ด์ฉ์ด ๋ค์ด๊ฐ์ง ์์ ๋, `<ํ๊ทธ />` ๋ก ํด์ค ์ ์์ต๋๋ค.
    
- ๋ฆฌ์กํธ Fragment
    
    ๋ ๊ฐ ์ด์์ ํ๊ทธ๋ฅผ ๋ฃ์ ๋, ๊ผญ ํ๋์ ํ๊ทธ๋ก ๋ซ์์ค์ผํ๋ค.
    
    divํ๊ทธ๋ก ๋ฌถ๊ธฐ ์ข ๋ถํธํ๋ฉด `<> </>`๋ก ๋ฌถ์ด๋ ๋๋ค. `<> </>`๊ฐ ๋ฐ๋ก Fragment์ด๋ค.
    
    ```jsx
    function App(){
    	return(
    		<>
    			<div/>
    			<div/>
    		</>
    	);
    }
    ```
    
- ๋ฆฌ์กํธ ์ฃผ์
    
    `{/* */}`
    

# useState

state(์ํ)๋, ์ปดํฌ๋ํธ์์ ๋์ ์ธ ๊ฐ์ ์๋ฏธํ๋ค.

state๋ฅผ ๊ด๋ฆฌํ๊ธฐ ์ํด, `useState` ๋ผ๋ ํจ์๋ฅผ ์ฌ์ฉํ๋ค.

```jsx
/*useState๋ฅผ ์ฌ์ฉํ๊ธฐ ์ํด importํด์ผํ  ๊ฒ*/
import React,{useState} from'react';

/*์ฌ์ฉํ๊ธฐ(๋ฐฐ์ด ๋น๊ตฌ์กฐํ ํ ๋น)*/
const [number,setNumber]=useState(0);
```

```jsx
import React from 'react';

function Counter() {
  const onIncrease = () => {
    console.log('+1')
  }
  const onDecrease = () => {
    console.log('-1');
  }
  return (
    <div>
      <h1>0</h1>
      <button onClick={onIncrease}>+1</button>
      <button onClick={onDecrease}>-1</button>
    </div>
  );
}

export default Counter;
```

```jsx
import React from 'react';
import Counter from './Counter';

function App() {
  return (
    <Counter />
  );
}

export default App;
```

- ๋ฐฐ์ด ๋น๊ตฌ์กฐํ ํ ๋น
    
    ```jsx
    useState(0);
    const numberState=[useState[0],useState[1]];
    const number=numberState[0];
    const useState=numberState[1];
    
    /*๋ฐฐ์ด ๋น๊ตฌ์กฐํ ํ ๋น*/
    const [number,setNumber]=useState(0);
    ```
    
    ![0726-1.png](https://polyester-orchestra-61e.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F4b7a8702-7006-4c0d-a794-348375a3f326%2F0726-1.png?table=block&id=24edee3d-897b-48f9-91a7-4687a0d7a6f1&spaceId=9e9794b7-89ce-4e4b-ad10-420fe112a252&width=2000&userId=&cache=v2)
    

`useState()` ๋ ๋ฐฐ์ด์ ์์ฑํด์ฃผ๋ ํจ์์ด๋ค.

๋ฐฐ์ด์ ์ฒซ ๋ฒ์งธ ์์๋ โํ์ฌ ์ํโ

๋ฐฐ์ด์ ๋ ๋ฒ์งธ ์์๋ โSetterํจ์โ ์ด๋ค. 

```jsx
/* setNumber(ํ๋ผ๋ฏธํฐ); */
setNumber(number+1);
```

Setter ํจ์๋ ์ ๋ฌ ๋ฐ์ ๊ฐ์ ์ต์  ์ํ๋ก ํ๋ ํ๋ผ๋ฏธํฐ๋ฅผ ๋ฃ์ด ์ํ๋ฅผ ์ค์ (set)ํด์ค๋ค.

# useEffect

`useEffect()` ํจ์๋ ํ๋ผ๋ฏธํฐ๋ฅผ ๋๊ฐ ๋ฃ๋๋ค. 

์ฒซ๋ฒ์งธ ํ๋ผ๋ฏธํฐ์๋ ํจ์๋ฅผ ๋ฃ๋๋ค.

์ด ํจ์๋ ์์กด๊ฐ์ด ๋ณํจ์ ๋ฐ๋ผ ์ฌ๋ ๋๋ง ๋๋ ์ฝ๋๋ฅผ ์ ์ํ๋ค.

๋๋ฒ์งธ ํ๋ผ๋ฏธํฐ์๋ ์์กด๊ฐ์ด ๋ค์ด์๋ ๋ฐฐ์ด(deps)์ ๋ฃ๋๋ค. 

์์กด๊ฐ์ด ๋ณํํ๋ฉด ํจ์๊ฐ ์ฌ๋ ๋๋ง(์ฌ์ ์)๋๋ค.

# useRef

DOM ์ ์ง์  ์๋์ง ์๊ณ  ๊ฐ์ DOM์ ์์ ํ์ฌ DOM์ ๋ณํ๋ฅผ ์ฃผ๋๊ฒ ๋ฆฌ์กํธ์ง๋ง, DOM์ ์ ํํด์ผ ํ  ๋๊ฐ ์๋ค.

์ด๋ ์ฐ๋๊ฒ `useRef()` ํจ์์ด๋ค.

+) ์ปดํฌ๋ํธ ์์์ ์กฐํ ๋ฐ ์์ ํ  ์ ์๋ ๋ณ์๋ฅผ ๊ด๋ฆฌํ  ๋๋ ์ฌ์ฉํ๋ค๊ณ ํจ.

useRef ๋ก ๊ด๋ฆฌํ๋ ๋ณ์๋ ๋ณ๊ฒฝ์ฌํญ์ด ์๊ฒจ๋ ์ปดํฌ๋ํธ๊ฐ ๋ฆฌ๋ ๋๋ง ๋์ง ์ํ๋ค.  ์ ๋ชจ๋ฅด๊ฒ ์ด์..