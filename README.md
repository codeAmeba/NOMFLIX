# React based movie app with Nomad Coders

## INDEX
<ul>
  <li><a href="#day01">DAY 01</a></li>
  <li><a href="#day02">DAY 02</a></li>
  <li><a href="#day03">DAY 03</a></li>
  <li><a href="#day04">DAY 04</a></li>
  <li><a href="#day05">DAY 05</a></li>
</ul>

***

<h1 id="day01">DAY 01</h1>

## 1.1 Arrow Function

- ES6에서 새롭게 추가된 기능
- ES6 이전 일반적인 형태의 함수에서는 return을 생략하면 undefined가 출력되었지만, 화살표 함수에서는 내부적으로 return을 자동으로 해주기 때문에 생략이 가능하다.
- 단,  `{}`를 사용한다면 return을 명시해줘야 한다.
- parameter가 1개일 경우에는 `()` 생략 가능.
- [화살표 함수 - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/%EC%95%A0%EB%A1%9C%EC%9A%B0_%ED%8E%91%EC%85%98)

```javascript
const beers = ['cass', 'hite', 'terra'];

// ES6 이전
const beerFilter = beers.filter(function(beer) {
  return beer.length > 4;
});
console.log(beerFilter); // [ 'terra' ]

// ES6 이후
const beerFilterVer2 = beers.filter(beer => beer.length < 5);
console.log(beerFilterVer2); // [ 'cass', 'hite' ]
```

## 1.2 Template Literals

- Template Literals는 Template와 변수, 문자열 등을 다루기에 적합한 방법이다.
- 백틱(backtracks)라고 부르는 기호를 활용하며 문자열로 출력하게 한다.
- 인자는 `${}`  이것으로 감싼다.
- [Template literals - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Template_literals)

```javascript
const beerBox = [
  {
    name: 'CASS',
    from: 'KOREA'
  },
  {
    name: 'STELLA',
    from: 'BELGIUM'
  },
  {
    name: 'KIRIN',
    from: 'JAPAN'
  }
];

const favBeer = beerBox.filter(beer => {
  if (beer.from === 'KOREA') {
    return console.log(`I LOVE ${beer.name}`); // <- template literals
  }
});

// I LOVE CASS
```

## 1.3 Object Destructuring

- 우리말로 **구조 분해 할당** 이라고 하며, 동일한 할당 작업을 반복해야 할 때 이를 한 번에 할 수 있게 해줌.
- 비교적 적은 코드가 사용되기 때문에 깔끔하게 보인다는 게 장점
- Object를 기반으로 생성됨.
- [구조 분해 할당 - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)

```javascript
const beer = {
  name: 'CASS',
  from: 'KOREA',
  taste: 'FRESH',
  type: 'LAGER',
  with: {
    morning: 'CUP RA-MYEON',
    afternoon: 'PIZZA',
    evening: 'SAM-GYEOP-SAL'
  }
};

const { name, from, taste, type, with: { afternoon } } = beer;

console.log(`${name} is from ${from}, this is ${taste} ${type}. I love drink with ${afternoon}`);
// CASS is from KOREA, this is FRESH LAGER. I love drink with PIZZA
```

## 1.4 Spread Operator

- 배열이나 객체를 풀어줌(Unpack).
- [전개 구문 - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Spread_syntax)

```javascript
const days = ['Mon', 'Tue', 'Wed'];
const otherDays = ['Thu', 'Fri', 'Sat'];

const allDays = [days, otherDays, 'Sun'];
console.log(allDays); 
// [ [ 'Mon', 'Tue', 'Wed' ], [ 'Thu', 'Fri', 'Sat' ], 'Sun' ]

const allDaysVer2 = [...days, ...otherDays, 'Sun'];
console.log(allDaysVer2); 
// [ 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun' ]
```

## 1.5 Classes 

- 프로그래밍에는 크게 두 종류의 패러다임이 있다
	- 함수형 프로그래밍(Functional Programming)
	- 객체 지향 프로그래밍(OOP, Object Oriented Programming)
- 객체 지향 프로그래밍의 경우 모든 것을 객체나 클래스로 만들고, 부모 자식의 관계가 분명하다.
- Class는 청사진(Blueprint)과 같다고 생각하면 된다.
- 리액트에서 지겹도록 사용하게 됨.
- [Classes - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Classes)

