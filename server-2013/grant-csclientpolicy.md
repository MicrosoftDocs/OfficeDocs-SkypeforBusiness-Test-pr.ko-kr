---
title: Grant-CsClientPolicy
TOCTitle: Grant-CsClientPolicy
ms:assetid: c09d743d-cf2c-4622-b00c-cc815852e4a6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412942(v=OCS.15)
ms:contentKeyID: 49304910
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Grant-CsClientPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자 또는 사용자 그룹에 클라이언트 정책을 할당합니다. 특히 클라이언트 정책은 사용자가 사용할 수 있는 Lync Server 기능을 결정하는 데 도움이 됩니다. 예를 들어 일부 사용자에게는 파일 전송 권한을 부여하고 다른 사용자에 대해서는 이 권한을 거부할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Grant-CsClientPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서 클라이언트 정책 SalesPolicy는 ID가 Ken Myer인 사용자에게 할당됩니다.

    Grant-CsClientPolicy -Identity "Ken Myer" -PolicyName SalesPolicy

## 예제 2

예제 2에서는 판매 부서에 속한 모든 사용자에게 SalesPolicy 클라이언트 정책이 할당됩니다. 명령은 먼저 **Get-CsUser** cmdlet 및 LdapFilter 매개 변수를 사용하여 판매 부서의 구성원인 모든 사용자의 컬렉션을 반환합니다. 그러면 이 사용자 컬렉션이 **Grant-CsClientPolicy** cmdlet에 파이프되어 SalesPolicy 정책을 컬렉션의 각 사용자에게 할당합니다.

    Get-CsUser -LDAPFilter "Department=Sales" | Grant-CsClientPolicy -PolicyName SalesPolicy

## 예제 3

예제 3에서는 다음 두 가지 조건을 만족하는 모든 사용자에게 클라이언트 정책 RedmondAccountingPolicy가 할당됩니다. 1) 사용자는 직책이 회계사여야 하고, 2) Redmond 시에서 근무해야 합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUser** cmdlet 및 LdapFilter 매개 변수를 사용하여 Redmond에서 근무하고 직책이 회계사인 모든 사용자의 컬렉션을 반환합니다. 필터 값 "(&(Title=Accountant)(l=Redmond))"는 반환되는 데이터를 직책이 회계사(Title=Accountant)이고(&) Redmond에서 근무하는(l=Redmond) 사용자로 제한합니다. "l"은 소문자 L이며 사용자의 locality(구/군/시)를 나타냅니다.

그러면 결과 컬렉션이 **Grant-CsClientPolicy** cmdlet에 파이프되어 RedmondAccountingPolicy 정책을 컬렉션의 각 사용자에게 할당합니다.

    Get-CsUser -LDAPFilter "(&(Title=Accountant)(l=Redmond))" | Grant-CsClientPolicy -PolicyName RedmondAccountingPolicy

## 예제 4

예제 4에서는 다음 두 가지 기준 중 하나를 만족하는 모든 사용자에게 AccountingPolicy 정책을 할당합니다. 사용자는 직책이 회계사이거나 선임 회계사여야 합니다. 이 작업을 수행하기 위해 **Get-CsUser** cmdlet 및 LdapFilter 매개 변수를 사용하여 직책이 회계사이거나 선임 회계사인 사용자의 컬렉션을 반환합니다. 필터 값 "(|(Title=Accountant)(Title=Senior Accountant))"는 반환되는 데이터를 직책이 회계사(Title=Accountant)인 사용자(|) 또는 선임 회계사(Title=Senior Accountant)인 사용자로 제한합니다. 이 필터링된 컬렉션은 **Grant-CsClientPolicy** cmdlet에 파이프되어 클라이언트 정책 AccountingPolicy를 컬렉션의 각 사용자에게 할당합니다.

    Get-CsUser -LdapFilter "(|(Title=Accountant)(Title=Senior Accountant))" | Grant-CsClientPolicy -PolicyName AccountingPolicy

## 예제 5

예제 5에서는 등록자 풀 atl-cs-001.litwareinc.com에 계정이 있는 모든 사용자에게 클라이언트 정책 AtlantaBranchPolicy를 할당합니다. 이 작업을 수행하기 위해 먼저 **Get-CsUser** cmdlet을 호출하여 해당 사용자 계정을 반환합니다. Filter 매개 변수 및 필터 값 {RegistrarPool -eq "atl-cs-001.litwareinc.com"}를 사용하면 등록자 풀 atl-cs-001.litwareinc.com을 홈으로 사용하는 사용자 계정만 반환됩니다. 이 컬렉션은 클라이언트 정책 AtlantaBranchPolicy를 각 사용자에게 할당하는 **Grant-CsClientPolicy** cmdlet에 파이프됩니다.

    Get-CsUser -Filter {RegistrarPool -eq "atl-cs-001.litwareinc.com"} | Grant-CsClientPolicy -PolicyName AtlantaBranchPolicy

