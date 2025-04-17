# 202130230 지영준. 

### 4월 17일 강의내용  
## Array.prototype.at()
1. Array 인스턴스의 at() 메서드는 정숫값을 받아 해당 인덱스에 있는 항목을 반환하며, 양수와 음수를 사용할 수 있습니다. 음의 정수는 배열의 마지막 항목부터 거슬러 셉니다.  
``` jsx 
const array1 = [5, 12, 8, 130, 44];

let index = 2;

console.log(`An index of ${index} returns ${array1.at(index)}`);
// Expected output: "An index of 2 returns 8"

index = -2;

console.log(`An index of ${index} returns ${array1.at(index)}`);
// Expected output: "An index of -2 returns 130"
```
* 출력값  
> "An index of 2 returns 8"  
> "An index of -2 returns 130"  


# 1. 📦 State 끌어올리기 (Lifting State Up) 추가설명

React에서 여러 컴포넌트가 동일한 데이터를 필요로 할 때, 각 컴포넌트가 개별적으로 state를 가지면 데이터의 **일관성 유지**가 어렵습니다. 이럴 때 사용하는 기법이 바로 **상태 끌어올리기(Lifting State Up)** 입니다.

---

## ✅ 개념 설명

- **상태 끌어올리기**란, 여러 컴포넌트에서 동일한 데이터가 필요할 때 해당 데이터를 이들의 **공통 부모 컴포넌트로 이동**시켜서 관리하는 것입니다.
- 공통 부모 컴포넌트가 state를 가지며, 자식 컴포넌트는 props를 통해 데이터를 전달받고, 변경 요청은 콜백 함수로 부모에게 전달합니다.

---

## 🎯 왜 필요한가요?

| 이유 | 설명 |
|------|------|
| 데이터 일관성 유지 | 여러 컴포넌트가 동일한 데이터를 사용 시, 서로 동기화된 상태 유지 가능 |
| 코드 간결성 | 중복된 상태와 로직 제거 |
| 상태 추적 용이 | 상태가 한 곳에 집중되므로 디버깅이 쉬움 |
| 컴포넌트 재사용성 향상 | 자식 컴포넌트는 props만 받아 동작하므로 더 유연하게 재사용 가능 |

---

## 🧪 예시 코드: 온도 변환기

섭씨(Celsius)와 화씨(Fahrenheit)를 입력하는 두 개의 컴포넌트를 동기화된 상태로 만들기

### TemperatureInput 컴포넌트

```jsx
function TemperatureInput({ scale, temperature, onTemperatureChange }) {
  const scaleNames = {
    c: '섭씨',
    f: '화씨'
  };

  return (
    <fieldset>
      <legend>{scaleNames[scale]} 온도를 입력하세요:</legend>
      <input
        value={temperature}
        onChange={(e) => onTemperatureChange(e.target.value)}
      />
    </fieldset>
  );
}
```
## 2. Calculator (공통 부모) 컴포넌트
```jsx
function Calculator() {
  const [temperature, setTemperature] = useState('');
  const [scale, setScale] = useState('c');

  const handleCelsiusChange = (temp) => {
    setScale('c');
    setTemperature(temp);
  };

  const handleFahrenheitChange = (temp) => {
    setScale('f');
    setTemperature(temp);
  };

  const toCelsius = (f) => ((f - 32) * 5) / 9;
  const toFahrenheit = (c) => (c * 9) / 5 + 32;

  const celsius = scale === 'f' ? toCelsius(temperature) : temperature;
  const fahrenheit = scale === 'c' ? toFahrenheit(temperature) : temperature;

  return (
    <div>
      <TemperatureInput
        scale="c"
        temperature={celsius}
        onTemperatureChange={handleCelsiusChange}
      />
      <TemperatureInput
        scale="f"
        temperature={fahrenheit}
        onTemperatureChange={handleFahrenheitChange}
      />
    </div>
  );
}
```

## 교대로 두기 - 1  
• 현재까지 작성한 틱택토 게임에서 가장 큰 결함인 0"를 보드에 표시할 수 없다는 문제를 수정할 차례입니다.
1. 첫 번째 선수가 두는 말을 X"로 설정합니다. 이제 Board 컴포넌트에 또 다른 state를 추가하 여 추적해 보겠습니다.
# X와 0가 번갈아 한 번씩 두어야 하기 때문에 X가 두었는지 아닌지 현재의 상태를 보관하면 됩니다.
```jsx

즉, X의 차례면 true,
0의 차례면 false 상태로 기억하면 됩니다.
function Board() {
const [xINext, seXIsNext] = useState(true) ;
const [squares, setSquares] = useState(Array (9). fill(null));
```

