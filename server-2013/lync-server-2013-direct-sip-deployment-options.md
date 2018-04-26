---
title: 'Lync Server 2013: 직접 SIP 배포 옵션'
TOCTitle: 직접 SIP 배포 옵션
ms:assetid: 84691944-03f2-4a89-9f2b-1ab3d7f388cc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398672(v=OCS.15)
ms:contentKeyID: 49304248
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 직접 SIP 배포 옵션

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 항목에서는 Direct SIP 연결을 배포하기 위한 예제 토폴로지를 제공합니다.

## Lync Server 독립 실행형

조직에서 이 섹션에 설명된 배포 중 하나를 사용하는 경우 Lync Server 2013을 조직 전체 또는 일부에 대한 단독 전화 통신 솔루션으로 사용할 수 있습니다. 이 섹션에서는 다음과 같은 배포에 대해 자세히 설명합니다.

  - **증분 배포:** 이 옵션에서는 기존 PBX(Private Branch Exchange) 인프라가 있고 조직 내의 보다 작은 규모의 그룹 또는 팀에 Enterprise Voice를 증분적으로 도입하려 한다고 가정합니다.

  - **Lync Server VoIP 전용 배포:** 이 옵션에서는 일반 전화 통신 인프라가 없는 사이트에 Enterprise Voice를 배포하려 한다고 가정합니다.

## 증분 배포

증분 배포에서는 개별 팀 또는 부서에 대해 Lync Server 2013이 단독 전화 통신 솔루션으로 배포되는 반면, 조직 내 나머지 사용자는 PBX를 계속 사용합니다. 이 증분 배포 전략은 제어된 파일럿 프로그램을 통해 IP 전화 통신을 엔터프라이즈에 도입하는 한 가지 방법을 제공합니다. Microsoft Unified Communications가 통신에 가장 효과적인 작업 그룹은 Enterprise Voice로 이동되고 다른 사용자는 기존 PBX에 남아 있습니다. 필요에 따라 추가 작업 그룹을 Enterprise Voice로 마이그레이션할 수 있습니다.

증분 옵션은 통신 요구 사항이 공통적이고 중앙에서 관리할 수 있는 명확히 정의된 사용자 그룹에 사용하는 것이 좋습니다. 또한 이 옵션은 넓은 지역에 분산되어 시외 전화 요금을 많이 절약할 수 있는 팀 또는 부서에 효과적입니다. 실제로 이 옵션은 구성원이 전 세계에 분산되어 있는 가상 팀을 만드는 데 유용합니다. 변화하는 비즈니스 요구 사항에 신속하게 대응하여 이러한 팀을 만들고 수정하거나 해산할 수 있습니다.

다음 그림에서는 PBX 뒤에 Enterprise Voice를 배포하는 일반적인 토폴로지를 보여 줍니다. 이 토폴로지는 증분 배포에 권장됩니다.

**증분 배포 옵션**

![부서별 마이그레이션 옵션 다이어그램](images/Gg398672.e951ecf4-7cd2-425a-9106-76977492d682(OCS.15).jpg "부서별 마이그레이션 옵션 다이어그램")


