# Master React16

Nomad Academy course to master all the new features of React 16

## 2 Return Types Strings and Fragments

```
class ReturnTypes extends Component {
  render() {
    return (
      <Fragment> or <>
        <header></header>
        <div></div>
        <footer></footer>
      </Fragment> or </>
    );
  }
}

- react 16 부터는 컴포넌트를 return할때 array나 span으로 감싸지 않고 Fragment로 감싸거나 <></>로 감싸서 한번에 2개 이상의 컴포넌트를 리턴해줄 수 있게 됨.
- 또한 return String 이 가능함.
```

## 3 Portals

- index.html에서 보면 알다싶이 ReactJS는 하나의 div를 찾아서 마운트를 해줌.
- Portals는 index.html에 있는 `<div id="root"></div>`이란 React root 밖에 리액트를 넣을 수 있도록 해줌
- Portals는 리액트가 아니라 리액트 돔 안에 있음.

- Portals 사용법
  1. index.html에 `<div id="root"></div>` 의 밖에 컴포넌트를 만들고 id값을 준다.
  2. App.js에서 `document.getElementById("touchme")` 로 리액트 밖에 만들어 뒀던 컴포넌트의 id값을 가져온다.

```
import React, { Component, Fragment } from "react";
import { createPortal } from "react-dom";

class Portals extends Component {
  render() {
    return createPortal(<Message />, document.getElementById("touchme"));
  }
}

const Message = () => "Just Touch This!";

class ReturnTypes extends Component {
  render() {
    return "안녕, 씨발럼아";
  }
}

class App extends Component {
  render() {
    return (
      <Fragment>
        <ReturnTypes />
        <Portals />
      </Fragment>
    );
  }
}

export default App;
```

<b>리액트 루트 밖에서 렌더를 할 때 사용할 수 있는 것. 그래서 포털이라고 불리는 것.</b>

## 4 Error Boundaries

- 컴포넌트로 하여금 컴포넌트 칠드런의 에러를 관리할 수 있게 해주는 것.
- App의 경우에서 보면은 ReturnTypes나 Portals에서 에러가 발생하면 App에서 관리를 할 수 있음
- 중요한건 이게 정상 작동할 때는 칠드런의 에러에만 한정이다.

- 에러가 발생한 부분만 따로 구분하고 관리할 수 있다는 개념인듯.

- componentDidCatch 사용한 것. 이 강의에서는 개념만 알려줌. 나중에 이거에대해 알고싶다면 해당 강의를 한번 더 보는게 나을듯 함.

- 지금 작성된 App.js 파일처럼 작성해도 되긴 하지만 모든 컴포넌트마다 이렇게 작성해 줄 수는 없기 때문에 다음 강의에서 더 멋진 방법 소개함.

## 5 Error Boundaries with Higher Order Components

- 4 강에서처럼 에러가 발생할 컴포넌트마다 하나씩 작업해주고 싶지 않음.
- 그래서 higher-order component를 만듦 -> HOC

- HOC를 통해 내가 원하는 모든 컴포넌트를 보호할 수 있음.

- 해당 영상 강의 나중에 다시 참고하셈.

## 6 this setStatenull

- 컴포넌트의 업데이트 프로세스 조절하는 것?

- setState를 하면 컴포넌트는 업데이트를 함. 근데 이걸 컨트롤 할 수 있다면?
- 언제 컴포넌트를 업데이트 할지, 안할지 결정 할 수 있음
  -> 이게 set state null 이 제공하는 기능임!!
