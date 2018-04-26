---
title: Grant-CsClientVersionPolicy
TOCTitle: Grant-CsClientVersionPolicy
ms:assetid: b94d9473-db5f-4350-a7b4-991d0e26e525
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412903(v=OCS.15)
ms:contentKeyID: 49304836
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Grant-CsClientVersionPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

전역 범위, 사이트 범위, 서비스 범위 또는 사용자별 범위에서 클라이언트 버전 정책을 할당합니다. 클라이언트 버전 정책을 사용하면 Lync Server 시스템에 로그온할 수 있는 클라이언트(예: Microsoft Office Communicator 2007 R2)를 지정할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Grant-CsClientVersionPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 클라이언트 버전 정책 RedmondClientVersionPolicy가 Ken Myer라는 사용자에게 할당됩니다.

    Grant-CsClientVersionPolicy -Identity "Ken Myer" -PolicyName "RedmondClientVersionPolicy"

## 예제 2

예제 2에 표시된 명령은 클라이언트 버전 정책 RedmondClientVersionPolicy를 Redmond 시에서 근무하는 모든 사용자에게 할당합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUser** cmdlet 및 LDAPFilter 매개 변수를 사용하여 해당하는 사용자 계정 컬렉션을 검색합니다. 필터 값 "l=Redmond"는 데이터 검색을 Redmond 시에서 근무하는 사용자로 제한합니다. 여기서 "l"은 소문자 L로서 "locality"의 LDAP 속성 이름입니다. 그러면 이 컬렉션이 **Grant-CsClientVersionPolicy** cmdlet에 파이프되어 지정된 정책을 컬렉션의 각 사용자에게 할당합니다.

    Get-CsUser -LdapFilter "l=Redmond" | Grant-CsClientVersionPolicy -PolicyName "RedmondClientVersionPolicy"

## 예제 3

예제 3에서는 특정 OU(조직 단위)의 모든 사용자에게 클라이언트 버전 정책 RedmondClientVersionPolicy를 할당합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUser** cmdlet 및 OU 매개 변수를 호출합니다. 매개 변수 값은 클라이언트 버전 정책을 할당할 사용자의 OU의 고유 이름을 나타냅니다(ou=Redmond,ou=North America,dc=litwareinc,dc=com). 사용자 계정을 검색한 후에는 컬렉션이 **Grant-CsClientVersionPolicy** cmdlet에 파이프되어 해당 사용자에게 각각 RedmondClientVersionPolicy를 할당합니다.

    Get-CsUser -OU "ou=Redmond,ou=North America,dc=litwareinc,dc=com" | Grant-CsClientVersionPolicy -PolicyName "RedmondClientVersionPolicy"

## 예제 4

예제 4에서는 이전에 음성 정책 RedmondVoicePolicy를 할당했던 모든 사용자에게 클라이언트 버전 정책 RedmondClientVersionPolicy를 할당합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUser** cmdlet 및 Filter 매개 변수를 호출합니다. 필터 값 {VoicePolicy -eq "RedmondVoicePolicy"}는 VoicePolicy 속성이 "RedmondVoicePolicy"와 같은 사용자 계정만 반환하도록 합니다. 그러면 결과 사용자 계정이 **Grant-CsClientVersionPolicy** cmdlet에 파이프되고 클라이언트 버전 정책 RedmondClientVersionPolicy가 할당됩니다.

    Get-CsUser -Filter {VoicePolicy -eq "RedmondVoicePolicy"} | Grant-CsClientVersionPolicy -PolicyName "RedmondClientVersionPolicy"

## 예제 5

예제 5에서는 조직의 모든 사용자에게 이전에 할당된 사용자별 클라이언트 버전 정책을 할당 취소합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUser** cmdlet을 사용하여 Lync Server에 대해 활성화된 조직의 모든 사용자 컬렉션을 반환합니다. 이 컬렉션은 이러한 사용자에게 할당된 사용자별 클라이언트 버전 정책을 제거하는 **Remove-CsClientVersionPolicy** cmdlet에 파이프됩니다. 이 작업을 수행하기 위해 PolicyName의 매개 변수 값을 $null로 설정합니다.

    Get-CsUser | Grant-CsClientVersionPolicy -PolicyName $Null

## 자세한 정보

클라이언트 버전 정책은 클라이언트 버전 규칙 컬렉션을 나타내고, 클라이언트 버전 규칙은 Lync Server에 로그온할 수 있는 클라이언트 응용 프로그램을 지정하는 데 사용됩니다. 사용자가 Lync Server에 로그온하려고 하면 클라이언트 응용 프로그램이 서버에 SIP 헤더를 전송합니다. 이 헤더에는 소프트웨어의 주 버전, 부 버전, 빌드 번호 등 응용 프로그램 자체에 대한 자세한 정보가 포함되어 있습니다. 그런 다음 SIP 헤더에 포함된 버전 정보에서 클라이언트 버전 규칙 컬렉션을 검사하여 특정 응용 프로그램에 적용되는 규칙이 있는지 확인합니다. 이러한 규칙이 있으면 Lync Server에서 해당 규칙에 의해 지정된 작업을 수행합니다. 예를 들어 Lync Server에서 로그온을 허용 또는 차단하거나 로그온을 허용하되 클라이언트 응용 프로그램을 최신 버전으로 자동 업데이트하도록 지정하는 규칙이 있을 수 있습니다(예: Office Communicator 2007 R2를 Lync 2013으로 업데이트).

