---
title: 'Lync Server 2013: 풀 장애 복구(failback)'
TOCTitle: 풀 장애 복구(failback)
ms:assetid: 6232b644-ef57-4c9c-abec-14ff8ffc9fe7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204945(v=OCS.15)
ms:contentKeyID: 49303827
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 풀 장애 복구(failback)

 

_**마지막으로 수정된 항목:** 2012-11-01_

재해가 발생한 풀을 다시 온라인으로 전환한 후(이 예의 Pool1) 다음 단계에 따라 배포를 일반 작업 상태로 복원합니다.

복구(Failback) 프로세스는 완료하는 데 몇 분 정도 걸립니다. 일반적으로 사용자가 20,000명인 풀을 복구하는 데에는 최대 60분 정도 소요될 수 있습니다.

1.  다음 cmdlet을 사용해서 원래 Pool1에 있다가 Pool2로 장애 조치(Failover)되었던 사용자를 복구(Failback)합니다.
    
        Invoke-CsPoolFailback -PoolFQDN <Pool1 FQDN> -Verbose

다른 단계는 필요하지 않습니다. 중앙 관리 서버로 장애 조치(failover)한 경우 Pool2에 둘 수 있습니다.

