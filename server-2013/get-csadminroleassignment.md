---
title: Get-CsAdminRoleAssignment
TOCTitle: Get-CsAdminRoleAssignment
ms:assetid: 61374f9b-e85a-4866-91f2-037a862ba0d6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398434(v=OCS.15)
ms:contentKeyID: 49303802
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAdminRoleAssignment

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자에게 할당된 RBAC(역할 기반 액세스 제어) 역할을 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsAdminRoleAssignment -Identity <String> [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 사용자 kenmyer에게 할당된 모든 RBAC 역할을 반환합니다.

    Get-CsAdminRoleAssignment -Identity "kenmyer"

## 예제 2

예제 2에서는 Lync Server를 사용하도록 설정된 모든 사용자의 RBAC 역할을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsUser** cmdlet을 호출합니다. 이는 Lync Server 또는 Office Communications Server를 사용할 수 있는 모든 사용자의 컬렉션을 반환합니다. 이 데이터는 **ForEach-Object** cmdlet에 파이프됩니다. 여기서 컬렉션의 각 사용자 계정을 순환하고 1) 사용자의 표시 이름을 화면에 반향 출력하고 2) **Get-CsAdminRoleAssignment** cmdlet을 사용하여 RBAC 역할을 반환합니다. **Get-CsAdminRoleAssignment** cmdlet은 파이프라인 데이터를 직접 받지 않으므로 사용자 계정 정보를 **ForEach-Object** cmdlet에 파이프해야 합니다.

    Get-CsUser | ForEach-Object {$_.DisplayName; Get-CsAdminRoleAssignment -Identity $_.SamAccountName}

## 자세한 정보

RBAC(역할 기반 액세스 제어)를 사용하면 관리자가 Lync Server의 특정 관리 작업에 대한 제어를 위임할 수 있습니다. 예를 들어 조직의 지원 센터에 모든 관리자 권한을 부여하는 대신, 사용자 계정만 관리할 권한, Enterprise Voice 구성 요소만 관리할 권한, 보관 및 보관 서버만 관리할 권한 등의 특정 권한을 이러한 직원에게 부여할 수 있습니다. 또한 이러한 권리의 범위를 제한할 수도 있습니다. 예를 들어 Redmond 사이트 내에서만 Enterprise Voice를 관리할 수 있는 권리를 부여하거나 Finance OU(조직 구성 단위)에 있는 사용자 계정만 관리할 수 있는 권리를 부여할 수 있습니다.

**Get-CsAdminRoleAssignment** cmdlet을 사용하면 사용자에게 할당된 RBAC 역할 목록을 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsAdminRoleAssignment** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsAdminRoleAssignment"}

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>RBAC 역할을 반환할 사용자의 SamAccountName입니다. 다음과 유사한 명령을 사용하여 사용자의 SamAccountName을 검색할 수 있습니다.</p>
<p>Get-CsUser &quot;Ken Myer&quot; | Select-Object SamAccountName</p>
<p>사용자 ID를 지정할 때는 SamAccountName을 사용해야 합니다. Active Directory 표시 이름이나 사용자의 SIP 주소와 같이 ID를 지정할 때 일반적으로 사용되는 다른 값은 <strong>Get-CsAdminRoleAssignment</strong>에 사용할 수 없습니다.</p></td>
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
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 RBAC 역할 할당 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열. **Get-CsAdminRoleAssignment** cmdlet은 사용자의 SamAccountName을 나타내는 파이프라인된 문자열 값을 허용합니다.

## 반환 형식

**Get-CsAdminRoleAssignment** cmdlet은 지정한 사용자가 보유하고 있는 RBAC 역할을 나타내는 문자열 값을 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsAdminRole](get-csadminrole.md)