전역 범위, 사이트 범위, 서비스 범위(등록자 서비스) 또는 사용자별 범위에서 적용할 수 있는 클라이언트 버전 정책을 통해 시스템에 액세스하는 데 사용할 수 있는 클라이언트 응용 프로그램을 유동적으로 결정할 수 있습니다. 예를 들어 Lync Server가 Lync와 동일한 요소 및 기능을 지원하지 않기 때문에 사용자가 Communicator 2007 R2를 사용하여 이러한 이전 버전의 클라이언트 응용 프로그램에 로그온하지 못하게 하려는 경우가 있습니다. 그러나 하드웨어 또는 소프트웨어 충돌로 인해 Lync로 업그레이드할 수 없는 사용자 선택 그룹이 있을 수 있습니다. 이 경우 해당 사용자가 Communicator 2007 R2 내에서 로그온하도록 하는 별도의 규칙과 별도의 클라이언트 버전 정책을 만들 수 있습니다.

**Grant-CsClientVersionPolicy** cmdlet을 사용하면 개별 사용자에게 클라이언트 버전 정책을 할당할 수 있습니다. 사용자별 정책을 만들 때 해당 정책은 누구에게도 자동으로 할당되지 않습니다. **Grant-CsClientVersionPolicy** cmdlet을 호출하여 한 명 또는 여러 명의 사용자에게 명시적으로 정책을 할당할 수 있을 때까지 할당되지 않습니다.

클라이언트 버전 정책은 페더레이션 사용자에게 적용되지 않습니다. 대신 페더레이션 사용자에게는 조직에서 사용되는 클라이언트 버전 정책이 적용됩니다. 예를 들어 페더레이션 사용자가 클라이언트 A를 사용하고, 이 클라이언트가 페더레이션 조직에서 허용된다고 가정해 보겠습니다. 페더레이션 조직에서 클라이언트 A 사용을 허용하는 한 이 사용자는 해당 클라이언트를 사용하여 조직과 통신할 수 있습니다. 이는 클라이언트 버전 정책이 클라이언트 A 사용을 차단하는 경우에도 마찬가지입니다. 조직에서 시행되는 클라이언트 버전 정책은 페더레이션 조직에서 사용되는 클라이언트 버전 정책을 무시하지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Grant-CsClientVersionPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Grant-CsClientVersionPolicy"}

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>정책을 할당할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 참조할 수도 있습니다.</p>
<p>또한 표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 &quot; Smith&quot; 문자열 값으로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PolicyName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>할당할 정책의 &quot;이름&quot;입니다. PolicyName은 간단히 말해 정책 ID에서 정책 범위(&quot;tag:&quot;)를 뺀 것입니다. 예를 들어 ID가 tag:Redmond인 정책의 PolicyName은 Redmond와 같고, ID가 tag:RedmondClientVersionPolicy인 정책의 PolicyName은 RedmondClientVersionPolicy와 같습니다. 사용자에게 이전에 할당한 사용자별 정책을 할당 취소하려면 PolicyName을 null 값($null)으로 설정합니다.</p></td>
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
<td><p>정책을 할당할 때 연결할 도메인 컨트롤러를 지정하는 데 사용됩니다. 이 매개 변수를 포함하지 않으면 cmdlet이 사용 가능한 첫 번째 도메인 컨트롤러를 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 cmdlet이 Windows PowerShell 파이프라인을 통해 사용자 개체를 하나 이상 전달합니다. 기본적으로 <strong>Grant-CsClientVersionPolicy</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
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

문자열 값 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Grant-CsClientVersionPolicy** cmdlet은 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값 입력을 허용합니다. 또한 이 cmdlet은 사용자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

기본적으로 **Grant-CsClientVersionPolicy** cmdlet은 개체 또는 값을 반환하지 않습니다. 그러나 PassThru 매개 변수를 포함할 경우 Microsoft.Rtc.Management.ADConnect.Schema.OCSUserOrAppContact 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClientVersionPolicy](get-csclientversionpolicy.md)  
[New-CsClientVersionPolicy](new-csclientversionpolicy.md)  
[Remove-CsClientVersionPolicy](remove-csclientversionpolicy.md)  
[Set-CsClientVersionPolicy](set-csclientversionpolicy.md)

