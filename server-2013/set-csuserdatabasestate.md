---
title: Set-CsUserDatabaseState
TOCTitle: Set-CsUserDatabaseState
ms:assetid: c4d8fe5e-ebc1-443b-943d-fc54649e94fd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412973(v=OCS.15)
ms:contentKeyID: 49304972
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsUserDatabaseState

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 Lync Server 사용자 데이터베이스를 사용하거나 사용하지 않도록 설정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsUserDatabaseState -RegistrarPool <Fqdn> <COMMON PARAMETERS>

    Set-CsUserDatabaseState -Identity <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: -Online <$true | $false> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 사용자 데이터베이스 UserDatabase:atl-sql-001.litwareinc.com을 오프라인 상태로 전환합니다. 이 작업을 수행하기 위해 Online 속성을 $False로 설정합니다.

    Set-CsUserDatabaseState -Identity "UserDatabase:atl-sql-001.litwareinc.com" -Online $False

## 예제 2

예제 2에서는 등록자 풀 atl-cs-001.litwareinc.com의 모든 사용자 데이터베이스를 오프라인 상태로 전환합니다.

    Set-CsUserDatabaseState -RegistrarPool atl-cs-001.litwareinc.com -Online $False

## 예제 3

예제 3에서는 현재 오프라인 상태인 모든 사용자 데이터베이스를 찾아서 다시 온라인 상태로 전환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsUserDatabaseState** cmdlet을 호출하여 조직의 모든 사용자 데이터베이스 컬렉션을 반환합니다. 이 컬렉션은 Online 속성이 False와 같은 데이터베이스만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 데이터베이스를 가져와 Online 속성을 True로 설정하는 **ForEach-Object** cmdlet에 파이프됩니다. 오프라인 데이터베이스 컬렉션은 **Set-CsUserDatabaseState** cmdlet 대신 **ForEach-Object** cmdlet에 파이프해야 합니다. Set-CsUserDatabaseState cmdlet은 파이프라인된 정보를 직접 수락할 수 없기 때문입니다.

    Get-CsUserDatabaseState | Where-Object {$_.Online -eq $False} | ForEach-Object {Set-CsUserDatabaseState -Identity $_.Identity -Online $True}

## 자세한 정보

Lync Server는 사용자 데이터베이스(사용자 저장소라고도 함)를 사용하여 Lync Server 사용자의 현재 상태 및 경로 지정 정보를 유지 관리합니다. **Set-CsUserDatabaseState** cmdlet을 사용하면 하나 이상의 사용자 데이터베이스의 상태를 변경할 수 있습니다. 이 cmdlet을 사용하여 데이터베이스를 오프라인 상태로 전환하거나 비활성화된 데이터베이스를 다시 온라인 상태로 만들 수 있습니다.

기본적으로 Lync Server Standard Edition을 설치하면 SQL Server Express에 대한 방화벽 예외가 활성화되지 않습니다. 즉, Windows PowerShell의 원격 인스턴스에서 **Set-CsUserDatabaseState** cmdlet을 실행할 수 없습니다. 명령이 방화벽을 통과하여 SQL Server Express 데이터베이스에 액세스할 수 없기 때문입니다. 그러나 cmdlet을 로컬에서(즉, Standard Edition 서버 자체에서) 실행할 수는 있습니다. 그러나 **Set-CsUserDatabaseState** cmdlet을 원격에서 실행하려면 SQL Server Express에 대한 방화벽 예외를 수동으로 활성화해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsUserDatabaseState** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsUserDatabaseState"}

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
<td><p>온라인 상태를 수정할 사용자 데이터베이스의 고유 식별자입니다 (예: -Identity &quot;UserDatabase:atl-sql-001.litwareinc.com&quot;).</p>
<p>Identity 및 RegistrarPool을 같은 명령에 함께 사용할 수 없으며 이러한 매개 변수에 와일드카드를 사용할 수도 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Online</em></p></td>
<td><p>필수</p></td>
<td><p>System.Boolean</p></td>
<td><p>True($True)로 하면 데이터베이스가 사용 가능한 온라인 상태로 전환되고, False($False)로 설정하면 데이터베이스가 오프라인 상태로 전환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPool</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>온라인 상태를 수정할 사용자 데이터베이스를 호스트하는 등록자 풀의 FQDN(정규화된 도메인 이름)입니다. (예: -RegistrarPool atl-cs-001.litwareinc.com).</p>
<p>-Identity 및 -RegistrarPool을 같은 명령에 함께 사용할 수 없으며 이러한 매개 변수에 와일드카드를 사용할 수도 없습니다.</p></td>
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
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열. **Set-CsUserDatabaseState** cmdlet은 업데이트할 사용자 데이터베이스의 ID를 나타내는 문자열 값을 허용합니다.

## 반환 형식

없음. 대신 **Set-CsUserDatabaseState** cmdlet은 Microsoft.Rtc.Management.Xds.UserStoreState 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUserDatabaseState](get-csuserdatabasestate.md)  
[Update-CsUserDatabase](update-csuserdatabase.md)