2.  플레이어가 움직일 때마다 다음 플레이어를 결정하기 위해 불리언 값인 xIsNext가 반전되고 게 임의 state가 저장됩니다. Board의 handleCLick 함수를 업데이트하여 xIsNext의 값을 반전시 키세요
```jsx
export default function Board() {
  const [xIsNext, setXIsNext] = useState(true);
  const [squares, setSquares] = useState(Array(9). fill(null));

function handleClick(i) {
  const nextSquares = squares.slice();
  if (xIsNext) {
  nextSquares [1] = "X";
  } else {
  nextSquares [i] = "0";
  }
  setSquares (nextSquares);
  setXIsNext(!XIsNext);
  }
  return (
  /...
}
```

## 교대로 두기 - 2

* 이제 다른 사각형을 클릭하면 정상적으로 X와 0가 번갈아 표시됩니다!
* 하지만 다른 문제가 발생했습니다. 같은 사각형을 여러 번 클릭해 보세요.
* 0가 X를 덮어씌웁니다! 이렇게 하면 게임이 좀 더 흥미로워질 수 있지만 지금은 원래의 규칙을 유지하겠습니다.
* 지금은 X와 0로 사각형을 표시할 때 먼저 해당 사각형에 이미 X 또는 0값이 있는지 확인하고 있 지 않습니다.
* 앞으로 돌아가서 이 문제를 해결하기 위해 사각형에 이미 X와 0가 있는지 확인하겠습니다.
1. Square가 이미 채워져 있는 경우 Board의 state를 업데이트하기 전에 handLecLick 함수에서 조기에 return 하겠습니다
```jsx
function handleClick(i) {
if (squares [1]) { 
  return;
}
const nextSquares = squares slice();
}
```
* 이제 빈 사각형에 X 또는 0만 추가할 수 있습니다!

# return의 의미
* 작성한 코드에는 return값이 없습니다.
* JavaScript에서 return값이 없는 return;은 함수를 즉시 종료하라는 의미입니다.
* 이때 값을 반환하지 않으면 자동으로 undefined를 반환합니다.
* squares[1]가 이미 값이 있다면 (누군가 이미 둔 곳이라면), 그 자리에 다시 둘 수 없으니 아무 일도 하지 말고 함수를 끝내는 것입니다  

## 승자 결정하기
*  이제 어느 플레이어의 다음 차례인지 표시했으니, 게임의 승자가 결정되어 더 이상 차례를 만들 필요가 없을 때도 표시해야 합니다.
* 이를 위해 9개의 사각형 배열을 가져와서 승자를 확인하고, 적절하게 'X', 0', 또는 nuLl을 반환하는 도우미 함수 calculateWinner를 추가하겠습니다.
* calculatewinner 함수에 대해 너무 걱정하지 마세요. 이 함수는 React에서만 국한되는 함수가 아닙니다.
* [중요] calculatewinner 함수를 Board의 앞에 정의하든 뒤에 정의하는 상관없습니다. 여기에선 컴포넌트를 편집할 때마다 편집기 상에서 스크롤 할 필요가 없도록 마지막에 배치하겠습니다.

## 승자 결정하기 - 1
1. 먼저 승리할 수 있는 경우의 자리를 2차원 배열로 선언합니다.
2. 선언된 배열 Line과 Squares를 비교하기 위한 for문을 작성합니다.
3. 비교를 위해 구조 분해 할당을 합니다
```jsx
export default function Board() {
// ...
function calculateWinner (squares) {
const lines = [
[0, 1, 2],
[3, 4, 5],
[6, 7, 8]
[0, 3, 6],
[1, 4, 7],
[2, 5, 8],
[0, 4, 8],
[2, 4, 6]
];
for (let i = 0; i ‹ lines. length; i++) {
const [a, b, c] - lines[i]; if (squares[a] && squares[a]
=== squares [b] && squares[a] === squares[c]) {
return squares [a];
}
return null;
}
```  

# 구조 분해 할당 (Destructuring Assignment)
* 비구조화 할당, 구조화 할당이라고도 번역되지만 구조 분해 할당을 많이 사용합니다.
* 구화 분해 할당은 배열이나 객체의 구조를 해체하여 내부 값을 개별 변수에 쉽게 할당하는 방법 입니다.
* 이를 통해 코드의 간결성과 가독성을 높일 수 있습니다.
* map함수에서도 사용되는 아주 많이 사용하는 방법입니다  
<hr>

### 배열인 경우  
```jsx
const pairs={
  [1,2],
  [3,4],
  [5,6]
};

pairs.map(([x,y]) => {
  console.log('x: ${x}, y: ${y}');
});
```  
### 객체인 경우

