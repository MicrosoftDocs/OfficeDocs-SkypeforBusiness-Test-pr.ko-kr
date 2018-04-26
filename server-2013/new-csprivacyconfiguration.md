---
title: New-CsPrivacyConfiguration
TOCTitle: New-CsPrivacyConfiguration
ms:assetid: 9b7f02d7-93a5-4fa5-a74c-3fe4baf8bbfc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398807(v=OCS.15)
ms:contentKeyID: 49304506
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsPrivacyConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

개인 정보 구성 설정의 새 컬렉션을 만듭니다. 개인 정보 보호 구성 설정은 사용자가 다른 사용자에게 공개할 정보의 수준을 결정하는 데 도움이 됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsPrivacyConfiguration -Identity <XdsIdentity> [-AutoInitiateContacts <$true | $false>] [-Confirm [<SwitchParameter>]] [-DisplayPublishedPhotoDefault <$true | $false>] [-EnablePrivacyMode <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-PublishLocationDataDefault <$true | $false>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트(-Identity site:Redmond)에 적용될 개인 정보 구성 설정의 새 컬렉션을 생성합니다. 새 설정은 개인 정보 모드를 활성화합니다. 이렇게 하려면 EnablePrivacyMode 매개 변수를 추가하고 매개 변수 값을 True로 설정합니다. Redmond 사이트에 이미 개인 정보 설정의 컬렉션이 있는 경우 이 명령이 실패합니다.

    New-CsPrivacyConfiguration -Identity site:Redmond -EnablePrivacyMode $True

## 예제 2

예제 2에서는 InMemory 매개 변수를 사용하여 처음에 메모리에만 존재하는 개인 정보 구성 설정의 새 컬렉션을 생성하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 **New-CsPrivacyConfiguration** cmdlet을 Identity 및 InMemory 매개 변수와 함께 호출합니다. 결과 개체는 $x라는 변수에 저장됩니다. 이때 개인 정보 설정은 메모리에만 존재합니다. **Get-CsPrivacyConfiguration** cmdlet을 실행하면 site:Redmond 목록이 표시되지 않습니다.

두 번째 명령에서는 EnablePrivacyMode 속성 값을 True로 설정합니다. 마지막으로 세 번째 명령은 **Set-CsPrivacyConfiguration** cmdlet을 사용하여 개인 정보 설정의 이 가상 컬렉션을 Redmond 사이트에 적용되는 실제 설정 컬렉션으로 변환합니다. **Set-CsPrivacyConfiguration** cmdlet을 호출하는 것이 중요합니다. 이 cmdlet을 호출하지 않으면 새 개인 정보 설정이 Redmond 사이트에 적용되지 않으며, Windows PowerShell 세션을 종료하거나 변수 $x를 삭제한 경우 완전히 사라집니다.

    $x = New-CsPrivacyConfiguration -Identity site:Redmond -InMemory
    $x.EnablePrivacyMode = $True
    Set-CsPrivacyConfiguration -Instance $x

## 자세한 정보

Lync Server는 사용자에게 다른 사람들과 자신의 다양한 현재 상태 정보를 공유할 기회를 제공합니다. 사진을 게시하고, 자세한 위치 정보를 제공하고, 조직의 모든 사람들에게 자신의 현재 상태 정보를 자동으로 공개할 수 있습니다(연락처 목록에 있는 사람에게만 공개하는 것이 아님).

어떤 사용자는 이 정보를 동료들에게 공개하게 되는 것을 흔쾌히 받아들이지만 이 데이터를 공유하기를 꺼리는 사용자도 있을 수 있습니다. 예를 들어 현재 상태 데이터에 자신의 사진을 포함하는 것을 원치 않는 사용자도 많습니다. 일반적으로 사용자는 공유하거나 공유하지 않을 정보를 제어할 수 있습니다. 예를 들어 사용자가 확인란을 선택하거나 선택 취소하여 위치 정보를 다른 사람과 공유할지 여부를 제어할 수 있습니다. 또한 개인 정보 구성 cmdlet을 통해 관리자는 사용자의 개인 정보 설정을 관리할 수 있습니다. 경우에 따라 관리자는 설정을 사용하거나 사용하지 않도록 설정할 수 있습니다. 예를 들어 AutoInitiateContacts 속성이 True로 설정된 경우 각 사용자의 연락처 목록에 팀원이 자동으로 추가됩니다. False로 설정된 경우에는 각 사용자의 연락처 목록에 팀원이 자동으로 추가되지 않습니다.

또는 Lync에서 기본값을 구성하고 사용자에게 이러한 값을 변경할 권한을 제공할 수 있습니다. 예를 들어 사용자에게는 위치 게시를 중지할 권한이 있지만 기본적으로 사용자에 대한 위치 데이터가 게시됩니다. PublishLocationDataByDefault 속성을 False로 설정하면 관리자가 이 동작을 변경할 수 있습니다. 이 경우에는 사용자에게 이 데이터를 게시할 권한이 여전히 있지만(선택한 경우) 위치 데이터가 기본적으로 게시되지 않습니다.

개인 정보 구성 설정은 전역 범위, 사이트 범위 및 서비스 범위(사용자 서버 서비스에만 해당)에서 적용할 수 있습니다. **New-CsPrivacyConfiguration** cmdlet을 사용하면 사이트 또는 서비스에 적용할 새 개인 정보 구성 설정을 생성할 수 있습니다. 전역 범위에서는 새 컬렉션을 만들 수 없습니다. 각 개별 사이트 또는 서비스에는 개인 정보 구성 설정의 단일 컬렉션만 포함할 수 있습니다. Redmond 사이트에 이미 개인 정보 설정 컬렉션이 있는데 해당 사이트에 대한 새 컬렉션을 생성하려고 하면 명령이 실패합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsPrivacyConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsPrivacyConfiguration"}

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
<td><p>생성할 개인 정보 구성 설정의 고유한 식별자입니다. 사이트 범위에서 새 설정 컬렉션을 생성하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 서비스 범위에서 새 설정을 만들려면 -Identity service:UserServer:atl-cs-001.litwareinc.com과 유사한 구문을 사용합니다. 개인 정보 설정은 사용자 서버 서비스에 대해서만 생성할 수 있습니다. 이러한 설정을 다른 서비스에 적용하려고 하면 오류가 발생합니다.</p>
<p>지정된 사이트나 서비스에 대한 개인 정보 구성 설정이 이미 있는 경우 명령이 실패합니다. 마찬가지로 전역 설정의 새 컬렉션을 생성하려고 하면 명령이 실패합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AutoInitiateContacts</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정된 경우 Lync에서 모든 관리자 및 부하 직원을 대화 상대 목록에 자동으로 추가합니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisplayPublishedPhotoDefault</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정된 경우 사용자의 사진이 Lync에 자동으로 게시됩니다. False로 설정된 경우 사용자가 [다른 사람에게 내 사진 표시] 옵션을 명시적으로 선택하지 않는 한 사용자의 사진을 사용할 수 없습니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnablePrivacyMode</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True인 경우 사용자가 고급 공개 수준 모드를 사용할 수 있습니다. 고급 공개 수준 모드에서는 대화 상대 목록의 사용자만 현재 상태 정보를 보도록 허용됩니다. False로 설정된 경우 조직의 모든 구성원이 사용자의 현재 상태 정보를 사용할 수 있습니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PublishLocationDataDefault</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정된 경우 위치 데이터가 Lync에 자동으로 게시됩니다. False로 설정된 경우 사용자가 [연락처 내 위치 표시] 옵션을 명시적으로 선택하지 않는 한 위치 데이터를 사용할 수 없습니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>새 개인 정보 구성 설정이 만들어지는 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally unique identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대한 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
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

없음. **New-CsPrivacyConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsPrivacyConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PrivacyConfiguration 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsPrivacyConfiguration](get-csprivacyconfiguration.md)  
[Remove-CsPrivacyConfiguration](remove-csprivacyconfiguration.md)  
[Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md)

