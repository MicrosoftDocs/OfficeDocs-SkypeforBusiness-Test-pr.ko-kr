---
title: "Lync Server 2013 프런트 엔드 풀에 SBA(Survivable Branch Appliance) 연결"
TOCTitle: Lync Server 2013 프런트 엔드 풀에 SBA(Survivable Branch Appliance) 연결
ms:assetid: 3c7ca33f-5295-4d82-9152-41d8bc6f35cf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688026(v=OCS.15)
ms:contentKeyID: 49885729
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 프런트 엔드 풀에 SBA(Survivable Branch Appliance) 연결

 

_**마지막으로 수정된 항목:** 2012-10-05_

모든 SBA( SBA(Survivable Branch Appliance))는 SBA에 대한 백업 등록자로 작동하는 프런트 엔드 풀과 연결됩니다. 프런트 엔드 풀을 Lync Server 2013으로 업그레이드할 경우에는 프런트 엔드 풀을 업그레이드하는 동안 프런트 엔드 풀에서 SBA 연결을 해제해야 합니다. 프런트 엔드 풀을 업그레이드한 후에는 SBA를 프런트 엔드 풀과 다시 연결할 수 있습니다. 이렇게 하려면 토폴로지 작성기를 사용하여 토폴로지에서 SBA를 삭제한 후 다시 SBA를 토폴로지 작성기에 추가해야 합니다. SBA에 있는 사용자는 토폴로지에서 SBA를 제거하기 전에 먼저 다른 프런트 엔드 풀로 이동해야 합니다. SBA를 토폴로지에 다시 추가한 후에는 해당 사용자를 다시 SBA로 이동할 수 있습니다.

이러한 단계는 아래에 요약되어 있습니다.

1.  SBA에 있는 분기 사용자를 다른 프런트 엔드 풀로 이동합니다.

2.  토폴로지에서 SBA를 제거하여 백업 등록자로 사용되는 기존 프런트 엔드 풀과의 연결을 해제합니다.

3.  프런트 엔드 풀을 Microsoft Lync Server 2013로 업그레이드합니다.

4.  토폴로지에 다시 SBA를 추가합니다.

5.  백업 등록자로 사용되는 새 프런트 엔드 풀을 SBA에 연결합니다.

6.  분기 사용자를 다시 SBA로 이동합니다.

## 이 단원의 내용

  - [토폴로지에 Lync Server 2013 SBA(Survivable Branch Appliance) 분기 사이트 추가](lync-server-2013-add-lync-server-2013-survivable-branch-appliance-branch-site-to-your-topology.md)

  - [토폴로지에 Lync Server 2010 SBA(Survivable Branch Appliance) 분기 사이트 추가](lync-server-2013-add-lync-server-2010-survivable-branch-appliance-branch-site-to-your-topology.md)