```javascript
class SmartPhone {
  constructor(name, made) {
    this.name = name;
    this.made = made;
  };
};

class Calling extends SmartPhone {
  ringRing() {
    console.log('Hello?');
  };
  intro() {
    console.log(`This phone is ${this.name}`)
  };
};

const myPhone = new SmartPhone('iphone', 'apple');
console.log(myPhone.name); 
// iphone

const yourPhone = new Calling('galaxy', 'samsung');
console.log(yourPhone.ringRing(), yourPhone.intro()); 
// Hello?
// This phone is galaxy
// undefined
```

***

<h1 id="day02">DAY 02</h1>

## 1.6 Array.map

- API로부터 배열로 된 데이터를 받게 되기 때문에 배열 메서드는 중요함
- map 메서드는 해당 배열 요소에 모두 동일한 사항을 매핑하여 새로운 배열을 만들어냄
- [Array.prototype.map() - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

```javascript
const days = ['Mon', 'Tue', 'Wed', 'Thu', 'Fri'];
const drinkDays = days.map(day => `${day}: I'll drink beer`);
console.log(drinkDays);
/*
[
'Mon: I'll drink beer',
'Tue: I'll drink beer',
'Wed: I'll drink beer',
'Thu: I'll drink beer',
'Fri: I'll drink beer'
]
*/
```

## 1.7 Array.filter

- filter 메서드는 주어진 조건을 만족하는 요소만으로 새로운 배열을 만듬
- [Array.prototype.filter() - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

```javascript 
const numbers = [ 3, 4, 7, 32, 31, 5, 64, 12, 24, 87, 66, 59, 243, 356, 645, 210 ];
const biggerThan50 = numbers.filter(num => num > 50);
console.log(biggerThan50);
/*
[
   64,  87,  66,  59, 243, 356, 645, 210
]
*/
```

## 1.8 forEach / includes / push

### forEach
- 새로운 배열을 반환하는 map이나 filter와 다름
- 배열 각각의 요소에 접근하여 조건에 받는 요소를 반환
- 로컬 스토리지에 저장한다던가, API로 보낸다던가, 경고를 보낸다던가 하는 등의 작업에 사용
- [Array.prototype.forEach() - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

```javascript
const beers = ['cass', 'hite', 'terra', 'fitz'];
beers.forEach(beer => console.log(beer));
/*
cass
hite
terra
fitz
*/
```

### push
- 배열에 새로운 요소를 추가할 때 사용함
- [Array.prototype.push() - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/push)

```javascript
const beers = ['cass', 'hite', 'terra', 'fitz'];
beers.push('kloud');

console.log(beers);
// [ 'cass', 'hite', 'terra', 'fitz', 'kloud' ]
```

### includes
- 배열 내에 특정 요소가 존재하는 확인
- [Array.prototype.includes() - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)

```javascript
const cars = ['BMW', 'AUDI', 'VOLVO'];

if(!cars.includes('BENZ')) {
  cars.push('BENZ');
}

console.log(cars);
// [ 'BMW', 'AUDI', 'VOLVO', 'BENZ' ]
```

## 추가) reduce

- reduce는 단순히 배열 내의 요소를 모두 합하여 하나로 만드는 역할만 하는 메서드가 아니다.
- 활용하기에 따라 무궁무진한 가능성이 있다.
- 꾸준히 반복 학습이 필요한 메서드 중 하나.
-  `배열.reduce((누적값,현재값,인덱스,요소)=>{return결과},초기값);`
- [Array.prototype.reduce() - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

***

<h1 id="day03">DAY 03</h1>

## 2.0 Setting up the project

### create-react-app
- yarn 또는 npm을 사용
	- `yarn global add create-react-app`
- 간편하게 react를 시작할 수 있게 해주는 모듈
	- `create-react-app`
- 컴퓨터에 저장하기 때문에 매번 버전 확인 및 업데이트를 해야한다는 번거로움이 있음.

### npx
- 앞의 경우를  보완한 것이 npx를 통한 설치
	-  `yarn global add npx` or `npm i npx -g`
- 이것 또한 모듈이지만, 컴퓨터에 저장할 필요가 없음.
- 항상 최신 버전의 create-react-app을 받아서 실행한 뒤, 끝나면 삭제 됨
	- `npx create-react-app`

### prop-types
- prop-types 모듈 설치 필요
	- `yarn add prop-types`


## 2.1 React router part one

### Screens

- [ ] Home
- [ ] TV Shows
- [ ] Search
- [ ] Detail

### React Router
- [GitHub - ReactTraining/react-router: Declarative routing for React](https://github.com/ReactTraining/react-router)
	- [React Router: Declarative Routing for React.js](https://reacttraining.com/react-router/web/guides/quick-start)
- React App에게 Home에서 시작해야 한다는 걸 알려주기 위한 도구
- React의 Routing 패키지
- DOM과 react-native에도 사용 가능함
- React Router는 컴포넌트 묶음이다.


## 2.2 React router part two

### HashRouter
- url에 해쉬태그가 들어가기 때문에 미관상 보기 좋지 않음
- `http://localhost:3000/#/home`

### BrowserRouter
- 일반적인 웹 페이지의 url
- `http://localhost:3000/home`

### Composition
- 두 개 이상의 Route를 동시에 랜더링 하는 방식
```javascript
export default () => (
  <Router>
    <Route path="/" exact component={Home} />
    <Route path="/tv" component={TV} />
    <Route path="/tv/popular" render={() => <h1>popular</h1>} />
    <Route path="/search" component={Search} />
  </Router>
);
```
<img src="/images/composition.png">


### Redirect
- `<Redirect from=“*” to=“/“ />`
- 해당되는 페이지만 렌더링 되도록 함.
	- But, 경로가 겹치게 되어서 에러가 나는데 그래서 `Switch`를 사용해야 함.

### Switch
- 한 번에 오직 하나의 Route만 랜더링 할 수 있게 함.
```javascript
// Router.js
import React from 'react';
import { BrowserRouter as Router, Route, Redirect, Switch } from 'react-router-dom';
import Home from 'Routes/Home';
import TV from 'Routes/TV';
import Search from 'Routes/Search';

export default () => (
  <Router>
    <Switch> // <- Switch
      <Route path="/" exact component={Home} />
      <Route path="/tv" component={TV} />
      <Route path="/tv/popular" render={() => <h1>popular</h1>} />
      <Route path="/search" component={Search} />
      <Redirect from="*" to="/" /> // <- Redirect
    </Switch>
  </Router>
);
```

### exact
- 주어진 경로와 정확히 동일할 때 설정한 컴포넌트를 보여줌.


### 참고자료
- [react-router :: 1장. 리액트 라우터 사용해보기 | VELOPERT.LOG](https://velopert.com/3417)

***

<h1 id="day04">DAY 04</h1>

## 3.0 CSS in React part One

### 리액트에서 CSS를 적용하는 방법 01

- styles.css 파일을 만들어서 스타일 적용
- CSS를 적용할 요소에 className으로 클래스명 적어야 함
- 최상위 파일(index.js)에 import 
	- `import 'styles.css';`
- 나쁜 방법은 아니나, 컴포넌트와 CSS가 분리되어 있다는 게 단점.
	- 컴포넌트를 쓰는 가장 큰 이유는 캡슐화(Encapulation)에 있다.

<br />

### 리액트에서 CSS를 적용하는 방법 02
- 기능별로 별도 컴포넌트를 생성
- 각 컴포넌트마다 CSS 파일의 생성 및 적용
- 이 방법에도 단점은 있음
	- 첫째, CSS 파일을 생성해야 된다는 점.
	- 둘째, 사용할 때마다 import를 해야 한다는 점.
	- 셋째, className을 기억해야 한다는 점.(CSS는 Global로 작동하기 때문)

<br />

## 3.1 CSS in React part Two

### 리액트에서 CSS를 적용하는 방법 03

- CSS를 컴포넌트 스코프에서 작동하도록 하는 방법.
- CSS 모듈이라고 부름.
- className을 임의화해서 local로 작동하게 함.

**src - Components - Header - Header.module.css**

```css
.navList {
  display: flex;
}
```

- CSS 파일명을 `Header.module.css` 방식으로 변경
- import는 자바스크립트와 같은 방식
	- `import styles from ‘./Header.module.css’;`
- className을 자바스크립트의 객체처럼 사용함.

**src - Components - Header - Header.js**
```javascript
export default () => (
    <header>
      <ul className={styles.navList}> // <- like this
        <li>
          <a href="/a">Home</a>
        </li>
        <li>
          <a href="/tv">TV</a>
        </li>
        <li>
          <a href="/search">Search</a>
        </li>
      </ul>
    </header>
);
```

- class명이 랜덤으로 생성됨.
<img src="/images/random-class.png">

- `yarn add node-sass` 설치 후 아래와 같이 작성할 수도 있음.
```scss
.navList {
  display: flex;
  &:hover {
    background-color: deeppink;
  }
}
```

- 이러한 모듈 방식도 괜찮기는 하지만 className을 기억해야 한다는 점이 마음에 들지 않음.
- 여전히 JS와 CSS가 동떨어져 있다는 느낌을 지울 수가 없다. 둘을 하나의 파일에서 쓸 수 있는 방법은 없을까?

<br/>

## 3.2 CSS in React part Three

### 리액트에서 CSS를 적용하는 방법 04
- JS를 이용한 니코의 최애 방법은 **styled-components**
- 우선 설치가 필요함
	- `yarn add styled-components`
- 설치 후 import
	- `import styled from 'styled-components'`

> TIP) 
> **vscode-styled-components** 확장 프로그램을 설치하면 텍스트에 색상이 들어감.

- styled-component 작성 후 아래와 같이 태그로 사용
	- **src - Components - Header.js**
```javascript
import React from 'react';
import styled from 'styled-components';

const List = styled.ul`
  display: flex;
  &:hover {
    background-color: deeppink;
  }
`;

export default () => (
    <header>
      <List> // <- here
        <li>
          <a href="/">Home</a>
        </li>
        <li>
          <a href="/tv">TV</a>
        </li>
        <li>
          <a href="/search">Search</a>
        </li>
      </List> // <- here
    </header>
);
```

<br/>

### Link

- `<a></a>`태그를 사용하면 링크로 이동할 때마다 뷰를 다시 렌더링 하는데, 굉장히 비효율적이다.
- 따라서, React에서는 `Link`라는 기능을 사용함.
  - `import { Link } from 'react-router-dom';`
  - 동일한 페이지에 있을 경우 해당 요소만 교체하는 방식
- 이 경우에는 아래와 같이 styled-components를 적용
  - `const SLink = styled(Link)``;`
- Link는 Router 밖에서 사용할 수 없으므로 아래와 같은 형식의 문장 구조를 이룸

```javascript
export default () => (
  <Router>
    <>
      <Header /> // <- here
      <Switch>
        <Route path="/" exact component={Home} />
        <Route path="/tv" exact component={TV} />
        <Route path="/tv/popular" render={() => <h1>popular</h1>} />
        <Route path="/search" component={Search} />
        <Redirect from*="*" to="/" />
      </Switch>
    </>
  </Router>
);
```

<br/>

## 3.3 GlobalStyles and Header

### Global style 적용

- 글로벌로 설정하는 이유는 해당 사이트의 폰트를 설정하거나, styled-components를 설치하거나 하는 등의 작업 때문.
- 우선 `yarn add styled-reset`
- [GitHub - zacanger/styled-reset: Eric Meyer’s Reset CSS for styled-components](https://github.com/zacanger/styled-reset)
- styled-reset은 SC를 이용하여 CSS초기화 한 뒤 0의 상태에서 시작할 수 있게 해줌.
- GlobalStyles.js 파일 생성

**src - Components - GlobalStyles.js**

```javascript
import { createGlobalStyle } from 'styled-components';
import reset from 'styled-reset';

const globalStyles = createGlobalStyle`
  ${reset};
  a {
    text-decoration: none;
    color: inherit;
  }
  * {
    box-sizing: border-box;
  }
  body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    font-size: 14px;
    background-color: rgba(20, 20, 20, 1);
  }
`;

export default globalStyles;
```

**src - Components - App.js**

```javascript
import React, { Component } from 'react';
import Router from 'Components/Router';
import GlobalStyles from './GlobalStyles';

class App extends Component {
  render() {
    return (
      <>
        <Router />
        <GlobalStyles />
      </>
    );
  }
}

export default App;
```

<br />

## 3.4 Location Aware Header

- 선택된 Header의 border에만 컬러링
- 해당 요소에 props를 줌

```javascript
const Item = styled.li`
  width: 50px;
  height: 50px;
  text-align: center;
  border-bottom: 5px solid ${props => props.current ? 'deeppink' : 'transparent'};
`;
```

- props로 현재 선택된 Header의 Router를 전달해야 함
	- 이때 `withRouter`을 사용. 이것은 컴포넌트를 감싸는 또 다른 컴포넌트의 개념.
	- Router에 대한 정보를 줌.
	- `import { Link, withRouter } from ‘react-router-dom’;`
	- 아래와 같은 형식으로 withRouter로 기존의 컴포넌트를 감싼다.

```javascript
const HeaderC = (props) => (
    <Header>
      {console.log(props)}
      <List>
        <Item current={false}>
          <SLink to="/">Movies</SLink>
        </Item>
        <Item current={true}>
          <SLink to="/tv">TV</SLink>
        </Item>
        <Item current={false}>
          <SLink to="/search">Search</SLink>
        </Item>
      </List>
    </Header>
);

export default withRouter(HeaderC);
```

- 위와 동일한 내용을 다른 형식으로 작성

```javascript
export default withRouter(props => (
    <Header>
      {console.log(props)}
      <List>
        <Item current={false}>
          <SLink to="/">Movies</SLink>
        </Item>
        <Item current={true}>
          <SLink to="/tv">TV</SLink>
        </Item>
        <Item current={false}>
          <SLink to="/search">Search</SLink>
        </Item>
      </List>
    </Header>
));
```

- console.log를 찍어보면 아래와 같이 props를 얻을 수 있음.

<img src="/images/withRouter-props.png">

- 여기서 필요한 것은 pathname
  - `{ location: { pathname } }`

- 최종적으로 아래와 같이 pathname의 확인 결과가 boolean으로 나올 수 있도록 작성하면 선택한 요소에만 border 색상이 들어감.

```javascript
export default withRouter(({ location: { pathname } }) => (
    <Header>
      <List>
        <Item current={pathname === ‘/‘}>
          <SLink to='/'>Movies</SLink>
        </Item>
        <Item current={pathname === ‘/tv’}>
          <SLink to='/tv'>TV</SLink>
        </Item>
        <Item current={pathname === ‘/search’}>
          <SLink to='/search'>Search</SLink>
        </Item>
      </List>
    </Header>
));
```
***

<h1 id="day05">DAY 05</h1>

## 4.0 Introduction to The Movie DB API

- 데이터가 오는 곳이 API(Application Programming Interface)
- Nomflix에서는 the movie db를 이용함(가입 필요).
  - [https://www.themoviedb.org/](https://www.themoviedb.org/) 
- setting -> API -> API KEY copy

<br />

## 4.1 Sexy Networking with Axios Instances


### API Verbs

- [x] Now playing (Movie)
- [x] Upcoming (Movie)
- [x] Top Rated (TV)
- [x] Popular (TV, X)
- [x] Airing Today (TV)


<br />

### 요청 방식

- 이전 강의들에서는 주로 fetch를 썼음
	- 라우터에서 호출하고, fetch 하고, 나머지 모든 작업들을 하는 방식인데 효율적이지 않음.
	- 왜냐하면 url의 동일한 내용이 반복되기 때문
	- 따라서 네트워킹과 API만 다루는 별도의 파일을 따로 만들고 호출할 것
	- 또한, fetch가 아닌, axios를 사용

<br />

### Axios

- [GitHub - axios/axios: Promise based HTTP client for the browser and node.js](https://github.com/axios/axios)
- 별도 모듈 설치 필요
	- `yarn add axios`
- axios의 장점은, 직접 인스턴스를 configure(설정)할 수 있다는 점.

**axios.create([config])**

```javascript
const instance = axios.create({
  baseURL: 'https://some-domain.com/api/',
  timeout: 1000,
  headers: {'X-Custom-Header': 'foobar'}
});
```

- 위의 axios.create를 통해 반복을 최소화 할 수 있음.
  - parameter에 api_key와 language 전달

```javascript
import axios from 'axios';

const api = axios.create({
  baseURL: 'https://api.themoviedb.org/3/',
  params: {
    api_key: 'b8e07a1bc39775b44d7ad690b461e764',
    language: 'en-US'
  }
});

api.get('tv/popular');

export default api;
```

- index.js에 api.js를 import하고 실행해보면 아래와 같이 데이터가 들어오는 것을 확인할 수 있음.
- 주의) api.get에서 `tv/popular`로 작성해야 상대경로로 접근함
  - `/tv/popular`로 작성하면 절대경로가 됨

<img src="/images/api-response.png">
<img src="/images/api-response2.png">

<br />

## 4.2 API Verbs part One

### API Verbs

- [x] Now playing (Movie)
- [x] Upcoming (Movie)
- [x] Top Rated (TV)
- [x] Popular (TV, X)
- [x] Airing Today (TV)
- [ ] TV Show Detail
- [ ] Movie Detail

- TV와 Movies 각각의 api 요청

```javascript
import axios from 'axios';

const api = axios.create({
  baseURL: 'https://api.themoviedb.org/3/',
  params: {
    api_key: 'b8e07a1bc39775b44d7ad690b461e764',
    language: 'en-US'
  }
});

export const MoviesApi = {
  nowPlaying: () => api.get('movie/now_playing'),
  upcoming: () => api.get('movie/upcoming'),
  popluar: () => api.get('movie/popular')
}

export const TvApi = {
  topRated: () => api.get('tv/top_rated'),
  popular: () => api.get('tv/popular'),
  airingToday: () => api.get('tv/airing_today')
}
```

- fetch 방식의 api 요청에 비해 훨씬 간결하고 가독성이 좋음.
- axios 짱짱맨

<br/>

## 4.3 API Verbs part Two
***
- Movie Detail을 가져오기 위해 id가 필요함
	- `movie/{movie_id}`

<br/>

### API Verbs
- [x] Now playing (Movie)
- [x] Upcoming (Movie)
- [x] Top Rated (TV)
- [x] Popular (TV, X)
- [x] Airing Today (TV)
- [x] TV Show Detail
- [x] Movie Detail
- [x] Search  (Movie, TV)

<br/>

### append_to_response

- api에서 지원하는 기능
- [API Docs](https://developers.themoviedb.org/3/getting-started/append-to-response)
- video나 image같은 것들을 덧붙이기(append)하면 포스터나 예고편 등으로 출력이 된다.

```javascript
export const MoviesApi = {
  nowPlaying: () => api.get('movie/now_playing'),
  upcoming: () => api.get('movie/upcoming'),
  popluar: () => api.get('movie/popular'),
  movieDetail: id => api.get(`movie/${id}`, {
    params: {
      appent_to_response: 'videos'
    }
  })
};
```

### Search
- search 기능은 url 외에도 검색어에 해당하는 파라미터가 추가로 필요함

<img src="api-search.png">

```javascript
  search: (term) => api.get('search/movie', {
    params: {
      query: term
    }
  })
```

- 그리고 api의 명세를 잘 찾아보면 아래와 같이 요구사항이 설명되어 있음.
- 이 경우에는 URI로 인코딩이 필요하다고 함.

<img src="api-search2.png">

- 따라서 아래와 같이 encodeURIComponent를 사용하면 값을 인코팅하고 그 문자열로 검색을 하게 됨.
```javascript
  search: (term) => api.get('search/movie', {
    params: {
      query: encodeURIComponent(term)
    }
  })
```

***


<h1 id="day06">DAY 06</h1>

## 5.0 Container Presenter Pattern part One

- Container Presenter Pattern에서 컨테이너는 data와 state를 지니고, api를 불러온다. 그리고 모든 로직을 처리.
- 그 다음, 프레젠터가 그 data들을 보여주는 역할.(프레젠터에는 state가 없고, api도 모르며 클래스도 없고 단지 함수형 컴포넌트)
- 쉽게 말해서 프레젠터는 ‘스타일’, 컨테이너는 ‘데이터’

<br />

### 각 컨테이너별 폴더를 따로 구성

- 폴더마다 index.js가 있어야 함. 컨테이너를 export해야 하기 때문.
- 이렇게 정리하는 게 혼란을 줄일 수 있음.
- index.js가 HomeContainer를 import / export하는 역할을 하고
- HomeContainer는 state를 가진 모든 리액트 컴포넌트가 된다.

**src - Routes - Home - HomeContainer.js**
```javascript
import React from 'react';
import HomePresenter from './HomePresenter';

export default class extends React.Component {
  state = {
    nowPlaying: null,
    upcoming: null,
    popular: null,
    error: null,
    loading: true
  };

  render() {
    const { nowPlaying, upcoming, popular, error, loading } = this.state;
    return (
      <HomePresenter 
        nowPlaying={nowPlaying} 
        upcoming={upcoming} 
        popular={popular} 
        error={error}
        loading={loading}
      />
    );
  }
}
```

<br />

## 5.1 Container Presenter Pattern part Two

- search container는 **상호작용**이 필요하기 때문에 조금 까다로움
- loading의 경우 기본값은 false
  - 유저가 아무런 행동을 취하지 않았는데 로딩이 되면 안 되니까

```javascript
import React from 'react';
import SearchPresenter from './SearchPresenter';

export default class extends React.Component {
  state = {
    MovieResults: null,
    TvResults: null,
    SearchTerm: '',
    error: null,
    loading: false
  }

  render() {
    const { MovieResults, TvResults, SearchTerm, error, loading } = this.state;
    return (
      <SearchPresenter 
        MovieResults={MovieResults}
        TvResults={TvResults}
        SearchTerm={SearchTerm}
        error={error}
        loading={loading}
      />
    );
  }
}
```

<br />

## 5.2 Home Container

- 두 가지 옵션이 있음
	- componentDidMount()를 통해 전체 api 요청을 할 수 있고
	- 각각의 요청을 분리된 함수로 따로 요청할 수도 있음.
		- ex) getNowPlaying(), getUpComing() 등등

- 이번 경우엔 굳이 분리할 필요가 없으므로 componentDidMount()를 사용함

<br />

### try - catch

- try가 먼저 실행되고, 작동하지 않으면 error를 catch 한다.

<br />

### async / await

- 준비가 될 때까지 기다려달라는 의미
- 예를 들어 아래와 같은 상황에서 async/await이 없으면, nowPlaying 데이터를 가져오기 시작한다. 하지만 api가 리턴할 때까지 자바스크립트는 기다려주지 않음.

```javascript
  async componentDidMount() {
    try {
      await MoviesApi.nowPlaying();
    } catch {
      this.setState({
        error: "Can't find movis information."
      });
    } finally {
      this.setState({
        loading: false
      });
    }
  }
```

- 하지만, async/await을 쓰면 데이터가 준비될 때까지 자바스크립트가 기다려줌.

<br />

### 비구조화 할당

- 변수명에 data를 정할 때 비구조화 할당을 쓰면 보기 좋음

```javascript
  async componentDidMount() {
    try {
      const { data: { results: nowPlaying }} = *await* MoviesApi.nowPlaying();
      console.log(nowPlaying);
    } catch {
      this.setState({
        error: "Aw, Snap!"
      });
    } finally {
      this.setState({
        loading: false
      });
    }
  }
```

<br />

## 5.3 TV Container

- Movies와 동일

<br />

## 5.4 Search Container

- 모든 로직을 갖는다.
- 첫 번째 로직은 handleSubmit
	- 입력 폼에 text를 입력한 뒤 엔터키를 누르면 Submit이 됨
	- searchTerm이 공백이 아닌지 체크하고 search 함수를 실행할 것
- 특히 try는 다른 컨테이너와 다름
	- 검색을 시도했을 때 로딩을 true로 만든다(기본값은 false).

```javascript
  handleSubmit = () => {
    const { searchTerm } = this.state;
    if (searchTerm !== '') {
      this.searchByTerm();
    }
  };

  searchByTerm = async() => {
    const { searchTerm } = this.state;
    try {
      const { data: { results: movieResults }} = await MoviesApi.search(searchTerm);
      const { data: { results: tvResults }} = await TvApi.search(searchTerm);
      this.setState({
        movieResults,
        tvResults
      })
      this.setState({
        loading: true
      })
    } catch {
      this.setState({
        error: "Can't find results."
      });
    } finally {
      this.setState({
        loading: false
      });
    }
  };
```

<br />

## 5.5 Detail Container part One

- Router Component에 Detail을 추가해야 함.
- Movie나 TV의 id를 가져와서 보여주는 방식

```javascript
export default () => (
  <Router>
    <>
      <Header />
      <Switch>
        <Route path="/" exact component={Home} />
        <Route path="/tv" component={TV} />
        <Route path="/search" component={Search} />
        <Route path="/movie/:id" component={Detail} />
        <Route path="/tv/:id" component={Detail} />
        <Redirect from="*" to="/" />
      </Switch>
    </>
  </Router>
);
```

- `:id`는 해당 위치는 랜덤한 id가 올 수 있음을 의미
- id는 url에서 가져올 예정
- Header component는 라우터의 위치를 알고 있음.
	- withRouter로 감쌌기 때문에


<br />

## 5.6 Detail Container part Two

