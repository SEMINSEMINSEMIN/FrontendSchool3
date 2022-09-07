# TIL
## 팁
* 개발되어 있는 바퀴를 새로 만들지 마라

* https://paullabworkspace.notion.site/WHATWG-URL-s-origin-property-de2eed15f8ef4688ba4b089c9e7e2d0a
---
# HTML > 9. Forms
## 1. <Form\> 기본 속성
* 정보를 입력하는 영역
* 로그인 화면, 회원 가입
* 폼에 입력을 하고 제출시 데이터는 **서버로** 전송되고, 서버 처리 후 로그인 결과 화면 같은 다른 웹 페이지를 클라이언트에 전송
### 1.1 폼 동작 방식
1. 웹 페이지에 있는 form에 데이터를 입력합니다.
2. 웹 페이지 내 액션이 일어나게 되면 데이터는 웹 서버로 이동하게 됩니다.
3. 웹 서버는 데이터를 처리하기 위해 APP을 호출합니다. 이때 APP은 물리적으로 별도의 서버일 수도 있습니다.
4. 필요에 따라 APP은 DB로 데이터를 전송합니다. 이때 DB는 물리적으로 별도의 서버일 수도 있습니다.
5. DB에서 CRUD 작업이 일어나고 작업 결과를 APP으로, WEB으로 전송합니다.
6. 웹 서버는 받은 결과를 Client 브라우저에게 보냅니다.
7. 사용자 브라우저는 Response 받은 페이지를 렌더링하여 사용자에게 보여줍니다.
* Server: 서빙, 24시간 돌아가는 컴퓨터, 대부분 IP 연결이 돼있음
    * 로컬
        * 장점: 비용(전기세 + 인터넷)
        * 단점: 트래픽 확장이 어려움, 서버 확장이 어려움, 들어오는 트래픽 제한(bandwidth의 문제), 정전(클라우드 서버 같은 경우 UPS)
    * 클라우드
        * 장점: 서버 확장이 쉽다, 이전도 쉽다, IP를 할당 받거나, 도메인 연결하기 쉽고, HTTPS 인증도 쉽고..
        * 단점: 비용
* Web Server: 대부분 정적 파일을 서빙, 그러나 PHP 같은 프로그래밍 언어도 처리하긴 한다..
* App server: 두뇌 역할, 아이디 패스워드를 입력하면 웹서버를 지나쳐 앱 서버로 옴. 그럼 앱 서버가 db에서 로그인 정보 확인하고 맞으면 웹 서버에 로그인 성공 페이지를 반환하라고 함. 그럼 웹 서버가 클라이언트에게 반환하는 거임
* 참고: WAS = Web Server + App Server
* DB: 데이터 저장, 그런데 이미지는 DB에 저장하지 않고 이미지는 이미지 경로에만 저장함. 이미지는 스토리지에 저장돼있음!
    * 비효율적
    * DB의 목적(데이터 인덱싱)에 맞지 않음
    * 이를 해결하기 위해 API image server를 따로 두는 경우 있음(API server의 경우 브라우저와 직접 연결되어 있음)
* [API server](https://paullabworkspace.notion.site/API-API-Server-bab406c7453b4654a183a03bcf8dac96)
    * 애플리케이션을 서로 연결하여 서로 통신할 수 있다
    * 이미지를 직접 만들 필요 없고 저장할 필요 없이 API 서버에 URL을 보내면 API 서버가 이미지를 줌
* CRUD
    * Create: SQL(INSERT), method(POST)
    * Read: SQL(SELECT), method(GET)
    * Update: SQL(UPDATE), method(PUT)
    * Delete: SQL(DELETE), method(DELETE)
### 1.2 폼의 속성
1. action: 입력 값을 전송할 서버의 URL
2. method: 폼의 데이터를 **전송**할 **방법**을 정함
    * get: **URL**로 데이터를 **전달**할 때 사용(큰 파일은 get으로 전송하지 않음. id와 pw와 같은 민감 데이터x), 남들한테 URL 공유시(예를 들어 447번 게시물 공유) get만 가능하고 POST는 불가능하다(주소에 입력 내용이 나타나지 않으니까)
    * post: url에 **데이터가 노출되면 안되는 것일 때**, 파일을 올리거나 보안이 필요한 데이터 **전송**할 때, 주소에 입력 내용이 나타나지 않도록 함, 민감 데이터 o, 큰 데이터 o, ?post로 불러올 수도 있음?
    * 얘네는 HTTP의 get, post와 다름
## 2. <input\>
### 2.1 속성
* 용어만 알아두기: Shadow DOM
1. type
2. name
3. readonly
4. maxlength
5. minlength: 꼭 입력하게 하려고
6. required
7. autofocus
8. placeholder
9. pattern
## 3. <label\>
## 4. <select\>
## 5. <fieldset\>