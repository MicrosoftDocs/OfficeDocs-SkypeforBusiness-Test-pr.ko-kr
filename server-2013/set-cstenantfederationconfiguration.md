---
title: Set-CsTenantFederationConfiguration
TOCTitle: Set-CsTenantFederationConfiguration
ms:assetid: e13c2f55-7a68-4174-a0da-5eec8c65f64c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994080(v=OCS.15)
ms:contentKeyID: 52056973
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsTenantFederationConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Microsoft Lync Online 테넌트에 대한 페더레이션 구성 설정을 관리합니다. 이 설정은 사용자가 통신할 수 있는 도메인(있는 경우)을 결정하는 데 사용됩니다.

**Set-CsTenantFederationConfiguration** cmdlet은 비즈니스용 Skype Online에서만 사용할 수 있습니다.

## 구문

    Set-CsTenantFederationConfiguration [[-Identity] <XdsIdentity>] [-Tenant <Nullable`1>] [-AllowedDomains <IAllowedDomainsChoice>] [-BlockedDomains <PSListModifier>] [-AllowFederatedUsers] [-AllowPublicUsers] [-SharedSipAddressSpace] [-Force] [-Verbose] [-WhatIf] [-Confirm]Set-CsTenantFederationConfiguration [-Tenant <Nullable`1>] [-AllowedDomains <IAllowedDomainsChoice>] [-BlockedDomains <PSListModifier>] [-AllowFederatedUsers] [-AllowPublicUsers] [-SharedSipAddressSpace] [-Instance <PSObject>] [-Force] [-Verbose] [-WhatIf] [-Confirm]

## 예제

## 예제 1

예제 1에 나와 있는 명령은 TenantId가 "bf19b7db-6960-41e5-a139-2aa373474354"인 테넌트에 대해 공용 공급자와 통신을 사용하지 않도록 설정합니다.

    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowPublicUsers $False

Tenant 매개 변수는 선택 사항입니다. 해당 매개 변수를 제외하면 Windows PowerShell이 연결 정보에 따라 올바른 테넌트 ID를 자동으로 삽입합니다.

## 예제 2

예제 2에는 조직의 모든 테넌트에 대해 공용 공급자 통신을 사용하지 않도록 설정하는 방법을 보여 줍니다. 이를 위해 명령은 먼저 **Get-CsTenant** cmdlet을 호출하여 사용 가능한 모든 테넌트 모음을 반환합니다. 그러면 해당 모음이 **Select-Object** cmdlet으로 파이프됩니다. 이 cmdlet은 모음에 있는 각 항목에 대한 TenantId 속성만 선택합니다. 그런 다음 해당 테넌트 ID 모음이 **ForEach-Object** cmdlet으로 파이프됩니다. F**orEach-Object** cmdlet은 각 테넌트 ID를 가져와 해당 ID에 대해 **Set-CsTenantFederationConfiguration** cmdlet을 실행하고 각 테넌트에 대한 AllowPublicUsers 속성을 False($False)로 설정합니다.

    Get-CsTenant | Select-Object TenantId | ForEach-Object {Set-CsTenantFederationConfiguration -Tenant $_.TenantId -AllowPublicUsers $False}

## 예제 3

예제 3에서 도메인 fabrikam.com은 TenantId가 "bf19b7db-6960-41e5-a139-2aa373474354"인 테넌트에 대한 차단 도메인 목록의 유일한 도메인으로 할당됩니다. 이를 위해 예제의 첫 번째 명령은 **New-CsEdgeDomainPattern** cmdlet을 사용하여 fabrikam.com에 대한 새 도메인 개체를 만듭니다. 이 도메인 개체는 $x라는 이름의 변수에 저장됩니다.

