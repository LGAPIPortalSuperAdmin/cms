---
contents:
  lang: yaml
  code: >
    openapi: 3.1.0
    
    info:
      title: ThinQ Connect API
      version: null
    tags:
      - name: PAT(Personal Access Token)
        description: >
          ThinQ API를 호출하기 위해 사용되는 개인 식별 토큰입니다. 
          개인적이고 비상업적 목적으로만 개인 권한 토큰을 사용할 수 있습니다. 개인 권한 토큰을 사용하여 LG전자가 허용하지 않은 추가 서비스를 개발하고자 하는 경우, LG전자와 이러한 잠재적 추가 서비스에 대해 논의하고 LG전자로부터 서면 동의를 받아야 합니다.
            1. https://connect-pat.lgthinq.com 페이지를 방문하세요.
            2. ThinQ 계정 로그인을 합니다.
            3. "새 토큰 만들기" 버튼을 선택합니다.
            4. 토큰 이름을 입력합니다.
            5. 권한 범위에서 해당 토큰이 사용하고자 하는 기능에 대해서 선택합니다.
            6. "토큰 만들기" 버튼을 누르면 토큰이 생성되고, PAT 페이지로 돌아갑니다.
            7. 새로 생성된 토큰을 복사해서 사용합니다.
      - name: Device API
        description: >
          ThinQ 기기 정보를 요청하고 제어하기 위한 API입니다.
      - name: Push API
        description: >
          ThinQ 기기에서 발생하는 푸쉬 메시지를 구독/해제하기 위한 API입니다.
      - name: Event API
        description: >
          ThinQ 기기에서 발생한 상태 변경에 대한 이벤트 메시지를 구독/해제하기 위한 API입니다.
      - name: Client API
        description: >
          ThinQ 기기에서 전달하는 메시지를 받기 위한 사용자 기기 인증서 발급/등록을 위한 API입니다.

    x-tagGroups:
      - name: Token
        tags:
          - PAT(Personal Access Token)
      - name: APIs
        tags:
          - Device API
          - Push API
          - Event API
          - Client API
    servers:
      - url: https://api-kic.lgthinq.com
      - url: https://api-aic.lgthinq.com
      - url: https://api-eic.lgthinq.com

    paths:
      /devices:
        $ref: path/devices/devices.yaml
      /devices/{deviceId}/profile:
        $ref: path/devices/devices_{deviceId}_profile.yaml
      /devices/{deviceId}/state:
        $ref: path/devices/devices_{deviceId}_state.yaml
      /devices/{deviceId}/control:
        $ref: path/devices/devices_{deviceId}_control.yaml
      /push:
        $ref: path/push/push.yaml
      /push/{deviceId}/subscribe:
        $ref: path/push/push_{deviceId}_subscribe.yaml
      /push/{deviceId}/unsubscribe:
        $ref: path/push/push_{deviceId}_unsubscribe.yaml
      /push/devices:
        $ref: path/push/push_devices.yaml
      /event:
        $ref: path/event/event.yaml
      /event/{deviceId}/subscribe:
        $ref: path/event/event_{deviceId}_subscribe.yaml
      /event/{deviceId}/unsubscribe:
        $ref: path/event/event_{deviceId}_unsubscribe.yaml
      /client/certificate:
        $ref: path/client/client_certificate.yaml
      /client:
        $ref: path/client/client.yaml

---
