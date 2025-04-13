# 202130230 지영준. 

### 4월 10일 강의내용

## props를 통해 데이터 전달하기
1. React의 component architecture를 사용해서 재사용할 수 있는 component를 만들어서 지저분하고 중복된 코드를 삭제합니다.  
    * Board component를 만들고, Square component의 내용을 복사합니다.
    * Square component의 button을 하나만 남기고 모두 삭제합니다.
    * Board component의 button을 Square component로 교체합니다.
    * App에서 호출하는 component를 Square에서 Board로 바꿔줍니다.
    * 정상적으로 출력이 되는지 확인해 보세요.
    * 여기까지 하면 component는 깔끔하게 정리 됐지만, 숫자 출력이 1만 나오게 됩니다.
    * 이 문제를 해결하기 위해 props를 사용하여 각 사각형이 가져야 할 값을 부모
    component (Board)에서 자식 component (Square)로 전달하겠습니다.
    * component를 호출하는 쪽이 부모 component입니다.  

<hr>


* Square component를 value prop을 전달 받을 수 있도록 수정합니다.  
``` jsx 
function Square({ value })
}
return <button className="square">1</but ton>;
```  
* 이렇게 수정한다고 해서 변하는 것은 없습니다. 왜냐하면 return값은 1이 전달되기 때 문입니다.
* 문서처럼 value를 문자열로 1과 교체해도 마찬가지 입니다.
* 문자열 "vaLue"가 아닌 Javascript 변수가 렌더링 되어야 합니다.
* JSX에서 "Javascript로 탈출" 하려면, 중괄호가 필요합니다. JSX에서 value 주위에 중 괄호를 추가합니다
``` jsx 
function Stuarelf
value }
{
return <button className="square" > value }</button>;
``` 
하지만 Board로 부터 value prop이 전달되지 않았기 때문에 않아 아무 것도 표시되지 않습니다.  

<hr>

### 사용자와 상호작용하는 컴포넌트 만들기
  *  다음으로 사각형 컴포넌트가 클릭 된 것을 "기억"하고 "X" 표시로 채워보겠습니다.
  * 컴포넌트는 무언가 "기억"하기 위해 state를 사용합니다.
  * React는 상태 기억을 위해 usestate라는 Hook을 제공합니다.
  * Square의 현재 값을 state에 저장하고 Square가 클릭하면 값이 변경되도록 하겠습니다.
1. 파일 상단에서 usestate를 import합니다.
2. Square 컴포넌트에서 value prop을 제거합니다. 대신 usestate를 사용합니다.
3. Square 컴포넌트의 시작 부분에 usestate를 호출하고, value라는 이름의 state 변수를 반환하도록 하세요.
``` jsx
import { useState ] from ' react';

function Square() {
const [value, setValue] = useState(null);

function handleclick() {
//..
```  

* 이제 Square가 클릭 되었을 때 X*를 표시하도록 변경하겠습니다.
5. console. 10g("cLicked!"); 이벤트 핸들러를 setValue('X');로 변경하세요.
``` jsx
function Square() {
const [value, setValue] = useState(null);
I
function handleClick() {
setValue('X') ;
}
``` 

* oncLick 핸들러에서 set 함수를 호출해서 button 이클릭 될 때마다 Square를 다시 렌 더링하도록 했습니다.
* 업데이트 후 Square의 value는 'X'가 되므로, 앞으로 Board에서 "X"를 볼 수 있습니다.
* Square를 클릭하면 X"가 표시됩니다

### React Developer Tools
1. React 개발자 도구를 사용하면 React 컴포넌트의 props와 state를 확인할 수 있습니다.
2. CodeSandBox의 브라우저 구역 하단에서 React 개발자 도구 탭을 찾을 수 있습니다.
? 찾을 수가 없음. ㅠㅠ
* React 개발자 도구는 Chrome, Firefox, 그리고 Edge 브라우저의 확장 프로그램으로 사 용할 수 있습니다.
  * chrome 웹 스토어에서 React Developer Tools을 설치 합니다.

# 게임 완료하기

이 문서는 리액트(React)를 활용한 간단한 게임(예: 틱택토)을 완성하는 데 필요한 주요 개념들을 다룹니다. 총 4단계로 구성되어 있으며, 각 단계는 게임의 핵심 기능 구현과 관련된 중요한 개념을 포함합니다.

---

