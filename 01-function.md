## 함수
```javascript
function getMyBot() {
    console.log("This is getMyBot function");
    return "Hello World";
}
```
#### 호출과 참조
- getMyBot()은 함수의 바디를 실행하는 호출이고, getMyBot은 참조이며 함수를 실행하지 않는다. 
- 함수 참조 패턴

```
// 다른 이름으로 함수 호출
const f = getMyBot;
f();

// 함수를 객체 프로퍼티에 할당
const o = {};
o.f = getMyBot;
o.f();

// 함수를 배열 요소에 할당
const arr = [1, 2, 3];
arr[1] = getMyBot;
arr[1]();
```
#### 함수와 매개변수 
```javascript
function f(o) {
    o.message = `f안에서 수정함`;
    o = {
        message: "이거는 새로운 객체"
    }
    console.log(`f안에서 o.message="${o.message}"`);
}
let o = {
    message: "초기값"
};
console.log(`f를 호출하기 전: o.message="${o.message}"`);
f(o);
console.log(`f를 호출한 다음: o.message="${o.message}"`);
```
원시값과는 다르게, 매개변수로 객체를 전달하면 함수안에서도 같은 객체를 참조한다. 함수 안에서 새로 할당한 객체는 함수 안에서만 유효하다. 
```
f를 호출하기 전: o.message="초기값"
f안에서 o.message="이거는 새로운 객체"
f를 호출한 다음: o.message="f안에서 수정함"
```
1. 함수 호출 시, 전달되는 매개변수의 개수  
자바스크립트는 함수 호출 시, 매개변수의 개수와는 상관없이 같은 함수를 호출한다. 정해진 매개변수보다 적으면 undefined가 할당되고, 많으면...
```javascript
function f(x) {
    console.log("x=" + x);
}
f();
```
```
x=undefined
```
2. 확산 연산자(ES6)  
함수 선언 시, 매개변수는 반드시 마지막 매개변수여야 한다. ES5의 arguments보다 확산 연산자 쓰는 것을 권장.
```javascript
function makeName(lastname, ...names) {
    for (let i = 0; i < names.length; i++) {
        console.log(`${lastname} ${names[i]}`);
    }
}
makeName("jee", "joker", "batman");
```

```
jee joker
jee batman
```
3. 매개변수 기본값(ES6)  
함수 호출 시 매개변수 수가 모자르면 undefined로 할당된다. ES6는 기본값을 설정할 수 있다.
```javascript
function defaultValue(a, b="default1", c=10) {
    console.log(`a=${a} b=${b} c=${c}`);
}
defaultValue(1);
defaultValue(1,2);
defaultValue(1,2,3);
defaultValue();
```
```
a=1 b=default1 c=10
a=1 b=2 c=10
a=1 b=2 c=3
a=undefined b=default1 c=10
```
#### 메소드
객체의 프로퍼티인 함수를 메소드(method)라고 한다.
```javascript
const o = {
    name: 'Ilsoon',
    bark() { return 'Woof!';}
}

o.sleep = function() { return 'zzz'; }
```
#### this 키워드
