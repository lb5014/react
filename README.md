# 202130230 지영준. 


## 5월 22일 강의내용
## React 시도하기
* 단순히 React를 사용해 보고 싶다면, 아무것도 설치할 필요 없습니다. 이 샌드박스를 통해 사용 해 보세요!
### Local에서 사용해 보고 싶다면 Node.js만 설치 하면 됩니다.
* 직접 편집하거나 오른쪽 상단의 "Fork(포크)" 버튼을 눌러 새 탭에서 열 수 있습니다.
* React 문서의 대부분 페이지에는 이와 같은 샌드박스가 있습니다.
* React 문서 외에도 CodeSandbox, StackBlitz, CodePen 등의 온라인 샌드박스에서 React를 지원합니다
```jsx
function Greeting({ name }) {
  return <h1>Hello, {name) </h1>;
}
export default function App() {
return ‹Greeting name="world" />
}
```
## 5-1. 새로운 React 앱 만들기
* React로 새로운 앱이나 웹사이트를 구축하려면 프레임워크부터 시작하는 것이 좋습니다.
* 앱에 기존 프레임워크에서 잘 제공되지 않는 제약 조건이 있거나, 자체 프레임워크를 빌드하는 것을 선호하거나, React 앱의 기본 사항만 배우려는 경우 React 앱을 처음부터 빌드할 수 있습 니다.
* 풀스택 프레임워크
- 권장 프레임워크는 프로덕션에서 앱을 배포하고 확장하는 데 필요한 모든 기능을 지원합니다.
- 최신 React 기능을 통합하고 React의 아키텍처를 활용합니다

### 중요합니다!
#### 풀스택 프레임워크에는 서버가 필요하지 않습니다
  * 이 페이지의 모든 프레임워크는 클라이언트 측 렌더링(CSR), 단일 페이지 앱(SPA), 정적 사이트 생성(SSG)을 지 원합니다. 이러한 앱은 서버 없이 CDN 또는 정적 호스팅 서비스에 배포할 수 있습니다. 또한 이러한 프레임워크 를 사용하면 사용 사례에 적합한 경우 경로별로 서버 측 렌더링을 추가할 수 있습니다.
  * 이렇게 하면 클라이언트 전용 앱으로 시작할 수 있으며, 나중에 요구 사항이 변경되는 경우 앱을 다시 작성하지 않 고도 개별 경로에서 서버 기능을 사용하도록 선택할 수 있습니다. 렌더링 전략을 구성하는 방법에 대한 프레임워 크 설명서를 참조하세요.

## 5-1. 새로운 React 앱 만들기
* Next.js (앱 라우터)
- Next.js의 앱 라우터는 React의 아키텍처를 최대한 활용하여 풀 스택 React 앱을 활성화하는 React 프레임워크입니다.
- Next.js는 Vercel에서 유지 관리합니다.
- Next.js 앱을 빌드해서 Node. is와 서버리스 호스팅 혹은 자체 서버에 배포할 수 있습니다.
- Next.js는 또한 서버가 필요 없는 정적 내보내기도 지원합니다.
- Vercel은 추가적으로 옵트-인 유료 클라우드 서비스도 지원합니다.
* opt-in이란 사용자가 옵션을 직접 선택할 수 있도록 하는 서비스 입니다.  

* React Router (v7)
   - React Router는 React에서 가장 인기있는 라우팅 라이브러리이며, Vite와 함께 사용하면 풀 스택 React 프레임워크를 만들 수 있습니다.
  - 표준 web API이며, 다양한 자바스크립트 런타임과 플랫폼을 위한 준비된 배포 템플릿이 있다 고 강조합니다.
  - React Router는 Shopify에서 유지 관리합니다

