
## Number, Math
### toString() : 문자로 변경
### toString(2/16) 10진수를 2진수/16진수로 변경
### Math 
#### Math.PI; //3.14159.....
#### Math.ceil() : 올림
#### Math.floor() : 내림
#### Math.round() : 반올림
#### 소수점 자릿수
<pre><code>
let userRate = 30.1234;
//요구사항 : 소수점 둘째자리 까지 표현(셋째 자리에서 반올림)
Math.floor(userRate * 100)/100
</code></pre>
#### Math.random() 0~1사이 무작위 숫자 생성.
<pre><code>
//1~100사이 임의의 숫자를 뽑고 싶다면?
Math.floor(Math.random()*100)+1
</code></pre>
#### Math.max(), Math.min (최대값,최소값 구함)
#### Math.abs(0 : 절대값
#### Math.pow(n,m) : 제곱 
#### Math.sqrt() : 제곱근
### toFixed() : 소수점 자릿수 변경
### isNaN() : Number 확인.
<pre><code>
let x = Number('x'); //NaN
x === NaN //false
x === NaN //false
NaN === NaN //false
isNaN(x) //true
isNaN(3) //false
</code></pre>
### parseInt()
<pre><code>
let margin = '10px';
parseInt(margin); //10
Number(margin); //NaN

let redColor = 'f3';
parseInt(redColor); //NaN
psrseInt(redColor, 16); // 243 //16진수로 변환
parseInt('11',2) //3 //2진수로 변환
</code></pre>
### parseFloat() : parseInt와 동일하지만 부동소수점을 반환한다.

## String
- 특정 위치의 접근가능.
### length : 문자열 길이
### toUpper(), toLower()
### str.indexOf(text)
### str.slice(n, m)
### str.substring(n,m)
- 음수 허용하지 않는다.

### str.substr(n, m)
- m개를 가져온다.

### str.trim(), str.repeat(n) 
- n번 반복한다.

