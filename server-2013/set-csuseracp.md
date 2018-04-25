---
title: Set-CsUserAcp
TOCTitle: Set-CsUserAcp
ms:assetid: f3138d9f-fa3e-4a3c-aa8e-f6dbdda8a834
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413018(v=OCS.15)
ms:contentKeyID: 49305505
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsUserAcp

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자 또는 사용자 그룹에 새 오디오 회의 공급자를 추가하거나 사용자에게 이미 할당된 기존의 오디오 회의 공급자를 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsUserAcp -Identity <UserIdParameter> -Domain <String> -Name <String> -ParticipantPasscode <String> -TollNumber <String> [-Confirm [<SwitchParameter>]] [-IsDefault <$true | $false>] [-PassThru <SwitchParameter>] [-TollFreeNumbers <String[]>] [-Url <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Set-CsUserAcp** cmdlet을 사용하여 사용자 Ken Myer에게 새 오디오 회의 공급자를 할당합니다. 이 작업을 수행하기 위해 Identity 매개 변수를 사용하여 수정할 사용자 계정을 나타냅니다. 또한 필수 매개 변수인 TollNumber, ParticipantPassCode, Domain 및 Name을 적절한 매개 변수 값과 함께 포함합니다.

    Set-CsUserAcp -Identity "Ken Myer" -TollNumber "14255551298" -ParticipantPassCode 13761 -Domain "fabrikam.com" -Name "Fabrikam ACP"

## 예제 2

예제 2에 표시된 명령은 동일한 오디오 회의 공급자를 Finance 부서에서 근무하는 모든 사용자에게 할당합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUser** cmdlet 및 LdapFilter에 필터 값 "Department=Finance"를 사용하여 Finance 부서에서 근무하는 모든 사용자 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 사용자에게 동일한 오디오 회의 공급자(Fabrikam ACP)를 할당하는 **Set-CsUserAcp** cmdlet에 파이프됩니다.

    Get-CsUser -LdapFilter "Department=Finance" | Set-CsUserAcp -TollNumber "14255551298" -ParticipantPassCode 13761 -Domain "fabrikam.com" -Name "Fabrikam ACP"

## 예제 3

예제 3에서는 사용자 Ken Myer에게 Fabrikam ACP 오디오 회의 공급자를 할당합니다. TollNumber, ParticipantPassCode, Domain 및 Name을 지정하는 것 외에 이 명령은 무료 전화 번호 쌍도 포함합니다. 이러한 두 값을 할당하기 위해 TollFreeNumbers 매개 변수를 포함하고 그 뒤에 쉼표로 구분된 두 전화 번호를 지정합니다.

    Set-CsUserAcp -Identity "Ken Myer" -TollNumber "14255551298" -ParticipantPassCode 13761 -Domain "fabrikam.com" -Name "Fabrikam ACP" -TollFreeNumbers "18005551010", "18005551020"

## 자세한 정보

오디오 회의 공급자는 조직에 회의 서비스를 제공하는 타회사입니다. 특히, 외부에 있거나 회사 네트워크 또는 인터넷에 연결되지 않은 사용자는 오디오 회의 공급자를 통해 회의 또는 모임의 오디오 부분에 참여할 수 있습니다. 오디오 회의 공급자는 실시간 번역, 기록 및 회의별 실시간 운영자 지원과 같은 최고의 서비스를 제공합니다.

Lync Server는 오디오 회의 공급자와의 완전한 통합을 허용하지 않습니다. **CsUserAcp** cmdlet을 통해 관리자는 전화 번호 및 암호를 설정하고, 사용자가 모임을 예약할 때마다 오디오 회의 공급자 통합에 사용할 수 있는 기타 정보를 구성할 수 있습니다. 그러나 이러한 cmdlet은 온-프레미스 버전의 Lync Server용으로 고안된 것이 아니고 Lync Online에서만 사용하도록 만들어진 것이므로 속성 값 할당 외에 추가 오디오 회의 공급자 통합이 제공되지 않습니다.

**Set-CsUserAcp** cmdlet을 사용하여 오디오 회의 공급자를 사용자 계정에 할당할 수 있습니다. 사용자에게 여러 오디오 회의 공급자를 할당할 수 있습니다. **Set-CsUserAcp** cmdlet은 기존의 오디오 회의 공급자 속성을 수정하는 데도 사용할 수 있습니다. **Set-CsUserAcp** cmdlet을 호출하면 이 cmdlet이 호출에 포함된 매개 변수 정보를 사용하여 사용자에게 할당된 기존의 오디오 회의 공급자를 확인합니다. 일치하는 항목이 발견되면 기존의 공급자가 수정됩니다. 예를 들어 다음과 같은 명령을 실행하는 경우를 가정해 보겠습니다.

Set-CsUserAcp –Identity "Ken Myer" –TollNumber "15554251298" –ParticipantPassCode 13761 –Domain "fabrikam.com" –Name "Fabrikam ACP"

또한 Ken Myer에게는 명령에 지정된 것과 동일한 TollNumber 및 Domain을 가진 Fabrikam ACP라는 오디오 회의 공급자가 이미 할당되어 있습니다. 즉, ParticipantPassCode만 다릅니다. 이 경우 **Set-CsUserAcp** cmdlet은 기존의 Fabrikam ACP 공급자를 수정합니다. 일치하는 항목이 발견되지 않으면 새 공급자가 Ken Myer의 사용자 계정에 추가됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsUserAcp** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsUserAcp"}

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
<td><p><em>Domain</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>오디오 회의 공급자의 도메인 이름입니다 (예: -Domain &quot;fabrikam.com&quot;).</p>
<p>도메인 이름은 오디오 회의 공급자가 제공합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>수정할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 도메인 서비스 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 참조할 수도 있습니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 문자열 값 &quot; Smith&quot;로 끝나는 모든 사용자를 반환합니다.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>오디오 회의 공급자의 이름입니다 (예: -Name &quot;Fabrikam Conference Services&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>ParticipantPasscode</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>오디오 회의 공급자를 통해 회의에 연결할 때 필요한 암호입니다(예: -PassCode &quot;0712&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>TollNumber</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>오디오 회의에 사용되는 유료 전화 번호입니다 (예: -TollNumber &quot;14255551298&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>IsDefault</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자의 기본 오디오 회의 공급자인지 여부를 지정합니다. 각 사용자는 기본 공급자를 하나만 가질 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>계정 속성이 구성되는 사용자를 나타내는 개체를 파이프라인을 통해 전달할 수 있습니다. 기본적으로 <strong>Set-CsUserAcp</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않으므로 이러한 경우 PassThru 매개 변수가 필요합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TollFreeNumbers</em></p></td>
<td><p>선택</p></td>
<td><p>System.String[]</p></td>
<td><p>오디오 회의에 사용되는 무료 전화 번호 컬렉션입니다 (예: -TollFreeNumbers &quot;18005551298&quot;). 여러 개의 무료 전화 번호를 추가하려면 각각의 번호를 쉼표를 사용하여 구분합니다(예: -TollFreeNumber &quot;18005551298&quot;, &quot;18005559876&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Url</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>오디오 회의 공급자의 웹 URL입니다(예: -Url &quot;http://acp.fabrikam.com&quot;). 웹 URL을 통해 오디오 회의 공급자는 추가 전화 접속 전화 번호 및 오디오 회의 공급자가 제공하는 서비스 관련 정보가 포함된 웹 페이지에 사용자를 연결할 수 있습니다.</p></td>
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

문자열 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Set-CsUserAcp** cmdlet은 Lync Server를 사용하도록 설정된 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다. 또한 Active Directory 사용자 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음.

## 참고 항목

#### 기타 리소스

[Get-CsUserAcp](get-csuseracp.md)  
[Remove-CsUserAcp](remove-csuseracp.md)

