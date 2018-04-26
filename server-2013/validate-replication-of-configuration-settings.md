---
title: 구성 설정 복제의 유효성 검사
TOCTitle: 구성 설정 복제의 유효성 검사
ms:assetid: 81a3c21d-b28a-4287-adac-11791e8db56d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205042(v=OCS.15)
ms:contentKeyID: 49304207
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 구성 설정 복제의 유효성 검사

 

_**마지막으로 수정된 항목:** 2012-10-19_

중앙 관리 저장소가 있는 내부 컴퓨터 또는 Lync Server 2013 핵심 구성 요소가 설치된 도메인 연결 컴퓨터에서 Lync Server 2013**Get-CsManagementStoreReplicationStatus** cmdlet을 실행하여 에지 서버에 대한 구성 정보 복제의 유효성을 검사할 수 있습니다.

초기 결과에서는 복제 상태가 "True"가 아닌 "False"로 표시될 수 있습니다.이 경우 **Invoke-CsManagementStoreReplication** cmdlet을 실행하여 복제가 완료될 때까지 기다린 후에 **Get-CsManagementStoreReplicationStatus** cmdlet을 다시 실행합니다.