## 5-1. 새로운 React 앱 만들기
* Expo (네이티브 앱용)
- Expo는 네이티브 UI를 사용하여 안드로이드, 105, 웹을 위한 범용 앱을 만들 수 있는 React 프레임워크입니다.
- 네이티브 부분을 쉽게 사용할 수 있게 해주는 React Native SDK를 제공합니다.
- Expo는 Expo(the company)에서 유지 관리합니다.
- EXpO로 앱을 빌드하는 것은 무료이고, 구글이나 애플 스토어에 제한 없이 제출할 수 있습니 다.- Expo는 추가적으로 옵트-인 유료 클라우드 서비스를 제공합니다.
* 풀스택 React 비전을 향해 나아가고 있는 또 다른 떠오르는 프레임워크가 있습니다.
* Tanstack Start (Beta): TanStack Start는 TanStack Router를 기반으로 하는 풀스택 React 프레임워크입니다. Nitro나 Vite와 같이 전체 문서 SSR, 스트리밍, 서버 함수, 번들링과 많은 유용한 도구를 제공합니다.
* RedwoodJS: Redwood는 쉽게 풀스택 웹 애플리케이션을 만들 수 있도록 사전탑재된 패키지와 구 성을 가진 풀스택 React 프레임워크입니다


## 5-1. 새로운 React 앱 만들기
[처음부터 시작하기 1- 기존 프레임워크를 사용하지 않고 ...
* 앱에 기존 프레임워크에서 잘 제공되지 않는 제약 조건이 있거나, 자체 프레임워크를 구축하는 것을 선호하거나, React 앱의 기본 사항을 배우려는 경우 React 프로젝트를 처음부터 시작하는 데 사용할 수 있는 다른 옵션이 있습니다.
* 처음부터 시작하면 더 많은 유연성을 얻을 수 있지만 라우팅, 데이터 가져오기 및 기타 일반적인 사용 패턴에 사용할 도구를 선택해야 합니다.
* 이미 존재하는 프레임워크를 사용하는 대신 자신만의 프레임워크를 구축하는 것과 비슷합니다.
저희가 권장하는 프레임워크에는 이러한 문제에 대한 기본 제공 솔루션이 있습니다.
* 자신만의 솔루션을 구축하려면, Vite, Parcel 또는 RSbuild와 같은 빌드 도구로 시작할 수 있 도록 하는 처음부터 React 앱 만들기 가이드를 참조하세

## 5-2. 처음부터 React 앱 만들기
#### [ Parcel ]
* ParceL은 뛰어난 기본 개발 경험과 확장 가능한 아키텍처를 결합하여 프로젝트를 시작 단계에서 대규모 프로덕션 애플리케이션으로 발전시킬 수 있습니다.
* Parcel은 빠른 새로고침, JSX, TypeScript, Flow 및 스타일링을 기본적으로 지원합니다.
Parcel의 React 레시피를 참조하여 시작해 보세요
#### [ Rsbuild ]
* Rsbuild는 React 애플리케이션 개발에 원활한 환경을 제공하는 Rspack 기반 빌드 도구입니다.
* 세심하게 조정된 기본 설정과 성능 최적화 기능을 바로 사용할 수 있도록 제공합니다.
* Rsbuild는 빠른 새로고침, JSX, TypeScript, 스타일링 등 React 기능을 기본적으로 지원합니 다.
* 시작하려면 Rsbuild의 React 가이드를 참조하세요.

## 5-2. 처음부터 React 앱 만들기
##### [ React Native® Metro ]
* React Native를 처음부터 사용하려면 React Native용 JavaScript 번들러인 Metro를 사용해야 합니다.
* Metro는 iOS 및 Android와 같은 플랫폼에 대한 번들링을 지원하지만, 여기 소개된 도구에 비해 기능이 부족한 편입니다.
* 프로젝트에 React Native 지원이 필요하지 않다면 Vite, Parcel 또는 Rsbuild로 시작하는 것 이 좋습니다.

## 5-2. 처음부터 React 앱 만들기
#### [ 2단계: 공통 애플리케이션 패턴 구축]
* 위에 나열된 빌드 도구는 클라이언트 전용 단일 페이지 앱(SPA)으로 시작하지만 라우팅, 데이터 가져오기, 스타일링과 같은 일반적인 기능에 대한 추가 솔루션은 포함하지 않습니다.
* React 생태계에는 이러한 문제를 해결하는 다양한 도구가 있습니다.
* 널리 사용되는 몇 가지 도구를 소개했지만, 더 나은 도구가 있다면 다른 도구를 선택해도 됩니 다.
##### [ Routing ]
* 라우팅은 사용자가 특정 URL을 방문할 때 표시할 콘텐츠나 페이지를 결정합니다.
* 앱의 여러 부분에 URL을 매핑하려면 라우터를 설정해야 합니다.
* 또한 중첩된 경로, 경로 매개변수, 쿼리 매개변수도 처리해야 합니다.
* 라우터는 코드 내에서 구성하거나 구성 요소 폴더 및 파일 구조에 따라 정의할 수 있습니다

## 5-2. 처음부터 React 앱 만들기
* 라우터는 최신 애플리케이션의 핵심 부분이며, 일반적으로
- 데이터 페치 : 더 빠른 로딩을 위해 전체 페이지에 대한 데이터를 미리 페치하는 것 포함
- 코드 분할 : 클라이언트 번들 크기를 최소화하기 위한 것
- 페이지 렌더링 방식 : 각 페이지가 생성되는 방식을 결정하기 위한 것 이 포함됩니다.
* 다음을 사용하는 것을 추천합니다.
- React Router
- Tanstack Router

#### [ Data Fetching ] 데이터 미리 가져오기
* 서버나 다른 데이터 소스에서 데이터를 미리 가져오는 것으로 대부분의 애플리케이션에서 핵심적 인 부분입니다.
* 이를 제대로 수행하려면 로딩 상태, 오류 상태, 그리고 가져온 데이터를 캐싱 등 복잡한 기능이 포함됩니다

## 5-2. 처음부터 React 앱 만들기
* 특별히 제작된 데이터 가져오기 라이브러리는 데이터를 가져오고 캐싱하는 어려운 작업을 대신 처 리해 주므로, 개발자는 앱에 필요한 데이터와 이를 표시하는 방법에 집중할 수 있습니다.
* 이러한 라이브러리는 일반적으로 컴포넌트에서 직접 사용되지만, 더 빠른 프리페칭과 더 나은 성 능을 위해 라우팅 로더에 통합되거나 서버 렌더링에도 사용할 수 있습니다.
* 컴포넌트에서 직접 데이터를 가져오면 네트워크 요청 폭주로 인해 로딩 시간이 느려질 수 있으므 로, 라우터 로더나 서버에서 데이터를 미리 가져오는 것이 좋습니다.
* 이렇게 하면 페이지가 표시될 때 페이지의 모든 데이터를 한 번에 가져올 수 있습니다.
* 대부분의 백엔드나 REST 스타일 API에서 데이터를 가져오는 경우 다음을 사용하는 것이 좋습니 다.
- React Query
- SWR
- RTK

#### [ Code-splitting ] 코드 분할
* 코드 분할은 앱을 필요에 따라 로드할 수 있는 작은 묶음으로 나누는 프로세스입니다.
* 앱의 코드 크기는 새로운 기능과 추가 종속성이 있을 때마다 합니다.
* 앱 전체의 코드를 전송해야 사용하기 때문에 앱 로드 속도가 느려질 수 있습니다.
* 캐싱, 기능/종속성 축소, 일부 코드를 서버에서 실행되도록 이동하면 로드 속도 저하를 완화하는 데 도움이 되지만,, 과도하게 사용하면 기능이 저하될 수 있는 불완전한 해결책입니다.
* 마찬가지로, 프레임워크를 사용하는 앱에 의존하여 코드를 분할하는 경우, 코드 분할이 전혀 발 생하지 않았을 때보다 로딩 속도가 느려지는 상황이 발생할 수 있습니다

## 5-2. 처음부터 React 앱 만들기
* 예를 들어, 차트를 지연 로딩하면 차트 렌더링에 필요한 코드 전송이 지연되어 차트 코드가 앱의 나머지 부분에서 분리됩니다.
* Parcel은 React. Lazy를 사용하여 코드 분할을 지원합니다.
* 그러나 차트가 처음 렌더링된 후 데이터를 로드하면 두 번 대기하게 됩니다.
  * 이 것을 워터폴(waterfalL) 현상이라고 합니다.
* 차트 데이터를 가져오는 것과 동시에 렌더링 코드를 전송하는 것이 아니라, 각 단계가 차례로 완 료될 때까지 기다려야 합니다.
* 번들링 및 데이터 페칭과 통합된 경로 별 코드 분할은
- 앱의 초기 로드 시간과 앱에서 가장 큰 콘텐츠를 렌더링하는 데 걸리는 시간을 줄일 수 있습니 다. ( 가장 큰 콘텐츠 페인트 )

## 5-2. 처음부터 React 앱 만들기
#### [ 애플리케이션 성능 개선 ]
* 선택한 빌드 도구는 단일 페이지 앱(SPA)만 지원하므로
- 서버 사이드 렌더링(SSR) # SSG와 유사하지만 매 요청 시 서버에서 정적 페이지 생성
- 정적 사이트 생성(SSG) # 빌드 시 한 번에 모든 정적 페이지 생성
- React 서버 컴포넌트(RSC) # 서버에서 동작하는 컴포넌트로 DB 접근 등이 가능 와 같은 다른 렌더링 패턴을 구현해야 합니다.
* 처음에는 이러한 기능이 필요하지 않더라도 나중에 SSR, SSG 또는 RSC에 도움이 될 수 있는 몇 가지 방법이 있을 수 있습니다.
1. 단일 페이지 앱(SPA)은 단일 HTML 페이지를 로드하고, 사용자가 앱과 상호작용할 때 페이지를 동적으로 업데이트합니다.
    - SPA는 시작하기는 쉽지만 초기 로드 시간이 느릴 수 있습니다.
    - SPA는 대부분의 빌드 도구에서 기본 아키텍처로 사용됩니다.


## 5월 15일 강의내용
## Step 3: 최소한의 데이터만 이용해서 완벽하게 UI State 표현하기
• 위 데이터들을 다시 한번 순서대로 살펴봅시다.
1. 제품의 원본 목록은 props로 전달되었기 때문에 state가 아닙니다.
2. 사용자가 입력한 검색어는 시간이 지남에 따라 변하고, 다른 요소로부터 계산될 수 없기 때문 에 state로 볼 수 있습니다.
3. 체크박스의 값은 시간에 따라 바뀌고 다른 요소로부터 계산될 수 없기 때문에 state로 볼 수 있습니다.
4. 필터링된 제품 목록은 원본 제품 목록을 받아서 검색어와 체크박스의 값에 따라 계산할 수 있 으므로, 이는 state가 아닙니다.  

• 따라서, 검색어와 체크박스의 값만이 state입니다! 잘하셨습니다!
#### 공식문서의 자세히 살표보기를 통해서 Props와 State에 관해서 다시한번 정리합니다.

## Step 4: State가 어디에 있어야 할 지 정하기 
* 이제 앱에서 최소한으로 필요한 state를 결정했습니다.
* 다음으로는 어떤 컴포넌트가 이 state를 소유하고, 변경할 책임을 지게 할지 정해야 합니다.
* React는 항상 컴포넌트 계층구조를 따라 부모에서 자식으로 데이터를 전달하는 단방향 데이터 흐 름을 사용하는 것을 기억하세요!
* 앱을 구현하면서 어떤 컴포넌트가 state를 가져야 하는 지 바로 명확하지 않을 수 있습니다.
* 이 개념이 처음이라면 더 어려울 수 있습니다.
* 그러나 아래의 과정을 따라가면 해결할 수 있습니다.
* 애플리케이션의 각 state에 대해서,

1. 해당 state를 기반으로 렌더링하는 모든 컴포넌트를 찾으세요.
2. 그들의 가장 가까운 공통되는 부모 컴포넌트를 찾으세요. - 계층에서 모두를 포괄하는 상위 컴포 넌트
3. state가 어디에 위치 돼야 하는지 결정합시다

## Step 4: State가 어디에 있어야 할 지 정하기
• state가 어디에 위치 돼야 하는지 결정하려면,
1. 대개, 공통 부모에 state를 그냥 두면 됩니다.
2. 혹은, 공통 부모 상위의 컴포넌트에 둬도 됩니다.
3. state를 소유할 적절한 컴포넌트를 찾지 못했다면, state를 소유하는 컴포넌트를 하나 만들어서 상위 계층에 추가하세요.
①
* 이전 단계에서, 이 애플리케이션의 도 가지 state인 사용자의 검색어 입력과 체크박스의 값"을 발견하였습니다.
* 이 예시에서 두 가지 state 항상 함께 나타나기 때문에 같은 위치에 두는 것이 합리적입니다.
* 이제 이 전략을 애플리케이션에 적용해 봅시다.





## 5월 8일 강의내용
## React로 사고하기
* React를 사용하게 되면 우리가 고려하고 있는 디자인이나 만들 앱들에 대한 생각을 바꿀 수 있습 니다.
* React로 사용자 인터페이스를 빌드할 때, 먼저 이를 컴포넌트라는 조각으로 나눕니다.
* 그리고 각 컴포넌트의 다양한 시각적 상태들을 정의합니다.
* 마지막으로 컴포넌트들을 연결하여 데이터가 그 사이를 흘러가게 합니다.
* 이 자습서에서는 React로 검색할 수 있는 상품 테이블을 만드는 과정을 체계적으로 안내해 드리 겠습니다.
    * React는 component 기반으로 개발 합니다. 이 번 장을 통해서 component의 조각 들이 어떻게 App으로 완성되는지 다시 한번 확인해 보세요.  

## 모의 시안과 함께 시작하기 그
• 이미 ISON API와 디자이너로부터 제공받은 모의 시안이 있다고 생각해 봅시다.
• JSON API는 아래와 같은 형태의 데이터를 반환합니다.
--JSON API
```jsx
[


{ category: "Fruits", price: "$1", stocked: true, name: "Apple" },

{ category: "Fruits", price: "$1", stocked: true, name: "Dragonfruit" },

{ category: "Fruits", price: "$2", stocked: false, name: "Passionfruit" },

{ category: "Vegetables", price: "$2", stocked: true, name: "Spinach" },

{ category: "Vegetables", price: "$4", stocked: false, name: "Pumpkin" }7,

{ category: "Vegetables", price: "$1", stocked: true, name: "Peas" 3}

]
```  
## Step 1: UI를 컴포넌트 계층으로 쪼개기
* 먼저 모의 시안에 있는 모든 컴포넌트와 하위 컴포넌트 주변에 박스를 그리고, 그들에게 이름을 붙이면서 시작해 보세요.
* 디자이너와 함께 일한다면 그들이 이미 디자인 툴을 통하여 이 컴포넌트들에 이름을 정해 두었을 수도 있습니다. 한번 여쭤보세요!
* 어떤 배경을 가지고 있냐에 따라, 디자인을 컴포넌트로 나누는 방법에 대한 관점이 달라질 수 있 습니다.
* Programming : 새로운 함수나 객체를 만드는 방식과 같은 방법으로 해봅시다.
  - 이 중 단일책임 원칙을 반영하고자 한다면 컴포넌트는 이상적으로는 화 번에 한 가지 일만 해 야 합니다.
  - 만약 컴포넌트가 점점 커진다면 작은 하위 컴포넌트로 쪼개져야 하겠죠.
* CSS : 클래스 선택자를 무엇으로 만들지 생각해 봅시다. (실제 컴포넌트들은 약간 좀 더 세분되어 있습니다)
* Design : 디자인 계층을 어떤 식으로 구성할 지 생각해 봅시다.
### Step 1: UI를 컴포넌트 계층으로 쪼개기
* JSON이 잘 구조화 되어 있다면, 종종 이것이 UI의 컴포넌트 구조가 자연스럽게 데이터 모델에 대응된다는 것을 발견할 수 있습니다.
* 이는 VI와 데이터 모델은 보통 같은 정보 아키텍처, 즉 같은 구조를 가지기 때문입니다.
* UI를 컴포너트로 분리하고, 각 컴포넌트가 데이터 모델에 매칭될 수 있도록 하세요.
* 여기 다섯 개의 컴포넌트가 있습니다

### Step 1: UI를 컴포넌트 계층으로 쪼개기
1. FilterableProductTable(회색): 예시 전체를 포괄합니다.
2. SearchBar(파란색): 사용자의 입력을 받습니다.
3. ProductTable(라벤더색): 데이터 리스트를 보여주고, 사용자의 입력을 기반으로 필터링합니다.
4. ProductCategoryRow(초록색): 각 카테고리의 헤더를 보여줍니다.
5. ProductRow(노란색): 각각의 제품에 해당하는 행을 보여줍니다.  


### Step 1: UI를 컴포넌트 계층으로 쪼개기
* ProductTable을 보면 "Name"과 "Price" 레이블을 포함한 테이블 헤더 기능만을 가진 컴포넌트 는 없습니다.
* 독립된 컴포넌트를 따로 생성할 지 생성하지 않을지는 당신의 선택입니다.
* 이 예시에서는 3.ProductTable에 있는 단순한 헤더들이 ProductTable의 일부이기 때문에 위 레이블들을 컴포넌트로 만들지 않고 그냥 남겨두었습니다
* 그러나 이 헤더가 복잡해지면 (즉 정렬을 위한 기능을 추가하는 등) ProductTabLeHeader 컴포 넌트를 만드는 것이 더 합리적일 것입니다.
* 이제 모의 시안 내의 컴포넌트들을 확인했으니, 이들을 계층 구조로 정리해 봅시다.
* 모의 시안에서 한 컴포넌트 내에 있는 다른 컴포넌트는 계층 구조에서 자식으로 표현됩니다.
```jsx
FilterableProductTable
- SearchBar
- ProductTable
  - ProductCategoryRow
  - ProductRow
```  
## Step 2: React로 정적인 버전 구현하기
* 이제 컴포넌트 계층구조가 만들어졌으니, 앱을 실제로 구현해 볼 시간입니다.
* 가장 쉬운 접근 방법은 상호작용 기능은 아직 추가하지 않고, 데이터 모델로부터 UI를 렌더링하 는 버전을 만드는 것입니다.
* 대체로 먼저 정적인 버전을 만들고 상호작용 기능을 추가하는 게 더 쉽습니다.
* 정적 버전을 만드는 것은 많은 타이핑이 필요하지만, 생각할 것은 적습니다.
* 반대로 상호작용 기능을 추가하는 것은 많은 생각이 필요하지만, 타이핑은 그리 많이 필요하지 않습니다.
* 데이터 모델을 렌더링하는 앱의 정적인 버전을 만들기 위해서는
- 다른 컴포넌트를 재사용하고,
- props를 이용하여 데이터를 넘겨주는 컴포넌트를 구현하는 것이 좋습니다.
* props는 부모가 자식에게 데이터를 넘겨줄 때 사용할 수 있는 방법입니다.

### Step 2: React로 정적인 버전 구현하기
* 혹시 state 개념에 익숙하다고 해도 정적인 버전을 만드는 데는 state를 쓰지 마세요!
* state는 오직 상호작용을 위해, 즉 시간이 지남에 따라 데이터가 바뀌는 것에 사용합니다.
* 우리는 앱의 정적 버전을 만들고 있기 때문에 지금은 필요하지 않습니다.
* 앱을 만들 때 계층 구조에 따라 상층부에 있는 컴포넌트 즉, 1. FilterableProductTable부터 시작하는 하향식(top-down)으로 만드는 방법이 있습니다.
* 또는 하층부에 있는 컴포넌트인 5. ProductRow)부터 상향식(bottom-up)으로 만들 수도 있습니 다.
* 간단한 예시에서는 보통 하향식으로 만드는 게 쉽지만, 프로젝트가 커지면 상향식으로 만들고 테 스트를 작성하면서 개발하기가 더 쉽습니다.
### 공식 문서의 첫 번째 코드는 state를 사용하기 전 완성된 코드입니다. 천천히 component 하나씩 완성해 봅니다.



