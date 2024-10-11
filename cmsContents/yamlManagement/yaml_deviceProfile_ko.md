---
contents:
  lang: yaml
  code: >
    openapi: 3.1.0

    info:
      version: null
      title: 디바이스 프로파일
    servers:
      - url: https://ap.api.lge.com
    tags:
      - name: overview
        x-displayName: 개요
        x-traitTag: true
        description: |
          **디바이스 프로파일**은 디바이스의 상태를 기술하거나 디바이스를 제어할 수 있는 속성들을 정의합니다. 디바이스 프로파일은 디바이스 타입별로 제공되며 같은 타입이라도 제품 또는 모델에 따라 내용에 차이가 있을 수 있습니다. 디바이스 프로파일에 정의된 속성을 이용하여 디바이스의 상태 조회 및 제어와 관련된 기능을 당신의 서비스에 적용하세요.
          본 문서에서는 디바이스 타입별로 아래의 내용을 설명합니다.

            - **디바이스 프로파일 스키마**
              
              **디바이스 프로파일 조회 API**를 호출하여 수신한 디바이스 프로파일의 스키마에 대하여 설명합니다.
              스키마와 함께 기재된 디바이스 프로파일의 메시지 예제를 참고하세요.
              디바이스 프로파일 메시지는 아래의 항목으로 구성되며 디바이스 타입에 따라 그 구성이 다를 수 있습니다.

                | Item | Description |
                |-|-|
                | property | 속성별 Read/Write 지원 여부와 값의 특성 |
                | notification |해당 디바이스에서 지원하는 푸시 메시지의 종류 |
                | error |해당 디바이스에서 지원하는 에러 유형 |
                | extensonProperty | 확장된 속성 |

            - **요청/응답 스키마**
              
              디바이스 프로파일을 기반으로 작성되는 **디바이스 상태 조회 API**의 응답 메시지와 **디바이스 제어 API**의 요청 메시지에 대하여 설명합니다.
              
      - name: device type
        x-displayName: 디바이스 타입
        x-traitTag: true
        description: |
          **디바이스 타입**은 디바이스의 특성을 구분하며 **디바이스 목록 조회 API** 응답에서 디바이스의 종류를 구분할 수 있게 해줍니다. 디바이스 프로파일은 이 디바이스 타입에 따라 정의됩니다.

            | Device Type | Name |
            |-|-|
            | DEVICE_REFRIGERATOR | 냉장고 |
            | DEVICE_WASHER | 세탁기 |
            | DEVICE_DRYER | 건조기 |
            | DEVICE_AIR_CONDITIONER | 에어컨 |
            | DEVICE_AIR_PURIFIER | 공기청정기 |
            | DEVICE_ROBOT_CLEANER | 로봇청소기 |
            | DEVICE_OVEN | 오븐 |
            | DEVICE_DISH_WASHER | 식기세척기 |
            | DEVICE_STYLER | 스타일러 |
            | DEVICE_WATER_PURIFIER | 정수기 |
            | DEVICE_DEHUMIDIFIER | 제습기 |
            | DEVICE_CEILING_FAN | 실링팬 |
            | DEVICE_WINE_CELLAR | 와인셀러 |
            | DEVICE_KIMCHI_REFRIGERATOR | 김치냉장고 |
            | DEVICE_HOME_BREW | 홈브루 |
            | DEVICE_PLANT_CULTIVATOR | 식물재배기 |
            | DEVICE_WASHTOWER_WASHER | 워시타워(세탁기) |
            | DEVICE_WASHTOWER_DRYER | 워시타워(건조기) |
            | DEVICE_WASHTOWER | 워시타워 |
            | DEVICE_COOKTOP | 쿡탑 |
            | DEVICE_HOOD | 후드 |
            | DEVICE_MICROWAVE_OVEN | 전자레인지 |
            | DEVICE_SYSTEM_BOILER | 시스템 보일러 |
            | DEVICE_AIR_PURIFIER_FAN | 공기청정팬 |
            | DEVICE_STICK_CLEANER | 스틱청소기 |
            | DEVICE_WATER_HEATER | 온수기 |
            | DEVICE_WASHCOMBO_MAIN | 워시콤보 (메인) |
            | DEVICE_WASHCOMBO_MINI | 워시콤보 (미니) |
            | DEVICE_HUMIDIFIER | 가습기 |
            | DEVICE_ODU | LG BECON Cloud에 등록된 시스템 에어컨의 실외기 |
            | DEVICE_IDU | LG BECON Cloud에 등록된 시스템 에어컨의 실내기 |
            | DEVICE_SIGNAGE | 사이니지 |
      - name: refrigerator
        x-displayName: 냉장고
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/refrigerator-profile"
            exampleRef="#/components/examples/refrigerator-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/refrigerator-object"
            exampleRef="#/components/examples/refrigerator-object-example" />

          ### 디바이스 제어 요청
          디바이스 프로파일에 'w' 권한이 있는 property는 제어가 가능하다. 제어하고자 하는 property의 상위 key 값과 value로 request body를 작성한다.
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/refrigerator-command-example" />
      - name: washer
        x-displayName: 세탁기
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/washer-profile"
            exampleRef="#/components/examples/washer-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/washer-object"
            exampleRef="#/components/examples/washer-object-example" />

          ### 디바이스 제어 요청
          디바이스 프로파일에 'w' 권한이 있는 property는 제어가 가능하다. 제어하고자 하는 property의 상위 key 값과 value로 request body를 작성한다.
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/washer-command-example" />
      - name: dryer
        x-displayName: 건조기
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/dryer-profile"
            exampleRef="#/components/examples/dryer-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/dryer-object"
            exampleRef="#/components/examples/dryer-object-example" />

          ### 디바이스 제어 요청
          디바이스 프로파일에 'w' 권한이 있는 property는 제어가 가능하다. 제어하고자 하는 property의 상위 key 값과 value로 request body를 작성한다.
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/dryer-command-example" />
      - name: air_conditioner
        x-displayName: 에어컨
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/air_conditioner-profile"
            exampleRef="#/components/examples/air_conditioner-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/air_conditioner-object"
            exampleRef="#/components/examples/air_conditioner-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/air_conditioner-command-example" />
      - name: air_purifier
        x-displayName: 공기청정기
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/air_purifier-profile"
            exampleRef="#/components/examples/air_purifier-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/air_purifier-object"
            exampleRef="#/components/examples/air_purifier-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/air_purifier-command-example" />
      - name: robot_cleaner
        x-displayName: 로봇청소기
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/robot_cleaner-profile"
            exampleRef="#/components/examples/robot_cleaner-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/robot_cleaner-object"
            exampleRef="#/components/examples/robot_cleaner-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/robot_cleaner-command-example" />
      - name: oven
        x-displayName: 오븐
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/oven-profile"
            exampleRef="#/components/examples/oven-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/oven-object"
            exampleRef="#/components/examples/oven-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/oven-command-example" />
      - name: dish_washer
        x-displayName: 식기세척기
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/dish_washer-profile"
            exampleRef="#/components/examples/dish_washer-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/dish_washer-object"
            exampleRef="#/components/examples/dish_washer-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/dish_washer-command-example" />
      - name: styler
        x-displayName: 스타일러
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/styler-profile"
            exampleRef="#/components/examples/styler-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/styler-object"
            exampleRef="#/components/examples/styler-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/styler-command-example" />
      - name: water_purifier
        x-displayName: 정수기
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/water_purifier-profile"
            exampleRef="#/components/examples/water_purifier-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/water_purifier-object"
            exampleRef="#/components/examples/water_purifier-object-example" />

          ### 디바이스 제어 요청
          정수기 디바이스는 제어 요청을 미지원합니다.
      - name: dehumidifier
        x-displayName: 제습기
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/dehumidifier-profile"
            exampleRef="#/components/examples/dehumidifier-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/dehumidifier-object"
            exampleRef="#/components/examples/dehumidifier-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/dehumidifier-command-example" />
      - name: ceiling_fan
        x-displayName: 실링팬
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/ceiling_fan-profile"
            exampleRef="#/components/examples/ceiling_fan-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/ceiling_fan-object"
            exampleRef="#/components/examples/ceiling_fan-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/ceiling_fan-command-example" />
      - name: wine_cellar
        x-displayName: 와인셀러
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/wine_cellar-profile"
            exampleRef="#/components/examples/wine_cellar-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/wine_cellar-object"
            exampleRef="#/components/examples/wine_cellar-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/wine_cellar-command-example" />
      - name: kimchi_refrigerator
        x-displayName: 김치냉장고
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/kimchi_refrigerator-profile"
            exampleRef="#/components/examples/kimchi_refrigerator-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/kimchi_refrigerator-object"
            exampleRef="#/components/examples/kimchi_refrigerator-object-example" />

          ### 디바이스 제어 요청
          김치냉장고 디바이스는 제어 요청을 미지원합니다.
      - name: home_brew
        x-displayName: 홈브루
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/home_brew-profile"
            exampleRef="#/components/examples/home_brew-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/home_brew-object"
            exampleRef="#/components/examples/home_brew-object-example" />

          ### 디바이스 제어 요청
          홈브루 디바이스는 제어 요청을 미지원합니다.
      - name: plant_cultivator
        x-displayName: 식물재배기
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/plant_cultivator-profile"
            exampleRef="#/components/examples/plant_cultivator-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/plant_cultivator-object"
            exampleRef="#/components/examples/plant_cultivator-object-example" />

          ### 디바이스 제어 요청
          식물재배기 디바이스는 제어 요청을 미지원합니다.
      - name: washtower_washer
        x-displayName: 워시타워(세탁기)
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/washtower_washer-profile"
            exampleRef="#/components/examples/washtower_washer-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/washtower_washer-object"
            exampleRef="#/components/examples/washtower_washer-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/washtower_washer-command-example" />
      - name: washtower_dryer
        x-displayName: 워시타워(건조기)
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/washtower_dryer-profile"
            exampleRef="#/components/examples/washtower_dryer-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/washtower_dryer-object"
            exampleRef="#/components/examples/washtower_dryer-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/washtower_dryer-command-example" />
      - name: washtower
        x-displayName: 워시타워
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/washtower-profile"
            exampleRef="#/components/examples/washtower-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/washtower-object"
            exampleRef="#/components/examples/washtower-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/washtower-command-example" />
      - name: cooktop
        x-displayName: 쿡탑
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/cooktop-profile"
            exampleRef="#/components/examples/cooktop-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/cooktop-object"
            exampleRef="#/components/examples/cooktop-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/cooktop-command-example" />
      - name: hood
        x-displayName: 후드
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/hood-profile"
            exampleRef="#/components/examples/hood-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/hood-object"
            exampleRef="#/components/examples/hood-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/hood-command-example" />
      - name: microwave_oven
        x-displayName: 전자레인지
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/microwave_oven-profile"
            exampleRef="#/components/examples/microwave_oven-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/microwave_oven-object"
            exampleRef="#/components/examples/microwave_oven-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/microwave_oven-command-example" />
      - name: system_boiler
        x-displayName: 시스템 보일러
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/system_boiler-profile"
            exampleRef="#/components/examples/system_boiler-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/system_boiler-object"
            exampleRef="#/components/examples/system_boiler-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/system_boiler-command-example" />
      - name: air_purifier_fan
        x-displayName: 공기청정팬
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/air_purifier_fan-profile"
            exampleRef="#/components/examples/air_purifier_fan-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/air_purifier_fan-object"
            exampleRef="#/components/examples/air_purifier_fan-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/air_purifier_fan-command-example" />
      - name: stick_cleaner
        x-displayName: 스틱청소기
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/stick_cleaner-profile"
            exampleRef="#/components/examples/stick_cleaner-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/stick_cleaner-object"
            exampleRef="#/components/examples/stick_cleaner-object-example" />

          ### 디바이스 제어 요청
          스틱청소기 디바이스는 제어 요청을 미지원합니다. (확인 필요함)
      - name: water_heater
        x-displayName: 온수기
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/water_heater-profile"
            exampleRef="#/components/examples/water_heater-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/water_heater-object"
            exampleRef="#/components/examples/water_heater-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/water_heater-command-example" />
      - name: main_washcombo
        x-displayName: 워시콤보 (메인)
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/main_washcombo-profile"
            exampleRef="#/components/examples/main_washcombo-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/main_washcombo-object"
            exampleRef="#/components/examples/main_washcombo-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/main_washcombo-command-example" />
      - name: mini_washcombo
        x-displayName: 워시콤보 (미니)
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/mini_washcombo-profile"
            exampleRef="#/components/examples/mini_washcombo-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/mini_washcombo-object"
            exampleRef="#/components/examples/mini_washcombo-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/mini_washcombo-command-example" />
      - name: humidifier
        x-displayName: 가습기
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/humidifier-profile"
            exampleRef="#/components/examples/humidifier-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/humidifier-object"
            exampleRef="#/components/examples/humidifier-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/device-command-schema"
            exampleRef="#/components/examples/humidifier-command-example" />
      - name: odu
        x-displayName: 실외기
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/odu-profile"
            exampleRef="#/components/examples/odu-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/odu-object"
            exampleRef="#/components/examples/odu-object-example" />

          ### 디바이스 제어 요청
          실외기 디바이스는 제어 요청을 미지원합니다.
      - name: idu
        x-displayName: 실내기
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/idu-profile"
            exampleRef="#/components/examples/idu-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/idu-object"
            exampleRef="#/components/examples/idu-object-example" />

          ### 디바이스 제어 요청
          <SchemaDefinition
            schemaRef="#/components/schemas/idu-command-schema"
            exampleRef="#/components/examples/idu-command-example" />
      - name: signage
        x-displayName: 사이니지
        description: |
          ## 디바이스 프로파일 스키마
          <SchemaDefinition
            schemaRef="#/components/schemas/signage-profile"
            exampleRef="#/components/examples/signage-profile-example" />

          ## 요청/응답 스키마
          ### 디바이스 상태 응답
          <SchemaDefinition
            schemaRef="#/components/schemas/signage-object"
            exampleRef="#/components/examples/signage-object-example" />

          ### 디바이스 제어 요청
          디바이스 프로파일 스키마에서 'w' 권한이 있는 값은 제어가 가능하다. API호출 1회에 하나의 값만 제어할 수 있다.
          <SchemaDefinition
            schemaRef="#/components/schemas/signage-command-schema"
            exampleRef="#/components/examples/signage-command-example" />

          화면 ON / OFF
          ```json
            {
              "power": {
                "screen": "SCREEN_ON"
              }
            }
          ```
          디스플레이 포트설정
          ```json
            {
              "display": {
                "input": "90"
              }
            }
          ```
          디스플레이 화면 모드
          ```json
            {
              "display": {
                "pictureMode": "00"
              }
            }
          ```
          오디오 볼륨 설정
          ```json
            {
              "audio": {
                "volume": 10
              }
            }
          ```
          오디오 음소거
          ```json
            {
              "audio": {
                "volumeMute": true
              }
            }
          ```
    paths:
      /device-profile:
        get:
          summary: device profile
          description: device profile
          operationId: device-profile
          security:
            - basic_auth: []
          responses:
            '200':
              description: device profile
              content:
                application/json:
                  schema:
                    oneOf:
                      - $ref: '#/components/schemas/refrigerator-profile'
                      - $ref: '#/components/schemas/refrigerator-object'
                      - $ref: '#/components/schemas/device-command-schema'
                      - $ref: '#/components/schemas/washer-profile'
                      - $ref: '#/components/schemas/washer-object'
                      - $ref: '#/components/schemas/dryer-profile'
                      - $ref: '#/components/schemas/dryer-object'
                      - $ref: '#/components/schemas/air_conditioner-profile'
                      - $ref: '#/components/schemas/air_conditioner-object'
                      - $ref: '#/components/schemas/air_purifier-profile'
                      - $ref: '#/components/schemas/air_purifier-object'
                      - $ref: '#/components/schemas/air_purifier_fan-profile'
                      - $ref: '#/components/schemas/air_purifier_fan-object'
                      - $ref: '#/components/schemas/dehumidifier-profile'
                      - $ref: '#/components/schemas/dehumidifier-object'
                      - $ref: '#/components/schemas/humidifier-profile'
                      - $ref: '#/components/schemas/humidifier-object'
                      - $ref: '#/components/schemas/robot_cleaner-profile'
                      - $ref: '#/components/schemas/robot_cleaner-object'
                      - $ref: '#/components/schemas/oven-profile'
                      - $ref: '#/components/schemas/oven-object'
                      - $ref: '#/components/schemas/dish_washer-profile'
                      - $ref: '#/components/schemas/dish_washer-object'
                      - $ref: '#/components/schemas/styler-profile'
                      - $ref: '#/components/schemas/styler-object'
                      - $ref: '#/components/schemas/water_purifier-profile'
                      - $ref: '#/components/schemas/water_purifier-object'
                      - $ref: '#/components/schemas/ceiling_fan-profile'
                      - $ref: '#/components/schemas/ceiling_fan-object'
                      - $ref: '#/components/schemas/wine_cellar-profile'
                      - $ref: '#/components/schemas/wine_cellar-object'
                      - $ref: '#/components/schemas/kimchi_refrigerator-profile'
                      - $ref: '#/components/schemas/kimchi_refrigerator-object'
                      - $ref: '#/components/schemas/home_brew-profile'
                      - $ref: '#/components/schemas/home_brew-object'
                      - $ref: '#/components/schemas/plant_cultivator-profile'
                      - $ref: '#/components/schemas/plant_cultivator-object'
                      - $ref: '#/components/schemas/washtower_washer-profile'
                      - $ref: '#/components/schemas/washtower_washer-object'
                      - $ref: '#/components/schemas/washtower_dryer-profile'
                      - $ref: '#/components/schemas/washtower_dryer-object'
                      - $ref: '#/components/schemas/washtower-profile'
                      - $ref: '#/components/schemas/washtower-object'
                      - $ref: '#/components/schemas/cooktop-profile'
                      - $ref: '#/components/schemas/cooktop-object'
                      - $ref: '#/components/schemas/hood-profile'
                      - $ref: '#/components/schemas/hood-object'
                      - $ref: '#/components/schemas/microwave_oven-profile'
                      - $ref: '#/components/schemas/microwave_oven-object'
                      - $ref: '#/components/schemas/system_boiler-profile'
                      - $ref: '#/components/schemas/system_boiler-object'
                      - $ref: '#/components/schemas/stick_cleaner-profile'
                      - $ref: '#/components/schemas/stick_cleaner-object'
                      - $ref: '#/components/schemas/water_heater-profile'
                      - $ref: '#/components/schemas/water_heater-object'
                      - $ref: '#/components/schemas/main_washcombo-profile'
                      - $ref: '#/components/schemas/main_washcombo-object'
                      - $ref: '#/components/schemas/mini_washcombo-profile'
                      - $ref: '#/components/schemas/mini_washcombo-object'
                      - $ref: '#/components/schemas/odu-profile'
                      - $ref: '#/components/schemas/odu-object'
                      - $ref: '#/components/schemas/idu-profile'
                      - $ref: '#/components/schemas/idu-object'
                      - $ref: '#/components/schemas/idu-command-schema'
                      - $ref: '#/components/schemas/signage-profile'
                      - $ref: '#/components/schemas/signage-object'
                      - $ref: '#/components/schemas/signage-command-schema'
                  examples:
                    refrigerator-profile-example:
                      $ref: '#/components/examples/refrigerator-profile-example'
                    refrigerator-object-example:
                      $ref: '#/components/examples/refrigerator-object-example'
                    refrigerator-command-example:
                      $ref: '#/components/examples/refrigerator-command-example'
                    washer-profile-example:
                      $ref: '#/components/examples/washer-profile-example'
                    washer-object-example:
                      $ref: '#/components/examples/washer-object-example'
                    washer-command-example:
                      $ref: '#/components/examples/washer-command-example'
                    dryer-profile-example:
                      $ref: '#/components/examples/dryer-profile-example'
                    dryer-object-example:
                      $ref: '#/components/examples/dryer-object-example'
                    dryer-command-example:
                      $ref: '#/components/examples/dryer-command-example'
                    air_conditioner-profile-example:
                      $ref: '#/components/examples/air_conditioner-profile-example'
                    air_conditioner-object-example:
                      $ref: '#/components/examples/air_conditioner-object-example'
                    air_conditioner-command-example:
                      $ref: '#/components/examples/air_conditioner-command-example'
                    air_purifier-profile-example:
                      $ref: '#/components/examples/air_purifier-profile-example'
                    air_purifier-object-example:
                      $ref: '#/components/examples/air_purifier-object-example'
                    air_purifier-command-example:
                      $ref: '#/components/examples/air_purifier-command-example'
                    air_purifier_fan-profile-example:
                      $ref: '#/components/examples/air_purifier_fan-profile-example'
                    air_purifier_fan-object-example:
                      $ref: '#/components/examples/air_purifier_fan-object-example'
                    air_purifier_fan-command-example:
                      $ref: '#/components/examples/air_purifier_fan-command-example'
                    dehumidifier-profile-example:
                      $ref: '#/components/examples/dehumidifier-profile-example'
                    dehumidifier-object-example:
                      $ref: '#/components/examples/dehumidifier-object-example'
                    dehumidifier-command-example:
                      $ref: '#/components/examples/dehumidifier-command-example'
                    humidifier-profile-example:
                      $ref: '#/components/examples/humidifier-profile-example'
                    humidifier-object-example:
                      $ref: '#/components/examples/humidifier-object-example'
                    humidifier-command-example:
                      $ref: '#/components/examples/humidifier-command-example'
                    robot_cleaner-profile-example:
                      $ref: '#/components/examples/robot_cleaner-profile-example'
                    robot_cleaner-object-example:
                      $ref: '#/components/examples/robot_cleaner-object-example'
                    robot_cleaner-command-example:
                      $ref: '#/components/examples/robot_cleaner-command-example'
                    oven-profile-example:
                      $ref: '#/components/examples/oven-profile-example'
                    oven-object-example:
                      $ref: '#/components/examples/oven-object-example'
                    oven-command-example:
                      $ref: '#/components/examples/oven-command-example'
                    dish_washer-profile-example:
                      $ref: '#/components/examples/dish_washer-profile-example'
                    dish_washer-object-example:
                      $ref: '#/components/examples/dish_washer-object-example'
                    dish_washer-command-example:
                      $ref: '#/components/examples/dish_washer-command-example'
                    styler-profile-example:
                      $ref: '#/components/examples/styler-profile-example'
                    styler-object-example:
                      $ref: '#/components/examples/styler-object-example'
                    styler-command-example:
                      $ref: '#/components/examples/styler-command-example'
                    water_purifier-profile-example:
                      $ref: '#/components/examples/water_purifier-profile-example'
                    water_purifier-object-example:
                      $ref: '#/components/examples/water_purifier-object-example'
                    ceiling_fan-profile-example:
                      $ref: '#/components/examples/ceiling_fan-profile-example'
                    ceiling_fan-object-example:
                      $ref: '#/components/examples/ceiling_fan-object-example'
                    ceiling_fan-command-example:
                      $ref: '#/components/examples/ceiling_fan-command-example'
                    wine_cellar-profile-example:
                      $ref: '#/components/examples/wine_cellar-profile-example'
                    wine_cellar-object-example:
                      $ref: '#/components/examples/wine_cellar-object-example'
                    wine_cellar-command-example:
                      $ref: '#/components/examples/wine_cellar-command-example'
                    kimchi_refrigerator-profile-example:
                      $ref: '#/components/examples/kimchi_refrigerator-profile-example'
                    kimchi_refrigerator-object-example:
                      $ref: '#/components/examples/kimchi_refrigerator-object-example'
                    home_brew-profile-example:
                      $ref: '#/components/examples/home_brew-profile-example'
                    home_brew-object-example:
                      $ref: '#/components/examples/home_brew-object-example'
                    plant_cultivator-profile-example:
                      $ref: '#/components/examples/plant_cultivator-profile-example'
                    plant_cultivator-object-example:
                      $ref: '#/components/examples/plant_cultivator-object-example'
                    washtower_washer-profile-example:
                      $ref: '#/components/examples/washtower_washer-profile-example'
                    washtower_washer-object-example:
                      $ref: '#/components/examples/washtower_washer-object-example'
                    washtower_washer-command-example:
                      $ref: '#/components/examples/washtower_washer-command-example'
                    washtower_dryer-profile-example:
                      $ref: '#/components/examples/washtower_dryer-profile-example'
                    washtower_dryer-object-example:
                      $ref: '#/components/examples/washtower_dryer-object-example'
                    washtower_dryer-command-example:
                      $ref: '#/components/examples/washtower_dryer-command-example'
                    washtower-profile-example:
                      $ref: '#/components/examples/washtower-profile-example'
                    washtower-object-example:
                      $ref: '#/components/examples/washtower-object-example'
                    washtower-command-example:
                      $ref: '#/components/examples/washtower-command-example'
                    cooktop-profile-example:
                      $ref: '#/components/examples/cooktop-profile-example'
                    cooktop-object-example:
                      $ref: '#/components/examples/cooktop-object-example'
                    cooktop-command-example:
                      $ref: '#/components/examples/cooktop-command-example'
                    hood-profile-example:
                      $ref: '#/components/examples/hood-profile-example'
                    hood-object-example:
                      $ref: '#/components/examples/hood-object-example'
                    hood-command-example:
                      $ref: '#/components/examples/hood-command-example'
                    microwave_oven-profile-example:
                      $ref: '#/components/examples/microwave_oven-profile-example'
                    microwave_oven-object-example:
                      $ref: '#/components/examples/microwave_oven-object-example'
                    microwave_oven-command-example:
                      $ref: '#/components/examples/microwave_oven-command-example'
                    system_boiler-profile-example:
                      $ref: '#/components/examples/system_boiler-profile-example'
                    system_boiler-object-example:
                      $ref: '#/components/examples/system_boiler-object-example'
                    system_boiler-command-example:
                      $ref: '#/components/examples/system_boiler-command-example'
                    stick_cleaner-profile-example:
                      $ref: '#/components/examples/stick_cleaner-profile-example'
                    stick_cleaner-object-example:
                      $ref: '#/components/examples/stick_cleaner-object-example'
                    water_heater-profile-example:
                      $ref: '#/components/examples/water_heater-profile-example'
                    water_heater-object-example:
                      $ref: '#/components/examples/water_heater-object-example'
                    water_heater-command-example:
                      $ref: '#/components/examples/water_heater-command-example'
                    main_washcombo-profile-example:
                      $ref: '#/components/examples/main_washcombo-profile-example'
                    main_washcombo-object-example:
                      $ref: '#/components/examples/main_washcombo-object-example'
                    main_washcombo-command-example:
                      $ref: '#/components/examples/main_washcombo-command-example'
                    mini_washcombo-profile-example:
                      $ref: '#/components/examples/mini_washcombo-profile-example'
                    mini_washcombo-object-example:
                      $ref: '#/components/examples/mini_washcombo-object-example'
                    mini_washcombo-command-example:
                      $ref: '#/components/examples/mini_washcombo-command-example'
                    odu-profile-example:
                      $ref: '#/components/examples/odu-profile-example'
                    odu-object-example:
                      $ref: '#/components/examples/odu-object-example'
                    idu-profile-example:
                      $ref: '#/components/examples/idu-profile-example'
                    idu-object-example:
                      $ref: '#/components/examples/idu-object-example'
                    idu-command-example:
                      $ref: '#/components/examples/idu-command-example'
                    signage-profile-example:
                      $ref: '#/components/examples/signage-profile-example'
                    signage-object-example:
                      $ref: '#/components/examples/signage-object-example'
                    signage-command-example:
                      $ref: '#/components/examples/signage-command-example'
            '400':
              description: device-profile
    components:
      securitySchemes:
        basic_auth:
          type: http
          scheme: basic
      schemas:
        refrigerator-profile:
          type: object
          title: Refrigerator
          properties:
            property:
              type: object
              properties:
                temperature:
                  type: array
                  description: 온도
                  items:
                    type: object
                    properties:
                      locationName:
                        type: string
                        enum:
                          - FRIDGE
                          - FREEZER
                          - CONVERTIBLE
                        description: |-
                          위치 이름
                          Value | Description
                          -|-
                          FRIDGE | 냉장실
                          FREEZER | 냉동실
                          CONVERTIBLE | 컨버터블
                      targetTemperature:
                        type: object
                        description: 희망온도
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                              w:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                      unit:
                        type: string
                        enum:
                          - C
                          - F
                        description: |-
                          Value | Description
                          -|-
                          C | 섭씨
                          F | 화씨
                refrigeration:
                  type: object
                  description: 기능
                  properties:
                    expressMode:
                      type: object
                      description: 특급 모드 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - boolean
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                true | 특급 모드 설정
                                false | 특급 모드 해제
                              items:
                                type: boolean
                                enum:
                                  - true
                                  - false
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                true | 특급 모드 설정
                                false | 특급 모드 해제
                              items:
                                type: boolean
                                enum:
                                  - true
                                  - false
                    rapidFreeze:
                      type: object
                      description: 급속 냉동
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - boolean
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                true | 급속 냉동 설정
                                false | 급속 냉동 해제
                              items:
                                type: boolean
                                enum:
                                  - true
                                  - false
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                true | 급속 냉동 설정
                                false | 급속 냉동 해제
                              items:
                                type: boolean
                                enum:
                                  - true
                                  - false
                    freshAirFilter:
                      type: object
                      description: 공기 필터 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                OFF | 해제
                                AUTO | 자동
                                POWER | 파워
                                REPLACE | 교체
                                SMART_POWER | 스마트 파워 모드
                                SMART_OFF | 스마트 모드 해제
                                SMART_ON | 스마트 오드 설정
                              items:
                                type: string
                                enum:
                                  - 'OFF'
                                  - AUTO
                                  - POWER
                                  - REPLACE
                                  - SMART_POWER
                                  - SMART_OFF
                                  - SMART_ON
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                OFF | 해제
                                AUTO | 자동
                                POWER | 파워
                              items:
                                typs: string
                                enum:
                                  - 'OFF'
                                  - AUTO
                                  - POWER
                    expressFridge:
                      type: object
                      description: 특습 냉장 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - boolean
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                true | 특급 냉장 설정
                                false | 특급 냉장 해제
                              items:
                                type: boolean
                                enum:
                                  - true
                                  - false
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                true | 특급 냉장 설정
                                false | 특급 냉장 해제
                              items:
                                type: boolean
                                enum:
                                  - true
                                  - false
                    expressModeName:
                      type: object
                      description: 특급 모드 이름
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                FRIDGE | 냉장실
                                FREEZER | 냉동실
                              items:
                                type: string
                                enum:
                                  - FRIDGE
                                  - FREEZER
                powerSave:
                  type: object
                  description: 절전 설정
                  properties:
                    powerSaveEnabled:
                      type: object
                      description: 절전 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - boolean
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                true | 절전 모드 설정
                                false | 절전 모드 해제
                              items:
                                type: boolean
                                enum:
                                  - true
                                  - false
                ecoFriendly:
                  type: object
                  description: 최저 운전 설정
                  properties:
                    ecoFriendlyMode:
                      type: object
                      description: 최저 운전 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - boolean
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                true | 최저 운전 설정 
                                false | 최저 운전 해제
                              items:
                                type: boolean
                                enum:
                                  - true
                                  - false
                sabbath:
                  type: object
                  description: 안식일 설정
                  properties:
                    sabbathMode:
                      type: object
                      description: 안식일 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - boolean
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                true | 안식일 설정 
                                false | 안식일 해제
                              items:
                                type: boolean
                                enum:
                                  - true
                                  - false
                doorStatus:
                  type: array
                  description: 냉장고 문 상태
                  items:
                    type: object
                    properties:
                      doorState:
                        type: object
                        description: 냉장고 문 열림 상태
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  OPEN | 문 열림 (냉장/냉동/컨버터블 중 적어도 1개 이상의 문이 열림)
                                  CLOSE | 문 닫힘 (모든 문이 닫힘)
                                items:
                                  type: string
                                  enum:
                                    - OPEN
                                    - CLOSE
                      locationName:
                        type: string
                        enum:
                          - MAIN
                        description: |-
                          위치 이름
                          Value | Description
                          -|-
                          MAIN | 냉장고 문
                waterFilterInfo:
                  type: object
                  description: 워터 필터 상태
                  properties:
                    usedTime:
                      type: object
                      description: 월단위 사용시간 (몇 개월)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
            notification:
              type: object
              properties:
                push:
                  type: array
                  minItems: 1
                  description: |-
                    Push Code | Description
                    -|-
                    FROZEN_IS_COMPLETE | 냉동이 완료되었습니다.
                    DOOR_IS_OPEN | 문이 열렸습니다.
                    TIME_TO_CHANGE_FILTER | 필터 교체 시기입니다.
                    TIME_TO_CHANGE_WATER_FILTER | 정수 필터 교체 시기입니다.
                  items:
                    type: string
                    enum:
                      - TIME_TO_CHANGE_WATER_FILTER
                      - FROZEN_IS_COMPLETE
                      - DOOR_IS_OPEN
                      - TIME_TO_CHANGE_FILTER
        refrigerator-object:
          title: Refrigerator
          properties:
            doorStatus:
              type: array
              items:
                type: object
                properties:
                  doorState:
                    type: string
                    enum:
                      - OPEN
                      - CLOSE
                  locationName:
                    type: string
                    enum:
                      - MAIN
            refrigeration:
              type: object
              properties:
                expressMode:
                  type: boolean
                  enum:
                    - true
                    - false
                rapidFreeze:
                  type: boolean
                  enum:
                    - true
                    - false
                freshAirFilter:
                  type: string
                  enum:
                    - 'OFF'
                    - AUTO
                    - POWER
                    - REPLACE
                    - SMART_POWER
                    - SMART_OFF
                    - SMART_ON
                expressFridge:
                  type: boolean
                  enum:
                    - true
                    - false
                expressModeName:
                  type: string
                  enum:
                    - FRIDGE
                    - FREEZER
            temperature:
              type: array
              items:
                type: object
                properties:
                  locationName:
                    type: string
                    enum:
                      - FRIDGE
                      - FREEZER
                      - CONVERTIBLE
                  targetTemperature:
                    type: integer
                    example: 5
                  unit:
                    type: string
                    enum:
                      - C
                      - F
            powerSave:
              type: object
              properties:
                powerSaveEnabled:
                  type: boolean
                  enum:
                    - true
                    - false
            waterFilterInfo:
              type: object
              readOnly: true
              properties:
                usedTime:
                  type: number
            ecoFriendly:
              type: object
              properties:
                ecoFriendlyMode:
                  type: boolean
                  enum:
                    - true
                    - false
            sabbath:
              type: object
              properties:
                sabbathMode:
                  type: boolean
                  enum:
                    - true
                    - false
        device-command-schema:
          title: Refrigerator
          minProperties: 1
          properties:
            상위 property:
              type: object
              properties:
                하위 property:
                  value: value
        washer-profile:
          type: object
          title: Washer
          properties:
            property:
              type: array
              items:
                type: object
                properties:
                  runState:
                    type: object
                    description: 상태
                    properties:
                      currentState:
                        type: object
                        description: 현재 상태
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  POWER_OFF | 제품 OFF
                                  INITIAL | 대기중 상태
                                  PAUSE | 일시정지
                                  DETECTING | 옷감량확인
                                  SOAKING | 불림 상태
                                  RUNNING | 행정중
                                  RINSING | 헹굼 중
                                  SPINNING | 탈수 중
                                  END | 세탁완료상태
                                  RESERVED | 예약 상태
                                  FIRMWARE | 펌웨어 업데이트 중
                                  DRYING | 건조 중
                                  COOL_DOWN | 구김 방지1
                                  RINSE_HOLD | 린스 후 일시 정지 중
                                  REFRESHING | 구김 방지2(FRESHCARE)
                                  STEAM_SOFTENING | 스팀소프트닝
                                  ERROR | 에러상태
                                  SMART_GRID_RUN | Smart Grid 동작 상태
                                  ADD_DRAIN | 배수 추가 상태
                                  DETERGENT_AMOUNT | 세제량 표시 중
                                  PREWASH | 예비 세탁 동작 상태
                                  SHOES_MODULE | 슈즈 건조 동작 상태
                                  PROOFING | 발수 처리 상태
                                  DISPENSING | 세제 자동 투입 중
                                  SOFTENING | 유연제량 확인
                                  CHECKING_TURBIDITY | 탁도감지 중(G+ Best 모델 AUTOWASH 코스 사용시)
                                  CHANGE_CONDITION | 탁도 감지 결과를 가지고 자동으로 옵션 변경 후 Display
                                  DISPLAY_LOADSIZE | 옷감량 확인 결과 Display
                                  FROZEN_PREVENT_INITIAL | 동결방지모드 대기상태
                                  FROZEN_PREVENT_RUNNING | 동결방지모드 진행상태
                                  FROZEN_PREVENT_PAUSE | 동결방지모드 멈춤상태
                                  SLEEP | Sleep 상태 
                                items:
                                  type: string
                                  enum:
                                    - POWER_OFF
                                    - INITIAL
                                    - PAUSE
                                    - DETECTING
                                    - SOAKING
                                    - RUNNING
                                    - RINSING
                                    - SPINNING
                                    - END
                                    - RESERVED
                                    - FIRMWARE
                                    - DRYING
                                    - COOL_DOWN
                                    - RINSE_HOLD
                                    - REFRESHING
                                    - STEAM_SOFTENING
                                    - ERROR
                                    - SMART_GRID_RUN
                                    - ADD_DRAIN
                                    - DETERGENT_AMOUNT
                                    - PREWASH
                                    - SHOES_MODULE
                                    - PROOFING
                                    - DISPENSING
                                    - SOFTENING
                                    - CHECKING_TURBIDITY
                                    - CHANGE_CONDITION
                                    - DISPLAY_LOADSIZE
                                    - FROZEN_PREVENT_INITIAL
                                    - FROZEN_PREVENT_RUNNING
                                    - FROZEN_PREVENT_PAUSE
                                    - SLEEP
                  operation:
                    type: object
                    description: 동작
                    properties:
                      washerOperationMode:
                        type: object
                        description: 세탁 동작
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - w
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              w:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  START | 세탁 시작
                                  STOP | 세탁 정지
                                  POWER_OFF | 전원 OFF
                                  WAKE_UP | Wake up
                                items:
                                  type: string
                                  enum:
                                    - START
                                    - STOP
                                    - POWER_OFF
                                    - WAKE_UP
                  remoteControlEnable:
                    type: object
                    description: 원격제어설정
                    properties:
                      remoteControlEnabled:
                        type: object
                        description: 원격제어설정상태
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - bool
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  TRUE | 원격제어 가능
                                  FALSE | 원격제어 불가능
                                items:
                                  type: boolean
                                  enum:
                                    - true
                                    - false
                  timer:
                    type: object
                    description: 타이머
                    properties:
                      remainHour:
                        description: 남은 시간(시)
                        type: object
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      remainMinute:
                        description: 남은 시간(분)
                        type: object
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      relativeHourToStart:
                        description: 세탁 시작 예약 시간(시)
                        type: object
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                              w:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      relativeMinuteToStart:
                        description: 세탁 시작 예약 시간(분)
                        type: object
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      relativeHourToStop:
                        description: 세탁 종료 예약 시간(시)
                        type: object
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                              w:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      relativeMinuteToStop:
                        description: 세탁 종료 예약 시간(분)
                        type: object
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      totalHour:
                        description: 세탁 전체 시간(시)
                        type: object
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      totalMinute:
                        description: 세탁 전체 시간(분)
                        type: object
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                  detergent:
                    type: object
                    description: 세제 설정
                    properties:
                      detergentSetting:
                        type: string
                        description: |-
                          Value | Description
                          -|-
                          AUTO | 자동 설정 기기
                          NORMAL | 일반 기기
                  location:
                    description: 위치
                    type: object
                    properties:
                      locationName:
                        type: string
                        description: |-
                          Value | Description
                          -|-
                          MAIN | main washer
                          MINI | mini washer
            notification:
              type: object
              properties:
                push:
                  type: array
                  minItems: 1
                  description: |-
                    Push Code | Description
                    -|-
                    WASHING_IS_COMPLETE | 세탁이 완료되었습니다.
                    ERROR_DURING_WASHING | 세탁 중 오류가 발생하였습니다.
                  items:
                    type: string
                    enum:
                      - WASHING_IS_COMPLETE
                      - ERROR_DURING_WASHING
            error:
              type: array
              minProperties: 1
              description: "Push Code | Description\n-|-\nWATER_SUPPLY_ERROR | 급수 에러\nWATER_DRAIN_ERROR | 배수 에러\nOUT_OF_BALANCE_ERROR | 탈수 에러\nLOCKED_MOTOR_ERROR\t | 드라이버 모터 에러\nCHILD_LOCK_ACTIVE_ERROR | childlock 에러\nTIME_TO_RUN_THE_TUB_CLEAN_CYCLE_ERROR | 통세척 에러\nUNBALANCED_LOAD_ERROR | 수평 에러\nDOOR_OPEN_ERROR\t| 문 열림 에러\nUNABLE_TO_LOCK_ERROR | 잠김 불가 에러\nOVERFILL_ERROR | 물 수위 에러\nWATER_LEVEL_SENSOR_ERROR | 물 수위 센서 에러\nPOWER_FAIL_ERROR | 전력 에러\nTEMPERATURE_SENSOR_ERROR | 온도 센서 에러\nTIMEOUT_ERROR | 타임아웃 에러\nPART_MALFUNCTION_ERROR | 기기 부품 에러"
              items:
                type: string
                enum:
                  - WATER_SUPPLY_ERROR
                  - WATER_DRAIN_ERROR
                  - OUT_OF_BALANCE_ERROR
                  - LOCKED_MOTOR_ERROR
                  - CHILD_LOCK_ACTIVE_ERROR
                  - TIME_TO_RUN_THE_TUB_CLEAN_CYCLE_ERROR
                  - UNBALANCED_LOAD_ERROR
                  - DOOR_OPEN_ERROR
                  - UNABLE_TO_LOCK_ERROR
                  - OVERFILL_ERROR
                  - WATER_LEVEL_SENSOR_ERROR
                  - POWER_FAIL_ERROR
                  - TEMPERATURE_SENSOR_ERROR
                  - TIMEOUT_ERROR
                  - PART_MALFUNCTION_ERROR
        washer-object:
          type: array
          title: Washer
          items:
            type: object
            properties:
              runState:
                type: object
                description: 상태
                properties:
                  currentState:
                    type: string
                    description: 현재 상태
                    enum:
                      - POWER_OFF
                      - INITIAL
                      - PAUSE
                      - DETECTING
                      - SOAKING
                      - RUNNING
                      - RINSING
                      - SPINNING
                      - END
                      - RESERVED
                      - FIRMWARE
                      - DRYING
                      - COOL_DOWN
                      - RINSE_HOLD
                      - REFRESHING
                      - STEAM_SOFTENING
                      - ERROR
                      - SMART_GRID_RUN
                      - ADD_DRAIN
                      - DETERGENT_AMOUNT
                      - PREWASH
                      - SHOES_MODULE
                      - PROOFING
                      - DISPENSING
                      - SOFTENING
                      - CHECKING_TURBIDITY
                      - CHANGE_CONDITION
                      - DISPLAY_LOADSIZE
                      - FROZEN_PREVENT_INITIAL
                      - FROZEN_PREVENT_RUNNING
                      - FROZEN_PREVENT_PAUSE
                      - SLEEP
              operation:
                type: object
                description: 동작
                properties:
                  washerOperationMode:
                    type: string
                    description: 세탁 동작
                    enum:
                      - START
                      - STOP
                      - POWER_OFF
                      - WAKE_UP
              remoteControlEnable:
                type: object
                description: 원격제어설정
                properties:
                  remoteControlEnabled:
                    type: bool
                    description: 원격제어 설정상태
                    enum:
                      - true
                      - false
              timer:
                type: object
                description: 타이머
                properties:
                  remainHour:
                    description: 남은 시간(시)
                    type: integer
                  remainMinute:
                    description: 남은 시간(분)
                    type: integer
                  relativeHourToStart:
                    description: 세탁 시작 예약 시간(시)
                    type: integer
                  relativeMinuteToStart:
                    description: 세탁 시작 예약 시간(분)
                    type: integer
                  relativeHourToStop:
                    description: 세탁 종료 예약 시간(시)
                    type: integer
                  relativeMinuteToStop:
                    description: 세탁 종료 예약 시간(분)
                    type: integer
                  totalHour:
                    description: 세탁 전체 시간(시)
                    type: integer
                  totalMinute:
                    description: 세탁 전체 시간(분)
                    type: integer
              detergent:
                type: object
                description: 세제 설정
                properties:
                  detergentSetting:
                    type: string
                    description: 세제 설정 모드
                    enum:
                      - AUTO
                      - NORMAL
              location:
                description: 위치
                type: object
                properties:
                  locationName:
                    type: string
                    description: 위치 이름
                    enum:
                      - MAIN
                      - MINI
        dryer-profile:
          type: object
          title: Washer
          properties:
            property:
              type: object
              properties:
                runState:
                  type: object
                  description: 상태
                  properties:
                    currentState:
                      type: object
                      description: 현재 상태
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_OFF | 제품 OFF
                                INITIAL | 대기중 상태
                                DETECTING | 옷감량 확인
                                PAUSE | 일시정지
                                COOLING | 쿨링
                                RUNNING | 실행중
                                WRINKLE_CARE | 주름 방지 실행 중
                                END | 건조 완료 상태
                                RESERVED | 예약상태
                                ERROR | 에러상태
                                SLEEP | Sleep 상태
                              items:
                                type: string
                                enum:
                                  - POWER_OFF
                                  - INITIAL
                                  - DETECTING
                                  - PAUSE
                                  - COOLING
                                  - RUNNING
                                  - WRINKLE_CARE
                                  - END
                                  - RESERVED
                                  - ERROR
                                  - SLEEP
                operation:
                  type: object
                  description: 건조 동작
                  properties:
                    dryerOperationMode:
                      type: object
                      description: 건조 동작
                      properties:
                        mode:
                          type: array
                          enum:
                            - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                START | 건조 시작
                                STOP | 건조 정지
                                POWER_OFF | 전원 OFF
                                WAKE_UP | Wake up
                              items:
                                type: string
                                enum:
                                  - START
                                  - STOP
                                  - POWER_OFF
                                  - WAKE_UP
                remoteControlEnable:
                  type: object
                  description: 원격 제어 설정
                  properties:
                    remoteControlEnabled:
                      type: object
                      description: 원격 제어 설정 상태
                      properties:
                        mode:
                          type: array
                          enum:
                            - r
                        type:
                          type: string
                          enum:
                            - boolean
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                TRUE | 원격 제어 가능
                                FALSE | 원격 제어 불가능
                              items:
                                type: boolean
                                enum:
                                  - true
                                  - false
                timer:
                  type: object
                  description: 타이머
                  properties:
                    remainHour:
                      description: 남은 시간(시)
                      type: object
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    remainMinute:
                      description: 남은 시간(분)
                      type: object
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    relativeHourToStart:
                      description: 건조 시작 예약 시간(시)
                      type: object
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                            w:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                    relativeMinuteToStart:
                      description: 건조 시작 예약 시간(분)
                      type: object
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    relativeHourToStop:
                      description: 건조 종료 예약 시간(시)
                      type: object
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                            w:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                    relativeMinuteToStop:
                      description: 건조 종료 예약 시간(분)
                      type: object
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    totalHour:
                      description: 건조 전체 시간(시)
                      type: object
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    totalMinute:
                      description: 건조 전체 시간(분)
                      type: object
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
            notification:
              type: object
              properties:
                push:
                  type: array
                  description: |-
                    Push Code | Description
                    -|-
                    DRYING_FAILED | 건조를 실패하였습니다.
                    DRYING_IS_COMPLETE | 건조가 완료되었습니다.
                  items:
                    type: string
                    enum:
                      - DRYING_FAILED
                      - DRYING_IS_COMPLETE
            error:
              type: array
              description: |-
                Push Code | Description
                -|-
                TEMPERATURE_SENSOR_ERROR | 온도 센서 에러
                COMPRESSOR_ERROR | 컴프레서 에러
                DRAINMOTOR_ERROR | 펌프 에러
                EMPTY_WATER_ALERT_ERROR | 풀 비우기 알림 에러
                HIGH_TEMPERATURE_DETECTION_ERROR | 고온 감지 에러
                MOTOR_LOCK_ERROR | 모터 멈춤 에러
                DOOR_SENSOR_ERROR | 문 센서 에러
                DOOR_OPEN_ERROR | 문 열림 에러
                DOOR_LOCK_ERROR | 문 잠김 에러
                NO_FILTER_ERROR | 필터 없음 에러
                FILTER_CLOGGING_ERROR | 필터 막힘 에러
                HIGH_POWER_SUPPLY_ERROR | 비 정상 전압 인가 에러
                POWER_CODE_CONNECTION_ERROR | 전원선 연결 이상 에러
                FAN_MOTOR_ERROR | 팬 모터 에러
              items:
                type: string
                enum:
                  - TEMPERATURE_SENSOR_ERROR
                  - COMPRESSOR_ERROR
                  - DRAINMOTOR_ERROR
                  - EMPTY_WATER_ALERT_ERROR
                  - HIGH_TEMPERATURE_DETECTION_ERROR
                  - MOTOR_LOCK_ERROR
                  - DOOR_SENSOR_ERROR
                  - DOOR_OPEN_ERROR
                  - DOOR_LOCK_ERROR
                  - NO_FILTER_ERROR
                  - FILTER_CLOGGING_ERROR
                  - HIGH_POWER_SUPPLY_ERROR
                  - POWER_CODE_CONNECTION_ERROR
                  - FAN_MOTOR_ERROR
        dryer-object:
          type: object
          title: Washer
          required:
            - property
          properties:
            runState:
              type: object
              description: 상태
              properties:
                currentState:
                  type: string
                  description: 현재 상태
                  enum:
                    - POWER_OFF
                    - INITIAL
                    - DETECTING
                    - PAUSE
                    - COOLING
                    - RUNNING
                    - WRINKLE_CARE
                    - END
                    - RESERVED
                    - ERROR
                    - SLEEP
            operation:
              type: object
              description: 건조 동작
              properties:
                dryerOperationMode:
                  type: string
                  description: 건조 동작
                  enum:
                    - START
                    - STOP
                    - POWER_OFF
                    - WAKE_UP
            remoteControlEnable:
              type: object
              description: 원격 제어 설정
              properties:
                remoteControlEnabled:
                  type: boolean
                  description: 원격 제어 설정 상태
                  enum:
                    - true
                    - false
            timer:
              type: object
              description: 타이머
              properties:
                remainHour:
                  description: 남은 시간(시)
                  type: integer
                remainMinute:
                  description: 남은 시간(분)
                  type: integer
                relativeHourToStart:
                  description: 건조 시작 예약 시간(시)
                  type: integer
                relativeMinuteToStart:
                  description: 건조 시작 예약 시간(분)
                  type: integer
                relativeHourToStop:
                  description: 건조 종료 예약 시간(시)
                  type: integer
                relativeMinuteToStop:
                  description: 건조 종료 예약 시간(분)
                  type: integer
                totalHour:
                  description: 건조 전체 시간(시)
                  type: integer
                totalMinute:
                  description: 건조 전체 시간(분)
                  type: integer
            notification:
              type: string
              description: Push Message
            error:
              type: string
              description: Error Message
        air_conditioner-profile:
          type: object
          title: Air_Conditioner
          properties:
            property:
              type: object
              properties:
                airConJobMode:
                  type: object
                  description: 모드
                  properties:
                    currentJonMode:
                      type: object
                      description: 운전 모드
                      properties:
                        mode:
                          type: array
                          enum:
                            - r
                            - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                COOL | 냉방운전
                                AIR_DRY | 제습운전
                                FAN | 송풍
                                AUTO | 자동운전
                                HEAT | 난방
                                AIR_CLEAN | 공기청정
                                AROMA | 아로마
                                ENERGY_SAVING | EnergySaving
                              items:
                                type: string
                                enum:
                                  - COOL
                                  - AIR_DRY
                                  - FAN
                                  - AUTO
                                  - HEAT
                                  - AIR_CLEAN
                                  - AROMA
                                  - ENERGY_SAVING
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                COOL | 냉방운전
                                AIR_DRY | 제습운전
                                FAN | 송풍
                                AUTO | 자동운전
                                HEAT | 난방
                                AIR_CLEAN | 공기청정
                                AROMA | 아로마
                                ENERGY_SAVING | EnergySaving
                              items:
                                type: string
                                enum:
                                  - COOL
                                  - AIR_DRY
                                  - FAN
                                  - AUTO
                                  - HEAT
                                  - AIR_CLEAN
                                  - AROMA
                                  - ENERGY_SAVING
                operation:
                  type: object
                  description: 동작
                  properties:
                    airConOperationMode:
                      type: object
                      description: 본체 동작
                      properties:
                        mode:
                          type: array
                          enum:
                            - r
                            - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_ON | 에어컨 가동 시작
                                POWER_OFF | 에어컨 가동 재 시작
                              items:
                                type: string
                                enum:
                                  - POWER_ON
                                  - POWER_OFF
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_ON | 에어컨 가동 시작
                                POWER_OFF | 에어컨 가동 재 시작
                              items:
                                type: string
                                enum:
                                  - POWER_ON
                                  - POWER_OFF
                    airCleanOperationMode:
                      type: object
                      description: 공기 청정 단독 동작
                      properties:
                        mode:
                          type: array
                          enum:
                            - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                START | 공기 청정 단독 모드 시작
                                STOP | 공기 청정 단독 모드 정지
                              items:
                                type: string
                                enum:
                                  - START
                                  - STOP
                temperature:
                  type: object
                  description: 온도
                  properties:
                    currentTemperature:
                      type: object
                      description: 현재 온도
                      properties:
                        mode:
                          type: array
                          enum:
                            - r
                        type:
                          type: string
                          enum:
                            - number
                    targetTemperature:
                      type: object
                      description: 희망 온도
                      properties:
                        mode:
                          type: array
                          enum:
                            - r
                            - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                            w:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                    heatTargetTemperature:
                      type: object
                      description: 난방 희망 온도
                      properties:
                        mode:
                          type: array
                          enum:
                            - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            w:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                    coolTargetTemperature:
                      type: object
                      description: 냉방 희망 온도
                      properties:
                        mode:
                          type: array
                          enum:
                            - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            w:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                    autoTargetTemperature:
                      type: object
                      description: 자동 희망 온도
                      properties:
                        mode:
                          type: array
                          enum:
                            - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            w:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                    unit:
                      type: object
                      properties:
                        mode:
                          type: array
                          enum:
                            - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              enum:
                                - C
                              description: |-
                                Value | Description
                                -|-
                                C | 섭씨
                twoSetTemperature:
                  type: object
                  description: 온도
                  properties:
                    currentTemperature:
                      type: object
                      description: 현재 온도
                      properties:
                        mode:
                          type: array
                          enum:
                            - r
                        type:
                          type: string
                          enum:
                            - range
                    heatTargetTemperature:
                      type: object
                      description: 난방 희망 온도
                      properties:
                        mode:
                          type: array
                          enum:
                            - r
                            - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                            w:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                    coolTargetTemperature:
                      type: object
                      description: 냉방 희망 온도
                      properties:
                        mode:
                          type: array
                          enum:
                            - r
                            - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                            w:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                    unit:
                      type: object
                      properties:
                        mode:
                          type: array
                          enum:
                            - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              enum:
                                - C
                              description: |-
                                Value | Description
                                -|-
                                C | 섭씨
                timer:
                  type: object
                  description: 타이머
                  properties:
                    relativeHourToStart:
                      type: object
                      description: 켜짐 예약시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    relativeMinuteToStart:
                      type: object
                      description: 켜짐 예약시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    relativeHourToStop:
                      type: object
                      description: 꺼짐 예약시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    relativeMinuteToStop:
                      type: object
                      description: 꺼짐 예약시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    relativeStartTimer:
                      type: object
                      description: 켜짐 예약시간 설정 여부
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SET | 켜짐 예약 시간 설정
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - SET
                                  - UNSET
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - UNSET
                    relativeStopTimer:
                      type: object
                      description: 꺼짐 예약시간 설정 여부
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SET | 꺼짐 예약 시간 설정
                                UNSET | 꺼짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - SET
                                  - UNSET
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                UNSET | 꺼짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - UNSET
                    absoluteHourToStart:
                      type: object
                      description: 지정한 켜짐 예약시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteMinuteToStart:
                      type: object
                      description: 지정한 켜짐 예약시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteHourToStop:
                      type: object
                      description: 지정한 꺼짐 예약시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteMinuteToStop:
                      type: object
                      description: 지정한 꺼짐 예약시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteStartTimer:
                      type: object
                      description: 지정한 켜짐 예약시간 설정 여부
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SET | 켜짐 예약 시간 설정
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - SET
                                  - UNSET
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - UNSET
                    absoluteStopTimer:
                      type: object
                      description: 지정한 꺼짐 예약시간 설정 여부
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SET | 켜짐 예약 시간 설정
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - SET
                                  - UNSET
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - UNSET
                sleepTimer:
                  type: object
                  description: 슬립타이머
                  properties:
                    relativeHourToStop:
                      type: object
                      description: 꺼짐 예약 시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    relativeMinuteToStop:
                      type: object
                      description: 꺼짐 예약 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    relativeStopTimer:
                      type: object
                      description: 지정한 꺼짐 예약시간 설정 여부
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SET | 켜짐 예약 시간 설정
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - SET
                                  - UNSET
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - UNSET
                powerSave:
                  type: object
                  description: 절전
                  properties:
                    powerSaveEnabled:
                      type: object
                      description: 절전 설정
                      properties:
                        mode:
                          type: array
                          enum:
                            - r
                            - w
                        type:
                          type: string
                          enum:
                            - boolean
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                TRUE | 절전 설정
                                FALSE | 절전 해제
                              items:
                                type: boolean
                                enum:
                                  - true
                                  - false
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                TRUE | 절전 설정
                                FALSE | 절전 해제
                              items:
                                type: boolean
                                enum:
                                  - true
                                  - false
                airFlow:
                  type: object
                  description: 바람 설정
                  properties:
                    windStrength:
                      type: object
                      description: 바람세기
                      properties:
                        mode:
                          type: array
                          enum:
                            - r
                            - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SLOW |  미풍
                                LOW | 약풍
                                MID | 중풍
                                HIGH | 강풍
                                POWER | 파워
                                AUTO | 자동
                              items:
                                type: string
                                enum:
                                  - SLOW
                                  - LOW
                                  - MID
                                  - HIGH
                                  - POWER
                                  - AUTO
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SLOW |  미풍
                                LOW | 약풍
                                MID | 중풍
                                HIGH | 강풍
                                POWER | 파워
                                AUTO | 자동
                              items:
                                type: string
                                enum:
                                  - SLOW
                                  - LOW
                                  - MID
                                  - HIGH
                                  - POWER
                                  - AUTO
                    windStep:
                      type: object
                      description: 바람 단계
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                            w:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                airQualitySensor:
                  type: object
                  description: 공기질
                  properties:
                    PM1:
                      type: object
                      description: PM1.0 극초미세먼지 농도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    PM2:
                      type: object
                      description: PM2.5 초미세먼지 농도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    PM10:
                      type: object
                      description: PM10 미세먼지 농도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    oder:
                      type: object
                      description: 냄새 농도 값(오타)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    odor:
                      type: object
                      description: 냄새 농도 값
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    odorLevel:
                      type: object
                      description: 냄새 농도 레벨 표시
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                INVALID | INVALID
                                GOOD | 좋음
                                NORMAL | 보통
                                BAD | 나쁨
                                VERY_BAD | 매우나쁨
                              enum:
                                - INVALID
                                - GOOD
                                - NORMAL
                                - BAD
                                - VERY_BAD
                    humidity:
                      type: object
                      description: 습도 값
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    totalPollution:
                      type: object
                      description: 종합공기청정도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    totalPollutionLevel:
                      type: object
                      description: 종합공기청정도 레벨표시
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                INVALID | INVALID
                                GOOD | 좋음
                                NORMAL | 보통
                                BAD | 나쁨
                                VERY_BAD | 매우나쁨
                              enum:
                                - INVALID
                                - GOOD
                                - NORMAL
                                - BAD
                                - VERY_BAD
                    monitoringEnabled:
                      type: object
                      description: 센서 모니터링 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                ON_WORKING | 센서 모니터링 - 운전중만
                                ALWAYS | 센서 모니터링 - 항상
                              enum:
                                - ON_WORKING
                                - ALWAYS
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                ON_WORKING | 센서 모니터링 - 운전중만
                                ALWAYS | 센서 모니터링 - 항상
                              enum:
                                - ON_WORKING
                                - ALWAYS
                filterInfo:
                  type: object
                  description: 필터
                  properties:
                    usedTime:
                      type: object
                      description: 필터 누적 사용량
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    filterLifetime:
                      type: object
                      description: 필터 잔여 시간
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
            notification:
              type: object
              properties:
                push:
                  type: array
                  minItems: 1
                  description: |-
                    Push Code | Description
                    -|-
                    WATER_IS_FULL | 물이 가득 찼습니다.
                  items:
                    type: string
                    enum:
                      - WATER_IS_FULL
        air_conditioner-object:
          type: object
          title: Air_Conditioner
          properties:
            airConJobMode:
              type: object
              description: 모드
              properties:
                currentJonMode:
                  type: string
                  description: 운전 모드
                  enum:
                    - COOL
                    - AIR_DRY
                    - FAN
                    - AUTO
                    - HEAT
                    - AIR_CLEAN
                    - AROMA
                    - ENERGY_SAVING
            operation:
              type: object
              description: 동작
              properties:
                airConOperationMode:
                  type: string
                  description: 본체 동작
                  enum:
                    - POWER_ON
                    - POWER_OFF
                airCleanOperationMode:
                  type: string
                  description: 공기 청정 단독 동작
                  enum:
                    - START
                    - STOP
            temperature:
              type: object
              description: 온도
              properties:
                currentTemperature:
                  type: number
                  description: 현재 온도
                targetTemperature:
                  type: range
                  description: 희망 온도
                heatTargetTemperature:
                  type: number
                  description: 난방 희망 온도
                coolTargetTemperature:
                  type: number
                  description: 냉방 희망 온도
                autoTargetTemperature:
                  type: number
                  description: 자동 희망 온도
                unit:
                  type: string
                  description: 온도 단위
            twoSetTemperature:
              type: object
              description: 온도
              properties:
                currentTemperature:
                  type: number
                  description: 현재 온도
                heatTargetTemperature:
                  type: number
                  description: 난방 희망 온도
                coolTargetTemperature:
                  type: number
                  description: 냉방 희망 온도
                unit:
                  type: string
                  description: 온도 단위
            timer:
              type: object
              description: 타이머
              properties:
                relativeHourToStart:
                  type: number
                  description: 켜짐 예약시간(시)
                relativeMinuteToStart:
                  type: number
                  description: 켜짐 예약시간(분)
                relativeHourToStop:
                  type: number
                  description: 꺼짐 예약시간(시)
                relativeMinuteToStop:
                  type: number
                  description: 꺼짐 예약시간(분)
                relativeStartTimer:
                  type: string
                  description: 켜짐 예약시간 설정 여부
                  enum:
                    - SET
                    - UNSET
                relativeStopTimer:
                  type: string
                  description: 꺼짐 예약시간 설정 여부
                  enum:
                    - SET
                    - UNSET
                absoluteHourToStart:
                  type: number
                  description: 지정한 켜짐 예약시간(시)
                absoluteMinuteToStart:
                  type: number
                  description: 지정한 켜짐 예약시간(분)
                absoluteHourToStop:
                  type: number
                  description: 지정한 꺼짐 예약시간(시)
                absoluteMinuteToStop:
                  type: number
                  description: 지정한 꺼짐 예약시간(분)
                absoluteStartTimer:
                  type: string
                  description: 지정한 켜짐 예약시간 설정 여부
                  enum:
                    - SET
                    - UNSET
                absoluteStopTimer:
                  type: string
                  description: 지정한 꺼짐 예약시간 설정 여부
                  enum:
                    - SET
                    - UNSET
            sleepTimer:
              type: object
              description: 슬립타이머
              properties:
                relativeHourToStop:
                  type: number
                  description: 꺼짐 예약 시간(시)
                relativeMinuteToStop:
                  type: number
                  description: 꺼짐 예약 시간(분)
                relativeStopTimer:
                  type: string
                  description: 지정한 꺼짐 예약시간 설정 여부
                  enum:
                    - SET
                    - UNSET
            powerSave:
              type: object
              description: 절전
              properties:
                powerSaveEnabled:
                  type: boolean
                  description: 절전 설정
                  enum:
                    - true
                    - false
            airFlow:
              type: object
              description: 바람 설정
              properties:
                windStrength:
                  type: string
                  description: 바람세기
                  enum:
                    - SLOW
                    - LOW
                    - MID
                    - HIGH
                    - POWER
                    - AUTO
                windStep:
                  type: range
                  description: 바람 단계
            airQualitySensor:
              type: object
              description: 공기질
              properties:
                PM1:
                  type: number
                  description: PM1.0 극초미세먼지 농도
                PM2:
                  type: number
                  description: PM2.5 초미세먼지 농도
                PM10:
                  type: number
                  description: PM10 미세먼지 농도
                oder:
                  type: number
                  description: 냄새 농도 값(오타)
                odor:
                  type: number
                  description: 냄새 농도 값
                odorLevel:
                  type: string
                  description: 냄새 농도 레벨 표시
                  enum:
                    - INVALID
                    - GOOD
                    - NORMAL
                    - BAD
                    - VERY_BAD
                humidity:
                  type: number
                  description: 습도 값
                totalPollution:
                  type: number
                  description: 종합공기청정도
                totalPollutionLevel:
                  type: string
                  description: 종합공기청정도 레벨표시
                  enum:
                    - INVALID
                    - GOOD
                    - NORMAL
                    - BAD
                    - VERY_BAD
                monitoringEnabled:
                  type: string
                  description: 센서 모니터링 설정
                  enum:
                    - ON_WORKING
                    - ALWAYS
            filterInfo:
              type: object
              description: 필터
              properties:
                usedTime:
                  type: number
                  description: 필터 누적 사용량
                filterLifetime:
                  type: number
                  description: 필터 잔여 시간
        air_purifier-profile:
          type: object
          title: Air_Purifier
          properties:
            property:
              type: object
              properties:
                airPurifierJobMode:
                  type: object
                  description: 모드
                  properties:
                    currentJobMode:
                      type: object
                      description: 운전 모드
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                CLEAN | 청정모드
                                SLEEP | 취침모드
                                SILENT | 정음, 저소음 모드
                                HUMIDITY | 가습 청정
                                CIRCULATOR | 순환 청정
                                BABY_CARE | 베이비 케어
                                DUAL_CLEAN | 듀얼 청정
                                AUTO | 오토 모드
                                FAST | 쾌속 모드
                                SMART | 스마트 모드
                              items:
                                type: string
                                enum:
                                  - CLEAN
                                  - SLEEP
                                  - SILENT
                                  - HUMIDITY
                                  - CIRCULATOR
                                  - BABY_CARE
                                  - DUAL_CLEAN
                                  - AUTO
                                  - FAST
                                  - SMART
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                CLEAN | 청정모드
                                SLEEP | 취침모드
                                SILENT | 정음, 저소음 모드
                                HUMIDITY | 가습 청정
                                CIRCULATOR | 순환 청정
                                BABY_CARE | 베이비 케어
                                DUAL_CLEAN | 듀얼 청정
                                AUTO | 오토 모드
                                FAST | 쾌속 모드
                                SMART | 스마트 모드
                              items:
                                type: string
                                enum:
                                  - CLEAN
                                  - SLEEP
                                  - SILENT
                                  - HUMIDITY
                                  - CIRCULATOR
                                  - BABY_CARE
                                  - DUAL_CLEAN
                                  - AUTO
                                  - FAST
                                  - SMART
                    personalizationMode:
                      type: object
                      description: 개인화 모드
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                AUTO_INSIDE | 실내 자동 모드
                                SLEEP | 취침 모드
                                BABY | 베이비 모드
                                SICK_HOUSE | 새집모드
                                AUTO_OUTSIDE | 실내외연동모드
                                PET | 펫모드
                                COOKING | 요리모드
                                SMOKE | 매연모드
                                EXERCISE | 운동모드
                                OTHERS | 이외 모드
                              items:
                                type: string
                                enum:
                                  - AUTO_INSIDE
                                  - SLEEP
                                  - BABY
                                  - SICK_HOUSE
                                  - AUTO_OUTSIDE
                                  - PET
                                  - COOKING
                                  - SMOKE
                                  - EXERCISE
                                  - OTHERS
                operation:
                  type: object
                  description: 동작
                  properties:
                    airPurifierOperationMode:
                      type: object
                      description: 본체 동작
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_ON | 공기청정기 가동 시작
                                POWER_OFF | 공기청정기 가동 재 시작
                              items:
                                type: string
                                enum:
                                  - POWER_ON
                                  - POWER_OFF
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_ON | 공기청정기 가동 시작
                                POWER_OFF | 공기청정기 가동 재 시작
                              items:
                                type: string
                                enum:
                                  - POWER_ON
                                  - POWER_OFF
                timer:
                  type: object
                  description: 타이머
                  properties:
                    absoluteHourToStart:
                      type: object
                      description: 지정한 켜짐 예약시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteMinuteToStart:
                      type: object
                      description: 지정한 켜짐 예약시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteHourToStop:
                      type: object
                      description: 지정한 꺼짐 예약시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteMinuteToStop:
                      type: object
                      description: 지정한 꺼짐 예약시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteStartTimer:
                      type: object
                      description: 지정한 켜짐 예약시간 설정 여부
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SET | 켜짐 예약 시간 설정
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - SET
                                  - UNSET
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - UNSET
                    absoluteStopTimer:
                      type: object
                      description: 지정한 꺼짐 예약시간 설정 여부
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SET | 켜짐 예약 시간 설정
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - SET
                                  - UNSET
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - UNSET
                sleepTimer:
                  type: object
                  description: 슬립타이머
                  properties:
                    relativeHourToStop:
                      type: object
                      description: 꺼짐 예약 시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    relativeMinuteToStop:
                      type: object
                      description: 꺼짐 예약 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    relativeStopTimer:
                      type: object
                      description: 지정한 꺼짐 예약시간 설정 여부
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SET | 켜짐 예약 시간 설정
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - SET
                                  - UNSET
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - UNSET
                airFlow:
                  type: object
                  description: 바람 설정
                  properties:
                    windStrength:
                      type: object
                      description: 바람세기
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SLOW |  미풍
                                LOW | 약풍
                                MID | 중풍
                                HIGH | 강풍
                                POWER | 파워
                                AUTO | 자동
                              items:
                                type: string
                                enum:
                                  - SLOW
                                  - LOW
                                  - MID
                                  - HIGH
                                  - POWER
                                  - AUTO
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SLOW |  미풍
                                LOW | 약풍
                                MID | 중풍
                                HIGH | 강풍
                                POWER | 파워
                                AUTO | 자동
                              items:
                                type: string
                                enum:
                                  - SLOW
                                  - LOW
                                  - MID
                                  - HIGH
                                  - POWER
                                  - AUTO
                airQualitySensor:
                  type: object
                  description: 공기질
                  properties:
                    PM1:
                      type: object
                      description: PM1.0 극초미세먼지 농도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    PM2:
                      type: object
                      description: PM2.5 초미세먼지 농도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    PM10:
                      type: object
                      description: PM10 미세먼지 농도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    oder:
                      type: object
                      description: 냄새 농도 값(오타)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    odor:
                      type: object
                      description: 냄새 농도 값
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    odorLevel:
                      type: object
                      description: 냄새 농도 레벨 표시
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                INVALID | INVALID
                                GOOD | 좋음
                                NORMAL | 보통
                                BAD | 나쁨
                                VERY_BAD | 매우나쁨
                              enum:
                                - INVALID
                                - GOOD
                                - NORMAL
                                - BAD
                                - VERY_BAD
                    humidity:
                      type: object
                      description: 습도 값
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    totalPollution:
                      type: object
                      description: 종합공기청정도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    totalPollutionLevel:
                      type: object
                      description: 종합공기청정도 레벨표시
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                INVALID | INVALID
                                GOOD | 좋음
                                NORMAL | 보통
                                BAD | 나쁨
                                VERY_BAD | 매우나쁨
                              enum:
                                - INVALID
                                - GOOD
                                - NORMAL
                                - BAD
                                - VERY_BAD
                    monitoringEnabled:
                      type: object
                      description: 센서 모니터링 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                ON_WORKING | 센서 모니터링 - 운전중만
                                ALWAYS | 센서 모니터링 - 항상
                              enum:
                                - ON_WORKING
                                - ALWAYS
                filterInfo:
                  type: object
                  description: 필터
                  properties:
                    usedTime:
                      type: object
                      description: 필터 누적 사용량
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    filterLifetime:
                      type: object
                      description: 필터 잔여 시간
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
            notification:
              type: object
              properties:
                push:
                  type: array
                  minItems: 1
                  description: |-
                    Push Code | Description
                    -|-
                    LACK_OF_WATER | 물이 부족합니다.
                    TIME_TO_CLEAN_FILTER | 필터 청소가 필요합니다.
                    POLLUTION_IS_HIGH | 오염도가 높습니다.
                    TIME_TO_CHANGE_FILTER | 필터 교체 시기입니다.
                  items:
                    type: string
                    enum:
                      - LACK_OF_WATER
                      - TIME_TO_CLEAN_FILTER
                      - POLLUTION_IS_HIGH
                      - TIME_TO_CHANGE_FILTER
        air_purifier-object:
          type: object
          title: Air_Purifier
          properties:
            airPurifierJobMode:
              type: object
              description: 모드
              properties:
                currentJobMode:
                  type: string
                  description: 운전 모드
                  enum:
                    - CLEAN
                    - SLEEP
                    - SILENT
                    - HUMIDITY
                    - CIRCULATOR
                    - BABY_CARE
                    - DUAL_CLEAN
                    - AUTO
                    - FAST
                    - SMART
                personalizationMode:
                  type: string
                  description: 개인화 모드
                  enum:
                    - AUTO_INSIDE
                    - SLEEP
                    - BABY
                    - SICK_HOUSE
                    - AUTO_OUTSIDE
                    - PET
                    - COOKING
                    - SMOKE
                    - EXERCISE
                    - OTHERS
            operation:
              type: object
              description: 동작
              properties:
                airPurifierOperationMode:
                  type: string
                  description: 본체 동작
                  enum:
                    - POWER_ON
                    - POWER_OFF
            timer:
              type: object
              description: 타이머
              properties:
                absoluteHourToStart:
                  type: number
                  description: 지정한 켜짐 예약시간(시)
                absoluteMinuteToStart:
                  type: number
                  description: 지정한 켜짐 예약시간(분)
                absoluteHourToStop:
                  type: number
                  description: 지정한 꺼짐 예약시간(시)
                absoluteMinuteToStop:
                  type: number
                  description: 지정한 꺼짐 예약시간(분)
                absoluteStartTimer:
                  type: string
                  description: 지정한 켜짐 예약시간 설정 여부
                  enum:
                    - SET
                    - UNSET
                absoluteStopTimer:
                  type: string
                  description: 지정한 꺼짐 예약시간 설정 여부
                  enum:
                    - SET
                    - UNSET
            sleepTimer:
              type: object
              description: 슬립타이머
              properties:
                relativeHourToStop:
                  type: number
                  description: 꺼짐 예약 시간(시)
                relativeMinuteToStop:
                  type: number
                  description: 꺼짐 예약 시간(분)
                relativeStopTimer:
                  type: string
                  description: 지정한 꺼짐 예약시간 설정 여부
                  enum:
                    - SET
                    - UNSET
            airFlow:
              type: object
              description: 바람 설정
              properties:
                windStrength:
                  type: string
                  description: 바람세기
                  enum:
                    - SLOW
                    - LOW
                    - MID
                    - HIGH
                    - POWER
                    - AUTO
            airQualitySensor:
              type: object
              description: 공기질
              properties:
                PM1:
                  type: number
                  description: PM1.0 극초미세먼지 농도
                PM2:
                  type: number
                  description: PM2.5 초미세먼지 농도
                PM10:
                  type: number
                  description: PM10 미세먼지 농도
                oder:
                  type: number
                  description: 냄새 농도 값(오타)
                odor:
                  type: number
                  description: 냄새 농도 값
                odorLevel:
                  type: string
                  description: 냄새 농도 레벨 표시
                  enum:
                    - INVALID
                    - GOOD
                    - NORMAL
                    - BAD
                    - VERY_BAD
                humidity:
                  type: number
                  description: 습도 값
                totalPollution:
                  type: number
                  description: 종합공기청정도
                totalPollutionLevel:
                  type: string
                  description: 종합공기청정도 레벨표시
                  enum:
                    - INVALID
                    - GOOD
                    - NORMAL
                    - BAD
                    - VERY_BAD
                monitoringEnabled:
                  type: string
                  description: 센서 모니터링 설정
                  enum:
                    - ON_WORKING
                    - ALWAYS
            filterInfo:
              type: object
              description: 필터
              properties:
                usedTime:
                  type: number
                  description: 필터 누적 사용량
                filterLifetime:
                  type: number
                  description: 필터 잔여 시간
            notification:
              type: string
              description: Push Message
        air_purifier_fan-profile:
          type: object
          title: Air_Purifier_Fan
          properties:
            property:
              type: object
              properties:
                airFanJobMode:
                  type: object
                  description: 모드
                  properties:
                    currentJobMode:
                      type: object
                      description: 운전 모드
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SPOT_CLEAN | 집중청정
                                SPACE_CLEAN | 공간청정
                                DIRECT_CLEAN | 다이렉트 청정
                                NATURE_CLEAN | 자연 청정
                                UP_FEATURE | 추가 청정 모드
                                PET_CLEAN | 펫케어 청정
                                SILENT_CLEAN | 조용 청정
                              items:
                                type: string
                                enum:
                                  - SPOT_CLEAN
                                  - SPACE_CLEAN
                                  - DIRECT_CLEAN
                                  - NATURE_CLEAN
                                  - UP_FEATURE
                                  - PET_CLEAN
                                  - SILENT_CLEAN
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SPOT_CLEAN | 집중청정
                                SPACE_CLEAN | 공간청정
                                DIRECT_CLEAN | 다이렉트 청정
                                NATURE_CLEAN | 자연 청정
                                PET_CLEAN | 펫케어 청정
                                SILENT_CLEAN | 조용 청정
                              items:
                                type: string
                                enum:
                                  - SPOT_CLEAN
                                  - SPACE_CLEAN
                                  - DIRECT_CLEAN
                                  - NATURE_CLEAN
                                  - PET_CLEAN
                                  - SILENT_CLEAN
                operation:
                  type: object
                  description: 동작
                  properties:
                    airFanOperationMode:
                      type: object
                      description: 본체 동작
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_ON | 공기청정팬 가동 시작
                                POWER_OFF | 공기청정팬 가동 재 시작
                              items:
                                type: string
                                enum:
                                  - POWER_ON
                                  - POWER_OFF
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_ON | 공기청정팬 가동 시작
                                POWER_OFF | 공기청정팬 가동 재 시작
                              items:
                                type: string
                                enum:
                                  - POWER_ON
                                  - POWER_OFF
                timer:
                  type: object
                  description: 타이머
                  properties:
                    absoluteHourToStart:
                      type: object
                      description: 지정한 켜짐 예약시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteMinuteToStart:
                      type: object
                      description: 지정한 켜짐 예약시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteHourToStop:
                      type: object
                      description: 지정한 꺼짐 예약시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteMinuteToStop:
                      type: object
                      description: 지정한 꺼짐 예약시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteStartTimer:
                      type: object
                      description: 지정한 켜짐 예약시간 설정 여부
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SET | 켜짐 예약 시간 설정
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - SET
                                  - UNSET
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - UNSET
                    absoluteStopTimer:
                      type: object
                      description: 지정한 꺼짐 예약시간 설정 여부
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SET | 켜짐 예약 시간 설정
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - SET
                                  - UNSET
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - UNSET
                sleepTimer:
                  type: object
                  description: 슬립타이머
                  properties:
                    relativeHourToStop:
                      type: object
                      description: 꺼짐 예약 시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    relativeMinuteToStop:
                      type: object
                      description: 꺼짐 예약 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    relativeStopTimer:
                      type: object
                      description: 지정한 꺼짐 예약시간 설정 여부
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SET | 켜짐 예약 시간 설정
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - SET
                                  - UNSET
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - UNSET
                airFlow:
                  type: object
                  description: 바람 설정
                  properties:
                    warmMode:
                      type: object
                      description: 바람 모드
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                WARM_ON | 온풍모드 ON
                                WARM_OFF | 온풍모드 OFF
                              items:
                                type: string
                                enum:
                                  - WARM_ON
                                  - WARM_OFF
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                WARM_ON | 온풍모드 ON
                                WARM_OFF | 온풍모드 OFF
                              items:
                                type: string
                                enum:
                                  - WARM_ON
                                  - WARM_OFF
                    windTemperature:
                      type: object
                      description: 바람 온도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: range
                              enum:
                                - number
                            w:
                              type: range
                              enum:
                                - number
                    windStrength:
                      type: object
                      description: 바람세기
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                AUTO | 지동
                                POWER | 파워
                                WIND_1 | 바람세기1
                                WIND_2 | 바람세기2
                                WIND_3 | 바람세기3
                                WIND_4 | 비림세기4
                                WIND_5 | 바람세기5
                                WIND_6 | 바람세기6
                                WIND_7 | 바람세기7
                                WIND_8 | 바람세기8
                                WIND_9 | 바람세기9
                                WIND_10 | 바람세기10
                              items:
                                type: string
                                enum:
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
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                AUTO | 지동
                                POWER | 파워
                                WIND_1 | 바람세기1
                                WIND_2 | 바람세기2
                                WIND_3 | 바람세기3
                                WIND_4 | 비림세기4
                                WIND_5 | 바람세기5
                                WIND_6 | 바람세기6
                                WIND_7 | 바람세기7
                                WIND_8 | 바람세기8
                                WIND_9 | 바람세기9
                                WIND_10 | 바람세기10
                              items:
                                type: string
                                enum:
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
                      type: object
                      description: 바람 각도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                OFF | 바람각도 OFF
                                ANGLE_45 | 바람각도 45
                                ANGLE_60 | 바람각도 60
                                ANGLE_90 | 바람각도 90
                                ANGLE_140 | 바람각도 140
                              items:
                                type: string
                                enum:
                                  - 'OFF'
                                  - ANGLE_45
                                  - ANGLE_60
                                  - ANGLE_90
                                  - ANGLE_140
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                OFF | 바람각도 OFF
                                ANGLE_45 | 바람각도 45
                                ANGLE_60 | 바람각도 60
                                ANGLE_90 | 바람각도 90
                                ANGLE_140 | 바람각도 140
                              items:
                                type: string
                                enum:
                                  - 'OFF'
                                  - ANGLE_45
                                  - ANGLE_60
                                  - ANGLE_90
                                  - ANGLE_140
                airQualitySensor:
                  type: object
                  description: 공기질
                  properties:
                    PM1:
                      type: object
                      description: PM1.0 극초미세먼지 농도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    PM2:
                      type: object
                      description: PM2.5 초미세먼지 농도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    PM10:
                      type: object
                      description: PM10 미세먼지 농도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    odor:
                      type: object
                      description: 냄새 농도 값
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    odorLevel:
                      type: object
                      description: 냄새 농도 레벨 표시
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                INVALID | INVALID
                                GOOD | 좋음
                                NORMAL | 보통
                                BAD | 나쁨
                                VERY_BAD | 매우나쁨
                              items:
                                type: string
                                enum:
                                  - INVALID
                                  - GOOD
                                  - NORMAL
                                  - BAD
                                  - VERY_BAD
                    humidity:
                      type: object
                      description: 습도 값
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    temperature:
                      type: object
                      description: 온도 값
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    totalPollution:
                      type: object
                      description: 종합공기청정도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    totalPollutionLevel:
                      type: object
                      description: 종합공기청정도 레벨표시
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                INVALID | INVALID
                                GOOD | 좋음
                                NORMAL | 보통
                                BAD | 나쁨
                                VERY_BAD | 매우나쁨
                              items:
                                type: string
                                enum:
                                  - INVALID
                                  - GOOD
                                  - NORMAL
                                  - BAD
                                  - VERY_BAD
                    monitoringEnabled:
                      type: object
                      description: 센서 모니터링 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                ON_WORKING | 센서 모니터링 - 운전중만
                                ALWAYS | 센서 모니터링 - 항상
                              items:
                                type: string
                                enum:
                                  - ON_WORKING
                                  - ALWAYS
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                ON_WORKING | 센서 모니터링 - 운전중만
                                ALWAYS | 센서 모니터링 - 항상
                              items:
                                type: string
                                enum:
                                  - ON_WORKING
                                  - ALWAYS
                display:
                  type: object
                  description: 디스플레이
                  properties:
                    light:
                      type: object
                      description: 화면 밝기
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                OFF | 조명 끔
                                LEVEL_1 | 화면 밝기 1단계
                                LEVEL_2 | 화면 밝기 2단계
                                LEVEL_3 | 화면 밝기 3단계
                              items:
                                type: string
                                enum:
                                  - 'OFF'
                                  - LEVEL_1
                                  - LEVEL2
                                  - LEVEL_3
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                OFF | 조명 끔
                                LEVEL_1 | 화면 밝기 1단계
                                LEVEL_2 | 화면 밝기 2단계
                                LEVEL_3 | 화면 밝기 3단계
                              items:
                                type: string
                                enum:
                                  - 'OFF'
                                  - LEVEL_1
                                  - LEVEL2
                                  - LEVEL_3
                misc:
                  type: object
                  description: 기타
                  properties:
                    uvNano:
                      type: object
                      description: UV 살균
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                ON | UV 살균 켜짐
                                OFF | UV 살균 꺼짐
                              items:
                                type: string
                                enum:
                                  - 'ON'
                                  - 'OFF'
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                ON | UV 살균 켜짐
                                OFF | UV 살균 꺼짐
                              items:
                                type: string
                                enum:
                                  - 'ON'
                                  - 'OFF'
            notification:
              type: object
              properties:
                push:
                  type: array
                  minItems: 1
                  description: |-
                    Push Code | Description
                    -|-
                    TIME_TO_CHANGE_FILTER | 필터 교체 시기 입니다.
                  items:
                    type: string
                    enum:
                      - TIME_TO_CHANGE_FILTER
        air_purifier_fan-object:
          type: object
          title: Air_Purifier_Fan
          properties:
            airFanJobMode:
              type: object
              description: 모드
              properties:
                currentJobMode:
                  type: string
                  description: 운전 모드
                  enum:
                    - SPOT_CLEAN
                    - SPACE_CLEAN
                    - DIRECT_CLEAN
                    - NATURE_CLEAN
                    - PET_CLEAN
                    - SILENT_CLEAN
            operation:
              type: object
              description: 동작
              properties:
                airFanOperationMode:
                  type: object
                  description: 본체 동작
                  enum:
                    - POWER_ON
                    - POWER_OFF
            timer:
              type: object
              description: 타이머
              properties:
                absoluteHourToStart:
                  type: number
                  description: 지정한 켜짐 예약시간(시)
                absoluteMinuteToStart:
                  type: number
                  description: 지정한 켜짐 예약시간(분)
                absoluteHourToStop:
                  type: number
                  description: 지정한 꺼짐 예약시간(시)
                absoluteMinuteToStop:
                  type: number
                  description: 지정한 꺼짐 예약시간(분)
                absoluteStartTimer:
                  type: string
                  description: 지정한 켜짐 예약시간 설정 여부
                  enum:
                    - SET
                    - UNSET
                absoluteStopTimer:
                  type: string
                  description: 지정한 꺼짐 예약시간 설정 여부
                  enum:
                    - SET
                    - UNSET
            sleepTimer:
              type: object
              description: 슬립타이머
              properties:
                relativeHourToStop:
                  type: number
                  description: 꺼짐 예약 시간(시)
                relativeMinuteToStop:
                  type: number
                  description: 꺼짐 예약 시간(분)
                relativeStopTimer:
                  type: string
                  description: 지정한 꺼짐 예약시간 설정 여부
                  enum:
                    - SET
                    - UNSET
            airFlow:
              type: object
              description: 바람 설정
              properties:
                warmMode:
                  type: string
                  description: 바람 모드
                  enum:
                    - WARM_ON
                    - WARM_OFF
                windTemperature:
                  type: number
                  description: 바람 온도
                windStrength:
                  type: string
                  description: 바람세기
                  enum:
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
                  type: string
                  description: 바람 각도
                  enum:
                    - 'OFF'
                    - ANGLE_45
                    - ANGLE_60
                    - ANGLE_90
                    - ANGLE_140
            airQualitySensor:
              type: object
              description: 공기질
              properties:
                PM1:
                  type: number
                  description: PM1.0 극초미세먼지 농도
                PM2:
                  type: number
                  description: PM2.5 초미세먼지 농도
                PM10:
                  type: number
                  description: PM10 미세먼지 농도
                odor:
                  type: number
                  description: 냄새 농도 값
                odorLevel:
                  type: string
                  description: 냄새 농도 레벨 표시
                  enum:
                    - INVALID
                    - GOOD
                    - NORMAL
                    - BAD
                    - VERY_BAD
                humidity:
                  type: number
                  description: 습도 값
                temperature:
                  type: number
                  description: 온도 값
                totalPollution:
                  type: number
                  description: 종합공기청정도
                totalPollutionLevel:
                  type: string
                  description: 종합공기청정도 레벨표시
                  enum:
                    - INVALID
                    - GOOD
                    - NORMAL
                    - BAD
                    - VERY_BAD
                monitoringEnabled:
                  type: string
                  description: 센서 모니터링 설정
                  enum:
                    - ON_WORKING
                    - ALWAYS
            display:
              type: object
              description: 디스플레이
              properties:
                light:
                  type: string
                  description: 화면 밝기
                  enum:
                    - 'OFF'
                    - LEVEL_1
                    - LEVEL2
                    - LEVEL_3
            misc:
              type: object
              description: 기타
              properties:
                uvNano:
                  type: string
                  description: UV 살균
                  enum:
                    - 'ON'
                    - 'OFF'
            notification:
              type: string
              description: Push Message
        dehumidifier-profile:
          type: object
          title: Dehumidifier
          properties:
            property:
              type: object
              properties:
                dehumidifierJobMode:
                  type: object
                  description: 모드
                  properties:
                    currentJobMode:
                      type: object
                      description: 운전 모드
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                RAPID_HUMIDITY | 쾌속제습
                                CLOTHES_DRY | 의류건조
                                AIR_CLEAN | 공기청정
                                QUIET_HUMIDITY | 저음제습
                                SMART_HUMIDITY | 스마트 제습
                                INTENSIVE_DRY | 집중 건조
                              items:
                                type: string
                                enum:
                                  - RAPID_HUMIDITY
                                  - CLOTHES_DRY
                                  - AIR_CLEAN
                                  - QUIET_HUMIDITY
                                  - SMART_HUMIDITY
                                  - INTENSIVE_DRY
                operation:
                  type: object
                  description: 동작
                  properties:
                    dehumidifierOperationMode:
                      type: object
                      description: 본체 동작
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_ON | 제습기 가동 시작
                                POWER_OFF | 제습기 가동 재 시작
                              items:
                                type: string
                                enum:
                                  - POWER_ON
                                  - POWER_OFF
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_ON | 제습기 가동 시작
                                POWER_OFF | 제습기 가동 재 시작
                              items:
                                type: string
                                enum:
                                  - POWER_ON
                                  - POWER_OFF
                timer:
                  type: object
                  description: 타이머
                  properties:
                    absoluteHourToStart:
                      type: object
                      description: 지정한 켜짐 예약시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteMinuteToStart:
                      type: object
                      description: 지정한 켜짐 예약시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteHourToStop:
                      type: object
                      description: 지정한 꺼짐 예약시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteMinuteToStop:
                      type: object
                      description: 지정한 꺼짐 예약시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteStartTimer:
                      type: object
                      description: 지정한 켜짐 예약시간 설정 여부
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SET | 켜짐 예약 시간 설정
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - SET
                                  - UNSET
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - UNSET
                    absoluteStopTimer:
                      type: object
                      description: 지정한 꺼짐 예약시간 설정 여부
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SET | 켜짐 예약 시간 설정
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - SET
                                  - UNSET
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - UNSET
                sleepTimer:
                  type: object
                  description: 슬립타이머
                  properties:
                    relativeHourToStop:
                      type: object
                      description: 꺼짐 예약 시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    relativeMinuteToStop:
                      type: object
                      description: 꺼짐 예약 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    relativeStopTimer:
                      type: object
                      description: 지정한 꺼짐 예약시간 설정 여부
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SET | 켜짐 예약 시간 설정
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - SET
                                  - UNSET
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - UNSET
                humidity:
                  type: object
                  description: 습도
                  properties:
                    currentHumidity:
                      type: string
                      description: 현재 습도(상대 습도)
                      enum:
                        - number
                    targetHumidity:
                      type: string
                      description: 희망 습도
                      enum:
                        - range
                airFlow:
                  type: object
                  description: 바람 설정
                  properties:
                    windStrength:
                      type: object
                      description: 바람세기
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                LOW | 약풍
                                HIGH | 강풍
                              items:
                                type: string
                                enum:
                                  - LOW
                                  - HIGH
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                LOW | 약풍
                                HIGH | 강풍
                              items:
                                type: string
                                enum:
                                  - LOW
                                  - HIGH
                    windStrengthLevel:
                      type: object
                      description: 바람 세기 레벨(2단 이상)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                LOW | 약풍
                                MID | 중풍
                                HIGH | 강풍
                                AUTO | 자동
                              items:
                                type: string
                                enum:
                                  - LOW
                                  - MID
                                  - HIGH
                                  - AUTO
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                LOW | 약풍
                                MID | 중풍
                                HIGH | 강풍
                                AUTO | 자동
                              items:
                                type: string
                                enum:
                                  - LOW
                                  - MID
                                  - HIGH
                                  - AUTO
            notification:
              type: object
              properties:
                push:
                  type: array
                  minItems: 1
                  description: |-
                    Push Code | Description
                    -|-
                    WATER_IS_FULL | 물이 가득 찼습니다.
                  items:
                    type: string
                    enum:
                      - WATER_IS_FULL
        dehumidifier-object:
          type: object
          title: Dehumidifier
          properties:
            dehumidifierJobMode:
              type: object
              description: 모드
              properties:
                currentJobMode:
                  type: string
                  description: 운전 모드
                  enum:
                    - RAPID_HUMIDITY
                    - CLOTHES_DRY
                    - AIR_CLEAN
                    - QUIET_HUMIDITY
                    - SMART_HUMIDITY
                    - INTENSIVE_DRY
            operation:
              type: object
              description: 동작
              properties:
                airFanOperationMode:
                  type: string
                  description: 본체 동작
                  enum:
                    - POWER_ON
                    - POWER_OFF
            timer:
              type: object
              description: 타이머
              properties:
                absoluteHourToStart:
                  type: number
                  description: 지정한 켜짐 예약시간(시)
                absoluteMinuteToStart:
                  type: number
                  description: 지정한 켜짐 예약시간(분)
                absoluteHourToStop:
                  type: number
                  description: 지정한 꺼짐 예약시간(시)
                absoluteMinuteToStop:
                  type: number
                  description: 지정한 꺼짐 예약시간(분)
                absoluteStartTimer:
                  type: object
                  description: 지정한 켜짐 예약시간 설정 여부
                  enum:
                    - SET
                    - UNSET
                absoluteStopTimer:
                  type: object
                  description: 지정한 꺼짐 예약시간 설정 여부
                  enum:
                    - SET
                    - UNSET
            sleepTimer:
              type: object
              description: 슬립타이머
              properties:
                relativeHourToStop:
                  type: number
                  description: 꺼짐 예약 시간(시)
                relativeMinuteToStop:
                  type: number
                  description: 꺼짐 예약 시간(분)
                relativeStopTimer:
                  type: string
                  description: 지정한 꺼짐 예약시간 설정 여부
                  enum:
                    - SET
                    - UNSET
            humidity:
              type: object
              description: 습도
              properties:
                currentHumidity:
                  type: number
                  description: 현재 습도(상대 습도)
                targetHumidity:
                  type: number
                  description: 희망 습도
            airFlow:
              type: object
              description: 바람 설정
              properties:
                windStrength:
                  type: string
                  description: 바람세기
                  enum:
                    - LOW
                    - HIGH
                windStrengthLevel:
                  type: string
                  description: 바람 세기 레벨(2단 이상)
                  enum:
                    - LOW
                    - MID
                    - HIGH
                    - AUTO
            notification:
              type: string
              description: Push Message
        humidifier-profile:
          type: object
          title: Humidifier
          properties:
            property:
              type: object
              properties:
                humidifierJobMode:
                  type: object
                  description: 모드
                  properties:
                    currentJobMode:
                      type: object
                      description: 운전 모드
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                HUMIDIFY | 가습
                                HUMIDIFY_AND_AIR_CLEAN | 가습 청정
                                AIR_CLEAN | 공기청정
                              items:
                                type: string
                                enum:
                                  - HUMIDIFY
                                  - HUMIDIFY_AND_AIR_CLEAN
                                  - AIR_CLEAN
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                HUMIDIFY | 가습
                                HUMIDIFY_AND_AIR_CLEAN | 가습 청정
                                AIR_CLEAN | 공기청정
                              items:
                                type: string
                                enum:
                                  - HUMIDIFY
                                  - HUMIDIFY_AND_AIR_CLEAN
                                  - AIR_CLEAN
                operation:
                  type: object
                  description: 동작
                  properties:
                    humidifierOperationMode:
                      type: object
                      description: 본체 동작
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_ON | 가습기 가동 시작
                                POWER_OFF | 가습기 가동 재 시작
                              items:
                                type: string
                                enum:
                                  - POWER_ON
                                  - POWER_OFF
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_ON | 가습기 가동 시작
                                POWER_OFF | 가습기 가동 재 시작
                              items:
                                type: string
                                enum:
                                  - POWER_ON
                                  - POWER_OFF
                    autoMode:
                      type: object
                      description: 자동 운전 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                AUTO_ON | 자동 운전 설정
                                AUTO_OFF | 자동 운전 해제
                              items:
                                type: string
                                enum:
                                  - AUTO_ON
                                  - AUTO_OFF
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                AUTO_ON | 자동 운전 설정
                                AUTO_OFF | 자동 운전 해제
                              items:
                                type: string
                                enum:
                                  - AUTO_ON
                                  - AUTO_OFF
                    sleepMode:
                      type: object
                      description: 슬립모드 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SLEEP_ON | 슬립 모드 설정 
                                SLEEP_OFF | 슬립 모드 해제
                              items:
                                type: string
                                enum:
                                  - SLEEP_ON
                                  - SLEEP_OFF
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SLEEP_ON | 슬립 모드 설정 
                                SLEEP_OFF | 슬립 모드 해제
                              items:
                                type: string
                                enum:
                                  - SLEEP_ON
                                  - SLEEP_OFF
                    hygieneDryMode:
                      type: object
                      description: 위생 건조 모드
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                OFF | 꺼짐
                                FAST | 쾌속모드
                                SILENT | 조용 모드
                                NORMAL | 섬세 모드
                              items:
                                type: string
                                enum:
                                  - 'OFF'
                                  - FAST
                                  - SILENT
                                  - NORMAL
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                OFF | 꺼짐
                                FAST | 쾌속모드
                                SILENT | 조용 모드
                                NORMAL | 섬세 모드
                              items:
                                type: string
                                enum:
                                  - 'OFF'
                                  - FAST
                                  - SILENT
                                  - NORMAL
                timer:
                  type: object
                  description: 타이머
                  properties:
                    absoluteHourToStart:
                      type: object
                      description: 지정한 켜짐 예약시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteMinuteToStart:
                      type: object
                      description: 지정한 켜짐 예약시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteHourToStop:
                      type: object
                      description: 지정한 꺼짐 예약시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteMinuteToStop:
                      type: object
                      description: 지정한 꺼짐 예약시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteStartTimer:
                      type: object
                      description: 지정한 켜짐 예약시간 설정 여부
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SET | 켜짐 예약 시간 설정
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - SET
                                  - UNSET
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - UNSET
                    absoluteStopTimer:
                      type: object
                      description: 지정한 꺼짐 예약시간 설정 여부
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SET | 꺼짐 예약 시간 설정
                                UNSET | 꺼짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - SET
                                  - UNSET
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - UNSET
                sleepTimer:
                  type: object
                  description: 슬립타이머
                  properties:
                    relativeHourToStop:
                      type: object
                      description: 꺼짐 예약 시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    relativeMinuteToStop:
                      type: object
                      description: 꺼짐 예약 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    relativeStopTimer:
                      type: object
                      description: 꺼짐 예약 시간 설정 여부
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SET | 켜짐 예약 시간 설정
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - SET
                                  - UNSET
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                UNSET | 켜짐 예약 시간 해제
                              items:
                                type: string
                                enum:
                                  - UNSET
                humidity:
                  type: object
                  description: 습도
                  properties:
                    warmMode:
                      type: object
                      description: 가습 모드
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                WARM_ON | 포근가습 ON
                                WARM_OFF | 포근가습 OFF
                              items:
                                type: string
                                enum:
                                  - WARM_ON
                                  - WARM_OFF
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                WARM_ON | 포근가습 ON
                                WARM_OFF | 포근가습 OFF
                              items:
                                type: string
                                enum:
                                  - WARM_ON
                                  - WARM_OFF
                    targetHumidity:
                      type: object
                      description: 희망 습도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: number
                                min:
                                  type: number
                                step:
                                  type: number
                            w:
                              type: object
                              properties:
                                max:
                                  type: number
                                min:
                                  type: number
                                step:
                                  type: number
                airFlow:
                  type: object
                  description: 바람 설정
                  properties:
                    windStrength:
                      type: object
                      description: 바람세기
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                LOW | 약풍
                                MID | 중풍
                                HIGH | 강풍
                                AUTO | 슬립모드 설정 시 자동
                              items:
                                type: string
                                enum:
                                  - LOW
                                  - MID
                                  - HIGH
                                  - AUTO
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                LOW | 약풍
                                MID | 중풍
                                HIGH | 강풍
                                AUTO | 슬립모드 설정 시 자동
                              items:
                                type: string
                                enum:
                                  - LOW
                                  - MID
                                  - HIGH
                                  - AUTO
                airQualitySensor:
                  type: object
                  description: 공기질
                  properties:
                    PM1:
                      type: object
                      description: PM1.0 극초미세먼지 농도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    PM2:
                      type: object
                      description: PM2.5 초미세먼지 농도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    PM10:
                      type: object
                      description: PM10 미세먼지 농도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    humidity:
                      type: object
                      description: 습도 값
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    temperature:
                      type: object
                      description: 온도 값
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    totalPollution:
                      type: object
                      description: 종합공기청정도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    totalPollutionLevel:
                      type: object
                      description: 종합공기청정도 레벨표시
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                INVALID | INVALID
                                GOOD | 좋음
                                NORMAL | 보통
                                BAD | 나쁨
                                VERY_BAD | 매우나쁨
                              items:
                                type: string
                                enum:
                                  - INVALID
                                  - GOOD
                                  - NORMAL
                                  - BAD
                                  - VERY_BAD
                    monitoringEnabled:
                      type: object
                      description: 센서 모니터링 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                ON_WORKING | 센서 모니터링 - 운전중만
                                ALWAYS | 센서 모니터링 - 항상
                              items:
                                type: string
                                enum:
                                  - ON_WORKING
                                  - ALWAYS
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                ON_WORKING | 센서 모니터링 - 운전중만
                                ALWAYS | 센서 모니터링 - 항상
                              items:
                                type: string
                                enum:
                                  - ON_WORKING
                                  - ALWAYS
                display:
                  type: object
                  description: 디스플레이
                  properties:
                    light:
                      type: object
                      description: 화면 밝기
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                OFF | 조명 끔
                                LEVEL_1 | 화면 밝기 1단계
                                LEVEL_2 | 화면 밝기 2단계
                                LEVEL_3 | 화면 밝기 3단계
                              items:
                                type: string
                                enum:
                                  - 'OFF'
                                  - LEVEL_1
                                  - LEVEL2
                                  - LEVEL_3
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                OFF | 조명 끔
                                LEVEL_1 | 화면 밝기 1단계
                                LEVEL_2 | 화면 밝기 2단계
                                LEVEL_3 | 화면 밝기 3단계
                              items:
                                type: string
                                enum:
                                  - 'OFF'
                                  - LEVEL_1
                                  - LEVEL2
                                  - LEVEL_3
                moodLamp:
                  type: object
                  description: 무드등
                  properties:
                    light:
                      type: object
                      description: 화면 밝기
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                ON | 무드등 켜짐
                                OFF | 무드등 꺼짐
                              items:
                                type: string
                                enum:
                                  - 'ON'
                                  - 'OFF'
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                ON | 무드등 켜짐
                                OFF | 무드등 꺼짐
                              items:
                                type: string
                                enum:
                                  - 'ON'
                                  - 'OFF'
            notification:
              type: object
              properties:
                push:
                  type: array
                  description: |-
                    Push Code | Description
                    -|-
                    TIME_TO_CHANGE_FILTER | 필터 교체 시기입니다.
                    LACK_OF_WATER | 물이 부족합니다.
                  items:
                    type: string
                    enum:
                      - TIME_TO_CHANGE_FILTER
                      - LACK_OF_WATER
        humidifier-object:
          type: object
          title: Humidifier
          properties:
            humidifierJobMode:
              type: object
              description: 모드
              properties:
                currentJobMode:
                  type: string
                  description: 운전 모드
                  enum:
                    - HUMIDIFY
                    - HUMIDIFY_AND_AIR_CLEAN
                    - AIR_CLEAN
            operation:
              type: object
              description: 동작
              properties:
                humidifierOperationMode:
                  type: string
                  description: 본체 동작
                  enum:
                    - POWER_ON
                    - POWER_OFF
                autoMode:
                  type: string
                  description: 자동 운전 설정
                  enum:
                    - AUTO_ON
                    - AUTO_OFF
                sleepMode:
                  type: string
                  description: 슬립모드 설정
                  enum:
                    - SLEEP_ON
                    - SLEEP_OFF
                hygieneDryMode:
                  type: string
                  description: 위생 건조 모드
                  enum:
                    - 'OFF'
                    - FAST
                    - SILENT
                    - NORMAL
            timer:
              type: object
              description: 타이머
              properties:
                absoluteHourToStart:
                  type: number
                  description: 지정한 켜짐 예약시간(시)
                absoluteMinuteToStart:
                  type: number
                  description: 지정한 켜짐 예약시간(분)
                absoluteHourToStop:
                  type: number
                  description: 지정한 꺼짐 예약시간(시)
                absoluteMinuteToStop:
                  type: number
                  description: 지정한 꺼짐 예약시간(분)
                absoluteStartTimer:
                  type: string
                  description: 지정한 켜짐 예약시간 설정 여부
                  enum:
                    - SET
                    - UNSET
                absoluteStopTimer:
                  type: string
                  description: 지정한 꺼짐 예약시간 설정 여부
                  enum:
                    - SET
                    - UNSET
            sleepTimer:
              type: object
              description: 슬립타이머
              properties:
                relativeHourToStop:
                  type: number
                  description: 꺼짐 예약 시간(시)
                relativeMinuteToStop:
                  type: number
                  description: 꺼짐 예약 시간(분)
                relativeStopTimer:
                  type: string
                  description: 꺼짐 예약 시간 설정 여부
                  enum:
                    - SET
                    - UNSET
            humidity:
              type: object
              description: 습도
              properties:
                warmMode:
                  type: string
                  description: 가습 모드
                  enum:
                    - WARM_ON
                    - WARM_OFF
                targetHumidity:
                  type: object
                  description: 희망 습도
                  properties:
                    max:
                      type: number
                    min:
                      type: number
                    step:
                      type: number
            airFlow:
              type: object
              description: 바람 설정
              properties:
                windStrength:
                  type: string
                  description: 바람세기
                  enum:
                    - LOW
                    - MID
                    - HIGH
                    - AUTO
            airQualitySensor:
              type: object
              description: 공기질
              properties:
                PM1:
                  type: number
                  description: PM1.0 극초미세먼지 농도
                PM2:
                  type: number
                  description: PM2.5 초미세먼지 농도
                PM10:
                  type: number
                  description: PM10 미세먼지 농도
                humidity:
                  type: number
                  description: 습도 값
                temperature:
                  type: number
                  description: 온도 값
                totalPollution:
                  type: number
                  description: 종합공기청정도
                totalPollutionLevel:
                  type: string
                  description: 종합공기청정도 레벨표시
                  enum:
                    - INVALID
                    - GOOD
                    - NORMAL
                    - BAD
                    - VERY_BAD
                monitoringEnabled:
                  type: string
                  description: 센서 모니터링 설정
                  enum:
                    - ON_WORKING
                    - ALWAYS
            display:
              type: object
              description: 디스플레이
              properties:
                light:
                  type: string
                  description: 화면 밝기
                  enum:
                    - 'OFF'
                    - LEVEL_1
                    - LEVEL2
                    - LEVEL_3
            moodLamp:
              type: object
              description: 무드등
              properties:
                light:
                  type: string
                  description: 화면 밝기
                  enum:
                    - 'ON'
                    - 'OFF'
            notification:
              type: string
              description: Push Message
              enum:
                - TIME_TO_CHANGE_FILTER
                - LACK_OF_WATER
        robot_cleaner-profile:
          type: object
          title: Robot_Cleaner
          properties:
            property:
              type: object
              properties:
                runState:
                  type: object
                  description: 상태
                  properties:
                    currentState:
                      type: object
                      description: 현재 상태
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                CHARGING | 충전중
                                DIAGNOSIS | 진단 중
                                HOMING | 충전대로 이동 중 - r9
                                INITIALIZING | 초기화
                                MACROSECTOR | 리모컨 제어 중
                                MONITORING_DETECTING | 홈가드 수행중
                                MONITORING_MOVING | 홈가드 타겟으로 지정한 목표로 이동중인 상태
                                MONITORING_POSITIONING | 홈가드 위치 지정 이동중 상태
                                PAUSE | 일시정지
                                RESERVATION | 리모컨 예약 중
                                SETDATE | 리모컨 시간 설정 중
                                SLEEP | 절전 모드 중
                                STANDBY | 대기 중 상태
                                WORKING | 청소중
                                ERROR | 에러 상태
                              items:
                                type: string
                                enum:
                                  - CHARGING
                                  - DIAGNOSIS
                                  - HOMING
                                  - INITIALIZING
                                  - MACROSECTOR
                                  - MONITORING_DETECTING
                                  - MONITORING_MOVING
                                  - MONITORING_POSITIONING
                                  - PAUSE
                                  - RESERVATION
                                  - SETDATE
                                  - SLEEP
                                  - STANDBY
                                  - WORKING
                                  - ERROR
                robotCleanerJobMode:
                  type: object
                  description: 모드
                  properties:
                    currentJobMode:
                      type: object
                      description: 청소 모드
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                ZIGZAG | 지그재그 청소
                                SECTOR_BASE | 꼼꼼 청소
                                SPOT | 집중 청소
                                EDGE | 엣지 청소(R9:꼼꼼청소)
                                MACRO | 매크로 모드(리모컨으로 영역 지정하여 청소)
                                SELECT | 지정영역 청소
                              items:
                                type: string
                                enum:
                                  - ZIGZAG
                                  - SECTOR_BASE
                                  - SPOT
                                  - EDGE
                                  - MACRO
                                  - SELECT
                operation:
                  type: object
                  description: 동작
                  properties:
                    cleanOperationMode:
                      type: object
                      description: 청소 동작
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                START | 청소 시작
                                RESUME | 청소 재시작
                                PAUSE | 청소 일시 정지
                                HOMING | 충전대로 이동
                                WAKE_UP | wake up (절전모드 해제)
                              items:
                                type: string
                                enum:
                                  - START
                                  - RESUME
                                  - PAUSE
                                  - HOMING
                                  - WAKE_UP
                battery:
                  type: object
                  description: 배터리
                  properties:
                    level:
                      type: object
                      description: 배터리 레벨
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              description: |-
                                Value | Description
                                -|-
                                MOVELESS | 적음(움직이지 못함)
                                DOCK_LEVEL | 적음(Docking까지 가능)
                                LOW | 적음
                                MID | 보통
                                HIGHT | 많음
                                FULL | 가득 참
                                OVER_CHARGE | Over charge 상태
                              items:
                                type: string
                                enum:
                                  - MOVELESS
                                  - DOCK_LEVEL
                                  - LOW
                                  - MID
                                  - HIGHT
                                  - FULL
                                  - OVER_CHARGE
                    percent:
                      type: object
                      description: 베터리 퍼센트
                      properties:
                        mode:
                          type: array
                          enum:
                            - r
                        type:
                          type: string
                          enum:
                            - number
                timer:
                  type: object
                  description: 타이머
                  properties:
                    absoluteHourToStart:
                      type: object
                      description: 청소 예약 시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    absoluteMinuteToStart:
                      type: object
                      description: 청소 예약 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    runningHour:
                      type: object
                      description: 진행 시간(시)
                      properties:
                        mode:
                          type: array
                          enum:
                            - r
                        type:
                          type: string
                          enum:
                            - number
                    runningMinute:
                      type: object
                      description: 진행 시간(분)
                      properties:
                        mode:
                          type: array
                          enum:
                            - r
                        type:
                          type: string
                          enum:
                            - number
            notification:
              type: object
              properties:
                push:
                  type: array
                  minItems: 1
                  description: |-
                    Push Code | Description
                    -|-
                    CLEANING_IS_COMPLETED | 청소가 완료되었습니다.
                    CLEANING_IS_FAILED | 청소를 실패하였습니다.
                    MOTION_IS_DETECTED | 홈가드 중에 움직임이 감지되어 사진을 보냈습니다.
                    NEED_TO_CHECK_LOCATION | 위치 확인이 필요합니다.
                    HOMEGUARD_IS_STOPPED | 홈가드가 중지되었습니다.
                    SCHEDULED_CLEANING_STARTS | 예약청소가 시작됩니다.
                  items:
                    type: string
                    enum:
                      - CLEANING_IS_COMPLETED
                      - CLEANING_IS_FAILED
                      - MOTION_IS_DETECTED
                      - NEED_TO_CHECK_LOCATION
                      - HOMEGUARD_IS_STOPPED
                      - SCHEDULED_CLEANING_STARTS
            push:
              type: array
              minItems: 1
              description: |-
                Push Code | Description
                -|-
                CLEANING_IS_COMPLETED | 청소가 완료되었습니다.
                CLEANING_IS_FAILED | 청소를 실패하였습니다.
                MOTION_IS_DETECTED | 홈가드 중에 움직임이 감지되어 사진을 보냈습니다.
                NEED_TO_CHECK_LOCATION | 위치 확인이 필요합니다.
                HOMEGUARD_IS_STOPPED | 홈가드가 중지되었습니다.
                SCHEDULED_CLEANING_STARTS | 예약청소가 시작됩니다.
              items:
                type: string
                enum:
                  - CLEANING_IS_COMPLETED
                  - CLEANING_IS_FAILED
                  - MOTION_IS_DETECTED
                  - NEED_TO_CHECK_LOCATION
                  - HOMEGUARD_IS_STOPPED
                  - SCHEDULED_CLEANING_STARTS
            error:
              type: array
              description: |-
                Value | Description
                -|-
                BRUSH_ERROR | 브러시 에러
                NO_BATTERY_ERROR | 베터리 없음
                DUST_FULL_ERROR | 먼지통 다 찼음
                NO_DUST_BIN_ERROR | 먼지통 없음
                MOVE_ERROR | 이동 못함 에러
                BLOCK_ERROR | 이동 막힘 에러
                RIGHT_WHEEL_ERROR | 오른쪽 바퀴 에러
                LEFT_WHEEL_ERROR | 왼쪽 바퀴 에러
                CLIFF_ERROR | 경사면 이동 못함
                SUCTION_BLOCKED_ERROR | 흡입 에러
                MOP_ERROR | 걸레 상태 에러
                UNKNOWN_ERROR | 정의되지 않은 에러
              items:
                type: string
                enum:
                  - BRUSH_ERROR
                  - NO_BATTERY_ERROR
                  - DUST_FULL_ERROR
                  - NO_DUST_BIN_ERROR
                  - MOVE_ERROR
                  - BLOCK_ERROR
                  - RIGHT_WHEEL_ERROR
                  - LEFT_WHEEL_ERROR
                  - CLIFF_ERROR
                  - SUCTION_BLOCKED_ERROR
                  - MOP_ERROR
                  - UNKNOWN_ERROR
        robot_cleaner-object:
          type: object
          title: Robot_Cleaner
          properties:
            runState:
              type: object
              description: 상태
              properties:
                currentState:
                  type: string
                  description: 현재 상태
                  enum:
                    - CHARGING
                    - DIAGNOSIS
                    - HOMING
                    - INITIALIZING
                    - MACROSECTOR
                    - MONITORING_DETECTING
                    - MONITORING_MOVING
                    - MONITORING_POSITIONING
                    - PAUSE
                    - RESERVATION
                    - SETDATE
                    - SLEEP
                    - STANDBY
                    - WORKING
                    - ERROR
            robotCleanerJobMode:
              type: object
              description: 모드
              properties:
                currentJobMode:
                  type: string
                  description: 청소 모드
                  enum:
                    - ZIGZAG
                    - SECTOR_BASE
                    - SPOT
                    - EDGE
                    - MACRO
                    - SELECT
            operation:
              type: object
              description: 동작
              properties:
                cleanOperationMode:
                  type: string
                  description: 청소 동작
                  enum:
                    - START
                    - RESUME
                    - PAUSE
                    - HOMING
                    - WAKE_UP
            battery:
              type: object
              description: 배터리
              properties:
                level:
                  type: string
                  description: 배터리 레벨
                  enum:
                    - MOVELESS
                    - DOCK_LEVEL
                    - LOW
                    - MID
                    - HIGHT
                    - FULL
                    - OVER_CHARGE
                percent:
                  type: object
                  description: 베터리 퍼센트
                  properties:
                    mode:
                      type: array
                      enum:
                        - r
                    type:
                      type: string
                      enum:
                        - number
            timer:
              type: object
              description: 타이머
              properties:
                absoluteHourToStart:
                  type: number
                  description: 청소 예약 시간(시)
                absoluteMinuteToStart:
                  type: number
                  description: 청소 예약 시간(분)
                runningHour:
                  type: number
                  description: 진행 시간(시)
                runningMinute:
                  type: number
                  description: 진행 시간(분)
            notification:
              type: string
              description: push message
              enum:
                - CLEANING_IS_COMPLETED
                - CLEANING_IS_FAILED
                - MOTION_IS_DETECTED
                - NEED_TO_CHECK_LOCATION
                - HOMEGUARD_IS_STOPPED
                - SCHEDULED_CLEANING_STARTS
            push:
              type: string
              description: push message
              enum:
                - CLEANING_IS_COMPLETED
                - CLEANING_IS_FAILED
                - MOTION_IS_DETECTED
                - NEED_TO_CHECK_LOCATION
                - HOMEGUARD_IS_STOPPED
                - SCHEDULED_CLEANING_STARTS
            error:
              type: string
              description: error message
              enum:
                - BRUSH_ERROR
                - NO_BATTERY_ERROR
                - DUST_FULL_ERROR
                - NO_DUST_BIN_ERROR
                - MOVE_ERROR
                - BLOCK_ERROR
                - RIGHT_WHEEL_ERROR
                - LEFT_WHEEL_ERROR
                - CLIFF_ERROR
                - SUCTION_BLOCKED_ERROR
                - MOP_ERROR
                - UNKNOWN_ERROR
        oven-profile:
          type: object
          title: Oven
          properties:
            property:
              type: array
              items:
                type: object
                properties:
                  runState:
                    type: object
                    description: 상태
                    properties:
                      currentState:
                        type: object
                        description: 제품 상태
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  COOKING_IN_PROGRESS | 조리중
                                  PAUSE | 일시 정지
                                  DONE | 조리 완료
                                  COOLING | 냉각중
                                  PREHEATING | 예열중
                                  PREHEATING_IS_DONE | 예열 완료
                                  CLEANING | 청소 중
                                  INITIAL | 대기단계
                                  PREFERENCE | 설정중
                                  ERROR | 에러
                                  CLEANING_IS_DONE | 청소 완료
                                items:
                                  type: string
                                  enum:
                                    - COOKING_IN_PROGRESS
                                    - PAUSE
                                    - DONE
                                    - COOLING
                                    - PREHEATING
                                    - PREHEATING_IS_DONE
                                    - CLEANING
                                    - INITIAL
                                    - PREFERENCE
                                    - ERROR
                                    - CLEANING_IS_DONE
                  operation:
                    type: object
                    description: 동작
                    properties:
                      ovenOperationMode:
                        type: object
                        description: 오븐 동작
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - w
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              w:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  PREHEATING | 예열 시작
                                  START | 요리 시작
                                  STOP | 요리 종료
                                items:
                                  type: string
                                  enum:
                                    - PREHEATING
                                    - START
                                    - STOP
                  cook:
                    type: object
                    description: 모드
                    properties:
                      cookMode:
                        type: object
                        description: 요리 모드
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  BAKE | 베이크
                                  CONVECTION_BAKE | 컨벡션 베이크
                                  CONVECTION_ROAST | 켄벡션 로스트
                                  ROAST | 로스트
                                  CRISP_CONVECTION | 크립스 켄벡션
                                  OTHERS | 그 외 모드
                                items:
                                  type: array
                                  enum:
                                    - BAKE
                                    - CONVECTION_BAKE
                                    - CONVECTION_ROAST
                                    - ROAST
                                    - CRISP_CONVECTION
                                    - OTHERS
                              w:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  BAKE | 베이크
                                  CONVECTION_BAKE | 컨벡션 베이크
                                  CONVECTION_ROAST | 켄벡션 로스트
                                  ROAST | 로스트
                                  CRISP_CONVECTION | 크립스 켄벡션
                                  OTHERS | 그 외 모드
                                items:
                                  type: array
                                  enum:
                                    - BAKE
                                    - CONVECTION_BAKE
                                    - CONVECTION_ROAST
                                    - ROAST
                                    - CRISP_CONVECTION
                                    - OTHERS
                  location:
                    type: object
                    description: 위치
                    properties:
                      locationName:
                        type: string
                        enum:
                          - OVEN
                          - UPPER
                          - LOWER
                        description: |-
                          Value | Description
                          -|-
                          OVEN | 오븐
                          UPPER | Upper 위치
                          LOWER | Lower 위치
                  remoteControlEnable:
                    type: object
                    description: 원격제어 설정
                    properties:
                      remoteControlEnabled:
                        type: object
                        description: 원격 제어 설정 상태
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - boolean
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  TRUE | 원격 제어 가능
                                  FALSE | 원격 제어 불가능
                                items:
                                  type: string
                                  enum:
                                    - true
                                    - false
                  temperature:
                    type: array
                    description: 온도
                    items:
                      type: object
                      properties:
                        targetTemperature:
                          type: object
                          description: 희망 온도
                          properties:
                            mode:
                              type: array
                              items:
                                type: string
                                enum:
                                  - r
                            type:
                              type: string
                              enum:
                                - number
                        unit:
                          type: string
                          description: 단위
                          enum:
                            - C
                            - F
                  timer:
                    type: object
                    description: 타이머
                    properties:
                      remainHour:
                        type: object
                        description: 남은 시간(시)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - number
                      remainMinute:
                        type: object
                        description: 남은 시간(분)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - number
                      remainSecond:
                        type: object
                        description: 남은 시간(초)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - number
                      targetHour:
                        type: object
                        description: 설정 시간(시)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - number
                      targetMinute:
                        type: object
                        description: 설정 시간(분)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - number
                      targeSecond:
                        type: object
                        description: 설정 시간(초)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - number
                      timeHour:
                        type: object
                        description: 알람 시간(시)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - w
                          type:
                            type: string
                            enum:
                              - number
                      timeMinute:
                        type: object
                        description: 알람 시간(분)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - w
                          type:
                            type: string
                            enum:
                              - number
                      timeSecond:
                        type: object
                        description: 알람 시간(초)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - w
                          type:
                            type: string
                            enum:
                              - number
            extensionProperty:
              type: object
              properties:
                info:
                  type: object
                  description: 정보
                  properties:
                    type:
                      type: string
                      description: |-
                        Value | Description
                        -|-
                        SINGLE | 싱글
                        COMBI | 콤비
                        DOUBLE_UL | 더블(위아레, Upper, Lower)
                        DOUBLE_LR | 더블(좌우, Left, Right)
                      enum:
                        - SINGLE
                        - COMBI
                        - DOUBLE_UL
                        - DOUBLE_LR
            notification:
              type: object
              properties:
                push:
                  type: array
                  minItems: 1
                  description: |-
                    Push Code | Description
                    -|-
                    PREHEATING_IS_COMPLETE | 예열이 완료되었습니다.
                    COOKING_IS_COMPLETE | 요리가 완료되었습니다.
                    TIME_TO_CLEAN | 청소가 필요합니다.
                    ERROR_HAS_OCCURRED | 오류가 발생하였습니다.
                  items:
                    type: string
                    enum:
                      - PREHEATING_IS_COMPLETE
                      - COOKING_IS_COMPLETE
                      - TIME_TO_CLEAN
                      - ERROR_HAS_OCCURRED
        oven-object:
          type: array
          title: Oven
          items:
            type: object
            properties:
              runState:
                type: object
                description: 상태
                properties:
                  currentState:
                    type: string
                    description: 제품 상태
                    enum:
                      - COOKING_IN_PROGRESS
                      - PAUSE
                      - DONE
                      - COOLING
                      - PREHEATING
                      - PREHEATING_IS_DONE
                      - CLEANING
                      - INITIAL
                      - PREFERENCE
                      - ERROR
                      - CLEANING_IS_DONE
              operation:
                type: object
                description: 동작
                properties:
                  ovenOperationMode:
                    type: string
                    description: 오븐 동작
                    enum:
                      - PREHEATING
                      - START
                      - STOP
              cook:
                type: object
                description: 모드
                properties:
                  cookMode:
                    type: string
                    description: 요리 모드
                    enum:
                      - BAKE
                      - CONVECTION_BAKE
                      - CONVECTION_ROAST
                      - ROAST
                      - CRISP_CONVECTION
                      - OTHERS
              location:
                type: object
                description: 위치
                properties:
                  locationName:
                    type: string
                    enum:
                      - OVEN
                      - UPPER
                      - LOWER
                    description: 위치 이름
              remoteControlEnable:
                type: object
                description: 원격제어 설정
                properties:
                  remoteControlEnabled:
                    type: boolean
                    description: 원격 제어 설정 상태
                    enum:
                      - true
                      - false
              temperature:
                type: object
                description: 온도
                properties:
                  targetTemperature:
                    type: number
                    description: 희망 온도
                  unit:
                    type: string
                    description: 단위
                    enum:
                      - C
                      - F
              timer:
                type: object
                description: 타이머
                properties:
                  remainHour:
                    type: integer
                    description: 남은 시간(시)
                  remainMinute:
                    type: integer
                    description: 남은 시간(분)
                  remainSecond:
                    type: integer
                    description: 남은 시간(초)
                  targetHour:
                    type: integer
                    description: 설정 시간(시)
                  targetMinute:
                    type: integer
                    description: 설정 시간(분)
                  targeSecond:
                    type: integer
                    description: 설정 시간(초)
                  timeHour:
                    type: integer
                    description: 알람 시간(시)
                  timeMinute:
                    type: integer
                    description: 알람 시간(분)
                  timeSecond:
                    type: integer
                    description: 알람 시간(초)
        dish_washer-profile:
          type: object
          title: Dish_Washer
          properties:
            property:
              type: object
              properties:
                runState:
                  type: object
                  description: 상태
                  properties:
                    currentState:
                      type: object
                      description: 제품 상태
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_OFF | 제품 OFF
                                INITIAL | 대기중 상태
                                RUNNING | 행정중
                                PAUSE | 일시정지
                                END | 완료 상태
                                POWER_FAIL | power fail
                                RESERVED | 예약상태
                                RINSING | 헹궁중
                                NIGHT_DRY | 보관중
                                CANCEL | 취소
                                ERROR | 에러 상태
                              items:
                                type: string
                                enum:
                                  - POWER_OFF | 제품 OFF
                                  - INITIAL | 대기중 상태
                                  - PAUSE | 일시정지
                                  - END | 완료 상태
                                  - POWER_FAIL | power fail
                                  - RESERVED | 예약상태
                                  - RINSING | 헹궁중
                                  - NIGHT_DRY | 보관중
                                  - CANCEL | 취소
                                  - ERROR | 에러 상태
                dishWashingStatus:
                  type: object
                  description: 설정 상태
                  properties:
                    rinseRefill:
                      type: object
                      description: 린스 리필
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - boolean
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                TRUE | 린스 리필 필요
                                FALSE | 린스 리필 필요 없음
                              items:
                                type: boolean
                                enum:
                                  - true
                                  - false
                preference:
                  type: object
                  description: 선호 설정
                  properties:
                    rinseLevel:
                      type: object
                      description: 선호하는 린스 양 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                RINSELEVEL_0 | rinse 양 0 (0)
                                RINSELEVEL_1 | rinse 양 1 (1)
                                RINSELEVEL_2 | rinse 양 2 (2)
                                RINSELEVEL_3 | rinse 양 3 (3)
                                RINSELEVEL_4 | rinse 양 4 (4)
                              items:
                                type: string
                                enum:
                                  - RINSELEVEL_0
                                  - RINSELEVEL_1
                                  - RINSELEVEL_2
                                  - RINSELEVEL_3
                                  - RINSELEVEL_4
                    softeningLevel:
                      type: object
                      description: 선호하는 유연제 양 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SOFTENINGLEVEL_0 | 유연제 양 0 (0)
                                SOFTENINGLEVEL_1 | 유연제 양 1 (1)
                                SOFTENINGLEVEL_2 | 유연제 양 2 (2)
                                SOFTENINGLEVEL_3 | 유연제 양 3 (3)
                                SOFTENINGLEVEL_4 | 유연제 양 4 (4)
                              items:
                                type: string
                                enum:
                                  - SOFTENINGLEVEL_0
                                  - SOFTENINGLEVEL_1
                                  - SOFTENINGLEVEL_2
                                  - SOFTENINGLEVEL_3
                                  - SOFTENINGLEVEL_4
                    mCReminder:
                      type: object
                      description: 내부 청소 알림 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                MCREMINDER_OFF | 내부 청소 알림 off (0)
                                MCREMINDER_ON | 내부 청소 알림 on (1)
                              items:
                                type: string
                                enum:
                                  - MCREMINDER_OFF
                                  - MCREMINDER_ON
                    signalLevel:
                      type: object
                      description: 부저음 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                SIGNALLEVEL_OFF | 부저음 Off (0)
                                SIGNALLEVEL_ON | 부저음 on (1)
                              items:
                                type: string
                                enum:
                                  - SIGNALLEVEL_OFF
                                  - SIGNALLEVEL_ON
                    cleanLReminder:
                      type: object
                      description: 세척 완료 표시창 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                CLEANLREMINDER_OFF | 세척 완료 표시창 off (0)
                                CLEANLREMINDER_ON | 세척 완료 표시창 on (1)
                              items:
                                type: string
                                enum:
                                  - CLEANLREMINDER_OFF
                                  - CLEANLREMINDER_ON
                doorStatus:
                  type: object
                  description: 도어 상태
                  properties:
                    doorState:
                      type: object
                      description: 도어 열림 상태
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                CLOSE | 문 닫힘
                                OPEN | 문 열림
                              items:
                                type: string
                                enum:
                                  - CLOSE
                                  - OPEN
                operation:
                  type: object
                  description: 동작
                  properties:
                    dishWasherOperationMode:
                      type: object
                      description: 세탁 동작
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                START | 세척 시작
                                STOP | 세척 정지
                                POWER_OFF | 전원 OFF
                                CANCEL | 취소 
                              items:
                                type: string
                                enum:
                                  - START
                                  - STOP
                                  - POWER_OFF
                                  - CANCEL
                remoteControlEnable:
                  type: object
                  description: 원격제어 설정
                  properties:
                    remoteControlEnabled:
                      type: object
                      description: 원격 제어 설정 상태
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - boolean
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                TRUE | 원격 제어 가능
                                FALSE | 원격 제어 불가능
                              items:
                                type: string
                                enum:
                                  - true
                                  - false
                timer:
                  type: object
                  description: 타이머
                  properties:
                    remainHour:
                      type: object
                      description: 남은 시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    remainMinute:
                      type: object
                      description: 남은 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    relativeHourToStart:
                      type: object
                      description: 예약 시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    relativeMinuteToStart:
                      type: object
                      description: 예약 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    totalHour:
                      type: object
                      description: 전체 시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    totalMinute:
                      type: object
                      description: 전체 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                dishWashingCourse:
                  type: object
                  description: 코스 정보
                  properties:
                    currentDishWashingCourse:
                      type: object
                      description: 현재 코스
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                AUTO | 자동
                                HEAVY | heavy
                                DELICATE | delicate
                                TURBO | turbo
                                NORMAL | normal
                                RINSE | rinse
                                REFRESH | refresh
                                EXPRESS | express
                                MACHINE_CLEAN | machine clean
                                SHORT_MODE | short mode
                                DOWNLOAD_CYCLE | download cycle
                                QUICK | quick
                                STEAM | steam
                                SPRAY | spray
                                ECO | eco
                              items:
                                type: array
                                enum:
                                  - AUTO
                                  - HEAVY
                                  - DELICATE
                                  - TURBO
                                  - NORMAL
                                  - RINSE
                                  - REFRESH
                                  - EXPRESS
                                  - MACHINE_CLEAN
                                  - SHORT_MODE
                                  - DOWNLOAD_CYCLE
                                  - QUICK
                                  - STEAM
                                  - SPRAY
                                  - ECO
            notification:
              type: object
              properties:
                push:
                  type: array
                  minItems: 1
                  description: |-
                    Push Code | Description
                    -|-
                    CLEANING_IS_COMPLETE | 세척이 완료되었습니다.
                    ERROR_DURING_CLEANING | 오류로 세척이 정지되었습니다.
                    WATER_LEAK_HAS_OCCURRED | 누수가 발생했습니다.
                    RINSE_IS_NOT_ENOUGH | 린스가 부족합니다.
                    SALT_REFILL_IS_NEEDED | 소금 추가가 필요합니다.
                  items:
                    type: string
                    enum:
                      - CLEANING_IS_COMPLETE
                      - ERROR_DURING_CLEANING
                      - WATER_LEAK_HAS_OCCURRED
                      - RINSE_IS_NOT_ENOUGH
                      - SALT_REFILL_IS_NEEDED
            error:
              type: array
              description: |-
                Push Code | Description
                -|-
                WATER_LEAKAGE_ERROR | 누수 에러
                BUBBLE_ERROR | 버블 에러
                HEATER_CIRCUIT_ERROR | 히터 에러
                WATER_SUPPLY_ERROR | 급수 에러
                MOTOR_ERROR | 모터 에러
                WATER_DRAIN_ERROR | 배수 에러
                TEMPERATURE_SENSOR_ERROR | 온도 센서 에러
              items:
                type: string
                enum:
                  - WATER_LEAKAGE_ERROR
                  - BUBBLE_ERROR
                  - HEATER_CIRCUIT_ERROR
                  - WATER_SUPPLY_ERROR
                  - MOTOR_ERROR
                  - WATER_DRAIN_ERROR
                  - TEMPERATURE_SENSOR_ERROR
        dish_washer-object:
          type: object
          title: Dish_Washer
          properties:
            runState:
              type: object
              description: 상태
              properties:
                currentState:
                  type: string
                  description: 제품 상태
                  enum:
                    - POWER_OFF | 제품 OFF
                    - INITIAL | 대기중 상태
                    - PAUSE | 일시정지
                    - END | 완료 상태
                    - POWER_FAIL | power fail
                    - RESERVED | 예약상태
                    - RINSING | 헹궁중
                    - NIGHT_DRY | 보관중
                    - CANCEL | 취소
                    - ERROR | 에러 상태
            dishWashingStatus:
              type: object
              description: 설정 상태
              properties:
                rinseRefill:
                  type: boolean
                  description: 린스 리필
                  enum:
                    - true
                    - false
            preference:
              type: object
              description: 선호 설정
              properties:
                rinseLevel:
                  type: string
                  description: 선호하는 린스 양 설정
                  enum:
                    - RINSELEVEL_0
                    - RINSELEVEL_1
                    - RINSELEVEL_2
                    - RINSELEVEL_3
                    - RINSELEVEL_4
                softeningLevel:
                  type: string
                  description: 선호하는 유연제 양 설정
                  enum:
                    - SOFTENINGLEVEL_0
                    - SOFTENINGLEVEL_1
                    - SOFTENINGLEVEL_2
                    - SOFTENINGLEVEL_3
                    - SOFTENINGLEVEL_4
                mCReminder:
                  type: string
                  description: 내부 청소 알림 설정
                  enum:
                    - MCREMINDER_OFF
                    - MCREMINDER_ON
                signalLevel:
                  type: string
                  description: 부저음 설정
                  enum:
                    - SIGNALLEVEL_OFF
                    - SIGNALLEVEL_ON
                cleanLReminder:
                  type: string
                  description: 세척 완료 표시창 설정
                  enum:
                    - CLEANLREMINDER_OFF
                    - CLEANLREMINDER_ON
            doorStatus:
              type: object
              description: 도어 상태
              properties:
                doorState:
                  type: string
                  description: 도어 열림 상태
                  enum:
                    - CLOSE
                    - OPEN
            operation:
              type: object
              description: 동작
              properties:
                dishWasherOperationMode:
                  type: string
                  description: 세탁 동작
                  enum:
                    - START
                    - STOP
                    - POWER_OFF
                    - CANCEL
            remoteControlEnable:
              type: object
              description: 원격제어 설정
              properties:
                remoteControlEnabled:
                  type: boolean
                  description: 원격 제어 설정 상태
                  enum:
                    - true
                    - false
            timer:
              type: object
              description: 타이머
              properties:
                remainHour:
                  type: integer
                  description: 남은 시간(시)
                  enum:
                    - integer
                remainMinute:
                  type: integer
                  description: 남은 시간(분)
                  enum:
                    - integer
                relativeHourToStart:
                  type: integer
                  description: 예약 시간(시)
                  enum:
                    - integer
                relativeMinuteToStart:
                  type: integer
                  description: 예약 시간(분)
                  enum:
                    - integer
                totalHour:
                  type: integer
                  description: 전체 시간(시)
                  enum:
                    - integer
                totalMinute:
                  type: integer
                  description: 전체 시간(분)
                  enum:
                    - integer
            dishWashingCourse:
              type: object
              description: 코스 정보
              properties:
                currentDishWashingCourse:
                  type: string
                  description: 현재 코스
                  enum:
                    - AUTO
                    - HEAVY
                    - DELICATE
                    - TURBO
                    - NORMAL
                    - RINSE
                    - REFRESH
                    - EXPRESS
                    - MACHINE_CLEAN
                    - SHORT_MODE
                    - DOWNLOAD_CYCLE
                    - QUICK
                    - STEAM
                    - SPRAY
                    - ECO
            notification:
              type: string
              description: Push Message
              enum:
                - CLEANING_IS_COMPLETE
                - ERROR_DURING_CLEANING
                - WATER_LEAK_HAS_OCCURRED
                - RINSE_IS_NOT_ENOUGH
                - SALT_REFILL_IS_NEEDED
            error:
              type: string
              description: 에러 메시지
              enum:
                - WATER_LEAKAGE_ERROR
                - BUBBLE_ERROR
                - HEATER_CIRCUIT_ERROR
                - WATER_SUPPLY_ERROR
                - MOTOR_ERROR
                - WATER_DRAIN_ERROR
                - TEMPERATURE_SENSOR_ERROR
        styler-profile:
          type: object
          title: Styler
          properties:
            property:
              type: object
              properties:
                runState:
                  type: object
                  description: 상태
                  properties:
                    currentState:
                      type: object
                      description: 제품 상태
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_OFF | 제품 OFF (0)
                                INITIAL | 대기중 상태 (1)
                                RUNNING | 행정중 (2)
                                PAUSE | 일시정지 (3)
                                COMPLETE | 완료 상태1 (4)
                                ERROR | 에러상태 (5)
                                DIAGNOSIS | 스마트진단 중 (6)
                                NIGHT_DRY | 보관중 (7)
                                RESERVED | 예약 상태 (8)
                                PRESTEAM | 스팀준비 (50)
                                PREHEAT | 리프레쉬1 (51)
                                STEAM | 리프레쉬2 (52)
                                STAY | 리프레쉬3 (53)
                                COOLING | 건조1 (54)
                                DRYING | 건조2 (55)
                                END_COOLING | 건조3 (56)
                                STERILIZE | 살균 (57)
                                RUNNING_END | 완료상태2 (58)
                                FOTA | 업데이트 중 (98)
                                SLEEP | 절전모드 
                              items:
                                type: string
                                enum:
                                  - POWER_OFF
                                  - INITIAL
                                  - RUNNING
                                  - PAUSE
                                  - COMPLETE
                                  - ERROR
                                  - DIAGNOSIS
                                  - NIGHT_DRY
                                  - RESERVED
                                  - PRESTEAM
                                  - PREHEAT
                                  - STEAM
                                  - STAY
                                  - COOLING
                                  - DRYING
                                  - END_COOLING
                                  - STERILIZE
                                  - RUNNING_END
                                  - FOTA
                                  - SLEEP
                    currentDetail:
                      type: object
                      description: 제품 상태 상세
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                 -|- 
                                 DETECTING | 무게 감지중
                                 REFRESH | 리프레쉬 4
                                 AIR_CARE | 공간청정 중
                                 DEHUMIDIFY | 실내제습 중
                              items:
                                type: string
                                enum:
                                  - DETECTING
                                  - REFRESH
                                  - AIR_CARE
                                  - DEHUMIDIFY
                operation:
                  type: object
                  description: 동작
                  properties:
                    stylerOperationMode:
                      type: object
                      description: 행정 동작
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                START | 행정 시작
                                STOP | 행정 멈춤
                                POWER_OFF | 제품 끔
                                WAKE_UP | Wake up 
                              items:
                                type: string
                                enum:
                                  - START
                                  - STOP
                                  - POWER_OFF
                                  - WAKE_UP
                remoteControlEnable:
                  type: object
                  description: 원격제어 설정
                  properties:
                    remoteControlEnabled:
                      type: object
                      description: 원격 제어 설정 상태
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - boolean
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                TRUE | 원격 제어 가능
                                FALSE | 원격 제어 불가능
                              items:
                                type: string
                                enum:
                                  - true
                                  - false
                timer:
                  type: object
                  description: 타이머
                  properties:
                    remainHour:
                      type: object
                      description: 남은 시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    remainMinute:
                      type: object
                      description: 남은 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    relativeHourToStop:
                      type: object
                      description: 스타일링 종료 예약 시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
                    relativeMinuteToStop:
                      type: object
                      description: 스타일링 종료 예약 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    totalHour:
                      type: object
                      description: 건조 전체 시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    totalMinute:
                      type: object
                      description: 건조 전체 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
            notification:
              type: object
              properties:
                push:
                  type: array
                  minItems: 1
                  description: |-
                    Push Code | Description
                    -|-
                    STYLING_IS_COMPLETE | 스타일링이 완료되었습니다.
                    ERROR_HAS_OCCURRED | 스타일러 동작중 오류가 발생하였습니다.
                  items:
                    type: string
                    enum:
                      - STYLING_IS_COMPLETE
                      - ERROR_HAS_OCCURRED
            error:
              type: array
              description: |-
                Push Code | Description
                -|-
                WATER_LEAKS_ERROR | 누수 에러
                DOOR_CLOSE_ERROR | 문 닫힘 에러
                DOOR_OPEN_ERROR | 문 열림 에러
                NEED_WATER_DRAIN | 배수 에러
                STEAM_HEAT_ERROR | 스팀 히트 에러
                NEED_WATER_REPLENISHMENT | 물 보충 필요 에러
                WATER_LEVEL_SENSOR_ERROR | 수위 센서 에러
                LE_ERROR | LE 에러
                LE2_ERROR | LE2 에러
                TEMPERATURE_SENSOR_ERROR | 온도 센서 에러
              items:
                type: string
                enum:
                  - WATER_LEAKS_ERROR
                  - DOOR_CLOSE_ERROR
                  - DOOR_OPEN_ERROR
                  - NEED_WATER_DRAIN
                  - STEAM_HEAT_ERROR
                  - NEED_WATER_REPLENISHMENT
                  - WATER_LEVEL_SENSOR_ERROR
                  - LE_ERROR
                  - LE2_ERROR
                  - TEMPERATURE_SENSOR_ERROR
        styler-object:
          type: object
          title: Styler
          properties:
            runState:
              type: object
              description: 상태
              properties:
                currentState:
                  type: string
                  description: 제품 상태
                  enum:
                    - POWER_OFF
                    - INITIAL
                    - RUNNING
                    - PAUSE
                    - COMPLETE
                    - ERROR
                    - DIAGNOSIS
                    - NIGHT_DRY
                    - RESERVED
                    - PRESTEAM
                    - PREHEAT
                    - STEAM
                    - STAY
                    - COOLING
                    - DRYING
                    - END_COOLING
                    - STERILIZE
                    - RUNNING_END
                    - FOTA
                    - SLEEP
                currentDetail:
                  type: string
                  description: 제품 상태 상세
                  enum:
                    - DETECTING
                    - REFRESH
                    - AIR_CARE
                    - DEHUMIDIFY
            operation:
              type: object
              description: 동작
              properties:
                stylerOperationMode:
                  type: string
                  description: 행정 동작
                  enum:
                    - START
                    - STOP
                    - POWER_OFF
                    - WAKE_UP
            remoteControlEnable:
              type: object
              description: 원격제어 설정
              properties:
                remoteControlEnabled:
                  type: boolean
                  description: 원격 제어 설정 상태
                  enum:
                    - true
                    - false
            timer:
              type: object
              description: 타이머
              properties:
                remainHour:
                  type: integer
                  description: 남은 시간(시)
                  enum:
                    - integer
                remainMinute:
                  type: integer
                  description: 남은 시간(분)
                  enum:
                    - integer
                relativeHourToStop:
                  type: integer
                  description: 스타일링 종료 예약 시간(시)
                  enum:
                    - number
                relativeMinuteToStop:
                  type: integer
                  description: 스타일링 종료 예약 시간(분)
                  enum:
                    - integer
                totalHour:
                  type: integer
                  description: 건조 전체 시간(시)
                  enum:
                    - integer
                totalMinute:
                  type: integer
                  description: 건조 전체 시간(분)
                  enum:
                    - integer
            notification:
              type: string
              description: Push Message
              enum:
                - STYLING_IS_COMPLETE
                - ERROR_HAS_OCCURRED
            error:
              type: string
              description: Error Message
              enum:
                - WATER_LEAKS_ERROR
                - DOOR_CLOSE_ERROR
                - DOOR_OPEN_ERROR
                - NEED_WATER_DRAIN
                - STEAM_HEAT_ERROR
                - NEED_WATER_REPLENISHMENT
                - WATER_LEVEL_SENSOR_ERROR
                - LE_ERROR
                - LE2_ERROR
                - TEMPERATURE_SENSOR_ERROR
        water_purifier-profile:
          type: object
          title: Water_Purifier
          properties:
            property:
              type: object
              properties:
                runState:
                  type: object
                  description: 상태
                  properties:
                    cockSate:
                      type: object
                      description: 코크 상태(UVNano)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                CLEANING | 살균 중
                                NORMAL | 일반
                              items:
                                type: string
                                enum:
                                  - CLEANING
                                  - NORMAL
                    sterilizingState:
                      type: object
                      description: 고온 살균 상태
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                 -|- 
                                 OFF | 꺼짐
                                 ON | 살균중
                                 CANCEL | 취소중
                              items:
                                type: string
                                enum:
                                  - 'OFF'
                                  - 'ON'
                                  - CANCEL
                waterInfo:
                  type: object
                  description: 물 종류
                  properties:
                    waterType:
                      type: object
                      description: 행정 동작
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - array
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                COLD | 냉수
                                HOT | 온수
                                NORMAL | 정수
                                MINERAL | 미네랄수
                                SODA | 틴신수 
                              items:
                                type: string
                                enum:
                                  - COLD
                                  - HOT
                                  - NORMAL
                                  - MINERAL
                                  - SODA
        water_purifier-object:
          type: object
          title: Water_Purifier
          properties:
            runState:
              type: object
              description: 상태
              properties:
                cockSate:
                  type: string
                  description: 코크 상태(UVNano)
                  enum:
                    - CLEANING
                    - NORMAL
                sterilizingState:
                  type: string
                  description: 고온 살균 상태
                  enum:
                    - 'OFF'
                    - 'ON'
                    - CANCEL
            waterInfo:
              type: object
              description: 물 종류
              properties:
                waterType:
                  type: array
                  description: 행정 동작
                  items:
                    type: string
                    enum:
                      - COLD
                      - HOT
                      - NORMAL
                      - MINERAL
                      - SODA
        ceiling_fan-profile:
          type: object
          title: Ceiling_Fan
          properties:
            property:
              type: object
              properties:
                operation:
                  type: object
                  description: 동작
                  properties:
                    ceilingfanOperationMode:
                      type: object
                      description: 본체 동작
                      properties:
                        mode:
                          type: array
                          enum:
                            - r
                            - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_ON | 실링팬 가동 시작
                                POWER_OFF | 실링팬 가동 중지
                              items:
                                type: string
                                enum:
                                  - POWER_ON
                                  - POWER_OFF
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_ON | 실링팬 가동 시작
                                POWER_OFF | 실링팬 가동 중지
                              items:
                                type: string
                                enum:
                                  - POWER_ON
                                  - POWER_OFF
                airFlow:
                  type: object
                  description: 바람 세기
                  properties:
                    windStrength:
                      type: object
                      description: 바람 세기
                      properties:
                        mode:
                          type: array
                          enum:
                            - r
                            - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                LOW | 약풍
                                MID | 중풍
                                HIGH | 강풍
                                TURBO | 터보 
                              items:
                                type: string
                                enum:
                                  - LOW
                                  - MID
                                  - HIGH
                                  - TURBO
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                LOW | 약풍
                                MID | 중풍
                                HIGH | 강풍
                                TURBO | 터보 
                              items:
                                type: string
                                enum:
                                  - LOW
                                  - MID
                                  - HIGH
                                  - TURBO
        ceiling_fan-object:
          type: object
          title: Ceiling_Fan
          properties:
            operation:
              type: object
              description: 동작
              properties:
                ceilingfanOperationMode:
                  type: string
                  description: 본체 동작
                  enum:
                    - POWER_ON
                    - POWER_OFF
            airFlow:
              type: object
              description: 바람 세기
              properties:
                windStrength:
                  type: string
                  description: 바람 세기
                  enum:
                    - LOW
                    - MID
                    - HIGH
                    - TURBO
        wine_cellar-profile:
          type: object
          title: Wine_Cellar
          properties:
            property:
              type: object
              properties:
                operation:
                  type: object
                  description: 기능
                  properties:
                    lightBrightness:
                      type: object
                      description: 조명 밝기
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                OFF | 꺼짐
                                35% | 35%
                                70% | 70%
                                100% | 100%
                                MAIN ROOM | main room 밝기
                                AUTO | 자동
                              items:
                                type: string
                                enum:
                                  - 'OFF'
                                  - 35%
                                  - 70%
                                  - 100%
                                  - MAIN ROOM
                                  - AUTO
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                OFF | 꺼짐
                                35% | 35%
                                70% | 70%
                                100% | 100%
                                MAIN ROOM | main room 밝기
                                AUTO | 자동
                              items:
                                type: string
                                enum:
                                  - 'OFF'
                                  - 35%
                                  - 70%
                                  - 100%
                                  - MAIN ROOM
                                  - AUTO
                    lightStatus:
                      type: object
                      description: 조명 상태
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                            w:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                    optimalHumidity:
                      type: object
                      description: 최적 습도 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                ON | 최적 습도 설정 켜짐
                                OFF | 최적 습도 설정 꺼짐 
                              items:
                                type: string
                                enum:
                                  - 'ON'
                                  - 'OFF'
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                ON | 최적 습도 설정 켜짐
                                OFF | 최적 습도 설정 꺼짐 
                              items:
                                type: string
                                enum:
                                  - 'ON'
                                  - 'OFF'
                    sabbathMode:
                      type: object
                      description: 안식일 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - boolean
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                TRUE | 안식일 설정
                                FALSE | 안식일 해제 
                              items:
                                type: string
                                enum:
                                  - true
                                  - false
                temperature:
                  type: array
                  description: 온도
                  items:
                    type: object
                    properties:
                      targetTemperature:
                        type: object
                        description: 희망 온도
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                              w:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      unit:
                        type: string
                        description: |-
                          Value | Description
                          -|-
                          C | 섭씨
                          F | 화씨
                        enum:
                          - C
                          - F
                      locationName:
                        type: string
                        description: |-
                          Value | Description
                          -|-
                          WINE_UPPER | UPPER 위치
                          WINE_MIDDLE | MIDDLE 위치
                          WINE_LOWER | LOWER 위치
                        enum:
                          - WINE_UPPER
                          - WINE_MIDDLE
                          - WINE_LOWER
        wine_cellar-object:
          type: object
          title: Wine_Cellar
          properties:
            operation:
              type: object
              description: 기능
              properties:
                lightBrightness:
                  type: string
                  description: 조명 밝기
                  enum:
                    - 'OFF'
                    - 35%
                    - 70%
                    - 100%
                    - MAIN ROOM
                    - AUTO
                lightStatus:
                  type: integer
                  description: 조명 상태
                optimalHumidity:
                  type: string
                  description: 최적 습도 설정
                  enum:
                    - 'ON'
                    - 'OFF'
                sabbathMode:
                  type: boolean
                  description: 안식일 설정
                  enum:
                    - true
                    - false
            temperature:
              type: array
              description: 온도
              items:
                type: object
                properties:
                  targetTemperature:
                    type: integer
                    description: 희망 온도
                  unit:
                    type: string
                    enum:
                      - C
                      - F
                    description: 단위
                  locationName:
                    type: string
                    description: 위치 이름
                    enum:
                      - WINE_UPPER
                      - WINE_MIDDLE
                      - WINE_LOWER
        kimchi_refrigerator-profile:
          type: object
          title: Kimchi_Refrigerator
          properties:
            property:
              type: object
              properties:
                refrigeration:
                  type: object
                  description: 기능
                  properties:
                    freshAirFilter:
                      type: object
                      description: 공기 필터 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                OFF | 해제
                                AUTO | 자동
                                POWER | 파워
                              items:
                                type: string
                                enum:
                                  - 'OFF'
                                  - AUTO
                                  - POWER
                    oneTouchFilter:
                      type: object
                      description: 공기 필터 설정
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: enum
                              description: |-
                                Value | Description
                                -|-
                                ON | 켜짐
                                OFF | 꺼짐 
                              items:
                                type: string
                                enum:
                                  - 'ON'
                                  - 'OFF'
                temperature:
                  type: array
                  description: 온도
                  items:
                    type: object
                    properties:
                      targetTemperature:
                        type: object
                        description: 희망 온도
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  KIMCHI | 김치
                                  OFF | 꺼짐
                                  FREEZER | 냉동
                                  FRIDGE | 냉장
                                  STORAGE | 보관
                                  MEAT_FISH | 육류/생선
                                  RICE_GRAIN | 쌀/곡류
                                  VEGETABLE_FRUIT | 채소/과일
                                  TEMPERATURE_NUMBER | 온도인 경우 숫자로 표시
                                items:
                                  type: string
                                  enum:
                                    - KIMCHI
                                    - 'OFF'
                                    - FREEZER
                                    - FRIDGE
                                    - STORAGE
                                    - MEAT_FISH
                                    - RICE_GRAIN
                                    - VEGETABLE_FRUIT
                      locationName:
                        type: string
                        description: |-
                          Value | Description
                          -|-
                          TOP | 상칸(좌칸)
                          LEFT | 좌칸
                          RIGHT | 우칸
                          MIDDLE | 중칸
                          BOTTOM | 하칸
                          SINGLE | 단일칸
                        enum:
                          - TOP
                          - LEFT
                          - RIGHT
                          - MIDDLE
                          - BOTTOM
                          - SINGLE
            notification:
              type: object
              properties:
                push:
                  type: array
                  minItems: 1
                  description: |-
                    Push Code | Description
                    -|-
                    DOOR_IS_OPEN | 문이 열렸습니다.
                  items:
                    type: string
                    enum:
                      - DOOR_IS_OPEN
        kimchi_refrigerator-object:
          type: object
          title: Kimchi_Refrigerator
          properties:
            property:
              type: object
              properties:
                refrigeration:
                  type: object
                  description: 기능
                  properties:
                    freshAirFilter:
                      type: string
                      description: 공기 필터 설정
                      enum:
                        - 'OFF'
                        - AUTO
                        - POWER
                    oneTouchFilter:
                      type: string
                      description: 공기 필터 설정
                      enum:
                        - 'ON'
                        - 'OFF'
                temperature:
                  type: array
                  description: 온도
                  items:
                    type: object
                    properties:
                      targetTemperature:
                        type: string
                        description: 희망 온도
                        enum:
                          - KIMCHI
                          - 'OFF'
                          - FREEZER
                          - FRIDGE
                          - STORAGE
                          - MEAT_FISH
                          - RICE_GRAIN
                          - VEGETABLE_FRUIT
                      locationName:
                        type: string
                        description: 위치 이름
                        enum:
                          - TOP
                          - LEFT
                          - RIGHT
                          - MIDDLE
                          - BOTTOM
                          - SINGLE
            notification:
              type: string
              description: Push Message
              enum:
                - DOOR_IS_OPEN
        home_brew-profile:
          type: object
          title: Home_Brew
          properties:
            property:
              type: object
              properties:
                runState:
                  type: object
                  description: 상태
                  properties:
                    currentState:
                      type: object
                      description: 현재 상태
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                STANDBY | 대기중
                                PREPAREING_FERMENTATION | 준비중
                                DURING_FERMENTATION | 발효중
                                CARBONATION | 탄산화중
                                DURING_AGING | 숙성중
                                EXTRACTION_MODE | 보관중
                                MELTING | 맥즙 용해중
                                TEMPERATURE_STABILIZATION | 온도 안정화 중
                                EXTRACTING_CAPSULE | 캡슐 추출 중
                                AS_POP_UP | 에러 발생
                              items:
                                type: string
                                enum:
                                  - STANDBY
                                  - PREPAREING_FERMENTATION
                                  - DURING_FERMENTATION
                                  - CARBONATION
                                  - DURING_AGING
                                  - EXTRACTION_MODE
                                  - MELTING
                                  - TEMPERATURE_STABILIZATION
                                  - EXTRACTING_CAPSULE
                                  - AS_POP_UP
                timer:
                  type: object
                  description: 타이머
                  properties:
                    elapsedDayState:
                      type: object
                      description: 제조 경과일
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                    elapsedDayTotal:
                      type: object
                      description: 전체 제조 경과일
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                recipe:
                  type: object
                  description: 레시피
                  properties:
                    recipeName:
                      type: object
                      description: 레시피 이름
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                IPA | 인디언 페일 에일
                                PALE_ALE | 페일 에일
                                STOUT | 스타우트
                                WHEAT | 위트
                                PILSNER | 필스너
                                RED_ALE | 레드 에일
                                MY_RECIPE | 마이 레시피
                              items:
                                type: string
                                enum:
                                  - IPA
                                  - PALE_ALE
                                  - STOUT
                                  - WHEAT
                                  - PILSNER
                                  - RED_ALE
                                  - MY_RECIPE
                    wortInfo:
                      type: object
                      description: 맥즙 정보
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                HOPPY | 호피
                                DEEP_GOLD | 딥골드
                                WHEAT | 위트
                                DARK | 다크
                              items:
                                type: string
                                enum:
                                  - HOPPY
                                  - DEEP_GOLD
                                  - WHEAT
                                  - DARK
                    yeastInfo:
                      type: object
                      description: 효모 정보
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                AMERICAN_ALE | 아메리칸 에일
                                ENGLISH_ALE | 잉글리쉬 에일
                                LAGER | 라거
                                WEIZEN | 바이젠
                              items:
                                type: string
                                enum:
                                  - AMERICAN_ALE
                                  - ENGLISH_ALE
                                  - LAGER
                                  - WEIZEN
                    hopOilInfo:
                      type: object
                      description: 홉오일 정보
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - array
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                CASCADE | 케스케이드
                                CHINOOK | 치누크
                                GOLDINGS | 골딩스
                                FUGGLES | 퍼글스
                                HALLERTAU | 할러타우
                                CITRUSSY | 시트러스
                              items:
                                type: string
                                enum:
                                  - CASCADE
                                  - CHINOOK
                                  - GOLDINGS
                                  - FUGGLES
                                  - HALLERTAU
                                  - CITRUSSY
                    flavorInfo:
                      type: object
                      description: 플레이버 정보
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - array
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                CASCADE | 케스케이드
                                CHINOOK | 치누크
                                GOLDINGS | 골딩스
                                FUGGLES | 퍼글스
                                HALLERTAU | 할러타우
                                CITRUSSY | 시트러스
                              items:
                                type: string
                                enum:
                                  - CASCADE
                                  - CHINOOK
                                  - GOLDINGS
                                  - FUGGLES
                                  - HALLERTAU
                                  - CITRUSSY
                    beerRemain:
                      type: object
                      description: 진행율
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
        home_brew-object:
          type: object
          title: Home_Brew
          properties:
            runState:
              type: object
              description: 상태
              properties:
                currentState:
                  type: string
                  description: 현재 상태
                  enum:
                    - STANDBY
                    - PREPAREING_FERMENTATION
                    - DURING_FERMENTATION
                    - CARBONATION
                    - DURING_AGING
                    - EXTRACTION_MODE
                    - MELTING
                    - TEMPERATURE_STABILIZATION
                    - EXTRACTING_CAPSULE
                    - AS_POP_UP
            timer:
              type: object
              description: 타이머
              properties:
                elapsedDayState:
                  type: integer
                  description: 제조 경과일
                elapsedDayTotal:
                  type: integer
                  description: 전체 제조 경과일
            recipe:
              type: object
              description: 레시피
              properties:
                recipeName:
                  type: string
                  description: 레시피 이름
                  enum:
                    - IPA
                    - PALE_ALE
                    - STOUT
                    - WHEAT
                    - PILSNER
                    - RED_ALE
                    - MY_RECIPE
                wortInfo:
                  type: string
                  description: 맥즙 정보
                  enum:
                    - HOPPY
                    - DEEP_GOLD
                    - WHEAT
                    - DARK
                yeastInfo:
                  type: string
                  description: 효모 정보
                  enum:
                    - AMERICAN_ALE
                    - ENGLISH_ALE
                    - LAGER
                    - WEIZEN
                hopOilInfo:
                  type: array
                  description: 홉오일 정보
                  items:
                    type: string
                    enum:
                      - CASCADE
                      - CHINOOK
                      - GOLDINGS
                      - FUGGLES
                      - HALLERTAU
                      - CITRUSSY
                flavorInfo:
                  type: array
                  description: 플레이버 정보
                  items:
                    type: string
                    enum:
                      - CASCADE
                      - CHINOOK
                      - GOLDINGS
                      - FUGGLES
                      - HALLERTAU
                      - CITRUSSY
                beerRemain:
                  type: integer
                  description: 진행율
        plant_cultivator-profile:
          type: object
          title: Plant_Cultivator
          properties:
            property:
              type: array
              items:
                type: object
                properties:
                  runState:
                    type: object
                    description: 상태
                    properties:
                      currentState:
                        type: object
                        description: 현재 상태
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  POWER_ON | 켜짐
                                  POWER_OFF | 꺼짐
                                items:
                                  type: string
                                  enum:
                                    - POWER_ON
                                    - POWER_OFF
                      growthMode:
                        type: object
                        description: 재배 환경
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  STANDARD | 표준
                                  EXT_LEAF | 엽채
                                  EXT_HERB | 허브
                                  EXT_FLOWER | 화훼
                                  EXT_EXPERT | 사용자 저장 환경
                                items:
                                  type: string
                                  enum:
                                    - STANDARD
                                    - EXT_LEAF
                                    - EXT_HERB
                                    - EXT_FLOWER
                                    - EXT_EXPERT
                      windVolume:
                        type: object
                        description: 바람 세기
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              min:
                                type: integer
                              max:
                                type: integer
                              step:
                                type: integer
                  light:
                    type: object
                    description: 조명
                    properties:
                      brightness:
                        type: object
                        description: 조명 밝기
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                      duration:
                        type: object
                        description: 조명 지속 시간
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                      startHour:
                        type: object
                        description: 조명 시작 시간
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                      startMinute:
                        type: object
                        description: 조명 시작 분
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                      endHour:
                        type: object
                        description: 조명 끝 시간
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                      endMinute:
                        type: object
                        description: 조명 끝 분
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                  temperature:
                    type: object
                    description: 온도
                    properties:
                      dayTargetTemperature:
                        type: object
                        description: 주간 재배 온도
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                      nightTargetTemperature:
                        type: object
                        description: 야간 재배 온도
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                      temperatureState:
                        type: object
                        description: 재배 온도 상태
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  HIGH | 높음
                                  NORMAL | 정상
                                  LOW | 낮음
                                items:
                                  type: string
                                  enum:
                                    - HIGH
                                    - NORMAL
                                    - LOW
                  location:
                    type: object
                    description: 위치
                    properties:
                      locationName:
                        type: string
                        description: |-
                          Value | Description
                          -|-
                          UPPER | 상칸
                          LOWER | 하칸
                        enum:
                          - UPPER
                          - LOWER
        plant_cultivator-object:
          title: Plant_Cultivator
          type: array
          items:
            type: object
            properties:
              runState:
                type: object
                description: 상태
                properties:
                  currentState:
                    type: string
                    description: 현재 상태
                    enum:
                      - POWER_ON
                      - POWER_OFF
                  growthMode:
                    type: string
                    description: 재배 환경
                    enum:
                      - STANDARD
                      - EXT_LEAF
                      - EXT_HERB
                      - EXT_FLOWER
                      - EXT_EXPERT
                  windVolume:
                    type: integer
                    description: 바람 세기
              light:
                type: object
                description: 조명
                properties:
                  brightness:
                    type: integer
                    description: 조명 밝기
                  duration:
                    type: integer
                    description: 조명 지속 시간
                  startHour:
                    type: integer
                    description: 조명 시작 시간
                  startMinute:
                    type: integer
                    description: 조명 시작 분
                  endHour:
                    type: integer
                    description: 조명 끝 시간
                  endMinute:
                    type: integer
                    description: 조명 끝 분
              temperature:
                type: object
                description: 온도
                properties:
                  dayTargetTemperature:
                    type: integer
                    description: 주간 재배 온도
                  nightTargetTemperature:
                    type: integer
                    description: 야간 재배 온도
                  temperatureState:
                    type: string
                    description: 재배 온도 상태
                    enum:
                      - HIGH
                      - NORMAL
                      - LOW
              location:
                type: object
                description: 위치
                properties:
                  locationName:
                    type: string
                    description: 위치 이름
                    enum:
                      - UPPER
                      - LOWER
        washtower_washer-profile:
          type: object
          title: Washtower_Washer
          properties:
            property:
              type: array
              items:
                type: object
                properties:
                  runState:
                    type: object
                    description: 상태
                    properties:
                      currentState:
                        type: object
                        description: 현재 상태
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: "Value | Description\n-|-\nPOWER_OFF | 제품 OFF\nINITIAL | 대기 중 상태\nPAUSE | 일시정지\nDETECTING | 옷감량확인\nSOAKING | 불림 상태\nRUNNING\t|\t행정중\nRINSING\t|\t행굼 중\nSPINNING | 탈수중\nEND\t| 세탁완료상태\nRESERVED | 예약상태\nFIRMWARE | 펌웨어 업데이트 중\nDRYING | 건조 중\nCOOL_DOWN\t| 구김방지1\nRINSE_HOLD | 린스 후 일시정지 중\nREFRESHING | 구김방지2 FRESHCARE\nSTEAM_SOFTENING | 스팀소프트닝\nERROR\t| 에러상태\nSMART_GRID_RUN | Smart Grid 동작 상태\nADD_DRAIN\t| 배수 추가 상태\nDETERGENT_AMOUNT | 세제량 표시중\nPREWASH | 예비 세탁 동작 상태\nSHOES_MODULE | 슈즈 건조 동작 상태\nPROOFING | 발수처리 상태\nDISPENSING | 세제 자동 투입 중\nSOFTENING | 유연제량 확인\nCHECKING_TURBIDITY | 탁도감지 중(G+Best모델 AUTOWASH 코스 사용 시)\nCHANGE_CONDITION | 탁도감지 결과를 가지고 자동으로 옵션변경 후 Display\nDISPLAY_LOADSIZE | 옷감량 확인 결과 Display\nFROZEN_PREVENT_INITIAL | 동결방지모드 대기상태\nFROZEN_PREVENT_RUNNING | 동결방지모드 진행상태\nFROZEN_PREVENT_PAUSE | 동결방지모드 멈춤상태\nSLEEP | Sleep 상태"
                                items:
                                  type: string
                                  enum:
                                    - POWER_OFF
                                    - INITIAL
                                    - PAUSE
                                    - DETECTING
                                    - SOAKING
                                    - RUNNING
                                    - RINSING
                                    - SPINNING
                                    - END
                                    - RESERVED
                                    - FIRMWARE
                                    - DRYING
                                    - COOL_DOWN
                                    - RINSE_HOLD
                                    - REFRESHING
                                    - STEAM_SOFTENING
                                    - ERROR
                                    - SMART_GRID_RUN
                                    - ADD_DRAIN
                                    - DETERGENT_AMOUNT
                                    - PREWASH
                                    - SHOES_MODULE
                                    - PROOFING
                                    - DISPENSING
                                    - SOFTENING
                                    - CHECKING_TURBIDITY
                                    - CHANGE_CONDITION
                                    - DISPLAY_LOADSIZE
                                    - FROZEN_PREVENT_INITIAL
                                    - FROZEN_PREVENT_RUNNING
                                    - FROZEN_PREVENT_PAUSE
                                    - SLEEP
                  operation:
                    type: object
                    description: 동작
                    properties:
                      washerOperationMode:
                        type: object
                        description: 세탁 동작
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - w
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              w:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  START | 세탁 시작
                                  STOP | 세탁 정지
                                  POWER_OFF | 전원 OFF
                                  WAKE_UP | Wake up
                                items:
                                  type: string
                                  enum:
                                    - START
                                    - STOP
                                    - POWER_OFF
                                    - WAKE_UP
                  remoteControlEnable:
                    type: object
                    description: 원격제어설정
                    properties:
                      remoteControlEnabled:
                        type: object
                        description: 원격 제어 설정 상태
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - boolean
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  TRUE | 원격 제어 가능
                                  FALSE | 원격 제어 불가능
                                items:
                                  type: boolean
                                  enum:
                                    - true
                                    - false
                  timer:
                    type: object
                    description: 타이머
                    properties:
                      remainHour:
                        type: object
                        description: 남은 시간(시)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      remainMinute:
                        type: object
                        description: 남은 시간(분)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      relativeHourToStart:
                        type: object
                        description: 세탁 시작 예약 시간(시)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                              w:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      relativeMinuteToStart:
                        type: object
                        description: 세탁 시작 예약 시간(분)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      relativeHourToStop:
                        type: object
                        description: 세탁 종료 예약 시간(시)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                              w:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      relativeMinuteToStop:
                        type: object
                        description: 세탁 종료 예약 시간(분)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      totalHour:
                        type: object
                        description: 세탁 전체 시간(시)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      totalMinute:
                        type: object
                        description: 세탁 전체 시간(분)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                  detergent:
                    type: object
                    description: 세제 설정
                    properties:
                      detergentSetting:
                        type: string
                        description: |-
                          Value | Description
                          -|-
                          AUTO | 자동 설정 기기
                          NORMAL | 일반 기기
                        enum:
                          - AUTO
                          - NORMAL
                  location:
                    type: object
                    description: 위치
                    properties:
                      locationName:
                        type: string
                        description: |-
                          Value | Description
                          -|-
                          MAIN | main washer
                          MINI | mini washer
                        enum:
                          - MAIN
                          - MINI
            notification:
              type: object
              properties:
                push:
                  type: array
                  minItems: 1
                  description: |-
                    Push Code | Description
                    -|-
                    WASHING_IS_COMPLETE | 세탁이 완료되었습니다.
                    ERROR_DURING_WASHING | 세탁 중 오류가 발생하였습니다.
                  items:
                    type: string
                    enum:
                      - WASHING_IS_COMPLETE
                      - ERROR_DURING_WASHING
            error:
              type: array
              description: |-
                Push Code | Description
                -|-
                WATER_SUPPLY_ERROR | 급수 에러
                WATER_DRAIN_ERROR | 배수 에러
                OUT_OF_BALANCE_ERROR | 탈수 에러
                LOCKED_MOTOR_ERROR | 드라이버 모터 에러
                CHILD_LOCK_ACTIVE_ERROR | childlock 에러
                TIME_TO_RUN_THE_TUB_CLEAN_CYCLE_ERROR | 통세척 에러
                UNBALANCED_LOAD_ERROR | 수평 에러
                DOOR_OPEN_ERROR | 문 열림 에러
                UNABLE_TO_LOCK_ERROR | 잠김 불가 에러
                OVERFILL_ERROR | 물 수위 에러
                WATER_LEVEL_SENSOR_ERROR | 물 수위 센서 에러
                POWER_FAIL_ERROR | 전력 에러
                TEMPERATURE_SENSOR_ERROR | 온도 센서 에러
                TIMEOUT_ERROR | 타임아웃 에러
                PART_MALFUNCTION_ERROR | 기기 부품 에러
              items:
                type: string
                enum:
                  - WATER_SUPPLY_ERROR
                  - WATER_DRAIN_ERROR
                  - OUT_OF_BALANCE_ERROR
                  - LOCKED_MOTOR_ERROR
                  - CHILD_LOCK_ACTIVE_ERROR
                  - TIME_TO_RUN_THE_TUB_CLEAN_CYCLE_ERROR
                  - UNBALANCED_LOAD_ERROR
                  - DOOR_OPEN_ERROR
                  - UNABLE_TO_LOCK_ERROR
                  - OVERFILL_ERROR
                  - WATER_LEVEL_SENSOR_ERROR
                  - POWER_FAIL_ERROR
                  - TEMPERATURE_SENSOR_ERROR
                  - TIMEOUT_ERROR
                  - PART_MALFUNCTION_ERROR
        washtower_washer-object:
          title: Washtower_Washer
          type: array
          items:
            type: object
            properties:
              runState:
                type: object
                description: 상태
                properties:
                  currentState:
                    type: string
                    description: 현재 상태
                    enum:
                      - POWER_OFF
                      - INITIAL
                      - PAUSE
                      - DETECTING
                      - SOAKING
                      - RUNNING
                      - RINSING
                      - SPINNING
                      - END
                      - RESERVED
                      - FIRMWARE
                      - DRYING
                      - COOL_DOWN
                      - RINSE_HOLD
                      - REFRESHING
                      - STEAM_SOFTENING
                      - ERROR
                      - SMART_GRID_RUN
                      - ADD_DRAIN
                      - DETERGENT_AMOUNT
                      - PREWASH
                      - SHOES_MODULE
                      - PROOFING
                      - DISPENSING
                      - SOFTENING
                      - CHECKING_TURBIDITY
                      - CHANGE_CONDITION
                      - DISPLAY_LOADSIZE
                      - FROZEN_PREVENT_INITIAL
                      - FROZEN_PREVENT_RUNNING
                      - FROZEN_PREVENT_PAUSE
                      - SLEEP
              operation:
                type: object
                description: 동작
                properties:
                  washerOperationMode:
                    type: string
                    description: 세탁 동작
                    enum:
                      - START
                      - STOP
                      - POWER_OFF
                      - WAKE_UP
              remoteControlEnable:
                type: object
                description: 원격제어설정
                properties:
                  remoteControlEnabled:
                    type: boolean
                    description: 원격 제어 설정 상태
                    enum:
                      - true
                      - false
              timer:
                type: object
                description: 타이머
                properties:
                  remainHour:
                    type: integer
                    description: 남은 시간(시)
                  remainMinute:
                    type: integer
                    description: 남은 시간(분)
                  relativeHourToStart:
                    type: integer
                    description: 세탁 시작 예약 시간(시)
                  relativeMinuteToStart:
                    type: integer
                    description: 세탁 시작 예약 시간(분)
                  relativeHourToStop:
                    type: integer
                    description: 세탁 종료 예약 시간(시)
                  relativeMinuteToStop:
                    type: integer
                    description: 세탁 종료 예약 시간(분)
                  totalHour:
                    type: integer
                    description: 세탁 전체 시간(시)
                  totalMinute:
                    type: integer
                    description: 세탁 전체 시간(분)
              detergent:
                type: object
                description: 세제 설정
                properties:
                  detergentSetting:
                    type: string
                    description: 세제 설정 모드
                    enum:
                      - AUTO
                      - NORMAL
              location:
                type: object
                description: 위치
                properties:
                  locationName:
                    type: string
                    description: 위치 이름
                    enum:
                      - MAIN
                      - MINI
              notification:
                type: string
                description: Error Message
                enum:
                  - WASHING_IS_COMPLETE
                  - ERROR_DURING_WASHING
              error:
                type: string
                description: Error Message
                enum:
                  - WATER_SUPPLY_ERROR
                  - WATER_DRAIN_ERROR
                  - OUT_OF_BALANCE_ERROR
                  - LOCKED_MOTOR_ERROR
                  - CHILD_LOCK_ACTIVE_ERROR
                  - TIME_TO_RUN_THE_TUB_CLEAN_CYCLE_ERROR
                  - UNBALANCED_LOAD_ERROR
                  - DOOR_OPEN_ERROR
                  - UNABLE_TO_LOCK_ERROR
                  - OVERFILL_ERROR
                  - WATER_LEVEL_SENSOR_ERROR
                  - POWER_FAIL_ERROR
                  - TEMPERATURE_SENSOR_ERROR
                  - TIMEOUT_ERROR
                  - PART_MALFUNCTION_ERROR
        washtower_dryer-profile:
          type: object
          title: Washtower_Dryer
          properties:
            property:
              type: object
              properties:
                runState:
                  type: object
                  description: 상태
                  properties:
                    currentState:
                      type: object
                      description: 현재 상태
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_OFF | 제품 OFF
                                INITIAL | 대기 중 상태
                                PAUSE | 일시정지
                                DETECTING | 옷감량확인
                                COOLING | 쿨링
                                RUNNING | 실행중
                                WRINKLE_CARE | 주름방지실행중
                                END | 건조완료상태
                                RESERVED | 예약상태
                                ERROR | 에러상태
                                SLEEP | Sleep 상태
                              items:
                                type: string
                                enum:
                                  - POWER_OFF
                                  - INITIAL
                                  - PAUSE
                                  - DETECTING
                                  - COOLING
                                  - RUNNING
                                  - WRINKLE_CARE
                                  - END
                                  - RESERVED
                                  - ERROR
                                  - SLEEP
                operation:
                  type: object
                  description: 동작
                  properties:
                    dryerOperationMode:
                      type: object
                      description: 건조 동작
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                START | 건조 시작
                                STOP | 건조 정지
                                POWER_OFF | 전원 OFF
                                WAKE_UP | Wake up
                              items:
                                type: string
                                enum:
                                  - START
                                  - STOP
                                  - POWER_OFF
                                  - WAKE_UP
                remoteControlEnable:
                  type: object
                  description: 원격제어설정
                  properties:
                    remoteControlEnabled:
                      type: object
                      description: 원격 제어 설정 상태
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - boolean
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                TRUE | 원격 제어 가능
                                FALSE | 원격 제어 불가능
                              items:
                                type: boolean
                                enum:
                                  - true
                                  - false
                timer:
                  type: object
                  description: 타이머
                  properties:
                    remainHour:
                      type: object
                      description: 남은 시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    remainMinute:
                      type: object
                      description: 남은 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    relativeHourToStart:
                      type: object
                      description: 건조 시작 예약 시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                            w:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                    relativeMinuteToStart:
                      type: object
                      description: 건조 시작 예약 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    relativeHourToStop:
                      type: object
                      description: 건조 종료 예약 시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                            w:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                    relativeMinuteToStop:
                      type: object
                      description: 건조 종료 예약 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    totalHour:
                      type: object
                      description: 건조 전체 시간(시)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    totalMinute:
                      type: object
                      description: 건조 전체 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
            notification:
              type: object
              properties:
                push:
                  type: array
                  description: |-
                    Push Code | Description
                    -|-
                    DRYING_FAILED | 건조를 실패하였습니다.
                    DRYING_IS_COMPLETE | 건조가 완료되었습니다.
                  items:
                    type: string
                    enum:
                      - DRYING_FAILED
                      - DRYING_IS_COMPLETE
            error:
              type: array
              description: |-
                Push Code | Description
                -|-
                TEMPERATURE_SENSOR_ERROR | 온도 센서 에러
                COMPRESSOR_ERROR | 컴프레서 에러
                DRAINMOTOR_ERROR | 펌프 에러
                EMPTY_WATER_ALERT_ERROR | 물 비우기 알림 에러
                HIGH_TEMPERATURE_DETECTION_ERROR | 고온감지 에러
                MOTOR_LOCK_ERROR | 모터 멈춤 에러
                DOOR_SENSOR_ERROR | 문 센서 에러
                DOOR_OPEN_ERROR | 문 열림 에러
                DOOR_LOCK_ERROR | 문 잠김 에러
                NO_FILTER_ERROR | 필터 없음 에러
                FILTER_CLOGGING_ERROR | 필터 막힘 에러
                HIGH_POWER_SUPPLY_ERROR | 비 정상 전압 인가 에러
                POWER_CODE_CONNECTION_ERROR | 전원선 연결 이상 에러
                FAN_MOTOR_ERROR | 팬 모터 에러
              items:
                type: string
                enum:
                  - TEMPERATURE_SENSOR_ERROR
                  - COMPRESSOR_ERROR
                  - DRAINMOTOR_ERROR
                  - EMPTY_WATER_ALERT_ERROR
                  - HIGH_TEMPERATURE_DETECTION_ERROR
                  - MOTOR_LOCK_ERROR
                  - DOOR_SENSOR_ERROR
                  - DOOR_OPEN_ERROR
                  - DOOR_LOCK_ERROR
                  - NO_FILTER_ERROR
                  - FILTER_CLOGGING_ERROR
                  - HIGH_POWER_SUPPLY_ERROR
                  - POWER_CODE_CONNECTION_ERROR
                  - FAN_MOTOR_ERROR
        washtower_dryer-object:
          type: object
          title: Washtower_Dryer
          properties:
            runState:
              type: object
              description: 상태
              properties:
                currentState:
                  type: string
                  description: 현재 상태
                  enum:
                    - POWER_OFF
                    - INITIAL
                    - PAUSE
                    - DETECTING
                    - COOLING
                    - RUNNING
                    - WRINKLE_CARE
                    - END
                    - RESERVED
                    - ERROR
                    - SLEEP
            operation:
              type: object
              description: 동작
              properties:
                dryerOperationMode:
                  type: string
                  description: 건조 동작
                  enum:
                    - START
                    - STOP
                    - POWER_OFF
                    - WAKE_UP
            remoteControlEnable:
              type: object
              description: 원격제어설정
              properties:
                remoteControlEnabled:
                  type: boolean
                  description: 원격 제어 설정 상태
                  enum:
                    - true
                    - false
            timer:
              type: object
              description: 타이머
              properties:
                remainHour:
                  type: integer
                  description: 남은 시간(시)
                remainMinute:
                  type: integer
                  description: 남은 시간(분)
                relativeHourToStart:
                  type: integer
                  description: 건조 시작 예약 시간(시)
                relativeMinuteToStart:
                  type: integer
                  description: 건조 시작 예약 시간(분)
                relativeHourToStop:
                  type: integer
                  description: 건조 종료 예약 시간(시)
                relativeMinuteToStop:
                  type: integer
                  description: 건조 종료 예약 시간(분)
                totalHour:
                  type: integer
                  description: 건조 전체 시간(시)
                totalMinute:
                  type: integer
                  description: 건조 전체 시간(분)
            notification:
              type: object
              description: Push Message
              enum:
                - DRYING_FAILED
                - DRYING_IS_COMPLETE
            error:
              type: object
              description: Error Message
              enum:
                - TEMPERATURE_SENSOR_ERROR
                - COMPRESSOR_ERROR
                - DRAINMOTOR_ERROR
                - EMPTY_WATER_ALERT_ERROR
                - HIGH_TEMPERATURE_DETECTION_ERROR
                - MOTOR_LOCK_ERROR
                - DOOR_SENSOR_ERROR
                - DOOR_OPEN_ERROR
                - DOOR_LOCK_ERROR
                - NO_FILTER_ERROR
                - FILTER_CLOGGING_ERROR
                - HIGH_POWER_SUPPLY_ERROR
                - POWER_CODE_CONNECTION_ERROR
                - FAN_MOTOR_ERROR
        washtower-profile:
          type: object
          title: Washtower
          properties:
            washer:
              type: object
              properties:
                property:
                  type: array
                  items:
                    type: object
                    properties:
                      runState:
                        type: object
                        description: 상태
                        properties:
                          currentState:
                            type: object
                            description: 현재 상태
                            properties:
                              mode:
                                type: array
                                items:
                                  type: string
                                  enum:
                                    - r
                              type:
                                type: string
                                enum:
                                  - enum
                              value:
                                type: object
                                properties:
                                  r:
                                    type: array
                                    description: "Value | Description\n-|-\nPOWER_OFF | 제품 OFF\nINITIAL | 대기 중 상태\nPAUSE | 일시정지\nDETECTING | 옷감량확인\nSOAKING | 불림 상태\nRUNNING\t|\t행정중\nRINSING\t|\t행굼 중\nSPINNING | 탈수중\nEND\t| 세탁완료상태\nRESERVED | 예약상태\nFIRMWARE | 펌웨어 업데이트 중\nDRYING | 건조 중\nCOOL_DOWN\t| 구김방지1\nRINSE_HOLD | 린스 후 일시정지 중\nREFRESHING | 구김방지2 FRESHCARE\nSTEAM_SOFTENING | 스팀소프트닝\nERROR\t| 에러상태\nSMART_GRID_RUN | Smart Grid 동작 상태\nADD_DRAIN\t| 배수 추가 상태\nDETERGENT_AMOUNT | 세제량 표시중\nPREWASH | 예비 세탁 동작 상태\nSHOES_MODULE | 슈즈 건조 동작 상태\nPROOFING | 발수처리 상태\nDISPENSING | 세제 자동 투입 중\nSOFTENING | 유연제량 확인\nCHECKING_TURBIDITY | 탁도감지 중(G+Best모델 AUTOWASH 코스 사용 시)\nCHANGE_CONDITION | 탁도감지 결과를 가지고 자동으로 옵션변경 후 Display\nDISPLAY_LOADSIZE | 옷감량 확인 결과 Display\nFROZEN_PREVENT_INITIAL | 동결방지모드 대기상태\nFROZEN_PREVENT_RUNNING | 동결방지모드 진행상태\nFROZEN_PREVENT_PAUSE | 동결방지모드 멈춤상태\nSLEEP | Sleep 상태"
                                    items:
                                      type: string
                                      enum:
                                        - POWER_OFF
                                        - INITIAL
                                        - PAUSE
                                        - DETECTING
                                        - SOAKING
                                        - RUNNING
                                        - RINSING
                                        - SPINNING
                                        - END
                                        - RESERVED
                                        - FIRMWARE
                                        - DRYING
                                        - COOL_DOWN
                                        - RINSE_HOLD
                                        - REFRESHING
                                        - STEAM_SOFTENING
                                        - ERROR
                                        - SMART_GRID_RUN
                                        - ADD_DRAIN
                                        - DETERGENT_AMOUNT
                                        - PREWASH
                                        - SHOES_MODULE
                                        - PROOFING
                                        - DISPENSING
                                        - SOFTENING
                                        - CHECKING_TURBIDITY
                                        - CHANGE_CONDITION
                                        - DISPLAY_LOADSIZE
                                        - FROZEN_PREVENT_INITIAL
                                        - FROZEN_PREVENT_RUNNING
                                        - FROZEN_PREVENT_PAUSE
                                        - SLEEP
                      operation:
                        type: object
                        description: 동작
                        properties:
                          washerOperationMode:
                            type: object
                            description: 세탁 동작
                            properties:
                              mode:
                                type: array
                                items:
                                  type: string
                                  enum:
                                    - w
                              type:
                                type: string
                                enum:
                                  - enum
                              value:
                                type: object
                                properties:
                                  w:
                                    type: array
                                    description: |-
                                      Value | Description
                                      -|-
                                      START | 세탁 시작
                                      STOP | 세탁 정지
                                      POWER_OFF | 전원 OFF
                                      WAKE_UP | Wake up
                                    items:
                                      type: string
                                      enum:
                                        - START
                                        - STOP
                                        - POWER_OFF
                                        - WAKE_UP
                      remoteControlEnable:
                        type: object
                        description: 원격제어설정
                        properties:
                          remoteControlEnabled:
                            type: object
                            description: 원격 제어 설정 상태
                            properties:
                              mode:
                                type: array
                                items:
                                  type: string
                                  enum:
                                    - r
                              type:
                                type: string
                                enum:
                                  - boolean
                              value:
                                type: object
                                properties:
                                  r:
                                    type: array
                                    description: |-
                                      Value | Description
                                      -|-
                                      TRUE | 원격 제어 가능
                                      FALSE | 원격 제어 불가능
                                    items:
                                      type: boolean
                                      enum:
                                        - true
                                        - false
                      timer:
                        type: object
                        description: 타이머
                        properties:
                          remainHour:
                            type: object
                            description: 남은 시간(시)
                            properties:
                              mode:
                                type: array
                                items:
                                  type: string
                                  enum:
                                    - r
                              type:
                                type: string
                                enum:
                                  - range
                              value:
                                type: object
                                properties:
                                  r:
                                    type: object
                                    properties:
                                      max:
                                        type: integer
                                      min:
                                        type: integer
                                      step:
                                        type: integer
                                      except:
                                        type: array
                          remainMinute:
                            type: object
                            description: 남은 시간(분)
                            properties:
                              mode:
                                type: array
                                items:
                                  type: string
                                  enum:
                                    - r
                              type:
                                type: string
                                enum:
                                  - range
                              value:
                                type: object
                                properties:
                                  r:
                                    type: object
                                    properties:
                                      max:
                                        type: integer
                                      min:
                                        type: integer
                                      step:
                                        type: integer
                                      except:
                                        type: array
                          relativeHourToStart:
                            type: object
                            description: 세탁 시작 예약 시간(시)
                            properties:
                              mode:
                                type: array
                                items:
                                  type: string
                                  enum:
                                    - r
                                    - w
                              type:
                                type: string
                                enum:
                                  - range
                              value:
                                type: object
                                properties:
                                  r:
                                    type: object
                                    properties:
                                      max:
                                        type: integer
                                      min:
                                        type: integer
                                      step:
                                        type: integer
                                      except:
                                        type: array
                                  w:
                                    type: object
                                    properties:
                                      max:
                                        type: integer
                                      min:
                                        type: integer
                                      step:
                                        type: integer
                                      except:
                                        type: array
                          relativeMinuteToStart:
                            type: object
                            description: 세탁 시작 예약 시간(분)
                            properties:
                              mode:
                                type: array
                                items:
                                  type: string
                                  enum:
                                    - r
                              type:
                                type: string
                                enum:
                                  - range
                              value:
                                type: object
                                properties:
                                  r:
                                    type: object
                                    properties:
                                      max:
                                        type: integer
                                      min:
                                        type: integer
                                      step:
                                        type: integer
                                      except:
                                        type: array
                          relativeHourToStop:
                            type: object
                            description: 세탁 종료 예약 시간(시)
                            properties:
                              mode:
                                type: array
                                items:
                                  type: string
                                  enum:
                                    - r
                                    - w
                              type:
                                type: string
                                enum:
                                  - range
                              value:
                                type: object
                                properties:
                                  r:
                                    type: object
                                    properties:
                                      max:
                                        type: integer
                                      min:
                                        type: integer
                                      step:
                                        type: integer
                                      except:
                                        type: array
                                  w:
                                    type: object
                                    properties:
                                      max:
                                        type: integer
                                      min:
                                        type: integer
                                      step:
                                        type: integer
                                      except:
                                        type: array
                          relativeMinuteToStop:
                            type: object
                            description: 세탁 종료 예약 시간(분)
                            properties:
                              mode:
                                type: array
                                items:
                                  type: string
                                  enum:
                                    - r
                              type:
                                type: string
                                enum:
                                  - range
                              value:
                                type: object
                                properties:
                                  r:
                                    type: object
                                    properties:
                                      max:
                                        type: integer
                                      min:
                                        type: integer
                                      step:
                                        type: integer
                                      except:
                                        type: array
                          totalHour:
                            type: object
                            description: 세탁 전체 시간(시)
                            properties:
                              mode:
                                type: array
                                items:
                                  type: string
                                  enum:
                                    - r
                              type:
                                type: string
                                enum:
                                  - range
                              value:
                                type: object
                                properties:
                                  r:
                                    type: object
                                    properties:
                                      max:
                                        type: integer
                                      min:
                                        type: integer
                                      step:
                                        type: integer
                                      except:
                                        type: array
                          totalMinute:
                            type: object
                            description: 세탁 전체 시간(분)
                            properties:
                              mode:
                                type: array
                                items:
                                  type: string
                                  enum:
                                    - r
                              type:
                                type: string
                                enum:
                                  - range
                              value:
                                type: object
                                properties:
                                  r:
                                    type: object
                                    properties:
                                      max:
                                        type: integer
                                      min:
                                        type: integer
                                      step:
                                        type: integer
                                      except:
                                        type: array
                      detergent:
                        type: object
                        description: 세제 설정
                        properties:
                          detergentSetting:
                            type: string
                            description: |-
                              Value | Description
                              -|-
                              AUTO | 자동 설정 기기
                              NORMAL | 일반 기기
                            enum:
                              - AUTO
                              - NORMAL
                      location:
                        type: object
                        description: 위치
                        properties:
                          locationName:
                            type: string
                            description: |-
                              Value | Description
                              -|-
                              MAIN | main washer
                              MINI | mini washer
                            enum:
                              - MAIN
                              - MINI
                notification:
                  type: object
                  properties:
                    push:
                      type: array
                      minItems: 1
                      description: |-
                        Push Code | Description
                        -|-
                        WASHING_IS_COMPLETE | 세탁이 완료되었습니다.
                        ERROR_DURING_WASHING | 세탁 중 오류가 발생하였습니다.
                      items:
                        type: string
                        enum:
                          - WASHING_IS_COMPLETE
                          - ERROR_DURING_WASHING
                error:
                  type: array
                  description: |-
                    Push Code | Description
                    -|-
                    WATER_SUPPLY_ERROR | 급수 에러
                    WATER_DRAIN_ERROR | 배수 에러
                    OUT_OF_BALANCE_ERROR | 탈수 에러
                    LOCKED_MOTOR_ERROR | 드라이버 모터 에러
                    CHILD_LOCK_ACTIVE_ERROR | childlock 에러
                    TIME_TO_RUN_THE_TUB_CLEAN_CYCLE_ERROR | 통세척 에러
                    UNBALANCED_LOAD_ERROR | 수평 에러
                    DOOR_OPEN_ERROR | 문 열림 에러
                    UNABLE_TO_LOCK_ERROR | 잠김 불가 에러
                    OVERFILL_ERROR | 물 수위 에러
                    WATER_LEVEL_SENSOR_ERROR | 물 수위 센서 에러
                    POWER_FAIL_ERROR | 전력 에러
                    TEMPERATURE_SENSOR_ERROR | 온도 센서 에러
                    TIMEOUT_ERROR | 타임아웃 에러
                    PART_MALFUNCTION_ERROR | 기기 부품 에러
                  items:
                    type: string
                    enum:
                      - WATER_SUPPLY_ERROR
                      - WATER_DRAIN_ERROR
                      - OUT_OF_BALANCE_ERROR
                      - LOCKED_MOTOR_ERROR
                      - CHILD_LOCK_ACTIVE_ERROR
                      - TIME_TO_RUN_THE_TUB_CLEAN_CYCLE_ERROR
                      - UNBALANCED_LOAD_ERROR
                      - DOOR_OPEN_ERROR
                      - UNABLE_TO_LOCK_ERROR
                      - OVERFILL_ERROR
                      - WATER_LEVEL_SENSOR_ERROR
                      - POWER_FAIL_ERROR
                      - TEMPERATURE_SENSOR_ERROR
                      - TIMEOUT_ERROR
                      - PART_MALFUNCTION_ERROR
            dryer:
              type: object
              properties:
                property:
                  type: object
                  properties:
                    runState:
                      type: object
                      description: 상태
                      properties:
                        currentState:
                          type: object
                          description: 현재 상태
                          properties:
                            mode:
                              type: array
                              items:
                                type: string
                                enum:
                                  - r
                            type:
                              type: string
                              enum:
                                - enum
                            value:
                              type: object
                              properties:
                                r:
                                  type: array
                                  description: |-
                                    Value | Description
                                    -|-
                                    POWER_OFF | 제품 OFF
                                    INITIAL | 대기 중 상태
                                    PAUSE | 일시정지
                                    DETECTING | 옷감량확인
                                    COOLING | 쿨링
                                    RUNNING | 실행중
                                    WRINKLE_CARE | 주름방지실행중
                                    END | 건조완료상태
                                    RESERVED | 예약상태
                                    ERROR | 에러상태
                                    SLEEP | Sleep 상태
                                  items:
                                    type: string
                                    enum:
                                      - POWER_OFF
                                      - INITIAL
                                      - PAUSE
                                      - DETECTING
                                      - COOLING
                                      - RUNNING
                                      - WRINKLE_CARE
                                      - END
                                      - RESERVED
                                      - ERROR
                                      - SLEEP
                    operation:
                      type: object
                      description: 동작
                      properties:
                        dryerOperationMode:
                          type: object
                          description: 건조 동작
                          properties:
                            mode:
                              type: array
                              items:
                                type: string
                                enum:
                                  - w
                            type:
                              type: string
                              enum:
                                - enum
                            value:
                              type: object
                              properties:
                                w:
                                  type: array
                                  description: |-
                                    Value | Description
                                    -|-
                                    START | 건조 시작
                                    STOP | 건조 정지
                                    POWER_OFF | 전원 OFF
                                    WAKE_UP | Wake up
                                  items:
                                    type: string
                                    enum:
                                      - START
                                      - STOP
                                      - POWER_OFF
                                      - WAKE_UP
                    remoteControlEnable:
                      type: object
                      description: 원격제어설정
                      properties:
                        remoteControlEnabled:
                          type: object
                          description: 원격 제어 설정 상태
                          properties:
                            mode:
                              type: array
                              items:
                                type: string
                                enum:
                                  - r
                            type:
                              type: string
                              enum:
                                - boolean
                            value:
                              type: object
                              properties:
                                r:
                                  type: array
                                  description: |-
                                    Value | Description
                                    -|-
                                    TRUE | 원격 제어 가능
                                    FALSE | 원격 제어 불가능
                                  items:
                                    type: boolean
                                    enum:
                                      - true
                                      - false
                    timer:
                      type: object
                      description: 타이머
                      properties:
                        remainHour:
                          type: object
                          description: 남은 시간(시)
                          properties:
                            mode:
                              type: array
                              items:
                                type: string
                                enum:
                                  - r
                            type:
                              type: string
                              enum:
                                - number
                        remainMinute:
                          type: object
                          description: 남은 시간(분)
                          properties:
                            mode:
                              type: array
                              items:
                                type: string
                                enum:
                                  - r
                            type:
                              type: string
                              enum:
                                - number
                        relativeHourToStart:
                          type: object
                          description: 건조 시작 예약 시간(시)
                          properties:
                            mode:
                              type: array
                              items:
                                type: string
                                enum:
                                  - r
                                  - w
                            type:
                              type: string
                              enum:
                                - range
                            value:
                              type: object
                              properties:
                                r:
                                  type: object
                                  properties:
                                    max:
                                      type: integer
                                    min:
                                      type: integer
                                w:
                                  type: object
                                  properties:
                                    max:
                                      type: integer
                                    min:
                                      type: integer
                        relativeMinuteToStart:
                          type: object
                          description: 건조 시작 예약 시간(분)
                          properties:
                            mode:
                              type: array
                              items:
                                type: string
                                enum:
                                  - r
                            type:
                              type: string
                              enum:
                                - number
                        relativeHourToStop:
                          type: object
                          description: 건조 종료 예약 시간(시)
                          properties:
                            mode:
                              type: array
                              items:
                                type: string
                                enum:
                                  - r
                                  - w
                            type:
                              type: string
                              enum:
                                - range
                            value:
                              type: object
                              properties:
                                r:
                                  type: object
                                  properties:
                                    max:
                                      type: integer
                                    min:
                                      type: integer
                                w:
                                  type: object
                                  properties:
                                    max:
                                      type: integer
                                    min:
                                      type: integer
                        relativeMinuteToStop:
                          type: object
                          description: 건조 종료 예약 시간(분)
                          properties:
                            mode:
                              type: array
                              items:
                                type: string
                                enum:
                                  - r
                            type:
                              type: string
                              enum:
                                - number
                        totalHour:
                          type: object
                          description: 건조 전체 시간(시)
                          properties:
                            mode:
                              type: array
                              items:
                                type: string
                                enum:
                                  - r
                            type:
                              type: string
                              enum:
                                - number
                        totalMinute:
                          type: object
                          description: 건조 전체 시간(분)
                          properties:
                            mode:
                              type: array
                              items:
                                type: string
                                enum:
                                  - r
                            type:
                              type: string
                              enum:
                                - number
                notification:
                  type: object
                  properties:
                    push:
                      type: array
                      description: |-
                        Push Code | Description
                        -|-
                        DRYING_FAILED | 건조를 실패하였습니다.
                        DRYING_IS_COMPLETE | 건조가 완료되었습니다.
                      items:
                        type: string
                        enum:
                          - DRYING_FAILED
                          - DRYING_IS_COMPLETE
                error:
                  type: array
                  description: |-
                    Push Code | Description
                    -|-
                    TEMPERATURE_SENSOR_ERROR | 온도 센서 에러
                    COMPRESSOR_ERROR | 컴프레서 에러
                    DRAINMOTOR_ERROR | 펌프 에러
                    EMPTY_WATHER_ALERT_ERROR | 물 비우기 알림 에러
                    HIGH_TEMPERATURE_DETECTION_ERROR | 고온감지 에러
                    MOTOR_LOCK_ERROR | 모터 멈춤 에러
                    DOOR_SENSOR_ERROR | 문 센서 에러
                    DOOR_OPEN_ERROR | 문 열림 에러
                    DOOR_LOCK_ERROR | 문 잠김 에러
                    NO_FILTER_ERROR | 필터 없음 에러
                    FILTER_CLOGGING_ERROR | 필터 막힘 에러
                    HIGH_POWER_SUPPLY_ERROR | 비 정상 전압 인가 에러
                    POWER_CODE_CONNECTION_ERROR | 전원선 연결 이상 에러
                    FAN_MOTOR_ERROR | 팬 모터 에러
                  items:
                    type: string
                    enum:
                      - TEMPERATURE_SENSOR_ERROR
                      - COMPRESSOR_ERROR
                      - DRAINMOTOR_ERROR
                      - EMPTY_WATER_ALERT_ERROR
                      - HIGH_TEMPERATURE_DETECTION_ERROR
                      - MOTOR_LOCK_ERROR
                      - DOOR_SENSOR_ERROR
                      - DOOR_OPEN_ERROR
                      - DOOR_LOCK_ERROR
                      - NO_FILTER_ERROR
                      - FILTER_CLOGGING_ERROR
                      - HIGH_POWER_SUPPLY_ERROR
                      - POWER_CODE_CONNECTION_ERROR
                      - FAN_MOTOR_ERROR
        washtower-object:
          type: object
          title: Washtower_Dryer
          required:
            - property
          properties:
            washer:
              type: object
              properties:
                runState:
                  type: object
                  description: 상태
                  properties:
                    currentState:
                      type: string
                      description: 현재 상태
                      enum:
                        - POWER_OFF
                        - INITIAL
                        - PAUSE
                        - DETECTING
                        - SOAKING
                        - RUNNING
                        - RINSING
                        - SPINNING
                        - END
                        - RESERVED
                        - FIRMWARE
                        - DRYING
                        - COOL_DOWN
                        - RINSE_HOLD
                        - REFRESHING
                        - STEAM_SOFTENING
                        - ERROR
                        - SMART_GRID_RUN
                        - ADD_DRAIN
                        - DETERGENT_AMOUNT
                        - PREWASH
                        - SHOES_MODULE
                        - PROOFING
                        - DISPENSING
                        - SOFTENING
                        - CHECKING_TURBIDITY
                        - CHANGE_CONDITION
                        - DISPLAY_LOADSIZE
                        - FROZEN_PREVENT_INITIAL
                        - FROZEN_PREVENT_RUNNING
                        - FROZEN_PREVENT_PAUSE
                        - SLEEP
                operation:
                  type: object
                  description: 동작
                  properties:
                    washerOperationMode:
                      type: string
                      description: 세탁 동작
                      enum:
                        - START
                        - STOP
                        - POWER_OFF
                        - WAKE_UP
                remoteControlEnable:
                  type: object
                  description: 원격제어설정
                  properties:
                    remoteControlEnabled:
                      type: boolean
                      description: 원격 제어 설정 상태
                      enum:
                        - true
                        - false
                timer:
                  type: object
                  description: 타이머
                  properties:
                    remainHour:
                      type: integer
                      description: 남은 시간(시)
                    remainMinute:
                      type: integer
                      description: 남은 시간(분)
                    relativeHourToStart:
                      type: integer
                      description: 세탁 시작 예약 시간(시)
                    relativeMinuteToStart:
                      type: integer
                      description: 세탁 시작 예약 시간(분)
                    relativeHourToStop:
                      type: integer
                      description: 세탁 종료 예약 시간(시)
                    relativeMinuteToStop:
                      type: integer
                      description: 세탁 종료 예약 시간(분)
                    totalHour:
                      type: integer
                      description: 세탁 전체 시간(시)
                    totalMinute:
                      type: integer
                      description: 세탁 전체 시간(분)
                detergent:
                  type: object
                  description: 세제 설정
                  properties:
                    detergentSetting:
                      type: string
                      description: 세제 설정 모드
                      enum:
                        - AUTO
                        - NORMAL
                location:
                  type: object
                  description: 위치
                  properties:
                    locationName:
                      type: string
                      description: 위치 이름
                      enum:
                        - MAIN
                        - MINI
                error:
                  type: string
                  description: Error Message
                  enum:
                    - WATER_SUPPLY_ERROR
                    - WATER_DRAIN_ERROR
                    - OUT_OF_BALANCE_ERROR
                    - LOCKED_MOTOR_ERROR
                    - CHILD_LOCK_ACTIVE_ERROR
                    - TIME_TO_RUN_THE_TUB_CLEAN_CYCLE_ERROR
                    - UNBALANCED_LOAD_ERROR
                    - DOOR_OPEN_ERROR
                    - UNABLE_TO_LOCK_ERROR
                    - OVERFILL_ERROR
                    - WATER_LEVEL_SENSOR_ERROR
                    - POWER_FAIL_ERROR
                    - TEMPERATURE_SENSOR_ERROR
                    - TIMEOUT_ERROR
                    - PART_MALFUNCTION_ERROR
                notification:
                  type: string
                  description: Error Message
                  enum:
                    - WASHING_IS_COMPLETE
                    - ERROR_DURING_WASHING
            dryer:
              type: object
              properties:
                runState:
                  type: object
                  description: 상태
                  properties:
                    currentState:
                      type: string
                      description: 현재 상태
                      enum:
                        - POWER_OFF
                        - INITIAL
                        - PAUSE
                        - DETECTING
                        - COOLING
                        - RUNNING
                        - WRINKLE_CARE
                        - END
                        - RESERVED
                        - ERROR
                        - SLEEP
                operation:
                  type: object
                  description: 동작
                  properties:
                    dryerOperationMode:
                      type: string
                      description: 건조 동작
                      enum:
                        - START
                        - STOP
                        - POWER_OFF
                        - WAKE_UP
                remoteControlEnable:
                  type: object
                  description: 원격제어설정
                  properties:
                    remoteControlEnabled:
                      type: boolean
                      description: 원격 제어 설정 상태
                      enum:
                        - true
                        - false
                timer:
                  type: object
                  description: 타이머
                  properties:
                    remainHour:
                      type: integer
                      description: 남은 시간(시)
                    remainMinute:
                      type: integer
                      description: 남은 시간(분)
                    relativeHourToStart:
                      type: integer
                      description: 건조 시작 예약 시간(시)
                    relativeMinuteToStart:
                      type: integer
                      description: 건조 시작 예약 시간(분)
                    relativeHourToStop:
                      type: integer
                      description: 건조 종료 예약 시간(시)
                    relativeMinuteToStop:
                      type: integer
                      description: 건조 종료 예약 시간(분)
                    totalHour:
                      type: integer
                      description: 건조 전체 시간(시)
                    totalMinute:
                      type: integer
                      description: 건조 전체 시간(분)
                notification:
                  type: object
                  description: Push Message
                  enum:
                    - DRYING_FAILED
                    - DRYING_IS_COMPLETE
                error:
                  type: object
                  description: Error Message
                  enum:
                    - TEMPERATURE_SENSOR_ERROR
                    - COMPRESSOR_ERROR
                    - DRAINMOTOR_ERROR
                    - EMPTY_WATER_ALERT_ERROR
                    - HIGH_TEMPERATURE_DETECTION_ERROR
                    - MOTOR_LOCK_ERROR
                    - DOOR_SENSOR_ERROR
                    - DOOR_OPEN_ERROR
                    - DOOR_LOCK_ERROR
                    - NO_FILTER_ERROR
                    - FILTER_CLOGGING_ERROR
                    - HIGH_POWER_SUPPLY_ERROR
                    - POWER_CODE_CONNECTION_ERROR
                    - FAN_MOTOR_ERROR
        cooktop-profile:
          type: object
          title: Cooktop
          properties:
            property:
              type: array
              items:
                type: object
                properties:
                  cookingZone:
                    type: object
                    description: 상태
                    properties:
                      currentState:
                        type: object
                        description: 제품 상태
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  INITIAL | 대기중
                                  COOK | 요리중
                                  PAUSE | 멈춤 
                                  LOCK | 잠금
                                items:
                                  type: string
                                  enum:
                                    - INITIAL
                                    - COOK
                                    - PAUSE
                                    - LOCK
                  remoteControlEnable:
                    type: object
                    description: 원격제어설정
                    properties:
                      remoteControlEnabled:
                        type: object
                        description: 원격 제어 설정 상태
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - boolean
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  TRUE | 원격 제어 가능
                                  FALSE | 원격 제어 불가능
                                items:
                                  type: boolean
                                  enum:
                                    - true
                                    - false
                  timer:
                    type: object
                    description: 타이머
                    properties:
                      remainHour:
                        type: object
                        description: 남은 시간(시)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                              w:
                                type: object
                                description: WBEF3MT, WBEI3GT, WBEY3GWT 한정
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                      remainMinute:
                        type: object
                        description: 남은 시간(분)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                              w:
                                type: object
                                description: WBEF3MT, WBEI3GT, WBEY3GWT 한정
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                  power:
                    type: object
                    description: 화력
                    properties:
                      powerLevel:
                        type: object
                        description: 화구 레벨
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                              w:
                                type: object
                                description: WBEF3MT, WBEI3GT, WBEY3GWT 한정
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                  location:
                    type: object
                    description: 위치
                    properties:
                      locationName:
                        type: string
                        description: 위치 이름
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  CENTER | 중앙
                                  CENTER_FRONT | 중앙 앞
                                  CENTER_REAR | 중앙 뒤
                                  LEFT_FRONT | 왼쪽 앞
                                  LEFT_REAR | 왼쪽 뒤
                                  RIGHT_FRONT | 오른쪽 앞
                                  RIGHT_REAR | 오른쪽 뒤
                                  BURNER_1 | 버너 1
                                  BURNER_2 | 버너 2
                                  BURNER_3 | 버너 3
                                  BURNER_4 | 버너 4
                                  BURNER_5 | 버너 5
                                  BURNER_6 | 버너 6
                                  BURNER_7 | 버너 7
                                  BURNER_8 | 버너 8
                                  INDUCTION_1 | 인덕션 1
                                  INDUCTION_2 | 인덕션 2
                                  SOUSVIDE_1 | 수비드 1
                                items:
                                  type: string
                                  enum:
                                    - CENTER
                                    - CENTER_FRONT
                                    - CENTER_REAR
                                    - LEFT_FRONT
                                    - LEFT_REAR
                                    - RIGHT_FRONT
                                    - RIGHT_REAR
                                    - BURNER_1
                                    - BURNER_2
                                    - BURNER_3
                                    - BURNER_4
                                    - BURNER_5
                                    - BURNER_6
                                    - BURNER_7
                                    - BURNER_8
                                    - INDUCTION_1
                                    - INDUCTION_2
                                    - SOUSVIDE_1
            extensionProperty:
              type: object
              properties:
                operation:
                  type: object
                  description: 동작
                  properties:
                    operationMode:
                      type: object
                      description: 동작 (WBEF3MT, WBEI3GT, WBEY3GWT 한정)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_OFF | 전체 OFF
        cooktop-object:
          type: array
          title: Cooktop
          items:
            type: object
            properties:
              cookingZone:
                type: object
                description: 상태
                properties:
                  currentState:
                    type: string
                    description: 제품 상태
                    enum:
                      - INITIAL
                      - COOK
                      - PAUSE
                      - LOCK
              remoteControlEnable:
                type: boolean
                description: 원격제어설정
                enum:
                  - true
                  - false
              timer:
                type: object
                description: 타이머
                properties:
                  remainHour:
                    type: integer
                    description: 남은 시간(시)
                  remainMinute:
                    type: integer
                    description: 남은 시간(분)
              power:
                type: object
                description: 화력
                properties:
                  powerLevel:
                    type: integer
                    description: 화구 레벨
              location:
                type: object
                description: 위치
                properties:
                  locationName:
                    type: string
                    description: 위치 이름
        hood-profile:
          type: object
          title: Hood
          properties:
            property:
              type: object
              properties:
                ventilation:
                  type: object
                  description: 환풍
                  properties:
                    fanSpeed:
                      type: object
                      description: 환풍 세기
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                            w:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                lamp:
                  type: object
                  description: 램프
                  properties:
                    lampBrightness:
                      type: object
                      description: 램프 밝기
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                            w:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                operation:
                  type: object
                  description: 동작
                  properties:
                    hoodOperationMode:
                      type: object
                      description: 후드 동작
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_ON | 후드 가동 중
                                POWER_OFF | 후드 가동 중지
                              items:
                                type: string
                                enum:
                                  - POWER_ON
                                  - POWER_OFF
                timer:
                  type: object
                  description: 타이머
                  properties:
                    remainMinute:
                      type: object
                      description: 남은 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                    remainSecond:
                      type: object
                      description: 남은 시간(초)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
        hood-object:
          type: object
          title: Hood
          properties:
            ventilation:
              type: object
              description: 환풍
              properties:
                fanSpeed:
                  type: integer
                  description: 환풍 세기
            lamp:
              type: object
              description: 램프
              properties:
                lampBrightness:
                  type: integer
                  description: 램프 밝기
            operation:
              type: object
              description: 동작
              properties:
                hoodOperationMode:
                  type: string
                  description: 후드 동작
                  enum:
                    - POWER_ON
                    - POWER_OFF
            timer:
              type: object
              description: 타이머
              properties:
                remainMinute:
                  type: integer
                  description: 남은 시간(분)
                remainSecond:
                  type: integer
                  description: 남은 시간(초)
        microwave_oven-profile:
          type: object
          title: Microwave_Oven
          properties:
            property:
              type: object
              properties:
                runState:
                  type: object
                  description: 상태
                  properties:
                    currentState:
                      type: object
                      description: 현재 상태
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                INITIAL | 대기 중
                                PREHEAT | 예열 중
                                COOK | 요리 중
                                PAUSE | 멈춤
                                COOK_COMPLETE | 요리 완료
                                PREHEAT_COMPLETE | 예열 완료
                                OVEN_SETTING | 쿡탑 연결
                              items:
                                type: string
                                enum:
                                  - INITIAL
                                  - PREHEAT
                                  - COOK
                                  - PAUSE
                                  - COOK_COMPLETE
                                  - PREHEAT_COMPLETE
                                  - OVEN_SETTING
                ventilation:
                  type: object
                  description: 환풍
                  properties:
                    fanSpeed:
                      type: object
                      description: 환풍 세기
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                            w:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                lamp:
                  type: object
                  description: 램프
                  properties:
                    lampBrightness:
                      type: object
                      description: 램프 밝기
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                            w:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                timer:
                  type: object
                  description: 타이머
                  properties:
                    remainMinute:
                      type: object
                      description: 남은 시간(분)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
                    remainSecond:
                      type: object
                      description: 남은 시간(초)
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - range
                        value:
                          type: object
                          properties:
                            r:
                              type: object
                              properties:
                                max:
                                  type: integer
                                min:
                                  type: integer
                                step:
                                  type: integer
            notification:
              type: object
              properties:
                push:
                  type: array
                  minItems: 1
                  description: |-
                    Push Code | Description
                    -|-
                    PREHEATING_IS_COMPLETE | 예열이 완료되었습니다.
                    COOKING_IS_COMPLETE | 요리가 완료되었습니다.
                    TIMER_IS_COMPLETE | -
                  items:
                    type: string
                    enum:
                      - PREHEATING_IS_COMPLETE
                      - COOKING_IS_COMPLETE
                      - TIMER_IS_COMPLETE
        microwave_oven-object:
          type: object
          title: Microwave_Oven
          properties:
            property:
              type: object
              properties:
                runState:
                  type: object
                  description: 상태
                  properties:
                    currentState:
                      type: string
                      description: 현재 상태
                      enum:
                        - INITIAL
                        - PREHEAT
                        - COOK
                        - PAUSE
                        - COOK_COMPLETE
                        - PREHEAT_COMPLETE
                        - OVEN_SETTING
                ventilation:
                  type: object
                  description: 환풍
                  properties:
                    fanSpeed:
                      type: integer
                      description: 환풍 세기
                lamp:
                  type: object
                  description: 램프
                  properties:
                    lampBrightness:
                      type: integer
                      description: 램프 밝기
                timer:
                  type: object
                  description: 타이머
                  properties:
                    remainMinute:
                      type: integer
                      description: 남은 시간(분)
                    remainSecond:
                      type: integer
                      description: 남은 시간(초)
            notification:
              type: string
              description: Push Message
              enum:
                - PREHEATING_IS_COMPLETE
                - COOKING_IS_COMPLETE
                - TIMER_IS_COMPLETE
        system_boiler-profile:
          type: object
          title: System_Boiler
          properties:
            property:
              type: object
              properties:
                boilerJobMode:
                  type: object
                  description: 모드
                  properties:
                    currentJobMode:
                      type: object
                      description: 운전 모드
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                COOL | 냉방 운전
                                AUTO | 자동 운전
                                HEAT | 난방
                              items:
                                type: string
                                enum:
                                  - COOL
                                  - AUTO
                                  - HEAT
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                COOL | 냉방 운전
                                AUTO | 자동 운전
                                HEAT | 난방
                              items:
                                type: string
                                enum:
                                  - COOL
                                  - AUTO
                                  - HEAT
                operation:
                  type: object
                  description: 동작
                  properties:
                    boilerOperationMode:
                      type: object
                      description: 본체 동작
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_ON | 보일러 가동 시작
                                POWER_OFF | 보일러 가동 끄기
                              items:
                                type: string
                                enum:
                                  - POWER_ON
                                  - POWER_OFF
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_ON | 보일러 가동 시작
                                POWER_OFF | 보일러 가동 끄기
                              items:
                                type: string
                                enum:
                                  - POWER_ON
                                  - POWER_OFF
                    hotWaterMode:
                      type: object
                      description: 본체 동작
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                ON | 온수 가동 시작
                                OFF | 온수 가동 끄기
                              items:
                                type: string
                                enum:
                                  - 'ON'
                                  - 'OFF'
                temperature:
                  type: object
                  description: 온도
                  properties:
                    currentTemperature:
                      type: object
                      description: 현재 온도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    targetTemperature:
                      type: object
                      description: 희망 온도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    heatTargetTemperature:
                      type: object
                      description: 난방 희망 온도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    coolTargetTemperature:
                      type: object
                      description: 난방 희망 온도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    heatMaxTemperature:
                      type: object
                      description: 난방 최대 온도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    heatMinTemperature:
                      type: object
                      description: 난방 최소 온도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    coolMaxTemperature:
                      type: object
                      description: 냉방 최대 온도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    coolMinTemperature:
                      type: object
                      description: 냉방 최소 온도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    unit:
                      type: object
                      description: 온도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                C | 섭씨
                              items:
                                type: string
                                enum:
                                  - C
        system_boiler-object:
          type: object
          title: System_Boiler
          properties:
            boilerJobMode:
              type: object
              description: 모드
              properties:
                currentJobMode:
                  type: string
                  description: 운전 모드
                  enum:
                    - COOL
                    - AUTO
                    - HEAT
            operation:
              type: object
              description: 동작
              properties:
                boilerOperationMode:
                  type: string
                  description: 본체 동작
                  enum:
                    - POWER_ON
                    - POWER_OFF
                hotWaterMode:
                  type: string
                  description: 본체 동작
                  enum:
                    - 'ON'
                    - 'OFF'
            temperature:
              type: object
              description: 온도
              properties:
                currentTemperature:
                  type: number
                  description: 현재 온도
                targetTemperature:
                  type: number
                  description: 희망 온도
                heatTargetTemperature:
                  type: number
                  description: 난방 희망 온도
                coolTargetTemperature:
                  type: number
                  description: 난방 희망 온도
                heatMaxTemperature:
                  type: number
                  description: 난방 최대 온도
                heatMinTemperature:
                  type: number
                  description: 난방 최소 온도
                coolMaxTemperature:
                  type: number
                  description: 냉방 최대 온도
                coolMinTemperature:
                  type: number
                  description: 냉방 최소 온도
            unit:
              type: string
              description: 단위
              enum:
                - C
        stick_cleaner-profile:
          type: object
          title: Stick_Cleaner
          properties:
            property:
              type: object
              properties:
                runState:
                  type: object
                  description: 상태
                  properties:
                    currentState:
                      type: object
                      description: 현재 상태
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                CHARGING | 충전 중
                                CHARGING_COMPLETE | 충전 완료
                                STANDBY | 대기중 상태
                                WORKING | 청소 중
                              items:
                                type: string
                                enum:
                                  - CHARGING
                                  - CHARGING_COMPLETE
                                  - STANDBY
                                  - WORKING
                stickCleanerJobMode:
                  type: object
                  description: 모드
                  properties:
                    currentJobMode:
                      type: object
                      description: 청소 모드
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                OFF | 꺼짐
                                NORMAL | 표준
                                HIGH | 강
                                TURBO | 터보
                                MOP | 물걸레
                                AUTO | 자동/저전력(ECO)
                              items:
                                type: string
                                enum:
                                  - 'OFF'
                                  - NORMAL
                                  - HIGH
                                  - TURBO
                                  - MOP
                                  - AUTO
                battery:
                  type: object
                  description: 배터리
                  properties:
                    level:
                      type: object
                      description: 베터리 레벨
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                HIGH | 많음
                                MID | 보통 
                                LOW | 적음
                                WARNING | 경고
                              items:
                                type: string
                                enum:
                                  - HIGH
                                  - MID
                                  - LOW
                                  - WARNING
                    percent:
                      type: object
                      description: 배터리 퍼센트
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
            notification:
              type: object
              properties:
                push:
                  type: array
                  minItems: 1
                  description: |-
                    Push Code | Description
                    -|-
                    CHARGING_IS_COMPLETE | 충전이 완료되었습니다.
                    TIME_TO_CLEAN_FILTER | 필터 청소가 필요합니다.
                  items:
                    type: string
                    enum:
                      - CHARGING_IS_COMPLETE
                      - TIME_TO_CLEAN_FILTER
        stick_cleaner-object:
          type: object
          title: Stick_Cleaner
          properties:
            runState:
              type: object
              description: 상태
              properties:
                currentState:
                  type: string
                  description: 현재 상태
                  enum:
                    - CHARGING
                    - CHARGING_COMPLETE
                    - STANDBY
                    - WORKING
            stickCleanerJobMode:
              type: object
              description: 모드
              properties:
                currentJobMode:
                  type: string
                  description: 청소 모드
                  enum:
                    - 'OFF'
                    - NORMAL
                    - HIGH
                    - TURBO
                    - MOP
                    - AUTO
            battery:
              type: object
              description: 배터리
              properties:
                level:
                  type: string
                  description: 베터리 레벨
                  enum:
                    - HIGH
                    - MID
                    - LOW
                    - WARNING
                percent:
                  type: number
                  description: 배터리 퍼센트
            notification:
              type: string
              description: Push Message
              enum:
                - CHARGING_IS_COMPLETE
                - TIME_TO_CLEAN_FILTER
        water_heater-profile:
          type: object
          title: Water_Heater
          properties:
            property:
              type: object
              properties:
                waterHeaterJobMode:
                  type: object
                  description: 모드
                  properties:
                    currentJobMode:
                      type: object
                      description: 운전 모드
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                HEAT_PUMP | 절전
                                AUTO | 자동
                                TURBO | 터보
                                VACATION | 휴가
                              items:
                                type: string
                                enum:
                                  - HEAT_PUMP
                                  - AUTO
                                  - TURBO
                                  - VACATION
                            w:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                HEAT_PUMP | 절전
                                AUTO | 자동
                                TURBO | 터보
                                VACATION | 휴가
                              items:
                                type: string
                                enum:
                                  - HEAT_PUMP
                                  - AUTO
                                  - TURBO
                                  - VACATION
                operation:
                  type: object
                  description: 동작
                  properties:
                    waterHeaterOperationMode:
                      type: object
                      description: 본체 동작
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - enum
                        value:
                          type: object
                          properties:
                            r:
                              type: array
                              description: |-
                                Value | Description
                                -|-
                                POWER_ON | 온수기 on
                                POWER_OFF | 온수기 off
                              items:
                                type: string
                                enum:
                                  - POWER_ON
                                  - POWER_OFF
                temperature:
                  type: object
                  description: 온도
                  properties:
                    currentTemperature:
                      type: object
                      description: 현재 온도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                        type:
                          type: string
                          enum:
                            - number
                    targetTemperature:
                      type: object
                      description: 설정 온도
                      properties:
                        mode:
                          type: array
                          items:
                            type: string
                            enum:
                              - r
                              - w
                        type:
                          type: string
                          enum:
                            - number
        water_heater-object:
          type: object
          title: Water_Heater
          properties:
            waterHeaterJobMode:
              type: object
              description: 모드
              properties:
                currentJobMode:
                  type: string
                  description: 운전 모드
                  enum:
                    - HEAT_PUMP
                    - AUTO
                    - TURBO
                    - VACATION
            operation:
              type: object
              description: 동작
              properties:
                waterHeaterOperationMode:
                  type: string
                  description: 본체 동작
                  enum:
                    - POWER_ON
                    - POWER_OFF
            temperature:
              type: object
              description: 온도
              properties:
                currentTemperature:
                  type: number
                  description: 현재 온도
                targetTemperature:
                  type: number
                  description: 설정 온도
        main_washcombo-profile:
          type: object
          title: Main_Washcombo
          properties:
            property:
              type: array
              items:
                type: object
                properties:
                  runState:
                    type: object
                    description: 상태
                    properties:
                      currentState:
                        type: object
                        description: 현재 상태
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: "Value | Description\n-|-\nPOWER_OFF | 제품 OFF\nINITIAL | 대기 중 상태\nPAUSE | 일시정지\nDETECTING | 옷감량확인\nSOAKING | 불림 상태\nRUNNING\t|\t행정중\nRINSING\t|\t행굼 중\nSPINNING | 탈수중\nEND\t| 세탁완료상태\nRESERVED | 예약상태\nFIRMWARE | 펌웨어 업데이트 중\nDRYING | 건조 중\nCOOL_DOWN\t| 구김방지1\nRINSE_HOLD | 린스 후 일시정지 중\nREFRESHING | 구김방지2 FRESHCARE\nSTEAM_SOFTENING | 스팀소프트닝\nERROR\t| 에러상태\nSMART_GRID_RUN | Smart Grid 동작 상태\nADD_DRAIN\t| 배수 추가 상태\nDETERGENT_AMOUNT | 세제량 표시중\nPREWASH | 예비 세탁 동작 상태\nSHOES_MODULE | 슈즈 건조 동작 상태\nPROOFING | 발수처리 상태\nDISPENSING | 세제 자동 투입 중\nSOFTENING | 유연제량 확인\nCHECKING_TURBIDITY | 탁도감지 중(G+Best모델 AUTOWASH 코스 사용 시)\nCHANGE_CONDITION | 탁도감지 결과를 가지고 자동으로 옵션변경 후 Display\nDISPLAY_LOADSIZE | 옷감량 확인 결과 Display\nFROZEN_PREVENT_INITIAL | 동결방지모드 대기상태\nFROZEN_PREVENT_RUNNING | 동결방지모드 진행상태\nFROZEN_PREVENT_PAUSE | 동결방지모드 멈춤상태\nCOOLING | 쿨링\nSLEEP | Sleep 상태"
                                items:
                                  type: string
                                  enum:
                                    - POWER_OFF
                                    - INITIAL
                                    - PAUSE
                                    - DETECTING
                                    - SOAKING
                                    - RUNNING
                                    - RINSING
                                    - SPINNING
                                    - END
                                    - RESERVED
                                    - FIRMWARE
                                    - DRYING
                                    - COOL_DOWN
                                    - RINSE_HOLD
                                    - REFRESHING
                                    - STEAM_SOFTENING
                                    - ERROR
                                    - SMART_GRID_RUN
                                    - ADD_DRAIN
                                    - DETERGENT_AMOUNT
                                    - PREWASH
                                    - SHOES_MODULE
                                    - PROOFING
                                    - DISPENSING
                                    - SOFTENING
                                    - CHECKING_TURBIDITY
                                    - CHANGE_CONDITION
                                    - DISPLAY_LOADSIZE
                                    - FROZEN_PREVENT_INITIAL
                                    - FROZEN_PREVENT_RUNNING
                                    - FROZEN_PREVENT_PAUSE
                                    - COOLING
                                    - SLEEP
                  operation:
                    type: object
                    description: 동작
                    properties:
                      washerOperationMode:
                        type: object
                        description: 세탁 동작
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  START | 세탁 시작
                                  STOP | 세탁 정지
                                  POWER_OFF | 전원 OFF
                                  WAKE_UP | Wake up
                                items:
                                  type: string
                                  enum:
                                    - START
                                    - STOP
                                    - POWER_OFF
                                    - WAKE_UP
                  mode:
                    type: object
                    description: 모드
                    properties:
                      washerOperationMode:
                        type: object
                        description: 세탁 모드
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  WASHING_DRYING | 세탁 건조 모드
                                  WASHING | 세탁 모드
                                  DRYING | 건조 모드
                                items:
                                  type: string
                                  enum:
                                    - WASHING_DRYING
                                    - WASHING
                                    - DRYING
                              w:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  WASHING_DRYING | 세탁 건조 모드
                                  WASHING | 세탁 모드
                                  DRYING | 건조 모드
                                items:
                                  type: string
                                  enum:
                                    - WASHING_DRYING
                                    - WASHING
                                    - DRYING
                  remoteControlEnable:
                    type: object
                    description: 원격제어설정
                    properties:
                      remoteControlEnabled:
                        type: object
                        description: 원격 제어 설정 상태
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - boolean
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  TRUE | 원격 제어 가능
                                  FALSE | 원격 제어 불가능
                                items:
                                  type: boolean
                                  enum:
                                    - true
                                    - false
                  timer:
                    type: object
                    description: 타이머
                    properties:
                      remainHour:
                        type: object
                        description: 남은 시간(시)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      remainMinute:
                        type: object
                        description: 남은 시간(분)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      relativeHourToStart:
                        type: object
                        description: 세탁 시작 예약 시간(시)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                              w:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      relativeMinuteToStart:
                        type: object
                        description: 세탁 시작 예약 시간(분)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      relativeHourToStop:
                        type: object
                        description: 세탁 종료 예약 시간(시)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                              w:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      relativeMinuteToStop:
                        type: object
                        description: 세탁 종료 예약 시간(분)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      totalHour:
                        type: object
                        description: 세탁 전체 시간(시)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      totalMinute:
                        type: object
                        description: 세탁 전체 시간(분)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                  detergent:
                    type: object
                    description: 세제 설정
                    properties:
                      detergentSetting:
                        type: string
                        description: |-
                          Value | Description
                          -|-
                          AUTO | 자동 설정 기기
                          NORMAL | 일반 기기
                        enum:
                          - AUTO
                          - NORMAL
                  location:
                    type: object
                    description: 위치
                    properties:
                      locationName:
                        type: string
                        description: |-
                          Value | Description
                          -|-
                          MAIN | main washer
                        enum:
                          - MAIN
            notification:
              type: object
              properties:
                push:
                  type: array
                  minItems: 1
                  description: |-
                    Push Code | Description
                    -|-
                    WASHING_IS_COMPLETE | 세탁이 완료되었습니다.
                    ERROR_DURING_WASHING | 세탁 중 오류가 발생하였습니다.
                    WASHING_IS_COMPLETE | 건조가 완료되었습니다.
                    DRYING_FAILED | 건조 중 오류가 발생하였습니다.
                  items:
                    type: string
                    enum:
                      - WASHING_IS_COMPLETE
                      - ERROR_DURING_WASHING
                      - WASHING_IS_COMPLETE
                      - DRYING_FAILED
            error:
              type: array
              description: "Push Code | Description\n-|-\nWATER_SUPPLY_ERROR | 급수 에러\nWATER_DRAIN_ERROR | 배수 에러\nOUT_OF_BALANCE_ERROR | 탈수 에러\nLOCKED_MOTOR_ERROR | 드라이버 모터 에러\nCHILD_LOCK_ACTIVE_ERROR | childlock 에러\nTIME_TO_RUN_THE_TUB_CLEAN_CYCLE_ERROR | 통세척 에러\nUNBALANCED_LOAD_ERROR | 수평 에러\nDOOR_OPEN_ERROR | 문 열림 에러\nUNABLE_TO_LOCK_ERROR | 잠김 불가 에러\nOVERFILL_ERROR | 물 수위 에러\nWATER_LEVEL_SENSOR_ERROR | 물 수위 센서 에러\nPOWER_FAIL_ERROR | 전력 에러\nTEMPERATURE_SENSOR_ERROR | 온도 센서 에러\nTIMEOUT_ERROR | 타임아웃 에러\nPART_MALFUNCTION_ERROR | 기기 부품 에러\nFROZEN_ERROR | 동결 감지 에러\nVIBRATION_SENSOR_ERROR | 진동 센서 에러\nDISPENSING_ERROR | 세제 및 유연제 투입 에러\nTURBIDITY_SENSOR_ERROR | 탁도 센서 에러\nSTEAM_HEAT_ERROR | 스팀 동작 안함\nIR_SENSOR_ERROR | 적외선 센서 에러\nDOOR_SENSOR_ERROR | 도어 센서 에러\nCLUTCH_ERROR | 클러치 에러\t\nINNER_LID_OPEN_ERROR | 안쪽 LID 오픈 에러\nSTACK_ERROR | 스택 에러"
              items:
                type: string
                enum:
                  - WATER_SUPPLY_ERROR
                  - WATER_DRAIN_ERROR
                  - OUT_OF_BALANCE_ERROR
                  - LOCKED_MOTOR_ERROR
                  - CHILD_LOCK_ACTIVE_ERROR
                  - TIME_TO_RUN_THE_TUB_CLEAN_CYCLE_ERROR
                  - UNBALANCED_LOAD_ERROR
                  - DOOR_OPEN_ERROR
                  - UNABLE_TO_LOCK_ERROR
                  - OVERFILL_ERROR
                  - WATER_LEVEL_SENSOR_ERROR
                  - POWER_FAIL_ERROR
                  - TEMPERATURE_SENSOR_ERROR
                  - TIMEOUT_ERROR
                  - PART_MALFUNCTION_ERROR
                  - FROZEN_ERROR
                  - VIBRATION_SENSOR_ERROR
                  - DISPENSING_ERROR
                  - TURBIDITY_SENSOR_ERROR
                  - STEAM_HEAT_ERROR
                  - IR_SENSOR_ERROR
                  - DOOR_SENSOR_ERROR
                  - CLUTCH_ERROR
                  - INNER_LID_OPEN_ERROR
                  - STACK_ERROR
        main_washcombo-object:
          title: Main_Washcombo
          type: array
          items:
            type: object
            properties:
              runState:
                type: object
                description: 상태
                properties:
                  currentState:
                    type: string
                    description: 현재 상태
                    enum:
                      - POWER_OFF
                      - INITIAL
                      - PAUSE
                      - DETECTING
                      - SOAKING
                      - RUNNING
                      - RINSING
                      - SPINNING
                      - END
                      - RESERVED
                      - FIRMWARE
                      - DRYING
                      - COOL_DOWN
                      - RINSE_HOLD
                      - REFRESHING
                      - STEAM_SOFTENING
                      - ERROR
                      - SMART_GRID_RUN
                      - ADD_DRAIN
                      - DETERGENT_AMOUNT
                      - PREWASH
                      - SHOES_MODULE
                      - PROOFING
                      - DISPENSING
                      - SOFTENING
                      - CHECKING_TURBIDITY
                      - CHANGE_CONDITION
                      - DISPLAY_LOADSIZE
                      - FROZEN_PREVENT_INITIAL
                      - FROZEN_PREVENT_RUNNING
                      - FROZEN_PREVENT_PAUSE
                      - COOLING
                      - SLEEP
              operation:
                type: object
                description: 동작
                properties:
                  washerOperationMode:
                    type: string
                    description: 세탁 동작
                    enum:
                      - START
                      - STOP
                      - POWER_OFF
                      - WAKE_UP
              mode:
                type: object
                description: 모드
                properties:
                  washerOperationMode:
                    type: string
                    description: 세탁 모드
                    enum:
                      - WASHING_DRYING
                      - WASHING
                      - DRYING
              remoteControlEnable:
                type: object
                description: 원격제어설정
                properties:
                  remoteControlEnabled:
                    type: boolean
                    description: 원격 제어 설정 상태
                    enum:
                      - true
                      - false
              timer:
                type: object
                description: 타이머
                properties:
                  remainHour:
                    type: integer
                    description: 남은 시간(시)
                  remainMinute:
                    type: integer
                    description: 남은 시간(분)
                  relativeHourToStart:
                    type: integer
                    description: 세탁 시작 예약 시간(시)
                  relativeMinuteToStart:
                    type: integer
                    description: 세탁 시작 예약 시간(분)
                  relativeHourToStop:
                    type: integer
                    description: 세탁 종료 예약 시간(시)
                  relativeMinuteToStop:
                    type: integer
                    description: 세탁 종료 예약 시간(분)
                  totalHour:
                    type: integer
                    description: 세탁 전체 시간(시)
                  totalMinute:
                    type: integer
                    description: 세탁 전체 시간(분)
              detergent:
                type: object
                description: 세제 설정
                properties:
                  detergentSetting:
                    type: string
                    description: 세제 설정 모드
                    enum:
                      - AUTO
                      - NORMAL
              location:
                type: object
                description: 위치
                properties:
                  locationName:
                    type: string
                    description: 위치 이름
                    enum:
                      - MAIN
              error:
                type: string
                description: Error Message
                enum:
                  - WATER_SUPPLY_ERROR
                  - WATER_DRAIN_ERROR
                  - OUT_OF_BALANCE_ERROR
                  - LOCKED_MOTOR_ERROR
                  - CHILD_LOCK_ACTIVE_ERROR
                  - TIME_TO_RUN_THE_TUB_CLEAN_CYCLE_ERROR
                  - UNBALANCED_LOAD_ERROR
                  - DOOR_OPEN_ERROR
                  - UNABLE_TO_LOCK_ERROR
                  - OVERFILL_ERROR
                  - WATER_LEVEL_SENSOR_ERROR
                  - POWER_FAIL_ERROR
                  - TEMPERATURE_SENSOR_ERROR
                  - TIMEOUT_ERROR
                  - PART_MALFUNCTION_ERROR
                  - FROZEN_ERROR
                  - VIBRATION_SENSOR_ERROR
                  - DISPENSING_ERROR
                  - TURBIDITY_SENSOR_ERROR
                  - STEAM_HEAT_ERROR
                  - IR_SENSOR_ERROR
                  - DOOR_SENSOR_ERROR
                  - CLUTCH_ERROR
                  - INNER_LID_OPEN_ERROR
                  - STACK_ERROR
        mini_washcombo-profile:
          type: object
          title: Mini_Washcombo
          properties:
            property:
              type: array
              items:
                type: object
                properties:
                  runState:
                    type: object
                    description: 상태
                    properties:
                      currentState:
                        type: object
                        description: 현재 상태
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: "Value | Description\n-|-\nPOWER_OFF | 제품 OFF\nINITIAL | 대기 중 상태\nPAUSE | 일시정지\nDETECTING | 옷감량확인\nSOAKING | 불림 상태\nRUNNING\t|\t행정중\nRINSING\t|\t행굼 중\nSPINNING | 탈수중\nEND\t| 세탁완료상태\nRESERVED | 예약상태\nFIRMWARE | 펌웨어 업데이트 중\nDRYING | 건조 중\nCOOL_DOWN\t| 구김방지1\nRINSE_HOLD | 린스 후 일시정지 중\nREFRESHING | 구김방지2 FRESHCARE\nSTEAM_SOFTENING | 스팀소프트닝\nERROR\t| 에러상태\nSMART_GRID_RUN | Smart Grid 동작 상태\nADD_DRAIN\t| 배수 추가 상태\nDETERGENT_AMOUNT | 세제량 표시중\nPREWASH | 예비 세탁 동작 상태\nSHOES_MODULE | 슈즈 건조 동작 상태\nPROOFING | 발수처리 상태\nDISPENSING | 세제 자동 투입 중\nSOFTENING | 유연제량 확인\nCHECKING_TURBIDITY | 탁도감지 중(G+Best모델 AUTOWASH 코스 사용 시)\nCHANGE_CONDITION | 탁도감지 결과를 가지고 자동으로 옵션변경 후 Display\nDISPLAY_LOADSIZE | 옷감량 확인 결과 Display\nFROZEN_PREVENT_INITIAL | 동결방지모드 대기상태\nFROZEN_PREVENT_RUNNING | 동결방지모드 진행상태\nFROZEN_PREVENT_PAUSE | 동결방지모드 멈춤상태\nCOOLING | 쿨링\nSLEEP | Sleep 상태"
                                items:
                                  type: string
                                  enum:
                                    - POWER_OFF
                                    - INITIAL
                                    - PAUSE
                                    - DETECTING
                                    - SOAKING
                                    - RUNNING
                                    - RINSING
                                    - SPINNING
                                    - END
                                    - RESERVED
                                    - FIRMWARE
                                    - DRYING
                                    - COOL_DOWN
                                    - RINSE_HOLD
                                    - REFRESHING
                                    - STEAM_SOFTENING
                                    - ERROR
                                    - SMART_GRID_RUN
                                    - ADD_DRAIN
                                    - DETERGENT_AMOUNT
                                    - PREWASH
                                    - SHOES_MODULE
                                    - PROOFING
                                    - DISPENSING
                                    - SOFTENING
                                    - CHECKING_TURBIDITY
                                    - CHANGE_CONDITION
                                    - DISPLAY_LOADSIZE
                                    - FROZEN_PREVENT_INITIAL
                                    - FROZEN_PREVENT_RUNNING
                                    - FROZEN_PREVENT_PAUSE
                                    - COOLING
                                    - SLEEP
                  operation:
                    type: object
                    description: 동작
                    properties:
                      washerOperationMode:
                        type: object
                        description: 세탁 동작
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - enum
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  START | 세탁 시작
                                  STOP | 세탁 정지
                                  POWER_OFF | 전원 OFF
                                  WAKE_UP | Wake up
                                items:
                                  type: string
                                  enum:
                                    - START
                                    - STOP
                                    - POWER_OFF
                                    - WAKE_UP
                  remoteControlEnable:
                    type: object
                    description: 원격제어설정
                    properties:
                      remoteControlEnabled:
                        type: object
                        description: 원격 제어 설정 상태
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - boolean
                          value:
                            type: object
                            properties:
                              r:
                                type: array
                                description: |-
                                  Value | Description
                                  -|-
                                  TRUE | 원격 제어 가능
                                  FALSE | 원격 제어 불가능
                                items:
                                  type: boolean
                                  enum:
                                    - true
                                    - false
                  timer:
                    type: object
                    description: 타이머
                    properties:
                      remainHour:
                        type: object
                        description: 남은 시간(시)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      remainMinute:
                        type: object
                        description: 남은 시간(분)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      relativeHourToStart:
                        type: object
                        description: 세탁 시작 예약 시간(시)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                              w:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      relativeMinuteToStart:
                        type: object
                        description: 세탁 시작 예약 시간(분)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      relativeHourToStop:
                        type: object
                        description: 세탁 종료 예약 시간(시)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                                - w
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                              w:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      relativeMinuteToStop:
                        type: object
                        description: 세탁 종료 예약 시간(분)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      totalHour:
                        type: object
                        description: 세탁 전체 시간(시)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                      totalMinute:
                        type: object
                        description: 세탁 전체 시간(분)
                        properties:
                          mode:
                            type: array
                            items:
                              type: string
                              enum:
                                - r
                          type:
                            type: string
                            enum:
                              - range
                          value:
                            type: object
                            properties:
                              r:
                                type: object
                                properties:
                                  max:
                                    type: integer
                                  min:
                                    type: integer
                                  step:
                                    type: integer
                                  except:
                                    type: array
                  detergent:
                    type: object
                    description: 세제 설정
                    properties:
                      detergentSetting:
                        type: string
                        description: |-
                          Value | Description
                          -|-
                          AUTO | 자동 설정 기기
                          NORMAL | 일반 기기
                        enum:
                          - AUTO
                          - NORMAL
                  location:
                    type: object
                    description: 위치
                    properties:
                      locationName:
                        type: string
                        description: |-
                          Value | Description
                          -|-
                          MINI | mini washer
                        enum:
                          - MINI
            notification:
              type: object
              properties:
                push:
                  type: array
                  minItems: 1
                  description: |-
                    Push Code | Description
                    -|-
                    WASHING_IS_COMPLETE | 세탁이 완료되었습니다.
                    ERROR_DURING_WASHING | 세탁 중 오류가 발생하였습니다.
                  items:
                    type: string
                    enum:
                      - WASHING_IS_COMPLETE
                      - ERROR_DURING_WASHING
            error:
              type: array
              description: "Push Code | Description\n-|-\nWATER_SUPPLY_ERROR | 급수 에러\nWATER_DRAIN_ERROR | 배수 에러\nOUT_OF_BALANCE_ERROR | 탈수 에러\nLOCKED_MOTOR_ERROR | 드라이버 모터 에러\nCHILD_LOCK_ACTIVE_ERROR | childlock 에러\nTIME_TO_RUN_THE_TUB_CLEAN_CYCLE_ERROR | 통세척 에러\nUNBALANCED_LOAD_ERROR | 수평 에러\nDOOR_OPEN_ERROR | 문 열림 에러\nUNABLE_TO_LOCK_ERROR | 잠김 불가 에러\nOVERFILL_ERROR | 물 수위 에러\nWATER_LEVEL_SENSOR_ERROR | 물 수위 센서 에러\nPOWER_FAIL_ERROR | 전력 에러\nTEMPERATURE_SENSOR_ERROR | 온도 센서 에러\nTIMEOUT_ERROR | 타임아웃 에러\nPART_MALFUNCTION_ERROR | 기기 부품 에러\nFROZEN_ERROR | 동결 감지 에러\nVIBRATION_SENSOR_ERROR | 진동 센서 에러\nDISPENSING_ERROR | 세제 및 유연제 투입 에러\nTURBIDITY_SENSOR_ERROR | 탁도 센서 에러\nSTEAM_HEAT_ERROR | 스팀 동작 안함\nIR_SENSOR_ERROR | 적외선 센서 에러\nDOOR_SENSOR_ERROR | 도어 센서 에러\nCLUTCH_ERROR | 클러치 에러\t\nINNER_LID_OPEN_ERROR | 안쪽 LID 오픈 에러\nSTACK_ERROR | 스택 에러"
              items:
                type: string
                enum:
                  - WATER_SUPPLY_ERROR
                  - WATER_DRAIN_ERROR
                  - OUT_OF_BALANCE_ERROR
                  - LOCKED_MOTOR_ERROR
                  - CHILD_LOCK_ACTIVE_ERROR
                  - TIME_TO_RUN_THE_TUB_CLEAN_CYCLE_ERROR
                  - UNBALANCED_LOAD_ERROR
                  - DOOR_OPEN_ERROR
                  - UNABLE_TO_LOCK_ERROR
                  - OVERFILL_ERROR
                  - WATER_LEVEL_SENSOR_ERROR
                  - POWER_FAIL_ERROR
                  - TEMPERATURE_SENSOR_ERROR
                  - TIMEOUT_ERROR
                  - PART_MALFUNCTION_ERROR
                  - FROZEN_ERROR
                  - VIBRATION_SENSOR_ERROR
                  - DISPENSING_ERROR
                  - TURBIDITY_SENSOR_ERROR
                  - STEAM_HEAT_ERROR
                  - IR_SENSOR_ERROR
                  - DOOR_SENSOR_ERROR
                  - CLUTCH_ERROR
                  - INNER_LID_OPEN_ERROR
                  - STACK_ERROR
        mini_washcombo-object:
          title: Mini_Washcombo
          type: array
          items:
            type: object
            properties:
              runState:
                type: object
                description: 상태
                properties:
                  currentState:
                    type: string
                    description: 현재 상태
                    enum:
                      - POWER_OFF
                      - INITIAL
                      - PAUSE
                      - DETECTING
                      - SOAKING
                      - RUNNING
                      - RINSING
                      - SPINNING
                      - END
                      - RESERVED
                      - FIRMWARE
                      - DRYING
                      - COOL_DOWN
                      - RINSE_HOLD
                      - REFRESHING
                      - STEAM_SOFTENING
                      - ERROR
                      - SMART_GRID_RUN
                      - ADD_DRAIN
                      - DETERGENT_AMOUNT
                      - PREWASH
                      - SHOES_MODULE
                      - PROOFING
                      - DISPENSING
                      - SOFTENING
                      - CHECKING_TURBIDITY
                      - CHANGE_CONDITION
                      - DISPLAY_LOADSIZE
                      - FROZEN_PREVENT_INITIAL
                      - FROZEN_PREVENT_RUNNING
                      - FROZEN_PREVENT_PAUSE
                      - COOLING
                      - SLEEP
              operation:
                type: object
                description: 동작
                properties:
                  washerOperationMode:
                    type: string
                    description: 세탁 동작
                    enum:
                      - START
                      - STOP
                      - POWER_OFF
                      - WAKE_UP
              remoteControlEnable:
                type: object
                description: 원격제어설정
                properties:
                  remoteControlEnabled:
                    type: boolean
                    description: 원격 제어 설정 상태
                    enum:
                      - true
                      - false
              timer:
                type: object
                description: 타이머
                properties:
                  remainHour:
                    type: integer
                    description: 남은 시간(시)
                  remainMinute:
                    type: integer
                    description: 남은 시간(분)
                  relativeHourToStart:
                    type: integer
                    description: 세탁 시작 예약 시간(시)
                  relativeMinuteToStart:
                    type: integer
                    description: 세탁 시작 예약 시간(분)
                  relativeHourToStop:
                    type: integer
                    description: 세탁 종료 예약 시간(시)
                  relativeMinuteToStop:
                    type: integer
                    description: 세탁 종료 예약 시간(분)
                  totalHour:
                    type: integer
                    description: 세탁 전체 시간(시)
                  totalMinute:
                    type: integer
                    description: 세탁 전체 시간(분)
              detergent:
                type: object
                description: 세제 설정
                properties:
                  detergentSetting:
                    type: string
                    description: 세제 설정 모드
                    enum:
                      - AUTO
                      - NORMAL
              location:
                type: object
                description: 위치
                properties:
                  locationName:
                    type: string
                    description: 위치 이름
                    enum:
                      - MINI
              error:
                type: string
                description: Error Message
                enum:
                  - WATER_SUPPLY_ERROR
                  - WATER_DRAIN_ERROR
                  - OUT_OF_BALANCE_ERROR
                  - LOCKED_MOTOR_ERROR
                  - CHILD_LOCK_ACTIVE_ERROR
                  - TIME_TO_RUN_THE_TUB_CLEAN_CYCLE_ERROR
                  - UNBALANCED_LOAD_ERROR
                  - DOOR_OPEN_ERROR
                  - UNABLE_TO_LOCK_ERROR
                  - OVERFILL_ERROR
                  - WATER_LEVEL_SENSOR_ERROR
                  - POWER_FAIL_ERROR
                  - TEMPERATURE_SENSOR_ERROR
                  - TIMEOUT_ERROR
                  - PART_MALFUNCTION_ERROR
                  - FROZEN_ERROR
                  - VIBRATION_SENSOR_ERROR
                  - DISPENSING_ERROR
                  - TURBIDITY_SENSOR_ERROR
                  - STEAM_HEAT_ERROR
                  - IR_SENSOR_ERROR
                  - DOOR_SENSOR_ERROR
                  - CLUTCH_ERROR
                  - INNER_LID_OPEN_ERROR
                  - STACK_ERROR
        odu-profile:
          type: object
          title: ODU
          properties:
            operation:
              type: object
              properties:
                operationMode:
                  type: object
                  description: 운전모드
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - enum
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            STOP | 운전정지
                            COOL | 냉방운전
                            HEAT | 난방운전
                          items:
                            type: string
                            enum:
                              - STOP
                              - COOL
                              - HEAT
            temperature:
              type: object
              description: 온도
              properties:
                outdoorTemperature:
                  type: object
                  description: 실내기 온도
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - number
            info:
              type: object
              description: 실외기 정보
              properties:
                modelName:
                  type: object
                  description: 실외기 모델명
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - string
                capacity:
                  type: object
                  description: 실외기 용량
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - string
        odu-object:
          title: ODU
          minProperties: 1
          properties:
            operation:
              readOnly: true
              type: object
              properties:
                operationMode:
                  type: string
                  enum:
                    - STOP
                    - COOL
                    - HEAT
            temperature:
              readOnly: true
              type: object
              properties:
                outdoorTemperature:
                  type: integer
                  example: 30
            info:
              readOnly: true
              type: object
              properties:
                modelName:
                  type: string
                  example: HP_SUPER5
                capacity:
                  type: number
                  example: 0
        idu-profile:
          type: object
          title: IDU
          properties:
            operation:
              type: object
              description: 동작
              properties:
                airConOperationMode:
                  type: object
                  description: 동작 상태
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - enum
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            POWER_ON | 동작 상태 ON
                            POWER_OFF | 동작 상태 OFF
                          items:
                            type: string
                            enum:
                              - POWER_ON
                              - POWER_OFF
                        w:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            POWER_ON | 동작 상태 ON
                            POWER_OFF | 동작 상태 OFF
                          items:
                            type: string
                            enum:
                              - POWER_ON
                              - POWER_OFF
                heaterOperationMode:
                  type: object
                  description: 히터동작 상태
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - enum
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            POWER_ON | 히터동작 ON
                            POWER_OFF | 히터동작 OFF
                          items:
                            type: string
                            enum:
                              - POWER_ON
                              - POWER_OFF
                        w:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            POWER_ON | 히터동작 ON
                            POWER_OFF | 히터동작 OFF
                          items:
                            type: string
                            enum:
                              - POWER_ON
                              - POWER_OFF
            jobMode:
              type: object
              description: 모드
              properties:
                airConJobMode:
                  type: object
                  description: 실내기 운전모드
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - enum
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            AUTO | 운전모드 자동
                            COOL | 냉방
                            AIR_DRY | 제습
                            FAN | 송풍
                            HEAT | 난방
                          items:
                            type: string
                            enum:
                              - AUTO
                              - COOL
                              - AIR_DRY
                              - FAN
                              - HEAT
                        w:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            AUTO | 운전모드 자동
                            COOL | 냉방
                            AIR_DRY | 제습
                            FAN | 송풍
                            HEAT | 난방
                          items:
                            type: string
                            enum:
                              - AUTO
                              - COOL
                              - AIR_DRY
                              - FAN
                              - HEAT
                heaterJobMode:
                  type: object
                  description: 실내기 히터동작 모드
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - boolean
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 히터 모드 제어 방식 자동
                            false | 히터 모드 제어 방식 수동
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
                        w:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 히터 모드 제어 방식 자동
                            false | 히터 모드 제어 방식 수동
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
            temperature:
              type: object
              description: 온도
              properties:
                currentTemperature:
                  type: object
                  description: 실내기 룸온도
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - number
                targetTemperature:
                  type: object
                  description: 실내기 설정온도
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - range
                    value:
                      type: object
                      properties:
                        r:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 30
                            min:
                              type: integer
                              enum:
                                - 16
                            step:
                              type: integer
                              enum:
                                - 1
                        w:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 30
                            min:
                              type: integer
                              enum:
                                - 16
                            step:
                              type: integer
                              enum:
                                - 1
                targetTemperatureLowLimit:
                  type: object
                  description: 실내기 설정온도하한
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - range
                    value:
                      type: object
                      properties:
                        r:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 30
                            min:
                              type: integer
                              enum:
                                - 16
                            step:
                              type: integer
                              enum:
                                - 1
                        w:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 30
                            min:
                              type: integer
                              enum:
                                - 16
                            step:
                              type: integer
                              enum:
                                - 1
                targetTemperatureUpperLimit:
                  type: object
                  description: 실내기 설정온도상한
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - range
                    value:
                      type: object
                      properties:
                        r:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 30
                            min:
                              type: integer
                              enum:
                                - 16
                            step:
                              type: integer
                              enum:
                                - 1
                        w:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 30
                            min:
                              type: integer
                              enum:
                                - 16
                            step:
                              type: integer
                              enum:
                                - 1
                outdoorTemperature1:
                  type: object
                  description: 히터조합난방설정온도(T1설정온도)
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - range
                    value:
                      type: object
                      properties:
                        r:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 0
                            min:
                              type: integer
                              enum:
                                - -23
                            step:
                              type: integer
                              enum:
                                - 1
                        w:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 0
                            min:
                              type: integer
                              enum:
                                - -23
                            step:
                              type: integer
                              enum:
                                - 1
                outdoorTemperature2:
                  type: object
                  description: 히터조합난방설정온도(T2설정온도)
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - range
                    value:
                      type: object
                      properties:
                        r:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 51
                            min:
                              type: integer
                              enum:
                                - -23
                            step:
                              type: integer
                              enum:
                                - 1
                        w:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 51
                            min:
                              type: integer
                              enum:
                                - -23
                            step:
                              type: integer
                              enum:
                                - 1
            powerSave:
              type: object
              description: 절전
              properties:
                powerSaveEnabled:
                  type: object
                  description: 실내기 쾌적절전 동작상태
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - boolean
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 절전 모드 설정
                            false | 절전 모드 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
                powerSaveStep:
                  type: object
                  description: 실내기 쾌적절전 동작스텝
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - enum
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            POWERSAVE_LEVEL_0 | 절전 모드 0단계
                            POWERSAVE_LEVEL_1 | 절전 모드 1단계
                            POWERSAVE_LEVEL_2 | 절전 모드 2단계
                            POWERSAVE_LEVEL_3 | 절전 모드 3단계
                          items:
                            type: string
                            enum:
                              - POWERSAVE_LEVEL_1
                              - POWERSAVE_LEVEL_2
                              - POWERSAVE_LEVEL_3
            airFlow:
              type: object
              description: 바람 설정
              properties:
                windStrength:
                  type: object
                  description: 실내기 팬풍량
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - enum
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            AUTO | 자동
                            HIGH | 강풍
                            MED | 중풍
                            LOW | 약풍
                          items:
                            type: string
                            enum:
                              - AUTO
                              - HIGH
                              - MED
                              - LOW
                        w:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            AUTO | 자동
                            HIGH | 강풍
                            MED | 중풍
                            LOW | 약풍
                          items:
                            type: string
                            enum:
                              - AUTO
                              - HIGH
                              - MED
                              - LOW
                windDirectionSetting:
                  type: object
                  description: 실내기 풍향
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - boolean
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 풍향 자동 설정
                            false | 풍향 자동 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
                        w:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 풍향 자동 설정
                            false | 풍향 자동 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
            outdoor:
              type: object
              description: null
              properties:
                outdoorHeaterSetting:
                  type: object
                  description: 실내기 outdoor 히터 heater 동작상태
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - boolean
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 실내기 outdoor 히터 heater 동작 설정
                            false | 실내기 outdoor 히터 heater 동작 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
                        w:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 실내기 outdoor 히터 heater 동작 설정
                            false | 실내기 outdoor 히터 heater 동작 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
                outdoorHeatPumpSetting:
                  type: object
                  description: 실내기 outdoor 히터 heatpump 동작상태
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - boolean
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 실내기 outdoor 히터 heatpump 동작 설정
                            false | 실내기 outdoor 히터 heatpump 동작 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
                        w:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 실내기 outdoor 히터 heatpump 동작 설정
                            false | 실내기 outdoor 히터 heatpump 동작 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
            lock:
              type: object
              description: 잠금
              properties:
                fullLock:
                  type: object
                  description: 실내기 잠금
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - boolean
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 실내기 잠금 설정
                            false | 실내기 잠금 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
                        w:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 실내기 잠금 설정
                            false | 실내기 잠금 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
                modeLock:
                  type: object
                  description: 실내기 모드잠금
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - boolean
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 실내기 모드잠금 설정
                            false | 실내기 모드잠금 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
                        w:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 실내기 모드잠금 설정
                            false | 실내기 모드잠금 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
                fanLock:
                  type: object
                  description: 실내기 팬잠금
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - boolean
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 실내기 팬잠금 설정
                            false | 실내기 팬잠금 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
                        w:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 실내기 팬잠금 설정
                            false | 실내기 팬잠금 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
                temperatureLock:
                  type: object
                  description: 실내기 설정온도잠금
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - boolean
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 실내기 설정온도잠금 설정
                            false | 실내기 설정온도잠금 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
                        w:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 실내기 설정온도잠금 설정
                            false | 실내기 설정온도잠금 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
            alarm:
              type: object
              description: 알람
              properties:
                filterReplacementAlarm:
                  type: object
                  description: 실내기 필터교체 알람
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - boolean
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 실내기 필터교체 알람 설정
                            false | 실내기 필터교체 알람 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
        idu-object:
          title: IDU
          minProperties: 1
          properties:
            error:
              readOnly: true
              type: object
              properties:
                errorCode:
                  type: string
                  example: 0
            operation:
              type: object
              properties:
                airConOperationMode:
                  type: string
                  enum:
                    - POWER_ON
                    - POWER_OFF
            jobMode:
              type: object
              properties:
                airConJobMode:
                  type: string
                  enum:
                    - AUTO
                    - COOL
                    - AIR_DRY
                    - FAN
                    - HEAT
            temperature:
              type: object
              properties:
                currentTemperature:
                  readOnly: true
                  type: integer
                  example: 23
                targetTemperature:
                  type: integer
                  example: 21
                targetTemperatureLowLimit:
                  writeOnly: true
                  type: integer
                  example: 18
                targetTemperatureUpperLimit:
                  writeOnly: true
                  type: integer
                  example: 29
            airFlow:
              type: object
              properties:
                windStrength:
                  type: string
                  enum:
                    - AUTO
                    - HIGH
                    - MED
                    - LOW
            lock:
              writeOnly: true
              type: object
              properties:
                fullLock:
                  type: boolean
                  enum:
                    - true
                    - false
                modeLock:
                  type: boolean
                  enum:
                    - true
                    - false
                fanLock:
                  type: boolean
                  enum:
                    - true
                    - false
                temperatureLock:
                  type: boolean
                  enum:
                    - true
                    - false
        idu-command-schema:
          title: IDU
          minProperties: 1
          properties:
            operation:
              type: object
              properties:
                airConOperationMode:
                  type: string
                  enum:
                    - POWER_ON
                    - POWER_OFF
            jobMode:
              type: object
              properties:
                airConJobMode:
                  type: string
                  enum:
                    - AUTO
                    - COOL
                    - AIR_DRY
                    - FAN
                    - HEAT
            temperature:
              type: object
              properties:
                targetTemperature:
                  type: integer
                  example: 21
                targetTemperatureLowLimit:
                  type: integer
                  example: 18
                targetTemperatureUpperLimit:
                  type: integer
                  example: 29
            airFlow:
              type: object
              properties:
                windStrength:
                  type: string
                  enum:
                    - AUTO
                    - HIGH
                    - MED
                    - LOW
            lock:
              type: object
              properties:
                fullLock:
                  type: boolean
                  enum:
                    - true
                    - false
                modeLock:
                  type: boolean
                  enum:
                    - true
                    - false
                fanLock:
                  type: boolean
                  enum:
                    - true
                    - false
                temperatureLock:
                  type: boolean
                  enum:
                    - true
                    - false
        signage-profile:
          type: object
          title: IDU
          properties:
            power:
              type: object
              description: 전원
              properties:
                power:
                  type: object
                  description: 전원
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - boolean
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true| 전원 켜짐
                            false| 전원 꺼짐
                          items:
                            type: string
                            enum:
                              - true
                              - false
                screen:
                  type: object
                  description: 화면 ON, OFF 상태
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - enum
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            SCREEN_ON| 화면 켜짐
                            SCREEN_OFF| 화면 꺼짐
                            UNKNOWN| 화면 상태를 가져올 수 없음
                          items:
                            type: string
                            enum:
                              - SCREEN_ON
                              - SCREEN_OFF
                              - UNKNOWN
                        w:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            SCREEN_ON| 화면 켜짐
                            SCREEN_OFF| 화면 꺼짐
                            UNKNOWN| 화면 상태를 가져올 수 없음
                          items:
                            type: string
                            enum:
                              - SCREEN_ON
                              - SCREEN_OFF
                              - UNKNOWN
                noSignalPowerOff:
                  type: object
                  description: 무신호 전원 꺼짐 설정
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - boolean
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true| 무신호 전원 꺼짐 설정
                            false| 무신호 전원 꺼짐 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
                noIrPowerOff:
                  type: object
                  description: IR 신호 없을 시 꺼짐 설정
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - boolean
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true| IR 신호 없을 때 자동 대기 설정
                            false| IR 신호 없을 때 자동 대기 해제
                          items:
                            type: string
                            enum:
                              - true
                              - false
                pmMode:
                  type: object
                  description: PM Mode 설정
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - enum
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            00| 전원 끄기
                            01| 화면 비율 유지
                            02| 화면 끄기
                            03| 항상 화면 끄기
                            04| 화면 끄기 및 백라이트 켜기
                            05| 네트워크 준비
                          items:
                            type: string
                            enum:
                              - '00'
                              - '01'
                              - '02'
                              - '03'
                              - '04'
                              - '05'
                powerOnStatus:
                  type: object
                  description: 전원 켜기 상태
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - enum
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            00| LST (마지막 상태)
                            01| STD (대기)
                            02| PWR (전원 켜기)
                          items:
                            type: string
                            enum:
                              - '00'
                              - '01'
                              - '02'
                powerOnDelay:
                  type: object
                  description: 전원 켜기 지연 (초)
                  properties:
                    mode:
                      type: array
                      enum:
                        - r
                    type:
                      type: number
                      enum:
                        - number
                    value:
                      type: object
                      properties:
                        r:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 250
                            min:
                              type: integer
                              enum:
                                - 0
                            step:
                              type: integer
                              enum:
                                - 1
                energySavingMode:
                  type: object
                  description: 절전 모드
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - enum
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            00| 절전 꺼짐
                            01| 최소 절전
                            02| 중간 절전
                            03| 최대 절전
                            04| 자동
                          items:
                            type: string
                            enum:
                              - '00'
                              - '01'
                              - '02'
                              - '03'
                              - '04'
                wol:
                  type: object
                  description: Wake On Lan 설정
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - boolean
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true| Wake On Lan 설정
                            false| Wake On Lan 해제
                          items:
                            type: string
                            enum:
                              - true
                              - false
            display:
              type: object
              description: 디스플레이
              properties:
                input:
                  type: object
                  description: 입력 신호 선택
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - enum
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: "Value | Description\n-|-\n20| AV\n40| COMPONENT\n60| RGB\n70| DVI-D (PC)\n80| DVI-D (DTV)\n90| HDMI1 (DTV)\na9| HDMI1 (PC)\n91| HDMI2 (DTV)\na1| HDMI2 (PC)\n92| OPS/HDMI3/DVI-D (DTV)\na2| OPS/HDMI3/DVI-D (PC)\n95| OPS/DVI-D (DTV)\na5| OPS/DVI-D (PC)\n96| HDMI3/DVI-D (DTV)\na6| HDMI3/DVI-D (PC)\n97| HDMI3/HDMI2/DVI-D (DTV)\na7| HDMI3/HDMI2/DVI-D (PC)\n98| OPS (DTV)\na8| OPS (PC)\n99| HDMI2/OPS (DTV)\na9| HDMI2/OPS (PC)\nc0| DISPLAYPORT (DTV)\nd0| DISPLAYPORT (PC)\nc1| DISPLAYPORT/USB-C (DTV)\nd1| DISPLAYPORT/USB-C (PC)\nc2| HDMI3 (DTV)\nd2| HDMI3 (PC)\nc3| HDBaseT (DTV)\nd3| HDBaseT (PC)\ne0| SuperSign webOS Player\ne1| Others\ne2| Multi Screen\ne3| URL\_재생\ne8| SI App\nf0| SDI 1\nf1| SDI 2\nf2| SDI 3\nf3| SDI 4\nf4| Dual Link (SDI 1&2)\nf5| Dual Link (SDI 3&4)\nf6| Quad Link : Auto\nf7| Quad Link : 2SI\nf8| Quad Link : Square\nf9| SDI Quad View"
                          items:
                            type: string
                            enum:
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
                          type: array
                          description: "Value | Description\n-|-\n20| AV\n40| COMPONENT\n60| RGB\n70| DVI-D (PC)\n80| DVI-D (DTV)\n90| HDMI1 (DTV)\na9| HDMI1 (PC)\n91| HDMI2 (DTV)\na1| HDMI2 (PC)\n92| OPS/HDMI3/DVI-D (DTV)\na2| OPS/HDMI3/DVI-D (PC)\n95| OPS/DVI-D (DTV)\na5| OPS/DVI-D (PC)\n96| HDMI3/DVI-D (DTV)\na6| HDMI3/DVI-D (PC)\n97| HDMI3/HDMI2/DVI-D (DTV)\na7| HDMI3/HDMI2/DVI-D (PC)\n98| OPS (DTV)\na8| OPS (PC)\n99| HDMI2/OPS (DTV)\na9| HDMI2/OPS (PC)\nc0| DISPLAYPORT (DTV)\nd0| DISPLAYPORT (PC)\nc1| DISPLAYPORT/USB-C (DTV)\nd1| DISPLAYPORT/USB-C (PC)\nc2| HDMI3 (DTV)\nd2| HDMI3 (PC)\nc3| HDBaseT (DTV)\nd3| HDBaseT (PC)\ne0| SuperSign webOS Player\ne1| Others\ne2| Multi Screen\ne3| URL\_재생\ne8| SI App\nf0| SDI 1\nf1| SDI 2\nf2| SDI 3\nf3| SDI 4\nf4| Dual Link (SDI 1&2)\nf5| Dual Link (SDI 3&4)\nf6| Quad Link : Auto\nf7| Quad Link : 2SI\nf8| Quad Link : Square\nf9| SDI Quad View"
                          items:
                            type: string
                            enum:
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
                  type: object
                  description: OSD 언어 설정
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - enum
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            00| 체코
                            01| 덴마크어
                            02| 독일어
                            03| 영어
                            04| 스페인어 (유럽)
                            05| 그리스어
                            06| 프랑스어
                            07| 이탈리아어
                            08| 네델란드어
                            09| 노르웨이어
                            0a| 포르투칼어
                            0b| 포르투칼어 (브라질)
                            0c| 러시아어
                            0d| 핀란드어
                            0e| 스웨덴어
                            0f| 한국어
                            10| 중국어 (북경어)
                            11| 일본어
                            12| 중국어 (광동어)
                            13| 아랍어
                            14| 터키어
                            15| 폴란드어
                          items:
                            type: string
                            enum:
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
                  type: object
                  description: 화면 잔상 방지
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - enum
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            02| 이동
                            04| 화이트 워시
                            08| 꺼짐
                            90| 사용자 이미지
                            91| 사용자 동영상
                          items:
                            type: string
                            enum:
                              - '02'
                              - '04'
                              - '08'
                              - '90'
                              - '91'
                pictureMode:
                  type: object
                  description: 영상 모드
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - enum
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            00| Mall / QSR / Shopping Mall (Vivid)
                            01| General / Airport & Station (Standard)
                            02| Gov. & Corp. / Office & School (Cinema)
                            03| Transportation (Sports)
                            04| Education / Control Room (Game)
                            05| Expert 1 / Expert(Bright Room)
                            08| Auto Power Save
                            11| Calibration / Expert (Dark Room)
                            12| Hospital
                          items:
                            type: string
                            enum:
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
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            00| Mall / QSR / Shopping Mall (Vivid)
                            01| General / Airport & Station (Standard)
                            02| Gov. & Corp. / Office & School (Cinema)
                            03| Transportation (Sports)
                            04| Education / Control Room (Game)
                            05| Expert 1 / Expert(Bright Room)
                            08| Auto Power Save
                            11| Calibration / Expert (Dark Room)
                            12| Hospital
                          items:
                            type: string
                            enum:
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
                  type: object
                  description: 화면 백라이트
                  properties:
                    mode:
                      type: array
                      enum:
                        - r
                    type:
                      type: number
                      enum:
                        - number
                    value:
                      type: object
                      properties:
                        r:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 100
                            min:
                              type: integer
                              enum:
                                - 0
                            step:
                              type: integer
                              enum:
                                - 1
                brightness:
                  type: object
                  description: 화면 밝기
                  properties:
                    mode:
                      type: array
                      enum:
                        - r
                    type:
                      type: number
                      enum:
                        - number
                    value:
                      type: object
                      properties:
                        r:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 100
                            min:
                              type: integer
                              enum:
                                - 0
                            step:
                              type: integer
                              enum:
                                - 1
                tint:
                  type: object
                  description: 화면 색상
                  properties:
                    mode:
                      type: array
                      enum:
                        - r
                    type:
                      type: number
                      enum:
                        - number
                    value:
                      type: object
                      properties:
                        r:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 100
                            min:
                              type: integer
                              enum:
                                - 0
                            step:
                              type: integer
                              enum:
                                - 1
                contrast:
                  type: object
                  description: 화면 명암
                  properties:
                    mode:
                      type: array
                      enum:
                        - r
                    type:
                      type: number
                      enum:
                        - number
                    value:
                      type: object
                      properties:
                        r:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 100
                            min:
                              type: integer
                              enum:
                                - 0
                            step:
                              type: integer
                              enum:
                                - 1
                sharpness:
                  type: object
                  description: 화면 선명도
                  properties:
                    mode:
                      type: array
                      enum:
                        - r
                    type:
                      type: number
                      enum:
                        - number
                    value:
                      type: object
                      properties:
                        r:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 50
                            min:
                              type: integer
                              enum:
                                - 0
                            step:
                              type: integer
                              enum:
                                - 1
                color:
                  type: object
                  description: 화면 색농도
                  properties:
                    mode:
                      type: array
                      enum:
                        - r
                    type:
                      type: number
                      enum:
                        - number
                    value:
                      type: object
                      properties:
                        r:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 100
                            min:
                              type: integer
                              enum:
                                - 0
                            step:
                              type: integer
                              enum:
                                - 1
            audio:
              type: object
              description: 오디오
              properties:
                volume:
                  type: object
                  description: 음량 조정
                  properties:
                    mode:
                      type: array
                      items:
                        type: number
                        enum:
                          - r
                          - w
                    type:
                      type: number
                      enum:
                        - range
                    value:
                      type: object
                      properties:
                        r:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 100
                            min:
                              type: integer
                              enum:
                                - 0
                            step:
                              type: integer
                              enum:
                                - 1
                        w:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 100
                            min:
                              type: integer
                              enum:
                                - 0
                            step:
                              type: integer
                              enum:
                                - 1
                volumeMute:
                  type: object
                  description: 음소거
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                          - w
                    type:
                      type: string
                      enum:
                        - boolean
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 음소거
                            false | 음소거 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
                        w:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            true | 음소거
                            false | 음소거 해제
                          items:
                            type: boolean
                            enum:
                              - true
                              - false
                soundMode:
                  type: object
                  description: 음향 모드
                  properties:
                    mode:
                      type: array
                      items:
                        type: string
                        enum:
                          - r
                    type:
                      type: string
                      enum:
                        - enum
                    value:
                      type: object
                      properties:
                        r:
                          type: array
                          description: |-
                            Value | Description
                            -|-
                            01| 표준
                            02| 음악
                            03| 영화
                            04| 스포츠
                            05| 게임
                            08| 인공지능 사운드 프로
                            09| 클리어 보이스IV
                          items:
                            type: string
                            enum:
                              - '00'
                              - '01'
                              - '02'
                              - '03'
                              - '04'
                              - '05'
                              - '08'
                              - '09'
                soundBalance:
                  type: object
                  description: 음향 밸런스
                  properties:
                    mode:
                      type: array
                      enum:
                        - r
                    type:
                      type: number
                      enum:
                        - number
                    value:
                      type: object
                      properties:
                        r:
                          type: object
                          properties:
                            max:
                              type: integer
                              enum:
                                - 100
                            min:
                              type: integer
                              enum:
                                - 0
                            step:
                              type: integer
                              enum:
                                - 1
            temperature:
              type: object
              description: 온도
              properties:
                main:
                  type: object
                  description: 디바이스 온도 (섭씨)
                  properties:
                    mode:
                      type: array
                      enum:
                        - r
                    type:
                      type: number
                      enum:
                        - number
            info:
              type: object
              description: 디바이스 정보
              properties:
                osType:
                  type: object
                  description: 운영체제 종류
                  properties:
                    mode:
                      type: array
                      enum:
                        - r
                    type:
                      type: string
                      enum:
                        - WEBOS
                        - WINDOWS
                        - ANDROID
                        - NONE
        signage-object:
          title: SIGNAGE
          minProperties: 1
          properties:
            power:
              type: object
              description: 전원
              properties:
                power:
                  description: 전원 설정
                  type: boolean
                  enum:
                    - true
                    - false
                screen:
                  description: 화면 ON, OFF 상태
                  type: string
                  enum:
                    - SCREEN_ON
                    - SCREEN_OFF
                noSignalPowerOff:
                  description: 무신호 전원 꺼짐 설정
                  type: boolean
                  enum:
                    - true
                    - false
                noIrPowerOff:
                  description: IR 신호 없을 시 꺼짐 설정
                  type: boolean
                  enum:
                    - true
                    - false
                pmMode:
                  description: PM Mode 설정
                  type: string
                  enum:
                    - '00'
                    - '01'
                    - '02'
                    - '03'
                    - '04'
                    - '05'
                powerOnStatus:
                  description: 전원 켜기 상태
                  type: string
                  enum:
                    - '00'
                    - '01'
                    - '02'
                powerOnDelay:
                  description: 전원 켜기 지연
                  type: integer
                  example: 0
                energySavingMode:
                  description: 절전 모드
                  type: string
                  enum:
                    - '00'
                    - '01'
                    - '02'
                    - '03'
                    - '04'
                wol:
                  description: Wake On Lan 설정
                  type: boolean
                  enum:
                    - true
                    - false
            display:
              type: object
              description: 디스플레이
              properties:
                input:
                  description: 입력 신호 선택
                  type: string
                  enum:
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
                  description: OSD 언어 설정
                  type: string
                  enum:
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
                  description: 화면 잔상 방지
                  type: string
                  enum:
                    - '02'
                    - '04'
                    - '08'
                    - '90'
                    - '91'
                pictureMode:
                  description: 영상 모드
                  type: string
                  enum:
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
                  description: 화면 백라이트
                  type: ingeger
                  example: 80
                brightness:
                  description: 화면 밝기
                  type: ingeger
                  example: 80
                tint:
                  description: 화면 색상
                  type: ingeger
                  example: 50
                contrast:
                  description: 화면 명암
                  type: ingeger
                  example: 30
                sharpness:
                  description: 화면 선명도
                  type: ingeger
                  example: 0
                color:
                  description: 화면 색농도
                  type: ingeger
                  example: 40
            audio:
              type: object
              description: 오디오
              properties:
                volume:
                  description: 오디오 볼륨
                  type: integer
                  example: 10
                volumeMute:
                  description: 음소거
                  type: boolean
                  enum:
                    - true
                    - false
                soundMode:
                  description: 음향 모드
                  type: string
                  enum:
                    - '00'
                    - '01'
                    - '02'
                    - '03'
                    - '04'
                    - '05'
                    - '08'
                    - '09'
                soundBalance:
                  description: 음향 밸런스
                  type: ingeger
                  example: 50
            temperature:
              readOnly: true
              type: object
              description: 온도
              properties:
                main:
                  description: 디바이스 온도 (섭씨)
                  type: ingeger
                  example: 30
            info:
              readOnly: true
              type: object
              description: 디바이스 정보
              properties:
                osType:
                  description: 운영체제 종류
                  type: string
                  enum:
                    - WEBOS
                    - WINDOWS
                    - ANDROID
                    - NONE
        signage-command-schema:
          title: IDU
          minProperties: 1
          properties:
            상위 property:
              type: object
              properties:
                하위 property:
                  value: value
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
        refrigerator-command-example:
          description: 냉장고 - 절전 모드 설정
          value:
            powerSave:
              powerSaveEnabled: true
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
        washer-command-example:
          description: 세탁기 - 운전 시작
          value:
            location:
              locationName: MAIN
            operation:
              washerOperationMode: START
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
        dryer-command-example:
          description: 건조기 - 세탁 시작
          value:
            operation:
              dryerOperationMode: START
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
        air_conditioner-command-example:
          description: 에어컨 - 지정한 켜짐 예약시간
          value:
            timer:
              absoluteHourToStart: 10
              absoluteMinuteToStart: 36
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
        air_purifier-command-example:
          description: 공기청정기 - 운전 모드
          value:
            airPurifierJobMode:
              currentJobMode: CLEAN
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
        air_purifier_fan-command-example:
          description: 공기청정팬 - 운전 모드
          value:
            airFanJobMode:
              currentJobMode: SPOT_CLEAN
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
        dehumidifier-command-example:
          description: 가습기 - 운전 모드
          value:
            humidifierJobMode:
              currentJobMode: HUMIDIFY
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
        humidifier-command-example:
          title: Humidifier
          description: 가습기 - 운전 모드
          value:
            humidifierJobMode:
              currentJobMode: HUMIDIFY
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
        robot_cleaner-object-example:
          title: Robot_Cleaner
          value:
            runState:
              currentState: CHARGING
            robotCleanerJobMode:
              currentJobMode: ZIGZAG
            battery:
              level: FULL
        robot_cleaner-command-example:
          title: Robot_Cleaner
          description: 로봇청소기 - 청소 모드
          value:
            operation:
              cleanOperationMode: HOMING
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
        oven-command-example:
          title: Oven
          description: 오븐 - 오븐 동작
          value:
            location:
              locationName: LOWER
            operation:
              ovenOperationMode: START
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
        dish_washer-command-example:
          description: 식기세척기 - 운전 모드
          value:
            operation:
              dishWasherOperationMode: START
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
        styler-command-example:
          description: 스타일러 - 운전 모드
          value:
            operation:
              stylerOperationMode: START
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
        ceiling_fan-object-example:
          value:
            airFlow:
              windStrength: LOW
            operation:
              ceilingfanOperationMode: POWER_ON
        ceiling_fan-command-example:
          description: 실링팬 - 운전 모드
          value:
            operation:
              ceilingfanOperationMode: POWER_ON
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
        wine_cellar-command-example:
          description: 와인셀러 - 조명 밝기
          value:
            operation:
              lightStatus: 90
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
        washtower_washer-command-example:
          description: 워시타워 세탁기 - 세탁 시작
          value:
            operation:
              washerOperationMode: START
            location:
              locationName: MAIN
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
        washtower_dryer-command-example:
          description: 워시타워(건조기) - 전원 POWER_OFF
          value:
            operation:
              dryerOperationMode: POWER_OFF
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
        washtower-command-example:
          description: 워시타워 - 건조기 시작
          value:
            dryer:
              operation:
                dryerOperationMode: START
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
        cooktop-command-example:
          description: 쿡탑 - 전원 OFF
          value:
            operation:
              operationMode: POWER_OFF
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
        hood-command-example:
          description: 후드 - 램프 밝기
          value:
            lamp:
              lampBrightness: 0
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
        microwave_oven-command-example:
          description: 전자레인지
          value:
            lamp:
              lampBrightness: 1
            ventilation:
              fanSpeed: 0
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
        system_boiler-command-example:
          description: 시스템 보일러 - 전원 ON
          value:
            operation:
              boilerOperationMode: POWER_ON
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
        stick_cleaner-object-example:
          value:
            runState:
              currentState: STANDBY
            stickCleanerJobMode:
              currentJobMode: 'OFF'
            battery:
              level: HIGH
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
        water_heater-object-example:
          value:
            waterHeaterJobMode:
              currentJobMode: VACATION
            temperature:
              currentTemperature: 42
              targetTemperature: 52
            operation:
              waterHeaterOperationMode: POWER_ON
        water_heater-command-example:
          description: 온수기 - 운전모드
          value:
            waterHeaterJobMode:
              currentJobMode: AUTO
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
        main_washcombo-command-example:
          description: 워시콤보세탁기 메인 - 동작
          value:
            location:
              locationName: MAIN
            operation:
              washerOperationMode: START
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
        mini_washcombo-command-example:
          description: 워시콤보세탁기 미니 - 동작
          value:
            location:
              locationName: MINI
            operation:
              washerOperationMode: START
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
        signage-command-example:
          title: SIGNAGE
          value:
            power:
              screen: SCREEN_ON
    x-tagGroups:
      - name: Get Started
        tags:
          - overview
          - device type
      - name: LG ThinQ
        tags:
          - refrigerator
          - washer
          - dryer
          - air_conditioner
          - air_purifier
          - robot_cleaner
          - oven
          - dish_washer
          - styler
          - water_purifier
          - dehumidifier
          - ceiling_fan
          - wine_cellar
          - kimchi_refrigerator
          - home_brew
          - plant_cultivator
          - washtower_washer
          - washtower_dryer
          - washtower
          - cooktop
          - hood
          - microwave_oven
          - system_boiler
          - air_purifier_fan
          - stick_cleaner
          - water_heater
          - main_washcombo
          - mini_washcombo
          - humidifier
      - name: LG BECON Cloud
        tags:
          - odu
          - idu
      - name: LG Business Cloud
        tags:
          - signage
---
