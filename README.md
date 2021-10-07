# jsExample
Record the latest javascript since Ecma Script 5

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
