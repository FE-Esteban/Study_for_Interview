# 스코프

## 스코프란?

스코프란 변수가 값을 참조할 때 접근할 수 있는 범위를 말한다.</br>
함수 내에서 선언된 변수는 함수 내부에서만 유효한 함수 레벨 스코프를 따른다.
```js
let a = "global";

function scope() {
  let a = "local";
  console.log(x);
}

scope();

console.log(x);

// 결과
"local"
"global"
```
* 가장 바깥 부분과 scope 함수 내부에 같은 이름을 갖는 변수 a를 선언했고 함수 외부와 내부에서 각각 변수 x를 참조한다.
* 위 코드에서 가장 바깥 영역에 선언된 a 변수는 어디서든 참조할 수 있다.
* 하지만, scope 함수 내부에 선언된 a 변수는 scope 함수 내부에서만 참조할 수 있고 외부에서는 참조할 수 없다.

## 스코프의 종류

스코프는 전역(global)과 지역(local)으로 구분할 수 있다.</br>
* 전역: 코드의 가장 바깥 영역
* 지역: 함수 몸체 내부

```js
var x = "global x";
var y = "global y";


function outer() {
  var z = "outer local z";
  
  console.log(x);   // global x
  console.log(y);   // global y
  console.log(z);   // outer local z
  
  function inner() {
    var x = "inner local x";
    
    console.log(x);   // inner local x
    console.log(y);   // global y
    console.log(z);   // outer local z
  }
  
  inner();
}

outer();

console.log(x);     // global x
console.log(y);     // global y
console.log(z);     // ReferenceError: z is not defined 
```
### 잔역-전역스코프
* 전역은 전역 스코프를 만든다. 전역에 변수를 선언하면 전역 스코프를 갖는 전역 변수가 된다.
* 전역 변수는 어디서든지 참조할 수 있다.
### 지역-지역스코프
* 지역도 지역 스코프를 만든다. 지역에 변수를 선언하면 지역 스코프를 갖는 지역 변수가 된다.
* 지역 변수는 자신이 선언된 지역과 하위 지역(중첩 함수)에서만 참조될 수 있다.
* 위에서 outer 함수 내부에 선언된 변수 z는 지역 변수이므로 자신의 지역 스코프인 outer 함수 내부와 하위 지역 스코프인 inner 함수 내부에서 참조할 수 있다.
* inner 함수에 선언된 x 변수와 전역 x 변수의 이름이 같을 때는 자바스크립트 엔진이 inner 함수 내부에 선언된 변수 x를 참조한다.
* 이는 자바스크립트 엔진이 스코프 체인을 통해 참조할 변수를 검색했기 때문이다.

## 스코프체인
스코프는 함수 중첩에 의해 계층적 구조를 갖는다.
* 위 코드에서 outer()함수는 <strong>외부 함수 또는 상위스코프</strong> 이며, inner()함수는 outer() 내부에 정의된 <strong>중첩 함수</strong># 스코프

## 스코프란?

스코프란 변수가 값을 참조할 때 접근할 수 있는 범위를 말한다.</br>
함수 내에서 선언된 변수는 함수 내부에서만 유효한 함수 레벨 스코프를 따른다.
```js
let a = "global";

function scope() {
  let a = "local";
  console.log(x);
}

scope();

console.log(x);

// 결과
"local"
"global"
```
* 가장 바깥 부분과 scope 함수 내부에 같은 이름을 갖는 변수 a를 선언했고 함수 외부와 내부에서 각각 변수 x를 참조한다.
* 위 코드에서 가장 바깥 영역에 선언된 a 변수는 어디서든 참조할 수 있다.
* 하지만, scope 함수 내부에 선언된 a 변수는 scope 함수 내부에서만 참조할 수 있고 외부에서는 참조할 수 없다.

## 스코프의 종류

스코프는 전역(global)과 지역(local)으로 구분할 수 있다.</br>
* 전역: 코드의 가장 바깥 영역
* 지역: 함수 몸체 내부

