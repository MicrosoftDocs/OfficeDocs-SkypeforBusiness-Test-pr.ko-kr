---
title: 'Lync Server 2013: 지원되는 서버 마이그레이션 경로 및 동시 사용 시나리오'
TOCTitle: 지원되는 서버 마이그레이션 경로 및 동시 사용 시나리오
ms:assetid: 2a6a730f-7f80-45f9-9540-3edfdaa265fb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425764(v=OCS.15)
ms:contentKeyID: 49303136
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 지원되는 서버 마이그레이션 경로 및 동시 사용 시나리오

 

_**마지막으로 수정된 항목:** 2012-10-16_

다음 항목에서 Lync Server 2013으로 마이그레이션할 수 있습니다.

  - Microsoft Lync Server 2010

  - Microsoft Office Communications Server 2007 R2

이 두 이전 버전을 모두 실행하는 환경으로부터의 마이그레이션은 지원되지 않습니다. Microsoft Office Communications Server 2007 또는 Live Communications Server 2005와 같은 이전 버전으로부터의 마이그레이션도 지원되지 않습니다. 이전 배포에 그룹 채팅이 포함되어 있는 경우에는 별도로 마이그레이션해야 합니다.

## 마이그레이션 방법

모든 Lync Server 토폴로지 및 서버 역할을 마이그레이션할 수 있습니다. Standard Edition 서버에서 Enterprise Edition 서버로의 마이그레이션을 포함하여 토폴로지 간 마이그레이션이 가능합니다.

Lync Server 2013에서는 다음 마이그레이션 방법만 지원합니다.

  -   
    **병렬 마이그레이션.** 병렬 마이그레이션에서는 Lync Server 2013이 기존 Microsoft Lync Server 2010 또는 Office Communications Server 2007 R2 배포와 함께 배포됩니다. 그런 후에 작업을 새 서버로 전송하고 사용자를 Lync Server 2013으로 이동합니다. 이 방법을 사용하는 경우 마이그레이션 도중 하드웨어 및 소프트웨어를 비롯한 추가 서버 플랫폼이 필요하며, 시스템 이름과 풀 이름이 새 구성에서 달라집니다. 이전 버전으로 롤백해야 하는 경우에는 작업을 다시 이전 서버로 이동하면 됩니다.

Active Directory 도메인 서비스 포리스트 간 마이그레이션은 지원되지 않습니다.

권장 마이그레이션 경로는 단계적 마이그레이션입니다. 적절한 구성 요소 배포 단계 지정을 비롯하여, 이전 릴리스에서 마이그레이션하는 방법에 대한 자세한 내용은 마이그레이션 설명서에서 다음 항목을 참조하십시오.

  - [Lync Server 2010에서 Lync Server 2013으로 마이그레이션](migration-from-lync-server-2010-to-lync-server-2013.md)

  - [Office Communications Server 2007 R2에서 Lync Server 2013으로 마이그레이션](migration-from-office-communications-server-2007-r2-to-lync-server-2013.md)

  - [Lync Server 2010, 그룹 채팅 또는 Office Communications Server 2007 R2 그룹 채팅에서 Lync Server 2013, 영구 채팅 서버로 마이그레이션](migration-from-lync-server-2010-group-chat-or-office-communications-server-2007-r2-group-chat-to-lync-server-2013-persistent-chat-server.md)

## 동시 사용 시나리오

Lync Server 2013은 Lync Server 2010 배포 또는 Office Communications Server 2007 R2 배포 구성 요소와 함께 사용할 수 있습니다. Lync Server 2013을 Lync Server 2010 및 Office Communications Server 2007 R2와 동시에 배포할 수는 없습니다(세 버전을 모두 동시에 배포할 수는 없음).

이전 Lync Server 2013 또는 Office Communications Server 2007 R2 배포가 일시적으로 새 Lync Server 2010 배포와 함께 사용되는 단계별 마이그레이션에서는 혼합 버전 라우팅 지원이 제한됩니다. 자세한 내용은 마이그레이션 설명서를 참조하십시오.

Microsoft SQL Server 2008 R2 또는 Microsoft SQL Server 2012를 실행하는 별도의 고유한 컴퓨터를 Lync Server 2013 데이터베이스 인스턴스용으로 사용해야 합니다. Lync Server 2010 또는 Office Communications Server 2007 R2 프런트 엔드 풀에 사용하는 것과 같은 Lync Server 2013 프런트 엔드 풀용 SQL Server 인스턴스를 사용할 수는 없습니다. Lync Server 2010 또는 Office Communications Server 2007 R2가 이미 배포되어 있는 배포에 대해 토폴로지 작성기에서 Lync Server 2013을 정의 및 구성하는 경우 토폴로지 작성기에서는 토폴로지에서 이미 사용 중인 Lync Server 2013 인스턴스를 정의하도록 허용하지 않습니다.

토폴로지 작성기에는 이 문제를 알리기 위해 "SQL Server \[서버 FQDN\]에는 이미 역할 '사용자 저장소'을(를) 호스트하는 SQL 인스턴스가 포함되어 있습니다."라는 메시지가 표시됩니다.


> [!NOTE]
> Lync Server 2013 배포에 새로운 서버 역할을 배포하려는 경우에는 먼저 마이그레이션 설명서와 배포 설명서에 설명된 대로 기존 배포를 업그레이드한 다음, 계획 설명서 및 배포 설명서에 설명된 대로 새 서버 역할을 배포해야 합니다. 이전 버전 그룹 채팅을 마이그레이션하는 경우 다른 모든 구성 요소를 Lync Server 2010 또는 Office Communications Server 2007 R2로 마이그레이션하는 프로세스를 완료한 후 마지막에 마이그레이션하십시오.



Lync Server 2010 또는 Office Communications Server 2007 R2 및 Lync Server 2013 구성 요소의 동시 사용 및 마이그레이션에 대한 특정 동시 사용 요구 사항 및 기타 자세한 내용은 마이그레이션 설명서에서 [Lync Server 2010에서 Lync Server 2013으로 마이그레이션](migration-from-lync-server-2010-to-lync-server-2013.md) 및 [Office Communications Server 2007 R2에서 Lync Server 2013으로 마이그레이션](migration-from-office-communications-server-2007-r2-to-lync-server-2013.md)을 참조하십시오. 클라이언트의 혼합 버전 지원에 대한 자세한 내용은 [Lync Server 2013의 이전 배포에서 지원되는 클라이언트](lync-server-2013-supported-clients-from-previous-deployments.md)를 참조하십시오.

