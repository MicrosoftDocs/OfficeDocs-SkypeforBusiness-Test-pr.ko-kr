---
title: Get-CsUserServicesPolicy
TOCTitle: Get-CsUserServicesPolicy
ms:assetid: 424cd3ca-6df4-4715-97f1-95d2da3b6d90
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204838(v=OCS.15)
ms:contentKeyID: 49303449
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsUserServicesPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 사용자 서비스 정책에 대한 정보를 반환합니다. 사용자 서비스 정책은 사용자의 연락처가 Lync Server 2013에 저장되는지 아니면 통합 연락처 저장소에 저장되는지를 결정합니다. 사용자는 통합 연락처 저장소를 통해 Lync 2013, Outlook 및/또는 Outlook Web Access를 사용하여 액세스할 수 있는 단일 연락처 집합을 유지 관리할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsUserServicesPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsUserServicesPolicy [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>] [-Tenant <Guid>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 현재 사용 중인 모든 사용자 서비스 정책에 대한 정보를 반환합니다.

    Get-CsUserServicesPolicy

## 예제 2

예제 2에서는 Redmond 사이트용으로 구성된 단일 사용자 서비스 정책에 대한 정보를 반환합니다.

    Get-CsUserServicesPolicy -Identity "site:Redmond"

## 예제 3

예제 3에서는 사이트 범위에서 구성된 모든 사용자 서비스 정책에 대한 정보를 반환합니다. 이 작업은 Filter 매개 변수와 필터 값 "site:\*"를 포함하여 수행됩니다.

    Get-CsUserServicesPolicy -Filter "site:*"

## 예제 4

예제 4에 표시된 명령은 통합 연락처 저장소를 사용하지 않도록 설정된 사용자 서비스 정책에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 매개 변수 없이 **Get-CsUserServicesPolicy** cmdlet을 호출합니다. 그러면 조직에서 사용하도록 구성된 모든 사용자 서비스 정책의 컬렉션이 반환됩니다. 해당 컬렉션은 UcsAllowed 속성이 False($False)로 설정된 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsUserServicesPolicy | Where-Object {$_.UcsAllowed -eq $False}

## 자세한 정보

Lync Server 2013에서 도입된 통합 연락처 저장소를 통해 관리자는 Lync Server가 아닌 Microsoft Exchange Server 2013에서 사용자 연락처를 저장할 수 있습니다. 그러면 사용자가 Lync 2013에서는 물론 Outlook과 Outlook Web Access에서도 같은 연락처 집합에 액세스할 수 있습니다. 계속 Lync Server 2013에서 연락처를 저장할 수도 있는데, 이 경우 사용자는 서로 다른 두 연락처 집합(Outlook 및 Outlook Web Access에서 사용할 연락처 집합과 Lync 2013에서 사용할 연락처 집합)을 유지 관리해야 합니다.

통합 연락처 저장소를 활용하려면 우선 통합 연락처 저장소를 사용할 수 있도록 설정하는 사용자 서비스 정책을 사용자에게 할당해야 합니다. 전역, 사이트 또는 사용자별 범위에서 구성할 수 있는 사용자 서비스 정책은 하나의 속성, 즉 UcsAllowed만 포함합니다. 이 속성을 True로 설정하는 경우 기타 모든 전제 조건이 충족되었다고 가정할 때 다음 번에 사용자가 Lync Server 2013에 로그온하면 사용자의 연락처가 통합 연락처 저장소로 자동 마이그레이션됩니다.

이 속성을 False로 설정하면 이와 같은 자동 마이그레이션이 수행되지 않습니다. 그러나 UcsAllowed만 설정한다고 해서 사용자 연락처가 통합 연락처 저장소에서 Lync Server로 다시 이동되지는 않습니다. 이러한 이동을 수행하려면 먼저 통합 연락처 저장소 사용을 허용하지 않는 사용자 서비스 정책을 사용자에게 할당해야 합니다. 그 후에는 **Invoke-UcsRollback** cmdlet을 사용하여 연락처를 통합 연락처 저장소에서 Lync Server로 다시 "수동으로" 마이그레이션해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsUserServicesPolicy"}

**Lync Server 제어판:** **Get-CsUserServicesPolicy** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>검색할 정책을 지정할 때 와일드카드를 사용할 수 있습니다. 예를 들어 다음 구문은 사이트 범위에서 구성된 모든 정책을 반환합니다.</p>
<p>-Filter &quot;site:*&quot;</p>
<p>다음 구문은 사용자별 범위에서 구성된 모든 정책을 반환합니다.</p>
<p>-Filter &quot;tag:*&quot;</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 정책의 고유 식별자입니다. 전역 정책을 반환하려면 다음 구문을 사용합니다.</p>
<p>-Identity global</p>
<p>사이트 범위에서 구성된 정책을 반환하려면 -Identity &quot;site:Redmond&quot; 형태의 구문을 사용합니다.</p>
<p>서비스 범위에서 구성된 정책을 반환하려면 -Identity &quot;UserServer:atl-cs-001.litwareinc.com&quot; 형태의 구문을 사용합니다.</p>
<p></p>
<p>사용자 서비스 정책을 호스트할 수 있는 서비스는 UserServer 서비스뿐입니다.</p>
<p></p>
<p>사용자별 범위에서 정책이 구성될 수도 있습니다. 이러한 정책 중 하나를 반환하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;RedmondUserServicesPolicy&quot;</p>
<p>이 매개 변수를 포함하지 않으면 조직에서 사용하도록 구성된 모든 사용자 서비스 정책이 반환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 사용자 서비스 정책 데이터를 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>사용하는 경우 지정된 비즈니스용 Skype Online 테넌트에 대한 사용자 서비스 정책을 검색합니다. 예를 들면 다음과 같습니다.</p>
<p>-Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>Tenant 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용해서는 안 됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsUserServicesPolicy** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsUserServicesPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.UsersServices.UserServicesPolicy 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Grant-CsUserServicesPolicy](grant-csuserservicespolicy.md)  
[New-CsUserServicesPolicy](new-csuserservicespolicy.md)  
[Remove-CsUserServicesPolicy](remove-csuserservicespolicy.md)  
[Set-CsUserServicesPolicy](set-csuserservicespolicy.md)

