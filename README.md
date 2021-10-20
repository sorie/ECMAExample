# ECMA script record

### ☘️ optional chaining & Template Literals
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

### ☘️ Promise & Async/await

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
