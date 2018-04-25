---
title: Debug-CsInterPoolReplication
TOCTitle: Debug-CsInterPoolReplication
ms:assetid: 945bfd1c-1759-4869-9316-b3260fcc633d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ619185(v=OCS.15)
ms:contentKeyID: 49304416
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Debug-CsInterPoolReplication

 

_**마지막으로 수정된 항목:** 2015-03-09_

등록자 풀과 할당된 해당 백업 풀 간에 복제가 제대로 이루어지는지 확인합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Debug-CsInterPoolReplication -PoolFqdn <Fqdn> [-BackupModule <All | CentralMgmt | PresenceFocus | DataConf>] [-Force <SwitchParameter>]

## 예제

## 예제 1

예제 1의 명령은 풀 atl-cs-001.litwareinc.com과 이전에 할당된 해당 백업 풀 간의 전체 복제 상태를 확인합니다.

    Debug-CsInterPoolReplication -PoolFqdn "atl-cs-001.litwareinc.com"

## 예제 2

예제 2에서는 풀 pool atl-cs-001.litwareinc.com과 이전에 할당된 해당 백업 풀 간 회의 데이터 복제만 확인합니다.

    Debug-CsInterPoolReplication -PoolFqdn "atl-cs-001.litwareinc.com" -BackupModule DataConf

## 자세한 정보

Lync Server 2013에서는 각 등록자 풀을 백업 풀과 연결할 수 있습니다. 백업 풀에는 기본 풀에 저장되어 있는 모든 데이터의 복사본이 유지됩니다. 기본 풀을 사용할 수 없게 되면 "장애 조치"에 의해 기본 풀 사용자가 백업 풀로 자동으로 이동합니다. 이를 통해 기본 풀 사용자는 홈 풀을 사용할 수 없게 된 경우에도 Lync Server를 계속 사용할 수 있습니다. Debug-CsInterPoolReplication cmdlet을 사용하여 기본 풀 및 해당 백업 풀의 데이터 저장소를 비교하여 두 풀 간의 복제가 올바로 이루어졌는지 확인합니다.

테스트할 풀에 백업 풀이 할당되어 있지 않으면 이 명령이 실패합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Debug-CsInterPoolReplication"}

**Lync Server 제어판:** Debug-CsInterPoolReplication cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>테스트할 기본 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>BackupModule</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Hadr.BackupService.BackupModules</p></td>
<td><p>관리자가 확인할 데이터 저장소를 지정합니다. 허용되는 값은 다음과 같습니다.</p>
<p>* All</p>
<p>* CentralMgmt</p>
<p>* PresenceFocus</p>
<p>* DataConf</p>
<p>기본 값은 All입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. Debug-CsInterPoolReplication은 파이프라인된 데이터를 허용하지 않습니다.

## 반환 형식

문자열 값

