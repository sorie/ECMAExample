## blur
blur 이벤트는 엘리먼트의 포커스가 해제되었을때 발생. 이 이벤트와 focusout 이벤트의 가장 다른점은 focusout 은 이벤트 버블링이 발생. <br/>
https://developer.mozilla.org/ko/docs/Web/API/Element/blur_event

<pre>
<code>
$(window).on("blur", (e) => {//포커스되지 않은 경우.(ex: 다른탭으로 이동시, 화면이 아닌 다른 곳을 클릭한 경우 )
    closing_window = true; 
    if (!document.hidden) { //when the window is being minimized 
        closing_window = false; 
    } 
    $(window).on('resize', function (e) { //when the window is being maximized 
        closing_window = false; 
    }); 
    // $(window).off('resize'); //avoid multiple listening
});
window.addEventListener('beforeunload', function (e) { 
    e.preventDefault(); 
    console.log('dev info closing_window: ' + closing_window);
    //confid가 존재하는 경우만 leaveRoom 되도록 수정.
    if(closing_window && GLOBAL_MODULE.getConfID()){
        this.send('leaveRoom'); 
    }
    // e.returnValue = '나가시는게 맞나요?'; //재확인메세지 
}.bind(this)); 
</code>
</pre>

## Window: beforeunload
beforeunload 이벤트는 문서와 그 리소스가 언로드 되기 직전에 window에서 발생. 이벤트 발생 시점엔 문서를 아직 볼 수 있으며 이벤트도 취소 가능. <br/>
예시 : 탭닫기, 새로고침 등의 해당 document가 없어지는 것을 체크 함. <br/>
https://developer.mozilla.org/ko/docs/Web/API/Window/beforeunload_event

