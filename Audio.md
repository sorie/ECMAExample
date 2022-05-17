## 오디오 worklet 프로세서의 구조
오디오 worklet 프로세서는 다음을 포함하는 JavaScript 모듈입니다:

- 오디오 프로세서를 정의하는 JavaScript 클래스. 이 클래스는 AudioWorkletProcessor 클래스를 상속받습니다(extends).
- 오디오 프로세서는 반드시 process() 메서드를 구현해야 하는데, 이 메서드는 들어오는 오디오 데이터를 받고 프로세서에 의해 조작된 데이터를 출력에 넣습니다.
- 이 모듈은 registerProcessor()를 호출함으로써 새로운 오디오 worklet 프로세서를 등록하는데, 등록할 때 오디오 프로세서의 이름과 프로세서를 정의하는 클래스를 인자로 전달합니다.



