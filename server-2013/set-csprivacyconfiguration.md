---
title: Set-CsPrivacyConfiguration
TOCTitle: Set-CsPrivacyConfiguration
ms:assetid: 67fbd99a-0708-4e6f-8755-cb1a08d07ff3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398484(v=OCS.15)
ms:contentKeyID: 49303898
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsPrivacyConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

개인 정보 구성 설정의 기존 집합을 수정합니다. 개인 정보 구성 설정을 사용하면 사용자가 다른 사용자에게 공개할 수 있는 정보를 결정할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsPrivacyConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsPrivacyConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AutoInitiateContacts <$true | $false>] [-Confirm [<SwitchParameter>]] [-DisplayPublishedPhotoDefault <$true | $false>] [-EnablePrivacyMode <$true | $false>] [-Force <SwitchParameter>] [-PublishLocationDataDefault <$true | $false>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 site:Redmond인 개인 정보 구성 설정에 대한 3개 속성 값을 수정합니다. 수정되는 속성 값 3개는 AutoInitiateContacts, PublishLocationDataDefault 및 DisplayPublishedPhotoDefault입니다.

    Set-CsPrivacyConfiguration -Identity site:Redmond -EnablePrivacyMode $False -AutoInitiateContacts $True -PublishLocationDataDefault $True -DisplayPublishedPhotoDefault $True

## 예제 2

예제 2에서는 조직에서 현재 사용되고 있는 모든 개인 정보 구성 설정에 대한 개인 정보 모드를 활성화합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPrivacyConfiguration** cmdlet을 매개 변수 없이 호출하여 개인 정보 설정의 전체 컬렉션을 반환합니다. 그런 다음 이 컬렉션은 컬렉션의 각 항목을 가져오고 EnablePrivacyMode 속성을 True로 설정하는**Set-CsPrivacyConfiguration** cmdlet에 파이프됩니다.

    Get-CsPrivacyConfiguration | Set-CsPrivacyConfiguration -EnablePrivacyMode $True

## 예제 3

예제 3에서는 현재 개인 정보 모드를 사용하지 않는 모든 개인 정보 구성 설정을 수정합니다. 이 작업을 수행하기 위해 먼저 **Get-CsPrivacyConfiguration** cmdlet을 사용하여 모든 개인 정보 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 EnablePrivacyMode 속성이 False와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목에서 AutoInitiateContacts, PublishLocationDataDefault 및 DisplayPublishedPhotoDefault 속성에 값을 할당하는 **Set-CsPrivacyConfiguration** cmdlet에 파이프됩니다.

    Get-CsPrivacyConfiguration | Where-Object {$_.EnablePrivacyMode -eq $False} | Set-CsPrivacyConfiguration -AutoInitiateContacts $True -PublishLocationDataDefault $True -DisplayPublishedPhotoDefault $True

## 자세한 정보

Lync Server는 사용자에게 다른 사람들과 자신의 다양한 현재 상태 정보를 공유할 기회를 제공합니다. 사진을 게시하고, 자세한 위치 정보를 제공하고, 조직의 모든 사람들에게 자신의 현재 상태 정보를 자동으로 공개할 수 있습니다(연락처 목록에 있는 사람에게만 공개하는 것이 아님).

어떤 사용자는 이 정보를 동료들에게 공개하게 되는 것을 흔쾌히 받아들이지만 이 데이터를 공유하기를 꺼리는 사용자도 있을 수 있습니다. 예를 들어 현재 상태 데이터에 자신의 사진을 포함하는 것을 원치 않는 사용자도 많습니다. 일반적으로 사용자는 공유하거나 공유하지 않을 정보를 제어할 수 있습니다. 예를 들어 사용자가 확인란을 선택하거나 선택 취소하여 위치 정보를 다른 사람과 공유할지 여부를 제어할 수 있습니다. 또한 개인 정보 구성 cmdlet을 통해 관리자는 사용자의 개인 정보 설정을 관리할 수 있습니다. 경우에 따라 관리자는 설정을 사용하거나 사용하지 않도록 설정할 수 있습니다. 예를 들어 AutoInitiateContacts 속성이 True로 설정된 경우 각 사용자의 연락처 목록에 팀원이 자동으로 추가됩니다. False로 설정된 경우에는 각 사용자의 연락처 목록에 팀원이 자동으로 추가되지 않습니다.

또는 Lync에서 기본값을 구성하고 사용자에게 이러한 값을 변경할 권한을 제공할 수 있습니다. 예를 들어 사용자에게는 위치 게시를 중지할 권한이 있지만 기본적으로 사용자에 대한 위치 데이터가 게시됩니다. PublishLocationDataByDefault 속성을 False로 설정하면 관리자가 이 동작을 변경할 수 있습니다. 이 경우에는 사용자에게 이 데이터를 게시할 권한이 여전히 있지만(선택한 경우) 위치 데이터가 기본적으로 게시되지 않습니다.

개인 정보 구성 설정은 전역 범위, 사이트 범위 및 서비스 범위(사용자 서버 서비스에만 해당)에서 적용할 수 있습니다. **Set-CsPrivacyConfiguration** cmdlet을 사용하면 조직에서 현재 사용되고 있는 개인 정보 구성 설정을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsPrivacyConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsPrivacyConfiguration"}

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
<td><p><em>AutoInitiateContacts</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정된 경우 Lync에서 모든 관리자 및 부하 직원을 대화 상대 목록에 자동으로 추가합니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayPublishedPhotoDefault</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정된 경우 사용자의 사진이 Lync에 자동으로 게시됩니다. False로 설정된 경우 사용자가 [다른 사람에게 내 사진 표시] 옵션을 명시적으로 선택하지 않는 한 사용자의 사진을 사용할 수 없습니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnablePrivacyMode</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True인 경우 사용자가 고급 공개 수준 모드를 사용할 수 있습니다. 고급 공개 수준 모드에서는 대화 상대 목록의 사용자만 현재 상태 정보를 보도록 허용됩니다. False로 설정된 경우 조직의 모든 구성원이 사용자의 현재 상태 정보를 사용할 수 있습니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 개인 정보 구성 설정의 고유한 식별자입니다. 전역 설정을 수정하려면 -Identity global 구문을 사용합니다. 사이트 범위에서 구성된 설정을 수정하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 서비스 수준에서 설정을 수정하려면 -Identity service:Redmond-UserServices-1과 같은 구문을 사용합니다. 개인 정보 설정은 사용자 서버 서비스에만 적용할 수 있습니다. 이러한 설정을 다른 서비스에 적용하려고 하면 오류가 발생합니다.</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Set-CsPrivacyConfiguration</strong> cmdlet을 호출할 때 전역 설정이 업데이트됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>PrivacyConfiguration 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PublishLocationDataDefault</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정된 경우 위치 데이터가 Lync Server에 자동으로 게시됩니다. False로 설정된 경우 사용자가 [연락처 내 위치 표시] 옵션을 명시적으로 선택하지 않는 한 위치 데이터를 사용할 수 없습니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>수정할 개인 정보 구성 설정에 대한 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Windows PowerShell의 원격 세션을 사용 중이고 비즈니스용 Skype Online에만 연결되는 경우 Tenant 매개 변수를 포함하지 않아도 됩니다. 대신, 연결 정보에 따라 테넌트 ID가 자동으로 채워집니다. Tenant 매개 변수는 하이브리드 배포에서 주로 사용됩니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PrivacyConfiguration 개체입니다. **Set-CsPrivacyConfiguration** cmdlet은 개인 정보 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsPrivacyConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PrivacyConfiguration 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPrivacyConfiguration](get-csprivacyconfiguration.md)  
[New-CsPrivacyConfiguration](new-csprivacyconfiguration.md)  
[Remove-CsPrivacyConfiguration](remove-csprivacyconfiguration.md)

