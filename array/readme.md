
## Array
- JavaScript Array 클래스는 리스트 형태의 고수준 객체인 배열을 생성할 때 사용하는 전역 객체.
- 대괄호로 감싸진 형태로 각각의 index값을 갖는다. 길이를 알기 위해서 length를 사용한다. 
- 배열은 문자 뿐만 아니라, 숫자, 객체, 함수 등도 포함할 수 있다.
- push():배열 끝에 추가, pop(): 배열 끝에 제거, unshift(): 배열 앞에 추가, shift(): 배열 앞에 제거
- 반복을 위해서 사용한다.(index를 이용)

침고 문헌 : https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array <br>
참고 동영상 : https://www.youtube.com/watch?v=KF6t61yuPCY

### for ... of 
- 객체를 순회하는 for...in을 사용할 수 있는데 장점 보다 단점이 많다. index를 얻진 못하지만 for...of를 많이 사용한다. 

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