그 다음 예제의 두 번째 명령이 **Set-CsTenantFederationConfiguration** cmdlet을 사용하여 차단된 도메인 목록을 업데이트합니다. Replace 메서드를 사용하면 기존 차단 도메인 목록이 새 목록(fabrikam.com 도메인만 포함된 목록)으로 바뀝니다.

    $x = New-CsEdgeDomainPattern "fabrikam.com"
    Set-CsTenantFederationConfiguration -Tenant bf19b7db-6960-41e5-a139-2aa373474354 -BlockedDomains @{Replace=$x}

## 예제 4

예제 4에 나와 있는 명령은 TenantID가 "bf19b7db-6960-41e5-a139-2aa373474354"인 테넌트의 차단 도메인 목록에서 fabrikam.com을 제거합니다. 이를 위해 예제의 첫 번째 명령은 **New-CsEdgeDomainPattern** cmdlet을 사용하여 fabrikam.com에 대한 도메인 개체를 만듭니다. 그 결과 만들어진 도메인 개체가 $x라는 이름의 변수에 저장됩니다.

다음으로 예제의 두 번째 명령이 **Set-CsTenantFederationConfiguration** cmdlet 및 Remove 메서드를 사용하여 지정된 테넌트에 대한 차단 도메인 목록에서 fabrikam.com을 제거합니다.

    $x = New-CsEdgeDomainPattern "fabrikam.com"
    Set-CsTenantFederationConfiguration -Tenant bf19b7db-6960-41e5-a139-2aa373474354 -BlockedDomains @{Remove=$x}

## 예제 5

예제 5에 나와 있는 명령은 도메인 fabrikam.com을 TenantId가 "bf19b7db-6960-41e5-a139-2aa373474354"인 테넌트의 차단 도메인 목록에 추가합니다. 새 차단 도메인을 추가하기 위해 예제의 첫 번째 명령은 **New-CsEdgeDomainPattern** cmdlet을 사용하여 fabrikam.com에 대한 도메인 개체를 만듭니다. 이 개체는 $x라는 이름의 변수에 저장됩니다.

도메인 개체를 만든 후에 두 번째 명령은 **Set-CsTenantFederationConfiguration** cmdlet 및 Add 메서드 사용하여 차단 도메인 목록에 이미 존재하는 도메인에 fabrikam.com을 추가합니다.

    $x = New-CsEdgeDomainPattern "fabrikam.com"
    Set-CsTenantFederationConfiguration -Tenant bf19b7db-6960-41e5-a139-2aa373474354 -BlockedDomains @{Add=$x}

## 예제 6

예제 6에는 지정된 테넌트의 차단 도메인 목록에 할당된 모든 도메인을 제거하는 방법을 보여 줍니다. 이렇게 하려면 BlockedDomains 매개 변수를 포함하고 매개 변수 값을 null($Null)로 설정하면 됩니다. 이 명령이 완료되면TenantID가 "bf19b7db-6960-41e5-a139-2aa373474354"인 테넌트의 차단 도메인 목록이 지워집니다.

    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -BlockedDomains $Null

## 자세한 정보

페더레이션은 사용자가 다른 도메인의 사용자와 메신저 대화 및 현재 상태 정보를 주고받을 수 있도록 하는 서비스입니다. Lync Online에서 관리자는 페더레이션 설정을 사용하여 다음을 제어할 수 있습니다.

  -   
    사용자가 다른 도메인의 사용자와 통신할 수 있는지 여부(및 가능한 경우 통신할 수 있는 도메인)

  -   
    사용자가 Windows Live, AOL, Yahoo 등의 공용 메신저 및 현재 상태 공급자에 계정이 있는 사용자와 통신할 수 있는지 여부