## 1. State 끌어올리기 (Lifting State Up)
React에서 여러 컴포넌트가 동일한 데이터를 필요로 할 때, 데이터를 공통 부모 컴포넌트로 끌어올려(state를 상위 컴포넌트로 이동) 상태를 공유하도록 합니다.

### 예시
- `Square` 컴포넌트에서 직접 상태를 관리하는 대신, `Board` 컴포넌트로 상태를 끌어올려 모든 `Square`가 같은 소스로부터 데이터를 받도록 합니다.
- 이렇게 하면 `Square` 간의 상태 동기화가 쉬워지고, 게임의 흐름 제어가 중앙화됩니다.

---

## 2. 불변성이 왜 중요할까요? (Why Immutability Matters)

React에서 상태를 직접 수정하는 대신 새로운 객체로 상태를 업데이트해야 합니다. 이를 **불변성(immutability)** 이라고 합니다.

### 이점
- **변경 감지**: 불변 객체는 이전 상태와 쉽게 비교할 수 있어 React가 효율적으로 렌더링을 결정할 수 있습니다.
- **Undo/Redo 구현이 쉬움**: 이전 상태를 보존할 수 있기 때문에 히스토리를 관리하기에 적합합니다.
- **디버깅 용이**: 상태 추적이 쉬워 버그를 찾기 쉽습니다.

---

## 3. 순서 정하기 (Sorting Moves)

게임 진행 시 각 턴의 히스토리를 저장하고, 이를 사용자가 오름차순 또는 내림차순으로 정렬해 볼 수 있도록 합니다.

### 구현 방법
- 각 턴을 배열로 저장합니다. 예: `history = [{squares: [...]}, ...]`
- 정렬 버튼을 추가하여 사용자가 턴 목록의 순서를 바꿀 수 있게 합니다.
- 현재 선택된 턴을 강조 표시하여 UX를 향상시킵니다.

---

## 4. 승자 결정하기 (Declaring a Winner)

게임의 상태를 확인하여 승자를 판단하는 로직을 구현합니다.

### 로직 예시 (틱택토 기준)
- 가능한 모든 승리 조건을 배열로 정의합니다.
- 현재 게임판 상태에서 이 조건을 만족하는지를 검사합니다.
- 승자가 결정되면 이를 화면에 표시하고, 더 이상 클릭 이벤트가 발생하지 않도록 처리합니다.

