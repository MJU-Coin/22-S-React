# 4-week-soyun-2

<aside>
๐ก useMemo, useCallback ์กฐ์ฌํ๊ธฐ / Hook(์น์7-3,7-4)

</aside>

- ๋ ๋๋ง์ด ๋ญ๊น..
    - ์ปดํฌ๋ํธ๊ฐ ๋ ๋๋ง ๋๋ค๋ ๊ฒ์ ๊ทธ ์ปดํฌ๋ํธ๊ฐ ํธ์ถ๋๊ณ  ์คํ๋๋ ๊ฒ์ ๋งํ๋ค.
    - ์ปดํฌ๋ํธ๊ฐ ์คํ๋  ๋ ๋ง๋ค ๋ด๋ถ์ ์ ์๋ ๋ด์ฉ์ด ๋งค๋ฒ ๋ค์ ์ ์ธ๋๋ค.
    - ์ปดํฌ๋ํธ๋ ์์ ์ state๊ฐ ๋ณ๊ฒฝ๋๊ฑฐ๋, ๋ถ๋ชจ์๊ฒ์ ๋ฐ๋ props๊ฐ ๋ณ๊ฒฝ๋์์ ๋ ๋ง๋ค ๋ฆฌ๋ ๋๋ง๋๋ค.
- useMemo์ useCallback์ ์ ์ธ๊น
    - state์ props๊ฐ ์ฌ๋ฌ๊ฐ์ด๊ณ , ๊ทธ์ค ํ๋๋ง ๋ณ๊ฒฝ๋์๋๋ฐ ๋ค๋ฅธ state์ props๊ฐ ๋ค๊ฐ์ด ๋ ๋๋ง๋๋ฉด ๋งค์ฐ ๋นํจ์จ์ ์ผ๊ฒ์ด๋ค.

# useMemo

```jsx
const memoizedValue = useMemo(()=> computeExpensiveValue(a,b) , [a,b] )
```

useMemoํจ์๋

๋๋ฒ์งธ ์ธ์์ธ ์์กด์ฑ ๋ฐฐ์ด์ด ๋ณ๊ฒฝ๋๊ธฐ ์  ๊น์ง

์ฒซ๋ฒ์งธ ์ธ์๋ก ๋ฐ์ ๊ฐ์ ๊ธฐ์ตํ๋ค.

```jsx
const getNumber = (number) => {
  console.log("์ซ์๊ฐ ๋ณ๋๋์์ต๋๋ค.");
  return number;
};

const getText = (text) => {
  console.log("๊ธ์๊ฐ ๋ณ๋๋์์ต๋๋ค.");
  return text;
};

const ShowState = ({ number, text }) => {
  const showNumber = getNumber(number);
  const showText = getText(text);

  return (
    <div className="info-wrapper">
      {showNumber} <br />
      {showText}
    </div>
  );
```

์ ์์ ์๋ number์ text๋ฅผ props๋ก ํ๋ ShowState๋ผ๋ ์ปดํฌ๋ํธ๊ฐ ์๋ค.

showNumber ๋ showText ๋ ์ค ํ๋๋ผ๋ ๋ณ๊ฒฝ๋๋ฉด ๋ชจ๋ ์ฌ๋ ๋๋ง๋ ๊ฒ์ด๋ค. 

```jsx
const getNumber = (number) => {
  console.log("์ซ์๊ฐ ๋ณ๋๋์์ต๋๋ค.");
  return number;
};

const getText = (text) => {
  console.log("๊ธ์๊ฐ ๋ณ๋๋์์ต๋๋ค.");
  return text;
};

const ShowState = ({ number, text }) => {
  const showNumber = useMemo(()=>getNumber(number),[number]);
  const showText = useMemo(()=>getText(text),[text]);

  return (
    <div className="info-wrapper">
      {showNumber} <br />
      {showText}
    </div>
  );
```

์ด์  ์์ ์์ showNumber์ showText์ useMemoํจ์๋ฅผ ์ฌ์ฉํด์ ๊ฐ์ ์ ๋ฌํด์ฃผ๋ ์ฝ๋์ด๋ค.

์ด๋ ๊ฒ ํ๋ฉด showNumber๋ showText ๊ฐ ๋ณ๊ฒฝ๋๋ฉด, ๋ณ๊ฒฝ๋ ๊ฒ๋ง ์ฌ๋ ๋๋งํ ๊ฒ์ด๋ค.

# useCallback

useMemo์ ๊ฐ์ ์ด์ ๋ก ์ฌ์ฉ๋๋ค.

## useMemo์ useCallback์ ์ฐจ์ด

```jsx
const getItems = useCallback(
    increaseValue => {
      return [
        number + increaseValue,
        number + 1 + increaseValue,
        number + 2 + increaseValue,
      ]
    },
    [number]
  )
```

