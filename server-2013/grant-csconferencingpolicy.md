---
title: Grant-CsConferencingPolicy
TOCTitle: Grant-CsConferencingPolicy
ms:assetid: 43c63a01-5072-45f0-89ee-8c3ae0cd9035
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425937(v=OCS.15)
ms:contentKeyID: 49303472
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Grant-CsConferencingPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자별 범위에서 전화 회의 정책을 할당합니다. 전화 회의 정책은 전화 회의에서 사용할 수 있는 기능을 결정합니다. 여기에는 모임에 IP 오디오 및 비디오를 포함할 수 있는지부터 모임에 참가할 수 있는 최대 사용자 수까지 모든 사항이 포함됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Grant-CsConferencingPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Grant-CsConferencingPolicy** cmdlet을 사용하여 Identity가 "Ken Myer"인 사용자에게 SalesConferencingPolicy 정책을 할당합니다.

    Grant-CsConferencingPolicy -identity "Ken Myer" -PolicyName SalesConferencingPolicy

## 예제 2

예제 2에서는 Finance 조직 구성 단위에 계정이 있는 모든 사용자에게 전화 회의 정책 FinanceConferencingPolicy가 할당됩니다. 지정된 OU(조직 구성 단위)의 모든 사용자에게 동일한 정책을 할당하기 위해 **Get-CsUser** cmdlet을 사용하여 해당 OU의 모든 계정을 검색합니다. 모든 사용자 계정이 검색된 후 해당 정보는 컬렉션의 각 사용자에게 FinanceConferencingPolicy 정책을 할당하는 **Grant-CsConferencingPolicy** cmdlet에 파이프됩니다.

    Get-CsUser -OU "ou=Finance,dc=litwareinc,dc=com" | Grant-CsConferencingPolicy -PolicyName FinanceConferencingPolicy

## 예제 3

예제 3은 예제 2의 변형을 나타내지만 이 경우에는 Finance OU의 사용자에게 이전에 할당된 모든 사용자별 전화 회의 정책을 할당 취소합니다. 이 작업을 수행하기 위해 PolicyName 매개 변수 값을 null 값($Null)으로 지정하고 **Grant-CsConferencingPolicy** cmdlet을 호출합니다.

    Get-CsUser -OU "ou=Finance,dc=litwareinc,dc=com" | Grant-CsConferencingPolicy -PolicyName $Null

## 예제 4

예제 4에서는 Human Resource 부서에서 근무하는 모든 사용자에게 HRConferencingPolicy 정책이 할당됩니다. 이 작업을 수행하기 위해 **Get-CsUser** cmdlet 및 LdapFilter 매개 변수를 호출하여 적절한 사용자 집합을 검색합니다. 매개 변수 값 "Department=Human Resources"는 Department 특성이 "Human Resources"로 설정된 사용자 계정만 반환되도록 항목을 제한합니다. 사용자 계정이 검색된 후 이 컬렉션은 컬렉션의 각 사용자에게 HRConferencingPolicy 정책을 할당하는 **Grant-CsConferencingPolicy** cmdlet에 파이프됩니다.

    Get-CsUser -LdapFilter "Department=Human Resources" | Grant-CsConferencingPolicy -PolicyName HRConferencingPolicy

## 자세한 정보

전화 회의는 Lync Server의 중요한 부분입니다. 전화 회의 기능을 사용하면 사용자 그룹이 온라인으로 모여 슬라이드 및 비디오 보기, 응용 프로그램 공유, 파일 교환, 기타 통신 및 공동 작업 등을 수행할 수 있기 때문입니다.

