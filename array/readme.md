
## Array
JavaScript Array 클래스는 리스트 형태의 고수준 객체인 배열을 생성할 때 사용하는 전역 객체.

#### fill & map

<pre>
<code>
const getpanes = new Array(2).fill(null).map((_, index) => {
	const id = String(index + 1);
	return { title: `Tab ${id}`, key: id };
});
</code>
</pre>
