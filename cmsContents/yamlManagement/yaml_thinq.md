---
contents:
  lang: yaml
  code: >
    openapi: 3.1.0

    info:
      version: null
      title: Business Connect API
    servers:
      - url: https://ap.api.lge.com/bc
      - url: https://eu.api.lge.com/bc
      - url: https://us.api.lge.com/bc
      - url: https://ap-test.api.lge.com/bc
      - url: https://eu-test.api.lge.com/bc
      - url: https://us-test.api.lge.com/bc
    tags:
      - name: Overview
        description: |
          여러분의 서비스가 LG전자의 가전제품, 디스플레이, 공조설비에 대하여 정보를 조회하거나 제어를 수행하려면 어떻게 해야 할까요? LG전자는 LG전자의 클라우드 서비스에 등록된 디바이스의 정보를 파트너의 서비스가 획득하거나 제어할 수 있도록 Business Connect API를 제공합니다.

                


          <디자인된 이미지 들어갈 공간>



          Business Connect API는 API의 사용 목적에 따라 다음과 같이 분류됩니다.


           |API 종류|요약|
           |-|-|
           |Token API|API 호출시 사용될 API Token을 발급하기 위한 API|
           |Device API|등록된 디바이스의 목록 및 상태를 조회하고, 제어를 수행하기 위한 API|
           |Event API|디바이스의 상태 변화를 수신하기 위해 대상 디바이스를 관리하기 위한 API|
           |User API|여러분의 서비스에 등록된 사용자를 관리하기 위한 API|
           |DR API|전력 수요반응(DR: Demand Response) 서비스 제공자로서 사용자의 디바이스를 제어하기 위한 API|
      - name: API Call Sequence
        description: |
          Business Connect API를 사용하여 서비스를 개발하는 방법을 API 호출 흐름을 통해 설명합니다.

          ## API Token 발급
          API Token은 모든 Business Connect API 호출의 HTTP 요청 헤더에 포함되어야 합니다. 이 API Token은 LG Open API Developer에서 사전에 발급 받은 API Key와 API Secret 쌍으로 발급될 수 있으며 24시간 동안 유효하기 때문에 만료되기 전에 Token API를 사용하여 API Token을 재발급해야 합니다.


           - 사용 API
              - [`POST /v1/token`](/#tag/Token-API/operation/createAPIToken)

           - 시퀀스


          ![Tux, the Linux mascot](../result/business-connect/sequence.jpg)

          ## 디바이스 상태 조회
          디바이스의 상태를 조회하기 위해 다음과 같이 Device API를 사용합니다.


           - 사용 API
              - [`GET /v1/devices`](/#tag/Token-API/operation/createAPIToken)
              - [`GET /v1/devices/{deviceId}`](/#tag/Token-API/operation/createAPIToken)

           - 시퀀스
              1. 여러분의 서비스는 디바이스 목록 조회 API (GET/bc/v1/devices)를 이용하여, LG전자 플랫폼에 등록된 디바이스 목록을 가져와야 합니다. 이 과정은 처음 한 번만 수행하면 되고, 목록을 한 번 가져온 후에는 매번 수행할 필요는 없습니다.
              2. 디바이스 목록에서 상태를 조회할 디바이스의 deviceId 값을 확인하고, 이 값을 이용하여 디바이스 상태 조회 API (GET /bc/v1/devices/{deviceId})를 호출합니다.


          ![Tux, the Linux mascot](../result/business-connect/sequence.jpg)

          ## 디바이스 제어
          디바이스를 제어하기 위해 다음과 같이 Device API를 사용합니다.


            - 사용 API
              - [`GET /v1/devices`](/#tag/Device-API/operation/getDevices)
              - [`GET /v1/devices/profile/{deviceId}`](/#tag/Device-API/operation/getStatusOfDevice)
              - [`POST /v1/devices/{deviceId}`](/#tag/Device-API/operation/controlDevice)

            - 시퀀스
              1. 여러분의 서비스는 디바이스 목록 조회 API (GET /bc/v1/devices)를 이용하여, LG플랫폼에 사용자의 디바이스 목록을 가져와야 합니다. 이 과정은 처음 한 번만 수행하면 되고, 목록을 한 번 가져온 후에는 매번 수행할 필요는 없습니다.
              2. 디바이스 목록에서 제어 대상 디바이스의 deviceId 값을 확인하고, 이 값을 이용하여 디바이스 프로파일 조회 API (GET/bc/v1/devices/profile/{device-id})를 호출합니다.
              3. API 호출 응답으로 받은 디바이스 프로파일을 바탕으로 해당 디바이스에 대한 제어 명령을 생성합니다. 제어 명령은 디바이스 프로파일에서 제어를 원하는 속성을 찾아 name 과 value 쌍으로 표현합니다.
              4. deviceId와 제어 명령을 이용하여, 디바이스 제어 API (POST /bc/v1/devices/{device-id})를 호출합니다.
              5. API 응답으로 디바이스 제어 결과를 반환 받습니다.


          ![Tux, the Linux mascot](../result/business-connect/sequence.jpg)

          ## DR 서비스에 사용자 등록
          B2B 파트너는 사전에 LG전자의 API 관리자와 협의한 이후 DR API를 사용하여 DR 서비스를 위한 사용자를 등록할 수 있습니다. LG전자 사용자와 디바이스는 다음의 순서에 따라 DR 서비스에 등록됩니다.


            - 사용 API
              - [`POST /v1/dr/users`](/#tag/Token-API/operation/createAPIToken)

            - 시퀀스
              1. LG전자 사용자는 LG ThinQ 서비스에 가입되어 있으며 파트너의 DR 서비스에 가입할 LG 가전제품을 등록한 상태여야 합니다.
              2. LG전자 사용자는 B2B 파트너의 DR 서비스에 대한 가입을 시도합니다.
              3. 파트너 서비스는 LMP(LGE Members Platform)의 OAuth 2.0 연동 절차에 따라 LG전자의 로그인 화면을 DR 서비스에서 제공하고 OAuth 연동 정보를 획득합니다.
              4. LG전자의 DR 서비스는 파트너 서비스와 사전에 정의한 연동 인터페이스에 따라 파트너 서비스 측 OAuth 연동 정보를 획득한 후, 파트너 서비스의 사용자 정보 API를 조회한 결과를 저장합니다. 
              5. LG전자 사용자가 LG ThinQ 모바일 앱에서 DR 서비스에 등록할 홈과 기기를 지정하면 LG전자의 DR 서비스가 해당 기기를 DR 대상 기기로 등록합니다.


          ![Tux, the Linux mascot](../result/business-connect/sequence.jpg)

          ## DR Event 등록 및 모니터링 데이터 다운로드
          DR Event 를 등록하고 DR 이벤트 전후의 디바이스의 모니터링 데이터를 다운로드 하는 과정을 설명합니다.


            - 사용 API
              - [`POST /v1/events`](/#tag/Token-API/operation/createAPIToken)
              - [`POST /v1/dr/events/{eventId}/targets`](/#tag/Token-API/operation/createAPIToken)
              - [`POST /v1/dr/events/{eventId}/targets/{targetId}`](/#tag/Token-API/operation/createAPIToken)
              - [`POST /v1/dr/events/{eventId}/targets/batch`](/#tag/Token-API/operation/createAPIToken)
              - [`POST /v1/dr/data-zip/files`](/#tag/Token-API/operation/createAPIToken)
              - [`POST /v1/dr/data-zip/files/{filename}`](/#tag/Token-API/operation/createAPIToken)

            - 시퀀스
              1. LG DR 서비스 서버에 DR Request를 등록하기 위해 DR Event 등록 API (POST /bc/v1/events)를 호출합니다.
              2. DR Event 가 정상적으로 등록되면, DR Event ID (eventId)를 반환합니다.
              3. 만약 DR Event 생성 후에 해당 DR Event에 참여 필요한 기기 목록 변경이 필요한 경우 DR Event Target 변경 API를 호출합니다.
              4. DR Event가 종료된 후에 해당 Event에 참여 요청한 기기들의 Event 참여 여부를 확인하고 싶은 경우 기기 상태 정보 조회 API를 호출합니다. 


          ![Tux, the Linux mascot](../result/business-connect/sequence.jpg)
            
      - name: Base URL
        description: |
          Lorem ipsum dolor sit amet, consectetur adipiscing eit. Integer dui ligula, sodales vel elit a, dignissim congue felis. Duis tempus vulputate erat.  Vestibulum quis feugiat mi. Fusce ut auctor odio. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Sed id nulla orci.  Curabitur luctus tincidunt nibh id pretium. Fusce tempus sem eu arcu viverra tincidunt. Nullam dignissim bibendum lacinia.  Cras vestibulum augue vitae placerat finibus. Duis tristique magna elit, ac placerat lorem viverra in. In non felis non ante porttitor pharetra non ut nisi.  Suspendisse at nisi tincidunt massa suscipit imperdiet eu et felis. Aliquam sodales enim ut congue mollis. Duis tristique nulla

           
      - name: Codes
        description: |
          # 국가 코드
          Lorem ipsum dolor sit amet, consectetur adipiscing eit. Integer dui ligula, sodales vel elit a, dignissim congue felis. Duis tempus vulputate erat.  Vestibulum quis feugiat mi. Fusce ut auctor odio. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Sed id nulla orci.  Curabitur luctus tincidunt nibh id pretium. Fusce tempus sem eu arcu viverra tincidunt. Nullam dignissim bibendum lacinia.  Cras vestibulum augue vitae placerat finibus. Duis tristique magna elit, ac placerat lorem viverra in. In non felis non ante porttitor pharetra non ut nisi.  Suspendisse at nisi tincidunt massa suscipit imperdiet eu et felis. Aliquam sodales enim ut congue mollis. Duis tristique nulla.

          # HTTP 상태 코드
          Lorem ipsum dolor sit amet, consectetur adipiscing eit. Integer dui ligula, sodales vel elit a, dignissim congue felis. Duis tempus vulputate erat.  Vestibulum quis feugiat mi. Fusce ut auctor odio. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Sed id nulla orci.  Curabitur luctus tincidunt nibh id pretium. Fusce tempus sem eu arcu viverra tincidunt. Nullam dignissim bibendum lacinia.  Cras vestibulum augue vitae placerat finibus. Duis tristique magna elit, ac placerat lorem viverra in. In non felis non ante porttitor pharetra non ut nisi.  Suspendisse at nisi tincidunt massa suscipit imperdiet eu et felis. Aliquam sodales enim ut congue mollis. Duis tristique nulla.

          # 에러 코드
          Lorem ipsum dolor sit amet, consectetur adipiscing eit. Integer dui ligula, sodales vel elit a, dignissim congue felis. Duis tempus vulputate erat.  Vestibulum quis feugiat mi. Fusce ut auctor odio. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Sed id nulla orci.  Curabitur luctus tincidunt nibh id pretium. Fusce tempus sem eu arcu viverra tincidunt. Nullam dignissim bibendum lacinia.  Cras vestibulum augue vitae placerat finibus. Duis tristique magna elit, ac placerat lorem viverra in. In non felis non ante porttitor pharetra non ut nisi.  Suspendisse at nisi tincidunt massa suscipit imperdiet eu et felis. Aliquam sodales enim ut congue mollis. Duis tristique nulla.
      - name: Token API
        description: |
          LG Open API Developer가 B2B 파트너에게 제공한 API Key와 API Secret 쌍을 이용하여 API Token을 주기적으로 발급하기 위해 Token API가 사용됩니다.       이 API로 발급된 API Token은 모든 Business Connect API 호출 시 HTTP 요청 헤더에 포함됩니다.
      - name: Device API
        description: "등록된 디바이스의 목록을 조회하고, 특정 디바이스의 프로파일 및 상태를 조회하거나 디바이스를 제어하기 위해 Device API가 사용됩니다.       기업이 구매한 여러가지 종류의 LG전자 제품에 대하여 Device API를 사용하는 경우, 디바이스가 일괄 등록되어 있는 LG전자 계정이나 설치 현장의 정보를 LG Open API Developer에서 사전에 지정해둘 수 있습니다.       또한 가전제품에 한정하여 Device API를 호출하는 시점에 특정 LG전자 사용자를 지정하여 해당 사용자의 디바이스에 대한 접근을 수행할 수 있습니다.       Device API를 호출하기 위해서는 B2B 파트너 또는 그의 고객이 디바이스를 등록하는 과정이 선행되어야 합니다.       구매한 디바이스는 아래와 같이 디바이스 종류에 따라 해당 LG전자의 플랫폼의 서비스에 가입하여 등록해야 합니다.\n\n |디바이스 종류|LG전자 플랫폼|\n |-|-|\n |가전제품|LG ThinQ (mobile app)|\n |디스플레이|LG Business Cloud\_ (https://lgbusinesscloud.com)|\n |공조설비|LG BECON cloud\_(https://beconcloud.lge.com)|\n"
      - name: Event API
        description: |
          특정 디바이스의 상태 변화를 파트너의 서비스가 수신하거나 수신을 해제하기 위하여 Event API가 사용됩니다. 이 API는 현재 가전제품에 한정하여 제공되며 향후 다른 제품의 지원이 확대될 예정입니다. 파트너 서비스가 디바이스의 상태를 수신하기 위해서는 사전에 LG Open API Developer에서 파트너 서비스의 Callback 호출 정보를 등록해야 합니다.
      - name: User API
        description: |
          파트너 서비스에 등록한 LG전자 사용자의 정보를 관리하기 위하여 User API가 사용됩니다. 이 API는 현재 가전제품에 한정하여 제공됩니다.
      - name: DR API
        description: |
          B2B파트너가 전력 수요반응(DR: Demand Response) 사업자로서 DR 서비스 가입자인 LG전자 사용자의 디바이스를 제어하기 위하여 DR API가 사용됩니다. B2B 파트너는 이 API를 활용하여 DR 가입자인 LG전자 사용자를 관리하고, 현재 전력량의 수요에 반응하여 특정 전력 피크 시간 동안 LG전자 사용자 측의 전력 사용을 줄이거나 변경시킬 수 있는 DR Event 를 등록하고, DR 대상 디바이스의 DR Event 참여 여부를 조회할 수 있습니다. DR 대상 디바이스는 현재 에어컨, TV ( ESS )에 한정하여 제공되며 향후 다른 제품의 지원이 확대될 예정입니다. 이 API를 활용한 DR 서비스는 다음의 절차에 따라 진행됩니다.
    paths:
      /v1/token:
        post:
          tags:
            - Token API
          summary: Create a new API Token
          description: |
            This operation creates a new `API Token` which is required for every calls of Business Connect API. This API Token is valid for **24 hours** so that your client have to be ready to call this API if needed. `API Secret` header is required for this operation.
          operationId: createAPIToken
          security:
            - Business_Connect_API_Key: []
          parameters:
            - name: X-Api-Secret
              in: header
              required: true
              schema:
                type: string
              description: |
                `API Secret` is a pair with `API Key`, which was obtained from **My Page** when the paired API Key was initially created.
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
      /v1/devices:
        get:
          tags:
            - Device API
          summary: List devices
          description: List all registered devices on your accounts.
          operationId: getDevices
          security:
            - Business_Connect_API_Key: []
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
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/device-list-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /v1/devices/profile/{deviceId}:
        get:
          tags:
            - Device API
          summary: Get Profile of the device
          description: Get Device Profile of the device.
          operationId: getProfileOfDevice
          security:
            - Business_Connect_API_Key: []
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
                    $ref: '#/components/schemas/device-profile-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /v1/devices/{deviceId}:
        get:
          tags:
            - Device API
          summary: Get status of the device
          description: Get status of the device.
          operationId: getStatusOfDevice
          security:
            - Business_Connect_API_Key: []
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
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/device-status-res'
                  examples:
                    냉장고:
                      $ref: '#/components/examples/refrigerator-object-example-res-1'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
        post:
          tags:
            - Device API
          summary: Control the device
          description: Control the device.
          operationId: controlDevice
          security:
            - Business_Connect_API_Key: []
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
                  description: 디바이스 유형별 제어 요청 메시지의 스키마는 [**디바이스 프로파일**](http://www.daum.net) 페이지를 참조해주세요.
                examples:
                  냉장고 - 냉장실 온도를 섭씨 0도로 설정:
                    $ref: '#/components/examples/refrigerator-object-example-req-1'
                  냉장고 - 절전 모드 설정:
                    $ref: '#/components/examples/refrigerator-object-example-req-2'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/device-status-res'
                  examples:
                    냉장고:
                      $ref: '#/components/examples/refrigerator-object-example-res-1'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /v1/push:
        get:
          tags:
            - Event API
          summary: List IDs of subscribed ThinQ Devices
          description: Get the list of IDs of ThinQ Devices whose push messages has been subscribed
          operationId: listDevicesSubscribed
          security:
            - Business_Connect_API_Key: []
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
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/device-id-list-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /v1/push/{deviceId}:
        post:
          tags:
            - Event API
          summary: Subscribe push messages
          description: Subscribe push messages of the ThinQ Device
          operationId: subscribePushMessages
          security:
            - Business_Connect_API_Key: []
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
            '401':
              description: Unauthorized
        delete:
          tags:
            - Event API
          summary: Unsubscribe push messages
          description: Unsubscribe push messages of the LG Device
          operationId: unsubscribePushMessages
          security:
            - Business_Connect_API_Key: []
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
            '401':
              description: Unauthorized
      /v1/users:
        get:
          tags:
            - User API
          summary: Get User Number
          description: Get User Number of the user
          operationId: getUserNumber
          security:
            - Business_Connect_API_Key: []
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
              description: Successfully processed the request
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/device-empty-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /v1/user/service:
        delete:
          tags:
            - User API
          summary: Disconnect the user
          description: Deactivate the user and Disconnect the user from your service
          operationId: disconnectService
          security:
            - Business_Connect_API_Key: []
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
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/device-empty-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /v1/dr/groups:
        post:
          tags:
            - DR API
          summary: Create & Update a Group
          description: A POST request to create a new group
          parameters:
            - in: header
              name: X-Api-Key
              description: API Key provided to the client in advance
              required: true
              schema:
                type: string
                example: x-api-key
            - in: header
              name: X-Api-Token
              description: API Token obtained by the client within last 24 hours
              required: true
              schema:
                type: string
                example: x-api-token
            - in: header
              name: X-Message-Id
              description: an ID generated by the client for request tracking  (UUID Version 4, url-safe-base64-no-padding, length:22)
              required: false
              schema:
                type: string
                example: x-message-id
            - in: header
              name: X-Country-Code
              description: country code
              required: true
              schema:
                type: string
                example: us
          requestBody:
            description: Group Infomation
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
                      example: 압구정 현대 1차 아파트
                      description: Group name
                    partnerId:
                      type: string
                      example: kepco-herit-lge
                      description: 그룹을 생성한 전력사/통합사 ID
                    areaCode:
                      type: string
                      example: '1168011000'
                      description: |-
                        - 법정동 코드(국토교통부)
                        - 10자리번호
                    buildingCode:
                      type: string
                      example: '1168011000103690001004767'
                      description: |-
                        - 도로명주소건물관리번호(공간정보 오픈플랫폼)
                        - 25자리번호
                        - 법정동코드(10) + 산여부(1) + 지번본번(4) + 지번부번(4) + 시스템번호(6)
                    comment:
                      type: string
                      example: 압구정 현대 1차 아파트
                      description: description of the resource
                  required:
                    - groupId
                    - partnerId
          responses:
            '200':
              description: '`2000`: Successful operation'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
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
              description: |-
                `4000`: Bad Request<br>
                `4101`: Missing or Invalid Parameter(s) in Request Header<br>
                `4102`: Missing or Invalid Parameter(s) in Request Body<br>
                `4103`: Missing or Invalid Token<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '401':
              description: '`4201`: Invalid or Expired Token<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '403':
              description: '`4202`: Unauthorized request<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '404':
              description: |-
                `4301`: Resource Not Found: User<br>
                `4302`: Resource Not Found: Event<br>
                `4303`: Resource Not Found: Event Target<br>
                `4304`: Resource Not Found: Device<br>
                `4305`: Resource Not Found: Zip File task<br>
                `4306`: Resource Not Found: Zip File<br>
                `4307`: Resource Not Found: Partner<br>
                `4308`: Resource Not Found: Group<br>
                `4313`: Resource Not Found: Partner User<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '405':
              description: Not Allowed
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '409':
              description: |-
                `4309`: Resource Already Exists: User<br>
                `4310`: Resource Already Exists: Event<br>
                `4311`: Resource Already Exists: Event Target<br>
                `4312`: Resource Already Exists: Partner User<br>
                `4314`: Resource Already Exists: Device<br>
                `4315`: Resource Already Exists: Group<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '500':
              description: '`5000`: Internal Server Error<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
      /v1/dr/groups/{groupId}:
        get:
          tags:
            - DR API
          summary: Get a Single Group
          description: A GET request to check a group of an aggregator
          parameters:
            - in: header
              name: X-Api-Key
              description: API Key provided to the client in advance
              required: true
              schema:
                type: string
                example: x-api-key
            - in: header
              name: X-Api-Token
              description: API Token obtained by the client within last 24 hours
              required: true
              schema:
                type: string
                example: x-api-token
            - in: header
              name: X-Message-Id
              description: an ID generated by the client for request tracking  (UUID Version 4, url-safe-base64-no-padding, length:22)
              required: false
              schema:
                type: string
                example: x-message-id
            - in: header
              name: X-Country-Code
              description: country code
              required: true
              schema:
                type: string
                example: us
            - in: path
              name: groupId
              description: a specific group ID. It could be group of users or group of end devices.
              required: true
              schema:
                type: string
                example: k-apt-1168011000
          responses:
            '200':
              description: '`2000`: Successful operation'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
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
                        description: contains information of the group
                        properties:
                          groupId:
                            type: string
                            example: k-apt-1168011000
                            description: uniquely identifiable group ID which is registered to LG DR service.
                          groupName:
                            type: string
                            example: 압구정 현대 1차 아파트
                            description: Group name
                          partnerId:
                            type: string
                            example: kepco-herit-lge
                            description: an ID of an aggregator/utility that created the group
                          areaCode:
                            type: string
                            example: '1168011000'
                            description: |-
                              - 법정동 코드(국토교통부)
                              - 10자리번호
                          buildingCode:
                            type: string
                            example: '1168011000103690001004767'
                            description: |-
                              - 도로명주소건물관리번호(공간정보 오픈플랫폼)
                              - 25자리번호
                              - 법정동코드(10) + 산여부(1) + 지번본번(4) + 지번부번(4) + 시스템번호(6)
                          comment:
                            type: string
                            example: 압구정 현대 1차 아파트
                            description: description of the resource
            '400':
              description: |-
                `4000`: Bad Request<br>
                `4101`: Missing or Invalid Parameter(s) in Request Header<br>
                `4102`: Missing or Invalid Parameter(s) in Request Body<br>
                `4103`: Missing or Invalid Token<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '401':
              description: '`4201`: Invalid or Expired Token<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '403':
              description: '`4202`: Unauthorized request<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '404':
              description: |-
                `4301`: Resource Not Found: User<br>
                `4302`: Resource Not Found: Event<br>
                `4303`: Resource Not Found: Event Target<br>
                `4304`: Resource Not Found: Device<br>
                `4305`: Resource Not Found: Zip File task<br>
                `4306`: Resource Not Found: Zip File<br>
                `4307`: Resource Not Found: Partner<br>
                `4308`: Resource Not Found: Group<br>
                `4313`: Resource Not Found: Partner User<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '405':
              description: Not Allowed<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '409':
              description: |-
                `4309`: Resource Already Exists: User<br>
                `4310`: Resource Already Exists: Event<br>
                `4311`: Resource Already Exists: Event Target<br>
                `4312`: Resource Already Exists: Partner User<br>
                `4314`: Resource Already Exists: Device<br>
                `4315`: Resource Already Exists: Group<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '500':
              description: '`5000`: Internal Server Error'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
      /v1/dr/partners/{partnerId}/groups:
        get:
          tags:
            - DR API
          summary: Get Groups
          description: A GET request to check groups of aggregator
          parameters:
            - in: header
              name: X-Api-Key
              description: API Key provided to the client in advance
              required: true
              schema:
                type: string
                example: x-api-key
            - in: header
              name: X-Api-Token
              description: API Token obtained by the client within last 24 hours
              required: true
              schema:
                type: string
                example: x-api-token
            - in: header
              name: X-Message-Id
              description: an ID generated by the client for request tracking  (UUID Version 4, url-safe-base64-no-padding, length:22)
              required: false
              schema:
                type: string
                example: x-message-id
            - in: header
              name: X-Country-Code
              description: country code
              required: true
              schema:
                type: string
                example: us
            - in: path
              name: partnerId
              description: an ID of an aggregator/utility that created the group
              required: true
              schema:
                type: string
                example: partnerId
          responses:
            '200':
              description: '`2000`: Successful operation'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
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
                        description: contains list of group
                        items:
                          properties:
                            groupId:
                              type: string
                              example: k-apt-1168011000
                              description: uniquely identifiable group ID which is registered to LG DR service.
                            groupName:
                              type: string
                              example: 압구정 현대 1차 아파트
                              description: Group name
                            partnerId:
                              type: string
                              example: kepco-herit-lge
                              description: an ID of an aggregator/utility that created the group
                            areaCode:
                              type: string
                              example: '1168011000'
                              description: |-
                                - 법정동 코드(국토교통부)
                                - 10자리번호
                            buildingCode:
                              type: string
                              example: '1168011000103690001004767'
                              description: |-
                                - 도로명주소건물관리번호(공간정보 오픈플랫폼)
                                - 25자리번호
                                - 법정동코드(10) + 산여부(1) + 지번본번(4) + 지번부번(4) + 시스템번호(6)
                            comment:
                              type: string
                              example: 압구정 현대 1차 아파트
                              description: description of the resource
                  examples:
                    200 OK:
                      value:
                        code: 2000
                        data:
                          - groupId: k-apt-1168011000
                            groupName: 압구정 현대 1차 아파트
                            partnerId: kepco-herit-lge
                            areaCode: '1168011000'
                            buildingCode: '1168011000103690001004767'
                            comment: 압구정 현대 1차 아파트
                          - groupId: k-apt-1165010700
                            groupName: 반포2동 아크로리버파크
                            partnerId: kepco-herit-lge
                            areaCode: '1165010700'
                            buildingCode: '1165010700100020001017796'
                            comment: 반포2동 아크로리버파크
            '400':
              description: |-
                `4000`: Bad Request<br>
                `4101`: Missing or Invalid Parameter(s) in Request Header<br>
                `4102`: Missing or Invalid Parameter(s) in Request Body<br>
                `4103`: Missing or Invalid Token<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '401':
              description: '`4201`: Invalid or Expired Token<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '403':
              description: '`4202`: Unauthorized request<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '404':
              description: |-
                `4301`: Resource Not Found: User<br>
                `4302`: Resource Not Found: Event<br>
                `4303`: Resource Not Found: Event Target<br>
                `4304`: Resource Not Found: Device<br>
                `4305`: Resource Not Found: Zip File task<br>
                `4306`: Resource Not Found: Zip File<br>
                `4307`: Resource Not Found: Partner<br>
                `4308`: Resource Not Found: Group<br>
                `4313`: Resource Not Found: Partner User<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '405':
              description: Not Allowed
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '409':
              description: |-
                `4309`: Resource Already Exists: User<br>
                `4310`: Resource Already Exists: Event<br>
                `4311`: Resource Already Exists: Event Target<br>
                `4312`: Resource Already Exists: Partner User<br>
                `4314`: Resource Already Exists: Device<br>
                `4315`: Resource Already Exists: Group<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '500':
              description: '`5000`: Internal Server Error'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
      /v1/dr/users:
        post:
          tags:
            - DR API
          summary: Create User (ThinQ app 공통)
          description: A POST request to create or update a user
          parameters:
            - in: header
              name: X-Api-Key
              description: API Key provided to the client in advance
              required: true
              schema:
                type: string
                example: x-api-key
            - in: header
              name: X-Api-Token
              description: API Token obtained by the client within last 24 hours
              required: true
              schema:
                type: string
                example: x-api-token
            - in: header
              name: X-Message-Id
              description: an ID generated by the client for request tracking  (UUID Version 4, url-safe-base64-no-padding, length:22)
              required: false
              schema:
                type: string
                example: x-message-id
            - in: header
              name: X-Country-Code
              description: country code
              required: true
              schema:
                type: string
                example: us
          requestBody:
            description: User Infomation
            content:
              application/json:
                schema:
                  type: object
                  properties:
                    userNo:
                      type: string
                      example: US1234
                      description: User Number issued by LG EMP service. You can use Get Profile API on EMP service to get user number of the target user. user key 값. 중복 불가
                    mail:
                      type: string
                      example: saldkjb@glkd.com
                      description: |-
                        Uniquely identifiable userNo which should not contain personal information nor provide clue to trace the target user.
                        User id registered to LG EMP service. You can use Get Profile API on EMP service to get user id of the target user.
                    groupId:
                      type: string
                      example: lgeDR-CE-TV
                      description: Uniquely identifiable group ID which is registered to LG DR service.
                    accessToken:
                      type: string
                      example: abcd123456
                      description: access_token issued by LG EMP service
                    refreshToken:
                      type: string
                      example: qaz2wsx345
                      description: refresh_token issued by LG EMP service
                    partner:
                      type: object
                      description: Partner information
                      properties:
                        partnerId:
                          type: string
                          example: abcded
                          description: Partner ID
                        programId:
                          type: string
                          example: abc123
                          description: DR Program Id (OC - mandatory)
                        programName:
                          type: string
                          example: OC DR Program
                          description: DR Program name (OC - mandatory)
                        partnerUserId:
                          type: string
                          example: abc123@lge.com
                          description: Partner system User ID
                        authCodeExt:
                          type: string
                          example: dlksjdfkjqjl
                          description: 3rd party OAuth 2.0 연동을 위한 Auth code
                      required:
                        - partnerId
                        - authCodeExt
                    insertTs:
                      type: number
                      example: 1234566000
                      description: timestamp when this request is made (10 digits). If empty, default timestamp will be added automatically.
                    updateTs:
                      type: number
                      example: 1234566000
                      description: timestamp when this request is updated (10 digits). If empty, default timestamp will be added automatically.
                  required:
                    - userNo
                    - accessToken
                    - refreshToken
                    - partner
          responses:
            '200':
              description: '`2000`: Successful operation'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
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
                            example: user1234
                            description: encrypted User No.
            '400':
              description: |-
                `4000`: Bad Request<br>
                `4101`: Missing or Invalid Parameter(s) in Request Header<br>
                `4102`: Missing or Invalid Parameter(s) in Request Body<br>
                `4103`: Missing or Invalid Token<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '401':
              description: '`4201`: Invalid or Expired Token<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '403':
              description: '`4202`: Unauthorized request<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '404':
              description: |-
                `4301`: Resource Not Found: User<br>
                `4302`: Resource Not Found: Event<br>
                `4303`: Resource Not Found: Event Target<br>
                `4304`: Resource Not Found: Device<br>
                `4305`: Resource Not Found: Zip File task<br>
                `4306`: Resource Not Found: Zip File<br>
                `4307`: Resource Not Found: Partner<br>
                `4308`: Resource Not Found: Group<br>
                `4313`: Resource Not Found: Partner User<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '405':
              description: Not Allowed<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '409':
              description: |-
                `4309`: Resource Already Exists: User<br>
                `4310`: Resource Already Exists: Event<br>
                `4311`: Resource Already Exists: Event Target<br>
                `4312`: Resource Already Exists: Partner User<br>
                `4314`: Resource Already Exists: Device<br>
                `4315`: Resource Already Exists: Group<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '500':
              description: '`5000`: Internal Server Error<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
      /v1/dr/users/{userNo}:
        delete:
          tags:
            - DR API
          summary: Delete a User (ThinQ app 공통)
          description: A DELETE request to delete a user
          parameters:
            - in: header
              name: X-Api-Key
              description: API Key provided to the client in advance
              required: true
              schema:
                type: string
                example: x-api-key
            - in: header
              name: X-Api-Token
              description: API Token obtained by the client within last 24 hours
              required: true
              schema:
                type: string
                example: x-api-token
            - in: header
              name: X-Message-Id
              description: an ID generated by the client for request tracking  (UUID Version 4, url-safe-base64-no-padding, length:22)
              required: false
              schema:
                type: string
                example: x-message-id
            - in: header
              name: X-Country-Code
              description: country code
              required: true
              schema:
                type: string
                example: us
            - in: path
              name: userNo
              description: EMP User No.
              required: true
              schema:
                type: string
                example: user1234
          responses:
            '200':
              description: '`2000`: Successful operation'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
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
                            example: user1234
                            description: deleted User No.
            '400':
              description: |-
                `4000`: Bad Request<br>
                `4101`: Missing or Invalid Parameter(s) in Request Header<br>
                `4102`: Missing or Invalid Parameter(s) in Request Body<br>
                `4103`: Missing or Invalid Token<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '401':
              description: '`4201`: Invalid or Expired Token<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '403':
              description: '`4202`: Unauthorized request<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '404':
              description: |-
                `4301`: Resource Not Found: User<br>
                `4302`: Resource Not Found: Event<br>
                `4303`: Resource Not Found: Event Target<br>
                `4304`: Resource Not Found: Device<br>
                `4305`: Resource Not Found: Zip File task<br>
                `4306`: Resource Not Found: Zip File<br>
                `4307`: Resource Not Found: Partner<br>
                `4308`: Resource Not Found: Group<br>
                `4313`: Resource Not Found: Partner User<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '405':
              description: Not Allowed<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '409':
              description: |-
                `4309`: Resource Already Exists: User<br>
                `4310`: Resource Already Exists: Event<br>
                `4311`: Resource Already Exists: Event Target<br>
                `4312`: Resource Already Exists: Partner User<br>
                `4314`: Resource Already Exists: Device<br>
                `4315`: Resource Already Exists: Group<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '500':
              description: '`5000`: Internal Server Error<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
        get:
          tags:
            - DR API
          summary: Get a User
          description: A GET request to get user information
          parameters:
            - in: header
              name: X-Api-Key
              description: API Key provided to the client in advance
              required: true
              schema:
                type: string
                example: x-api-key
            - in: header
              name: X-Api-Token
              description: API Token obtained by the client within last 24 hours
              required: true
              schema:
                type: string
                example: x-api-token
            - in: header
              name: X-Message-Id
              description: an ID generated by the client for request tracking  (UUID Version 4, url-safe-base64-no-padding, length:22)
              required: false
              schema:
                type: string
                example: x-message-id
            - in: header
              name: X-Country-Code
              description: country code
              required: true
              schema:
                type: string
                example: us
            - in: path
              name: userNo
              description: EMP User No.
              required: true
              schema:
                type: string
                example: user1234
          responses:
            '200':
              description: '`2000`: Successful operation'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
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
                            example: user1234
                            description: EMP User No.
                          drHomeId:
                            type: string
                            example: home-01
                            description: ID of the ThinQ Home that the user has selected to be linked to DR Service
                          partnerId:
                            type: string
                            example: ohmconnect-01
                            description: the Partner ID (ID of the DR Service Provider that the user is enrolled to)
                          groupId:
                            type: string
                            example: group-01
                            description: the ID of the group the user is grouped to.
            '400':
              description: |-
                `4000`: Bad Request<br>
                `4101`: Missing or Invalid Parameter(s) in Request Header<br>
                `4102`: Missing or Invalid Parameter(s) in Request Body<br>
                `4103`: Missing or Invalid Token<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '401':
              description: '`4201`: Invalid or Expired Token<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '403':
              description: '`4202`: Unauthorized request<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '404':
              description: |-
                `4301`: Resource Not Found: User<br>
                `4302`: Resource Not Found: Event<br>
                `4303`: Resource Not Found: Event Target<br>
                `4304`: Resource Not Found: Device<br>
                `4305`: Resource Not Found: Zip File task<br>
                `4306`: Resource Not Found: Zip File<br>
                `4307`: Resource Not Found: Partner<br>
                `4308`: Resource Not Found: Group<br>
                `4313`: Resource Not Found: Partner User<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '405':
              description: Not Allowed<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '409':
              description: |-
                `4309`: Resource Already Exists: User<br>
                `4310`: Resource Already Exists: Event<br>
                `4311`: Resource Already Exists: Event Target<br>
                `4312`: Resource Already Exists: Partner User<br>
                `4314`: Resource Already Exists: Device<br>
                `4315`: Resource Already Exists: Group<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '500':
              description: '`5000`: Internal Server Error<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
      /v1/dr/users/{userNo}/devices:
        get:
          tags:
            - DR API
          summary: Get Devices (User Based, ThinQ app 공통)
          description: A Get request to get device list of a user
          parameters:
            - in: header
              name: X-Api-Key
              description: API Key provided to the client in advance
              required: true
              schema:
                type: string
                example: x-api-key
            - in: header
              name: X-Api-Token
              description: API Token obtained by the client within last 24 hours
              required: true
              schema:
                type: string
                example: x-api-token
            - in: header
              name: X-Message-Id
              description: an ID generated by the client for request tracking  (UUID Version 4, url-safe-base64-no-padding, length:22)
              required: false
              schema:
                type: string
                example: x-message-id
            - in: header
              name: X-Country-Code
              description: country code
              required: true
              schema:
                type: string
                example: us
            - in: path
              name: userNo
              description: EMP User No.
              required: true
              schema:
                type: string
                example: KRXXXXXY
          responses:
            '200':
              description: '`2000`: Successful operation'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
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
                              description: Device ThinQ ID
                            macAddress:
                              type: string
                              example: abcd1234
                              description: MAC address of the device (encrypted)
                            groupId:
                              type: string
                              example: k-apt-1168011000
                              description: Group ID
                            userNo:
                              type: string
                              example: KRXXXXXY
                              description: EMP User No.
                            homeId:
                              type: string
                              example: '1'
                              description: ThinQ Home ID (ThinQ Home ID the devie is registered to)
                            drParticipate:
                              type: boolean
                              example: true
                              description: Auto-DR Selected Device or Not (true/false)
                            opt:
                              type: string
                              example: IN
                              description: Currently in DR Event Mode or not ("IN"/"OUT")
                            deviceType:
                              type: string
                              example: DEVICE_AIR_CONDITIONER
                              description: Device type
                            modelName:
                              type: string
                              example: PAC_910604_US
                              description: Model Name of the device
                            alias:
                              type: string
                              example: air conditioner
                              description: alias of the device
                  examples:
                    200 OK:
                      value:
                        code: 2000
                        data:
                          - deviceId: 111e0f0a-8d50-41f8-9120-94a8728c57e4
                            macAddress: abcd1234
                            groupId: k-apt-1168011000
                            userNo: KRXXXXXY
                            homeId: '1'
                            drParticipate: true
                            opt: IN
                            deviceType: DEVIE_AIR_CONDITIONER
                            modelName: PAC_910604_US
                            alias: air conditioner
                          - deviceId: aaaaaaaa-1234-11d3-80ae-044eaf8f70cc
                            macAddress: bcdef2345
                            groupId: k-apt-1165010700
                            userNo: KRXXXXXY
                            homeId: '2'
                            drParticipate: true
                            opt: OUT
                            deviceType: DEVIE_AIR_CONDITIONER
                            modelName: PAC_910604_US
                            alias: air conditioner
            '400':
              description: |-
                `4000`: Bad Request<br>
                `4101`: Missing or Invalid Parameter(s) in Request Header<br>
                `4102`: Missing or Invalid Parameter(s) in Request Body<br>
                `4103`: Missing or Invalid Token<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '401':
              description: '`4201`: Invalid or Expired Token<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '403':
              description: '`4202`: Unauthorized request<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '404':
              description: |-
                `4301`: Resource Not Found: User<br>
                `4302`: Resource Not Found: Event<br>
                `4303`: Resource Not Found: Event Target<br>
                `4304`: Resource Not Found: Device<br>
                `4305`: Resource Not Found: Zip File task<br>
                `4306`: Resource Not Found: Zip File<br>
                `4307`: Resource Not Found: Partner<br>
                `4308`: Resource Not Found: Group<br>
                `4313`: Resource Not Found: Partner User<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '405':
              description: Not Allowed<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '409':
              description: |-
                `4309`: Resource Already Exists: User<br>
                `4310`: Resource Already Exists: Event<br>
                `4311`: Resource Already Exists: Event Target<br>
                `4312`: Resource Already Exists: Partner User<br>
                `4314`: Resource Already Exists: Device<br>
                `4315`: Resource Already Exists: Group<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '500':
              description: '`5000`: Internal Server Error<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
      /v1/dr/users/{userNo}/devices/{deviceId}:
        get:
          tags:
            - DR API
          summary: Get a Single Device (User based)
          description: A GET request to get a single device on user based
          parameters:
            - in: header
              name: X-Api-Key
              description: API Key provided to the client in advance
              required: true
              schema:
                type: string
                example: x-api-key
            - in: header
              name: X-Api-Token
              description: API Token obtained by the client within last 24 hours
              required: true
              schema:
                type: string
                example: x-api-token
            - in: header
              name: X-Message-Id
              description: an ID generated by the client for request tracking  (UUID Version 4, url-safe-base64-no-padding, length:22)
              required: false
              schema:
                type: string
                example: x-message-id
            - in: header
              name: X-Country-Code
              description: country code
              required: true
              schema:
                type: string
                example: us
            - in: path
              name: userNo
              description: EMP User No.
              required: true
              schema:
                type: string
                example: KRXXXXXY
            - in: path
              name: deviceId
              description: Device ThinQ ID
              required: true
              schema:
                type: string
                example: 111e0f0a-8d50-41f8-9120-94a8728c57e4
          responses:
            '200':
              description: '`2000`: Successful operation'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
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
                          deviceId:
                            type: string
                            example: 111e0f0a-8d50-41f8-9120-94a8728c57e4
                            description: Device ThinQ ID
                          macAddress:
                            type: string
                            example: abcd1234
                            description: MAC address of the device (encrypted)
                          groupId:
                            type: string
                            example: k-apt-1168011000
                            description: Group ID
                          userNo:
                            type: string
                            example: KRXXXXXY
                            description: EMP User No.
                          homeId:
                            type: string
                            example: '1'
                            description: ThinQ Home ID (ThinQ Home ID the devie is registered to)
                          drParticipate:
                            type: boolean
                            example: true
                            description: Auto-DR Selected Device or Not (true/false)
                          opt:
                            type: string
                            example: IN
                            description: Currently in DR Event Mode or not ("IN"/"OUT")
                          deviceType:
                            type: string
                            example: DEVICE_AIR_CONDITIONER
                            description: Device type
                          modelName:
                            type: string
                            example: PAC_910604_US
                            description: Model Name of the device
                          alias:
                            type: string
                            example: air conditioner
                            description: alias of the device
            '400':
              description: |-
                `4000`: Bad Request<br>
                `4101`: Missing or Invalid Parameter(s) in Request Header<br>
                `4102`: Missing or Invalid Parameter(s) in Request Body<br>
                `4103`: Missing or Invalid Token<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '401':
              description: '`4201`: Invalid or Expired Token<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '403':
              description: '`4202`: Unauthorized request<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '404':
              description: |-
                `4301`: Resource Not Found: User<br>
                `4302`: Resource Not Found: Event<br>
                `4303`: Resource Not Found: Event Target<br>
                `4304`: Resource Not Found: Device<br>
                `4305`: Resource Not Found: Zip File task<br>
                `4306`: Resource Not Found: Zip File<br>
                `4307`: Resource Not Found: Partner<br>
                `4308`: Resource Not Found: Group<br>
                `4313`: Resource Not Found: Partner User<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '405':
              description: Not Allowed<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '409':
              description: |-
                `4309`: Resource Already Exists: User<br>
                `4310`: Resource Already Exists: Event<br>
                `4311`: Resource Already Exists: Event Target<br>
                `4312`: Resource Already Exists: Partner User<br>
                `4314`: Resource Already Exists: Device<br>
                `4315`: Resource Already Exists: Group<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '500':
              description: '`5000`: Internal Server Error<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
      /v1/dr/events:
        post:
          tags:
            - DR API
          summary: Create & update DR Event
          description: A POST request to create a new DR request.
          parameters:
            - in: header
              name: X-Api-Key
              description: API Key provided to the client in advance
              required: true
              schema:
                type: string
                example: x-api-key
            - in: header
              name: X-Api-Token
              description: API Token obtained by the client within last 24 hours
              required: true
              schema:
                type: string
                example: x-api-token
            - in: header
              name: X-Message-Id
              description: an ID generated by the client for request tracking  (UUID Version 4, url-safe-base64-no-padding, length:22)
              required: false
              schema:
                type: string
                example: x-message-id
            - in: header
              name: X-Country-Code
              description: country code
              required: true
              schema:
                type: string
                example: us
          requestBody:
            description: Event information
            content:
              application/json:
                schema:
                  type: object
                  properties:
                    eventId:
                      type: string
                      example: 2023-04-25-dr-01
                      description: ID of an event
                    eventName:
                      type: string
                      example: 2023-04-25-dr-01
                      description: Event Name
                    partnerId:
                      type: string
                      example: herit-01
                      description: Partner ID
                    startTs:
                      type: number
                      example: 1682423399890
                      description: milliseconds
                    endTs:
                      type: number
                      example: 1682426999000
                      description: milliseconds
                    targets:
                      type: array
                      items:
                        properties:
                          targetType:
                            type: string
                            example: GROUP
                            description: type of targets (GROUP, USER, DEVICE)
                          targetIds:
                            type: array
                            items:
                              type: string
                              example: k-apt-1168011000
                            description: list of ids (of GROUP, USER or DEVICE)
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
                            description: Signal ID
                          deviceType:
                            type: string
                            example: DEVICE_AIR_CONDITIONER
                            description: Device Types of the target for the Signal
                          modelNames:
                            type: array
                            items:
                              type: string
                              example: RAC_056905_WW
                            description: Model Names of the target for the Signal
                          signalType:
                            type: string
                            example: CONTROL_RESTORE
                            description: signal Types (CONTROL, CONTROL_RESTORE)
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
                              Specific control values for the Signal
                              ex) { temerpature: { min: 26, max: 32, unit: "C } }
                          constrolType:
                            type: string
                            example: Temperature
                            description: Control Method (Temperature, TwoSetTemperature, ToU, Empty)
                          restoreType:
                            type: string
                            example: Temperature
                            description: Restore Method (Temperature, TwoSetTemperature, Empty)
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
              description: '`2000`: Successful operation'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
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
                            example: 2023-04-25-dr-01-signal-01
                            description: event ID of DR
            '400':
              description: |-
                `4000`: Bad Request<br>
                `4101`: Missing or Invalid Parameter(s) in Request Header<br>
                `4102`: Missing or Invalid Parameter(s) in Request Body<br>
                `4103`: Missing or Invalid Token<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '401':
              description: '`4201`: Invalid or Expired Token<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '403':
              description: '`4202`: Unauthorized request<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '404':
              description: |-
                `4301`: Resource Not Found: User<br>
                `4302`: Resource Not Found: Event<br>
                `4303`: Resource Not Found: Event Target<br>
                `4304`: Resource Not Found: Device<br>
                `4305`: Resource Not Found: Zip File task<br>
                `4306`: Resource Not Found: Zip File<br>
                `4307`: Resource Not Found: Partner<br>
                `4308`: Resource Not Found: Group<br>
                `4313`: Resource Not Found: Partner User<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '405':
              description: Not Allowed<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '409':
              description: |-
                `4309`: Resource Already Exists: User<br>
                `4310`: Resource Already Exists: Event<br>
                `4311`: Resource Already Exists: Event Target<br>
                `4312`: Resource Already Exists: Partner User<br>
                `4314`: Resource Already Exists: Device<br>
                `4315`: Resource Already Exists: Group<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '500':
              description: '`5000`: Internal Server Error<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
      /v1/dr/events/{eventId}/targets:
        post:
          tags:
            - DR API
          summary: Create Event Target (POST)
          description: A POST request to create a DR Event Target
          parameters:
            - in: header
              name: X-Api-Key
              description: API Key provided to the client in advance
              required: true
              schema:
                type: string
                example: x-api-key
            - in: header
              name: X-Api-Token
              description: API Token obtained by the client within last 24 hours
              required: true
              schema:
                type: string
                example: x-api-token
            - in: header
              name: X-Message-Id
              description: an ID generated by the client for request tracking  (UUID Version 4, url-safe-base64-no-padding, length:22)
              required: false
              schema:
                type: string
                example: x-message-id
            - in: header
              name: X-Country-Code
              description: country code
              required: true
              schema:
                type: string
                example: us
            - in: path
              name: eventId
              description: Event ID
              required: true
              schema:
                type: string
                example: event-01
          requestBody:
            description: Event information
            content:
              application/json:
                schema:
                  type: object
                  properties:
                    type:
                      type: string
                      example: USER
                      description: |-
                        type of targets
                        - GROUP
                        - USER
                        - DEVICE
                    id:
                      type: string
                      example: KRXXXX
                      description: |-
                        ids of each targets
                        - when type is USER: userNo
                        - when type is GROUP: groupId
                        - when type is DEVICE: deviceId
                    opt:
                      type: string
                      example: OUT
                      description: |-
                        Opt in / out of an event
                        - IN: participate in the DR Event (default)
                        - OUT: Opt out of an Event
                  required:
                    - type
                    - id
                    - opt
          responses:
            '200':
              description: '`2000`: Successful operation'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
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
              description: |-
                `4000`: Bad Request<br>
                `4101`: Missing or Invalid Parameter(s) in Request Header<br>
                `4102`: Missing or Invalid Parameter(s) in Request Body<br>
                `4103`: Missing or Invalid Token<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '401':
              description: '`4201`: Invalid or Expired Token<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '403':
              description: '`4202`: Unauthorized request<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '404':
              description: |-
                `4301`: Resource Not Found: User<br>
                `4302`: Resource Not Found: Event<br>
                `4303`: Resource Not Found: Event Target<br>
                `4304`: Resource Not Found: Device<br>
                `4305`: Resource Not Found: Zip File task<br>
                `4306`: Resource Not Found: Zip File<br>
                `4307`: Resource Not Found: Partner<br>
                `4308`: Resource Not Found: Group<br>
                `4313`: Resource Not Found: Partner User<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '405':
              description: Not Allowed<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '409':
              description: |-
                `4309`: Resource Already Exists: User<br>
                `4310`: Resource Already Exists: Event<br>
                `4311`: Resource Already Exists: Event Target<br>
                `4312`: Resource Already Exists: Partner User<br>
                `4314`: Resource Already Exists: Device<br>
                `4315`: Resource Already Exists: Group<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '500':
              description: '`5000`: Internal Server Error<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
      /v1/dr/events/{eventId}/targets/{targetId}:
        post:
          tags:
            - DR API
          summary: Update Event Target (POST)
          description: A POST request to update a DR Event Target
          parameters:
            - in: header
              name: X-Api-Key
              description: API Key provided to the client in advance
              required: true
              schema:
                type: string
                example: x-api-key
            - in: header
              name: X-Api-Token
              description: API Token obtained by the client within last 24 hours
              required: true
              schema:
                type: string
                example: x-api-token
            - in: header
              name: X-Message-Id
              description: an ID generated by the client for request tracking  (UUID Version 4, url-safe-base64-no-padding, length:22)
              required: false
              schema:
                type: string
                example: x-message-id
            - in: header
              name: X-Country-Code
              description: country code
              required: true
              schema:
                type: string
                example: us
            - in: path
              name: eventId
              description: Event ID
              required: true
              schema:
                type: string
                example: event-01
            - in: path
              name: targetId
              description: Target ID
              required: true
              schema:
                type: string
                example: KRXXXX
          requestBody:
            description: Event information
            content:
              application/json:
                schema:
                  type: object
                  properties:
                    opt:
                      type: string
                      example: OUT
                      description: |-
                        Opt in / out of an event
                        - IN: participate in the DR Event (default)
                        - OUT: Opt out of an Event
          responses:
            '200':
              description: '`2000`: Successful operation'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
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
              description: |-
                `4000`: Bad Request<br>
                `4101`: Missing or Invalid Parameter(s) in Request Header<br>
                `4102`: Missing or Invalid Parameter(s) in Request Body<br>
                `4103`: Missing or Invalid Token<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '401':
              description: '`4201`: Invalid or Expired Token<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '403':
              description: '`4202`: Unauthorized request<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '404':
              description: |-
                `4301`: Resource Not Found: User<br>
                `4302`: Resource Not Found: Event<br>
                `4303`: Resource Not Found: Event Target<br>
                `4304`: Resource Not Found: Device<br>
                `4305`: Resource Not Found: Zip File task<br>
                `4306`: Resource Not Found: Zip File<br>
                `4307`: Resource Not Found: Partner<br>
                `4308`: Resource Not Found: Group<br>
                `4313`: Resource Not Found: Partner User<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '405':
              description: Not Allowed<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '409':
              description: |-
                `4309`: Resource Already Exists: User<br>
                `4310`: Resource Already Exists: Event<br>
                `4311`: Resource Already Exists: Event Target<br>
                `4312`: Resource Already Exists: Partner User<br>
                `4314`: Resource Already Exists: Device<br>
                `4315`: Resource Already Exists: Group<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '500':
              description: '`5000`: Internal Server Error<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
      /v1/dr/events/{eventId}/targets/batch:
        post:
          tags:
            - DR API
          summary: Create & Update Event Target in a Batch
          description: A POST request to update Targets for a DR Event
          parameters:
            - in: header
              name: X-Api-Key
              description: API Key provided to the client in advance
              required: true
              schema:
                type: string
                example: x-api-key
            - in: header
              name: X-Api-Token
              description: API Token obtained by the client within last 24 hours
              required: true
              schema:
                type: string
                example: x-api-token
            - in: header
              name: X-Message-Id
              description: an ID generated by the client for request tracking  (UUID Version 4, url-safe-base64-no-padding, length:22)
              required: false
              schema:
                type: string
                example: x-message-id
            - in: header
              name: X-Country-Code
              description: country code
              required: true
              schema:
                type: string
                example: us
            - in: path
              name: eventId
              description: Event ID
              required: true
              schema:
                type: string
                example: event-01
          requestBody:
            description: DR Event를 위한 Target 업데이트 정보
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
                          Action to be performed for each targets (path)
                          - create
                          - replace(or update)
                      path:
                        type: string
                        example: /
                        description: |-
                          ID of each target
                          - create: "/"
                          - update: "/{targetId}"
                          - Ex) creating: "/"
                          - Ex) updating: "/23lk2jl1k32j1"
                      value:
                        type: object
                        example:
                          type: DEVICE
                          id: +2YjaqUmSr3ke2nmdssxAG5n0KDMwrJrvi8bTbzbdHelEEflqNkAx0WWmTIgyCQf
                          opt: IN
                        description: |-
                          Opt in / out of an event
                          - create: {id, type, opt}
                          - update: {opt}
                          - Ex) creating: { type: "DEVICE", id: "23lk2jl1k32j1", opt: "IN"}
                          - Ex) updating: { opt: "IN"}
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
              description: '`2000`: Successful operation'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
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
                          action:
                            type: string
                            example: create
                          path:
                            type: string
                            example: /
                          value:
                            type: object
                            example:
                              type: DEVICE
                              id: +2YjaqUmSr3ke2nmdssxAG5n0KDMwrJrvi8bTbzbdHelEEflqNkAx0WWmTIgyCQf
                              opt: IN
                          status:
                            type: string
                            example: success
                  examples:
                    create:
                      value:
                        code: 2000
                        data:
                          - action: create
                            path: /
                            value:
                              type: DEVICE
                              id: +2YjaqUmSr3ke2nmdssxAG5n0KDMwrJrvi8bTbzbdHelEEflqNkAx0WWmTIgyCQf
                              opt: IN
                            status: success
                    update:
                      value:
                        code: 2000
                        data:
                          - action: update
                            path: /KRXXXX
                            value:
                              opt: OUT
                            status: success
                    create/update:
                      value:
                        code: 2000
                        data:
                          - action: create
                            path: /
                            value:
                              type: DEVICE
                              id: +2YjaqUmSr3ke2nmdssxAG5n0KDMwrJrvi8bTbzbdHelEEflqNkAx0WWmTIgyCQf
                              opt: IN
                            status: success
                          - action: update
                            path: /KRXXXX
                            value:
                              opt: OUT
                            status: success
                          - action: update
                            path: /KRXXXY
                            value:
                              opt: IN
                            status: success
            '400':
              description: |-
                `4000`: Bad Request<br>
                `4101`: Missing or Invalid Parameter(s) in Request Header<br>
                `4102`: Missing or Invalid Parameter(s) in Request Body<br>
                `4103`: Missing or Invalid Token<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '401':
              description: '`4201`: Invalid or Expired Token<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '403':
              description: '`4202`: Unauthorized request<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '404':
              description: |-
                `4301`: Resource Not Found: User<br>
                `4302`: Resource Not Found: Event<br>
                `4303`: Resource Not Found: Event Target<br>
                `4304`: Resource Not Found: Device<br>
                `4305`: Resource Not Found: Zip File task<br>
                `4306`: Resource Not Found: Zip File<br>
                `4307`: Resource Not Found: Partner<br>
                `4308`: Resource Not Found: Group<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '405':
              description: Not Allowed<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '409':
              description: |-
                `4309`: Resource Already Exists: User<br>
                `4310`: Resource Already Exists: Event<br>
                `4311`: Resource Already Exists: Event Target<br>
                `4312`: Resource Already Exists: Device<br>
                `4313`: Resource Already Exists: Group<br>
                `4314`: Resource Already Exists: authCodeExt(Already connected 3rd party user)<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '500':
              description: '`5000`: Internal Server Error'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
      /v1/dr/data-zip/files:
        post:
          tags:
            - DR API
          summary: Create a Data Zip File
          description: A POST Request for a creation of a zip file for DR Status data of devices during a DR Event
          parameters:
            - in: header
              name: X-Api-Key
              description: API Key provided to the client in advance
              required: true
              schema:
                type: string
                example: x-api-key
            - in: header
              name: X-Api-Token
              description: API Token obtained by the client within last 24 hours
              required: true
              schema:
                type: string
                example: x-api-token
            - in: header
              name: X-Message-Id
              description: an ID generated by the client for request tracking  (UUID Version 4, url-safe-base64-no-padding, length:22)
              required: false
              schema:
                type: string
                example: x-message-id
            - in: header
              name: X-Country-Code
              description: country code
              required: true
              schema:
                type: string
                example: us
          requestBody:
            description: DR Event & Target Information for zip file creation
            content:
              application/json:
                schema:
                  type: object
                  properties:
                    eventId:
                      type: string
                      example: 2023-04-26-01-dr-event-01
                      description: event Id
                    targets:
                      type: array
                      items:
                        properties:
                          targetId:
                            type: string
                            example: USXXXX
                            description: ID of a target
                          targetType:
                            type: string
                            example: USER
                            description: |-
                              Target Type
                              - USER
                              - DEVICE
                              - GROUP
                  required:
                    - eventId
                examples:
                  Create a Data Zip File:
                    value:
                      eventId: 2023-04-26-01-dr-event-01
                      targets:
                        - targetType: USER
                          targetId: USXXXX
                        - targetType: GROUP
                          targetId: k-apt-1168011000
          responses:
            '200':
              description: '`2000`: Successful operation'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
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
                            example: data-zip-2023-04-26-01-dr-event-01-1548892800123.zip
                            description: name of the zie file
                  examples:
                    Create a Data Zip File:
                      value:
                        code: 2000
                        data:
                          fileName: data-zip-2023-04-26-01-dr-event-01-1548892800123.zip
            '400':
              description: |-
                `4000`: Bad Request<br>
                `4101`: Missing or Invalid Parameter(s) in Request Header<br>
                `4102`: Missing or Invalid Parameter(s) in Request Body<br>
                `4103`: Missing or Invalid Token<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '401':
              description: '`4201`: Invalid or Expired Token<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '403':
              description: '`4202`: Unauthorized request<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '404':
              description: |-
                `4301`: Resource Not Found: User<br>
                `4302`: Resource Not Found: Event<br>
                `4303`: Resource Not Found: Event Target<br>
                `4304`: Resource Not Found: Device<br>
                `4305`: Resource Not Found: Zip File task<br>
                `4306`: Resource Not Found: Zip File<br>
                `4307`: Resource Not Found: Partner<br>
                `4308`: Resource Not Found: Group<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '405':
              description: Not Allowed<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '409':
              description: |-
                `4309`: Resource Already Exists: User<br>
                `4310`: Resource Already Exists: Event<br>
                `4311`: Resource Already Exists: Event Target<br>
                `4312`: Resource Already Exists: Device<br>
                `4313`: Resource Already Exists: Group<br>
                `4314`: Resource Already Exists: authCodeExt(Already connected 3rd party user)<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '500':
              description: '`5000`: Internal Server Error'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
      /v1/dr/data-zip/files/{filename}:
        get:
          tags:
            - DR API
          summary: Download a Data Zip File
          description: A GET Request to get download link for zip file
          parameters:
            - in: header
              name: X-Api-Key
              description: API Key provided to the client in advance
              required: true
              schema:
                type: string
                example: x-api-key
            - in: header
              name: X-Api-Token
              description: API Token obtained by the client within last 24 hours
              required: true
              schema:
                type: string
                example: x-api-token
            - in: header
              name: X-Message-Id
              description: an ID generated by the client for request tracking  (UUID Version 4, url-safe-base64-no-padding, length:22)
              required: false
              schema:
                type: string
                example: x-message-id
            - in: header
              name: X-Country-Code
              description: country code
              required: true
              schema:
                type: string
                example: us
            - in: path
              name: filename
              description: Name of the zip file (value received as a response from Create a Data zip API)
              required: true
              schema:
                type: string
                example: data-zip-2023-04-26-01-dr-event-01-1548892800123.zip
          responses:
            '200':
              description: '`2000`: Successful operation'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
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
                            example: https://test-dr.s3.{region}.amazonaws.com/data-zip-2023-04-26-01-dr-event-01-1548892800123?response-content-disposition=inline&X-Amz-Security-Token=IQoJ......
                            description: zip file download url (temporary url)
            '400':
              description: |-
                `4000`: Bad Request<br>
                `4101`: Missing or Invalid Parameter(s) in Request Header<br>
                `4102`: Missing or Invalid Parameter(s) in Request Body<br>
                `4103`: Missing or Invalid Token<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '401':
              description: '`4201`: Invalid or Expired Token<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '403':
              description: '`4202`: Unauthorized request<br>'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '404':
              description: |-
                `4301`: Resource Not Found: User<br>
                `4302`: Resource Not Found: Event<br>
                `4303`: Resource Not Found: Event Target<br>
                `4304`: Resource Not Found: Device<br>
                `4305`: Resource Not Found: Zip File task<br>
                `4306`: Resource Not Found: Zip File<br>
                `4307`: Resource Not Found: Partner<br>
                `4308`: Resource Not Found: Group<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '405':
              description: Not Allowed<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '409':
              description: |-
                `4309`: Resource Already Exists: User<br>
                `4310`: Resource Already Exists: Event<br>
                `4311`: Resource Already Exists: Event Target<br>
                `4312`: Resource Already Exists: Device<br>
                `4313`: Resource Already Exists: Group<br>
                `4314`: Resource Already Exists: authCodeExt(Already connected 3rd party user)<br>
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
            '500':
              description: '`5000`: Internal Server Error'
              headers:
                X-Request-Id:
                  schema:
                    type: string
                  description: an ID generated by API service for request tracking
                X-Response-Code:
                  schema:
                    type: string
                  description: a response code of API service against request
                X-Message-Id:
                  schema:
                    type: string
                  description: The value of the X-Message-Id header sent by the client during API calls
    components:
      securitySchemes:
        Business_Connect_API_Key:
          type: apiKey
          description: |
            `API Key` obtained from **My Page**.
          in: header
          name: X-Api-Key
      schemas:
        api-token-res:
          type: object
          description: Response Object that includes API Token.
          properties:
            access_token:
              type: string
              description: API Token which is represented as JWT(header.payload.signature).
              example: eyJhbGciOiJIUzI1NiIsImtpZCI6InNpbTIifQ.eyJleHAiOjE3MDQzNDE3MDIsImlhdCI6MTcwNDI1NTMwMiwiaXNzIjoiTEcgQnVzaW5lc3MgQ29ubmVjdCIsInJvbGVzIjpbImdldEJlY29uVXNlcnMiLCJnZXREclVzZXJzIiwicG9zdFRva2VuIl0sInN1YiI6IjRkMmM2MWUxLTM0YzQtZTk2Yy05NDU2LTE1YmQ5ODNjNTAxOSJ9.plRjXmZRoXkOy_U95VXGzX-ouJyCrorEmMO8OzrEvF8
        device-base-res:
          type: object
          description: Response Object for any device
          properties:
            messageId:
              type: string
              description: The `X-Message-Id` value included in the header is returned so that it can be checked from the outside upon request.
              example: 2ADaRijIk8CvaSHVPeEWNw
            timestamp:
              type: string
              description: Refers to time when the request is received. Follows the `ISO-8601` format.
              example: '2024-10-01T06:23:20.866279'
        device-list-item:
          type: object
          title: LG Device
          properties:
            deviceId:
              type: string
              description: An ID that can identify the device
              example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
            deviceInfo:
              type: object
              properties:
                deviceType:
                  type: string
                  description: |
                    Appliance type of the device https://thinq.developer.lge.com/en/cloud/docs/thinq-connect/api-reference/common-data-type//#3
                  example: DEVICE_WASHTOWER_WASHER
                alias:
                  type: string
                  description: An alias of the device
                  example: My New WashTower Washer
                modelName:
                  type: string
                  description: A model name of the device, appeared when the device is one of **ThinQ Devices**
                  example: FAKPK21021
                reportable:
                  type: boolean
                  description: Whether or not your service is subscribing to events which occur when the device status changes, appeared when the device is one of **ThinQ Devices**
                  example: false
                groupId:
                  type: string
                  description: |
                    Group ID, appeared when the `deviceType` is `DEVICE_WASHTOWER_WASHER` or `DEVICE_WASHTOWER_DRYER`
                  example: '171807013576723372'
                parentId:
                  type: string
                  description: Device ID of the parent of this device, appeared when `deviceType` is `IDU`
                  example: fe12ed5bca00acc0ed68ec9f632342d0822a929f377b76cbe700649a11053f23
              required:
                - deviceType
          required:
            - deviceId
            - deviceInfo
        device-list-res:
          description: Object for device list
          allOf:
            - $ref: '#/components/schemas/device-base-res'
            - type: object
              properties:
                response:
                  type: array
                  items:
                    allOf:
                      - $ref: '#/components/schemas/device-list-item'
        device-profile-res:
          description: Object for the Device Profile of a Device
          allOf:
            - $ref: '#/components/schemas/device-base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: 디바이스 유형별 디바이스 프로파일 메시지의 스키마는 [**디바이스 프로파일**](http://www.naver.com) 페이지를 참조해주세요.
                  example: <<디바이스 프로파일 페이지에서 참조>>
        device-status-res:
          description: Object for status of devices
          allOf:
            - $ref: '#/components/schemas/device-base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: 디바이스 유형별 디바이스 상태 응답 메시지의 스키마는 [**디바이스 프로파일**](http://www.daum.net) 페이지를 참조해주세요.
        device-id-list-res:
          description: Object for Device ID list Response
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
                        description: 디바이스 식별자
                        example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
        device-empty-res:
          description: Object for Empty Response
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
                type of targets
                - GROUP
                - USER
                - DEVICE
            id:
              type: string
              example: KRXXXX
              description: |-
                ids of each targets
                - when type is USER: userNo
                - when type is GROUP: groupId
                - when type is DEVICE: deviceId
            opt:
              type: string
              example: OUT
              description: |-
                Opt in / out of an event
                - IN: participate in the DR Event (default)
                - OUT: Opt out of an Event
      parameters:
        X-Api-Token:
          name: X-Api-Token
          in: header
          schema:
            type: string
          description: |
            `API Token` obtained from **[Create a new API Token](/#tag/Token-API/operation/createAPIToken)** API.
          example: eyJleHAiOjE3MDQzNDE3MDIsImlhdCI6MTcwNDI1NTMwMiwiaXNzIjoiTEcgQnVzaW5lc3MgQ29ubmVjdCIsInJvbGVzIjpbImdldEJlY29uVXNlcnMiLCJnZXREclVzZXJzIiwicG9zdFRva2VuIl0sInN1YiI6IjRkMmM2MWUxLTM0YzQtZTk2Yy05NDU2LTE1YmQ5ODNjNTAxOSJ9
        X-Message-Id:
          name: X-Message-Id
          in: header
          schema:
            type: string
          description: |
            A value for tracking the information requested by LG ThinQ Platform that is used to track the flow of a specific API and to find the cause of an error. You must create and enter a new unique value for each API call. How to create: 
              Must be created with the url-safe-base64-no-padding (UUID Version 4) method.
              Up to 22 characters
          example: 2ADaRijIk8CvaSHVPeEWNw
        X-Use-Account:
          name: X-Use-Account
          in: header
          schema:
            type: string
          description: |
            API 요청 처리시 사용될 LG전자 계정의 출처를 지정합니다.

              |Value|Description|
              |-|-|
              |REGISTERED|My Page에서 이미 등록한 계정|
              |IN-HEADER|이 HTTP 요청의 `Authorization` 헤더에 OAuth 토큰으로 지정된 계정 (**현재 LG ThinQ 등록 가전제품에 대해서만 지원합니다.**)|
          example: REGISTERED
        Authorization:
          name: Authorization
          in: header
          schema:
            type: string
          description: |
            LG ThinQ에 가입한 LG전자 계정의 `Bearer` OAuth 토큰.  `X-Use-Account` 헤더가 HTTP 요청에 포함되어 있으면서 헤더의 값이 `IN-HEADER`인 경우, 이 헤더는 필수적으로 요청에 포함되어야 합니다.
          example: Bearer 5a9a713f51a95c53d781addd1af0dfa4f6e1e7420a8bff3c5198308dac571aa9845832b8d29bbe1f04deec2d35229c6d
        X-Country-Code:
          name: X-Country-Code
          in: header
          schema:
            type: string
          description: |
            LG전자가 지원하는 국가의 `ISO-3166 alpha-2` 국가 코드.  `X-Use-Account` 헤더가 HTTP 요청에 포함되어 있으면서 헤더의 값이 `IN-HEADER`인 경우, 이 헤더는 필수적으로 요청에 포함되어야 합니다.
          example: KR
        deviceId:
          name: deviceId
          in: path
          schema:
            type: string
          description: an ID that can identify the device
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
      examples:
        refrigerator-object-example-res-1:
          value:
            messageId: 2ADaRijIk8CvaSHVPeEWNw
            timestamp: '2024-10-01T06:23:20.866279'
            response:
              temperature:
                - targetTemperature: 5
                  locationName: FRIDGE
                  unit: ''
                - targetTemperature: -23
                  locationName: FREEZER
                  unit: ''
              refrigeration:
                expressMode: true
              powerSave:
                powerSaveEnabled: true
        refrigerator-object-example-req-1:
          description: 냉장고 - 냉장실 온도를 섭씨 0도로 설정
          value:
            temperature:
              - targetTemperature: 0
                locationName: FRIDGE
                unit: C
        refrigerator-object-example-req-2:
          description: 냉장고 - 절전 모드 설정
          value:
            powerSave:
              powerSaveEnabled: true
    x-tagGroups:
      - name: Get Started
        tags:
          - Overview
          - API Call Sequence
          - Base URL
          - Codes
      - name: APIs
        tags:
          - Token API
          - Device API
          - Event API
          - User API
          - DR API
---
