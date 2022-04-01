


#### fill & map

<pre>
<code>
const getpanes = new Array(2).fill(null).map((_, index) => {
	const id = String(index + 1);
	return { title: `Tab ${id}`, key: id };
});
</code>
</pre>
