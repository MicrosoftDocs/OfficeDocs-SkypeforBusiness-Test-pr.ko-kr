---
title: Grant-CsPresencePolicy
TOCTitle: Grant-CsPresencePolicy
ms:assetid: 756c08a7-26b0-4ea8-816b-b33ebcac51aa
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398571(v=OCS.15)
ms:contentKeyID: 49304067
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Grant-CsPresencePolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자 또는 사용자 그룹에 사용자별 현재 상태 정책을 부여합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Grant-CsPresencePolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1의 명령은 한 명의 사용자, 즉 ID가 Ken Myer인 사용자에게 사용자별 현재 상태 정책 RedmondPresencePolicy를 할당합니다.

    Grant-CsPresencePolicy -Identity "Ken Myer" -PolicyName "RedmondPresencePolicy"

## 예제 2

예제 2에서는 Active Directory 도메인 서비스의 Redmond OU에 계정이 있는 모든 사용자에게 현재 상태 정책 RedmondPresencePolicy를 할당합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUser** cmdlet 및 OU 매개 변수를 사용하여 Redmond OU(OU=Redmond,dc=litwareinc,dc=com)에서 찾은 모든 사용자 계정의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 사용자에게 RedmondArchivingPolicy 정책을 할당하는 **Grant-CsPresencePolicy** cmdlet에 파이프됩니다.

    Get-CsUser -OU "OU=Redmond,dc=litwareinc,dc=com" | Grant-CsPresencePolicy -PolicyName "RedmondPresencePolicy"

## 예제 3

예제 3에서는 RedmondPresencePolicy 정책을 Redmond에 위치한 모든 사용자에게 할당합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUser** cmdlet 및 LdapFilter 매개 변수를 사용하여 Redmond에 위치한 모든 사용자의 컬렉션을 반환합니다. 필터 값 "l=Redmond"는 Redmond의 사용자만 반환되도록 합니다. LDAP 쿼리 언어에서 l(소문자 L)은 "locality", 즉 구/군/시의 줄임말입니다. 검색된 컬렉션은 컬렉션의 각 사용자에게 RedmondArchivingPolicy 정책을 할당하는 **Grant-CsPresencePolicy** cmdlet에 파이프됩니다.

    Get-CsUser -LdapFilter "l=Redmond" | Grant-CsPresencePolicy -PolicyName "RedmondPresencePolicy"

## 예제 4

예제 4의 명령은 Redmond에서 근무하는 사용자에게 이전에 할당된 모든 사용자별 정책의 할당을 취소합니다. PolicyName 매개 변수를 null 값($Null)으로 설정하여 **Grant-CsPresencePolicy** cmdlet을 호출하면 이 명령의 영향을 받는 사용자에게 할당된 사용자별 현재 상태 정책이 모두 제거됩니다.

    Get-CsUser -LdapFilter "l=Redmond" | Grant-CsPresencePolicy -PolicyName $Null

## 자세한 정보

현재 상태 정보는 대화 상대가 메신저 대화에 참여할 수 있는지를 알려 주는 매우 유용한 정보입니다. 하지만 이와 동시에 현재 상태 정보와 관련하여 발생하는 비용이 있습니다. 현재 상태 구독 수가 많아질수록 현재 상태 정보를 업데이트하는 데 더 많은 네트워크 대역폭을 할당해야 합니다. 네트워크 대역폭이 문제가 되는 경우 사용자당 허용되는 현재 상태 구독 수를 제한할 수 있습니다.

CsPresencePolicy cmdlet을 사용하면 현재 상태 구독의 중요한 두 가지 요소인 프롬프트 구독자 및 범주 구독을 관리할 수 있습니다. 사용자가 다른 사람의 Lync 대화 상대 목록에 추가되면 기본적으로 이 목록에 추가되었음을 알리는 팝업 메시지가 나타납니다. 팝업을 해제할 때까지 각 알림에서 프롬프트 구독자로 간주합니다. 현재 상태 정책의 MaxPromptedSubscriber 속성을 사용하면 한 사용자에게 허용되는 확인되지 않은 알림 대화 상자의 최대 개수를 지정할 수 있습니다. 최대 개수에 도달하면 일부 대화 상자를 확인할 때까지 새 대화 상대 알림을 받을 수 없습니다.

범주 구독은 예를 들어 일정 데이터를 요청하는 응용 프로그램과 같은 특정 정보 범주에 대한 요청을 나타냅니다. 관리자는 MaxCategorySubscription 속성을 사용하여 사용자별 범주 구독의 수를 제한할 수 있습니다.

Lync Server 버전 이전에는 프롬프트 구독자와 범주 구독을 전역적으로 관리했습니다. 하지만 이제는 **CsPresencePolicy** cmdlet을 사용하여 이러한 현재 상태 구독을 전역 범위, 사이트 범위 또는 사용자별 범위에서 관리할 수 있습니다. 이렇게 하면 대역폭 사용을 제어하는 동시에 사용자가 작업을 수행하는 데 필요한 현재 상태 정보에 액세스하도록 할 수 있습니다.

사용자별 정책을 만드는 경우 이 정책은 자동으로 할당되지 않습니다. 사용자별 현재 상태 정책은 **Grant-CsPresencePolicy** cmdlet을 사용하여 사용자 또는 사용자 그룹에 명시적으로 할당해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Grant-CsPresencePolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Grant-CsPresencePolicy"}

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
<td><p>현재 상태 정책을 할당할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 지정할 수도 있습니다.</p>
<p>또한 표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 ID &quot;* Smith&quot;는 표시 이름이 문자열 값 &quot; Smith&quot;로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PolicyName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>할당할 사용자별 정책의 ID입니다(예: -PolicyName &quot;RedmondPresencePolicy&quot;). PolicyName은 정책의 Identity에서 &quot;tag:&quot; 접두사를 뺀 것입니다. 예를 들어 Identity가 &quot;tag:NorthAmericaPresencePolicy&quot;인 정책의 PolicyName은 &quot;NorthAmericaPresencePolicy&quot;와 같습니다.</p></td>
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
<td><p>정책을 할당할 때 연결할 도메인 컨트롤러의 FQDN(정규화된 도메인 이름)입니다(예: -DomainController atl-dc-001.litwareinc.com).</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Grant-CsPresencePolicy</strong> cmdlet은 정책을 할당할 때 사용 가능한 가장 가까운 도메인 컨트롤러에 연결합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>정책이 할당되는 사용자를 나타내는 파이프라인을 통해 사용자 개체를 전달할 수 있도록 합니다. 기본적으로 <strong>Grant-CsPresencePolicy</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
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

문자열 값 또는 Microsoft.Rtc.Management.WritebleConfig.Policy.Presence.PresencePolicy 개체입니다. **Grant-CsPresencePolicy** cmdlet은 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값 입력을 허용합니다. 또한 이 cmdlet은 사용자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

기본적으로 **Grant-CsPresencePolicy** cmdlet은 개체나 값을 반환하지 않습니다. 그러나 PassThru 매개 변수를 포함할 경우 이 cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSUserOrAppContact의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPresencePolicy](get-cspresencepolicy.md)  
[New-CsPresencePolicy](new-cspresencepolicy.md)  
[Remove-CsPresencePolicy](remove-cspresencepolicy.md)  
[Set-CsPresencePolicy](set-cspresencepolicy.md)