관리자는 **Set-CsTenantFederationConfiguration** cmdlet을 사용하여 다른 도메인 및 공용 공급자와의 페더레이션을 설정하거나 해제할 수 있습니다. 또한 이 cmdlet을 사용하여 사용자가 통신할 수 있는 도메인 및/또는 사용자가 통신할 수 없는 도메인을 명시적으로 나타낼 수 있습니다. 그러나 사용자가 통신하거나 통신할 수 없는 공용 메신저 및 현재 상태 공급자를 나타내기 위해서는 관리자가 **Set-CsTenantPublicProvider** cmdlet을 사용해야 합니다.

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
<td><p><em>AllowedDomains</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Edge.IAllowedDomainsChoice</p></td>
<td><p><strong>New-CsEdgeAllowList</strong> cmdlet 또는 <strong>New-CsEdgeAllowAllKnownDomains</strong> cmdlet을 사용하여 만든 도메인 개체로, 사용자가 통신할 수 있는 도메인을 나타냅니다. <strong>New-CsEdgeAllowAllKnownDomains</strong> cmdlet이 사용된 경우 사용자는 차단 도메인 목록에 나타나지 않은 도메인과 통신할 수 있습니다. <strong>New-CsEdgeAllowList</strong> cmdlet이 사용된 경우 사용자는 허용 도메인 목록에 추가된 도메인을 상대로만 통신할 수 있습니다.</p>
<p>AllowedDomains 매개 변수에 문자열 값을 직접 전달할 수 없습니다. 대신 <strong>New-CsEdgeAllowList</strong> cmdlet 또는 <strong>New-CsEdgeAllowAllKnownDomains</strong> cmdlet을 사용하여 개체 참조를 만든 다음 개체 참조 변수를 매개 변수 값으로 사용해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowFederatedUsers</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 사용자가 다른 도메인의 사용자와 잠재적으로 통신할 수 있습니다. 이 속성을 False로 설정하면 사용자가 AllowedDomains 및 BlockedDomains 속성에 지정된 값에 상관없이 다른 도메인의 사용자와 통신할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowPublicUsers</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 사용자가 Windows Live, Yahoo, AOL 등의 공용 메신저 및 현재 상태 공급자에 계정이 있는 사용자와 잠재적으로 통신할 수 있습니다. 사용자가 실제로 통신할 수 있는 공용 공급자의 모음은 Set-CsTenantPublicProvider cmdlet을 사용하여 관리할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>BlockedDomains</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>AllowedDomains 속성이 AllowAllKnownDomains로 설정되면 사용자가 차단 도메인 목록에 나타나는 도메인을 제외한 모든 도메인의 사용자와 통신할 수 있습니다. AllowedDomains 속성이 AllowAllKnownDomains로 설정되면 차단 목록이 무시되고 사용자가 허용 도메인 목록에 명시적으로 추가된 도메인을 상대로만 통신할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 테넌트 페더레이션 구성 설정의 모음을 지정합니다. 각 테넌트는 페더레이션 설정의 전역 모음 하나로 제한되기 때문에 <strong>Set-CsTenantFederationConfiguration</strong> cmdlet을 호출할 때 이 매개 변수를 포함할 필요가 없습니다. Identity 매개 변수를 사용하도록 선택한 경우 Tenant 매개 변수도 포함해야 합니다. 예를 들면 다음과 같습니다.</p>
<p>Set-CsTenantFederationConfiguration -Tenant &quot;bf19b7db-6960-41e5-a139-2aa373474354&quot; –Identity &quot;global&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SharedSipAddressSpace</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정되면 Lync Online에 속한 사용자가 온-프레미스 버전의 Lync Server에 속한 사용자와 같은 SIP 도메인을 사용한다는 뜻입니다. 기본값은 False로, 사용자의 두 집합이 각각 다른 SIP 도메인을 사용하는 것을 의미합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>페더레이션 설정을 수정 중인 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>-Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대한 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Windows PowerShell의 원격 세션을 사용 중이고 비즈니스용 Skype Online에만 연결되는 경우 Tenant 매개 변수를 포함하지 않아도 됩니다. 대신, 연결 정보에 따라 테넌트 ID가 자동으로 채워집니다. Tenant 매개 변수는 하이브리드 배포에서 주로 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Set-CsTenantFederationConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.TenantFederationSettings 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsTenantFederationConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.TenantFederationSettings 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsTenantFederationConfiguration](get-cstenantfederationconfiguration.md)

