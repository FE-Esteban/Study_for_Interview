# this
## this란?
this는 함수를 호출할 때 생성되는 실행 컨텍스트 객체이다. </br>
this가 가리키는 대상은 어떻게 this가 호출되는 지에 따라 다르다.

## this바인딩이란?
바인딩이란 식별자와 값을 연결사키는 과정을 말하는데, 하여, this바인딩이란 this호출방식에 따라 this가 특정 객체에 연결되는 것이다.

## this의 동적 바인딩
this 호출 방식에 따라 바인딩 되는 객체가 달라진다.
</br>
* 일반 함수로 호출시 this는 전역 변수에 바인딩됩니다.(기본 바인딩)
* 메서드로서 호출 시에는 호출한 객체를 바인딩합니다.(암시적 바인딩)
* 생성자함수로서 호출시에는 생성자 함수가 생성할 객체에 바인딩 됩니다.(new 바인딩)
* call,bind,apply메소드 사용 시 첫번재 인수로 전달하는 객체에 바인딩 됩니다.(명시적 바인딩)
* 화살표 함수에서는 위의 규칙들이 적용되지 않고, this에 lexical scope가 적용되어, 화살표함수를 정의하는 시점의 컨택스트 객체가 this에 바인딩된다.

### 기본 바인딩
* 기본 바인딩이 적용되면 this는 전역객체에 바인딩된다. (브라우저는 window, Node.js는 global에 바인딩 됨.)
* 다른 바인딩 규칙이 적용되지 않을 때 적욕되는 기본규칙이다.
* 엄격모드에서는 기본 바인딩 대상에서 전역객체는 제외된다.
```js
function foo() {
    const a=10;
    console.log(this.a)
}
foo() //undefined
```
> this에 전역객체가 바인딩 되므로 a라는 프로퍼티가 없어서 undefined가 출력된다.
```js
window.a=20
function foo() {
    console.log(this.a)
}
foo() //20
```
> this가 전역객체에 바인딩 되는데 foo 함수 위에서 전역객체의 a라는 프로퍼티에 값을 주었으므로 해당 a의 프로퍼티 값이 출력된다.
```js
// 엄격모드
window.a=20
function foo() {
    console.log(this.a)
}
foo() // undefined
```
> 엄격모드에서는 전역객체를 바인딩 하지 않아 this가 바인딩 될 대상이 없어 에러가 난다.

## 암시적 바인딩
* 암시적 바인딩이란 함수가 객체의 메서드로서 호출되는 상황에서 this는 해당 함수를 호출한 객체, 즉 콘텍스트 객체에 바인딩된다.
```js
const foo = {
    a: 20,
    bar: function () {
        console.log(this.a)
    }
}

foo.bar() //20
```
### 암시적 바인딩을 사용할 때 문제점
* 암시적 바인딩을 사용할 때 문제점은 함수를 매개변수(콜백)로 넘겨서 실행 할 때, 바인딩이 소실된다는 점이다.
```js
const foo = {
    a: 20,
    bar: function () {
        console.log(this.a)
    }
}

setTimeout(foo.bar, 1) //undefined
```
> setTimeout 함수 안에 전달한 콜백은 bar함수의 레퍼런스 일 뿐, foo의 콘텍스트를 가지고 있지 않다. 따라서, this는 기본바인딩이 적용되어 전역객체에 바인딩 되고 undefined의 결과가 다온다.</br>
이것을 <strong>바인딩이 소실</strong>되었다고 한다.

## 명시적 바인딩
* 자바스크립트의 모든 Function은 call(),apply(),bind()라는 프로토타입 메소드를 가진다.
* 3가지 메소드 중 하나를 호출하면 this는 내가 명시한 객체에 바인딩된다.
### call(), apply()
```js
const foo = {
    a: 20,
}

function bar() {
    console.log(this.a)
}

bar.call(foo) //20
bar.apply(foo) //20
```
> 메서드 call,apply의 매개변수로 바인딩할 객체를 넘겨주면 bar함수를 실행할 때, this에 foo컨텍스트를 직접 바인딩 할 수 있다.

> call과 apply 동작은 같지만 두번째 매개변수로 call은 매개변수의 목록, apply는 배열을 받는다는 차이점이 있다.

### bind()
```js
const foo = {
    a: 20,
}

function bar() {
    console.log(this.a)
}

const bound = bar.bind(foo)
bound() //20
```
> bind 메서드는 매개변수로 전달받은 객체에 this가 바인딩 된 함수를 반환한다. 이를 하드 바인딩이라 한다.

> 바인딩 된 함수는 후에 호출 될 때마다 처음 정해진 this 바인딩을 가지고 호출된다.

## new 바인딩
* 자바스크립트의 new 키워드는 함수를 호출할 때 앞에 new키워드를 사용하는 것으로 객체를 초기화 시킬 수 있다. 이때 사용되는 함수를 생성자 함수라 한다. (생성자 함수는 대문자로 시작)
* 생성자 함수는 this키워드를 해당 생성자를 이용해 생성할 객체해 대한 참조로 사용한다.

```js
function Foo() {
    this.a=20;
}

const foo = new Foo();

consol.log(foo.a)//20
```
> Foo함수가 new키워드와 함께 호출되는 순간 새로운 객체가 생성되고, 새로 생성된 객체가 this로 바인딩 된다.

## 화살표 함수
* ES6에 추가된 화살표 함수는 this를 바인딩할 때 위의 규칙들이 적용되지 않고 this에 Lexical scope가 적용된다. 
* 즉, 화살표 함수를 정의하는 시점의 컨텍스트 객체가 this에 바인딩된다.
```js
const foo = {
    a: 20,
    bar: function() {
        setTimeout(()=>{
            console.log(this.a)
        },1)
    }
}

foo.bar() //20
```
> setTimeout의 콜백인 화살표 함수 선언시에 this는 foo객체를 가리킨다.(렉시컬 스코프) 콜백이 실행될 때 this는 foo에 바인딩된다.

> 화살표 함수로 선언시 렉시컬 스코프를 통해 바인딩 된 this는 apply,bind등의 함수나 new 함수로 오버라이드 할 수 없다. 그래서 콜백 함수로 사용할 때 유용하다.