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
        x-displayName: 소개
        description: |
          **ThinQ Business API**를 활용하면 LG전자의 가전제품 뿐만 아니라, 사이니지, 공조설비와 IoT 디바이스의 상태도 한 번에 조회하거나 제어할 수 있습니다.  LG전자 클라우드 플랫폼(LG ThinQ, LG Business Cloud, LG BECON Cloud 등)에 등록된 디바이스라면 직접 손쉽게 B2B 파트너사의 SW와 연동하여 LG전자 디바이스의 상태를 조회/ 제어할 수 있도록 통합 API를 제공합니다.        ThinQ Business API에서 지원하는 디바이스의 종류 및 호출 메시지의 스키마는 **[디바이스 프로파일](/ko/apiManage/device_profile)** 페이지를 참조해주십시오.      

          ThinQ Business API를 사용하기 위해서는 **[파트너십 체결](/ko/mypage/partner/landing)** 절차가 선행되어야 합니다. 파트너십이 승인되면, 실제 제품 없이도 제품이 있는 것처럼 LG전자 클라우드 플랫폼 내에 제품을 등록하고 API 호출을 테스트해 볼 수 있도록 **ThinQ Business 시뮬레이터**를 함께 제공하고 있습니다.      

          ThinQ Business API는 API의 사용 목적에 따라 다음과 같이 분류합니다.

           |API 종류|요약|
           |-|-|
           |Device API|등록한 디바이스의 목록 및 상태를 조회하고, 제어를 수행하기 위한 API|
           |Push API|디바이스의 상태 변화를 수신하기 위해 대상 디바이스를 관리하기 위한 API|
           |User API|B2B 파트너의 서비스에 등록한 사용자를 관리하기 위한 API|
           |DR API|B2B 파트너가 전력 수요반응(DR: Demand Response) 서비스 제공자로서 사용자의 디바이스를 제어하기 위한 API|
      - name: API Call Sequence
        x-displayName: API 호출 시퀀스
        description: "ThinQ Business API를 사용해 서비스를 개발하는 방법을 API 호출 시퀀스로 설명합니다.\n\n## API Token 발급\nAPI Token은 모든 ThinQ Business API 호출의 HTTP 요청 헤더에 포함해야 합니다. API Token은 LG Smart Solution API Developer에서 사전에 받은 API Key와 API Secret 쌍으로 발급할 수 있습니다.  또한 24시간 동안 유효하므로 만료 전에 API Token 발급 API를 사용해 API Token을 재발급해야 합니다.\n\n\n - 사용 API\n    - [`POST /token`](#tag/auth/operation/createAPIToken)\n\n - 시퀀스\n    1. LG Smart Solution API Developer에서 받은 API Key와 API Secret을 API Token 발급 로직을 위해 설정합니다.(API Secret은 API Key 발행 시 메일로 발송됩니다.)\n    2. API Token을 주기적으로 발급받기 위해 API Token 발급 API (POST /token)를 호출합니다. 24시간 이내에 API Token 발급 요청을 다시 수행해야 합니다.\n    \n    <?xml version=\"1.0\" encoding=\"us-ascii\" standalone=\"no\"?><svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" contentStyleType=\"text/css\" height=\"447px\" preserveAspectRatio=\"none\" style=\"width:606px;height:447px;background:#FFFFFF;\" version=\"1.1\" viewBox=\"0 0 606 447\" width=\"606px\" zoomAndPan=\"magnify\"><defs/><g><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"350\" y=\"208.7622\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"350\" y=\"306.439\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"281\" x=\"153.5\" y=\"164.9414\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"281\" x=\"153.5\" y=\"262.6182\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"46\" x2=\"46\" y1=\"84.2295\" y2=\"363.2949\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"219.5\" x2=\"219.5\" y1=\"84.2295\" y2=\"363.2949\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"354.5\" x2=\"354.5\" y1=\"84.2295\" y2=\"363.2949\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"517.5\" x2=\"517.5\" y1=\"84.2295\" y2=\"363.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"77\" x=\"5\" y=\"81.1533\">B2B Partner</text><ellipse cx=\"46.5\" cy=\"13.5\" fill=\"#E2E2F0\" rx=\"8\" ry=\"8\" style=\"stroke:#181818;stroke-width:0.5;\"/><path d=\"M46.5,21.5 L46.5,48.5 M33.5,29.5 L59.5,29.5 M46.5,48.5 L33.5,63.5 M46.5,48.5 L59.5,63.5 \" fill=\"none\" style=\"stroke:#181818;stroke-width:0.5;\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"77\" x=\"5\" y=\"378.4482\">B2B Partner</text><ellipse cx=\"46.5\" cy=\"390.0244\" fill=\"#E2E2F0\" rx=\"8\" ry=\"8\" style=\"stroke:#181818;stroke-width:0.5;\"/><path d=\"M46.5,398.0244 L46.5,425.0244 M33.5,406.0244 L59.5,406.0244 M46.5,425.0244 L33.5,440.0244 M46.5,425.0244 L59.5,440.0244 \" fill=\"none\" style=\"stroke:#181818;stroke-width:0.5;\"/><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"163.5\" y=\"50\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"170.5\" y=\"73.1533\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"163.5\" y=\"362.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"170.5\" y=\"385.4482\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"285.5\" y=\"50\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"292.5\" y=\"73.1533\">ThinQ Business API</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"285.5\" y=\"362.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"292.5\" y=\"385.4482\">ThinQ Business API</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"166\" x=\"434.5\" y=\"50\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"152\" x=\"441.5\" y=\"73.1533\">LG Smart Solution API Developer</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"166\" x=\"434.5\" y=\"362.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"152\" x=\"441.5\" y=\"385.4482\">LG Smart Solution API Developer</text><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"350\" y=\"208.7622\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"350\" y=\"306.439\"/><polygon fill=\"#181818\" points=\"57.5,114.0854,47.5,118.0854,57.5,122.0854,53.5,118.0854\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"51.5\" x2=\"516.5\" y1=\"118.0854\" y2=\"118.0854\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"149\" x=\"63.5\" y=\"113.229\">API Key, API Secret &#51228;&#44277;</text><polygon fill=\"#181818\" points=\"207.5,145.9414,217.5,149.9414,207.5,153.9414,211.5,149.9414\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"46.5\" x2=\"213.5\" y1=\"149.9414\" y2=\"149.9414\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"149\" x=\"53.5\" y=\"145.085\">API Key, API Secret &#49444;&#51221;</text><path d=\"M153.5,164.9414 L230.5,164.9414 L230.5,174.7974 L220.5,184.7974 L153.5,184.7974 L153.5,164.9414 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"281\" x=\"153.5\" y=\"164.9414\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"28\" x=\"168.5\" y=\"180.9409\">loop</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"86\" x=\"245.5\" y=\"179.6333\">[24&#49884;&#44036; &#45236; &#48152;&#48373;]</text><polygon fill=\"#181818\" points=\"338,204.7622,348,208.7622,338,212.7622,342,208.7622\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"219.5\" x2=\"344\" y1=\"208.7622\" y2=\"208.7622\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"75\" x=\"226.5\" y=\"203.9058\">POST /token</text><polygon fill=\"#181818\" points=\"230.5,236.6182,220.5,240.6182,230.5,244.6182,226.5,240.6182\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"224.5\" x2=\"354\" y1=\"240.6182\" y2=\"240.6182\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"60\" x=\"236.5\" y=\"235.7617\">API Token</text><path d=\"M153.5,262.6182 L214.5,262.6182 L214.5,272.4741 L204.5,282.4741 L153.5,282.4741 L153.5,262.6182 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"281\" x=\"153.5\" y=\"262.6182\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"16\" x=\"168.5\" y=\"278.6177\">alt</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"103\" x=\"229.5\" y=\"277.3101\">[API Token &#47564;&#47308;&#49884;]</text><polygon fill=\"#181818\" points=\"338,302.439,348,306.439,338,310.439,342,306.439\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"219.5\" x2=\"344\" y1=\"306.439\" y2=\"306.439\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"75\" x=\"226.5\" y=\"301.5825\">POST /token</text><polygon fill=\"#181818\" points=\"230.5,334.2949,220.5,338.2949,230.5,342.2949,226.5,338.2949\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"224.5\" x2=\"354\" y1=\"338.2949\" y2=\"338.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"60\" x=\"236.5\" y=\"333.4385\">API Token</text><!--SRC=[XP2_IyD05CVdt5_npE9Y4OfJ1y6WbcAnaMGJXslwj4UJk-Fk9UWgtUmgE7GeABWMQl-ffd-4bpGW7TJjyNqVFk-7dGYfkU4PZF2UvobTAadNF4FeTozwCJuIEpoWCReWuuH6y9RAAHKI6Kz86V23TW0XDoJH-C0jv1ODSqeIYT1S4lXD5o8qXKYmflGksmVZiP0t4EJMwQs5ix1NiyDa7-jtOQ1HLdqunm9JfPlP8ooi86IiAQ1rMk_JgTahV3ggYmWJWmJRnNopMhCAgC1cfL_OwSTsySeUZCerf4ffk6sVR5_cc-KKokSlA9TlvMfznxp6KWc7IGV2GHJ3CQa9IkQvZud2VR6wo7FMtEoEYEisoX7ZAVqaK7xEolUPcyBWBo_yB_u6]--></g></svg>\n\n## 디바이스 상태 조회\n디바이스 상태를 조회하기 위해 다음과 같이 Device API를 사용합니다.\n\n\n  - 사용 API\n    - [`GET /devices`](#tag/Device-API/operation/getDevices)\n    - [`GET /devices/{deviceId}/state`](#tag/Device-API/operation/getStatusOfDevice)\n\n  - 시퀀스\n    1. B2B 파트너의 서비스는 디바이스 목록 조회 API(GET /devices)를 이용해 LG전자 플랫폼에 등록된 디바이스 목록을 가져와야 합니다. 이 과정은 처음 한 번만 수행하면 되고, 추가되거나 삭제된 디바이스가 없다면 매번 수행할 필요는 없습니다.\n    2. 디바이스 목록에서 상태를 조회할 디바이스의 deviceId 값을 확인하고, 이 값을 이용해 디바이스 상태 조회 API (GET /devices/{deviceId}/state)를 호출합니다.\n\n    <?xml version=\"1.0\" encoding=\"us-ascii\" standalone=\"no\"?><svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" contentStyleType=\"text/css\" height=\"258px\" preserveAspectRatio=\"none\" style=\"width:346px;height:258px;background:#FFFFFF;\" version=\"1.1\" viewBox=\"0 0 346 258\" width=\"346px\" zoomAndPan=\"magnify\"><defs/><g><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"256\" y=\"100.0503\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"256\" y=\"170.7622\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"330.5\" x=\"10\" y=\"56.2295\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"76\" x2=\"76\" y1=\"39.2295\" y2=\"220.6182\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"260.5\" x2=\"260.5\" y1=\"39.2295\" y2=\"220.6182\"/><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"20\" y=\"5\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"27\" y=\"28.1533\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"20\" y=\"219.6182\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"27\" y=\"242.7715\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"191.5\" y=\"5\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"198.5\" y=\"28.1533\">ThinQ Business API</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"191.5\" y=\"219.6182\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"198.5\" y=\"242.7715\">ThinQ Business API</text><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"256\" y=\"100.0503\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"256\" y=\"170.7622\"/><path d=\"M10,56.2295 L71,56.2295 L71,66.0854 L61,76.0854 L10,76.0854 L10,56.2295 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"330.5\" x=\"10\" y=\"56.2295\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"16\" x=\"25\" y=\"72.229\">alt</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"86\" y=\"70.9214\">[&#49352; &#47785;&#47197;&#51060; &#54596;&#50836;&#54620; &#44221;&#50864;]</text><polygon fill=\"#181818\" points=\"244,96.0503,254,100.0503,244,104.0503,248,100.0503\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"76\" x2=\"250\" y1=\"100.0503\" y2=\"100.0503\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"77\" x=\"83\" y=\"95.1938\">GET /devices</text><polygon fill=\"#181818\" points=\"87,127.9063,77,131.9063,87,135.9063,83,131.9063\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"81\" x2=\"260\" y1=\"131.9063\" y2=\"131.9063\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"82\" x=\"93\" y=\"127.0498\">&#46356;&#48148;&#51060;&#49828; &#47785;&#47197;</text><polygon fill=\"#181818\" points=\"244,166.7622,254,170.7622,244,174.7622,248,170.7622\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"76\" x2=\"250\" y1=\"170.7622\" y2=\"170.7622\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"161\" x=\"83\" y=\"165.9058\">GET /device/{deviceId}/state</text><polygon fill=\"#181818\" points=\"87,198.6182,77,202.6182,87,206.6182,83,202.6182\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"81\" x2=\"260\" y1=\"202.6182\" y2=\"202.6182\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"82\" x=\"93\" y=\"197.7617\">&#46356;&#48148;&#51060;&#49828; &#49345;&#53468;</text><!--SRC=[AyxEp2j8B4hCLKX9JKiipIbnoyyhyKlCJLNmSNVr34cjAE42IfTa9cSM9EQLA2W503bvgKKAmQb5PPd9gKeAYSKA1H0nL8KX6PbvWGfEfSMPUQd5nGgE0PvWjKd9N8av9GflcZiKNgzQ-NhXt3TpjoYydThoPjQKjrFdABpQjFVDh0rS2fnGCnLqxO1Qh1JSNKCKz5DIGLOM0sKJaqioon9BKa76SHQbbfGMvIcydZBbzOOfGEFUT2s1cisLcfV2XTia_Me8xPbIgrzS0ZIE2zbSRCQ-QMvyspm70000]--></g></svg>\n\n## 디바이스 제어\n디바이스 제어를 위해 다음과 같이 Device API를 사용합니다.\n\n  - 사용 API\n    - [`GET /devices`](#tag/Device-API/operation/getDevices)\n    - [`GET /devices/{deviceId}/profile`](#tag/Device-API/operation/getProfileOfDevice)\n    - [`POST /devices/{deviceId}/state`](#tag/Device-API/operation/controlDevice)\n\n  - 시퀀스\n    1. B2B 파트너의 서비스는 디바이스 목록 조회 API (GET /devices)를 이용해 LG전자 플랫폼에 등록된 디바이스 목록을 가져와야 합니다. 이 과정은 처음 한 번만 수행하면 되고, 추가되거나 삭제된 디바이스가 없다면 매번 수행할 필요는 없습니다.\n    2. 디바이스 목록에서 제어 대상 디바이스의 deviceId 값을 확인하고, 이 값을 이용해 디바이스 프로파일 조회 API (GET /devices/{device-id}/profile)를 호출합니다.\n    3. API 호출 응답으로 받은 디바이스 프로파일을 토대로 해당 디바이스에 대한 제어 명령을 생성합니다. 제어 명령은 디바이스 프로파일에서 제어를 원하는 속성을 찾아 name 과 value 쌍으로 표현합니다.\n    4. deviceId와 제어 명령을 이용해 디바이스 제어 API (POST /devices/{device-id}/state)를 호출합니다.\n    5. API 응답으로 디바이스 제어 결과를 반환받습니다.\n\n    <?xml version=\"1.0\" encoding=\"us-ascii\" standalone=\"no\"?><svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" contentStyleType=\"text/css\" height=\"397px\" preserveAspectRatio=\"none\" style=\"width:360px;height:397px;background:#FFFFFF;\" version=\"1.1\" viewBox=\"0 0 360 397\" width=\"360px\" zoomAndPan=\"magnify\"><defs/><g><rect fill=\"#FFFFFF\" height=\"170.4238\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"71\" y=\"170.7622\"/><rect fill=\"#FFFFFF\" height=\"28\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"76\" y=\"242.4741\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"270\" y=\"100.0503\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"270\" y=\"170.7622\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"270\" y=\"309.3301\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"344.5\" x=\"10\" y=\"56.2295\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"76\" x2=\"76\" y1=\"39.2295\" y2=\"359.186\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"274.5\" x2=\"274.5\" y1=\"39.2295\" y2=\"359.186\"/><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"20\" y=\"5\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"27\" y=\"28.1533\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"20\" y=\"358.186\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"27\" y=\"381.3394\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"205.5\" y=\"5\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"212.5\" y=\"28.1533\">ThinQ Business API</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"205.5\" y=\"358.186\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"212.5\" y=\"381.3394\">ThinQ Business API</text><rect fill=\"#FFFFFF\" height=\"170.4238\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"71\" y=\"170.7622\"/><rect fill=\"#FFFFFF\" height=\"28\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"76\" y=\"242.4741\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"270\" y=\"100.0503\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"270\" y=\"170.7622\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"270\" y=\"309.3301\"/><path d=\"M10,56.2295 L71,56.2295 L71,66.0854 L61,76.0854 L10,76.0854 L10,56.2295 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"344.5\" x=\"10\" y=\"56.2295\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"16\" x=\"25\" y=\"72.229\">alt</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"86\" y=\"70.9214\">[&#49352; &#47785;&#47197;&#51060; &#54596;&#50836;&#54620; &#44221;&#50864;]</text><polygon fill=\"#181818\" points=\"258,96.0503,268,100.0503,258,104.0503,262,100.0503\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"76\" x2=\"264\" y1=\"100.0503\" y2=\"100.0503\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"77\" x=\"83\" y=\"95.1938\">GET /devices</text><polygon fill=\"#181818\" points=\"87,127.9063,77,131.9063,87,135.9063,83,131.9063\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"81\" x2=\"274\" y1=\"131.9063\" y2=\"131.9063\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"82\" x=\"93\" y=\"127.0498\">&#46356;&#48148;&#51060;&#49828; &#47785;&#47197;</text><polygon fill=\"#181818\" points=\"258,166.7622,268,170.7622,258,174.7622,262,170.7622\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"81\" x2=\"264\" y1=\"170.7622\" y2=\"170.7622\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"166\" x=\"88\" y=\"165.9058\">GET /device/{deviceId}/profile</text><polygon fill=\"#181818\" points=\"92,198.6182,82,202.6182,92,206.6182,88,202.6182\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"86\" x2=\"274\" y1=\"202.6182\" y2=\"202.6182\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"108\" x=\"98\" y=\"197.7617\">&#46356;&#48148;&#51060;&#49828; &#54532;&#47196;&#54028;&#51068;</text><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"86\" x2=\"128\" y1=\"234.4741\" y2=\"234.4741\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"128\" x2=\"128\" y1=\"234.4741\" y2=\"247.4741\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"87\" x2=\"128\" y1=\"247.4741\" y2=\"247.4741\"/><polygon fill=\"#181818\" points=\"97,243.4741,87,247.4741,97,251.4741,93,247.4741\" style=\"stroke:#181818;stroke-width:1.0;\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"56\" x=\"93\" y=\"229.6177\">&#47749;&#47161; &#49373;&#49457;</text><polygon fill=\"#181818\" points=\"258,305.3301,268,309.3301,258,313.3301,262,309.3301\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"81\" x2=\"264\" y1=\"309.3301\" y2=\"309.3301\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"170\" x=\"88\" y=\"304.4736\">POST /device/{deviceId}/state</text><polygon fill=\"#181818\" points=\"87,337.186,77,341.186,87,345.186,83,341.186\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"81\" x2=\"274\" y1=\"341.186\" y2=\"341.186\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"56\" x=\"93\" y=\"336.3296\">&#47749;&#47161; &#44208;&#44284;</text><!--SRC=[TOzFIyCm68VFwwTusLrwtq5GcACWMbc_G6pVOR3BIf8EGJnPGMJ7xZ9MSE15JtNk8imlrAJVmSnMcQwUahn_dkSNSKbPH3WPGe034eVoQCJa2HaY7FUwZeTNqZ9jINqQ4IQXxPe7Gmvzv6FgOnk8WAYg_HxqBYWxWyDOK8P2m87hVCsU-nO99UZRUr0lpsgHwMm5vJJHixISpg5OVkXPRa6hPiBUlbdfGA_hWHtWHYbCb_YIZed43Qx5KSQSWKfJbQS6fn-UQhQ5BB3-9zdNrUa4DtR4HmCQelL3_lxKjgh9LAQ9MipBoKHdwsrNVUsOA7VgyTtyEDF9wou_m9tIdyJkQRynif1cgJ5VPIoMUV6sRX1y0W00]--></g></svg>\n\n## 디바이스 푸시 구독\n디바이스의 푸시 알림을 구독하기 위해 Push API를 사용합니다. (현재 LG ThinQ 등록 가전제품만 지원합니다.)\n\n  - 사용 API\n    - [`GET /devices`](#tag/Device-API/operation/getDevices)\n    - [`POST /push/{deviceId}/subscribe`](#tag/Event-API/operation/subscribePushMessages)\n\n  - 시퀀스\n    1. B2B 파트너의 서비스는 디바이스 목록 조회 API (GET /devices)를 이용해 LG전자 플랫폼에 등록된 디바이스 목록을 가져와야 합니다. 이 과정은 처음 한 번만 수행하면 되고, 추가되거나 삭제된 디바이스가 없다면 매번 수행할 필요는 없습니다.\n    2. 디바이스 목록에서 푸시 알림을 받을 디바이스의 deviceId 값을 확인하고, 이 값를 이용해 디바이스 푸시 구독 API (POST /push/{deviceId}/subscribe)를 호출합니다.\n    3. API 응답으로 구독 성공/실패에 대한 결과를 반환받습니다. \_\n    4. 디바이스에서 푸시 알림이 발생했을 때, 등록한 callback URL로 푸시 메시지를 전달받습니다. 사용자에게 전달해야 하는 메시지가 있다면 적절히 처리합니다.\_\n\n    <?xml version=\"1.0\" encoding=\"us-ascii\" standalone=\"no\"?><svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" contentStyleType=\"text/css\" height=\"356px\" preserveAspectRatio=\"none\" style=\"width:441px;height:356px;background:#FFFFFF;\" version=\"1.1\" viewBox=\"0 0 441 356\" width=\"441px\" zoomAndPan=\"magnify\"><defs/><g><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"284\" y=\"100.0503\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"284\" y=\"170.7622\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"358.5\" x=\"10\" y=\"56.2295\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"425.5\" x=\"10\" y=\"217.6182\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"76\" x2=\"76\" y1=\"39.2295\" y2=\"318.2949\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"288.5\" x2=\"288.5\" y1=\"39.2295\" y2=\"318.2949\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"396.5\" x2=\"396.5\" y1=\"39.2295\" y2=\"318.2949\"/><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"20\" y=\"5\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"27\" y=\"28.1533\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"20\" y=\"317.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"27\" y=\"340.4482\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"219.5\" y=\"5\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"226.5\" y=\"28.1533\">ThinQ Business API</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"219.5\" y=\"317.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"226.5\" y=\"340.4482\">ThinQ Business API</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"57\" x=\"368.5\" y=\"5\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"43\" x=\"375.5\" y=\"28.1533\">Device</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"57\" x=\"368.5\" y=\"317.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"43\" x=\"375.5\" y=\"340.4482\">Device</text><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"284\" y=\"100.0503\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"284\" y=\"170.7622\"/><path d=\"M10,56.2295 L71,56.2295 L71,66.0854 L61,76.0854 L10,76.0854 L10,56.2295 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"358.5\" x=\"10\" y=\"56.2295\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"16\" x=\"25\" y=\"72.229\">alt</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"86\" y=\"70.9214\">[&#49352; &#47785;&#47197;&#51060; &#54596;&#50836;&#54620; &#44221;&#50864;]</text><polygon fill=\"#181818\" points=\"272,96.0503,282,100.0503,272,104.0503,276,100.0503\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"76\" x2=\"278\" y1=\"100.0503\" y2=\"100.0503\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"77\" x=\"83\" y=\"95.1938\">GET /devices</text><polygon fill=\"#181818\" points=\"87,127.9063,77,131.9063,87,135.9063,83,131.9063\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"81\" x2=\"288\" y1=\"131.9063\" y2=\"131.9063\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"82\" x=\"93\" y=\"127.0498\">&#46356;&#48148;&#51060;&#49828; &#47785;&#47197;</text><polygon fill=\"#181818\" points=\"272,166.7622,282,170.7622,272,174.7622,276,170.7622\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"76\" x2=\"278\" y1=\"170.7622\" y2=\"170.7622\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"189\" x=\"83\" y=\"165.9058\">POST /push/{deviceId}/subscribe</text><polygon fill=\"#181818\" points=\"87,198.6182,77,202.6182,87,206.6182,83,202.6182\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"81\" x2=\"288\" y1=\"202.6182\" y2=\"202.6182\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"32\" x=\"93\" y=\"197.7617\">result</text><path d=\"M10,217.6182 L71,217.6182 L71,227.4741 L61,237.4741 L10,237.4741 L10,217.6182 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"425.5\" x=\"10\" y=\"217.6182\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"16\" x=\"25\" y=\"233.6177\">alt</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"149\" x=\"86\" y=\"232.3101\">[&#54392;&#49884; &#47700;&#49884;&#51648;&#44032; &#48156;&#49373;&#54620; &#44221;&#50864;]</text><polygon fill=\"#181818\" points=\"300,257.439,290,261.439,300,265.439,296,261.439\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"294\" x2=\"396\" y1=\"261.439\" y2=\"261.439\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"69\" x=\"306\" y=\"256.5825\">&#54392;&#49884; &#47700;&#49884;&#51648;</text><polygon fill=\"#181818\" points=\"87,289.2949,77,293.2949,87,297.2949,83,293.2949\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"81\" x2=\"288\" y1=\"293.2949\" y2=\"293.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"69\" x=\"93\" y=\"288.4385\">&#54392;&#49884; &#47700;&#49884;&#51648;</text><!--SRC=[RP11IyCm68RFpQ_us5rwzo0epZ4GhQn_84q_MN2B9Kc78C9W7aHFGdSPxK4GP9wAUF3Y7rhI_s3MLjc6foJV-txF-n9rnKL29Hr3Z9Sq7UcJQw7Fw1ZXjDVjXtYZYPCrPpoXGaCdS0-14WOe9vnX1wY2f9bj6yCX5nTmb2ekK2au3FgrDsBRjcFymyJrbT2H1Zjx0FE-D2-5BJwXcj_RHLRDSrXzVDj5IS1h8s7lm17teTSDmM_sbLCfqtn2DQxJF8awbG9CbfaoSpZx-Dgo2OgOx922yu539QaQ-hSDi1_V-IgD59CySkqsq2rPedB_LlUkdh_iKmvccRd3larNvHHCcTjPiT7UQxY_YRixn8lOMckB_MDmjNy0]--></g></svg>\n\n## DR 서비스 사용자 등록\nB2B 파트너는 사전에 LG전자의 API 관리자와 협의한 이후 DR API를 사용해 DR 서비스를 위한 사용자를 등록할 수 있습니다. LG전자 사용자와 디바이스는 다음의 순서에 따라 DR 서비스에 등록됩니다.\n\n\n  - 사용 API\n    - [`POST /dr/users`](#tag/DR-API/operation/createDrUser)\n\n  - 시퀀스\n    1. LG전자 사용자는 LG ThinQ 서비스에 가입해 있으며 파트너의 DR 서비스에 가입할 LG 가전제품을 등록한 상태여야 합니다.\n    2. LG전자 사용자는 B2B 파트너의 DR 서비스에 대한 가입을 시도합니다.\n    3. 파트너 서비스는 LMP(LGE Members Platform)의 OAuth 2.0 연동 절차에 따라 LG전자의 로그인 화면을 DR 서비스에서 제공하고 OAuth 연동 정보를 획득합니다.\n    4. LG전자의 DR 서비스는 파트너 서비스와 사전에 정의한 연동 인터페이스에 따라 파트너 서비스 측 OAuth 연동 정보를 획득한 후, 파트너 서비스의 사용자 정보 API를 조회한 결과를 저장합니다. \n    5. LG전자 사용자가 LG ThinQ 모바일 앱에서 DR 서비스에 등록할 홈과 디바이스를 지정하면 LG전자의 DR 서비스가 해당 디바이스를 DR 대상 디바이스로 등록합니다.\n\n    <?xml version=\"1.0\" encoding=\"us-ascii\" standalone=\"no\"?><svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" contentStyleType=\"text/css\" height=\"698px\" preserveAspectRatio=\"none\" style=\"width:819px;height:698px;background:#FFFFFF;\" version=\"1.1\" viewBox=\"0 0 819 698\" width=\"819px\" zoomAndPan=\"magnify\"><defs/><g><rect fill=\"#DDDDDD\" height=\"686.2983\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"223\" x=\"150.5\" y=\"6\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"99\" x=\"212.5\" y=\"20.9995\">Partner Service</text><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"266\" y=\"436.645\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"337.5\" y=\"372.9331\"/><rect fill=\"#FFFFFF\" height=\"40.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"427\" y=\"560.2129\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"574.5\" y=\"213.6533\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"574.5\" y=\"277.3652\"/><rect fill=\"#FFFFFF\" height=\"141.4238\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"739\" y=\"341.0771\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"37\" x2=\"37\" y1=\"84.2295\" y2=\"610.0688\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"190.5\" x2=\"190.5\" y1=\"84.2295\" y2=\"610.0688\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"270.5\" x2=\"270.5\" y1=\"84.2295\" y2=\"610.0688\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"342.5\" x2=\"342.5\" y1=\"84.2295\" y2=\"610.0688\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"431.5\" x2=\"431.5\" y1=\"84.2295\" y2=\"610.0688\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"579.5\" x2=\"579.5\" y1=\"84.2295\" y2=\"610.0688\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"743.5\" x2=\"743.5\" y1=\"84.2295\" y2=\"610.0688\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"59\" x=\"5\" y=\"81.1533\">End-User</text><ellipse cx=\"37.5\" cy=\"13.5\" fill=\"#E2E2F0\" rx=\"8\" ry=\"8\" style=\"stroke:#181818;stroke-width:0.5;\"/><path d=\"M37.5,21.5 L37.5,48.5 M24.5,29.5 L50.5,29.5 M37.5,48.5 L24.5,63.5 M37.5,48.5 L50.5,63.5 \" fill=\"none\" style=\"stroke:#181818;stroke-width:0.5;\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"59\" x=\"5\" y=\"625.2222\">End-User</text><ellipse cx=\"37.5\" cy=\"636.7983\" fill=\"#E2E2F0\" rx=\"8\" ry=\"8\" style=\"stroke:#181818;stroke-width:0.5;\"/><path d=\"M37.5,644.7983 L37.5,671.7983 M24.5,652.7983 L50.5,652.7983 M37.5,671.7983 L24.5,686.7983 M37.5,671.7983 L50.5,686.7983 \" fill=\"none\" style=\"stroke:#181818;stroke-width:0.5;\"/><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"72\" x=\"154.5\" y=\"50\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"58\" x=\"161.5\" y=\"73.1533\">Frontend</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"72\" x=\"154.5\" y=\"609.0688\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"58\" x=\"161.5\" y=\"632.2222\">Frontend</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"69\" x=\"236.5\" y=\"50\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"55\" x=\"243.5\" y=\"73.1533\">Backend</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"69\" x=\"236.5\" y=\"609.0688\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"55\" x=\"243.5\" y=\"632.2222\">Backend</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"54\" x=\"315.5\" y=\"50\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"40\" x=\"322.5\" y=\"73.1533\">OAuth</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"54\" x=\"315.5\" y=\"609.0688\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"40\" x=\"322.5\" y=\"632.2222\">OAuth</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"105\" x=\"379.5\" y=\"50\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"91\" x=\"386.5\" y=\"73.1533\">LG ThinQ App</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"105\" x=\"379.5\" y=\"609.0688\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"91\" x=\"386.5\" y=\"632.2222\">LG ThinQ App</text><rect fill=\"#E2E2F0\" height=\"52.459\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"170\" x=\"494.5\" y=\"30.7705\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"72\" x=\"543.5\" y=\"53.9238\">LMP OAuth</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"156\" x=\"501.5\" y=\"73.1533\">(LGE Members Platform)</text><rect fill=\"#E2E2F0\" height=\"52.459\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"170\" x=\"494.5\" y=\"609.0688\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"72\" x=\"543.5\" y=\"632.2222\">LMP OAuth</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"156\" x=\"501.5\" y=\"651.4517\">(LGE Members Platform)</text><rect fill=\"#E2E2F0\" height=\"52.459\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"674.5\" y=\"30.7705\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"681.5\" y=\"53.9238\">ThinQ Business API</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"81\" x=\"703.5\" y=\"73.1533\">(DR Service)</text><rect fill=\"#E2E2F0\" height=\"52.459\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"674.5\" y=\"609.0688\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"681.5\" y=\"632.2222\">ThinQ Business API</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"81\" x=\"703.5\" y=\"651.4517\">(DR Service)</text><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"266\" y=\"436.645\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"337.5\" y=\"372.9331\"/><rect fill=\"#FFFFFF\" height=\"40.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"427\" y=\"560.2129\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"574.5\" y=\"213.6533\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"574.5\" y=\"277.3652\"/><rect fill=\"#FFFFFF\" height=\"141.4238\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"739\" y=\"341.0771\"/><polygon fill=\"#181818\" points=\"420,114.0854,430,118.0854,420,122.0854,424,118.0854\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"37.5\" x2=\"426\" y1=\"118.0854\" y2=\"118.0854\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"238\" x=\"44.5\" y=\"113.229\">&#46356;&#48148;&#51060;&#49828; &#46321;&#47197; : Air Conditioner, ESS, TV</text><polygon fill=\"#181818\" points=\"178.5,145.9414,188.5,149.9414,178.5,153.9414,182.5,149.9414\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"37.5\" x2=\"184.5\" y1=\"149.9414\" y2=\"149.9414\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"104\" x=\"44.5\" y=\"145.085\">DR &#49436;&#48708;&#49828;&#50640; &#44032;&#51077;</text><polygon fill=\"#181818\" points=\"48.5,177.7974,38.5,181.7974,48.5,185.7974,44.5,181.7974\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"42.5\" x2=\"189.5\" y1=\"181.7974\" y2=\"181.7974\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"129\" x=\"54.5\" y=\"176.9409\">LG&#51204;&#51088; &#47196;&#44536;&#51064; &#54168;&#51060;&#51648;</text><polygon fill=\"#181818\" points=\"562.5,209.6533,572.5,213.6533,562.5,217.6533,566.5,213.6533\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"37.5\" x2=\"568.5\" y1=\"213.6533\" y2=\"213.6533\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"116\" x=\"44.5\" y=\"208.7969\">LG&#51204;&#51088; &#44228;&#51221; &#47196;&#44536;&#51064;</text><polygon fill=\"#181818\" points=\"282,241.5093,272,245.5093,282,249.5093,278,245.5093\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"276\" x2=\"578.5\" y1=\"245.5093\" y2=\"245.5093\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"106\" x=\"288\" y=\"240.6528\">authorization code</text><polygon fill=\"#181818\" points=\"562.5,273.3652,572.5,277.3652,562.5,281.3652,566.5,277.3652\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"271\" x2=\"568.5\" y1=\"277.3652\" y2=\"277.3652\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"108\" x=\"278\" y=\"272.5088\">access token &#50836;&#52397;</text><polygon fill=\"#181818\" points=\"282,305.2212,272,309.2212,282,313.2212,278,309.2212\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"276\" x2=\"578.5\" y1=\"309.2212\" y2=\"309.2212\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"78\" x=\"288\" y=\"304.3647\">access token</text><polygon fill=\"#181818\" points=\"727,337.0771,737,341.0771,727,345.0771,731,341.0771\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"271\" x2=\"733\" y1=\"341.0771\" y2=\"341.0771\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"171\" x=\"278\" y=\"336.2207\">&#49324;&#50857;&#51088; &#49373;&#49457; (POST /dr/users)</text><polygon fill=\"#181818\" points=\"358.5,368.9331,348.5,372.9331,358.5,376.9331,354.5,372.9331\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"352.5\" x2=\"738\" y1=\"372.9331\" y2=\"372.9331\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"151\" x=\"364.5\" y=\"368.0767\">access/refresh token &#50836;&#52397;</text><polygon fill=\"#181818\" points=\"727,400.7891,737,404.7891,727,408.7891,731,404.7891\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"342.5\" x2=\"733\" y1=\"404.7891\" y2=\"404.7891\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"121\" x=\"349.5\" y=\"399.9326\">access/refresh token</text><polygon fill=\"#181818\" points=\"287,432.645,277,436.645,287,440.645,283,436.645\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"281\" x2=\"738\" y1=\"436.645\" y2=\"436.645\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"99\" x=\"293\" y=\"431.7886\">&#49324;&#50857;&#51088; &#51221;&#48372; &#50836;&#52397;</text><polygon fill=\"#181818\" points=\"727,464.501,737,468.501,727,472.501,731,468.501\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"271\" x2=\"733\" y1=\"468.501\" y2=\"468.501\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"69\" x=\"278\" y=\"463.6445\">&#49324;&#50857;&#51088; &#51221;&#48372;</text><polygon fill=\"#181818\" points=\"282,478.501,272,482.501,282,486.501,278,482.501\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"276\" x2=\"743\" y1=\"482.501\" y2=\"482.501\"/><polygon fill=\"#181818\" points=\"201.5,492.501,191.5,496.501,201.5,500.501,197.5,496.501\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"195.5\" x2=\"270\" y1=\"496.501\" y2=\"496.501\"/><polygon fill=\"#181818\" points=\"48.5,524.3569,38.5,528.3569,48.5,532.3569,44.5,528.3569\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"42.5\" x2=\"189.5\" y1=\"528.3569\" y2=\"528.3569\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"72\" x=\"54.5\" y=\"523.5005\">LG ThinQ &#50545;</text><polygon fill=\"#181818\" points=\"415,556.2129,425,560.2129,415,564.2129,419,560.2129\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"37.5\" x2=\"421\" y1=\"560.2129\" y2=\"560.2129\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"164\" x=\"44.5\" y=\"555.3564\">DR &#45824;&#49345; &#54856;&#44284; &#46356;&#48148;&#51060;&#49828; &#49440;&#53469;</text><polygon fill=\"#181818\" points=\"732,588.0688,742,592.0688,732,596.0688,736,592.0688\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"437\" x2=\"738\" y1=\"592.0688\" y2=\"592.0688\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"134\" x=\"444\" y=\"587.2124\">DR &#45824;&#49345; &#54856;&#44284; &#46356;&#48148;&#51060;&#49828;</text><!--SRC=[XL91QnD15BxFhtZarDA67Bpr8AIQba9hLnCzUPdiJCZGxEmoEod5KpGhY8WKJ51BKr8GH51eJC4A_gBiv3_uPj8akodeddPclkzxxttVYu-4ZAYY0J3UeEsMtWcbVaG33lkxbRqQFz64-ZfKKAX8LdmQSrK06aCRVqWzF862HvMMN46LgsFXym81_51H2rz4L6eex2YKv98vuZt56lPy5xPD_QCCgex7kw33Sbitvn1t8CW1x8JaSFkxK6iA-HZAKUJWD8e0LZ077ZY9vt8DXuK37jIvYi5hKTq8LR3kYAqWojDckjljM4WUnr3szf3_yCdSW1cBAKAiHr2yxqflGThhfLSzCxWsRxz0-c6KNWxmjYmKF0Wb4rg4wE8cLAhLJQWzMv3dVY4MQvZaFFsTe8BvU0gJguwvU4qMY2B27MqBipF3n5oSGdfvFlbrOmOtC7t_oHR_sbb8usHPw6ISc65_oR2vYsEgkRF0WekpVcmoIAJeNAZ42sfR1pzad32UuyonireR6vRa-zOq7MBKOCvwvkSFehXkAvbx8bakKuvgNdqtPzzifwOxCCa8rhp3QWrAJ9NiHF4wONF7NAgPUYN56uh7pN_KpKEMKhQ9rVB3VZg-Nb5PVRwzNywHoJ8JMIQnsuKr_L5sSrnjJ3vzrp7Tbp3z_6Oo_fDV9fCCfzq1iMlctFeVuIy0]--></g></svg>\n\n\n## DR 이벤트 생성 및 모니터링 데이터 다운로드\nDR 이벤트를 등록하고 DR 이벤트 전후의 디바이스의 모니터링 데이터를 다운로드하는 과정을 설명합니다.\n\n  - 사용 API\n    - [`POST /dr/events`](#tag/DR-API/operation/createDrEvent)\n    - [`POST /dr/events/{eventId}/targets`](#tag/DR-API/operation/createEventTarget)\n    - [`POST /dr/events/{eventId}/targets/{targetId}`](#tag/DR-API/operation/updateEventTarget)\n    - [`POST /dr/events/{eventId}/targets/batch`](#tag/DR-API/operation/createEventTargetBatch)\n    - [`POST /dr/events/{eventId}/targets/batch`](#tag/DR-API/operation/createEventTargetBatch)\n    - [`POST /dr/data-zip/files`](#tag/DR-API/operation/createDataZipFile)\n    - [`POST /dr/data-zip/files/{filename}`](#tag/DR-API/operation/downloadDataZipFile)\n\n  - 시퀀스\n    1. LG DR 서비스 서버에 DR 이벤트를 등록하기 위해 DR 이벤트 생성 API (POST /dr/events)를 호출합니다.\n    2. DR 이벤트가 정상적으로 등록되면, DR 이벤트 ID(eventId)를 반환합니다.\n    3. 만약 DR 이벤트 생성 후에 해당 DR 이벤트에 참여 필요한 디바이스 목록 변경이 필요한 경우 DR 이벤트 타깃 변경 API를 호출합니다.\n    4. DR 이벤트가 종료된 후 DR 이벤트 기간 내 대상 디바이스의 모니터링 데이터를 다운로드 받습니다.\n\n    <?xml version=\"1.0\" encoding=\"us-ascii\" standalone=\"no\"?><svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" contentStyleType=\"text/css\" height=\"760px\" preserveAspectRatio=\"none\" style=\"width:517px;height:760px;background:#FFFFFF;\" version=\"1.1\" viewBox=\"0 0 517 760\" width=\"517px\" zoomAndPan=\"magnify\"><defs/><g><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"119.1709\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"209.8477\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"290.6685\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"371.4893\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"519.166\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"582.8779\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"463.5\" y=\"646.5898\"/><rect fill=\"none\" height=\"342.8862\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"435.5\" x=\"10\" y=\"75.459\"/><rect fill=\"none\" height=\"245.3184\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"415.5\" x=\"20\" y=\"166.0269\"/><rect fill=\"none\" height=\"210.9917\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"491.5\" x=\"20\" y=\"475.4541\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"86\" x2=\"86\" y1=\"58.459\" y2=\"425.3452\"/><line style=\"stroke:#A80036;stroke-width:1.0;stroke-dasharray:1.0,4.0;\" x1=\"86\" x2=\"86\" y1=\"425.3452\" y2=\"468.4541\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"86\" x2=\"86\" y1=\"468.4541\" y2=\"703.4458\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"355.5\" x2=\"355.5\" y1=\"58.459\" y2=\"425.3452\"/><line style=\"stroke:#A80036;stroke-width:1.0;stroke-dasharray:1.0,4.0;\" x1=\"355.5\" x2=\"355.5\" y1=\"425.3452\" y2=\"468.4541\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"355.5\" x2=\"355.5\" y1=\"468.4541\" y2=\"703.4458\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"468.5\" x2=\"468.5\" y1=\"58.459\" y2=\"425.3452\"/><line style=\"stroke:#A80036;stroke-width:1.0;stroke-dasharray:1.0,4.0;\" x1=\"468.5\" x2=\"468.5\" y1=\"425.3452\" y2=\"468.4541\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"468.5\" x2=\"468.5\" y1=\"468.4541\" y2=\"703.4458\"/><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"30\" y=\"24.2295\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"37\" y=\"47.3828\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"30\" y=\"702.4458\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"37\" y=\"725.5991\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"52.459\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"286.5\" y=\"5\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"293.5\" y=\"28.1533\">ThinQ Business API</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"81\" x=\"315.5\" y=\"47.3828\">(DR Service)</text><rect fill=\"#E2E2F0\" height=\"52.459\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"286.5\" y=\"702.4458\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"293.5\" y=\"725.5991\">ThinQ Business API</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"81\" x=\"315.5\" y=\"744.8286\">(DR Service)</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"66\" x=\"435.5\" y=\"24.2295\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"52\" x=\"442.5\" y=\"47.3828\">AWS S3</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"66\" x=\"435.5\" y=\"702.4458\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"52\" x=\"442.5\" y=\"725.5991\">AWS S3</text><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"119.1709\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"209.8477\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"290.6685\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"371.4893\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"519.166\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"582.8779\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"463.5\" y=\"646.5898\"/><path d=\"M10,75.459 L151,75.459 L151,85.3149 L141,95.3149 L10,95.3149 L10,75.459 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"342.8862\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"435.5\" x=\"10\" y=\"75.459\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"96\" x=\"25\" y=\"91.4585\">DR &#51060;&#48292;&#53944; &#49373;&#49457;</text><polygon fill=\"#181818\" points=\"339,115.1709,349,119.1709,339,123.1709,343,119.1709\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"86\" x2=\"345\" y1=\"119.1709\" y2=\"119.1709\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"95\" x=\"93\" y=\"114.3145\">POST /dr/events</text><polygon fill=\"#181818\" points=\"97,147.0269,87,151.0269,97,155.0269,93,151.0269\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"91\" x2=\"355\" y1=\"151.0269\" y2=\"151.0269\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"32\" x=\"103\" y=\"146.1704\">result</text><path d=\"M20,166.0269 L81,166.0269 L81,175.8828 L71,185.8828 L20,185.8828 L20,166.0269 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"245.3184\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"415.5\" x=\"20\" y=\"166.0269\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"16\" x=\"35\" y=\"182.0264\">alt</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"200\" x=\"96\" y=\"180.7188\">[&#51060;&#48292;&#53944; &#53440;&#44191;&#51060; &#52628;&#44032;&#46104;&#50612;&#50556; &#54616;&#45716; &#44221;&#50864;]</text><polygon fill=\"#181818\" points=\"339,205.8477,349,209.8477,339,213.8477,343,209.8477\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"86\" x2=\"345\" y1=\"209.8477\" y2=\"209.8477\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"191\" x=\"93\" y=\"204.9912\">POST /dr/events/{eventId}/targets</text><polygon fill=\"#181818\" points=\"97,237.7036,87,241.7036,97,245.7036,93,241.7036\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"91\" x2=\"355\" y1=\"241.7036\" y2=\"241.7036\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"32\" x=\"103\" y=\"236.8472\">result</text><line style=\"stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"20\" x2=\"435.5\" y1=\"250.7036\" y2=\"250.7036\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"227\" x=\"25\" y=\"263.3955\">[&#53945;&#51221; &#51060;&#48292;&#53944; &#53440;&#44191;&#51060; &#49688;&#51221;&#46104;&#50612;&#50556; &#54616;&#45716; &#44221;&#50864;]</text><polygon fill=\"#181818\" points=\"339,286.6685,349,290.6685,339,294.6685,343,290.6685\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"86\" x2=\"345\" y1=\"290.6685\" y2=\"290.6685\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"246\" x=\"93\" y=\"285.812\">POST /dr/events/{eventId}/targets/{targetId}</text><polygon fill=\"#181818\" points=\"97,318.5244,87,322.5244,97,326.5244,93,322.5244\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"91\" x2=\"355\" y1=\"322.5244\" y2=\"322.5244\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"32\" x=\"103\" y=\"317.668\">result</text><line style=\"stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"20\" x2=\"435.5\" y1=\"331.5244\" y2=\"331.5244\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"227\" x=\"25\" y=\"344.2163\">[&#51060;&#48292;&#53944; &#53440;&#44191;&#51060; &#51068;&#44292; &#49373;&#49457;&#46104;&#50612;&#50556; &#54616;&#45716; &#44221;&#50864;]</text><polygon fill=\"#181818\" points=\"339,367.4893,349,371.4893,339,375.4893,343,371.4893\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"86\" x2=\"345\" y1=\"371.4893\" y2=\"371.4893\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"227\" x=\"93\" y=\"366.6328\">POST /dr/events/{eventId}/targets/batch</text><polygon fill=\"#181818\" points=\"97,399.3452,87,403.3452,97,407.3452,93,403.3452\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"91\" x2=\"355\" y1=\"403.3452\" y2=\"403.3452\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"32\" x=\"103\" y=\"398.4888\">result</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" lengthAdjust=\"spacing\" textLength=\"93\" x=\"232.25\" y=\"452.0371\">&lt; DR &#51060;&#48292;&#53944; &#49892;&#54665; &gt;</text><path d=\"M20,475.4541 L227,475.4541 L227,485.3101 L217,495.3101 L20,495.3101 L20,475.4541 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"210.9917\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"491.5\" x=\"20\" y=\"475.4541\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"162\" x=\"35\" y=\"491.4536\">&#47784;&#45768;&#53552;&#47553; &#45936;&#51060;&#53552; &#45796;&#50868;&#47196;&#46300;</text><polygon fill=\"#181818\" points=\"339,515.166,349,519.166,339,523.166,343,519.166\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"86\" x2=\"345\" y1=\"519.166\" y2=\"519.166\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"131\" x=\"93\" y=\"514.3096\">POST /dr/data-zip/files</text><polygon fill=\"#181818\" points=\"97,547.022,87,551.022,97,555.022,93,551.022\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"91\" x2=\"355\" y1=\"551.022\" y2=\"551.022\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"39\" x=\"103\" y=\"546.1655\">&#54028;&#51068;&#47749;</text><polygon fill=\"#181818\" points=\"339,578.8779,349,582.8779,339,586.8779,343,582.8779\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"86\" x2=\"345\" y1=\"582.8779\" y2=\"582.8779\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"191\" x=\"93\" y=\"578.0215\">POST /dr/data-zip/files/{filename}</text><polygon fill=\"#181818\" points=\"97,610.7339,87,614.7339,97,618.7339,93,614.7339\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"91\" x2=\"355\" y1=\"614.7339\" y2=\"614.7339\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"112\" x=\"103\" y=\"609.8774\">&#54028;&#51068; &#45796;&#50868;&#47196;&#46300; &#51221;&#48372;</text><polygon fill=\"#181818\" points=\"451.5,642.5898,461.5,646.5898,451.5,650.5898,455.5,646.5898\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"86\" x2=\"457.5\" y1=\"646.5898\" y2=\"646.5898\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"82\" x=\"93\" y=\"641.7334\">&#54028;&#51068; &#45796;&#50868;&#47196;&#46300;</text><polygon fill=\"#181818\" points=\"97,674.4458,87,678.4458,97,682.4458,93,678.4458\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"91\" x2=\"467.5\" y1=\"678.4458\" y2=\"678.4458\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"26\" x=\"103\" y=\"673.5894\">&#54028;&#51068;</text><!--SRC=[jLFBIiD05DtdAowk5B5PT2SYA3ueY5PJSEDcR4ORJASXCorY4HGhQ5j1i2r5B2eKbAvY3Q9GVoWp-GUdQGlM1XyB0yFDVPmpPoOdTCyW5h9H6dIyWx8cMyeGjehI65QM5sC9lCyKsMP6qh0GOJ0Mbmd1DcZOpXb9F0Q8WjMh3GycKWPPX_aiDGYc5ERYiIqolh0n04u4IFqBQ6vJ0oqQj6XKKNRjJDO22H8DbxURVl4Ln4b359uKa4z_MvYQbJoJap0DyJKj0QfkgpY72QF1b8rPrYOoK7cue89CzedGFpdoshSo1_5IyPmZVbaNDLTKE-1NwxnO0Q_zBgwT0FchNTLy46FweSgGlOlxEiArO9DYy8jluguQhkciBbl_e4dDzrvawITveReQ7SyjzB_6VyZRHYoP-auPqPNkKYAH2CnyyKYfwTVEOLQs1XxYhKTUElCB3dyu1dxXo66P02yrnRNBxs_urSrFdj8HGrC7XgNk62OUyfPVBilxuArJvMySQhuRYFpP3aVfXhH1rmJFxWW_ZGRy8OXHmk2wFW00]--></g></svg>\n"
      - name: Base URL
        description: |
          ThinQ Business API는 고객의 디바이스의 위치에 따라 Base URL을 구분하고 있습니다.  따라서 고객의 디바이스가 위치하는 지역 또는 B2B 파트너의 비지니스가 진행 중인 지역을 고려해, API 호출 시 Base URL을 선택해 적용해주십시오.  그리고 아래와 같이 Production 환경과 Simulator Testing 환경을 위한 Base URL이 구분되어 있으니 참고하시기를 바랍니다.  
          ## Production 환경
          Production 환경에서 **Business API Key**를 활용해 ThinQ Business API를 호출하려면 아래의 Base URL을 사용해주십시오.

            |Region|API Token 발급 API|ThinQ Business API|
            |-|-|-|
            |South Asia, East Asia and Pacific|https://ap.biz.api.lge.com|https://ap.biz.api.lge.com/v1|
            |America|https://us.biz.api.lge.com|https://us.biz.api.lge.com/v1|
            |Europe, Middle East, Africa|https://eu.biz.api.lge.com|https://eu.biz.api.lge.com/v1|

            
          ## Simulator Testing 환경
          Simulator Testing 환경에서 **Test API Key**를 활용해 ThinQ Business API를 호출하기 위해 아래의 Base URL을 사용해주십시오.

            |Region|API Token 발급 API|ThinQ Business API|
            |-|-|-|
            |South Asia, East Asia and Pacific|https://ap-test.biz.api.lge.com|https://ap-test.biz.api.lge.com/v1|
            |America|https://us-test.biz.api.lge.com|https://us-test.biz.api.lge.com/v1|
            |Europe, Middle East, Africa|https://eu-test.biz.api.lge.com|https://eu-test.biz.api.lge.com/v1|      
           
      - name: Codes
        x-displayName: 코드 정의
        description: |
          ThinQ Business API를 활용할 때 참고할 수 있는 코드 유형을 설명합니다. 
          ## 국가 코드
          ThinQ Business API 호출에서 사용하는 국가 코드는 `ISO-3166 alpha-2` 규격을 지원하며 LG ThinQ 서비스를 지원하는 국가에서 사용할 수 있습니다.  지원하는 국가 코드는 아래 표와 같습니다.

            ### South Asia, East Asia and Pacific

            | Code | Name       | Code | Name       | Code | Name       | Code | Name       | Code | Name       | Code | Name       | Code | Name       | Code | Name       |
            |------|------------|------|------------|------|------------|------|------------|------|------------|------|------------|------|------------|------|------------|
            | AU   | 호주       | BD   | 방글라데시 | CN   | 중국       | HK   | 홍콩       | ID   | 인도네시아 | IN   | 인도       | JP   | 일본       | KR   | 대한민국   |
            | LA   | 라오스     | MY   | 말레이시아 | NP   | 네팔       | NZ   | 뉴질랜드   | PH   | 필리핀     | SG   | 싱가포르   | TH   | 태국       | TW   | 대만       |
            | VN   | 베트남     | MM   | 미얀마     | KH   | 캄보디아   | LK   | 스리랑카   |      |            |      |            |      |            |      |            |
            
            ### America

            | Code | Name                | Code | Name                | Code | Name                | Code | Name                | Code | Name                | Code | Name                | Code | Name                | Code | Name                |
            |------|---------------------|------|---------------------|------|---------------------|------|---------------------|------|---------------------|------|---------------------|------|---------------------|------|---------------------|
            | AG   | 앤티가 바부다       | AR   | 아르헨티나          | AW   | 아루바              | BB   | 바베이도스          | BO   | 볼리비아            | BR   | 브라질              | BS   | 바하마              | BZ   | 벨리즈              |
            | CA   | 캐나다              | CL   | 칠레                | CO   | 콜롬비아            | CR   | 코스타리카          | CU   | 쿠바                | DM   | 도미니카            | DO   | 도미니카 공화국     | EC   | 에콰도르            |
            | GD   | 그레나다            | GT   | 과테말라            | GY   | 가이아나            | HN   | 온두라스            | HT   | 아이티              | JM   | 자메이카            | KN   | 세인트키츠 네비스   | LC   | 세인트루시아        |
            | MX   | 멕시코              | NI   | 니카라과            | PA   | 파나마              | PE   | 페루                | PR   | 푸에르토리코        | PY   | 파라과이            | SR   | 수리남              | SV   | 엘살바도르          |
            | TT   | 트리니다드 섬       | US   | 미국                | UY   | 우루과이            | VC   | 세인트빈센트 그레나딘 | VE   | 베네수엘라          |      |                     |      |                     |      |                     |

            ### Europe, Middle East, Africa

            | Code | Name                | Code | Name                | Code | Name                | Code | Name                | Code | Name                | Code | Name                | Code | Name                | Code | Name                |
            |------|---------------------|------|---------------------|------|---------------------|------|---------------------|------|---------------------|------|---------------------|------|---------------------|------|---------------------|
            | AE   | 아랍에미리트        | AF   | 아프가니스탄        | AL   | 알바니아            | AM   | 아르메니아          | AO   | 앙골라              | AT   | 오스트리아          | AZ   | 아제르바이잔        | BA   | 보스니아 헤르체고비나 |
            | BE   | 벨기에              | BF   | 부르키나파소        | BG   | 불가리아            | BH   | 바레인              | BJ   | 베냉                | BY   | 벨라루스            | CD   | 콩고 민주공화국     | CF   | 중앙아프리카공화국  |
            | CG   | 콩고                | CH   | 스위스              | CI   | 코트디부아르        | CM   | 카메룬              | CV   | 카보베르데          | CY   | 키프로스            | CZ   | 체코                | DE   | 독일                |
            | DJ   | 지부티              | DK   | 덴마크              | DZ   | 알제리              | EE   | 에스토니아          | EG   | 이집트              | ES   | 스페인              | ET   | 이디오피아          | FI   | 핀란드              |
            | FR   | 프랑스              | GA   | 가봉                | GB   | 영국                | GE   | 조지아              | GH   | 가나                | GM   | 감비아              | GN   | 기니                | GQ   | 적도 기니           |
            | GR   | 그리스              | HR   | 크로아티아          | HU   | 헝가리              | IE   | 아일랜드            | IL   | 이스라엘            | IQ   | 이라크              | IR   | 이란                | IS   | 아이슬란드          |
            | IT   | 이탈리아            | JO   | 요르단              | KE   | 케냐                | KG   | 키르기스스탄        | KW   | 쿠웨이트            | KZ   | 카자흐스탄          | LB   | 레바논              | LR   | 라이베리아          |
            | LT   | 리투아니아          | LU   | 룩셈부르크          | LV   | 라트비아            | LY   | 리비아              | MA   | 모로코              | MD   | 몰도바              | ME   | 몬테네그로          | MK   | 마케도니아          |
            | ML   | 말리                | MR   | 모리타니아          | MT   | 몰타                | MU   | 모리셔스            | MW   | 말라위              | NE   | 니제르              | NG   | 나이지리아          | NL   | 네덜란드            |
            | NO   | 노르웨이            | OM   | 오만                | PK   | 파키스탄            | PL   | 폴란드              | PS   | 팔레스타인          | PT   | 포르투갈            | QA   | 카타르              | RO   | 루마니아            |
            | RS   | 세르비아            | RW   | 르완다              | SA   | 사우디아라비아      | SD   | 수단                | SE   | 스웨덴              | SI   | 슬로베니아          | SK   | 슬로바키아          | SL   | 시에라리온          |
            | SN   | 세네갈              | SO   | 소말리아            | ST   | 상투메 프린시페     | SY   | 시리아              | TD   | 차드                | TG   | 토고                | TN   | 튀니지              | TR   | 터키                |
            | TZ   | 탄자니아            | UA   | 우크라이나          | UG   | 우간다              | UZ   | 우즈베키스탄        | XK   | 코소보              | YE   | 예멘                | ZA   | 남아프리카 공화국   | ZM   | 잠비아              |
            | RU   | 러시아              |      |                     |      |                     |      |                     |      |                     |      |                     |      |                     |      |                     |


          ## 응답 코드
          각 API를 호출하면 HTTP 상태 코드와 함께 응답 유형을 부가적으로 설명하는 응답 코드가 함께 반환될 수 있습니다.  이 응답 코드는 HTTP 응답 헤더와 응답 바디의 메시지에 포함되어 있으며 API의 종류별로 그 정의는 다를 수 있습니다.  API의 종류별로 지원하는 응답 코드는 아래와 같습니다.

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
                  <td>정상 응답 스키마의 데이터</td>
                </tr>
                <tr>
                  <td><code>206</code></td>
                  <td><code>6201</code> : Partial Success</td>
                  <td>정상 응답 스키마의 데이터</td>
                </tr>
                <tr>
                  <td><code>400</code></td>
                  <td><code>6400</code> : Bad Request</td>
                  <td>
                      에러 응답 스키마의 <code>code</code> 필드 :<br>
                      <code>1000</code> : 잘못된 요청 <br>
                      <code>1101</code> : 필수 입력 항목이 누락됨 <br>
                      <code>1102</code> : 허용하지 않는 파라미터들이 입력됨 <br>
                      <code>1104</code> : 메시지 ID의 문법이 잘못됨 <br>
                      <code>1216</code> : 헤더에 포함된 값이 올바르지 않음 <br>
                      <code>1217</code> : 해당 디바이스가 삭제되었음 <br> 
                      <code>1218</code> : 유효하지 않은 토큰임 <br> 
                      <code>2202</code> : 지원하는 제품군이 아님 <br> 
                      <code>2205</code> : 디바이스 상태 정보가 정상적으로 전송되지 않았거나, 전송된 정보가 정상적으로 파싱되지 않았을 경우 <br> 
                      <code>2207</code> : 유효하지 않은 제어 명령일 때 (제어 명령에 정의되지 않은 resource, property 가 포함된 경우) <br> 
                      <code>2208</code> : 디바이스 제어 실패 <br> 
                      <code>2209</code> : 디바이스 응답 지연 <br> 
                      <code>2210</code> : 상태조회 재요청 필요 <br>
                      <code>2214</code> : 요청 실패 <br>
                      <code>2301</code> : 지원하는 제어 명령이 없는 디바이스의 경우 (remoteControl이 false일 때)  <br>
                      <code>2302</code> : 해당 STATE에서는 해당 제어 명령을 지원하지 않음 (ex: "Command not supported in HEAT (2302)")<br>
                      <code>2303</code> : 디바이스가 에러 상태여서 제어가 불가능한 경우 <br>
                      <code>2304</code> : 디바이스 전원이 꺼져있어서 제어가 불가능한 경우 <br>
                      <code>2305</code> : 해당 MODE에서는 해당 제어 명령을 지원하지 않음 (ex: "Command not supported in STANDBY (2305)") <br>
                  </td>
                </tr>
                <tr>
                  <td><code>401</code></td>
                  <td><code>6401</code> : Unauthorized</td>
                  <td>
                      에러 응답 스키마의 <code>code</code> 필드 :<br>
                      <code>1307</code> : 지원하지 않는 국가 <br>
                      <code>1308</code> : 디바이스 제어권 없음 (ThinQ App에서 사용중) <br>
                      <code>1311</code> : 요청 포맷이 잘못된 경우 <br>
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
                      에러 응답 스키마의 <code>code</code> 필드 :<br>
                      <code>1202</code> : 등록된 사용자가 없음 <br>
                      <code>1204</code> : 구독된 이벤트가 없음 <br>
                      <code>1205</code> : 등록된 디바이스가 없음 <br>
                      <code>1206</code> : 구독된 푸시가 없음 <br>
                      <code>1207</code> : 등록된 푸시가 있음 (동일한 푸시가 이미 존재함) <br>
                      <code>1210</code> : 서비스가 허용하는 디바이스 아님 <br> 
                      <code>1211</code> : 사용자가 등록한 디바이스가 아님 <br> 
                      <code>1212</code> : 사용자가 가지고 있지 않은 디바이스 <br> 
                      <code>1213</code> : 등록된 디바이스가 없음 <br> 
                      <code>1214</code> : 구독을 허용하지 않는 디바이스 <br> 
                      <code>1224</code> : 허용되지 않은 디바이스 ID
                  </td>
                </tr>
                <tr>
                  <td><code>406</code></td>
                  <td><code>6406</code> : Not Supported Resource</td>
                  <td>
                      에러 응답 스키마의 <code>code</code> 필드 :<br>
                      <code>1219</code> : 지원하지 않는 제품 모델임 <br>
                      <code>1220</code> : 해당 제품 모델에서는 지원하지 않는 기능임 <br>
                      <code>1221</code> : 지원하지 않는 디바이스 타입임
                  </td>
                </tr>
                <tr>
                  <td><code>416</code></td>
                  <td><code>6416</code> : Invalid Device Status</td>
                  <td>
                      에러 응답 스키마의 <code>code</code> 필드 :<br>
                      <code>1222</code> : 디바이스가 네트워크에 연결되어 있지 않음 <br>
                      <code>1223</code> : 전달된 디바이스 상태 값이 유효하지 않음
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
                      에러 응답 스키마의 <code>code</code> 필드 :<br>
                      <code>0000</code> : 정의되지 않은 에러 <br>
                      <code>2000</code> : 내부 서버 에러
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
        x-displayName: API 인증
        description: |
          LG Smart Solution API Developer가 B2B 파트너에게 제공한 API Key와 API Secret 쌍을 이용해 API Token을 주기적으로 발급하려면 아래의 API를 사용합니다.  이 API로 발급한 API Token은 모든 ThinQ Business API 호출 시 HTTP 요청 헤더에 포함해야 합니다.
      - name: Device API
        description: "등록한 디바이스의 목록을 조회하고, 특정 디바이스의 프로파일 및 상태를 조회하거나 디바이스를 제어하기 위해 Device API를 사용합니다.  기업이 구매한 다양한 LG전자 제품의 Device API를 사용하는 경우, 디바이스가 일괄 등록되어 있는 LG전자 계정이나 설치 현장의 정보를 LG Smart Solution API Developer에서 사전에 지정할 수 있습니다.  또한 LG전자 제품의 Device API를 호출할 때 특정 LG전자 사용자를 지정해 해당 사용자의 디바이스에 대한 접근을 수행할 수 있습니다.  Device API를 호출하기 위해서는 B2B 파트너 또는 그의 고객이 디바이스를 등록하는 과정을 거쳐야 합니다.  구매한 디바이스는 아래와 같이 디바이스 종류에 따라 해당 LG전자의 플랫폼의 서비스에 가입해 등록해야 합니다.\n\n |디바이스 종류|LG전자 플랫폼|\n |-|-|\n |가전제품 및 기타 IoT 디바이스|LG ThinQ (mobile app)|\n |사이니지|LG Business Cloud\_(https://lgbusinesscloud.com)|\n |상업용 HVAC|LG BECON Cloud\_(https://beconcloud.lge.com)|\n"
      - name: Push API
        description: |
          특정 디바이스 상태 변화를 B2B 파트너의 서비스가 수신하거나 수신을 해제하기 위해 Push API를 사용합니다.  이 API는 현재 LG ThinQ 등록 디바이스에 한해 제공되며 향후 다른 디바이스의 지원을 확대할 예정입니다.  B2B 파트너의 서비스가 디바이스의 상태를 수신하기 위해서는 사전에 LG Smart Solution API Developer에서 B2B 파트너 서비스의 Callback 호출 정보를 등록해야 합니다.  Callback으로 제공하는 디바이스의 상태 변화 종류는 아래와 같고, 종류별로 Callback 구독이 수행하는 조건이 다를 수 있습니다.

           | Push Type | Description | Pre-Condition |
           |-|-|-|
           | DEVICE_PUSH | 디바이스의 동작 완료, 디바이스 부품 교체 등을 알림<br> (예: 세탁 완료, 필터 교체 등) | 디바이스 푸시 메시지 구독 API 호출 |
           | DEVICE_REGISTERED | 디바이스가 추가됨 | 디바이스 목록 조회 API 호출 |
           | DEVICE_UNREGISTERED | 디바이스가 삭제됨 | 디바이스 목록 조회 API 호출 |
           | DEVICE_ALIAS_CHANGED | 디바이스의 닉네임이 변경됨 | 디바이스 목록 조회 API 호출 |

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
          B2B 파트너의 서비스에 등록한 LG전자 사용자의 정보를 관리하기 위해 User API를 사용합니다. <b>이 API는 현재 LG ThinQ 등록 디바이스에 한해 제공합니다.</b>
      - name: DR API
        description: |
          B2B 파트너가 전력 수요반응(DR: Demand Response) 사업자로서 DR 서비스 가입자인 LG전자 사용자의 디바이스를 제어하기 위해 DR API가 사용됩니다.  B2B 파트너는 이 API를 활용해 DR 가입자인 사용자를 관리할 수 있습니다.  그리고 특정 전력 피크 시간 동안 사용자의 전력 사용을 줄이거나 바꾸는 DR 이벤트를 등록하고, DR 대상 디바이스의 DR 이벤트 참여 여부를 조회할 수 있습니다.  DR 대상 디바이스는 현재 에어컨, TV에 한해 제공하며 향후 다른 제품의 지원을 확대할 예정입니다.  이 API를 활용한 DR 서비스는 다음의 절차에 따라 진행됩니다.
          ### 1. 디바이스 등록 및 DR 서비스 가입

            - LG ThinQ 사용자는 LG ThinQ 앱에 DR 대상 디바이스를 등록하고, B2B 파트너의 DR 서비스에 가입합니다.
            
            <img src="https://smartsolution.developer.lge.com/assets/images/img_DR_01.png" width="600"/>

          ### 2. DR Request 발령

            - B2B 파트너는 DR 이벤트 시작 전에 DR API로 DR 이벤트를 등록합니다.
            - LG전자는 등록된 DR 이벤트를 지정된 시작 시간에 대상 디바이스에 전달합니다.
            - LG ThinQ 사용자는 DR 이벤트 시작 전에 LG ThinQ 앱에서 알림을 수신합니다. 

              <img src="https://smartsolution.developer.lge.com/assets/images/img_DR_02.png" width="600"/>

          ### 3. 상태 모니터링

            - LG전자는 DR 이벤트를 실행하는 동안 디바이스의 상태를 모니터링해 기록합니다.
            - B2B 파트너는 DR API로 모니터링 데이터를 다운로드합니다. 

              <img src="https://smartsolution.developer.lge.com/assets/images/img_DR_03.png" width="600"/>

          ### 4. DR 서비스 정산

            - B2B 파트너는 DR API가 제공한 데이터를 기반으로 DR 가입자의 DR 참여율에 따라 정산을 실시하고 가입자들에게 정산 내역을 제공합니다.

              <img src="https://smartsolution.developer.lge.com/assets/images/img_DR_04.png" width="600"/>



            
    paths:
      /token:
        post:
          tags:
            - auth
          summary: API Token 발급
          description: |
            ThinQ Business API에 속하는 모든 API를 호출할 때 'API Key'와 'API Token'이 필요합니다.  이 API는 API Token 발급을 위해 사용되며 발급된 API Token은 **24시간** 동안 유효하므로 B2B 파트너는 새 API Token을 획득하도록 준비해야 합니다.  'API Secret'은 API Token을 발급하기 위해서만 사용합니다.
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
                B2B 파트너가 `API Key`와 한 쌍으로 획득한 비밀 문자열인 `API Secret`입니다.
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
          summary: 디바이스 목록 조회
          description: LG전자 계정에 등록한 모든 디바이스의 목록을 조회합니다.
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
          summary: 디바이스 프로파일 조회
          description: 특정 디바이스의 프로파일을 조회합니다.
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
                    냉장고:
                      $ref: '#/components/examples/refrigerator-profile-example'
                    세탁기:
                      $ref: '#/components/examples/washer-profile-example'
                    건조기:
                      $ref: '#/components/examples/dryer-profile-example'
                    에어컨:
                      $ref: '#/components/examples/air_conditioner-profile-example'
                    공기청정기:
                      $ref: '#/components/examples/air_purifier-profile-example'
                    로봇청소기:
                      $ref: '#/components/examples/robot_cleaner-profile-example'
                    오븐:
                      $ref: '#/components/examples/oven-profile-example'
                    식기세척기:
                      $ref: '#/components/examples/dish_washer-profile-example'
                    스타일러:
                      $ref: '#/components/examples/styler-profile-example'
                    정수기:
                      $ref: '#/components/examples/water_purifier-profile-example'
                    제습기:
                      $ref: '#/components/examples/dehumidifier-profile-example'
                    실링팬:
                      $ref: '#/components/examples/ceiling_fan-profile-example'
                    와인셀러:
                      $ref: '#/components/examples/wine_cellar-profile-example'
                    김치냉장고:
                      $ref: '#/components/examples/kimchi_refrigerator-profile-example'
                    홈브루:
                      $ref: '#/components/examples/home_brew-profile-example'
                    식물재배기:
                      $ref: '#/components/examples/plant_cultivator-profile-example'
                    워시타워 (세탁기):
                      $ref: '#/components/examples/washtower_washer-profile-example'
                    워시타워 (건조기):
                      $ref: '#/components/examples/washtower_dryer-profile-example'
                    워시타워:
                      $ref: '#/components/examples/washtower-profile-example'
                    쿡탑:
                      $ref: '#/components/examples/cooktop-profile-example'
                    후드:
                      $ref: '#/components/examples/hood-profile-example'
                    전자레인지:
                      $ref: '#/components/examples/microwave_oven-profile-example'
                    시스템보일러:
                      $ref: '#/components/examples/system_boiler-profile-example'
                    공기청정팬:
                      $ref: '#/components/examples/air_purifier_fan-profile-example'
                    스틱청소기:
                      $ref: '#/components/examples/stick_cleaner-profile-example'
                    온수기:
                      $ref: '#/components/examples/water_heater-profile-example'
                    워시콤보(메인):
                      $ref: '#/components/examples/main_washcombo-profile-example'
                    워시콤보(미니):
                      $ref: '#/components/examples/mini_washcombo-profile-example'
                    가습기:
                      $ref: '#/components/examples/humidifier-profile-example'
                    BECON Cloud에 등록된 시스템 에어컨의 실외기:
                      $ref: '#/components/examples/odu-profile-example'
                    BECON Cloud에 등록된 시스템 에어컨의 실내기:
                      $ref: '#/components/examples/idu-profile-example'
                    Business Cloud에 등록된 사이니지:
                      $ref: '#/components/examples/signage-profile-example'
                    스마트 모션 센서:
                      $ref: '#/components/examples/motion_sensor-profile-example'
                    스마트 온습도 센서:
                      $ref: '#/components/examples/temperature_humidity_sensor-profile-example'
                    스마트 도어 센서:
                      $ref: '#/components/examples/door_sensor-profile-example'
                    스마트 버튼:
                      $ref: '#/components/examples/button-profile-example'
                    스마트 조명 스위치:
                      $ref: '#/components/examples/light_switch-profile-example'
                    스마트 도어락:
                      $ref: '#/components/examples/door_lock-profile-example'
                    스마트 푸시풀 도어락:
                      $ref: '#/components/examples/push_pull_door_lock-profile-example'
                    스마트 플러그:
                      $ref: '#/components/examples/plug-profile-example'
                    스마트 플러그 미니:
                      $ref: '#/components/examples/plug_mini-profile-example'
                    스마트 전구(화이트):
                      $ref: '#/components/examples/bulb_white-profile-example'
                    스마트 전구(컬러):
                      $ref: '#/components/examples/bulb_color-profile-example'
                    스마트 라인 LED:
                      $ref: '#/components/examples/line_led-profile-example'
                    스마트 전동 커튼 컨트롤러:
                      $ref: '#/components/examples/curtain_ctrl-profile-example'
                    스마트 전동 블라인드:
                      $ref: '#/components/examples/blind_motor-profile-example'
                    스마트 스위치 스트립:
                      $ref: '#/components/examples/switch_strip-profile-example'
                    스마트 스타 라이트:
                      $ref: '#/components/examples/starlight-profile-example'
                    스마트 도어벨:
                      $ref: '#/components/examples/doorbell-profile-example'
                    스마트 펫 급식기:
                      $ref: '#/components/examples/pet_peeder-profile-example'
                    스마트 홈 카메라:
                      $ref: '#/components/examples/home_camera-profile-example'
                    싱크 박스:
                      $ref: '#/components/examples/sync_box-profile-example'
                    싱크 박스 서브:
                      $ref: '#/components/examples/sync_box_sub-profile-example'
                    스마트 가스 감지 센서:
                      $ref: '#/components/examples/gas_sensor-profile-example'
                    스마트 화재 감지 센서:
                      $ref: '#/components/examples/fire_sensor-profile-example'
                    스마트 누수 감지 센서:
                      $ref: '#/components/examples/water_leak_sensor-profile-example'
                    스마트 온습도계:
                      $ref: '#/components/examples/thermo_hygrometer-profile-example'
                    스마트 사이렌:
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
          summary: 디바이스 상태 조회
          description: 특정 디바이스의 상태를 조회합니다.
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
                    냉장고:
                      $ref: '#/components/examples/refrigerator-object-example'
                    세탁기:
                      $ref: '#/components/examples/washer-object-example'
                    건조기:
                      $ref: '#/components/examples/dryer-object-example'
                    에어컨:
                      $ref: '#/components/examples/air_conditioner-object-example'
                    공기청정기:
                      $ref: '#/components/examples/air_purifier-object-example'
                    로봇청소기:
                      $ref: '#/components/examples/robot_cleaner-object-example'
                    오븐:
                      $ref: '#/components/examples/oven-object-example'
                    식기세척기:
                      $ref: '#/components/examples/dish_washer-object-example'
                    스타일러:
                      $ref: '#/components/examples/styler-object-example'
                    정수기:
                      $ref: '#/components/examples/water_purifier-object-example'
                    제습기:
                      $ref: '#/components/examples/dehumidifier-object-example'
                    실링팬:
                      $ref: '#/components/examples/ceiling_fan-object-example'
                    와인셀러:
                      $ref: '#/components/examples/wine_cellar-object-example'
                    김치냉장고:
                      $ref: '#/components/examples/kimchi_refrigerator-object-example'
                    홈브루:
                      $ref: '#/components/examples/home_brew-object-example'
                    식물재배기:
                      $ref: '#/components/examples/plant_cultivator-object-example'
                    워시타워 (세탁기):
                      $ref: '#/components/examples/washtower_washer-object-example'
                    워시타워 (건조기):
                      $ref: '#/components/examples/washtower_dryer-object-example'
                    워시타워:
                      $ref: '#/components/examples/washtower-object-example'
                    쿡탑:
                      $ref: '#/components/examples/cooktop-object-example'
                    후드:
                      $ref: '#/components/examples/hood-object-example'
                    전자레인지:
                      $ref: '#/components/examples/microwave_oven-object-example'
                    시스템보일러:
                      $ref: '#/components/examples/system_boiler-object-example'
                    공기청정팬:
                      $ref: '#/components/examples/air_purifier_fan-object-example'
                    스틱청소기:
                      $ref: '#/components/examples/stick_cleaner-object-example'
                    온수기:
                      $ref: '#/components/examples/water_heater-object-example'
                    워시콤보(메인):
                      $ref: '#/components/examples/main_washcombo-object-example'
                    워시콤보(미니):
                      $ref: '#/components/examples/mini_washcombo-object-example'
                    가습기:
                      $ref: '#/components/examples/humidifier-object-example'
                    BECON Cloud에 등록된 시스템 에어컨의 실외기:
                      $ref: '#/components/examples/odu-object-example'
                    BECON Cloud에 등록된 시스템 에어컨의 실내기:
                      $ref: '#/components/examples/idu-object-example'
                    Business Cloud에 등록된 사이니지:
                      $ref: '#/components/examples/signage-object-example'
                    스마트 모션 센서:
                      $ref: '#/components/examples/motion_sensor-object-example'
                    스마트 온습도 센서:
                      $ref: '#/components/examples/temperature_humidity_sensor-object-example'
                    스마트 도어 센서:
                      $ref: '#/components/examples/door_sensor-object-example'
                    스마트 버튼:
                      $ref: '#/components/examples/button-object-example'
                    스마트 조명 스위치:
                      $ref: '#/components/examples/light_switch-object-example'
                    스마트 도어락:
                      $ref: '#/components/examples/door_lock-object-example'
                    스마트 푸시풀 도어락:
                      $ref: '#/components/examples/push_pull_door_lock-object-example'
                    스마트 플러그:
                      $ref: '#/components/examples/plug-object-example'
                    스마트 플러그 미니:
                      $ref: '#/components/examples/plug_mini-object-example'
                    스마트 전구(화이트):
                      $ref: '#/components/examples/bulb_white-object-example'
                    스마트 전구(컬러):
                      $ref: '#/components/examples/bulb_color-object-example'
                    스마트 라인 LED:
                      $ref: '#/components/examples/line_led-object-example'
                    스마트 전동 커튼 컨트롤러:
                      $ref: '#/components/examples/curtain_ctrl-object-example'
                    스마트 전동 블라인드:
                      $ref: '#/components/examples/blind_motor-object-example'
                    스마트 스위치 스트립:
                      $ref: '#/components/examples/switch_strip-object-example'
                    스마트 스타 라이트:
                      $ref: '#/components/examples/starlight-object-example'
                    스마트 도어벨:
                      $ref: '#/components/examples/doorbell-object-example'
                    스마트 펫 급식기:
                      $ref: '#/components/examples/pet_peeder-object-example'
                    스마트 홈 카메라:
                      $ref: '#/components/examples/home_camera-object-example'
                    싱크 박스:
                      $ref: '#/components/examples/sync_box-object-example'
                    싱크 박스 서브:
                      $ref: '#/components/examples/sync_box_sub-object-example'
                    스마트 가스 감지 센서:
                      $ref: '#/components/examples/gas_sensor-object-example'
                    스마트 화재 감지 센서:
                      $ref: '#/components/examples/fire_sensor-object-example'
                    스마트 누수 감지 센서:
                      $ref: '#/components/examples/water_leak_sensor-object-example'
                    스마트 온습도계:
                      $ref: '#/components/examples/thermo_hygrometer-object-example'
                    스마트 사이렌:
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
          summary: 디바이스 제어
          description: 특정 디바이스의 상태를 제어합니다. 디바이스 프로파일에서 제어 가능한 속성이 없는 제품은 제어할 수 없습니다.
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
                  description: 디바이스 유형별 제어 요청 메시지의 스키마는 [**디바이스 프로파일**](/ko/apiManage/device_profile) 페이지를 참조해주십시오.
                examples:
                  냉장고:
                    $ref: '#/components/examples/refrigerator-command-example'
                  세탁기:
                    $ref: '#/components/examples/washer-command-example'
                  건조기:
                    $ref: '#/components/examples/dryer-command-example'
                  에어컨:
                    $ref: '#/components/examples/air_conditioner-command-example'
                  공기청정기:
                    $ref: '#/components/examples/air_purifier-command-example'
                  로봇청소기:
                    $ref: '#/components/examples/robot_cleaner-command-example'
                  오븐:
                    $ref: '#/components/examples/oven-command-example'
                  식기세척기:
                    $ref: '#/components/examples/dish_washer-command-example'
                  스타일러:
                    $ref: '#/components/examples/styler-command-example'
                  제습기:
                    $ref: '#/components/examples/dehumidifier-command-example'
                  실링팬:
                    $ref: '#/components/examples/ceiling_fan-command-example'
                  와인셀러:
                    $ref: '#/components/examples/wine_cellar-command-example'
                  워시타워 (세탁기):
                    $ref: '#/components/examples/washtower_washer-command-example'
                  워시타워 (건조기):
                    $ref: '#/components/examples/washtower_dryer-command-example'
                  워시타워:
                    $ref: '#/components/examples/washtower-command-example'
                  쿡탑:
                    $ref: '#/components/examples/cooktop-command-example'
                  후드:
                    $ref: '#/components/examples/hood-command-example'
                  전자레인지:
                    $ref: '#/components/examples/microwave_oven-command-example'
                  시스템보일러:
                    $ref: '#/components/examples/system_boiler-command-example'
                  공기청정팬:
                    $ref: '#/components/examples/air_purifier_fan-command-example'
                  온수기:
                    $ref: '#/components/examples/water_heater-command-example'
                  워시콤보(메인):
                    $ref: '#/components/examples/main_washcombo-command-example'
                  워시콤보(미니):
                    $ref: '#/components/examples/mini_washcombo-command-example'
                  가습기:
                    $ref: '#/components/examples/humidifier-command-example'
                  BECON Cloud에 등록된 시스템 에어컨의 실내기:
                    $ref: '#/components/examples/idu-command-example'
                  Business Cloud에 등록된 사이니지:
                    $ref: '#/components/examples/signage-command-example'
                  스마트 조명 스위치:
                    $ref: '#/components/examples/light_switch-command-example'
                  스마트 도어락:
                    $ref: '#/components/examples/door_lock-command-example'
                  스마트 푸시풀 도어락:
                    $ref: '#/components/examples/push_pull_door_lock-command-example'
                  스마트 플러그:
                    $ref: '#/components/examples/plug-command-example'
                  스마트 플러그 미니:
                    $ref: '#/components/examples/plug_mini-command-example'
                  스마트 전구(화이트):
                    $ref: '#/components/examples/bulb_white-command-example'
                  스마트 전구(컬러):
                    $ref: '#/components/examples/bulb_color-command-example'
                  스마트 라인 LED:
                    $ref: '#/components/examples/line_led-command-example'
                  스마트 전동 커튼 컨트롤러:
                    $ref: '#/components/examples/curtain_ctrl-command-example'
                  스마트 전동 블라인드:
                    $ref: '#/components/examples/blind_motor-command-example'
                  스마트 스위치 스트립:
                    $ref: '#/components/examples/switch_strip-command-example'
                  스마트 스타 라이트:
                    $ref: '#/components/examples/starlight-command-example'
                  스마트 도어벨:
                    $ref: '#/components/examples/doorbell-command-example'
                  스마트 펫 급식기:
                    $ref: '#/components/examples/pet_peeder-command-example'
                  스마트 홈 카메라:
                    $ref: '#/components/examples/home_camera-command-example'
                  싱크 박스:
                    $ref: '#/components/examples/sync_box-command-example'
                  싱크 박스 서브:
                    $ref: '#/components/examples/sync_box_sub-command-example'
                  스마트 사이렌:
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
                    냉장고:
                      $ref: '#/components/examples/refrigerator-object-example'
                    세탁기:
                      $ref: '#/components/examples/washer-object-example'
                    건조기:
                      $ref: '#/components/examples/dryer-object-example'
                    에어컨:
                      $ref: '#/components/examples/air_conditioner-object-example'
                    공기청정기:
                      $ref: '#/components/examples/air_purifier-object-example'
                    로봇청소기:
                      $ref: '#/components/examples/robot_cleaner-object-example'
                    오븐:
                      $ref: '#/components/examples/oven-object-example'
                    식기세척기:
                      $ref: '#/components/examples/dish_washer-object-example'
                    스타일러:
                      $ref: '#/components/examples/styler-object-example'
                    제습기:
                      $ref: '#/components/examples/dehumidifier-object-example'
                    실링팬:
                      $ref: '#/components/examples/ceiling_fan-object-example'
                    와인셀러:
                      $ref: '#/components/examples/wine_cellar-object-example'
                    워시타워 (세탁기):
                      $ref: '#/components/examples/washtower_washer-object-example'
                    워시타워 (건조기):
                      $ref: '#/components/examples/washtower_dryer-object-example'
                    워시타워:
                      $ref: '#/components/examples/washtower-object-example'
                    쿡탑:
                      $ref: '#/components/examples/cooktop-object-example'
                    후드:
                      $ref: '#/components/examples/hood-object-example'
                    전자레인지:
                      $ref: '#/components/examples/microwave_oven-object-example'
                    시스템보일러:
                      $ref: '#/components/examples/system_boiler-object-example'
                    공기청정팬:
                      $ref: '#/components/examples/air_purifier_fan-object-example'
                    온수기:
                      $ref: '#/components/examples/water_heater-object-example'
                    워시콤보(메인):
                      $ref: '#/components/examples/main_washcombo-object-example'
                    워시콤보(미니):
                      $ref: '#/components/examples/mini_washcombo-object-example'
                    가습기:
                      $ref: '#/components/examples/humidifier-object-example'
                    BECON Cloud에 등록된 시스템 에어컨의 실내기:
                      $ref: '#/components/examples/idu-object-example'
                    Business Cloud에 등록된 사이니지:
                      $ref: '#/components/examples/signage-object-example'
                    스마트 조명 스위치:
                      $ref: '#/components/examples/light_switch-object-example'
                    스마트 도어락:
                      $ref: '#/components/examples/door_lock-object-example'
                    스마트 푸시풀 도어락:
                      $ref: '#/components/examples/push_pull_door_lock-object-example'
                    스마트 플러그:
                      $ref: '#/components/examples/plug-object-example'
                    스마트 플러그 미니:
                      $ref: '#/components/examples/plug_mini-object-example'
                    스마트 전구(화이트):
                      $ref: '#/components/examples/bulb_white-object-example'
                    스마트 전구(컬러):
                      $ref: '#/components/examples/bulb_color-object-example'
                    스마트 라인 LED:
                      $ref: '#/components/examples/line_led-object-example'
                    스마트 전동 커튼 컨트롤러:
                      $ref: '#/components/examples/curtain_ctrl-object-example'
                    스마트 전동 블라인드:
                      $ref: '#/components/examples/blind_motor-object-example'
                    스마트 스위치 스트립:
                      $ref: '#/components/examples/switch_strip-object-example'
                    스마트 스타 라이트:
                      $ref: '#/components/examples/starlight-object-example'
                    스마트 도어벨:
                      $ref: '#/components/examples/doorbell-object-example'
                    스마트 펫 급식기:
                      $ref: '#/components/examples/pet_peeder-object-example'
                    스마트 홈 카메라:
                      $ref: '#/components/examples/home_camera-object-example'
                    싱크 박스:
                      $ref: '#/components/examples/sync_box-object-example'
                    싱크 박스 서브:
                      $ref: '#/components/examples/sync_box_sub-object-example'
                    스마트 사이렌:
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
          summary: 디바이스 푸시 구독 목록 조회
          description: |
            푸시 메시지를 구독한 디바이스의 ID 목록을 조회합니다. **(현재 LG ThinQ 등록 디바이스만 지원합니다.)**
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
          summary: 디바이스 푸시 구독
          description: |
            특정 디바이스에서 전달하는 푸시 메시지를 구독합니다. **(현재 LG ThinQ 등록 디바이스만 지원합니다.)**
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
          summary: 디바이스 푸시 해제
          description: |
            특정 디바이스에서 전달하는 푸시 메시지의 구독을 해제합니다. **(현재 LG ThinQ 등록 디바이스만 지원합니다.)**
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
          summary: 사용자 번호 조회
          description: |
            특정 LG ThinQ 사용자의 사용자 번호를 조회합니다.  사용자가 B2B 파트너의 서비스에 가입할 때 미리 사용자 번호를 조회하면, Callback으로 수신한 푸시 메시지의 디바이스 소유자를 식별합니다.
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
          summary: 사용자 비활성화
          description: |
            더 이상 특정 LG ThinQ 사용자를 연동하지 않을 때 사용자를 비활성화합니다. 특정 사용자가 비활성화되면 그 사용자에게 등록된 디바이스의 상태 조회와 제어를 수행할 수 없습니다. 사용자를 다시 활성화하려면 해당 사용자에 대하여 **[디바이스 목록 조회](#tag/Device-API/operation/getDevices)** API를 호출하면 됩니다.
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
          summary: 그룹 생성 및 갱신
          description: 새 그룹을 생성하거나 기존 그룹을 갱신합니다.
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
            description: 그룹 정보
            content:
              application/json:
                schema:
                  type: object
                  properties:
                    groupId:
                      type: string
                      example: k-apt-1234567890
                      description: 그룹 ID입니다.
                    groupName:
                      type: string
                      example: 압구정 현대 1차 아파트
                      description: 그룹 명입니다.
                    partnerId:
                      type: string
                      example: partner-1
                      description: 그룹을 생성한 전력사/통합사 ID입니다.
                    areaCode:
                      type: string
                      example: '1168011000'
                      description: 법정동 코드(국토교통부에서 지정한 10자리 번호)입니다.
                    buildingCode:
                      type: string
                      example: '1168011000103690001004767'
                      description: |-
                        - 도로명주소건물 관리번호(공간정보 오픈플랫폼)입니다.
                        - 25자리 번호입니다.
                        - 법정동코드(10) + 산여부(1) + 지번본번(4) + 지번부번(4) + 시스템번호(6)로 구성되어 있습니다.
                    comment:
                      type: string
                      example: 압구정 현대 1차 아파트
                      description: 해당 그룹에 대한 설명입니다.
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
                            description: 그룹 ID입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4307
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
                            example: Internal Server Error
      /dr/groups/{groupId}:
        get:
          tags:
            - DR API
          summary: 그룹 조회
          description: 특정 그룹을 조회합니다.
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
              description: 특정 그룹의 ID입니다. 사용자 또는 디바이스의 그룹에 해당됩니다.
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
                        description: 그룹에 대한 정보입니다.
                        properties:
                          groupId:
                            type: string
                            example: k-apt-1234567890
                            description: 그룹을 구분하기 위해 DR 서비스에 등록한 고유한 그룹 ID입니다.
                          groupName:
                            type: string
                            example: 압구정 현대 1차 아파트입니다.
                            description: 그룹명
                          partnerId:
                            type: string
                            example: kepco-herit-lge
                            description: DR 서비스의 파트너사 ID입니다.
                          areaCode:
                            type: string
                            example: '1168011000'
                            description: 법정동 코드(국토교통부에서 지정한 10자리 번호)입니다.
                          buildingCode:
                            type: string
                            example: '1168011000103690001004767'
                            description: |-
                              - 도로명주소건물 관리번호(공간정보 오픈플랫폼)입니다.
                              - 25자리 번호입니다.
                              - 법정동코드(10) + 산여부(1) + 지번본번(4) + 지번부번(4) + 시스템번호(6)로 구성되어 있습니다.
                          comment:
                            type: string
                            example: 압구정 현대 1차 아파트
                            description: 해당 그룹에 대한 설명입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4308
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
                            example: Internal Server Error
      /dr/partners/{partnerId}/groups:
        get:
          tags:
            - DR API
          summary: 그룹 목록 조회
          description: 파트너의 그룹 목록을 조회합니다.
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
              description: 그룹을 생성한 Aggregator 또는 Utility 파트너의 ID입니다.
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
                        description: 그룹 리스트입니다.
                        items:
                          properties:
                            groupId:
                              type: string
                              example: k-apt-1234567890
                              description: DR 서비스에 등록된 그룹 ID입니다.
                            groupName:
                              type: string
                              example: 압구정 현대 1차 아파트
                              description: 그룹명입니다.
                            partnerId:
                              type: string
                              example: partner-1
                              description: 파트너 ID입니다.
                            areaCode:
                              type: string
                              example: '1168011000'
                              description: '- 법정동 코드(국토교통부에서 지정한 10자리 번호)입니다.'
                            buildingCode:
                              type: string
                              example: '1168011000103690001004767'
                              description: |-
                                - 도로명주소건물 관리번호(공간정보 오픈플랫폼)입니다.
                                - 25자리 번호입니다.
                                - 법정동코드(10) + 산여부(1) + 지번본번(4) + 지번부번(4) + 시스템번호(6)로 구성되어 있습니다.
                            comment:
                              type: string
                              example: 압구정 현대 1차 아파트
                              description: 해당 그룹에 대한 설명입니다.
                  examples:
                    200 OK:
                      value:
                        code: 2000
                        data:
                          - groupId: k-apt-1234567890
                            groupName: 압구정 현대 1차 아파트
                            partnerId: partner-1
                            areaCode: '1168011000'
                            buildingCode: '1168011000103690001004767'
                            comment: 압구정 현대 1차 아파트
                          - groupId: k-apt-1234567899
                            groupName: 반포2동 아크로리버파크
                            partnerId: kepco-herit-lge
                            areaCode: '1165010700'
                            buildingCode: '1165010700100020001017796'
                            comment: 반포2동 아크로리버파크
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4308
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
                            example: Internal Server Error
      /dr/users:
        post:
          tags:
            - DR API
          summary: 사용자 생성
          description: 사용자를 생성합니다. (LG ThinQ App 공통)
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
                      description: LG전자 계정의 사용자 번호입니다.
                    mail:
                      type: string
                      example: test_mail@lge.com
                      description: LG전자 계정의 이메일 주소입니다.
                    groupId:
                      type: string
                      example: A15721009
                      description: 사용자를 등록할 그룹 ID입니다.
                    accessToken:
                      type: string
                      example: 67a184e62a412bb19b6ec2742b94695e06c1ce19d04f8d92121c6c28c99faf841150dba911da301e5617ae3945218a05
                      description: LMP(LGE Members Platform) 시스템에서 발급된 access_token입니다.
                    refreshToken:
                      type: string
                      example: 3559466b6c19e312357c277108aed936c22840672b1c2a6a8fb7597a6473f9a59fbec4a3f4e03595b8358413ba1d8088
                      description: LMP(LGE Members Platform) 시스템에서 발급된 refresh_token입니다.
                    partner:
                      type: object
                      description: Partner information
                      properties:
                        partnerId:
                          type: string
                          example: partner-1
                          description: 파트너사 ID입니다.
                        programId:
                          type: string
                          example: test-dr-1
                          description: DR 프로그램 ID(북미지역 한정)입니다.
                        programName:
                          type: string
                          example: test DR Program
                          description: DR 프로그램명(북미지역 한정)입니다.
                        partnerUserId:
                          type: string
                          example: partnerId-1
                          description: 파트너사 사용자 ID입니다.
                        authCodeExt:
                          type: string
                          example: d778581e-4431-2531-1315-c823beebc72f.f81a0977-a553-417e-8873-64faafa0534a.160df234-7s14-4ed2-b710-74afc12eaa12
                          description: 3rd party OAuth 2.0 연동을 위한 Auth code(3rd party system에서 발급받으며 1회용)입니다.
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
                            description: 생성된 사용자의 암호화된 LG전자 계정의 사용자 번호입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4307
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4309
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
                            example: Internal Server Error
      /dr/users/{userNo}:
        delete:
          tags:
            - DR API
          summary: 사용자 삭제
          description: LG전자 계정의 사용자 번호에 해당하는 특정 사용자를 삭제합니다. 사용자의 디바이스 정보도 함께 삭제됩니다.
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
              description: 암호화된 LG전자 계정의 사용자 번호입니다.
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
                            description: 삭제된 사용자 LG전자 계정의 사용자 번호입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4301
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
                            example: Internal Server Error
        get:
          tags:
            - DR API
          summary: 사용자 정보 조회
          description: 암호화된 LG전자 계정의 사용자 번호에 해당하는 사용자 정보를 조회합니다.
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
              description: 암호화된 LG전자 계정의 사용자 번호입니다.
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
                            description: 암호화된 LG전자 계정의 사용자 번호입니다.
                          drHomeId:
                            type: string
                            example: '123456789012345678'
                            description: DR 서비스에 연결된 사용자의 ThinQ Home ID입니다.
                          partnerId:
                            type: string
                            example: partner-1
                            description: 사용자가 가입한 DR 서비스의 파트너 ID입니다.
                          groupId:
                            type: string
                            example: A12345678
                            description: 사용자가 속한 그룹 ID입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4301
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
                            example: Internal Server Error
      /dr/users/{userNo}/devices:
        get:
          tags:
            - DR API
          summary: 사용자 디바이스 목록 조회
          description: DR 이벤트 참여 가능한 사용자의 디바이스 목록을 조회합니다.
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
              description: 암호화된 LG전자 계정의 사용자 번호입니다.
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
                              description: 암호화된 ThinQ 디바이스 ID입니다.
                            macAddress:
                              type: string
                              example: 66e71f19ada4fcaf3156aa26d49d4291
                              description: 암호화된 MAC address입니다.
                            groupId:
                              type: string
                              example: A12345678
                              description: 그룹 ID입니다.
                            userNo:
                              type: string
                              example: 01581c1135488770282d3c09d478cef7
                              description: 암호화된 LG전자 계정의 사용자 번호입니다.
                            homeId:
                              type: string
                              example: '123456789012345678'
                              description: 디바이스가 등록된 ThinQ Home ID입니다.
                            drParticipate:
                              type: boolean
                              example: true
                              description: DR 이벤트 참여 가능 여부(true/false)입니다.
                            opt:
                              type: string
                              example: IN
                              description: 현재 DR 이벤트 참여중 여부("IN"/"OUT")입니다.
                            deviceType:
                              type: string
                              example: DEVICE_AIR_CONDITIONER
                              description: 디바이스 타입입니다.
                            modelName:
                              type: string
                              example: PAC_910604_US
                              description: 디바이스 모델명입니다.
                            alias:
                              type: string
                              example: air conditioner
                              description: 디바이스 별칭(alias)입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4301
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
                            example: Internal Server Error
      /dr/users/{userNo}/devices/{deviceId}:
        get:
          tags:
            - DR API
          summary: 사용자 디바이스 정보 조회
          description: 사용자의 특정 디바이스 정보를 조회합니다.
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
              description: 암호화된 LG전자 계정의 사용자 번호입니다.
              required: true
              schema:
                type: string
                example: 01581c1135488770282d3c09d478cef7
            - in: path
              name: deviceId
              description: 암호화된 ThinQ 디바이스 ID입니다.
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
                              description: 암호화된 ThinQ 디바이스 ID입니다.
                            macAddress:
                              type: string
                              example: 66e71f19ada4fcaf3156aa26d49d4291
                              description: 암호화된 MAC address입니다.
                            groupId:
                              type: string
                              example: A12345678
                              description: 그룹 ID입니다.
                            userNo:
                              type: string
                              example: 01581c1135488770282d3c09d478cef7
                              description: 암호화된 LG전자 계정의 사용자 번호입니다.
                            homeId:
                              type: string
                              example: '123456789012345678'
                              description: 디바이스가 등록된 ThinQ Home ID입니다.
                            drParticipate:
                              type: boolean
                              example: true
                              description: DR 이벤트 참여 가능 여부(true/false)입니다.
                            opt:
                              type: string
                              example: IN
                              description: 현재 DR 이벤트 참여중 여부("IN"/"OUT")입니다.
                            deviceType:
                              type: string
                              example: DEVICE_AIR_CONDITIONER
                              description: 디바이스 타입입니다.
                            modelName:
                              type: string
                              example: PAC_910604_US
                              description: 디바이스 모델명입니다.
                            alias:
                              type: string
                              example: air conditioner
                              description: 디바이스 별칭(alias)입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4301
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
                            example: Internal Server Error
      /dr/events:
        post:
          tags:
            - DR API
          summary: DR 이벤트 생성 및 갱신
          description: DR 이벤트를 생성하거나 기존 이벤트를 갱신합니다.
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
            description: DR 이벤트 정보입니다.
            content:
              application/json:
                schema:
                  type: object
                  properties:
                    eventId:
                      type: string
                      example: 2024-04-25-dr-01
                      description: DR 이벤트 ID입니다.
                    eventName:
                      type: string
                      example: 2024-04-25 test DR event
                      description: DR 이벤트 명입니다.
                    partnerId:
                      type: string
                      example: partner-1
                      description: 파트너 ID입니다.
                    startTs:
                      type: number
                      example: 1714024800000
                      description: DR 이벤트 시작 시간(milliseconds)입니다.
                    endTs:
                      type: number
                      example: 1714028400000
                      description: DR 이벤트 종료 시간(milliseconds)입니다.
                    targets:
                      type: array
                      items:
                        properties:
                          targetType:
                            type: string
                            example: GROUP
                            description: 이벤트 타깃 타입(GROUP, USER, DEVICE)입니다.
                          targetIds:
                            type: array
                            items:
                              type: string
                              example: k-apt-1234567890
                            description: 이벤트 타깃 ID 리스트 (of GROUP, USER or DEVICE)입니다.
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
                            description: DR 이벤트 시그널 ID입니다.
                          deviceType:
                            type: string
                            example: DEVICE_AIR_CONDITIONER
                            description: DR 이벤트 타깃 디바이스 타입입니다.
                          modelNames:
                            type: array
                            items:
                              type: string
                              example: RAC_056905_WW
                            description: DR 이벤트 타깃 디바이스 모델명입니다.
                          signalType:
                            type: string
                            example: CONTROL_RESTORE
                            description: DR 이벤트 시그널 타입 (CONTROL, CONTROL_RESTORE)입니다.
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
                              구체적인 제어 값입니다.
                              ex) { temerpature: { min: 20, max: 26, unit: "C } }
                          constrolType:
                            type: string
                            example: Temperature
                            description: 제어 방식(Temperature, TwoSetTemperature, ToU, Empty)입니다.
                          restoreType:
                            type: string
                            example: Temperature
                            description: 제어 원복 방식 (Temperature, TwoSetTemperature, Empty)입니다.
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
                            description: 생성된 DR 이벤트 ID입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4307
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4311
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
                            example: Internal Server Error
      /dr/events/{eventId}:
        delete:
          tags:
            - DR API
          summary: DR 이벤트 삭제
          description: 생성한 DR 이벤트를 삭제합니다.
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
                            description: 삭제된 DR 이벤트 ID입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4302
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
                            example: Internal Server Error
      /dr/events/{eventId}/targets:
        post:
          tags:
            - DR API
          summary: DR 이벤트 타깃 생성
          description: 이미 생성된 DR 이벤트에 이벤트 타깃 정보를 추가합니다.
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
              description: DR 이벤트 ID입니다.
              required: true
              schema:
                type: string
                example: event-01
          requestBody:
            description: DR 이벤트 타깃 정보입니다.
            content:
              application/json:
                schema:
                  type: object
                  properties:
                    type:
                      type: string
                      example: USER
                      description: |-
                        타깃 타입입니다.
                        - GROUP
                        - USER
                        - DEVICE
                    id:
                      type: string
                      example: KR1234567890123
                      description: |-
                        DR 이벤트 타깃 ID입니다.
                        - 이벤트 타깃 타입이 USER일 경우: userNo
                        - 이벤트 타깃 타입이 GROUP일 경우: groupId
                        - 이벤트 타깃 타입이 DEVICE일 경우: deviceId
                    opt:
                      type: string
                      example: OUT
                      description: |-
                        DR 이벤트 참여 여부(Opt in / out)를 확인할 수 있습니다.
                        - IN: DR 이벤트에 참여(default)
                        - OUT: DR 이벤트에 미참여
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
                            description: 생성된 DR 이벤트 타깃 ID입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4302
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
                            example: Internal Server Error
      /dr/events/{eventId}/targets/{targetId}:
        post:
          tags:
            - DR API
          summary: DR 이벤트 타깃 수정
          description: 이미 생성한 DR 이벤트 타깃을 수정합니다.
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
              description: DR 이벤트 ID입니다.
              required: true
              schema:
                type: string
                example: event-01
            - in: path
              name: targetId
              description: DR 이벤트 타깃 ID입니다.
              required: true
              schema:
                type: string
                example: KR1234567890123
          requestBody:
            description: DR 이벤트 정보입니다.
            content:
              application/json:
                schema:
                  type: object
                  properties:
                    opt:
                      type: string
                      example: OUT
                      description: |-
                        DR 이벤트 참여 여부 (Opt in / out)를 확인할 수 있습니다.
                        - IN: DR 이벤트 참여 (default)
                        - OUT: DR 이벤트 미참여
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4102
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4302
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
                            example: Internal Server Error
      /dr/events/{eventId}/targets/batch:
        post:
          tags:
            - DR API
          summary: DR 이벤트 타깃 일괄 생성
          description: DR 이벤트 타깃을 한 번에 여러 개 생성합니다.
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
              description: DR 이벤트 ID입니다.
              required: true
              schema:
                type: string
                example: event-01
          requestBody:
            description: DR 이벤트 타깃의 업데이트 정보입니다.
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
                          DR 이벤트 타깃 생성/수정 여부입니다.
                          - create
                          - replace(미사용)
                      path:
                        type: string
                        example: /
                        description: |-
                          DR 이벤트 타깃 ID입니다.
                          - create: "/"
                          - replace: "/{targetId}"
                          - Ex) 생성: "/"
                          - Ex) 수정: "/2YjaqUmSr3ke2nmdssxAG5n0KDMwrJrvi8bTbzbdHelEEflqNkAx0WWmTIgyCQf"
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
                          DR 이벤트 참여 여부(Opt in / out)를 확인할 수 있습니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4102
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4302
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
                            example: Internal Server Error
      /dr/data-zip/files:
        post:
          tags:
            - DR API
          summary: 모니터링 데이터 파일 생성
          description: DR 이벤트 기간 내 DR 이벤트에 참여한 디바이스의 모니터링 데이터를 ZIP 파일로 생성하도록 요청합니다.
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
            description: DR 이벤트 정보입니다.
            content:
              application/json:
                schema:
                  type: object
                  properties:
                    eventId:
                      type: string
                      example: 2023-04-25-dr-01
                      description: DR 이벤트 ID입니다.
                    targets:
                      type: array
                      items:
                        properties:
                          targetId:
                            type: string
                            example: KR1234567890123
                            description: DR 이벤트 타깃 ID입니다.
                          targetType:
                            type: string
                            example: USER
                            description: |-
                              DR 이벤트 타깃 타입입니다.
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
                            description: 생성된 ZIP 파일명입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4102
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4302
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
                            example: Internal Server Error
      /dr/data-zip/files/{filename}:
        get:
          tags:
            - DR API
          summary: 모니터링 데이터 파일 다운로드
          description: DR 이벤트에 참여한 디바이스의 모니터링 데이터 ZIP 파일을 다운받을 수 있는 링크를 요청합니다.
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
              description: 생성된 ZIP 파일명입니다.
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
                            description: 생성된 DR 이벤트 ZIP 파일 다운로드 경로입니다.(1시간 유효)
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 4306
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
                    description: 요청 실패 시 응답입니다.
                    properties:
                      code:
                        type: number
                        description: 상태 코드입니다.
                        example: 5000
                      error:
                        type: object
                        properties:
                          message:
                            type: string
                            description: 에러 상세 메시지입니다.
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
            파트너 요청 또는 권한 업데이트 요청이 승인된 이후 획득한 `API Key` 문자열입니다.
          in: header
          name: X-Api-Key
      schemas:
        api-token-res:
          type: object
          description: API Token을 포함하는 응답입니다.
          properties:
            access_token:
              type: string
              description: API Token 문자열이며 JWT(header.payload.signature)로 표현됩니다.
              example: eyJhbGciOiJIUzI1NiIsImtpZCI6InNpbTIifQ.eyJleHAiOjE3MDQzNDE3MDIsImlhdCI6MTcwNDI1NTMwMiwiaXNzIjoiTEcgQnVzaW5lc3MgQ29ubmVjdCIsInJvbGVzIjpbImdldEJlY29uVXNlcnMiLCJnZXREclVzZXJzIiwicG9zdFRva2VuIl0sInN1YiI6IjRkMmM2MWUxLTM0YzQtZTk2Yy05NDU2LTE1YmQ5ODNjNTAxOSJ9.plRjXmZRoXkOy_U95VXGzX-ouJyCrorEmMO8OzrEvF8
        device-base-res:
          type: object
          description: 디바이스 관련 기본 응답 항목입니다.
          properties:
            messageId:
              type: string
              description: API 요청 헤더에 포함되었던 `X-Message-Id`의 문자열입니다.
              example: 2ADaRijIk8CvaSHVPeEWNw
            timestamp:
              type: string
              description: API 요청이 수신된 시각입니다. `ISO-8601` 포맷을 따릅니다.
              example: '2024-10-01T06:23:20.866279'
        device-list-item:
          type: object
          title: 디바이스 목록 응답입니다.
          properties:
            deviceId:
              type: string
              description: 특정 디바이스의 ID입니다.
              example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
            deviceInfo:
              type: object
              properties:
                deviceType:
                  type: string
                  description: 디바이스 타입입니다. 지원하는 디바이스 타입의 목록은 [**디바이스 프로파일**](/ko/apiManage/device_profile) 페이지를 참조해주세요.
                  example: DEVICE_WASHTOWER_WASHER
                alias:
                  type: string
                  description: 디바이스 별칭입니다.
                  example: My New WashTower Washer
                modelName:
                  type: string
                  description: 디바이스 모델명입니다.
                  example: FAKPK21021
                reportable:
                  type: boolean
                  description: 디바이스 상태 변경 시 발생하는 이벤트에 대한 구독 가능 여부입니다.
                  example: 'true'
                groupId:
                  type: string
                  description: 디바이스 타입이 `DEVICE_WASHTOWER_WASHER` 또는 `DEVICE_WASHTOWER_DRYER`일 때, 다른 디바이스와의 동일 그룹임을 식별하기 위한 그룹 ID입니다.
                  example: '171807013576723372'
                parentId:
                  type: string
                  description: 디바이스 타입이 `IDU`일 때, 상위의 `ODU` 디바이스의 ID입니다.
                  example: fe12ed5bca00acc0ed68ec9f632342d0822a929f377b76cbe700649a11053f23
              required:
                - deviceType
                - alias
          required:
            - deviceId
            - deviceInfo
        device-list-res:
          description: 디바이스 목록 응답입니다.
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
          description: 요청 실패 시 응답입니다.
          properties:
            messageId:
              type: string
              description: 요청 헤더 `X-Message-Id`의 값입니다.
              example: 2ADaRijIk8CvaSHVPeEWNw
            timestamp:
              type: datetime
              description: 현재 시간입니다.
              example: '2024-09-13T06:55:58.65064'
            error:
              type: object
              description: 상세 에러입니다.
              properties:
                message:
                  type: string
                  description: 상세 에러 메시지입니다.
                code:
                  type: string
                  description: 상세 오류 코드입니다.
        device-profile-res:
          description: 특정 디바이스의 프로파일 응답입니다.
          allOf:
            - $ref: '#/components/schemas/device-base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: 디바이스 유형별 디바이스 프로파일 메시지의 스키마는 [**디바이스 프로파일**](/ko/apiManage/device_profile) 페이지를 참조해주십시오.
        device-status-res:
          description: 특정 디바이스의 상태 응답입니다.
          allOf:
            - $ref: '#/components/schemas/device-base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: 디바이스 유형별 디바이스 상태 응답 메시지의 스키마는 [**디바이스 프로파일**](/ko/apiManage/device_profile) 페이지를 참조해주십시오.
        device-id-list-res:
          description: 디바이스 ID 목록의 응답입니다.
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
                        description: 특정 디바이스의 ID입니다.
                        example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
        device-empty-res:
          description: 내용이 없는 응답입니다.
          allOf:
            - $ref: '#/components/schemas/device-base-res'
            - type: object
              properties:
                response:
                  type: object
        userno-res:
          description: 사용자 번호 응답입니다.
          allOf:
            - $ref: '#/components/schemas/device-base-res'
            - type: object
              properties:
                response:
                  type: object
                  properties:
                    userNumber:
                      type: string
                      description: 사용자 번호입니다.
                      example: SaGvM4ETAgOHSAFhezzi
        dr-event-target-opt-res:
          type: object
          properties:
            type:
              type: string
              example: USER
              description: |-
                타깃 타입입니다.
                - GROUP
                - USER
                - DEVICE
            id:
              type: string
              example: KRXXXX
              description: |-
                DR 이벤트 타깃 ID입니다.
                - 이벤트 타깃 타입이 USER일 경우: userNo
                - 이벤트 타깃 타입이 GROUP일 경우: groupId
                - 이벤트 타깃 타입이 DEVICE일 경우: deviceId
            opt:
              type: string
              example: OUT
              description: |-
                DR 이벤트 참여 여부(Opt in / out)를 확인할 수 있습니다.
                - IN: DR 이벤트에 참여(default)
                - OUT: DR 이벤트에 미참여
        callback-base-res:
          type: object
          description: Callback 관련 기본 응답 항목입니다.
          properties:
            messageId:
              type: string
              description: 메시지의 흐름을 추적하기 위해 url-safe-base64-no-padding(UUID Version 4)의 22개 문자로 생성한 문자열입니다.
              example: 8O4J3mY-dkKYhH4LSo-Hpw
            timestamp:
              type: string
              description: 메시지를 생성한 시각입니다. `ISO-8601` 포맷을 따릅니다.
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
                      description: 푸시 타입입니다.
                      example: DEVICE_PUSH
                    deviceId:
                      type: string
                      description: 특정 디바이스의 ID입니다.
                      example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
                    deviceType:
                      type: string
                      description: 디바이스 타입입니다. 지원하는 디바이스 타입의 목록은 [**디바이스 프로파일**](/ko/apiManage/device_profile) 페이지를 참조해주세요.
                      example: DEVICE_WASHTOWER_WASHER
                    pushCode:
                      type: string
                      description: 푸시 메시지 코드입니다. 지원하는 코드의 목록은 [**디바이스 프로파일**](/ko/apiManage/device_profile) 페이지를 참조해주세요.
                      example: WASHING_IS_COMPLETE
                    userList:
                      type: array
                      description: 푸시를 구독한 사용자 번호의 목록입니다.
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
                      description: 푸시 타입입니다.
                      example: DEVICE_REGISTERED
                    userNumber:
                      type: string
                      description: 사용자 번호입니다.
                      example: SaGvM4ETAgOHSAFhezzi
                    deviceId:
                      type: string
                      description: 특정 디바이스의 ID입니다.
                      example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
                    deviceType:
                      type: string
                      description: 디바이스 타입. 지원하는 디바이스 타입의 목록은 [**디바이스 프로파일**](/ko/apiManage/device_profile) 페이지를 참조해주세요.
                      example: DEVICE_WASHTOWER_WASHER
                    alias:
                      type: string
                      description: 디바이스 별칭입니다.
                      example: My New WashTower Washer
                    modelName:
                      type: string
                      description: 디바이스 모델명입니다.
                      example: FAKPK21021
                    reportable:
                      type: boolean
                      description: 디바이스 상태 변경 시 발생하는 이벤트에 대한 구독 가능 여부입니다.
                      example: 'true'
                    groupId:
                      type: string
                      description: 디바이스 타입이 `DEVICE_WASHTOWER_WASHER` 또는 `DEVICE_WASHTOWER_DRYER`일 때, 다른 디바이스와의 동일 그룹임을 식별하기 위한 그룹 ID입니다.
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
                      description: 푸시 타입입니다.
                      example: DEVICE_UNREGISTERED
                    userNumber:
                      type: string
                      description: 사용자 번호입니다.
                      example: SaGvM4ETAgOHSAFhezzi
                    deviceId:
                      type: string
                      description: 특정 디바이스의 ID입니다.
                      example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
                    deviceType:
                      type: string
                      description: 디바이스 타입. 지원하는 디바이스 타입의 목록은 [**디바이스 프로파일**](/ko/apiManage/device_profile) 페이지를 참조해주세요.
                      example: DEVICE_WASHTOWER_WASHER
                    alias:
                      type: string
                      description: 디바이스 별칭입니다.
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
                      description: 푸시 타입입니다.
                      example: DEVICE_ALIAS_CHANGED
                    userNumber:
                      type: string
                      description: 사용자 번호입니다.
                      example: SaGvMtETAgOHSAFhezzi
                    deviceId:
                      type: string
                      description: 특정 디바이스의 ID입니다.
                      example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
                    alias:
                      type: string
                      description: 디바이스 별칭입니다.
                      example: My New WashTower Washer
      parameters:
        X-Api-Token:
          name: X-Api-Token
          in: header
          schema:
            type: string
          description: |
            **[API Token 발급](#tag/auth/operation/createAPIToken)** API를 통하여 사전에 발급 받은 문자열인 `API Token`입니다.
          example: eyJhbGciOiJIUzI1NiIsImtpZCI6InNpbTIifQ.eyJleHAiOjE3MDQzNDE3MDIsImlhdCI6MTcwNDI1NTMwMiwiaXNzIjoiTEcgQnVzaW5lc3MgQ29ubmVjdCIsInJvbGVzIjpbImdldEJlY29uVXNlcnMiLCJnZXREclVzZXJzIiwicG9zdFRva2VuIl0sInN1YiI6IjRkMmM2MWUxLTM0YzQtZTk2Yy05NDU2LTE1YmQ5ODNjNTAxOSJ9.plRjXmZRoXkOy_U95VXGzX-ouJyCrorEmMO8OzrEvF8
        X-Message-Id:
          name: X-Message-Id
          in: header
          schema:
            type: string
          description: |
            API 호출 처리 흐름을 추적하기 위해 API의 클라이언트가 url-safe-base64-no-padding(UUID Version 4)의 22개 문자로 생성한 문자열입니다.
          example: 2ADaRijIk8CvaSHVPeEWNw
        X-Use-Account:
          name: X-Use-Account
          in: header
          schema:
            type: string
          description: |
            API 요청 처리시 사용할 LG전자 계정의 출처입니다.

              |Value|Description|
              |-|-|
              |REGISTERED|파트너 요청 및 권한 업데이트를 통해 이미 등록한 계정입니다.|
              |IN-HEADER|이 HTTP 요청의 `Authorization` 헤더에 OAuth 토큰(Token)으로 지정된 계정입니다. (**현재 LG ThinQ 등록 디바이스만 지원합니다.**)|
          example: REGISTERED
        Authorization:
          name: Authorization
          in: header
          schema:
            type: string
          description: |
            LG ThinQ에 가입한 LG전자 계정의 `Bearer` OAuth 토큰(Token)입니다.  `X-Use-Account` 헤더가 HTTP 요청에 포함되어 있으면서 헤더의 값이 `IN-HEADER`인 경우, 이 헤더를 필수적으로 요청에 포함해야 합니다.
          example: Bearer 5a9a713f51a95c53d781addd1af0dfa4f6e1e7420a8bff3c5198308dac571aa9845832b8d29bbe1f04deec2d35229c6d
        X-Country-Code:
          name: X-Country-Code
          in: header
          schema:
            type: string
          description: |
            LG ThinQ가 지원하는 국가의 `ISO-3166 alpha-2` 국가 코드입니다.  `X-Use-Account` 헤더가 HTTP 요청에 포함되어 있으면서 헤더의 값이 `IN-HEADER`인 경우, 이 헤더를 필수적으로 요청에 포함해야 하며 `Authorization`에서 지정한 LG전자 계정의 등록 국가의 코드여야 합니다.
          example: KR
        deviceId:
          name: deviceId
          in: path
          schema:
            type: string
          description: 특정 디바이스의 ID입니다.
          example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
        Authorization-2:
          name: Authorization
          in: header
          schema:
            type: string
          description: |
            LG ThinQ에 가입한 LG전자 계정의 `Bearer` OAuth 토큰
          example: Bearer 5a9a713f51a95c53d781addd1af0dfa4f6e1e7420a8bff3c5198308dac571aa9845832b8d29bbe1f04deec2d35229c6d
        X-Country-Code-2:
          name: X-Country-Code
          in: header
          schema:
            type: string
          description: |
            LG전자가 지원하는 국가의 `ISO-3166 alpha-2` 국가 코드
          example: KR
      headers:
        X-Message-Id-response:
          schema:
            type: string
          description: |
            API 호출 처리 흐름을 추적하기 위해 API의 클라이언트가 url-safe-base64-no-padding(UUID Version 4)의 22개 문자로 생성한 문자열입니다.
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
          description: 냉장고 - 절전 모드 설정
          value:
            powerSave:
              powerSaveEnabled: true
        washer-command-example:
          description: 세탁기 - 운전 시작
          value:
            location:
              locationName: MAIN
            operation:
              washerOperationMode: START
        dryer-command-example:
          description: 건조기 - 세탁 시작
          value:
            operation:
              dryerOperationMode: START
        air_conditioner-command-example:
          description: 에어컨 - 지정한 켜짐 예약시간
          value:
            timer:
              absoluteHourToStart: 10
              absoluteMinuteToStart: 36
        air_purifier-command-example:
          description: 공기청정기 - 운전 모드
          value:
            airPurifierJobMode:
              currentJobMode: CLEAN
        robot_cleaner-command-example:
          title: Robot_Cleaner
          description: 로봇청소기 - 청소 모드
          value:
            operation:
              cleanOperationMode: HOMING
        oven-command-example:
          title: Oven
          description: 오븐 - 오븐 동작
          value:
            location:
              locationName: LOWER
            operation:
              ovenOperationMode: START
        dish_washer-command-example:
          description: 식기세척기 - 운전 모드
          value:
            operation:
              dishWasherOperationMode: START
        styler-command-example:
          description: 스타일러 - 운전 모드
          value:
            operation:
              stylerOperationMode: START
        dehumidifier-command-example:
          description: 가습기 - 운전 모드
          value:
            humidifierJobMode:
              currentJobMode: HUMIDIFY
        ceiling_fan-command-example:
          description: 실링팬 - 운전 모드
          value:
            operation:
              ceilingfanOperationMode: POWER_ON
        wine_cellar-command-example:
          description: 와인셀러 - 조명 밝기
          value:
            operation:
              lightStatus: 90
        washtower_washer-command-example:
          description: 워시타워 (세탁기) - 세탁 시작
          value:
            operation:
              washerOperationMode: START
            location:
              locationName: MAIN
        washtower_dryer-command-example:
          description: 워시타워 (건조기) - 전원 POWER_OFF
          value:
            operation:
              dryerOperationMode: POWER_OFF
        washtower-command-example:
          description: 워시타워 - 건조기 시작
          value:
            dryer:
              operation:
                dryerOperationMode: START
        cooktop-command-example:
          description: 쿡탑 - 전원 OFF
          value:
            operation:
              operationMode: POWER_OFF
        hood-command-example:
          description: 후드 - 램프 밝기
          value:
            lamp:
              lampBrightness: 0
        microwave_oven-command-example:
          description: 전자레인지
          value:
            lamp:
              lampBrightness: 1
            ventilation:
              fanSpeed: 0
        system_boiler-command-example:
          description: 시스템 보일러 - 전원 ON
          value:
            operation:
              boilerOperationMode: POWER_ON
        air_purifier_fan-command-example:
          description: 공기청정팬 - 운전 모드
          value:
            airFanJobMode:
              currentJobMode: SPOT_CLEAN
        water_heater-command-example:
          description: 온수기 - 운전모드
          value:
            waterHeaterJobMode:
              currentJobMode: AUTO
        main_washcombo-command-example:
          description: 워시콤보세탁기 메인 - 동작
          value:
            location:
              locationName: MAIN
            operation:
              washerOperationMode: START
        mini_washcombo-command-example:
          description: 워시콤보세탁기 미니 - 동작
          value:
            location:
              locationName: MINI
            operation:
              washerOperationMode: START
        humidifier-command-example:
          title: Humidifier
          description: 가습기 - 운전 모드
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
