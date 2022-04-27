
## Array
- JavaScript Array 클래스는 리스트 형태의 고수준 객체인 배열을 생성할 때 사용하는 전역 객체.
- 대괄호로 감싸진 형태로 각각의 index값을 갖는다. 길이를 알기 위해서 length를 사용한다. <br/>
침고 문헌 : https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array

### for ... of 
for...in을 사용할 수 있는데 장점 보다 단점이 많다. index를 알순 없지만 for...of를 많이 사용한다. 

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
