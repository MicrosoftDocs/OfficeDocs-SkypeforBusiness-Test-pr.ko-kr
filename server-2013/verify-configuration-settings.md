---
title: 구성 설정 확인
TOCTitle: 구성 설정 확인
ms:assetid: 51c2d1d9-63f7-43ab-88ca-b8913da7cede
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204885(v=OCS.15)
ms:contentKeyID: 49303633
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 구성 설정 확인

 

_**마지막으로 수정된 항목:** 2012-09-06_

중앙 관리 저장소가 있는 내부 컴퓨터 또는 Lync Server 2013 핵심 구성 요소(OcsCore.msi)가 설치되어 있는 도메인에 가입된 컴퓨터에서 Lync Server 2013**Get-CsManagementStoreReplicationStatus** cmdlet을 실행하여 에지 서버에 대한 구성 정보 복제의 유효성을 확인할 수 있습니다.

초기 결과에서는 복제 상태가 "True"가 아닌 "False"로 표시될 수 있습니다.이 경우 **Invoke-CsManagementStoreReplication** cmdlet을 실행하여 복제가 완료될 때까지 기다린 후에 **Get-CsManagementStoreReplicationStatus**를 다시 실행합니다.

