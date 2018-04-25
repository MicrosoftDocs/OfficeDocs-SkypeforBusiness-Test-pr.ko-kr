---
title: Grant-CsArchivingPolicy
TOCTitle: Grant-CsArchivingPolicy
ms:assetid: 675f5d8d-d8f9-4d19-b11b-75df48b09467
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398475(v=OCS.15)
ms:contentKeyID: 49303888
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Grant-CsArchivingPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자 또는 사용자 집합에 메신저 대화 세션 보관 정책을 할당할 수 있습니다. 이러한 정책은 내부 사용자 간에 발생하는 모든 메신저 대화 세션을 보관하고 내부 사용자와 외부 파트너 간에 발생하는 모든 메신저 대화 세션을 보관하는 기능을 제공합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Grant-CsArchivingPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 표시 이름이 "Ken Myer"인 사용자에게 보관 정책 RedmondArchivingPolicy가 할당됩니다. **Grant-CsArchivingPolicy** cmdlet을 사용할 경우 Identity 속성은 보관 정책의 ID가 아닌 사용자의 ID를 참조합니다. 대신 할당할 정책은 PolicyName 매개 변수를 사용하여 지정합니다. 매개 변수 값은 정책 ID에서 "tag:" 접두사를 뺀 것입니다.

    Grant-CsArchivingPolicy -Identity "Ken Myer" -PolicyName RedmondArchivingPolicy

## 예제 2

예제 2에서는 Redmond OU(조직 구성 단위)에 계정이 있는 모든 사용자에게 보관 정책 RedmondArchivingPolicy가 할당됩니다. 이 작업을 수행하기 위해 **Get-CsUser** cmdlet 및 OU 매개 변수를 사용하여 고유 이름이 "OU=Redmond,dc=litwareinc,dc=com"인 OU에 계정이 있는 모든 사용자 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 사용자에게 RedmondArchivingPolicy 정책을 할당하는 **Grant-CsArchivingPolicy** cmdlet에 파이프됩니다.

    Get-CsUser -OU "OU=Redmond,dc=litwareinc,dc=com" | Grant-CsArchivingPolicy -PolicyName RedmondArchivingPolicy

## 예제 3

예제 3에 표시된 명령은 Redmond에서 근무하는 모든 사용자에게 RedmondArchivingPolicy 정책을 할당합니다. 이 작업을 수행하기 위해 **Get-CsUser** cmdlet을 LDAPFilter 매개 변수와 함께 호출합니다. LDAP 필터 값 "l=Redmond"는 Redmond 시에서 근무하는 모든 사용자의 컬렉션을 반환합니다. LDAP 쿼리 언어에서 l(소문자 L)은 "locality", 즉 구/군/시의 줄임말입니다. 이 컬렉션은 컬렉션의 각 사용자에게 RedmondArchivingPolicy를 할당하는 **Grant-CsArchivingPolicy** cmdlet에 파이프됩니다.

    Get-CsUser -LdapFilter "l=Redmond" | Grant-CsArchivingPolicy -PolicyName RedmondArchivingPolicy

## 예제 4

예제 4에서는 등록자 풀 atl-cs-001.litwareinc.com에 있는 모든 사용자에게 RedmondArchivingPolicy 정책이 할당됩니다. 이 작업을 수행하기 위해 먼저 **Get-CsUser** cmdlet을 사용하여 Lync Server를 사용하도록 설정된 모든 사용자를 반환합니다. 이 컬렉션은 등록자 풀이 atl-cs-001-litwareinc.com과 같은 사용자만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 사용자에게 RedmondArchivingPolicy 정책을 할당하는 **Grant-CsArchivingPolicy** cmdlet에 파이프됩니다.

    Get-CsUser -Filter {RegistrarPool -eq "atl-cs-001.litwareinc.com"} | Grant-CsArchivingPolicy -PolicyName RedmondArchivingPolicy

## 예제 5

예제 5에서는 RedmondArchivingPolicy 정책이 할당된 모든 사용자를 찾은 다음 이러한 각 사용자에게 다른 정책 NorthAmericaArchivingPolicy를 할당합니다. 이 작업을 수행하기 위해 **Get-CsUser** cmdlet을 사용하여 Lync Server를 사용하도록 설정된 모든 사용자의 컬렉션을 반환합니다. Filter 매개 변수 및 필터 값 {ArchivingPolicy -eq "RedmondArchivingPolicy"}는 ArchivingPolicy가 "RedmondArchivingPolicy"와 같은 계정에 대한 데이터만 반환하도록 제한합니다. 그런 다음 필터링된 컬렉션이 컬렉션의 각 사용자에게 NorthAmericaArchivingPolicy 정책을 할당하는 **Grant-CsArchivingPolicy** cmdlet에 파이프됩니다.

    Get-CsUser -Filter {ArchivingPolicy -eq "RedmondArchivingPolicy"} | Grant-CsArchivingPolicy -PolicyName "NorthAmericaArchivingPolicy"

## 예제 6