### 4월 18일 강의내용
## 한 번 더 state 끌어올리기
1. 먼저 export default가 있는 Game 컴포넌트를 추가하세요.
2. 마크업 안에 Board 컴포넌트를 렌더링하도록 하세요.
3. export default 컴포넌트는 하나의 컴포넌트 파일 안에 하나만 존재해야 하므로 Board에서는 삭제합니다.
4. 이것은 index.js 파일에서 Board 컴포넌트 대신 Game 컴포넌트를 최상위 컴포넌트로 사용하도록 지시합니다.

5. Game 컴포넌트가 반환하는 내용에 추가한 div는 나중에 보드에 추가할 게임 정보를 위한 공간을 확보합니다.
```jsx
function Board() {
//...
}

export default function Game() {
return (
<div className="game">
<div className="game-board">
<Board />
</div>
<div className="game-info">
<ol> {/*TODO*/}</ol>
</div>
</div>
);
}
```
### 주의
* 우리는 index가 아니고 App에서 불러오고 있습니다.
* 최상위 컴포넌트이기 때문에 최상위에 선언합니다.
* 최상위 컴포넌트와 파일이름은 일치 시키는 것이 좋습니다.

6. 다음 플레이어와 플레이 기록을 추적하기 위해
Game 컴포넌트에 몇 개의 state를 추가하세요.
```jsx
export default function Game ) {
const [xINext, seXIsNext] = useState(true);
const [history, setHistory] = useState([Array(9) .fill(null)]);
// ...
```
7. 현재 플레이에 대한 square을 렌더링하려면 history에서 마지막 Squares의 배열을 읽어야 합 니다.
8. 렌더링 중에 계산할 수 있는 충분한 정보가 이미 있으므로 usestate는 필요하지 않습니다.

