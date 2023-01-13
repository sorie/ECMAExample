

## Reflow 특징
- 문서 내 요소의 위치와 도형을 다시 계산하기 위한 웹브라우저 프로세스의 이름
- 문서의 일부 또는 전체를 다시 렌더링 하는데 사용된다.
- 브라우저에서 사용자를 차단하는 작업이므로, 개발자가 리플로우 시간을 향상하는 방법을 이해하고 다양한 문서 속성<br>
(DOM 심도, CSS규칙 효율성, 다양한 스타아리 유형 변경)이 리플로우 시간에 미치는 영향을 이해하는 것이 중요하다.<br>
- 단일 요소를 리플로우하려면 상위 요소 및 이어지는 모든 요소도 리플로우해야 할 수 있다.
- 리플로우를 트리거할 수 있는 사용자 작업 및 가능한 DHTML변경사항은 매우 다양. 브라우저 창의 크기 변경, <br>
계산된 스타일이 수반되는 자바스크립트 메소드 사용, <br>
DOM에서 요소 추가 또는 삭제, 요소 클래스 변경은 리플로우를 트리거하는 몇가지 예이다. <br>
![image](https://user-images.githubusercontent.com/12015609/165247845-c7d3a642-ba54-4f76-9107-ffee2c1c430d.png)<br>
이미지 출처 : https://blinders.tistory.com/92

## Reflow, Repaint, Composite
layout 단계를 reflow, paint단계를 repaint, compositor thread단계를 composite라고 이해 하면 된다. <br>
만약 reflow가 발생했다면, repaint, composite도 연이어 발생 해야한다.<br>
![image](https://user-images.githubusercontent.com/12015609/165247882-67f02c89-e076-4eb1-bc06-fcc52162d93e.png)<br>
이미지 출처 : https://blinders.tistory.com/92<br>
만약 기존에 UI적인 어떤 변경점이 있었는데, 그 변경점에 의해 Reflow 단계부터 발생하던 과정을 Repaint부터 발생하게 할 수 있다면 <br>
불필요한 연산이 소거되는 것이고 이런 과정을 거치며 적은 리소스로 최대의 효과를 얻게 하는 것을 <b>최적화</b>라고 한다.<br><br>

- reflow :높이, 너비, 위치와 같이 화면의 구조적인 요소에 변경이 가해질때
- repaint: 구조외적으로 보여지는 요소가 변경될때 (색상 배경색들)
- composite: 현재는 opacity, transform 2가의 요소값에 의해 호출
 <br>
동일한 css요소도라도 브라우저별로 동작이 다르기때문에, 이를 잘 정리한 사이트 : <br>
https://csstriggers.com/

## 기본 크롬 퍼포먼스 사용하기 (체크사항)
1. 특정구간을 녹화한 후 그 구간을 분석해서 수행.
2. 2~3초 정도의 구간을 녹화하고 stop 
![image](https://user-images.githubusercontent.com/12015609/165247343-865a8a15-f64c-472a-a18a-e4d9a214446a.png) 
3. 애니메이션을 비롯, 이용자가 '편안하고 빠른 어플리케이션'이라는 것을 체감하기 위해서는 화면의 초당 프레임 수(FPS)가 높은 것이 필수. 
- 사용자들은 보통 웹이 60FPS이상으로 동작할 때 부드러움과 빠른 동작을 체감할 수 있다. 
4. 빨간 색 바가 보인다면 FPS가 너무 낮아서 사용자가 불편을 느낄 수 있음을 의미, 녹색 막대가 위에 위치할 수록 높은 FPS가 잘 분포하고 있음을 나타낸다.<br>
![image](https://user-images.githubusercontent.com/12015609/165247469-dc3877fc-a9b4-45f9-beff-00ac74ffca44.png)<br>
5. 바로 아래 부분은 CPU 사용량 분포이다. 주황, 보라, 초록 등 색상으로 뒤섞인 바가 크고 높게 보일수록, CPU를 많이 사용하고 있다.<br>
(그만큼 성능이 좋지 않다는 의미이다.)<br>
![image](https://user-images.githubusercontent.com/12015609/165250168-d6cdaae0-432c-4cce-9ac4-89191b519ff2.png)<br>
6. 위그림은 CPU 성능 색과 같게 구성된 원형 그래프이다. 전체 연산 시간에서 scripting, rendering, painting, 기타 항목들이 얼만큼 처리 시간을 가졌는지 보여준다.
7. 주황색이 보라색 위에 있으면 스크립팅이 렌더링보다 더 많은 CPU를 사용했음을 알 수 있다.
8. 분포에 직접 마우스를 가져다 대면 그 시점에서의 화면을 보여준다. 마우스를 움직여 보면서 애니메이션이 어떻게 흘러가는지 수동으로 관찰 할 수 있고 이것을 scrubbing이라고 말한다.
9. 녹색 사각형들의 수평 분포에서 FPS수치를 확인 할 수 있다.
![image](https://user-images.githubusercontent.com/12015609/165251175-f1517950-5a26-4161-bfa6-07047569aef3.png)
10. 성능확인을 위해 마우스 휠이나 막대를 옮겨 좁히고 하단의 main섹션을 확장한다.
- 확장햇을 때 나오는 차트를 flame차트라고 부르며, x축은 시간을, y축으로 쌓인 막대들은 콜스텍을 시각적으로 보여준다.
![image](https://user-images.githubusercontent.com/12015609/165252431-d4d6101a-6b25-4dab-9279-0e0b1d75a9bc.png)
11. 막대중 이벤트 막대를 클릭하면 해당 이벤트를 추적할 수 있다. 
- 추척하다보면 정확히 어느 함수의 어느 행이 문제를 발생시키는지 알 수 있다.
- 해당 코드가 다른 코드들과 비교해서 많은 시간을 잡아 먹는지 확인 한다.
- 예를 들어 top과 같이 요소의 기하학적인 영향을 주는 css속성을 변경하는 것은 강제 레이아웃을 발생시키기 때문에 많은 시간을 뺏는다.
참고 사이트 : https://codingmoondoll.tistory.com/entry/%ED%81%AC%EB%A1%AC-%EA%B0%9C%EB%B0%9C%EC%9E%90-%EB%8F%84%EA%B5%AC%EC%9D%98-Performance-%ED%83%AD-%EB%8B%A4%EB%A3%A8%EA%B8%B0-%EA%B8%B0%EB%B3%B8%ED%8E%B8 <br>
https://developer.chrome.com/docs/devtools/evaluate-performance/



## 렌더링 성능 최적화

### virture DOM 
dom에 추상화 개념을 더해 만든 dom이다. 빈번한 reflow와 repaint를 덜 발생시켜 최적의 성능을 보인다.

### What forces layout / reflow
강제로 한줄한줄 reflow 시키는 동작들이 있다.
- focus()
- scrollBy()
- innerText()
https://blog.drakejin.me/React-VirtualDOM-And-Repaint-Reflow/

#### 성능 튜닝방법 예시
1. 모범 사례 레이아웃 기술 사용
인라인 스타일은 html 다운로드 될 때 레이아웃에 영향을 미치고 추가 리플로우를 트리거 한다.
파서가 셀 크기를 계산하기 위해서는 두번 이상의 패스가 필요하기 때문에 테이블은 비용이 많이 든다. table-layout: fixed를 하면 좋다.
2. CSS 규칙 수 최소화
사용하는 규칙이 적을수록 리플로우가 빨라진다. 가능한 경우 복잡한 CSS 선택기도 피해야 한다.
Bootstrap과 같은 프레임워크를 사용하는 경우 특히 문제가 될 수 있다. Unused CSS , uCSS , grunt-uncss 및 gulp-uncss 와 같은 도구는 스타일 정의 및 파일 크기를 크게 줄일 수 있다.
.
.
.
7. 일괄 업데이트 요소
단일 작업으로 모든 DOM 요소를 업데이트하여 성능을 향상시킬 수 있다. 이 간단한 예는 세 가지 리플로우를 유발한다.

<pre>
<code>
var myelement = document.getElementById('myelement');
myelement.width = '100px';
myelement.height = '200px';
myelement.style.margin = '10px';
</code>
</pre>

유지 관리가 더 쉬운 단일 리플로우로 이를 줄일 수 있다.

<pre>
<code>
var myelement = document.getElementById('myelement');
myelement.classList.add('newstyles');
.newstyles {
	width: 100px;
	height: 200px;
	margin: 10px;
}
</code>
</pre>

DOM을 터치해야 하는 시간을 최소화할 수도 있다. 이 글머리기호 목록을 만들고 싶다고 가정해 보겠다.

<pre>
<code>
항목 1
항목 2
항목 3
</code>
</pre>

각 요소를 한 번에 하나씩 추가하면 최대 7개의 리플로우가 발생한다. <ul>가 추가될 때 1개, 각각에 대해 <li>3개, 텍스트에 대해 3개가 추가된다. 그러나 DOM 조각을 사용하여 단일 리플로우를 구현하고 먼저 메모리에 노드를 구축할 수 있다.

<pre>
<code>
var
	i, li,
	frag = document.createDocumentFragment(),
	ul = frag.appendChild(document.createElement('ul'));

for (i = 1; i <= 3; i++) {
	li = ul.appendChild(document.createElement('li'));
	li.textContent = 'item ' + i;
}

document.body.appendChild(frag);
</code>
</pre>
 

참고 사이트
https://www.sitepoint.com/10-ways-minimize-reflows-improve-performance/





