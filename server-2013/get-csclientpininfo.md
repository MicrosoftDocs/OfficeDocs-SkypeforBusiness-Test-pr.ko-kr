---
title: Get-CsClientPinInfo
TOCTitle: Get-CsClientPinInfo
ms:assetid: 45feaa2c-f284-4374-a8a6-d3ff3c87d660
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425947(v=OCS.15)
ms:contentKeyID: 49303504
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsClientPinInfo

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자에게 할당된 개인식별번호(PIN) 정보를 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsClientPinInfo -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Lync Server를 사용할 수 있도록 설정된 모든 사용자에 대한 PIN 정보를 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsUser** cmdlet을 호출하여 Lync Server를 사용할 수 있도록 설정된 모든 사용자를 가져옵니다. 이 컬렉션은 컬렉션의 각 사용자에 대한 PIN 정보를 표시하는 **Get-CsClientPinInfo** cmdlet에 파이프됩니다.

    Get-CsUser | Get-CsClientPinInfo

## 예제 2

예제 2에서는 **Get-CsClientPinInfo** cmdlet을 사용하여 Identity가 litwareinc\\kenmyer인 단일 사용자에 대한 PIN 정보를 표시합니다.

    Get-CsClientPinInfo -Identity "litwareinc\kenmyer"

## 예제 3

예제 3에서는 Finance OU(조직 구성 단위)에 계정이 있는 모든 사용자에 대한 PIN 정보를 반환합니다. 이 작업을 수행하기 위해 **Get-CsUser** cmdlet 및 OU 매개 변수를 사용하여 Finance OU의 모든 사용자 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 사용자에 대한 PIN 정보를 표시하는 **Get-CsClientPinInfo** cmdlet에 파이프됩니다.

    Get-CsUser -OU "OU=Finance,DC=litwareinc,DC=com" | Get-CsClientPinInfo

## 예제 4

예제 4에 표시된 명령은 조직의 모든 관리자에 대한 PIN 정보를 표시합니다. 모든 관리자 컬렉션을 검색하기 위해 **Get-CsUser** cmdlet 및 LDAPFilter 매개 변수를 사용합니다. "Title=Manager" 필터는 직함이 "Manager"인 사용자만 반환되도록 컬렉션을 제한합니다. 그런 다음 **Get-CsClientPinInfo** cmdlet을 사용하여 각 사용자에 대한 PIN 정보를 표시합니다.

    Get-CsUser -LdapFilter "Title=Manager" | Get-CsClientPinInfo

## 자세한 정보

Lync Server를 사용하면 사용자가 전화를 통해 시스템에 연결하거나 PSTN(공중 전화망) 전화 회의에 참가할 수 있습니다. 일반적으로 사용자가 시스템에 로그온하거나 전화 회의에 참가하려면 사용자 이름 또는 암호를 입력해야 합니다. 그러나 영숫자 키패드가 없는 전화기를 사용하는 경우에는 사용자 이름 및 암호를 입력하기 어려울 수 있습니다. 따라서 Lync Server는 사용자에게 숫자로만 구성된 PIN을 제공할 수 있도록 지원합니다. PIN을 묻는 메시지가 표시되면 사용자 이름 및 암호 대신 PIN을 입력하여 시스템에 로그온하거나 전화 회의에 참가할 수 있습니다.

관리자는 **Get-CsClientPinInfo** cmdlet을 실행하여 사용자 또는 사용자 그룹의 PIN 설정을 검색할 수 있습니다. 관리자가 사용자에게 할당된 PIN을 검색할 수는 없습니다. 사용자가 PIN을 잊어버린 경우에는 관리자가 새 PIN을 할당하거나 사용자가 전화 접속 회의 웹 페이지에서 새 PIN을 받을 때까지 PIN 인증을 사용하여 시스템에 액세스할 수 없습니다.

Lync Server Standard Edition을 설치한 경우에는 기본적으로 SQL Server Express에 대한 방화벽 예외가 활성화되지 않습니다. 따라서 Windows PowerShell의 원격 인스턴스에서 **Get-CsClientPinInfo** cmdlet을 실행할 수 없습니다. 이는 명령이 방화벽을 통과하여 SQL Server Express 데이터베이스에 액세스할 수 없기 때문입니다. 그러나 Standard Edition 서버에서 로컬로 cmdlet을 실행할 수는 있습니다. **Get-CsClientPinInfo** cmdlet을 Standard Edition 서버에 대해 원격으로 실행하려면 SQL Server Express에 대한 방화벽 예외를 수동으로 활성화해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsClientPinInfo** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsClientPinInfo"}

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
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>PIN을 잠가야 하는 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 계정을 참조할 수도 있습니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 &quot;Smith&quot; 문자열 값으로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열 값 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Get-CsClientPinInfo** cmdlet은 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값 입력을 허용합니다. 또한 이 cmdlet은 사용자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Get-CsClientPinInfo** cmdlet은 Microsoft.Rtc.Management.UserPinService.PinInfoDetails 개체의 인스턴스를 하나 이상 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPinPolicy](get-cspinpolicy.md)  
[Lock-CsClientPin](lock-csclientpin.md)  
[Set-CsClientPin](set-csclientpin.md)  
[Unlock-CsClientPin](unlock-csclientpin.md)

