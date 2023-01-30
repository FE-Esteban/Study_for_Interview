# this

> 자신이 속한 객체 또는 자신이 생성하는 인스턴스를 가리키는 자기 참조 변수
>
> 함수가 호출될 때 결정된다는 특징이 있다

## this 바인딩 특징

> 기본적으로 this에는 전역 객체가 바인딩 되지만 <br />
> 호출하는 방식에 따라 this가 가리키는 값이 동적으로 변화함

1. 일반함수로 호출된 모든 함수 내부의 this에는 전역 객체가 바인딩
2. 메서드로 호출시에는 호출한 객체가 바인딩
3. 생성자 함수로 호출시에는 미래에 생설할 인스턴스가 바인딩
4. call, apply, bind 메서드에 의한 호출시에는 첫 번째 인수가 바인딩

## this 예시 코드 1 : 일반함수, 메서드 호출

```javascript
const someone = {
  name: "sso",
  whoAmI: function () {
    console.log(this);
  },
};

// 일반함수 호출
const myWhoAmI = someone.whoAmI;
myWhoAmI(); // window 객체

// 메서드 호출
someone.whoAmI(); // someone 객체 {name: "sso", whoAmI: function}
```

## this 예시 2 : 생성자 함수 호출

```javascript
function Person(name) {
  this.name = name;
  return this;
}

const person1 = new Person("so");
const person2 = new Person("상오");
const person3 = Person("asd");

console.log(person1); // Person {name : "so"}
console.log(person2); // Person {name: "상오"}
console.log(person3); // window 객체
```

➡️ 생성자 함수 호출시 `new` 연산자와 함께 호출하지 않으면
일반함수로 동작한다

## this 예시 3 : call, apply, bind 호출

```js
function getThisBind() {
  return this;
}

// 인수로 넣을 식별자 thisArg
const thisArg = { a: 1 };

// 일반함수, call, apply, bind 호출통한 this 바인딩
const normal = getThisBind(thisArg);
const applyThisBind = getThisBind.apply(thisArg);
const callThisBind = getThisBind.call(thisArg);
const bindThisBind = getThisBind.bind(thisArg);

// 출력
console.log(normal); // window 객체
console.log(applyThisBind); // {a : 1}
console.log(callThisBind); // {a : 1}
console.log(bindThisBind); // getThisBind 함수 => bind는 호출 키워드 x
```
