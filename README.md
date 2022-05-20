# ECMAscript 
“ECMAScript is a standard.”

“JavaScript is a standard.”

“ECMAScript is a specification.”

“JavaScript is an implementation of the ECMAScript standard.”

“ECMAScript is standardized JavaScript.”

“ECMAScript is a language.”

“JavaScript is a dialect of ECMAScript.”

“ECMAScript is JavaScript.”

“In 『What’s the difference between JavaScript and ECMAScript?』 of Michael Aranda”

ECMAScript는 Ecma 인터내셔널에 의해 제정된 ECMA-262 기술 규격에 의해 정의된 범용 스크립트 언어이며
Ecma인터내셔널은 정보 통신에 대한 표준을 제정하는 비영리 표준화 기구입니다.

## ♦️ 둘의 관계 (js vs es)
- JS엔진을 가진 브라우저 마다 지원되는 ECMAScript가 다릅니다.
- JavaScript 엔진이 최신 ECMAScript의 사양을 준수하는지 아닌지는 JavaScript 엔진을 담당하는 회사나 조직(Google, Mozilla, Microsoft 등)의 업데이트에 따라 달려있습니다.
- 새 버전의 ECMAScript가 나오면 JavaScript 엔진을 통째로 업데이트하지는 않고, 새로 추가된 ECMAScript 기능을 점진적으로 업데이트합니다.

## ☘️ 기초 문법 
## 화살표 함수 =>
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

## 단축평가(short-circuit evaluation)

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

#### 변수가 null, undefined가 아닌지 확인한 후에 하위 속성을 참조할 때, 단축 평가를 통해 에러를 방지할 수도 있다.
<pre><code>
let el = null; 
let val = el && el.val;
</code></pre>

### optional chaining & Template Literals
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


## map && filter 

<pre><code>
const devices = [
                  {"deviceId":"default","kind":"audioinput","label":"기본값 - 마이크(Realtek Audio)","groupId":"2fc5a70356cd629dff0f57c8c5b420757f34b7f60a40184617607bdf125025f8"},
                  {"deviceId":"communications","kind":"audioinput","label":"커뮤니케이션 - 마이크(Realtek Audio)","groupId":"2fc5a70356cd629dff0f57c8c5b420757f34b7f60a40184617607bdf125025f8"},{"deviceId":"80f28f21743218d1430300452892a9272426095e48d4ddd344bef16a57e2d7cb","kind":"audioinput","label":"마이크(Realtek Audio)","groupId":"2fc5a70356cd629dff0f57c8c5b420757f34b7f60a40184617607bdf125025f8"},{"deviceId":"7fb6410182a2ef6910e68e942dfa9bd4f29350f391599099ed1563ab6e7ac185","kind":"videoinput","label":"Integrated Webcam (0bda:5689)","groupId":"80117ee788b9447605cce20ce90cefec3f387bb62f2df256e2a1559dac667d41"},{"deviceId":"7fb6410182a2ef6910e68e942dfa9bd4f29350f391599099ed1563ab6e7ac185","kind":"videoinput","label":"test Webcam (0bda:5689)","groupId":"80117ee788b9447605cce20ce90cefec3f387bb62f2df256e2a1559dac667d41"},
                  {"deviceId":"default","kind":"audiooutput","label":"기본값 - 스피커 / 헤드폰(Realtek Audio)","groupId":"2fc5a70356cd629dff0f57c8c5b420757f34b7f60a40184617607bdf125025f8"},
                  {"deviceId":"communications","kind":"audiooutput","label":"커뮤니케이션 - 스피커 / 헤드폰(Realtek Audio)","groupId":"2fc5a70356cd629dff0f57c8c5b420757f34b7f60a40184617607bdf125025f8"},{"deviceId":"b1ef42095920cde890023686cc26c6792fae6fadcc3e1dc195905097adb3d8a4","kind":"audiooutput","label":"스피커 / 헤드폰(Realtek Audio)","groupId":"2fc5a70356cd629dff0f57c8c5b420757f34b7f60a40184617607bdf125025f8"}
                ];

