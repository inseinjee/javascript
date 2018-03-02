## 리터럴과 변수, 상수, 데이터 타입
#### 문자열
- 문자열 템플릿 : 문자열의 정해진 위치에 값을 채워넣는 방법(ES6)
<code>
<pre>
let paymentMethod = "신용카드";
const message = `${paymentMethod}로 결제하시겠습니까?`
</pre>
</code>


## 함수
<code>
<pre>
function getMyBot() {
    console.log("This is getMyBot function");
    return "Hello World";
}
</pre>
</code>

#### 호출과 참조
- getMyBot()은 함수의 바디를 실행하는 호출이고, getMyBot은 참조이며 함수를 실행하지 않는다.  
- 다른 이름으로 함수 호출
<code>
<pre>
const temp = getMyBot;
temp()
</pre>
</code>



