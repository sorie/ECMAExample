
## Array
JavaScript Array 클래스는 리스트 형태의 고수준 객체인 배열을 생성할 때 사용하는 전역 객체. <br/>
침고 문헌 : https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array

#### 배열 예시
<pre>
<code>
let fruits = ['사과', '바나나'];
console.log(fruits.length);
</code>
</pre>

#### fill & map

<pre>
<code>
const getpanes = new Array(2).fill(null).map((_, index) => {
	const id = String(index + 1);
	return { title: `Tab ${id}`, key: id };
});
</code>
</pre>