```js
var x = "global x";
var y = "global y";


function outer() {
  var z = "outer local z";
  
  console.log(x);   // global x
  console.log(y);   // global y
  console.log(z);   // outer local z
  
  function inner() {
    var x = "inner local x";
    
    console.log(x);   // inner local x
    console.log(y);   // global y
    console.log(z);   // outer local z
  }
  
  inner();
}

outer();

console.log(x);     // global x
console.log(y);     // global y
console.log(z);     // ReferenceError: z is not defined 
```
### 잔역-전역스코프
* 전역은 전역 스코프를 만든다. 전역에 변수를 선언하면 전역 스코프를 갖는 전역 변수가 된다.
* 전역 변수는 어디서든지 참조할 수 있다.
### 지역-지역스코프
* 지역도 지역 스코프를 만든다. 지역에 변수를 선언하면 지역 스코프를 갖는 지역 변수가 된다.
* 지역 변수는 자신이 선언된 지역과 하위 지역(중첩 함수)에서만 참조될 수 있다.
* 위에서 outer 함수 내부에 선언된 변수 z는 지역 변수이므로 자신의 지역 스코프인 outer 함수 내부와 하위 지역 스코프인 inner 함수 내부에서 참조할 수 있다.
* inner 함수에 선언된 x 변수와 전역 x 변수의 이름이 같을 때는 자바스크립트 엔진이 inner 함수 내부에 선언된 변수 x를 참조한다.
* 이는 자바스크립트 엔진이 스코프 체인을 통해 참조할 변수를 검색했기 때문이다.

## 스코프체인
스코프는 함수 중첩에 의해 계층적 구조를 갖는다.
* 위 코드에서 outer()함수는 <strong>외부 함수 또는 상위스코프</strong> 이며, inner()함수는 outer() 내부에 정의된 <strong>중첩 함수</strong>이다.
* 모든 스코프는 하나의 계층적 구조로 연결되며, 모든 지역 스코프의 최상위 스코프는 전역 스코프이다.
* 변수를 참조할 때 자바스크립트 엔진은 스코프 체인을 통해 변수를 참조하는 코드의 스코프에서 시작하여 상위 스코프 방향으로 이동하며 선언된 변수를 검색 한다. 즉, 상위 스코프의 변수를 하위 스코프가 참조할 수 있다.

### 변수 검색 과정
1. inner 함수 지역 스코프에 x 변수가 선언 되었는지 검색 </br>
 -inner 함수에 x 변수가 선언되었으므로 그 변수를 참조하고 검색을 종료
2. y 변수 inner 함수 지역 스코프에 선언되었는지 검색</br>
 -inner 함수 내부에는 y 변수가 선언되지 않았으므로 상위 스코프인 outer 함수의 지역 스코프로 이동해 검색 </br>
 -outer 함수 내부에도 y 변수의 선언이 존재하지 않으므로 상위 스코프인 전역 스코프로 이동해 검색</br>
 -전역 스코프에 y 변수의 선언이 존재하므로 검색된 변수를 참조하고 검색을 종료
3. z 변수 inner 함수를 먼저 검색하고 outer 함수를 검색 </br>
 -outer 함수 내부에 z 변수가 선언되었으므로 검색된 변수를 참조하고 검색을 종료
 </br>

<strong>하위 스코프에서 유효한 변수를 상위 스코프에서 참조할 수 없음</strong>
이다.
* 모든 스코프는 하나의 계층적 구조로 연결되며, 모든 지역 스코프의 최상위 스코프는 전역 스코프이다.
* 변수를 참조할 때 자바스크립트 엔진은 스코프 체인을 통해 변수를 참조하는 코드의 스코프에서 시작하여 상위 스코프 방향으로 이동하며 선언된 변수를 검색 한다. 즉, 상위 스코프의 변수를 하위 스코프가 참조할 수 있다.

### 변수 검색 과정
1. inner 함수 지역 스코프에 x 변수가 선언 되었는지 검색 </br>
 -inner 함수에 x 변수가 선언되었으므로 그 변수를 참조하고 검색을 종료
2. y 변수 inner 함수 지역 스코프에 선언되었는지 검색</br>
 -inner 함수 내부에는 y 변수가 선언되지 않았으므로 상위 스코프인 outer 함수의 지역 스코프로 이동해 검색 </br>
 -outer 함수 내부에도 y 변수의 선언이 존재하지 않으므로 상위 스코프인 전역 스코프로 이동해 검색</br>
 -전역 스코프에 y 변수의 선언이 존재하므로 검색된 변수를 참조하고 검색을 종료
3. z 변수 inner 함수를 먼저 검색하고 outer 함수를 검색 </br>
 -outer 함수 내부에 z 변수가 선언되었으므로 검색된 변수를 참조하고 검색을 종료
 </br>

<strong>하위 스코프에서 유효한 변수를 상위 스코프에서 참조할 수 없음</strong>
