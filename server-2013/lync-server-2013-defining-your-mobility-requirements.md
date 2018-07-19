---
title: 'Lync Server 2013: 모바일 기능 요구 사항 정의'
TOCTitle: 모바일 기능 요구 사항 정의
ms:assetid: b7608335-cdeb-4aae-8e4b-d80c55f0d62b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690039(v=OCS.15)
ms:contentKeyID: 49304812
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 모바일 기능 요구 사항 정의

 

_**마지막으로 수정된 항목:** 2015-03-09_

    Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

Lync 2010 Mobile 및 Lync 2013 모바일 클라이언트 사용 시에는 Lync Server 2013 모바일 기능의 계획 단계에서 배포 단계를 결정하는 몇 가지 사항을 결정해야 합니다.

다음은 고려해야 할 결정 사항입니다.

  - **Lync 모바일 클라이언트에 대해 자동 검색을 사용할지 여부**
    
    자동 검색을 지원하려는 경우에는 새 내부 및 외부 DNS(Domain Name System) 레코드를 만들고, 프런트 엔드 서버, 디렉터 및 역방향 프록시의 인증서에 주체 대체 이름을 추가하고, 역방향 프록시에서 기존 게시 규칙을 수정해야 합니다. 자세한 내용은 [Lync Server 2013의 모바일 기능에 대한 기술 요구 사항](lync-server-2013-technical-requirements-for-mobility.md)을 참조하십시오. 자동 검색을 사용하는 경우 사용자가 자신의 모바일 장치 설정에서 URL을 입력하지 않고도 회사 네트워크 내부나 외부 어디서나 Lync Server 2013 웹 서비스를 자동으로 찾을 수 있습니다.
    
    자동 검색 대신 수동 설정을 사용하는 경우 모바일 사용자가 모바일 장치에서 다음 URL을 수동으로 입력해야 합니다.
    
      - https://\<외부 풀 FQDN\>/Autodiscover/autodiscoverservice.svc/외부 액세스 루트
    
      - https://\<내부 풀 FQDN\>/AutoDiscover/ autodiscoverservice.svc/내부 액세스 루트
    
    자동 검색은 사용하는 것이 좋습니다. 수동 설정은 주로 문제 해결 시에 사용됩니다.

  - **자동 검색을 지원하기로 결정하는 경우 각 SIP 도메인의 주체 대체 이름으로 역방향 프록시의 인증서를 업데이트할지 여부**
    
    SIP 도메인이 여러 개인 경우 역방향 프록시에서 공용 인증서를 업데이트하려면 비용이 매우 많이 들 수 있습니다. 이 경우에는 자동 검색을 구현하여 초기 자동 검색 서비스 요청이 포트 443에서 HTTPS를 사용하는 대신 포트 80에서 HTTP를 사용하도록 할 수 있습니다. 그러나 이 방식은 사용하지 않는 것이 좋습니다. 이 대체 방법을 선택하는 경우 역방향 프록시에서 인증서를 업데이트할 필요는 없지만 포트 80에서 HTTP용으로 웹 게시 규칙을 만들어야 합니다. 자세한 내용은 [Lync Server 2013의 모바일 기능에 대한 기술 요구 사항](lync-server-2013-technical-requirements-for-mobility.md)을 참조하십시오.

  - **Lync 모바일 클라이언트를 지원할 위치(회사 네트워크 내부와 외부에서 모두 지원/회사 네트워크 내부에서만 지원)**
    
    모바일 클라이언트를 네트워크 내부와 외부에서 모두 지원하는 경우 모바일 장치가 어디서나 모바일 기능에 액세스할 수 있습니다. 기본 구성에서는 회사 네트워크 내부와 외부에서 모두 클라이언트가 지원됩니다.
    
    기본 구성에서는 모바일 클라이언트 트래픽이 외부 사이트를 통과할 수 있지만, 모바일 클라이언트 트래픽을 내부 회사 네트워크로 제한할 수 있습니다. 트래픽을 내부 네트워크로 제한하면 사용자는 네트워크 내에 있을 때만 모바일 장치에서 Lync 모바일 응용 프로그램을 사용할 수 있습니다.
    
    Mcx Mobility Service 및 Lync 2010 Mobile을 사용하는 모바일 기능을 지원하는 배포의 경우 **Set-CsMcxConfiguration** cmdlet을 실행합니다. 내부 전용 모바일 기능을 설정하려면 다음과 같은 명령을 사용합니다.
    
        Set-CsMcxConfiguration -Identity site:Redmond -ExposedWebURL Internal
    

    > [!NOTE]
    > UCWA에 필요한 추가 구성은 없습니다. UCWA에는 위와 동일한 내부 전용 구성이 없습니다.

    

    > [!IMPORTANT]
    > Lync Server 2013프런트 엔드 서버 또는 프런트 엔드 풀을 사용하고 있으며 Lync Server 2010프런트 엔드 서버 또는 프런트 엔드 풀이 <STRONG>없는</STRONG> 경우 <STRONG>쿠키 기반 지속성이 필요 없습니다</STRONG>. Lync Server 2010프런트 엔드 서버 또는 프런트 엔드 풀을 보존해야 하는 경우 Lync Server 2010과 동일한 쿠키 기반 지속성 관련 규칙이 계속 적용됩니다.



  - **Apple iOS 장치 및 Windows Phone에 대해 푸시 알림을 지원할지 여부**
    
    푸시 알림을 지원하는 경우 지원되는 Apple iOS 장치 및 Windows Phone에서는 모바일 응용 프로그램이 비활성 상태일 때 발생하는 이벤트의 알림을 받게 됩니다. 에지 서버가 클라우드 기반 Lync Server 푸시 알림 서비스(Lync Online 데이터 센터에 있음)와 페더레이션 관계를 가지도록 구성해야 하며, cmdlet을 실행해 푸시 알림을 사용하도록 설정해야 합니다.
    
    모바일 장치 공급자의 3G 또는 데이터 네트워크를 통해 푸시 알림을 지원하는 것 외에 Wi-Fi 네트워크를 통해서도 푸시 알림을 지원하려면 엔터프라이즈 Wi-Fi 네트워크에서 아웃바운드 포트 5223을 열어야 합니다. Wi-Fi만 사용하는 모바일 장치와 실내 수신 상태가 좋지 않은 모바일 장치에 한해 Wi-Fi 네트워크를 통해 푸시 알림을 지원할 수 있습니다.
    

    > [!IMPORTANT]
    > Lync 2010 Mobile 클라이언트를 실행하는 Apple 장치를 지원할 때만 TCP 5223 포트를 열면 됩니다.

    
    푸시 알림을 지원하지 않으면 Apple 모바일 장치 및 Windows Phone 사용자는 인스턴트 메시지 초대, 부재 중 메시지 등 모바일 응용 프로그램이 비활성 상태일 때 발생한 이벤트에 대해 알 수 없습니다.
    

    > [!NOTE]
    > Apple 장치의 Lync 2013 모바일 클라이언트에서는 푸시 알림이 필요하지 않습니다. Windows Phone의 Lync 2013 모바일 클라이언트는 푸시 알림을 사용합니다. 푸시 알림 및 푸시 알림 클리어링 하우스에 대한 계획은 Windows Phone의 Lync Mobile과 Lync 2013 모바일 클라이언트를 실행할 수 없는 Apple 장치에서 동일하게 유지됩니다.



  - **모바일 기능에 액세스할 수 있는 사용자(모든 사용자에게 액세스 권한 제공/기능에 액세스할 수 있는 사용자 지정)**
    
    아래 표에는 Lync Server 2013에서 사용자에게 제공되는 기능에 대한 설명이 나와 있습니다. 기본값을 적용하면 회사번호로 전화 및 VoIP(Voice over IP)가 허용되고 모바일 기능이 사용하도록 설정됩니다. 사용 가능한 모든 옵션 집합은 다음과 같습니다.
    
    
    <table>
    <colgroup>
    <col style="width: 33%" />
    <col style="width: 33%" />
    <col style="width: 33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>기능/매개 변수 이름/범위 (정책 매개 변수 이름은 다를 수 있음)</th>
    <th>설명</th>
    <th>도입</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>모바일 사용</p>
    <p>매개 변수 이름: <code>EnableMobility</code></p>
    <p>범위: 전역/사이트/사용자</p></td>
    <td><p>Lync Mobile을 설치한 지정된 범위의 사용자를 제어하기 위한 관리 설정입니다. 정책을 False로 설정하면 사용자가 클라이언트에 로그인할 수 없습니다.</p>
    <p>기본 설정은 True입니다.</p></td>
    <td><p>Lync Server 2010용 누적 업데이트(2011년 11월)</p></td>
    </tr>
    <tr class="even">
    <td><p>외부 음성 사용</p>
    <p>매개 변수 이름: <code>EnableOutsideVoice</code></p>
    <p>범위: 전역/사이트/사용자</p></td>
    <td><p>사용자가 회사번호로 전화(휴대폰 번호가 아닌 회사 번호를 사용하여 전화를 걸고 받는 기능)를 사용하는 기능을 제어합니다. False로 설정하면 사용자가 모바일 장치에서 회사 번호를 사용하여 전화를 걸거나 받을 수 없습니다.</p>
    <p>기본 설정은 True입니다.</p></td>
    <td><p>Lync Server 2010용 누적 업데이트(2011년 11월)</p></td>
    </tr>
    <tr class="odd">
    <td><p>IP 오디오/비디오 사용</p>
    <p>매개 변수 이름: <code>EnableIPAudioVideo</code></p>
    <p>범위: 전역/사이트/사용자</p></td>
    <td><p>사용자가 모바일 장치에서 VoIP를 사용하여 음성 또는 비디오 통화를 걸거나 받을 수 있는지 여부를 제어합니다. False로 설정하면 사용자가 장치에서 VoIP 또는 비디오 통화를 걸거나 받을 수 없습니다.</p>
    <p>기본 설정은 True입니다.</p></td>
    <td><p>Microsoft Lync Server 2013</p></td>
    </tr>
    <tr class="even">
    <td><p>IP 오디오에 대해 Wi-Fi 필요</p>
    <p>매개 변수 이름: <code>RequireWiFiForIPAudio</code></p>
    <p>범위: 전역/사이트/사용자</p></td>
    <td><p>이 설정은 클라이언트가 셀룰러 데이터 네트워크가 아닌 Wi-Fi에서 VoIP를 통해 전화를 걸고 받아야 하는지를 정의합니다. True로 설정하면 사용자는 Wi-Fi 네트워크에 연결되어 있을 때만 VoIP 통화를 걸고 받을 수 있습니다.</p>
    <p>기본 설정은 False입니다.</p></td>
    <td><p>Microsoft Lync Server 2013</p></td>
    </tr>
    <tr class="odd">
    <td><p>IP 비디오에 대해 Wi-Fi 필요</p>
    <p>매개 변수 이름: <code>RequireWiFiForIPVideo</code></p>
    <p>범위: 전역/사이트/사용자</p></td>
    <td><p>이 설정은 클라이언트가 셀룰러 데이터 네트워크가 아닌 Wi-Fi에서 비디오 통화를 걸고 받아야 하는지를 정의합니다. True로 설정하면 사용자는 Wi-Fi 네트워크에 연결되어 있을 때만 비디오 통화를 걸고 받을 수 있습니다.</p>
    <p>기본 설정은 False입니다.</p></td>
    <td><p>Microsoft Lync Server 2013</p></td>
    </tr>
    </tbody>
    </table>
    
    구성할 수 있는 정책 설정 및 정책을 관리하는 방법에 대한 설명은 [New-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsMobilityPolicy), [Set-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsMobilityPolicy), [Get-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsMobilityPolicy), [Grant-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsMobilityPolicy) 및 [Remove-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsMobilityPolicy)를 참조하십시오.

  - **Enterprise Voice를 사용할 수 있도록 설정되지 않은 사용자가 클릭하여 참가를 사용하여 회의에 참가하도록 할지 여부**
    
    모바일 기능 및 회사번호로 전화 기능에 액세스할 수 있는 사용자는 Enterprise Voice를 사용할 수 있도록 설정해야 합니다. 그러나 Enterprise Voice를 사용할 수 있도록 설정되지 않은 사용자라도 적절한 음성 정책이 지정된 경우 모바일 장치에서 링크를 클릭하여 회의에 참가할 수 있습니다. 이러한 사용자에게 특정 음성 정책을 지정할 수도 있고, 사용자에게 적용되는 전역 정책 또는 사이트 수준 정책이 있는지 확인할 수도 있습니다. 사용자에게 지정하는 음성 정책에는 사용자가 회의에 참가하기 위해 전화를 걸 수 있는 영역을 정의하는 경로와 PSTN(공중 전화망) 사용 레코드가 포함되어 있어야 합니다. 음성 정책, PSTN 사용 레코드 및 경로 설정에 대한 자세한 내용은 [Lync Server 2013에서 음성 정책, PSTN 사용 레코드 및 음성 경로 구성](lync-server-2013-configuring-voice-policies-pstn-usage-records-and-voice-routes.md)을 참조하십시오.
    

    > [!NOTE]
    > 클릭하여 참가 기능을 사용하려는 모바일 사용자에게는 음성 정책 및 관련 PSTN 사용 레코드와 음성 경로가 필요합니다. 모바일 장치에서 링크를 클릭하면 Lync Server 2013에서 아웃바운드 통화가 수행되기 때문입니다.



## 참고 항목

#### 개념

[Lync Server 2013의 모바일 기능에 대한 기술 요구 사항](lync-server-2013-technical-requirements-for-mobility.md)  

#### 기타 리소스

[Lync Server 2013에서 음성 정책, PSTN 사용 레코드 및 음성 경로 구성](lync-server-2013-configuring-voice-policies-pstn-usage-records-and-voice-routes.md)

