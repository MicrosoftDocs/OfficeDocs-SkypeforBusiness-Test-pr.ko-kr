---
title: Lync Server 2013에서 프런트 엔드 서버 업그레이드 또는 업데이트
TOCTitle: Lync Server 2013에서 프런트 엔드 서버 업그레이드 또는 업데이트
ms:assetid: 20fa39ae-ecfb-4c72-9cc4-8e183d3c752f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204736(v=OCS.15)
ms:contentKeyID: 49303034
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 프런트 엔드 서버 업그레이드 또는 업데이트

 

_**마지막으로 수정된 항목:** 2013-06-28_

Enterprise Edition 풀의 프런트 엔드 서버는 *업그레이드 도메인*으로 구성됩니다. 이러한 도메인은 풀에 있는 프런트 엔드 서버의 하위 집합입니다. 업그레이드 도메인은 토폴로지 작성기에서 자동으로 작성됩니다.

프런트 엔드 서버를 업그레이드할 때는 업그레이드 도메인을 한 번에 하나씩 수행해야 합니다. 하나의 업그레이드 도메인의 각 서버를 가져와서 업그레이드한 다음 다른 업그레이드 도메인으로 이동하기 전에 다시 시작합니다. 지금까지 업그레이드한 업그레이드 도메인 및 서버를 계속 추적해야 합니다. 각 서버를 업그레이드할 때 다음과 같은 순서도 다이어그램을 사용하세요.

![서버 업그레이드 순서도](images/JJ204736.42ed59a4-1c26-49f7-ade4-a5a788457ab9(OCS.15).jpg "서버 업그레이드 순서도")

## 풀의 프런트 엔드 서버에 업그레이드 적용

1.  풀의 프런트 엔드 서버에서 다음 cmdlet을 실행합니다.
    
    **Get-CsPoolUpgradeReadinessState**
    
    *PoolUpgradeState*의 상태가 **Busy**이면 10분 동안 기다렸다가 **Get-CsPoolUpgradeReadinessState**를 다시 실행해 봅니다. 각 시도 사이에 10분 동안 기다렸다가 cmdlet을 다시 실행했는데 **Busy**가 3회 이상 표시되거나 **PoolUpgradeState**에 대해 결과로 **InsufficientActiveFrontEnds**가 표시되는 경우에는 풀에 문제가 있는 것입니다. 이 풀이 재해 복구 토폴로지의 다른 프런트 엔드 풀과 쌍으로 지정되어 있는 경우 해당 풀을 백업 풀로 장애 조치(failover)한 후 이 풀의 서버를 업데이트해야 합니다. 자세한 내용은 [Lync Server 2013 에서 풀 장애 조치(failover)](lync-server-2013-failing-over-a-pool.md)를 참고하세요.
    
    *PoolUpgradeState*의 값이 **Ready**이면 2단계로 이동합니다.

2.  **Get-CsPoolUpgradeReadinessState**cmdlet은 풀의 각 업그레이드 도메인에 대한 정보와 각 업그레이드 도메인에 있는 프런트 엔드 서버에 대한 정보도 반환합니다. 업그레이드하려는 서버가 포함된 업그레이드 도메인에 대해 **ReadyforUpgrade** 값이 **True**이면 해당 서버를 바로 업그레이드해도 안전합니다. 이렇게 하려면 다음을 수행합니다.
    
    1.  `Stop-CsWindowsService -Graceful -Verbose` cmdlet을 사용하여 업그레이드하려는 프런트 엔드 서버에 대한 새 연결을 중지합니다..
        

        > [!NOTE]
        > 예정된 서버 중단 시간 동안에 이러한 서버 업그레이드를 수행할 예정이라면 ‘-<STRONG>Graceful</STRONG>‘ 매개 변수 없이 <STRONG>Stop-CsWindowsService</STRONG>처럼 이 cmdlet을 실행할 수 있습니다. 이렇게 하면 기존 서비스 요청이 모두 채워질 때까지 기다리지 않고 서비스가 바로 종료됩니다.

    
    2.  이 업그레이드 도메인과 연결된 서버를 업그레이드합니다.
    
    3.  서버를 다시 시작한 다음 서버가 새 연결을 수락하는지 확인합니다.

3.  프런트 엔드 서버가 모두 업그레이드될 때까지 풀에 있는 다른 모든 업그레이드 도메인에 대해 1-2단계를 반복합니다.

