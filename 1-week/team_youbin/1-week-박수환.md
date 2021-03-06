## 상단의 태그

### head 태그

메타데이터가 담기는 곳

- 페이지의 제목
- 파비콘
    
    ```html
    <link rel="shortcut icon" href="./favicon.png" type="image/x-icon">
    ```
    
- 기타 메타 정보
    
    뷰포트 관련 정보
    
    ```html
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    ```
    
    Open Graph 정보 : 페이스북, 카카오톡 등에 링크 공유시 카드효과 기능
    
    ```html
    <meta property="og:title" content="이름">
    <meta property="og:description" content="내용">
    <meta property="og:image" content="이미지">
    ```
    
- CSS 자바스크립트 등의 코드 및 링크

### 시맨틱 태그
```html
<header>
  ```
페이지나 구획의 제목 역할을 하는 요소들을 두는데 사용됩니다.

로고와 제목, 검색창 등이 들어갑니다.
```html
<nav>
  ```
링크들을 포함하는 태그입니다.

주로 페이지의 메뉴들이나 색인 등에 사용됩니다.
```html
<footer>
  ```
페이지나 구획의 최하단에 보여지는 푸터에 사용됩니다.

페이지의 주인 연락처 및 저작권 정보 등이 들어갑니다.
```html
<main>
  ```
페이지의 주요 내용이 들어가는 곳입니다.

페이지에서 하나만 존재해야 합니다.
```html
<aside>
  ```
사이드바 등 주요 내용과 간접적으로 연관된 컨텐츠를 포함합니다.
```html
<section>
  ```
페이지의 컨텐츠를 일정 단위의 구획으로 나누는데 사용됩니다.

더 작은 단위의 컨테이너는 div를 사용합니다.
```html
<article>
  ```
페이지 내에서 재사용될 수 있거나 페이지로부터 독립적인,

즉 다른 페이지에서도 사용될 수 있는 컨텐츠에 사용합니다.

기사나 블로그 포스트, 댓글 등에 사용됩니다.

### 가독성을 위한  이름 짓기

****BEM(Block Element Modifier)**

```css
.BLOCK__ELEMENT--MODIFIER { /* ... */ }
```

[https://9elements.com/bem-cheat-sheet/](https://9elements.com/bem-cheat-sheet/)

### 다른 CSS파일 가져오기

@import url(경로)를 통해 가져온다.

→ 장점: 여러 페이지에서 공통적으로 사용되는 스타일을 따로 작성해 가져와 적용하면 수정 관리에 용이하다.

### CSS 변수 사용

```css
/* 모든 요소들에서 사용될 수 있는 변수 */
:root {
--font-small: 8px;
--font-normal: 16px;
--font-large: 24px;
--font-x-large: 32px;
--font-xx-large: 40px;
--font-xxx-large: 48px;
--font-w-normal: 400;
--font-w-bold: 600;
--font-w-extrabold: 900;
--color-main: #FF4200;
--color-sub: #865A55;
--color-text: #49281C;
}
```
var(변수명) 으로 사용가능

### 상속과 리셋

속성을 따로 지정하지 않은 자식은 부모의 속성값을 물려받는다.

[https://developer.mozilla.org/en-US/docs/Web/CSS/Reference#index](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference#index)

→ 상속되는 CSS속성들

**inherit: 스스로의 값을 포기하고 부모로부터 받은 상속값을 적용**

**initial: 브라우저가 부여한 값을 포기하고 각 속성의 초기값을 적용** 

### 웹 폰트

서버에 저장된 서체를 사용자의 컴퓨터에서 사용 가능하도록 함

[https://fonts.google.com/](https://fonts.google.com/)→ 구글 폰트

1. 서버에서 그대로 가져와 사용
2. 폰트를 자체 서버에 탑재하여 사용