```jsx
const users = [
{ id: 1, name: "Alice" },
{id: 2, name: "Bob" }
];

users-map(({ id, name }) => {
console.log('${id}: ${name}');
});
```
• lines는 승리 할 수 있는 Squares의 index 번호입니다.
• for문을 통해 lines의 길이 만큼 비교를 반복합니다.
• 구조 분해 할당을 통해 Lines의 index를 a, b, C에 보관합니다.
• Squares의 해당
I index 값을 비교하여 3개가 모두 일치하면 값이 X인지 0인지를 return합니다.
• 일치하는 것이 없으면 null을 return합니다
```jsx
function calculateWinner (squares) {
const lines - [
[0, 1, 2],
[3, 4, 5],
[6, 7, 8],
[0, 3, 6],
[1, 4, 7],
[2, 5, 8],
[0, 4, 8],
[2, 4, 6］
];
for (let i = 0; 1 < lines. length; 1++) {
  const [a, b, c) - lines[i];
  if (squares[a) && squares[a) -=- squares[b] && squares[a) -== square[c])v{
    return squares [a];
  }
}
return null;
}
```
### 승자 결정하기 - 1  
4. Board 컴포넌트의 handleCLick 함수에서
calculatewinner (Squares)를 호출하여 플레이어가
이겼는지 확인하세요.  
5. 이 검사는 사용자가 이미 X 또는 0가 있는 사각형을 클릭했는지를 확인하는 것과 동시에 수행할 수 있습니다.  
6. 두 경우 모두 함수를 조기 반환하겠습니다. 함수를 즉시 종료한다는 의미 입니다.
```jsx
function handleClick(i) {
if (squares[i] || calculateWinner (squares)) {
return;
}
const nextSquares = squares slice();
//...
}
```
*  여기까지 작성하면 경기는 정상적으로 진행되지만, 경기 종료 알림 표시가 나오지 않습니다.  

### 승자 결정하기 - 2
7. 게임이 끝났을 때 플레이어에게 알리기 위해 "Winner: X” 또는 "Winner: 0”라고 표시하겠습니다.  
8. 이렇게 하려면 Board 컴포넌트에 status 구역을 추가하면 됩니다.  
9. 게임이 끝나면 status는 승자를 표시하고, 게임이 진행 중인 경우 다음 플레이어의 차례를 표시 합니다  

```jsx
export default function Board() {
  //...
const winner = calculateWinner (squares) ;
let status;
if (winner) {
status = "Winner:" + winner;
} else {
status = "Next player: " + (xIsNext ? "X" : "0");
}
  return (
    <>
    <div className="status"> {status}</div>
    <div className="board-row">
      //...
  )
}
```
## 시간여행 추가하기
* 마지막 연습으로 게임의 이전 동작으로 "시간을 거슬러 올라가는" 기능을 만들어 보겠습니다.  
[플레이 히스토리 저장하기]  
* Squares 배열을 직접 업데이트하면 시간 여행을 구현하기는 매우 어려울 것입니다.  
* 하지만 우리는 sLiceO를 사용하여 플레이어가 클릭할 때마다 Squares 배열의 새 복사본을 만들 고 이를 불변으로 처리했습니다.  
* 덕분에 squares 배열의 모든 과거 버전을 저장할 수 있고, 의미 발생한 플레이의 내용을 탐색할 수 있습니다  
• 과거의 sauares 배열을 history라는 다른 배열에 저장하고, 이 배열을 새로운 * state 변수로 저장하겠습니다.  
* history 배열은 첫 번째 플레이부터 마지막 플레이까지 모든 보드 state를 나타내며 다음과 같은 모양을 갖습니다
```jsx
[
// Before first move
[null, null, null, null, null, null, null, null, null],
Il After first move
[null, null, null, null, 'X', null, null, null, null],
// After second move
[null, null, null, null, 'X', null, null, null, '0'],
// ...
]
```
## 한번 더 state 끌어올리기
* 이제 과거 플레이 목록을 표시하기 위해 새로운 최상위 컴포넌트 Game을 작성하세요.
* 여기에 전체 게임 기록을 포함하는 history state를 배치하겠습니다.
* history state를 Game 컴포넌트에 배치하면 자식 Board 컴포넌트에서 Squares state를 제거 할 수 있습니다.
* Square 컴포넌트에서 Board 컴포넌트로 State를 "끌어올렸던" 것처럼, 이제 Board 컴포넌트에 서 최상위 Game 컴포넌트로 state를 끌어올릴 수 있습니다.
* 이렇게 하면 Game 컴포넌트가 Board 컴포넌트의 데이터를 완전히 제어하고 Board의 history에 서 이전 순서를 렌더링하도록 지시할 수 있습니다.
#### 이번 절은 단계가 많아서 도중에 오류가 나거나, WARNING이 많이 발생합니다.끝까지 작성하면 정상 동작합니다.

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