관리자가 전화 회의 및 전화 회의 설정에 대한 제어를 유지 관리하는 기능도 중요합니다. 경우에 따라 보안 문제가 발생할 수 있습니다. 기본적으로 인증되지 않은 사용자를 비롯한 모든 사용자가 모임에 참가하고 모임 중에 배포된 슬라이드나 유인물을 저장할 수 있습니다. 대역폭 문제가 발생하는 경우도 있습니다. 예를 들어 동시 모임 수가 많은 경우, 각 모임에 수백 명의 참가자가 있는 경우 및 각 모임에서 화상 공급 및 파일 공유를 사용하는 경우에 네트워크에 문제가 발생할 수 있습니다. 또한 법적인 문제가 발생할 수 있습니다. 예를 들어 모임 참가자는 기본적으로 공유 콘텐츠에 주석을 추가할 수 있지만 이러한 주석은 모임을 보관할 때 저장되지 않습니다. 조직에서 모든 전자 통신의 기록을 보관해야 하는 경우 주석을 비활성화해야 할 수도 있습니다.

물론 전화 회의 설정을 관리해야 하는 것도 중요한 사항입니다. 실제로 이러한 설정을 관리하는 것은 또 다른 문제입니다. Lync Server에서는 전화 회의 정책을 사용하여 전화 회의를 관리합니다. 이전 버전의 소프트웨어에서는 이러한 정책을 모임 정책이라고 했습니다. 앞서 언급한 것처럼 전화 회의 정책은 전화 회의에서 사용할 수 있는 기능을 결정하며, 여기에는 전화 회의에 IP 오디오 및 비디오를 포함할 수 있는지 여부부터 모임에 참가할 수 있는 최대 사용자 수에 이르기까지 모든 기능이 포함됩니다. 전화 회의 정책은 전역 범위, 사이트 범위 또는 사용자별 범위에서 구성할 수 있습니다. 따라서 각 사용자가 사용할 수 있는 기능을 관리자가 유동적으로 결정할 수 있습니다.

사이트 정책을 만드는 경우 해당 정책이 만들어질 때 적절한 사이트에 자동으로 할당됩니다. 이와 달리, 사용자별 정책은 만들어질 때 아무에게도 할당되지 않습니다. 대신 **Grant-CsConferencingPolicy** cmdlet을 사용하여 사용자 또는 사용자 집합에 사용자별 전화 회의 정책을 명시적으로 할당해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Grant-CsConferencingPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Grant-CsConferencingPolicy"}

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
<td><p>정책을 할당할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그인 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 참조할 수도 있습니다.</p>
<p>사용자 ID를 지정할 때 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 ID &quot;* Smith&quot;는 표시 이름이 문자열 값 &quot; Smith&quot;로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PolicyName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>할당할 정책의 &quot;이름&quot;입니다. PolicyName은 간단히 말해 정책 ID에서 정책 범위(&quot;tag:&quot; 접두사)를 뺀 부분입니다. 예를 들어 Identity가 tag:Redmond인 정책의 PolicyName은 Redmond와 같고, Identity가 tag:RedmondConferencingPolicy인 정책의 PolicyName은 RedmondConferencingPolicy와 같습니다.</p>
<p>사용자에게 이전에 할당된 사용자별 정책을 할당 취소하려면 PolicyName 매개 변수를 $Null로 설정합니다.</p></td>
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
<td><p>새 정책을 할당할 때 연결할 도메인 컨트롤러의 FQDN(정규화된 도메인 이름)을 지정하는 데 사용됩니다. 이 매개 변수를 지정하지 않으면 <strong>Grant-CsConferencingPolicy</strong> cmdlet은 사용 가능한 첫 번째 도메인 컨트롤러에 연결합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>정책을 할당할 사용자를 나타내는 사용자 개체를 파이프라인을 통해 전달하는 데 사용됩니다. 기본적으로 <strong>Grant-CsConferencingPolicy</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
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

문자열 값 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Grant-CsConferencingPolicy** cmdlet은 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값 입력을 허용합니다. 또한 이 cmdlet은 사용자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

기본적으로 **Grant-CsConferencingPolicy** cmdlet은 개체나 값을 반환하지 않습니다. 그러나 PassThru 매개 변수를 포함한 경우 이 cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSUserOrAppContact 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsConferencingPolicy](get-csconferencingpolicy.md)  
[New-CsConferencingPolicy](new-csconferencingpolicy.md)  
[Remove-CsConferencingPolicy](remove-csconferencingpolicy.md)  
[Set-CsConferencingPolicy](set-csconferencingpolicy.md)

