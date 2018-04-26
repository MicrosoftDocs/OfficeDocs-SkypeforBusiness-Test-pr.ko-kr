---
title: 'Lync Server 2013: 고급 Enterprise Voice 기능에 대한 네트워크 설정'
TOCTitle: 고급 Enterprise Voice 기능에 대한 네트워크 설정
ms:assetid: 7f6de9e4-c8a4-44e4-8d14-21fe8c45283a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398637(v=OCS.15)
ms:contentKeyID: 49304185
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 고급 Enterprise Voice 기능에 대한 네트워크 설정

 

_**마지막으로 수정된 항목:** 2012-10-10_

Lync Server에는 세 가지 고급 Enterprise Voice 기능, 즉 CAC(통화 허용 제어), 응급 서비스(E9-1-1) 및 미디어 바이패스 기능이 있습니다. 이러한 기능은 네트워크 지역, 네트워크 사이트 및 Lync Server 토폴로지의 각 서브넷과 네트워크 사이트의 연결에 대한 특정 구성 요구 사항을 공유합니다. 이러한 기능의 배포 계획에 대한 자세한 내용은 다음을 참조하십시오.

  - [Lync Server 2013의 통화 허용 제어 서비스 계획](lync-server-2013-planning-for-call-admission-control.md)

  - [Lync Server 2013의 응급 서비스 계획(E9-1-1)](lync-server-2013-planning-for-emergency-services-e9-1-1.md)

  - [Lync Server 2013의 미디어 바이패스 계획](lync-server-2013-planning-for-media-bypass.md)

이러한 기능의 배포에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 고급 Enterprise Voice 기능 배포](lync-server-2013-deploying-advanced-enterprise-voice-features.md)를 참조하십시오.

이 항목에서는 세 가지 고급 Enterprise Voice 기능 모두에 공통적인 구성 요구 사항에 대한 개요를 제공합니다.

## 네트워크 지역

네트워크 지역은 CAC(통화 허용 제어), E9-1-1 및 미디어 바이패스 구성에만 사용되는 네트워크 허브 또는 네트워크 백본입니다.


> [!NOTE]
> 네트워크 지역은 전화 접속 회의 액세스 번호를 하나 이상의 Lync Server 다이얼 플랜과 연결해야 하는 Lync Server 전화 접속 회의 지역과 다릅니다. 전화 접속 회의 지역에 대한 자세한 내용은 계획 설명서에서 <A href="lync-server-2013-dial-in-conferencing-requirements.md">Lync Server 2013의 전화 접속 회의 요구 사항</A>을 참조하십시오.



CAC를 사용하려면 모든 네트워크 지역에 지역 내의 미디어 트래픽을 관리(즉, 구성한 정책을 기반으로 실시간 오디오 또는 비디오 세션을 설정할 수 있는지 여부를 결정)하는 연결된 Lync Server 중앙 사이트가 있어야 합니다. Lync Server 중앙 사이트는 지리적 위치를 나타내는 것이 아니라 풀 또는 풀 집합으로 구성된 논리적 서버 그룹을 나타냅니다. 중앙 사이트에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 참조 토폴로지](lync-server-2013-reference-topologies.md)를 참조하십시오. 또한 지원 가능성 설명서에서 [Lync Server 2013의 지원되는 토폴로지](lync-server-2013-supported-topologies.md)를 참조하십시오.

네트워크 지역을 구성하려는 경우 Lync Server 제어판의 **네트워크 구성** 섹션에서 **지역** 탭을 사용하거나 **New-CsNetworkRegion** 또는 **Set-CsNetworkRegion**Lync Server 관리 셸 cmdlet을 실행합니다. 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 네트워크 지역 만들기 또는 수정](lync-server-2013-create-or-modify-a-network-region.md)을 참조하거나 Lync Server 관리 셸 설명서를 참조하십시오.

세 가지 고급 Enterprise Voice 기능 모두 같은 네트워크 지역 정의를 공유합니다. 따라서 하나의 기능에 대한 네트워크 지역을 이미 만든 경우 다른 기능에 대한 새 네트워크 지역을 만들 필요가 없습니다. 그러나 기능별 설정을 적용하기 위해 기존 네트워크 지역 정의를 수정해야 하는 경우가 있을 수 있습니다. 예를 들어 E9-1-1(연결된 중앙 사이트 필요 없음)에 대한 네트워크 지역을 만들고 나중에 통화 허용 제어를 배포한 경우 각 네트워크 지역 정의를 수정하여 중앙 사이트를 지정해야 합니다.

Lync Server 중앙 사이트를 네트워크 지역과 연결하려면 Lync Server 제어판의 **네트워크 구성** 섹션을 사용하거나 **New-CsNetworkRegion** 또는 **Set-CsNetworkRegion**Lync Server 관리 셸 cmdlet을 실행하여 중앙 사이트 이름을 지정합니다. 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 네트워크 지역 만들기 또는 수정](lync-server-2013-create-or-modify-a-network-region.md)을 참조하거나 Lync Server 관리 셸 설명서를 참조하십시오.

## 네트워크 사이트

네트워크 사이트는 지점, 지사 또는 본사와 같은 지리적 위치를 나타냅니다. 각 네트워크 사이트는 특정 네트워크 지역과 연결되어야 합니다.


