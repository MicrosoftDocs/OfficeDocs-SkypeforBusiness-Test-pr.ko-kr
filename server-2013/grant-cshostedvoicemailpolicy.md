---
title: Grant-CsHostedVoicemailPolicy
TOCTitle: Grant-CsHostedVoicemailPolicy
ms:assetid: ae69358f-1618-4a08-9ec2-225ded3f301f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412829(v=OCS.15)
ms:contentKeyID: 49304715
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Grant-CsHostedVoicemailPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자별 범위에서 호스트된 음성 메일 정책을 할당합니다. 사용자별 범위를 사용하면 개별 사용자 또는 그룹에 정책을 할당할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Grant-CsHostedVoicemailPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 ID가 ExRedmond인 호스트된 음성 메일 정책을 표시 이름이 Ken Myer인 사용자에게 할당합니다.

    Grant-CsHostedVoicemailPolicy -Identity "Ken Myer" -PolicyName ExRedmond

## 예제 2

이 예제에서는 Finance OU(조직 구성 단위)의 모든 사용자에게 ID가 ExRedmond인 호스트된 음성 메일 정책을 할당합니다(OU=Finance,OU=NorthAmerica,DC=litwareinc,DC=com). 명령의 첫 번째 부분은 **Get-CsUser** cmdlet을 호출하여 지정된 OU에서 Lync Server 또는 Office Communications Server를 사용하도록 설정된 모든 사용자를 검색합니다. 이 사용자 컬렉션은 각 사용자에게 ExRedmond 정책을 할당하는 **Grant-CsHostedVoicemailPolicy** cmdlet에 파이프됩니다.

    Get-CsUser -OU "ou=Finance,ou=North America,dc=litwareinc,dc=com" | Grant-CsHostedVoicemailPolicy -PolicyName ExRedmond

## 자세한 정보

이 cmdlet은 기존의 사용자별 호스트된 음성 메일 정책을 사용자에게 할당합니다. 호스트된 음성 메일 정책은 응답하지 않는 통화를 호스트된 Exchange 통합 메시징(UM) 서비스로 경로 지정하는 방법을 지정합니다.

사용자별 호스트된 음성 메일 정책이 사용자에게 부여되었는지 확인하려면 Get-CsUser "\<user name\>" | Select-Object HostedVoicemailPolicy 형식의 명령을 호출합니다. 예를 들면 다음과 같습니다.

Get-CsUser "Ken Myer" | Select-Object HostedVoicemailPolicy

대상이 포함되지 않은 호스트된 음성 메일 정책을 사용자에게 할당한 경우에는 호스트된 음성 메일에 대해 해당 사용자를 활성화할 수 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Grant-CsHostedVoicemailPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Grant-CsHostedVoicemailPolicy"}

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
<td><p>호스트된 음성 메일 정책을 할당할 사용자의 ID(고유 식별자)입니다.</p>
<p>사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어, ID &quot;* Smith&quot;는 성이 Smith인 모든 사용자를 반환합니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
</tr>
<tr class="even">
<td><p><em>PolicyName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>사용자에게 할당할 호스트된 음성 메일 정책의 이름(ID)입니다. Identity의 이름 부분만 여기에 포함됩니다. 사용자별 호스트된 음성 메일 정책 ID는 PolicyName에 포함되지 않아야 하는 접두사 tag:을 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인 컨트롤러를 지정하는 데 사용됩니다. 도메인 컨트롤러가 지정되지 않은 경우 사용 가능한 첫 번째 도메인 컨트롤러가 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령 결과를 반환합니다. 기본적으로 이 cmdlet에서는 출력을 생성하지 않습니다.</p></td>
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

문자열. 호스트된 음성 메일 정책을 할당할 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다.

## 반환 형식

PassThru 매개 변수와 함께 사용된 경우 Microsoft.Rtc.Management.ADConnect.Schema.OCSADUserOrAppContact 개체 유형을 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsHostedVoicemailPolicy](new-cshostedvoicemailpolicy.md)  
[Remove-CsHostedVoicemailPolicy](remove-cshostedvoicemailpolicy.md)  
[Set-CsHostedVoicemailPolicy](set-cshostedvoicemailpolicy.md)  
[Get-CsHostedVoicemailPolicy](get-cshostedvoicemailpolicy.md)  
[Get-CsUser](get-csuser.md)

