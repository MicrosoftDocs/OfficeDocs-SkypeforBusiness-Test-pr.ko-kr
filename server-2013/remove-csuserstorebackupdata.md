---
title: Remove-CsUserStoreBackupData
TOCTitle: Remove-CsUserStoreBackupData
ms:assetid: 71c8e8ee-61c7-4737-bdac-8cfc80bac126
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205003(v=OCS.15)
ms:contentKeyID: 49304001
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsUserStoreBackupData

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 사용자 저장소에서 오래된 정보를 제거합니다. "오래된 정보"란 등록자 풀에서 지정된 사용자 저장소와 더 이상 쌍으로 연결되지 않는 사용자 데이터를 의미합니다. 예를 들어 이전에는 풀 A와 B가 쌍이었는데 지금은 해당 연결이 변경되어 풀 A와 C가 쌍으로 연결되어 있다고 가정할 때, 풀 A에 대해 Remove-CsUserStoreBackupData cmdlet을 실행하면 풀 B의 사용자에 대한 정보가 제거됩니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsUserStoreBackupData -PoolFqdn <Fqdn> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-cs-001.litwareinc.com 풀 및 이 풀에 연결된 백업 풀에 의해 저장된 오래된 사용자 저장소 정보를 제거합니다.

    Remove-CsUserStoreBackupData -PoolFqdn "atl-cs-001.litwareinc.com"

## 자세한 정보

Lync Server 2013에서는 한 쌍의 풀을 연결할 수 있습니다. 이렇게 하면 각 풀에서는 두 개의 사용자 정보 집합, 즉 원래 풀에 있는 사용자에 대한 정보와 연결된 풀에 있는 사용자에 대한 정보가 유지됩니다. 두 사용자 정보 집합을 모두 유지하면 풀 A를 장애 조치(failover)해야 하는 경우 풀 B가 풀 A의 사용자를 등록하여 서비스를 제공할 수 있습니다.

나중에 이 두 풀 간의 연결을 변경해도 "추가" 사용자 데이터는 두 풀에서 자동으로 삭제되지 않습니다. 예를 들어 풀 A에는 풀 B의 사용자 데이터가 계속 저장되어 있습니다. 그러나 이 데이터는 더 이상 업데이트 및 복제되지 않습니다. **Remove-CsUserStoreBackupData** cmdlet을 사용하면 풀 A에서 더 이상 필요하지 않은 풀 B의 데이터를 삭제할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsUserStoreBackupData"}

**Lync Server 제어판:** **Remove-CsUserStoreBackupData** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>PoolFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>&quot;오래된&quot; 사용자 정보를 제거할 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>–PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>실제로 명령을 수행하지는 않고 명령을 실행했을 때 발생할 결과에 대해 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Remove-CsUserStoreBackupData** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음

## 참고 항목

#### 기타 리소스

[Get-CsBackupServiceStatus](get-csbackupservicestatus.md)

