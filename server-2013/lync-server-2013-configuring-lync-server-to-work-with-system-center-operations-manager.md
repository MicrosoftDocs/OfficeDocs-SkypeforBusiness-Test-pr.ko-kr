---
title: System Center Operations Manager와 함께 작동하도록 Lync Server 구성
TOCTitle: System Center Operations Manager와 함께 작동하도록 Lync Server 구성
ms:assetid: b55a24ab-648b-4142-b3cd-3792860ba872
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205188(v=OCS.15)
ms:contentKeyID: 49304786
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# System Center Operations Manager와 함께 작동하도록 Lync Server 구성

 

_**마지막으로 수정된 항목:** 2012-10-22_

Microsoft Lync Server 2013 인프라가 System Center Operations Manager와 함께 작동하도록 구성하려면 다음 세 가지 작업을 수행해야 합니다.

  - 주 System Center Operations Manager 관리 서버를 지정하고 구성합니다. 관리 서버를 구성하는 작업에는 System Center Operations Manager 2012 또는 System Center Operations Manager 2007 R2 설치와 SQL Server를 사용한 백 엔드 데이터베이스 설정이 포함됩니다. 사용해야 할 실제 SQL Server 버전은 사용 중인 System Center Operations Manager 버전에 따라 달라집니다. 자세한 내용은 [기본 관리 서버 구성](lync-server-2013-configuring-the-primary-management-server.md)을 참조하십시오.

  - 모니터링할 Lync Server 컴퓨터를 지정하고 구성합니다. System Center Operations Manager를 사용하여 Lync Server 컴퓨터를 모니터링하려면 System Center Operations Manager 에이전트 파일을 설치하고 각 서버가 프록시로 작동하도록 구성해야 합니다.

  - Lync Server*감시자 노드*로 작동할 컴퓨터를 지정하고 구성합니다. 감시자 노드는 정기적으로 Lync Server 가상 트랜잭션을 실행하는 컴퓨터입니다. 이러한 가상 트랜잭션은 Windows PowerShell cmdlet으로서 시스템에 로그온하는 기능이나 인스턴트 메시지 교환 기능이 예상대로 작동하는지를 확인하는 것을 비롯하여 주요 Lync Server 구성 요소를 확인합니다.

이 섹션의 항목에는 이러한 각 작업을 수행하는 지침이 포함되어 있습니다.

## 이 섹션의 내용

  - [기본 관리 서버 구성](lync-server-2013-configuring-the-primary-management-server.md)

  - [Lync Server 2013 관리 팩 설치](lync-server-2013-installing-the-lync-server-2013-management-packs.md)

  - [모니터링할 Lync Server 컴퓨터 구성](lync-server-2013-configuring-the-lync-server-computers-that-will-be-monitored.md)

  - [감시자 노드 설치 및 구성](lync-server-2013-installing-and-configuring-watcher-nodes.md)

