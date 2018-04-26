---
title: 'Lync Server 2013: Exchange UM(통합 메시징) 지원'
TOCTitle: Exchange UM(통합 메시징) 지원
ms:assetid: 0da62b8d-7416-4fb8-a405-381ca805c53a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398179(v=OCS.15)
ms:contentKeyID: 49302797
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Exchange UM(통합 메시징) 지원

 

_**마지막으로 수정된 항목:** 2012-09-21_

Lync Server 2013에서는 음성 메시지와 전자 메일 메시지를 단일 메시징 인프라에 통합할 수 있도록 Exchange 통합 메시징(UM)과의 통합을 지원합니다. Exchange 2013에서 Exchange UM은 Exchange UM 서비스(사서함 서버에서 설치 및 실행됨) 및 UM Call Router(클라이언트 액세스 서버에서 설치 및 실행됨)로 구성됩니다. Lync Server 2013 Enterprise Voice 배포의 경우 Exchange UM은 음성 메시지와 전자 메일 메시지를 전화에서 액세스할 수 있는 단일 저장소(Outlook Voice Access) 또는 컴퓨터에 통합합니다. Exchange UM 및 Lync Server 2013은 함께 작동하여 Enterprise Voice 사용자에게 전화 응답, Outlook Voice Access 및 자동 전화 교환 서비스를 제공합니다.

온-프레미스 Exchange UM 배포와의 통합을 위한 지원 외에, Lync Server 2013에서는 호스팅된 Exchange UM과의 통합도 지원됩니다. 따라서 일부 또는 모든 사용자를 Microsoft Exchange Online 등의 호스팅된 Exchange 서비스 공급자로 마이그레이션하는 경우 해당 사용자에게 음성 메시지를 제공할 수 있습니다.

Lync Server 2013에서 지원하는 버전은 다음과 같습니다.

  - Microsoft Exchange 2013

  - Microsoft Exchange Server 2010(필수) 또는 최신 서비스 팩(권장)

  - Microsoft Exchange Server 2007 SP1(서비스 팩 1)(필수) 또는 최신 서비스 팩(권장)

Exchange UM을 Lync Server 2013 또는 Lync Server 2013 데이터베이스와 함께 배치할 수는 없습니다. Exchange UM 및 Lync Server 2013은 각각 별도의 포리스트에 설치할 수 있습니다.


> [!NOTE]
> PBX가 배포된 Enterprise Voice 배포에서는 Exchange UM이 필요하지 않을 수 있는데, 이는 PBX로 모든 사용자에게 음성 메일 및 관련 서비스를 계속 제공할 수 있기 때문입니다. 이후에 PBX를 사용하지 않게 될 경우, 예를 들어 공중 전화망(PSTN) 연결용으로 SIP 트렁크를 배포하는 경우에는 이전에 PBX 음성 메일 시스템을 사용했던 사용자에게 음성 메일을 제공하도록 Exchange UM을 다시 구성해야 합니다.



## 이 단원의 내용

  - [Lync Server 2013의 온-프레미스 통합 메시징의 구성 요소 및 토폴로지](lync-server-2013-components-and-topologies-for-on-premises-unified-messaging.md)

  - [Lync Server 2013의 호스팅된 Exchange UM 통합 지원](lync-server-2013-support-for-hosted-exchange-um-integration.md)