> [!NOTE]
> 네트워크 사이트는 고급 Enterprise Voice 기능에서만 사용됩니다. 네트워크 사이트는 Lync Server 토폴로지에서 구성하는 분기 사이트와는 다릅니다. 분기 사이트에 대한 자세한 내용은 계획 설명서에서 <A href="lync-server-2013-reference-topologies.md">Lync Server 2013의 참조 토폴로지</A>를 참조하십시오. 또한 지원 가능성 설명서에서 <A href="lync-server-2013-supported-topologies.md">Lync Server 2013의 지원되는 토폴로지</A>를 참조하십시오.



네트워크 사이트를 구성하고 이를 네트워크 지역과 연결하려는 경우 Lync Server 제어판의 **네트워크 구성** 을 사용하거나 Lync Server 관리 셸**New-CsNetworkSite** 또는 **Set-CsNetworkSite** cmdlet을 실행할 수 있습니다. 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 네트워크 사이트 만들기 또는 수정](lync-server-2013-create-or-modify-a-network-site.md)을 참조하거나 Lync Server 관리 셸 설명서를 참조하십시오.

## IP 서브넷 확인

각 네트워크 사이트에 대해 네트워크 관리자와 함께 각 네트워크 사이트에 지정된 IP 서브넷을 확인해야 합니다. 네트워크 관리자가 네트워크 지역 및 네트워크 사이트에 대한 IP 서브넷을 이미 구성한 경우에는 작업이 훨씬 간편합니다.

예를 들어 북미 지역의 뉴욕 사이트에 172.29.80.0/23, 157.57.216.0/25, 172.29.91.0/23, 172.29.81.0/24 IP 서브넷을 지정할 수 있습니다. 주로 디트로이트에서 근무하는 Bob이 교육을 받기 위해 뉴욕 사무실에 출장을 왔다고 가정해 보겠습니다. Bob이 컴퓨터를 켜고 네트워크에 연결하면 컴퓨터에서 뉴욕에 할당된 네 개 범위 중 하나의 IP 주소(예: 172.29.80.103)를 가져옵니다.


> [!WARNING]
> 서버에서 네트워크를 구성하는 동안 지정된 IP 서브넷을 미디어 바이패스에 사용하려면 IP 서브넷이 클라이언트 컴퓨터에서 제공한 형식과 일치해야 합니다. Lync 클라이언트는 해당 로컬 IP 주소를 가져와 연결된 서브넷 마스크로 IP 주소를 마스킹합니다. 각 클라이언트에 연결된 바이패스 ID를 확인할 때 등록자는 각 네트워크 사이트에 연결된 IP 서브넷 목록이 클라이언트에서 제공한 서브넷과 정확히 일치하는지 비교합니다. 따라서 서버에서 네트워크를 구성할 때 가상 서브넷 대신 실제 서브넷을 입력해야 합니다. 미디어 바이패스가 아니라 통화 허용 제어를 배포한 경우에는 가상 서브넷을 구성한 경우에도 통화 허용 제어가 제대로 작동합니다.<BR>예를 들어 클라이언트가 IP 서브넷 마스크가 255.255.255.0인 IP 주소 172.29.81.57을 사용하여 컴퓨터에 로그인한 경우 Lync에서는 서브넷 172.29.81.0과 연결된 바이패스 ID를 요청합니다. 클라이언트가 가상 서브넷에 속해 있더라도 서브넷이 172.29.0.0/16으로 정의된 경우 등록자는 이를 일치하는 것으로 간주하지 않습니다. 등록자는 서브넷 172.29.81.0을 찾기 때문입니다. 따라서 관리자는 정확히 Lync 클라이언트에서 제공하는 서브넷을 입력해야 합니다. 클라이언트는 정적 네트워크 구성 또는 DHCP(Dynamic Host Configuration Protocol)에 의한 네트워크 구성 중에 제공된 서브넷으로 프로비전됩니다.



## 서브넷과 네트워크 사이트 연결

엔터프라이즈 네트워크의 모든 서브넷은 네트워크 사이트와 연결되어야 합니다. 즉, 모든 서브넷을 지리적 위치와 연결해야 합니다. 이러한 서브넷 연결을 통해 고급 Enterprise Voice 기능에서 지리적 끝점을 효과적으로 찾을 수 있습니다. 예를 들어 끝점을 찾으면 CAC에서 네트워크 사이트로 들어오고 나가는 오디오 및 비디오 데이터 흐름을 실시간으로 통제할 수 있습니다.

서브넷을 네트워크 사이트와 연결하려는 경우에는 Lync Server 제어판의 **네트워크 구성** 섹션을 사용하거나 Lync Server 관리 셸을 사용할 수 있습니다. 자세한 내용은 배포 설명서에서 [Lync Server 2013 에서 네트워크 사이트에 서브넷 연결](lync-server-2013-associate-a-subnet-with-a-network-site.md)을 참조하거나 Lync Server 관리 셸 설명서를 참조하십시오.

## 참고 항목

#### 기타 리소스

[Lync Server 2013의 통화 허용 제어 서비스 계획](lync-server-2013-planning-for-call-admission-control.md)  
[Lync Server 2013의 응급 서비스 계획(E9-1-1)](lync-server-2013-planning-for-emergency-services-e9-1-1.md)  
[Lync Server 2013의 미디어 바이패스 계획](lync-server-2013-planning-for-media-bypass.md)