```jsx
export default function Game () {
const [xIsNext, setXIsNext] = useState(true) ;
const [history, setHistory] = useState([Array(9).fill(null)]);
const currentSquares
}
```
9. 다음으로 Game 컴포넌트 안의 Board 컴포넌트가 게임을 업데이트할 때 호출할 handleplay 함 소를 만드세요.  
10. XISNext, currentsquares, handleplay 를 Board 컴포넌트에 props로 전달하세요.  

```jsx
export default function Game() {
const [xIsNext, setXIsNext] = useState (true) ;
const [history, setHistory] = useState([Array(9).fill(null)]);
const currentSquares = history[history.length - 1];
function handlePlay(nextSquares) {
/I TODO
}
return (
‹div className="game">
‹div className="game-board">
‹Board xIsNext={xIsNext} squares={currentSquares} onPlay={handlePlay} /›
//...
)
}
```  
* Board 컴포넌트가 props에 의해 완전히 제어되도록 만들겠습니다.
11. Board 컴포넌트가 xIsNext, squares, onPlay 함수를 props로 받을 수 있도록 변경합니다.
- onPlay는 Board가 업데이트된 Squares를 배열로 호출할 수 있는 새로운 함수입니다.
12. 다음으로 Board 함수에서 usestate를 호출하는 처음 두 줄을 제거하세요.
```jsx
function Board({ xIsNext, squares, onPlay }){
function handleClick(1) {
//..
}
//..
}
```
13. 이제 Board 컴포넌트의 handLeClick에 있는 setSquares 및 setxIsNext 호출을 새로운 onPlay 함수에 대한 단일 호출로 대체함으로써 사용자가 사각형을 클릭할 때 Game 컴포넌트가 Board를 업데이트할 수 있습니다.

