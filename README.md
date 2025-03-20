# 202130230 지영준. 
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




