---
contents:
  lang: yaml
  code: >+
    openapi: 3.1.0

    info:
      title : LGE Membership API
      version: v1
    servers:
      - url: https://qt-{CNTRY}.m.lgaccount.com/emp/v2
        description: QA url
      - url: https://{CNTRY}.m.lgaccount.com/emp/v2
        description: OP url
    tags:
      - name: Overview
        x-displayName: 소개
        description: |
          
          LGE Membership Platform은 OAuth2.0표준을 따르는 API를 활용하여 서비스 사용자와 ThinQ 디바이스 사용자를 통합할 수 있습니다. 또한 사용자로부터 권한을 위임받아 ThinQ Platform에 사용자 디바이스와 관련된 작업을 요청할 수 있습니다. 
          
          <b><h2>What is LG EMP?</h2></b>
          <hr></hr>
          LG Electronics Enterprise Membership Platform (이하 EMP)는 LG전자와 관련된 서비스를 제공하기 위한 회원 관리 플랫폼입니다. EMP는 LG 계정 혹은 LG 계정과 연동하는 3rd party 계정으로 로그인하여, LG전자 혹은 LG전자 파트너가 제공하는 서비스를 이용할 수 있도록 해줍니다.  
          
          <b><h3>Key Features</h3></b>
          EMP는 OAuth 2.0 프로토콜 중 Authorization Code Grant Type에 기반한 인증 프레임워크를 제공합니다. 여러분의 서비스는 EMP가 제공하는 API를 호출하여 다음을 요청할 수 있습니다.  
            - LG 계정 연동 로그인 (EMP 웹로그인)
            - 액세스 토큰, 리프레쉬 토큰 발급
            - 액세스 토큰 갱신 발급
          
          ><b><h3>Authorization Code Grant Type</h3></b>
          EMP는 OAuth 2.0의 다양한 권한 부여 방식 중, Authorization Code Grant Type을 사용합니다. 이 방식은 여러분의 서비스와 같이 웹 서버에서 돌아가는 애플리케이션에 주로 사용되는 방식으로, 웹 브라우저(user-agent)와의 인터랙션이 포함됩니다. 서비스가 EMP에 로그인 프로세스를 요청하면 EMP는 사용자의 웹 브라우저를 로그인 페이지로 이동시켜 로그인을 진행하고, 로그인이 완료되면 사용자의 웹 브라우저를 약속된 Redirect URI로 이동시켜줍니다. 이때, EMP는 Redirect URI에 인증 코드 (Authorization Code)를 포함하여 리다이렉션합니다.<br><br>
          서비스는 이 인증 코드로 EMP에 액세스 토큰을 요청하여 발급받고, 액세스 토큰을 제시하여 사용자의 자원에 접근할 수 있습니다.
          
          <b><h3>Benefits</h3></b>
          ThinQ 서비스 사용자와 제공자에게 EMP는 다음과 같은 편의를 제공합니다.
            - <b>서비스 사용자</b>
              - 디바이스를 ThinQ 앱에서 한 번만 등록하면, LG전자 혹은 LG전자 파트너가 제공하는 다양한 서비스를 이용할 수 있습니다.
            - <b>서비스 제공자</b>
              - EMP와 ThinQ Platform에 연동하여, 전 세계 수많은 ThinQ 디바이스 사용자에게 서비스를 제공할 수 있습니다.
          
          <img src="https://thinq.developer.lge.com/download_file/view_inline/12981/" style="width:70%; padding:20px;"/>
          
          <b><h3>Basic Concept</h3></b>
          여러분이 에어컨을 제어하는 서비스를 제공한다고 가정해 봅시다. ThinQ 에어컨 사용자가 여러분의 서비스를 이용하기까지 어떤 과정이 필요한지 다음과 같이 확인할수 있습니다.

          <b>A. 에어컨을 ThinQ Platform에 등록 (User/ LG ThinQ 앱)</b>
          1. 사용자가 LG전자가 제공하는 ThinQ 앱에서 LG 계정 연동 계정으로 가입하고 로그인합니다. 
          2. 사용자가 에어컨을 등록합니다.
          <br>→ 사용자의 에어컨이 ThinQ Platform에 등록됩니다.
          
          <b>B. 서비스 로그인 및 액세스 토큰 발급 (User/ Service/ LG EMP)</b>
          1. 사용자가 서비스에 로그인을 요청합니다.
          2. 서비스는 EMP에 로그인을 요청합니다. (→ EMP는 사용자의 웹브라우저를 EMP가 제공하는 로그인 페이지로 이동시키고 사용자와 인터랙션 하여 로그인을 진행합니다.)
          3. 사용자가 로그인합니다. (→ EMP는 사용자의 웹브라우저를 서비스로 돌려주고 인증 코드를 발급합니다.)
          4. 서비스는 EMP에 인증 코드를 전달하고 액세스 토큰을 요청합니다.
          5. EMP는 서비스에 액세스 토큰을 발급합니다.
          <br>→ 서비스는 EMP로부터 액세스 토큰을 발급받습니다.
          
          <b>C. 에어컨 제어 (User/ Service/ LG ThinQ Platform)</b>
          1. 사용자가 서비스에서 에어컨 제어를 요청합니다.
          2. 서비스는 ThinQ Platform에 에어컨 제어를 요청합니다. 요청 시, EMP가 발급해준 액세스 토큰을 전달해야 합니다.
          3. ThinQ Platform은 EMP와 통신하여 다음을 검사합니다.
            - 사용자에 대한 요청 정보
            - 유효한 액세스 토큰 여부 
          4. 액세스 토큰이 유효하다면, ThinQ Platform은 에어컨을 제어하고 서비스에 결과를 응답합니다.
          5. 서비스는 사용자에게 결과를 피드백합니다.
          <br>→ 서비스는 액세스 토큰으로 ThinQ Platform에 사용자의 에어컨 제어를 요청합니다.

          <b><h4>Interaction Between Service, EMP, and ThinQ Platform</h4></b>
          위 과정을 서비스 입장에서 간략히 설명하면 다음과 같습니다.

          1. 서비스는 EMP에 다음을 요청합니다. 
            - 사용자가 로그인할 수 있도록 로그인 프로세스를 요청합니다.
            - 사용자가 로그인하면 EMP로부터 액세스 토큰을 발급받습니다.
          2. 서비스는 ThinQ Platform에 사용자의 디바이스와 관련된 작업을 요청합니다. 요청 시, EMP가 발급한 액세스 토큰을 반드시 전달해야 합니다. 
            - 예) ThinQ Connect API를 통해 ThinQ Platform에 요청할 수 있는 작업
              - 사용자가 등록한 디바이스 리스트를 조회
              - 해당 에어컨의 현재 상태를 조회 (예: 목표 온도 조회)
              - 해당 에어컨에 제어 명령을 전달 (예: 에어컨 온도 1도 올리기)
              - 해당 에어컨의 푸쉬 알림을 구독 (예: 필터 교체 알림) 
          
          <b><h2>Basic Workflow</h2></b>
          <hr></hr>
          서비스와 EMP 간의 인터랙션은 OAuth 2.0 프로토콜을 따릅니다. 
          <b><h3>OAuth 2.0 Protocol</h3></b>
          <b><h4>OAuth 2.0 Basic</h4></b>
          OAuth 2.0 프로토콜을 구성하기 위해서는 기본적으로 다음 4가지 역할이 필요합니다. 

          - <b>리소스 소유자 (사용자)</b>
            - 리소스 서버 안에 보호된 자신의 자원을 이용할 수 있도록 권한을 부여하는 주체입니다.
            - 애플리케이션 사용자를 의미합니다.
          - <b>애플리케이션</b>
            - 인증 서버에 인증을 요청하여 액세스 토큰을 발급받고, 리소스 서버에 액세스 토큰을 제시하여 리소스 소유자의 자원을 요청합니다.
            - 포괄적인 의미의 응용 프로그램을 일컬으며 여러분의 서비스가 이에 해당됩니다.
          - <b>인증 서버 (Authorization Server)</b>
            - 애플리케이션이 리소스 소유자로부터 권한을 부여받았음을 인증하고, 애플리케이션에게 액세스 토큰을 발급해주는 서버입니다.
          - <b>리소스 서버 (Resource Server)</b>
            - 애플리케이션에게 사용자의 자원을 제공하는 서버입니다.
            - 애플리케이션이 유효한 액세스 토큰으로 요청한 경우에만, 요청을 수락하고 사용자의 자원을 제공합니다.
          
          이들이 상호 작용하는 기본 흐름은 다음과 같습니다.
          1. <b>Request Authorization</b>
            - 애플리케이션이 리소스 소유자(사용자)에게 권한을 요청합니다.
          2. <b>Grant Authorization</b>
            - 사용자가 권한을 승인하면, 애플리케이션은 권한을 부여받습니다.
          3. <b>Request Access token with Authorization Grant</b>
            - 애플리케이션은 부여된  권한으로 인증 서버에 액세스 토큰을 요청합니다.
          4. <b>Issue Access Token</b>
            - 인증 서버는 애플리케이션에 액세스 토큰을 발급합니다.
          5. <b>Request Protected Resource with  Access Token</b>
            - 애플리케이션은 액세스 토큰을 제시하여 리소스 서버에 해당 사용자의 자원을 요청합니다.
          6. <b>Serve Protected Resource</b>
            - 액세스 토큰이 유효하다면, 리소스 서버는 애플리케이션에 사용자의 자원을 제공합니다.

          <b><h3>EMP Basic Workflow</h3></b>
          OAuth 2.0의 EMP의 역할과 ThinQ Platform의 역할은 다음과 같습니다.
          <table>
          <tr><th> OAuth 2.0 </th><th width="220"> Service/ EMP/ ThinQ Platform </th><th> Description </th></tr>
          <tr><td> 애플리케이션 </td><td style=color:red> Service (Partner Server) </td><td> 
            - 여러분의 서비스가 이에 해당합니다. </td></tr>
          <tr><td> 리소스 소유자 (사용자) </td><td style=color:red> User </td><td> 
            - ThinQ 디바이스의 소유자이자 서비스 사용자입니다.<br>
            - ThinQ 앱을 통해 디바이스를 등록하고, 서비스가 이 디바이스 정보를 이용할 수 있도록 권한을 부여합니다.  </td></tr>
          <tr><td> 인증 서버 (Authorization Server) </td><td style=color:red> EMP (LG Server) </td><td> 
            - 서비스가 사용자로부터 권한을 부여받았음을 인증하고, 액세스 토큰을 발급해주는 서버입니다. </td></tr>
          <tr><td> 리소스 서버 (Resource Server) </td><td style=color:red> ThinQ Platform (LG Server) </td><td> 
            - 사용자의 자원(ThinQ 디바이스 데이터 등)을 서비스에 제공해주는 서버입니다.<br>
            - 서비스가 유효한 액세스 토큰으로 요청한 경우에만 요청한 작업을 수행합니다.<br>
              <br><b>ThinQ Platform</b><br>
              AI/ IoT/ 클라우드 등 LG ThinQ 디바이스와 관련된 다양한 기술을 아우르는 플랫폼이며, 여러 개의 복합적인 서버로 구성되어 있습니다. ThinQ Platform은 ThinQ 디바이스와 연동하는 파트너 서비스를 위해 여러 가지 API (Application Programming Interface)를 제공합니다. 예를 들어, 파트너 서비스는 ThinQ Connect API를 이용하여 다음과 같은 작업을 요청할 수 있습니다. <br>
                <br>   - 사용자의 디바이스 리스트 조회
                <br>   - 디바이스 상태 조회
                <br>   - 디바이스 제어
                <br>   - 디바이스 푸쉬 알림 구독 및 해지 등
          </td></tr>
          </table>
          기본적인 흐름은 다음과 같습니다.
          
          1. <b>Request Authorization</b>
            <br>여러분의 서비스가 사용자에게 ThinQ Platform에 등록된 사용자의 디바이스를 이용할 수 있는 권한을 요청합니다.
          
            - 서비스가 EMP에 로그인 프로세스를 요청하면,
            - EMP는 사용자의 웹 브라우저(user-agent)를 EMP가 제공하는 로그인 URI로 이동시키고, 사용자에게 로그인을 제공합니다.
          2. <b>Grant Authorization</b>
            <br>사용자가 승인하면, 여러분의 서비스는 EMP로부터 권한을 부여받습니다.
          
              - 사용자가 로그인하면,
              - EMP는 사용자의 웹 브라우저를 서비스가 사전에 제공한 Redirect URI로 돌려주고,
              - 서비스에 인증 코드(Authorization Code)를 발급합니다.
          3. <b>Request Access token with Authorization Grant.</b>
            <br>여러분의 서비스는 EMP가 발급한 인증 코드(Authorization Code)를 이용하여, EMP에 액세스 토큰을 요청합니다.
          
              - 서비스는 EMP가 돌려준 Redirect URI에 포함된 인증 코드(Authorization Code)를 추출하고
              - 이 코드를 EMP에 전달하여 액세스 토큰을 요청합니다.
          4. <b>Issue Access Token</b>
            <br>EMP는 여러분의 서비스에 액세스 토큰을 발급합니다.
          
              - EMP는 인증 코드를 검증하고,
              - 서비스에 액세스 토큰을 발급합니다.
          5. <b>Request Protected Resource with  Access Token.</b>
            <br>여러분의 서비스는 액세스 토큰을 제시하여 ThinQ Platform에 해당 사용자의 디바이스와 연동한 작업(예: 에어컨 온도 1도 올려줘)을 요청합니다.
          
              - 서비스는 ThinQ Platform의 API를 호출할 때 액세스 토큰을 파라미터로 전달해야 합니다.
          6. <b>Serve Protected Resource</b>
            <br>액세스 토큰이 유효하다면, ThinQ Platform은 해당 에어컨과 연동하여 명령을 수행한 뒤 여러분의 서비스에 결과를 응답합니다.
          
              - ThinQ Platform은 EMP와 통신하여 액세스 토큰이 유효한지 검증하고,
              - 유효한 경우에만 요청을 수행한 후 결과를 응답합니다.
          
          <b><h2>How to Develop with EMP?</h2></b>
          <hr></hr>
          <b><h3>Development Process</h3></b>
          여러분의 서비스(앱)와 EMP를 연동하여 개발하는 절차는 다음과 같습니다.

          1. <b>EMP 연동 방식 협의</b>
          <br> 여러분의 서비스(앱)가 어떤 방식으로 EMP와 연동해야 하는지를 LG 담당자에게 공유를 하면, 상황에 맞는 정보를 제공 받을것 입니다.
          
          2. <b>EMP App Key 발급</b>
          <br> LG 담당자에게 여러분의 서비스(앱)에 대한 App Key 발급을 요청합니다.
          > <b>App Key</b>
          > - EMP에서 서비스(앱)를 식별하고 인증하기 위해서 사용하는 식별자(identifier)로, client_id라고도 부릅니다.
          
          3. <b>EMP 연동 개발</b>
          <br> 본 개발자 사이트의 문서와 LG 담당자가 제공하는 정보를 참조하여, 여러분의 서비스(앱)와 EMP가 연동개발을 진행합니다.
          
            EMP 로그인 방식은 크게 다음과 같이 나누어 볼 수 있습니다.
          
            - LG 계정으로 로그인하는 경우
            - 3rd party 계정으로 로그인하는 경우
              - EMP 웹 로그인을 사용하는 경우
              - 3rd party가 제공하는 App SDK를 사용하는 경우
          
          <b>LG 계정으로 로그인하는 경우</b>
            1. 서비스(앱)는 EMP API를 호출하여 EMP Sign-in 페이지로 진입합니다.
            2. 사용자는 LG계정의 ID/PW를 입력하여 로그인합니다.
            3. EMP는 로그인된 사용자의 authorize code 값을 리턴합니다.
            4. 서비스(앱)는 authorize code 값으로 access token을 발급받아 사용합니다.

          <b><h3>3rd Party 계정으로 로그인하는 경우</h3></b>
            <b>1) EMP 로그인 웹 로그인을 사용하는 경우</b>
            <br>이 방식은 EMP Front를 통해 3rd party 계정의 인증과 EMP로그인 과정을 모두 처리합니다.
            > - 지원 계정
            >  - 다음 3rd party 계정만 사용 가능합니다.
            >    - Google Account
            >      - 단, 구글이 권장하는 Chrome Custom tab 혹은 SFSafariViewController를 사용해야 하며, WebView는 사용할 수 없습니다.
            >    - Facebook Account
            >    - Amazon Account 
            >    - Naver Account (국내 한정) 
            1. 서비스(앱)는 EMP API를 호출하여 EMP Sign-in 페이지로 진입합니다.
            2. 사용자는 로그인할 3rd party 계정 유형을 선택합니다.
            3. EMP는 사용자가 선택한 계정에 대한 인증 페이지를 요청합니다.
            4. 사용자는 해당 3rd party 계정의 ID/PW를 입력하여 로그인합니다.
            5. EMP는 인증이 완료되면 authorize code를 리턴합니다.
            6. 서비스(앱)는 authorize code 값으로 access token을 발급받아 사용합니다.
            <br>
          
          <b>2) 3rd party가 제공하는 App SDK를 사용하는 경우</b>
          <br>이 방식은 3rd party App SDK를 통해, 사용자가 3rd party 계정으로 로그인하도록 하는 방식입니다.
          + LG전자는 3rd party 의존적인 변경 사항(예: 계정 정책 변경, API 버전 변경, 단말 OS 업데이트 등)으로 인한 문제에 대해서는 책임지지 않으며, 이에 대한 수정 및 검증은 각 서비스(앱)에서 수행해야 합니다.
          
          > - 지원 계정
          >    - 다음 3rd party 계정만 사용 가능합니다.
          >      - Google Account
          >        - 단, Facebook 개발자 사이트에서 서비스(앱) 등록 후, 반드시 EMP에 business 그룹 요청을 해야 합니다.
          >      - Naver Account (국내 한정) 
          >        - 단, 네이버는 공식적으로 business grouping을 지원하지 않으므로, 네이버에 요청하여 허용된 경우에 한해서만 제한적으로 지원합니다.  
          
          다음을 참조하여 개발을 진행합니다.
          
          1. 귀사의 LG 담당자에게 사용하고자 하는 3rd party SDK 정보를 공유 받습니다.
          2. 3rd party 인증 과정은 각 3rd Party 회사가 제공하는 SDK 및 문서를 참조하여 구현합니다.
          3. EMP 연동 과정은 다음을 참고하거나 귀사의 LG 담당자를 통해 안내를 받습니다.
          
          <br><b>예) Google – App SDK를 사용하는 경우</b>
          
          1. 서비스(앱)은 EMP API (`{EMPBaseURL}/authorize`)를 호출하여 EMP Front UI에 진입합니다.
          2. EMP Front UI (empsign_in)에서 사용자가 Google 로그인 버튼을 클릭하면, 서비스(앱)의 callback_url로 다음 값이 리턴됩니다.
            - returnCode = 910
            - returnDescription = confirm_ggl
          3. 서비스(앱)은 해당 리턴을 받으면 WebView를 종료하고 Google App SDK를 사용하여 구글 인증을 수행합니다.
          4. Google 인증이 완료되면 서비스(앱)은 EMP Front UI (empsign_in) 페이지를 재호출합니다. 이 때, 헤더에 다음 정보를 포함하여 호출합니다.
            - user_id_type = GGL
            - user_id = 해당 사용자의 Google ID
            - user_thirdparty_token = 구글로부터 발급받은 토큰 값
          5. 인증이 유효하면, EMP는 authorize code를 발급합니다.
          6. 서비스(앱)는 authorize code로 access token을 발급받아 사용합니다.

      - name: Terminology
        x-displayName: 용어 정의
        description: |
          
          EMP API는 <b>OAuth 2.0 - Authorization Code Grant Type</b> 프로토콜에 기반하여 설계되었습니다. (단, 변수명/ required option 등은 표준과 다소 차이가 있을 수 있습니다.) 
          
            - <b>Authorization Server</b> (OAuth 2.0): EMP Proxy 서버에 해당합니다. 이하 <b>EMP</b>로 표현합니다.
            - <b>Client Application</b> (OAuth 2.0): 여러분의 서비스에 해당합니다. 이하 <b>서비스</b>로 표현합니다.

      - name: info
        x-displayName: 기본 정보
        description: |
          <b>EMPBaseURL</b>
          - LG 담당자가 개별적으로 전달.
            <table>
            <tr><th>서버 형상</th><th>EMPBaseURL</th><th>비고</th></tr>
            <tr><td>QA</td><td>https://qt-{CNTRY}.m.lgaccount.com/emp/v2</td><td rowspan=2>CNTRY : ISO 국가코드 2자리
                                                                                                  <br>
                                                                                                  예)<br>
                                                                                                - 한국: kr<br>
                                                                                                - 미국: us<br>
                                                                                                - 중국: cn<br>
                                                                                                - 러시아: ru<br>
                                                                                                  ......</td></tr>
            <tr><td>OP</td><td>https://{CNTRY}.m.lgaccount.com/emp/v2</td></tr>
      - name: API Call Sequence
        x-displayName: API 호출 시퀀스
        description: |
      
          <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" contentStyleType="text/css" height="705px" preserveAspectRatio="none" style="width:954px;height:705px;background:#FFFFFF;" version="1.1" viewBox="0 0 954 705" width="954px" zoomAndPan="magnify"><title>Request Authorization (Login)</title><defs/><g><text fill="#000000" font-family="sans-serif" font-size="14" font-weight="bold" lengthAdjust="spacing" textLength="238.1094" x="359.2439" y="27.9951">Request Authorization (Login)</text><rect fill="#FFFFFF" height="405.6641" style="stroke:#181818;stroke-width:1.0;" width="10" x="260.0288" y="149.7266"/><rect fill="#FFFFFF" height="397.6641" style="stroke:#181818;stroke-width:1.0;" width="10" x="499.5576" y="128.5938"/><rect fill="#FFFFFF" height="29.1328" style="stroke:#181818;stroke-width:1.0;" width="10" x="695.1943" y="336.3281"/><rect fill="#FFFFFF" height="44.2656" style="stroke:#181818;stroke-width:1.0;" width="10" x="695.1943" y="423.7266"/><rect fill="#FFFFFF" height="102.5313" style="stroke:#181818;stroke-width:1.0;" width="10" x="904.1802" y="394.5938"/><rect fill="none" height="442.6016" style="stroke:#000000;stroke-width:1.5;" width="937.5972" x="10" y="164.7266"/><rect fill="none" height="119.3359" style="stroke:#000000;stroke-width:1.5;" width="537.8359" x="20" y="188.8594"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="74" x2="74" y1="118.5938" y2="624.3281"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="264.1816" x2="264.1816" y1="118.5938" y2="624.3281"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="504.2793" x2="504.2793" y1="118.5938" y2="624.3281"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="700.1035" x2="700.1035" y1="118.5938" y2="624.3281"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="908.7632" x2="908.7632" y1="118.5938" y2="624.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="83.542" x="30" y="115.292">Service App</text><ellipse cx="74.771" cy="50.7969" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M74.771,58.7969 L74.771,85.7969 M61.771,66.7969 L87.771,66.7969 M74.771,85.7969 L61.771,100.7969 M74.771,85.7969 L87.771,100.7969 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="83.542" x="30" y="636.3232">Service App</text><ellipse cx="74.771" cy="648.125" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M74.771,656.125 L74.771,683.125 M61.771,664.125 L87.771,664.125 M74.771,683.125 L61.771,698.125 M74.771,683.125 L87.771,698.125 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="103.6943" x="213.1816" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="89.6943" x="220.1816" y="107.292">Proxy Server</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="103.6943" x="213.1816" y="623.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="89.6943" x="220.1816" y="643.3232">Proxy Server</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="86.5566" x="461.2793" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="72.5566" x="468.2793" y="107.292">Emp Front</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="86.5566" x="461.2793" y="623.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="72.5566" x="468.2793" y="643.3232">Emp Front</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="110.1816" x="645.1035" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="96.1816" x="652.1035" y="107.292">Emp Backend</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="110.1816" x="645.1035" y="623.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="96.1816" x="652.1035" y="643.3232">Emp Backend</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="56.834" x="880.7632" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="42.834" x="887.7632" y="107.292">Oauth</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="56.834" x="880.7632" y="623.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="42.834" x="887.7632" y="643.3232">Oauth</text><rect fill="#FFFFFF" height="405.6641" style="stroke:#181818;stroke-width:1.0;" width="10" x="260.0288" y="149.7266"/><rect fill="#FFFFFF" height="397.6641" style="stroke:#181818;stroke-width:1.0;" width="10" x="499.5576" y="128.5938"/><rect fill="#FFFFFF" height="29.1328" style="stroke:#181818;stroke-width:1.0;" width="10" x="695.1943" y="336.3281"/><rect fill="#FFFFFF" height="44.2656" style="stroke:#181818;stroke-width:1.0;" width="10" x="695.1943" y="423.7266"/><rect fill="#FFFFFF" height="102.5313" style="stroke:#181818;stroke-width:1.0;" width="10" x="904.1802" y="394.5938"/><polygon fill="#181818" points="248.0288,145.7266,258.0288,149.7266,248.0288,153.7266,252.0288,149.7266" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="74.771" x2="254.0288" y1="149.7266" y2="149.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="166.2578" x="81.771" y="144.6606">1. Login  (GET /authorize)</text><path d="M10,164.7266 L74.4429,164.7266 L74.4429,171.8594 L64.4429,181.8594 L10,181.8594 L10,164.7266 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="442.6016" style="stroke:#000000;stroke-width:1.5;" width="937.5972" x="10" y="164.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="19.4429" x="25" y="177.7935">alt</text><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="58.0293" x="89.4429" y="176.937">[success]</text><path d="M20,188.8594 L84.4429,188.8594 L84.4429,195.9922 L74.4429,205.9922 L20,205.9922 L20,188.8594 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="119.3359" style="stroke:#000000;stroke-width:1.5;" width="537.8359" x="20" y="188.8594"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="19.4429" x="35" y="201.9263">alt</text><polygon fill="#181818" points="487.5576,223.125,497.5576,227.125,487.5576,231.125,491.5576,227.125" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="270.0288" x2="493.5576" y1="227.125" y2="227.125"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="69.9258" x="277.0288" y="222.0591">2. Request</text><line style="stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="20" x2="557.8359" y1="236.125" y2="236.125"/><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="41.4004" x="25" y="246.3354">[Error]</text><polygon fill="#181818" points="85.771,267.0625,75.771,271.0625,85.771,275.0625,81.771,271.0625" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="79.771" x2="259.0288" y1="271.0625" y2="271.0625"/><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="63.7368" x="91.771" y="265.9966">400, 500</text><polygon fill="#181818" points="85.771,296.1953,75.771,300.1953,85.771,304.1953,81.771,300.1953" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="79.771" x2="498.5576" y1="300.1953" y2="300.1953"/><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="405.7866" x="91.771" y="295.1294">This service is not currently supported in your country.</text><polygon fill="#181818" points="683.1943,332.3281,693.1943,336.3281,683.1943,340.3281,687.1943,336.3281" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="509.5576" x2="689.1943" y1="336.3281" y2="336.3281"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="152.0073" x="516.5576" y="331.2622">3. Session Key Request</text><polygon fill="#181818" points="520.5576,361.4609,510.5576,365.4609,520.5576,369.4609,516.5576,365.4609" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="514.5576" x2="699.1943" y1="365.4609" y2="365.4609"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="161.6367" x="526.5576" y="360.395">4. Session Key Response</text><polygon fill="#181818" points="892.1802,390.5938,902.1802,394.5938,892.1802,398.5938,896.1802,394.5938" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="509.5576" x2="898.1802" y1="394.5938" y2="394.5938"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="181.6636" x="516.5576" y="389.5278">5. Session Key transmission</text><polygon fill="#181818" points="716.1943,419.7266,706.1943,423.7266,716.1943,427.7266,712.1943,423.7266" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="710.1943" x2="903.1802" y1="423.7266" y2="423.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="147.1577" x="722.1943" y="418.6606">6. Session key confrim</text><polygon fill="#181818" points="892.1802,463.9922,902.1802,467.9922,892.1802,471.9922,896.1802,467.9922" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="700.1943" x2="898.1802" y1="467.9922" y2="467.9922"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="119.3359" x="707.1943" y="447.7935">7. userNo, county,</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="170.8535" x="711.3267" y="462.9263">accountType transmission</text><polygon fill="#181818" points="520.5576,493.125,510.5576,497.125,520.5576,501.125,516.5576,497.125" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="514.5576" x2="908.1802" y1="497.125" y2="497.125"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="183.3013" x="526.5576" y="492.0591">8. Authorize Code Response</text><polygon fill="#181818" points="281.0288,522.2578,271.0288,526.2578,281.0288,530.2578,277.0288,526.2578" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="275.0288" x2="503.5576" y1="526.2578" y2="526.2578"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="151.0234" x="287.0288" y="521.1919">9. Code, URL Response</text><polygon fill="#181818" points="85.771,551.3906,75.771,555.3906,85.771,559.3906,81.771,555.3906" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="79.771" x2="264.0288" y1="555.3906" y2="555.3906"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="60.106" x="91.771" y="550.3247">10. Login</text><line style="stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="10" x2="947.5972" y1="564.3906" y2="564.3906"/><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="41.4004" x="15" y="574.6011">[Error]</text><polygon fill="#181818" points="85.771,595.3281,75.771,599.3281,85.771,603.3281,81.771,599.3281" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="79.771" x2="908.1802" y1="599.3281" y2="599.3281"/><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="223.6978" x="91.771" y="594.2622">Mismathing Redirect URI Error</text><!--SRC=[VLDTJzj047o_Nx7A4qY9QoZGOa4agDAg0jeAqZTUZlE6d73khdjdXFdrt5TiKgAysAlppEtCxDf9ro3SuhyMhOEBrYqroLVkf5QmTwqVfTfdZ0kd2KPtICzI85mOCm9kWHl332SdXJHSEHZz8VtIGO0XHOG91vkOsSh0TzBAHS0YL1y1brmyeQeZv27Lcw3Vt2kDdtMec9SocQPs5HmK49K3xFsOpU4Jpwvmd_76WMs5G6j37Pp9P-vmhJGQy3T5NHKS5kje63OMOKQaAQ4c7kMxLd2sy50Gkj5qJbXFpnwcHsKvXkEoPF6QNSZvKbgmELTVAkq1BH4grtHUgJ6Q7DRWpNIw9KzkbQEkO26HNdnACJw3-9nO1PyBFmnhmooliEkjzBnrjFaDay7vqVzKQxIoo6hymExxnb5KSBn9TSILNSbuCBHEOulFsBRNV3AmdpnRQBKWkTgXEVU52huKqFeiV-bnogaRtolW8jRppk2cb2rE1ZavXQz5_qiWVDCrRWqYUSan36juMaJA6FxUNc_bvULFExTUaeCoR-_xZNj7IekQfExQh1jfLzmjfNhqlMj9A9mNyZDVwDs-0G00]--></g></svg>
          
          EMP에 로그인 프로세스를 요청하는 시퀀스입니다.
          
          <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" contentStyleType="text/css" height="440px" preserveAspectRatio="none" style="width:751px;height:440px;background:#FFFFFF;" version="1.1" viewBox="0 0 751 440" width="751px" zoomAndPan="magnify"><title>Request Access Token</title><defs/><g><text fill="#000000" font-family="sans-serif" font-size="14" font-weight="bold" lengthAdjust="spacing" textLength="176.0664" x="288.6499" y="27.9951">Request Access Token</text><rect fill="#FFFFFF" height="132.6641" style="stroke:#181818;stroke-width:1.0;" width="10" x="407.3472" y="128.5938"/><rect fill="#FFFFFF" height="29.1328" style="stroke:#181818;stroke-width:1.0;" width="10" x="700.9492" y="202.9922"/><rect fill="none" height="177.6016" style="stroke:#000000;stroke-width:1.5;" width="734.3662" x="10" y="164.7266"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="64" x2="64" y1="118.5938" y2="359.3281"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="411.5" x2="411.5" y1="118.5938" y2="359.3281"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="705.5322" x2="705.5322" y1="118.5938" y2="359.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="83.542" x="20" y="115.292">Service App</text><ellipse cx="64.771" cy="50.7969" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M64.771,58.7969 L64.771,85.7969 M51.771,66.7969 L77.771,66.7969 M64.771,85.7969 L51.771,100.7969 M64.771,85.7969 L77.771,100.7969 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="83.542" x="20" y="371.3232">Service App</text><ellipse cx="64.771" cy="383.125" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M64.771,391.125 L64.771,418.125 M51.771,399.125 L77.771,399.125 M64.771,418.125 L51.771,433.125 M64.771,418.125 L77.771,433.125 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="103.6943" x="360.5" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="89.6943" x="367.5" y="107.292">Proxy Server</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="103.6943" x="360.5" y="358.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="89.6943" x="367.5" y="378.3232">Proxy Server</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="56.834" x="677.5322" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="42.834" x="684.5322" y="107.292">Oauth</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="56.834" x="677.5322" y="358.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="42.834" x="684.5322" y="378.3232">Oauth</text><rect fill="#FFFFFF" height="132.6641" style="stroke:#181818;stroke-width:1.0;" width="10" x="407.3472" y="128.5938"/><rect fill="#FFFFFF" height="29.1328" style="stroke:#181818;stroke-width:1.0;" width="10" x="700.9492" y="202.9922"/><polygon fill="#181818" points="395.3472,145.7266,405.3472,149.7266,395.3472,153.7266,399.3472,149.7266" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="64.771" x2="401.3472" y1="149.7266" y2="149.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="318.5762" x="71.771" y="144.6606">1. (POST /Token) grant_type=authorization_code</text><path d="M10,164.7266 L74.4429,164.7266 L74.4429,171.8594 L64.4429,181.8594 L10,181.8594 L10,164.7266 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="177.6016" style="stroke:#000000;stroke-width:1.5;" width="734.3662" x="10" y="164.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="19.4429" x="25" y="177.7935">alt</text><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="58.0293" x="89.4429" y="176.937">[success]</text><polygon fill="#181818" points="688.9492,198.9922,698.9492,202.9922,688.9492,206.9922,692.9492,202.9922" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="417.3472" x2="694.9492" y1="202.9922" y2="202.9922"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="264.6021" x="424.3472" y="197.9263">2. Access Token, Refresh Token Request</text><polygon fill="#181818" points="428.3472,228.125,418.3472,232.125,428.3472,236.125,424.3472,232.125" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="422.3472" x2="704.9492" y1="232.125" y2="232.125"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="64.2383" x="434.3472" y="227.0591">3. 200 OK</text><polygon fill="#181818" points="75.771,257.2578,65.771,261.2578,75.771,265.2578,71.771,261.2578" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="69.771" x2="411.3472" y1="261.2578" y2="261.2578"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="275.082" x="81.771" y="256.1919">4. Aceess Token, Refresh Token Response</text><line style="stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="10" x2="744.3662" y1="270.2578" y2="270.2578"/><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="41.4004" x="15" y="280.4683">[Error]</text><polygon fill="#181818" points="75.771,301.1953,65.771,305.1953,75.771,309.1953,71.771,305.1953" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="69.771" x2="411.3472" y1="305.1953" y2="305.1953"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="12.4033" x="81.771" y="300.1294">5.</text><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="100.3374" x="98.3066" y="300.1294">400, 401, 412</text><polygon fill="#181818" points="75.771,330.3281,65.771,334.3281,75.771,338.3281,71.771,334.3281" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="69.771" x2="704.9492" y1="334.3281" y2="334.3281"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="12.4033" x="81.771" y="329.2622">6.</text><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="27.1362" x="98.3066" y="329.2622">500</text><!--SRC=[VL3BJW8n5DttAqvOQG93GN0n6IPXuSe5HDYJqhb8usHQRmiHlzvf6ICeSNFJntdUO49DUA7t0_c0kTRaFTRsZHe8eNImZDwA-6WqOUvS3yf3EIUSuc2qSQe9w2tPVfmGOSG9uUB3DMQX3c6VFcqy9N5pL84wS2kAGNc-v1Xbk5ikLciCKvPxl7AhiWadHxD8jsm-LJ2ssMXRaL1rW3-ay28fHAdaasESNTNgjsLtJ7xVjUog_yGvnqiJW-z4oF6GOImb5i-Yeb_Wph85nnOv9j6I_h7qpZQUBeNEIw3Q4vwOBLzhvfXcA7QsNQIsjUKPKrKMst8YPHyJEMh7Q5mCjsKnZA3o8dvYFzvaJwMyvFn98wYflW00]--></g></svg>  
          
          EMP에 토큰 발급 시퀀스입니다.
      
          <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" contentStyleType="text/css" height="440px" preserveAspectRatio="none" style="width:620px;height:440px;background:#FFFFFF;" version="1.1" viewBox="0 0 620 440" width="620px" zoomAndPan="magnify"><title>Refresh Access Token</title><defs/><g><text fill="#000000" font-family="sans-serif" font-size="14" font-weight="bold" lengthAdjust="spacing" textLength="172.3477" x="224.9126" y="27.9951">Refresh Access Token</text><rect fill="#FFFFFF" height="132.6641" style="stroke:#181818;stroke-width:1.0;" width="10" x="372.9429" y="128.5938"/><rect fill="#FFFFFF" height="29.1328" style="stroke:#181818;stroke-width:1.0;" width="10" x="569.7559" y="202.9922"/><rect fill="none" height="177.6016" style="stroke:#000000;stroke-width:1.5;" width="603.1729" x="10" y="164.7266"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="64" x2="64" y1="118.5938" y2="359.3281"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="377.0957" x2="377.0957" y1="118.5938" y2="359.3281"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="574.3389" x2="574.3389" y1="118.5938" y2="359.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="83.542" x="20" y="115.292">Service App</text><ellipse cx="64.771" cy="50.7969" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M64.771,58.7969 L64.771,85.7969 M51.771,66.7969 L77.771,66.7969 M64.771,85.7969 L51.771,100.7969 M64.771,85.7969 L77.771,100.7969 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="83.542" x="20" y="371.3232">Service App</text><ellipse cx="64.771" cy="383.125" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M64.771,391.125 L64.771,418.125 M51.771,399.125 L77.771,399.125 M64.771,418.125 L51.771,433.125 M64.771,418.125 L77.771,433.125 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="103.6943" x="326.0957" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="89.6943" x="333.0957" y="107.292">Proxy Server</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="103.6943" x="326.0957" y="358.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="89.6943" x="333.0957" y="378.3232">Proxy Server</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="56.834" x="546.3389" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="42.834" x="553.3389" y="107.292">Oauth</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="56.834" x="546.3389" y="358.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="42.834" x="553.3389" y="378.3232">Oauth</text><rect fill="#FFFFFF" height="132.6641" style="stroke:#181818;stroke-width:1.0;" width="10" x="372.9429" y="128.5938"/><rect fill="#FFFFFF" height="29.1328" style="stroke:#181818;stroke-width:1.0;" width="10" x="569.7559" y="202.9922"/><polygon fill="#181818" points="360.9429,145.7266,370.9429,149.7266,360.9429,153.7266,364.9429,149.7266" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="64.771" x2="366.9429" y1="149.7266" y2="149.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="284.1719" x="71.771" y="144.6606">1. (POST /Token) grant_type=refresh_token</text><path d="M10,164.7266 L74.4429,164.7266 L74.4429,171.8594 L64.4429,181.8594 L10,181.8594 L10,164.7266 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="177.6016" style="stroke:#000000;stroke-width:1.5;" width="603.1729" x="10" y="164.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="19.4429" x="25" y="177.7935">alt</text><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="58.0293" x="89.4429" y="176.937">[success]</text><polygon fill="#181818" points="557.7559,198.9922,567.7559,202.9922,557.7559,206.9922,561.7559,202.9922" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="382.9429" x2="563.7559" y1="202.9922" y2="202.9922"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="167.813" x="389.9429" y="197.9263">2. Refresh Token Request</text><polygon fill="#181818" points="393.9429,228.125,383.9429,232.125,393.9429,236.125,389.9429,232.125" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="387.9429" x2="573.7559" y1="232.125" y2="232.125"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="64.2383" x="399.9429" y="227.0591">3. 200 OK</text><polygon fill="#181818" points="75.771,257.2578,65.771,261.2578,75.771,265.2578,71.771,261.2578" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="69.771" x2="376.9429" y1="261.2578" y2="261.2578"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="173.0625" x="81.771" y="256.1919">4. Aceess Token Response</text><line style="stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="10" x2="613.1729" y1="270.2578" y2="270.2578"/><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="41.4004" x="15" y="280.4683">[Error]</text><polygon fill="#181818" points="75.771,301.1953,65.771,305.1953,75.771,309.1953,71.771,305.1953" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="69.771" x2="376.9429" y1="305.1953" y2="305.1953"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="12.4033" x="81.771" y="300.1294">5.</text><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="100.3374" x="98.3066" y="300.1294">400, 401, 412</text><polygon fill="#181818" points="75.771,330.3281,65.771,334.3281,75.771,338.3281,71.771,334.3281" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="69.771" x2="573.7559" y1="334.3281" y2="334.3281"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="12.4033" x="81.771" y="329.2622">6.</text><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="27.1362" x="98.3066" y="329.2622">500</text><!--SRC=[RP1FJuCm6CRl_HHFE6dYe23pG91a1qyUMDpkImVl797GsdQB-_QsPKxcl3IqF7z-xsixsnFUQAV9xB5e6Z86Q_b10sEYiL8ZMf4-TWrXeLG4OI2KOafespMT4eD5jDJowmGl8nqKoZzSQsfniFlmK_gl4DuTXQMps8LYLesN0ccCksMzMYC9AFTurovbOq-AdlN8kh41KlGMvX2mMJ3xb51H88ilWuKOT_iyaB6_tIDBE37xgKU1nnWPvwXVMKj_nESI9_R81VBOROqkMtCTHid1qDGvZaYz8RneBVLrI85vZ78dtPeQsKlj9cohSblbd3yWvwaxqgnCjbMPU54ruGtkft_TSywddXiQHaFx3G00]--></g></svg>
          
          EMP에 토큰 재발급 시퀀스입니다.

      - name: Authorize API
        description: EMP 에서 제공하는 인증 및 권한 부여 요청 API 입니다.
      - name: Token API
        description: EMP 에서 제공하는 토큰 발급/재발급 API 입니다.
    paths:
      /authorize:
        get:
          tags:
            - Authorize API
          summary: 로그인 요청 (Authorization)
          description: |-
            EMP에 로그인 페이지를 요청하여 사용자가 LG 계정 (혹은 LG 계정과 연동하는 3rd party 계정)으로 로그인할 수 있도록 하고, 사용자가 로그인하면 EMP로부터 인증 코드 (Authorization Code)를 전달받습니다.
            - Error Code
            <table>
            <tr><th> Service  </th><th> Error Code </th><th> Error Message </th><th> Remark </th></tr> 
            <tr><td> v1.0 DR </td><td> <code>400</code> </span> </td><td> app_id is invalid </td><td> client_id가 잘못된 경우 </td></tr> 
            <tr><td> v2.0 ThinQ Connect </td><td> <code>500</code> </td><td> Page not found </td><td> 요청 정보에 오류가 있는 경우 </td></tr> 
            <tr><td rowspan=2> 공통 </td><td rowspan=2> 로그인 시 alert pop-up </td><td> Mismathing Redirect URI Error </td><td> 등록되지 않은 Redirect_URI로 요청한 경우 </td></tr> 
            <tr><td> 현재 고객님의 국가에서는 지원되지 않는 서비스입니다. </td><td> 제 3자 동의 약관이 등록되지 않은 경우 </td></tr> 
            </table>
          operationId: authorize
          requestBody:
            required: true
            content:
              application/x-www-form-urlencoded:
                schema:
                  type: object
                  properties:
                    client_id:
                      type: string
                      description: |-
                        서비스(Application) 식별자
                        - EMP(Authorization Server)가 서비스를 식별하기 위해 발급하는 값입니다.
                        - LG 담당자에게 요청하여 발급받을 수 있습니다.
                    redirect_uri:
                      type: string
                      description: |-
                        요청 수행 후, EMP가 사용자의 웹브라우저를 서비스로 리다이렉트 해줄 URI 
                        - 이 API가 호출되면 EMP는 사용자에게 로그인 웹페이지를 제공하고 로그인 프로세스를 완료한 후 사용자의 웹 브라우저 (user-agent)를 다시 서비스로 돌려보냅니다. 이때, 돌려보낼 주소를 의미합니다.
                        - 반드시 UTF-8 인코딩을 해야 합니다.
                    response_type:
                      type: string
                      description: |-
                        code로 입력합니다.
                        - OAuth 2.0 Grant Type 중 Authorization Code Grant Type을 사용함을 의미합니다.
                    state:
                      type: string
                      description: |-
                        크로스 사이트 요청 위조(Cross-site request forgery) 방어를 위한 값입니다. 요청 수행 후, EMP가 사용자의 웹 브라우저를 서비스로 다시 리다이렉션할 때 이 값을 포함합니다.
                  required:
                    - client_id
                    - redirect_uri
                    - response_type
                    - state
          responses:
            '200':
              description: |-
                성공과 에러의 상태값은 200으로 동일합니다. 정상적인 파라미터가 리턴되지 않았다면, Error Code 표를 참조 바랍니다.
                <br><br>성공 시, EMP는 사용자의 웹 브라우저(user-agent)를 EMP가 제공하는 로그인 페이지로 이동시킵니다. 사용자가 로그인에 정상적으로 성공하면 EMP는 사용자의 웹 브라우저를 서비스로 리다이렉션 해줍니다. 리다이렉션 주소는 파라미터로 전달받은 redirect_uri를 사용합니다.
                
                또한 EMP는 웹 브라우저를 돌려줄 때 redirect_uri의 query string에 인증 코드(Authorization Code)를 포함시킴으로써 서비스에 인증 코드를 발급합니다.
      /token?grant_type=authorization_code :
        post:
          tags:
            - Token API
          summary: 액세스 토큰 발급 요청
          description: |-
            EMP에 토큰 발급을 요청합니다. 성공 시 EMP로부터 액세스 토큰과 리프레쉬 토큰을 응답받습니다
            - Error Code
            <table>
            <tr><th> Service  </th><th> Error Code </th><th> Error Message </th><th> Remark </th></tr> 
            <tr><td rowspan=2> v1.0 DR </td><td> <code>400</code> </span> </td><td> App_id Fail </td><td> 허용되지 않은 App_key (i.e., client_id) </td></tr> 
            <tr><td> LG.OAUTH.EC.4001 </td><td> OAuth2 processing error </td><td> 파라미터가 유효하지 않음  </td></tr> 
            <tr><td rowspan=6> v2.0 ThinQ Connect </td><td rowspan=4> <code>412</code> </td><td> required client_id </td><td> 파라미터가 누락됨 (client_id) </td></tr> 
            <tr><td> required backend_url </td><td> 파라미터가 누락됨 (backend_url) </td></tr> 
            <tr><td> required grant_type </td><td> 파라미터가 누락됨 (grant_type) </td></tr> 
            <tr><td> required refresh_token </td><td> 파라미터가 누락됨 (refresh_token) </td></tr> 
            <tr><td> <code>401</code> </td><td> not allowed client_id </td><td> 허용되지 않은 client_id (EMP에서 발급한 App_key)임 </td></tr>
            <tr><td> <code>500</code> </td><td> oauth date time error </td><td> OAuth 통신 오류 </td></tr> 
            </table>

          operationId: token
          requestBody:
            required: true
            content:
              application/x-www-form-urlencoded:
                schema:
                  type: object
                  properties:
                    client_id:
                      type: string
                      description: |-
                        서비스(Application) 식별자
                    redirect_uri:
                      type: string
                      description: |-
                        GET {{EMPBaseURL}}/authorize 호출 시 사용한 redirect_uri와 동일한 값
                    code:
                      type: string
                      description: |-
                        EMP로부터 전달받은 인증 코드 (Authorization Code)
                        - 인증 코드 값은 GET {{EMPBaseURL}}/authorize 호출 후 리다이렉션된 URI에 query string으로 포함되어 있습니다.
                    grant_type:
                      type: string
                      description: |-
                        authorization_code로 입력
                        <br>
                        <br>
                        참고
                        - 액세스 토큰을 요청하는 경우: authorization_code 입력 
                        - 액세스 토큰을 재발급 요청하는 경우: refresh_token 입력
                      enum:
                        - authorization_code
                        - refresh_token
                    backend_url:
                      type: string
                      description: |-
                        EMP 로그인 후 전달받은 backend_url 값
                  required:
                    - client_id
                    - redirect_uri
                    - code
                    - grant_type
          responses:
            '200':
              description: Success
                <br>성공과 에러의 상태값은 200으로 동일합니다. 정상적인 파라미터가 리턴되지 않았다면, Error Code 표를 참조 바랍니다.
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      access_token:
                        type: string
                        description: |-
                          EMP가 발급하는 OAuth 2.0 액세스 토큰입니다.
                        example:
                          xxxxxxxxxxxxxxxxxxxx
                      expires_in:
                        type: string
                        description: |-
                          액세스 토큰이 만료되기까지 남은 시간입니다. (단위: sec)
                        example:
                          3600
                      refresh_token:
                        type: string
                        description: |-
                          EMP에 새로운 액세스 토큰을 요청하기 위해 사용되는 토큰입니다.
                          - API 요청 시, grant_type을 refresh_token으로 입력하지 않은 경우에만 전달되는 값입니다.
                        example:
                          xxxxxxxxxxxxxxxxxxxx
                      oauth2_backend_url:
                        type: string
                        description: |-
                          EMP backend url입니다.
                          - API 요청 시, grant_type을 refresh_token으로 입력하지 않은 경우에만 전달되는 값입니다.
                        example:
                          'https://example.lge.com/'
      #        500:
      #          description: |-
      #            | Error Code | Error Message | Remark |
      #            |-|-|-|
      #            | 412 | required client_id | 파라미터가 누락됨 (client_id) |
      #            | 412 | required backend_url | 파라미터가 누락됨 (backend_url) |
      #            | 412 | required grant_type | 파라미터가 누락됨 (grant_type) |
      #            | 412 | required refresh_token | 파라미터가 누락됨 (refresh_token) |
      #            | 401 | not allowed client_id | 허용되지 않은 client_id (EMP에서 발급한 App_key)임 |
      #            | 500 | oauth date time error | OAuth 통신 오류 |
      #          content:
      #            application/json:
      #              schema:
      #                $ref: '#/components/schemas/error'
      /token?grant_type=refresh_token:
        post:
          tags:
            - Token API
          summary: 액세스 토큰 재발급 요청
          description: |-
            EMP에 액세스 토큰 재발급을 요청합니다. 요청 시 리프레쉬 토큰을 전달하고 응답으로 새로운 액세스 토큰을 발급 받습니다.
            - Error Code
                <table>
                <tr><th> Service  </th><th> Error Code </th><th> Error Message </th><th> Remark </th></tr> 
                <tr><td rowspan=2> v1.0 DR </td><td> <code>400</code> </span> </td><td> App_id Fail </td><td> 허용되지 않은 App_key (i.e., client_id) </td></tr> 
                <tr><td> LG.OAUTH.EC.4001 </td><td> OAuth2 processing error </td><td> 파라미터가 유효하지 않음  </td></tr> 
                <tr><td rowspan=6> v2.0 ThinQ Connect </td><td rowspan=4> <code>412</code> </td><td> required client_id </td><td> 파라미터가 누락됨 (client_id) </td></tr> 
                <tr><td> required backend_url </td><td> 파라미터가 누락됨 (backend_url) </td></tr> 
                <tr><td> required grant_type </td><td> 파라미터가 누락됨 (grant_type) </td></tr> 
                <tr><td> required refresh_token </td><td> 파라미터가 누락됨 (refresh_token) </td></tr> 
                <tr><td> <code>401</code> </td><td> not allowed client_id </td><td> 허용되지 않은 client_id (EMP에서 발급한 App_key)임 </td></tr>
                <tr><td> <code>500</code> </td><td> oauth date time error </td><td> OAuth 통신 오류 </td></tr> 
                </table>
          operationId: token2
          requestBody:
            required: true
            content:
              application/x-www-form-urlencoded:
                schema:
                  type: object
                  properties:
                    client_id:
                      type: string
                      description: |-
                        서비스(Application) 식별자
                    refresh_token:
                      type: string
                      description: |-
                        로그인 시, 액세스 토큰 발급 요청의 응답 결과에 포함된 refresh_token 값
                    grant_type:
                      type: string
                      description: |-
                        authorization_code로 입력
                        <br>
                        <br>
                        참고
                        - 액세스 토큰을 요청하는 경우: authorization_code 입력 
                        - 액세스 토큰을 재발급 요청하는 경우: refresh_token 입력
                      enum:
                        - authorization_code
                        - refresh_token
                    backend_url:
                      type: string
                      description: |-
                        EMP 로그인 후 전달받은 backend_url 값
                  required:
                    - client_id
                    - refresh_token
                    - grant_type
          responses:
            '200':
              description: Success
                <br>성공과 에러의 상태값은 200으로 동일합니다. 정상적인 파라미터가 리턴되지 않았다면, Error Code 표를 참조 바랍니다.
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      access_token:
                        type: string
                        description: |-
                          EMP가 발급하는 OAuth 2.0 액세스 토큰입니다.
                        example:
                          xxxxxxxxxxxxxxxxxxxx
                      expires_in:
                        type: string
                        description: |-
                          액세스 토큰이 만료되기까지 남은 시간입니다. (단위: sec)
                        example:
                          3600
    #          500:

    #            description: |-

    #              | Error Code | Error Message | Remark |

    #              |-|-|-|

    #              | 412 | required client_id | 파라미터가 누락됨 (client_id) |

    #              | 412 | required backend_url | 파라미터가 누락됨 (backend_url) |

    #              | 412 | required grant_type | 파라미터가 누락됨 (grant_type) |

    #              | 412 | required refresh_token | 파라미터가 누락됨 (refresh_token) |

    #              | 401 | not allowed client_id | 허용되지 않은 client_id (EMP에서 발급한 App_key)임 |

    #              | 500 | oauth date time error | OAuth 통신 오류 |

    #            content:

    #              application/json:

    #                schema:

    #                  $ref: '#/components/schemas/error'

    components:
      schemas:
        error:
          type: object
          properties:
            httpError:
              type: string
    x-tagGroups:
      - name: Get Started
        tags:
          - Overview
          - API Call Sequence
          - Terminology
          - info
      - name: EMP API
        tags:
          - Authorize API
          - Token API
---