```jsx
if (xIsNext) {
nextSquares [i] = "X";
} else {
nextSquares [i] = "0";
}
onPlay (nextSquares) ;
```
* Board 컴포넌트는 Game 컴포넌트가 전달한 props에 의해 완전히 제어됩니다.
* 게임이 다시 작동하게 하려면 Game 컴포넌트에서 handleplay 함수를 구현해야 합니다.
* handLepLay가 호출되면 무엇을 해야 할까요?  
-> 이전의 Board는 업데이트된 setSquares를 호출했지만, 이제는 업데이트된 Squares 배열을 onPlay로 전달한다는 걸 기억하세요.
* handlePlay 함수는 리렌더링을 트리거하기 위해 Game의 state를 업데이트해야 하지만, 더 이상 호출할 수 있는 setSquares 함수가 없습니다.
대신 이 정보를 저장하기 위해 history state 변수를 사용하고 있습니다.
* 업데이트된 squares 배열을 새 히스토리 항목으로 추가하여 history를 업데이트해야 하고, Board에서 했던 것처럼 xIsNext 값을 반전시켜야 합니다.
```jsx
export default function Game () {
//...
function handlePlay(nextSquares) {
setHistory([...history, nextSquares]);
setXIsNext(!xIsNext);
}
//...
}
```
* 앞에서 [..history, nextSquares]는 history에 있는 모든 항목을 포함하는 새 배열을 만들 고 그 뒤에 nextSquares를 만듭니다.  
 * ...history **전개 구문**을 사용하면 history 의 모든 항목 열거"로 읽을 수 있습니다.
