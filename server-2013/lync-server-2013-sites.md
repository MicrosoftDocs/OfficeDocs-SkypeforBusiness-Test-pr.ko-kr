---
title: Lync Server 2013 사이트
TOCTitle: 사이트
ms:assetid: 022cb6dd-37e2-4882-a53e-5ddfdbc6f53a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398076(v=OCS.15)
ms:contentKeyID: 49302621
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 Lync Server 사이트

 

_**마지막으로 수정된 항목:** 2012-10-16_

Lync Server에서는 네트워크에서 Lync Server 구성 요소가 포함된 *사이트* 를 정의합니다. 사이트는 단일 LAN(Local Area Network)이나 고속 광섬유 네트워크로 연결된 두 개의 네트워크와 같이 고속, 짧은 대기 시간 네트워크로 견고하게 연결된 컴퓨터 집합입니다. Lync Server 사이트는 Active Directory 도메인 서비스 사이트 및 Microsoft Exchange Server 사이트와는 별도의 개념입니다. Lync Server 사이트가 Active Directory 사이트에 해당할 필요는 없습니다.

## 사이트 유형

각 사이트는 프런트 엔드 풀 또는 Standard Edition 서버를 하나 이상 포함하는 *중앙 사이트* 이거나, *분기 사이트* 입니다. 각 분기 사이트는 정확히 하나의 중앙 사이트에 연결되며, 분기 사이트의 사용자는 연결된 중앙 사이트에 있는 서버에서 대부분의 Lync Server 기능을 사용하게 됩니다.

각 분기 사이트는 다음 중 하나를 포함합니다.

  - *SBA(Survivable Branch Appliance)* 는 Windows Server에서 실행 중인 Lync Server 등록자 및 중재 서버를 포함하는 업계 표준 블레이드 서버입니다. SBA(Survivable Branch Appliance)에는 공중 전화망(PSTN) 게이트웨이도 포함됩니다. SBA(Survivable Branch Appliance)는 사용자가 25~1,000명 사이인 분기 사이트용으로 디자인됩니다.

  - *SBS(지속 가능 분기 서버)* 는 지정된 하드웨어 요구 사항을 충족하는 Windows Server를 실행 중인 서버로, Lync Server 등록자 및 중재 서버 소프트웨어가 설치되어 있습니다. 이 서버는 전화 서비스 공급자에 대한 SIP 트렁크 또는 PSTN 게이트웨이에 연결되어야 합니다. 지속 가능 분기 서버는 사용자가 1,000~5,000명 사이인 분기 사이트용으로 디자인됩니다.

  - PSTN 게이트웨이 및 *중재 서버* (선택 사항). 이 역할 및 기타 서버 역할에 대한 자세한 내용은 [Lync Server 2013의 서버 역할](lync-server-2013-server-roles.md)을 참조하십시오.

중앙 사이트에 대한 복원 가능 WAN(광역 네트워크) 링크가 있는 지점에서는 세 번째 옵션인 PSTN 게이트웨이 및 중재 서버(선택 사항)를 사용할 수 있습니다. 복원력이 떨어지는 링크가 있는 지점 사이트에서는 광역 네트워크 오류 발생 시 복원 기능을 제공하는 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버를 사용해야 합니다. 예를 들어 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버가 배포된 사이트에서 사용자는 분기 사이트와 중앙 사이트를 연결하는 WAN의 작동이 중단된 경우에도 Enterprise Voice 전화를 걸고 받을 수 있습니다. SBA(Survivable Branch Appliance), 지속 가능 분기 서버, 복원 기능에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013 의 Enterprise Voice 복구 계획](lync-server-2013-planning-for-enterprise-voice-resiliency.md)을 참고하세요.

## 사이트 토폴로지

배포에는 하나 이상의 중앙 사이트가 포함되어야 하며, 분기 사이트는 포함되지 않을 수도 있고 여러 개 포함될 수도 있습니다. 각 분기 사이트는 중앙 사이트 하나와 연결됩니다. 중앙 사이트에서는 분기 사이트에서 로컬로 호스트되지 않는 현재 상태, 회의 등의 Lync Server 서비스를 분기 사이트에 제공합니다.

사이트가 여러 개인 경우에는 각 사이트의 프런트 엔드 풀을 페어링하여 재해 복구 기능을 사용하도록 설정해야 합니다. 자세한 내용은 [Lync Server 2013의 고가용성 및 재해 복구 지원](lync-server-2013-high-availability-and-disaster-recovery-support.md)을 참조하십시오.

## 참고 항목

#### 개념

[Lync Server 2013의 서버 역할](lync-server-2013-server-roles.md)  
[Lync Server 2013의 고가용성 및 재해 복구 지원](lync-server-2013-high-availability-and-disaster-recovery-support.md)  

#### 기타 리소스

[Lync Server 2013 의 Enterprise Voice 복구 계획](lync-server-2013-planning-for-enterprise-voice-resiliency.md)

