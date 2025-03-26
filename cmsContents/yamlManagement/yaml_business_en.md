---
contents:
  lang: yaml
  code: >
    openapi: 3.1.0

    info:
      version: v1
      title: ThinQ Business API
    servers:
      - url: https://ap.biz.api.lge.com/v1
      - url: https://eu.biz.api.lge.com/v1
      - url: https://us.biz.api.lge.com/v1
      - url: https://ap-test.biz.api.lge.com/v1
      - url: https://eu-test.biz.api.lge.com/v1
      - url: https://us-test.biz.api.lge.com/v1
    tags:
      - name: Overview
        x-displayName: Overview
        description: |
          By using the **ThinQ Business API**, you can check or control the status of LG Electronics' Home appliances, Signage, Commercial HVAC, and IoT devices all at once. ThinQ Business API provides integrated APIs, allowing B2B partner software to directly connect with and manage the status of registered devices on LG Electronics' cloud platforms, such as LG ThinQ, LG Business Cloud, and LG BECON Cloud. For more details on the types of supported devices and the schema of the API call messages, please refer to the  **[Device Profile](/en/apiManage/device_profile)** page.
          
          To use the ThinQ Business API, you should **[request a partnership](/en/mypage/partner/landing)** first. Once approved, you can simulate a product and call APIs for testing without registering actual devices on LG Electronics' cloud platform, as the **ThinQ Business Simulator** will be provided as well
          
          ThinQ Business APIs are categorized based on what their purposes are.
            |API Type|Summary|
            |-|-|
            |Device API|API to get a list and status of enrolled devices and perform controls|
            |Push API|API for managing target devices to receive status changes on devices|
            |User API|API for managing users registered with B2B partner's service|
            |DR API|API for B2B partners to control a user's device as an electricity demand response (DR) service provider|
      - name: API Call Sequence
        x-displayName: API Call Sequence
        description: |
          Describes how to develop a service using the ThinQ Business API through a sequence of API calls.

          ## Issue API Token
          An API Token must be included in the HTTP request header of all ThinQ Business API calls. This API Token can be issued with a pair of pre-issued API Key and API Secret from LG Smart Solution API Developer and is valid for 24 hours.      

            - API to Use
              - [`POST /token`](#tag/auth/operation/createAPIToken)
              
            - Sequence
              1. Set the API Key and API Secret received from LG Smart Solution API Developer for the API Token issuance logic (API Secret will be sent via email when the API Key is issued).
              2. Call the Issue API Token API (POST /token) to get an API Token periodically. You'll need to make another API Token issuance request within 24 hours.  
              
              <?xml version="1.0" encoding="us-ascii" standalone="no"?><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" contentStyleType="text/css" height="447px" preserveAspectRatio="none" style="width:623px;height:447px;background:#FFFFFF;" version="1.1" viewBox="0 0 623 447" width="623px" zoomAndPan="magnify"><defs/><g><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="367" y="208.7622"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="367" y="306.439"/><rect fill="none" height="83.6768" style="stroke:#000000;stroke-width:1.5;" width="281" x="170.5" y="164.9414"/><rect fill="none" height="83.6768" style="stroke:#000000;stroke-width:1.5;" width="281" x="170.5" y="262.6182"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="46" x2="46" y1="84.2295" y2="363.2949"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="236.5" x2="236.5" y1="84.2295" y2="363.2949"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="371.5" x2="371.5" y1="84.2295" y2="363.2949"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="534.5" x2="534.5" y1="84.2295" y2="363.2949"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="77" x="5" y="81.1533">B2B Partner</text><ellipse cx="46.5" cy="13.5" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M46.5,21.5 L46.5,48.5 M33.5,29.5 L59.5,29.5 M46.5,48.5 L33.5,63.5 M46.5,48.5 L59.5,63.5 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="77" x="5" y="378.4482">B2B Partner</text><ellipse cx="46.5" cy="390.0244" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M46.5,398.0244 L46.5,425.0244 M33.5,406.0244 L59.5,406.0244 M46.5,425.0244 L33.5,440.0244 M46.5,425.0244 L59.5,440.0244 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="112" x="180.5" y="50"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="98" x="187.5" y="73.1533">Partner Service</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="112" x="180.5" y="362.2949"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="98" x="187.5" y="385.4482">Partner Service</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="139" x="302.5" y="50"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="125" x="309.5" y="73.1533">ThinQ Business API</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="139" x="302.5" y="362.2949"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="125" x="309.5" y="385.4482">ThinQ Business API</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="166" x="451.5" y="50"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="152" x="458.5" y="73.1533">LG Smart Solution API Developer</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="166" x="451.5" y="362.2949"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="152" x="458.5" y="385.4482">LG Smart Solution API Developer</text><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="367" y="208.7622"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="367" y="306.439"/><polygon fill="#181818" points="57.5,114.0854,47.5,118.0854,57.5,122.0854,53.5,118.0854" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="51.5" x2="533.5" y1="118.0854" y2="118.0854"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="188" x="63.5" y="113.229">provide API Key, API Secret pair</text><polygon fill="#181818" points="224.5,145.9414,234.5,149.9414,224.5,153.9414,228.5,149.9414" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="46.5" x2="230.5" y1="149.9414" y2="149.9414"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="166" x="53.5" y="145.085">set API Key, API Secret pair</text><path d="M170.5,164.9414 L247.5,164.9414 L247.5,174.7974 L237.5,184.7974 L170.5,184.7974 L170.5,164.9414 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="83.6768" style="stroke:#000000;stroke-width:1.5;" width="281" x="170.5" y="164.9414"/><text fill="#000000" font-family="LGEIText" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="28" x="185.5" y="180.9409">loop</text><text fill="#000000" font-family="LGEIText" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="93" x="262.5" y="179.6333">[within 24 hours]</text><polygon fill="#181818" points="355,204.7622,365,208.7622,355,212.7622,359,208.7622" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="236.5" x2="361" y1="208.7622" y2="208.7622"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="75" x="243.5" y="203.9058">POST /token</text><polygon fill="#181818" points="247.5,236.6182,237.5,240.6182,247.5,244.6182,243.5,240.6182" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="241.5" x2="371" y1="240.6182" y2="240.6182"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="60" x="253.5" y="235.7617">API Token</text><path d="M170.5,262.6182 L231.5,262.6182 L231.5,272.4741 L221.5,282.4741 L170.5,282.4741 L170.5,262.6182 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="83.6768" style="stroke:#000000;stroke-width:1.5;" width="281" x="170.5" y="262.6182"/><text fill="#000000" font-family="LGEIText" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="16" x="185.5" y="278.6177">alt</text><text fill="#000000" font-family="LGEIText" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="109" x="246.5" y="277.3101">[API Token expired]</text><polygon fill="#181818" points="355,302.439,365,306.439,355,310.439,359,306.439" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="236.5" x2="361" y1="306.439" y2="306.439"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="75" x="243.5" y="301.5825">POST /token</text><polygon fill="#181818" points="247.5,334.2949,237.5,338.2949,247.5,342.2949,243.5,338.2949" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="241.5" x2="371" y1="338.2949" y2="338.2949"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="60" x="253.5" y="333.4385">API Token</text><!--SRC=[XP11JyCm38NFpQ-mUWOXJPnwGAA2JHCJAsflY4EM6cQjIoB7AUFVasQLq0x0pVBx_FpiS23hDUiZzFYkuo1BP-LP7n4sgyTrXoTHseXZAEj53OrciSWbw00n8AiqAcJ8QojGpYgqo2CPp9G_zox1Ra_s1UeOo688SD-iCxipbzXc1LkFTjBX0KSSd9ztzpW64bHgBk3wBkUfmBCRgSSyyuHVLxbeqJ1AoaAi9cp2vs0LXAJyId-mYnu6vpoyVfAatB2uXRsB7DvKCNjCTZjJGRDjExWHTq2hYlGr6dMAbgugab_ayo5Tbj7sIW_oqm4yUMBi5Vpb2l_RVWC0]--></g></svg>
              
          ## Get Device Status
          To search the status of a device, the following Device API is used.      

            - API to Use
              - [`GET /devices`](#tag/Device-API/operation/getDevices)
              - [`GET /devices/{deviceId}/state`](#tag/Device-API/operation/getStatusOfDevice)
              
            - Sequence
              1. Your service needs to use Get Device List API (GET /devices) to retrieve the device list registered on the LG platform. This process only needs to be done once and does not need to be done every time after the list is retrieved.
              2. Check the deviceId value of the device whose status you want to get from the device list, and call Get Device Status API (GET /devices/{deviceId}/state) using this value.

              <?xml version="1.0" encoding="us-ascii" standalone="no"?><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" contentStyleType="text/css" height="258px" preserveAspectRatio="none" style="width:346px;height:258px;background:#FFFFFF;" version="1.1" viewBox="0 0 346 258" width="346px" zoomAndPan="magnify"><defs/><g><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="256" y="100.0503"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="256" y="170.7622"/><rect fill="none" height="83.6768" style="stroke:#000000;stroke-width:1.5;" width="330.5" x="10" y="56.2295"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="76" x2="76" y1="39.2295" y2="220.6182"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="260.5" x2="260.5" y1="39.2295" y2="220.6182"/><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="112" x="20" y="5"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="98" x="27" y="28.1533">Partner Service</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="112" x="20" y="219.6182"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="98" x="27" y="242.7715">Partner Service</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="139" x="191.5" y="5"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="125" x="198.5" y="28.1533">ThinQ Business API</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="139" x="191.5" y="219.6182"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="125" x="198.5" y="242.7715">ThinQ Business API</text><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="256" y="100.0503"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="256" y="170.7622"/><path d="M10,56.2295 L71,56.2295 L71,66.0854 L61,76.0854 L10,76.0854 L10,56.2295 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="83.6768" style="stroke:#000000;stroke-width:1.5;" width="330.5" x="10" y="56.2295"/><text fill="#000000" font-family="LGEIText" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="16" x="25" y="72.229">alt</text><text fill="#000000" font-family="LGEIText" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="125" x="86" y="70.9214">[If you need a new list]</text><polygon fill="#181818" points="244,96.0503,254,100.0503,244,104.0503,248,100.0503" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="76" x2="250" y1="100.0503" y2="100.0503"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="77" x="83" y="95.1938">GET /devices</text><polygon fill="#181818" points="87,127.9063,77,131.9063,87,135.9063,83,131.9063" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="81" x2="260" y1="131.9063" y2="131.9063"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="57" x="93" y="127.0498">device list</text><polygon fill="#181818" points="244,166.7622,254,170.7622,244,174.7622,248,170.7622" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="76" x2="250" y1="170.7622" y2="170.7622"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="161" x="83" y="165.9058">GET /device/{deviceId}/state</text><polygon fill="#181818" points="87,198.6182,77,202.6182,87,206.6182,83,202.6182" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="81" x2="260" y1="202.6182" y2="202.6182"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="69" x="93" y="197.7617">device state</text><!--SRC=[TOtB2i9034NNdQ-uk9VkNGWAjHH45Fi3iPFYO1lBJEe3yT-TMXUwS7L9pir9E3dfo5CBopNrZQxEeXjg6UiyAqg-gObONUKw4iLa6mTXZptxYwju0WhenjrliJmwsM7P1oSS0XRRujqzL8OQHL7ZVkuXp1OKuuh61JL8FYvCvx4wGvwLI2qFhqAaLAcxaFAWIJnhxmKZ7UzPhFblI1zZ5lQP1eqQy-txrRtv2m00]--></g></svg>
              
          ## Control Device
          To control devices, the following Device API is used.

            - API to Use
              - [`GET /devices`](#tag/Device-API/operation/getDevices)
              - [`GET /devices/{deviceId}/profile`](#tag/Device-API/operation/getProfileOfDevice)
              - [`POST /devices/{deviceId}/state`](#tag/Device-API/operation/controlDevice)
              
            - Sequence
              1. Your service needs to use Get Device List API (GET /devices) to retrieve the device list registered on the LG platform. This process only needs to be done once and does not need to be done every time after the list is retrieved.
              2. Check the deviceId value of the device to be controlled in the device list, and call Get Device Profile API (GET /devices/{device-id}/profile) using this value.
              3. Generate control commands for the device based on the device profile received in the API call response. The control command finds the attributes in the device profile that you want to control and expresses them as names and values.
              4. Using the deviceId and the control command, call Control Device API (POST /devices/{device-id}/state).
              5. Get the device control result back as an API response.

              <?xml version="1.0" encoding="us-ascii" standalone="no"?><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" contentStyleType="text/css" height="397px" preserveAspectRatio="none" style="width:360px;height:397px;background:#FFFFFF;" version="1.1" viewBox="0 0 360 397" width="360px" zoomAndPan="magnify"><defs/><g><rect fill="#FFFFFF" height="170.4238" style="stroke:#181818;stroke-width:1.0;" width="10" x="71" y="170.7622"/><rect fill="#FFFFFF" height="28" style="stroke:#181818;stroke-width:1.0;" width="10" x="76" y="242.4741"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="270" y="100.0503"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="270" y="170.7622"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="270" y="309.3301"/><rect fill="none" height="83.6768" style="stroke:#000000;stroke-width:1.5;" width="344.5" x="10" y="56.2295"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="76" x2="76" y1="39.2295" y2="359.186"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="274.5" x2="274.5" y1="39.2295" y2="359.186"/><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="112" x="20" y="5"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="98" x="27" y="28.1533">Partner Service</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="112" x="20" y="358.186"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="98" x="27" y="381.3394">Partner Service</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="139" x="205.5" y="5"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="125" x="212.5" y="28.1533">ThinQ Business API</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="139" x="205.5" y="358.186"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="125" x="212.5" y="381.3394">ThinQ Business API</text><rect fill="#FFFFFF" height="170.4238" style="stroke:#181818;stroke-width:1.0;" width="10" x="71" y="170.7622"/><rect fill="#FFFFFF" height="28" style="stroke:#181818;stroke-width:1.0;" width="10" x="76" y="242.4741"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="270" y="100.0503"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="270" y="170.7622"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="270" y="309.3301"/><path d="M10,56.2295 L71,56.2295 L71,66.0854 L61,76.0854 L10,76.0854 L10,56.2295 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="83.6768" style="stroke:#000000;stroke-width:1.5;" width="344.5" x="10" y="56.2295"/><text fill="#000000" font-family="LGEIText" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="16" x="25" y="72.229">alt</text><text fill="#000000" font-family="LGEIText" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="125" x="86" y="70.9214">[If you need a new list]</text><polygon fill="#181818" points="258,96.0503,268,100.0503,258,104.0503,262,100.0503" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="76" x2="264" y1="100.0503" y2="100.0503"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="77" x="83" y="95.1938">GET /devices</text><polygon fill="#181818" points="87,127.9063,77,131.9063,87,135.9063,83,131.9063" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="81" x2="274" y1="131.9063" y2="131.9063"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="57" x="93" y="127.0498">device list</text><polygon fill="#181818" points="258,166.7622,268,170.7622,258,174.7622,262,170.7622" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="81" x2="264" y1="170.7622" y2="170.7622"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="166" x="88" y="165.9058">GET /device/{deviceId}/profile</text><polygon fill="#181818" points="92,198.6182,82,202.6182,92,206.6182,88,202.6182" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="86" x2="274" y1="202.6182" y2="202.6182"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="74" x="98" y="197.7617">device profile</text><line style="stroke:#181818;stroke-width:1.0;" x1="86" x2="128" y1="234.4741" y2="234.4741"/><line style="stroke:#181818;stroke-width:1.0;" x1="128" x2="128" y1="234.4741" y2="247.4741"/><line style="stroke:#181818;stroke-width:1.0;" x1="87" x2="128" y1="247.4741" y2="247.4741"/><polygon fill="#181818" points="97,243.4741,87,247.4741,97,251.4741,93,247.4741" style="stroke:#181818;stroke-width:1.0;"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="97" x="93" y="229.6177">create command</text><polygon fill="#181818" points="258,305.3301,268,309.3301,258,313.3301,262,309.3301" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="81" x2="264" y1="309.3301" y2="309.3301"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="170" x="88" y="304.4736">POST /device/{deviceId}/state</text><polygon fill="#181818" points="87,337.186,77,341.186,87,345.186,83,341.186" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="81" x2="274" y1="341.186" y2="341.186"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="93" x="93" y="336.3296">command result</text><!--SRC=[TL7DIiD043vtd-AZTycz1q6XBG7HIFC2u-u45vDDs9bKHVhktJIfj3QUPdU-tsNbmuUE8ZLmN55VwwOD-amDuscxpal-KfDWzTPt51JB8bq2H-muxhtb9KZGZRjhOldkmoiUU_61HV1Gv2VkcpLKA_8AtssFmEn0QNoYzg86YyaBT_U9ki9sNI9pF4H9GicgtvFoOBE8h7qC6D5Hpy6P_nsodt7cxf1riQrypURNyVo8ouZhXBFa8c0whc0Z3nhRDWsb3ZUkZczMVteMBxlPeg99DDTgoa9aITysat04]--></g></svg>
              
          ## Subscribe to Device Push
          Uses the Push API to subscribe to push notifications on a device (Currently, only home appliances registered on LG ThinQ are supported.)

            - API to Use
              - [`GET /devices`](#tag/Device-API/operation/getDevices)
              - [`POST /push/{deviceId}/subscribe`](#tag/Event-API/operation/subscribePushMessages)
              
            - Sequence
              1. Your service needs to use Get Device List API (GET /devices) to retrieve the device list registered on the LG platform. This process only needs to be done once and does not need to be done every time after the list is retrieved.
              2. Check the deviceId value of the device you want to receive push notifications for from the device list, and call Subscribe to Device Push API (POST /push/{deviceId}/subscribe) using this value.
              3. In the API response, you get a result for the subscription success/failure.
              4. When a push notification occurs on your device, you'll receive a push message to the callback URL you registered. If there's a message you need to deliver to the user, you will handle it accordingly.

              <?xml version="1.0" encoding="us-ascii" standalone="no"?><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" contentStyleType="text/css" height="356px" preserveAspectRatio="none" style="width:442px;height:356px;background:#FFFFFF;" version="1.1" viewBox="0 0 442 356" width="442px" zoomAndPan="magnify"><defs/><g><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="284" y="100.0503"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="284" y="170.7622"/><rect fill="none" height="83.6768" style="stroke:#000000;stroke-width:1.5;" width="358.5" x="10" y="56.2295"/><rect fill="none" height="83.6768" style="stroke:#000000;stroke-width:1.5;" width="426.5" x="10" y="217.6182"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="76" x2="76" y1="39.2295" y2="318.2949"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="288.5" x2="288.5" y1="39.2295" y2="318.2949"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="397.5" x2="397.5" y1="39.2295" y2="318.2949"/><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="112" x="20" y="5"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="98" x="27" y="28.1533">Partner Service</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="112" x="20" y="317.2949"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="98" x="27" y="340.4482">Partner Service</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="139" x="219.5" y="5"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="125" x="226.5" y="28.1533">ThinQ Business API</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="139" x="219.5" y="317.2949"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="125" x="226.5" y="340.4482">ThinQ Business API</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="57" x="369.5" y="5"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="43" x="376.5" y="28.1533">Device</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="57" x="369.5" y="317.2949"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="43" x="376.5" y="340.4482">Device</text><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="284" y="100.0503"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="284" y="170.7622"/><path d="M10,56.2295 L71,56.2295 L71,66.0854 L61,76.0854 L10,76.0854 L10,56.2295 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="83.6768" style="stroke:#000000;stroke-width:1.5;" width="358.5" x="10" y="56.2295"/><text fill="#000000" font-family="LGEIText" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="16" x="25" y="72.229">alt</text><text fill="#000000" font-family="LGEIText" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="125" x="86" y="70.9214">[If you need a new list]</text><polygon fill="#181818" points="272,96.0503,282,100.0503,272,104.0503,276,100.0503" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="76" x2="278" y1="100.0503" y2="100.0503"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="77" x="83" y="95.1938">GET /devices</text><polygon fill="#181818" points="87,127.9063,77,131.9063,87,135.9063,83,131.9063" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="81" x2="288" y1="131.9063" y2="131.9063"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="57" x="93" y="127.0498">device list</text><polygon fill="#181818" points="272,166.7622,282,170.7622,272,174.7622,276,170.7622" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="76" x2="278" y1="170.7622" y2="170.7622"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="189" x="83" y="165.9058">POST /push/{deviceId}/subscribe</text><polygon fill="#181818" points="87,198.6182,77,202.6182,87,206.6182,83,202.6182" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="81" x2="288" y1="202.6182" y2="202.6182"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="32" x="93" y="197.7617">result</text><path d="M10,217.6182 L71,217.6182 L71,227.4741 L61,237.4741 L10,237.4741 L10,217.6182 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="83.6768" style="stroke:#000000;stroke-width:1.5;" width="426.5" x="10" y="217.6182"/><text fill="#000000" font-family="LGEIText" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="16" x="25" y="233.6177">alt</text><text fill="#000000" font-family="LGEIText" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="91" x="86" y="232.3101">[if push created]</text><polygon fill="#181818" points="300,257.439,290,261.439,300,265.439,296,261.439" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="294" x2="397" y1="261.439" y2="261.439"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="85" x="306" y="256.5825">push message</text><polygon fill="#181818" points="87,289.2949,77,293.2949,87,297.2949,83,293.2949" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="81" x2="288" y1="293.2949" y2="293.2949"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="85" x="93" y="288.4385">push message</text><!--SRC=[NP31JiCm38RFpLDOkq-zSq02RKoLfb6qle2RkCnQcrLnCa28TyTj8yHsIkB_z_VRaJFx4GCEuAZ3rCUNYuy770ZskstLq6SqAaUsFAAFiAhruId0aSALBQq01SQbTcjiJkpVu3a9UnA1fxgQlQszjMte3-Fcgy4-GjN1roM19tA0Udn0pn8D53aArezAUe3Tje5owHDLqKQ-OgGffGWKK_2PklIJT-QEKByU5J4cEPNVYxLoFwMaLcpWLgVvXyp4GAB_DC_97KojO0EfnvaYfsNuh0swFhwJALexrNF-dQYJ_G80]--></g></svg>
              
          ## Register for DR service
          After consulting with LG Electronics' API manager in advance, B2B partners can register users for the DR service using a DR API.

            - API to Use
              - [`POST /dr/users`](#tag/DR-API/operation/createDrUser)

            - Sequence
              1. LG Electronics users must be signed up for the LG ThinQ service and the LG home appliances that will be registered for the partner's DR service must be registered.
              2. The LG Electronics user attempts to sign up for the B2B partner's DR service.
              3. According to the OAuth 2.0 integration procedure of the LGE Members Platform (LMP), the partner service provides LG Electronics' login screen to the DR service and obtains OAuth integration information.
              4. LG Electronics' DR service acquires the OAuth integration information of the partner service according to the integration interface pre-defined with the partner service and saves the result of the partner service's user information API.
              5. When an LG Electronics user assigns a home and device to register with the DR service on the LG ThinQ mobile app, LG Electronics' DR service registers the device as a DR device.

              <?xml version="1.0" encoding="us-ascii" standalone="no"?><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" contentStyleType="text/css" height="698px" preserveAspectRatio="none" style="width:851px;height:698px;background:#FFFFFF;" version="1.1" viewBox="0 0 851 698" width="851px" zoomAndPan="magnify"><defs/><g><rect fill="#DDDDDD" height="686.2983" style="stroke:#181818;stroke-width:0.5;" width="223" x="182.5" y="6"/><text fill="#000000" font-family="LGEIText" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="99" x="244.5" y="20.9995">Partner Service</text><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="298" y="436.645"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="369.5" y="372.9331"/><rect fill="#FFFFFF" height="40.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="459" y="560.2129"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="606.5" y="213.6533"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="606.5" y="277.3652"/><rect fill="#FFFFFF" height="141.4238" style="stroke:#181818;stroke-width:1.0;" width="10" x="771" y="341.0771"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="37" x2="37" y1="84.2295" y2="610.0688"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="222.5" x2="222.5" y1="84.2295" y2="610.0688"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="302.5" x2="302.5" y1="84.2295" y2="610.0688"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="374.5" x2="374.5" y1="84.2295" y2="610.0688"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="463.5" x2="463.5" y1="84.2295" y2="610.0688"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="611.5" x2="611.5" y1="84.2295" y2="610.0688"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="775.5" x2="775.5" y1="84.2295" y2="610.0688"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="59" x="5" y="81.1533">End-User</text><ellipse cx="37.5" cy="13.5" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M37.5,21.5 L37.5,48.5 M24.5,29.5 L50.5,29.5 M37.5,48.5 L24.5,63.5 M37.5,48.5 L50.5,63.5 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="59" x="5" y="625.2222">End-User</text><ellipse cx="37.5" cy="636.7983" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M37.5,644.7983 L37.5,671.7983 M24.5,652.7983 L50.5,652.7983 M37.5,671.7983 L24.5,686.7983 M37.5,671.7983 L50.5,686.7983 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="72" x="186.5" y="50"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="58" x="193.5" y="73.1533">Frontend</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="72" x="186.5" y="609.0688"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="58" x="193.5" y="632.2222">Frontend</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="69" x="268.5" y="50"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="55" x="275.5" y="73.1533">Backend</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="69" x="268.5" y="609.0688"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="55" x="275.5" y="632.2222">Backend</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="54" x="347.5" y="50"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="40" x="354.5" y="73.1533">OAuth</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="54" x="347.5" y="609.0688"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="40" x="354.5" y="632.2222">OAuth</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="105" x="411.5" y="50"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="91" x="418.5" y="73.1533">LG ThinQ App</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="105" x="411.5" y="609.0688"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="91" x="418.5" y="632.2222">LG ThinQ App</text><rect fill="#E2E2F0" height="52.459" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="170" x="526.5" y="30.7705"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="72" x="575.5" y="53.9238">LMP OAuth</text><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="156" x="533.5" y="73.1533">(LGE Members Platform)</text><rect fill="#E2E2F0" height="52.459" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="170" x="526.5" y="609.0688"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="72" x="575.5" y="632.2222">LMP OAuth</text><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="156" x="533.5" y="651.4517">(LGE Members Platform)</text><rect fill="#E2E2F0" height="52.459" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="139" x="706.5" y="30.7705"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="125" x="713.5" y="53.9238">ThinQ Business API</text><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="81" x="735.5" y="73.1533">(DR Service)</text><rect fill="#E2E2F0" height="52.459" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="139" x="706.5" y="609.0688"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="125" x="713.5" y="632.2222">ThinQ Business API</text><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="81" x="735.5" y="651.4517">(DR Service)</text><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="298" y="436.645"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="369.5" y="372.9331"/><rect fill="#FFFFFF" height="40.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="459" y="560.2129"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="606.5" y="213.6533"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="606.5" y="277.3652"/><rect fill="#FFFFFF" height="141.4238" style="stroke:#181818;stroke-width:1.0;" width="10" x="771" y="341.0771"/><polygon fill="#181818" points="452,114.0854,462,118.0854,452,122.0854,456,118.0854" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="37.5" x2="458" y1="118.0854" y2="118.0854"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="246" x="44.5" y="113.229">register devices : Air Conditioner, ESS, TV</text><polygon fill="#181818" points="210.5,145.9414,220.5,149.9414,210.5,153.9414,214.5,149.9414" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="37.5" x2="216.5" y1="149.9414" y2="149.9414"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="161" x="44.5" y="145.085">sign up partner's DR service</text><polygon fill="#181818" points="48.5,177.7974,38.5,181.7974,48.5,185.7974,44.5,181.7974" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="42.5" x2="221.5" y1="181.7974" y2="181.7974"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="140" x="54.5" y="176.9409">direct to LGE login page</text><polygon fill="#181818" points="594.5,209.6533,604.5,213.6533,594.5,217.6533,598.5,213.6533" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="37.5" x2="600.5" y1="213.6533" y2="213.6533"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="76" x="44.5" y="208.7969">log in to LGE</text><polygon fill="#181818" points="314,241.5093,304,245.5093,314,249.5093,310,245.5093" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="308" x2="610.5" y1="245.5093" y2="245.5093"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="106" x="320" y="240.6528">authorization code</text><polygon fill="#181818" points="594.5,273.3652,604.5,277.3652,594.5,281.3652,598.5,277.3652" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="303" x2="600.5" y1="277.3652" y2="277.3652"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="125" x="310" y="272.5088">request access token</text><polygon fill="#181818" points="314,305.2212,304,309.2212,314,313.2212,310,309.2212" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="308" x2="610.5" y1="309.2212" y2="309.2212"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="78" x="320" y="304.3647">access token</text><polygon fill="#181818" points="759,337.0771,769,341.0771,759,345.0771,763,341.0771" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="303" x2="765" y1="341.0771" y2="341.0771"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="196" x="310" y="336.2207">register the user (POST /dr/users)</text><polygon fill="#181818" points="390.5,368.9331,380.5,372.9331,390.5,376.9331,386.5,372.9331" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="384.5" x2="770" y1="372.9331" y2="372.9331"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="168" x="396.5" y="368.0767">request access/refresh token</text><polygon fill="#181818" points="759,400.7891,769,404.7891,759,408.7891,763,404.7891" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="374.5" x2="765" y1="404.7891" y2="404.7891"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="121" x="381.5" y="399.9326">access/refresh token</text><polygon fill="#181818" points="319,432.645,309,436.645,319,440.645,315,436.645" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="313" x2="770" y1="436.645" y2="436.645"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="96" x="325" y="431.7886">request user info</text><polygon fill="#181818" points="759,464.501,769,468.501,759,472.501,763,468.501" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="303" x2="765" y1="468.501" y2="468.501"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="49" x="310" y="463.6445">user info</text><polygon fill="#181818" points="314,478.501,304,482.501,314,486.501,310,482.501" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="308" x2="775" y1="482.501" y2="482.501"/><polygon fill="#181818" points="233.5,492.501,223.5,496.501,233.5,500.501,229.5,496.501" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="227.5" x2="302" y1="496.501" y2="496.501"/><polygon fill="#181818" points="48.5,524.3569,38.5,528.3569,48.5,532.3569,44.5,528.3569" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="42.5" x2="221.5" y1="528.3569" y2="528.3569"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="133" x="54.5" y="523.5005">direct to LG ThinQ App</text><polygon fill="#181818" points="447,556.2129,457,560.2129,447,564.2129,451,560.2129" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="37.5" x2="453" y1="560.2129" y2="560.2129"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="190" x="44.5" y="555.3564">choose home and devices for DR</text><polygon fill="#181818" points="764,588.0688,774,592.0688,764,596.0688,768,592.0688" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="469" x2="770" y1="592.0688" y2="592.0688"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="182" x="476" y="587.2124">send chosen home and devices</text><!--SRC=[RLDDJ-Cm4BtxLunoMH1KFUoDmqe52aA29RljxcalhZrfB1exEvuWnAzdx92IjCqb6Vkz-NXl4b-SRpNf1YnMkjlnNV3yKpS8Z_VBXpM-iTA60q6nz7Rs9o8Le2Dqyg4suGsAKXDx95WXlJg3XG9v92Cxurhj6OexafJeRIP-9rkb-1XshStB2BMHy1ZqlEYu7Y0vKC81wKHDS8_tiAwT_mMBjirmtRO01vYd4dAAV_vCXeKdR3P84SgTvYfGSvw9kwQTqlgyrrrq7cE4HVaW_DlVWm0zov9IIIEO_SYbhu1mwoBBYSK4YtAqS0GtmLl7BeY4bx1ShIvX_NVF7CGIR7HR3rsRrH3ijmXIClObrHut4r8cNu5rX8Q1Gp8ITc7hl92tk4ykWmbCBa1kUbYoshrgnZnr0ipwBf8P0jOYLY3thbF3O895PN726R1z_ekBFFZ_3YE3DYRfnK5SLeJSaP-UZScMFhcVed6D_M1dvVDg3NDBynJ6SsK7fRAL9ohE2Il2M9-gV72tpvNQcAJAjPslmi0_FFXgVkJRo9YJldpjw7XPSc5JXn0HwY1_efOD7xP65bESLscdianfDT8V87Xv7-4_0000]--></g></svg>
              
          ## Create DR Event and Get Data
          Describes the process of registering a DR event and downloading monitoring data for a device before and after the DR event.

            - API to Use
              - [`POST /dr/events`](#tag/DR-API/operation/createDrEvent)
              - [`POST /dr/events/{eventId}/targets`](#tag/DR-API/operation/createEventTarget)
              - [`POST /dr/events/{eventId}/targets/{targetId}`](#tag/DR-API/operation/updateEventTarget)
              - [`POST /dr/events/{eventId}/targets/batch`](#tag/DR-API/operation/createEventTargetBatch)
              - [`POST /dr/events/{eventId}/targets/batch`](#tag/DR-API/operation/createEventTargetBatch)
              - [`POST /dr/data-zip/files`](#tag/DR-API/operation/createDataZipFile)
              - [`POST /dr/data-zip/files/{filename}`](#tag/DR-API/operation/downloadDataZipFile)
              
            - Sequence
              1. Call Create DR Event API (POST /dr/events) to register DR events on the LG DR service server.
              2. When the DR event is successfully registered, the DR Event ID (eventId) is retrieved.
              3. If the list of the devices that need to be participated in the DR event needs to be modified after the DR event has been created, call Modify DR Event target API.
              4. After the DR Event ends, download the monitoring data of the device within the DR event period.

              <?xml version="1.0" encoding="us-ascii" standalone="no"?><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" contentStyleType="text/css" height="760px" preserveAspectRatio="none" style="width:517px;height:760px;background:#FFFFFF;" version="1.1" viewBox="0 0 517 760" width="517px" zoomAndPan="magnify"><defs/><g><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="351" y="119.1709"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="351" y="209.8477"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="351" y="290.6685"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="351" y="371.4893"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="351" y="519.166"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="351" y="582.8779"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="463.5" y="646.5898"/><rect fill="none" height="342.8862" style="stroke:#000000;stroke-width:1.5;" width="435.5" x="10" y="75.459"/><rect fill="none" height="245.3184" style="stroke:#000000;stroke-width:1.5;" width="415.5" x="20" y="166.0269"/><rect fill="none" height="210.9917" style="stroke:#000000;stroke-width:1.5;" width="491.5" x="20" y="475.4541"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="86" x2="86" y1="58.459" y2="425.3452"/><line style="stroke:#A80036;stroke-width:1.0;stroke-dasharray:1.0,4.0;" x1="86" x2="86" y1="425.3452" y2="468.4541"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="86" x2="86" y1="468.4541" y2="703.4458"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="355.5" x2="355.5" y1="58.459" y2="425.3452"/><line style="stroke:#A80036;stroke-width:1.0;stroke-dasharray:1.0,4.0;" x1="355.5" x2="355.5" y1="425.3452" y2="468.4541"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="355.5" x2="355.5" y1="468.4541" y2="703.4458"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="468.5" x2="468.5" y1="58.459" y2="425.3452"/><line style="stroke:#A80036;stroke-width:1.0;stroke-dasharray:1.0,4.0;" x1="468.5" x2="468.5" y1="425.3452" y2="468.4541"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="468.5" x2="468.5" y1="468.4541" y2="703.4458"/><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="112" x="30" y="24.2295"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="98" x="37" y="47.3828">Partner Service</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="112" x="30" y="702.4458"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="98" x="37" y="725.5991">Partner Service</text><rect fill="#E2E2F0" height="52.459" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="139" x="286.5" y="5"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="125" x="293.5" y="28.1533">ThinQ Business API</text><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="81" x="315.5" y="47.3828">(DR Service)</text><rect fill="#E2E2F0" height="52.459" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="139" x="286.5" y="702.4458"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="125" x="293.5" y="725.5991">ThinQ Business API</text><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="81" x="315.5" y="744.8286">(DR Service)</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="66" x="435.5" y="24.2295"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="52" x="442.5" y="47.3828">AWS S3</text><rect fill="#E2E2F0" height="33.2295" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="66" x="435.5" y="702.4458"/><text fill="#000000" font-family="LGEIText" font-size="14" lengthAdjust="spacing" textLength="52" x="442.5" y="725.5991">AWS S3</text><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="351" y="119.1709"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="351" y="209.8477"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="351" y="290.6685"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="351" y="371.4893"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="351" y="519.166"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="351" y="582.8779"/><rect fill="#FFFFFF" height="31.856" style="stroke:#181818;stroke-width:1.0;" width="10" x="463.5" y="646.5898"/><path d="M10,75.459 L217,75.459 L217,85.3149 L207,95.3149 L10,95.3149 L10,75.459 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="342.8862" style="stroke:#000000;stroke-width:1.5;" width="435.5" x="10" y="75.459"/><text fill="#000000" font-family="LGEIText" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="162" x="25" y="91.4585">Create a new DR Request</text><polygon fill="#181818" points="339,115.1709,349,119.1709,339,123.1709,343,119.1709" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="86" x2="345" y1="119.1709" y2="119.1709"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="95" x="93" y="114.3145">POST /dr/events</text><polygon fill="#181818" points="97,147.0269,87,151.0269,97,155.0269,93,151.0269" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="91" x2="355" y1="151.0269" y2="151.0269"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="32" x="103" y="146.1704">result</text><path d="M20,166.0269 L81,166.0269 L81,175.8828 L71,185.8828 L20,185.8828 L20,166.0269 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="245.3184" style="stroke:#000000;stroke-width:1.5;" width="415.5" x="20" y="166.0269"/><text fill="#000000" font-family="LGEIText" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="16" x="35" y="182.0264">alt</text><text fill="#000000" font-family="LGEIText" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="157" x="96" y="180.7188">[if targets need to be added]</text><polygon fill="#181818" points="339,205.8477,349,209.8477,339,213.8477,343,209.8477" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="86" x2="345" y1="209.8477" y2="209.8477"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="191" x="93" y="204.9912">POST /dr/events/{eventId}/targets</text><polygon fill="#181818" points="97,237.7036,87,241.7036,97,245.7036,93,241.7036" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="91" x2="355" y1="241.7036" y2="241.7036"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="32" x="103" y="236.8472">result</text><line style="stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="20" x2="435.5" y1="250.7036" y2="250.7036"/><text fill="#000000" font-family="LGEIText" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="223" x="25" y="263.3955">[if a specific target needs to be updated]</text><polygon fill="#181818" points="339,286.6685,349,290.6685,339,294.6685,343,290.6685" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="86" x2="345" y1="290.6685" y2="290.6685"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="246" x="93" y="285.812">POST /dr/events/{eventId}/targets/{targetId}</text><polygon fill="#181818" points="97,318.5244,87,322.5244,97,326.5244,93,322.5244" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="91" x2="355" y1="322.5244" y2="322.5244"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="32" x="103" y="317.668">result</text><line style="stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="20" x2="435.5" y1="331.5244" y2="331.5244"/><text fill="#000000" font-family="LGEIText" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="175" x="25" y="344.2163">[if targets needs to be updated]</text><polygon fill="#181818" points="339,367.4893,349,371.4893,339,375.4893,343,371.4893" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="86" x2="345" y1="371.4893" y2="371.4893"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="227" x="93" y="366.6328">POST /dr/events/{eventId}/targets/batch</text><polygon fill="#181818" points="97,399.3452,87,403.3452,97,407.3452,93,403.3452" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="91" x2="355" y1="403.3452" y2="403.3452"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="32" x="103" y="398.4888">result</text><text fill="#000000" font-family="LGEIText" font-size="11" lengthAdjust="spacing" textLength="112" x="222.75" y="452.0371">&lt; DR Event execution &gt;</text><path d="M20,475.4541 L234,475.4541 L234,485.3101 L224,495.3101 L20,495.3101 L20,475.4541 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="210.9917" style="stroke:#000000;stroke-width:1.5;" width="491.5" x="20" y="475.4541"/><text fill="#000000" font-family="LGEIText" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="169" x="35" y="491.4536">Download monitoring data</text><polygon fill="#181818" points="339,515.166,349,519.166,339,523.166,343,519.166" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="86" x2="345" y1="519.166" y2="519.166"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="131" x="93" y="514.3096">POST /dr/data-zip/files</text><polygon fill="#181818" points="97,547.022,87,551.022,97,555.022,93,551.022" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="91" x2="355" y1="551.022" y2="551.022"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="48" x="103" y="546.1655">filename</text><polygon fill="#181818" points="339,578.8779,349,582.8779,339,586.8779,343,582.8779" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="86" x2="345" y1="582.8779" y2="582.8779"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="191" x="93" y="578.0215">POST /dr/data-zip/files/{filename}</text><polygon fill="#181818" points="97,610.7339,87,614.7339,97,618.7339,93,614.7339" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="91" x2="355" y1="614.7339" y2="614.7339"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="78" x="103" y="609.8774">download info</text><polygon fill="#181818" points="451.5,642.5898,461.5,646.5898,451.5,650.5898,455.5,646.5898" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="86" x2="457.5" y1="646.5898" y2="646.5898"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="96" x="93" y="641.7334">download the file</text><polygon fill="#181818" points="97,674.4458,87,678.4458,97,682.4458,93,678.4458" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="91" x2="467.5" y1="678.4458" y2="678.4458"/><text fill="#000000" font-family="LGEIText" font-size="13" lengthAdjust="spacing" textLength="16" x="103" y="673.5894">file</text><!--SRC=[hLBTQy8m47_lNt7uj26Q1z_64DnqGnYRiy9UzXARguRLIvTSLIR-xqjZAtx0FjWA9UdTxolfkJTDkRHo0GfJMMHyPuWVvGBXuNumdE2Q8zzcdUXS4aDZv3y8BSHebph11aW7-Qvs39pCDJt3JU4qeNFG6mrVwQ8_hecNWQbEIBsN6E9EQBbE5CsiANAujIWPGGBX2hp26DyBT1o1VofhQ7MzLhC9Lp1wYYSWb1MuH68NK1QviEGNvmyOAZ9Zq2cmj3DavvLH0HkOUXkbK0NCZ_J59gn3jHMLs9vxxegPmz9MWiinqQbEgWGXWAiI5Bdov_rJ1h7PRNpf1t4ER-4_Gqmb9_El_4b5vHkrsssuBd_je9G0N6DIi3O4NT-fnw1lLfGPgM1XIBEnccRWCyhlvg34j3vqBbATuT4yb0NoenxzJa9iQkBsK4tL-JIbvapITOBa7iHp3FwdUSA5V080]--></g></svg>
              
      - name: Base URL
        description: |
          The ThinQ Business API distinguishes the Base URL according to the location of the customer's device. Therefore, please select and apply the Base URL when calling the API by considering the region where the customer's device is located or the region where the B2B partner's business is located. Also, please note that the Base URLs for the Production environment and Simulator Testing environment are different, as follows. 
          ## Production Environment
          Use the Base URL below to call ThinQ Business API by utilizing **Business API Key** in the production environment.  

            |Region|Issue API Token API|ThinQ Business API|
            |-|-|-|
            |South Asia, East Asia and Pacific|https://ap.biz.api.lge.com|https://ap.biz.api.lge.com/v1|
            |America|https://us.biz.api.lge.com|https://us.biz.api.lge.com/v1|
            |Europe, Middle East, Africa|https://eu.biz.api.lge.com|https://eu.biz.api.lge.com/v1|

            
          ## Simulator Testing Environment
          Use the Base URL below to call ThinQ Business API by utilizing the **Test API Key** in the Simulator Testing environment.

            |Region|Issue API Token API|ThinQ Business API|
            |-|-|-|
            |South Asia, East Asia and Pacific|https://ap-test.biz.api.lge.com|https://ap-test.biz.api.lge.com/v1|
            |America|https://us-test.biz.api.lge.com|https://us-test.biz.api.lge.com/v1|
            |Europe, Middle East, Africa|https://eu-test.biz.api.lge.com|https://eu-test.biz.api.lge.com/v1|   
           
      - name: Codes
        x-displayName: Code Definition
        description: |
          Describes the types of code you can refer to when utilizing the ThinQ Business API.
          ## Country Code
          The country code used in ThinQ Business API Call supports the `ISO-3166 alpha-2` specification and can be used for countries, where LG ThinQ service is available. The supported country codes are shown in the table below.

            ### South Asia, East Asia and Pacific

            | Code | Name       | Code | Name       | Code | Name       | Code | Name       | Code | Name       | Code | Name       | Code | Name       | Code | Name       |
            |------|------------|------|------------|------|------------|------|------------|------|------------|------|------------|------|------------|------|------------|
            | AU   | Australia  | BD   | Bangladesh | CN   | China      | HK   | Hong Kong  | ID   | Indonesia  | IN   | India      | JP   | Japan      | KR   | South Korea|
            | LA   | Laos       | MY   | Malaysia   | NP   | Nepal      | NZ   | New Zealand| PH   | Philippines| SG   | Singapore  | TH   | Thailand   | TW   | Taiwan     |
            | VN   | Vietnam    | MM   | Myanmar    | KH   | Cambodia   | LK   | Sri Lanka  |      |            |      |            |      |            |      |            |
            
            ### America

            | Code | Name                | Code | Name                | Code | Name                | Code | Name                | Code | Name                | Code | Name                | Code | Name                | Code | Name                |
            |------|---------------------|------|---------------------|------|---------------------|------|---------------------|------|---------------------|------|---------------------|------|---------------------|
            | AG   | Antigua and Barbuda | AR   | Argentina           | AW   | Aruba               | BB   | Barbados            | BO   | Bolivia             | BR   | Brazil              | BS   | Bahamas             | BZ   | Belize              |
            | CA   | Canada              | CL   | Chile               | CO   | Colombia            | CR   | Costa Rica          | CU   | Cuba                | DM   | Dominica            | DO   | Dominican Republic  | EC   | Ecuador             |
            | GD   | Grenada             | GT   | Guatemala           | GY   | Guyana              | HN   | Honduras            | HT   | Haiti               | JM   | Jamaica             | KN   | Saint Kitts and Nevis| LC   | Saint Lucia         |
            | MX   | Mexico              | NI   | Nicaragua           | PA   | Panama              | PE   | Peru                | PR   | Puerto Rico         | PY   | Paraguay            | SR   | Suriname            | SV   | El Salvador         |
            | TT   | Trinidad and Tobago | US   | United States       | UY   | Uruguay             | VC   | Saint Vincent and the Grenadines | VE   | Venezuela           |      |                     |      |                     |      |                     |

            ### Europe, Middle East, Africa

            | Code | Name                | Code | Name                | Code | Name                | Code | Name                | Code | Name                | Code | Name                | Code | Name                | Code | Name                |
            |------|---------------------|------|---------------------|------|---------------------|------|---------------------|------|---------------------|------|---------------------|------|---------------------|------|---------------------|
            | AE   | United Arab Emirates| AF   | Afghanistan         | AL   | Albania             | AM   | Armenia             | AO   | Angola              | AT   | Austria             | AZ   | Azerbaijan          | BA   | Bosnia and Herzegovina |
            | BE   | Belgium             | BF   | Burkina Faso        | BG   | Bulgaria            | BH   | Bahrain             | BJ   | Benin               | BY   | Belarus             | CD   | Democratic Republic of the Congo | CF   | Central African Republic |
            | CG   | Republic of the Congo| CH   | Switzerland         | CI   | Ivory Coast         | CM   | Cameroon            | CV   | Cape Verde          | CY   | Cyprus              | CZ   | Czech Republic      | DE   | Germany             |
            | DJ   | Djibouti            | DK   | Denmark             | DZ   | Algeria             | EE   | Estonia             | EG   | Egypt               | ES   | Spain               | ET   | Ethiopia            | FI   | Finland             |
            | FR   | France              | GA   | Gabon               | GB   | United Kingdom      | GE   | Georgia             | GH   | Ghana               | GM   | Gambia              | GN   | Guinea              | GQ   | Equatorial Guinea   |
            | GR   | Greece              | HR   | Croatia             | HU   | Hungary             | IE   | Ireland             | IL   | Israel              | IQ   | Iraq                | IR   | Iran                | IS   | Iceland             |
            | IT   | Italy               | JO   | Jordan              | KE   | Kenya               | KG   | Kyrgyzstan          | KW   | Kuwait              | KZ   | Kazakhstan          | LB   | Lebanon             | LR   | Liberia             |
            | LT   | Lithuania           | LU   | Luxembourg          | LV   | Latvia              | LY   | Libya               | MA   | Morocco             | MD   | Moldova             | ME   | Montenegro          | MK   | North Macedonia     |
            | ML   | Mali                | MR   | Mauritania          | MT   | Malta               | MU   | Mauritius           | MW   | Malawi              | NE   | Niger               | NG   | Nigeria             | NL   | Netherlands         |
            | NO   | Norway              | OM   | Oman                | PK   | Pakistan            | PL   | Poland              | PS   | Palestine           | PT   | Portugal            | QA   | Qatar               | RO   | Romania             |
            | RS   | Serbia              | RW   | Rwanda              | SA   | Saudi Arabia        | SD   | Sudan               | SE   | Sweden              | SI   | Slovenia            | SK   | Slovakia            | SL   | Sierra Leone        |
            | SN   | Senegal             | SO   | Somalia             | ST   | Sao Tome and Principe| SY   | Syria               | TD   | Chad                | TG   | Togo                | TN   | Tunisia             | TR   | Turkey              |
            | TZ   | Tanzania            | UA   | Ukraine             | UG   | Uganda              | UZ   | Uzbekistan          | XK   | Kosovo              | YE   | Yemen               | ZA   | South Africa        | ZM   | Zambia              |
            | RU   | Russia              |      |                     |      |                     |      |                     |      |                     |      |                     |      |                     |      |                     |

          ## Response code
          When calling each API, a response code, which provides additional information on the type of response, may be retrieved with an HTTP status code. This response code is included in the HTTP response header and response body message, and its definition may vary by API type. Response codes supported by each type of API are listed below.
          ### Device API, Push API, User API

            <table>
              <thead>
                <tr>
                  <th width="120">Status Code</th>
                  <th width="250">Header : <code>X-Response-Code</code></th>
                  <th>Body</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td><code>200</code></td>
                  <td><code>6200</code> : OK</td>
                  <td>Data in a normal response schema</td>
                </tr>
                <tr>
                  <td><code>206</code></td>
                  <td><code>6201</code> : Partial Success</td>
                  <td>Data in a normal response schema</td>
                </tr>
                <tr>
                  <td><code>400</code></td>
                  <td><code>6400</code> : Bad Request</td>
                  <td>
                      <code>code</code> field in the error response schema :<br>
                      <code>1000</code> : Undefined error (the error to analyze) <br>
                      <code>1101</code> : Required input items are missing. <br>
                      <code>1102</code> : Parameters that are not permitted have been entered. <br>
                      <code>1104</code> : Message ID grammar is incorrect. <br>
                      <code>1216</code> : Values in the header are not correct. <br>
                      <code>1217</code> : The device is deleted. <br> 
                      <code>1218</code> : The token is not valid. <br> 
                      <code>2202</code> : The product family is not supported. <br> 
                      <code>2205</code> : The device status data is not transmitted normally or the transmitted data is not parsed normally. <br> 
                      <code>2207</code> : The control command is not invalid. (The control command contains undefined resources or properties.) <br> 
                      <code>2208</code> : Failed to control the device. <br> 
                      <code>2209</code> : The response from the device is being delayed. <br> 
                      <code>2210</code> : Retry the request. <br>
                      <code>2214</code> : Failed to request. <br>
                      <code>2301</code> : The device does not support control command. (If the remoteControl is false)  <br>
                      <code>2302</code> : In the state, the control command is not supported. <br>
                      <code>2303</code> : The control command cannot be processed because the device is in an error state. <br>
                      <code>2304</code> : The control command cannot be processed because the device is powered off. <br>
                      <code>2305</code> : In the mode, the control command is not supported. <br>
                  </td>
                </tr>
                <tr>
                  <td><code>401</code></td>
                  <td><code>6401</code> : Unauthorized</td>
                  <td>
                      <code>code</code> field in the error response schema :<br>
                      <code>1307</code> : The country is not supported. <br>
                      <code>1308</code> : Unable to get the device control authority (The ThinQ App has the authority.) <br>
                      <code>1311</code> : The request format is wrong. <br>
                  </td>
                </tr>
                <tr>
                  <td><code>403</code></td>
                  <td><code>6403</code> : Forbidden</td>
                  <td>
                      N/A
                  </td>
                </tr>
                <tr>
                  <td><code>404</code></td>
                  <td><code>6404</code> : Not Found</td>
                  <td>
                      <code>code</code> field in the error response schema :<br>
                      <code>1202</code> : There is no registered user. <br>
                      <code>1204</code> : There is no registered user <br>
                      <code>1205</code> : There is no registered device. <br>
                      <code>1206</code> : There is no subscribed push. <br>
                      <code>1207</code> : There is a subscribed push (an identical push already exists). <br>
                      <code>1210</code> : The device is not allowed by the service. <br> 
                      <code>1211</code> : The device is not registered by the user. <br> 
                      <code>1212</code> : The device is not owned by the user. <br> 
                      <code>1213</code> : There is no registered device. <br> 
                      <code>1214</code> : The device does not allow the event subscription. <br> 
                      <code>1224</code> : The device ID is not allowed.
                  </td>
                </tr>
                <tr>
                  <td><code>406</code></td>
                  <td><code>6406</code> : Not Supported Resource</td>
                  <td>
                      <code>code</code> field in the error response schema :<br>
                      <code>1219</code> : The product model is not supported. <br>
                      <code>1220</code> : The feature is not supported. (The feature is not allowed for the product model.) <br>
                      <code>1221</code> : The device type is not supported. (The device type is not allowed for the service key.)
                  </td>
                </tr>
                <tr>
                  <td><code>416</code></td>
                  <td><code>6416</code> : Invalid Device Status</td>
                  <td>
                      <code>code</code> field in the error response schema :<br>
                      <code>1222</code> : The device is not connected.  <br>
                      <code>1223</code> : The device status values delivered are invalid.
                  </td>
                </tr>
                <tr>
                  <td><code>429</code></td>
                  <td><code>6429</code> : Too Many Requests</td>
                  <td>
                      N/A
                  </td>
                </tr>
                <tr>
                  <td><code>500</code></td>
                  <td><code>6516</code> : Internal Server Error</td>
                  <td>
                      <code>code</code> field in the error response schema :<br>
                      <code>0000</code> : Undefined error (the error to analyze) <br>
                      <code>2000</code> : Internal server error
                  </td>
                </tr>
              </tbody>
            </table>

          ### DR API
          <table>
            <thead>
              <tr>
                <th width="120">Status Code</th>
                <th width="400">Header : <code>X-Response-Code</code></th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td><code>200</code></td>
                <td><code>2000</code> : OK</td>
              </tr>
              <tr>
                <td><code>400</code></td>
                <td>
                    <code>4000</code> : Bad Request <br>
                    <code>4101</code> : Missing or Invalid Parameter(s) in Request Header <br>
                    <code>4102</code> : Missing or Invalid Parameter(s) in Request Body <br>
                    <code>4103</code> : Missing or Invalid Token
                </td>
              </tr>
              <tr>
                <td><code>401</code></td>
                <td>
                    <code>6401</code> : Unauthorized
                </td>
              </tr>
              <tr>
                <td><code>403</code></td>
                <td>
                    <code>4201</code> : Forbidden <br>
                    <code>6403</code> : Forbidden
                </td>
              </tr>
              <tr>
                <td><code>404</code></td>
                <td>
                    <code>4301</code> : Resource Not Found: User <br>
                    <code>4302</code> : Resource Not Found: Event <br>
                    <code>4303</code> : Resource Not Found: Event Target <br>
                    <code>4304</code> : Resource Not Found: Device <br>
                    <code>4305</code> : Resource Not Found: Zip File task <br>
                    <code>4306</code> : Resource Not Found: Zip File <br>
                    <code>4307</code> : Resource Not Found: Partner <br>
                    <code>4308</code> : Resource Not Found: Group <br>
                    <code>4313</code> : Resource Not Found: Partner User <br>
                    <code>6404</code> : Not Found
                </td>
              </tr>
              <tr>
                <td><code>409</code></td>
                <td>
                    <code>4309</code> : Resource Already Exists: User <br>
                    <code>4310</code> : Resource Already Exists: Event <br>
                    <code>4311</code> : Resource Already Exists: Event Target <br>
                    <code>4312</code> : Resource Already Exists: Partner User <br>
                    <code>4314</code> : Resource Already Exists: Group <br>
                    <code>4315</code> : Resource Already Exists: User
                </td>
              </tr>          
              <tr>
                <td><code>429</code></td>
                <td><code>6429</code> : Too Many Requests</td>
              </tr>
              <tr>
                <td><code>500</code></td>
                <td>
                    <code>5000</code> : Internal Server Error
                </td>
              </tr>
            </tbody>
          </table>
      - name: auth
        x-displayName: API Authentication
        description: |
          The following API is used to perodically issue an `API Token` using a pair of `API Key` and `API Secret`, which is provided by LG Smart Solution API Developer to B2B partners. The `API Token` issued by this API must be included in the HTTP request header when calling the ThinQ Business API.
      - name: Device API
        description: |
          The Device API is used to search a list of registered devices, search the profile and status of specific devices, or control devices. If the Device API for multiple types of LG Electronics products purchased by a company is used, the LG Electronics account on which the products are registered or the location information can be assigned in the LG Smart Solution API Developer in advance. For home appliances only, it's possible to assign a specific LG Electronics user when calling the Device API to access the devices of that user. Before calling the Device API, the B2B partner or the partner's customer must register the device. As shown below, the purchased device must be registered and signed up for the service on the appropriate LG Electronics platform, depending on the type of device.

            |Device Type|LG Electronics Platform|
            |-|-|
            |Appliances and other IoT devices|LG ThinQ (mobile app)|
            |Signage|LG Business Cloud (https://lgbusinesscloud.com)|
            |Commercial HVAC|LG BECON Cloud (https://beconcloud.lge.com)|
      - name: Push API
        description: |
          The Push API is used to allow B2B partners' services to receive or stop receiving messages whenever there is a change in the status of a specific device. This API is currently available to products registered on LG ThinQ only, but more products will be supported in the future. In order for the B2B partner service to receive the device status, the Callback call information of the B2B partner service must be registered in the LG Smart Solution API Developer in advance. The types of device status changes provided by Callback are as follows. The conditions for the Callback subscription may differ by type.

            | Push Type | Description | Pre-Condition |
            |-|-|-|
            | DEVICE_PUSH | Device operation is completed, Part replacements is required. <br> (e.g. washer - washing completed, air purifier - filter replacement) | Subscribe to Device Push API called |
            | DEVICE_REGISTERED | Device added | Get Device List API called|
            | DEVICE_UNREGISTERED | Device has been deleted | Get Device List API called|
            | DEVICE_ALIAS_CHANGED | Device's alias changed | Get Device List API called|

          <br/><br/>
          ### DEVICE_PUSH
            <SchemaDefinition
            schemaRef="#/components/schemas/push-callback-device-push-schema"
            exampleRef="#/components/examples/push-callback-device-push-example" />

          ### DEVICE_REGISTERED
            <SchemaDefinition
            schemaRef="#/components/schemas/push-callback-device-registered-schema"
            exampleRef="#/components/examples/push-callback-device-registered-example" />

          ### DEVICE_UNREGISTERED
            <SchemaDefinition
            schemaRef="#/components/schemas/push-callback-device-unregistered-schema"
            exampleRef="#/components/examples/push-callback-device-unregistered-example" />

          ### DEVICE_ALIAS_CHANGED
            <SchemaDefinition
            schemaRef="#/components/schemas/push-callback-device-alias-changed-schema"
            exampleRef="#/components/examples/push-callback-device-alias-changed-example" />
      - name: User API
        description: |
          The User API is used to manage the information of LG Electronics users who have registered for partner services. <b> Currently, the API is only available to devices registered on LG ThinQ.</b>
      - name: DR API
        description: |
          With B2B partners as demand response (DR) providers, the DR API is used to control the devices of LG Electronics users, who are DR service users. B2B partners can utilize this API to manage LG Electronics users who are DR service users, register DR events that may reduce or change the power consumption of LG Electronics users during certain power peak hours in response to the electricity demand, and search whether the DR target device participates in DR events. The DR target devices are currently limited to air conditioners and TVs, but more products will be supported in the future. The DR service using this API follows the following procedure.
          ### 1. Device registration and signing-up for DR service 

            - LG ThinQ users register their DR devices on the LG ThinQ app and sign up for a B2B partner's DR service.
            
            <img src="https://smartsolution.developer.lge.com/assets/images/img_DR_01.png" width="600"/>

          ### 2. DR request issuance

            - B2B partners register a DR event using the DR API before the DR event starts.
            - LG Electronics delivers the registered DR event to the target device before a specified start time.
            - LG ThinQ users receive a notification on the LG ThinQ app before the DR event starts.

              <img src="https://smartsolution.developer.lge.com/assets/images/img_DR_02.png" width="600"/>

          ### 3. Status monitoring

            - LG Electronics monitors and records the status of the device while the DR event takes place. 
            - the B2B partners download monitoring data using the DR API.

              <img src="https://smartsolution.developer.lge.com/assets/images/img_DR_03.png" width="600"/>

          ### 4. DR service billing

            - Based on the data provided by the DR API, the B2B partner calculates a bill based on the DR participation rate of the DR service users and provides the bill details to the users.

            <img src="https://smartsolution.developer.lge.com/assets/images/img_DR_04.png" width="600"/>        
    paths:
      /token:
        post:
          tags:
            - auth
          summary: Issue API Token
          description: |
            An `API Key` and an `API Token` are required when calling any API that belongs to the ThinQ Business API.
            This API is used to issue an `API Token` and the issued `API Token` is valid for **24 hours**, so the client must be prepared to call this API to obtain a new `API Token`.
            An `API Secret` is only used to issue an `API Token`.
          operationId: createAPIToken
          security:
            - ThinQ_Business_API_Key: []
          servers:
            - url: https://ap.biz.api.lge.com
            - url: https://us.biz.api.lge.com
            - url: https://eu.biz.api.lge.com
            - url: https://ap-test.biz.api.lge.com
            - url: https://us-test.biz.api.lge.com
            - url: https://eu-test.biz.api.lge.com
          parameters:
            - name: X-Api-Secret
              in: header
              required: true
              schema:
                type: string
              description: |
                The `API Secret`, a secret string obtained by the B2B partner paired with the `API Key`.
              example: 5f3c0222-cb51-4ea8-bae9-60879e8760bb
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/api-token-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
            '500':
              description: Internal Server Error
      /devices:
        get:
          tags:
            - Device API
          summary: Get Device List
          description: Get a list of all devices registered to the LG Electronics account.
          operationId: getDevices
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Use-Account'
            - required: false
              $ref: '#/components/parameters/Authorization'
            - required: false
              $ref: '#/components/parameters/X-Country-Code'
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6200`: Successful operation'
                  example: 6200
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/device-list-res'
                  example:
                    value:
                      messageId: 2ADaRijIk8CvaSHVPeEWNw
                      timestamp: '2024-10-01T06:23:20.866279'
                      response:
                        - deviceId: 8a6bc612a906a788e021f907819a8fe6a354c972e72d17c6c270ee94b6d9e4ca
                          deviceInfo:
                            deviceType: DEVICE_AIR_PURIFIER
                            modelName: AIR_910604_WW
                            alias: My New AIR PURIFIER
                            reportable: 'true'
                        - deviceId: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
                          deviceInfo:
                            deviceType: DEVICE_WASHTOWER_WASHER
                            alias: My New WashTower Washer
                            modelName: FAKPK21021
                            reportable: 'true'
                            groupId: '171807013576723372'
                        - deviceId: bab8196f0d3529ce1243457333fcbed8fa2d7bc17f64e4e0a7f48377abf4494f
                          deviceInfo:
                            deviceType: DEVICE_WASHTOWER_DRYER
                            alias: My New WashTower Dryer
                            modelName: SDH_WT4101_KR
                            reportable: 'true'
                            groupId: '171807013576723372'
                        - deviceId: df37d9f9fdf9360255754b1e916008f31b29d44dd6dac1a026b726f0496bd755
                          deviceInfo:
                            deviceType: DEVICE_SIGNAGE
                            alias: SKJY1107 UH5E
                            modelName: 65UH5E
                        - deviceId: 7bd6ef74940bda3c9007a3abbd7a2d4f224134f9ba513dc32691cba371de8304
                          deviceInfo:
                            deviceType: DEVICE_IDU
                            alias: AC_00
                            parentId: e75adfb7f3aea29228198bf06a4213ad3a60644d21e45357cb083fe306c07bf1
                        - deviceId: e75adfb7f3aea29228198bf06a4213ad3a60644d21e45357cb083fe306c07bf1
                          deviceInfo:
                            deviceType: DEVICE_ODU
                            alias: ODU[00]
            '400':
              description: Bad request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6400`: Bad Request'
                  example: 6400
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6401`: Unauthorized'
                  example: 6401
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '403':
              description: Forbidden
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6403`: Forbidden'
                  example: 6403
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found Resource
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6404`: Not Found Resource'
                  example: 6404
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '406':
              description: Not Supported Resource
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6406`: Not Supported Resource'
                  example: 6406
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '416':
              description: Invalid Device Status
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6416`: Invalid Device Status'
                  example: 6416
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6500`: Internal Server Error'
                  example: 6500
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
      /devices/{deviceId}/profile:
        get:
          tags:
            - Device API
          summary: Get Device Profile List
          description: Get profile for a specific device.
          operationId: getProfileOfDevice
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/deviceId'
            - required: true
              $ref: '#/components/parameters/X-Use-Account'
            - required: false
              $ref: '#/components/parameters/Authorization'
            - required: false
              $ref: '#/components/parameters/X-Country-Code'
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6200`: Successful operation'
                  example: 6200
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/device-profile-res'
                  examples:
                    Refrigerator:
                      $ref: '#/components/examples/refrigerator-profile-example'
                    Washer:
                      $ref: '#/components/examples/washer-profile-example'
                    Dryer:
                      $ref: '#/components/examples/dryer-profile-example'
                    Air Conditioner:
                      $ref: '#/components/examples/air_conditioner-profile-example'
                    Air Purifier:
                      $ref: '#/components/examples/air_purifier-profile-example'
                    Robot Cleaner:
                      $ref: '#/components/examples/robot_cleaner-profile-example'
                    Oven:
                      $ref: '#/components/examples/oven-profile-example'
                    Dish Washer:
                      $ref: '#/components/examples/dish_washer-profile-example'
                    Styler:
                      $ref: '#/components/examples/styler-profile-example'
                    Water Purifier:
                      $ref: '#/components/examples/water_purifier-profile-example'
                    Dehumidifier:
                      $ref: '#/components/examples/dehumidifier-profile-example'
                    Ceiling Fan:
                      $ref: '#/components/examples/ceiling_fan-profile-example'
                    Wine Cellar:
                      $ref: '#/components/examples/wine_cellar-profile-example'
                    Kimchi Refrigerator:
                      $ref: '#/components/examples/kimchi_refrigerator-profile-example'
                    Home Brew:
                      $ref: '#/components/examples/home_brew-profile-example'
                    Plant Cultivator:
                      $ref: '#/components/examples/plant_cultivator-profile-example'
                    WashTower (Washer):
                      $ref: '#/components/examples/washtower_washer-profile-example'
                    WashTower (Dryer):
                      $ref: '#/components/examples/washtower_dryer-profile-example'
                    WashTower:
                      $ref: '#/components/examples/washtower-profile-example'
                    Cooktop:
                      $ref: '#/components/examples/cooktop-profile-example'
                    Hood:
                      $ref: '#/components/examples/hood-profile-example'
                    Microwave Oven:
                      $ref: '#/components/examples/microwave_oven-profile-example'
                    System Boiler:
                      $ref: '#/components/examples/system_boiler-profile-example'
                    Air Purifier Fan:
                      $ref: '#/components/examples/air_purifier_fan-profile-example'
                    Stick Cleaner:
                      $ref: '#/components/examples/stick_cleaner-profile-example'
                    Water Heater:
                      $ref: '#/components/examples/water_heater-profile-example'
                    Main WashCombo:
                      $ref: '#/components/examples/main_washcombo-profile-example'
                    Mini WashCombo:
                      $ref: '#/components/examples/mini_washcombo-profile-example'
                    Humidifier:
                      $ref: '#/components/examples/humidifier-profile-example'
                    Outdoor unit of a system air conditioner registered in BECON Cloud:
                      $ref: '#/components/examples/odu-profile-example'
                    Indoor unit of a system air conditioner registered in BECON Cloud:
                      $ref: '#/components/examples/idu-profile-example'
                    Signage registered in the Business Cloud:
                      $ref: '#/components/examples/signage-profile-example'
                    Smart motion sensor:
                      $ref: '#/components/examples/motion_sensor-profile-example'
                    Smart temperature and humidity sensor:
                      $ref: '#/components/examples/temperature_humidity_sensor-profile-example'
                    Smart door sensor:
                      $ref: '#/components/examples/door_sensor-profile-example'
                    Smart button:
                      $ref: '#/components/examples/button-profile-example'
                    Smart light switch:
                      $ref: '#/components/examples/light_switch-profile-example'
                    Smart door lock:
                      $ref: '#/components/examples/door_lock-profile-example'
                    Smart push-pull door lock:
                      $ref: '#/components/examples/push_pull_door_lock-profile-example'
                    Smart plug:
                      $ref: '#/components/examples/plug-profile-example'
                    Smart plug mini:
                      $ref: '#/components/examples/plug_mini-profile-example'
                    Smart bulb(white):
                      $ref: '#/components/examples/bulb_white-profile-example'
                    Smart bulb(multi-color):
                      $ref: '#/components/examples/bulb_color-profile-example'
                    Smart string light LED:
                      $ref: '#/components/examples/line_led-profile-example'
                    Smart motorized curtain control:
                      $ref: '#/components/examples/curtain_ctrl-profile-example'
                    Smart electric blind:
                      $ref: '#/components/examples/blind_motor-profile-example'
                    Smart switch strip:
                      $ref: '#/components/examples/switch_strip-profile-example'
                    Smart star light:
                      $ref: '#/components/examples/starlight-profile-example'
                    Smart chime bell:
                      $ref: '#/components/examples/doorbell-profile-example'
                    Smart pet feeder:
                      $ref: '#/components/examples/pet_peeder-profile-example'
                    Smart home camera:
                      $ref: '#/components/examples/home_camera-profile-example'
                    Sync box:
                      $ref: '#/components/examples/sync_box-profile-example'
                    Sync box sub:
                      $ref: '#/components/examples/sync_box_sub-profile-example'
                    Smart gas detection sensor:
                      $ref: '#/components/examples/gas_sensor-profile-example'
                    Smart fire detection sensor:
                      $ref: '#/components/examples/fire_sensor-profile-example'
                    Smart water leeak detection sensor:
                      $ref: '#/components/examples/water_leak_sensor-profile-example'
                    Smart thermohygrometer:
                      $ref: '#/components/examples/thermo_hygrometer-profile-example'
                    Smart siren:
                      $ref: '#/components/examples/siren-profile-example'
            '400':
              description: Bad request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6400`: Bad Request'
                  example: 6400
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6401`: Unauthorized'
                  example: 6401
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '403':
              description: Forbidden
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6403`: Forbidden'
                  example: 6403
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found Resource
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6404`: Not Found Resource'
                  example: 6404
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '406':
              description: Not Supported Resource
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6406`: Not Supported Resource'
                  example: 6406
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '416':
              description: Invalid Device Status
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6416`: Invalid Device Status'
                  example: 6416
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6500`: Internal Server Error'
                  example: 6500
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
      /devices/{deviceId}/state:
        get:
          tags:
            - Device API
          summary: Get Device Status
          description: Get status of a specific device.
          operationId: getStatusOfDevice
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Use-Account'
            - required: true
              $ref: '#/components/parameters/deviceId'
            - required: false
              $ref: '#/components/parameters/Authorization'
            - required: false
              $ref: '#/components/parameters/X-Country-Code'
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6200`: Successful operation'
                  example: 6200
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/device-status-res'
                  examples:
                    Refrigerator:
                      $ref: '#/components/examples/refrigerator-object-example'
                    Washer:
                      $ref: '#/components/examples/washer-object-example'
                    Dryer:
                      $ref: '#/components/examples/dryer-object-example'
                    Air Conditioner:
                      $ref: '#/components/examples/air_conditioner-object-example'
                    Air Purifier:
                      $ref: '#/components/examples/air_purifier-object-example'
                    Robot Cleaner:
                      $ref: '#/components/examples/robot_cleaner-object-example'
                    Oven:
                      $ref: '#/components/examples/oven-object-example'
                    Dish Washer:
                      $ref: '#/components/examples/dish_washer-object-example'
                    Styler:
                      $ref: '#/components/examples/styler-object-example'
                    Water Purifier:
                      $ref: '#/components/examples/water_purifier-object-example'
                    Dehumidifier:
                      $ref: '#/components/examples/dehumidifier-object-example'
                    Ceiling Fan:
                      $ref: '#/components/examples/ceiling_fan-object-example'
                    Wine Cellar:
                      $ref: '#/components/examples/wine_cellar-object-example'
                    Kimchi Refrigerator:
                      $ref: '#/components/examples/kimchi_refrigerator-object-example'
                    Home Brew:
                      $ref: '#/components/examples/home_brew-object-example'
                    Plant Cultivator:
                      $ref: '#/components/examples/plant_cultivator-object-example'
                    WashTower (Washer):
                      $ref: '#/components/examples/washtower_washer-object-example'
                    WashTower (Dryer):
                      $ref: '#/components/examples/washtower_dryer-object-example'
                    WashTower:
                      $ref: '#/components/examples/washtower-object-example'
                    Cooktop:
                      $ref: '#/components/examples/cooktop-object-example'
                    Hood:
                      $ref: '#/components/examples/hood-object-example'
                    Microwave Oven:
                      $ref: '#/components/examples/microwave_oven-object-example'
                    System Boiler:
                      $ref: '#/components/examples/system_boiler-object-example'
                    Air Purifier Fan:
                      $ref: '#/components/examples/air_purifier_fan-object-example'
                    Stick Cleaner:
                      $ref: '#/components/examples/stick_cleaner-object-example'
                    Water Heater:
                      $ref: '#/components/examples/water_heater-object-example'
                    Main WashCombo:
                      $ref: '#/components/examples/main_washcombo-object-example'
                    Mini WashCombo:
                      $ref: '#/components/examples/mini_washcombo-object-example'
                    Humidifier:
                      $ref: '#/components/examples/humidifier-object-example'
                    Outdoor unit of a system air conditioner registered in BECON Cloud:
                      $ref: '#/components/examples/odu-object-example'
                    Indoor unit of a system air conditioner registered in BECON Cloud:
                      $ref: '#/components/examples/idu-object-example'
                    Signage registered in the Business Cloud:
                      $ref: '#/components/examples/signage-object-example'
                    Smart motion sensor:
                      $ref: '#/components/examples/motion_sensor-object-example'
                    Smart temperature and humidity sensor:
                      $ref: '#/components/examples/temperature_humidity_sensor-object-example'
                    Smart door sensor:
                      $ref: '#/components/examples/door_sensor-object-example'
                    Smart button:
                      $ref: '#/components/examples/button-object-example'
                    Smart light switch:
                      $ref: '#/components/examples/light_switch-object-example'
                    Smart door lock:
                      $ref: '#/components/examples/door_lock-object-example'
                    Smart push-pull door lock:
                      $ref: '#/components/examples/push_pull_door_lock-object-example'
                    Smart plug:
                      $ref: '#/components/examples/plug-object-example'
                    Smart plug mini:
                      $ref: '#/components/examples/plug_mini-object-example'
                    Smart bulb(white):
                      $ref: '#/components/examples/bulb_white-object-example'
                    Smart bulb(multi-color):
                      $ref: '#/components/examples/bulb_color-object-example'
                    Smart string light LED:
                      $ref: '#/components/examples/line_led-object-example'
                    Smart motorized curtain control:
                      $ref: '#/components/examples/curtain_ctrl-object-example'
                    Smart electric blind:
                      $ref: '#/components/examples/blind_motor-object-example'
                    Smart switch strip:
                      $ref: '#/components/examples/switch_strip-object-example'
                    Smart star light:
                      $ref: '#/components/examples/starlight-object-example'
                    Smart chime bell:
                      $ref: '#/components/examples/doorbell-object-example'
                    Smart pet feeder:
                      $ref: '#/components/examples/pet_peeder-object-example'
                    Smart home camera:
                      $ref: '#/components/examples/home_camera-object-example'
                    Sync box:
                      $ref: '#/components/examples/sync_box-object-example'
                    Sync box sub:
                      $ref: '#/components/examples/sync_box_sub-object-example'
                    Smart gas detection sensor:
                      $ref: '#/components/examples/gas_sensor-object-example'
                    Smart fire detection sensor:
                      $ref: '#/components/examples/fire_sensor-object-example'
                    Smart water leeak detection sensor:
                      $ref: '#/components/examples/water_leak_sensor-object-example'
                    Smart thermohygrometer:
                      $ref: '#/components/examples/thermo_hygrometer-object-example'
                    Smart siren:
                      $ref: '#/components/examples/siren-object-example'
            '400':
              description: Bad request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6400`: Bad Request'
                  example: 6400
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6401`: Unauthorized'
                  example: 6401
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '403':
              description: Forbidden
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6403`: Forbidden'
                  example: 6403
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found Resource
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6404`: Not Found Resource'
                  example: 6404
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '406':
              description: Not Acceptable
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6406`: Not Supported Resource'
                  example: 6406
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '416':
              description: Invalid Device Status
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6416`: Invalid Device Status'
                  example: 6416
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6500`: Internal Server Error'
                  example: 6500
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
        post:
          tags:
            - Device API
          summary: Control Device
          description: Control the state of a specific device. You can't control products that don't have controllable properties in the device profile.
          operationId: controlDevice
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Use-Account'
            - required: true
              $ref: '#/components/parameters/deviceId'
            - required: false
              $ref: '#/components/parameters/Authorization'
            - required: false
              $ref: '#/components/parameters/X-Country-Code'
          requestBody:
            content:
              application/json:
                schema:
                  type: object
                  description: For a schema of control request messages by device type, see the [**Device Profiles**](/en/apiManage/device_profile) page.
                examples:
                  Refrigerator:
                    $ref: '#/components/examples/refrigerator-command-example'
                  Washer:
                    $ref: '#/components/examples/washer-command-example'
                  Dryer:
                    $ref: '#/components/examples/dryer-command-example'
                  Air Conditioner:
                    $ref: '#/components/examples/air_conditioner-command-example'
                  Air Purifier:
                    $ref: '#/components/examples/air_purifier-command-example'
                  Robot Cleaner:
                    $ref: '#/components/examples/robot_cleaner-command-example'
                  Oven:
                    $ref: '#/components/examples/oven-command-example'
                  Dish Washer:
                    $ref: '#/components/examples/dish_washer-command-example'
                  Styler:
                    $ref: '#/components/examples/styler-command-example'
                  Dehumidifier:
                    $ref: '#/components/examples/dehumidifier-command-example'
                  Ceiling Fan:
                    $ref: '#/components/examples/ceiling_fan-command-example'
                  Wine Cellar:
                    $ref: '#/components/examples/wine_cellar-command-example'
                  WashTower (Washer):
                    $ref: '#/components/examples/washtower_washer-command-example'
                  WashTower (Dryer):
                    $ref: '#/components/examples/washtower_dryer-command-example'
                  WashTower:
                    $ref: '#/components/examples/washtower-command-example'
                  Cooktop:
                    $ref: '#/components/examples/cooktop-command-example'
                  Hood:
                    $ref: '#/components/examples/hood-command-example'
                  Microwave Oven:
                    $ref: '#/components/examples/microwave_oven-command-example'
                  System Boiler:
                    $ref: '#/components/examples/system_boiler-command-example'
                  Air Purifier Fan:
                    $ref: '#/components/examples/air_purifier_fan-command-example'
                  Water Heater:
                    $ref: '#/components/examples/water_heater-command-example'
                  Main WashCombo:
                    $ref: '#/components/examples/main_washcombo-command-example'
                  Mini WashCombo:
                    $ref: '#/components/examples/mini_washcombo-command-example'
                  Humidifier:
                    $ref: '#/components/examples/humidifier-command-example'
                  Indoor unit of a system air conditioner registered in BECON Cloud:
                    $ref: '#/components/examples/idu-command-example'
                  Signage registered in the Business Cloud:
                    $ref: '#/components/examples/signage-command-example'
                  Smart light switch:
                    $ref: '#/components/examples/light_switch-command-example'
                  Smart door lock:
                    $ref: '#/components/examples/door_lock-command-example'
                  Smart push-pull door lock:
                    $ref: '#/components/examples/push_pull_door_lock-command-example'
                  Smart plug:
                    $ref: '#/components/examples/plug-command-example'
                  Smart plug mini:
                    $ref: '#/components/examples/plug_mini-command-example'
                  Smart bulb(white):
                    $ref: '#/components/examples/bulb_white-command-example'
                  Smart bulb(multi-color):
                    $ref: '#/components/examples/bulb_color-command-example'
                  Smart string light LED:
                    $ref: '#/components/examples/line_led-command-example'
                  Smart motorized curtain control:
                    $ref: '#/components/examples/curtain_ctrl-command-example'
                  Smart electric blind:
                    $ref: '#/components/examples/blind_motor-command-example'
                  Smart switch strip:
                    $ref: '#/components/examples/switch_strip-command-example'
                  Smart star light:
                    $ref: '#/components/examples/starlight-command-example'
                  Smart chime bell:
                    $ref: '#/components/examples/doorbell-command-example'
                  Smart pet feeder:
                    $ref: '#/components/examples/pet_peeder-command-example'
                  Smart home camera:
                    $ref: '#/components/examples/home_camera-command-example'
                  Sync box:
                    $ref: '#/components/examples/sync_box-command-example'
                  Sync box sub:
                    $ref: '#/components/examples/sync_box_sub-command-example'
                  Smart siren:
                    $ref: '#/components/examples/siren-command-example'
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6200`: Successful operation'
                  example: 6200
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/device-status-res'
                  examples:
                    Refrigerator:
                      $ref: '#/components/examples/refrigerator-object-example'
                    Washer:
                      $ref: '#/components/examples/washer-object-example'
                    Dryer:
                      $ref: '#/components/examples/dryer-object-example'
                    Air Conditioner:
                      $ref: '#/components/examples/air_conditioner-object-example'
                    Air Purifier:
                      $ref: '#/components/examples/air_purifier-object-example'
                    Robot Cleaner:
                      $ref: '#/components/examples/robot_cleaner-object-example'
                    Oven:
                      $ref: '#/components/examples/oven-object-example'
                    Dish Washer:
                      $ref: '#/components/examples/dish_washer-object-example'
                    Styler:
                      $ref: '#/components/examples/styler-object-example'
                    Dehumidifier:
                      $ref: '#/components/examples/dehumidifier-object-example'
                    Ceiling Fan:
                      $ref: '#/components/examples/ceiling_fan-object-example'
                    Wine Cellar:
                      $ref: '#/components/examples/wine_cellar-object-example'
                    WashTower (Washer):
                      $ref: '#/components/examples/washtower_washer-object-example'
                    WashTower (Dryer):
                      $ref: '#/components/examples/washtower_dryer-object-example'
                    WashTower:
                      $ref: '#/components/examples/washtower-object-example'
                    Cooktop:
                      $ref: '#/components/examples/cooktop-object-example'
                    Hood:
                      $ref: '#/components/examples/hood-object-example'
                    Microwave Oven:
                      $ref: '#/components/examples/microwave_oven-object-example'
                    System Boiler:
                      $ref: '#/components/examples/system_boiler-object-example'
                    Air Purifier Fan:
                      $ref: '#/components/examples/air_purifier_fan-object-example'
                    Water Heater:
                      $ref: '#/components/examples/water_heater-object-example'
                    Main WashCombo:
                      $ref: '#/components/examples/main_washcombo-object-example'
                    Mini WashCombo:
                      $ref: '#/components/examples/mini_washcombo-object-example'
                    Humidifier:
                      $ref: '#/components/examples/humidifier-object-example'
                    Indoor unit of a system air conditioner registered in BECON Cloud:
                      $ref: '#/components/examples/idu-object-example'
                    Signage registered in the Business Cloud:
                      $ref: '#/components/examples/signage-object-example'
                    Smart light switch:
                      $ref: '#/components/examples/light_switch-object-example'
                    Smart door lock:
                      $ref: '#/components/examples/door_lock-object-example'
                    Smart push-pull door lock:
                      $ref: '#/components/examples/push_pull_door_lock-object-example'
                    Smart plug:
                      $ref: '#/components/examples/plug-object-example'
                    Smart plug mini:
                      $ref: '#/components/examples/plug_mini-object-example'
                    Smart bulb(white):
                      $ref: '#/components/examples/bulb_white-object-example'
                    Smart bulb(multi-color):
                      $ref: '#/components/examples/bulb_color-object-example'
                    Smart string light LED:
                      $ref: '#/components/examples/line_led-object-example'
                    Smart motorized curtain control:
                      $ref: '#/components/examples/curtain_ctrl-object-example'
                    Smart electric blind:
                      $ref: '#/components/examples/blind_motor-object-example'
                    Smart switch strip:
                      $ref: '#/components/examples/switch_strip-object-example'
                    Smart star light:
                      $ref: '#/components/examples/starlight-object-example'
                    Smart chime bell:
                      $ref: '#/components/examples/doorbell-object-example'
                    Smart pet feeder:
                      $ref: '#/components/examples/pet_peeder-object-example'
                    Smart home camera:
                      $ref: '#/components/examples/home_camera-object-example'
                    Sync box:
                      $ref: '#/components/examples/sync_box-object-example'
                    Sync box sub:
                      $ref: '#/components/examples/sync_box_sub-object-example'
                    Smart siren:
                      $ref: '#/components/examples/siren-object-example'
            '400':
              description: Bad request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6400`: Bad Request'
                  example: 6400
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6401`: Unauthorized'
                  example: 6401
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '403':
              description: Forbidden
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6403`: Forbidden'
                  example: 6403
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found Resource
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6404`: Not Found Resource'
                  example: 6404
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '406':
              description: Not Supported Resource
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6406`: Not Supported Resource'
                  example: 6406
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '416':
              description: Invalid Device Status
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6416`: Invalid Device Status'
                  example: 6416
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6500`: Internal Server Error'
                  example: 6500
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
      /push:
        get:
          tags:
            - Push API
          summary: Get Device Push Subscription List
          description: |
            Get ID list of devices that have subscribed to push messages. **(Currently, only LG ThinQ registered devices are supported.)**
          operationId: listDevicesSubscribed
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Use-Account'
            - required: false
              $ref: '#/components/parameters/Authorization'
            - required: false
              $ref: '#/components/parameters/X-Country-Code'
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6200`: Successful operation'
                  example: 6200
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/device-id-list-res'
            '400':
              description: Bad request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6400`: Bad Request'
                  example: 6400
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6401`: Unauthorized'
                  example: 6401
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '403':
              description: Forbidden
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6403`: Forbidden'
                  example: 6403
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found Resource
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6404`: Not Found Resource'
                  example: 6404
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '406':
              description: Not Supported Resource
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6406`: Not Supported Resource'
                  example: 6406
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '416':
              description: Invalid Device Status
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6416`: Invalid Device Status'
                  example: 6416
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6500`: Internal Server Error'
                  example: 6500
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
      /push/{deviceId}/subscribe:
        post:
          tags:
            - Push API
          summary: Subscribe to Device Push
          description: |
            Subscribe to push notifications from the target device. **(Currently, only LG ThinQ registered devices are supported.)**
          operationId: subscribePushMessages
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/deviceId'
            - required: true
              $ref: '#/components/parameters/X-Use-Account'
            - required: false
              $ref: '#/components/parameters/Authorization'
            - required: false
              $ref: '#/components/parameters/X-Country-Code'
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6200`: Successful operation'
                  example: 6200
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/device-empty-res'
            '400':
              description: Bad request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6400`: Bad Request'
                  example: 6400
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6401`: Unauthorized'
                  example: 6401
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '403':
              description: Forbidden
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6403`: Forbidden'
                  example: 6403
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '406':
              description: Not Supported Resource
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6406`: Not Supported Resource'
                  example: 6406
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6500`: Internal Server Error'
                  example: 6500
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
      /push/{deviceId}/unsubscribe:
        delete:
          tags:
            - Push API
          summary: Unsubscribe to Device Push
          description: |
            Unsubscribed to push notifications of the target device. **(Currently, only LG ThinQ registered devices are supported.)**
          operationId: unsubscribePushMessages
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/deviceId'
            - required: true
              $ref: '#/components/parameters/X-Use-Account'
            - required: false
              $ref: '#/components/parameters/Authorization'
            - required: false
              $ref: '#/components/parameters/X-Country-Code'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/device-empty-res'
            '400':
              description: Bad request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6400`: Bad Request'
                  example: 6400
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6401`: Unauthorized'
                  example: 6401
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '403':
              description: Forbidden
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6403`: Forbidden'
                  example: 6403
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found Resource
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6404`: Not Found Resource'
                  example: 6404
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '406':
              description: Not Supported Resource
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6406`: Not Supported Resource'
                  example: 6406
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '416':
              description: Invalid Device Status
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6416`: Invalid Device Status'
                  example: 6416
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6500`: Internal Server Error'
                  example: 6500
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
      /user:
        get:
          tags:
            - User API
          summary: Get User Number
          description: |
            Get the user number of a specific LG ThinQ user. When a user signs up for a B2B partner's service, lookup the user number in advance to identify the device owner for push messages received by Callback.
          operationId: getUserNumber
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/Authorization-2'
            - required: true
              $ref: '#/components/parameters/X-Country-Code-2'
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6200`: Successful operation'
                  example: 6200
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/userno-res'
            '400':
              description: Bad request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6400`: Bad Request'
                  example: 6400
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6401`: Unauthorized'
                  example: 6401
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '403':
              description: Forbidden
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6403`: Forbidden'
                  example: 6403
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found Resource
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6404`: Not Found Resource'
                  example: 6404
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '406':
              description: Not Supported Resource
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6406`: Not Supported Resource'
                  example: 6406
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '416':
              description: Invalid Device Status
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6416`: Invalid Device Status'
                  example: 6416
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6500`: Internal Server Error'
                  example: 6500
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
      /user/service:
        delete:
          tags:
            - User API
          summary: Deactivate User
          description: Deactivate a specific LG ThinQ user when the user is no longer synchronized. Once the user is deactivated, s/he cannot check the status of or control devices registered to the user. To reactivate this user, you need to call the **[Get Device List](#tag/Device-API/operation/getDevices)** for the user.
          operationId: disconnectService
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/Authorization-2'
            - required: true
              $ref: '#/components/parameters/X-Country-Code-2'
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6200`: Successful operation'
                  example: 6200
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/device-empty-res'
            '400':
              description: Bad request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6400`: Bad Request'
                  example: 6400
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6401`: Unauthorized'
                  example: 6401
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '403':
              description: Forbidden
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6403`: Forbidden'
                  example: 6403
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found Resource
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6404`: Not Found Resource'
                  example: 6404
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '406':
              description: Not Supported Resource
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6406`: Not Supported Resource'
                  example: 6406
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '416':
              description: Invalid Device Status
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6416`: Invalid Device Status'
                  example: 6416
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6500`: Internal Server Error'
                  example: 6500
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error-res-backend'
      /dr/groups:
        post:
          tags:
            - DR API
          summary: Create / Update Group
          description: Create a new group or update an existing one.
          operationId: createGroup
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Country-Code-2'
          requestBody:
            description: Group information
            content:
              application/json:
                schema:
                  type: object
                  properties:
                    groupId:
                      type: string
                      example: k-apt-1234567890
                      description: Group ID
                    groupName:
                      type: string
                      example: Apgujeong Hyundai 1st Apartment
                      description: Group Name
                    partnerId:
                      type: string
                      example: partner-1
                      description: The utility/integrator ID that created the group
                    areaCode:
                      type: string
                      example: '1168011000'
                      description: Legal address numbers(10-digit number assigned by the Ministry of Land, Infrastructure, and Transport)
                    buildingCode:
                      type: string
                      example: '1168011000103690001004767'
                      description: |-
                        - Street Name Address Building Control Number (Open Geospatial Information Platform)
                        - 25-digit number
                        - Legal address numbers(10) + Mountain or not(1) + main Address Number(4) + Appendages Address Number(4) + System Number(6)
                    comment:
                      type: string
                      example: Apgujeong Hyundai 1st Apartment
                      description: Description of the group
                  required:
                    - groupId
                    - partnerId
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`2000`: Successful operation'
                  example: 2000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      code:
                        type: integer
                        example: 2000
                      data:
                        type: object
                        properties:
                          groupId:
                            type: string
                            example: k-apt-1234567890
                            description: Group ID
            '400':
              description: Bad Request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4000`: Bad Request'
                  example: 4000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4201`: Unauthorized'
                  example: 4201
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4307`: Resource Not Found: Partner'
                  example: 4307
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4307
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: 'Resource Not Found: Partner'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`5000`: Internal Server Error'
                  example: 5000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Internal Server Error
      /dr/groups/{groupId}:
        get:
          tags:
            - DR API
          summary: Get Group
          description: Get a specific group.
          operationId: getGroup
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Country-Code-2'
            - in: path
              name: groupId
              description: The ID of a specific group. This corresponds to a group of users or devices.
              required: true
              schema:
                type: string
                example: k-apt-1234567890
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`2000`: Successful operation'
                  example: 2000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      code:
                        type: integer
                        example: 2000
                      data:
                        type: object
                        description: Group information
                        properties:
                          groupId:
                            type: string
                            example: k-apt-1234567890
                            description: The unique group ID that you registered with the DR service to distinguish between groups.
                          groupName:
                            type: string
                            example: Apgujeong Hyundai 1st Apartment
                            description: Group Name
                          partnerId:
                            type: string
                            example: partner-1
                            description: Partner ID of the DR service
                          areaCode:
                            type: string
                            example: '1168011000'
                            description: Legal address numbers(10-digit number assigned by the Ministry of Land, Infrastructure, and Transport)
                          buildingCode:
                            type: string
                            example: '1168011000103690001004767'
                            description: |-
                              - Street Name Address Building Control Number (Open Geospatial Information Platform)
                              - 25-digit number
                              - Legal address numbers(10) + Mountain or not(1) + main Address Number(4) + Appendages Address Number(4) + System Number(6)
                          comment:
                            type: string
                            example: Apgujeong Hyundai 1st Apartment
                            description: Description of the group
            '400':
              description: Bad Request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4000`: Bad Request'
                  example: 4000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4201`: Unauthorized'
                  example: 4201
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4308`: Resource Not Found: Group'
                  example: 4308
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4308
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: 'Resource Not Found: Group'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`5000`: Internal Server Error'
                  example: 5000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Internal Server Error
      /dr/partners/{partnerId}/groups:
        get:
          tags:
            - DR API
          summary: Get Group List
          description: Get a list of your partner's groups.
          operationId: getGroups
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Country-Code-2'
            - in: path
              name: partnerId
              description: ID of the Aggregator or Utility partner that created the group
              required: true
              schema:
                type: string
                example: partnerId
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`2000`: Successful operation'
                  example: 2000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      code:
                        type: integer
                        example: 2000
                      data:
                        type: array
                        description: Group List
                        items:
                          properties:
                            groupId:
                              type: string
                              example: k-apt-1234567890
                              description: Group ID registered with DR service
                            groupName:
                              type: string
                              example: Apgujeong Hyundai 1st Apartment
                              description: Group Name
                            partnerId:
                              type: string
                              example: partner-1
                              description: Partner ID
                            areaCode:
                              type: string
                              example: '1168011000'
                              description: '- Legal address numbers(10-digit number assigned by the Ministry of Land, Infrastructure, and Transport)'
                            buildingCode:
                              type: string
                              example: '1168011000103690001004767'
                              description: |-
                                - Street Name Address Building Control Number (Open Geospatial Information Platform)
                                - 25-digit number
                                - Legal address numbers(10) + Mountain or not(1) + main Address Number(4) + Appendages Address Number(4) + System Number(6)
                            comment:
                              type: string
                              example: Apgujeong Hyundai 1st Apartment
                              description: Description of the group
                  examples:
                    200 OK:
                      value:
                        code: 2000
                        data:
                          - groupId: k-apt-1234567890
                            groupName: Apgujeong Hyundai 1st Apartment
                            partnerId: partner-1
                            areaCode: '1168011000'
                            buildingCode: '1168011000103690001004767'
                            comment: Apgujeong Hyundai 1st Apartment
                          - groupId: k-apt-1234567899
                            groupName: Banpo 2-dong Acroriver Park
                            partnerId: partner-1
                            areaCode: '1165010700'
                            buildingCode: '1165010700100020001017796'
                            comment: Banpo 2-dong Acroriver Park
            '400':
              description: Bad Request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4000`: Bad Request'
                  example: 4000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4201`: Unauthorized'
                  example: 4201
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4308`: Resource Not Found: Group'
                  example: 4308
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4308
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: 'Resource Not Found: Group'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`5000`: Internal Server Error'
                  example: 5000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Internal Server Error
      /dr/users:
        post:
          tags:
            - DR API
          summary: Create User
          description: Create new users (LG ThinQ App common)
          operationId: createDrUser
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Country-Code-2'
          requestBody:
            description: User Infomation
            content:
              application/json:
                schema:
                  type: object
                  properties:
                    userNo:
                      type: string
                      example: KR1234567890123
                      description: User number of the LG Electronics account
                    mail:
                      type: string
                      example: test_mail@lge.com
                      description: E-mail address of the LG Electronics account
                    groupId:
                      type: string
                      example: A12345678
                      description: Group ID to enroll users in
                    accessToken:
                      type: string
                      example: 67a184e62a412bb19b6ec2742b94695e06c1ce19d04f8d92121c6c28c99faf841150dba911da301e5617ae3945218a05
                      description: An access_token value issued by the LMP(LGE Members Platform)
                    refreshToken:
                      type: string
                      example: 3559466b6c19e312357c277108aed936c22840672b1c2a6a8fb7597a6473f9a59fbec4a3f4e03595b8358413ba1d8088
                      description: A refresh_token value issued by the LMP(LGE Members Platform)
                    partner:
                      type: object
                      description: Partner information
                      properties:
                        partnerId:
                          type: string
                          example: partner-1
                          description: Partner ID
                        programId:
                          type: string
                          example: test-dr-1
                          description: DR Program ID (North America only)
                        programName:
                          type: string
                          example: test DR Program
                          description: DR Program Name (North America only)
                        partnerUserId:
                          type: string
                          example: partnerId-1
                          description: Partner user ID
                        authCodeExt:
                          type: string
                          example: d778581e-4431-2531-1315-c823beebc72f.f81a0977-a553-417e-8873-64faafa0534a.160df234-7s14-4ed2-b710-74afc12eaa12
                          description: Auth code for 3rd party OAuth 2.0 integration (issued by 3rd party system, one-time use)
                      required:
                        - partnerId
                        - authCodeExt
                  required:
                    - userNo
                    - accessToken
                    - refreshToken
                    - partner
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`2000`: Successful operation'
                  example: 2000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      code:
                        type: integer
                        example: 2000
                      data:
                        type: object
                        properties:
                          userNo:
                            type: string
                            example: 01581c1893b95f30282d3c09d478cef7
                            description: The user number of the created user's encrypted LG Electronics account.
            '400':
              description: Bad Request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4000`: Bad Request'
                  example: 4000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4201`: Unauthorized'
                  example: 4201
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found
              headers:
                X-Response-Code:
                  schema:
                    type: string
                    description1: '`4307`: Resource Not Found: Partner'
                    example: 4307
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4307
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: 'Resource Not Found: Partner'
            '409':
              description: Conflict
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4309`: Resource Already Exists: User'
                  example: 4309
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4309
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: 'Resource Not Found: Event'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`5000`: Internal Server Error'
                  example: 5000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Internal Server Error
      /dr/users/{userNo}:
        delete:
          tags:
            - DR API
          summary: Delete User
          description: Delete a specific user corresponding to the user number in the LG Electronics account. The user's device information will also be deleted.
          operationId: deleteDrUser
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Country-Code-2'
            - in: path
              name: userNo
              description: The encrypted user number of the LG Electronics account
              required: true
              schema:
                type: string
                example: 01581c1135488770282d3c09d478cef7
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`2000`: Successful operation'
                  example: 2000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      code:
                        type: integer
                        example: 2000
                      data:
                        type: object
                        properties:
                          userNo:
                            type: string
                            example: 01581c1135488770282d3c09d478cef7
                            description: Deleted User number of the LG Electronics account
            '400':
              description: Bad Request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4000`: Bad Request'
                  example: 4000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4201`: Unauthorized'
                  example: 4201
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4301`: Resource Not Found: User'
                  example: 4301
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4301
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: 'Resource Not Found: User'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`5000`: Internal Server Error'
                  example: 5000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Internal Server Error
        get:
          tags:
            - DR API
          summary: Get User
          description: Get user information corresponding to the encrypted user number of the LG Electronics account.
          operationId: getDrUser
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Country-Code-2'
            - in: path
              name: userNo
              description: The encrypted user number of the LG Electronics account
              required: true
              schema:
                type: string
                example: 01581c1135488770282d3c09d478cef7
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`2000`: Successful operation'
                  example: 2000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      code:
                        type: integer
                        example: 2000
                      data:
                        type: object
                        properties:
                          userNo:
                            type: string
                            example: 01581c1135488770282d3c09d478cef7
                            description: The encrypted user number of the LG Electronics account
                          drHomeId:
                            type: string
                            example: '123456789012345678'
                            description: ThinQ Home ID of the user connected to the DR service
                          partnerId:
                            type: string
                            example: partner-1
                            description: Partner ID of the DR service to which the user is subscribed
                          groupId:
                            type: string
                            example: A12345678
                            description: Group ID of the user
            '400':
              description: Bad Request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4000`: Bad Request'
                  example: 4000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4201`: Unauthorized'
                  example: 4201
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4301`: Resource Not Found: User'
                  example: 4301
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4301
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: 'Resource Not Found: User'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`5000`: Internal Server Error'
                  example: 5000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Internal Server Error
      /dr/users/{userNo}/devices:
        get:
          tags:
            - DR API
          summary: Get User's Device List
          description: Get a list of users' devices that can participate in DR events.
          operationId: getDrDevices
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Country-Code-2'
            - in: path
              name: userNo
              description: The encrypted user number of the LG Electronics account
              required: true
              schema:
                type: string
                example: 01581c1135488770282d3c09d478cef7
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`2000`: Successful operation'
                  example: 2000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      code:
                        type: integer
                        example: 2000
                      data:
                        type: array
                        items:
                          properties:
                            deviceId:
                              type: string
                              example: 1f6bfb2796410a429f0015bf91f9583618458881645497851352d690513b13353f1da753095de970faba8099e2a56aa1
                              description: The encrypted ThinQ device ID
                            macAddress:
                              type: string
                              example: 66e71f19ada4fcaf3156aa26d49d4291
                              description: The encrypted MAC address
                            groupId:
                              type: string
                              example: k-apt-1234567890
                              description: Group ID
                            userNo:
                              type: string
                              example: 01581c1135488770282d3c09d478cef7
                              description: The encrypted user number of the LG Electronics account
                            homeId:
                              type: string
                              example: '123456789012345678'
                              description: ThinQ Home ID where the device is registered
                            drParticipate:
                              type: boolean
                              example: true
                              description: Whether you can participate in to DR events (true/false)
                            opt:
                              type: string
                              example: IN
                              description: Whether you are currently participating in a DR event (“IN”/“OUT”)
                            deviceType:
                              type: string
                              example: DEVICE_AIR_CONDITIONER
                              description: Appliance type of the device
                            modelName:
                              type: string
                              example: PAC_910604_US
                              description: A model name of the device
                            alias:
                              type: string
                              example: air conditioner
                              description: An alias of the device
                  examples:
                    200 OK:
                      value:
                        code: 2000
                        data:
                          - deviceId: 1f6bfb2796410a429f0015bf91f9583618458881645497851352d690513b13353f1da753095de970faba8099e2a56aa1
                            macAddress: 66e71f19ada4fcaf3156aa26d49d4291
                            groupId: A12345678
                            userNo: 01581c1135488770282d3c09d478cef7
                            homeId: '123456789012345678'
                            drParticipate: true
                            opt: IN
                            deviceType: DEVIE_AIR_CONDITIONER
                            modelName: PAC_910604_US
                            alias: room air conditioner
                          - deviceId: 1f6bfb2796410a429f0015bf91f9583618458881645497851352d690513b13353f1da75309885740faba8099e2a56aa1
                            macAddress: 66e78259ada4fcaf3114aa26d49d4291
                            groupId: A12345678
                            userNo: 01581c1135488770282d3c09d478cef7
                            homeId: '123456789012345678'
                            drParticipate: true
                            opt: OUT
                            deviceType: DEVIE_AIR_CONDITIONER
                            modelName: PAC_910604_US
                            alias: living air conditioner
            '400':
              description: Bad Request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4000`: Bad Request'
                  example: 4000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4201`: Unauthorized'
                  example: 4201
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found
              headers:
                X-Response-Code:
                  schema:
                    type: string
                    description1: '`4301`: Resource Not Found: User'
                    example: 4301
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4301
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: 'Resource Not Found: User'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`5000`: Internal Server Error'
                  example: 5000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Internal Server Error
      /dr/users/{userNo}/devices/{deviceId}:
        get:
          tags:
            - DR API
          summary: Get User's Device Info
          description: Retrieve the specific device information.
          operationId: getDrDevice
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Country-Code-2'
            - in: path
              name: userNo
              description: The encrypted user number of the LG Electronics account
              required: true
              schema:
                type: string
                example: 01581c1135488770282d3c09d478cef7
            - in: path
              name: deviceId
              description: The encrypted ThinQ device ID
              required: true
              schema:
                type: string
                example: 1f6bfb2796410a429f0015bf91f9583618458881645497851352d690513b13353f1da753095de970faba8099e2a56aa1
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`2000`: Successful operation'
                  example: 2000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      code:
                        type: integer
                        example: 2000
                      data:
                        type: array
                        items:
                          properties:
                            deviceId:
                              type: string
                              example: 1f6bfb2796410a429f0015bf91f9583618458881645497851352d690513b13353f1da753095de970faba8099e2a56aa1
                              description: The encrypted ThinQ device ID
                            macAddress:
                              type: string
                              example: 66e71f19ada4fcaf3156aa26d49d4291
                              description: The encrypted MAC address
                            groupId:
                              type: string
                              example: A12345678
                              description: Group ID
                            userNo:
                              type: string
                              example: 01581c1135488770282d3c09d478cef7
                              description: The encrypted user number of the LG Electronics account
                            homeId:
                              type: string
                              example: '123456789012345678'
                              description: ThinQ Home ID where the device is registered
                            drParticipate:
                              type: boolean
                              example: true
                              description: Whether you can participate in to DR events (true/false)
                            opt:
                              type: string
                              example: IN
                              description: Whether you are currently participating in a DR event (“IN”/“OUT”)
                            deviceType:
                              type: string
                              example: DEVICE_AIR_CONDITIONER
                              description: Appliance type of the device
                            modelName:
                              type: string
                              example: PAC_910604_US
                              description: A model name of the device
                            alias:
                              type: string
                              example: air conditioner
                              description: An alias of the device
                  examples:
                    200 OK:
                      value:
                        code: 2000
                        data:
                          - deviceId: 1f6bfb2796410a429f0015bf91f9583618458881645497851352d690513b13353f1da753095de970faba8099e2a56aa1
                            macAddress: 66e71f19ada4fcaf3156aa26d49d4291
                            groupId: A12345678
                            userNo: 01581c1135488770282d3c09d478cef7
                            homeId: '123456789012345678'
                            drParticipate: true
                            opt: IN
                            deviceType: DEVIE_AIR_CONDITIONER
                            modelName: PAC_910604_US
                            alias: room air conditioner
            '400':
              description: Bad Request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4000`: Bad Request'
                  example: 4000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4201`: Unauthorized'
                  example: 4201
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4301`: Resource Not Found: User'
                  example: 4301
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4301
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: 'Resource Not Found: User'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`5000`: Internal Server Error'
                  example: 5000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Internal Server Error
      /dr/events:
        post:
          tags:
            - DR API
          summary: Create / Update DR Event
          description: Create a new DR Event or or update an existing one.
          operationId: createDrEvent
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Country-Code-2'
          requestBody:
            description: DR Event information
            content:
              application/json:
                schema:
                  type: object
                  properties:
                    eventId:
                      type: string
                      example: 2024-04-25-dr-01
                      description: DR Event ID
                    eventName:
                      type: string
                      example: 2024-04-25 test DR event
                      description: DR Event Name
                    partnerId:
                      type: string
                      example: partner-1
                      description: Partner ID
                    startTs:
                      type: number
                      example: 1714024800000
                      description: DR Event start time(milliseconds)
                    endTs:
                      type: number
                      example: 1714028400000
                      description: DR end time(milliseconds)
                    targets:
                      type: array
                      items:
                        properties:
                          targetType:
                            type: string
                            example: GROUP
                            description: The event target type (GROUP, USER, DEVICE)
                          targetIds:
                            type: array
                            items:
                              type: string
                              example: k-apt-1234567890
                            description: A list of event target ID (of GROUP, USER or DEVICE)
                        required:
                          - targetType
                          - targetIds
                    signals:
                      type: array
                      items:
                        properties:
                          signalId:
                            type: string
                            example: 2024-04-25-dr-01-signal-01
                            description: The event signal ID
                          deviceType:
                            type: string
                            example: DEVICE_AIR_CONDITIONER
                            description: The event target type
                          modelNames:
                            type: array
                            items:
                              type: string
                              example: RAC_056905_WW
                            description: A model name of the DR Event target dvice
                          signalType:
                            type: string
                            example: CONTROL_RESTORE
                            description: The DR Event signal type(CONTROL, CONTROL_RESTORE)
                          signalData:
                            type: object
                            properties:
                              temperature:
                                type: object
                                properties:
                                  min:
                                    type: number
                                    example: 26
                                  max:
                                    type: number
                                    example: 32
                                  unit:
                                    type: string
                                    example: C
                            description: |-
                              The specific control value
                              ex) { temerpature: { min: 20, max: 26, unit: "C } }
                          constrolType:
                            type: string
                            example: Temperature
                            description: Control method (Temperature, TwoSetTemperature, ToU, Empty)
                          restoreType:
                            type: string
                            example: Temperature
                            description: Control recover method (Temperature, TwoSetTemperature, Empty)
                  required:
                    - eventId
                    - eventName
                    - partnerId
                    - startTs
                    - endTs
                    - targets
                examples:
                  Create & Update Event:
                    value:
                      eventId: 2024-04-25-dr-01
                      eventName: 2024-04-25-dr-01
                      partnerId: herit-01
                      startTs: 1714024800000
                      endTs: 1714028400000
                      targets:
                        - targetType: GROUP
                          targetIds:
                            - k-apt-1234567890
                            - k-apt-1234567899
                        - targetType: USER
                          targetIds:
                            - US1234567890123
                            - KR1234567890123
                      signals:
                        - signalId: 2023-04-25-dr-01-signal-01
                          deviceType: DEVICE_AIR_CONDITIONER
                          modelNames:
                            - RAC_056905_WW
                          signalType: CONTROL_RESTORE
                          signalData:
                            temperature:
                              min: 20
                              max: 26
                              unit: C
                          controlType: Temperature
                          restoreType: Temperature
                        - signalId: 2023-04-25-dr-01-signal-02
                          deviceType: DEVICE_TV
                          modelNames: []
                          signalType: CONTROL
                          signalData: {}
                          controlType: Empty
                          restoreType: Empty
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`2000`: Successful operation'
                  example: 2000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      code:
                        type: integer
                        example: 2000
                      data:
                        type: object
                        properties:
                          eventId:
                            type: string
                            example: 2023-04-25-dr-01
                            description: The generated DR Event ID
            '400':
              description: Bad Request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4000`: Bad Request'
                  example: 4000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4201`: Unauthorized'
                  example: 4201
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4307`: Resource Not Found: Partner'
                  example: 4307
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4307
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: 'Resource Not Found: Partner'
            '409':
              description: Conflict
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4311`: Resource Already Exists: Event'
                  example: 4311
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4311
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: 'Resource Not Found: Event'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`5000`: Internal Server Error'
                  example: 5000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Internal Server Error
      /dr/events/{eventId}:
        delete:
          tags:
            - DR API
          summary: Delete DR Event
          description: Delete a DR Event you created.
          operationId: deleteDrEvent
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Country-Code-2'
            - in: path
              name: eventId
              required: true
              schema:
                type: string
                example: 2024-04-25-dr-01
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`2000`: Successful operation'
                  example: 2000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      code:
                        type: integer
                        example: 2000
                      data:
                        type: object
                        properties:
                          groupId:
                            type: string
                            example: 2024-04-25-dr-01
                            description: Deleted DR Evnet ID
            '400':
              description: Bad Request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4000`: Bad Request'
                  example: 4000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4201`: Unauthorized'
                  example: 4201
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4302`: Resource Not Found: Event'
                  example: 4302
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4302
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: 'Resource Not Found: Event'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`5000`: Internal Server Error'
                  example: 5000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Internal Server Error
      /dr/events/{eventId}/targets:
        post:
          tags:
            - DR API
          summary: Create DR Event target
          description: Add event target information to an already created DR Event.
          operationId: createEventTarget
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Country-Code-2'
            - in: path
              name: eventId
              description: DR Event ID
              required: true
              schema:
                type: string
                example: event-01
          requestBody:
            description: DR Event target information.
            content:
              application/json:
                schema:
                  type: object
                  properties:
                    type:
                      type: string
                      example: USER
                      description: |-
                        The target type
                        - GROUP
                        - USER
                        - DEVICE
                    id:
                      type: string
                      example: KR1234567890123
                      description: |-
                        DR Event target ID
                        - If the event target type is USER: userNo
                        - If the event target type is GROUP: groupId
                        - If the event target type is DEVICE: deviceId
                    opt:
                      type: string
                      example: OUT
                      description: |-
                        You can check whether you are opted in or out of DR Event.
                        - IN : Opt in to DR Event(default)
                        - OUT : Opt out of DR Event
                  required:
                    - type
                    - id
                    - opt
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`2000`: Successful operation'
                  example: 2000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      code:
                        type: integer
                        example: 2000
                      data:
                        type: object
                        properties:
                          groupId:
                            type: string
                            example: 2024-04-25-dr-01
                            description: Generated DR Event target ID
            '400':
              description: Bad Request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4000`: Bad Request'
                  example: 4000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4201`: Unauthorized'
                  example: 4201
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4302`: Resource Not Found: Event'
                  example: 4302
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4302
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: 'Resource Not Found: Event'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`5000`: Internal Server Error'
                  example: 5000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Internal Server Error
      /dr/events/{eventId}/targets/{targetId}:
        post:
          tags:
            - DR API
          summary: Modify DR Event target
          description: Modify already created DR Event target.
          operationId: updateEventTarget
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Country-Code-2'
            - in: path
              name: eventId
              description: DR Event ID
              required: true
              schema:
                type: string
                example: event-01
            - in: path
              name: targetId
              description: DR Event target ID
              required: true
              schema:
                type: string
                example: KR1234567890123
          requestBody:
            description: DR Event information
            content:
              application/json:
                schema:
                  type: object
                  properties:
                    opt:
                      type: string
                      example: OUT
                      description: |-
                        Whether to participate in DR events (Opt in / out)
                        - IN : Opt in to DR Event (default)
                        - OUT : Opt out of DR Event
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`2000`: Successful operation'
                  example: 2000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      code:
                        type: integer
                        example: 2000
                      data:
                        $ref: '#/components/schemas/dr-event-target-opt-res'
            '400':
              description: Bad Request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4102`: Bad Request'
                  example: 4102
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4102
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Missing or Invalid Parameter(s) in Request Body
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4201`: Unauthorized'
                  example: 4201
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4302`: Resource Not Found: Event'
                  example: 4302
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4302
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: 'Resource Not Found: Event'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`5000`: Internal Server Error'
                  example: 5000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Internal Server Error
      /dr/events/{eventId}/targets/batch:
        post:
          tags:
            - DR API
          summary: Create DR Event targets in bulk
          description: Create multiple DR Event targets at once.
          operationId: createEventTargetBatch
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Country-Code-2'
            - in: path
              name: eventId
              description: DR Event ID
              required: true
              schema:
                type: string
                example: event-01
          requestBody:
            description: Update information for the DR Event targets
            content:
              application/json:
                schema:
                  type: array
                  items:
                    properties:
                      action:
                        type: string
                        example: create
                        description: |-
                          Whether to create/modify DR Event targets
                          - create
                          - replace(unused)
                      path:
                        type: string
                        example: /
                        description: |-
                          DR Event target ID.
                          - create: "/"
                          - replace: "/{targetId}"
                          - Ex) Create: "/"
                          - Ex) Modify: "/2YjaqUmSr3ke2nmdssxAG5n0KDMwrJrvi8bTbzbdHelEEflqNkAx0WWmTIgyCQf"
                      value:
                        type: object
                        properties:
                          type:
                            type: string
                            example: DEVICE
                          id:
                            type: string
                            example: 2YjaqUmSr3ke2nmdssxAG5n0KDMwrJrvi8bTbzbdHelEEflqNkAx0WWmTIgyCQf
                          opt:
                            type: string
                            example: IN
                        description: |-
                          You can check whether you are opted in or out of DR Event.
                          - create: {type, id, opt}
                          - replace: {opt}
                          - Ex) create: { type: "DEVICE", id: "2YjaqUmSr3ke2nmdssxAG5n0KDMwrJrvi8bTbzbdHelEEflqNkAx0WWmTIgyCQf", opt: "IN"}
                          - Ex) replace: { opt: "IN"}
                    required:
                      - action
                      - path
                      - value
                examples:
                  create:
                    value:
                      - action: create
                        path: /
                        value:
                          type: DEVICE
                          id: 2YjaqUmSr3ke2nmdssxAG5n0KDMwrJrvi8bTbzbdHelEEflqNkAx0WWmTIgyCQf
                          opt: IN
                  update:
                    value:
                      - action: update
                        path: /KRXXX
                        value:
                          opt: OUT
                  create/update:
                    value:
                      - action: create
                        path: /
                        value:
                          type: DEVICE
                          id: +2YjaqUmSr3ke2nmdssxAG5n0KDMwrJrvi8bTbzbdHelEEflqNkAx0WWmTIgyCQf
                          opt: IN
                      - action: update
                        path: /KRXXX
                        value:
                          opt: OUT
                      - action: update
                        path: /KRXXXY
                        value:
                          opt: IN
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`2000`: Successful operation'
                  example: 2000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      code:
                        type: integer
                        example: 2000
                      data:
                        type: object
                        properties:
                          value:
                            type: object
                            properties:
                              type:
                                type: string
                                example: DEVICE
                              id:
                                type: string
                                example: 2YjaqUmSr3ke2nmdssxAG5n0KDMwrJrvi8bTbzbdHelEEflqNkAx0WWmTIgyCQf
                              opt:
                                type: string
                                example: IN
                              status:
                                type: string
                                example: success
            '400':
              description: Bad Request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4102`: Missing or Invalid Parameter(s) in Request Body'
                  example: 4102
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4102
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Missing or Invalid Parameter(s) in Request Body
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4201`: Unauthorized'
                  example: 4201
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4302`: Resource Not Found: Event'
                  example: 4302
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4302
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: 'Resource Not Found: Event'
            '409':
              description: Conflict
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4315`: Resource Already Exists: Group'
                  example: 4315
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`5000`: Internal Server Error'
                  example: 5000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Internal Server Error
      /dr/data-zip/files:
        post:
          tags:
            - DR API
          summary: Create monitoring data files
          description: Request to create a ZIP file of monitoring data from devices that participated in a DR event during the DR event period.
          operationId: createDataZipFile
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Country-Code-2'
          requestBody:
            description: DR Event information
            content:
              application/json:
                schema:
                  type: object
                  properties:
                    eventId:
                      type: string
                      example: 2024-04-25-dr-01
                      description: DR Event ID
                    targets:
                      type: array
                      items:
                        properties:
                          targetId:
                            type: string
                            example: KR1234567890123
                            description: DR Event target ID
                          targetType:
                            type: string
                            example: USER
                            description: |-
                              DR Event target type
                              - USER
                              - DEVICE
                              - GROUP
                  required:
                    - eventId
                examples:
                  Create a Data Zip File:
                    value:
                      eventId: test_event_1713834322772
                      targets:
                        - targetType: GROUP
                          targetId: k-apt-1234567890
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`2000`: Successful operation'
                  example: 2000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      code:
                        type: integer
                        example: 2000
                      data:
                        type: object
                        properties:
                          fileName:
                            type: string
                            example: data-zip-test_event_1234567890123-2345678901234.zip
                            description: generated ZIP file name
            '400':
              description: Bad Request
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4102`: Missing or Invalid Parameter(s) in Request Body'
                  example: 4102
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4102
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Missing or Invalid Parameter(s) in Request Body
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4201`: Unauthorized'
                  example: 4201
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4302`: Resource Not Found: Event'
                  example: 4302
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4302
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: 'Resource Not Found: Event'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`5000`: Internal Server Error'
                  example: 5000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Internal Server Error
      /dr/data-zip/files/{filename}:
        get:
          tags:
            - DR API
          summary: Download monitoring data files
          description: Request a link to download a ZIP file of the monitoring data for the devices that participated in the DR event.
          operationId: downloadDataZipFile
          security:
            - ThinQ_Business_API_Key: []
          parameters:
            - required: true
              $ref: '#/components/parameters/X-Api-Token'
            - required: true
              $ref: '#/components/parameters/X-Message-Id'
            - required: true
              $ref: '#/components/parameters/X-Country-Code-2'
            - in: path
              name: filename
              description: generated ZIP file name
              required: true
              schema:
                type: string
                example: data-zip-test_event_1234567890123-2345678901234.zip
          responses:
            '200':
              description: OK
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`2000`: Successful operation'
                  example: 2000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      code:
                        type: integer
                        example: 2000
                      data:
                        type: object
                        properties:
                          presignedUrl:
                            type: string
                            example: https://s3-an2-tems-qa-dr-archiver.s3.ap-northeast-2.amazonaws.com/zip/data-zip-test_event_1234567890123-2345678901234?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIARU3MB3TCEDODQ2DO%2F20241004%2Fap-northeast-2%2Fs3%2Faws4_request&X-Amz-Date=20241004T002817Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEID%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLW5vcnRoZWFzdC0yIkcwRQIhALefnNnWXhAZcAcMWZA%2Bm23i5uALS%2FOI9ZwzOwUQMMQyAiACqvSExTC%2B3ErlEfOGtIXnZ450mlJRDu02kW4S2RojcyrVBQjJ%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDExMzUwNjM3NjkwMCIMi5fbbY%2Bs9%2FoMe2jWKqkFntfKoeTR0blrYtIPk0PdBLXhVa%2BpMgj9P0Y2%2F4c8g1IK0LOWuQrLL9bQ%2Bjg%2B4pzsgZWjdFZ8smSNqj3oQ%2FAgpHI56EltlZrnDQNPL%2FkMtj8dSgOJtxtgOE89wzYvB8hd9obkO0c%2BQN76loIX71y6MOC6JtCNlzbf0SpLkONT09IlOMhmFHB4KC87r%2Bb6V7ZIgFp56w9amawSxYK%2BCRj0yw5uXoboEUBwuqcn%2BSF6u2Xq4Z1cS018f%2F9bYtBxqz5M6rUrTup5xkf4ZEbUzFwMpFWk2WhXiu64uzKaF41C3d%2F5YUNa2K725HfWbntEAa0jr37AZtR%2BNagZGvnVnryZsmz%2Fn272kPdhdb3NLv55i1dtqWHu9HjJ2P35ujd5RadNO%2BCki9Vths6O99XDnHpCbrTWoQyCvHIq3wM38Nbbbnv%2BxXeKbzJ1PMbOmmGbqSPhGdFEwHzTiGLkiUXxREFtLLkC5xQn%2F%2FyBFmyoZBrpdVEvt6Ggyk5gh%2F%2BSxG1OvpmCcmYjRloE%2Bh%2F7QCZvboHaeD4wpre1xdRFrW%2FiPSeraR1MxurDFbf8nWqak88IQ%2B82EwOucjX6SKhdk148Vt6mBrd0Ae9MW7W4f82NksX%2FVFeDjeGmkRe4bg85B8b7gwIA8qHl3MwYhUgPm0%2BRlkzdFKYy%2B2eoBZpK0kx3tO52DIeb%2Fk41gfrxQj3lc41y7zKVxZsiftqK7bDbMt4eHkFZ5dTaf0uJlgzsU0AYanJjgZvDxlUCywCHfCTG%2Bb03dWwomJYy4cuN%2Fix8uYzYbM8TAdwFfjYKG0KH3n4W%2FDNvCiQBedoG%2Byx7e5MCr0dpAV2%2F90L9x%2Bq1HloUbqtnVqQ1MRV3PN%2FBv3brupENConWTz90ebLDCd4rJQLKmGprA0UOX2nI8yxMV6u6MLbl%2FLcGOrEBIPFbJuDYy4nYDv0IJF5FHnEM9hZFiC1s1kOPMQkUHbhXENPK4TWBPLx46Ewp%2FvT2PTdkzMVeZLVJ33YVg1V9uL%2BNT1KYs9KuwDdfCMUD22ItcGhm9DCHnp3Db%2FyyWus%2BtBVrdcIsbhtvyfVx0qsFa29MJmxdv%2FdTrOZZ8c6ZSFAOeM5RGsxTs9%2FBZrWyvHy6cbfcMlr8Utm%2BzCGxy5L87LkBhrD9wT6o1%2B3eGI333lGc&X-Amz-Signature=dcdb7b02b2350142fb4b41ab15036ac529981f7dc14d2fa2e6a4bf615b82f827&X-Amz-SignedHeaders=host&x-id=GetObject
                            description: Download path for generated DR Event ZIP file (valid for 1 hour)
            '401':
              description: Unauthorized
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4201`: Unauthorized'
                  example: 4201
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '404':
              description: Not Found
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`4306`: Resource Not Found: Zip File'
                  example: 4306
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 4306
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: 'Resource Not Found: Zip File'
            '429':
              description: Too Many Requests
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`6429`: Too Many Requests'
                  example: 6429
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
            '500':
              description: Internal Server Error
              headers:
                X-Response-Code:
                  schema:
                    type: string
                  description: '`5000`: Internal Server Error'
                  example: 5000
                X-Message-Id:
                  $ref: '#/components/headers/X-Message-Id-response'
              content:
                application/json:
                  schema:
                    type: object
                    description: Response of failed requests
                    properties:
                      code:
                        type: number
                        description: The status code
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: Detailed error message
                            example: Internal Server Error
      /your-callback-uri:
        post:
          summary: callback API of your service
          description: callback API of your service
          operationId: yourCallback
          security:
            - basic_auth: []
          servers:
            - url: https://your-domain
          requestBody:
            description: dummy
            content:
              application/json:
                schema:
                  oneOf:
                    - $ref: '#/components/schemas/push-callback-device-push-schema'
                    - $ref: '#/components/schemas/push-callback-device-registered-schema'
                    - $ref: '#/components/schemas/push-callback-device-unregistered-schema'
                    - $ref: '#/components/schemas/push-callback-device-alias-changed-schema'
                examples:
                  device-push-example:
                    $ref: '#/components/examples/push-callback-device-push-example'
                  device-registered-example:
                    $ref: '#/components/examples/push-callback-device-registered-example'
                  device-unregistered-example:
                    $ref: '#/components/examples/push-callback-device-unregistered-example'
                  device-alias-changed-example:
                    $ref: '#/components/examples/push-callback-device-alias-changed-example'
    components:
      securitySchemes:
        ThinQ_Business_API_Key:
          type: apiKey
          description: |
            The `API Key` string obtained after the partner request or permission updates was approved.
          in: header
          name: X-Api-Key
      schemas:
        api-token-res:
          type: object
          description: Response containing an API token
          properties:
            access_token:
              type: string
              description: API Token string, represented as a JWT (header.payload.signature).
              example: eyJhbGciOiJIUzI1NiIsImtpZCI6InNpbTIifQ.eyJleHAiOjE3MDQzNDE3MDIsImlhdCI6MTcwNDI1NTMwMiwiaXNzIjoiTEcgQnVzaW5lc3MgQ29ubmVjdCIsInJvbGVzIjpbImdldEJlY29uVXNlcnMiLCJnZXREclVzZXJzIiwicG9zdFRva2VuIl0sInN1YiI6IjRkMmM2MWUxLTM0YzQtZTk2Yy05NDU2LTE1YmQ5ODNjNTAxOSJ9.plRjXmZRoXkOy_U95VXGzX-ouJyCrorEmMO8OzrEvF8
        device-base-res:
          type: object
          description: The default response item for device
          properties:
            messageId:
              type: string
              description: The string from the `X-Message-Id` in the API request header
              example: 2ADaRijIk8CvaSHVPeEWNw
            timestamp:
              type: string
              description: The time the API request was received. Follows the `ISO-8601` format.
              example: '2024-10-01T06:23:20.866279'
        device-list-item:
          type: object
          title: Device list response
          properties:
            deviceId:
              type: string
              description: A specific device ID
              example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
            deviceInfo:
              type: object
              properties:
                deviceType:
                  type: string
                  description: Device type. For a list of supported device types, see the [**Device Profiles**](/en/apiManage/device_profile) page.
                  example: DEVICE_WASHTOWER_WASHER
                alias:
                  type: string
                  description: An alias of the device
                  example: My New WashTower Washer
                modelName:
                  type: string
                  description: A model name of the device
                  example: FAKPK21021
                reportable:
                  type: boolean
                  description: Whether or not your service can subscribe to events which occur when the device status changes
                  example: 'true'
                groupId:
                  type: string
                  description: An group ID that a device is in the same group as another device when the device type is `DEVICE_WASHTOWER_WASHER` or `DEVICE_WASHTOWER_DRYER`.
                  example: '171807013576723372'
                parentId:
                  type: string
                  description: The ID of the parent `ODU` device when the device type is `IDU`.
                  example: fe12ed5bca00acc0ed68ec9f632342d0822a929f377b76cbe700649a11053f23
              required:
                - deviceType
                - alias
          required:
            - deviceId
            - deviceInfo
        device-list-res:
          description: Device list response
          allOf:
            - $ref: '#/components/schemas/device-base-res'
            - type: object
              properties:
                response:
                  type: array
                  items:
                    allOf:
                      - $ref: '#/components/schemas/device-list-item'
        error-res-backend:
          type: object
          description: Response of failed requests
          properties:
            messageId:
              type: string
              description: Value of the request header `X-Message-Id`
              example: 2ADaRijIk8CvaSHVPeEWNw
            timestamp:
              type: datetime
              description: The current time
              example: '2024-09-13T06:55:58.65064'
            error:
              type: object
              description: Detailed error
              properties:
                message:
                  type: string
                  description: Detailed error message
                code:
                  type: string
                  description: Detailed error code
        device-profile-res:
          description: Response for profile of a specific device
          allOf:
            - $ref: '#/components/schemas/device-base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: For a schema of device profile messages by device type, see the [**Device Profile**](/en/apiManage/device_profile) page.
        device-status-res:
          description: Response for statas of a specific device
          allOf:
            - $ref: '#/components/schemas/device-base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: For a schema of device status response messages by device type, see the [**Device Profile**](/en/apiManage/device_profile) page.
        device-id-list-res:
          description: Response for Device ID list
          allOf:
            - $ref: '#/components/schemas/device-base-res'
            - type: object
              properties:
                response:
                  type: array
                  items:
                    type: object
                    properties:
                      deviceId:
                        type: string
                        description: A specific device ID
                        example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
        device-empty-res:
          description: No Content response
          allOf:
            - $ref: '#/components/schemas/device-base-res'
            - type: object
              properties:
                response:
                  type: object
        userno-res:
          description: Response of the uer number
          allOf:
            - $ref: '#/components/schemas/device-base-res'
            - type: object
              properties:
                response:
                  type: object
                  properties:
                    userNumber:
                      type: string
                      description: User number of the LG Electronics account
                      example: SaGvM4ETAgOHSAFhezzi
        dr-event-target-opt-res:
          type: object
          properties:
            type:
              type: string
              example: USER
              description: |-
                Target type
                - GROUP
                - USER
                - DEVICE
            id:
              type: string
              example: KRXXXX
              description: |-
                DR Event target ID
                - If the event target type is USER: userNo
                - If the event target type is GROUP: groupId
                - If the event target type is DEVICE: deviceId
            opt:
              type: string
              example: OUT
              description: |-
                You can check whether you are opted in or out of DR Event.
                 - IN : Opt in to DR Event(default)
                 - OUT : Opt out of DR Event
        callback-base-res:
          type: object
          description: Base Response items of callback
          properties:
            messageId:
              type: string
              description: A string generated with 22 characters of url-safe-base64-no-padding (UUID Version 4) to track the flow of API call processing.
              example: 8O4J3mY-dkKYhH4LSo-Hpw
            timestamp:
              type: string
              description: The time the message was created. Follows the `ISO-8601` format.
              example: '2024-10-01T06:23:20.866279'
        push-callback-device-push-schema:
          allOf:
            - $ref: '#/components/schemas/callback-base-res'
            - type: object
              properties:
                push:
                  type: object
                  properties:
                    pushType:
                      type: string
                      description: Push Type
                      example: DEVICE_PUSH
                    deviceId:
                      type: string
                      description: A specific device ID
                      example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
                    deviceType:
                      type: string
                      description: Device type. For a list of supported device types, see the [**Device Profiles**](/en/apiManage/device_profile) page.
                      example: DEVICE_WASHTOWER_WASHER
                    pushCode:
                      type: string
                      description: Push code. For a list of supported push codes, see the [**Device Profiles**](/en/apiManage/device_profile) page.
                      example: WASHING_IS_COMPLETE
                    userList:
                      type: array
                      description: List of user numbers of the LG Electronics account which subscribe push messages.
                      items:
                        type: string
                        example: n2uR0D5vLjvZRvTdvhVJ
        push-callback-device-registered-schema:
          allOf:
            - $ref: '#/components/schemas/callback-base-res'
            - type: object
              properties:
                push:
                  type: object
                  properties:
                    pushType:
                      type: string
                      description: Push Type
                      example: DEVICE_REGISTERED
                    userNumber:
                      type: string
                      description: User number of the LG Electronics account
                      example: SaGvM4ETAgOHSAFhezzi
                    deviceId:
                      type: string
                      description: A specific device ID
                      example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
                    deviceType:
                      type: string
                      description: Device type. For a list of supported device types, see the [**Device Profiles**](/en/apiManage/device_profile) page.
                      example: DEVICE_WASHTOWER_WASHER
                    alias:
                      type: string
                      description: An alias of the device
                      example: My New WashTower Washer
                    modelName:
                      type: string
                      description: A model name of the device
                      example: FAKPK21021
                    reportable:
                      type: boolean
                      description: Whether or not your service can subscribe to events which occur when the device status changes
                      example: 'true'
                    groupId:
                      type: string
                      description: Group ID for grouping WashTower devices which device types are `DEVICE_WASHTOWER_WASHER` or `DEVICE_WASHTOWER_DRYER`
                      example: '171807013576723372'
                  required:
                    - pushType
                    - userNumber
                    - deviceId
                    - deviceType
                    - alias
        push-callback-device-unregistered-schema:
          allOf:
            - $ref: '#/components/schemas/callback-base-res'
            - type: object
              properties:
                push:
                  type: object
                  properties:
                    pushType:
                      type: string
                      description: Push Type
                      example: DEVICE_UNREGISTERED
                    userNumber:
                      type: string
                      description: User number of the LG Electronics account
                      example: SaGvM4ETAgOHSAFhezzi
                    deviceId:
                      type: string
                      description: A specific device ID
                      example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
                    deviceType:
                      type: string
                      description: Device type. For a list of supported device types, see the [**Device Profiles**](/en/apiManage/device_profile) page.
                      example: DEVICE_WASHTOWER_WASHER
                    alias:
                      type: string
                      description: An alias of the device
                      example: My New WashTower Washer
        push-callback-device-alias-changed-schema:
          allOf:
            - $ref: '#/components/schemas/callback-base-res'
            - type: object
              properties:
                push:
                  type: object
                  properties:
                    pushType:
                      type: string
                      description: Push Type
                      example: DEVICE_ALIAS_CHANGED
                    userNumber:
                      type: string
                      description: User number of the LG Electronics account
                      example: SaGvMtETAgOHSAFhezzi
                    deviceId:
                      type: string
                      description: A specific device ID
                      example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
                    alias:
                      type: string
                      description: An alias of the device
                      example: My New WashTower Washer
      parameters:
        X-Api-Token:
          name: X-Api-Token
          in: header
          schema:
            type: string
          description: |
            `API Token`, a string that is issued in advance through the **[Issue API Token](#tag/auth/operation/createAPIToken)** API.
          example: eyJhbGciOiJIUzI1NiIsImtpZCI6InNpbTIifQ.eyJleHAiOjE3MDQzNDE3MDIsImlhdCI6MTcwNDI1NTMwMiwiaXNzIjoiTEcgQnVzaW5lc3MgQ29ubmVjdCIsInJvbGVzIjpbImdldEJlY29uVXNlcnMiLCJnZXREclVzZXJzIiwicG9zdFRva2VuIl0sInN1YiI6IjRkMmM2MWUxLTM0YzQtZTk2Yy05NDU2LTE1YmQ5ODNjNTAxOSJ9.plRjXmZRoXkOy_U95VXGzX-ouJyCrorEmMO8OzrEvF8
        X-Message-Id:
          name: X-Message-Id
          in: header
          schema:
            type: string
          description: |
            A string generated by the API's client with 22 characters of url-safe-base64-no-padding (UUID Version 4) to track the flow of API call processing.
          example: 2ADaRijIk8CvaSHVPeEWNw
        X-Use-Account:
          name: X-Use-Account
          in: header
          schema:
            type: string
          description: |
            The source of the LG Electronics account to use when processing API requests.

              |Value|Description|
              |-|-|
              |REGISTERED|The account that have already registered through partner requests or permission updates.|
              |IN-HEADER|The account specified as the OAuth token in the `Authorization` header of this HTTP request. (**Currently, only LG ThinQ registered devices are supported.**)|
          example: REGISTERED
        Authorization:
          name: Authorization
          in: header
          schema:
            type: string
          description: |
            The `Bearer` OAuth token of the LG Electronics account that subscribed to LG ThinQ. If the `X-Use-Account` header is included in the HTTP request and the value of the header is `IN-HEADER`, this header must be included in the request.
          example: Bearer 5a9a713f51a95c53d781addd1af0dfa4f6e1e7420a8bff3c5198308dac571aa9845832b8d29bbe1f04deec2d35229c6d
        X-Country-Code:
          name: X-Country-Code
          in: header
          schema:
            type: string
          description: |
            The `ISO-3166 alpha-2` country code for the countries supported by LG ThinQ. If the `X-Use-Account` header is included in the HTTP request and the value of the header is `IN-HEADER`, this header must be included in the request and must be the code of the country of registration of the LG Electronics account specified in `Authorization`.
          example: KR
        deviceId:
          name: deviceId
          in: path
          schema:
            type: string
          description: A specific device ID
          example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
        Authorization-2:
          name: Authorization
          in: header
          schema:
            type: string
          description: |
            The `Bearer` OAuth token of the LG Electronics account that signed up for the LG ThinQ.
          example: Bearer 5a9a713f51a95c53d781addd1af0dfa4f6e1e7420a8bff3c5198308dac571aa9845832b8d29bbe1f04deec2d35229c6d
        X-Country-Code-2:
          name: X-Country-Code
          in: header
          schema:
            type: string
          description: |
            The `ISO-3166 alpha-2` country code for the countries supported by LG Electronics
          example: KR
      headers:
        X-Message-Id-response:
          schema:
            type: string
          description: |
            A string generated by the API's client with 22 characters of url-safe-base64-no-padding (UUID Version 4) to track the flow of API call processing.
          example: 2ADaRijIk8CvaSHVPeEWNw
      examples:
        refrigerator-profile-example:
          value:
            property:
              temperature:
                - locationName: FRIDGE
                  unit: C
                  targetTemperature:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 7
                        min: 0
                        step: 1
                      w:
                        max: 7
                        min: 0
                        step: 1
                - locationName: FREEZER
                  unit: C
                  targetTemperature:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: -16
                        min: -21
                        step: 1
                      w:
                        max: -16
                        min: -21
                        step: 1
              temperatureInUnits:
                - targetTemperatureC:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 8
                        min: 1
                        step: 1
                      w:
                        max: 8
                        min: 1
                        step: 1
                  targetTemperatureF:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 46
                        min: 33
                        step: 1
                      w:
                        max: 46
                        min: 33
                        step: 1
                  unit:
                    type: enum
                    mode:
                      - r
                    value:
                      r:
                        - C
                        - F
                  locationName: FRIDGE
                - targetTemperatureC:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: -13
                        min: -21
                        step: 1
                      w:
                        max: -13
                        min: -21
                        step: 1
                  targetTemperatureF:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 8
                        min: -6
                        step: 1
                        except:
                          - -5
                          - 7
                      w:
                        max: 8
                        min: -6
                        step: 1
                        except:
                          - -5
                          - 7
                  unit:
                    type: enum
                    mode:
                      - r
                    value:
                      r:
                        - C
                        - F
                  locationName: FREEZER
              refrigeration:
                expressMode:
                  type: boolean
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - true
                      - false
                    w:
                      - true
                      - false
                expressModeName:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - FREEZER
                freshAirFilter:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - 'OFF'
                      - AUTO
                    w:
                      - 'OFF'
                      - AUTO
              doorStatus:
                - doorState:
                    type: enum
                    mode:
                      - r
                    value:
                      r:
                        - OPEN
                        - CLOSE
                  locationName: MAIN
              waterFilterInfo:
                usedTime:
                  type: number
                  mode:
                    - r
            notification:
              push:
                - TIME_TO_CHANGE_WATER_FILTER
                - TIME_TO_CHANGE_FILTER
                - DOOR_IS_OPEN
                - FROZEN_IS_COMPLETE
        washer-profile-example:
          value:
            error:
              - DOOR_OPEN_ERROR
              - TEMPERATURE_SENSOR_ERROR
              - OUT_OF_BALANCE_ERROR
              - WATER_LEVEL_SENSOR_ERROR
              - LOCKED_MOTOR_ERROR
              - WATER_DRAIN_ERROR
              - UNABLE_TO_LOCK_ERROR
              - OVERFILL_ERROR
              - WATER_SUPPLY_ERROR
            notification:
              push:
                - WASHING_IS_COMPLETE
                - ERROR_DURING_WASHING
            property:
              - detergent:
                  detergentSetting: NORMAL
                cycle:
                  cycleCount:
                    type: number
                    mode:
                      - r
                location:
                  locationName: MAIN
                operation:
                  washerOperationMode:
                    mode:
                      - w
                    type: enum
                    value:
                      w:
                        - START
                        - STOP
                        - POWER_OFF
                remoteControlEnable:
                  remoteControlEnabled:
                    mode:
                      - r
                    type: boolean
                    value:
                      r:
                        - false
                        - true
                runState:
                  currentState:
                    mode:
                      - r
                    type: enum
                    value:
                      r:
                        - RUNNING
                        - INITIAL
                        - RINSING
                        - SPINNING
                        - FIRMWARE
                        - RESERVED
                        - PAUSE
                        - POWER_OFF
                        - DETECTING
                        - END
                        - SOAKING
                        - ERROR
                timer:
                  relativeHourToStart:
                    mode:
                      - r
                      - w
                    type: range
                    value:
                      r:
                        except: []
                        max: 19
                        min: 0
                        step: 1
                      w:
                        except: []
                        max: 19
                        min: 0
                        step: 1
                  relativeMinuteToStart:
                    mode:
                      - r
                    type: range
                    value:
                      r:
                        except: []
                        max: 59
                        min: 0
                        step: 1
                  remainHour:
                    mode:
                      - r
                    type: range
                    value:
                      r:
                        except: []
                        max: 30
                        min: 0
                        step: 1
                  remainMinute:
                    mode:
                      - r
                    type: range
                    value:
                      r:
                        except: []
                        max: 59
                        min: 0
                        step: 1
                  totalHour:
                    mode:
                      - r
                    type: range
                    value:
                      r:
                        except: []
                        max: 30
                        min: 0
                        step: 1
                  totalMinute:
                    mode:
                      - r
                    type: range
                    value:
                      r:
                        except: []
                        max: 59
                        min: 0
                        step: 1
        dryer-profile-example:
          value:
            error:
              - DOOR_SENSOR_ERROR
              - COMPRESSOR_ERROR
              - TEMPERATURE_SENSOR_ERROR
              - DRAINMOTOR_ERROR
              - EMPTY_WATER_ALERT_ERROR
              - MOTOR_LOCK_ERROR
              - DOOR_OPEN_ERROR
              - HIGH_TEMPERATURE_DETECTION_ERROR
              - DOOR_LOCK_ERROR
              - NO_FILTER_ERROR
            notification:
              push:
                - DRYING_IS_COMPLETE
                - DRYING_FAILED
            property:
              operation:
                dryerOperationMode:
                  mode:
                    - w
                  type: enum
                  value:
                    w:
                      - START
                      - STOP
                      - POWER_OFF
                      - WAKE_UP
              remoteControlEnable:
                remoteControlEnabled:
                  mode:
                    - r
                  type: boolean
                  value:
                    r:
                      - false
                      - true
              runState:
                currentState:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - INITIAL
                      - ERROR
                      - SLEEP
                      - DETECTING
                      - COOLING
                      - WRINKLE_CARE
                      - RESERVED
                      - POWER_OFF
                      - RUNNING
                      - PAUSE
                      - END
              timer:
                relativeHourToStop:
                  mode:
                    - r
                    - w
                  type: range
                  value:
                    r:
                      max: 19
                      min: 3
                    w:
                      max: 19
                      min: 3
                relativeMinuteToStop:
                  mode:
                    - r
                  type: number
                remainHour:
                  mode:
                    - r
                  type: number
                remainMinute:
                  mode:
                    - r
                  type: number
                totalHour:
                  mode:
                    - r
                  type: number
                totalMinute:
                  mode:
                    - r
                  type: number
        air_conditioner-profile-example:
          value:
            notification:
              push:
                - WATER_IS_FULL
            property:
              airConJobMode:
                currentJobMode:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - AIR_DRY
                      - COOL
                      - AIR_CLEAN
                    w:
                      - AIR_DRY
                      - COOL
                      - AIR_CLEAN
              airFlow:
                windStrength:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - HIGH
                      - LOW
                      - MID
                    w:
                      - HIGH
                      - LOW
                      - MID
              windDirection:
                airGuideWind:
                  type: boolean
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - true
                      - false
                    w:
                      - true
                      - false
                swirlWind:
                  type: boolean
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - true
                      - false
                    w:
                      - true
                      - false
                highCeilingWind:
                  type: boolean
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - true
                      - false
                    w:
                      - true
                      - false
                concentrationWind:
                  type: boolean
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - true
                      - false
                    w:
                      - true
                      - false
                autoFitWind:
                  type: boolean
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - true
                      - false
                    w:
                      - true
                      - false
                forestWind:
                  type: boolean
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - true
                      - false
                    w:
                      - true
                      - false
              filterInfo:
                filterLifetime:
                  mode:
                    - r
                  type: number
                usedTime:
                  mode:
                    - r
                  type: number
                filterRemainPercent:
                  mode:
                    - r
                  type: number
              airQualitySensor:
                PM1:
                  mode:
                    - r
                  type: number
                PM10:
                  mode:
                    - r
                  type: number
                PM2:
                  mode:
                    - r
                  type: number
                humidity:
                  mode:
                    - r
                  type: number
                totalPollution:
                  mode:
                    - r
                  type: number
                totalPollutionLevel:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - INVALID
                      - GOOD
                      - NORMAL
                      - BAD
                      - VERY_BAD
                monitoringEnabled:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - ON_WORKING
                      - ALWAYS
                    w:
                      - ON_WORKING
                      - ALWAYS
              operation:
                airCleanOperationMode:
                  mode:
                    - w
                  type: enum
                  value:
                    w:
                      - STOP
                      - START
                airConOperationMode:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - POWER_OFF
                      - POWER_ON
                    w:
                      - POWER_OFF
                      - POWER_ON
              powerSave:
                powerSaveEnabled:
                  mode:
                    - r
                    - w
                  type: boolean
                  value:
                    r:
                      - false
                      - true
                    w:
                      - false
                      - true
              sleepTimer:
                relativeHourToStop:
                  mode:
                    - r
                    - w
                  type: number
                relativeMinuteToStop:
                  mode:
                    - r
                    - w
                  type: number
                relativeStopTimer:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - SET
                      - UNSET
                    w:
                      - UNSET
              temperature:
                coolTargetTemperature:
                  mode:
                    - w
                  type: range
                  value:
                    w:
                      max: 30
                      min: 18
                      step: 1
                currentTemperature:
                  mode:
                    - r
                  type: number
                targetTemperature:
                  mode:
                    - r
                    - w
                  type: range
                  value:
                    r:
                      max: 30
                      min: 18
                      step: 1
                    w:
                      max: 30
                      min: 18
                      step: 1
                unit:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - C
              temperatureInUnits:
                - currentTemperature:
                    type: number
                    mode:
                      - r
                  targetTemperature:
                    type: number
                    mode:
                      - r
                  coolTargetTemperature:
                    type: range
                    mode:
                      - w
                    value:
                      w:
                        max: 30
                        min: 16
                        step: 0.5
                  heatTargetTemperature:
                    type: range
                    mode:
                      - w
                    value:
                      w:
                        max: 30
                        min: 16
                        step: 0.5
                  unit: C
                - currentTemperature:
                    type: number
                    mode:
                      - r
                  targetTemperature:
                    type: number
                    mode:
                      - r
                  coolTargetTemperature:
                    type: range
                    mode:
                      - w
                    value:
                      w:
                        max: 86
                        min: 60
                        step: 1
                  heatTargetTemperature:
                    type: range
                    mode:
                      - w
                    value:
                      w:
                        max: 86
                        min: 60
                        step: 1
                  unit: F
              twoSetTemperature:
                currentTemperature:
                  type: number
                  mode:
                    - r
                unit:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - C
                coolTargetTemperature:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 37.5
                      min: 10
                      step: 0.5
                    w:
                      max: 37.5
                      min: 10
                      step: 0.5
                heatTargetTemperature:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 32
                      min: 4
                      step: 0.5
                    w:
                      max: 32
                      min: 4
                      step: 0.5
                twoSetEnabled:
                  type: boolean
                  mode:
                    - r
                  value:
                    r:
                      - true
                      - false
              twoSetTemperatureInUnits:
                - unit: C
                  coolTargetTemperature:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 37.5
                        min: 10
                        step: 0.5
                      w:
                        max: 37.5
                        min: 10
                        step: 0.5
                  heatTargetTemperature:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 32
                        min: 4
                        step: 0.5
                      w:
                        max: 32
                        min: 4
                        step: 0.5
                - unit: F
                  coolTargetTemperature:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 99
                        min: 50
                        step: 1
                      w:
                        max: 99
                        min: 50
                        step: 1
                  heatTargetTemperature:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 90
                        min: 40
                        step: 1
                      w:
                        max: 90
                        min: 40
                        step: 1
              timer:
                relativeHourToStart:
                  mode:
                    - r
                    - w
                  type: number
                relativeHourToStop:
                  mode:
                    - r
                    - w
                  type: number
                relativeMinuteToStart:
                  mode:
                    - r
                    - w
                  type: number
                relativeMinuteToStop:
                  mode:
                    - r
                    - w
                  type: number
                relativeStartTimer:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - SET
                      - UNSET
                    w:
                      - UNSET
                relativeStopTimer:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - SET
                      - UNSET
                    w:
                      - UNSET
              display:
                light:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - 'ON'
                      - 'OFF'
                    w:
                      - 'ON'
                      - 'OFF'
        air_purifier-profile-example:
          value:
            notification:
              push:
                - TIME_TO_CHANGE_FILTER
                - TIME_TO_CLEAN_FILTER
                - POLLUTION_IS_HIGH
                - LACK_OF_WATER
            property:
              airFlow:
                windStrength:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - LOW
                      - MID
                      - HIGH
                      - AUTO
                      - POWER
                    w:
                      - LOW
                      - MID
                      - HIGH
                      - AUTO
                      - POWER
              airPurifierJobMode:
                currentJobMode:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - CLEAN
                      - AUTO
                      - CIRCULATOR
                      - DUAL_CLEAN
                    w:
                      - CLEAN
                      - AUTO
                      - CIRCULATOR
                      - DUAL_CLEAN
              airQualitySensor:
                PM1:
                  mode:
                    - r
                  type: number
                PM10:
                  mode:
                    - r
                  type: number
                PM2:
                  mode:
                    - r
                  type: number
                monitoringEnabled:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - ON_WORKING
                      - ALWAYS
                oder:
                  mode:
                    - r
                  type: number
                odor:
                  mode:
                    - r
                  type: number
                odorLevel:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - INVALID
                      - WEAK
                      - NORMAL
                      - STRONG
                      - VERY_STRONG
                totalPollution:
                  mode:
                    - r
                  type: number
                totalPollutionLevel:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - INVALID
                      - GOOD
                      - NORMAL
                      - BAD
                      - VERY_BAD
              operation:
                airPurifierOperationMode:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - POWER_ON
                      - POWER_OFF
                    w:
                      - POWER_ON
                      - POWER_OFF
              timer:
                absoluteHourToStart:
                  mode:
                    - r
                    - w
                  type: number
                absoluteHourToStop:
                  mode:
                    - r
                    - w
                  type: number
                absoluteMinuteToStart:
                  mode:
                    - r
                    - w
                  type: number
                absoluteMinuteToStop:
                  mode:
                    - r
                    - w
                  type: number
                absoluteStartTimer:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - SET
                      - UNSET
                    w:
                      - UNSET
                absoluteStopTimer:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - SET
                      - UNSET
                    w:
                      - UNSET
              sleepTimer:
                relativeHourToStop:
                  mode:
                    - r
                    - w
                  type: number
                relativeMinuteToStop:
                  mode:
                    - r
                  type: number
                relativeStopTimer:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - SET
                      - UNSET
                    w:
                      - UNSET
        robot_cleaner-profile-example:
          title: Robot_Cleaner
          value:
            property:
              runState:
                currentState:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - CHARGING
                      - MACROSECTOR
                      - WORKING
                      - SLEEP
                      - INITIALIZING
                      - HOMING
                      - PAUSE
                      - RESERVATION
                      - STANDBY
                      - SETDATE
                      - DIAGNOSIS
                      - ERROR
              robotCleanerJobMode:
                currentJobMode:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - ZIGZAG
                      - SELECT
                      - SECTOR_BASE
                      - SPOT
                      - EDGE
                      - MACRO
              operation:
                cleanOperationMode:
                  type: enum
                  mode:
                    - w
                  value:
                    w:
                      - HOMING
                      - WAKE_UP
                      - PAUSE
                      - START
              battery:
                level:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - MOVELESS
                      - DOCK_LEVEL
                      - LOW
                      - MID
                      - HIGH
                      - FULL
                      - OVER_CHARGE
                percent:
                  type: number
                  mode:
                    - r
              timer:
                runningHour:
                  type: number
                  mode:
                    - r
                runningMinute:
                  type: number
                  mode:
                    - r
                absoluteHourToStart:
                  type: number
                  mode:
                    - r
                absoluteMinuteToStart:
                  type: number
                  mode:
                    - r
            notification:
              push:
                - MOTION_IS_DETECTED
                - HOMEGUARD_IS_STOPPED
                - CLEANING_IS_COMPLETED
                - SCHEDULED_CLEANING_STARTS
                - NEED_TO_CHECK_LOCATION
                - CLEANING_IS_FAILED
            error:
              - RIGHT_WHEEL_ERROR
              - MOVE_ERROR
              - UNKNOWN_ERROR
              - NO_DUST_BIN_ERROR
              - BLOCK_ERROR
              - BRUSH_ERROR
              - MOP_ERROR
              - CLIFF_ERROR
              - SUCTION_BLOCKED_ERROR
        oven-profile-example:
          title: Oven
          value:
            notification:
              push:
                - PREHEATING_IS_COMPLETE
                - COOKING_IS_COMPLETE
                - ERROR_HAS_OCCURRED
                - TIME_TO_CLEAN
            property:
              - location:
                  locationName: UPPER
                remoteControlEnable:
                  remoteControlEnabled:
                    mode:
                      - r
                    type: boolean
                    value:
                      r:
                        - false
                        - true
                runState:
                  currentState:
                    mode:
                      - r
                    type: enum
                    value:
                      r:
                        - COOLING
                        - PREHEATING
                        - INITIAL
                        - COOKING_IN_PROGRESS
                        - DONE
                        - CLEANING
                        - ERROR
                        - CLEANING_IS_DONE
                operation:
                  ovenOperationMode:
                    type: enum
                    mode:
                      - w
                    value:
                      w:
                        - STOP
                temperature:
                  - targetTemperature:
                      mode:
                        - r
                      type: number
                    unit: F
                  - targetTemperature:
                      mode:
                        - r
                      type: number
                    unit: C
                timer:
                  remainHour:
                    mode:
                      - r
                    type: number
                  remainMinute:
                    mode:
                      - r
                    type: number
                  remainSecond:
                    mode:
                      - r
                    type: number
            extensionProperty:
              info:
                type: SINGLE
        dish_washer-profile-example:
          value:
            error:
              - HEATER_CIRCUIT_ERROR
              - BUBBLE_ERROR
              - WATER_LEAKAGE_ERROR
              - MOTOR_ERROR
              - WATER_SUPPLY_ERROR
              - WATER_DRAIN_ERROR
              - TEMPERATURE_SENSOR_ERROR
            notification:
              push:
                - RINSE_IS_NOT_ENOUGH
                - ERROR_DURING_CLEANING
                - CLEANING_IS_COMPLETE
                - SALT_REFILL_IS_NEEDED
                - WATER_LEAK_HAS_OCCURRED
            property:
              dishWashingCourse:
                currentDishWashingCourse:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - DELICATE
                      - TURBO
                      - RINSE
                      - REFRESH
                      - HEAVY
                      - NORMAL
                      - AUTO
                      - EXPRESS
                      - MACHINE_CLEAN
                      - DOWNLOAD_CYCLE
              dishWashingStatus:
                rinseRefill:
                  mode:
                    - r
                  type: boolean
                  value:
                    r:
                      - false
                      - true
              doorStatus:
                doorState:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - CLOSE
                      - OPEN
              preference:
                cleanLReminder:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - CLEANLREMINDER_OFF
                      - CLEANLREMINDER_ON
                mCReminder:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - MCREMINDER_ON
                      - MCREMINDER_OFF
                rinseLevel:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - RINSELEVEL_4
                      - RINSELEVEL_0
                      - RINSELEVEL_1
                      - RINSELEVEL_2
                      - RINSELEVEL_3
                signalLevel:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - SIGNALLEVEL_ON
                      - SIGNALLEVEL_OFF
                softeningLevel:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - SOFTENINGLEVEL_4
                      - SOFTENINGLEVEL_2
                      - SOFTENINGLEVEL_3
                      - SOFTENINGLEVEL_1
                      - SOFTENINGLEVEL_0
              runState:
                currentState:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - POWER_FAIL
                      - INITIAL
                      - CANCEL
                      - PAUSE
                      - RUNNING
                      - RESERVED
                      - POWER_OFF
                      - NIGHT_DRY
                      - RINSING
                      - END
                      - DRYING
                      - ERROR
              timer:
                relativeHourToStart:
                  mode:
                    - r
                  type: number
                relativeMinuteToStart:
                  mode:
                    - r
                  type: number
                remainHour:
                  mode:
                    - r
                  type: number
                remainMinute:
                  mode:
                    - r
                  type: number
                totalHour:
                  mode:
                    - r
                  type: number
                totalMinute:
                  mode:
                    - r
                  type: number
        styler-profile-example:
          value:
            property:
              runState:
                currentState:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - SLEEP
                      - RUNNING
                      - STAY
                      - RESERVED
                      - INITIAL
                      - POWER_OFF
                      - DRYING
                      - COOLING
                      - END_COOLING
                      - COMPLETE
                      - STERILIZE
                      - PAUSE
                      - NIGHT_DRY
                      - RUNNING_END
                      - PREHEAT
                      - DIAGNOSIS
                      - PRESTEAM
                      - STEAM
                      - FOTA
                      - ERROR
              operation:
                stylerOperationMode:
                  type: enum
                  mode:
                    - w
                  value:
                    w:
                      - POWER_OFF
                      - STOP
                      - START
                      - WAKE_UP
              remoteControlEnable:
                remoteControlEnabled:
                  type: boolean
                  mode:
                    - r
                  value:
                    r:
                      - true
                      - false
              timer:
                relativeHourToStop:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      min: 3
                      max: 19
                    w:
                      min: 3
                      max: 19
                relativeMinuteToStop:
                  type: number
                  mode:
                    - r
                remainHour:
                  type: number
                  mode:
                    - r
                remainMinute:
                  type: number
                  mode:
                    - r
                totalHour:
                  type: number
                  mode:
                    - r
                totalMinute:
                  type: number
                  mode:
                    - r
            notification:
              push:
                - STYLING_IS_COMPLETE
                - ERROR_HAS_OCCURRED
            error:
              - NEED_WATER_DRAIN
              - DOOR_CLOSE_ERROR
              - TEMPERATURE_SENSOR_ERROR
              - WATER_LEAKS_ERROR
              - WATER_LEVEL_SENSOR_ERROR
              - STEAM_HEAT_ERROR
              - LE_ERROR
              - LE2_ERROR
              - DOOR_OPEN_ERROR
              - NEED_WATER_REPLENISHMENT
        water_purifier-profile-example:
          value:
            property:
              runState:
                cockState:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - CLEANING
                      - NORMAL
              waterInfo:
                waterType:
                  mode:
                    - r
                  type: list
                  value:
                    r:
                      - COLD
                      - NORMAL
                      - HOT
                      - SODA
        dehumidifier-profile-example:
          value:
            notification:
              push:
                - WATER_IS_FULL
            property:
              airFlow:
                windStrength:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - LOW
                      - HIGH
                    w:
                      - LOW
                      - HIGH
              dehumidifierJobMode:
                currentJobMode:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - QUIET_HUMIDITY
                      - CLOTHES_DRY
                      - INTENSIVE_DRY
                      - SMART_HUMIDITY
                      - RAPID_HUMIDITY
                      - AIR_CLEAN
              humidity:
                currentHumidity:
                  mode:
                    - r
                  type: range
                  value:
                    r:
                      max: 100
                      min: 0
                      step: 1
                targetHumidity:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 70
                      min: 30
                      step: 5
                    w:
                      max: 70
                      min: 30
                      step: 5
              operation:
                dehumidifierOperationMode:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - POWER_ON
                      - POWER_OFF
                    w:
                      - POWER_ON
                      - POWER_OFF
              timer:
                absoluteHourToStart:
                  mode:
                    - r
                    - w
                  type: number
                absoluteHourToStop:
                  mode:
                    - r
                    - w
                  type: number
                absoluteMinuteToStart:
                  mode:
                    - r
                    - w
                  type: number
                absoluteMinuteToStop:
                  mode:
                    - r
                    - w
                  type: number
                absoluteStartTimer:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - SET
                      - UNSET
                    w:
                      - UNSET
                absoluteStopTimer:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - SET
                      - UNSET
                    w:
                      - UNSET
        ceiling_fan-profile-example:
          value:
            property:
              airFlow:
                windStrength:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - TURBO
                      - HIGH
                      - LOW
                      - MID
                    w:
                      - TURBO
                      - HIGH
                      - LOW
                      - MID
              operation:
                ceilingfanOperationMode:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - POWER_ON
                      - POWER_OFF
                    w:
                      - POWER_ON
                      - POWER_OFF
        wine_cellar-profile-example:
          value:
            property:
              temperature:
                - locationName: WINE_UPPER
                  unit: C
                  targetTemperature:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 18
                        min: 5
                        step: 1
                        except: []
                      w:
                        max: 18
                        min: 5
                        step: 1
                        except: []
                - locationName: WINE_LOWER
                  unit: C
                  targetTemperature:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 18
                        min: 5
                        step: 1
                        except: []
                      w:
                        max: 18
                        min: 5
                        step: 1
                        except: []
              temperatureInUnits:
                - locationName: WINE_UPPER
                  targetTemperatureC:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 18
                        min: 11
                        step: 1
                        except: []
                      w:
                        max: 18
                        min: 11
                        step: 1
                        except: []
                  targetTemperatureF:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 18
                        min: 11
                        step: 1
                        except: []
                      w:
                        max: 18
                        min: 11
                        step: 1
                        except: []
                  unit:
                    type: enum
                    mode:
                      - r
                    value:
                      r:
                        - C
                        - F
                - locationName: WINE_LOWER
                  targetTemperatureC:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 11
                        min: 5
                        step: 1
                        except: []
                      w:
                        max: 11
                        min: 5
                        step: 1
                        except: []
                  targetTemperatureF:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 11
                        min: 5
                        step: 1
                        except: []
                      w:
                        max: 11
                        min: 5
                        step: 1
                        except: []
                  unit:
                    type: enum
                    mode:
                      - r
                    value:
                      r:
                        - C
                        - F
              operation:
                lightStatus:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 0
                      step: 10
                    w:
                      max: 100
                      min: 0
                      step: 10
            notification:
              push:
                - DOOR_IS_OPEN
        kimchi_refrigerator-profile-example:
          value:
            notification:
              push:
                - DOOR_IS_OPEN
            property:
              refrigeration:
                oneTouchFilter:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - 'OFF'
                      - 'ON'
              temperature:
                - locationName: TOP
                  targetTemperature:
                    mode:
                      - r
                    type: enum
                    value:
                      r:
                        - FREEZER
                        - FRIDGE
                        - KIMCHI
                        - 'OFF'
                - locationName: MIDDLE
                  targetTemperature:
                    mode:
                      - r
                    type: enum
                    value:
                      r:
                        - VEGETABLE_FRUIT
                        - KIMCHI
                        - MEAT_FISH
                        - 'OFF'
                - locationName: BOTTOM
                  targetTemperature:
                    mode:
                      - r
                    type: enum
                    value:
                      r:
                        - KIMCHI
                        - STORAGE
                        - 'OFF'
                        - VEGETABLE_FRUIT
                        - RICE_GRAIN
        home_brew-profile-example:
          value:
            property:
              recipe:
                beerRemain:
                  mode:
                    - r
                  type: range
                  value:
                    r:
                      max: 100
                      min: 0
                      step: 1
                flavorInfo:
                  mode:
                    - r
                  type: list
                  value:
                    r:
                      - ORANGE
                      - CORIANDER
                      - CORIANDER_SEED
                flavorCapsule1:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - ORANGE
                      - CORIANDER
                flavorCapsule2:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - ORANGE
                      - CORIANDER_SEED
                hopOilInfo:
                  mode:
                    - r
                  type: list
                  value:
                    r:
                      - FUGGLES
                      - CASCADE
                      - HALLERTAU
                      - CITRUSSY
                      - GOLDINGS
                      - CHINOOK
                hopOilCapsule1:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - FUGGLES
                      - CASCADE
                      - HALLERTAU
                      - CITRUSSY
                      - GOLDINGS
                      - CHINOOK
                hopOilCapsule2:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - FUGGLES
                      - CASCADE
                      - HALLERTAU
                      - CITRUSSY
                      - GOLDINGS
                      - CHINOOK
                recipeName:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - PALE_ALE
                      - MY_RECIPE
                      - RED_ALE
                      - STOUT
                      - WHEAT
                      - PILSNER
                      - IPA
                wortInfo:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - DARK
                      - HOPPY
                      - WHEAT
                      - DEEP_GOLD
                yeastInfo:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - ENGLISH_ALE
                      - AMERICAN_ALE
                      - LAGER
                      - WEIZEN
              runState:
                currentState:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - PREPAREING_FERMENTATION
                      - STANDBY
                      - DURING_FERMENTATION
                      - TEMPERATURE_STABILIZATION
                      - EXTRACTION_MODE
                      - DURING_AGING
                      - EXTRACTING_CAPSULE
                      - MELTING
                      - AS_POP_UP
                      - CARBONATION
              timer:
                elapsedDayState:
                  mode:
                    - r
                  type: range
                  value:
                    r:
                      max: 2731
                      min: 0
                      step: 1
                elapsedDayTotal:
                  mode:
                    - r
                  type: range
                  value:
                    r:
                      max: 2731
                      min: 0
                      step: 1
        plant_cultivator-profile-example:
          value:
            property:
              - location:
                  locationName: UPPER
                runState:
                  currentState:
                    type: enum
                    mode:
                      - r
                    value:
                      r:
                        - POWER_ON
                        - POWER_OFF
                  growthMode:
                    type: enum
                    mode:
                      - r
                    value:
                      r:
                        - STANDARD
                        - EXT_FLOWER
                        - EXT_HERB
                        - EXT_LEAF
                        - EXT_EXPERT
                  windVolume:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 1
                        max: 3
                        step: 1
                light:
                  brightness:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 1
                        max: 5
                        step: 1
                  duration:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 10
                        max: 18
                        step: 1
                  startHour:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 0
                        max: 23
                        step: 1
                  startMinute:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 0
                        max: 50
                        step: 10
                  endHour:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 0
                        max: 23
                        step: 1
                  endMinute:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 0
                        max: 50
                        step: 10
                temperature:
                  dayTargetTemperature:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 22
                        max: 29
                        step: 1
                  nightTargetTemperature:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 15
                        max: 21
                        step: 1
              - location:
                  locationName: LOWER
                runState:
                  currentState:
                    type: enum
                    mode:
                      - r
                    value:
                      r:
                        - POWER_ON
                        - POWER_OFF
                  growthMode:
                    type: enum
                    mode:
                      - r
                    value:
                      r:
                        - STANDARD
                        - EXT_FLOWER
                        - EXT_HERB
                        - EXT_LEAF
                        - EXT_EXPERT
                  windVolume:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 1
                        max: 3
                        step: 1
                light:
                  brightness:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 1
                        max: 5
                        step: 1
                  duration:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 10
                        max: 18
                        step: 1
                  startHour:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 0
                        max: 23
                        step: 1
                  startMinute:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 0
                        max: 50
                        step: 10
                  endHour:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 0
                        max: 23
                        step: 1
                  endMinute:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 0
                        max: 50
                        step: 10
                temperature:
                  dayTargetTemperature:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 22
                        max: 29
                        step: 1
                  nightTargetTemperature:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        min: 15
                        max: 21
                        step: 1
        washtower_washer-profile-example:
          value:
            error:
              - TEMPERATURE_SENSOR_ERROR
              - WATER_SUPPLY_ERROR
              - LOCKED_MOTOR_ERROR
              - DOOR_OPEN_ERROR
              - WATER_LEVEL_SENSOR_ERROR
              - OUT_OF_BALANCE_ERROR
              - OVERFILL_ERROR
              - POWER_FAIL_ERROR
              - UNABLE_TO_LOCK_ERROR
              - WATER_DRAIN_ERROR
            notification:
              push:
                - WASHING_IS_COMPLETE
                - ERROR_DURING_WASHING
            property:
              - detergent:
                  detergentSetting: NORMAL
                cycle:
                  cycleCount:
                    type: number
                    mode:
                      - r
                location:
                  locationName: MAIN
                operation:
                  washerOperationMode:
                    mode:
                      - w
                    type: enum
                    value:
                      w:
                        - START
                        - STOP
                        - POWER_OFF
                remoteControlEnable:
                  remoteControlEnabled:
                    mode:
                      - r
                    type: boolean
                    value:
                      r:
                        - false
                        - true
                runState:
                  currentState:
                    mode:
                      - r
                    type: enum
                    value:
                      r:
                        - POWER_OFF
                        - INITIAL
                        - ADD_DRAIN
                        - SPINNING
                        - FROZEN_PREVENT_RUNNING
                        - RESERVED
                        - PAUSE
                        - DRYING
                        - REFRESHING
                        - RINSING
                        - RINSE_HOLD
                        - FROZEN_PREVENT_INITIAL
                        - ERROR
                        - FROZEN_PREVENT_PAUSE
                        - DETERGENT_AMOUNT
                        - END
                        - DETECTING
                        - RUNNING
                        - PREWASH
                timer:
                  relativeHourToStop:
                    mode:
                      - r
                      - w
                    type: range
                    value:
                      r:
                        except: []
                        max: 19
                        min: 3
                        step: 1
                      w:
                        except: []
                        max: 19
                        min: 3
                        step: 1
                  relativeMinuteToStop:
                    mode:
                      - r
                    type: range
                    value:
                      r:
                        except: []
                        max: 59
                        min: 0
                        step: 1
                  remainHour:
                    mode:
                      - r
                    type: range
                    value:
                      r:
                        except: []
                        max: 30
                        min: 0
                        step: 1
                  remainMinute:
                    mode:
                      - r
                    type: range
                    value:
                      r:
                        except: []
                        max: 59
                        min: 0
                        step: 1
                  totalHour:
                    mode:
                      - r
                    type: range
                    value:
                      r:
                        except: []
                        max: 30
                        min: 0
                        step: 1
                  totalMinute:
                    mode:
                      - r
                    type: range
                    value:
                      r:
                        except: []
                        max: 59
                        min: 0
                        step: 1
        washtower_dryer-profile-example:
          value:
            error:
              - DRAINMOTOR_ERROR
              - COMPRESSOR_ERROR
              - DOOR_LOCK_ERROR
              - MOTOR_LOCK_ERROR
              - HIGH_TEMPERATURE_DETECTION_ERROR
              - FAN_MOTOR_ERROR
              - DOOR_SENSOR_ERROR
              - DOOR_OPEN_ERROR
              - NO_FILTER_ERROR
              - TEMPERATURE_SENSOR_ERROR
              - EMPTY_WATER_ALERT_ERROR
            notification:
              push:
                - DRYING_IS_COMPLETE
                - DRYING_FAILED
            property:
              operation:
                dryerOperationMode:
                  mode:
                    - w
                  type: enum
                  value:
                    w:
                      - START
                      - STOP
                      - POWER_OFF
              remoteControlEnable:
                remoteControlEnabled:
                  mode:
                    - r
                  type: boolean
                  value:
                    r:
                      - false
                      - true
              runState:
                currentState:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - INITIAL
                      - RESERVED
                      - ERROR
                      - END
                      - PAUSE
                      - RUNNING
                      - DETECTING
                      - POWER_OFF
                      - COOLING
                      - WRINKLE_CARE
              timer:
                relativeHourToStop:
                  mode:
                    - r
                    - w
                  type: range
                  value:
                    r:
                      max: 19
                      min: 3
                    w:
                      max: 19
                      min: 3
                relativeMinuteToStop:
                  mode:
                    - r
                  type: number
                remainHour:
                  mode:
                    - r
                  type: number
                remainMinute:
                  mode:
                    - r
                  type: number
                totalHour:
                  mode:
                    - r
                  type: number
                totalMinute:
                  mode:
                    - r
                  type: number
        washtower-profile-example:
          value:
            washer:
              error:
                - TEMPERATURE_SENSOR_ERROR
                - WATER_LEVEL_SENSOR_ERROR
                - OVERFILL_ERROR
                - LOCKED_MOTOR_ERROR
                - DOOR_OPEN_ERROR
                - UNABLE_TO_LOCK_ERROR
                - WATER_DRAIN_ERROR
                - WATER_SUPPLY_ERROR
                - POWER_FAIL_ERROR
                - OUT_OF_BALANCE_ERROR
              property:
                runState:
                  currentState:
                    type: enum
                    mode:
                      - r
                    value:
                      r:
                        - FROZEN_PREVENT_PAUSE
                        - DETECTING
                        - DETERGENT_AMOUNT
                        - SPINNING
                        - PREWASH
                        - REFRESHING
                        - STEAM_SOFTENING
                        - DRYING
                        - RINSE_HOLD
                        - RESERVED
                        - ERROR
                        - INITIAL
                        - DISPENSING
                        - FROZEN_PREVENT_INITIAL
                        - PAUSE
                        - RUNNING
                        - END
                        - POWER_OFF
                        - RINSING
                        - FROZEN_PREVENT_RUNNING
                        - ADD_DRAIN
                        - SOAKING
                operation:
                  washerOperationMode:
                    type: enum
                    mode:
                      - w
                    value:
                      w:
                        - START
                        - STOP
                        - POWER_OFF
                detergent:
                  detergentSetting: AUTO
                cycle:
                  cycleCount:
                    type: number
                    mode:
                      - r
                remoteControlEnable:
                  remoteControlEnabled:
                    type: boolean
                    mode:
                      - r
                    value:
                      r:
                        - false
                        - true
                timer:
                  remainHour:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        max: 30
                        min: 0
                        step: 1
                        except: []
                  remainMinute:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        max: 59
                        min: 0
                        step: 1
                        except: []
                  totalHour:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        max: 30
                        min: 0
                        step: 1
                        except: []
                  totalMinute:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        max: 59
                        min: 0
                        step: 1
                        except: []
                  relativeHourToStart:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 19
                        min: 1
                        step: 1
                        except: []
                      w:
                        max: 19
                        min: 1
                        step: 1
                        except: []
                  relativeMinuteToStart:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        max: 30
                        min: 0
                        step: 1
                        except: []
              notification:
                push:
                  - WASHING_IS_COMPLETE
                  - ERROR_DURING_WASHING
            dryer:
              property:
                runState:
                  currentState:
                    type: enum
                    mode:
                      - r
                    value:
                      r:
                        - DETECTING
                        - ERROR
                        - COOLING
                        - INITIAL
                        - POWER_OFF
                        - RESERVED
                        - PAUSE
                        - RUNNING
                        - WRINKLE_CARE
                        - END
                operation:
                  dryerOperationMode:
                    type: enum
                    mode:
                      - w
                    value:
                      w:
                        - START
                        - STOP
                        - POWER_OFF
                remoteControlEnable:
                  remoteControlEnabled:
                    type: boolean
                    mode:
                      - r
                    value:
                      r:
                        - false
                        - true
                timer:
                  remainHour:
                    type: number
                    mode:
                      - r
                  remainMinute:
                    type: number
                    mode:
                      - r
                  totalHour:
                    type: number
                    mode:
                      - r
                  totalMinute:
                    type: number
                    mode:
                      - r
              notification:
                push:
                  - DRYING_FAILED
                  - DRYING_IS_COMPLETE
              error:
                - HIGH_POWER_SUPPLY_ERROR
                - TEMPERATURE_SENSOR_ERROR
                - POWER_CODE_CONNECTION_ERROR
        cooktop-profile-example:
          value:
            extensionProperty:
              operation:
                operationMode:
                  mode:
                    - w
                  type: enum
                  value:
                    w:
                      - POWER_OFF
            property:
              - cookingZone:
                  currentState:
                    mode:
                      - r
                    type: enum
                    value:
                      r:
                        - INITIAL
                        - COOK
                        - PAUSE
                        - LOCK
                location:
                  locationName: LEFT_FRONT
                power:
                  powerLevel:
                    mode:
                      - r
                      - w
                    type: range
                    value:
                      r:
                        max: 11
                        min: 0
                        step: 1
                      w:
                        max: 11
                        min: 0
                        step: 1
                remoteControlEnable:
                  remoteControlEnabled:
                    mode:
                      - r
                    type: boolean
                    value:
                      r:
                        - false
                        - true
                timer:
                  remainHour:
                    mode:
                      - r
                      - w
                    type: range
                    value:
                      r:
                        max: 11
                        min: 0
                        step: 1
                      w:
                        max: 11
                        min: 0
                        step: 1
                  remainMinute:
                    mode:
                      - r
                      - w
                    type: range
                    value:
                      r:
                        max: 59
                        min: 0
                        step: 1
                      w:
                        max: 59
                        min: 0
                        step: 1
              - cookingZone:
                  currentState:
                    mode:
                      - r
                    type: enum
                    value:
                      r:
                        - INITIAL
                        - COOK
                        - PAUSE
                        - LOCK
                location:
                  locationName: RIGHT_FRONT
                power:
                  powerLevel:
                    mode:
                      - r
                      - w
                    type: range
                    value:
                      r:
                        max: 11
                        min: 0
                        step: 1
                      w:
                        max: 11
                        min: 0
                        step: 1
                remoteControlEnable:
                  remoteControlEnabled:
                    mode:
                      - r
                    type: boolean
                    value:
                      r:
                        - false
                        - true
                timer:
                  remainHour:
                    mode:
                      - r
                      - w
                    type: range
                    value:
                      r:
                        max: 11
                        min: 0
                        step: 1
                      w:
                        max: 11
                        min: 0
                        step: 1
                  remainMinute:
                    mode:
                      - r
                      - w
                    type: range
                    value:
                      r:
                        max: 59
                        min: 0
                        step: 1
                      w:
                        max: 59
                        min: 0
                        step: 1
              - cookingZone:
                  currentState:
                    mode:
                      - r
                    type: enum
                    value:
                      r:
                        - INITIAL
                        - COOK
                        - PAUSE
                        - LOCK
                location:
                  locationName: LEFT_REAR
                power:
                  powerLevel:
                    mode:
                      - r
                      - w
                    type: range
                    value:
                      r:
                        max: 11
                        min: 0
                        step: 1
                      w:
                        max: 11
                        min: 0
                        step: 1
                remoteControlEnable:
                  remoteControlEnabled:
                    mode:
                      - r
                    type: boolean
                    value:
                      r:
                        - false
                        - true
                timer:
                  remainHour:
                    mode:
                      - r
                      - w
                    type: range
                    value:
                      r:
                        max: 11
                        min: 0
                        step: 1
                      w:
                        max: 11
                        min: 0
                        step: 1
                  remainMinute:
                    mode:
                      - r
                      - w
                    type: range
                    value:
                      r:
                        max: 59
                        min: 0
                        step: 1
                      w:
                        max: 59
                        min: 0
                        step: 1
        hood-profile-example:
          value:
            property:
              ventilation:
                fanSpeed:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 5
                      min: 0
                      step: 1
                    w:
                      max: 5
                      min: 0
                      step: 1
              lamp:
                lampBrightness:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 2
                      min: 0
                      step: 1
                    w:
                      max: 2
                      min: 0
                      step: 1
              operation:
                hoodOperationMode:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - POWER_OFF
                      - POWER_ON
              timer:
                remainMinute:
                  type: range
                  mode:
                    - r
                  value:
                    r:
                      max: 59
                      min: 0
                      step: 1
                remainSecond:
                  type: range
                  mode:
                    - r
                  value:
                    r:
                      max: 59
                      min: 0
                      step: 1
        microwave_oven-profile-example:
          value:
            property:
              runState:
                currentState:
                  mode: r
                  type: enum
                  value:
                    r:
                      - INITIAL
                      - PREHEAT
                      - COOK
                      - COOK_COMPLETE
                      - PAUSE
                      - PREHEAT_COMPLETE
                      - OVEN_SETTING
              timer:
                remainMinute:
                  mode: r
                  type: range
                  value:
                    r:
                      min: 0
                      max: 59
                      step: 1
                remainSecond:
                  mode: r
                  type: range
                  value:
                    r:
                      min: 0
                      max: 59
                      step: 1
              ventilation:
                fanSpeed:
                  mode: rw
                  type: range
                  value:
                    r:
                      min: 0
                      max: 4
                      step: 1
                    w:
                      min: 0
                      max: 4
                      step: 1
              lamp:
                lampBrightness:
                  mode: rw
                  type: range
                  value:
                    r:
                      min: 0
                      max: 2
                      step: 1
                    w:
                      min: 0
                      max: 2
                      step: 1
            notification:
              push:
                - PREHEATING_IS_COMPLETE
                - COOKING_IS_COMPLETE
                - TIMER_IS_COMPLETE
        system_boiler-profile-example:
          value:
            property:
              boilerJobMode:
                currentJobMode:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - COOL
                      - AUTO
                      - HEAT
                    w:
                      - COOL
                      - AUTO
                      - HEAT
              operation:
                boilerOperationMode:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - POWER_ON
                      - POWER_OFF
                    w:
                      - POWER_ON
                      - POWER_OFF
                hotWaterMode:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - 'ON'
                      - 'OFF'
                    w:
                      - 'ON'
                      - 'OFF'
                roomTempMode:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - AIR
                      - WATER
                roomWaterMode:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - OUT_WATER
                      - IN_WATER
              temperature:
                currentTemperature:
                  mode:
                    - r
                  type: number
                targetTemperature:
                  mode:
                    - r
                  type: number
                heatTargetTemperature:
                  mode:
                    - w
                  type: number
                coolTargetTemperature:
                  mode:
                    - w
                  type: number
                heatMaxTemperature:
                  mode:
                    - r
                  type: number
                heatMinTemperature:
                  mode:
                    - r
                  type: number
                coolMaxTemperature:
                  mode:
                    - r
                  type: number
                coolMinTemperature:
                  mode:
                    - r
                  type: number
                unit:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - C
              hotWaterTemperatureInUnits:
                - currentTemperature:
                    type: number
                    mode:
                      - r
                  targetTemperature:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 80
                        min: 30
                        step: 1
                      w:
                        max: 80
                        min: 30
                        step: 1
                  maxTemperature:
                    type: number
                    mode:
                      - r
                  minTemperature:
                    type: number
                    mode:
                      - r
                  unit: C
                - currentTemperature:
                    type: number
                    mode:
                      - r
                  targetTemperature:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 176
                        min: 86
                        step: 2
                      w:
                        max: 176
                        min: 86
                        step: 2
                  maxTemperature:
                    type: number
                    mode:
                      - r
                  minTemperature:
                    type: number
                    mode:
                      - r
                  unit: F
              roomTemperatureInUnits:
                - currentTemperature:
                    type: number
                    mode:
                      - r
                  airCurrentTemperature:
                    type: number
                    mode:
                      - r
                  outWaterCurrentTemperature:
                    type: number
                    mode:
                      - r
                  inWaterCurrentTemperature:
                    type: number
                    mode:
                      - r
                  targetTemperature:
                    type: number
                    mode:
                      - r
                  airCoolTargetTemperature:
                    type: range
                    mode:
                      - w
                    value:
                      w:
                        max: 30
                        min: 18
                        step: 1
                  airHeatTargetTemperature:
                    type: range
                    mode:
                      - w
                    value:
                      w:
                        max: 30
                        min: 16
                        step: 1
                  waterCoolTargetTemperature:
                    type: range
                    mode:
                      - w
                    value:
                      w:
                        max: 24
                        min: 5
                        step: 1
                  waterHeatTargetTemperature:
                    type: range
                    mode:
                      - w
                    value:
                      w:
                        max: 57
                        min: 14
                        step: 1
                  airHeatMaxTemperature:
                    type: number
                    mode:
                      - r
                  airHeatMinTemperature:
                    type: number
                    mode:
                      - r
                  airCoolMaxTemperature:
                    type: number
                    mode:
                      - r
                  airCoolMinTemperature:
                    type: number
                    mode:
                      - r
                  waterHeatMaxTemperature:
                    type: number
                    mode:
                      - r
                  waterHeatMinTemperature:
                    type: number
                    mode:
                      - r
                  waterCoolMaxTemperature:
                    type: number
                    mode:
                      - r
                  waterCoolMinTemperature:
                    type: number
                    mode:
                      - r
                  unit: C
                - currentTemperature:
                    type: number
                    mode:
                      - r
                  airCurrentTemperature:
                    type: number
                    mode:
                      - r
                  outWaterCurrentTemperature:
                    type: number
                    mode:
                      - r
                  inWaterCurrentTemperature:
                    type: number
                    mode:
                      - r
                  targetTemperature:
                    type: number
                    mode:
                      - r
                  airCoolTargetTemperature:
                    type: range
                    mode:
                      - w
                    value:
                      w:
                        max: 86
                        min: 64
                        step: 2
                  airHeatTargetTemperature:
                    type: range
                    mode:
                      - w
                    value:
                      w:
                        max: 86
                        min: 60
                        step: 2
                  waterCoolTargetTemperature:
                    type: range
                    mode:
                      - w
                    value:
                      w:
                        max: 76
                        min: 40
                        step: 2
                  waterHeatTargetTemperature:
                    type: range
                    mode:
                      - w
                    value:
                      w:
                        max: 134
                        min: 58
                        step: 2
                  airHeatMaxTemperature:
                    type: number
                    mode:
                      - r
                  airHeatMinTemperature:
                    type: number
                    mode:
                      - r
                  airCoolMaxTemperature:
                    type: number
                    mode:
                      - r
                  airCoolMinTemperature:
                    type: number
                    mode:
                      - r
                  waterHeatMaxTemperature:
                    type: number
                    mode:
                      - r
                  waterHeatMinTemperature:
                    type: number
                    mode:
                      - r
                  waterCoolMaxTemperature:
                    type: number
                    mode:
                      - r
                  waterCoolMinTemperature:
                    type: number
                    mode:
                      - r
                  unit: F
        air_purifier_fan-profile-example:
          value:
            notification:
              push:
                - TIME_TO_CHANGE_FILTER
            property:
              airFanJobMode:
                currentJobMode:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - SPOT_CLEAN
                      - SPACE_CLEAN
                      - DIRECT_CLEAN
                      - UP_FEATURE
                    w:
                      - SPOT_CLEAN
                      - SPACE_CLEAN
                      - DIRECT_CLEAN
              operation:
                airFanOperationMode:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - POWER_ON
                      - POWER_OFF
                    w:
                      - POWER_ON
                      - POWER_OFF
              airFlow:
                warmMode:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - WARM_ON
                      - WARM_OFF
                    w:
                      - WARM_ON
                      - WARM_OFF
                windTemperature:
                  mode:
                    - r
                    - w
                  type: range
                  value:
                    r:
                      max: 30
                      min: 16
                      step: 1
                    w:
                      max: 30
                      min: 16
                      step: 1
                windStrength:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - AUTO
                      - POWER
                      - WIND_1
                      - WIND_2
                      - WIND_3
                      - WIND_4
                      - WIND_5
                      - WIND_6
                      - WIND_7
                      - WIND_8
                      - WIND_9
                      - WIND_10
                    w:
                      - AUTO
                      - POWER
                      - WIND_1
                      - WIND_2
                      - WIND_3
                      - WIND_4
                      - WIND_5
                      - WIND_6
                      - WIND_7
                      - WIND_8
                      - WIND_9
                      - WIND_10
                windAngle:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - 'OFF'
                      - ANGLE_45
                      - ANGLE_60
                      - ANGLE_90
                      - ANGLE_140
                    w:
                      - 'OFF'
                      - ANGLE_45
                      - ANGLE_60
                      - ANGLE_90
                      - ANGLE_140
              timer:
                absoluteHourToStart:
                  mode:
                    - r
                    - w
                  type: number
                absoluteHourToStop:
                  mode:
                    - r
                    - w
                  type: number
                absoluteMinuteToStart:
                  mode:
                    - r
                    - w
                  type: number
                absoluteMinuteToStop:
                  mode:
                    - r
                    - w
                  type: number
                absoluteStartTimer:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - SET
                      - UNSET
                    w:
                      - UNSET
                absoluteStopTimer:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - SET
                      - UNSET
                    w:
                      - UNSET
              sleepTimer:
                relativeHourToStop:
                  mode:
                    - r
                    - w
                  type: number
                relativeMinuteToStop:
                  mode:
                    - r
                  type: number
                relativeStopTimer:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - SET
                      - UNSET
                    w:
                      - UNSET
              airQualitySensor:
                totalPollution:
                  mode:
                    - r
                  type: number
                totalPollutionLevel:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - INVALID
                      - GOOD
                      - NORMAL
                      - BAD
                      - VERY_BAD
                PM1:
                  mode:
                    - r
                  type: number
                PM2:
                  mode:
                    - r
                  type: number
                PM10:
                  mode:
                    - r
                  type: number
                odor:
                  mode:
                    - r
                  type: number
                odorLevel:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - INVALID
                      - WEAK
                      - NORMAL
                      - STRONG
                      - VERY_STRONG
                temperature:
                  mode:
                    - r
                  type: number
                humidity:
                  mode:
                    - r
                  type: number
                monitoringEnabled:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - ON_WORKING
                      - ALWAYS
              display:
                light:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - 'OFF'
                      - LEVEL_1
                      - LEVEL_2
                      - LEVEL_3
                    w:
                      - 'OFF'
                      - LEVEL_1
                      - LEVEL_2
                      - LEVEL_3
              misc:
                uvNano:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - 'ON'
                      - 'OFF'
                    w:
                      - 'ON'
                      - 'OFF'
        stick_cleaner-profile-example:
          value:
            property:
              runState:
                currentState:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - CHARGING
                      - CHARGING_COMPLETE
                      - WORKING
                      - STANDBY
              stickCleanerJobMode:
                currentJobMode:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - 'OFF'
                      - AUTO
                      - HIGH
                      - NORMAL
                      - TURBO
                      - MOP
              battery:
                level:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - WARNING
                      - HIGH
                      - LOW
                      - MID
            notification:
              push:
                - TIME_TO_CLEAN_FILTER
                - CHARGING_IS_COMPLETE
        water_heater-profile-example:
          value:
            property:
              waterHeaterJobMode:
                currentJobMode:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - HEAT_PUMP
                      - AUTO
                      - VACATION
                      - TURBO
                    w:
                      - HEAT_PUMP
                      - AUTO
                      - VACATION
                      - TURBO
              operation:
                waterHeaterOperationMode:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - POWER_ON
                      - POWER_OFF
              temperature:
                currentTemperature:
                  type: number
                  mode:
                    - r
                targetTemperature:
                  type: number
                  mode:
                    - r
                    - w
        main_washcombo-profile-example:
          value:
            error:
              - TURBIDITY_SENSOR_ERROR
              - DOOR_OPEN_ERROR
              - WATER_DRAIN_ERROR
              - FILTER_CLOGGING_ERROR
              - FAN_MOTOR_LOCK_ERROR
              - DISPENSING_ERROR
              - LOCKED_MOTOR_ERROR
              - WATER_LEVEL_SENSOR_ERROR
              - OUT_OF_BALANCE_ERROR
              - IR_SENSOR_ERROR
              - DOOR_LOCK_ERROR
              - FROZEN_ERROR
              - NO_FILTER_ERROR
              - VIBRATION_SENSOR_ERROR
              - STEAM_HEAT_ERROR
              - WATER_SUPPLY_ERROR
              - OVERFILL_ERROR
              - TEMPERATURE_SENSOR_ERROR
              - COMPRESSOR_ERROR
              - HIGH_TEMPERATURE_DETECTION_ERROR
            property:
              - runState:
                  currentState:
                    type: enum
                    mode:
                      - r
                    value:
                      r:
                        - POWER_OFF
                        - RINSING
                        - PREWASH
                        - DISPENSING
                        - RESERVED
                        - FROZEN_PREVENT_RUNNING
                        - COOLING
                        - DETECTING
                        - INITIAL
                        - END
                        - ERROR
                        - STEAM_SOFTENING
                        - PAUSE
                        - FROZEN_PREVENT_PAUSE
                        - DRYING
                        - FROZEN_PREVENT_INITIAL
                        - ADD_DRAIN
                        - SOAKING
                        - RINSE_HOLD
                        - SPINNING
                        - DETERGENT_AMOUNT
                        - RUNNING
                        - REFRESHING
                operation:
                  washerOperationMode:
                    type: enum
                    mode:
                      - w
                    value:
                      w:
                        - START
                        - STOP
                        - POWER_OFF
                detergent:
                  detergentSetting: AUTO
                cycle:
                  cycleCount:
                    type: number
                    mode:
                      - r
                remoteControlEnable:
                  remoteControlEnabled:
                    type: boolean
                    mode:
                      - r
                    value:
                      r:
                        - false
                        - true
                timer:
                  remainHour:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        max: 30
                        min: 0
                        step: 1
                        except: []
                  remainMinute:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        max: 59
                        min: 0
                        step: 1
                        except: []
                  totalHour:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        max: 30
                        min: 0
                        step: 1
                        except: []
                  totalMinute:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        max: 59
                        min: 0
                        step: 1
                        except: []
                  relativeHourToStop:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 19
                        min: 3
                        step: 1
                        except: []
                      w:
                        max: 19
                        min: 3
                        step: 1
                        except: []
                  relativeMinuteToStop:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        max: 30
                        min: 0
                        step: 1
                        except: []
                location:
                  locationName: MAIN
            notification:
              push:
                - WASHING_IS_COMPLETE
                - DRYING_IS_COMPLETE
                - ERROR_DURING_WASHING
                - DRYING_FAILED
        mini_washcombo-profile-example:
          value:
            error:
              - OUT_OF_BALANCE_ERROR
              - STACK_ERROR
              - DOOR_OPEN_ERROR
              - LOCKED_MOTOR_ERROR
              - DOOR_SENSOR_ERROR
              - WATER_LEVEL_SENSOR_ERROR
              - WATER_SUPPLY_ERROR
              - OVERFILL_ERROR
              - DOOR_LOCK_ERROR
              - WATER_DRAIN_ERROR
              - INNER_LID_OPEN_ERROR
              - TEMPERATURE_SENSOR_ERROR
              - FROZEN_ERROR
              - CLUTCH_ERROR
            property:
              - runState:
                  currentState:
                    type: enum
                    mode:
                      - r
                    value:
                      r:
                        - END
                        - POWER_OFF
                        - RINSING
                        - SOAKING
                        - ERROR
                        - SPINNING
                        - RESERVED
                        - PAUSE
                        - DETECTING
                        - FIRMWARE
                        - INITIAL
                        - RUNNING
                operation:
                  washerOperationMode:
                    type: enum
                    mode:
                      - w
                    value:
                      w:
                        - START
                        - STOP
                        - POWER_OFF
                detergent:
                  detergentSetting: NORMAL
                cycle:
                  cycleCount:
                    type: number
                    mode:
                      - r
                remoteControlEnable:
                  remoteControlEnabled:
                    type: boolean
                    mode:
                      - r
                    value:
                      r:
                        - false
                        - true
                timer:
                  remainHour:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        max: 30
                        min: 0
                        step: 1
                        except: []
                  remainMinute:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        max: 59
                        min: 0
                        step: 1
                        except: []
                  totalHour:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        max: 30
                        min: 0
                        step: 1
                        except: []
                  totalMinute:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        max: 59
                        min: 0
                        step: 1
                        except: []
                  relativeHourToStop:
                    type: range
                    mode:
                      - r
                      - w
                    value:
                      r:
                        max: 19
                        min: 3
                        step: 1
                        except: []
                      w:
                        max: 19
                        min: 3
                        step: 1
                        except: []
                  relativeMinuteToStop:
                    type: range
                    mode:
                      - r
                    value:
                      r:
                        max: 30
                        min: 0
                        step: 1
                        except: []
                location:
                  locationName: MINI
            notification:
              push:
                - WASHING_IS_COMPLETE
                - ERROR_DURING_WASHING
        humidifier-profile-example:
          title: Humidifier
          value:
            notification:
              push:
                - TIME_TO_CHANGE_FILTER
                - LACK_OF_WATER
            property:
              humidifierJobMode:
                currentJobMode:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - HUMIDIFY
                      - HUMIDIFY_AND_AIR_CLEAN
                      - AIR_CLEAN
                    w:
                      - HUMIDIFY
                      - HUMIDIFY_AND_AIR_CLEAN
                      - AIR_CLEAN
              operation:
                humidifierOperationMode:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - POWER_ON
                      - POWER_OFF
                    w:
                      - POWER_ON
                      - POWER_OFF
                autoMode:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - AUTO_ON
                      - AUTO_OFF
                    w:
                      - AUTO_ON
                      - AUTO_OFF
                sleepMode:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - SLEEP_ON
                      - SLEEP_OFF
                    w:
                      - SLEEP_ON
                      - SLEEP_OFF
                hygieneDryMode:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - FAST
                      - SILENT
                      - 'OFF'
                      - NORMAL
                    w:
                      - FAST
                      - SILENT
                      - 'OFF'
                      - NORMAL
              timer:
                absoluteHourToStart:
                  mode:
                    - r
                    - w
                  type: number
                absoluteHourToStop:
                  mode:
                    - r
                    - w
                  type: number
                absoluteMinuteToStart:
                  mode:
                    - r
                    - w
                  type: number
                absoluteMinuteToStop:
                  mode:
                    - r
                    - w
                  type: number
                absoluteStartTimer:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - SET
                      - UNSET
                    w:
                      - UNSET
                absoluteStopTimer:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - SET
                      - UNSET
                    w:
                      - UNSET
              sleepTimer:
                relativeHourToStop:
                  mode:
                    - r
                    - w
                  type: number
                relativeMinuteToStop:
                  mode:
                    - r
                  type: number
                relativeStopTimer:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - SET
                      - UNSET
                    w:
                      - UNSET
              humidity:
                targetHumidity:
                  mode:
                    - r
                    - w
                  type: range
                  value:
                    r:
                      max: 70
                      min: 30
                      step: 5
                    w:
                      max: 70
                      min: 30
                      step: 5
                warmMode:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - WARM_ON
                      - WARM_OFF
                    w:
                      - WARM_ON
                      - WARM_OFF
              airFlow:
                windStrength:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - POWER
                      - HIGH
                      - MID
                      - LOW
                      - AUTO
                    w:
                      - POWER
                      - HIGH
                      - MID
                      - LOW
              airQualitySensor:
                totalPollution:
                  mode:
                    - r
                  type: number
                totalPollutionLevel:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - INVALID
                      - GOOD
                      - NORMAL
                      - BAD
                      - VERY_BAD
                PM1:
                  mode:
                    - r
                  type: number
                PM2:
                  mode:
                    - r
                  type: number
                PM10:
                  mode:
                    - r
                  type: number
                humidity:
                  mode:
                    - r
                  type: number
                temperature:
                  mode:
                    - r
                  type: number
                monitoringEnabled:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - ON_WORKING
                      - ALWAYS
              display:
                light:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - 'OFF'
                      - LEVEL_1
                      - LEVEL_2
                      - LEVEL_3
                    w:
                      - 'OFF'
                      - LEVEL_1
                      - LEVEL_2
                      - LEVEL_3
              moodLamp:
                moodLampState:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - 'ON'
                      - 'OFF'
                    w:
                      - 'ON'
                      - 'OFF'
        odu-profile-example:
          value:
            operation:
              operationMode:
                type: enum
                mode:
                  - r
                value:
                  r:
                    - STOP
                    - COOL
                    - HEAT
            temperature:
              outdoorTemperature:
                type: number
                mode:
                  - r
            info:
              modelName:
                type: string
                mode:
                  - r
              capacity:
                type: number
                mode:
                  - r
        idu-profile-example:
          value:
            operation:
              airConOperationMode:
                type: enum
                mode:
                  - r
                  - w
                value:
                  r:
                    - POWER_ON
                    - POWER_OFF
                  w:
                    - POWER_ON
                    - POWER_OFF
              heaterOperationMode:
                type: enum
                mode:
                  - r
                  - w
                value:
                  r:
                    - POWER_ON
                    - POWER_OFF
                  w:
                    - POWER_ON
                    - POWER_OFF
            jobMode:
              airConJobMode:
                type: enum
                mode:
                  - r
                  - w
                value:
                  r:
                    - AUTO
                    - COOL
                    - AIR_DRY
                    - FAN
                    - HEAT
                  w:
                    - AUTO
                    - COOL
                    - AIR_DRY
                    - FAN
                    - HEAT
              heaterJobMode:
                type: boolean
                mode:
                  - r
                  - w
                value:
                  r:
                    - true
                    - false
                  w:
                    - true
                    - false
            temperature:
              currentTemperature:
                type: number
                mode:
                  - r
              targetTemperature:
                type: range
                mode:
                  - r
                  - w
                value:
                  r:
                    max: 30
                    min: 16
                    step: 1
                  w:
                    max: 30
                    min: 16
                    step: 1
              targetTemperatureLowLimit:
                type: range
                mode:
                  - r
                  - w
                value:
                  r:
                    max: 30
                    min: 16
                    step: 1
                  w:
                    max: 30
                    min: 16
                    step: 1
              targetTemperatureUpperLimit:
                type: range
                mode:
                  - r
                  - w
                value:
                  r:
                    max: 30
                    min: 16
                    step: 1
                  w:
                    max: 30
                    min: 16
                    step: 1
              outdoorTemperature1:
                type: range
                mode:
                  - r
                  - w
                value:
                  r:
                    max: 0
                    min: -23
                    step: 1
                  w:
                    max: 0
                    min: -23
                    step: 1
              outdoorTemperature2:
                type: range
                mode:
                  - r
                  - w
                value:
                  r:
                    max: 51
                    min: -23
                    step: 1
                  w:
                    max: 51
                    min: -23
                    step: 1
            powerSave:
              powerSaveEnabled:
                type: boolean
                mode:
                  - r
                value:
                  r:
                    - true
                    - false
              powerSaveStep:
                type: enum
                mode:
                  - r
              value:
                r:
                  - POWERSAVE_LEVEL_1
                  - POWERSAVE_LEVEL_2
                  - POWERSAVE_LEVEL_3
            airFlow:
              windStrength:
                type: enum
                mode:
                  - r
                  - w
                value:
                  r:
                    - AUTO
                    - HIGH
                    - MED
                    - LOW
                  w:
                    - AUTO
                    - HIGH
                    - MED
                    - LOW
              windDirectionSetting:
                type: boolean
                mode:
                  - r
                  - w
                value:
                  r:
                    - true
                    - false
                  w:
                    - true
                    - false
            outdoor:
              outdoorHeaterSetting:
                type: boolean
                mode:
                  - r
                  - w
                value:
                  r:
                    - true
                    - false
                  w:
                    - true
                    - false
              outdoorHeatPumpSetting:
                type: boolean
                mode:
                  - r
                  - w
                value:
                  r:
                    - true
                    - false
                  w:
                    - true
                    - false
            lock:
              fullLock:
                type: boolean
                mode:
                  - r
                  - w
                value:
                  r:
                    - true
                    - false
                  w:
                    - true
                    - false
              modeLock:
                type: boolean
                mode:
                  - r
                  - w
                value:
                  r:
                    - true
                    - false
                  w:
                    - true
                    - false
              fanLock:
                type: boolean
                mode:
                  - r
                  - w
                value:
                  r:
                    - true
                    - false
                  w:
                    - true
                    - false
              temperatureLock:
                type: boolean
                mode:
                  - r
                  - w
                value:
                  r:
                    - true
                    - false
                  w:
                    - true
                    - false
            alarm:
              filterReplacementAlarm:
                type: boolean
                mode:
                  - r
                value:
                  r:
                    - true
                    - false
            address:
              targetAddress:
                type: string
                mode:
                  - w
                value:
                  w:
                    - 00~FF
            execution:
              executionDevice:
                type: boolean
                mode:
                  - w
                value:
                  w:
                    - true
                    - false
        signage-profile-example:
          value:
            power:
              power:
                type: boolean
                mode:
                  - r
                value:
                  r:
                    - true
                    - false
              screen:
                type: enum
                mode:
                  - r
                  - w
                value:
                  r:
                    - SCREEN_ON
                    - SCREEN_OFF
                  w:
                    - SCREEN_ON
                    - SCREEN_OFF
              noSignalPowerOff:
                type: boolean
                mode:
                  - r
                value:
                  r:
                    - true
                    - false
              noIrPowerOff:
                type: boolean
                mode:
                  - r
                value:
                  r:
                    - true
                    - false
              pmMode:
                type: enum
                mode:
                  - r
                value:
                  r:
                    - '00'
                    - '01'
                    - '02'
                    - '03'
                    - '04'
                    - '05'
              powerOnStatus:
                type: enum
                mode:
                  - r
                value:
                  r:
                    - '00'
                    - '01'
                    - '02'
              powerOnDelay:
                type: number
                mode:
                  - r
                value:
                  r:
                    max: 250
                    min: 0
                    step: 1
              energySavingMode:
                type: enum
                mode:
                  - r
                value:
                  r:
                    - '00'
                    - '01'
                    - '02'
                    - '03'
                    - '04'
              wol:
                type: boolean
                mode:
                  - r
                value:
                  r:
                    - true
                    - false
            display:
              input:
                type: enum
                mode:
                  - r
                  - w
                value:
                  r:
                    - '20'
                    - '40'
                    - '60'
                    - '70'
                    - '80'
                    - '90'
                    - a9
                    - '91'
                    - a1
                    - '92'
                    - a2
                    - '95'
                    - a5
                    - '96'
                    - a6
                    - '97'
                    - a7
                    - '98'
                    - a8
                    - '99'
                    - a9
                    - c0
                    - d0
                    - c1
                    - d1
                    - c2
                    - d2
                    - c3
                    - d3
                    - e0
                    - e1
                    - e2
                    - e3
                    - e8
                    - f0
                    - f1
                    - f2
                    - f3
                    - f4
                    - f5
                    - f6
                    - f7
                    - f8
                    - f9
                  w:
                    - '20'
                    - '40'
                    - '60'
                    - '70'
                    - '80'
                    - '90'
                    - a9
                    - '91'
                    - a1
                    - '92'
                    - a2
                    - '95'
                    - a5
                    - '96'
                    - a6
                    - '97'
                    - a7
                    - '98'
                    - a8
                    - '99'
                    - a9
                    - c0
                    - d0
                    - c1
                    - d1
                    - c2
                    - d2
                    - c3
                    - d3
                    - e0
                    - e1
                    - e2
                    - e3
                    - e8
                    - f0
                    - f1
                    - f2
                    - f3
                    - f4
                    - f5
                    - f6
                    - f7
                    - f8
                    - f9
              language:
                type: enum
                mode:
                  - r
                value:
                  r:
                    - '00'
                    - '01'
                    - '02'
                    - '03'
                    - '04'
                    - '05'
                    - '06'
                    - '07'
                    - '08'
                    - '09'
                    - 0a
                    - 0b
                    - 0c
                    - 0d
                    - 0e
                    - 0f
                    - '10'
                    - '11'
                    - '12'
                    - '13'
                    - '14'
                    - '15'
              ism:
                type: enum
                mode:
                  - r
                value:
                  r:
                    - '02'
                    - '04'
                    - '08'
                    - '90'
                    - '91'
              pictureMode:
                type: enum
                mode:
                  - r
                  - w
                value:
                  r:
                    - '00'
                    - '01'
                    - '02'
                    - '03'
                    - '04'
                    - '05'
                    - '08'
                    - '11'
                    - '12'
                  w:
                    - '00'
                    - '01'
                    - '02'
                    - '03'
                    - '04'
                    - '05'
                    - '08'
                    - '11'
                    - '12'
              backlight:
                type: number
                mode:
                  - r
                value:
                  r:
                    max: 100
                    min: 0
                    step: 1
              brightness:
                type: number
                mode:
                  - r
                value:
                  r:
                    max: 100
                    min: 0
                    step: 1
              tint:
                type: number
                mode:
                  - r
                value:
                  r:
                    max: 100
                    min: 0
                    step: 1
              contrast:
                type: number
                mode:
                  - r
                value:
                  r:
                    max: 100
                    min: 0
                    step: 1
              sharpness:
                type: number
                mode:
                  - r
                value:
                  r:
                    max: 50
                    min: 0
                    step: 1
              color:
                type: number
                mode:
                  - r
                value:
                  r:
                    max: 100
                    min: 0
                    step: 1
            audio:
              volume:
                type: number
                mode:
                  - r
                  - w
                value:
                  r:
                    max: 100
                    min: 0
                    step: 1
                  w:
                    max: 100
                    min: 0
                    step: 1
              volumeMute:
                type: boolean
                mode:
                  - r
                value:
                  r:
                    - true
                    - false
              soundMode:
                type: enum
                mode:
                  - r
                value:
                  r:
                    - '01'
                    - '02'
                    - '03'
                    - '04'
                    - '05'
                    - '08'
                    - '09'
              soundBalance:
                type: number
                mode:
                  - r
                value:
                  r:
                    max: 100
                    min: 0
                    step: 1
            temperature:
              main:
                type: number
                mode:
                  - r
            info:
              osType:
                type: enum
                mode:
                  - r
                value:
                  r:
                    - WEBOS
                    - WINDOWS
                    - ANDROID
                    - NONE
        motion_sensor-profile-example:
          value:
            property:
              battery:
                percent:
                  mode:
                    - r
                  type: range
                  value:
                    r:
                      min: 0
                      max: 100
            notification:
              push:
                - BATTERY_IS_LOW
                - MOTION_IS_DETECTED
        temperature_humidity_sensor-profile-example:
          value:
            property:
              battery:
                percent:
                  mode:
                    - r
                  type: range
                  value:
                    r:
                      min: 0
                      max: 100
              temperature:
                currentTemperature:
                  mode:
                    - r
                  type: number
              humidity:
                currentHumidity:
                  mode:
                    - r
                  type: range
                  value:
                    r:
                      min: 0
                      max: 100
            notification:
              push:
                - BATTERY_IS_LOW
        door_sensor-profile-example:
          value:
            property:
              battery:
                percent:
                  mode:
                    - r
                  type: range
                  value:
                    r:
                      min: 0
                      max: 100
                      step: 1
              doorState:
                currentState:
                  mode:
                    - r
                  type: enum
                  value:
                    r:
                      - OPEN
                      - CLOSE
            notification:
              push:
                - BATTERY_IS_LOW
                - DOOR_WINDOW_IS_OPENED
                - DOOR_WINDOW_IS_CLOSED
        button-profile-example:
          value:
            property:
              battery:
                percent:
                  type: range
                  mode:
                    - r
                  value:
                    r:
                      max: 100
                      min: 0
                      step: 1
            notification:
              push:
                - BATTERY_IS_LOW
        light_switch-profile-example:
          value:
            property:
              switchState:
                - switchName: SWITCH_1
                  currentSwitch:
                    type: enum
                    mode:
                      - r
                      - w
                    value:
                      r:
                        - 'ON'
                        - 'OFF'
                      w:
                        - 'ON'
                        - 'OFF'
                - switchName: SWITCH_2
                  currentSwitch:
                    type: enum
                    mode:
                      - r
                      - w
                    value:
                      r:
                        - 'ON'
                        - 'OFF'
                      w:
                        - 'ON'
                        - 'OFF'
                - switchName: SWITCH_3
                  currentSwitch:
                    type: enum
                    mode:
                      - r
                      - w
                    value:
                      r:
                        - 'ON'
                        - 'OFF'
                      w:
                        - 'ON'
                        - 'OFF'
        door_lock-profile-example:
          value:
            property:
              battery:
                percent:
                  mode:
                    - r
                  type: range
                  value:
                    r:
                      min: 0
                      max: 100
              doorState:
                currentState:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - OPEN
                      - CLOSE
                    w:
                      - OPEN
        push_pull_door_lock-profile-example:
          value:
            property:
              battery:
                percent:
                  mode:
                    - r
                  type: range
                  value:
                    r:
                      min: 0
                      max: 100
              doorState:
                currentState:
                  mode:
                    - r
                    - w
                  type: enum
                  value:
                    r:
                      - OPEN
                      - CLOSE
                    w:
                      - OPEN
        plug-profile-example:
          value:
            property:
              runState:
                currentState:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - POWER_ON
                      - POWER_OFF
                    w:
                      - POWER_ON
                      - POWER_OFF
              electricity:
                current:
                  type: number
                  mode:
                    - r
                currentUnit:
                  type: string
                  mode:
                    - r
                voltage:
                  type: number
                  mode:
                    - r
                voltageUnit:
                  type: string
                  mode:
                    - r
                power:
                  type: number
                  mode:
                    - r
                powerUnit:
                  type: string
                  mode:
                    - r
            notification:
              push:
                - BATTERY_IS_LOW
                - POWER_IS_OVERLOADED
        plug_mini-profile-example:
          value:
            property:
              runState:
                currentState:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - POWER_ON
                      - POWER_OFF
                    w:
                      - POWER_ON
                      - POWER_OFF
              electricity:
                current:
                  type: number
                  mode:
                    - r
                currentUnit:
                  type: string
                  mode:
                    - r
                voltage:
                  type: number
                  mode:
                    - r
                voltageUnit:
                  type: string
                  mode:
                    - r
                power:
                  type: number
                  mode:
                    - r
                powerUnit:
                  type: string
                  mode:
                    - r
              switchState:
                currentSwitch:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - 'ON'
                      - 'OFF'
                      - LAST
                    w:
                      - 'ON'
                      - 'OFF'
                      - LAST
                indicateLight:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - ON_RELAY
                      - ON_POS
                      - 'OFF'
                    w:
                      - ON_RELAY
                      - ON_POS
                      - 'OFF'
                kidLock:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - LOCK
                      - UNLOCK
                    w:
                      - LOCK
                      - UNLOCK
            notification:
              push:
                - BATTERY_IS_LOW
                - POWER_IS_OVERLOADED
        bulb_white-profile-example:
          value:
            property:
              runState:
                currentState:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - POWER_ON
                      - POWER_OFF
                    w:
                      - POWER_ON
                      - POWER_OFF
              whiteLight:
                brightness:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 1
                      step: 1
                    w:
                      max: 100
                      min: 1
                      step: 1
                colorTemperature:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 6500
                      min: 3000
                      step: 1
                    w:
                      max: 6500
                      min: 3000
                      step: 1
        bulb_color-profile-example:
          value:
            property:
              runState:
                currentState:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - POWER_ON
                      - POWER_OFF
                    w:
                      - POWER_ON
                      - POWER_OFF
              mode:
                lightMode:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - WHITE
                      - COLOR
                      - SCENE
                    w:
                      - WHITE
                      - COLOR
              whiteLight:
                brightness:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 1
                      step: 1
                    w:
                      max: 100
                      min: 1
                      step: 1
              colorLight:
                hue:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 360
                      min: 0
                      step: 1
                    w:
                      max: 360
                      min: 0
                      step: 1
                saturation:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 0
                      step: 1
                    w:
                      max: 100
                      min: 0
                      step: 1
                brightness:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 1
                      step: 1
                    w:
                      max: 100
                      min: 1
                      step: 1
        line_led-profile-example:
          value:
            property:
              runState:
                currentState:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - POWER_ON
                      - POWER_OFF
                    w:
                      - POWER_ON
                      - POWER_OFF
              mode:
                lightMode:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - WHITE
                      - COLOR
                      - SCENE
                    w:
                      - WHITE
                      - COLOR
              whiteLight:
                brightness:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 1
                      step: 1
                    w:
                      max: 100
                      min: 1
                      step: 1
              colorLight:
                hue:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 360
                      min: 0
                      step: 1
                    w:
                      max: 360
                      min: 0
                      step: 1
                saturation:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 0
                      step: 1
                    w:
                      max: 100
                      min: 0
                      step: 1
                brightness:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 1
                      step: 1
                    w:
                      max: 100
                      min: 1
                      step: 1
        curtain_ctrl-profile-example:
          value:
            property:
              openCloseState:
                currentState:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - OPEN
                      - CLOSE
                    w:
                      - OPEN
                      - CLOSE
                      - STOP
                level:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 0
                      step: 1
                    w:
                      max: 100
                      min: 0
                      step: 1
              calibration:
                railCalibration:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - ACTIVATE
                      - DEACTIVATE
                    w:
                      - ACTIVATE
                      - DEACTIVATE
              motor:
                motorDirection:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - FORWARD
                      - BACKWARD
                    w:
                      - FORWARD
                      - BACKWARD
        blind_motor-profile-example:
          value:
            property:
              openCloseState:
                currentState:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - OPEN
                      - CLOSE
                      - STOP
                    w:
                      - OPEN
                      - CLOSE
                      - STOP
                level:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 0
                      step: 1
                    w:
                      max: 100
                      min: 0
                      step: 1
              operation:
                operationMode:
                  type: enum
                  mode:
                    - w
                  value:
                    w:
                      - OPEN
                      - CLOSE
                      - STOP
              motor:
                motorDirection:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - FORWARD
                      - BACKWARD
                    w:
                      - FORWARD
                      - BACKWARD
        switch_strip-profile-example:
          value:
            property:
              runState:
                currentState:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - POWER_ON
                      - POWER_OFF
                    w:
                      - POWER_ON
                      - POWER_OFF
              switchState:
                - switchName: SWITCH_1
                  currentSwitch:
                    type: enum
                    mode:
                      - r
                      - w
                    value:
                      r:
                        - 'ON'
                        - 'OFF'
                      w:
                        - 'ON'
                        - 'OFF'
                - switchName: SWITCH_2
                  currentSwitch:
                    type: enum
                    mode:
                      - r
                      - w
                    value:
                      r:
                        - 'ON'
                        - 'OFF'
                      w:
                        - 'ON'
                        - 'OFF'
                - switchName: SWITCH_3
                  currentSwitch:
                    type: enum
                    mode:
                      - r
                      - w
                    value:
                      r:
                        - 'ON'
                        - 'OFF'
                      w:
                        - 'ON'
                        - 'OFF'
                - switchName: SWITCH_USB
                  currentSwitch:
                    type: enum
                    mode:
                      - r
                      - w
                    value:
                      r:
                        - 'ON'
                        - 'OFF'
                      w:
                        - 'ON'
                        - 'OFF'
        starlight-profile-example:
          value:
            property:
              runState:
                currentState:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - POWER_ON
                      - POWER_OFF
                    w:
                      - POWER_ON
                      - POWER_OFF
              switchState:
                switchLaser:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - 'ON'
                      - 'OFF'
                    w:
                      - 'ON'
                      - 'OFF'
                switchColor:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - 'ON'
                      - 'OFF'
                    w:
                      - 'ON'
                      - 'OFF'
              mode:
                lightMode:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - WHITE
                      - COLOR
                      - SCENE
                sceneMode:
                  type: boolean
                  mode:
                    - r
                  value:
                    r:
                      - true
                      - false
              laserLight:
                brightness:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 1
                      step: 1
                    w:
                      max: 100
                      min: 1
                      step: 1
                motorSpeed:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 1
                      step: 1
                    w:
                      max: 100
                      min: 1
                      step: 1
              colorLight:
                hue:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 360
                      min: 0
                      step: 1
                    w:
                      max: 360
                      min: 0
                      step: 1
                saturation:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 0
                      step: 1
                    w:
                      max: 100
                      min: 0
                      step: 1
                brightness:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 1
                      step: 1
                    w:
                      max: 100
                      min: 1
                      step: 1
        doorbell-profile-example:
          value:
            property:
              chime:
                volume:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 0
                      step: 1
                    w:
                      max: 100
                      min: 0
                      step: 1
            notification:
              push:
                - BATTERY_IS_LOW
                - MOTION_IS_DETECTED
                - DOORBELL_RING
        pet_peeder-profile-example:
          value:
            property:
              feed:
                amount:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 200
                      min: 10
                      step: 10
                    w:
                      max: 200
                      min: 10
                      step: 10
            notification:
              push:
                - MOTION_IS_DETECTED
                - FEEDING_IS_COMPLETE
        home_camera-profile-example:
          value:
            property:
              mode:
                privateMode:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - 'ON'
                      - 'OFF'
                    w:
                      - 'ON'
                      - 'OFF'
            notification:
              push:
                - MOTION_IS_DETECTED
                - SOUND_IS_DETECTED
        sync_box-profile-example:
          value:
            property:
              runState:
                currentState:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - POWER_ON
                      - POWER_OFF
                    w:
                      - POWER_ON
                      - POWER_OFF
              mode:
                lightMode:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - COLOR
                      - MUSIC
                      - SCENE
                      - VIDEO
                    w:
                      - COLOR
                      - MUSIC
                musicMode:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - ROCK
                      - JAZZ
                      - CLASSIC
                      - NONE
                    w:
                      - ROCK
                      - JAZZ
                      - CLASSIC
                      - NONE
              colorLight:
                hue:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 360
                      min: 0
                      step: 1
                    w:
                      max: 360
                      min: 0
                      step: 1
                saturation:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 0
                      step: 1
                    w:
                      max: 100
                      min: 0
                      step: 1
                brightness:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 1
                      step: 1
                    w:
                      max: 100
                      min: 1
                      step: 1
              video:
                videoScene:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - MOVIE
                      - GAME
                    w:
                      - MOVIE
                      - GAME
                intensity:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - LOW
                      - MIDDLE
                      - HIGH
                      - MUSIC
                    w:
                      - LOW
                      - MIDDLE
                      - HIGH
                      - MUSIC
                colorMode:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - MULTIPLE
                      - SINGLE
                      - STOP
                    w:
                      - MULTIPLE
                      - SINGLE
                      - STOP
              input:
                hdmiSwitch:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 3
                      min: 1
                      step: 1
                    w:
                      max: 3
                      min: 1
                      step: 1
              layout:
                lightPosition:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - LOW_LEFT
                      - LOW_RIGHT
                    w:
                      - LOW_LEFT
                      - LOW_RIGHT
                lightDirection:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - CLOCKWISE
                      - COUNTERCLOCKWISE
                    w:
                      - CLOCKWISE
                      - COUNTERCLOCKWISE
        sync_box_sub-profile-example:
          value:
            property:
              runState:
                currentState:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - POWER_ON
                      - POWER_OFF
                    w:
                      - POWER_ON
                      - POWER_OFF
              mode:
                lightMode:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - WHITE
                      - COLOR
                      - MUSIC
                      - SCENE
                    w:
                      - WHITE
                      - COLOR
                      - MUSIC
              whiteLight:
                brightness:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 1
                      step: 1
                    w:
                      max: 100
                      min: 1
                      step: 1
                colorTemperature:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 1
                      step: 1
                    w:
                      max: 100
                      min: 1
                      step: 1
              colorLight:
                hue:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 360
                      min: 0
                      step: 1
                    w:
                      max: 360
                      min: 0
                      step: 1
                saturation:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 0
                      step: 1
                    w:
                      max: 100
                      min: 0
                      step: 1
                brightness:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 100
                      min: 1
                      step: 1
                    w:
                      max: 100
                      min: 1
                      step: 1
        gas_sensor-profile-example:
          value:
            property:
              detectState:
                gasState:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - ALARM
                      - NORMAL
            notification:
              push:
                - GAS_IS_DETECTED
        fire_sensor-profile-example:
          value:
            property:
              detectState:
                smokeState:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - ALARM
                      - NORMAL
                coverState:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - OPEN
                      - CLOSE
              battery:
                percent:
                  type: range
                  mode:
                    - r
                  value:
                    r:
                      max: 100
                      min: 0
                      step: 1
            notification:
              push:
                - BATTERY_IS_LOW
                - FIRE_IS_DETECTED
                - COVER_IS_SEPARATED
        water_leak_sensor-profile-example:
          value:
            property:
              detectState:
                leakState:
                  type: enum
                  mode:
                    - r
                  value:
                    r:
                      - ALARM
                      - NORMAL
              battery:
                percent:
                  type: range
                  mode:
                    - r
                  value:
                    r:
                      max: 100
                      min: 0
                      step: 1
            notification:
              push:
                - BATTERY_IS_LOW
                - WATER_LEAK_IS_DETECTED
        thermo_hygrometer-profile-example:
          value:
            property:
              temperature:
                currentTemperature:
                  type: number
                  mode:
                    - r
              humidity:
                currentHumidity:
                  type: range
                  mode:
                    - r
                  value:
                    r:
                      max: 100
                      min: 0
                      step: 1
              battery:
                percent:
                  type: range
                  mode:
                    - r
                  value:
                    r:
                      max: 100
                      min: 0
                      step: 1
            notification:
              push:
                - BATTERY_IS_LOW
        siren-profile-example:
          value:
            property:
              switchState:
                currentSwitch:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - 'ON'
                      - 'OFF'
                    w:
                      - 'ON'
                      - 'OFF'
              alarm:
                volume:
                  type: enum
                  mode:
                    - r
                    - w
                  value:
                    r:
                      - MUTE
                      - LOW
                      - MID
                      - HIGH
                    w:
                      - MUTE
                      - LOW
                      - MID
                      - HIGH
                time:
                  type: range
                  mode:
                    - r
                    - w
                  value:
                    r:
                      max: 3600
                      min: 1
                      step: 1
                    w:
                      max: 3600
                      min: 1
                      step: 1
            notification:
              push:
                - BATTERY_IS_LOW
                - ALARM_IS_DETECTED
        refrigerator-object-example:
          value:
            doorStatus:
              - doorState: CLOSE
                locationName: MAIN
            powerSave:
              powerSaveEnabled: false
            refrigeration:
              expressMode: false
              expressModeName: FREEZER
            temperature:
              - locationName: FRIDGE
                targetTemperature: 8
                unit: C
              - locationName: FREEZER
                targetTemperature: -13
                unit: C
            temperatureInUnits:
              - targetTemperatureC: 7
                targetTemperatureF: 46
                unit: C
                locationName: FRIDGE
              - targetTemperatureC: -16
                targetTemperatureF: 8
                unit: C
                locationName: FREEZER
            waterFilterInfo:
              usedTime: 0
        washer-object-example:
          value:
            - location:
                locationName: MAIN
              remoteControlEnable:
                remoteControlEnabled: true
              runState:
                currentState: INITIAL
              cycle:
                cycleCount: 0
              timer:
                relativeHourToStop: 3
                relativeMinuteToStop: 0
                remainHour: 0
                remainMinute: 0
                totalHour: 0
                totalMinute: 0
        dryer-object-example:
          value:
            remoteControlEnable:
              remoteControlEnabled: false
            runState:
              currentState: PAUSE
            timer:
              relativeHourToStop: 3
              relativeMinuteToStop: 0
              remainHour: 0
              remainMinute: 0
              totalHour: 0
              totalMinute: 0
        air_conditioner-object-example:
          value:
            airConJobMode:
              currentJobMode: AUTO
            airQualitySensor:
              PM1: 27
              PM2: 35
              PM10: 49
              humidity: 27
            temperature:
              currentTemperature: 10.5
              targetTemperature: 14
              unit: C
            temperatureInUnits:
              - currentTemperature: 10.5
                targetTemperature: 14
                unit: C
              - currentTemperature: 51
                targetTemperature: 58
                unit: F
            twoSetTemperature:
              currentTemperature: 10.5
              coolTargetTemperature: 29.5
              heatTargetTemperature: 14
              unit: C
              twoSetEnabled: true
            twoSetTemperatureInUnits:
              - coolTargetTemperature: 29.5
                heatTargetTemperature: 14
                unit: C
              - coolTargetTemperature: 85
                heatTargetTemperature: 58
                unit: F
            filterInfo:
              filterRemainPercent: 98
            airFlow:
              windStrength: HIGH
            windDirection:
              swirlWind: false
              forestWind: false
              airGuideWind: false
              highCeilingWind: false
              autoFitWind: false
              concentrationWind: false
            operation:
              airConOperationMode: POWER_ON
              airCleanOperationMode: 'ON'
            timer:
              absoluteStartTimer: UNSET
              absoluteStopTimer: UNSET
            sleepTimer:
              relativeStopTimer: UNSET
            display:
              light: 'OFF'
        air_purifier-object-example:
          value:
            airPurifierJobMode:
              currentJobMode: CLEAN
            operation:
              airPurifierOperationMode: POWER_OFF
            timer:
              absoluteHourToStart: 23
              absoluteMinuteToStart: 24
              absoluteHourToStop: 9
              absoluteMinuteToStop: 8
              absoluteStartTimer: SET
              absoluteStopTimer: SET
            sleepTimer:
              relativeStopTimer: UNSET
            airFlow:
              windStrength: HIGH
            airQualitySensor:
              PM1: 0
              PM2: 0
              PM10: 72
              oder: 0
              odor: 0
              odorLevel: INVALID
              totalPollution: 1
              totalPollutionLevel: GOOD
              monitoringEnabled: ON_WORKING
        robot_cleaner-object-example:
          title: Robot_Cleaner
          value:
            runState:
              currentState: CHARGING
            robotCleanerJobMode:
              currentJobMode: ZIGZAG
            battery:
              level: FULL
        oven-object-example:
          title: Oven
          value:
            - runState:
                currentState: INITIAL
              location:
                locationName: UPPER
              temperature:
                targetTemperature: 0
                unit: F
              timer:
                remainHour: 0
                remainMinute: 0
                remainSecond: 0
            - runState:
                currentState: PREHEATING
              cook:
                cookMode: BAKE
              location:
                locationName: LOWER
              temperature:
                targetTemperature: 350
                unit: F
              remoteControlEnable:
                remoteControlEnabled: true
              timer:
                remainHour: 0
                remainMinute: 2
                remainSecond: 51
        dish_washer-object-example:
          value:
            dishWashingStatus:
              rinseRefill: false
            doorStatus:
              doorState: CLOSE
            preference:
              cleanLReminder: CLEANLREMINDER_OFF
              mCReminder: MCREMINDER_OFF
              rinseLevel: RINSELEVEL_0
              signalLevel: SIGNALLEVEL_OFF
              softeningLevel: SOFTENINGLEVEL_0
            runState:
              currentState: POWER_OFF
            timer:
              relativeHourToStart: 0
              relativeMinuteToStart: 0
              remainHour: 0
              remainMinute: 0
              totalHour: 0
              totalMinute: 0
        styler-object-example:
          value:
            remoteControlEnable:
              remoteControlEnabled: false
            runState:
              currentState: INITIAL
            timer:
              relativeHourToStop: 0
              relativeMinuteToStop: 0
              remainHour: 0
              remainMinute: 0
              totalHour: 0
              totalMinute: 0
        water_purifier-object-example:
          value:
            runState:
              cockState: CLEANING
            waterInfo:
              waterType:
                - COLD
                - NORMAL
                - HOT
                - SODA
        dehumidifier-object-example:
          value:
            airFlow:
              windStrength: HIGH
            dehumidifierJobMode:
              currentJobMode: INTENSIVE_DRY
            humidity:
              currentHumidity: 45
              targetHumidity: 50
            operation:
              dehumidifierOperationMode: POWER_ON
            timer:
              absoluteStartTimer: UNSET
              absoluteStopTimer: UNSET
        ceiling_fan-object-example:
          value:
            airFlow:
              windStrength: LOW
            operation:
              ceilingfanOperationMode: POWER_ON
        wine_cellar-object-example:
          value:
            operation:
              optimalHumidity: 'OFF'
            temperature:
              - locationName: WINE_UPPER
                targetTemperature: 18
                unit: C
              - locationName: WINE_LOWER
                targetTemperature: 11
                unit: C
            temperatureInUnits:
              - targetTemperatureC: 18
                targetTemperatureF: 18
                unit: C
                locationName: WINE_UPPER
              - targetTemperatureC: 11
                targetTemperatureF: 11
                unit: C
                locationName: WINE_LOWER
        kimchi_refrigerator-object-example:
          value:
            refrigeration:
              oneTouchFilter: 'OFF'
            temperature:
              - locationName: TOP
                targetTemperature: KIMCHI
              - locationName: MIDDLE
                targetTemperature: KIMCHI
              - locationName: BOTTOM
                targetTemperature: KIMCHI
        home_brew-object-example:
          value:
            runState:
              currentState: STANDBY
            recipe:
              recipeName: MY_RECIPE
              wortInfo: HOPPY
              yeastInfo: AMERICAN_ALE
              hopOilInfo:
                - CASCADE
              hopOilCapsule1: CASCADE
              hopOilCapsule2: CASCADE
              flavorInfo:
                - CORIANDER
                - CORIANDER_SEED
              flavorCapsule1: CORIANDER
              flavorCapsule2: CORIANDER_SEED
              beerRemain: 1
            timer:
              elapsedDayState: 0
              elapsedDayTotal: 0
        plant_cultivator-object-example:
          value:
            - location:
                locationName: UPPER
              runState:
                currentState: POWER_ON
                growthMode: EXT_EXPERT
                windVolume: 1
              light:
                brightness: 4
                duration: 14
                startHour: 3
                startMinute: 0
                endHour: 17
                endMinute: 0
              temperature:
                dayTargetTemperature: 22
                nightTargetTemperature: 21
            - location:
                locationName: LOWER
              runState:
                currentState: POWER_ON
                growthMode: STANDARD
                windVolume: 2
              light:
                brightness: 5
                duration: 17
                startHour: 3
                startMinute: 0
                endHour: 17
                endMinute: 0
              temperature:
                dayTargetTemperature: 25
                nightTargetTemperature: 18
        washtower_washer-object-example:
          value:
            - location:
                locationName: MAIN
              remoteControlEnable:
                remoteControlEnabled: false
              cycle:
                cycleCount: 0
              runState:
                currentState: END
              timer:
                relativeHourToStop: 3
                relativeMinuteToStop: 0
                remainHour: 0
                remainMinute: 0
                totalHour: 0
                totalMinute: 0
        washtower_dryer-object-example:
          value:
            remoteControlEnable:
              remoteControlEnabled: false
            runState:
              currentState: RESERVED
            timer:
              relativeHourToStop: 0
              relativeMinuteToStop: 0
              remainHour: 0
              remainMinute: 0
              totalHour: 0
              totalMinute: 0
        washtower-object-example:
          value:
            washer:
              runState:
                currentState: POWER_OFF
              remoteControlEnable:
                remoteControlEnabled: false
              cycle:
                cycleCount: 0
              timer:
                remainHour: 0
                remainMinute: 0
                relativeHourToStart: 0
                relativeMinuteToStart: 0
                totalHour: 0
                totalMinute: 0
            dryer:
              runState:
                currentState: POWER_OFF
              remoteControlEnable:
                remoteControlEnabled: false
              timer:
                remainHour: 0
                remainMinute: 0
                relativeHourToStop: 0
                relativeMinuteToStop: 0
                totalHour: 0
                totalMinute: 0
        cooktop-object-example:
          value:
            - location:
                locationName: LEFT_FRONT
              cookingZone:
                currentState: INITIAL
              power:
                powerLevel: 3
              timer:
                remainHour: 0
                remainMinute: 27
              remoteControlEnable:
                remoteControlEnabled: false
            - location:
                locationName: RIGHT_FRONT
              cookingZone:
                currentState: INITIAL
              power:
                powerLevel: 0
              timer:
                remainHour: 0
                remainMinute: 0
              remoteControlEnable:
                remoteControlEnabled: false
            - location:
                locationName: LEFT_REAR
              cookingZone:
                currentState: INITIAL
              power:
                powerLevel: 0
              timer:
                remainHour: 0
                remainMinute: 0
              remoteControlEnable:
                remoteControlEnabled: false
        hood-object-example:
          value:
            operation:
              hoodOperationMode: POWER_ON
            lamp:
              lampBrightness: 2
            ventilation:
              fanSpeed: 1
            timer:
              remainMinute: 3
              remainSecond: 25
        microwave_oven-object-example:
          value:
            runState:
              currentState: INITIAL
            timer:
              remainMinute: 0
              remainSecond: 0
            ventilation:
              fanSpeed: 3
            lamp:
              lampBrightness: 0
        system_boiler-object-example:
          value:
            boilerJobMode:
              currentJobMode: COOL
            operation:
              boilerOperationMode: POWER_OFF
              hotWaterMode: 'OFF'
              roomTempMode: AIR
              roomWaterMode: OUT_WATER
            temperature:
              currentTemperature: 40
              targetTemperature: 18
              unit: C
            hotWaterTemperatureInUnits:
              - currentTemperature: 0
                unit: C
              - currentTemperature: 32
                unit: F
            roomTemperatureInUnits:
              - airCurrentTemperature: 40
                targetTemperature: 18
                currentTemperature: 40
                unit: C
              - airCurrentTemperature: 104
                targetTemperature: 64
                currentTemperature: 104
                unit: F
        air_purifier_fan-object-example:
          value:
            airFanJobMode:
              currentJobMode: SPOT_CLEAN
            operation:
              airFanOperationMode: POWER_ON
            airFlow:
              warmMode: WARM_OFF
              windStrength: WIND_5
              windTemperature: 0
              windAngle: ANGLE_45
            airQualitySensor:
              PM1: 31
              PM10: 45
              PM2: 35
              humidity: 30
              temperature: 40
              monitoringEnabled: ON_WORKING
              odor: 1
              odorLevel: WEAK
              totalPollution: 2
              totalPollutionLevel: NORMAL
            display:
              light: LEVEL_1
            misc:
              uvNano: 'OFF'
            timer:
              absoluteStartTimer: UNSET
              absoluteStopTimer: UNSET
            sleepTimer:
              relativeStopTimer: UNSET
        stick_cleaner-object-example:
          value:
            runState:
              currentState: STANDBY
            stickCleanerJobMode:
              currentJobMode: 'OFF'
            battery:
              level: HIGH
        water_heater-object-example:
          value:
            waterHeaterJobMode:
              currentJobMode: VACATION
            temperature:
              currentTemperature: 42
              targetTemperature: 52
            operation:
              waterHeaterOperationMode: POWER_ON
        main_washcombo-object-example:
          value:
            - runState:
                currentState: POWER_OFF
              remoteControlEnable:
                remoteControlEnabled: false
              timer:
                remainHour: 0
                remainMinute: 0
                relativeHourToStop: 0
                relativeMinuteToStop: 0
                totalHour: 0
                totalMinute: 0
              cycle:
                cycleCount: 0
              location:
                locationName: MAIN
        mini_washcombo-object-example:
          value:
            - runState:
                currentState: POWER_OFF
              remoteControlEnable:
                remoteControlEnabled: false
              timer:
                remainHour: 0
                remainMinute: 0
                relativeHourToStop: 0
                relativeMinuteToStop: 0
                totalHour: 0
                totalMinute: 0
              cycle:
                cycleCount: 0
              location:
                locationName: MINI
        humidifier-object-example:
          title: Humidifier
          value:
            humidifierJobMode:
              currentJobMode: HUMIDIFY
            operation:
              humidifierOperationMode: POWER_ON
              autoMode: AUTO_ON
              sleepMode: SLEEP_OFF
              hygieneDryMode: SILENT
            humidity:
              targetHumidity: 65
              warmMode: WARM_ON
            airFlow:
              windStrength: AUTO
            airQualitySensor:
              PM1: 4
              PM2: 4
              PM10: 6
              humidity: 36
              temperature: 24.5
              totalPollution: 1
              totalPollutionLevel: GOOD
              monitoringEnabled: ON_WORKING
            display:
              light: LEVEL_2
            moodLamp:
              moodLampState: 'ON'
            timer:
              absoluteStartTimer: UNSET
              absoluteStopTimer: UNSET
            sleepTimer:
              relativeStopTimer: UNSET
        odu-object-example:
          title: ODU
          value:
            operation:
              operationMode: STOP
            temperature:
              outdoorTemperature: 20
            info:
              modelName: HP_SUPER5
              capacity: 0
        idu-object-example:
          title: IDU
          value:
            operation:
              airConOperationMode: POWER_ON
            jobMode:
              airConJobMode: AUTO
            temperature:
              currentTemperature: 23
              targetTemperature: 20
              targetTemperatureLowLimit: 18
              targetTemperatureUpperLimit: 21
            powerSave:
              powerSaveEnabled: false
              powerSaveStep: POWERSAVE_LEVEL_1
            airFlow:
              windStrength: LOW
              windDirectionSetting: false
            outdoor:
              outdoorHeaterSetting: false
              outdoorHeatPumpSetting: false
            lock:
              fullLock: false
              modeLock: false
              fanLock: false
              temperatureLock: false
            alarm:
              filterReplacementAlarm: false
            error:
              errorCode: '0'
        signage-object-example:
          title: SIGNAGE
          value:
            power:
              power: true
              screen: SCREEN_ON
              noSignalPowerOff: false
              noIrPowerOff: false
              pmMode: '00'
              powerOnStatus: '00'
              powerOnDelay: 0
              energySavingMode: '00'
              wol: false
            display:
              input: '91'
              language: 0f
              ism: '08'
              pictureMode: '08'
              backlight: 100
              brightness: 50
              tint: 50
              contrast: 100
              sharpness: 25
              color: 60
            audio:
              volume: 3
              volumeMute: false
              soundMode: '01'
              soundBalance: 50
            temperature:
              main: 39
            info:
              osType: WEBOS
        motion_sensor-object-example:
          value:
            battery:
              percent: 10
        temperature_humidity_sensor-object-example:
          value:
            battery:
              percent: 10
            temperature:
              currentTemperature: '19'
            humidity:
              currentHumidity: '60'
        door_sensor-object-example:
          value:
            battery:
              percent: 10
            doorState:
              currentState: OPEN
        button-object-example:
          value:
            battery:
              percent: 10
        light_switch-object-example:
          value:
            switchState:
              - switchName: SWITCH_1
                currentSwitch: 'ON'
              - switchName: SWITCH_2
                currentSwitch: 'OFF'
              - switchName: SWITCH_3
                currentSwitch: 'ON'
        door_lock-object-example:
          value:
            battery:
              percent: 10
            doorState:
              currentState: OPEN
        push_pull_door_lock-object-example:
          value:
            battery:
              percent: 10
            doorState:
              currentState: OPEN
        plug-object-example:
          value:
            runState:
              currentState: POWER_ON
            electricity:
              current: 1000
              currentUnit: mA
              voltage: 210
              voltageUnit: V
              power: 0
              powerUnit: W
        plug_mini-object-example:
          value:
            runState:
              currentState: POWER_ON
            electricity:
              current: 0
              currentUnit: mA
              voltage: 216.1
              voltageUnit: V
              power: 0
              powerUnit: W
            switchState:
              currentSwitch: LAST
              indicateLight: ON_RELAY
              kidLock: UNLOCK
        bulb_white-object-example:
          value:
            runState:
              currentState: POWER_OFF
            whiteLight:
              brightness: 7
              colorTemperature: 4500
        bulb_color-object-example:
          value:
            runState:
              currentState: POWER_OFF
            mode:
              lightMode: COLOR
            whiteLight:
              brightness: 7
            colorLight:
              hue: 0
              saturation: 100
              brightness: 100
        line_led-object-example:
          value:
            runState:
              currentState: POWER_OFF
            mode:
              lightMode: COLOR
            whiteLight:
              brightness: 7
            colorLight:
              hue: 0
              saturation: 100
              brightness: 100
        curtain_ctrl-object-example:
          value:
            openCloseState:
              currentState: CLOSE
              level: 0
            calibration:
              railCalibration: DEACTIVATE
            motor:
              motorDirection: FORWARD
        blind_motor-object-example:
          value:
            openCloseState:
              currentState: STOP
              level: 0
            motor:
              motorDirection: BACKWARD
        switch_strip-object-example:
          value:
            runState:
              currentState: POWER_OFF
            switchState:
              - switchName: SWITCH_1
                currentSwitch: 'ON'
              - switchName: SWITCH_2
                currentSwitch: 'OFF'
              - switchName: SWITCH_3
                currentSwitch: 'ON'
              - switchName: SWITCH_USB
                currentSwitch: 'ON'
        starlight-object-example:
          value:
            runState:
              currentState: POWER_OFF
            switchState:
              switchLaser: 'OFF'
              switchColor: 'OFF'
            mode:
              lightMode: COLOR
              sceneMode: false
            laserLight:
              brightness: 70
              motorSpeed: 100
            colorLight:
              hue: 360
              saturation: 50
              brightness: 100
        doorbell-object-example:
          value:
            chime:
              volume: 5
        pet_peeder-object-example:
          value:
            feed:
              amount: 50
        home_camera-object-example:
          value:
            mode:
              privateMode: 'ON'
        sync_box-object-example:
          value:
            runState:
              currentState: POWER_OFF
            mode:
              lightMode: MUSIC
              musicMode: JAZZ
            colorLight:
              hue: 0
              saturation: 100
              brightness: 100
            video:
              videoScene: MOVIE
              intensity: HIGH
              colorMode: STOP
            input:
              hdmiSwitch: 1
            layout:
              lightPosition: LOW_RIGHT
              lightDirection: CLOCKWISE
        sync_box_sub-object-example:
          value:
            runState:
              currentState: POWER_ON
            mode:
              lightMode: COLOR
            whiteLight:
              brightness: 48
              colorTemperature: 30
            colorLight:
              hue: 0
              saturation: 100
              brightness: 100
        gas_sensor-object-example:
          value:
            detectState:
              gasState: ALARM
        fire_sensor-object-example:
          value:
            detectState:
              smokeState: NORMAL
              coverState: OPEN
            battery:
              percent: 57
        water_leak_sensor-object-example:
          value:
            detectState:
              leakState: ALARM
            battery:
              percent: 57
        thermo_hygrometer-object-example:
          value:
            temperature:
              currentTemperature: 24
            humidity:
              currentHumidity: 50
            battery:
              percent: 57
        siren-object-example:
          value:
            switchState:
              currentSwitch: 'OFF'
            alarm:
              volume: MUTE
              time: 0
        refrigerator-command-example:
          description: Refrigerator - Power Save On
          value:
            powerSave:
              powerSaveEnabled: true
        washer-command-example:
          description: Washer - Power ON / Start washing
          value:
            location:
              locationName: MAIN
            operation:
              washerOperationMode: START
        dryer-command-example:
          description: Dryer - Start drying
          value:
            operation:
              dryerOperationMode: START
        air_conditioner-command-example:
          description: Air Conditioner - Set On Timer
          value:
            timer:
              absoluteHourToStart: 10
              absoluteMinuteToStart: 36
        air_purifier-command-example:
          description: Air Purifier - Run mode
          value:
            airPurifierJobMode:
              currentJobMode: CLEAN
        robot_cleaner-command-example:
          title: Robot_Cleaner
          description: Robot Cleaner - Run mode
          value:
            operation:
              cleanOperationMode: HOMING
        oven-command-example:
          title: Oven
          description: Oven - Oven operation Mode
          value:
            location:
              locationName: LOWER
            operation:
              ovenOperationMode: START
        dish_washer-command-example:
          description: Dish Washer - Run mode
          value:
            operation:
              dishWasherOperationMode: START
        styler-command-example:
          description: Styler - Run mode
          value:
            operation:
              stylerOperationMode: START
        dehumidifier-command-example:
          description: Dehumidifier - Run mode
          value:
            humidifierJobMode:
              currentJobMode: HUMIDIFY
        ceiling_fan-command-example:
          description: Ceiling Fan - Run mode
          value:
            operation:
              ceilingfanOperationMode: POWER_ON
        wine_cellar-command-example:
          description: Wine Cellar - light Brightness
          value:
            operation:
              lightStatus: 90
        washtower_washer-command-example:
          description: WashTower(Washer) - Start washing
          value:
            operation:
              washerOperationMode: START
            location:
              locationName: MAIN
        washtower_dryer-command-example:
          description: WashTower(Dryer) - Power OFF
          value:
            operation:
              dryerOperationMode: POWER_OFF
        washtower-command-example:
          description: WashTower(Single Unit) - Start drying
          value:
            dryer:
              operation:
                dryerOperationMode: START
        cooktop-command-example:
          description: Cooktop - Power Off
          value:
            operation:
              operationMode: POWER_OFF
        hood-command-example:
          description: Hood - Lamp Brightness
          value:
            lamp:
              lampBrightness: 0
        microwave_oven-command-example:
          description: Microwave Oven
          value:
            lamp:
              lampBrightness: 1
            ventilation:
              fanSpeed: 0
        system_boiler-command-example:
          description: System Boiler - Power ON
          value:
            operation:
              boilerOperationMode: POWER_ON
        air_purifier_fan-command-example:
          description: Air Purifier Fan - Run mode
          value:
            airFanJobMode:
              currentJobMode: SPOT_CLEAN
        water_heater-command-example:
          description: Water Heater - Run mode
          value:
            waterHeaterJobMode:
              currentJobMode: AUTO
        main_washcombo-command-example:
          description: Main WashCombo - operation
          value:
            location:
              locationName: MAIN
            operation:
              washerOperationMode: START
        mini_washcombo-command-example:
          description: Mini WashCombo - operation
          value:
            location:
              locationName: MINI
            operation:
              washerOperationMode: START
        humidifier-command-example:
          title: Humidifier
          description: Humidifier - Run mode
          value:
            humidifierJobMode:
              currentJobMode: HUMIDIFY
        idu-command-example:
          title: IDU
          value:
            operation:
              airConOperationMode: POWER_ON
            jobMode:
              airConJobMode: AUTO
            airFlow:
              windStrength: LOW
            lock:
              fullLock: false
              modeLock: false
              fanLock: false
              temperatureLock: false
            temperature:
              targetTemperature: 20
              targetTemperatureLowLimit: 18
              targetTemperatureUpperLimit: 21
        signage-command-example:
          title: SIGNAGE
          value:
            power:
              screen: SCREEN_ON
        light_switch-command-example:
          value:
            switchState:
              switchName: SWITCH_1
              currentSwitch: 'ON'
        door_lock-command-example:
          value:
            doorState:
              currentState: OPEN
        push_pull_door_lock-command-example:
          value:
            doorState:
              currentState: OPEN
        plug-command-example:
          value:
            runState:
              currentState: POWER_OFF
        plug_mini-command-example:
          value:
            runState:
              currentState: POWER_OFF
        bulb_white-command-example:
          value:
            runState:
              currentState: POWER_OFF
        bulb_color-command-example:
          value:
            runState:
              currentState: POWER_OFF
        line_led-command-example:
          value:
            runState:
              currentState: POWER_OFF
        curtain_ctrl-command-example:
          value:
            openCloseState:
              currentState: OPEN
        blind_motor-command-example:
          value:
            operation:
              operationMode: CLOSE
        switch_strip-command-example:
          value:
            runState:
              currentState: POWER_ON
        starlight-command-example:
          value:
            runState:
              currentState: POWER_ON
        doorbell-command-example:
          value:
            chime:
              volume: 0
        pet_peeder-command-example:
          value:
            feed:
              amount: 30
        home_camera-command-example:
          value:
            mode:
              privateMode: 'ON'
        sync_box-command-example:
          value:
            colorLight:
              hue: 320
              saturation: 30
              brightness: 80
        sync_box_sub-command-example:
          value:
            mode:
              lightMode: COLOR
        siren-command-example:
          value:
            switchState:
              currentSwitch: 'ON'
        push-callback-device-push-example:
          value:
            messageId: kVuV69kGTS25FUs1wrkECQ
            timestamp: '2025-01-09T04:24:35.540658'
            push:
              pushType: DEVICE_PUSH
              deviceId: 30d81ed55587005b58e8143804f93550a6acce04e540a451e5044b6a0489bd02
              deviceType: DEVICE_DRYER
              pushCode: DRYING_IS_COMPLETE
              userList:
                - n2uR0D5vLjvZRvTdvhVJ
        push-callback-device-registered-example:
          value:
            messageId: e5NYvUUApkimXi1yhu3NCA
            timestamp: '2025-01-09T05:23:59.492982'
            push:
              pushType: DEVICE_REGISTERED
              deviceId: 7de94bb8509ade98c49914897f4f12076a45124f28d20a18e105dfcdbfb6dd16
              userNumber: R9EToaDa98Rdnr7KZayE
              modelName: RH16KX
              deviceType: DEVICE_DRYER
              alias: My Dryer
              reportable: true
        push-callback-device-unregistered-example:
          value:
            messageId: M5TIAMMdHUmI1lz3nImWfF
            timestamp: '2025-01-09T05:23:59.492982'
            push:
              pushType: DEVICE_UNREGISTERED
              deviceId: 7de94bb8509ade98c49914897f4f12076a45124f28d20a18e105dfcdbfb6dd16
              userNumber: R9EToaDa98Rdnr7KZayE
              deviceType: DEVICE_DRYER
              alias: My Dryer
        push-callback-device-alias-changed-example:
          value:
            messageId: oGS8u4DVHsuEio7PuZEVmV
            timestamp: '2025-01-09T05:26:46.403987'
            push:
              pushType: DEVICE_ALIAS_CHANGED
              deviceId: 7de94bb8509ade98c49914897f4f12076a45124f28d20a18e105dfcdbfb6dd16
              userNumber: R9EToaDa98Rdnr7KZayE
              alias: My New Dryer
    x-tagGroups:
      - name: Get Started
        tags:
          - Overview
          - API Call Sequence
          - Base URL
          - Codes
          - auth
      - name: ThinQ Business API
        tags:
          - Device API
          - Push API
          - User API
          - DR API
---
