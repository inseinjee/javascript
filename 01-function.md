## 함수
```
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
```
function f(o) {
    o.message = `f안에서 수정함 (이전 값: '${o.message}')`;
}
let o = {
    message: "초기값"
};
console.log(`f를 호출하기 전: o.message="${o.message}"`);
f(o);
console.log(`f를 호출한 다음: o.message="${o.message}"`);
```
```
f를 호출하기 전: o.message="초기값"
f를 호출한 다음: o.message="f안에서 수정함 (이전 값: '초기값')"
```
