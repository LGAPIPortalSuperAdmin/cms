---
contents:
  lang: yaml
  code: >
    openapi: 3.1.0

    info:
      version: null
      title: ThinQ Connect API
    servers:
      - url: https://api-kic.lgthinq.com
      - url: https://api-aic.lgthinq.com
      - url: https://api-eic.lgthinq.com
    tags:
      - name: PAT(Personal Access Token)
        description: |
          Identification tokens used to call ThinQ API. The Identification tokens can only be used for personal and non-commercial purposes. To develop additional services not sanctioned by LG Electronics, the developer must discuss the matter regarding the additional services with LG Electronics, and then acquire a written consent from LG Electronics.
            1. Visit the website: https://connect-pat.lgthinq.com
            2. Log in on the ThinQ account.
            3. Select the "Create New Token" button.
            4. Enter Token name.
            5. Select a feature you want.
            6. Select the "Create Token" button, and the token will be created. You will then be redirected to the PAT page.
            7. Copy the newly generated token for use.
      - name: Device API
        description: |
          API used to request ThinQ device information and control the device.
      - name: Push API
        description: |
          API used to subscribe to/unsubscribe the push messages generated from the ThinQ devices.
      - name: Event API
        description: |
          API used to subscribe to/unsubscribe the event messages generated from the ThinQ devices when their statuses change.
      - name: Client API
        description: |
          API used to issue/register user device authentication certificate for receiving messages delivered from the ThinQ devices.  
    paths:
      /devices:
        get:
          tags:
            - Device API
          summary: Get device list
          description: |
            API for getting a list of devices that have been registered on the ThinQ Platform. It must be called at least once before using any other APIs. The list of devices returned by this API contains a device-id to identify the device, which can be used to call other device APIs by specifying the target device. Therefore, this API must be called the first time, but does not need to be called every time after the device list is resolved.      parameters:
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
          summary: Get Device Profile
          description: API for viewing device profiles > Device profiles are information describing the attributes of an LG home appliance and are the device data used by the LG ThinQ platform.
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
                    Refrigerator:
                      $ref: '#/components/examples/refrigerator-profile-example'
                    Water Purifier:
                      $ref: '#/components/examples/water_purifier-profile-example'
                    Wine Cellar:
                      $ref: '#/components/examples/wine_cellar-profile-example'
                    Kimchi Refrigerator:
                      $ref: '#/components/examples/kimchi_refrigerator-profile-example'
                    Home Brew:
                      $ref: '#/components/examples/home_brew-profile-example'
                    Plant Cultivator:
                      $ref: '#/components/examples/plant_cultivator-profile-example'
                    Washer:
                      $ref: '#/components/examples/washer-profile-example'
                    Dryer:
                      $ref: '#/components/examples/dryer-profile-example'
                    Styler:
                      $ref: '#/components/examples/styler-profile-example'
                    Dish Washer:
                      $ref: '#/components/examples/dish_washer-profile-example'
                    WashTower Washer:
                      $ref: '#/components/examples/washtower_washer-profile-example'
                    WashTower Dryer:
                      $ref: '#/components/examples/washtower_dryer-profile-example'
                    WashTower (Single Unit):
                      $ref: '#/components/examples/washtower-profile-example'
                    Main WashCombo:
                      $ref: '#/components/examples/main_washcombo-profile-example'
                    Mini WashCombo:
                      $ref: '#/components/examples/mini_washcombo-profile-example'
                    Oven:
                      $ref: '#/components/examples/oven-profile-example'
                    Cooktop:
                      $ref: '#/components/examples/cooktop-profile-example'
                    Hood:
                      $ref: '#/components/examples/hood-profile-example'
                    Microwave Oven:
                      $ref: '#/components/examples/microwave_oven-profile-example'
                    Air Conditioner:
                      $ref: '#/components/examples/air_conditioner-profile-example'
                    System Boiler:
                      $ref: '#/components/examples/system_boiler-profile-example'
                    Air Purifier:
                      $ref: '#/components/examples/air_purifier-profile-example'
                    Dehumidifier:
                      $ref: '#/components/examples/dehumidifier-profile-example'
                    Humidifier:
                      $ref: '#/components/examples/humidifier-profile-example'
                    Water Heater:
                      $ref: '#/components/examples/water_heater-profile-example'
                    Ceiling Fan:
                      $ref: '#/components/examples/ceiling_fan-profile-example'
                    Air Purifier Fan:
                      $ref: '#/components/examples/air_purifier_fan-profile-example'
                    Robot Cleaner:
                      $ref: '#/components/examples/robot_cleaner-profile-example'
                    Stick Cleaner:
                      $ref: '#/components/examples/stick_cleaner-profile-example'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /devices/{deviceId}/state:
        get:
          tags:
            - Device API
          summary: Device status inquiry
          description: API for viewing the current status of a device. You can retrieve the current status of the specified device-id.
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
                    Refrigerator:
                      $ref: '#/components/examples/refrigerator-object-example'
                    Water Purifier:
                      $ref: '#/components/examples/water_purifier-object-example'
                    Wine Cellar:
                      $ref: '#/components/examples/wine_cellar-object-example'
                    Kimchi Refrigerator:
                      $ref: '#/components/examples/kimchi_refrigerator-object-example'
                    Home Brew:
                      $ref: '#/components/examples/home_brew-object-example'
                    Plant Cultivator:
                      $ref: '#/components/examples/plant_cultivator-object-example'
                    Washer:
                      $ref: '#/components/examples/washer-object-example'
                    Dryer:
                      $ref: '#/components/examples/dryer-object-example'
                    Styler:
                      $ref: '#/components/examples/styler-object-example'
                    Dish Washer:
                      $ref: '#/components/examples/dish_washer-object-example'
                    WashTower Washer(Washer):
                      $ref: '#/components/examples/washtower_washer-object-example'
                    WashTower Washer(Dryer):
                      $ref: '#/components/examples/washtower_dryer-object-example'
                    WashTower (Single Unit):
                      $ref: '#/components/examples/washtower-object-example'
                    Main WashCombo:
                      $ref: '#/components/examples/main_washcombo-object-example'
                    Mini WashCombo:
                      $ref: '#/components/examples/mini_washcombo-object-example'
                    Oven:
                      $ref: '#/components/examples/oven-object-example'
                    Cooktop:
                      $ref: '#/components/examples/cooktop-object-example'
                    Hood:
                      $ref: '#/components/examples/hood-object-example'
                    Microwave Oven:
                      $ref: '#/components/examples/microwave_oven-object-example'
                    Air Conditioner:
                      $ref: '#/components/examples/air_conditioner-object-example'
                    System Boiler:
                      $ref: '#/components/examples/system_boiler-object-example'
                    Air Purifier:
                      $ref: '#/components/examples/air_purifier-object-example'
                    Dehumidifier:
                      $ref: '#/components/examples/dehumidifier-object-example'
                    Humidifier:
                      $ref: '#/components/examples/humidifier-object-example'
                    Water Heater:
                      $ref: '#/components/examples/water_heater-object-example'
                    Ceiling Fan:
                      $ref: '#/components/examples/ceiling_fan-object-example'
                    Air Purifier Fan:
                      $ref: '#/components/examples/air_purifier_fan-object-example'
                    Robot Cleaner:
                      $ref: '#/components/examples/robot_cleaner-object-example'
                    Stick Cleaner:
                      $ref: '#/components/examples/stick_cleaner-object-example'
            '400':
              description: Bad request
            '401':
              description: Unauthorized
      /devices/{deviceId}/control:
        post:
          tags:
            - Device API
          summary: Control Device
          description: API for controlling devices. You can send control commands to the specified device-id.
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
                  description: a control command for the device based on the device profile information.
                examples:
                  Refrigerator:
                    $ref: '#/components/examples/refrigerator-command-example'
                  Wine Cellar:
                    $ref: '#/components/examples/wine_cellar-command-example'
                  Washer:
                    $ref: '#/components/examples/washer-command-example'
                  Dryer:
                    $ref: '#/components/examples/dryer-command-example'
                  Styler:
                    $ref: '#/components/examples/styler-command-example'
                  Dish Washer:
                    $ref: '#/components/examples/dish_washer-command-example'
                  WashTower Washer(Washer):
                    $ref: '#/components/examples/washtower_washer-command-example'
                  WashTower Washer(Dryer):
                    $ref: '#/components/examples/washtower_dryer-command-example'
                  WashTower (Single Unit):
                    $ref: '#/components/examples/washtower-command-example'
                  Main WashCombo:
                    $ref: '#/components/examples/main_washcombo-command-example'
                  Mini WashCombo:
                    $ref: '#/components/examples/mini_washcombo-command-example'
                  Oven:
                    $ref: '#/components/examples/oven-command-example'
                  Cooktop:
                    $ref: '#/components/examples/cooktop-command-example'
                  Hood:
                    $ref: '#/components/examples/hood-command-example'
                  Microwave Oven:
                    $ref: '#/components/examples/microwave_oven-command-example'
                  Air Conditioner:
                    $ref: '#/components/examples/air_conditioner-command-example'
                  System Boiler:
                    $ref: '#/components/examples/system_boiler-command-example'
                  Air Purifier:
                    $ref: '#/components/examples/air_purifier-command-example'
                  Dehumidifier:
                    $ref: '#/components/examples/dehumidifier-command-example'
                  Humidifier:
                    $ref: '#/components/examples/humidifier-command-example'
                  Water Heater:
                    $ref: '#/components/examples/water_heater-command-example'
                  Ceiling Fan:
                    $ref: '#/components/examples/ceiling_fan-command-example'
                  Air Purifier Fan:
                    $ref: '#/components/examples/air_purifier_fan-command-example'
                  Robot Cleaner:
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
          summary: Get Device List under Subscribtion
          description: Gets a list of the user's devices from which the user is receiving Push notifications.
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
          summary: Subscribed to Push notifications of the device.
          description: Subscription requests to receive push notifications from devices
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
          summary: Unsubscribed to Push notifications of the device
          description: Requests to cancel subscriptions to the Push notifications of the device
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
          summary: Get a list of clients subscribed to device add/delete notifications.
          description: Get a list of clients where users have requested subscriptions to add/delete/change devices.
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
          summary: Subscribe to the Add/Delete Device Notification Client
          description: Request to register client to receive device add/delete/change subscription
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
          summary: Unsubscribe to the Add/Delete Device Notification Client
          description: Request to register client to receive device add/delete/change subscription
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
          summary: Get a list of device event subscriptions.
          description: Get a list of devices to which users are subscribed to device status notifications.
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
          summary: Subscribe to Device Events
          description: Unsubscribes to events of the device when the device status changes
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
          summary: Unsubscribe to Device Events.
          description: Unsubscribes to events of the device when the device status changes.
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
          summary: Issuing client certificates
          description: Verify the client's AWS IoT certificate, subscribable MQTT Topic
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
          summary: Client registration
          description: Client registration
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
          summary: Client deactivation
          description: Client deactivation
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
        Authorization:
          name: Authorization
          in: header
          schema:
            type: string
          description: |
            PAT token received via https://connect-pat.lgthinq.com
          example: Bearer 4d76546d61f01baf31c1sd8f6b4e38b110ba0a34f825b8c5d54c
        x-message-id:
          name: x-message-id
          in: header
          schema:
            type: string
          description: |
            This value is for tracking the information being requested. You can track the flow of a particular API and find the cause of errors when they occur. The generation rules are as follows:
                Generated with the url-safe-base64-no-padding (UUID Version 4) method.
                The length is 22 characters.
          example: fNvdZ1brTn-wWKUlWGoSVw
        x-country:
          name: x-country
          in: header
          schema:
            type: string
          description: |
            Specify the country where you want to provide the service. Follow the two digits of the ISO country code alphabet (ISO 3166-1 alpha-2) (e.g., KR, US, GB, ...)
          example: KR
        x-client-id:
          name: x-client-id
          in: header
          schema:
            type: string
          description: |
            The identifier ID of the requesting client. It should be generated so that it has a unique value.
          example: test-client-123456
        x-api-key:
          name: x-api-key
          in: header
          schema:
            type: string
          description: |
            API key for making API calls. Modify the value below to make the call. ""
          example: default value
        x-conditional-control:
          name: x-conditional-control
          in: header
          schema:
            type: boolean
          description: |
            Activate control only in controllable states after Device status inquiry
          example: true
      schemas:
        base-res:
          type: object
          description: Response Object for any device
          properties:
            messageId:
              type: string
              description: The X-Message-ID included in the header of the request. Include this value in the response message so that you can see if there are any problems.
              example: fNvdZ1brTn-wWKUlWGoSVw
            timestamp:
              type: string
              description: The time when the request came in, following the ISO 8601 format.
              example: '2024-09-01T06:23:20.866279'
        device-list-res:
          description: Device list inquiry response
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
                        description: An ID that can identify the device
                        example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
                      deviceInfo:
                        type: object
                        description: An object containing the followings
                        properties:
                          deviceType:
                            type: string
                            description: The device type
                            example: DEVICE_AIR_CONDITIONER
                          modelName:
                            type: string
                            description: The (device) model name
                            example: PAC_910604_WW
                          alias:
                            type: string
                            description: The device alias name
                            example: living room Air Conditioner
                          reportable:
                            type: boolean
                            description: Whether or not your service is subscribing to events which occur when the device status changes
                            example: true
                          groupId:
                            type: string
                            description: groupId. Value for displaying the Washtower group value where Washtower washers and Washtower dryers are separated by a device identification Id.
                            example: '234506858'
        device-profile-res:
          description: Device profile inquiry response
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: Device Profile
                  example:
                    '-$ref': ../../../device-profile/air_conditioner/air_conditioner-profile-example.yaml
        device-state-res:
          description: Device status inquiry response
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: Device Status
                  example:
                    '-$ref': ../../../device-profile/air_conditioner/air_conditioner-profile-example.yaml
        device-control-res:
          description: Control Device response
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: An empty dictionay is passed on success
                  example: {}
        push-list-res:
          description: Push list inquiry response
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
                        description: Device id that subscribed to the push
                        example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
        push-deviceId-res:
          description: Push subscription/unsubscription responses
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: An empty dictionay is passed on success
                  example: {}
        push-client-list-res:
          description: User push clientId list inquiry response
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
          description: Event subscription list inquiry response
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
                        description: Device Id that subscribed to events
                        example: eb8ce6a99e63beb7e2074409bc244f3fd6c534e40ca270b6895371f12b398660
        event-register-req:
          description: Subscribe to Device Events body
          type: object
          properties:
            expire:
              type: object
              description: If you set an API expiration time or subscribe to it and the expiration time passes, the previously subscribed device is automatically turned off. If you subscribe to the device again, the expiration time will be renewed.
              properties:
                unit:
                  type: string
                  description: unit of time (default value - HOUR)
                  example: HOUR
                timer:
                  type: integer
                  description: |
                    The expiration time of the event subscription. (min: 1, max: 24, default: 1) 
                  example: 1
        event-deviceId-res:
          description: Event subscription/unsubscription responses
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: An empty dictionay is passed on success
                  example: {}
        client-certificate-req:
          description: Client authentication body
          type: object
          properties:
            body:
              type: object
              description: user's information
              properties:
                service-code:
                  type: string
                  description: Service Code (fixed value - SVC202)
                  example: SVC202
                csr:
                  type: string
                  description: CSR data based on the device's self-generated private key
                  example: '===xzx'
        client-certificate-res:
          description: Client certificate enrollment response
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: object
                  properties:
                    resultCode:
                      type: string
                      description: Result response code
                      example: '0000'
                    result:
                      type: object
                      properties:
                        certificatePem:
                          type: string
                          description: AWS IoT Certificate
                          example: |
                            -----BEGIN CERTIFICATE-----
                            MIIEUzCCAzugAw
                            -----END CERTIFICATE-----
                        subscriptions:
                          type: array
                          desription: List of topics that require MQTT subscriptions on the client (List)
                          example:
                            - app/clients/home-assistant-test-01234/push
        client-register-req:
          description: Client subscription body
          type: object
          properties:
            body:
              type: object
              description: user's information
              properties:
                type:
                  type: string
                  description: Push type (fixed value - MQTT)
                  example: MQTT
                service-code:
                  type: string
                  description: Service Code (fixed value - SVC202)
                  example: SVC202
                device-type:
                  type: string
                  description: Client device type (fixed value - 607)
                  example: '607'
        client-res:
          description: Client Subscribe/Unsubscribe Response
          allOf:
            - $ref: '#/components/schemas/base-res'
            - type: object
              properties:
                response:
                  type: object
                  description: An empty dictionay is passed on success
                  example: {}
        client-unregister-req:
          description: Client unsubscription body
          type: object
          properties:
            body:
              type: object
              description: user's information
              properties:
                type:
                  type: string
                  description: Push type (fixed value - MQTT)
                  example: MQTT
                service-code:
                  type: string
                  description: Service Code (fixed value - SVC202)
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
          description: Refrigerator - Power Save On
          value:
            powerSave:
              powerSaveEnabled: true
        wine_cellar-command-example:
          description: Wine Cellar - light Brightness
          value:
            operation:
              lightStatus: 90
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
        styler-command-example:
          description: Styler - stylerOperationMode
          value:
            operation:
              stylerOperationMode: START
        dish_washer-command-example:
          description: Dish Washer - washerOperationMode
          value:
            operation:
              dishWasherOperationMode: START
        washtower_washer-command-example:
          description: WashTower Washer Washer - Start washing
          value:
            operation:
              washerOperationMode: START
            location:
              locationName: MAIN
        washtower_dryer-command-example:
          description: WashTower Washer(Dryer) - POWER_OFF
          value:
            operation:
              dryerOperationMode: POWER_OFF
        washtower-command-example:
          description: WashTower Washer - Start drying
          value:
            dryer:
              operation:
                dryerOperationMode: START
        main_washcombo-command-example:
          description: Main WashCombo - runState / operation
          value:
            location:
              locationName: MAIN
            operation:
              washerOperationMode: START
        mini_washcombo-command-example:
          description: Mini WashCombo - runState / operation
          value:
            location:
              locationName: MINI
            operation:
              washerOperationMode: START
        oven-command-example:
          title: Oven
          description: Oven -  ovenOperationMode
          value:
            location:
              locationName: LOWER
            operation:
              ovenOperationMode: START
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
        air_conditioner-command-example:
          description: Air Conditioner - Set On Timer 
          value:
            timer:
              absoluteHourToStart: 10
              absoluteMinuteToStart: 36
        system_boiler-command-example:
          description: System Boiler - Power ON
          value:
            operation:
              boilerOperationMode: POWER_ON
        air_purifier-command-example:
          description: Air Purifier - Run mode
          value:
            airPurifierJobMode:
              currentJobMode: CLEAN
        dehumidifier-command-example:
          description: Humidifier - humidifierJobMode
          value:
            humidifierJobMode:
              currentJobMode: HUMIDIFY
        humidifier-command-example:
          title: Humidifier
          description: Humidifier - humidifierJobMode
          value:
            humidifierJobMode:
              currentJobMode: HUMIDIFY
        water_heater-command-example:
          description: Water Heater - waterHeaterJobMode 
          value:
            waterHeaterJobMode:
              currentJobMode: AUTO
        ceiling_fan-command-example:
          description: Ceiling Fan - ceilingfanOperationMode
          value:
            operation:
              ceilingfanOperationMode: POWER_ON
        air_purifier_fan-command-example:
          description: Air Purifier Fan - airFanJobMode
          value:
            airFanJobMode:
              currentJobMode: SPOT_CLEAN
        robot_cleaner-command-example:
          title: Robot_Cleaner
          description: Robot Cleaner - robotCleanerJobMode
          value:
            operation:
              cleanOperationMode: HOMING
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
---
