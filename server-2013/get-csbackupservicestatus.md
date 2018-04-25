---
title: Get-CsBackupServiceStatus
TOCTitle: Get-CsBackupServiceStatus
ms:assetid: 7f56cc81-534c-48e8-9f74-5741d4534a83
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205032(v=OCS.15)
ms:contentKeyID: 49304178
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsBackupServiceStatus

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 풀의 백업 서비스 현재 상태에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsBackupServiceStatus -PoolFqdn <Fqdn> [-Category <UserData | CMS>] [-Force <SwitchParameter>]

## 예제

## 예제 1

위 명령은 atl-cs-001.litwareinc.com 풀에 대한 백업 서비스 상태를 반환합니다.

    Get-CsBackupServiceStatus -PoolFqdn "atl-cs-001.litwareinc.com"

## 자세한 정보

관리자는 **Get-CsBackupServiceStatus** cmdlet을 사용하여 지정된 등록자 풀의 백업 서비스가 구성되었으며 정상적으로 작동하는지를 확인할 수 있습니다. 기본적으로는 RTCUniversalServerAdmins 그룹에 속하는 사용자만 이 cmdlet을 실행하여 풀의 백업 상태를 확인할 수 있습니다. cmdlet 실행 권한을 추가 그룹에 제공하려면 **Set-CsBackupServiceConfiguration** cmdlet을 실행하여 원하는 그룹을 AuthorizedUniversalGroups 속성에 추가합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsBackupServiceStatus"}

**Lync Server 제어판:** **Get-CsBackupServiceStatus** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>백업 서비스 상태를 확인할 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Category</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Hadr.BackupService.BackupCategory</p></td>
<td><p>해당 상태를 확인할 백업의 유형입니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* CMS</p>
<p>* UserData</p>
<p>이 매개 변수를 지정하지 않으면 두 백업 유형을 모두 확인합니다.</p></td>
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

없음. **Get-CsBackupServiceStatus** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

백업 서비스에 대한 정보를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsBackupServiceConfiguration](get-csbackupserviceconfiguration.md)