* 예를 들어, history가 [[nult,nult,null], ["x",nult,nuLt]]이고 nextSquares 가 ["X", nult, "0"]라면 새로운 [history, nextSquares] 배열은 [tnultnuLt,nuL], ["X",nult,null], ["X",nll,0]]가 될 것입니다.
* 이 시점에서 state를 Game 컴포넌트로 옮겼으므로 리팩토링 전과 마찬가지로 UI가 완전히 작동 해야 합니다.
  * 전개 연산자(spread operator) ...

# ⏳ React 시간 여행 (Time Travel) 기능 구현

React로 상태의 변경 이력을 추적하고, 이전 상태로 되돌아가거나 다시 앞으로 이동할 수 있는 “시간 여행(Time Travel)” 기능을 구현하는 방법을 설명합니다. 이 기능은 디버깅, 복잡한 상태 관리, 또는 사용자 편의성을 높이기 위한 다양한 UI에 사용됩니다.

---

## 🧠 시간 여행 기능이란?

- **상태 변경 이력(history)** 을 배열로 저장해두고,
- 사용자가 원하는 시점의 상태로 **되돌아가거나(Undo)** 또는 **되돌린 상태에서 다시 앞으로 가는(Redo)** 기능을 제공합니다.
- 모든 상태 변경은 **새로운 상태 객체를 생성**하여, 불변성을 유지하며 관리합니다.

