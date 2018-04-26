---
title: Get-CsManagementStoreReplicationStatus
TOCTitle: Get-CsManagementStoreReplicationStatus
ms:assetid: ea7162d6-d1e5-4301-b162-38da4e422293
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399052(v=OCS.15)
ms:contentKeyID: 49305413
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsManagementStoreReplicationStatus

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 복제 프로세스에 대한 정보를 반환합니다. 여기에는 Lync Server 컴퓨터에 대한 복제 상태가 최신 상태인지에 대한 정보가 포함됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsManagementStoreReplicationStatus [-ReplicaFqdn <String>] [-CentralManagementStoreStatus <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 매개 변수 없이 **Get-CsManagementStoreReplicationStatus** cmdlet을 호출합니다. 그러면 모든 Lync Server 컴퓨터에 대한 복제 상태(최신 상태든 아니든)가 반환됩니다.

    Get-CsManagementStoreReplicationStatus

## 예제 2

예제 2에서는 복제가 최신 상태가 아닌 모든 컴퓨터 컬렉션을 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsManagementStoreReplicationStatus** cmdlet을 사용하여 모든 서버의 복제 상태가 포함된 컬렉션을 검색합니다. 이 컬렉션은 반환되는 데이터를 UpToDate 속성이 False와 같은 컴퓨터로 제한하는 필터를 적용하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsManagementStoreReplicationStatus | Where-Object {$_.UpToDate -eq $False}

## 예제 3

예제 3에서는 반환되는 데이터를 단일 컴퓨터 atl-cs-001.litwareinc.com/으로 제한합니다.

    Get-CsManagementStoreReplicationStatus -ReplicaFqdn atl-cs-001.litwareinc.com

## 예제 4

예제 4에서는 2010년 8월 11일 오후 8:00 이전에 마지막으로 복제된 컴퓨터에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsManagementStoreReplicationStatus** cmdlet을 호출하여 모든 Lync Server 컴퓨터에 대한 복제 정보를 반환합니다. 이 정보는 LastUpdateCreation 속성이 2010년 8월 11일 오후 08:00(8/11/2010 8:00 P.M.)보다 작은 컴퓨터만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 2010년 8월 11일 오후 8:00 이후에 마지막으로 복제된 컴퓨터에 대한 정보를 반환하려면 다음과 같이 -gt(보다 큼) 연산자를 사용합니다.

Where-Object {$\_.LastUpdateCreation -gt "8/11/2010 8:00 PM"}

이 예제에 지정된 날짜는 날짜-시간 값에 대해 미국 영어 형식을 사용합니다. 날짜는 사용자의 국가 및 언어 옵션과 호환되는 형식을 사용하여 지정해야 합니다.

    Get-CsManagementStoreReplicationStatus | Where-Object {$_.LastUpdateCreation -lt "8/11/2010 8:00 PM"}

## 예제 5

예제 5에 표시된 명령은 CentralManagementStoreStatus 매개 변수를 사용하여 중앙 관리 저장소의 현재 상태에 대한 자세한 정보를 반환합니다. 여기에는 Active Master 및 File Transfer Agent 서비스의 정규화된 도메인 이름 및 이러한 각 서비스에 대해 마지막으로 탐지된 하트비트의 날짜 및 시간이 포함됩니다.

    Get-CsManagementStoreReplicationStatus -CentralManagementStoreStatus

## 자세한 정보

관리자가 Lync Server에서 어떤 부분을 변경하는 경우, 예를 들어 관리자가 새 음성 정책을 만들거나 주소록 서버 구성 설정을 변경하는 경우 해당 변경 내용이 중앙 관리 저장소에 기록됩니다. 그러면 이러한 변경 내용을 Lync Server 서비스 또는 서버 역할을 실행 중인 모든 컴퓨터에 복제해야 합니다.

데이터를 복제하기 위해 중앙 관리 서버에서 실행되는 Master Replicator는 수정된 구성 데이터의 스냅샷을 만들고 이 스냅샷의 복사본을 Lync Server 서비스 또는 서버 역할을 실행 중인 각 컴퓨터에 전송합니다. 이러한 컴퓨터에서는 복제 에이전트가 스냅샷을 수신하고 수정된 데이터를 업로드합니다. 그런 다음 Master Replicator에게 최신 복제 상태를 알리는 메시지를 전송합니다.

**Get-CsManagementStoreReplicationStatus** cmdlet을 사용하면 조직에서 사용하는 모든 Lync Server 컴퓨터의 복제 상태를 확인할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsManagementStoreReplicationStatus** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsManagementStoreReplicationStatus"}

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
<td><p><em>CentralManagementStoreStatus</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>활성 복제본 및 삭제된 복제본 목록과 Active Master 및 File Transfer Agent 서비스의 위치 등 중앙 관리 저장소의 현재 상태에 대한 추가 정보를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ReplicaFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>복제 상태를 확인할 컴퓨터의 FQDN(정규화된 도메인 이름)입니다(예: -ReplicaFqdn &quot;atl-cs-001.litwareinc.com&quot;).</p>
<p>이 매개 변수를 포함하지 않으면 모든 Lync Server 컴퓨터의 복제 상태 정보가 반환됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsManagementStoreReplicationStatus** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

기본적으로 **Get-CsManagementStoreReplicationStatus** cmdlet은 Microsoft.Rtc.Management.Xds.ReplicaState 개체의 인스턴스를 반환합니다. CentralManagementStoreStatus 매개 변수를 사용하면 cmdlet이 Microsoft.Rtc.Management.Xds.CentralManagementStoreStatusResult 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Invoke-CsManagementStoreReplication](invoke-csmanagementstorereplication.md)

