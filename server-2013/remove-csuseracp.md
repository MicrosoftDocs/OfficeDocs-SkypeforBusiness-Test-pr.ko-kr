---
title: Remove-CsUserAcp
TOCTitle: Remove-CsUserAcp
ms:assetid: dec450bb-d523-468d-aee4-07fdc3d567c4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398982(v=OCS.15)
ms:contentKeyID: 49305272
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsUserAcp

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자 또는 사용자 그룹에 할당된 하나 이상의 오디오 회의 공급자를 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsUserAcp -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-Name <String>] [-ParticipantPasscode <String>] [-PassThru <SwitchParameter>] [-TollNumber <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 사용자 Ken Myer에게 할당된 모든 오디오 회의 공급자를 제거합니다.

    Remove-CsUserAcp -Identity "Ken Myer"

## 예제 2

예제 2에서는 Lync Server를 사용하도록 설정된 모든 사용자에게 할당된 모든 오디오 회의 공급자를 제거하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUser** cmdlet을 사용하여 Lync Server를 사용하도록 설정된 모든 사용자 컬렉션을 검색합니다. 이 컬렉션은 컬렉션의 각 사용자에게 할당된 모든 오디오 회의 공급자를 제거하는 **Remove-CsUserAcp** cmdlet에 파이프됩니다.

    Get-CsUser | Remove-CsUserAcp

## 예제 3

예제 3에서는 이름이 "Fabrikam ACP"인 모든 오디오 회의 공급자를 Ken Myer의 사용자 계정에서 제거합니다.

    Remove-CsUserAcp -Identity "Ken Myer" -Name "Fabrikam ACP"

## 예제 4

예제 4에서는 오디오 회의 공급자가 할당된 모든 사용자 계정에서 유료 번호 "14255551298"을 사용하는 오디오 회의 공급자를 제거합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUserAcp** cmdlet을 사용하여 모든 사용자에게 할당된 모든 오디오 회의 공급자에 대한 정보를 반환합니다. 이 정보는 AcpInfo 속성에 전화 번호 "14255551298"이 포함된(-match) 계정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 이 컬렉션의 각 계정에서 해당 오디오 회의 공급자를 제거하는 **Remove-CsUserAcp** cmdlet에 파이프됩니다.

    Get-CsUserAcp | Where-Object {$_.AcpInfo -match "14255551298"} | Remove-CsUserAcp

## 자세한 정보

오디오 회의 공급자는 조직에 회의 서비스를 제공하는 타회사입니다. 특히, 외부에 있거나 회사 네트워크 또는 인터넷에 연결되지 않은 사용자는 오디오 회의 공급자를 통해 회의 또는 모임의 오디오 부분에 참여할 수 있습니다. 오디오 회의 공급자는 실시간 번역, 기록 및 회의별 실시간 운영자 지원과 같은 최고의 서비스를 제공합니다.

Lync Server는 오디오 회의 공급자와의 완전한 통합을 허용하지 않습니다. **CsUserAcp** cmdlet을 통해 관리자는 전화 번호 및 암호를 설정하고, 사용자가 모임을 예약할 때마다 오디오 회의 공급자 통합에 사용할 수 있는 기타 정보를 구성할 수 있습니다. 그러나 이러한 cmdlet은 온-프레미스 버전의 Lync Server용으로 고안된 것이 아니고 원래 Lync Online에서 사용하도록 만들어진 것이므로 속성 값 할당 외에 추가 오디오 회의 공급자 통합이 제공되지 않습니다.

사용자에게 할당된 오디오 회의 공급자는 나중에 **Remove-CsUserAcp** cmdlet을 사용하여 제거할 수 있습니다. 수정할 사용자 계정을 나타내는 Identity 매개 변수 외에 다른 매개 변수 없이 **Remove-CsUserAcp** cmdlet을 호출하면 사용자에게 할당된 모든 오디오 회의 공급자가 제거됩니다. 또는 **Remove-CsUserAcp** cmdlet과 함께 포함된 선택적 매개 변수를 사용하여 사용자 계정에서 선택한 공급자를 제거할 수 있습니다. 예를 들어 다음 명령은 Ken Myer 사용자 계정을 찾아서 Name이 "Fabrikam ACP"와 같은 모든 오디오 회의 공급자를 제거합니다.

Remove-CsUserAcp –Identity "Ken Myer" –Name "Fabrikam ACP"

오디오 회의 공급자를 보다 세분화하여 제거하려면 추가 매개 변수를 포함하면 됩니다. 예를 들어 다음 명령은 Name이 “Fabrikam ACP”이고 TollNumber가 "14255551298"과 같은 오디오 회의 공급자를 제거합니다.

Remove-CsUserAcp –Identity "Ken Myer" –Name "Fabrikam ACP" –TollNumber "14255551298"

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Remove-CsUserAcp** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsUserAcp"}

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
<td><p>오디오 회의 공급자를 제거할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 도메인 서비스 표시 이름(예: Ken Myer)입니다. 사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 참조할 수도 있습니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 ID &quot;* Smith&quot;는 표시 이름이 문자열 값 &quot; Smith&quot;로 끝나는 모든 사용자를 반환합니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>오디오 회의 공급자의 이름입니다 (예: -Name &quot;Fabrikam Conference Services&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>ParticipantPasscode</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>오디오 회의 공급자를 통해 회의에 연결할 때 필요한 암호입니다 (예: -PassCode &quot;0712&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>파이프라인을 통해 오디오 회의 공급자를 제거할 사용자를 나타내는 사용자 개체를 전달하는 데 사용됩니다. 기본적으로 <strong>Remove-CsUserAcp</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TollNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>오디오 회의에 사용되는 유료 전화 번호입니다 (예: -TollNumber &quot;14255551298&quot;).</p></td>
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

문자열 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Remove-CsUserAcp** cmdlet은 Lync Server를 사용하도록 설정된 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다. 또한 Active Directory 사용자 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음.

## 참고 항목

#### 기타 리소스

[Get-CsUserAcp](get-csuseracp.md)  
[Set-CsUserAcp](set-csuseracp.md)

