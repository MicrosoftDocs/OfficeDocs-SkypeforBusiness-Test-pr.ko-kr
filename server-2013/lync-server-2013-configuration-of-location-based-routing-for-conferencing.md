---
title: 'Lync Server 2013: 회의를 위한 위치 기반 라우팅 구성'
TOCTitle: 회의를 위한 위치 기반 라우팅 구성
ms:assetid: d8c708cc-a1b1-48b1-808c-a64df15f7701
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362846(v=OCS.15)
ms:contentKeyID: 56270310
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 회의를 위한 위치 기반 라우팅 구성

 

_**마지막으로 수정된 항목:** 2014-09-29_

위치 기반 라우팅 회의 응용 프로그램은 Lync Server 2013 위치 기반 라우팅의 구성을 기반으로 합니다. 기본 구성은 다음과 같습니다.

  - 모임에 참가하는 참가자의 위치는 해당 네트워크 사이트를 기준으로 결정됩니다. 위치 기반 라우팅을 적용하려면 Lync Server에서 네트워크 사이트와 연결된 네트워크 하위 집합을 정의해야 합니다.

  - 모임의 위치 기반 라우팅을 적용하려면 Lync 참가자가 위치 기반 라우팅을 설정해야 합니다.

  - 모임에 참가하는 PSTN 끝점의 위치 기반 라우팅을 적용하려면 PSTN 끝점을 연결하는 데 사용되는 SIP 트렁크가 위치 기반 라우팅용으로 구성되어 있어야 합니다.

Lync Server 2013 위치 기반 라우팅을 배포하고 구성하는 방법에 대한 추가 정보는 [위치 기반 라우팅](lync-server-2013-configuring-location-based-routing.md)을 참조하세요.

## 위치 기반 라우팅 회의 응용 프로그램 설정

위치 기반 라우팅 회의 응용 프로그램은 기본적으로 해제되어 있습니다. 이 응용 프로그램을 설정하기 전에 응용 프로그램에 대해 할당할 권한 우선 순위를 결정해야 합니다. 이 우선 순위를 결정하려면 Lync Server 관리 셸에서 다음 cmdlet을 실행합니다.

Get-CsServerApplication -Identity Service:Registrar:\<Pool FQDN\>

이 cmdlet에서 \<Pool FQDN\>은 위치 기반 라우팅 회의 응용 프로그램을 설정할 풀입니다.

이 cmdlet은 Lync Server에서 호스팅하는 응용 프로그램 목록과 각 응용 프로그램의 우선 순위 값을 반환합니다. 위치 기반 라우팅 회의 응용 프로그램에는 “UdcAgent” 응용 프로그램보다 크고 “DefaultRouting”, “ExumRouting”, “OutboundRouting” 응용 프로그램보다 작은 우선 순위 값을 할당해야 합니다. 위치 기반 라우팅 회의 응용 프로그램에 “UdcAgent” 응용 프로그램의 우선 순위 값보다 1포인트 높은 우선 순위 값을 할당하는 것이 좋습니다.

예를 들어 "UdcAgent" 응용 프로그램의 우선 순위 값은 "2", "DefaultRouting" 응용 프로그램의 우선 순위 값은 "8", "ExumRouting" 응용 프로그램의 우선 순위 값은 "9", "OutboundRouting" 응용 프로그램의 우선 순위 값은 "10"인 경우 위치 기반 라우팅 회의 응용 프로그램에 우선 순위 값 "3"을 할당해야 합니다. 이렇게 하면 응용 프로그램의 우선 순위가 기타 응용 프로그램(우선 순위: 0-1), "UdcAgent"(우선 순위: 2), 위치 기반 라우팅 회의 응용 프로그램(우선 순위: 3), 기타 응용 프로그램(우선 순위: 4-8), "DefaultRouting"(우선 순위: 9), "ExumRouting"(우선 순위: 10), "OutboundRouting"(우선 순위: 11) 순서로 정리됩니다.

위치 기반 라우팅 회의 응용 프로그램에 대해 올바른 우선 순위 값을 찾은 후에 위치 기반 라우팅이 설정된 사용자가 있는 각 프런트 엔드 풀 또는 Standard Edition Server에 대해 다음 cmdlet을 입력합니다.

New-CsServerApplication -Identity Service:Registrar:\<Pool FQDN\>/LBRouting -Priority \<Application Priority\> -Enabled $true -Critical $true -Uri http://www.microsoft.com/LCS/LBRouting

예를 들면 다음과 같습니다.

New-CsServerApplication -Identity Service:Registrar:LS2013CU2LBRPool.contoso.com/LBRouting -Priority 3 -Enabled $true -Critical $true -Uri http://www.microsoft.com/LCS/LBRouting

이 cmdlet을 사용한 후에는 위치 기반 라우팅 회의 응용 프로그램이 설정된 풀의 모든 프런트 엔드 서버 또는 Standard Edition Server를 다시 시작합니다.


> [!IMPORTANT]
> 회의 또는 협의 전송에 대한 위치 기반 라우팅 적용 사항은 해당 풀의 모든 프런트 엔드 서버 또는 Standard Edition Server를 다시 시작할 때까지 적용되지 않습니다. 위 cmdlet에서 <STRONG>–Critical</STRONG>을 <STRONG>$true</STRONG>로 설정한 경우 Lync 서비스가 바로 다시 시작됩니다. 이 서비스가 바로 다시 시작되지 않도록 하려면 일단 <STRONG>–Critical</STRONG>을 <STRONG>$false</STRONG>로 설정해 두었다가 나중에 서비스가 다시 시작된 후에 <STRONG>Set-CsServerApplication</STRONG>을 사용하여 <STRONG>-Critical</STRONG>을 <STRONG>$true</STRONG>로 변경합니다.



위치 기반 라우팅 회의 응용 프로그램을 성공적으로 설정하고 해당되는 모든 Lync Server를 다시 시작한 경우, PSTN 유료 우회를 방지하기 위해 위치 기반 라우팅이 설정된 Lync 사용자가 구성한 모든 회의가 모니터링됩니다.

