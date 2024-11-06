---
contents:
  lang: yaml
  code: >
    openapi: 3.1.0

    info:
      version: null
      title: ThinQ Business API
    servers:
      - url: https://ap.api.lge.com/biz/v1
      - url: https://eu.api.lge.com/biz/v1 
      - url: https://us.api.lge.com/biz/v1
      - url: https://ap-test.api.lge.com/biz/v1
      - url: https://eu-test.api.lge.com/biz/v1
      - url: https://us-test.api.lge.com/biz/v1
    tags:
      - name: Overview
        x-displayName: Overview
        description: |
          To search or control information about LG Electronics' home appliances, displays, and air conditioners with your service, you can utilize the ThinQ Business API. LG Electronics provides the ThinQ Business API so that a partner's service can obtain or control information about devices registered in LG Electronics' cloud service. ThinQ Business APIs are categorized as follows, depending on the usage purpose of the API.

           |API Type|Summary|
           |-|-|
           |Device API|API to get a list and status of enrolled devices and perform controls|
           |Event API|API for managing target devices to receive status changes on devices|
           |User API|API for managing users registered with B2B partner's service|
           |DR API|API for B2B partners to control a user's device as an electricity demand response (DR) service provider|
      - name: API Call Sequence
        x-displayName: API Call Sequence
        description: "Describes how to develop a service using the ThinQ Business API through a sequence of API calls.\n\n## API Token Issuance\nAPI Token Issuance: An API Token must be included in the HTTP request header of all ThinQ Business API calls. This API Token can be issued with a pair of pre-issued API Key and API Secret from LG Open API Developer and is valid for 24 hours.\n\n\n - API Usage\n    - [`POST /token`](#tag/auth/operation/createAPIToken)\n\n - Sequence\n    1.Set the API Key and API Secret received from LG Open API Developer for the API Token issuance logic (API Secret will be sent via email when the API Key is issued). \n    2. Call the API Token issuance API (POST /token) to get an API Token periodically. You'll need to make another API token issuance request within 24 hours.\n    \n    <?xml version=\"1.0\" encoding=\"us-ascii\" standalone=\"no\"?><svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" contentStyleType=\"text/css\" height=\"447px\" preserveAspectRatio=\"none\" style=\"width:606px;height:447px;background:#FFFFFF;\" version=\"1.1\" viewBox=\"0 0 606 447\" width=\"606px\" zoomAndPan=\"magnify\"><defs/><g><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"350\" y=\"208.7622\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"350\" y=\"306.439\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"281\" x=\"153.5\" y=\"164.9414\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"281\" x=\"153.5\" y=\"262.6182\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"46\" x2=\"46\" y1=\"84.2295\" y2=\"363.2949\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"219.5\" x2=\"219.5\" y1=\"84.2295\" y2=\"363.2949\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"354.5\" x2=\"354.5\" y1=\"84.2295\" y2=\"363.2949\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"517.5\" x2=\"517.5\" y1=\"84.2295\" y2=\"363.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"77\" x=\"5\" y=\"81.1533\">B2B Partner</text><ellipse cx=\"46.5\" cy=\"13.5\" fill=\"#E2E2F0\" rx=\"8\" ry=\"8\" style=\"stroke:#181818;stroke-width:0.5;\"/><path d=\"M46.5,21.5 L46.5,48.5 M33.5,29.5 L59.5,29.5 M46.5,48.5 L33.5,63.5 M46.5,48.5 L59.5,63.5 \" fill=\"none\" style=\"stroke:#181818;stroke-width:0.5;\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"77\" x=\"5\" y=\"378.4482\">B2B Partner</text><ellipse cx=\"46.5\" cy=\"390.0244\" fill=\"#E2E2F0\" rx=\"8\" ry=\"8\" style=\"stroke:#181818;stroke-width:0.5;\"/><path d=\"M46.5,398.0244 L46.5,425.0244 M33.5,406.0244 L59.5,406.0244 M46.5,425.0244 L33.5,440.0244 M46.5,425.0244 L59.5,440.0244 \" fill=\"none\" style=\"stroke:#181818;stroke-width:0.5;\"/><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"163.5\" y=\"50\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"170.5\" y=\"73.1533\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"163.5\" y=\"362.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"170.5\" y=\"385.4482\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"285.5\" y=\"50\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"292.5\" y=\"73.1533\">ThinQ Business API</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"285.5\" y=\"362.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"292.5\" y=\"385.4482\">ThinQ Business API</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"166\" x=\"434.5\" y=\"50\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"152\" x=\"441.5\" y=\"73.1533\">LG Open API Developer</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"166\" x=\"434.5\" y=\"362.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"152\" x=\"441.5\" y=\"385.4482\">LG Open API Developer</text><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"350\" y=\"208.7622\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"350\" y=\"306.439\"/><polygon fill=\"#181818\" points=\"57.5,114.0854,47.5,118.0854,57.5,122.0854,53.5,118.0854\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"51.5\" x2=\"516.5\" y1=\"118.0854\" y2=\"118.0854\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"149\" x=\"63.5\" y=\"113.229\">API Key, API Secret &#51228;&#44277;</text><polygon fill=\"#181818\" points=\"207.5,145.9414,217.5,149.9414,207.5,153.9414,211.5,149.9414\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"46.5\" x2=\"213.5\" y1=\"149.9414\" y2=\"149.9414\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"149\" x=\"53.5\" y=\"145.085\">API Key, API Secret &#49444;&#51221;</text><path d=\"M153.5,164.9414 L230.5,164.9414 L230.5,174.7974 L220.5,184.7974 L153.5,184.7974 L153.5,164.9414 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"281\" x=\"153.5\" y=\"164.9414\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"28\" x=\"168.5\" y=\"180.9409\">loop</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"86\" x=\"245.5\" y=\"179.6333\">[24&#49884;&#44036; &#45236; &#48152;&#48373;]</text><polygon fill=\"#181818\" points=\"338,204.7622,348,208.7622,338,212.7622,342,208.7622\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"219.5\" x2=\"344\" y1=\"208.7622\" y2=\"208.7622\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"75\" x=\"226.5\" y=\"203.9058\">POST /token</text><polygon fill=\"#181818\" points=\"230.5,236.6182,220.5,240.6182,230.5,244.6182,226.5,240.6182\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"224.5\" x2=\"354\" y1=\"240.6182\" y2=\"240.6182\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"60\" x=\"236.5\" y=\"235.7617\">API Token</text><path d=\"M153.5,262.6182 L214.5,262.6182 L214.5,272.4741 L204.5,282.4741 L153.5,282.4741 L153.5,262.6182 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"281\" x=\"153.5\" y=\"262.6182\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"16\" x=\"168.5\" y=\"278.6177\">alt</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"103\" x=\"229.5\" y=\"277.3101\">[API Token &#47564;&#47308;&#49884;]</text><polygon fill=\"#181818\" points=\"338,302.439,348,306.439,338,310.439,342,306.439\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"219.5\" x2=\"344\" y1=\"306.439\" y2=\"306.439\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"75\" x=\"226.5\" y=\"301.5825\">POST /token</text><polygon fill=\"#181818\" points=\"230.5,334.2949,220.5,338.2949,230.5,342.2949,226.5,338.2949\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"224.5\" x2=\"354\" y1=\"338.2949\" y2=\"338.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"60\" x=\"236.5\" y=\"333.4385\">API Token</text><!--SRC=[XP2_IyD05CVdt5_npE9Y4OfJ1y6WbcAnaMGJXslwj4UJk-Fk9UWgtUmgE7GeABWMQl-ffd-4bpGW7TJjyNqVFk-7dGYfkU4PZF2UvobTAadNF4FeTozwCJuIEpoWCReWuuH6y9RAAHKI6Kz86V23TW0XDoJH-C0jv1ODSqeIYT1S4lXD5o8qXKYmflGksmVZiP0t4EJMwQs5ix1NiyDa7-jtOQ1HLdqunm9JfPlP8ooi86IiAQ1rMk_JgTahV3ggYmWJWmJRnNopMhCAgC1cfL_OwSTsySeUZCerf4ffk6sVR5_cc-KKokSlA9TlvMfznxp6KWc7IGV2GHJ3CQa9IkQvZud2VR6wo7FMtEoEYEisoX7ZAVqaK7xEolUPcyBWBo_yB_u6]--></g></svg>\n\n## 
        Device Status Search:\nTo search the status of a device, the following Device API is used.\n\n\n  - API Usage\n    - [`GET /devices`](#tag/Device-API/operation/getDevices)\n    - [`GET /devices/{deviceId}/state`](#tag/Device-API/operation/getStatusOfDevice)\n\n  - Sequence\n    1. Your service needs to use the Device List Search API(GET /devices) to retrieve the device list registered on the LG platform. This process only needs to be done once and does not need to be done every time after the list is retrieved.\n    2. Check the deviceId value of the device whose status you want to get from the device list, and call the Device Status Search API (GET /devices/profile/{device-id}) using this value.\n\n    <?xml version=\"1.0\" encoding=\"us-ascii\" standalone=\"no\"?><svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" contentStyleType=\"text/css\" height=\"258px\" preserveAspectRatio=\"none\" style=\"width:346px;height:258px;background:#FFFFFF;\" version=\"1.1\" viewBox=\"0 0 346 258\" width=\"346px\" zoomAndPan=\"magnify\"><defs/><g><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"256\" y=\"100.0503\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"256\" y=\"170.7622\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"330.5\" x=\"10\" y=\"56.2295\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"76\" x2=\"76\" y1=\"39.2295\" y2=\"220.6182\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"260.5\" x2=\"260.5\" y1=\"39.2295\" y2=\"220.6182\"/><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"20\" y=\"5\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"27\" y=\"28.1533\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"20\" y=\"219.6182\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"27\" y=\"242.7715\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"191.5\" y=\"5\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"198.5\" y=\"28.1533\">ThinQ Business API</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"191.5\" y=\"219.6182\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"198.5\" y=\"242.7715\">ThinQ Business API</text><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"256\" y=\"100.0503\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"256\" y=\"170.7622\"/><path d=\"M10,56.2295 L71,56.2295 L71,66.0854 L61,76.0854 L10,76.0854 L10,56.2295 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"330.5\" x=\"10\" y=\"56.2295\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"16\" x=\"25\" y=\"72.229\">alt</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"86\" y=\"70.9214\">[&#49352; &#47785;&#47197;&#51060; &#54596;&#50836;&#54620; &#44221;&#50864;]</text><polygon fill=\"#181818\" points=\"244,96.0503,254,100.0503,244,104.0503,248,100.0503\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"76\" x2=\"250\" y1=\"100.0503\" y2=\"100.0503\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"77\" x=\"83\" y=\"95.1938\">GET /devices</text><polygon fill=\"#181818\" points=\"87,127.9063,77,131.9063,87,135.9063,83,131.9063\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"81\" x2=\"260\" y1=\"131.9063\" y2=\"131.9063\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"82\" x=\"93\" y=\"127.0498\">&#46356;&#48148;&#51060;&#49828; &#47785;&#47197;</text><polygon fill=\"#181818\" points=\"244,166.7622,254,170.7622,244,174.7622,248,170.7622\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"76\" x2=\"250\" y1=\"170.7622\" y2=\"170.7622\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"161\" x=\"83\" y=\"165.9058\">GET /device/{deviceId}/state</text><polygon fill=\"#181818\" points=\"87,198.6182,77,202.6182,87,206.6182,83,202.6182\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"81\" x2=\"260\" y1=\"202.6182\" y2=\"202.6182\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"82\" x=\"93\" y=\"197.7617\">&#46356;&#48148;&#51060;&#49828; &#49345;&#53468;</text><!--SRC=[AyxEp2j8B4hCLKX9JKiipIbnoyyhyKlCJLNmSNVr34cjAE42IfTa9cSM9EQLA2W503bvgKKAmQb5PPd9gKeAYSKA1H0nL8KX6PbvWGfEfSMPUQd5nGgE0PvWjKd9N8av9GflcZiKNgzQ-NhXt3TpjoYydThoPjQKjrFdABpQjFVDh0rS2fnGCnLqxO1Qh1JSNKCKz5DIGLOM0sKJaqioon9BKa76SHQbbfGMvIcydZBbzOOfGEFUT2s1cisLcfV2XTia_Me8xPbIgrzS0ZIE2zbSRCQ-QMvyspm70000]--></g></svg>\n
        \n## Device Control\nTo control devices, the following Device API is used. \n\n  - API Usage\n    - [`GET /devices`](#tag/Device-API/operation/getDevices)\n    - [`GET /devices/{deviceId}/profile`](#tag/Device-API/operation/getProfileOfDevice)\n    - [`POST /devices/{deviceId}/state`](#tag/Device-API/operation/controlDevice)\n\n  - Sequence\n    1. Your service needs to use the Device List Search API(GET /devices) to retrieve the device list registered on the LG platform. This process only needs to be done once and does not need to be done every time after the list is retrieved.\n    2.  Check the deviceId value of the device to be controlled in the device list, and call the Device Profile Search API (GET /devices/profile/{device-id}) using this value.\n    3.Generate control commands for the device based on the device profile received in the API call response. The control command finds the attributes in the device profile that you want to control and expresses them as names and values.\n    4. Using the deviceId and the control command, call the Device Control API (POST /devices/{device-id}).\n    5. Get the device control result back as an API response.\n\n    <?xml version=\"1.0\" encoding=\"us-ascii\" standalone=\"no\"?><svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" contentStyleType=\"text/css\" height=\"397px\" preserveAspectRatio=\"none\" style=\"width:360px;height:397px;background:#FFFFFF;\" version=\"1.1\" viewBox=\"0 0 360 397\" width=\"360px\" zoomAndPan=\"magnify\"><defs/><g><rect fill=\"#FFFFFF\" height=\"170.4238\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"71\" y=\"170.7622\"/><rect fill=\"#FFFFFF\" height=\"28\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"76\" y=\"242.4741\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"270\" y=\"100.0503\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"270\" y=\"170.7622\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"270\" y=\"309.3301\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"344.5\" x=\"10\" y=\"56.2295\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"76\" x2=\"76\" y1=\"39.2295\" y2=\"359.186\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"274.5\" x2=\"274.5\" y1=\"39.2295\" y2=\"359.186\"/><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"20\" y=\"5\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"27\" y=\"28.1533\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"20\" y=\"358.186\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"27\" y=\"381.3394\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"205.5\" y=\"5\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"212.5\" y=\"28.1533\">ThinQ Business API</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"205.5\" y=\"358.186\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"212.5\" y=\"381.3394\">ThinQ Business API</text><rect fill=\"#FFFFFF\" height=\"170.4238\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"71\" y=\"170.7622\"/><rect fill=\"#FFFFFF\" height=\"28\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"76\" y=\"242.4741\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"270\" y=\"100.0503\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"270\" y=\"170.7622\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"270\" y=\"309.3301\"/><path d=\"M10,56.2295 L71,56.2295 L71,66.0854 L61,76.0854 L10,76.0854 L10,56.2295 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"344.5\" x=\"10\" y=\"56.2295\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"16\" x=\"25\" y=\"72.229\">alt</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"86\" y=\"70.9214\">[&#49352; &#47785;&#47197;&#51060; &#54596;&#50836;&#54620; &#44221;&#50864;]</text><polygon fill=\"#181818\" points=\"258,96.0503,268,100.0503,258,104.0503,262,100.0503\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"76\" x2=\"264\" y1=\"100.0503\" y2=\"100.0503\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"77\" x=\"83\" y=\"95.1938\">GET /devices</text><polygon fill=\"#181818\" points=\"87,127.9063,77,131.9063,87,135.9063,83,131.9063\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"81\" x2=\"274\" y1=\"131.9063\" y2=\"131.9063\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"82\" x=\"93\" y=\"127.0498\">&#46356;&#48148;&#51060;&#49828; &#47785;&#47197;</text><polygon fill=\"#181818\" points=\"258,166.7622,268,170.7622,258,174.7622,262,170.7622\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"81\" x2=\"264\" y1=\"170.7622\" y2=\"170.7622\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"166\" x=\"88\" y=\"165.9058\">GET /device/{deviceId}/profile</text><polygon fill=\"#181818\" points=\"92,198.6182,82,202.6182,92,206.6182,88,202.6182\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"86\" x2=\"274\" y1=\"202.6182\" y2=\"202.6182\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"108\" x=\"98\" y=\"197.7617\">&#46356;&#48148;&#51060;&#49828; &#54532;&#47196;&#54028;&#51068;</text><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"86\" x2=\"128\" y1=\"234.4741\" y2=\"234.4741\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"128\" x2=\"128\" y1=\"234.4741\" y2=\"247.4741\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"87\" x2=\"128\" y1=\"247.4741\" y2=\"247.4741\"/><polygon fill=\"#181818\" points=\"97,243.4741,87,247.4741,97,251.4741,93,247.4741\" style=\"stroke:#181818;stroke-width:1.0;\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"56\" x=\"93\" y=\"229.6177\">&#47749;&#47161; &#49373;&#49457;</text><polygon fill=\"#181818\" points=\"258,305.3301,268,309.3301,258,313.3301,262,309.3301\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"81\" x2=\"264\" y1=\"309.3301\" y2=\"309.3301\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"170\" x=\"88\" y=\"304.4736\">POST /device/{deviceId}/state</text><polygon fill=\"#181818\" points=\"87,337.186,77,341.186,87,345.186,83,341.186\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"81\" x2=\"274\" y1=\"341.186\" y2=\"341.186\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"56\" x=\"93\" y=\"336.3296\">&#47749;&#47161; &#44208;&#44284;</text><!--SRC=[TOzFIyCm68VFwwTusLrwtq5GcACWMbc_G6pVOR3BIf8EGJnPGMJ7xZ9MSE15JtNk8imlrAJVmSnMcQwUahn_dkSNSKbPH3WPGe034eVoQCJa2HaY7FUwZeTNqZ9jINqQ4IQXxPe7Gmvzv6FgOnk8WAYg_HxqBYWxWyDOK8P2m87hVCsU-nO99UZRUr0lpsgHwMm5vJJHixISpg5OVkXPRa6hPiBUlbdfGA_hWHtWHYbCb_YIZed43Qx5KSQSWKfJbQS6fn-UQhQ5BB3-9zdNrUa4DtR4HmCQelL3_lxKjgh9LAQ9MipBoKHdwsrNVUsOA7VgyTtyEDF9wou_m9tIdyJkQRynif1cgJ5VPIoMUV6sRX1y0W00]--></g></svg>\n\n## 
        Device Push Subscription\nUses the Event API to subscribe to push notifications on a device (Currently, only home appliances registered on LG ThinQ are supported.)\n\n  - API Usage\n    - [`GET /devices`](#tag/Device-API/operation/getDevices)\n    - [`POST /push/{deviceId}/subscribe`](#tag/Event-API/operation/subscribePushMessages)\n\n  - Sequence\n    1.  Your service needs to use the Device List Search API(GET /devices) to retrieve the device list registered on the LG platform. This process only needs to be done once and does not need to be done every time after the list is retrieved.\n    2.  Check the deviceId value of the device you want to receive push notifications for from the device list, and call the Device Notification Subscription API (POST /push/{deviceId}) using this value.\n    3. Generate control commands for the device based on the device profile received in the API call response. The control command finds the attributes in the device profile that you want to control and expresses them as names and values. \_\n    4. Using the deviceId and the control command, call the Device Control API (POST /devices/{device-id}).\_\n\n    <?xml version=\"1.0\" encoding=\"us-ascii\" standalone=\"no\"?><svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" contentStyleType=\"text/css\" height=\"356px\" preserveAspectRatio=\"none\" style=\"width:441px;height:356px;background:#FFFFFF;\" version=\"1.1\" viewBox=\"0 0 441 356\" width=\"441px\" zoomAndPan=\"magnify\"><defs/><g><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"284\" y=\"100.0503\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"284\" y=\"170.7622\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"358.5\" x=\"10\" y=\"56.2295\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"425.5\" x=\"10\" y=\"217.6182\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"76\" x2=\"76\" y1=\"39.2295\" y2=\"318.2949\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"288.5\" x2=\"288.5\" y1=\"39.2295\" y2=\"318.2949\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"396.5\" x2=\"396.5\" y1=\"39.2295\" y2=\"318.2949\"/><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"20\" y=\"5\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"27\" y=\"28.1533\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"20\" y=\"317.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"27\" y=\"340.4482\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"219.5\" y=\"5\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"226.5\" y=\"28.1533\">ThinQ Business API</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"219.5\" y=\"317.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"226.5\" y=\"340.4482\">ThinQ Business API</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"57\" x=\"368.5\" y=\"5\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"43\" x=\"375.5\" y=\"28.1533\">Device</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"57\" x=\"368.5\" y=\"317.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"43\" x=\"375.5\" y=\"340.4482\">Device</text><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"284\" y=\"100.0503\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"284\" y=\"170.7622\"/><path d=\"M10,56.2295 L71,56.2295 L71,66.0854 L61,76.0854 L10,76.0854 L10,56.2295 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"358.5\" x=\"10\" y=\"56.2295\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"16\" x=\"25\" y=\"72.229\">alt</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"86\" y=\"70.9214\">[&#49352; &#47785;&#47197;&#51060; &#54596;&#50836;&#54620; &#44221;&#50864;]</text><polygon fill=\"#181818\" points=\"272,96.0503,282,100.0503,272,104.0503,276,100.0503\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"76\" x2=\"278\" y1=\"100.0503\" y2=\"100.0503\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"77\" x=\"83\" y=\"95.1938\">GET /devices</text><polygon fill=\"#181818\" points=\"87,127.9063,77,131.9063,87,135.9063,83,131.9063\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"81\" x2=\"288\" y1=\"131.9063\" y2=\"131.9063\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"82\" x=\"93\" y=\"127.0498\">&#46356;&#48148;&#51060;&#49828; &#47785;&#47197;</text><polygon fill=\"#181818\" points=\"272,166.7622,282,170.7622,272,174.7622,276,170.7622\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"76\" x2=\"278\" y1=\"170.7622\" y2=\"170.7622\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"189\" x=\"83\" y=\"165.9058\">POST /push/{deviceId}/subscribe</text><polygon fill=\"#181818\" points=\"87,198.6182,77,202.6182,87,206.6182,83,202.6182\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"81\" x2=\"288\" y1=\"202.6182\" y2=\"202.6182\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"32\" x=\"93\" y=\"197.7617\">result</text><path d=\"M10,217.6182 L71,217.6182 L71,227.4741 L61,237.4741 L10,237.4741 L10,217.6182 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"83.6768\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"425.5\" x=\"10\" y=\"217.6182\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"16\" x=\"25\" y=\"233.6177\">alt</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"149\" x=\"86\" y=\"232.3101\">[&#54392;&#49884; &#47700;&#49884;&#51648;&#44032; &#48156;&#49373;&#54620; &#44221;&#50864;]</text><polygon fill=\"#181818\" points=\"300,257.439,290,261.439,300,265.439,296,261.439\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"294\" x2=\"396\" y1=\"261.439\" y2=\"261.439\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"69\" x=\"306\" y=\"256.5825\">&#54392;&#49884; &#47700;&#49884;&#51648;</text><polygon fill=\"#181818\" points=\"87,289.2949,77,293.2949,87,297.2949,83,293.2949\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"81\" x2=\"288\" y1=\"293.2949\" y2=\"293.2949\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"69\" x=\"93\" y=\"288.4385\">&#54392;&#49884; &#47700;&#49884;&#51648;</text><!--SRC=[RP11IyCm68RFpQ_us5rwzo0epZ4GhQn_84q_MN2B9Kc78C9W7aHFGdSPxK4GP9wAUF3Y7rhI_s3MLjc6foJV-txF-n9rnKL29Hr3Z9Sq7UcJQw7Fw1ZXjDVjXtYZYPCrPpoXGaCdS0-14WOe9vnX1wY2f9bj6yCX5nTmb2ekK2au3FgrDsBRjcFymyJrbT2H1Zjx0FE-D2-5BJwXcj_RHLRDSrXzVDj5IS1h8s7lm17teTSDmM_sbLCfqtn2DQxJF8awbG9CbfaoSpZx-Dgo2OgOx922yu539QaQ-hSDi1_V-IgD59CySkqsq2rPedB_LlUkdh_iKmvccRd3larNvHHCcTjPiT7UQxY_YRixn8lOMckB_MDmjNy0]--></g></svg>\n\n##
        Registering users for the DR service\nAfter consulting with LG Electronics' API manager in advance, B2B partners can register users for the DR service using a DR API..\n\n\n  - API Usage\n    - [`POST /dr/users`](#tag/DR-API/operation/createDrUser)\n\n  - Sequence\n    1.LG Electronics users must be signed up for the LG ThinQ service and the LG home appliances that will be registered for the partner's DR service must be registered. .\n    2. The LG Electronics user attempts to sign up for the B2B partner's DR service.\n    3. According to the OAuth 2.0 integration procedure of the LGE Members Platform (LMP), the partner service provides LG Electronics' login screen to the DR service and obtains OAuth integration information .\n    4. LG Electronics' DR service acquires the OAuth integration information of the partner service according to the integration interface pre-defined with the partner service and saves the result of the partner service's user information API. \n    5. When an LG Electronics user assigns a home and device to register with the DR service on the LG ThinQ mobile app, LG Electronics' DR service registers the device as a DR device.\n\n    <?xml version=\"1.0\" encoding=\"us-ascii\" standalone=\"no\"?><svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" contentStyleType=\"text/css\" height=\"698px\" preserveAspectRatio=\"none\" style=\"width:819px;height:698px;background:#FFFFFF;\" version=\"1.1\" viewBox=\"0 0 819 698\" width=\"819px\" zoomAndPan=\"magnify\"><defs/><g><rect fill=\"#DDDDDD\" height=\"686.2983\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"223\" x=\"150.5\" y=\"6\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"99\" x=\"212.5\" y=\"20.9995\">Partner Service</text><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"266\" y=\"436.645\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"337.5\" y=\"372.9331\"/><rect fill=\"#FFFFFF\" height=\"40.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"427\" y=\"560.2129\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"574.5\" y=\"213.6533\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"574.5\" y=\"277.3652\"/><rect fill=\"#FFFFFF\" height=\"141.4238\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"739\" y=\"341.0771\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"37\" x2=\"37\" y1=\"84.2295\" y2=\"610.0688\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"190.5\" x2=\"190.5\" y1=\"84.2295\" y2=\"610.0688\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"270.5\" x2=\"270.5\" y1=\"84.2295\" y2=\"610.0688\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"342.5\" x2=\"342.5\" y1=\"84.2295\" y2=\"610.0688\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"431.5\" x2=\"431.5\" y1=\"84.2295\" y2=\"610.0688\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"579.5\" x2=\"579.5\" y1=\"84.2295\" y2=\"610.0688\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"743.5\" x2=\"743.5\" y1=\"84.2295\" y2=\"610.0688\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"59\" x=\"5\" y=\"81.1533\">End-User</text><ellipse cx=\"37.5\" cy=\"13.5\" fill=\"#E2E2F0\" rx=\"8\" ry=\"8\" style=\"stroke:#181818;stroke-width:0.5;\"/><path d=\"M37.5,21.5 L37.5,48.5 M24.5,29.5 L50.5,29.5 M37.5,48.5 L24.5,63.5 M37.5,48.5 L50.5,63.5 \" fill=\"none\" style=\"stroke:#181818;stroke-width:0.5;\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"59\" x=\"5\" y=\"625.2222\">End-User</text><ellipse cx=\"37.5\" cy=\"636.7983\" fill=\"#E2E2F0\" rx=\"8\" ry=\"8\" style=\"stroke:#181818;stroke-width:0.5;\"/><path d=\"M37.5,644.7983 L37.5,671.7983 M24.5,652.7983 L50.5,652.7983 M37.5,671.7983 L24.5,686.7983 M37.5,671.7983 L50.5,686.7983 \" fill=\"none\" style=\"stroke:#181818;stroke-width:0.5;\"/><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"72\" x=\"154.5\" y=\"50\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"58\" x=\"161.5\" y=\"73.1533\">Frontend</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"72\" x=\"154.5\" y=\"609.0688\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"58\" x=\"161.5\" y=\"632.2222\">Frontend</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"69\" x=\"236.5\" y=\"50\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"55\" x=\"243.5\" y=\"73.1533\">Backend</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"69\" x=\"236.5\" y=\"609.0688\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"55\" x=\"243.5\" y=\"632.2222\">Backend</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"54\" x=\"315.5\" y=\"50\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"40\" x=\"322.5\" y=\"73.1533\">OAuth</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"54\" x=\"315.5\" y=\"609.0688\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"40\" x=\"322.5\" y=\"632.2222\">OAuth</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"105\" x=\"379.5\" y=\"50\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"91\" x=\"386.5\" y=\"73.1533\">LG ThinQ App</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"105\" x=\"379.5\" y=\"609.0688\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"91\" x=\"386.5\" y=\"632.2222\">LG ThinQ App</text><rect fill=\"#E2E2F0\" height=\"52.459\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"170\" x=\"494.5\" y=\"30.7705\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"72\" x=\"543.5\" y=\"53.9238\">LMP OAuth</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"156\" x=\"501.5\" y=\"73.1533\">(LGE Members Platform)</text><rect fill=\"#E2E2F0\" height=\"52.459\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"170\" x=\"494.5\" y=\"609.0688\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"72\" x=\"543.5\" y=\"632.2222\">LMP OAuth</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"156\" x=\"501.5\" y=\"651.4517\">(LGE Members Platform)</text><rect fill=\"#E2E2F0\" height=\"52.459\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"674.5\" y=\"30.7705\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"681.5\" y=\"53.9238\">ThinQ Business API</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"81\" x=\"703.5\" y=\"73.1533\">(DR Service)</text><rect fill=\"#E2E2F0\" height=\"52.459\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"674.5\" y=\"609.0688\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"681.5\" y=\"632.2222\">ThinQ Business API</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"81\" x=\"703.5\" y=\"651.4517\">(DR Service)</text><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"266\" y=\"436.645\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"337.5\" y=\"372.9331\"/><rect fill=\"#FFFFFF\" height=\"40.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"427\" y=\"560.2129\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"574.5\" y=\"213.6533\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"574.5\" y=\"277.3652\"/><rect fill=\"#FFFFFF\" height=\"141.4238\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"739\" y=\"341.0771\"/><polygon fill=\"#181818\" points=\"420,114.0854,430,118.0854,420,122.0854,424,118.0854\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"37.5\" x2=\"426\" y1=\"118.0854\" y2=\"118.0854\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"238\" x=\"44.5\" y=\"113.229\">&#46356;&#48148;&#51060;&#49828; &#46321;&#47197; : Air Conditioner, ESS, TV</text><polygon fill=\"#181818\" points=\"178.5,145.9414,188.5,149.9414,178.5,153.9414,182.5,149.9414\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"37.5\" x2=\"184.5\" y1=\"149.9414\" y2=\"149.9414\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"104\" x=\"44.5\" y=\"145.085\">DR &#49436;&#48708;&#49828;&#50640; &#44032;&#51077;</text><polygon fill=\"#181818\" points=\"48.5,177.7974,38.5,181.7974,48.5,185.7974,44.5,181.7974\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"42.5\" x2=\"189.5\" y1=\"181.7974\" y2=\"181.7974\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"129\" x=\"54.5\" y=\"176.9409\">LG&#51204;&#51088; &#47196;&#44536;&#51064; &#54168;&#51060;&#51648;</text><polygon fill=\"#181818\" points=\"562.5,209.6533,572.5,213.6533,562.5,217.6533,566.5,213.6533\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"37.5\" x2=\"568.5\" y1=\"213.6533\" y2=\"213.6533\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"116\" x=\"44.5\" y=\"208.7969\">LG&#51204;&#51088; &#44228;&#51221; &#47196;&#44536;&#51064;</text><polygon fill=\"#181818\" points=\"282,241.5093,272,245.5093,282,249.5093,278,245.5093\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"276\" x2=\"578.5\" y1=\"245.5093\" y2=\"245.5093\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"106\" x=\"288\" y=\"240.6528\">authorization code</text><polygon fill=\"#181818\" points=\"562.5,273.3652,572.5,277.3652,562.5,281.3652,566.5,277.3652\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"271\" x2=\"568.5\" y1=\"277.3652\" y2=\"277.3652\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"108\" x=\"278\" y=\"272.5088\">access token &#50836;&#52397;</text><polygon fill=\"#181818\" points=\"282,305.2212,272,309.2212,282,313.2212,278,309.2212\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"276\" x2=\"578.5\" y1=\"309.2212\" y2=\"309.2212\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"78\" x=\"288\" y=\"304.3647\">access token</text><polygon fill=\"#181818\" points=\"727,337.0771,737,341.0771,727,345.0771,731,341.0771\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"271\" x2=\"733\" y1=\"341.0771\" y2=\"341.0771\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"171\" x=\"278\" y=\"336.2207\">&#49324;&#50857;&#51088; &#49373;&#49457; (POST /dr/users)</text><polygon fill=\"#181818\" points=\"358.5,368.9331,348.5,372.9331,358.5,376.9331,354.5,372.9331\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"352.5\" x2=\"738\" y1=\"372.9331\" y2=\"372.9331\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"151\" x=\"364.5\" y=\"368.0767\">access/refresh token &#50836;&#52397;</text><polygon fill=\"#181818\" points=\"727,400.7891,737,404.7891,727,408.7891,731,404.7891\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"342.5\" x2=\"733\" y1=\"404.7891\" y2=\"404.7891\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"121\" x=\"349.5\" y=\"399.9326\">access/refresh token</text><polygon fill=\"#181818\" points=\"287,432.645,277,436.645,287,440.645,283,436.645\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"281\" x2=\"738\" y1=\"436.645\" y2=\"436.645\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"99\" x=\"293\" y=\"431.7886\">&#49324;&#50857;&#51088; &#51221;&#48372; &#50836;&#52397;</text><polygon fill=\"#181818\" points=\"727,464.501,737,468.501,727,472.501,731,468.501\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"271\" x2=\"733\" y1=\"468.501\" y2=\"468.501\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"69\" x=\"278\" y=\"463.6445\">&#49324;&#50857;&#51088; &#51221;&#48372;</text><polygon fill=\"#181818\" points=\"282,478.501,272,482.501,282,486.501,278,482.501\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"276\" x2=\"743\" y1=\"482.501\" y2=\"482.501\"/><polygon fill=\"#181818\" points=\"201.5,492.501,191.5,496.501,201.5,500.501,197.5,496.501\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"195.5\" x2=\"270\" y1=\"496.501\" y2=\"496.501\"/><polygon fill=\"#181818\" points=\"48.5,524.3569,38.5,528.3569,48.5,532.3569,44.5,528.3569\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"42.5\" x2=\"189.5\" y1=\"528.3569\" y2=\"528.3569\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"72\" x=\"54.5\" y=\"523.5005\">LG ThinQ &#50545;</text><polygon fill=\"#181818\" points=\"415,556.2129,425,560.2129,415,564.2129,419,560.2129\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"37.5\" x2=\"421\" y1=\"560.2129\" y2=\"560.2129\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"164\" x=\"44.5\" y=\"555.3564\">DR &#45824;&#49345; &#54856;&#44284; &#46356;&#48148;&#51060;&#49828; &#49440;&#53469;</text><polygon fill=\"#181818\" points=\"732,588.0688,742,592.0688,732,596.0688,736,592.0688\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"437\" x2=\"738\" y1=\"592.0688\" y2=\"592.0688\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"134\" x=\"444\" y=\"587.2124\">DR &#45824;&#49345; &#54856;&#44284; &#46356;&#48148;&#51060;&#49828;</text><!--SRC=[XL91QnD15BxFhtZarDA67Bpr8AIQba9hLnCzUPdiJCZGxEmoEod5KpGhY8WKJ51BKr8GH51eJC4A_gBiv3_uPj8akodeddPclkzxxttVYu-4ZAYY0J3UeEsMtWcbVaG33lkxbRqQFz64-ZfKKAX8LdmQSrK06aCRVqWzF862HvMMN46LgsFXym81_51H2rz4L6eex2YKv98vuZt56lPy5xPD_QCCgex7kw33Sbitvn1t8CW1x8JaSFkxK6iA-HZAKUJWD8e0LZ077ZY9vt8DXuK37jIvYi5hKTq8LR3kYAqWojDckjljM4WUnr3szf3_yCdSW1cBAKAiHr2yxqflGThhfLSzCxWsRxz0-c6KNWxmjYmKF0Wb4rg4wE8cLAhLJQWzMv3dVY4MQvZaFFsTe8BvU0gJguwvU4qMY2B27MqBipF3n5oSGdfvFlbrOmOtC7t_oHR_sbb8usHPw6ISc65_oR2vYsEgkRF0WekpVcmoIAJeNAZ42sfR1pzad32UuyonireR6vRa-zOq7MBKOCvwvkSFehXkAvbx8bakKuvgNdqtPzzifwOxCCa8rhp3QWrAJ9NiHF4wONF7NAgPUYN56uh7pN_KpKEMKhQ9rVB3VZg-Nb5PVRwzNywHoJ8JMIQnsuKr_L5sSrnjJ3vzrp7Tbp3z_6Oo_fDV9fCCfzq1iMlctFeVuIy0]--></g></svg>\n\n\n## 
        Creating a DR event and downloading monitoring data\nDescribes the process of registering a DR event and downloading monitoring data for a device before and after the DR event.\n\n  -API Usage\n    - [`POST /dr/events`](#tag/DR-API/operation/createDrEvent)\n    - [`POST /dr/events/{eventId}/targets`](#tag/DR-API/operation/createEventTarget)\n    - [`POST /dr/events/{eventId}/targets/{targetId}`](#tag/DR-API/operation/updateEventTarget)\n    - [`POST /dr/events/{eventId}/targets/batch`](#tag/DR-API/operation/createEventTargetBatch)\n    - [`POST /dr/events/{eventId}/targets/batch`](#tag/DR-API/operation/createEventTargetBatch)\n    - [`POST /dr/data-zip/files`](#tag/DR-API/operation/createDataZipFile)\n    - [`POST /dr/data-zip/files/{filename}`](#tag/DR-API/operation/downloadDataZipFile)\n\n  - Sequence\n    1.Call the DR Event Registration API (POST /dr/events) to register DR events on the LG DR service server.\n    2. When the DR event is successfully registered, the DR event ID (eventId) is retrieved.\n    3. If the list of the devices that need to be participated in the DR event needs to be modified after the DR event has been created, call the DR Event Target Modification API.\n    4. After the DR event ends, download the monitoring data of the device within the DR event period.\n\n    <?xml version=\"1.0\" encoding=\"us-ascii\" standalone=\"no\"?><svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" contentStyleType=\"text/css\" height=\"760px\" preserveAspectRatio=\"none\" style=\"width:517px;height:760px;background:#FFFFFF;\" version=\"1.1\" viewBox=\"0 0 517 760\" width=\"517px\" zoomAndPan=\"magnify\"><defs/><g><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"119.1709\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"209.8477\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"290.6685\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"371.4893\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"519.166\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"582.8779\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"463.5\" y=\"646.5898\"/><rect fill=\"none\" height=\"342.8862\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"435.5\" x=\"10\" y=\"75.459\"/><rect fill=\"none\" height=\"245.3184\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"415.5\" x=\"20\" y=\"166.0269\"/><rect fill=\"none\" height=\"210.9917\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"491.5\" x=\"20\" y=\"475.4541\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"86\" x2=\"86\" y1=\"58.459\" y2=\"425.3452\"/><line style=\"stroke:#A80036;stroke-width:1.0;stroke-dasharray:1.0,4.0;\" x1=\"86\" x2=\"86\" y1=\"425.3452\" y2=\"468.4541\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"86\" x2=\"86\" y1=\"468.4541\" y2=\"703.4458\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"355.5\" x2=\"355.5\" y1=\"58.459\" y2=\"425.3452\"/><line style=\"stroke:#A80036;stroke-width:1.0;stroke-dasharray:1.0,4.0;\" x1=\"355.5\" x2=\"355.5\" y1=\"425.3452\" y2=\"468.4541\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"355.5\" x2=\"355.5\" y1=\"468.4541\" y2=\"703.4458\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"468.5\" x2=\"468.5\" y1=\"58.459\" y2=\"425.3452\"/><line style=\"stroke:#A80036;stroke-width:1.0;stroke-dasharray:1.0,4.0;\" x1=\"468.5\" x2=\"468.5\" y1=\"425.3452\" y2=\"468.4541\"/><line style=\"stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;\" x1=\"468.5\" x2=\"468.5\" y1=\"468.4541\" y2=\"703.4458\"/><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"30\" y=\"24.2295\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"37\" y=\"47.3828\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"112\" x=\"30\" y=\"702.4458\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"98\" x=\"37\" y=\"725.5991\">Partner Service</text><rect fill=\"#E2E2F0\" height=\"52.459\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"286.5\" y=\"5\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"293.5\" y=\"28.1533\">ThinQ Business API</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"81\" x=\"315.5\" y=\"47.3828\">(DR Service)</text><rect fill=\"#E2E2F0\" height=\"52.459\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"139\" x=\"286.5\" y=\"702.4458\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"125\" x=\"293.5\" y=\"725.5991\">ThinQ Business API</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"81\" x=\"315.5\" y=\"744.8286\">(DR Service)</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"66\" x=\"435.5\" y=\"24.2295\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"52\" x=\"442.5\" y=\"47.3828\">AWS S3</text><rect fill=\"#E2E2F0\" height=\"33.2295\" rx=\"2.5\" ry=\"2.5\" style=\"stroke:#181818;stroke-width:0.5;\" width=\"66\" x=\"435.5\" y=\"702.4458\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"14\" lengthAdjust=\"spacing\" textLength=\"52\" x=\"442.5\" y=\"725.5991\">AWS S3</text><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"119.1709\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"209.8477\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"290.6685\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"371.4893\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"519.166\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"351\" y=\"582.8779\"/><rect fill=\"#FFFFFF\" height=\"31.856\" style=\"stroke:#181818;stroke-width:1.0;\" width=\"10\" x=\"463.5\" y=\"646.5898\"/><path d=\"M10,75.459 L151,75.459 L151,85.3149 L141,95.3149 L10,95.3149 L10,75.459 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"342.8862\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"435.5\" x=\"10\" y=\"75.459\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"96\" x=\"25\" y=\"91.4585\">DR &#51060;&#48292;&#53944; &#49373;&#49457;</text><polygon fill=\"#181818\" points=\"339,115.1709,349,119.1709,339,123.1709,343,119.1709\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"86\" x2=\"345\" y1=\"119.1709\" y2=\"119.1709\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"95\" x=\"93\" y=\"114.3145\">POST /dr/events</text><polygon fill=\"#181818\" points=\"97,147.0269,87,151.0269,97,155.0269,93,151.0269\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"91\" x2=\"355\" y1=\"151.0269\" y2=\"151.0269\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"32\" x=\"103\" y=\"146.1704\">result</text><path d=\"M20,166.0269 L81,166.0269 L81,175.8828 L71,185.8828 L20,185.8828 L20,166.0269 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"245.3184\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"415.5\" x=\"20\" y=\"166.0269\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"16\" x=\"35\" y=\"182.0264\">alt</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"200\" x=\"96\" y=\"180.7188\">[&#51060;&#48292;&#53944; &#53440;&#44191;&#51060; &#52628;&#44032;&#46104;&#50612;&#50556; &#54616;&#45716; &#44221;&#50864;]</text><polygon fill=\"#181818\" points=\"339,205.8477,349,209.8477,339,213.8477,343,209.8477\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"86\" x2=\"345\" y1=\"209.8477\" y2=\"209.8477\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"191\" x=\"93\" y=\"204.9912\">POST /dr/events/{eventId}/targets</text><polygon fill=\"#181818\" points=\"97,237.7036,87,241.7036,97,245.7036,93,241.7036\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"91\" x2=\"355\" y1=\"241.7036\" y2=\"241.7036\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"32\" x=\"103\" y=\"236.8472\">result</text><line style=\"stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"20\" x2=\"435.5\" y1=\"250.7036\" y2=\"250.7036\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"227\" x=\"25\" y=\"263.3955\">[&#53945;&#51221; &#51060;&#48292;&#53944; &#53440;&#44191;&#51060; &#49688;&#51221;&#46104;&#50612;&#50556; &#54616;&#45716; &#44221;&#50864;]</text><polygon fill=\"#181818\" points=\"339,286.6685,349,290.6685,339,294.6685,343,290.6685\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"86\" x2=\"345\" y1=\"290.6685\" y2=\"290.6685\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"246\" x=\"93\" y=\"285.812\">POST /dr/events/{eventId}/targets/{targetId}</text><polygon fill=\"#181818\" points=\"97,318.5244,87,322.5244,97,326.5244,93,322.5244\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"91\" x2=\"355\" y1=\"322.5244\" y2=\"322.5244\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"32\" x=\"103\" y=\"317.668\">result</text><line style=\"stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"20\" x2=\"435.5\" y1=\"331.5244\" y2=\"331.5244\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"227\" x=\"25\" y=\"344.2163\">[&#51060;&#48292;&#53944; &#53440;&#44191;&#51060; &#51068;&#44292; &#49373;&#49457;&#46104;&#50612;&#50556; &#54616;&#45716; &#44221;&#50864;]</text><polygon fill=\"#181818\" points=\"339,367.4893,349,371.4893,339,375.4893,343,371.4893\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"86\" x2=\"345\" y1=\"371.4893\" y2=\"371.4893\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"227\" x=\"93\" y=\"366.6328\">POST /dr/events/{eventId}/targets/batch</text><polygon fill=\"#181818\" points=\"97,399.3452,87,403.3452,97,407.3452,93,403.3452\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"91\" x2=\"355\" y1=\"403.3452\" y2=\"403.3452\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"32\" x=\"103\" y=\"398.4888\">result</text><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"11\" lengthAdjust=\"spacing\" textLength=\"93\" x=\"232.25\" y=\"452.0371\">&lt; DR &#51060;&#48292;&#53944; &#49892;&#54665; &gt;</text><path d=\"M20,475.4541 L227,475.4541 L227,485.3101 L217,495.3101 L20,495.3101 L20,475.4541 \" fill=\"#EEEEEE\" style=\"stroke:#000000;stroke-width:1.5;\"/><rect fill=\"none\" height=\"210.9917\" style=\"stroke:#000000;stroke-width:1.5;\" width=\"491.5\" x=\"20\" y=\"475.4541\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" font-weight=\"bold\" lengthAdjust=\"spacing\" textLength=\"162\" x=\"35\" y=\"491.4536\">&#47784;&#45768;&#53552;&#47553; &#45936;&#51060;&#53552; &#45796;&#50868;&#47196;&#46300;</text><polygon fill=\"#181818\" points=\"339,515.166,349,519.166,339,523.166,343,519.166\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"86\" x2=\"345\" y1=\"519.166\" y2=\"519.166\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"131\" x=\"93\" y=\"514.3096\">POST /dr/data-zip/files</text><polygon fill=\"#181818\" points=\"97,547.022,87,551.022,97,555.022,93,551.022\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"91\" x2=\"355\" y1=\"551.022\" y2=\"551.022\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"39\" x=\"103\" y=\"546.1655\">&#54028;&#51068;&#47749;</text><polygon fill=\"#181818\" points=\"339,578.8779,349,582.8779,339,586.8779,343,582.8779\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"86\" x2=\"345\" y1=\"582.8779\" y2=\"582.8779\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"191\" x=\"93\" y=\"578.0215\">POST /dr/data-zip/files/{filename}</text><polygon fill=\"#181818\" points=\"97,610.7339,87,614.7339,97,618.7339,93,614.7339\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"91\" x2=\"355\" y1=\"614.7339\" y2=\"614.7339\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"112\" x=\"103\" y=\"609.8774\">&#54028;&#51068; &#45796;&#50868;&#47196;&#46300; &#51221;&#48372;</text><polygon fill=\"#181818\" points=\"451.5,642.5898,461.5,646.5898,451.5,650.5898,455.5,646.5898\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;\" x1=\"86\" x2=\"457.5\" y1=\"646.5898\" y2=\"646.5898\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"82\" x=\"93\" y=\"641.7334\">&#54028;&#51068; &#45796;&#50868;&#47196;&#46300;</text><polygon fill=\"#181818\" points=\"97,674.4458,87,678.4458,97,682.4458,93,678.4458\" style=\"stroke:#181818;stroke-width:1.0;\"/><line style=\"stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;\" x1=\"91\" x2=\"467.5\" y1=\"678.4458\" y2=\"678.4458\"/><text fill=\"#000000\" font-family=\"LGEIText\" font-size=\"13\" lengthAdjust=\"spacing\" textLength=\"26\" x=\"103\" y=\"673.5894\">&#54028;&#51068;</text><!--SRC=[jLFBIiD05DtdAowk5B5PT2SYA3ueY5PJSEDcR4ORJASXCorY4HGhQ5j1i2r5B2eKbAvY3Q9GVoWp-GUdQGlM1XyB0yFDVPmpPoOdTCyW5h9H6dIyWx8cMyeGjehI65QM5sC9lCyKsMP6qh0GOJ0Mbmd1DcZOpXb9F0Q8WjMh3GycKWPPX_aiDGYc5ERYiIqolh0n04u4IFqBQ6vJ0oqQj6XKKNRjJDO22H8DbxURVl4Ln4b359uKa4z_MvYQbJoJap0DyJKj0QfkgpY72QF1b8rPrYOoK7cue89CzedGFpdoshSo1_5IyPmZVbaNDLTKE-1NwxnO0Q_zBgwT0FchNTLy46FweSgGlOlxEiArO9DYy8jluguQhkciBbl_e4dDzrvawITveReQ7SyjzB_6VyZRHYoP-auPqPNkKYAH2CnyyKYfwTVEOLQs1XxYhKTUElCB3dyu1dxXo66P02yrnRNBxs_urSrFdj8HGrC7XgNk62OUyfPVBilxuArJvMySQhuRYFpP3aVfXhH1rmJFxWW_ZGRy8OXHmk2wFW00]--></g></svg>\n"
      - name: Base URL
        description: |
          The ThinQ Business API distinguishes the Base URL according to the location of the customer's device. Therefore, select and apply the Base URL when calling the API by considering the region where the customer's device is located or the region where the B2B partner's business is located. Also, please note that the Base URLs for the Production environment and Simulator Testing environment are different, as follows. 
          ## Production Environment
          Use the Base URL below to call the ThinQ Business API by utilizing the Business API Key in the production environment.  

            |Region|API Token Issuance API|ThinQ Business API|
            |-|-|-|
            |South Asia, East Asia and Pacific|https://ap.api.lge.com|https://ap.api.lge.com/biz/v1|
            |America|https://us.api.lge.com|https://us.api.lge.com/biz/v1|
            |Europe, Middle East, Africa|https://eu.api.lge.com|https://eu.api.lge.com/biz/v1|

            
          ## Simulator Testing Environment
          Use the Base URL below to call the ThinQ Business API by utilizing the Test API Key in the Simulator Testing environment.

            |Region|API Token Issuance API|ThinQ Business API|
            |-|-|-|
            |South Asia, East Asia and Pacific|https://ap-test.api.lge.com|https://ap-test.api.lge.com/biz/v1|
            |America|https://us-test.api.lge.com|https://us-test.api.lge.com/biz/v1|
            |Europe, Middle East, Africa|https://eu-test.api.lge.com|https://eu-test.api.lge.com/biz/v1|      
           
      - name: Codes
        x-displayName: Define the code
        description: |
          Describes the types of code you can refer to when utilizing the ThinQ Business API.
          ## Country Code
          The country code used in ThinQ Business API Call supports the `ISO-3166 alpha-2` specification and can be used for countries, where LG ThinQ service is available. The supported country codes are shown in the table below.


            | Code | Name          | Code | Name         | Code | Name          | Code | Name          | Code | Name           | Code | Name         | Code | Name         | Code | Name         |
            |-----------|------------------|-----------|------------------|-----------|------------------|-----------|------------------|-----------|------------------|-----------|------------------|-----------|------------------|-----------|------------------|
            | KR | South Korea | GH | Ghana | GA | Gabon | GY | Guyana | GM | Gambia | GT | Guatemala | GD | Grenada | GR | Greece |
            | GN | Guinea | NG | Nigeria | ZA | South Africa| NL | Netherlands| NO | Norway| NZ | New Zealand| NE | Niger | NI | Nicaragua|
            | TW | Taiwan | DK | Denmark | DM | Dominica | DO | Dominican Republic | DE | Germany | LR | Liberia | LV | Latvia | RU | Russia |
            | LB | Lebanon | RO | Romania| LU | Luxembourg | RW | Rwanda | LY | Libya | LT | Lithuania | MK | Macedonia | MY | Malaysia |
            | ML | Mali | MX | Mexico | MA | Morocco | MU | Mauritius | ME | Montenegro | MD | Moldova | MT | Malta | US | United States |
            | MM | Myanmar | BH | Bahrain | BB | Barbados | BS | Bahamas | BD | Bangladesh | BJ | Benin | VE | Venezuela | VN | Vietnam |
            | BE | Belgium | BY | Belarus | BZ | Belize | BA | Bosnia | BO | Bolivia | BF | Burkina Faso | BG | Bulgaria | BR | Brazil |
            | SA | Saudi Arabia | ST | São Tomé and Príncipe | SN | Senegal | RS | Serbia | LC | Saint Lucia | VC | Saint Vincent and the Grenadines | KN | Saint Kitts and Nevis | SO | Somalia
            | SD | Sudan | SR | Suriname | LK | Sri Lanka| SE | Sweden | CH | Switzerland | ES | Spain | SK | Slovakia | SI | Slovenia |
            | SY | Syria | SL | Sierra Leone | SG | Singapore | AE | United Arab Emirates | AM | Armenia | AR | Argentina | IS | Iceland | HT | Haiti |
            | IE | Ireland | AZ | Azerbaijan | AL | Albania | DZ | Algeria | AO | Angola | AG | Antigua and Barbuda | EE | Estonia | EC | Ecuador |
            | SV | El Salvador | GB | United Kingdom | YE | Yemen | OM | Oman | AT | Austria | HN | Honduras | JO | Jordan | UG | Uganda | Ethiopia | IQ | Iraq | IR | Iran | IL | Israel | EG | Egypt
            | UY | Uruguay| UZ | Uzbekistan | UA | Ukraine | ET | Ethiopia | IQ | Iraq | IR | Iran | IL | Israel | EG | Egypt |
            | IT | Italy | IN | India | ID | Indonesia | JP | Japan | JM | Jamaica | ZM | Zambia | GQ | Equatorial Guinea | GE | Georgia |
            | CN | China | CF | Central African Republic | DJ | Djibouti | TD | Chad | CZ | Czech Republic | CL | Chile | CM | Cameroon | CV | Cape Verde |
            | KZ | Kazakhstan | QA | Qatar | KH | Cambodia | CA | Canada | KE | Kenya | XK | Kosovo | CR | Costa Rica | CI | Côte d'Ivoire |
            | CO | Colombia | CG | Congo | CD | Democratic Republic of the Congo | CU | Cuba | KW | Kuwait | HR | Croatia | KG | Kyrgyzstan | CY | Cyprus | Tanzania | TZ | Tanzania
            | TZ | Tanzania| TH | Thailand | TR | Turkey | TG | Togo | TN | Tunisia | TT | Trinidad and Tobago | PA | Panama | PY | Paraguay|
            | PK | Pakistan | PS | Palestine | PE | Peru | PT | Portugal | PL | Poland | PR | Puerto Rico | FR | France | FI | Finland |
            | PH | Philippines | HU | Hungary | AU | Australia | HK | Hong Kong | NP | Nepal | || || || ||

          ## Response code
          When calling each API, a response code, which provides additional information on the type of response, may be retrieved with an HTTP status code. This response code is included in the HTTP response header and response body message, and its definition may vary by API type. Response codes supported by each type of API are listed below.

          ### Device API, Event API, User API

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
          The following API is used to regularly issue an `API Token` using a pair of `API Key` and `API Secret`, which is provided by LG Open API Developer to B2B partners. The `API Token` issued by this API must be included in the HTTP request header when calling the ThinQ Business API.
      - name: Device API
        description: "The Device API is used to search a list of registered devices, search the profile and status of specific devices, or control devices. If the Device API for multiple types of LG Electronics products purchased by a company is used, the LG Electronics account on which the products are registered or the location information can be assigned in the LG Open API Developer in advance. For home appliances only, it's possible to assign a specific LG Electronics user when calling the Device API to access the devices of that user. Before calling the Device API, the B2B partner or the partner's customer must register the device. As shown below, the purchased device must be registered and signed up for the service on the appropriate LG Electronics platform, depending on the type of device. \n\n |Device Type|LG Electronics Platform|\n |-|-|\n |Appliances and other IoT devices|LG ThinQ (mobile app)|\n |Signage|LG Business Cloud\_ (https://lgbusinesscloud.com)|\n |Commercial HVAC|LG BECON Cloud\_ (https://beconcloud.lge.com)|\n”
      - name: Event API
        description: |
          The Event API is used to allow B2B partners' services to receive or stop receiving messages whenever there is a change in the status of a specific device. This API is currently available to products registered on LG ThinQ only, but more products will be supported in the future. In order for the B2B partner service to receive the device status, the Callback call information of the B2B partner service must be registered in the LG Open API Developer in advance. The types of device status changes provided by Callback are as follows. The conditions for the Callback subscription may differ by type.

           | Category | Type | Description | Pre-Condition |
           |-|-|-|-|
           | Push | DEVICE_PUSH | Device operation is completed, Part replacements is required. <br> (e.g. washer - washing completed, air purifier - filter replacement) | Call the Device Push Message Subscription API |
           | Push | DEVICE_REGISTERED | Device added | API call to get device list |
           | Push | DEVICE_UNREGISTERED | Device has been deleted | API call to get device list |
            | Push | DEVICE_ALIAS_CHANGED | Device's nickname changed | API call to get device list |
      - name: User API
        description: |
          The User API is used to manage the information of LG Electronics users who have registered for partner services. <b> Currently, the API is only available to products registered on LG ThinQ only.</b>
      - name: DR API
        description: |
          With B2B partners as demand response (DR) providers, the DR API is used to control the devices of LG Electronics users, who are DR service users. B2B partners can utilize this API to manage LG Electronics users, who are DR service users, register DR events that may reduce or change the power consumption of LG Electronics users during certain power peak hours in response to the electricity demand, and search whether the DR target device participates in DR events. The DR target devices are currently limited to air conditioners and TVs, but more products will be supported in the future. The DR service using this API follows the following procedure.
          ### 1. Device registration and signing-up for DR service 

            - LG ThinQ users register their DR devices on the LG ThinQ app and sign up for a B2B partner's DR service.
            
            <img src="https://dev.openapi.developer.lge.com/assets/images/img_DR_01.png" width="600"/>

          ### 2. DR request issuance

             - B2B partners register a DR event using the DR API before the DR event starts.
             - LG Electronics delivers the registered DR event to the target device before a specified start time.
             - LG ThinQ users receive a notification on the LG ThinQ app before the DR event starts.

              <img src="https://dev.openapi.developer.lge.com/assets/images/img_DR_02.png" width="600"/>

          ### 3. Status monitoring

            - LG Electronics monitors and records the status of the device while the DR event takes place. 
            - the B2B partners download monitoring data using the DR API.

              <img src="https://dev.openapi.developer.lge.com/assets/images/img_DR_03.png" width="600"/>

          ### 4. DR service billing

            - Based on the data provided by the DR API, the B2B partner calculates a bill based on the DR participation rate of the DR service users and provides the bill details to the users.

              <img src="https://dev.openapi.developer.lge.com/assets/images/img_DR_04.png" width="600"/>


            
    paths:
      /token:
        post:
          tags:
            - auth
          summary: Issue API Token
          description: |
            An `API Key` and an `API Token` are required when calling any API that belongs to the ThinQ Business API. This API is used to issue an `API Token` and the issued `API Token` is valid for **24 hours**, so the client must be prepared to call this API to obtain a new `API Token`. An `API Secret` is only used to issue an `API Token`.
          operationId: createAPIToken
          security:
            - ThinQ_Business_API_Key: []
          servers:
            - url: https://ap.api.lge.com
            - url: https://us.api.lge.com
            - url: https://eu.api.lge.com
            - url: https://ap-test.api.lge.com
            - url: https://us-test.api.lge.com
            - url: https://eu-test.api.lge.com
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
          description: Get profile for a specific device
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
                    WashTower Washer:
                      $ref: '#/components/examples/washtower_washer-profile-example'
                    WashTower Dryer:
                      $ref: '#/components/examples/washtower_dryer-profile-example'
                    WashTower (Single Unit):
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
                    Signage registered in the BECON Cloud:
                      $ref: '#/components/examples/signage-profile-example'
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
          summary: Device status inquiry
          description: Retrieve the device status.
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
                    WashTower Washer:
                      $ref: '#/components/examples/washtower_washer-object-example'
                    WashTower Dryer:
                      $ref: '#/components/examples/washtower_dryer-object-example'
                    WashTower (Single Unit):
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
                    Signage registered in the BECON Cloud:
                      $ref: '#/components/examples/signage-object-example'
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
                  description: For a schema of control request messages by device type, see the [**Device Profiles**](/api/device_profile) page.
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
                  WashTower Washer:
                    $ref: '#/components/examples/washtower_washer-command-example'
                  WashTower Dryer:
                    $ref: '#/components/examples/washtower_dryer-command-example'
                  WashTower (Single Unit):
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
                  Signage registered in the BECON Cloud:
                    $ref: '#/components/examples/signage-command-example'
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
                    WashTower Washer:
                      $ref: '#/components/examples/washtower_washer-object-example'
                    WashTower Dryer:
                      $ref: '#/components/examples/washtower_dryer-object-example'
                    WashTower (Single Unit):
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
                    Signage registered in the BECON Cloud:
                      $ref: '#/components/examples/signage-object-example'
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
            - Event API
          summary: Get Device Push Subscription List
          description: |
            Get ID list of devices that have subscribed to push messages. **(Currently, only LG ThinQ registered appliances are supported.)**
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
            - Event API
          summary: Subscribe to Device Push
          description: |
            Subscribes push messages from the target device. **(Currently, only LG ThinQ registered appliances are supported.)**
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
            - Event API
          summary: Unsubscribe to Device Push
          description: |
            Unsubscribed to Push notifications of the device. **(Currently, only LG ThinQ registered appliances are supported.)**
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
          summary: Get a user's information(User Number)
          description: |
            Get the user number of a specific LG ThinQ user.  When a user signs up for a B2B partner's service, lookup the user number in advance to identify the device owner for push messages received by Callback.
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
      /user/service:
        delete:
          tags:
            - User API
          summary: Disconnect a service
          description: B2B partner requests deactivation when they no longer want to connect a specific LG ThinQ user.
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
                      example: k-apt-1168011000
                      description: Group ID
                    groupName:
                      type: string
                      example: Apgujeong Hyundai 1st Apartment
                      description: Group Name
                    partnerId:
                      type: string
                      example: kepco-herit-lge
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
                        -  25-digit number
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
                            example: k-apt-1168011000
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
                example: k-apt-1168011000
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
                            example: k-apt-1168011000
                            description: The unique group ID that you registered with the DR service to distinguish between groups.
                          groupName:
                            type: string
                            example: Apgujeong Hyundai 1st Apartment
                            description: Group Name
                          partnerId:
                            type: string
                            example: kepco-herit-lge
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
                              example: k-apt-1168011000
                              description: Group ID registered with DR service
                            groupName:
                              type: string
                              example: Apgujeong Hyundai 1st Apartment
                              description: Group Name
                            partnerId:
                              type: string
                              example: herit-01
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
                          - groupId: k-apt-1168011000
                            groupName: Apgujeong Hyundai 1st Apartment
                            partnerId: kepco-herit-lge
                            areaCode: '1168011000'
                            buildingCode: '1168011000103690001004767'
                            comment: Apgujeong Hyundai 1st Apartment
                          - groupId: k-apt-1165010700
                            groupName: Banpo 2-dong Acroriver Park
                            partnerId: kepco-herit-lge
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
                      example: KR2306146584898
                      description: User number of the LG Electronics account
                    mail:
                      type: string
                      example: dr_kr_qa001@yopmail.com
                      description: E-mail address of the LG Electronics account
                    groupId:
                      type: string
                      example: A15721009
                      description: Group ID to enroll users in
                    accessToken:
                      type: string
                      example: 67a184e62a412bb19b6ec2742b94695e06c1ce19d04f8d92121c6c28c99faf841150dba922da301e5617ae3942918a05
                      description: An access_token value issued by the LMP(LGE Members Platform)
                    refreshToken:
                      type: string
                      example: 3559466b6c19e334557c277108aed936c22840672b1c2a6a8fb7597a6473f9a59fbec4a3f4e03595b8a38513ba1d8088
                      description: A refresh_token value issued by the LMP(LGE Members Platform)
                    partner:
                      type: object
                      description: Partner information
                      properties:
                        partnerId:
                          type: string
                          example: herit-01
                          description: Partner ID
                        programId:
                          type: string
                          example: oc-dr-001
                          description: DR Program ID (North America only)
                        programName:
                          type: string
                          example: OC DR Program
                          description: DR Program Name (North America only)
                        partnerUserId:
                          type: string
                          example: lgautodr10
                          description: Partner user ID
                        authCodeExt:
                          type: string
                          example: d778581e-14f5-4531-943b-c823beebc72f.f81a0977-a553-417e-8873-64faafa0534a.160df234-fa67-4ed2-b710-74afc12eaa12
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
                example: 01581c1893b95f30282d3c09d478cef7
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
                example: 01581c1893b95f30282d3c09d478cef7
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
                            description: The encrypted user number of the LG Electronics account
                          drHomeId:
                            type: string
                            example: '171072582282622861'
                            description: ThinQ Home ID of the user connected to the DR service
                          partnerId:
                            type: string
                            example: herit-01
                            description: Partner ID of the DR service to which the user is subscribed
                          groupId:
                            type: string
                            example: A15721009
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
                example: 01581c1893b95f30282d3c09d478cef7
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
                              example: 111e0f0a-8d50-41f8-9120-94a8728c57e4
                              description: The encrypted ThinQ device ID
                            macAddress:
                              type: string
                              example: abcd1234
                              description: The encrypted MAC address
                            groupId:
                              type: string
                              example: k-apt-1168011000
                              description: Group ID
                            userNo:
                              type: string
                              example: KRXXXXXY
                              description: The encrypted user number of the LG Electronics account
                            homeId:
                              type: string
                              example: '1'
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
                          - deviceId: 1f6bfb2796410a429f0015bf91f958361845888164cb0a61fefdd690513b13353f1da753095de970faba8099e2a56aa1
                            macAddress: 66e71f19ada4fcaf5cd7aa26d49d4291
                            groupId: A15721009
                            userNo: 01581c1893b95f30282d3c09d478cef7
                            homeId: '171072582282622861'
                            drParticipate: true
                            opt: IN
                            deviceType: DEVIE_AIR_CONDITIONER
                            modelName: PAC_910604_US
                            alias: room air conditioner
                          - deviceId: 2369ecd9276e62577e97692bc4b345502a2d1b46c616a1ea8d12eead4293979cf10bce3e5242da16a0d6a3afef694da3
                            macAddress: 74d7483ebfc2d52702857244440faf8f
                            groupId: A15721009
                            userNo: 01581c1893b95f30282d3c09d478cef7
                            homeId: '171072582282622861'
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
          summary: Get user device information
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
                example: 01581c1893b95f30282d3c09d478cef7
            - in: path
              name: deviceId
              description: The encrypted ThinQ device ID
              required: true
              schema:
                type: string
                example: 1f6bfb2796410a429f0015bf91f958361845888164cb0a61fefdd690513b13353f1da753095de970faba8099e2a56aa1
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
                              example: 1f6bfb2796410a429f0015bf91f958361845888164cb0a61fefdd690513b13353f1da753095de970faba8099e2a56aa1
                              description: The encrypted ThinQ device ID
                            macAddress:
                              type: string
                              example: 66e71f19ada4fcaf5cd7aa26d49d4291
                              description: The encrypted MAC address
                            groupId:
                              type: string
                              example: A15721009
                              description: Group ID
                            userNo:
                              type: string
                              example: 01581c1893b95f30282d3c09d478cef7
                              description: The encrypted user number of the LG Electronics account
                            homeId:
                              type: string
                              example: '171072582282622861'
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
                          - deviceId: 1f6bfb2796410a429f0015bf91f958361845888164cb0a61fefdd690513b13353f1da753095de970faba8099e2a56aa1
                            macAddress: 66e71f19ada4fcaf5cd7aa26d49d4291
                            groupId: A15721009
                            userNo: 01581c1893b95f30282d3c09d478cef7
                            homeId: '171072582282622861'
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
            description: DR Event information.
            content:
              application/json:
                schema:
                  type: object
                  properties:
                    eventId:
                      type: string
                      example: 2023-04-25-dr-01
                      description: DR Event ID
                    eventName:
                      type: string
                      example: 2023-04-25-dr-01
                      description: DR Event ID
                    partnerId:
                      type: string
                      example: herit-01
                      description: Partner ID
                    startTs:
                      type: number
                      example: 1682423399890
                      description: DR Event start time(milliseconds)
                    endTs:
                      type: number
                      example: 1682426999000
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
                              example: k-apt-1168011000
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
                            example: 2023-04-25-dr-01-signal-01
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
                              ex) { temerpature: { min: 26, max: 32, unit: "C } }
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
                      eventId: 2023-04-25-dr-01
                      eventName: 2023-04-25-dr-01
                      partnerId: herit-01
                      startTs: 1682423399890
                      endTs: 1682426999000
                      targets:
                        - targetType: GROUP
                          targetIds:
                            - k-apt-1168011000
                            - k-apt-1165010700
                        - targetType: USER
                          targetIds:
                            - USXXXXXX
                            - KRXXXXXX
                      signals:
                        - signalId: 2023-04-25-dr-01-signal-01
                          deviceType: DEVICE_AIR_CONDITIONER
                          modelNames:
                            - RAC_056905_WW
                          signalType: CONTROL_RESTORE
                          signalData:
                            temperature:
                              min: 26
                              max: 32
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
                example: 2023-04-25-dr-01
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
                            example: 2023-04-25-dr-01
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
          summary: Create DR Event targets
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
                            example: 2023-04-25-dr-01
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
                example: KRXXXX
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
                          - Ex) Modify: "/23lk2jl1k32j1"
                      value:
                        type: object
                        properties:
                          type:
                            type: string
                            example: DEVICE
                          id:
                            type: string
                            example: +2YjaqUmSr3ke2nmdssxAG5n0KDMwrJrvi8bTbzbdHelEEflqNkAx0WWmTIgyCQf
                          opt:
                            type: string
                            example: IN
                        description: |-
                         You can check whether you are opted in or out of DR Event.
                          - create: {type, id, opt}
                          - replace: {opt}
                          - Ex) create: { type: "DEVICE", id: "23lk2jl1k32j1", opt: "IN"}
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
                          id: +2YjaqUmSr3ke2nmdssxAG5n0KDMwrJrvi8bTbzbdHelEEflqNkAx0WWmTIgyCQf
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
                                example: +2YjaqUmSr3ke2nmdssxAG5n0KDMwrJrvi8bTbzbdHelEEflqNkAx0WWmTIgyCQf
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
                      example: 2023-04-25-dr-01
                      description: DR Event ID
                    targets:
                      type: array
                      items:
                        properties:
                          targetId:
                            type: string
                            example: KRXXXX
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
                          targetId: k-apt-1168011000
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
                            example: data-zip-test_event_1713834322772-1728001286135.zip
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
                example: data-zip-test_event_1713834322772-1728001286135.zip
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
                            example: https://s3-an2-tems-qa-dr-archiver.s3.ap-northeast-2.amazonaws.com/zip/data-zip-test_event_1713834322772-1728001286135.zip?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIARU3MB3TCEDODQ2DO%2F20241004%2Fap-northeast-2%2Fs3%2Faws4_request&X-Amz-Date=20241004T002817Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEID%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLW5vcnRoZWFzdC0yIkcwRQIhALefnNnWXhAZcAcMWZA%2Bm23i5uALS%2FOI9ZwzOwUQMMQyAiACqvSExTC%2B3ErlEfOGtIXnZ450mlJRDu02kW4S2RojcyrVBQjJ%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDExMzUwNjM3NjkwMCIMi5fbbY%2Bs9%2FoMe2jWKqkFntfKoeTR0blrYtIPk0PdBLXhVa%2BpMgj9P0Y2%2F4c8g1IK0LOWuQrLL9bQ%2Bjg%2B4pzsgZWjdFZ8smSNqj3oQ%2FAgpHI56EltlZrnDQNPL%2FkMtj8dSgOJtxtgOE89wzYvB8hd9obkO0c%2BQN76loIX71y6MOC6JtCNlzbf0SpLkONT09IlOMhmFHB4KC87r%2Bb6V7ZIgFp56w9amawSxYK%2BCRj0yw5uXoboEUBwuqcn%2BSF6u2Xq4Z1cS018f%2F9bYtBxqz5M6rUrTup5xkf4ZEbUzFwMpFWk2WhXiu64uzKaF41C3d%2F5YUNa2K725HfWbntEAa0jr37AZtR%2BNagZGvnVnryZsmz%2Fn272kPdhdb3NLv55i1dtqWHu9HjJ2P35ujd5RadNO%2BCki9Vths6O99XDnHpCbrTWoQyCvHIq3wM38Nbbbnv%2BxXeKbzJ1PMbOmmGbqSPhGdFEwHzTiGLkiUXxREFtLLkC5xQn%2F%2FyBFmyoZBrpdVEvt6Ggyk5gh%2F%2BSxG1OvpmCcmYjRloE%2Bh%2F7QCZvboHaeD4wpre1xdRFrW%2FiPSeraR1MxurDFbf8nWqak88IQ%2B82EwOucjX6SKhdk148Vt6mBrd0Ae9MW7W4f82NksX%2FVFeDjeGmkRe4bg85B8b7gwIA8qHl3MwYhUgPm0%2BRlkzdFKYy%2B2eoBZpK0kx3tO52DIeb%2Fk41gfrxQj3lc41y7zKVxZsiftqK7bDbMt4eHkFZ5dTaf0uJlgzsU0AYanJjgZvDxlUCywCHfCTG%2Bb03dWwomJYy4cuN%2Fix8uYzYbM8TAdwFfjYKG0KH3n4W%2FDNvCiQBedoG%2Byx7e5MCr0dpAV2%2F90L9x%2Bq1HloUbqtnVqQ1MRV3PN%2FBv3brupENConWTz90ebLDCd4rJQLKmGprA0UOX2nI8yxMV6u6MLbl%2FLcGOrEBIPFbJuDYy4nYDv0IJF5FHnEM9hZFiC1s1kOPMQkUHbhXENPK4TWBPLx46Ewp%2FvT2PTdkzMVeZLVJ33YVg1V9uL%2BNT1KYs9KuwDdfCMUD22ItcGhm9DCHnp3Db%2FyyWus%2BtBVrdcIsbhtvyfVx0qsFa29MJmxdv%2FdTrOZZ8c6ZSFAOeM5RGsxTs9%2FBZrWyvHy6cbfcMlr8Utm%2BzCGxy5L87LkBhrD9wT6o1%2B3eGI333lGc&X-Amz-Signature=dcdb7b02b2350142fb4b41ab15036ac529981f7dc14d2fa2e6a4bf615b82f827&X-Amz-SignedHeaders=host&x-id=GetObject
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
    components:
      securitySchemes:
        ThinQ_Business_API_Key:
          type: apiKey
          description: |
            The `API Key` string obtained after the partner request was approved.
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
                  description: Device type. For a list of supported device types, see the [**Device Profiles**](http://www.naver.com) page.
                  example: DEVICE_WASHTOWER_WASHER
                alias:
                  type: string
                  description: An alias of the device
                  example: My New WashTower Washer
                modelName:
                  type: string
                  description: A model name of the device
                  example: FAKPK21021
                groupId:
                  type: string
                  description: To identify that a device is in the same group as another device when the device type is `DEVICE_WASHTOWER_WASHER` or `DEVICE_WASHTOWER_DRYER`.
                  example: '171807013576723372'
                parentId:
                  type: string
                  description: The ID of the parent `ODU` device when the device type is `IDU`.
                  example: fe12ed5bca00acc0ed68ec9f632342d0822a929f377b76cbe700649a11053f23
              required:
                - deviceType
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
              description: Value of the request header X-Message-Id
              example: 2ADaRijIk8CvaSHVPeEWNw
            timestamp:
              type: datetime
              description: The current time
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
          description: Profile responses for a specific device
          allOf:
            - $ref: '#/components/schemas/device-base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: For a schema of device profile messages by device type, see the [**Device Profile**](/api/device_profile) page.
        device-status-res:
          description: Status responses for a specific device
          allOf:
            - $ref: '#/components/schemas/device-base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: For a schema of device status response messages by device type, see the [**Device Profile**] (/api/device_profile) page.
        device-id-list-res:
          description: Response from the device ID list
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
      parameters:
        X-Api-Token:
          name: X-Api-Token
          in: header
          schema:
            type: string
          description: |
            **[Issue API Token](#tag/auth/operation/createAPIToken)** `API Token`, a string that is issued in advance through the API.
          example: eyJleHAiOjE3MDQzNDE3MDIsImlhdCI6MTcwNDI1NTMwMiwiaXNzIjoiTEcgQnVzaW5lc3MgQ29ubmVjdCIsInJvbGVzIjpbImdldEJlY29uVXNlcnMiLCJnZXREclVzZXJzIiwicG9zdFRva2VuIl0sInN1YiI6IjRkMmM2MWUxLTM0YzQtZTk2Yy05NDU2LTE1YmQ5ODNjNTAxOSJ9
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
              |REGISTERED|Account that have already registered through partner requests and permission updates.|
              |IN-HEADER|The account specified as the OAuth token in the `Authorization` header of this HTTP request. (**Currently, only LG ThinQ registered appliances are supported.**)|
          example: REGISTERED
        Authorization:
          name: Authorization
          in: header
          schema:
            type: string
          description: |
            The `Bearer` OAuth token of the LG Electronics account that subscribed to LG ThinQ.  If the `X-Use-Account` header is included in the HTTP request and the value of the header is `IN-HEADER`, this header must be included in the request.
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
              filterInfo:
                filterLifetime:
                  mode:
                    - r
                  type: number
                usedTime:
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
                  type: enum
                  value:
                    r:
                      - 'ON'
                      - 'OFF'
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
                  - w
                value:
                  r:
                    - true
                    - false
                  w:
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
              currentJobMode: FAN
            airFlow:
              windStrength: HIGH
              windStep: 5
            operation:
              airConOperationMode: POWER_OFF
            powerSave:
              powerSaveEnabled: false
            temperature:
              currentTemperature: 27
              targetTemperature: 24.5
              unit: C
            timer:
              absoluteStopTimer: UNSET
              absoluteStartTimer: UNSET
            sleepTimer:
              relativeStopTimer: UNSET
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
            temperature:
              - targetTemperature: 18
                unit: C
                locationName: WINE_UPPER
              - targetTemperature: 18
                unit: C
                locationName: WINE_LOWER
            operation:
              lightStatus: 100
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
              flavorInfo:
                - CORIANDER
                - CORIANDER_SEED
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
              boilerOperationMode: POWER_ON
              hotWaterMode: 'ON'
            temperature:
              currentTemperature: 40
              targetTemperature: 18
              unit: C
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
        refrigerator-command-example:
          description: Refrigerator - Power Save On
          value:
            powerSave:
              powerSaveEnabled: true
        washer-command-example:
          description: Washer - Start washing
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
          description: Oven - Operation mode
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
          description: WashTower Washer - Start washing
          value:
            operation:
              washerOperationMode: START
            location:
              locationName: MAIN
        washtower_dryer-command-example:
          description: WashTower Dryer - Power OFF
          value:
            operation:
              dryerOperationMode: POWER_OFF
        washtower-command-example:
          description: WashTower (Single Unit) - Start drying
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
          description: Main WashCombo - Operation
          value:
            location:
              locationName: MAIN
            operation:
              washerOperationMode: START
        mini_washcombo-command-example:
          description: Mini WashCombo - Operation
          value:
            location:
              locationName: MINI
            operation:
              washerOperationMode: START
        humidifier-command-example:
          title: Humidifier
          description: Humidifier- Run mode
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
          - Event API
          - User API
          - DR API
---
