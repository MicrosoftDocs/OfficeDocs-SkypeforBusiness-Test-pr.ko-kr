---
title: 'Lync Server 2013: 워크플로 작성 시나리오의 개요'
TOCTitle: 워크플로 작성 시나리오의 개요
ms:assetid: 05e0c175-0f1a-4bb1-b048-c68584d00649
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204646(v=OCS.15)
ms:contentKeyID: 49302689
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 워크플로 작성 시나리오의 개요

 

_**마지막으로 수정된 항목:** 2012-10-17_

워크플로를 만들 때는 다음의 두 가지 시나리오를 사용할 수 있습니다.

  - **관리자가 워크플로를 만들고 구성함** - CsResponseGroupAdministrator 역할 구성원 또는 그와 동일한 사용자가 워크플로 및 워크플로의 모든 요소(예: 에이전트 그룹, 큐, 휴일, 업무 시간, 통화 대기음 등)를 만들고 활성화합니다.

  - **관리자가 워크플로를 만들고 관리자가 옵션을 구성함** - CsResponseGroupAdministrator 역할 구성원 또는 그와 동일한 사용자가 기본 SIP URI와 표시 이름을 정의하고, CsResponseGroupManager 역할의 구성원을 한 명 이상 할당하고, 큐를 선택하고 워크플로를 할당합니다. 그러면 CsResponseGroupManager가 로그온한 다음 에이전트 그룹을 만들어 워크플로 구성을 편집할 수 있으며, 그룹을 큐에 할당하여 전화 번호, 휴일/업무 시간, 통화 대기음 등을 구성할 수 있습니다.
    

    > [!NOTE]
    > 관리되는 워크플로를 만들려면 워크플로를 활성으로 만들어야 합니다. 활성 관리되는 워크플로를 저장하고 나면 워크플로를 수정하고 비활성화할 수 있습니다.


