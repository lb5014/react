# 202130230 지영준. 
### 3월 13일 강의내용  
# React.js 기능 설명 README

## 개요
React.js는 Facebook에서 개발한 오픈 소스 자바스크립트 라이브러리로, 사용자 인터페이스(UI)를 구축하는 데 사용됩니다. React는 빠르고 유연하며 확장성이 뛰어난 라이브러리로, 컴포넌트 기반 아키텍처를 통해 재사용성이 높은 코드를 작성할 수 있습니다.

## 주요 기능

### 1. 컴포넌트 기반 구조
React는 UI를 독립적이고 재사용 가능한 컴포넌트로 나누어 개발합니다. 이러한 컴포넌트는 작은 단위로 구성되어 유지보수 및 확장이 용이합니다.

#### 예제:
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

### 2. 가상 DOM (Virtual DOM)
React는 가상 DOM을 사용하여 실제 DOM 조작을 최소화하고 성능을 최적화합니다. 상태(state)가 변경될 때마다 React는 가상 DOM을 업데이트하고 변경된 부분만 실제 DOM에 적용합니다.

### 3. JSX (JavaScript XML)
JSX는 JavaScript에서 HTML과 유사한 문법을 사용하여 UI를 정의할 수 있도록 도와줍니다. JSX는 브라우저가 이해할 수 있도록 Babel을 통해 JavaScript로 변환됩니다.

#### 예제:
```jsx
const element = <h1>Hello, world!</h1>;
```

### 4. 상태 관리 (State Management)
React의 state는 컴포넌트의 데이터를 관리하는 중요한 개념입니다. 상태가 변경되면 React는 해당 컴포넌트를 다시 렌더링합니다.

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

### 5. 프롭스 (Props)
Props는 부모 컴포넌트에서 자식 컴포넌트로 데이터를 전달하는 방법입니다. Props는 읽기 전용(immutable)입니다.

#### 예제:
```jsx
function Greeting(props) {
  return <h1>Hello, {props.name}</h1>;
}

<Greeting name="Alice" />
```

### 6. 이벤트 처리 (Event Handling)
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

### 7. 라이프사이클 메서드 (Lifecycle Methods)
클래스 컴포넌트에서는 컴포넌트의 생명 주기를 관리할 수 있는 메서드를 제공합니다.

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

### 8. 훅 (Hooks)
React 16.8부터 함수형 컴포넌트에서 상태와 라이프사이클 기능을 사용할 수 있도록 훅이 도입되었습니다.

#### 주요 훅:
- `useState()`: 상태 관리
- `useEffect()`: 사이드 이펙트 관리
- `useContext()`: 컨텍스트 API 사용

#### 예제:
```jsx
import { useEffect, useState } from 'react';

function Timer() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setCount((prev) => prev + 1);
    }, 1000);

    return () => clearInterval(interval);
  }, []);

  return <p>Timer: {count}</p>;
}
```

### 9. 컨텍스트 API (Context API)
Context API를 사용하면 컴포넌트 트리 전체에서 데이터를 쉽게 공유할 수 있습니다.

#### 예제:
```jsx
import { createContext, useContext } from 'react';

const ThemeContext = createContext('light');

function ThemeButton() {
  const theme = useContext(ThemeContext);
  return <button style={{ background: theme === 'dark' ? '#333' : '#fff' }}>Theme Button</button>;
}
```

### 10. React Router
React Router를 사용하면 SPA에서 클라이언트 측 라우팅을 구현할 수 있습니다.

#### 예제:
```jsx
import { BrowserRouter as Router, Route, Routes, Link } from 'react-router-dom';

function Home() {
  return <h1>Home Page</h1>;
}

function About() {
  return <h1>About Page</h1>;
}

function App() {
  return (
    <Router>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </Router>
  );
}
```

## 결론
React는 컴포넌트 기반 아키텍처와 가상 DOM을 활용하여 성능과 유지보수성을 높인 강력한 프론트엔드 라이브러리입니다. 상태 관리, 훅, 컨텍스트 API, React Router 등의 기능을 활용하여 효율적인 애플리케이션을 개발할 수 있습니다.

### 3월 20일 강의내용

