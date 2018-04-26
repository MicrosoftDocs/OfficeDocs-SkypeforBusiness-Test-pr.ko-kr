---
title: Grant-CsPinPolicy
TOCTitle: Grant-CsPinPolicy
ms:assetid: ce5f610b-117b-46b3-ad06-0e93f5b7a4de
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398871(v=OCS.15)
ms:contentKeyID: 49305072
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Grant-CsPinPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자 또는 사용자 그룹에 클라이언트 개인식별번호(PIN) 정책을 할당합니다. PIN 인증을 통해 사용자는 사용자 이름 및 암호 대신 PIN을 제공하여 Lync Server에 액세스할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Grant-CsPinPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 사용자 kenmyer@litwareinc.com에게 RedmondUsersPinPolicy 정책을 할당합니다.

    Grant-CsPinPolicy -Identity "kenmyer@litwareinc.com" -PolicyName RedmondUsersPinPolicy

## 예제 2

예제 2에서는 사용자 kenmyer@litwareinc.com에게 이전에 할당된 사용자별 PIN 정책을 할당 취소합니다. **Grant-CsPinPolicy** cmdlet을 호출하고 정책 이름을 null 값($Null)으로 설정하면 사용자에게 할당된 모든 사용자별 정책이 제거됩니다.

    Grant-CsPinPolicy -Identity kenmyer@litwareinc.com -PolicyName $Null 

## 예제 3

예제 3에서는 Redmond 시에서 근무하는 모든 사용자에게 RedmondUsersPinPolicy 정책을 할당합니다. 이 작업을 수행하기 위해 먼저 **Get-CsUser** cmdlet이 Redmond에서 근무하는 모든 사용자 컬렉션을 검색합니다. 이때 LdapFilter 매개 변수를 포함하고 필터 값 "l=Redmond"를 사용합니다. LDAP 필터에서 "l"은 소문자 L이며 사용자의 locality(구/군/시)를 나타냅니다. 이 사용자 컬렉션은 각 사용자에게 RedmondUsersPinPolicy 정책을 할당하는 **Grant-CsPinPolicy** cmdlet에 파이프됩니다.

    Get-CsUser -LdapFilter "l=Redmond" | Grant-CsPinPolicy -PolicyName RedmondUsersPinPolicy

## 예제 4

예제 4에서는 사용자별 PIN 정책이 할당되지 않은 모든 사용자에게 RedmondUsersPinPolicy 정책을 할당합니다. PIN 정책이 할당되지 않은 사용자를 확인하려면 Filter 매개 변수와 함께 **Get-CsUser** cmdlet을 호출합니다. 필터 값 {ClientPinPolicy -eq $Null}은 ClientPinPolicy 속성이 null인(즉, 사용자별 PIN 정책이 할당되지 않은) 사용자만 반환합니다. 이 사용자 컬렉션은 컬렉션의 각 사용자에게 RedmondUsersPinPolicy 정책을 할당하는 **Grant-CsPinPolicy** cmdlet에 파이프됩니다.

    Get-CsUser -Filter {PinPolicy -eq $Null} | Grant-CsPinPolicy -PolicyName RedmondUsersPinPolicy

## 자세한 정보

Lync Server를 사용하면 사용자가 전화를 통해 시스템에 연결하거나 PSTN(공중 전화망) 전화 회의에 참가할 수 있습니다. 일반적으로 사용자가 시스템에 로그온하거나 전화 회의에 참가하려면 사용자 이름 또는 암호를 입력해야 하지만 영숫자 키패드가 없는 전화기를 사용하는 경우 사용자 이름 및 암호를 입력하기 어려울 수 있습니다. 따라서 Lync Server는 사용자에게 숫자로만 구성된 PIN을 제공할 수 있도록 지원합니다. PIN을 묻는 메시지가 표시되면 사용자 이름 및 암호 대신 PIN을 입력하여 시스템에 로그온하거나 전화 회의에 참가할 수 있습니다.

Lync Server에서는 PIN 정책을 사용하여 PIN 인증 속성을 관리합니다. 예를 들어 PIN의 최소 길이를 지정하고 반복되는 숫자(예: 11223344와 같은 PIN) 등의 "공통 패턴"을 사용하는 PIN의 허용 여부를 결정할 수 있습니다. PIN 정책은 전역 또는 사이트 범위에서 구성할 수 있습니다. 또한 PIN 정책을 사용자별 범위에서 구성한 다음 사용자 또는 지정된 사용자 집합에 할당할 수 있습니다. 사용자별 정책을 할당하려면 **Grant-CsPinPolicy** cmdlet을 사용해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Grant-CsPinPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Grant-CsPinPolicy"}

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
<td><p>사용자별 PIN 정책을 할당할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 지정할 수도 있습니다.</p>
<p>또한 표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 &quot; Smith&quot; 문자열 값으로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PolicyName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>할당할 정책의 &quot;이름&quot;입니다. PolicyName은 간단히 말해 정책 ID에서 정책 범위(&quot;tag:&quot; 접두사)를 뺀 것입니다. 예를 들어 ID가 tag:Redmond인 정책의 PolicyName은 Redmond와 같고, ID가 tag:RedmondUsersPinPolicy인 정책의 PolicyName은 RedmondUsersPinPolicy와 같습니다. 사용자에게 이전에 할당한 사용자별 정책을 할당 취소하려면 PolicyName을 null 값($Null)으로 설정합니다.</p></td>
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
<td><p>새 정책을 할당할 때 연결할 도메인 컨트롤러의 FQDN(정규화된 도메인 이름)을 지정하는 데 사용됩니다. 이 매개 변수를 지정하지 않으면 <strong>Grant-CsPinPolicy</strong> cmdlet에서 사용 가능한 첫 번째 도메인 컨트롤러에 연결합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>정책을 할당할 사용자를 나타내는 사용자 개체를 파이프라인을 통해 전달하는 데 사용됩니다. 기본적으로 <strong>Grant-CsPinPolicy</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
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

문자열 값 또는 Microsoft.Rtc.Management.UserPinService.PinInfoDetails 개체입니다. **Grant-CsPinPolicy** cmdlet은 사용자 계정의 ID를 나타내는 문자열 값의 파이프라인된 입력을 허용합니다. 이 cmdlet은 또한 사용자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

기본적으로 **Grant-CsPinPolicy** cmdlet은 값 또는 개체를 반환하지 않습니다. 그러나 PassThru 매개 변수를 포함할 경우 Microsoft.Rtc.Management.ADConnect.Schema.OCSUserOrAppContact의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPinPolicy](get-cspinpolicy.md)  
[New-CsPinPolicy](new-cspinpolicy.md)  
[Remove-CsPinPolicy](remove-cspinpolicy.md)  
[Set-CsPinPolicy](set-cspinpolicy.md)

