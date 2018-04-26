---
title: 'Lync Server 2013: 응답 그룹 구성'
TOCTitle: 응답 그룹 구성
ms:assetid: c56db929-cb21-4af0-be3f-c8f807b78a5a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205249(v=OCS.15)
ms:contentKeyID: 49304978
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 응답 그룹 구성

 

_**마지막으로 수정된 항목:** 2012-10-30_

응답 그룹은 지원 센터나 고객 서비스 센터와 같이 수신 전화를 사용자 그룹( *에이전트* 라고도 함)으로 경로 지정하거나 큐에 대기시키는 Enterprise Voice 기능입니다.

응답 그룹에 필요한 구성 요소는 Enterprise Voice를 배포하는 동안 자동으로 프런트 엔드 서버 또는 Standard Edition Server에 설치되어 사용하도록 설정됩니다. 사용자가 응답 그룹을 사용할 수 있도록 하려면 에이전트 그룹을 구성하고, 큐와 워크플로를 차례로 구성해야 합니다. 또한 응답 그룹 관리자는 기존 워크플로 구성을 응답 그룹 관리자에게 위임하여 관련 에이전트 그룹 및 큐, 그리고 워크플로를 수정 및 재구성할 수 있도록 해야 합니다.

이 섹션에서는 Lync Server 2013응답 그룹을 구성하는 단계를 안내합니다. 본 섹션의 내용은 사용자가 응답 그룹 관련 계획 섹션을 읽고 Enterprise Edition 서버 또는 Standard Edition Server에 Enterprise Voice을 배포했음을 전제로 합니다.


> [!TIP]
> 샘플 스크립트를 포함한 Lync Server 관리 셸을 사용하여 응답 그룹을 만드는 방법에 대한 자세한 내용은 <A class=uri href="http://go.microsoft.com/fwlink/?linkid=204108%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=204108&amp;clcid=0x412</A>()의 "Creating Your First Response Group Using Lync Server Management Shell(Lync Server 관리 셸을 사용하여 첫 번째 응답 그룹 만들기)"을 참조하십시오.



## 이 단원의 내용

  - [Lync Server 2013의 응답 그룹 구성 권한 및 필수 구성 요소](lync-server-2013-response-group-configuration-permissions-and-prerequisites.md)

  - [Lync Server 2013의 응답 그룹 배포 프로세스](lync-server-2013-deployment-process-for-response-group.md)

  - [Lync Server 2013의 워크플로 작성 시나리오의 개요](lync-server-2013-overview-of-workflow-creation-scenarios.md)

  - [Lync Server 2013에서 응답 그룹 에이전트 그룹 만들기](lync-server-2013-create-response-group-agent-groups.md)

  - [Lync Server 2013에서 응답 그룹 큐 만들기](lync-server-2013-create-response-group-queues.md)

  - [(선택 사항) Lync Server 2013에서 응답 그룹 업무 시간 정의](lync-server-2013-optional-define-response-group-business-hours.md)

  - [(선택 사항) Lync Server 2013에서 응답 그룹 휴일 집합 정의](lync-server-2013-optional-define-response-group-holiday-sets.md)

  - [Lync Server 2013에서 응답 그룹 워크플로 만들기](lync-server-2013-create-response-group-workflows.md)

  - [(선택 사항) Lync Server 2013에서 응답 그룹 배포 확인](lync-server-2013-optional-verify-response-group-deployment.md)

## 참고 항목

#### 기타 리소스

[Lync Server 2013의 통화 관리 기능 계획](lync-server-2013-planning-for-call-management-features.md)

