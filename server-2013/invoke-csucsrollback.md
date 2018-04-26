---
title: Invoke-CsUcsRollback
TOCTitle: Invoke-CsUcsRollback
ms:assetid: 0aed0286-e552-4d47-93bc-3375cab48a03
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204661(v=OCS.15)
ms:contentKeyID: 49302757
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Invoke-CsUcsRollback

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자 연락처를 통합 연락처 저장소에서 제거하고 해당 연락처 정보를 Lync Server 2013에 대신 저장합니다. 사용자는 통합 연락처 저장소를 통해 Lync 2013, Microsoft Outlook 및/또는 Microsoft Outlook Web Access를 사용하여 액세스할 수 있는 단일 연락처 집합을 유지 관리할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Invoke-CsUcsRollback -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 사용자 Ken Myer를 통합 연락처 저장소에서 제거합니다.

    Invoke-CsUcsRollback -Identity "Ken Myer"

## 예제 2

예제 2에서는 등록자 풀 atl-cs-001.litwareinc.com에 있는 모든 사용자가 통합 연락처 저장소에서 제거됩니다. 이를 위해 명령은 먼저 Filter 매개 변수를 사용하여 **Get-CsUser** cmdlet을 호출합니다. 필터 값 {RegistrarPool –eq "atl-cs-001.litwareinc.com"}은 반환되는 데이터를 atl-cs-001.litwareinc.com 풀에 있는 사용자로 제한합니다. 이러한 사용자 계정은 **Invoke-CsUcsRollback** cmdlet에 파이프되며, 이 cmdlet은 통합 연락처 저장소에서 각 사용자를 제거합니다. cmdlet이 사용자 계정을 롤백할 때마다 표시되는 확인 메시지가 표시되지 않도록 하기 위해 -Confirm:$False 구문을 사용하여 Confirm 매개 변수가 포함되었습니다.

    Get-CsUser -Filter {RegistrarPool -eq "atl-cs-001.litwareinc.com"} | Invoke-CsUcsRollback -Confirm:$False

## 자세한 정보

Lync Server 2013에서 도입된 통합 연락처 저장소를 통해 관리자는 Lync Server가 아닌 Microsoft Exchange Server 2013에서 사용자 연락처를 저장할 수 있습니다. 그러면 사용자가 Lync 2013에서는 물론 Microsoft Outlook과 Outlook Web Access에서도 같은 연락처 집합에 액세스할 수 있습니다. 계속 Lync Server에서 연락처를 저장할 수도 있는데, 이 경우 사용자는 서로 다른 두 연락처 집합(Outlook 및 Outlook Web Access에서 사용할 연락처 집합과 Lync 2013에서 사용할 연락처 집합)을 유지 관리해야 합니다.

통합 연락처 저장소를 활용하려면 우선 통합 연락처 저장소를 사용할 수 있도록 설정하는 사용자 서비스 정책을 사용자에게 할당해야 합니다. 기타 모든 전제 조건이 충족된 경우 다음 번에 사용자가 Lync Server 2013를 사용하여 로그온하면 사용자의 연락처가 Lync Server에서 통합 연락처 저장소로 자동 이동됩니다. 자세한 내용은 Set-CsUserServicesPolicy cmdlet의 도움말 항목을 참조하십시오.

나중에 이러한 연락처를 통합 연락처 저장소에서 다시 Lync Server로 이동하려면 두 가지 작업을 수행해야 합니다. 먼저 사용자에게 통합 연락처 저장소 사용을 금지하는 새 사용자 서비스 정책을 할당해야 합니다. 그런 다음 **Invoke-CsUcsRollback** cmdlet을 사용하여 연락처를 통합 연락처 저장소에서 Lync Server로 "수동" 마이그레이션해야 합니다. 사용자 서비스 정책만 변경한다고 사용자 연락처가 통합 연락처 저장소에서 제거되지는 않으며, **Invoke-CsUcsRollback** cmdlet을 호출해야 연락처를 제거할 수 있습니다.

기술적으로는 사용자 서비스 정책을 수정하지 않고 **Invoke-CsUcsRollback** cmdlet만 호출하면 사용자의 연락처가 통합 연락처 저장소에서 제거됩니다. 그러나 이 변경 작업은 일시적으로만 적용되며, 사용자 서비스 정책을 변경하지 않으면 7일의 대기 기간 후에 사용자 연락처가 통합 연락처 저장소로 다시 자동 이동됩니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Invoke-CsUcsRollback"}

**Lync Server 제어판:** **Invoke-CsUcsRollback** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>롤백할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 보통 네 가지 형식 중 하나를 사용하여 지정되는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다.</p>
<p>또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 계정을 참조할 수도 있습니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 &quot; Smith&quot; 문자열 값으로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다. 사용자 계정을 롤백할 때마다 확인 메시지가 표시되지 않도록 하려면 다음 구문을 사용합니다.</p>
<p>-Confirm:$False</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>사용자 정보를 검색하기 위해 지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-dc-001) 또는 FQDN(정규화된 도메인 이름)(예: atl-dc-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>통합 연락처 저장소에서 제거되는 사용자 계정을 나타내는 사용자 개체를 파이프라인을 통해 전달할 수 있습니다. 기본적으로 <strong>Invoke-CsUcsRollback</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
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

문자열 값 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Invoke-CsUcsRollback** cmdlet은 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값 입력을 허용합니다. 또한 이 cmdlet은 사용자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

없음

## 참고 항목

#### 기타 리소스

[New-CsUserServicesPolicy](new-csuserservicespolicy.md)  
[Set-CsUserServicesPolicy](set-csuserservicespolicy.md)  
[Test-CsUnifiedContactStore](test-csunifiedcontactstore.md)

