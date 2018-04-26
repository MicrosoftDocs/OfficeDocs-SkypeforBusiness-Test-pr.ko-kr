---
title: Remove-CsPrivacyConfiguration
TOCTitle: Remove-CsPrivacyConfiguration
ms:assetid: 32052c51-953d-4278-9425-306245d297ed
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425821(v=OCS.15)
ms:contentKeyID: 49303240
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsPrivacyConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존의 개인 정보 구성 설정 컬렉션을 제거합니다. 개인 정보 구성 설정은 사용자가 다른 사용자에게 공개할 정보의 수준을 결정하는 데 도움이 됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsPrivacyConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트에 할당된 개인 정보 구성 설정을 반환합니다. 이러한 설정을 삭제하면 Redmond 사이트의 사용자에게 자동으로 전역 개인 정보 설정이 상속됩니다.

    Remove-CsPrivacyConfiguration -Identity site:Redmond

## 예제 2

예제 2에서는 사이트 범위에 할당된 모든 개인 정보 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsPrivacyConfiguration** cmdlet을 Filter 매개 변수와 함께 호출합니다. 필터 값 "site:\*"는 ID가 "site" 문자로 시작하는 설정만 반환되도록 합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 제거하는 **Remove-CsPrivacyConfiguration** cmdlet에 파이프됩니다.

    Get-CsPrivacyConfiguration -Filter "site:*" | Remove-CsPrivacyConfiguration

## 예제 3

예제 3에 나오는 명령은 개인 정보 보호 모드가 사용하지 않도록 설정된 모든 개인 정보 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsPrivacyConfiguration** cmdle을 추가 매개 변수 없이 호출합니다. 그러면 조직에서 사용 중인 모든 개인 정보 보호 구성 설정의 컬렉션이 반환됩니다. 이 컬렉션은 EnablePrivacyMode 속성이 False와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsPrivacyConfiguration** cmdlet에 파이프됩니다.

    Get-CsPrivacyConfiguration | Where-Object {$_.EnablePrivacyMode -eq $False} | Remove-CsPrivacyConfiguration

## 자세한 정보

Lync Server는 사용자에게 다른 사람들과 자신의 다양한 현재 상태 정보를 공유할 기회를 제공합니다. 사진을 게시하고, 자세한 위치 정보를 제공하고, 조직의 모든 사람들에게 자신의 현재 상태 정보를 자동으로 공개할 수 있습니다(연락처 목록에 있는 사람에게만 공개하는 것이 아님).

이러한 정보를 다른 사람에게 공개할 수 있는 기회를 환영하는 사용자도 있지만 반대로 공개를 꺼리는 사용자도 있습니다. 예를 들어 현재 상태 데이터에 자신의 사진을 포함하는 것을 원치 않는 사용자도 많습니다. 일반적으로 사용자는 공유하거나 공유하지 않을 정보를 제어할 수 있습니다. 예를 들어 사용자는 확인란을 선택하거나 선택 취소하여 위치 정보를 다른 사람과 공유할지 여부를 제어할 수 있습니다. 또한 개인 정보 구성 cmdlet을 통해 관리자는 사용자의 개인 정보 설정을 관리할 수 있습니다. 경우에 따라 관리자는 설정을 사용하거나 사용하지 않도록 설정할 수 있습니다. 예를 들어 AutoInitiateContacts 속성이 True로 설정된 경우 각 사용자의 연락처 목록에 팀원이 자동으로 추가됩니다. False로 설정된 경우 각 사용자의 연락처 목록에 팀원이 자동으로 추가되지 않습니다.

또는 Lync Server에서 기본값을 구성하고 사용자에게 이러한 값을 변경할 권한을 제공할 수 있습니다. 예를 들어 기본적으로 사용자의 위치 데이터가 게시되지만 사용자에게 위치 게시를 중지할 권한이 있습니다. PublishLocationDataByDefault 속성을 False로 설정하면 이러한 동작을 변경할 수 있습니다. 이 경우 위치 데이터가 기본적으로 게시되지 않지만 사용자는 여전히 필요할 경우 이 데이터를 게시할 수 있습니다.

개인 정보 보호 구성 설정은 전역 범위, 사이트 범위 및 서비스 범위(사용자 서버 서비스에만 해당)에 적용할 수 있습니다. **Remove-CsPrivacyConfiguration** cmdlet을 사용하면 사이트나 서비스 범위에 구성된 설정을 삭제할 수 있습니다. 예를 들어 사이트 범위에 구성된 설정을 대상으로 cmdlet을 실행하면 이러한 설정이 삭제되고 해당 사이트에 있는 사용자들의 개인 정보 설정은 전역 컬렉션에 의해 제어됩니다. 전역 컬렉션에 대해 **Remove-CsPrivacyConfiguration** cmdlet을 실행할 수도 있지만 전역 컬렉션이 삭제되지는 않습니다. 대신 컬렉션의 모든 속성이 기본값으로 다시 설정됩니다. 예를 들어 이전에 EnablePrivacyMode 속성을 True로 변경했다고 가정해 보겠습니다. 이제 전역 컬렉션을 "삭제"하면 EnablePrivacyMode가 기본값인 False로 돌아갑니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsPrivacyConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsPrivacyConfiguration"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>제거할 개인 정보 구성 설정에 대한 고유한 식별자입니다. 사이트 범위에서 구성된 설정을 제거하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 서비스 수준에서 설정을 제거하려면 -Identity service:UserServer:atl-cs-001.litwareinc.com과 유사한 구문을 사용합니다.</p>
<p><strong>Remove-CsPrivacyConfiguration</strong> cmdlet은 설정의 전역 컬렉션에 대해서도 실행할 수 있지만 전역 컬렉션은 삭제되지 않습니다. 대신 컬렉션의 모든 속성이 기본값으로 다시 설정됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>개인 정보 구성 설정을 삭제할 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PrivacyConfiguration 개체입니다. **Remove-CsPrivacyConfiguration** cmdlet은 개인 정보 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

없음. 대신, **Remove-CsPrivacyConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PrivacyConfiguration 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPrivacyConfiguration](get-csprivacyconfiguration.md)  
[New-CsPrivacyConfiguration](new-csprivacyconfiguration.md)  
[Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md)

