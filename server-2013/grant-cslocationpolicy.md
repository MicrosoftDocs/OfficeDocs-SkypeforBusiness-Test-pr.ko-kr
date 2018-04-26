---
title: Grant-CsLocationPolicy
TOCTitle: Grant-CsLocationPolicy
ms:assetid: f820f892-c247-447c-947a-00414189842e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413049(v=OCS.15)
ms:contentKeyID: 49305577
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Grant-CsLocationPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

E9-1-1(Enhanced 911) 위치 정책을 개별 사용자 또는 그룹에 할당합니다. E9-1-1 서비스를 사용하면 911 전화 응답자가 발신자의 지리적 위치를 확인할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Grant-CsLocationPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Grant-CsLocationPolicy** cmdlet을 사용하여 사용자 Ken Myer에게 Reno 위치 정책을 할당합니다.

    Grant-CsLocationPolicy -Identity "Ken Myer" -PolicyName Reno

## 예제 2

예제 2에서는 Accounting 부서에 속한 모든 사용자에게 AccountingArea 정책을 할당합니다. Accounting 부서의 모든 사용자 컬렉션을 반환하기 위해 **Get-CsUser** cmdlet을 LDAPFilter 매개 변수와 함께 사용합니다. LDAPFilter--"Department=Accounting"--에 전달된 쿼리 값은 Active Directory Department 설정이 Accounting인 모든 사용자를 반환합니다. 이 컬렉션은 컬렉션의 각 사용자에게 계속 AccountingArea 정책을 할당하는 **Grant-CsLocationPolicy** cmdlet에 전달됩니다.

    Get-CsUser -LDAPFilter "Department=Accounting" | Grant-CsLocationPolicy -PolicyName AccountingArea

## 예제 3

이 예제에서는 ID(이 경우에는 표시 이름)가 Ken Myer인 사용자에게 위치 정책 Reno를 부여합니다. 또한 위치 정책이 부여된 후 사용자 Ken Myer에 대한 사용자 정보를 표시하는 PassThru 매개 변수도 포함합니다. 그러나 사용자 정보를 콘솔에 즉시 표시하는 것이 아니라 해당 정보가 **Select-Object** cmdlet에 파이프되어 사용자의 DisplayName 및 LocationPolicy 속성만 표시됩니다.

이 예제에서 주목할 점은 새로 부여된 위치 정책이 LocationPolicy 아래 출력에 나타나지만 정책 이름이 아니라 Anchor 값으로 표시된다는 점입니다. Anchor 값은 정책이 만들어질 때 정책에 자동으로 할당되는 숫자 값입니다. 적용된 정책 이름을 보려면 Get-CsUser –Identity "Ken Myer" | Select-Object DisplayName, LocationPolicy 명령을 실행합니다.

    Grant-CsLocationPolicy -Identity "Ken Myer" -PolicyName Reno -PassThru | Select-Object DisplayName, LocationPolicy

## 자세한 정보

위치 정책은 E9-1-1 기능과 관련된 설정을 적용하는 데 사용되며, 사용자가 E9-1-1을 사용하도록 설정되어 있는지 여부를 확인하고, 설정된 경우 응급 통화에 대한 행동을 결정합니다. 예를 들어 위치 정책을 사용하여 응급 통화 번호(한국의 경우 119)를 정의하고, 회사 보안 부서에 자동으로 알림을 제공할지 여부, 통화를 경로 지정할 방법 등을 지정할 수 있습니다. 이 cmdlet은 특정 사용자 또는 그룹에 위치 정책을 부여합니다.

중요: 위치 정책은 범위 체계와 관련하여 Lync Server의 다른 정책과 다르게 동작합니다. 다른 모든 정책의 경우 정책이 사용자별 범위에 정의되어 있으면 해당 정책이 부여된 모든 사용자에게 정책이 적용됩니다. 사용자에게 사용자별 정책이 부여되지 않았으면 사이트 정책이 적용됩니다. 사이트 정책이 없으면 전역 정책이 적용됩니다. 위치 정책도 동일한 방식으로 적용됩니다. 단, 한 가지 예외는 네트워크 사이트에 사용자별 위치 정책을 할당할 수도 있다는 점입니다. 네트워크 사이트는 서브넷 그룹으로 구성됩니다. 사용자가 조직 내 네트워크 사이트에 매핑된 위치에서 긴급 통화를 걸면 해당 네트워크에 할당된 사용자 수준 정책이 사용됩니다. 이 기능은 해당 사용자에게 부여된 사용자별 정책보다 우선합니다. 사용자가 조직에서 알 수 없거나 매핑되지 않은 위치에서 전화를 거는 경우 표준 정책 범위가 적용됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Grant-CsLocationPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Grant-CsLocationPolicy"}

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
<td><p>정책을 할당해야 하는 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. SAMAccountName은 ID로 사용할 수 없습니다.</p>
<p>또한 표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 ID &quot;* Smith&quot;는 성이 Smith인 모든 사용자에게 정책을 부여합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PolicyName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>사용자에게 적용할 위치 정책의 ID입니다.</p></td>
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
<td><p>도메인 컨트롤러를 지정하도록 합니다. 도메인 컨트롤러를 지정하지 않으면 사용 가능한 첫 번째 도메인 컨트롤러가 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 값을 사용하지 않고 포함하면 cmdlet이 완료될 때 사용자 정보가 표시됩니다. 일반적으로 이 cmdlet을 실행하면 출력이 표시되지 않습니다.</p></td>
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

문자열. 위치 정책을 부여할 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다.

## 반환 형식

PassThru 매개 변수와 함께 사용된 경우 Microsoft.Rtc.Management.ADConnect.Schema.OCSADUserOrAppContact 개체 유형을 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsLocationPolicy](new-cslocationpolicy.md)  
[Remove-CsLocationPolicy](remove-cslocationpolicy.md)  
[Set-CsLocationPolicy](set-cslocationpolicy.md)  
[Get-CsLocationPolicy](get-cslocationpolicy.md)  
[Test-CsLocationPolicy](test-cslocationpolicy.md)  
[Get-CsUser](get-csuser.md)

