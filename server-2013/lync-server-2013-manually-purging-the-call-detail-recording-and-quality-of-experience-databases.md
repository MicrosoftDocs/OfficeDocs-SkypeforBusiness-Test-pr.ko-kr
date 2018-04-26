---
title: 통화 정보 기록 및 체감 품질 데이터베이스 수동 제거
TOCTitle: 통화 정보 기록 및 체감 품질 데이터베이스 수동 제거
ms:assetid: 3a3a965b-b861-41a4-b9a8-27184d622c17
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204812(v=OCS.15)
ms:contentKeyID: 49303350
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 통화 정보 기록 및 체감 품질 데이터베이스 수동 제거

 

_**마지막으로 수정된 항목:** 2014-07-07_

이전 섹션에서 언급한 것처럼, 관리자는 데이터베이스에서 오래된 레코드를 자동으로 삭제하도록 CDR(통화 정보 기록) 및/또는 QoE(체감 품질) 데이터베이스를 구성할 수 있습니다. 지정된 데이터베이스(CDR 또는 QoE)에 대해 삭제가 사용하도록 설정되었으며 데이터베이스에 지정한 시간보다 오랫동안 보관된 레코드가 있는 경우 이 작업이 수행됩니다. 예를 들어 관리자는 60일보다 오래된 QoE 레코드가 매일 오전 1시에 QoE 데이터베이스에서 삭제되도록 시스템을 구성할 수 있습니다.

자동 삭제 외에도 두 개의 새로운 cmdlet(Invoke-CsCdrDatabasePurge 및 Invoke-CsQoEDatbasePurge)이 Microsoft Lync Server 2013에 추가되었습니다.

    Invoke-CsCdrDatabasePurge -Identity MonitoringDatabase:atl-sql-001.litwareinc.com -PurgeCallDetailDataOlderThanDays 10 -PurgeDiagnosticDataOlderThanDays 10

위의 예에서는 10일보다 오래된 통화 정보 기록 및 진단 데이터 레코드가 모두 atl-sql-001.litwareinc.com의 모니터링 데이터베이스에서 삭제됩니다. 통화 정보 기록은 사용자/세션 보고서입니다. 진단 데이터 레코드는 Lync 2013 등의 클라이언트 응용 프로그램에서 업로드하는 진단 로그입니다.

위에 나와 있는 것처럼, Invoke-CsCdrDatabasePurge cmdlet을 실행할 때는 PurgeCallDetaiDataOlderThanDays 및 PurgeDiagnosticDataOlderThanDays 매개 변수를 둘 다 포함해야 합니다. 그러나 이러한 매개 변수를 같은 값으로 설정할 필요는 없습니다. 예를 들어 10일보다 오래된 통화 정보 기록은 삭제하는 동시에 진단 데이터 레코드는 모두 데이터베이스에 남겨 둘 수 있습니다. 이렇게 하려면 PurgeCallDetailDataOlderThanDays는 10으로 설정하고 PurgeDiagnosticDataOlderThanDays는 0으로 설정합니다. 예를 들면 다음과 같습니다.

    Invoke-CsCdrDatabasePurge -Identity MonitoringDatabase:atl-sql-001.litwareinc.com -PurgeCallDetailDataOlderThanDays 10 -PurgeDiagnosticDataOlderThanDays 0

기본적으로 Invoke-CsCdrDatabasePurge를 실행할 때마다 삭제해야 하는 각 데이터베이스 테이블에 대해 다음과 같은 메시지가 표시됩니다.

    Confirm
    Are you sure you want to perform this action?
    Performing operation "Stored procedure: RtcCleanupDiag" on Target "Target SQL Server:atl-sql-001.litwareinc.com\archinst Database: lcscdr".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All [S] Suspend  [?] Help (default is "Y"):

Y(예) 또는 A(모두 예)를 입력해야 데이터베이스 삭제가 실제로 수행됩니다. 이러한 확인 메시지가 표시되지 않도록 하려면 Invoke-CsCdrDatabasePurge 호출 끝부분에 다음 매개 변수를 추가합니다.

    -Confirm:$False

예를 들면 다음과 같습니다.

    Invoke-CsCdrDatabasePurge -Identity MonitoringDatabase:atl-sql-001.litwareinc.com -PurgeCallDetailDataOlderThanDays 10 -PurgeDiagnosticDataOlderThanDays 10 -Confirm:$False

이렇게 하면 확인 메시지가 표시되지 않으며 데이터베이스 삭제가 즉시 수행됩니다.

QoE 데이터베이스를 삭제하려면 Invoke-CsQoEDatabasePurge cmdlet을 사용하고 삭제할 레코드의 기간을 일 단위로 지정합니다.

    Invoke-CsQoEDatabasePurge -Identity MonitoringDatabase:atl-sql-001.litwareinc.com -PurgeQoEDataOlderThanDays 10

