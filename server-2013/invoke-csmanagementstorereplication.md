---
title: Invoke-CsManagementStoreReplication
TOCTitle: Invoke-CsManagementStoreReplication
ms:assetid: fa3dece3-afd8-4669-94f9-fc3b70201e81
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413060(v=OCS.15)
ms:contentKeyID: 49305589
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Invoke-CsManagementStoreReplication

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 복제 서비스가 지정된 컴퓨터에 완전한 구성 데이터를 전송하도록 강제 설정합니다. 이 작업을 수행하기 위해 중앙 관리 저장소에서 컴퓨터의 복제 상태가 삭제됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Invoke-CsManagementStoreReplication [-ReplicaFqdn <String>] [-Force <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 매개 변수 없이 **Invoke-CsManagementStoreReplication** cmdlet을 호출합니다. 그러면 모든 Lync Server 컴퓨터에서 복제가 강제로 실행됩니다.

    Invoke-CsManagementStoreReplication

## 예제 2

예제 2에서는 **Invoke-CsManagementStoreReplication** cmdlet을 호출할 때 ReplicaFqdn 매개 변수를 사용합니다. 그러면 atl-cs-001.litwareinc.com 컴퓨터에서만 복제가 실행됩니다.

    Invoke-CsManagementStoreReplication -ReplicaFqdn atl-cs-001.litwareinc.com

## 자세한 정보

관리자가 Lync Server에서 어떤 부분을 변경하는 경우, 예를 들어 관리자가 새 음성 정책을 만들거나 주소록 서버 구성 설정을 변경하는 경우 해당 변경 내용이 중앙 관리 저장소에 기록됩니다. 그러면 이러한 변경 내용을 Lync Server 서비스 또는 서버 역할을 실행 중인 모든 컴퓨터에 복제해야 합니다.

데이터를 복제하기 위해 중앙 관리 서버에서 실행되는 Master Replicator는 수정된 구성 데이터의 스냅샷을 만들고 이 스냅샷의 복사본을 Lync Server 서비스 또는 서버 역할을 실행 중인 각 컴퓨터에 전송합니다. 이러한 컴퓨터에서는 복제 에이전트가 스냅샷을 수신하고 수정된 데이터를 업로드합니다. 그런 다음 Master Replicator에게 최신 복제 상태를 알리는 메시지를 전송합니다.

복제에는 일반적으로 사용자 작업이 필요하지 않습니다. 사실 Master Replicator로 복제 프로세스를 처리하는 것이 가장 좋습니다. 그러나 표준 복제 주기가 실행될 때까지 기다리지 않고 컴퓨터 또는 컴퓨터 그룹에서 강제로 복제를 시작해야 하는 경우가 있을 수 있습니다. 이러한 상황이 발생할 경우 **Invoke-CsManagementStoreReplication** cmdlet을 사용하여 강제로 컴퓨터에 정보를 복제할 수 있습니다.

일반적으로 복제는 증분 방식으로 작동합니다. 데이터를 복제할 때 전체 구성 데이터 집합이 아니라 변경 사항만 복제됩니다. 그러나 **Invoke-CsManagementStoreReplication** cmdlet을 호출하면 변경 사항만 더 일반적으로 복제되는 것이 아니라 모든 데이터가 강제로 전체 복제됩니다. **Invoke-CsManagementStoreReplication** cmdlet을 호출하는 즉시 복제가 반드시 실행되지는 않습니다. 대신 Master Replicator에서 변경 사항을 처리하는 동안 2-3분 정도 시간 지연이 발생할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Invoke-CsManagementStoreReplication** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Invoke-CsManagementStoreReplication"}

## 매개 변수


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>매개 변수</th>
<th>필수</th>
<th>유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ReplicaFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>복제를 시작할 컴퓨터의 FQDN(정규화된 도메인 이름)입니다(예: -ReplicaFqdn &quot;atl-cs-001.litwareinc.com&quot;).</p>
<p>이 매개 변수를 포함하지 않으면 모든 Lync Server 컴퓨터를 대상으로 복제가 시작됩니다.</p>
<p></p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Invoke-CsManagementStoreReplication** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Invoke-CsManagementStoreReplication** cmdlet은 어떠한 개체도 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Get-CsManagementStoreReplicationStatus](get-csmanagementstorereplicationstatus.md)