---

## 🔧 필요한 기능 요약

| 기능 | 설명 |
|------|------|
| 상태 이력 저장 | 상태를 배열(history)로 저장 |
| 현재 인덱스 추적 | 현재 상태가 이력 중 몇 번째인지 추적 |
| 상태 업데이트 | 새로운 상태로 업데이트 시, 현재 인덱스 이후의 상태를 잘라냄 |
| Undo | 현재 인덱스 -1로 이동 |
| Redo | 현재 인덱스 +1로 이동 |
| 단축키 지원 | Ctrl+Z (undo), Ctrl+Y 또는 Ctrl+Shift+Z (redo) |

---

## 🧱 전체 JSX 코드 예시

```jsx
import React, { useState, useEffect } from 'react';

function TimeTravelApp() {
  // 초기 상태 정의
  const initialState = { count: 0 };

  // 상태 이력과 현재 인덱스
  const [history, setHistory] = useState([initialState]);
  const [currentIndex, setCurrentIndex] = useState(0);

  // 현재 상태는 history 배열의 currentIndex 번째
  const currentState = history[currentIndex];

  // 상태 업데이트 함수
  const updateState = (newState) => {
    const trimmedHistory = history.slice(0, currentIndex + 1);
    const newHistory = [...trimmedHistory, newState];
    setHistory(newHistory);
    setCurrentIndex(newHistory.length - 1);
  };

  // 증가/감소 핸들러
  const increment = () => updateState({ count: currentState.count + 1 });
  const decrement = () => updateState({ count: currentState.count - 1 });

  // Undo/Redo 핸들러
  const undo = () => {
    if (currentIndex > 0) {
      setCurrentIndex(currentIndex - 1);
    }
  };

  const redo = () => {
    if (currentIndex < history.length - 1) {
      setCurrentIndex(currentIndex + 1);
    }
  };

  // 단축키 이벤트 핸들링
  useEffect(() => {
    const handleKeyDown = (e) => {
      if (e.ctrlKey && e.key === 'z') {
        e.preventDefault();
        undo();
      } else if ((e.ctrlKey && e.key === 'y') || (e.ctrlKey && e.shiftKey && e.key === 'Z')) {
        e.preventDefault();
        redo();
      }
    };

    window.addEventListener('keydown', handleKeyDown);
    return () => window.removeEventListener('keydown', handleKeyDown);
  }, [currentIndex, history]);

  return (
    <div style={{ textAlign: 'center', marginTop: '50px' }}>
      <h1>🕰️ 시간 여행 예제</h1>
      <h2>Count: {currentState.count}</h2>
      <button onClick={decrement}>-</button>
      <button onClick={increment}>+</button>
      <br /><br />
      <button onClick={undo} disabled={currentIndex === 0}>Undo (Ctrl+Z)</button>
      <button onClick={redo} disabled={currentIndex === history.length - 1}>Redo (Ctrl+Y)</button>
      <p>현재 인덱스: {currentIndex}</p>
    </div>
  );
}

export default TimeTravelApp;
```
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

