---
title: New-CsEdgeAllowAllKnownDomains
TOCTitle: New-CsEdgeAllowAllKnownDomains
ms:assetid: f9416909-c328-41b3-9215-7ebd091b0ca0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994088(v=OCS.15)
ms:contentKeyID: 52057000
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsEdgeAllowAllKnownDomains

 

_**마지막으로 수정된 항목:** 2015-03-09_

차단된 도메인 목록에 포함된 도메인을 제외한 모든 도메인과 Microsoft Lync Online 페더레이션을 설정합니다.

이 cmdlet은 비즈니스용 Skype Online에서만 사용할 수 있습니다.

## 구문

    New-CsEdgeAllowAllKnownDomains [-Verbose]

## 예제

## 예제 1

예제 1에 표시된 두 개의 명령은 모든 알려진 도메인을 허용하도록 ID가 "bf19b7db-6960-41e5-a139-2aa373474354"인 테넌트의 페더레이션 설정을 구성합니다. 이를 수행하기 위해 예제의 첫 번째 명령은 **New-CsEdgeAllowAllKnownDomains** cmdlet을 사용하여 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.AllowAllKnownDomains 개체의 인스턴스를 만듭니다. 이 인스턴스는 $x라는 변수에 저장됩니다. 두 번째 명령에서는 **Set-CsTenantFederationConfiguration** cmdlet이 AllowedDomains 매개 변수와 함께 호출되며, 이 매개 변수에는 모든 알려진 도메인을 허용하도록 페더레이션 설정을 구성하는 매개 변수 값으로 $x가 사용됩니다.

    $x = New-CsEdgeAllowAllKnownDomains
    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $x

## 예제 2

예제 2에서는 차단된 도메인 목록에 명시적으로 표시되지 않는 모든 도메인과 통신할 수 있도록 모든 테넌트를 구성하는 방법을 보여 줍니다. 이를 수행하기 위해 예제의 첫 번째 명령은 **New-CsEdgeAllowAllKnownDomains** cmdlet을 사용하여 AllowAllKnownDomains 개체의 인스턴스를 만듭니다. 이 개체는 $x라는 변수에 저장됩니다.

그런 다음 예제의 두 번째 명령은 **Get-CsTenant** cmdlet을 사용하여 사용 가능한 모든 테넌트 컬렉션을 반환합니다. 그런 다음 이 컬렉션은 **ForEach-Object** cmdlet에 파이프됩니다. 따라서 **ForEach-Object** cmdlet은 컬렉션의 각 테넌트에 대해 **Set-CsTenantFederationConfiguration** cmdlet을 실행하며, 모든 알려진 도메인을 허용하도록 AllowedDomains 속성을 구성합니다.

    $x = New-CsEdgeAllowAllKnownDomains
    Get-CsTenant | ForEach-Object {Set-CsTenantFederationConfiguration -Tenant $_.TenantID -AllowedDomains $x}

## 자세한 정보

페더레이션은 사용자가 다른 도메인의 사용자와 메신저 및 현재 상태 정보를 교환할 수 있도록 하는 서비스입니다. Lync Online에서는 관리자가 페더레이션 구성 설정을 사용하여 다음을 제어할 수 있습니다.

  - 사용자가 다른 도메인의 사용자와 통신할 수 있는지 여부와 통신이 가능한 경우 통신하도록 허용된 도메인

  - 사용자가 공용 메신저 및 현재 상태 공급자(Windows Live, AOL, Yahoo)의 계정이 있는 사용자와 통신할 수 있는지 여부

페더레이션은 허용 도메인 및 차단된 도메인 목록을 사용하여 부분적으로 관리됩니다. 허용 도메인 목록은 사용자가 통신하도록 허용된 도메인을 지정하고 차단된 도메인 목록은 사용자가 통신하도록 허용되지 않은 도메인을 지정합니다. 기본적으로 사용자는 차단된 목록에 표시되지 않은 모든 도메인과 통신할 수 있습니다. 하지만 관리자는 이 기본 설정을 수정하여 허용 도메인 목록에 있는 도메인하고만 통신할 수 있도록 제한할 수 있습니다.

Lync Online에서는 사용자가 허용 목록이나 차단된 목록을 직접 수정할 수 있도록 허용되지 않습니다. 예를 들어 도메인 이름을 나타내는 문자열 값을 허용 도메인 목록으로 전달하는 다음과 유사한 명령은 사용할 수 없습니다.

    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains "fabrikam.com"

대신 **New-CsEdgeAllowAllKnownDomains** cmdlet 또는 **New-CsEdgeAllowList** cmdlet을 사용하여 도메인 개체를 만들고 해당 도메인 개체를 **Set-CsTenantFederationConfiguration** cmdlet에 전달해야 합니다. **New-CsEdgeAllowAllKnownDomains** cmdlet은 사용자가 차단된 도메인 목록에 명시적으로 지정된 도메인 이외의 모든 도메인과 통신할 수 있도록 허용하려는 경우에 사용합니다. N**ew-CsEdgeAllowList** cmdlet은 사용자가 지정된 도메인 컬렉션과 통신할 수 없도록 제한하려는 경우에 사용합니다. 이 경우 사용자는 허용 도메인 목록에 표시된 도메인하고만 통신하도록 허용됩니다.

모든 알려진 도메인과의 페더레이션을 구성하려면 다음과 유사한 명령 집합을 사용합니다.

    $x = New-CsEdgeAllowAllKnownDomains
    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $x

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
<td><p>이 cmdlet은 일반 Windows PowerShell 매개 변수만 제공합니다.</p></td>
<td><p>해당 없음</p></td>
<td><p>해당 없음</p></td>
<td><p>해당 없음</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsEdgeAllowAllKnownDomains** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsEdgeAllowAllKnownDomains** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.AllowAllKnownDomains 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsEdgeAllowList](new-csedgeallowlist.md)  
[New-CsEdgeDomainPattern](new-csedgedomainpattern.md)  
[Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)

