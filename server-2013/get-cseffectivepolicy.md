---
title: Get-CsEffectivePolicy
TOCTitle: Get-CsEffectivePolicy
ms:assetid: 03b2984f-3a24-4b8d-bcaf-5049de9e2556
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204636(v=OCS.15)
ms:contentKeyID: 49302647
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsEffectivePolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

한 명 이상의 지정된 사용자에 대한 "실제 정책"을 반환합니다. 이는 사용자에게 사용자별 정책이 할당된 경우 해당 정책의 ID가 표시됨을 의미합니다. 사용자에게 사용자별 정책이 할당되지 않은 경우 **Get-CsEffectivePolicy** cmdlet은 해당 사용자를 관리하는 데 사용되는 정책(서비스 정책, 사이트 정책 또는 전역 정책)을 나타냅니다. 따라서 지정된 사용자를 관리하는 데 사용되는 정책을 정확히 확인할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsEffectivePolicy -Identity <UserIdParameter> [-Credential <PSCredential>] [-DomainController <Fqdn>] [-ResultSize <Unlimited>]

## 예제

## 예제 1

예제 1에 표시된 명령은 Active Directory 표시 이름이 Ken Myer인 사용자에 대한 실제 정책을 반환합니다.

    Get-CsEffectivePolicy - Identity "Ken Myer"

## 예제 2

위의 명령에서는 표시 이름이 Ken Myer 및 Pilar Ackerman인 사용자에 대한 실제 정책 정보가 반환됩니다. 여러 사용자 ID를 **Get-CsEffectivePolicy** cmdlet에 파이프하면 여러 사용자에 대한 정책 정보를 반환할 수 있습니다.

    "Ken Myer","Pilar Ackerman" | Get-CsEffectivePolicy

## 예제 3

예제 3에서는 RedmondConferencingPolicy 회의 정책이 할당된 모든 사용자에 대한 실제 정책 정보를 반환합니다. 이를 위해 명령은 먼저 **Get-CsUser** cmdlet을 사용하여 RedmondConferencingPolicy가 할당된 사용자의 컬렉션을 반환합니다. Filter 매개 변수 및 필터 값 {ConferencingPolicy –eq "RedmondConferencingPolicy"}를 통해 반환되는 데이터를 RedmondConferencingPolicy 사용자별 회의 정책이 할당된 사용자로 제한합니다. 해당 사용자 계정 컬렉션은 **Get-CsEffectivePolicy** cmdlet에 파이프되며, 이 cmdlet은 컬렉션의 각 사용자에 대한 실제 정책 정보를 표시합니다.

    Get-CsUser -Filter {ConferencingPolicy -eq "RedmondConferencingPolicy"} | Get-CsEffectivePolicy

## 예제 4

예제 4는 예제 3에 표시된 명령의 변형입니다. 이 예제에서도 RedmondConferencingPolicy 회의 정책이 할당된 모든 사용자에 대한 실제 정책 정보가 반환되지만, 반환되는 정보는 사용자 ID 및 모바일 정책으로 제한됩니다. 이 작업을 수행하기 위해 모든 실제 정책 정보를 반환한 다음 해당 데이터를 **Select-Object** cmdlet에 파이프합니다. 그런 다음 이 cmdlet을 사용하여 표시되는 데이터를 Identity 및 MobilityPolicy 속성으로 제한합니다.

    Get-CsUser -Filter {ConferencingPolicy -eq "RedmondConferencingPolicy"} | Get-CsEffectivePolicy | Select-Object Identity, MobilityPolicy

## 예제 5

예제 5에서는 Finance 부서의 모든 사용자에 대한 실제 정책 정보가 표시됩니다. 이 작업을 수행하기 위해 먼저 **Get-CsUser** cmdlet 및 LdapFilter 속성을 사용하여 사용자 계정 컬렉션을 반환합니다. 필터 값 "Department=Finance"는 컬렉션에 포함되는 계정을 Finance 부서에서 근무하는 사용자로 제한합니다. 해당 컬렉션은 **Get-CsEffectivePolicy** cmdlet에 파이프되며, 이 cmdlet은 컬렉션의 각 사용자에 대한 실제 정책 정보를 표시합니다.

    Get-CsUser -LdapFilter "Department=Finance" | Get-CsEffectivePolicy

## 자세한 정보

**Get-CsUser** cmdlet의 가장 중요한 기능은 사용자 동작을 제어하는 데 사용되는 Microsoft Lync Server 정책에 대한 정보를 반환하는 것입니다. 예를 들면 다음과 같습니다.

DialPlan : RedmondDialPlan

