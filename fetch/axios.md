
### Axios GET
`axios.get(url,[,config])`<br/>
`response : json`
<br/>
#### param이 있는 경우
<pre>
<code>
axios.get("url", {
  params: {
    id: sorie
  }
})
.then((response) => {
// response  
}).catch((error) => {
// 오류발생시 실행
})
   
   
// async await 함수를 사용할 때, 

try {
const data = await axios.get("url", params: { id: 123 });
} catch {
// 오류 발생시 실행
}
</code>
</pre>
