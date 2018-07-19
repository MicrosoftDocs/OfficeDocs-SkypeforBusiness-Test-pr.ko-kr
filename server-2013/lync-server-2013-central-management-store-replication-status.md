---
title: 'Lync Server 2013: 중앙 관리 저장소 복제 상태'
TOCTitle: 중앙 관리 저장소 복제 상태
ms:assetid: f514f88d-986b-4e45-b79b-e04a7616c1fe
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn720926(v=OCS.15)
ms:contentKeyID: 62240127
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 중앙 관리 저장소 복제 상태

 

_**마지막으로 수정된 항목:** 2015-01-26_

관리자가 Lync Server에서 어떤 부분을 변경하는 경우, 예를 들어 관리자가 새 음성 정책을 만들거나 주소록 서버 구성 설정을 변경하는 경우 해당 변경 내용이 중앙 관리 저장소에 기록됩니다. 그러면 이러한 변경 내용을 Lync Server 서비스 또는 서버 역할을 실행 중인 모든 컴퓨터에 복제해야 합니다.

데이터를 복제하기 위해 중앙 관리 서버에서 실행되는 Master Replicator는 변경된 구성 데이터의 스냅샷을 만듭니다. 그러면 이 스냅샷의 복사본을 Lync Server 서비스 또는 서버 역할을 실행 중인 각 컴퓨터에 전송합니다. 이러한 컴퓨터에서는 복제 에이전트가 스냅샷을 수신하고 변경된 데이터를 업로드합니다. 그런 다음 에이전트는 Master Replicator에 최신 복제 상태를 알리는 메시지를 전송합니다.

Get-CsManagementStoreReplicationStatus cmdlet을 사용하면 조직에서 사용하는 모든 Lync Server 컴퓨터의 복제 상태를 확인할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자는 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원이며, Get-CsManagementStoreReplicationStatus cmdlet을 로컬로 실행할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsManagementStoreReplicationStatus"}

## 참고 항목

#### 기타 리소스

[Get-CsManagementStoreReplicationStatus](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsManagementStoreReplicationStatus)

