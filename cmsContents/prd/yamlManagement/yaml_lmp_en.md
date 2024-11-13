---
contents:
  lang: yaml
  code: >
    openapi: 3.1.0

    info:
      title: LGE Members Platform
      version: v0.8.3
    servers:
      - url: http://localhost:8080
        description: Generated server url
    tags:
      - name: Overview
        x-displayName: 소개
        description: |

          본 페이지는 LGE Members Platform을 사용하기 위한 OAuth 2.0 API에 대해 기술합니다.  
            
          LG전자 로그인 절차는 인증 요청 API (/auth), 토큰 발급(갱신)/삭제 APIs (/token, /revoke) 등으로 구성되어 있습니다.  
          - /auth : LG전자 회원 로그인 페이지를 통해 인증을 시작하는 API
          - /token : LG전자 회원 인증 토큰을 얻는 API
          - /revoke : LG전자 회원 인증 토큰을 비활성화하는 API
          - /introspect : LG전자 회원 인증 토큰을 검증하는 API
          - /userinfo : LG전자 회원 인증 토큰에 대한 간단한 사용자 정보를 얻는 API
            
          발급된 Access Token으로 공개된 LG전자 리소스 서버의 API를 사용하실 수 있습니다.  
          아래는 공개된 LG전자의 리소스 서버 목록입니다.  
          - IoT 서버 : 링크
          - 기타 서버 : 링크
            
          (안내) client_id와 secret는 LG전자 관리자 페이지 (xxx)를 통해 생성하세요.  
          - 링크
      - name: Authentication
        x-displayName: 인증
        description: |

          인증(Authentication)은 LG전자 회원 계정에 접근을 요청한 사용자가 실제 소유자인지 확인하는 절차입니다.  
          인증 방법의 대표적인 방법은 ID와 Password를 확인하는 것 입니다.
      - name: Authorization
        x-displayName: 인가
        description: |

          인가(Authorization)는 서비스에서 요청한 사용자 동의 필요 정보 또는 접근권한 필요 기능을 
          LGE Members Platform이 제공해도 될지 사용자에게 동의를 구하는 일입니다.  
          LGE Members Platform은 사용자에게 인가받지 않은 자원을 서비스에 제공하지 않습니다.  
      - name: Token
        x-displayName: 토큰
        description: |

          토큰은 LG전자 회원의 인증과 권한 정보를 담은 문자열입니다. 서비스는 인가 결과로 발급받은 인가 코드로 토큰 발급을 요청할 수 있고,  
          발급받은 토큰을 API 요청에 포함해서 정보 수신 또는 기능 사용 권한이 있음을 증명할 수 있습니다.  
          LGE Members Platform은 OAuth 2.0 표준 규격에 따라 엑세스 토큰(Access Token), 리프레시 토큰(Refresh Token) 두 종류의 토큰을 발급합니다.  
          - 토큰별 역할
            - 엑세스 토큰
              - 사용자 인증 및 보유 권한을 증명
            - 리프레시 토큰
              - 추가 인증 없이 엑세스 토큰 갱신
      - name: API Call Sequence
        x-displayName: API 호출 시퀀스
        description: |

          <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" contentStyleType="text/css" height="856px" preserveAspectRatio="none" style="width:839px;height:856px;background:#FFFFFF;" version="1.1" viewBox="0 0 839 856" width="839px" zoomAndPan="magnify"><defs/><g><text fill="#000000" font-family="sans-serif" font-size="14" font-weight="bold" lengthAdjust="spacing" textLength="45.083" x="395.4763" y="27.9951">token</text><rect fill="#FFFFFF" height="29.1328" style="stroke:#181818;stroke-width:1.0;" width="10" x="100.8511" y="178.8594"/><rect fill="#FFFFFF" height="184.6016" style="stroke:#181818;stroke-width:1.0;" width="10" x="100.8511" y="529.9297"/><rect fill="#FFFFFF" height="607.9375" style="stroke:#181818;stroke-width:1.0;" width="10" x="318.7329" y="149.7266"/><rect fill="#FFFFFF" height="205.4063" style="stroke:#181818;stroke-width:1.0;" width="10" x="740.6011" y="237.125"/><rect fill="#FFFFFF" height="29.1328" style="stroke:#181818;stroke-width:1.0;" width="10" x="740.6011" y="471.6641"/><rect fill="#FFFFFF" height="126.3359" style="stroke:#181818;stroke-width:1.0;" width="10" x="740.6011" y="559.0625"/><rect fill="none" height="442.2734" style="stroke:#000000;stroke-width:1.5;" width="764.6899" x="58.5859" y="287.2578"/><rect fill="none" height="148.4688" style="stroke:#000000;stroke-width:1.5;" width="744.6899" x="68.5859" y="574.0625"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="36" x2="36" y1="118.5938" y2="775.6641"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="105.5859" x2="105.5859" y1="118.5938" y2="775.6641"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="323.0332" x2="323.0332" y1="118.5938" y2="775.6641"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="744.9263" x2="744.9263" y1="118.5938" y2="775.6641"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="57.5859" x="5" y="115.292">Member</text><ellipse cx="36.793" cy="50.7969" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M36.793,58.7969 L36.793,85.7969 M23.793,66.7969 L49.793,66.7969 M36.793,85.7969 L23.793,100.7969 M36.793,85.7969 L49.793,100.7969 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="57.5859" x="5" y="787.6592">Member</text><ellipse cx="36.793" cy="799.4609" fill="#E2E2F0" rx="8" ry="8" style="stroke:#181818;stroke-width:0.5;"/><path d="M36.793,807.4609 L36.793,834.4609 M23.793,815.4609 L49.793,815.4609 M36.793,834.4609 L23.793,849.4609 M36.793,834.4609 L49.793,849.4609 " fill="none" style="stroke:#181818;stroke-width:0.5;"/><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="54.5303" x="78.5859" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="40.5303" x="85.5859" y="107.292">Client</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="54.5303" x="78.5859" y="774.6641"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="40.5303" x="85.5859" y="794.6592">Client</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="107.3994" x="270.0332" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="93.3994" x="277.0332" y="107.292">User Browser</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="107.3994" x="270.0332" y="774.6641"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="93.3994" x="277.0332" y="794.6592">User Browser</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="115.3496" x="687.9263" y="87.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="101.3496" x="694.9263" y="107.292">LGE-MP OAuth</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="115.3496" x="687.9263" y="774.6641"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="101.3496" x="694.9263" y="794.6592">LGE-MP OAuth</text><rect fill="#FFFFFF" height="29.1328" style="stroke:#181818;stroke-width:1.0;" width="10" x="100.8511" y="178.8594"/><rect fill="#FFFFFF" height="184.6016" style="stroke:#181818;stroke-width:1.0;" width="10" x="100.8511" y="529.9297"/><rect fill="#FFFFFF" height="607.9375" style="stroke:#181818;stroke-width:1.0;" width="10" x="318.7329" y="149.7266"/><rect fill="#FFFFFF" height="205.4063" style="stroke:#181818;stroke-width:1.0;" width="10" x="740.6011" y="237.125"/><rect fill="#FFFFFF" height="29.1328" style="stroke:#181818;stroke-width:1.0;" width="10" x="740.6011" y="471.6641"/><rect fill="#FFFFFF" height="126.3359" style="stroke:#181818;stroke-width:1.0;" width="10" x="740.6011" y="559.0625"/><polygon fill="#181818" points="306.7329,145.7266,316.7329,149.7266,306.7329,153.7266,310.7329,149.7266" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="36.793" x2="312.7329" y1="149.7266" y2="149.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="43.793" y="144.6606">1</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="58.1001" x="56.8384" y="144.6606">Click link</text><polygon fill="#181818" points="121.8511,174.8594,111.8511,178.8594,121.8511,182.8594,117.8511,178.8594" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="115.8511" x2="317.7329" y1="178.8594" y2="178.8594"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="127.8511" y="173.7935">2</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="148.605" x="140.8965" y="173.7935">Access protected page</text><polygon fill="#181818" points="306.7329,203.9922,316.7329,207.9922,306.7329,211.9922,310.7329,207.9922" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="105.8511" x2="312.7329" y1="207.9922" y2="207.9922"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="112.8511" y="202.9263">3</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="166.2197" x="125.8965" y="202.9263">redirect to LGE-MP OAuth</text><polygon fill="#181818" points="728.6011,233.125,738.6011,237.125,728.6011,241.125,732.6011,237.125" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="328.7329" x2="734.6011" y1="237.125" y2="237.125"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="335.7329" y="232.0591">4</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="130.8125" x="348.7783" y="232.0591">NTH.002(GET /auth)</text><path d="M658,250.125 L658,275.125 L832,275.125 L832,260.125 L822,250.125 L658,250.125 " fill="#FEFFDD" style="stroke:#181818;stroke-width:0.5;"/><path d="M822,250.125 L822,260.125 L832,260.125 L822,250.125 " fill="#FEFFDD" style="stroke:#181818;stroke-width:0.5;"/><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="153.0356" x="664" y="267.1919">Member Authentication</text><path d="M58.5859,287.2578 L123.0288,287.2578 L123.0288,294.3906 L113.0288,304.3906 L58.5859,304.3906 L58.5859,287.2578 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="442.2734" style="stroke:#000000;stroke-width:1.5;" width="764.6899" x="58.5859" y="287.2578"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="19.4429" x="73.5859" y="300.3247">alt</text><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="172.7236" x="138.0288" y="299.4683">[redirect_uri/client_id Error]</text><polygon fill="#181818" points="339.7329,321.5234,329.7329,325.5234,339.7329,329.5234,335.7329,325.5234" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="333.7329" x2="739.6011" y1="325.5234" y2="325.5234"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="345.7329" y="320.4575">5</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="175.8364" x="358.7783" y="320.4575">Error Message for NTH.002</text><line style="stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="58.5859" x2="823.2759" y1="334.5234" y2="334.5234"/><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="40.2886" x="63.5859" y="344.7339">[&#44536;&#50808; &#50724;&#47448;]</text><polygon fill="#181818" points="339.7329,365.4609,329.7329,369.4609,339.7329,373.4609,335.7329,369.4609" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="333.7329" x2="739.6011" y1="369.4609" y2="369.4609"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="345.7329" y="364.395">6</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="374.8228" x="358.7783" y="364.395">redirect to {redirect_uri} with Error Message for NTH.002</text><polygon fill="#181818" points="116.8511,394.5938,106.8511,398.5938,116.8511,402.5938,112.8511,398.5938" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="110.8511" x2="317.7329" y1="398.5938" y2="398.5938"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="122.8511" y="393.5278">7</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="175.8364" x="135.8965" y="393.5278">Error Message for NTH.002</text><line style="stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="58.5859" x2="823.2759" y1="407.5938" y2="407.5938"/><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="209.8057" x="63.5859" y="417.8042">[Member Authentication Success]</text><polygon fill="#181818" points="339.7329,438.5313,329.7329,442.5313,339.7329,446.5313,335.7329,442.5313" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="333.7329" x2="744.6011" y1="442.5313" y2="442.5313"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="345.7329" y="437.4653">8</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="249.4565" x="358.7783" y="437.4653">Delegation of Authority_Consent .html</text><polygon fill="#181818" points="728.6011,467.6641,738.6011,471.6641,728.6011,475.6641,732.6011,471.6641" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="328.7329" x2="734.6011" y1="471.6641" y2="471.6641"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="335.7329" y="466.5981">9</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="296.499" x="348.7783" y="466.5981">Submit Delegation of Authority_Consent form</text><polygon fill="#181818" points="339.7329,496.7969,329.7329,500.7969,339.7329,504.7969,335.7329,500.7969" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="333.7329" x2="744.6011" y1="500.7969" y2="500.7969"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="18.0908" x="345.7329" y="495.731">10</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="186.9702" x="367.8237" y="495.731">redirect to client with "code"</text><polygon fill="#181818" points="121.8511,525.9297,111.8511,529.9297,121.8511,533.9297,117.8511,529.9297" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="115.8511" x2="317.7329" y1="529.9297" y2="529.9297"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="18.0908" x="127.8511" y="524.8638">11</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="31.3511" x="149.9419" y="524.8638">code</text><polygon fill="#181818" points="728.6011,555.0625,738.6011,559.0625,728.6011,563.0625,732.6011,559.0625" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="110.8511" x2="734.6011" y1="559.0625" y2="559.0625"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="18.0908" x="117.8511" y="553.9966">12</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="138.0869" x="139.9419" y="553.9966">NTH.003(GET /token)</text><path d="M68.5859,574.0625 L133.0288,574.0625 L133.0288,581.1953 L123.0288,591.1953 L68.5859,591.1953 L68.5859,574.0625 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="148.4688" style="stroke:#000000;stroke-width:1.5;" width="744.6899" x="68.5859" y="574.0625"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="19.4429" x="83.5859" y="587.1294">alt</text><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="138.3057" x="148.0288" y="586.2729">[success case 200 OK]</text><polygon fill="#181818" points="121.8511,608.3281,111.8511,612.3281,121.8511,616.3281,117.8511,612.3281" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="115.8511" x2="739.6011" y1="612.3281" y2="612.3281"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="18.0908" x="127.8511" y="607.2622">13</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="215.0015" x="149.9419" y="607.2622">Access Token and Refresh Token</text><polygon fill="#181818" points="306.7329,637.4609,316.7329,641.4609,306.7329,645.4609,310.7329,641.4609" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="110.8511" x2="312.7329" y1="641.4609" y2="641.4609"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="18.0908" x="117.8511" y="636.395">14</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="135.8525" x="139.9419" y="636.395">protected_page.html</text><line style="stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="68.5859" x2="813.2759" y1="650.4609" y2="650.4609"/><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="104.0381" x="73.5859" y="660.6714">[error case NOK]</text><polygon fill="#181818" points="121.8511,681.3984,111.8511,685.3984,121.8511,689.3984,117.8511,685.3984" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="115.8511" x2="744.6011" y1="685.3984" y2="685.3984"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="18.0908" x="127.8511" y="680.3325">15</text><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="198.4468" x="149.9419" y="680.3325">Error Message for NTH.003</text><polygon fill="#181818" points="306.7329,710.5313,316.7329,714.5313,306.7329,718.5313,310.7329,714.5313" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="105.8511" x2="312.7329" y1="714.5313" y2="714.5313"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="18.0908" x="112.8511" y="709.4653">16</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="128.4004" x="134.9419" y="709.4653">access_denied.html</text><polygon fill="#181818" points="47.793,753.6641,37.793,757.6641,47.793,761.6641,43.793,757.6641" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="41.793" x2="322.7329" y1="757.6641" y2="757.6641"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="18.0908" x="53.793" y="752.5981">17</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="70.1987" x="75.8838" y="752.5981">show page</text><!--SRC=[XLFDRXD133vddiBQ4rMrRTJUgX2fbAX8q1RHS5xDpZhDA9DnD3-D4E8zoXsUWJuJz27mUfCeYu0ULbhP_lpv- -pHEP7Fong3KiacXv1eWLufRH85AAwmpHMW8-IeLZeaQ-nA-mJ5XRFeawICwwS-HWpmAj0wRh5rl-3TvQIyUWytvpdDfS2HKZb2EURImqCu0-vk5k2iNwXSjt7Z97vk3CO8gq09JS86LleEbN5G2hOikIPWOmDdMGliCsqwEP9ErzCtHyFXoOlBoHIEDQSFbFBS5UYUftV49PrwQB4irHgTBBNUkBJZg7AmnqQig6m3an0eg04JZNWKQI8XRXKZJmep_jymAtGHuUUFnwUlZ_3qyEtNzuS-Sb_7vtt2Bx2sQVwVpeEjPy_p_rKZt6RnMUt6ASipU8qExxeypGH1mQPFrGNvo5WucgUbKtsNRtEzjEbPA8-rL05J3hudktEsariOQh1G_NjeOxB-F_PwskrLhlb0DXOxIM0qgpuP3k7chHgmp-NMgCrfJLi8QD_01vm5ZFCkibkDrExkhshlhnCkTgAuBHpNBS56qsX6BCEGe_2IzOr7zVXVUpdjCscPgchGMsmwea63_3pjlKweq3VoRSsBSrhBc_WD]--></g></svg>
            
          토큰 발급 시퀀스입니다.
            
          <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" contentStyleType="text/css" height="262px" preserveAspectRatio="none" style="width:362px;height:262px;background:#FFFFFF;" version="1.1" viewBox="0 0 362 262" width="362px" zoomAndPan="magnify"><defs/><g><text fill="#000000" font-family="sans-serif" font-size="14" font-weight="bold" lengthAdjust="spacing" textLength="53.9492" x="155.2415" y="27.9951">revoke</text><rect fill="#FFFFFF" height="97.2031" style="stroke:#181818;stroke-width:1.0;" width="10" x="282.7573" y="104.7266"/><rect fill="none" height="90.2031" style="stroke:#000000;stroke-width:1.5;" width="345.4321" x="10" y="119.7266"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="47" x2="47" y1="73.5938" y2="226.9297"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="287.0825" x2="287.0825" y1="73.5938" y2="226.9297"/><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="54.5303" x="20" y="42.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="40.5303" x="27" y="62.292">Client</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="54.5303" x="20" y="225.9297"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="40.5303" x="27" y="245.9248">Client</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="115.3496" x="230.0825" y="42.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="101.3496" x="237.0825" y="62.292">LGE-MP OAuth</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="115.3496" x="230.0825" y="225.9297"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="101.3496" x="237.0825" y="245.9248">LGE-MP OAuth</text><rect fill="#FFFFFF" height="97.2031" style="stroke:#181818;stroke-width:1.0;" width="10" x="282.7573" y="104.7266"/><polygon fill="#181818" points="270.7573,100.7266,280.7573,104.7266,270.7573,108.7266,274.7573,104.7266" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="47.2651" x2="276.7573" y1="104.7266" y2="104.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="54.2651" y="99.6606">1</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="153.8228" x="67.3105" y="99.6606">NTH.005(POST /revoke)</text><path d="M10,119.7266 L74.4429,119.7266 L74.4429,126.8594 L64.4429,136.8594 L10,136.8594 L10,119.7266 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="90.2031" style="stroke:#000000;stroke-width:1.5;" width="345.4321" x="10" y="119.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="19.4429" x="25" y="132.7935">alt</text><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="89.8101" x="89.4429" y="131.937">[success case]</text><polygon fill="#181818" points="58.2651,153.9922,48.2651,157.9922,58.2651,161.9922,54.2651,157.9922" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="52.2651" x2="281.7573" y1="157.9922" y2="157.9922"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="64.2651" y="152.9263">2</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="47.7026" x="77.3105" y="152.9263">200 OK</text><line style="stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="10" x2="355.4321" y1="166.9922" y2="166.9922"/><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="73.1274" x="15" y="177.2026">[error case]</text><polygon fill="#181818" points="58.2651,197.9297,48.2651,201.9297,58.2651,205.9297,54.2651,201.9297" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="52.2651" x2="286.7573" y1="201.9297" y2="201.9297"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="64.2651" y="196.8638">3</text><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="198.4468" x="77.3105" y="196.8638">Error Message for NTH.005</text><!--SRC=[NOxT2e9044Rlvoa6hmgnbg0RCI522ieKyWNMTQobpPNzwVdRh9kw6JwOSxuPxfqU_ACb0-2aKuI6dlfE02CtJWevyi5Xj5EI1XSXjoZKx-gqBvAonchhtMq250SG2fCyf3Z65C_DOS7OUbPNbmQNd_uvSENGUY78XavkwUraIHAaeAmOm-e8f2mX6QFD7n96YbclmmD2AsqsXheyQ_DYOilGoQ-4VSZVuq13zm80]--></g></svg>
            
          토큰 폐기 시퀀스입니다.
            
          <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" contentStyleType="text/css" height="262px" preserveAspectRatio="none" style="width:367px;height:262px;background:#FFFFFF;" version="1.1" viewBox="0 0 367 262" width="367px" zoomAndPan="magnify"><defs/><g><text fill="#000000" font-family="sans-serif" font-size="14" font-weight="bold" lengthAdjust="spacing" textLength="80.8213" x="144.1763" y="27.9951">introspect</text><rect fill="#FFFFFF" height="97.2031" style="stroke:#181818;stroke-width:1.0;" width="10" x="287.499" y="104.7266"/><rect fill="none" height="90.2031" style="stroke:#000000;stroke-width:1.5;" width="350.1738" x="10" y="119.7266"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="47" x2="47" y1="73.5938" y2="226.9297"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="291.8242" x2="291.8242" y1="73.5938" y2="226.9297"/><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="54.5303" x="20" y="42.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="40.5303" x="27" y="62.292">Client</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="54.5303" x="20" y="225.9297"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="40.5303" x="27" y="245.9248">Client</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="115.3496" x="234.8242" y="42.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="101.3496" x="241.8242" y="62.292">LGE-MP OAuth</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="115.3496" x="234.8242" y="225.9297"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="101.3496" x="241.8242" y="245.9248">LGE-MP OAuth</text><rect fill="#FFFFFF" height="97.2031" style="stroke:#181818;stroke-width:1.0;" width="10" x="287.499" y="104.7266"/><polygon fill="#181818" points="275.499,100.7266,285.499,104.7266,275.499,108.7266,279.499,104.7266" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="47.2651" x2="281.499" y1="104.7266" y2="104.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="54.2651" y="99.6606">1</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="174.8208" x="67.3105" y="99.6606">NTH.004(POST /introspect)</text><path d="M10,119.7266 L74.4429,119.7266 L74.4429,126.8594 L64.4429,136.8594 L10,136.8594 L10,119.7266 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="90.2031" style="stroke:#000000;stroke-width:1.5;" width="350.1738" x="10" y="119.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="19.4429" x="25" y="132.7935">alt</text><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="95.7075" x="89.4429" y="131.937">[Token is valid]</text><polygon fill="#181818" points="58.2651,153.9922,48.2651,157.9922,58.2651,161.9922,54.2651,157.9922" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="52.2651" x2="286.499" y1="157.9922" y2="157.9922"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="64.2651" y="152.9263">2</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="203.1885" x="77.3105" y="152.9263">200 OK, json data(active=true)</text><line style="stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="10" x2="360.1738" y1="166.9922" y2="166.9922"/><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="163.2759" x="15" y="177.2026">[invalid client credentials]</text><polygon fill="#181818" points="58.2651,197.9297,48.2651,201.9297,58.2651,205.9297,54.2651,201.9297" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="52.2651" x2="291.499" y1="201.9297" y2="201.9297"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="64.2651" y="196.8638">3</text><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="172.0278" x="77.3105" y="196.8638">401 Unauthorized Error</text><!--SRC=[LOxDJiCm48Jl-nIZdbgLb81wgj985Qf0uYULI1zWQo_2OEp8tlJ0q-Fq0bnsLvhvTeP7ZM7yEaaYKgTUu8Acc0SnIZHmKcVSm44nk_DEWix06SR_bvxkzzNp0TrkrFUBmKSYur6rvLekiS5B_x2gw_NyqBtskFxDM12nL_JnKm9SnfcziuIIWAQg2btOsxf6ztY5Znm3B2lFsQWxorRJA0iIdwVM5x9mKqcO9BPinpx_VLR61irRd1pHnxGjjhOvjUlw1iV0fNrCxbiizYd5H1Bi3m00]--></g></svg>
            
          토큰 검증 시퀀스입니다.
            
          <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" contentStyleType="text/css" height="301px" preserveAspectRatio="none" style="width:372px;height:301px;background:#FFFFFF;" version="1.1" viewBox="0 0 372 301" width="372px" zoomAndPan="magnify"><defs/><g><text fill="#000000" font-family="sans-serif" font-size="14" font-weight="bold" lengthAdjust="spacing" textLength="65.1738" x="159.6292" y="27.9951">userinfo</text><rect fill="#FFFFFF" height="16" style="stroke:#181818;stroke-width:1.0;" width="10" x="52.2651" y="240.8672"/><rect fill="#FFFFFF" height="92.2031" style="stroke:#181818;stroke-width:1.0;" width="10" x="292.7573" y="104.7266"/><rect fill="none" height="105.0078" style="stroke:#000000;stroke-width:1.5;" width="345.4321" x="20" y="143.8594"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="57" x2="57" y1="73.5938" y2="265.8672"/><line style="stroke:#181818;stroke-width:0.5;stroke-dasharray:5.0,5.0;" x1="297.0825" x2="297.0825" y1="73.5938" y2="265.8672"/><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="54.5303" x="30" y="42.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="40.5303" x="37" y="62.292">Client</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="54.5303" x="30" y="264.8672"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="40.5303" x="37" y="284.8623">Client</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="115.3496" x="240.0825" y="42.2969"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="101.3496" x="247.0825" y="62.292">LGE-MP OAuth</text><rect fill="#E2E2F0" height="30.2969" rx="2.5" ry="2.5" style="stroke:#181818;stroke-width:0.5;" width="115.3496" x="240.0825" y="264.8672"/><text fill="#000000" font-family="sans-serif" font-size="14" lengthAdjust="spacing" textLength="101.3496" x="247.0825" y="284.8623">LGE-MP OAuth</text><rect fill="#FFFFFF" height="16" style="stroke:#181818;stroke-width:1.0;" width="10" x="52.2651" y="240.8672"/><rect fill="#FFFFFF" height="92.2031" style="stroke:#181818;stroke-width:1.0;" width="10" x="292.7573" y="104.7266"/><polygon fill="#181818" points="280.7573,100.7266,290.7573,104.7266,280.7573,108.7266,284.7573,104.7266" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="57.2651" x2="286.7573" y1="104.7266" y2="104.7266"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="64.2651" y="99.6606">1</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="154.0068" x="77.3105" y="99.6606">NTH.006(GET /userinfo)</text><path d="M20,143.8594 L343.3193,143.8594 L343.3193,150.9922 L333.3193,160.9922 L20,160.9922 L20,143.8594 " fill="#EEEEEE" style="stroke:#000000;stroke-width:1.5;"/><rect fill="none" height="105.0078" style="stroke:#000000;stroke-width:1.5;" width="345.4321" x="20" y="143.8594"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="278.3193" x="35" y="156.9263">seq NTH.006(GET /userinfo) Response</text><line style="stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="20" x2="365.4321" y1="161.9922" y2="161.9922"/><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="72.311" x="25" y="172.2026">[Error NOK]</text><polygon fill="#181818" points="68.2651,192.9297,58.2651,196.9297,68.2651,200.9297,64.2651,196.9297" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="62.2651" x2="296.7573" y1="196.9297" y2="196.9297"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="74.2651" y="191.8638">2</text><text fill="#FF0000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="198.4468" x="87.3105" y="191.8638">Error Message for NTH.006</text><line style="stroke:#000000;stroke-width:1.0;stroke-dasharray:2.0,2.0;" x1="20" x2="365.4321" y1="205.9297" y2="205.9297"/><text fill="#000000" font-family="sans-serif" font-size="11" font-weight="bold" lengthAdjust="spacing" textLength="54.7207" x="25" y="216.1401">[200 OK]</text><polygon fill="#181818" points="73.2651,236.8672,63.2651,240.8672,73.2651,244.8672,69.2651,240.8672" style="stroke:#181818;stroke-width:1.0;"/><line style="stroke:#181818;stroke-width:1.0;" x1="67.2651" x2="296.7573" y1="240.8672" y2="240.8672"/><text fill="#000000" font-family="sans-serif" font-size="13" font-weight="bold" lengthAdjust="spacing" textLength="9.0454" x="79.2651" y="235.8013">3</text><text fill="#000000" font-family="sans-serif" font-size="13" lengthAdjust="spacing" textLength="59.9917" x="92.3105" y="235.8013">json data</text><!--SRC=[TOwnJiD038PtFyMlJZ0K8WQ6gaIgK5GaQ8jGNy1Dd7BeE0UVZ-Vd869WOBFbpvy-BgxSU_Xa5sWYhdigxoSn8WyU1IMBXJGgqSJceGyJ9yVYFWP9lW1dzF7lwMdRBNVFE6oAl_u0aOdwY6LR9womFpvSDStjnROxulfNVqaSdSwcPKAMZtyWl4YUD6KXYLdGcQbXVtWa4o-Mi1wr5lGQrUvCXdPzQcTc9pdpMJ1-yxDwLjmq3Uf_3QjvDNA5jwm90pkJfE4B]--></g></svg>
            
          토큰 사용자 정보 시퀀스입니다.  
      - name: auth
        description: |
          전사회원플랫폼 (LGE Members Platform) 에서 제공하는 인증 및 권한 부여 요청 API 입니다.
      - name: token
        description: |
          전사회원플랫폼 (LGE Members Platform) 에서 제공하는 엑세스 토큰을 얻는 요청 API 입니다.
      - name: revoke
        description: |
          전사회원플랫폼 (LGE Members Platform) 에서 제공하는 엑세스 토큰을 취소하는 요청 API 입니다.
      - name: introspect
        description: |
          전사회원플랫폼 (LGE Members Platform) 에서 제공하는 엑세스 토큰을 확인/검증하는 요청 API 입니다.
      - name: userinfo
        description: |
          전사회원플랫폼 (LGE Members Platform) 에서 제공하는 엑세스 토큰에 대한 사용자 정보 요청 API 입니다.
    paths:
      /realms//LGE-MP/protocol/openid-connect/auth:
        get:
          tags:
            - auth
          summary: 권한 부여 요청 (NTH.002)
          description: |-
            권한 부여 코드 부여의 부여 유형을 사용하여 OAuth 2.0 서버에서 권한을 얻기 위한 API입니다.
            OAuth 2.0 표준을 유지하기 위해 이 API를 사용하는 것이 좋습니다.

            [참고] 현재 LGE-MP OAuth 서버는 권한 부여 코드 부여의 부여 유형만 지원합니다.

            토큰을 갱신할 때 만료 시간은 연장되지 않습니다.

            무제한 토큰을 원하시면 오프라인 토큰을 사용하세요.
          operationId: auth
          parameters:
            - name: response_type
              in: query
              description: |-
                응답 유형.

                값은 "code" 로 설정해야 합니다.
              required: true
              schema:
                type: string
            - name: client_id
              in: query
              description: |-
                클라이언트 식별자.

                LGE-MP OAuth Admin 에서 생성할 수 있습니다. (필요한 경우 LGE-MP OAuth Admin 에 문의하세요.)
              required: true
              schema:
                type: string
            - name: redirect_uri
              in: query
              description: 클라이언트의 redirection 엔드포인트 에 대한 사용자 에이전트 입니다.
              required: true
              schema:
                type: string
            - name: scope
              in: query
              description: |-
                엑세스 요청 scope 입니다.

                권한 부여 및 토큰 엔드포인트를 사용하면 클라이언트가 "scope" 요청 매개변수를 사용하여 액세스 요청의 범위를 지정할 수 있습니다. 
                그러면 권한 부여 서버는 "scope" 응답 매개변수를 사용하여 발급된 액세스 토큰의 범위를 클라이언트에 알립니다.

                범위는 문자열 사이에 공백으로 구분해야 합니다.

                [참고] 이 값은 액세스 토큰(NTH.003, ../openid-connect/token)을 가져오는 API의 응답에 포함되며 이 API 의 응답에는 포함되지 않습니다.

                "openid"는 scope 에 포함되어야 합니다.

                오프라인 토큰을 원하면, offline_access 를 추가하세요.
              required: true
              schema:
                type: string
            - name: state
              in: query
              description: 요청과 콜백 사이의 상태를 유지하기 위해 클라이언트가 사용하는 불투명(opaque) 값입니다.
              required: false
              schema:
                type: string
            - name: code_challenge_method
              in: query
              description: 요청에 없으면 기본값은 "plain"입니다. 코드 검증기 변환 방법은 "S256" 또는 "plain"입니다.
              required: false
              schema:
                type: string
            - name: code_challenge_method
              in: query
              description: |-
                코드 검증기에서 다음 변환 중 하나를 사용:  

                plain:  
                - code_challenge = code_verifier  

                S256:  
                - code_challenge = BASE64URL-ENCODE(SHA256(ASCII(code_verifier)))  

                ex) q51jlVr6odO6oV6lS3ptzO0Skyrts5M2oTJir22vA04
              required: false
              schema:
                type: string
          responses:
            '302':
              description: |-
                성공과 에러의 상태 값은 302 로 동일합니다.

                [참고] 누락, 유효하지 않음 또는 일치하지 않는 redirection URI 로 인해 요청이 실패하거나 클라이언트 식별자가 누락되거나 유효하지 않은 경우 
                권한 부여 서버는 리소스 소유자에게 오류를 알려야 하며 사용자 에이전트를 유효하지 않은 redirection URI 로 자동으로 redirection 해서는 안 됩니다. (RFC6749)
              headers:
                Location:
                  schema:
                    type: string
                  description: |-
                    클라이언트에 데이터를 전달하기 위한 리디렉션 URI.

                    요청에 유효한 redirection URI 가 있는 경우 redirection URI 에 redirection URI 가 사용됩니다.

                    그렇지 않은 경우 Keycloak 은 미리 정의된 redirection URI 를 선택합니다. (미리 정의된 redirection URI 는 클라이언트가 등록될 때 설정됩니다.)

                    추가 쿼리 매개변수가 redirection URI 에 추가됩니다.

                    <br>

                    [성공]

                    <br>

                    예시)

                    Location: https://client.example.com/cb?code=qwelrjk&state=asldkfjs

                    <br>

                    Redirection URI 요청 파라미터)

                    code (M) : 권한 부여 서버에서 생성된 권한 부여 코드

                    state (C) : 요청에 "state" 파라미터가 존재하는 경우 필수 값입니다.

                    <br>

                    [에러]

                    <br>

                    example)

                    Location: https://client.example.com/cb?error=access_denied&state=asldkfjs

                    <br>

                    Redirection URI 요청 파라미터)

                    error : invalid_request, unauthorized_client, access_denied, unsupported_response_type, invalid_scope, server_error, temporarily_unavailable

                    error_description : error description

                    error_uri : error uri

                    state : 요청에 "state" 파라미터가 존재하는 경우 필수 값입니다.
      /realms//LGE-MP/protocol/openid-connect/token:
        post:
          tags:
            - token
          summary: Access Token 요청, authrization_code or refresh_token (NTH.003)
          description: |-
            인증 코드 부여의 부여 유형을 사용하여 OAuth 2.0 서버에 액세스 토큰을 요청하는 API 입니다.

            [NOTE] 현재 LGE-MP OAuth 서버는 권한 부여 코드 부여 유형만 지원합니다.
          operationId: token
          parameters:
            - name: Authorization
              in: header
              description: |-
                client 에 대한 HTTP basic 인증. "client_id:secret"을 base64로 인코딩합니다.

                <br>

                ex) 

                Authorization: “Basic Y2xpZW50MTozREJvVUVhc05XSnIxa0E0QzY2RDhNU2ppZ0pQRFpOVA==”
              required: true
              explode: true
              schema:
                type: string
          requestBody:
            required: true
            content:
              application/x-www-form-urlencoded:
                schema:
                  type: object
                  properties:
                    grant_type:
                      type: string
                      description: |-
                        다음 둘 중 하나만 가능합니다. "authorization_code" or "refresh_token"

                        <br>

                        ex) 
                        - grant_type=authorization_code
                        - grant_type=refresh_token
                      enum:
                        - authorization_code
                        - refresh_token
                    code:
                      type: string
                      description: |-
                        [Only authorization_code, M]

                        권한서버로부터 수신된 권한코드
                    redirect_uri:
                      type: string
                      description: |-
                        [Only authorization_code, M]

                        클라이언트의 리디렉션 엔드포인트에 대한 사용자 에이전트.

                        "redirect_uri" 매개변수가 권한 부여 요청([NTH.002])에 포함된 경우 해당 값은 반드시 동일해야 합니다.
                    code_verifier:
                      type: string
                      description: |-
                        [Only authorization_code, M]

                        암호화 난수 문자열, [A-Z] / [a-z] / [0-9] / "-" / "." / "_" / "~" from Section 2.3 of [RFC3986], 최소 43자, 최대 128자 길이.

                        <br>

                        ex) 8253f747278a4fdc8597d31a0dee6ab7fb842cbce2e13bca925977e777
                    scope:
                      type: string
                      description: |-
                        [Only refresh_token, O]

                        요청된 범위에는 리소스 소유자가 원래 부여하지 않은 범위가 포함되어서는 안 되며, 생략된 경우 리소스 소유자가 원래 부여한 범위와 동일한 것으로 간주됩니다.
                    refresh_token:
                      type: string
                      description: |-
                        [Only refresh_token, M]

                        client 에게 발급된 refresh token 입니다.
                  required:
                    - grant_type
          responses:
            '200':
              description: Success
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      access_token:
                        type: string
                      expires_in:
                        type: integer
                      refresh_expires_in:
                        type: integer
                      refresh_token:
                        type: string
                      token_type:
                        type: string
                      id_token:
                        type: string
                      not_before_policy:
                        type: integer
                      session_state:
                        type: string
                      scope:
                        type: string
            '400':
              description: |-
                [error]

                A single ASCII [USASCII] error code

                <br>

                ex)
                - invalid_request : 요청에 필수 매개변수가 없습니다.
                - invalid_client : 인증에 실패했습니다. HTTP 401 상태 코드를 반환합니다.
                - unauthorized_client : 제공된 권한 부여 또는 refresh token 이 잘못되었습니다.
                - unsupported_grant_type : 권한 부여 유형이 권한 부여 서버에서 지원되지 않습니다.
                - invalid_scope : 요청된 범위가 잘못되었거나, 알 수 없거나, 형식이 잘못되었거나, 리소스 소유자가 부여한 범위를 초과합니다.

                [error_description]

                오류 설명

                <br>

                [error_uri]

                오류에 대한 정보가 있는, 사람이 읽을 수 있는 웹 페이지를 식별하는 URI입니다.

                <br>

                [state]

                인증 요청에 "state" 매개변수가 있는 경우 필수입니다.
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error'
      /realms//LGE-MP/protocol/openid-connect/revoke:
        post:
          tags:
            - revoke
          summary: Token 철회 (NTH.005)
          description: LGE-MP OAuth 2.0 서버에서 발급된 액세스 토큰을 취소하는 API 입니다.
          operationId: revoke
          parameters:
            - name: Authorization
              in: header
              description: |-
                client 에 대한 HTTP basic 인증. "client_id:secret" 을 base64 로 인코딩합니다.

                <br>

                ex) 

                Authorization: “Basic Y2xpZW50MTozREJvVUVhc05XSnIxa0E0QzY2RDhNU2ppZ0pQRFpOVA==”
              required: true
              explode: true
              schema:
                type: string
          requestBody:
            required: true
            content:
              application/x-www-form-urlencoded:
                schema:
                  type: object
                  properties:
                    token:
                      type: string
                      description: client 가 취소하려는 토큰(AccessToken 또는 RefreshToken).
                    token_type_hint:
                      type: string
                      description: |-
                        취소를 위해 제출된 토큰의 유형에 대한 힌트입니다.

                        <br>

                        ex) token_type_hint=refresh_token
                  required:
                    - token
          responses:
            '200':
              description: Success
            '400':
              description: |-
                [error]

                A single ASCII [USASCII] error code

                <br>

                ex)
                - invalid_request : 요청에 필수 매개변수가 없습니다.
                - invalid_client : 인증에 실패했습니다. HTTP 401 상태 코드를 반환합니다.
                - unauthorized_client : 제공된 권한 부여 또는 refresh token 이 잘못되었습니다.
                - unsupported_grant_type : 권한 부여 유형이 권한 부여 서버에서 지원되지 않습니다.
                - invalid_scope : 요청된 범위가 잘못되었거나, 알 수 없거나, 형식이 잘못되었거나, 리소스 소유자가 부여한 범위를 초과합니다.

                [error_description]

                오류 설명

                <br>

                [error_uri]

                오류에 대한 정보가 있는, 사람이 읽을 수 있는 웹 페이지를 식별하는 URI입니다.

                <br>

                [state]

                클라이언트 인증 요청에 "state" 매개변수가 있는 경우 필수입니다.
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error'
      /realms//LGE-MP/protocol/openid-connect/token/introspect:
        post:
          tags:
            - introspect
          summary: Token 확인 및 유효성 검증 (NTH.004)
          description: LGE-MP OAuth 2.0 서버에서 발급된 액세스 토큰을 확인/검증하는 API입니다.
          operationId: introspect
          parameters:
            - name: Authorization
              in: header
              description: |-
                클라이언트에 대한 HTTP 기본 인증. "client_id:secret" 을 base64 로 인코딩합니다.

                <br>

                ex) 

                Authorization: “Basic Y2xpZW50MTozREJvVUVhc05XSnIxa0E0QzY2RDhNU2ppZ0pQRFpOVA==”
              required: true
              explode: true
              schema:
                type: string
          requestBody:
            required: true
            content:
              application/x-www-form-urlencoded:
                schema:
                  type: object
                  properties:
                    token:
                      type: string
                      description: 확인 및 검증이 필요한 access token
                    token_type_hint:
                      type: string
                      description: 내부 검증을 위한 토큰 유형에 대한 hint
                  required:
                    - token
          responses:
            '200':
              description: |-
                Success
                - active: 제시된 토큰이 현재 활성화되어 있는지 여부
                - exp: Integer timestamp (UTC), 토큰 만료 시간
                - iat: Integer timestamp, 토큰 발행 시점
                - jti: 토큰에 대한 문자열 식별자
                - aud: 해당 토큰의 서비스별 문자열 식별자
                - sub: 해당 토큰을 승인한 리소스 소유자의 문자열 식별자
                - typ: 토큰의 유형. 현재 Bearer 만 사용 가능
                - azp: OAuth 2.0 클라이언트 아이디
                - session_state: 최종 사용자의 로그인 상태. 클라이언트에게는 불투명(opaque) 값 입니다.
                - name: 최종 사용자 풀네임
                - given_name: Given name(s) or first name(s)
                - family_name: The surname(s) or last name(s) of the end-user
                - preferred_username: Shorthand name by which the End-User wishes to be referred to
                - email: 사용자 이메일 주소
                - email_verified: 사용자 이메일 주소 검증
                - scope: A JSON string containing a space-separated list of scopes associated with this token.
                - sid: End-User's login state. This value is opaque to the client.
                - client_id: Client ID
                - username: username
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      active:
                        type: boolean
                      exp:
                        type: integer
                      iat:
                        type: integer
                      jit:
                        type: string
                      aud:
                        type: string
                      sub:
                        type: string
                      typ:
                        type: integer
                      azp:
                        type: string
                      session_state:
                        type: string
                      name:
                        type: string
                      given_name:
                        type: string
                      family_nmae:
                        type: string
                      preferred_username:
                        type: string
                      email:
                        type: string
                      email_verified:
                        type: boolean
                      scope:
                        type: string
                      sid:
                        type: string
                      client_id:
                        type: string
                      username:
                        type: string
            '400':
              description: |-
                Error

                <br>

                [error]

                다음 중 하나의 오류 코드:

                - invalid_client : 인증 실패 (e.g., unknown client, no client authentication included, or unsupported authentication method).

                <br>

                [error_description]

                오류 설명

                <br>

                [error_uri]

                오류에 대한 정보가 있는 사람이 읽을 수 있는 웹 페이지를 식별하는 URI
              content:
                application/json:
                  schema:
                    $ref: '#/components/schemas/error'
      /realms//LGE-MP/protocol/openid-connect/userinfo:
        get:
          tags:
            - userinfo
          summary: 사용자 정보 요청 (NTH.006)
          description: LGE-MP OAuth 2.0 서버에서 발급된 액세스 토큰에 대한 간단한 사용자 정보를 가져오기 위한 API입니다.
          operationId: userinfo
          parameters:
            - name: Authorization
              in: header
              description: |-
                Bearer Token

                ex) 

                Authorization: “Bearer (access_token)”
              required: true
              schema:
                type: string
          responses:
            '200':
              description: Success
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      sub:
                        type: string
                      email_verified:
                        type: boolean
                      name:
                        type: string
                      preferred_username:
                        type: string
                      given_name:
                        type: string
                      family_name:
                        type: string
                      email:
                        type: string
            '400':
              description: Error
              headers:
                WWW-Authenticate:
                  schema:
                    type: string
                  description: |-
                    Possible errors:
                    - invalid_request
                    - invalid_token
                    - insufficient_scope

                    <br>

                    ex)

                    WWW-Authenticate: "Bearer error=invalid_token, error_description="The access token expired"
    components:
      schemas:
        error:
          type: object
          properties:
            error:
              type: string
            error_description:
              type: string
            error_uri:
              type: string
    x-tagGroups:
      - name: Get Started
        tags:
          - Overview
          - API Call Sequence
          - Authentication
          - Authorization
          - Token
      - name: LMP API
        tags:
          - auth
          - token
          - revoke
          - introspect
          - userinfo
---
