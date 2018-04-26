---
title: Get-CsPoolBackupRelationship
TOCTitle: Get-CsPoolBackupRelationship
ms:assetid: 230bbb04-b4cb-410f-8284-00740558655d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204745(v=OCS.15)
ms:contentKeyID: 49303058
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPoolBackupRelationship

 

_**마지막으로 수정된 항목:** 2015-03-09_

비즈니스용 Skype Online 풀과 연결된 백업 풀에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsPoolBackupRelationship -PoolFqdn <Fqdn> [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제에 표시된 명령은 atl-cs-001.litwareinc.com 풀에 할당된 백업 관계에 대한 정보를 반환합니다.

    Get-CsPoolBackupRelationship -PoolFqdn "atl-cs-001.litwareinc.com"

## 자세한 정보

**et-CsPoolBackupRelationship** cmdlet은 등록자 풀과 연결된 백업 풀의 정규화된 도메인 이름을 반환합니다. 이 정보는 읽기 전용 정보이며, Windows PowerShell 명령줄 인터페이스을 사용하여 백업 연결을 만들 수 있도록 하는 해당 **Set-CsPoolBackupRelationship** cmdlet은 없습니다. 대신 Lync Server 토폴로지 작성기를 사용하여 백업 풀을 할당해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPoolBackupRelationship"}

**Lync Server 제어판:**전 **Get-CsPoolBackupRelationship** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>PoolFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>백업 관계를 확인할 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 백업 관계 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsPoolBackupRelationship** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsPoolBackupRelationship** cmdlet은 Microsoft.Rtc.Management.Hadr.BackupService.BackupRelation 개체의 인스턴스를 반환합니다.

