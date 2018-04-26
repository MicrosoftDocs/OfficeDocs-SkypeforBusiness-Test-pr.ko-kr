---
title: 'Lync Server 2013: 백업 서비스로 전화 회의 내용 복원'
TOCTitle: 백업 서비스로 전화 회의 내용 복원
ms:assetid: 3e0f18ec-7319-4c07-a59b-2938e7787bc9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688030(v=OCS.15)
ms:contentKeyID: 49885734
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 백업 서비스로 전화 회의 내용 복원

 

_**마지막으로 수정된 항목:** 2012-11-01_

프런트 엔드 풀의 파일 저장소에 저장된 회의 정보가 사용할 수 없는 상태가 되면 풀에 있는 사용자가 자신의 회의 데이터를 보유할 수 있도록 이 정보를 복원해야 합니다. 회의 데이터가 손실된 프런트 엔드 풀이 다른 프런트 엔드 풀과 쌍으로 연결된 경우 백업 서비스를 사용하여 데이터를 복원할 수 있습니다.

또한 전체 풀이 실패한 경우에도 이 작업을 수행해야 하며 해당 사용자를 백업 풀로 장애 조치(failover)해야 합니다. 이러한 사용자를 원래 풀로 다시 장애 조치(failover)한 경우 이 절차에 따라 해당 회의 콘텐츠를 다시 원래 풀에도 복사해야 합니다.

풀1이 풀2와 쌍으로 연결되었고 풀1의 회의 데이터가 손실되었다고 가정한다면 다음 cmdlet을 사용해서 콘텐츠를 복원하도록 백업 서비스를 호출할 수 있습니다.

    Invoke-CsBackupServiceSync -PoolFqdn <Pool2 FQDN> -BackupModule ConfServices.DataConf

회의 콘텐츠를 복원할 때는 크기에 따라 시간이 오래 걸릴 수 있습니다. 다음 cmdlet을 사용해서 프로세스 상태를 확인할 수 있습니다.

    Get-CsBackupServiceStatus -PoolFqdn <Pool2 FQDN> -BackupModule ConfServices.DataConf

이 cmdlet이 데이터 회의 모듈에 대해 정상 상태 값을 반환하면 처리가 완료된 것입니다.

