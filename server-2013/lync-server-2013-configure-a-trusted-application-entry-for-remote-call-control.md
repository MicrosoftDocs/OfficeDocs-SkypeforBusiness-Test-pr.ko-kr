---
title: 'Lync Server 2013: 원격 통화 제어를 위한 신뢰할 수 있는 응용 프로그램 항목 구성'
TOCTitle: 원격 통화 제어를 위한 신뢰할 수 있는 응용 프로그램 항목 구성
ms:assetid: 37777f93-8b24-40cf-808e-7c6230eb2132
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg558636(v=OCS.15)
ms:contentKeyID: 49303308
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 원격 통화 제어를 위한 신뢰할 수 있는 응용 프로그램 항목 구성

 

_**마지막으로 수정된 항목:** 2012-10-22_

SIP/CSTA 게이트웨이를 신뢰할 수 있는 응용 프로그램으로 구성해야 Lync Server에서 게이트웨이에 대한 통화를 라우팅하는 고정 경로를 적용할 수 있습니다.


> [!IMPORTANT]
> 사용자를 이전 버전 Lync Server 배포에서 마이그레이션하는 경우, 이 항목의 절차를 수행하기 전에 SIP/CSTA 게이트웨이용으로 만들었던 기존의 모든 신뢰할 수 있는 응용 프로그램 항목(이전 이름: 권한이 부여된 호스트 항목)을 제거했는지 확인하십시오. 자세한 내용은 <A href="lync-server-2013-remove-a-legacy-authorized-host-optional.md">Lync Server 2013에서 권한이 부여된 기존 호스트 제거(선택 사항)</A>를 참조하십시오.



## SIP/CSTA 게이트웨이용으로 신뢰할 수 있는 응용 프로그램 항목을 구성하려면

1.  Lync Server 관리 셸이 설치된 컴퓨터에 RTCUniversalServerAdmins 그룹의 구성원 또는 **New-CsTrustedApplicationPool** cmdlet을 할당한 RBAC(역할 기반 액세스 제어) 역할로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  신뢰할 수 있는 응용 프로그램 항목을 만들려면 다음 중 하나를 수행합니다.
    
      - TLS(전송 계층 보안) 연결의 경우 명령 프롬프트에 다음을 입력합니다.
        
            New-CsTrustedApplicationPool -Identity <FQDN of the SIP/CSTA gateway> [-Registrar <Service ID or FQDN of the Registrar service>] -Site <Site ID for the site where you want to create the trusted application pool>
        
        예를 들면 다음과 같습니다.
        
            New-CsTrustedApplicationPool -Identity rccgateway.contoso.net -Registrar registrar1.contoso.net -Site co1 -TreatAsAuthenticated $true -ThrottleAsServer $true
    
      - TCP(Transmission Control Protocol) 연결의 경우 명령 프롬프트에 다음을 입력합니다.
        
            New-CsTrustedApplicationPool -Identity <IP address or FQDN of the SIP/CSTA gateway> [-Registrar <Service ID or FQDN of the Registrar service>] -Site <Site ID for the site where you want to create the trusted application pool>
        
        예를 들면 다음과 같습니다.
        
            New-CsTrustedApplicationPool -Identity 192.168.0.240 -Registrar registrar1.contoso.net -Site co1 -TreatAsAuthenticated $true -ThrottleAsServer $true

4.  신뢰할 수 있는 응용 프로그램을 풀에 추가하려면 다음 중 하나를 수행합니다.
    
      - TLS 연결의 경우 명령 프롬프트에 다음을 입력합니다.
        
            New-CsTrustedApplication -ApplicationID <application name> -TrustedApplicationPoolFqdn <FQDN of the SIP/CSTA gateway> -Port <SIP listening port on the gateway>
        
        예를 들면 다음과 같습니다.
        
            New-CsTrustedApplication -ApplicationID RccGateway-1 -TrustedApplicationPoolFqdn rccgateway.contoso.net -Port 5065
    
      - TCP 연결의 경우 명령 프롬프트에 다음을 입력합니다.
        
            New-CsTrustedApplication -ApplicationID <application name> -TrustedApplicationPoolFqdn <IP address or FQDN of the SIP/CSTA gateway> -Port <SIP listening port on the gateway> -EnableTcp
        
        예를 들면 다음과 같습니다.
        
            New-CsTrustedApplication -ApplicationID RccGateway-1 -TrustedApplicationPoolFqdn 192.169.0.240 -Port 5065 -EnableTcp

5.  토폴로지에 적용한 게시된 변경 내용을 구현하려면 명령 프롬프트에 다음을 입력합니다.
    
        Enable-CsTopology

## 참고 항목

#### 작업

[Lync Server 2013에서 원격 통화 제어에 대한 고정 경로 구성](lync-server-2013-configure-a-static-route-for-remote-call-control.md)  
[Lync Server 2013에서 SIP/CSTA 게이트웨이 IP 주소 정의](lync-server-2013-define-a-sip-csta-gateway-ip-address.md)

