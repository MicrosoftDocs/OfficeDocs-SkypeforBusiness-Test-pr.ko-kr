---
title: New-CsEdgeAllowList
TOCTitle: New-CsEdgeAllowList
ms:assetid: 21a6d546-9e03-485c-b7ec-9deb778f2b01
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994023(v=OCS.15)
ms:contentKeyID: 52056804
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsEdgeAllowList

 

_**마지막으로 수정된 항목:** 2015-03-09_

관리자가 도메인을 지정하여 사용자가 통신할 수 있는 도메인을 지정할 수 있도록 합니다. Microsoft Lync Online에서만 사용할 수 있는 **New-CsEdgeAllowList** cmdlet은 **New-CsEdgeDomainPattern** cmdlet 및 **Set-CsTenantFederationConfiguration** cmdlet과 함께 사용해야 합니다.

## 구문

    New-CsEdgeAllowList [-AllowedDomain <PSListModifier>] [-Verbose]

## 예제

## 예제 1

예제 1에 나오는 명령은 fabrikam.com 도메인을 TenantId가 "bf19b7db-6960-41e5-a139-2aa373474354"인 테넌트에 대한 허용 도메인 목록에 할당합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsEdgeDomainPattern** cmdlet을 사용하여 fabrikam.com에 대한 도매인 개체를 만듭니다. 이 개체는 $x 변수에 저장됩니다. 도메인 개체를 만든 후에는 **New-CsEdgeAllowList** cmdlet을 사용하여 fabrikam.com 도메인만 포함하는 새 허용 목록을 만듭니다.

허용 도메인 목록이 만들어진 다음 예제의 마지막 명령은 **Set-CsTenantFederationConfiguration** cmdlet을 사용하여 fabrikam.com을 지정된 테넌트의 허용 도메인 목록에 대한 유일한 도메인으로 구성할 수 있습니다.

    $x = New-CsEdgeDomainPattern -Domain "fabrikam.com"
    $newAllowList = New-CsEdgeAllowList -AllowedDomain $x
    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $newAllowList

Tenant 매개 변수는 하이브리드 배포에서만 필요합니다. 비즈니스용 Skype Online에만 연결된 경우 Tenant 매개 변수는 생략해도 됩니다.

## 예제 2

예제 2에서는 허용 도메인 목록에 여러 도메인을 추가하는 방법을 보여줍니다. 이 작업을 수행하기 위해 **New-CsEdgeDomainPattern** cmdlet을 여러 번(각 도메인당 하나가 목록에 추가되어야 함) 호출하고 생성되는 도메인 개체를 별도의 변수에 저장합니다. 그런 다음 **New-CsEdgeAllowList** cmdlet으로 만든 허용 목록에 각각의 해당 변수를 추가할 수 있는데 허용 목록을 만들 때는 AllowedDomain 매개 변수를 사용하고 변수 이름을 쉼표로 구분하기만 하면 됩니다.

$newAllowList = New-CsEdgeAllowList -AllowedDomain $x,$y

    $x = New-CsEdgeDomainPattern -Domain "contoso.com"
    $y = New-CsEdgeDomainPattern -Domain "fabrikam.com"
    $newAllowList = New-CsEdgeAllowList -AllowedDomain $x,$y
    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $newAllowList

## 예제 3

예제 3에서는 모든 도메인을 허용 도메인 목록에서 제거합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsEdgeAllowList** cmdlet을 사용하여 허용 도메인의 새 목록을 만듭니다. 그러려면 AllowedDomain 속성을 null 값($Null)으로 설정해야 합니다. 그런 다음 생성되는 개체 참조($newAllowList)가 **Set-CsTenantFederationConfiguration** cmdlet과 함께 사용되어 모든 도메인을 TenantId가 "bf19b7db-6960-41e5-a139-2aa373474354"인 테넌트에 대한 허용 도메인 목록에서 제거합니다.

    $newAllowList = New-CsEdgeAllowList -AllowedDomain $Null
    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $newAllowList

## 자세한 정보

페더레이션은 사용자가 다른 도메인의 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있는 서비스입니다. 관리자는 Lync Online을 사용하여 다음 항목을 관리하는 페더레이션 구성 설정을 사용할 수 있습니다.

  - 사용자가 다른 도메인의 사용자와 통신할 수 있는지 여부 및 통신할 수 있는 경우 통신이 허용되는 도메인의 종류

  - 사용자가 Windows Live, AOL, Yahoo 등의 공용 메신저 및 현재 상태 공급자 계정을 보유한 다른 사용자와 통신할 수 있는지 여부

페더레이션은 허용 도메인 및 차단된 도메인 목록을 사용하여 어느 정도 관리됩니다. 허용 도메인 목록은 사용자가 통신할 수 있도록 허용되는 도메인을 지정합니다. 차단된 도메인 목록은 사용자가 통신할 수 있도록 허용되지 않는 도메인을 지정합니다. 기본적으로 사용자는 차단된 목록에 표시되지 않는 모든 도메인과 통신할 수 있습니다. 하지만 관리자가 이러한 기본 설정을 수정하고 허용 도메인 목록에 있는 도메인과의 통신을 제한할 수 있습니다.

Lync Online에서는 허용 목록 또는 차단 목록을 직접 수정할 수 없습니다. 예를 들어 도메인 이름을 나타내는 문자열 값을 허용 도메인 목록에 전달하는, 다음과 비슷한 명령을 사용할 수 없습니다.

    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains "fabrikam.com"

대신 **New-CsEdgeAllowAllKnownDomains** cmdlet 또는 **New-CsEdgeAllowList** cmdlet을 사용하여 도메인 개체를 만든 다음 해당 도메인 개체를 **Set-CsTenantFederationConfiguration** cmdlet에 전달해야 합니다. 차단된 도메인 목록에 명시적으로 지정된 도메인을 제외하고 사용자가 모든 도메인과 통신할 수 있도록 허용하려면 **New-CsEdgeAllowAllKnownDomains** cmdlet을 사용합니다. 사용자 통신을 지정된 도메인 컬렉션으로 제한하려면 **New-CsEdgeAllowList** cmdlet을 사용합니다. 이 경우 사용자는 허용 도메인 목록에 표시된 도메인과만 통신할 수 있습니다.

단일 도메인(fabrikam.com)을 허용 도메인 목록에 추가하려면 다음과 같은 명령 집합을 사용해야 합니다.

    $x = New-CsEdgeDomainPattern -Domain "fabrikam.com"
    $newAllowList = New-CsEdgeAllowList -AllowedDomain $x
    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $newAllowList

이 명령의 실행이 완료되면 사용자는 fabrikam.com 도메인의 사용자와만 통신할 수 있습니다.

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
<td><p><em>AllowedDomain</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>새 도메인(또는 도메인 집합)에 대한 개체 참조가 허용 도메인 목록에 추가되어야 합니다. 도메인 개체 참조는 <strong>New-CsEdgeDomainPattern</strong> cmdlet을 사용하여 만들어야 합니다. 개체 참조를 쉼표로 구분하여 여러 도메인 개체를 추가할 수 있습니다. 예를 들면 다음과 같습니다.</p>
<p>-AllowedDomain $x,$y</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsEdgeAllowList** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsEdgeAllowList** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.AllowList 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsEdgeAllowAllKnownDomains](new-csedgeallowallknowndomains.md)  
[New-CsEdgeDomainPattern](new-csedgedomainpattern.md)  
[Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)

