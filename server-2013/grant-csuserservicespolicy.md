---
title: Grant-CsUserServicesPolicy
TOCTitle: Grant-CsUserServicesPolicy
ms:assetid: f68b5c61-9820-4b49-954a-2dd61156bc02
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205388(v=OCS.15)
ms:contentKeyID: 49305561
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Grant-CsUserServicesPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

한 명 이상의 사용자에게 사용자별 사용자 서비스 정책을 할당합니다. 사용자 서비스 정책은 사용자의 연락처가 Lync Server 2013에 저장되는지 아니면 통합 연락처 저장소에 저장되는지를 결정합니다. 사용자는 통합 연락처 저장소를 통해 Lync 2013, Microsoft Outlook 및/또는 Microsoft Outlook Web Access를 사용하여 액세스할 수 있는 단일 연락처 집합을 유지 관리할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Grant-CsUserServicesPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID(여기서는 Active Directory 표시 이름)가 Ken Myer인 사용자에게 사용자별 사용자 서비스 정책 RedmondUserServicesPolicy를 할당합니다.

    Grant-CsUserServicesPolicy -Identity "Ken Myer" -PolicyName "RedmondUserServicesPolicy"

## 예제 2

예제 2에서는 이전에 Ken Myer에게 할당되었던 사용자별 사용자 서비스 정책의 할당을 취소합니다. 사용자별 정책의 할당을 취소하려면 PolicyName 매개 변수를 Null 값($Null)으로 설정합니다.

    Grant-CsUserServicesPolicy -Identity "Ken Myer" -PolicyName $Null

## 예제 3

예제 3에서는 RegistrarPool atl-cs-001.litwareinc.com에 있는 모든 사용자에게 사용자별 사용자 서비스 정책 RedmondUserServicesPolicy를 할당합니다. 이를 위해 먼저 Filter 매개 변수를 포함하여 **Get-CsUser** cmdlet을 호출합니다. 필터 값 {RegistrarPool –eq "atl-cs-001.litwareinc.com"은 반환되는 데이터를 홈이 등록자 풀 atl-cs-001.litwareinc.com으로 지정된 사용자로 제한합니다. 이 사용자 컬렉션은 **Grant-CsUserServicesPolicy** cmdlet에 파이프되며, 해당 cmdlet은 컬렉션의 각 사용자에게 RedmondUserServicesPolicy 정책을 할당합니다.

    Get-CsUser -Filter {RegistrarPool -eq "atl-cs-001.litwareinc.com"} | Grant-CsUserServicesPolicy -PolicyName "RedmondUserServicesPolicy"

## 자세한 정보

Lync Server 2013에서 도입된 통합 연락처 저장소를 통해 관리자는 Lync Server가 아닌 Microsoft Exchange Server 2013에서 사용자 연락처를 저장할 수 있습니다. 그러면 사용자가 Lync 2013에서는 물론 Microsoft Outlook과 Outlook Web Access에서도 같은 연락처 집합에 액세스할 수 있습니다. 계속 Lync Server 2013에서 연락처를 저장할 수도 있는데, 이 경우 사용자는 서로 다른 두 연락처 집합(Outlook 및 Outlook Web Access에서 사용할 연락처 집합과 Lync 2013에서 사용할 연락처 집합)을 유지 관리해야 합니다.

통합 연락처 저장소를 활용하려면 우선 통합 연락처 저장소를 사용할 수 있도록 설정하는 사용자 서비스 정책을 사용자에게 할당해야 합니다. 전역, 사이트 또는 사용자별 범위에서 구성할 수 있는 사용자 서비스 정책은 하나의 속성, 즉 UcsAllowed만 포함합니다. 이 속성을 True로 설정하는 경우 기타 모든 전제 조건이 충족되었다고 가정할 때 다음 번에 사용자가 Lync Server 2013에 로그온하면 사용자의 연락처가 통합 연락처 저장소로 자동 마이그레이션됩니다.

이 속성을 False로 설정하면 이와 같은 자동 마이그레이션이 수행되지 않습니다. 그러나 UcsAllowed만 설정한다고 해서 사용자 연락처가 통합 연락처 저장소에서 Lync Server로 다시 이동되지는 않습니다. 이러한 이동을 수행하려면 먼저 통합 연락처 저장소 사용을 허용하지 않는 사용자 서비스 정책을 사용자에게 할당해야 합니다. 그 후에는 I**nvoke-UcsRollback** cmdlet을 사용하여 연락처를 통합 연락처 저장소에서 Lync Server로 다시 "수동으로" 마이그레이션해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Grant-CsUserServicesPolicy"}

**Lync Server 제어판:** **Grant-CsUserServicesPolicy** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>사용자별 사용자 환경 정책을 할당할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 보통 네 가지 형식 중 하나를 사용하여 지정되는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다.</p>
<p>사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 지정할 수도 있습니다.</p>
<p>또한 표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 &quot; Smith&quot; 문자열 값으로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PolicyName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>할당할 정책의 &quot;이름&quot;입니다. PolicyName은 간단히 말해 정책 ID에서 정책 범위(&quot;tag:&quot; 접두사)를 뺀 부분입니다. 예를 들어 ID가 tag:Redmond인 정책의 PolicyName은 Redmond와 같습니다. 마찬가지로 ID가 tag:RedmondUserExperiencePolicy인 정책의 PolicyName은 RedmondUserExperiencePolicy와 같습니다.</p>
<p>사용자에게 이전에 할당한 사용자별 정책을 할당 취소하려면 PolicyName을 null 값($Null)으로 설정합니다.</p></td>
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
<td><p>사용자 정보를 검색하기 위해 지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-dc-001) 또는 FQDN(정규화된 도메인 이름)(예: atl-dc-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>정책을 할당할 사용자 계정을 나타내는 사용자 개체를 파이프라인을 통해 전달하는 데 사용됩니다. 기본적으로 <strong>Grant-CsUserServicesPolicy</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>실제로 명령을 수행하지는 않고 명령을 실행했을 때 발생할 결과에 대해 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열 값 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Grant-CsUserServicesPolicy** cmdlet은 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값 입력을 허용합니다. 또한 이 cmdlet은 사용자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

기본적으로 **Grant-CsUserServicesPolicy** cmdlet은 값 또는 개체를 반환하지 않습니다. 그러나 PassThru 매개 변수를 포함할 경우 이 cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSUserOrAppContact의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUserServicesPolicy](get-csuserservicespolicy.md)  
[New-CsUserServicesPolicy](new-csuserservicespolicy.md)  
[Remove-CsUserServicesPolicy](remove-csuserservicespolicy.md)  
[Set-CsUserServicesPolicy](set-csuserservicespolicy.md)

