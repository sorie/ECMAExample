# ECMA script record

## ☘️ 화살표 함수 =>
#### => 기호로 함수를 축약해서 표현하는 방식이다. 
✔️ 자신의 this, arguments을 바인딩 하지 않고 전역의 this를 가리킨다.<br/><br/>
화살표 함수를 이용하여 클로저를 활용할 수 있다. 
예를 들어 ,
<pre><code>
function outer(a) {
  return function inner(b) {
    return a + b;
  }
}
outer(10)(20);
</code></pre>
를 아래와 같이 직관적이고 간략하게 바꿀 수 있다.
<pre><code>
const outer = (a) => (b) => a + b;
outer(10)(20);
</code></pre>

## ☘️ 단축평가(short-circuit evaluation)

#### && 연산자를 사용해 if문을 대체할 수 있다.
<pre><code>
let done = true; 
let message = ''; 
if (done) message = '완료'; 
message = done && '완료';
</code></pre>

####  반대로 조건의 결과값이 false일 때 무언가 동작하게 하고 싶다면 || 연산자를 사용해 if문을 대체
<pre><code>
let done = false; 
let message = ''; 
if (!done) message = '아직'; 
message = done || '아직';
</code></pre>

####  변수가 null, undefined가 아닌지 확인한 후에 하위 속성을 참조할 때, 단축 평가를 통해 에러를 방지할 수도 있다.
<pre><code>
let el = null; 
let val = el && el.val;
</code></pre>

### ♦️  optional chaining & Template Literals
"?." => optional chaining ES11부터 도입된 연산자이다. <br/>
표기 방식은 ?. 이런식으로 쓰는데, <br/>
왼쪽 피연산자가 null이나 undefined면 undefined를 반환하고, 그렇지 않으면 오른쪽의 프로퍼티 참조를 실행해 반환한다. 
<br/><br/>
"\`test : ${param}\`" => Template Literals<br/>
문자와 파라미터 값을 함께 사용하여 번거롭게 'test : ' + param 이라고 쓰지 않아도 된다.<br/>

#### Before
<pre><code>
ucEngine.webSocketSend( [ 'ping.sys.conn', [ 'openvc', GLOBAL.getEncData( 'device.uuid' ) ] ], 
'##### CLIENT CONSOLE MSG : [ novideo , id = ' + GLOBAL.getMyID()  + ', restartICEConnect param null = ' + conftype + ', video of selectdevice = ' + selectdevice?selectdevice.video.label:'none' + '] #####' );
</code></pre>

#### After
<pre><code>
ucEngine.webSocketSend( [ 'ping.sys.conn', [ 'openvc', GLOBAL.getEncData( 'device.uuid' ) ] ], 
`##### CLIENT CONSOLE MSG : [ novideo , id = ${GLOBAL.getMyID()}, restartICEConnect param null = ${conftype}, video of selectdevice = ${selectdevice?.video?.label}] #####` );
</code></pre>
<br/>

### null 병합 연산자(nullish coalescing)
null 병합 연산자도 ES11부터 도입되었다. ?? 이렇게 사용하는데, 왼쪽 피연산자가 null이나 undefined면 오른쪽 피연산자를 반환하고, 아닌 경우에는 왼쪽의 피연산자를 반환한다. 변수에 기본값을 설정할 때 유용하게 쓸 수 있다.

<pre><code>
let str = null ?? 'default'; 
console.log(str); // 'default'
</code></pre>

기존처럼 || 연산자로 기본값을 설정했을 때를 생각해보자. ||는 왼쪽 피연산자가 falsy값이면 오른쪽 피연산자를 반환했는데, falsy값으로 취급되는 0 이나 ''(빈문자열)을 넣으면  예상치 못한 결과가 나오기도 했다. 하지만 ?? 연산자를 사용하면 이런 경우를 방지할 수 있다.

<pre><code>
let str = '' || 'default'; 
console.log(str); // 'default' 
let str = '' ?? 'default'; 
console.log(str); // ''
</code></pre>
출처: https://joooing.tistory.com/entry/단축평가-옵셔널체이닝연산자-null병합연산자?category=907322 [joooing]

## ☘️ Promise & Async/await

#### Example
<pre><code>
//bad code
function displayUser() {
  fetchUser()
  .then((user) => {
    fetchProfile(user)
    .then((profile) => {
      updateUI(user, profile);
    });
  });
}

//good code
async function displayUser() {
  const user = await fetchUser();
  const profile = await fetchProfile(user);
  updateUI(user, profile);
}
</code></pre>

`
await 와 Promise#then을 혼동하지 마세요
두 개 이상의 프러미스를 동시에 wait 하고 싶다면, 
Promise#then을 사용하고 순차적으로 실행시키고 싶다면 async/await을 사용한다.
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/async_function
`
#### Example
<pre><code>
async function getApple() {
    await delay(1000);
    return '사과';
}
async function getBanana() {
    await delay(1000);
    return '바나나';
}

async function pickFruits() {
    const applePromise = getApple();//프로미스생성
    const bananaPromise = getBanana();
    const apple = await applePromise;
    const banana = await bananaPromise;
    return `${apple} + ${banana}`;
}

pickFruits().then (console.log);//전체 소요시간 1초만 걸립니다.
//사과 + 바나나 출력

대채 useful Promise APIs 
function pickAllFruits() {
    return Promise.all([getApple(), getBanana()])
    .then(fruits => fruits.join(' + ')
    );
}
pickAllFuits().then(console.log);//사과 + 바나나 출력

function pickOnlyOne(){
     return Promise.race([getApple(), getBanana()]);   
}

pickOnlyone().then(console.log);//바나나만 출력됨.
</code></pre>
