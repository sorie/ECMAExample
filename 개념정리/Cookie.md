## 쿠키

쿠키는 브라우저에 저장되는 작은 크기의 문자열, HTTP 프로토콜의 일부.
쿠키는 웹 서버에 의해 만들어진다. 
서버가 HTTP 응답 헤더(header)의 Set-Cookie에 내용을 넣어 전달하면, 
브라우저는 이 내용을 자체적으로 브라우저에 저장. 이게 바로 쿠키라 한다. 
브라우저는 사용자가 쿠키를 생성하도록 한 동일 서버(사이트)에 접속할 때마다 
쿠키의 내용을 Cookie 요청 헤더에 넣어서 함께 전달.

쿠키는 클라이언트 식별과 같은 인증에 가장 많이 쓰인다.
1. 사용자가 로그인하면 서버는 HTTP응답 헤더의 Set-Cookie에 담긴 "섹션 식별자(session identifier)"정보를 사용해 쿠키를 설정한다.
2. 사용자가 동일 도메인에 접속하려고 하면 브라우저는 HTTP Cookie헤더에 인증 정보가 담긴 고윳값(세션 식별자)을 함께 실어 서버에 요청을 보냅니다.
3. 서버는 브라우저가 보낸 요청 헤더의 섹션 식별자를 읽어 사용자를 식별한다.




참고문헌:
https://ko.javascript.info/cookie
나중에 참고할 자료 
gtag.js를 사용한 쿠키 및 사용자 식별
https://developers.google.com/analytics/devguides/collection/gtagjs/cookies-user-id?hl=ko



로컬 스토리지 