```js
function calculateWinner(squares) {
  const lines = [
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8],
    [0, 3, 6],
    [1, 4, 7],
    [2, 5, 8],
    [0, 4, 8],
    [2, 4, 6],
  ];
  for (let [a, b, c] of lines) {
    if (squares[a] && squares[a] === squares[b] && squares[a] === squares[c]) {
      return squares[a];
    }
  }
  return null;
}
```
### 4월 3일 강의내용  
## 이벤트에 응답하기
1. component 내부에 event handler 함수를 선언하면 event에 응답할 수 있습니다.
2. 0nClick={handleClick의 끝에 소괄호()가 없는 것을 주목하세요!
3. 함수를 호출하지 않고 전달만 하면 됩니다.
4. React는 사용자가 버튼을 클릭할 때 이벤트 핸들러를 호출 합니다.
```jsx
/*ㅇ
* onclick event
*/
function MyButton {
  function handleClick {
    alert('You clicked me!');

｝
return (
    <button onClick=thandle(lick)>
          I'm a button </button>
)
}
```
앞에서 실습한 MyButton component를 수정하고, 정상 출력되는지 확인해 봅니다.
MyButton component를 App.js에서 분리하지 않았다면 App.js에서 수정해도 됩니다.
<hr>

## 화면 업데이트하기
1. component가 특정 정보를 기억해 두었다가 표시하기를 원하는 경우가 있습니다.
2. 예를 들어 버튼이 클릭된 횟수를 세고 싶을 수 있습니다.
3. 이렇게 하려면 component에 state를 추가하면 됩니다.  
```jsx 
import { useState } from 'react';
```  
1. 먼저, React에서 usestate를 import합니다.
2. 이 코드를 보면 usestate는 react 파일 안에 Named Exports로 선언되어 있는 여러 개의 component 중 하나는 것을 알 수 있습니다.
3. 이제 component 내부에 state 변수를 선언할 수 있습니다.  
```jsx 
function MyButton) {
const [count, setCountl = usestate(o);
```  
<hr>  

## 화면 업데이트하기  

1. usestate로부터 현재의 state를 저장할 수 있는 변수인 count와 이를 업데이트할 수 있 는 함수인 setcount를 얻을 수 있습니다.
2. 이름은 자유롭게 지정할 수 있지만 [something, setSomething]으로 작성하는 것이 일반 적입니다.
3. 즉, 변수 이름과 변수 이름 앞에 set을 붙인 업데이트 함수를 관용적으로 사용합니다.  
<hr>

``` jsx 
function Button() {
const [count, setCount] = useState(0);
function handleClickO {
setCount (count + 1);

return (
<button onClick=(handleClick}>
Clicked {count) times </button>
)
}
```  
1. 버튼이 처음 표시될 때는 usestate()에 0을 전달했기 때문에 count가 0이 됩니다.
2. state를 변경하고 싶다면 setCount()를 실행하고 새 값을 전달하세요.
3. 이 버튼을 클릭하면 카운터가 증가합니다.  
## Hook 사용하기
1. use로 시작하는 함수를 Hook이라고 합니다.
2. usestate는 React에서 제공하는 내장 Hook입니다.
3. 다른 내정 Hook은 API 참고서에서 찾아볼 수 있습니다.
4. 또한 기존의 것들을 조합하여 자신만의 Hook을 작성할 수도 있습니다. 사용자 Hook.
    1.  Hook은 다른 함수보다 더 제한적입니다.
  예를 들면 ...
    2. component 또는 다른 Hook의 상단에서만 Hook을 호출할 수 있습니다.
    3. 조건이나 반복문에서 usestate를 사용하고 싶다면 새 컴포넌트를 추출하여 그곳에 넣으 세요.
<hr>

## Hooks의 사용 규칙(Rules of Hooks)
Hook은 React의 렌더링 및 상태 관리 메커니즘과 밀접하게 연결되어 있으며, 아래와 같은 규칙을 따라야 합니다.  
1. 최상위에서만 호출해야 한다  
* if, for, while 등의 블록 내부에서 Hooks를 호출하면 안 됩니다.
* 함수의 조건문 내부에서 호출하면 실행 순서가 달라질 수 있기 때문입니다.
<hr>

## 왜 이런 제한이 필요한가?
: React의 동작을 예측 가능하고, 안정성을 높이기 위해 필요한 규칙입니다.
1. rendering 순서를 보장하기 위해
    * 조건문이나 반복문 안에서 Hooks를 사용하면 매 rendering마다 Hook의 호출 순서가 달 라질 수 있기 때문에 React가 상태를 제대로 추적할 수 없습니다.
2. 불필요한 사이드 이펙트 방지
    * component가 여러 번 rendering될 때마다 동일한 순서로 Hook이 실행되어야 React가 의도한 동작을 수행할 수 있습니다.  

## 왜 function형 컴포넌트에서만 Hook을 사용할까?
* Class형 component는 lifecycLe 함수를 통해서 상태 관리를 했습니다.
* 그런 이유 때문에 Class형 component는 유지보수가 어렵고 복잡해질 수 있었습니다.
* React는 component의 상태 관리(lifecycle)와 로직을 더 간결하게 만들기 위해 Hooks를 도입 하게 됩니다.
* 따라서 React 팀은 function형 component를 권장하고 있습니다.
* Hook은 function형 component 전용으로 설계되었습니다.
#### 이런 이유 때문에 function형 component에서만 Hook을 사용하는 것입니다. 
<hr>  



### 3월 27일 강의내용  
## 개요

React.js는 Facebook에서 개발한 오픈 소스 자바스크립트 라이브러리로, 사용자 인터페이스(UI)를 구축하는 데 사용됩니다. React는 빠르고 유연하며 확장성이 뛰어난 라이브러리로, 컴포넌트 기반 아키텍처를 통해 재사용성이 높은 코드를 작성할 수 있습니다.

React는 다음과 같은 특징을 가집니다:

컴포넌트 기반 아키텍처: UI를 독립적이고 재사용 가능한 컴포넌트로 분리하여 관리합니다.

가상 DOM (Virtual DOM): 실제 DOM을 직접 조작하는 대신, 가상 DOM을 사용하여 성능을 최적화합니다.

단방향 데이터 흐름 (One-Way Data Flow): 데이터가 부모에서 자식으로 흐르도록 설계되어 관리가 용이합니다.

JSX (JavaScript XML): HTML과 유사한 문법을 통해 UI를 선언적으로 작성할 수 있습니다.

상태 관리 (State Management): 상태(state)를 통해 UI를 동적으로 업데이트할 수 있습니다.

React Hooks 지원: 함수형 컴포넌트에서 상태와 라이프사이클을 관리할 수 있도록 지원합니다.

라우팅 및 데이터 페칭: React Router, Fetch API, Axios, SWR 등을 활용한 네트워크 요청이 가능함.

성능 최적화 기능: 코드 스플리팅(Code Splitting), 지연 로딩(Lazy Loading) 등의 최적화 기법이 존재함.

## 주요 기능

1.컴포넌트 생성 및 중첩 방법

React에서는 **컴포넌트(Component)**를 사용하여 UI를 구성합니다. 컴포넌트는 다른 컴포넌트를 포함할 수 있으며, 이를 통해 계층적인 구조를 만들 수 있습니다.

예제 (컴포넌트 생성 및 중첩)
```jsx
function Header() {
  return <h1>Welcome to My Website</h1>;
}

function Main() {
  return (
    <div>
      <Header />
      <p>This is the main content of the website.</p>
    </div>
  );
}
```
2.마크업과 스타일 추가 방법

JSX를 사용하여 HTML과 유사한 문법으로 마크업을 작성할 수 있으며, 인라인 스타일, CSS 파일, CSS 모듈, Styled Components 등을 활용하여 스타일을 적용할 수 있습니다.

예제 (인라인 스타일 적용)
```jsx
function StyledComponent() {
  const style = {
    color: "blue",
    fontSize: "20px",
  };
  return <p style={style}>This text is styled with inline styles.</p>;
}
```
예제 (CSS 파일 적용)
```jsx
/* styles.css */
.text {
  color: red;
  font-size: 18px;
}

import "./styles.css";

function StyledComponent() {
  return <p className="text">This text is styled with CSS.</p>;
}
```
3.데이터를 표시하는 방법

React에서 데이터를 표시하는 가장 기본적인 방법은 props와 state를 활용하는 것입니다.

예제 (props를 사용한 데이터 표시)
```jsx
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

function App() {
  return <Greeting name="Alice" />;
}
```
4.조건부 렌더링과 목록 렌더링 방법

조건부 렌더링 (if문 및 삼항 연산자 사용)
```jsx
function UserStatus({ isLoggedIn }) {
  return isLoggedIn ? <p>Welcome back!</p> : <p>Please sign in.</p>;
}
```
목록 렌더링 (map 함수 사용)
```jsx
function ItemList({ items }) {
  return (
    <ul>
      {items.map((item, index) => (
        <li key={index}>{item}</li>
      ))}
    </ul>
  );
}
```
5.이벤트에 응답하고 화면을 업데이트하는 방법

React에서는 onClick, onChange 등의 이벤트 핸들러를 통해 사용자 입력을 처리할 수 있습니다.

예제 (버튼 클릭 이벤트 처리)
```jsx
function ClickCounter() {
  const [count, setCount] = React.useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increase</button>
    </div>
  );
}
```
6. 컴포넌트 간에 데이터를 공유하는 방법

React에서는 props, Context API, Redux, Recoil 등을 사용하여 컴포넌트 간 데이터를 공유할 수 있습니다.

예제 (props를 사용한 데이터 전달)
```jsx
function Child({ message }) {
  return <p>{message}</p>;
}

function Parent() {
  return <Child message="Hello from Parent!" />;
}
```
예제 (Context API를 사용한 데이터 공유)
```jsx
const ThemeContext = React.createContext("light");

function ThemedComponent() {
  const theme = React.useContext(ThemeContext);
  return <p>The current theme is {theme}.</p>;
}

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <ThemedComponent />
    </ThemeContext.Provider>
  );
}
```
결론

React는 컴포넌트 기반 아키텍처와 가상 DOM을 활용하여 성능과 유지보수성을 높인 강력한 프론트엔드 라이브러리입니다. 상태 관리, 훅, 컨텍스트 API, React Router 등의 기능을 활용하여 효율적인 애플리케이션을 개발할 수 있습니다.

React는 배우기 쉽고 다양한 생태계를 갖춘 라이브러리로, 웹 애플리케이션 개발에서 필수적인 도구로 자리 잡았습니다. React를 효과적으로 활용하면 대규모 애플리케이션도 쉽게 관리하고 유지보수할 수 있습니다.


### 3월 20일 강의내용

## 개요
React.js는 Facebook에서 개발한 오픈 소스 자바스크립트 라이브러리로, 사용자 인터페이스(UI)를 구축하는 데 사용됩니다. React는 빠르고 유연하며 확장성이 뛰어난 라이브러리로, 컴포넌트 기반 아키텍처를 통해 재사용성이 높은 코드를 작성할 수 있습니다.

React는 다음과 같은 특징을 가집니다:
- **컴포넌트 기반 아키텍처**: UI를 독립적이고 재사용 가능한 컴포넌트로 분리하여 관리합니다.
- **가상 DOM (Virtual DOM)**: 실제 DOM을 직접 조작하는 대신, 가상 DOM을 사용하여 성능을 최적화합니다.
- **단방향 데이터 흐름 (One-Way Data Flow)**: 데이터가 부모에서 자식으로 흐르도록 설계되어 관리가 용이합니다.
- **JSX (JavaScript XML)**: HTML과 유사한 문법을 통해 UI를 선언적으로 작성할 수 있습니다.
- **상태 관리 (State Management)**: 상태(state)를 통해 UI를 동적으로 업데이트할 수 있습니다.

## 주요 기능

### 1. 컴포넌트 기반 구조
React는 UI를 독립적이고 재사용 가능한 컴포넌트로 나누어 개발합니다. 이러한 컴포넌트는 작은 단위로 구성되어 유지보수 및 확장이 용이합니다.

React 컴포넌트는 크게 두 가지 유형으로 나뉩니다:
1. **함수형 컴포넌트 (Functional Component)**: 간단한 UI를 정의할 때 사용되며, React Hooks를 통해 상태와 라이프사이클 기능을 사용할 수 있습니다.
2. **클래스형 컴포넌트 (Class Component)**: `React.Component`를 확장하여 생성되며, `this.state`와 `this.setState()`를 사용하여 상태를 관리할 수 있습니다.

#### 예제:
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

### 2. 가상 DOM (Virtual DOM)
React는 가상 DOM을 사용하여 실제 DOM 조작을 최소화하고 성능을 최적화합니다. 상태(state)가 변경될 때마다 React는 가상 DOM을 업데이트하고 변경된 부분만 실제 DOM에 적용합니다.

가상 DOM이 적용되는 과정:
1. 상태가 변경되면 React는 가상 DOM을 업데이트합니다.
2. React는 이전 가상 DOM과 새로운 가상 DOM을 비교(diffing)합니다.
3. 변경된 부분만 실제 DOM에 적용합니다.

이러한 방식으로 불필요한 렌더링을 최소화하여 성능을 향상시킵니다.

### 3. JSX (JavaScript XML)
JSX는 JavaScript에서 HTML과 유사한 문법을 사용하여 UI를 정의할 수 있도록 도와줍니다. JSX는 브라우저가 이해할 수 있도록 Babel을 통해 JavaScript로 변환됩니다.

#### 예제:
```jsx
const element = <h1>Hello, world!</h1>;
```

JSX를 사용하면 다음과 같은 장점이 있습니다:
- 코드의 가독성이 높아짐
- HTML과 JavaScript를 직관적으로 결합 가능
- React의 강력한 기능과 결합하여 동적인 UI를 쉽게 구현 가능

### 4. 상태 관리 (State Management)
React의 `state`는 컴포넌트의 데이터를 관리하는 중요한 개념입니다. 상태가 변경되면 React는 해당 컴포넌트를 다시 렌더링합니다.

#### 예제:
```jsx
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

React에서 상태를 관리하는 방법은 다양하며, 규모가 커지면 다음과 같은 라이브러리를 활용할 수 있습니다:
- Redux
- Recoil
- Zustand
- Context API

### 5. 프롭스 (Props)
Props는 부모 컴포넌트에서 자식 컴포넌트로 데이터를 전달하는 방법입니다. Props는 읽기 전용(immutable)이며, 컴포넌트 간 데이터 전달을 위한 주요 수단입니다.

#### 예제:
```jsx
function Greeting(props) {
  return <h1>Hello, {props.name}</h1>;
}

<Greeting name="Alice" />
```

### 6. React의 이벤트 처리
React에서는 표준 DOM 이벤트를 처리할 수 있으며, JSX에서 이벤트를 설정할 수 있습니다.

#### 예제:
```jsx
function Button() {
  function handleClick() {
    alert('Button clicked!');
  }

  return <button onClick={handleClick}>Click me</button>;
}
```

React의 이벤트 시스템은 SyntheticEvent를 사용하여 브라우저 간의 호환성을 보장합니다.

### 7. 라이프사이클 메서드 (Lifecycle Methods)
React 클래스형 컴포넌트는 컴포넌트의 생명 주기를 관리할 수 있는 여러 가지 라이프사이클 메서드를 제공합니다.

#### 주요 라이프사이클 메서드:
- `componentDidMount()`: 컴포넌트가 마운트된 후 실행됨
- `componentDidUpdate()`: 상태 또는 프롭스가 변경될 때 실행됨
- `componentWillUnmount()`: 컴포넌트가 언마운트되기 전에 실행됨

#### 예제:
```jsx
class MyComponent extends React.Component {
  componentDidMount() {
    console.log('Component mounted!');
  }

  componentWillUnmount() {
    console.log('Component will unmount!');
  }

  render() {
    return <h1>Hello, world!</h1>;
  }
}
```

## 결론
React는 컴포넌트 기반 아키텍처와 가상 DOM을 활용하여 성능과 유지보수성을 높인 강력한 프론트엔드 라이브러리입니다. 상태 관리, 훅, 컨텍스트 API, React Router 등의 기능을 활용하여 효율적인 애플리케이션을 개발할 수 있습니다.

React는 배우기 쉽고 다양한 생태계를 갖춘 라이브러리로, 웹 애플리케이션 개발에서 필수적인 도구로 자리 잡았습니다. React를 효과적으로 활용하면 대규모 애플리케이션도 쉽게 관리하고 유지보수할 수 있습니다.


### 3월 13일 강의내용  

# VS Code에서 React 설치 및 Git 연동 가이드

## 1. VS Code에서 React 개발 환경 설정하기

### 1.1 VS Code 설치
React 개발을 위해 **Visual Studio Code(VS Code)**를 설치해야 합니다. 아래 링크에서 다운로드 후 설치를 진행하세요.
- [VS Code 다운로드](https://code.visualstudio.com/)

설치가 완료되면 VS Code를 실행합니다.

### 1.2 Node.js 및 npm 설치
React는 **Node.js** 환경에서 실행되므로, 최신 버전의 Node.js를 설치해야 합니다.
- [Node.js 다운로드](https://nodejs.org/)

설치 후 터미널을 열어 버전을 확인합니다:
```sh
node -v  # Node.js 버전 확인
npm -v   # npm 버전 확인
```

### 1.3 Create React App으로 React 프로젝트 생성

Create React App(CRA)을 사용하면 손쉽게 React 프로젝트를 만들 수 있습니다.

터미널에서 원하는 디렉토리로 이동 후 아래 명령어 실행:
```sh
npx create-react-app my-app
cd my-app
npm start
```
위 명령어를 실행하면 `http://localhost:3000`에서 React 애플리케이션이 실행됩니다.

## 2. Git을 사용하여 프로젝트 관리하기

### 2.1 Git 설치
Git이 설치되지 않았다면 아래 사이트에서 다운로드 후 설치하세요.
- [Git 다운로드](https://git-scm.com/)

설치 후 버전 확인:
```sh
git --version
```

### 2.2 Git 초기화 및 GitHub 연동

#### 1) Git 초기화
프로젝트 폴더에서 Git을 초기화합니다:
```sh
git init
```

#### 2) `.gitignore` 파일 생성
React 프로젝트에서 불필요한 파일을 Git에 포함하지 않도록 `.gitignore` 파일을 추가해야 합니다.
기본적으로 `create-react-app`은 자동으로 `.gitignore` 파일을 생성합니다.

#### 3) GitHub 저장소 생성 및 연결
GitHub에 접속하여 새 저장소(repository)를 생성한 후, 터미널에서 다음 명령어를 실행하여 연결합니다.
```sh
git remote add origin https://github.com/사용자이름/저장소이름.git
```

#### 4) 프로젝트 커밋 및 푸시
```sh
git add .
git commit -m "Initial commit"
git branch -M main
git push -u origin main
```
위 명령어를 실행하면 프로젝트가 GitHub에 업로드됩니다.

### 2.3 Git에서 변경 사항 반영
#### 1) 변경 사항 확인
```sh
git status
```
#### 2) 변경 사항 커밋 및 푸시
```sh
git add .
git commit -m "Updated project"
git push origin main
```

## 3. 결론
이제 VS Code에서 React 프로젝트를 생성하고, GitHub와 연동하여 관리할 수 있습니다. 이를 활용하여 체계적으로 React 애플리케이션을 개발하세요!

