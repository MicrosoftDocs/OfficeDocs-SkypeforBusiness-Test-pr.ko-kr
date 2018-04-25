---
title: Grant-CsVoicePolicy
TOCTitle: Grant-CsVoicePolicy
ms:assetid: c8aa8d0f-6fb4-43f7-82b0-38d4da2d5611
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398828(v=OCS.15)
ms:contentKeyID: 49305009
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Grant-CsVoicePolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

음성 정책을 하나 이상의 사용자나 그룹에 할당합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Grant-CsVoicePolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 ID가 VoicePolicyRedmond인 음성 정책을 표시 이름이 Ken Myer인 사용자에게 할당합니다.

    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName VoicePolicyRedmond

## 예제 2

이 예제에서는 ID가 VoicePolicyRedmond인 음성 정책을 Finance OU: OU=Finance,OU=NorthAmerica,DC=litwareinc,DC=com에 있는 모든 사용자에게 할당합니다. 명령의 첫 번째 부분은 **Get-CsUser** cmdlet을 호출하여 Lync Server 또는 Office Communications Server에 대해 활성화된 모든 사용자를 지정한 OU에서 검색합니다. 이 사용자 컬렉션은 각 사용자에게 VoicePolicyRedmond 정책을 할당하는 **Grant-CsVoicePolicy** cmdlet에 파이프됩니다.

    Get-CsUser -OU "ou=Finance,ou=North America,dc=litwareinc,dc=com" | Grant-CsVoicePolicy -PolicyName VoicePolicyRedmond

## 자세한 정보

이 cmdlet은 기존 사용자별 음성 정책을 사용자에게 할당합니다. 음성 정책은 동시 벨 울림(누군가가 사무실 전화에 전화를 걸 때마다 또 다른 전화에서 벨이 울리는 기능) 및 착신 전환과 같은 Enterprise Voice 관련 기능을 관리하는 데 사용됩니다. 이 cmdlet을 사용하여 특정 사용자에 대해 이러한 기능을 활성화 및 비활성화하는 설정을 할당합니다.

사용자별 음성 정책이 사용자에게 부여되었는지 여부를 확인하려면 Get-CsUser "\<user name\>" | Select-Object VoicePolicy 형식의 명령을 호출합니다. 예를 들면 다음과 같습니다.

Get-CsUser "Ken Myer" | Select-Object VoicePolicy

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Grant-CsVoicePolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Grant-CsVoicePolicy"}

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
<td><p>정책을 할당할 사용자의 ID(고유 식별자)입니다.</p>
<p>사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그인 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어, ID &quot;* Smith&quot;는 성이 Smith인 모든 사용자를 반환합니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
</tr>
<tr class="even">
<td><p><em>PolicyName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>사용자에게 할당할 음성 정책의 이름(Identity)입니다. Identity의 이름 부분만 여기에 포함됩니다. 사용자별 정책 ID는 PolicyName에 포함되지 않아야 하는 접두사 tag:을 포함합니다.</p></td>
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

문자열. 음성 정책을 부여할 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다.

## 반환 형식

PassThru 매개 변수와 함께 사용된 경우 Microsoft.Rtc.Management.ADConnect.Schema.OCSADUserOrAppContact 개체 유형을 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoicePolicy](new-csvoicepolicy.md)  
[Remove-CsVoicePolicy](remove-csvoicepolicy.md)  
[Set-CsVoicePolicy](set-csvoicepolicy.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)  
[Test-CsVoicePolicy](test-csvoicepolicy.md)  
[Get-CsUser](get-csuser.md)