> [!NOTE]
> Lync Server 배포를 인증된 Direct SIP 파트너에 연결하려는 경우 중재 서버와 PBX 간에 PSTN(공중 전화망) 게이트웨이가 필요하지 않습니다. 인증된 Direct SIP 파트너 목록은 Microsoft Unified Communications Open Interoperability Program 웹 사이트( <A class=uri href="http://go.microsoft.com/fwlink/?linkid=203309%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=203309&amp;clcid=0x412</A>)를 참조하십시오.




> [!NOTE]
> 이 그림에 나와 있는 미디어 경로에는 미디어 바이패스가 사용되었습니다(권장 구성). 미디어 바이패스를 사용하지 않도록 선택한 경우 미디어 경로가 중재 서버를 통해 라우팅됩니다.



이 토폴로지에서 선택된 부서 또는 작업 그룹은 Enterprise Voice에 대해 사용하도록 설정되어 있습니다. PSTN 게이트웨이는 VoIP(Voice over Internet Protocol)를 사용하는 작업 그룹을 PBX에 연결합니다. Enterprise Voice에 대해 사용하도록 설정되어 있는 사용자(원격 직원 포함)는 IP 네트워크를 통해 통신합니다. Enterprise Voice 사용자가 PSTN에 거는 전화와 Enterprise Voice에 대해 사용하도록 설정되어 있지 않은 동료에게 거는 전화는 적절한 PSTN 게이트웨이로 라우팅됩니다. 여전히 PBX 시스템에 있는 동료나 PSTN에 있는 발신자의 통화는 라우팅을 위해 Lync Server로 착신 전환되도록 하는 PSTN 게이트웨이로 라우팅됩니다.

Enterprise Voice를 기존 PBX 인프라에 연결할 때 상호 운용성을 위해 권장되는 두 가지 구성은 PBX 뒤에 Enterprise Voice를 배포하는 것과 PBX 앞에 Enterprise Voice를 배포하는 것입니다.

## PBX 뒤에 Enterprise Voice 배포

Enterprise Voice를 PBX 뒤에 배포하면 PSTN으로부터의 모든 통화가 PBX에 도착하고 PBX는 Enterprise Voice 사용자에 대한 통화를 PSTN 게이트웨이로 라우팅하고 PBX 사용자에 대한 통화를 PBX로 라우팅합니다.

## PBX 앞에 Enterprise Voice 배포

Enterprise Voice를 PBX 앞에 배포하면 모든 통화가 PSTN 게이트웨이에 도착하고 PSTN 게이트웨이는 Enterprise Voice 사용자에 대한 통화를 Lync Server로 라우팅하고 PBX 사용자에 대한 통화를 PBX로 라우팅합니다. PSTN에 대한 Enterprise Voice 및 PBX 사용자의 통화는 IP 네트워크를 통해 가장 비용 효율적인 PSTN 게이트웨이로 라우팅됩니다. 다음 표는 이 구성의 장점 및 단점을 보여 줍니다.

### PBX 앞에 Enterprise Voice를 배포하는 경우의 장점 및 단점

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>장점</th>
<th>단점</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PBX에서 Enterprise Voice에 대해 사용하도록 설정되지 않은 사용자에게 계속 서비스를 제공합니다.</p></td>
<td><p>기존 게이트웨이에서 원하는 기능이나 용량을 지원하지 않을 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p>PBX에서 모든 이전 장치를 처리합니다.</p></td>
<td><p>게이트웨이에서 PBX로의 트렁크 및 게이트웨이에서 중재 서버로의 트렁크가 필요합니다. 서비스 공급자가 제공하는 트렁크가 더 필요할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p>Enterprise Voice 사용자가 동일한 전화 번호를 유지합니다.</p></td>
<td><p> </p></td>
</tr>
</tbody>
</table>


## Lync Server VoIP 전용 배포

Enterprise Voice는 PBX 통합에 대해 걱정할 필요 없이 또는 상당한 IP-PBX 인프라 배포 및 유지 관리 비용을 발생시키지 않고도 모든 기능을 갖춘 VoIP 솔루션을 구현할 수 있는 기회를 통해 기존 비즈니스에 새 비즈니스 및 새 사무실 사이트를 제공합니다. 이 솔루션은 사무실에서 근무하는 직원과 원격 직원을 모두 지원합니다.

이 배포에서 모든 통화는 IP 네트워크를 통해 라우팅됩니다. PSTN에 대한 통화는 적절한 PSTN 게이트웨이로 라우팅됩니다. Lync 2013 또는 Lync Phone Edition이 소프트폰의 역할을 합니다. 사용자가 제어할 PBX 전화가 없으므로 원격 통화 제어는 사용할 수 없고 필요하지 않습니다. 음성 메일 및 자동 전화 교환 서비스는 Exchange 통합 메시징(UM)을 선택적으로 배포하여 사용할 수 있습니다.


> [!NOTE]
> Lync Server 2013을 지원하는 데 필요한 네트워크 인프라 외에 VoIP 전용 배포에서는 소규모의 적합한 게이트웨이를 사용하여 팩스 및 아날로그 장치를 지원할 수 있습니다.



다음 그림은 VoIP 전용 배포의 일반적인 토폴로지를 보여 줍니다.

**VoIP 전용 배포 옵션**

![Greenfidle 배포 옵션](images/Gg398672.820dc5fe-0e20-431b-ae4e-fefdf2221d3b(OCS.15).jpg "Greenfidle 배포 옵션")


> [!NOTE]
> 이 그림에 나와 있는 미디어 경로에는 미디어 바이패스가 사용되었습니다(권장 구성). 미디어 바이패스를 사용하지 않도록 선택한 경우 미디어 경로가 중재 서버를 통해 라우팅됩니다.


