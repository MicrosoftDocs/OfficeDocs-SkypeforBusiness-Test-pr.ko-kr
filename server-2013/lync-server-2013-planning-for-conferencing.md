---
title: 'Lync Server 2013: 회의 계획'
TOCTitle: 회의 계획
ms:assetid: 983a272a-e1b3-4d70-8f84-836b092fe526
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398781(v=OCS.15)
ms:contentKeyID: 49304470
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 회의 계획

 

_**마지막으로 수정된 항목:** 2013-01-29_

Lync Server 2013에서는 다음과 같은 풍부한 회의 기능을 제공합니다.

  - 웹 회의: 문서 공동 작업, 응용 프로그램 공유 및 데스크톱 공유가 포함됩니다. Lync Server 2013에서는 Office Web Apps와 Office Web Apps 서버를 사용하여 PowerPoint 프레젠테이션 공유 및 렌더링을 처리합니다. Office Web Apps 서버를 설치하고 구성하는 방법에 대한 자세한 내용은 [Office Online Server 및 Lync Server 2013과 통합 구성](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md)를 참조하십시오.

  - A/V(오디오/비디오) 회의: Microsoft Live Meeting 서비스나 타사 오디오 브리지 등의 외부 서비스 없이 실시간 오디오 또는 비디오 회의를 할 수 있습니다.

  - 전화 접속 회의: 타사 오디오 회의 공급자 없이 PSTN(공중 전화망) 전화를 사용하여 Lync Server 2013 회의의 오디오 부분에 참가할 수 있습니다.

  - IM(인스턴트 메시징) 회의: 단일 IM 세션에서 두 명 이상의 사람이 통신합니다. IM 회의에 대한 자세한 내용은 [Lync Server 2013의 프런트 엔드 서버, 메신저 및 현재 상태 계획](lync-server-2013-planning-for-front-end-servers-instant-messaging-and-presence.md)을 참조하십시오.

Lync Server 2013에서는 예약된 회의와 즉석 회의가 모두 지원됩니다.

Lync Server 2013,  프런트 엔드 서버 배포 시 웹 회의, A/V 회의 및 전화 접속 회의 기능도 배포할 것인지를 선택할 수 있습니다. IM 회의 기능은 항상 자동으로 IM 대화 기능과 함께 Lync Server 2013  프런트 엔드 서버에 배포됩니다.


> [!NOTE]
> 배포에 Office Communicator 2007 R2 클라이언트( Live Meeting 콘솔 또는 Microsoft Office Outlook용 회의 추가 기능 포함)를 사용하는 모임이 포함된 경우 해당 모임을 Lync Server 2013으로 마이그레이션하고 나면 다음과 같은 제한이 적용됩니다. 
> <UL>
> <LI>
> <P>모임의 사용자가 문서 공동 작업, 응용 프로그램 공유, 데스크톱 공유를 비롯한 데이터 공동 작업 기능을 사용할 수 없게 됩니다.</P>
> <LI>
> <P>Office Communicator 2007 R2 클라이언트는 Lync Server 2013에서 지원되지 않기 때문에 안정성 문제가 발생할 수 있습니다.</P></LI></UL>이러한 문제를 방지하려면 Office Communicator 2007 R2 클라이언트를 사용하여 구성된 모임을 Outlook 2010 또는 Outlook 2013에서 Lync 2010용 온라인 모임 추가 기능이나 Lync 2013용 온라인 모임 추가 기능을 사용해 다시 예약합니다.



다음 섹션에서는 계획 프로세스, 구성 요소, 하드웨어와 소프트웨어 요구 사항 및 배포 프로세스를 비롯한 다양한 회의 기능 유형을 배포하는 데 필요한 사항에 대해 설명합니다.

## 이 단원의 내용

  - [Lync Server 2013의 회의 개요](lync-server-2013-overview-of-conferencing.md)

  - [Lync Server 2013에서 회의 요구 사항 정의](lync-server-2013-defining-your-requirements-for-conferencing.md)

  - [Lync Server 2013의 회의의 구성 요소 및 토폴로지](lync-server-2013-components-and-topologies-for-conferencing.md)

  - [Lync Server 2013의 회의에 대한 기술 요구 사항](lync-server-2013-technical-requirements-for-conferencing.md)

  - [Lync Server 2013의 회의에 대한 배포 검사 목록](lync-server-2013-deployment-checklist-for-conferencing.md)

  - [Lync Server 2013의 대규모 모임 지원](lync-server-2013-support-for-large-meetings.md)

