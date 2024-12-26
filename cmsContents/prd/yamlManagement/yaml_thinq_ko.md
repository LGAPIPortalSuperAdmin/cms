---
contents:
  lang: yaml
  code: >
    openapi: 3.1.0

    info:
      version: null
      title: ThinQ API
    servers:
      - url: https://api-kic.lgthinq.com
      - url: https://api-aic.lgthinq.com
      - url: https://api-eic.lgthinq.com
    tags:
      - name: PAT(Personal Access Token)
        description: |
          ThinQ API를 호출하기 위해 사용되는 개인 식별 토큰입니다.  개인적이고 비상업적 목적으로만 개인 권한 토큰을 사용할 수 있습니다. 개인 권한 토큰을 사용하여 LG전자가 허용하지 않은 추가 서비스를 개발하고자 하는 경우, LG전자와 이러한 잠재적 추가 서비스에 대해 논의하고 LG전자로부터 서면 동의를 받아야 합니다.
            1. https://connect-pat.lgthinq.com 페이지를 방문하세요.
            2. ThinQ 계정 로그인을 합니다.
            3. "새 토큰 만들기" 버튼을 선택합니다.
            4. 토큰 이름을 입력합니다.
            5. 권한 범위에서 해당 토큰이 사용하고자 하는 기능에 대해서 선택합니다.
            6. "토큰 만들기" 버튼을 누르면 토큰이 생성되고, PAT 페이지로 돌아갑니다.
            7. 새로 생성된 토큰을 복사해서 사용합니다.
      - name: Base URL
        description: |
          ThinQ API는 고객의 디바이스의 위치에 따라 Base URL을 구분하고 있습니다. <br>  따라서 고객의 디바이스가 위치하는 지역을 고려해, ThinQ API 호출 시 아래 Base URL을 선택하여 적용해주십시오. 

            |Region|ThinQ API|
            |-|-|
            |South Asia, East Asia and Pacific|https://api-kic.lgthinq.com|
            |America|https://api-aic.lgthinq.com|
            |Europe, Middle East, Africa|https://api-eic.lgthinq.com|
      - name: Route API
        description: |
          ThinQ Backend 도메인 이름을 조회하기 위한 API입니다.
      - name: Device API
        description: |
          ThinQ 디바이스 정보를 요청하고 제어하기 위한 API입니다.
      - name: Push API
        description: |
          ThinQ 디바이스에서 발생하는 푸시 메시지를 구독/해제하기 위한 API입니다.
      - name: Event API
        description: |
          ThinQ 디바이스에서 발생한 상태 변경에 대한 이벤트 메시지를 구독/해제하기 위한 API입니다.
      - name: Client API
        description: |
          ThinQ 디바이스에서 전달하는 메시지를 받기 위한 사용자 디바이스 인증서 발급/등록을 위한 API입니다.  
    paths:
      /route:
        get:
          tags:
            - Route API
          summary: 도메인 이름 조회
          description: |
            ThinQ Platform에 Backend 주소를 얻어오기 위한 API입니다. 리전 별, 형상 별 도메인 이름을 조회합니다.
          parameters:
            - required: true
              $ref: '#/components/parameters/x-message-id'
            - required: true
              $ref: '#/components/parameters/x-country'
            - required: true
              $ref: '#/components/parameters/x-service-phase'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/route-res'
            '400':
              description: Bad request
      /devices:
        get:
          tags:
            - Device API
          summary: 디바이스 목록 조회
          description: |
            ThinQ Platform에 등록한 디바이스 목록을 얻어오기 위한 API입니다. 다른 API를 사용하기 전에 반드시 한 번은 호출되어야 합니다.  해당 API가 응답한 디바이스 목록에는 디바이스를 식별할 수 있는 device-id가 포함되어 있으며, 이 값으로 대상 디바이스를 지정하여 다른 디바이스 API를 호출할 수 있습니다.  따라서 이 API는 반드시 최초 1번은 호출되어야 하며, 디바이스 목록을 확인 후에는 매번 호출할 필요 없습니다.
          parameters:
            - required: true
              $ref: '#/components/parameters/Authorization'
            - required: true
              $ref: '#/components/parameters/x-message-id'
            - required: true
              $ref: '#/components/parameters/x-country'
            - required: true
              $ref: '#/components/parameters/x-client-id'
            - required: true
              $ref: '#/components/parameters/x-api-key'
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
      /devices/{deviceId}/profile:
        get:
          tags:
            - Device API
          summary: 디바이스 프로파일 조회
          description: |
            디바이스 프로파일을 조회하기 위한 API입니다. 디바이스 프로파일은 LG 가전의 속성을 기술한 정보로, LG ThinQ 플랫폼이 사용하는 디바이스 데이터입니다.
          parameters:
            - required: true
              $ref: '#/components/parameters/Authorization'
            - required: true
              $ref: '#/components/parameters/x-message-id'
            - required: true
              $ref: '#/components/parameters/x-country'
            - required: true
              $ref: '#/components/parameters/x-client-id'
            - required: true
              $ref: '#/components/parameters/x-api-key'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/device-profile-res'
                  examples:
                    냉장고:
                      $ref: '#/components/examples/refrigerator-profile-example'
                    정수기:
                      $ref: '#/components/examples/water_purifier-profile-example'
                    와인냉장고:
                      $ref: '#/components/examples/wine_cellar-profile-example'
                    김치냉장고:
                      $ref: '#/components/examples/kimchi_refrigerator-profile-example'
                    맥주제조기:
                      $ref: '#/components/examples/home_brew-profile-example'
                    식물재배기:
                      $ref: '#/components/examples/plant_cultivator-profile-example'
                    세탁기:
                      $ref: '#/components/examples/washer-profile-example'
                    건조기:
                      $ref: '#/components/examples/dryer-profile-example'
                    스타일러:
                      $ref: '#/components/examples/styler-profile-example'
                    식기세척기:
                      $ref: '#/components/examples/dish_washer-profile-example'
                    워시타워(세탁기):
                      $ref: '#/components/examples/washtower_washer-profile-example'
                    워시타워(건조기):
                      $ref: '#/components/examples/washtower_dryer-profile-example'
                    일체형워시타워:
                      $ref: '#/components/examples/washtower-profile-example'
                    워시콤보세탁기:
                      $ref: '#/components/examples/main_washcombo-profile-example'
                    워시콤보미니세탁기:
                      $ref: '#/components/examples/mini_washcombo-profile-example'
                    오븐:
                      $ref: '#/components/examples/oven-profile-example'
                    쿡탑:
                      $ref: '#/components/examples/cooktop-profile-example'
                    후드:
                      $ref: '#/components/examples/hood-profile-example'
                    전자레인지:
                      $ref: '#/components/examples/microwave_oven-profile-example'
                    에어컨:
                      $ref: '#/components/examples/air_conditioner-profile-example'
                    시스템보일러:
                      $ref: '#/components/examples/system_boiler-profile-example'
                    공기청정기:
                      $ref: '#/components/examples/air_purifier-profile-example'
                    제습기:
                      $ref: '#/components/examples/dehumidifier-profile-example'
                    가습기:
                      $ref: '#/components/examples/humidifier-profile-example'
                    온수기:
                      $ref: '#/components/examples/water_heater-profile-example'
                    실링팬:
                      $ref: '#/components/examples/ceiling_fan-profile-example'
                    공기청정팬:
                      $ref: '#/components/examples/air_purifier_fan-profile-example'
                    로봇청소기:
                      $ref: '#/components/examples/robot_cleaner-profile-example'
                    스틱청소기:
                      $ref: '#/components/examples/stick_cleaner-profile-example'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /devices/{deviceId}/state:
        get:
          tags:
            - Device API
          summary: 디바이스 상태 조회
          description: 디바이스 현재 상태를 조회하기 위한 API입니다. 지정한 device-id의 현재 상태를 얻어올 수 있습니다.
          parameters:
            - required: true
              $ref: '#/components/parameters/Authorization'
            - required: true
              $ref: '#/components/parameters/x-message-id'
            - required: true
              $ref: '#/components/parameters/x-country'
            - required: true
              $ref: '#/components/parameters/x-client-id'
            - required: true
              $ref: '#/components/parameters/x-api-key'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/device-state-res'
                  examples:
                    냉장고:
                      $ref: '#/components/examples/refrigerator-object-example'
                    정수기:
                      $ref: '#/components/examples/water_purifier-object-example'
                    와인냉장고:
                      $ref: '#/components/examples/wine_cellar-object-example'
                    김치냉장고:
                      $ref: '#/components/examples/kimchi_refrigerator-object-example'
                    맥주제조기:
                      $ref: '#/components/examples/home_brew-object-example'
                    식물재배기:
                      $ref: '#/components/examples/plant_cultivator-object-example'
                    세탁기:
                      $ref: '#/components/examples/washer-object-example'
                    건조기:
                      $ref: '#/components/examples/dryer-object-example'
                    스타일러:
                      $ref: '#/components/examples/styler-object-example'
                    식기세척기:
                      $ref: '#/components/examples/dish_washer-object-example'
                    워시타워(세탁기):
                      $ref: '#/components/examples/washtower_washer-object-example'
                    워시타워(건조기):
                      $ref: '#/components/examples/washtower_dryer-object-example'
                    일체형워시타워:
                      $ref: '#/components/examples/washtower-object-example'
                    워시콤보세탁기:
                      $ref: '#/components/examples/main_washcombo-object-example'
                    워시콤보미니세탁기:
                      $ref: '#/components/examples/mini_washcombo-object-example'
                    오븐:
                      $ref: '#/components/examples/oven-object-example'
                    쿡탑:
                      $ref: '#/components/examples/cooktop-object-example'
                    후드:
                      $ref: '#/components/examples/hood-object-example'
                    전자레인지:
                      $ref: '#/components/examples/microwave_oven-object-example'
                    에어컨:
                      $ref: '#/components/examples/air_conditioner-object-example'
                    시스템보일러:
                      $ref: '#/components/examples/system_boiler-object-example'
                    공기청정기:
                      $ref: '#/components/examples/air_purifier-object-example'
                    제습기:
                      $ref: '#/components/examples/dehumidifier-object-example'
                    가습기:
                      $ref: '#/components/examples/humidifier-object-example'
                    온수기:
                      $ref: '#/components/examples/water_heater-object-example'
                    실링팬:
                      $ref: '#/components/examples/ceiling_fan-object-example'
                    공기청정팬:
                      $ref: '#/components/examples/air_purifier_fan-object-example'
                    로봇청소기:
                      $ref: '#/components/examples/robot_cleaner-object-example'
                    스틱청소기:
                      $ref: '#/components/examples/stick_cleaner-object-example'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /devices/{deviceId}/control:
        post:
          tags:
            - Device API
          summary: 디바이스 제어
          description: 디바이스를 제어하기 위한 API입니다. 지정한 device-id에 제어 명령을 보낼 수 있습니다.
          parameters:
            - required: true
              $ref: '#/components/parameters/Authorization'
            - required: true
              $ref: '#/components/parameters/x-message-id'
            - required: true
              $ref: '#/components/parameters/x-country'
            - required: true
              $ref: '#/components/parameters/x-client-id'
            - required: true
              $ref: '#/components/parameters/x-api-key'
            - required: false
              $ref: '#/components/parameters/x-conditional-control'
          requestBody:
            content:
              application/json:
                schema:
                  type: object
                  description: 디바이스 프로파일에 정의된 제어 명령
                examples:
                  냉장고:
                    $ref: '#/components/examples/refrigerator-command-example'
                  와인냉장고:
                    $ref: '#/components/examples/wine_cellar-command-example'
                  세탁기:
                    $ref: '#/components/examples/washer-command-example'
                  건조기:
                    $ref: '#/components/examples/dryer-command-example'
                  스타일러:
                    $ref: '#/components/examples/styler-command-example'
                  식기세척기:
                    $ref: '#/components/examples/dish_washer-command-example'
                  워시타워(세탁기):
                    $ref: '#/components/examples/washtower_washer-command-example'
                  워시타워(건조기):
                    $ref: '#/components/examples/washtower_dryer-command-example'
                  일체형워시타워:
                    $ref: '#/components/examples/washtower-command-example'
                  워시콤보세탁기:
                    $ref: '#/components/examples/main_washcombo-command-example'
                  워시콤보미니세탁기:
                    $ref: '#/components/examples/mini_washcombo-command-example'
                  오븐:
                    $ref: '#/components/examples/oven-command-example'
                  쿡탑:
                    $ref: '#/components/examples/cooktop-command-example'
                  후드:
                    $ref: '#/components/examples/hood-command-example'
                  전자레인지:
                    $ref: '#/components/examples/microwave_oven-command-example'
                  에어컨:
                    $ref: '#/components/examples/air_conditioner-command-example'
                  시스템보일러:
                    $ref: '#/components/examples/system_boiler-command-example'
                  공기청정기:
                    $ref: '#/components/examples/air_purifier-command-example'
                  제습기:
                    $ref: '#/components/examples/dehumidifier-command-example'
                  가습기:
                    $ref: '#/components/examples/humidifier-command-example'
                  온수기:
                    $ref: '#/components/examples/water_heater-command-example'
                  실링팬:
                    $ref: '#/components/examples/ceiling_fan-command-example'
                  공기청정팬:
                    $ref: '#/components/examples/air_purifier_fan-command-example'
                  로봇청소기:
                    $ref: '#/components/examples/robot_cleaner-command-example'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/device-control-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /push:
        get:
          tags:
            - Push API
          summary: 디바이스 푸시 구독 목록 조회
          description: 사용자가 디바이스 푸시 알림을 설정한 디바이스 목록을 조회합니다.
          parameters:
            - required: true
              $ref: '#/components/parameters/Authorization'
            - required: true
              $ref: '#/components/parameters/x-message-id'
            - required: true
              $ref: '#/components/parameters/x-country'
            - required: true
              $ref: '#/components/parameters/x-client-id'
            - required: true
              $ref: '#/components/parameters/x-api-key'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/push-list-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /push/{deviceId}/subscribe:
        post:
          tags:
            - Push API
          summary: 디바이스 푸시 구독
          description: 디바이스로부터 발생하는 푸시 알림을 설정합니다.
          parameters:
            - required: true
              $ref: '#/components/parameters/Authorization'
            - required: true
              $ref: '#/components/parameters/x-message-id'
            - required: true
              $ref: '#/components/parameters/x-country'
            - required: true
              $ref: '#/components/parameters/x-client-id'
            - required: true
              $ref: '#/components/parameters/x-api-key'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/push-deviceId-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /push/{deviceId}/unsubscribe:
        delete:
          tags:
            - Push API
          summary: 디바이스 푸시 해제
          description: 디바이스로부터 발생하는 푸시 알림을 해제합니다.
          parameters:
            - required: true
              $ref: '#/components/parameters/Authorization'
            - required: true
              $ref: '#/components/parameters/x-message-id'
            - required: true
              $ref: '#/components/parameters/x-country'
            - required: true
              $ref: '#/components/parameters/x-client-id'
            - required: true
              $ref: '#/components/parameters/x-api-key'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/push-deviceId-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /push/devices:
        get:
          tags:
            - Push API
          summary: 디바이스 추가/삭제 알림 구독 클라이언트 목록 조회
          description: 사용자가 디바이스 추가/삭제/변경 구독을 요청한 client 목록 조회
          parameters:
            - required: true
              $ref: '#/components/parameters/Authorization'
            - required: true
              $ref: '#/components/parameters/x-message-id'
            - required: true
              $ref: '#/components/parameters/x-country'
            - required: true
              $ref: '#/components/parameters/x-client-id'
            - required: true
              $ref: '#/components/parameters/x-api-key'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/push-client-list-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
        post:
          tags:
            - Push API
          summary: 디바이스 추가/삭제 알림 클라이언트 구독
          description: 디바이스 추가/삭제/변경 구독을 받기 위해 client 등록 요청
          parameters:
            - required: true
              $ref: '#/components/parameters/Authorization'
            - required: true
              $ref: '#/components/parameters/x-message-id'
            - required: true
              $ref: '#/components/parameters/x-country'
            - required: true
              $ref: '#/components/parameters/x-client-id'
            - required: true
              $ref: '#/components/parameters/x-api-key'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/push-list-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
        delete:
          tags:
            - Push API
          summary: 디바이스 추가/삭제 알림 클라이언트 해제
          description: 디바이스 추가/삭제/변경 구독을 받기 위해 client 등록 요청
          parameters:
            - required: true
              $ref: '#/components/parameters/Authorization'
            - required: true
              $ref: '#/components/parameters/x-message-id'
            - required: true
              $ref: '#/components/parameters/x-country'
            - required: true
              $ref: '#/components/parameters/x-client-id'
            - required: true
              $ref: '#/components/parameters/x-api-key'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/push-list-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /event:
        get:
          tags:
            - Event API
          summary: 디바이스 이벤트 구독 목록 조회
          description: 디바이스 상태 변경 알림을 설정한 디바이스 목록을 조회합니다.
          parameters:
            - required: true
              $ref: '#/components/parameters/Authorization'
            - required: true
              $ref: '#/components/parameters/x-message-id'
            - required: true
              $ref: '#/components/parameters/x-country'
            - required: true
              $ref: '#/components/parameters/x-client-id'
            - required: true
              $ref: '#/components/parameters/x-api-key'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/event-list-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /event/{deviceId}/subscribe:
        post:
          tags:
            - Event API
          summary: 디바이스 이벤트 구독
          description: 디바이스로부터 발생하는 상태 변경 알림을 설정합니다.
          parameters:
            - required: true
              $ref: '#/components/parameters/Authorization'
            - required: true
              $ref: '#/components/parameters/x-message-id'
            - required: true
              $ref: '#/components/parameters/x-country'
            - required: true
              $ref: '#/components/parameters/x-client-id'
            - required: true
              $ref: '#/components/parameters/x-api-key'
          requestBody:
            content:
              application/json:
                schema:
                  type: object
                  $ref: '#/components/schemas/event-register-req'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/event-deviceId-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /event/{deviceId}/unsubscribe:
        delete:
          tags:
            - Event API
          summary: 디바이스 이벤트 구독 해제
          description: 디바이스로부터 발생하는 상태 변경 알림을 해제합니다.
          parameters:
            - required: true
              $ref: '#/components/parameters/Authorization'
            - required: true
              $ref: '#/components/parameters/x-message-id'
            - required: true
              $ref: '#/components/parameters/x-country'
            - required: true
              $ref: '#/components/parameters/x-client-id'
            - required: true
              $ref: '#/components/parameters/x-api-key'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/event-deviceId-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /client/certificate:
        post:
          tags:
            - Client API
          summary: 클라이언트 인증서 발급
          description: 클라이언트의 AWS IoT 인증서, 구독 가능한 MQTT Topic 확인합니다.
          parameters:
            - required: true
              $ref: '#/components/parameters/Authorization'
            - required: true
              $ref: '#/components/parameters/x-message-id'
            - required: true
              $ref: '#/components/parameters/x-country'
            - required: true
              $ref: '#/components/parameters/x-client-id'
            - required: true
              $ref: '#/components/parameters/x-api-key'
          requestBody:
            content:
              application/json:
                schema:
                  type: object
                  $ref: '#/components/schemas/client-certificate-req'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/client-certificate-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /client:
        post:
          tags:
            - Client API
          summary: 클라이언트 등록
          description: 클라이언트를 등록합니다.
          parameters:
            - required: true
              $ref: '#/components/parameters/Authorization'
            - required: true
              $ref: '#/components/parameters/x-message-id'
            - required: true
              $ref: '#/components/parameters/x-country'
            - required: true
              $ref: '#/components/parameters/x-client-id'
            - required: true
              $ref: '#/components/parameters/x-api-key'
          requestBody:
            content:
              application/json:
                schema:
                  type: object
                  $ref: '#/components/schemas/client-register-req'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/client-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
        delete:
          tags:
            - Client API
          summary: 클라이언트 해제
          description: 클라이언트를 해제합니다.
          parameters:
            - required: true
              $ref: '#/components/parameters/Authorization'
            - required: true
              $ref: '#/components/parameters/x-message-id'
            - required: true
              $ref: '#/components/parameters/x-country'
            - required: true
              $ref: '#/components/parameters/x-client-id'
            - required: true
              $ref: '#/components/parameters/x-api-key'
          requestBody:
            content:
              application/json:
                schema:
                  type: object
                  $ref: '#/components/schemas/client-unregister-req'
          responses:
            '200':
              description: OK
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/client-res'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
    components:
      parameters:
        x-message-id:
          name: x-message-id
          in: header
          schema:
            type: string
          description: |
            요청되는 정보를 추적하기 위한 값입니다. 특정 API의 흐름을 추적하고 에러 발생 시 원인을 찾을 수 있습니다. 생성 규칙은 아래와 같습니다.
                url-safe-base64-no-padding (UUID Version 4) 방법으로 생성합니다.
                길이는 22자입니다.
          example: fNvdZ1brTn-wWKUlWGoSVw
        x-country:
          name: x-country
          in: header
          schema:
            type: string
          description: |
            서비스를 제공할 국가를 지정합니다 ISO 국가코드 알파벳 두 자리(ISO 3166-1 alpha-2)를 따릅니다. (예: KR, US, GB, ...)
          example: KR
        x-service-phase:
          name: x-service-phase
          in: header
          schema:
            type: string
          description: |
            서비스를 제공할 형상을 지정할 수 있습니다.
          example: OP
        Authorization:
          name: Authorization
          in: header
          schema:
            type: string
          description: |
            https://connect-pat.lgthinq.com 을 통해서 받은 PAT 토큰
          example: Bearer 4d76546d61f01baf31c1sd8f6b4e38b110ba0a34f825b8c5d54c
        x-client-id:
          name: x-client-id
          in: header
          schema:
            type: string
          description: |
            요청하는 클라이언트의 식별자 ID 값 입니다. unique한 값을 가질 수 있도록 생성해야 합니다.
          example: test-client-123456
        x-api-key:
          name: x-api-key
          in: header
          schema:
            type: string
          description: |
            API 호출을 위한 api key 값입니다. 아래값을 고정해서 호출해주세요.<br> "v6GFvkweNo7DK7yD3ylIZ9w52aKBU0eJ7wLXkSR3"
          example: v6GFvkweNo7DK7yD3ylIZ9w52aKBU0eJ7wLXkSR3
        x-conditional-control:
          name: x-conditional-control
          in: header
          schema:
            type: boolean
          description: |
            디바이스 상태 조회 후 제어 가능한 상태에서만 제어되도록 설정
          example: true
      schemas:
        base-res:
          type: object
          description: Response Object for any device
          properties:
            messageId:
              type: string
              description: 요청 시 헤더에 포함된 X-Message-ID 값입니다. 이 값을 응답 메시지에 포함시켜서 문제가 있을 때 확인할 수 있도록 합니다.
              example: fNvdZ1brTn-wWKUlWGoSVw
            timestamp:
              type: string
              description: 요청이 들어왔을 때의 시간을 의미하며 ISO 8601 Format을 따릅니다.
              example: '2024-09-01T06:23:20.866279'
        route-res:
          description: 도메인 이름 조회 응답
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: object
                  properties:
                    apiServer:
                      type: string
                      description: API 서버 도메인 이름
                      example: https://kic-connect-client.lgthinq.com
                    mqttServer:
                      type: string
                      description: MQTT 도메인 이름
                      example: mqtts://a3phael99lf879-ats.iot.ap-northeast-2.amazonaws.com:8883
                    webSocketServer:
                      type: string
                      description: 웹소켓 도메인 이름
                      example: wss://a3phael99lf879-ats.iot.ap-northeast-2.amazonaws.com:443/mqtt
        device-list-res:
          description: 디바이스 목록 조회 응답
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: array
                  items:
                    type: object
                    properties:
                      deviceId:
                        type: string
                        description: 디바이스를 식별할 수 있는 Id
                        example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
                      deviceInfo:
                        type: object
                        description: 디바이스에 대한 정보를 담은 객체
                        properties:
                          deviceType:
                            type: string
                            description: 디바이스 가전 타입
                            example: DEVICE_AIR_CONDITIONER
                          modelName:
                            type: string
                            description: 디바이스 모델 이름
                            example: PAC_910604_WW
                          alias:
                            type: string
                            description: 디바이스 닉네임
                            example: 거실 에어컨
                          reportable:
                            type: boolean
                            description: 디바이스 상태 변경 시 발생하는 event에 대해, event 구독 가능 여부 표시
                            example: true
                          groupId:
                            type: string
                            description: groupId, 워시타워 세탁기와 워시타워 건조기가 디바이스 식별 Id가 구분되어서 전달되는 워시타워 그룹값을 표시하기 위한 값
                            example: '234506858'
        device-profile-res:
          description: 디바이스 프로파일 조회 응답
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: 디바이스 프로파일 정보
                  example:
                    '-$ref': ../../../device-profile/air_conditioner/air_conditioner-profile-example.yaml
        device-state-res:
          description: 디바이스 상태 조회 응답
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: 디바이스 상태 정보
                  example:
                    '-$ref': ../../../device-profile/air_conditioner/air_conditioner-profile-example.yaml
        device-control-res:
          description: 디바이스 제어 응답
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: 성공 시 빈 dictionary가 전달됩니다.
                  example: {}
        push-list-res:
          description: 푸시 목록 조회 응답
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: array
                  items:
                    type: object
                    properties:
                      deviceId:
                        type: string
                        description: 푸시를 구독한 디바이스 Id
                        example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
        push-deviceId-res:
          description: 푸시 구독/해제 응답
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: 성공 시 빈 dictionary가 전달됩니다.
                  example: {}
        push-client-list-res:
          description: 사용자 푸시 clientId 목록 조회 응답
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: array
                  properties:
                    description: clientId list
                    example:
                      - ha-connect-client-st-test-230830_1st11
                      - ha-connect-client-st-test-230830_1st111
        event-list-res:
          description: 이벤트 구독 목록 조회 응답
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: array
                  items:
                    type: object
                    properties:
                      deviceId:
                        type: string
                        description: event를 구독한 디바이스 Id
                        example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
        event-register-req:
          description: 이벤트 구독 body
          type: object
          properties:
            expire:
              type: object
              description: API 만료 시간 설정, 구독한 이후 만료 시간을 넘으면 기존에 구독한 디바이스는 자동으로 해제됩니다. 만일 구독한 디바이스에 대해 다시 구독을 할 경우 만료시간이 현재시간으로부터 갱신됩니다.
              properties:
                unit:
                  type: string
                  description: 시간 단위 (고정값 - HOUR)
                  example: HOUR
                timer:
                  type: integer
                  description: |
                    이벤트 구독 만료 시간을 결정합니다. (기본 1시간, 최소 1시간, 최대 24시간) 
                  example: 1
        event-deviceId-res:
          description: 이벤트 구독/해제 응답
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: 성공 시 빈 dictionary가 전달됩니다.
                  example: {}
        client-certificate-req:
          description: 클라이언트 인증 body
          type: object
          properties:
            body:
              type: object
              description: 사용자 정보
              properties:
                service-code:
                  type: string
                  description: 서비스 코드 (고정값 - SVC202)
                  example: SVC202
                csr:
                  type: string
                  description: 디바이스에서 자체 생성한 Private Key 기반의 CSR 데이터
                  example: '===xzx'
        client-certificate-res:
          description: 클라이언트 인증서 등록 응답
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: object
                  properties:
                    resultCode:
                      type: string
                      description: 결과 응답 code
                      example: '0000'
                    result:
                      type: object
                      properties:
                        certificatePem:
                          type: string
                          description: AWS IoT 인증서
                          example: |
                            -----BEGIN CERTIFICATE-----
                            MIIEUzCCAzugAw
                            -----END CERTIFICATE-----
                        subscriptions:
                          type: array
                          desription: 클라이언트에서 MQTT subscribe가 필요한 Topic 목록 (List)
                          example:
                            - app/clients/home-assistant-test-01234/push
        client-register-req:
          description: 클라이언트 구독 body
          type: object
          properties:
            body:
              type: object
              description: 사용자 정보
              properties:
                type:
                  type: string
                  description: Push type (고정값 - MQTT)
                  example: MQTT
                service-code:
                  type: string
                  description: 서비스 코드 (고정값 - SVC202)
                  example: SVC202
                device-type:
                  type: string
                  description: 클라이언트 디바이스타입 (고정값 - 607)
                  example: '607'
        client-res:
          description: 클라이언트 구독/해제 응답
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: 성공 시 빈 dictionary가 전달됩니다.
                  example: {}
        client-unregister-req:
          description: 클라이언트 해제 body
          type: object
          properties:
            body:
              type: object
              description: 사용자 정보
              properties:
                type:
                  type: string
                  description: Push type (고정값 - MQTT)
                  example: MQTT
                service-code:
                  type: string
                  description: 서비스 코드 (고정값 - SVC202)
                  example: SVC202
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
        water_heater-object-example:
          value:
            waterHeaterJobMode:
              currentJobMode: VACATION
            temperature:
              currentTemperature: 42
              targetTemperature: 52
            operation:
              waterHeaterOperationMode: POWER_ON
        ceiling_fan-object-example:
          value:
            airFlow:
              windStrength: LOW
            operation:
              ceilingfanOperationMode: POWER_ON
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
        robot_cleaner-object-example:
          title: Robot_Cleaner
          value:
            runState:
              currentState: CHARGING
            robotCleanerJobMode:
              currentJobMode: ZIGZAG
            battery:
              level: FULL
        stick_cleaner-object-example:
          value:
            runState:
              currentState: STANDBY
            stickCleanerJobMode:
              currentJobMode: 'OFF'
            battery:
              level: HIGH
        refrigerator-command-example:
          description: 냉장고 - 절전 모드 설정
          value:
            powerSave:
              powerSaveEnabled: true
        wine_cellar-command-example:
          description: 와인셀러 - 조명 밝기
          value:
            operation:
              lightStatus: 90
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
        styler-command-example:
          description: 스타일러 - 운전 모드
          value:
            operation:
              stylerOperationMode: START
        dish_washer-command-example:
          description: 식기세척기 - 운전 모드
          value:
            operation:
              dishWasherOperationMode: START
        washtower_washer-command-example:
          description: 워시타워 세탁기 - 세탁 시작
          value:
            operation:
              washerOperationMode: START
            location:
              locationName: MAIN
        washtower_dryer-command-example:
          description: 워시타워(건조기) - 전원 POWER_OFF
          value:
            operation:
              dryerOperationMode: POWER_OFF
        washtower-command-example:
          description: 워시타워 - 건조기 시작
          value:
            dryer:
              operation:
                dryerOperationMode: START
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
        oven-command-example:
          title: Oven
          description: 오븐 - 오븐 동작
          value:
            location:
              locationName: LOWER
            operation:
              ovenOperationMode: START
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
        air_conditioner-command-example:
          description: 에어컨 - 지정한 켜짐 예약시간
          value:
            timer:
              absoluteHourToStart: 10
              absoluteMinuteToStart: 36
        system_boiler-command-example:
          description: 시스템 보일러 - 전원 ON
          value:
            operation:
              boilerOperationMode: POWER_ON
        air_purifier-command-example:
          description: 공기청정기 - 운전 모드
          value:
            airPurifierJobMode:
              currentJobMode: CLEAN
        dehumidifier-command-example:
          description: 가습기 - 운전 모드
          value:
            humidifierJobMode:
              currentJobMode: HUMIDIFY
        humidifier-command-example:
          title: Humidifier
          description: 가습기 - 운전 모드
          value:
            humidifierJobMode:
              currentJobMode: HUMIDIFY
        water_heater-command-example:
          description: 온수기 - 운전모드
          value:
            waterHeaterJobMode:
              currentJobMode: AUTO
        ceiling_fan-command-example:
          description: 실링팬 - 운전 모드
          value:
            operation:
              ceilingfanOperationMode: POWER_ON
        air_purifier_fan-command-example:
          description: 공기청정팬 - 운전 모드
          value:
            airFanJobMode:
              currentJobMode: SPOT_CLEAN
        robot_cleaner-command-example:
          title: Robot_Cleaner
          description: 로봇청소기 - 청소 모드
          value:
            operation:
              cleanOperationMode: HOMING
    x-tagGroups:
      - name: Token
        tags:
          - PAT(Personal Access Token)
      - name: Base URL
        tags:
          - Base URL
      - name: APIs
        tags:
          - Route API
          - Device API
          - Push API
          - Event API
          - Client API
---
