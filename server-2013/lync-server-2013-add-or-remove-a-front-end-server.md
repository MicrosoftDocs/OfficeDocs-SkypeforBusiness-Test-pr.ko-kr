---
title: Lync Server 2013에서 프런트 엔드 서버 추가 또는 제거
TOCTitle: Lync Server 2013에서 프런트 엔드 서버 추가 또는 제거
ms:assetid: ab748733-6bad-4c93-8dda-db8d5271653d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205153(v=OCS.15)
ms:contentKeyID: 49304691
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 프런트 엔드 서버 추가 또는 제거

 

_**마지막으로 수정된 항목:** 2013-11-19_

풀에 프런트 엔드 서버를 추가하거나 풀에서 프런트 엔드 서버를 제거한 경우 풀을 다시 시작해야 합니다. 프런트 엔드 서버를 추가하거나 제거할 때 사용자에 대한 서비스 중단을 방지하려면 다음 절차를 따르십시오.

## 프런트 엔드 서버 추가 또는 제거

1.  프런트 엔드 서버를 제거하는 경우 먼저 해당 서버에 대한 새 연결을 중지합니다. 이를 위해 다음 cmdlet을 사용할 수 있습니다.
    
        Stop -CsWindowsServices -Graceful

2.  제거하려는 서버에 현재 세션이 없는 경우 해당 서버에서 Lync Server 서비스를 중지합니다.

3.  토폴로지 작성기를 열고 필요한 서버를 추가하거나 제거합니다.

4.  토폴로지를 게시합니다.

5.  풀에 프런트 엔드 서버가 2개에서 3개 이상으로 늘어났거나 3개 이상에서 정확히 2개로 줄어든 경우 다음 cmdlet을 입력해야 합니다.
    
        Reset-CsPoolRegistrarState-ResetType FullReset -PoolFqdn <PoolFqdn>
    
    풀에 서버가 3개 이상 있는 경우 이 cmdlet을 입력할 때 이러한 서버 중 적어도 3개가 실행되고 있어야 합니다.

6.  풀의 모든 프런트 엔드 서버를 한 번에 하나씩 다시 시작합니다.