예제 6은 예제 5의 변형입니다. 그러나 이번에는 이전에 RedmondArchivingPolicy 정책이 할당된 모든 사용자에 대해 이 정책의 할당을 취소합니다. $Null과 같은 PolicyName과 함께 **Grant-CsArchivingPolicy** cmdlet을 호출하면 이전에 할당된 사용자별 정책이 제거됩니다.

    Get-CsUser -Filter {ArchivingPolicy -eq "RedmondArchivingPolicy"} | Grant-CsArchivingPolicy -PolicyName $Null

## 자세한 정보

대부분의 조직에서는 조직의 사용자가 참가하는 모든 메신저 대화 세션을 보관하는 것이 유용하다는 것을 인지하고 있습니다. 다른 조직의 경우 법적으로 메신저 대화 세션을 보관해야 하기도 합니다. Lync Server를 사용하여 메신저 대화 세션을 보관하려면 두 가지 단계를 수행해야 합니다. 먼저 **Set-CsArchivingConfiguration** cmdlet을 사용하여 전역 및/또는 사이트 범위에서 보관을 설정해야 합니다. 이렇게 하면 메신저 대화 세션을 보관할 수 있지만 자동으로 이러한 세션의 보관이 시작되지는 않습니다.

실제로 메신저 대화 세션의 대화 내용을 저장하려면 다음 2단계인 하나 이상의 메신저 대화 세션 보관 정책 만들기를 완료해야 합니다. 이러한 정책은 메신저 대화 세션을 기록할 사용자와 보관할 메신저 대화 세션의 유형(내부 및/또는 외부)을 결정합니다. 내부 메신저 대화 세션은 조직 내에 Active Directory 계정이 있는 인증된 사용자만 참가하는 세션입니다. 반대로, 외부 메신저 대화 세션은 조직 내에 Active Directory 계정을 가지고 있지 않은 인증되지 않은 사용자가 한 명 이상 참가하는 세션입니다. 내부 세션 또는 외부 세션만 보관하거나 내부 및 외부 세션을 모두 보관하도록 선택할 수 있습니다.

보관 정책은 전역 범위 또는 사이트 범위에 할당할 수 있습니다. 또한 이러한 정책을 사용자별 범위에 할당한 다음 특정 사용자나 특정 사용자 집합에 적용할 수도 있습니다. 예를 들어 전역 정책이 내부 메신저 대화 세션만 보관한다고 가정해 보겠습니다. 이 경우 내부 및 외부 세션을 모두 보관하는 두 번째 정책을 만들고 해당 정책을 영업 사원에게만 적용할 수 있습니다. 사용자별 정책은 전역 및 사이트 정책에 우선하기 때문에 영업 직원의 모든 메신저 대화 세션이 보관됩니다. 다른 사용자(즉, 영업 부서에 속하지 않으므로 영업 정책의 영향을 받지 않는 사용자)는 내부 메신저 대화 세션만 보관됩니다.

**Grant-CsArchivingPolicy** cmdlet은 사용자 또는 지정된 사용자 집합에 사용자별 보관 정책을 할당하는 데 사용됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Grant-CsArchivingPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Grant-CsArchivingPolicy"}

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
<td><p>정책을 할당해야 하는 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그인 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 참조할 수도 있습니다.</p>
<p>또한 표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 ID &quot;* Smith&quot;는 표시 이름이 문자열 값 &quot; Smith&quot;로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PolicyName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>할당할 정책의 &quot;이름&quot;입니다. PolicyName은 간단히 말해 정책 ID에서 범위 지정자 &quot;tag:&quot;을 뺀 것입니다. 예를 들어 ID가 tag:Redmond인 정책의 PolicyName은 Redmond와 같고, ID가 tag:RedmondArchivingPolicy인 정책의 PolicyName은 RedmondArchivingPolicy와 같습니다.</p>
<p>사용자에게 할당된 사용자별 정책을 제거하려면 PolicyName을 null 값으로 설정합니다.</p>
<p>-PolicyName $Null</p></td>
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
<td><p>정책을 할당할 때 연결할 도메인 컨트롤러를 지정할 수 있습니다. 이 매개 변수를 포함하지 않으면 cmdlet이 사용 가능한 첫 번째 도메인 컨트롤러를 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 cmdlet이 Windows PowerShell 파이프라인을 통해 사용자 개체를 하나 이상 전달합니다. 기본적으로 <strong>Grant-CsArchivingPolicy</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
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

문자열 값 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Grant-CsArchivingPolicy** cmdlet은 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값 입력을 허용합니다. 또한 이 cmdlet은 사용자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Grant-CsArchivingPolicy** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 사용자 또는 사용자 그룹에 Microsoft.Rtc.Management.WriteableConfig.Policy.IM.ImArchivingPolicy 개체의 인스턴스를 할당합니다. 그러나 PassThru 매개 변수를 포함할 경우 이 cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSUserOrAppContact의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsArchivingPolicy](get-csarchivingpolicy.md)  
[New-CsArchivingPolicy](new-csarchivingpolicy.md)  
[Remove-CsArchivingPolicy](remove-csarchivingpolicy.md)  
[Set-CsArchivingPolicy](set-csarchivingpolicy.md)

