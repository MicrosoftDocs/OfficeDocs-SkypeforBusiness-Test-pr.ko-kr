---
title: Get-CsTenant
TOCTitle: Get-CsTenant
ms:assetid: 7b642117-5ca7-4a5b-bca7-16b0ae694ae2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994044(v=OCS.15)
ms:contentKeyID: 52056877
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTenant

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 비즈니스용 Skype Online 테넌트에 대한 정보를 반환합니다. 테넌트는 온라인 사용자 그룹을 나타냅니다. 대부분의 경우에는 단일 테넌트만 필요합니다. 그러나 다른 관리 요구 사항이 있는 여러 사용자 그룹이 있는 경우 비즈니스용 Skype Online에서는 여러 테넌트가 있는 단일 조직에 대한 지원을 제공합니다.

Get-CsTenant는 비즈니스용 Skype Online에서만 사용할 수 있습니다.

## 구문

    Get-CsTenant [[-Identity] <OUIdParameter>] [-Filter <String>] [-ResultSize <Unlimited`1>] [-Verbose]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 테넌트에 대한 정보를 반환합니다.

    Get-CsTenant

## 예제 2

예제 2에서는 ID가 "bf19b7db-6960-41e5-a139-2aa373474354"인 단일 테넌트에 대한 정보가 반환됩니다.

    Get-CsTenant -Identity "bf19b7db-6960-41e5-a139-2aa373474354"

## 예제 3

위 명령은 단일 테넌트에 대한 정보를 반환하는 다른 방법을 보여줍니다. 이 예에서는 Filter 매개 변수와 필터 값 {DisplayName –eq "Fabrikam"}을 포함하여 수행했습니다. 해당 구문은 표시 이름이 Fabrikam인 테넌트에 대한 정보만 반환합니다.

    Get-CsTenant -Filter {DisplayName -eq "Fabrikam"}

## 예제 4

예제 4에 표시된 명령은 ServiceInstance가 "LitwareincCommunicationsOnline/San Antonio"인 모든 테넌트에 대한 정보를 반환합니다. 이를 수행하기 위해 명령에 Filter 매개 변수와 필터 값 {ServiceInstance -eq "LitwareincCommunicationsOnline/San Antonio"}가 포함되어 있습니다. 해당 필터 값은 반환되는 데이터를 ServiceInstance 속성이 "LitwareincCommunicationsOnline/San Antonio"와 같은(-eq) 테넌트로 제한합니다.

    Get-CsTenant -Filter {ServiceInstance -eq "LitwareincCommunicationsOnline/San Antonio"}

## 예제 5

예제 5는 국가 또는 지역 표시 이름이 Australia인 모든 테넌트에 대한 정보를 반환합니다. 이 명령은 Filter 매개 변수와 매개 변수 값 {CountryOrRegionDisplayName -eq "Australia"}를 사용하여 수행했습니다.

    Get-CsTenant -Filter {CountryOrRegionDisplayName -eq "Australia"}

## 자세한 정보

비즈니스용 Skype Online에서 테넌트는 해당 서비스에 속한 계정을 가진 사용자의 그룹을 나타냅니다. 대부분의 조직은 모든 사용자 계정을 포함하는 하나의 테넌트만 필요하지만, 테넌트 단위로 비즈니스용 Skype Online 관리가 수행되는 경우도 있습니다. 즉, 동일한 테넌트의 모든 사용자는 동일한 음성 정책, 동일한 페더레이션 구성 설정 등을 갖습니다. 일부 사용자를 각각 다른 방식으로 관리해야 하는 경우 각각 고유한 정책 및 설정 컬렉션을 가진 여러 테넌트를 사용할 수 있습니다.

소유한 테넌트 수에 관계없이 **Get-CsTenant** cmdlet을 사용하여 이러한 테넌트에 대한 정보를 반환할 수 있습니다.

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
<td><p>사용자가 전체 Active Directory 고유 이름을 지정할 필요 없이 Active Directory 특성을 사용하여 데이터를 반환할 수 있도록 합니다. 예를 들어 테넌트 표시 이름을 사용하여 테넌트를 검색하려면 다음과 유사한 구문을 사용합니다.</p>
<p>Get-CsTenant –Filter {DisplayName –eq &quot;FabrikamTenant&quot;}</p>
<p>Fabrikam 도메인을 사용하는 모든 테넌트를 반환하려면 다음 구문을 사용합니다.</p>
<p>Get-CsTenant –Filter {Domains –like &quot;*fabrikam*&quot;}</p>
<p>Filter 매개 변수는 Where-Object cmdlet에 사용되는 구문과 동일한 Windows PowerShell 필터링 구문을 사용합니다.</p>
<p>Identity 매개 변수와 Filter 매개 변수를 같은 명령에 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>테넌트의 Active Directory 고유 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;OU=bf19b7db-6960-41e5-a139-2aa373474354,OU=OCS Tenants,dc=litwareinc,dc=com&quot;</p>
<p>Identity 또는 Filter 매개 변수 중 하나를 포함하지 않으면 <strong>Get-CsTenant</strong> cmdlet이 모든 테넌트에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited`1</p></td>
<td><p>cmdlet에서 반환되는 레코드 수를 제한하는 데 사용됩니다. 예를 들어 포리스트에 있는 테넌트 수에 상관없이 7개의 테넌트를 반환하려면 ResultSize 매개 변수를 포함하고 매개 변수 값을 7로 설정합니다. 반환될 7명의 사용자를 지정하는 방법은 없습니다.</p>
<p>결과 크기는 0에서 2147483647(포함) 사이의 임의 정수로 설정할 수 있습니다. 0으로 설정할 경우 명령이 실행되지만 데이터가 반환되지 않습니다. 테넌트를 7로 설정했지만 포리스트에 대화 상대가 3명만 있는 경우 명령을 통해 이 3개의 테넌트가 반환된 다음 오류 없이 완료됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Get-CsTenant** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.TenantObject 개체의 파이프라인된 인스턴스뿐 아니라 비즈니스용 Skype Online 테넌트의 ID(예: "OU=bf19b7db-6960-41e5-a139-2aa373474354,OU=OCS Tenants,dc=vdomain,dc=com")를 나타내는 문자열 값도 허용합니다.

## 반환 형식

**Get-CsTenant** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.TenantObject 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsOnlineUser](get-csonlineuser.md)