```jsx
const getItems = useMemo(
    () => increaseValue => {
      return [
        number + increaseValue,
        number + 1 + increaseValue,
        number + 2 + increaseValue,
      ]
    },
    [number]
  )
```

์์ ๋ ์ฝ๋๋ number์ ๊ฐ์ ์ค์ ํ๊ณ , increaseValue๊ฐ(input)์ด ๋ค์ด์ค๋ฉด number์ increaseValue๋ฅผ ํ๋ํ๋ ๋ฃ์ด์ฃผ๋ ์ฝ๋์ด๋ค.

๊ฐ์ ๊ธฐ๋ฅ์ด์ง๋ง, useCallback์ด๋ useMemo๋์ ๋ฐ๋ผ ๋ฏธ์ธํ๊ฒ ์ฝ๋๊ฐ ๋ฌ๋ผ์ก๋ค.

```jsx
//useMemo
useMemo(()=>fn, deps)
//useCallback
useCallback(fn, deps)
```

- useMemo๋ ํจ์๋ฅผ ๋ฐํํ์ง ์๊ณ  ํจ์์ ๊ฐ๋ง memoizationํด์ ๋ฐํํ๊ธฐ ๋๋ฌธ์ ํ๋ผ๋ฏธํฐ๋ก ํจ์(์์๋ ํ์ดํํจ์)๋ฅผ ์ ๋ฌํด์ค์ผํ๋ค.
- useCallback์ ํจ์ ์์ฒด๋ฅผ ๋ฐํํ๋ค.

# ์ปค์คํ Hook

## ์ปค์คํ Hook์ด๋?

โ ๊ฐ๋ฐ์์ ์๋ง์ ๋ฐ๋ผ ์ฝ๋๋ฅผ ๋ฌถ์ด Hook์ผ๋ก ๋ง๋ ๊ฒ.

โ ๋ฐ๋ณต๋๋ ๋ก์ง์ ์ฌ์ฌ์ฉํ๊ธฐ ์ํด ์ฌ์ฉํ๋ค. 

## ์ฌ์ฉ๋ฐฉ๋ฒ?

1. ์ปค์คํ Hook์ ๊ธฐ์กด์ Hook ๊ท์น์ ๊ทธ๋๋ก ๋ฐ๋ผ์ผ ํ๋ค.
- Hook ๊ท์น
    1. ๋ฆฌ์กํธ ํจ์ ๋ด์์๋ง ์ฌ์ฉ๋ ๊ฒ.( ์ผ๋ฐ์ ์ธ js๋ ์๋๋ค.)
    2. ๋ฆฌ์กํธ ํจ์ ์ต์์์์ ํธ์ถํ ๊ฒ.(๋ฐ๋ณต๋ฌธ,์กฐ๊ฑด๋ฌธ ๋ฑ ํธ์ถ ์์๊ฐ ๊ผฌ์ผ ๊ฐ๋ฅ์ฑ์ ์์ ๊ธฐ์ํด)
1. ๋ค๋ฅธ ํ ๋ค๊ณผ ๋๊ฐ์ด ์ปค์คํ ํ์ ๋ง๋ค๋ ์์ use๋ง ๋ถ์ฌ์ฃผ๋ฉด ๋๋ค.

## etc

- ์ปค์คํ ํ์ ์ฌ์ฉํ  ๋ ๊ณ ๋ คํด์ผํ  ์ 
    - ์ปค์คํํ์ ๋๋ฌด ๋จ๋ฐํ์ง ์์๋์ง. (์ฌ์ฉํ์ง ์์๋ ๋  ๊ณณ์ ์ฌ์ฉX)
    - ๊ธฐ๋ฅ์ ์ ๋ถ๋ฆฌํด์ ํ์ผ๋ก ๋ง๋ค์๋์ง.( ๋จ์ผ๊ธฐ๋ฅ? ํด๋ฆฐ์ฝ๋์ ๊ด๋ จ์๋ค๊ณ ํจ.)
    - ์ฌ์ด๋์ดํํธ๊ฐ ์ผ์ด๋  ๊ฐ๋ฅ์ฑ์ ์๋์ง. (๋ ๋๋ง ์ค์ ์คํ๋๋ ์ ์ ๊ณ ๋ ค)

# ์๊ฐ(?)

๋ฆฌ์กํธ ํ๋ก์ ํธ๋ก to-do list๋ฅผ ๋ง์ด ํ๋๋ผ๊ตฌ์.

์ปค์คํ Hook์ฒ๋ผ ์ปค์คํ ๋จ์ถํค๋ฅผ ์ง์  ์ง์ ํด์ ์ฌ์ฉํ  ์ ์๋ to-do list๋ฅผ ๋ง๋ค๊ณ ์ถ์ด์.

(ํ๋์ ํ๊ดํ์ ctrl+alt+b ๋ผ๋๊ฐ..)

์คํ๊ฐ๋ฅํ์ง๋ ๋ชจ๋ฅด๊ฒ ์ต๋๋ค ใใ