LocationPolicy : RedmondLocationPolicy

ClientPolicy :

위의 출력에 따르면 사용자는 클라이언트가 아닌 특정 다이얼 플랜 및 위치 정책에 의해 관리되는 것처럼 보이지만, 실제로는 사용자가 클라이언트 정책(전역 정책 또는 사이트 정책)을 통해 관리됩니다. 그러나 **Get-CsUser** cmdlet은 사용자에게 할당된 사용자별 정책에 대한 정보만 반환합니다. 사용자가 전역 정책, 사이트 정책 또는 서비스 정책에 의해 관리되는 경우 **Get-CsUser** cmdlet은 아무 정보도 반환하지 않습니다.

문제 해결 시나리오에서는 사용자를 관리하는 데 사용되는 정책(전역 정책, 사이트 정책 또는 서비스 정책)을 알아 두면 매우 유용할 수 있습니다. 이러한 경우 **Get-CsEffectivePolicy** cmdlet을 사용하여 사용자 동작을 제어하는 데 사용되는 정책에 대한 정확한 정보를 반환할 수 있습니다. 위에 나와 있는 사용자의 경우 **Get-CsEffectivePolicy** cmdlet은 다음과 같은 정보를 반환합니다.

LocationProfile : RedmondDialPlan

LocationPolicy : RedmondLocationPolicy

ClientPolicy : Global

이 출력을 통해 사용자가 전역 클라이언트 정책으로 관리됨을 확인할 수 있습니다.

**Get-CsUser** cmdlet과는 달리 **Get-CsEffectivePolicy** cmdlet은 정책에 대한 정보만 반환하며 사용자 전화 번호, 등록자 풀 등의 추가 정보는 반환하지 않습니다. 또한 **Get-CsUser** cmdlet에서 정책 이름에 레이블을 지정하는 데 사용되는 용어와 **Get-CsEffectivePolicy** cmdlet에서 사용되는 용어에는 몇 가지 차이가 있습니다. 예를 들어 **Get-CsUser** cmdlet은 DialPlan이라는 이름을 사용하는 반면 **Get-CsEffectivePolicy** cmdlet은 LocationProfile이라는 이름을 사용합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsEffectivePolicy"}

**Lync Server 제어판:** **Get-CsEffectivePolicy** cmdlet에 의해 수행되는 기능을 Lync Server 제어판에서 직접 사용할 수는 없습니다.

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
<td><p>실제 정책 설정이 적용되는 사용자 계정의 ID를 나타냅니다. 사용자 ID는 보통 다음 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 계정을 참조할 수도 있습니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 &quot; Smith&quot; 문자열 값으로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Credential</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>대체 자격 증명으로 Get-CsEffectivePolicy cmdlet을 실행할 수 있도록 합니다. Windows에 로그온하는 데 사용한 계정에 사용자 개체를 사용하는 데 필요한 권한이 없는 경우 이 기능이 필요할 수 있습니다.</p>
<p>Credential 매개 변수를 사용하려면 먼저 <strong>Get-Credential</strong> cmdlet을 사용하여 PSCredential 개체를 만들어야 합니다. 자세한 내용은 <strong>Get-Credential</strong> cmdlet 도움말 항목을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>사용자 정보를 검색하기 위해 지정한 도메인 컨트롤러에 연결할 수 있습니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 FQDN(정규화된 도메인 이름)을 포함합니다. 예를 들면 다음과 같습니다.</p>
<p>-DomainController &quot;atl-dc-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>ResultSize</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>cmdlet에서 반환되는 레코드 수를 제한하는 데 사용됩니다. 예를 들어 포리스트에 있는 사용자 수에 상관없이 7명의 사용자를 반환하려면 ResultSize 매개 변수를 포함하고 매개 변수 값을 7로 설정합니다. 반환될 7명의 사용자를 지정하는 방법은 없습니다.</p>
<p>결과 크기는 0에서 2147483647(포함) 사이의 정수로 설정할 수 있습니다. 0으로 설정하면 명령은 실행되지만 데이터는 반환되지 않습니다. ResultSize를 7로 설정했는데 포리스트에 사용자가 3명밖에 없으면 3명의 사용자가 반환되고 오류 없이 완료됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Get-CsEffectivePolicy** cmdlet은 Lync Server를 사용하도록 설정된 사용자 계정의 표시 이름을 나타내는 파이프라인된 문자열 값을 허용합니다. 또한 이 cmdlet은 Active Directory 사용자 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Get-CsEffectivePolicy** cmdlet은 Microsoft.Rtc.Management.AD.Cmdlets.EffectivePolicies 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUser](get-csuser.md)

