# 🍀 useState

- 컴포넌트는 종종 상호작용에 의해 화면이 반응할 필요가 있는데, 입력 창이나, 다음 버튼, 구매 버튼 등이 있다.
- 사용자의 이벤트에 의해 렌더링이 되도록 원할 때 사용하는 훅이다.
- state가 변할 때마다 렌더링이 발생하기 때문에, 과도한 사용은 자제하는 것이 좋다.
- state를 직접적으로 변경하지 않는 이유는 state가 객체로 이루어져 있기 때문에, 직접 변경할 경우 메모리 주소 값이 변경되지 않기 때문에 immutable한 객체의 특성상 state가 변경 되었다는 인식을 하지 못하게 된다. 따라서 setState를 통해서 새로운 객체를 할당해야 한다.

### 사용법

```Javascript
const [state, setState] = useState(defaultValue);
```

- 초기값을 defaultValue안에 넣어주고, 값이 변경되길 원할 경우, setState(원하는 state 값)으로 변경해준다.
  <br/><br/>

# 🍀 useEffect

- 컴포넌트가 렌더링 될 때 특정 작업을 실행할 수 있도록 하는 Hook이다.
- 리액트의 useEffect 훅을 사용하면 함수 컴포넌트에서도 side effect를 사용할 수 있다.
- 클래스형 컴포넌트의 라이프 사이클을 자체적으로 대체할 수 있다.

## 사용법

```JavaScript
useEffect(effect,[deps])
```

### effect

- 렌더링 이후 실행항 함수(DOM 업데이트 이후에 불러낸다.)
  > 당시의 state나 props의 값을 뽑아 놓기 때문에, 연속적으로 setTimeout을 이용해서 값을 받아오는 걸 지연시켜도 정상적으로 값을 반환한다.
- 함수를 return 할 경우 컴포넌트가 Unmount 될 때 정리의 개념으로 함수가 한 번 실행된다.(componentWillUnmount 기능)

### deps

- 의존성 배열안에 넣은 값이 변경될 때마다 실행이 된다.
- 배열이 없을 경우, 렌더링이 될 때마다 실행되며, 빈 배열일 경우 mount 될 때만 실행이 된다.
  <br/><br/>

# 🍀 useRef

- 컴포넌트에서 특정 DOM 요소에 접근하고 싶을 때 ref를 사용한다. (자바스크립트의 document.querySelector() 기능)
- 렌더링을 일으키지 않으며, 값이 계속 변경 되지만, 렌더링이 일어나야 화면에 적용이 된다.
- 선택하고 싶은 DOM에 ref 값으로 설정해서 사용한다. 해당 DOM 요소를 확인하고 싶으면 .current로 확인

## 사용법

```JavaScript
const inputRef = useRef(default);
return <input ref={inputRef}/>
```

# 🍀 useCallback

- 메모이제이션 기능을 지원하는 React 내장 훅.
- 함수를 메모이제이션 해서 의존성 배열안의 값이 변경 될 때마다 함수를 반환한다.
- 의존성 배열의 값은 함수 내부에서 사용하는 값으로 설정해야한다. 외부에서 사용되는 값을 사용할 경우

## 사용법

```JavaScript
const memoizedCallback = useCallback(() => {
    doSomething(a, b);
  },[a, b]);
```

# 🍀 useMemo

- 메모이제이션 기능을 지원하는 React 내장 훅2.
- 함수의 반환 값을 메모이제이션 해서 의존성 배열안의 값이 변경 될 때마다 값을 반환 함.
- useMemo는 함수의 결과 값을 메모이제이션하는 것이기 때문에 렌더링 될 때마다 함수는 계속 실행이 된다.

## 사용법

```JavaScript
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

> useCallback과 useMemo는 자체적으로 메모리를 만들어 값을 보관하는 훅이기 때문에, 간단한 함수에는 적용하지 않는 것이 좋다. 컴포넌트를 끌어다 쓰는 경우, 해당 컴포넌트에 React.memo로 묶어 컴포넌트 자체를 메모이제이션 해야한다.
