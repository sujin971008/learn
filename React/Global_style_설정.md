# GlobalStyle이란?
styled components에서 각 componet에 동일한 스타일을 부여하고 싶을 때 겹치는 부분만 따로 떼어서 하나의 component로 작성하고 그 컨포넌트 안에 있는 스타일을 적용하고 싶은 부분에 import 하면 해당 component 전역에 그 스타일이 부여된다.
(라우터를 설정해주는 부분에서 GlobalStyle을 불러와 적용 )

## Step1 -- 패키지설치 
yarn add  styled-components
또는 npm install styled-components

## Step2
styled-components는 따로 동작하기 때문에 Global.js 파일을 생성해서 관리한다.
### src/styles/GlobalStyle.js
```js
import { createGlobalStyle } from 'styled-components';

const GlobalStyle = createGlobalStyle`
* {
font-family: 'Noto Sans KR';
}

body {
padding: 0;
margin: 0;
}
`; 

export default GlobalStyle;
```
### App.js
```js
import React from "react";
import Header from "./component/header";
import Section from "./pages/section";
import Footer from "./component/footer";
import Meta from "./Meta";
import styled from 'styled-components';
import GlobalStyles from './components/GlobalStyle';


const App = () => {
  return (
   <div>
      <Meta />
      //<GlobalStyles/> --> 이렇게도 적용 가능
    <GlobalStyles>
      <Header />
      <Section />
      <Footer />
    </GlobalStyles>
    </div>
  );
};

export default App;

```
