---
title: 'Lync Server 2013: 내부 서버와 에지 서버 간의 연결 확인'
TOCTitle: 내부 서버와 에지 서버 간의 연결 확인
ms:assetid: 219f706e-2b8a-46c5-b394-c384240eef50
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398292(v=OCS.15)
ms:contentKeyID: 49303040
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 내부 서버와 에지 서버 간의 연결 확인

 

_**마지막으로 수정된 항목:** 2012-09-08_

Lync Server 2013에서는 별도의 유효성 검사 마법사를 통해 에지 서버와 내부 서버 간의 연결 유효성을 검사할 수 있었습니다. Lync Server 2013에서는 에지 서버를 설치하면 연결 유효성 검사가 자동으로 수행됩니다.

중앙 관리 저장소가 있는 내부 컴퓨터 또는 Lync Server 2013 핵심 구성 요소(OcsCore.msi)가 설치되어 있는 도메인에 가입된 컴퓨터에서 Windows PowerShell**Get-CsManagementStoreReplicationStatus** cmdlet을 실행하여 에지에 대한 구성 정보 복제의 유효성을 확인할 수 있습니다. 초기 결과에서는 복제 상태가 "True"가 아닌 "False"로 표시될 수 있습니다. 이 경우 **Invoke-CsManagementStoreReplication** cmdlet을 실행하고 복제가 완료될 때까지 기다린 후에 **Get-CsManagementStoreReplicationStatus**를 다시 실행합니다.

외부 사용자 연결은 별도로 확인할 수 있으며, Office Communications Server 원격 연결 분석기를 사용하여 원격 사용자 연결을 확인할 수도 있습니다. 자세한 내용은 [Lync Server 2013에서 외부 사용자에 대한 연결 확인](lync-server-2013-verify-connectivity-for-external-users.md)을 참조하십시오.