## 자세한 정보

Lync Server에서는 이전 버전의 제품에서 사용된 그룹 정책 설정 대신 클라이언트 정책을 사용합니다. Microsoft Office Communicator 2007 및 Microsoft Office Communicator 2007 R2에서는 Communicator 및 기타 클라이언트로 사용자가 수행할 수 있는 작업을 결정할 때 그룹 정책을 사용했습니다. 예를 들어 사용자가 메신저 대화 세션의 대화 내용을 저장할 수 있는지 여부, Microsoft Outlook의 정보를 상태 정보로 통합할지 여부, 사용자가 메신저 대화에 이모티콘이나 서식 있는 텍스트를 포함할 수 있는지 여부 등을 결정하는 그룹 정책 설정이 있었습니다.

그룹 정책은 유용하지만 Lync Server에 적용할 때 몇 가지 기술적인 제한이 있습니다. 우선, 그룹 정책은 도메인별 또는 OU(조직 구성 단위)별로 적용하도록 설계되었기 때문에 보다 선별적인 사용자 그룹(예: 특정 부서에서 근무하는 모든 사용자나 특정 직책의 모든 사용자)에 적용하기 어렵습니다. 또한 그룹 정책은 도메인에 로그온하거나 컴퓨터를 사용하여 로그온한 사용자에게만 적용됩니다. 인터넷을 통해 Lync Server에 액세스하거나 휴대폰을 사용하여 시스템에 액세스한 사용자에게는 적용되지 않습니다. 따라서 로그온하는 데 사용한 장치 및 로그온한 위치에 따라 동일한 사용자에게 다른 환경이 제공될 수 있습니다.

이러한 불일치를 해결하기 위해 Lync Server에서는 그룹 정책 대신 클라이언트 정책을 사용합니다. 클라이언트 정책은 로그온한 위치 및 로그온하는 데 사용한 장치 유형에 관계없이 사용자가 시스템에 액세스할 때마다 적용됩니다. 또한 다른 Lync Server 정책과 마찬가지로 클라이언트 정책을 언제든지 선택한 사용자 그룹으로 지정할 수 있을 뿐만 아니라 단일 사용자에게 할당되는 사용자 지정 정책을 만들 수도 있습니다.

클라이언트 정책은 전역, 사이트 및 사용자별 범위에서 구성할 수 있습니다. 사용자에게 사용자별 정책을 할당하려면 **Grant-CsClientPolicy** cmdlet을 사용해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Grant-CsClientPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Grant-CsClientPolicy"}

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
<td><p>정책을 할당할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 참조할 수도 있습니다.</p>
<p>또한 표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 ID &quot;* Smith&quot;는 표시 이름이 문자열 값 &quot; Smith&quot;로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PolicyName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>할당할 정책의 &quot;이름&quot;입니다. PolicyName은 간단히 말해 정책 ID에서 정책 범위(&quot;tag:&quot;)를 뺀 것입니다. 예를 들어 ID가 tag:Redmond인 정책의 PolicyName은 Redmond와 같고, ID가 tag:RedmondConferencingPolicy인 정책의 PolicyName은 RedmondConferencingPolicy와 같습니다.</p>
<p>PolicyName을 null 값으로 설정하면 명령이 사용자에게 할당된 사용자별 정책의 할당을 해제합니다. 예를 들면 다음과 같습니다.</p>
<p>Grant-CsClientPolicy –Identity &quot;Ken Myer&quot; –PolicyName $Null</p></td>
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
<td><p>이 매개 변수가 있으면 cmdlet이 Windows PowerShell 파이프라인을 통해 사용자 개체를 하나 이상 전달합니다. 기본적으로 <strong>Grant-CsClientPolicy</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
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

문자열 값 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Grant-CsClientPolicy** cmdlet은 사용자 계정의 ID를 나타내는 문자열 값의 파이프라인된 입력을 허용합니다. 이 cmdlet은 또한 사용자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

기본적으로 **Grant-CsClientPolicy** cmdlet은 개체 또는 값을 반환하지 않습니다. 그러나 PassThru 매개 변수를 포함할 경우 Microsoft.Rtc.Management.ADConnect.Schema.OCSUserOrAppContact 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClientPolicy](get-csclientpolicy.md)  
[New-CsClientPolicy](new-csclientpolicy.md)  
[Remove-CsClientPolicy](remove-csclientpolicy.md)  
[Set-CsClientPolicy](set-csclientpolicy.md)

