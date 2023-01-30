# this

- JavaScript의 예약어.
- 자신이 **속한 객체** 또는 자신이 **생성할 인스턴스**를 가리키는 자기 참조 변수.
- 속한 객체나 생성할 인스턴스의 **프로퍼티, 메소드를 참조**할 수 있다.
- '**이것**'이라는 의미 그대로 **함수가 호출되는 방식**에 따라 동적으로 결정된다.
- strict mode의 경우 기본 바인딩 대상에서 전역객체는 제외된다.
  <br/><br/>

# 🍀 this 바인딩

- 바인딩이란 **식별자와 값을 연결하는 과정**을 말한다.
- 변수 선언은 변수명과 메모리 주소를 바인딩 하는 것.
- this의 호출 방식에 따라 this가 특정 객체에 연결되는 것.
- 일반 함수, 메서드, 생성자 함수, Call,Apply,Bind를 통한 호출 방식으로 나눌 수 있다.
  <br/><br/>

## 1. 전역에서의 this

- **브라우저 런타임**의 경우 this는 전역 객체 **window를** 참조한다.
- **node.js 런타임**의 경우 this는 전역 객체 **global을** 참조한다.
  <br/><br/>

## 2. 일반 함수에서의 this

- 함수가 **프로퍼티 값이 아니라면 모든 함수의 this는 전역객체**인 window나 global이 된다.
- 내부 함수, 콜백 함수의 경우도 this는 전역 객체에 바인딩 된다.
- 프로퍼티가 함수인 경우, 메소드의 내부함수도 this가 전역 객체에 바인딩이 된다.
- this가 전역객체를 참조하는 것을 막기 위해 명시적으로 바인딩할 필요가 있다.(call, apply, bind 등)
  <br/><br/>
  > 단, **화살표 함수**의 경우 this 바인딩할 객체가 선언할 때 정적으로 결정되는데, 언제나 **상위 스코프의 this**를 가르킨다.(Lexical this) 따라서 call, apply, bind 메소드를 사용하여 this를 변경할 수 없다.

<br/><br/>

## 3. 메소드에서의 this

- 함수가 객체의 프로퍼티 값이면 메소드로서 호출되는데, 이때 메소드 내부의 this는 해당 **메소드를 소유한 객체에 바인딩**된다.
- 모든 객체에 해당되므로 프로토타입 객체도 해당된다.
  <br/><br/>

## 4. 생성자 함수에서의 this

- **생성자 함수는 객체를 생성하는 함수**다. new 연산자를 붙여 호출하면 해당 함수는 생성자 함수로 동작한다.
  1. 호출 했을 때, 빈 객체를 생성하고 이 객체에 this 바인딩을 한다.
  2. 빈 객체는 생성자 함수의 프로토타입 프로퍼티가 가르키는 객체를 자신의 프로토타입 객체로 설정하고,
  3. 빈 객체에 this를 이용해 프로퍼티, 메소드를 생성해 추가한다.
  4. 객체를 반환한다.

<br/><br/>

## 5. EventListner에서의 this

- 이벤트 리스너에서의 this는 이벤트를 발생시킨 객체가 된다.
- 혼동을 줄 수 있기 때문에, 콜백 함수를 화살표 함수로 작성하거나 bind로 this 바인딩 해 줄 필요가 있다.

```JavaScript
class Event {
  init() {
    div.addEventListener("click", this.sayThis);
    div.addEventListener("click", this.sayThat);
    div.addEventListener("click", this.useBind.bind(this));
  }
  sayThis() {
    console.log("함수 선언식", this); // div
  }
  sayThat = () => {
    console.log("화살표 함수", this); //Event
  };
  useBind() {
    console.log("함수 선언식 with bind", this); //Event
  }
}
```
