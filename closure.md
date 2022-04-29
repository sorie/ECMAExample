
## 어휘적 환경(Lexical Environment)
- 내부 함수에서 못 찾은 변수를 외부 함수> 전역까지 올라가 찾아내는 정적인 환경.
- 코드가 적힌 순간 스코프가 정해진다. 이것을 렉시컬 스코프라고 한다.

<pre><code>
var name = 'Anne';
function log() {
  console.log(name);
}

function wrapper() {
  name = 'woo';
  log();
}
wrapper();
</code></pre>
<pre><code>
var name = 'Anne';
function log() {
  console.log(name);// 렉시컬 환경이기 때문에 함수 안에 변수가 없어 위로 올라가 'Anne'을 호출
}

function wrapper() {
  var name = 'Woo';
  log();
}
wrapper();
</code></pre>

## 동적 환경(Dinamic Environment)
순차적으로 선언된 변수에 따라 변수가 변하는 동적인 확경. (자바스크립트 환경에선 없는일)


## 클로저
- 함수와 렉시컬 환경의 조합, 함수가 생성될 당시의 외부 변수를 기억한다. 생성 이후에도 계속 접근 가능하다.
- 외부 함수의 변수를 기억하고 있다가 외부함수가 끝나더라도 외부함수의 변수를 호출할 수 있는 것으로 은닉화에 이용할 수 있다.

<pre><code>
function makeCounter() {
  let num = 0;// 은닉화 (num을 강제로 변경할 수 없음);
  
  return function () {
    return num++;
  };
}

let counter = makeCounter();

console.log(counter());
console.log(counter()); 
console.log(counter()); 
</code></pre>
