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
        x-displayName: Overview
        description: |

          How can your service users and ThinQ device users be integrated? How can your service get authorization from users to access and use their data on the ThinQ Platform? For all this and more, the LG EMP provides you with an API based on the OAuth 2.0 standard.
          
          <b><h2>What is LG EMP?</h2></b>
          <hr></hr>
          The LG Electronics Enterprise Membership Platform (EMP) is a member management platform providing services related to LG Electronics. The EMP enables you to log in with LG account, or a 3rd party account linked with the LG account, and use the services provided by LG Electronics or LG Electronics partners.  
          
          <b><h3>Key Features</h3></b>
          The EMP provides an authorization framework based on the Authorization Code Grant Type over various methods of the OAuth 2.0 standard. Your service can request the followings by calling APIs provided by the EMP.
            - Web login linked to an LG account
            - Issuance of access tokens and refresh tokens
            - Re-issuance of access tokens
          
          ><b><h3>Authorization Code Grant Type</h3></b>
          The EMP uses Authorization Code Grant Type over various methods of the OAuth 2.0 standard. This method is mainly used for applications that run on a web server, such as your service, and includes interaction with a web browser (user agent). If the service requests a login process from the EMP, the EMP redirects the user to the login page. Once the login has been completed, the EMP redirects the user's web browser to the promised redirect URI. At that time, the redirect URI includes an authorization code.<br><br>
          Using the code, the service can obtain an access token on request from EMP, and then access the user resources by presenting the token.
          
          <b><h3>Benefits</h3></b>
          The EMP provides the following benefits for ThinQ service users and providers.
            - <b>Service user</b>
              - Once you register your device on the ThinQ app, you can use various services provided by LG Electronics or LG Electronics partners.
            - <b>Service provider</b>
              - You can provide services to ThinQ device users worldwide by linking services with the EMP and the ThinQ Platform.
          
          <img src="https://thinq.developer.lge.com/download_file/view_inline/12981/" style="width:70%; padding:20px;"/>
          
          <b><h3>Basic Concept</h3></b>
          Let's assume that you provide a service to control an air conditioner. What process is required before a ThinQ air conditioner can be used?

          <b>A. Registering the air conditioner on the ThinQ Platform (User/LG ThinQ app)</b>
          1. The user registers and logs into an account linked to an LG account.
          2. The user registers the air conditioner.
          <br>→ The user's air conditioner is registered on the ThinQ Platform.
          
          <b>B. Service login and access token issuance (User/Service/LG EMP)</b>
          1. The user requests to log in to the service.
          2. The service requests the login process from the EMP. (→ The EMP redirects the user to a secure login page, and prompts the user to log in.)
          3. The user logs in. (→ The EMP returns the user to the service and issues an authorization code.)
          4. The service sends the authorization code to the EMP and requests an access token.
          5. The EMP issues an access token to the service.
          <br>→ The service receives an access token from the EMP.
          
          <b>C. Air conditioner control (User/Service/LG ThinQ Platform)</b>
          1. The user sends a request to the service to control the air conditioner.
          2. The service sends a request to the ThinQ Platform to control the air conditioner. Upon request, the service needs to send an access token issued by the EMP.
          3. The ThinQ Platform communicates with the EMP to check the following:
            - Which user is making the request?
            - Is the access token valid? (Has the unexpired token been authorized by the corresponding user?)
          4. If the access token is valid, the ThinQ Platform controls the air conditioner and sends the results to the service.
          5. The service then provides the result to the user.
          <br>→ The service sends a request to the ThinQ Platform to control the user's air conditioner with an access token.

          <b><h4>Interaction Between Service, EMP, and ThinQ Platform</h4></b>
          The above procedure can be explained briefly in the terms of service.

          1. The service requests the following to the EMP. 
            - The service requests the login process so that a user can log in to the service.
            - If the user logs in, the service receives an access token from the EMP.
          2. The service requests the ThinQ Platform to perform a task related to the user's device. Upon request, the service needs to send an access token issued by the EMP. 
            - E.g) Tasks that can be requested from the ThinQ Platform through the ThinQ Connect API
              - Retrieve the list of devices registered by a user.
              - Retrieve the current status of the air conditioner (e.g., retrieve the target temperature).
              - Send a control command to the air conditioner (e.g., increase the air conditioner temperature by 1 degree).
              - Subscribe to push notifications for the air conditioner (e.g., a filter replacement notification).
          
          <b><h2>Basic Workflow</h2></b>
          <hr></hr>
          Interaction between the service and the EMP follows the OAuth 2.0 protocol.
          <b><h3>OAuth 2.0 Protocol</h3></b>
          <b><h4>OAuth 2.0 Basic</h4></b>
          The following four roles are required to configure the OAuth 2.0 protocol.
          
          - <b>Resource owner (user) </b>
            - The authority that grants permission to use its resources protected on the resource server.
            - This refers to the application user.
          - <b>Application</b>
            - Requests authorization from the authorization server and is issued an access token. And then, it presents an access token to the resource server and requests resources from the resource owner.
            - This refers to applications in general, your service being one of them.
          - <b>Authorization server</b>
            - Authenticates that an application has been authorized by the resource owner, and issues an access token to the application.
          - <b>Resource server</b>
            - Provides user resources to applications.
            - Only when an application sends a request with a valid access token is the request accepted. It will then provide the user's resources to the application.
          
          These interact with each other according to the following basic flow.
          1. <b>Request Authorization</b>
            - An application requests authorization from the resource owner (user).
          2. <b>Grant Authorization</b>
            - When a user approves the authorization, the application is granted with authorization.
          3. <b>Request Access token with Authorization Grant</b>
            - The application requests an access token from the authorization server with granted authorization.
          4. <b>Issue Access Token</b>
            - The authorization server issues an access token to the application.
          5. <b>Request Protected Resource with  Access Token</b>
            - The application requests the user's resources from the resource server by presenting the access token.
          6. <b>Serve Protected Resource</b>
            - If the access token is valid, the resource server provides the application with the user's resources.

          <b><h3>EMP Basic Workflow</h3></b>
          Let's use the OAuth 2.0 protocol for your situation. What are your services? What roles do the EMP and the ThinQ Platform play? 
          <table>
          <tr><th> OAuth 2.0 </th><th width="220"> Service/ EMP/ ThinQ Platform </th><th> Description </th></tr>
          <tr><td> Application </td><td style=color:red> Service (Partner Server) </td><td> 
            - Your service </td></tr>
          <tr><td> Resource Owner (User) </td><td style=color:red> User </td><td> 
            - An owner of ThinQ device and service user<br>
            - Registers a device in the ThinQ App and authorizes the service to use the device data.  </td></tr>
          <tr><td> Authorization Server </td><td style=color:red> EMP (LG Server) </td><td> 
            - Authenticates that the service has been authorized by the user and issues an access token. </td></tr>
          <tr><td> Resource Server </td><td style=color:red> ThinQ Platform (LG Server) </td><td> 
            - A server that provides the user's resources (ThinQ device data, etc.) to the service.<br>
            - Performs the requested action only if the service requested it with a valid access token.<br>
              <br><b>ThinQ Platform</b><br>
              A platform that encompasses a wide range of technologies related to LG ThinQ devices such as AI/IoT/Cloud, consisting of multiple complex servers. It provides various APIs (Application Programming Interfaces) for LG partner services that work with ThinQ devices. For example, a partner service can use the ThinQ Connect APIs to request the following actions:<br>
                <br>   - User's device list inquiry
                <br>   - Device status inquiry
                <br>   - Device Control
                <br>   - Device push notification subscription/unsubscription, etc.
          </td></tr>
          </table>
          The basic flow is as follows:
          
          1. <b>Request Authorization</b>
            <br>Your service asks the user for permission to use the user's device registered on the ThinQ Platform.
          
            - The service requests a login from the EMP.
            - The EMP redirects the user's web browser (user agent) to the login URI and offers the login to the user.
          2. <b>Grant Authorization</b>
            <br>If the user logs in, your service is authorized by the EMP.
          
              - The user logs in.
              - The EMP redirects the user's web browser to the redirect URI previously provided by the service.
              - An authorization code is issued to the service.
          3. <b>Request Access token with Authorization Grant.</b>
            <br>Your service requests an access token from the EMP using the authorization code issued by the EMP.
          
              - The service extracts an authorization code from the redirect URI returned by the EMP.
              - The code is sent to the EMP to request an access token.
          4. <b>Issue Access Token</b>
            <br>The EMP issues an access token to your service.
          
              - The EMP verifies the verification code.
              - An access token is issued to the service.
          5. <b>Request Protected Resource with  Access Token.</b>
            <br>Your service presents an access token and requests the ThinQ Platform to perform a task linked to the user's device. (e.g., increase air conditioner temperature by 1 degree.)
          
              - The service must pass on an access token as a parameter when calling the ThinQ Platform API.
          6. <b>Serve Protected Resource</b>
            <br>If the access token is valid, the ThinQ Platform interacts with the air conditioner to execute a command, then replies with the result to your service.
          
              - The ThinQ Platform communicates with the EMP to verify that the access token is valid.
              - If the token is valid, the ThinQ Platform carries out the request and replies with the result.
          
          <b><h2>How to Develop with EMP?</h2></b>
          <hr></hr>
          <b><h3>Development Process</h3></b>
          You can carry out development by linking your service (app) with the EMP as follows:

          1. <b>Discussion on how to link the EMP</b>
          <br> First, discuss with your LG representative how your service should be linked with the EMP. They will provide more information pertaining to your situation and needs.
          
          2. <b>Issuance of an EMP App Key</b>
          <br> Request that your LG representative issue an App Key for your service, and get the information you need.
          > <b>App Key</b>
          > - An identifier used by the EMP to identify and authorize a service (app), also known as client_id
          
          3. <b>Development linked with the EMP</b>
          <br> Please refer to the documents provided on the developers site, as well as information provided to you by your LG representative, to develop and link your service with the EMP.
          
            EMP sign-in methods can be broadly divided into the following:
          
            - When signing in with an LG account
            - When signing in with a third-party account
              - When using EMP web sign-in
              - When using an App SDK provided by a third party
          
          <b>When signing in with an LG account</b>
            1. Your service (app) enters the EMP sign-in page by calling an EMP API.
            2. A user signs in by entering an ID/password for the LG account.
            3. The EMP returns an authorization code of the sign-in user to your service (app).
            4. The service (app) receives an access token with the authorization code.

          <b><h3>When signing in with a third-party account</h3></b>
            <b>1) When using EMP web sign-in</b>
            <br>This method uses the EMP Front to process both the authentication of a third-party account and the EMP sign-in.
          > - Supported Accounts
          >    - Only the following third-party accounts are supported.
          >      - Google Account
          >        - Use the Chrome Custom tab recommended by Google or use the SFSafariViewController. Do NOT use the WebView.
          >      - Facebook Account
          >      - Amazon Account 
          >      - Naver Account (Only allowed within South Korea) 
            1. Your service (app) enters the EMP sign-in page by calling an EMP API.
            2. A user selects the type of a third-party account to be used for sign-in.
            3. The EMP requests an authentication page for the third-party account type selected by the user.
            4. The user enters the ID/password for the third-party account to sign in.
            5. Once the authentication is complete, the EMP returns an authorization code.
            6. The service (app) receives an access token with the authorization code.
            <br>
          
          <b>2) When using an App SDK provided by a third party</b>
          <br>This method allows a user to sign in with a third-party account through a third-party App SDK.
          + LG Electronics is not responsible for any problem caused by 3rd party-dependent changes (e.g., account policy change, API version change, terminal OS update, etc.), and you need to perform the correction and verification in the service (app).
          
          > - Supported Accounts
          >    - Only the following third-party accounts are supported.
          >      - Google Account
          >      - Facebook Account
          >        - You need to register your service (app) on the Facebook developer site and request the EMP a business group.
          >      - Naver Account (Only allowed B2C services (apps) operating in South Korea ) 
          >        - You need to receive approval from Naver, as Naver does not officially support business grouping.   
          
          Refer to the following to carry out the development.
          
          1. Share with your LG representative the information on the third-party SDK that you want to use.
          2. Implement a third-party authentication process by using the SDK and documentation provided by the third party.
          3. For EMP sign-in linkage, refer to the following or get guidance from your LG representative.
          
          <br><b>E.g., Using Google - App SDK</b>
          
          1. The service (app) calls the EMP API (`{EMPBaseURL}/authorize`) and enters the EMP Front UI.
          2. On the EMP Front UI (empsign_in), a user clicks the Google Sign-in button. Then the following values are returned as callback_url of the service (app).
            - returnCode = 910
            - returnDescription = confirm_ggl
          3. Once the service (app) receives the returned values, it closes WebView and uses the Google App SDK to perform Google authentication.
          4. Once Google authentication is complete, the service (app) calls the EMP Front UI (empsign_in) page again. At this time, the following information is included in the header.
            - user_id_type = GGL
            - user_id = Google ID of the user 
            - user_thirdparty_token = A token issued by Google
          5. If the authentication is valid, the EMP issues an authorization code. 
          6. The service (app) receives an access token with the authorization code.

      - name: Terminology
        x-displayName: Terminology
        description: |
          
          The EMP API has been designed based on the <b>OAuth 2.0 - Authorization Code Grant Type</b> protocol. (Note that variable names, required options, etc. may be slightly different from the standard.)
          
            - <b>Authorization Server (OAuth 2.0)</b>: Corresponds to the EMP proxy server. Hereafter expressed as the <b>EMP</b>.
            - <b>Client Application (OAuth 2.0)</b>: Corresponds to your service. Hereafter expressed as the <b>service</b>.

      - name: info
        x-displayName: Basic information
        description: |
          <b>EMPBaseURL</b>
          - The LG representative will provide information to the individual based on their needs.
            <table>
            <tr><th>Server Phase</th><th>EMPBaseURL</th><th>Remark</th></tr>
            <tr><td>QA</td><td>https://qt-{CNTRY}.m.lgaccount.com/emp/v2</td><td rowspan=2>CNTRY : CNTRY : ISO country code (2 digits)
                                                                                                  <br>
                                                                                                  example)<br>
                                                                                                - Korea: kr<br>
                                                                                                - USA: us<br>
                                                                                                - China: cn<br>
                                                                                                - Russian Federation: ru<br>
                                                                                                  ......</td></tr>
            <tr><td>OP</td><td>https://{CNTRY}.m.lgaccount.com/emp/v2</td></tr>
      - name: API Call Sequence
        x-displayName: API request sequence
        description: |
          
          <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" contentStyleType="text/css" height="705px" preserveAspectRatio="none" style="width:954px;height:705px;background:#FFFFFF;" version="1.1" viewBox="0 0 954 705" width="954px" zoomAndPan="magnify"><title>Request Authorization (Login)</title><defs/><g><text fill="#000000" font-family="sans-serif" font-size="14" font-weight="bold" lengthAdjust="spacing" textLength="238.1094" x="359.2439" y="27.9951">Request Authorization (Login)</text><rect fill="#FFFFFF" height="405.6641" style="stroke:#181818;stroke-width:1.0;" width="10" x="260.0288" y="149.7266"/><rect fill="#FFFFFF" height="397.6641" style="stroke:#181818;stroke-width:1.0;" width="10" x="499.5576" y="128.5938"/><rect fill="#FFFFFF" height="29.1328" style="stroke:#181818;stroke-width:1.0;" width="10" x="695.1943" y="336.3281"/><rect fill="#FFFFFF" height="44.2656" style="stroke:#181818;stroke-width:1.0;" width="10" x="695.1943" y="423.7266"/><rect fill="#FFFFFF" height="102.5313" style="stroke:#181818;stroke-width:1.0;" width="10" x="904.1802" y="394.5938"/><rect fill="none" height="442.6016" style="stroke:#000000;stroke-width:1.5;" width="937.5972" x="10" y="164.7266"/><rect fill="none" height="119.3359" style="stroke:#000000;stroke-width:1.5;" width="537.8359" x="20" y="188.8594"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="74" x2="74" y1="118.5938" y2="624.3281"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="264.1816" x2="264.1816" y1="118.5938" y2="624.3281"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="504.2793" x2="504.2793" y1="118.5938" y2="624.3281"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="700.1035" x2="700.1035" y1="118.5938" y2="624.3281"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="908.7632" x2="908.7632" y1="118.5938" y2="624.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="83.542" x="30" y="115.292">Service App</text><ellipse cx="74.771" cy="50.7969" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M74.771,58.7969 L74.771,85.7969 M61.771,66.7969 L87.771,66.7969 M74.771,85.7969 L61.771,100.7969 M74.771,85.7969 L87.771,100.7969 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="83.542" x="30" y="636.3232">Service App</text><ellipse cx="74.771" cy="648.125" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M74.771,656.125 L74.771,683.125 M61.771,664.125 L87.771,664.125 M74.771,683.125 L61.771,698.125 M74.771,683.125 L87.771,698.125 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="103.6943" x="213.1816" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="89.6943" x="220.1816" y="107.292">Proxy Server</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="103.6943" x="213.1816" y="623.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="89.6943" x="220.1816" y="643.3232">Proxy Server</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="86.5566" x="461.2793" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="72.5566" x="468.2793" y="107.292">Emp Front</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="86.5566" x="461.2793" y="623.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="72.5566" x="468.2793" y="643.3232">Emp Front</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="110.1816" x="645.1035" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="96.1816" x="652.1035" y="107.292">Emp Backend</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="110.1816" x="645.1035" y="623.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="96.1816" x="652.1035" y="643.3232">Emp Backend</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="56.834" x="880.7632" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="42.834" x="887.7632" y="107.292">Oauth</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="56.834" x="880.7632" y="623.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="42.834" x="887.7632" y="643.3232">Oauth</text><rect fill="#FFFFFF" height="405.6641" style="stroke:#181818;stroke-width:1.0;" width="10" x="260.0288" y="149.7266"/><rect fill="#FFFFFF" height="397.6641" style="stroke:#181818;stroke-width:1.0;" width="10" x="499.5576" y="128.5938"/><rect fill="#FFFFFF" height="29.1328" style="stroke:#181818;stroke-width:1.0;" width="10" x="695.1943" y="336.3281"/><rect fill="#FFFFFF" height="44.2656" style="stroke:#181818;stroke-width:1.0;" width="10" x="695.1943" y="423.7266"/><rect fill="#FFFFFF" height="102.5313" style="stroke:#181818;stroke-width:1.0;" width="10" x="904.1802" y="394.5938"/><polygon fill="#181818" points="248.0288,145.7266,258.0288,149.7266,248.0288,153.7266,252.0288,149.7266" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="74.771" x2="254.0288" y1="149.7266" y2="149.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="166.2578" x="81.771" y="144.6606">1. Login  (GET /authorize)</text><path d="M10,164.7266 L74.4429,164.7266 L74.4429,171.8594 L64.4429,181.8594 L10,181.8594 L10,164.7266 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="442.6016" style="stroke:#000000;stroke-width:1.5;" width="937.5972" x="10" y="164.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="19.4429" x="25" y="177.7935">alt</text><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="58.0293" x="89.4429" y="176.937">[success]</text><path d="M20,188.8594 L84.4429,188.8594 L84.4429,195.9922 L74.4429,205.9922 L20,205.9922 L20,188.8594 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="119.3359" style="stroke:#000000;stroke-width:1.5;" width="537.8359" x="20" y="188.8594"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="19.4429" x="35" y="201.9263">alt</text><polygon fill="#181818" points="487.5576,223.125,497.5576,227.125,487.5576,231.125,491.5576,227.125" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="270.0288" x2="493.5576" y1="227.125" y2="227.125"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="69.9258" x="277.0288" y="222.0591">2. Request</text><line style="stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="20" x2="557.8359" y1="236.125" y2="236.125"/><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="41.4004" x="25" y="246.3354">[Error]</text><polygon fill="#181818" points="85.771,267.0625,75.771,271.0625,85.771,275.0625,81.771,271.0625" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="79.771" x2="259.0288" y1="271.0625" y2="271.0625"/><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="63.7368" x="91.771" y="265.9966">400, 500</text><polygon fill="#181818" points="85.771,296.1953,75.771,300.1953,85.771,304.1953,81.771,300.1953" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="79.771" x2="498.5576" y1="300.1953" y2="300.1953"/><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="405.7866" x="91.771" y="295.1294">This service is not currently supported in your country.</text><polygon fill="#181818" points="683.1943,332.3281,693.1943,336.3281,683.1943,340.3281,687.1943,336.3281" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="509.5576" x2="689.1943" y1="336.3281" y2="336.3281"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="152.0073" x="516.5576" y="331.2622">3. Session Key Request</text><polygon fill="#181818" points="520.5576,361.4609,510.5576,365.4609,520.5576,369.4609,516.5576,365.4609" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="514.5576" x2="699.1943" y1="365.4609" y2="365.4609"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="161.6367" x="526.5576" y="360.395">4. Session Key Response</text><polygon fill="#181818" points="892.1802,390.5938,902.1802,394.5938,892.1802,398.5938,896.1802,394.5938" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="509.5576" x2="898.1802" y1="394.5938" y2="394.5938"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="181.6636" x="516.5576" y="389.5278">5. Session Key transmission</text><polygon fill="#181818" points="716.1943,419.7266,706.1943,423.7266,716.1943,427.7266,712.1943,423.7266" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="710.1943" x2="903.1802" y1="423.7266" y2="423.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="147.1577" x="722.1943" y="418.6606">6. Session key confrim</text><polygon fill="#181818" points="892.1802,463.9922,902.1802,467.9922,892.1802,471.9922,896.1802,467.9922" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="700.1943" x2="898.1802" y1="467.9922" y2="467.9922"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="119.3359" x="707.1943" y="447.7935">7. userNo, county,</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="170.8535" x="711.3267" y="462.9263">accountType transmission</text><polygon fill="#181818" points="520.5576,493.125,510.5576,497.125,520.5576,501.125,516.5576,497.125" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="514.5576" x2="908.1802" y1="497.125" y2="497.125"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="183.3013" x="526.5576" y="492.0591">8. Authorize Code Response</text><polygon fill="#181818" points="281.0288,522.2578,271.0288,526.2578,281.0288,530.2578,277.0288,526.2578" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="275.0288" x2="503.5576" y1="526.2578" y2="526.2578"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="151.0234" x="287.0288" y="521.1919">9. Code, URL Response</text><polygon fill="#181818" points="85.771,551.3906,75.771,555.3906,85.771,559.3906,81.771,555.3906" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="79.771" x2="264.0288" y1="555.3906" y2="555.3906"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="60.106" x="91.771" y="550.3247">10. Login</text><line style="stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="10" x2="947.5972" y1="564.3906" y2="564.3906"/><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="41.4004" x="15" y="574.6011">[Error]</text><polygon fill="#181818" points="85.771,595.3281,75.771,599.3281,85.771,603.3281,81.771,599.3281" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="79.771" x2="908.1802" y1="599.3281" y2="599.3281"/><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="223.6978" x="91.771" y="594.2622">Mismathing Redirect URI Error</text><!--SRC=[VLDTJzj047o_Nx7A4qY9QoZGOa4agDAg0jeAqZTUZlE6d73khdjdXFdrt5TiKgAysAlppEtCxDf9ro3SuhyMhOEBrYqroLVkf5QmTwqVfTfdZ0kd2KPtICzI85mOCm9kWHl332SdXJHSEHZz8VtIGO0XHOG91vkOsSh0TzBAHS0YL1y1brmyeQeZv27Lcw3Vt2kDdtMec9SocQPs5HmK49K3xFsOpU4Jpwvmd_76WMs5G6j37Pp9P-vmhJGQy3T5NHKS5kje63OMOKQaAQ4c7kMxLd2sy50Gkj5qJbXFpnwcHsKvXkEoPF6QNSZvKbgmELTVAkq1BH4grtHUgJ6Q7DRWpNIw9KzkbQEkO26HNdnACJw3-9nO1PyBFmnhmooliEkjzBnrjFaDay7vqVzKQxIoo6hymExxnb5KSBn9TSILNSbuCBHEOulFsBRNV3AmdpnRQBKWkTgXEVU52huKqFeiV-bnogaRtolW8jRppk2cb2rE1ZavXQz5_qiWVDCrRWqYUSan36juMaJA6FxUNc_bvULFExTUaeCoR-_xZNj7IekQfExQh1jfLzmjfNhqlMj9A9mNyZDVwDs-0G00]--></g></svg>
          
          This is the sequence that requests the EMP for the login process.
          
          <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" contentStyleType="text/css" height="440px" preserveAspectRatio="none" style="width:751px;height:440px;background:#FFFFFF;" version="1.1" viewBox="0 0 751 440" width="751px" zoomAndPan="magnify"><title>Request Access Token</title><defs/><g><text fill="#000000" font-family="sans-serif" font-size="14" font-weight="bold" lengthAdjust="spacing" textLength="176.0664" x="288.6499" y="27.9951">Request Access Token</text><rect fill="#FFFFFF" height="132.6641" style="stroke:#181818;stroke-width:1.0;" width="10" x="407.3472" y="128.5938"/><rect fill="#FFFFFF" height="29.1328" style="stroke:#181818;stroke-width:1.0;" width="10" x="700.9492" y="202.9922"/><rect fill="none" height="177.6016" style="stroke:#000000;stroke-width:1.5;" width="734.3662" x="10" y="164.7266"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="64" x2="64" y1="118.5938" y2="359.3281"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="411.5" x2="411.5" y1="118.5938" y2="359.3281"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="705.5322" x2="705.5322" y1="118.5938" y2="359.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="83.542" x="20" y="115.292">Service App</text><ellipse cx="64.771" cy="50.7969" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M64.771,58.7969 L64.771,85.7969 M51.771,66.7969 L77.771,66.7969 M64.771,85.7969 L51.771,100.7969 M64.771,85.7969 L77.771,100.7969 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="83.542" x="20" y="371.3232">Service App</text><ellipse cx="64.771" cy="383.125" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M64.771,391.125 L64.771,418.125 M51.771,399.125 L77.771,399.125 M64.771,418.125 L51.771,433.125 M64.771,418.125 L77.771,433.125 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="103.6943" x="360.5" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="89.6943" x="367.5" y="107.292">Proxy Server</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="103.6943" x="360.5" y="358.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="89.6943" x="367.5" y="378.3232">Proxy Server</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="56.834" x="677.5322" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="42.834" x="684.5322" y="107.292">Oauth</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="56.834" x="677.5322" y="358.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="42.834" x="684.5322" y="378.3232">Oauth</text><rect fill="#FFFFFF" height="132.6641" style="stroke:#181818;stroke-width:1.0;" width="10" x="407.3472" y="128.5938"/><rect fill="#FFFFFF" height="29.1328" style="stroke:#181818;stroke-width:1.0;" width="10" x="700.9492" y="202.9922"/><polygon fill="#181818" points="395.3472,145.7266,405.3472,149.7266,395.3472,153.7266,399.3472,149.7266" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="64.771" x2="401.3472" y1="149.7266" y2="149.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="318.5762" x="71.771" y="144.6606">1. (POST /Token) grant_type=authorization_code</text><path d="M10,164.7266 L74.4429,164.7266 L74.4429,171.8594 L64.4429,181.8594 L10,181.8594 L10,164.7266 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="177.6016" style="stroke:#000000;stroke-width:1.5;" width="734.3662" x="10" y="164.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="19.4429" x="25" y="177.7935">alt</text><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="58.0293" x="89.4429" y="176.937">[success]</text><polygon fill="#181818" points="688.9492,198.9922,698.9492,202.9922,688.9492,206.9922,692.9492,202.9922" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="417.3472" x2="694.9492" y1="202.9922" y2="202.9922"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="264.6021" x="424.3472" y="197.9263">2. Access Token, Refresh Token Request</text><polygon fill="#181818" points="428.3472,228.125,418.3472,232.125,428.3472,236.125,424.3472,232.125" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="422.3472" x2="704.9492" y1="232.125" y2="232.125"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="64.2383" x="434.3472" y="227.0591">3. 200 OK</text><polygon fill="#181818" points="75.771,257.2578,65.771,261.2578,75.771,265.2578,71.771,261.2578" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="69.771" x2="411.3472" y1="261.2578" y2="261.2578"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="275.082" x="81.771" y="256.1919">4. Aceess Token, Refresh Token Response</text><line style="stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="10" x2="744.3662" y1="270.2578" y2="270.2578"/><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="41.4004" x="15" y="280.4683">[Error]</text><polygon fill="#181818" points="75.771,301.1953,65.771,305.1953,75.771,309.1953,71.771,305.1953" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="69.771" x2="411.3472" y1="305.1953" y2="305.1953"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="12.4033" x="81.771" y="300.1294">5.</text><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="100.3374" x="98.3066" y="300.1294">400, 401, 412</text><polygon fill="#181818" points="75.771,330.3281,65.771,334.3281,75.771,338.3281,71.771,334.3281" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="69.771" x2="704.9492" y1="334.3281" y2="334.3281"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="12.4033" x="81.771" y="329.2622">6.</text><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="27.1362" x="98.3066" y="329.2622">500</text><!--SRC=[VL3BJW8n5DttAqvOQG93GN0n6IPXuSe5HDYJqhb8usHQRmiHlzvf6ICeSNFJntdUO49DUA7t0_c0kTRaFTRsZHe8eNImZDwA-6WqOUvS3yf3EIUSuc2qSQe9w2tPVfmGOSG9uUB3DMQX3c6VFcqy9N5pL84wS2kAGNc-v1Xbk5ikLciCKvPxl7AhiWadHxD8jsm-LJ2ssMXRaL1rW3-ay28fHAdaasESNTNgjsLtJ7xVjUog_yGvnqiJW-z4oF6GOImb5i-Yeb_Wph85nnOv9j6I_h7qpZQUBeNEIw3Q4vwOBLzhvfXcA7QsNQIsjUKPKrKMst8YPHyJEMh7Q5mCjsKnZA3o8dvYFzvaJwMyvFn98wYflW00]--></g></svg>  
          
          This is the order of token issuance of EMP.
          
          <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" contentStyleType="text/css" height="440px" preserveAspectRatio="none" style="width:620px;height:440px;background:#FFFFFF;" version="1.1" viewBox="0 0 620 440" width="620px" zoomAndPan="magnify"><title>Refresh Access Token</title><defs/><g><text fill="#000000" font-family="sans-serif" font-size="14" font-weight="bold" lengthAdjust="spacing" textLength="172.3477" x="224.9126" y="27.9951">Refresh Access Token</text><rect fill="#FFFFFF" height="132.6641" style="stroke:#181818;stroke-width:1.0;" width="10" x="372.9429" y="128.5938"/><rect fill="#FFFFFF" height="29.1328" style="stroke:#181818;stroke-width:1.0;" width="10" x="569.7559" y="202.9922"/><rect fill="none" height="177.6016" style="stroke:#000000;stroke-width:1.5;" width="603.1729" x="10" y="164.7266"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="64" x2="64" y1="118.5938" y2="359.3281"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="377.0957" x2="377.0957" y1="118.5938" y2="359.3281"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="574.3389" x2="574.3389" y1="118.5938" y2="359.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="83.542" x="20" y="115.292">Service App</text><ellipse cx="64.771" cy="50.7969" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M64.771,58.7969 L64.771,85.7969 M51.771,66.7969 L77.771,66.7969 M64.771,85.7969 L51.771,100.7969 M64.771,85.7969 L77.771,100.7969 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="83.542" x="20" y="371.3232">Service App</text><ellipse cx="64.771" cy="383.125" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M64.771,391.125 L64.771,418.125 M51.771,399.125 L77.771,399.125 M64.771,418.125 L51.771,433.125 M64.771,418.125 L77.771,433.125 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="103.6943" x="326.0957" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="89.6943" x="333.0957" y="107.292">Proxy Server</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="103.6943" x="326.0957" y="358.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="89.6943" x="333.0957" y="378.3232">Proxy Server</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="56.834" x="546.3389" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="42.834" x="553.3389" y="107.292">Oauth</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="56.834" x="546.3389" y="358.3281"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="42.834" x="553.3389" y="378.3232">Oauth</text><rect fill="#FFFFFF" height="132.6641" style="stroke:#181818;stroke-width:1.0;" width="10" x="372.9429" y="128.5938"/><rect fill="#FFFFFF" height="29.1328" style="stroke:#181818;stroke-width:1.0;" width="10" x="569.7559" y="202.9922"/><polygon fill="#181818" points="360.9429,145.7266,370.9429,149.7266,360.9429,153.7266,364.9429,149.7266" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="64.771" x2="366.9429" y1="149.7266" y2="149.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="284.1719" x="71.771" y="144.6606">1. (POST /Token) grant_type=refresh_token</text><path d="M10,164.7266 L74.4429,164.7266 L74.4429,171.8594 L64.4429,181.8594 L10,181.8594 L10,164.7266 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="177.6016" style="stroke:#000000;stroke-width:1.5;" width="603.1729" x="10" y="164.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="19.4429" x="25" y="177.7935">alt</text><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="58.0293" x="89.4429" y="176.937">[success]</text><polygon fill="#181818" points="557.7559,198.9922,567.7559,202.9922,557.7559,206.9922,561.7559,202.9922" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="382.9429" x2="563.7559" y1="202.9922" y2="202.9922"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="167.813" x="389.9429" y="197.9263">2. Refresh Token Request</text><polygon fill="#181818" points="393.9429,228.125,383.9429,232.125,393.9429,236.125,389.9429,232.125" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="387.9429" x2="573.7559" y1="232.125" y2="232.125"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="64.2383" x="399.9429" y="227.0591">3. 200 OK</text><polygon fill="#181818" points="75.771,257.2578,65.771,261.2578,75.771,265.2578,71.771,261.2578" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="69.771" x2="376.9429" y1="261.2578" y2="261.2578"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="173.0625" x="81.771" y="256.1919">4. Aceess Token Response</text><line style="stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="10" x2="613.1729" y1="270.2578" y2="270.2578"/><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="41.4004" x="15" y="280.4683">[Error]</text><polygon fill="#181818" points="75.771,301.1953,65.771,305.1953,75.771,309.1953,71.771,305.1953" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="69.771" x2="376.9429" y1="305.1953" y2="305.1953"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="12.4033" x="81.771" y="300.1294">5.</text><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="100.3374" x="98.3066" y="300.1294">400, 401, 412</text><polygon fill="#181818" points="75.771,330.3281,65.771,334.3281,75.771,338.3281,71.771,334.3281" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="69.771" x2="573.7559" y1="334.3281" y2="334.3281"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="12.4033" x="81.771" y="329.2622">6.</text><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="27.1362" x="98.3066" y="329.2622">500</text><!--SRC=[RP1FJuCm6CRl_HHFE6dYe23pG91a1qyUMDpkImVl797GsdQB-_QsPKxcl3IqF7z-xsixsnFUQAV9xB5e6Z86Q_b10sEYiL8ZMf4-TWrXeLG4OI2KOafespMT4eD5jDJowmGl8nqKoZzSQsfniFlmK_gl4DuTXQMps8LYLesN0ccCksMzMYC9AFTurovbOq-AdlN8kh41KlGMvX2mMJ3xb51H88ilWuKOT_iyaB6_tIDBE37xgKU1nnWPvwXVMKj_nESI9_R81VBOROqkMtCTHid1qDGvZaYz8RneBVLrI85vZ78dtPeQsKlj9cohSblbd3yWvwaxqgnCjbMPU54ruGtkft_TSywddXiQHaFx3G00]--></g></svg>
          
          This is the token re-issuance sequence for EMP.

      - name: Authorize API
        description: Authentication and authorization request API provided by EMP.
      - name: Token API
        description: This is the token issuance/reissue API provided by EMP.
    paths:
      /authorize:
        get:
          tags:
            - Authorize API
          summary: Request Authorization (Login)
          description: |-
            During this process, the service requests a login page from the EMP so the user can log in with an LG account (or 3rd party account linked with an LG account). When the user logs in, an authentication code is sent from the EMP.
            - Error Code
            <table>
            <tr><th> Service  </th><th> Error Code </th><th> Error Message </th><th> Remark </th></tr> 
            <tr><td> v1.0 DR </td><td> <code>400</code> </span> </td><td> app_id is invalid </td><td> The client_id is invalid. </td></tr> 
            <tr><td> v2.0 ThinQ Connect </td><td> <code>500</code> </td><td> Page not found </td><td> There is an error in the requested information. </td></tr> 
            <tr><td rowspan=2> common </td><td rowspan=2> An alert pop-up upon login </td><td> Mismathing Redirect URI Error </td><td> ogin requested with an unregistered redirect_uri </td></tr> 
            <tr><td> This service is not currently supported in your country. </td><td> The user didn't agree to the terms of a third party agreement </td></tr> 
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
                        Service (Application) identifier
                        - A value issued by the EMP (authorization server) in order to identify the service.
                        - You can request that your LG representative issue this value for you.
                    redirect_uri:
                      type: string
                      description: |-
                        A URI that the EMP uses to redirect the user's web browser to the service after performing a request
                        - If this API is called, the EMP redirects the user to a login page, completes the login process, and returns the user (user agent) back to the service. This value refers to the address where the user will be returned.
                        - You must perform UTF-8 encoding for the value.
                    response_type:
                      type: string
                      description: |-
                        Enter this as code.
                        - This denotes use of the Authorization Code Grant Type over the grant methods of the OAuth 2.0 protocol.
                    state:
                      type: string
                      description: |-
                        A value for defending against cross-site request forgery. Include this value when the EMP redirects the user's web browser back to the service after performing a request.
                  required:
                    - client_id
                    - redirect_uri
                    - response_type
                    - state
          responses:
            '200':
              description: |-
                The status values for success and error are the same, 200. If normal parameters are not returned, please refer to the Error Code table.
                <br><br>If successful, the EMP redirects the user's web browser (user agent) to the login page. If the user logs in successfully, the EMP redirects the web browser to the service again. For the redirect address, the EMP uses the redirect_uri value that was sent as a parameter.

                In addition, the EMP issues an authorization code to the service by including the code in the query string of redirect_uri when redirecting the web browser.
      /token?grant_type=authorization_code :
        post:
          tags:
            - Token API
          summary: Request Access Token
          description: |-
            Requests the EMP to issue a token. Upon success, the EMP provides an access token and a refresh token.
            - Error Code
            <table>
            <tr><th> Service  </th><th> Error Code </th><th> Error Message </th><th> Remark </th></tr> 
            <tr><td rowspan=2> v1.0 DR </td><td> <code>400</code> </span> </td><td> App_id Fail </td><td> Invalid client_id (i.e., client_id) </td></tr> 
            <tr><td> LG.OAUTH.EC.4001 </td><td> OAuth2 processing error </td><td> Invalid parameter  </td></tr> 
            <tr><td rowspan=6> v2.0 ThinQ Connect </td><td rowspan=4> <code>412</code> </td><td> required client_id </td><td> Parameter missing (client_id) </td></tr> 
            <tr><td> required backend_url </td><td> Parameter missing (backend_url) </td></tr> 
            <tr><td> required grant_type </td><td> Parameter missing (grant_type) </td></tr> 
            <tr><td> required refresh_token </td><td> Parameter missing (refresh_token) </td></tr> 
            <tr><td> <code>401</code> </td><td> not allowed client_id </td><td> Not allowed client_id </td></tr>
            <tr><td> <code>500</code> </td><td> oauth date time error </td><td> OAuth communication error </td></tr> 
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
                        Service (Application) identifier
                    redirect_uri:
                      type: string
                      description: |-
                        The same value as redirect_uri used when calling GET {{EMPBaseURL}}/authorize
                    code:
                      type: string
                      description: |-
                        An authorization code received from the EMP
                        - It is included in the redirect_uri as a query string after calling GET {{EMPBaseURL}}/authorize.
                    grant_type:
                      type: string
                      description: |-
                        Enter this as authorization_code.
                        <br>
                        <br>
                        Backend_url value sent after the EMP login
                        - When requesting an access token: enter it as authorization_code.
                        - When renewing an access token (reissuing an access token as a refresh token): enter it as refresh_token.
                      enum:
                        - authorization_code
                        - refresh_token
                    backend_url:
                      type: string
                      description: |-
                        Backend_url value sent after the EMP login
                  required:
                    - client_id
                    - redirect_uri
                    - code
                    - grant_type
          responses:
            '200':
              description: Success
                <br>The status values for success and error are the same, 200. If normal parameters are not returned, please refer to the Error Code table.
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      access_token:
                        type: string
                        description: |-
                          An OAuth 2.0 access token issued by the EMP
                        example:
                          xxxxxxxxxxxxxxxxxxxx
                      expires_in:
                        type: string
                        description: |-
                          Time remaining until an access token expires (unit: sec)
                        example:
                          3600
                      refresh_token:
                        type: string
                        description: |-
                          A token used to request a new access token from the EMP
                          - The value is sent only when grant_type is not entered as refresh_token when making the API's request
                        example:
                          xxxxxxxxxxxxxxxxxxxx
                      oauth2_backend_url:
                        type: string
                        description: |-
                          EMP backend url
                          - The value is sent only when grant_type is not entered as refresh_token when making the API's request
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
          summary: Refresh Access Token
          description: |-
            Requests the EMP to issue a token. Upon success, the EMP provides an access token and a refresh token.
            - Error Code
                <table>
                <tr><th> Service  </th><th> Error Code </th><th> Error Message </th><th> Remark </th></tr> 
                <tr><td rowspan=2> v1.0 DR </td><td> <code>400</code> </span> </td><td> App_id Fail </td><td> Invalid client_id (i.e., client_id) </td></tr> 
                <tr><td> LG.OAUTH.EC.4001 </td><td> OAuth2 processing error </td><td> Invalid parameter  </td></tr> 
                <tr><td rowspan=6> v2.0 ThinQ Connect </td><td rowspan=4> <code>412</code> </td><td> required client_id </td><td> Parameter missing (client_id) </td></tr> 
                <tr><td> required backend_url </td><td> Parameter missing (backend_url) </td></tr> 
                <tr><td> required grant_type </td><td> Parameter missing (grant_type) </td></tr> 
                <tr><td> required refresh_token </td><td> Parameter missing (refresh_token) </td></tr> 
                <tr><td> <code>401</code> </td><td> not allowed client_id </td><td> Not allowed client_id </td></tr>
                <tr><td> <code>500</code> </td><td> oauth date time error </td><td> OAuth communication error </td></tr> 
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
                        Service (Application) identifier
                    refresh_token:
                      type: string
                      description: |-
                        A refresh_token value included in the response of an access token issuance request at the time of login
                    grant_type:
                      type: string
                      description: |-
                        Enter this as refresh_token.
                        <br>
                        <br>
                        Through this API's request,
                        - When requesting an access token: enter it as authorization_code
                        - When renewing an access token (reissuing an access token as a refresh token): enter it as refresh_token
                      enum:
                        - authorization_code
                        - refresh_token
                    backend_url:
                      type: string
                      description: |-
                        Backend_url value sent after the EMP login
                  required:
                    - client_id
                    - refresh_token
                    - grant_type
          responses:
            '200':
              description: Success
                <br>The status values for success and error are the same, 200. If normal parameters are not returned, please refer to the Error Code table.
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      access_token:
                        type: string
                        description: |-
                          An OAuth 2.0 access token issued by the EMP
                        example:
                          xxxxxxxxxxxxxxxxxxxx
                      expires_in:
                        type: string
                        description: |-
                          Time remaining until an access token expires (unit: sec)
                        example:
                          3600
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
