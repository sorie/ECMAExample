
## Location 프로퍼티
1. hash


## Location 메소드
1. assign

`
location.assign('vc.dial070.co.kr');
`

파라미터로 적은 URL로 리다이렉트 시킨다. 
history관리가 된다. (뒤로가기, 앞으로 가기 기능 구현 가능)

2. reload
현재 페이지에서 새로고침(refresh)을 한다. 
true 파라미터를 넘겨줄 때는 서버에서부터 새로고침 하고 파라미터를 넘기지 않거나, false로 넘길 때는 캐시에서부터 새로고침한다.

<code>
location.reload();
location.reload();

location.reload(true);
</code>

3. replace
assign 하고 하는 역할은 비슷하나 history 세션 관리가 되지 않는다. 
(뒤로가기, 앞으로가기 기능 구현 불가)

4. toString
URL를 string으로 반환해준다. 

* javascript 에서 method 는 함수로 된 property이다.

