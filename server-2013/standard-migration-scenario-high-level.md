---
title: 표준 마이그레이션 시나리오 - 고급
TOCTitle: 표준 마이그레이션 시나리오 - 고급
ms:assetid: e768a7ca-44e3-4969-a6d9-7ed3e7029c5c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205354(v=OCS.15)
ms:contentKeyID: 49305370
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 표준 마이그레이션 시나리오 - 고급

 

_**마지막으로 수정된 항목:** 2013-01-30_

Lync Server 2010, 그룹 채팅 또는 Office Communications Server 2007 R2그룹 채팅에서 Lync Server 2013, 영구 채팅 서버로 마이그레이션할 때 다음 항목을 시작점으로 사용하십시오. 표준 Lync Server 2013 마이그레이션 경로는 다음과 같습니다.

  - 조직에서 Lync Server 2010, 그룹 채팅 또는 Office Communications Server 2007 R2그룹 채팅을 배포했으며 Lync Server 2013, 영구 채팅 서버를 배포하려고 합니다.

  - Lync Server 2013을 배포하고 영구 채팅 서버 풀을 배포합니다.

  - 영구 채팅 대화방 마이그레이션을 준비하고 계획한 후, 마이그레이션을 위해 시스템을 종료할 적절한 시간을 결정합니다.

  - 마이그레이션을 위한 Windows PowerShell cmdlet(**Export-CsPersistentChatData** 및 **Import-CsPersistentChatData**)을 실행하여 콘텐츠를 영구 채팅 서버로 옮깁니다.

  - 마이그레이션이 성공적으로 수행되었는지 확인합니다.

  - 레거시 배포를 해제합니다.

  - 레거시 클라이언트가 Lync Server 2013, 영구 채팅 서버에 연결할 수 있도록 영구 채팅 서버를 구성합니다. 레거시 클라이언트를 보유한 기존 사용자가 최대한 빨리 대화방에 액세스할 수 있어야 하며 새 클라이언트를 배포하는 데는 다소 시간이 걸리므로 이 작업이 반드시 필요합니다.

  - 새 클라이언트를 배포합니다. 배포하는 동안 레거시 그룹 채팅(클라이언트)을 사용하는 작업자가 대화방에 연결할 수 있도록 계속 지원해야 합니다.

