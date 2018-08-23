---
title: "SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 배포 - 중앙 사이트 작업"
TOCTitle: SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 배포 - 중앙 사이트 작업
ms:assetid: 0f631a36-fc2e-41cd-8a0d-f27e84f4a89e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398189(v=OCS.15)
ms:contentKeyID: 49302823
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013을 통해 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 배포 - 중앙 사이트 작업

 

_**마지막으로 수정된 항목:** 2012-10-18_

중앙 사이트에서 이 섹션의 작업을 완료하십시오. 지속 가능 분기 서버를 배포하는 경우에는 첫 작업을 건너뜁니다.


> [!IMPORTANT]
> 이 섹션의 작업을 완료하려면 다음 조건이 충족되어야 합니다. 
> <UL>
> <LI>
> <P>Lync Server를 중앙 사이트에 설치해야 합니다.</P>
> <LI>
> <P>분기 사이트의 설치 기술자를 RTCUniversalSBATechnicians 그룹에 추가해야 합니다.</P></LI></UL>또한 다음 작업도 수행하는 것이 좋습니다. 
> <UL>
> <LI>
> <P>클라이언트가 IP 주소를 가져올 수 있도록 각 분기 사이트에서 DHCP 서버를 배포합니다.</P>
> <LI>
> <P>각 분기 사이트에서 DHCP 서버를 배포하는 대신, Lync Server 관리 셸 cmdlet <STRONG>Set-CsRegistrarConfiguration –EnableDHCPServer $true</STRONG>를 사용하여 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버에서 Lync Server DHCP를 사용하도록 설정합니다. 자세한 내용은 계획 설명서에서 <A href="lync-server-2013-branch-site-resiliency-requirements.md">Lync Server 2013에 대한 분기 사이트 복구 요구 사항</A>의 "하드웨어 및 소프트웨어 요구 사항" 섹션을 참고하세요.</P></LI></UL>



## 이 단원의 내용

  - [Lync Server 2013에서 Active Directory에 SBA(Survivable Branch Appliance) 추가](lync-server-2013-add-a-survivable-branch-appliance-to-active-directory.md)

  - [Lync Server 2013에서 토폴로지에 분기 사이트 추가](lync-server-2013-add-branch-sites-to-your-topology.md)

  - [Lync Server 2013에서 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 정의](lync-server-2013-define-a-survivable-branch-appliance-or-server.md)

