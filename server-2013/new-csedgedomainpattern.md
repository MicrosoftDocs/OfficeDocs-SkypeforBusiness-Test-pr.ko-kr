---
title: New-CsEdgeDomainPattern
TOCTitle: New-CsEdgeDomainPattern
ms:assetid: 653bc148-c22b-4ad4-afdd-17aaeaa299d2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994040(v=OCS.15)
ms:contentKeyID: 52056870
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsEdgeDomainPattern

 

_**마지막으로 수정된 항목:** 2015-03-09_

페더레이션을 사용하도록 설정되거나 사용하지 않도록 설정된 도메인 집합에서 추가 또는 제거될 도메인을 지정하는 데 사용됩니다. 허용되거나 차단된 도메인 목록을 수정할 경우 **New-CsEdgeDomainPattern** cmdlet을 사용해야 합니다. 문자열 값(예: "fabrikam.com")은 이러한 목록을 관리하는 데 사용되는 cmdlet에 직접 전달될 수 없습니다.

**New-CsEdgeDomainPattern** cmdlet은 비즈니스용 Skype Online에서만 사용할 수 있습니다.

## 구문

    New-CsEdgeDomainPattern -Domain <String> [-Verbose]

## 예제

## 예제 1

예제 1에서는 지정된 테넌트에 대해 단일 도메인을 차단된 도메인 목록에 할당하는 방법을 보여줍니다. 이를 수행하기 위해 예제의 첫 번째 명령은 fabrikam.com 도메인에 대한 도메인 개체를 만듭니다. 이 작업은 **New-CsEdgeDomainPattern** cmdlet을 호출하고 결과 도메인 개체를 $x라는 변수에 저장하여 수행됩니다. 그런 다음 두 번째 명령은 **Set-CsTenantFederationConfiguration** cmdlet과 BlockedDomains 매개 변수를 사용하여 fabrikam.com을 TenantId가 "bf19b7db-6960-41e5-a139-2aa373474354"인 테넌트에 의해 차단된 유일한 도메인으로 구성합니다.

    $x = New-CsEdgeDomainPattern -Domain "fabrikam.com"
    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -BlockedDomains $x

## 자세한 정보

페더레이션은 사용자가 다른 도메인의 사용자와 메신저 및 현재 상태 정보를 교환할 수 있도록 하는 서비스입니다. 비즈니스용 Skype Online에서는 관리자가 페더레이션 구성 설정을 사용하여 다음을 제어할 수 있습니다.

  - 사용자가 다른 도메인의 사용자와 통신할 수 있는지 여부와 통신이 가능한 경우 통신하도록 허용된 도메인

  - 사용자가 공용 메신저 및 현재 상태 공급자(예: Windows Live, AOL, Yahoo)의 계정이 있는 사용자와 통신할 수 있는지 여부

페더레이션은 허용 도메인 및 차단된 도메인 목록을 사용하여 부분적으로 관리됩니다. 허용 도메인 목록은 사용자가 통신하도록 허용된 도메인을 지정하고 차단된 도메인 목록은 사용자가 통신하도록 허용되지 않은 도메인을 지정합니다. 기본적으로 사용자는 차단된 목록에 표시되지 않은 모든 도메인과 통신할 수 있습니다. 하지만 관리자는 이 기본 설정을 수정하여 허용 도메인 목록에 있는 도메인하고만 통신할 수 있도록 제한할 수 있습니다.

비즈니스용 Skype Online에서는 사용자가 허용 목록이나 차단된 목록을 직접 수정할 수 있도록 허용되지 않습니다. 예를 들어 도메인 이름을 나타내는 문자열 값을 차단된 도메인 목록으로 전달하는 다음과 유사한 명령은 사용할 수 없습니다.

    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -BlockedDomains "fabrikam.com"

대신, **New-CsEdgeDomainPattern** cmdlet을 사용하여 도메인 개체를 만들고 해당 도메인 개체를 변수(이 예제에서는 $x)에 저장한 다음 이 변수 이름을 차단된 도메인 목록으로 전달해야 합니다.

    $x = New-CsEdgeDomainPattern -Domain "fabrikam.com"
    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -BlockedDomains $x

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
<td><p><em>Domain</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>허용 목록에 추가할 도메인의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-Domain &quot;fabrikam.com&quot;</p>
<p>도메인 이름을 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsEdgeDomainPattern** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsEdgeDomainPattern** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DomainPattern 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsEdgeAllowAllKnownDomains](new-csedgeallowallknowndomains.md)  
[New-CsEdgeAllowList](new-csedgeallowlist.md)  
[Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)

