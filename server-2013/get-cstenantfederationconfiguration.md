---
title: Get-CsTenantFederationConfiguration
TOCTitle: Get-CsTenantFederationConfiguration
ms:assetid: e5f836d0-6066-4c23-9594-6e3f1cbd39ef
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994072(v=OCS.15)
ms:contentKeyID: 52056980
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTenantFederationConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Microsoft Lync Online 테넌트의 페더레이션 구성 설정에 대한 정보를 반환합니다. 페더레이션 구성 설정은 사용자가 통신할 수 있도록 허용된 도메인(있는 경우)을 결정하는 데 사용됩니다.

**Get-CsTenantFederationConfiguration** cmdlet은 비즈니스용 Skype Online에서만 사용할 수 있습니다.

## 구문

    Get-CsTenantFederationConfiguration [[-Identity] <XdsIdentity>] [-Tenant <Nullable`1>] [-LocalStore] [-Verbose] Get-CsTenantFederationConfiguration [-Tenant <Nullable`1>] [-Filter <String>] [-LocalStore] [-Verbose]

## 예제

## 예제 1

예제 1에 표시된 명령은 테넌트 ID가 "bf19b7db-6960-41e5-a139-2aa373474354"인 테넌트의 페더레이션 구성 정보를 반환합니다. 테넌트 ID는 다음과 비슷한 명령을 사용하여 검색할 수 있습니다.

Get-CsTenant | Select-Object TenantID

    Get-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354"

Tenant 매개 변수는 선택 사항입니다. 다음 구문을 사용하여 Get-CsTenantFederationConfiguration을 호출할 수도 있습니다.

    Get-CsTenantFederationConfiguration

## 예제 2

예제 2에서는 bf19b7db-6960-41e5-a139-2aa373474354 테넌트에 대한 페더레이션 허용 목록에서 검색된 모든 도메인에 대한 정보가 반환됩니다. 허용 목록은 테넌트가 페더레이션하도록 허용된 모든 도메인을 나타냅니다. 이를 수행하기 위해 이 명령은 먼저 **Get-CsTenantFederationConfiguration** cmdlet을 호출하여 지정된 도메인에 대한 페더레이션 정보를 반환합니다. 그러면 해당 정보가 ExpandProperty를 사용해 AllowedList 속성을 "확장"하는 **Select-Object** cmdlet에 파이프됩니다. 속성을 확장한다는 것은 간단히 말해 해당 속성 화면에 저장된 모든 정보를 읽기 쉬운 형식으로 표시하는 것을 의미합니다.

    Get-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" | Select-Object -ExpandProperty AllowedList

## 예제 3

위 명령은 조직에서 현재 사용되고 있는 모든 테넌트에 대한 페더레이션 구성을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsTenant** cmdlet을 호출하여 사용 가능한 테넌트 컬렉션을 반환합니다. 그런 다음 해당 컬렉션은 **ForEach-Object** cmdlet에 파이프됩니다. ForEach-Object는 컬렉션의 각 테넌트 ID를 가져와 **Get-CsTenantFederationConfiguration** cmdlet을 실행하고, 테넌트 ID를 나타내기 위해 속성 값 TenantID(**Get-CsTenant** cmdlet에서 반환됨)를 사용합니다.

    Get-CsTenant | ForEach-Object {Get-CsTenantFederationConfiguration -Tenant $_.TenantId}

## 예제 4

예제 4에서는 공용 사용자와 페더레이션이 허용되지 않는 테넌트에 대해서만 페더레이션 구성 정보가 반환됩니다. 이를 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsTenant** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 테넌트 컬렉션을 반환합니다. 해당 컬렉션은 **ForEach-Object** cmdlet에 파이프됩니다. 이 cmdlet은 컬렉션의 각 테넌트를 가져와 **Get-CsTenantFederationConfiguration** cmdlet을 사용하여 페더레이션 구성 정보를 반환합니다. 그런 다음 페더레이션 구성 정보의 전체 집합이 **Where-Object** cmdlet에 파이프되며, 이 cmdlet은 AllowPublicUsers 속성이 $False와 같은(-eq) 테넌트만 선택합니다.

    Get-CsTenant | Select-Object TenantId | ForEach-Object {Get-CsTenantFederationConfiguration -Tenant $_.TenantId} | Where-Object {$_.AllowPublicUsers -eq $False}

## 자세한 정보

페더레이션은 사용자가 다른 도메인의 사용자와 메신저 및 현재 상태 정보를 교환할 수 있도록 하는 서비스입니다. Lync Online에서는 관리자가 페더레이션 구성 설정을 사용하여 다음을 제어할 수 있습니다.

  - 사용자가 다른 도메인의 사용자와 통신할 수 있는지 여부와 통신이 가능한 경우 통신하도록 허용된 도메인

  - 사용자가 공용 메신저 및 현재 상태 공급자(Windows Live, AOL, Yahoo)의 계정이 있는 사용자와 통신할 수 있는지 여부

**Get-CsTenantFederationConfiguration** cmdlet을 통해 관리자는 해당 Lync Online 테넌트에 대한 페더레이션 정보를 반환할 수 있습니다. 이 cmdlet은 사용자가 통신 가능한/불가능한 도메인을 지정하는 데 사용되는 허용 목록과 차단된 목록을 검토하는 데에도 사용할 수 있습니다. 하지만 사용자가 통신하도록 허용된 공용 메신저 및 현재 상태 공급자를 확인하려는 경우 관리자는 **Get-CsTenantPublicProvider** cmdlet을 사용해야 합니다.

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
<td><p>테넌트 페더레이션 구성 설정 컬렉션을 반환하기 위해 와일드카드 문자를 사용할 수 있도록 합니다. 각 테넌트가 페더레이션 구성 설정의 단일 전역 컬렉션으로 제한되므로 Filter 매개 변수를 사용할 필요가 없습니다. 하지만 <strong>Get-CsTenantFederationConfiguration</strong> cmdlet에 다음과 같은 구문을 사용할 수는 있습니다.</p>
<p>Get-CsTenantFederationConfiguration –Tenant &quot;bf19b7db-6960-41e5-a139-2aa373474354&quot; –Filter &quot;g*&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환될 테넌트 페더레이션 구성 설정 컬렉션을 지정합니다. 각 테넌트가 페더레이션 설정의 단일 전역 컬렉션으로 제한되므로 <strong>Get-CsTenantFederationConfiguration</strong> cmdlet을 호출할 때 이 매개 변수를 포함할 필요가 없습니다. Identity 매개 변수를 사용하도록 선택할 경우 Tenant 매개 변수도 포함해야 합니다. 예를 들면 다음과 같습니다.</p>
<p>Get-CsTenantFederationConfiguration -Tenant &quot;bf19b7db-6960-41e5-a139-2aa373474354&quot; –Identity &quot;global&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 테넌트 페더레이션 구성 데이터를 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>페더레이션 설정이 반환되는 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Windows PowerShell 원격 세션을 사용 중이며 비즈니스용 Skype Online에만 연결되어 있는 경우에는 Tenant 매개 변수를 포함하지 않아도 됩니다. 대신, 연결 정보를 기반으로 테넌트 ID가 자동으로 채워집니다. Tenant 매개 변수는 하이브리드 배포에서 주로 사용됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsTenantFederationConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsTenantFederationConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.TenantFederationSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)