const newdevices = devices.filter(item => item.kind === 'videoinput').map(item => item.label);
console.log(`dev test devices : ${JSON.stringify(newdevices)}`);
//dev test devices : ["Integrated Webcam (0bda:5689)","test Webcam (0bda:5689)"]
</code></pre>

## Basic

#### Object Destructuring

<pre><code>
const person = {
  name = 'Julia',
  age = 20,
  phone: '0102222222'
};

//bad code
function displayPerson(person){
  displayAvatar(person.name);
  displayName(person.name);
  displayProfile(person.name, person.age);
}

fucntion displayPerson(person) {
  const { name, age } = person;
  displayAvatar(name);
  displayName(name);
  displayProfile(name, age);
}
</code></pre>

#### Array Destructuring

<pre><code>
// ES6 Destructuring
const arr = [1, 2, 3];

// 배열의 인덱스를 기준으로 배열로부터 요소를 추출하여 변수에 할당
// 변수 one, two, three가 선언되고 arr(initializer(초기화자))가 Destructuring(비구조화, 파괴)되어 할당된다.
const [one, two, three] = arr;
// 디스트럭처링을 사용할 때는 반드시 initializer(초기화자)를 할당해야 한다.
// const [one, two, three]; // SyntaxError: Missing initializer in destructuring declaration

console.log(one, two, three); // 1 2 3
// 코드 출처 : https://poiemaweb.com/es6-destructuring
</code></pre>

##### 중첩객체의 경우
<pre><code>
const person = {
  name: 'Lee',
  address: {
    zipCode: '03068',
    city: 'Seoul'
  }
};

const { address: { city } } = person;
console.log(city); // 'Seoul'
// 코드 출처 : https://poiemaweb.com/es6-destructuring
</code></pre>

#### Spread Syntax
<pre><code>
//Spread Syntax - Object
const item = { type: 'shirts', size : 'M' };
const detail = { price: 20, made: 'Kores', gender: 'M' };

//bad code 
item['price'] = detail.price;

//bad code
const newObject = new Object;
newObject['type'] = itme.type;
newObject['size'] = itme.size;
newObject['price'] = itme.price;
newObject['made'] = itme.made;
newObject['gender'] = itme.gender;

//bad code
const newObject2 = {
  type: item.type,
  size: item.size,
  price: detail.price,
  made: detail.made,
  gender: detail.gender,
};

//good code 
const chirt0 == Object.assign(item, detail);

//better code 
const shirt = {...item, ...detail, price: 40 };

//spread syntax - arrray
let fruits = ['수박', '귤', '바나나'];

//fruits.push
fruits = [...fruits, '딸기'];

//fruits.unshift
fruits = ['딸기', ...fruits];

const fruits2 = ['메론','피치', '파인애플'];
let combined = fruits.concat(fruits2);
combined = [...fruits, ...fruits2);
            
</code></pre>

## Promise & Async/await

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

### promise.all
promise는 동기지만 .then을 사용하면 비동기가 된다. 병렬 형식의 비동기로 호출하고 싶다면 promise.all을 사용한다. 즉 순서대로 실행되지만 앞에 함수가 끝나는 것을 기다려주지 않는다.
그리고 마지막 함수가 끝날때까지 기다리다가 반환한다.
- 중간에 어떤 함수가 에러가 났을때 즉시 에러를 반환한다. 예를 들어, await으로 각각을 실행했을때 첫번째 함수의 시간을 전부 채우고 에러를 반환하는 반면 promise.all은 에러즉시 반환한다. 그리고 다른 함수가 실행되기 전에 에러 발생시 즉시 반환되는 것이다.

### Promise.allSettled()
- 메서드는 주어진 모든 프로미스를 이행하거나 거부한 후, 각 프로미스에 대한 결과를 나타내는 객체 배열을 반환.
- 일반적으로 서로의 성공 여부에 관련 없는 여러 비동기 작업을 수행해야 하거나, 항상 각 프로미스의 실행 결과를 알고 싶을 때 사용.

https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise/allSettled



