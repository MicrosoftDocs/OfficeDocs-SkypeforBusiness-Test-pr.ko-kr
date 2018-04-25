---
title: Disable-CsUser
TOCTitle: Disable-CsUser
ms:assetid: 92e7e29e-2620-4852-9e4a-2fd3569bb095
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398747(v=OCS.15)
ms:contentKeyID: 49304404
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Disable-CsUser

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 단일 또는 여러 사용자의 Active Directory를 수정합니다. 이로 인해 사용자는 Lync 2013과 같은 Lync Server 클라이언트를 사용할 수 없게 됩니다. **Disable-CsUser** cmdlet은 Lync Server에 관련된 활동만 제한하며 사용자의 Active Directory 계정을 비활성화하거나 제거하지는 않습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Disable-CsUser -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 사용자 Ken Myer에 대해 Lync Server 계정을 비활성화합니다. 이 예제에서는 사용자의 표시 이름을 사용하여 사용자의 ID를 나타냅니다.

    Disable-CsUser -Identity "Ken Myer"

## 예제 2

예제 2에서는 Finance 부서의 모든 사용자가 비활성화된 Lync Server 계정을 가집니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUser** cmdlet 및 LdapFilter 매개 변수를 사용하여 Finance 부서에 있는 모든 사용자의 컬렉션을 반환합니다. 그런 다음, 컬렉션의 각 계정을 비활성화하는 **Disable-CsUser** cmdlet에 해당 컬렉션이 파이프됩니다.

    Get-CsUser -LdapFilter "Department=Finance" | Disable-CsUser

## 예제 3

이 예제에서는 등록자 풀에 현재 할당되지 않은 모든 사용자 계정이 비활성화됩니다. 이 작업을 수행하기 위해 **Get-CsUser** cmdlet이 UnassignedUser 매개 변수와 함께 호출됩니다. 이 매개 변수는 유효한 사용자 계정을 갖고 있지만 등록자 풀에 할당되지 않은 사용자에 대한 데이터만 반환하도록 제한합니다. 그런 다음, 컬렉션의 각 계정을 비활성화하는 Disable-CsUser cmdlet에 해당 컬렉션이 파이프됩니다.

    Get-CsUser -UnassignedUser | Disable-CsUser

## 자세한 정보

**Disable-CsUser** cmdlet은 Lync Server와 관련된 모든 특성 정보를 Active Directory 사용자 계정에서 삭제합니다. 이 경우 사용자는 Lync Server에 로그온할 수 없게 됩니다. **Disable-CsUser** cmdlet을 실행하면 해당 계정에 할당된 사용자별 정책의 ID를 비롯한 모든 Lync Server 관련 특성이 계정에서 제거됩니다. 나중에 **Enable-CsUser** cmdlet을 사용하여 계정을 다시 활성화할 수 있습니다. 그러나 해당 계정과 이전에 연결되었던 모든 Lync Server 관련 정보(예: 정책 할당)는 다시 만들어야 합니다. 사용자만 Lync Server에 로그온할 수 없게 하고 사용자의 계정 정보를 유지하려면 **Set-CsUser** cmdlet을 대신 사용합니다. 자세한 내용은 [Set-CsUser](set-csuser.md) cmdlet 도움말 항목을 참조하십시오.

**Disable-CsUser** cmdlet을 사용하여 계정을 비활성화한 후에는 **Get-CsUser** cmdlet에서 영향을 받는 사용자를 더 이상 반환하지 않습니다. 따라서 사용자에게 더 이상 유효한 Lync Server 계정이 없습니다. 비활성화된 사용자 계정에 대한 정보를 검색하려면 **Get-CsAdUser** cmdlet을 사용합니다.

또한 삭제된 사용자 계정에 속한 사용자 데이터가 백 엔드 데이터베이스에서 제거됩니다. 예를 들어 조직의 연락처 목록에서 사용자가 제거되고 해당 사용자가 예약한 모든 전화 회의가 삭제됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Disable-CsUser** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Disable-CsUser"}

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
<td><p>비활성화할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 또한 Active Directory 고유 이름을 사용하여 사용자 계정을 참조할 수도 있습니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 &quot; Smith&quot; 문자열 값으로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>사용자 계정을 비활성화하기 위해 지정된 도메인 컨트롤러에 연결할 수 있게 합니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-cs-001) 또는 FQDN(정규화된 도메인 이름)(예: atl-cs-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>비활성화되는 사용자 계정을 나타내는 파이프라인을 통해 사용자 개체를 전달할 수 있도록 합니다. 기본적으로 <strong>Disable-CsUser</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
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

문자열 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Disable-CsUser** cmdlet은 Lync Server를 사용하도록 설정된 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다. 또한 Active Directory 사용자 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Disable-CsUser** cmdlet은 값이나 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Enable-CsUser](enable-csuser.md)  
[Get-CsUser](get-csuser.md)

