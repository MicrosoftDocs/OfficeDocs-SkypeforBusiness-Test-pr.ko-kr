---
title: Get-CsPrivacyConfiguration
TOCTitle: Get-CsPrivacyConfiguration
ms:assetid: f10ebf4a-1af5-48cf-96dc-4f5d56281848
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413002(v=OCS.15)
ms:contentKeyID: 49305486
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPrivacyConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용 중인 개인 정보 보호 구성 설정에 대한 정보를 반환합니다. 개인 정보 구성 설정을 사용하면 사용자가 다른 사용자에게 공개할 수 있는 정보를 결정할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsPrivacyConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsPrivacyConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>] [-Tenant <Guid>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 현재 사용 중인 모든 개인 정보 보호 서버 구성 설정을 반환합니다.

    Get-CsPrivacyConfiguration

## 예제 2

예제 2에서는 ID가 site:Redmond인 개인 정보 보호 구성 설정의 단일 컬렉션을 반환합니다.

    Get-CsPrivacyConfiguration -Identity site:Redmond

## 예제 3

예제 3에서는 사이트 범위에 할당된 모든 개인 정보 보호 구성 설정에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수가 필터 값 "site:\*"와 함께 포함됩니다. 이 필터 값은 ID(필터링할 수 있는 유일한 속성)가 "site:" 문자로 시작하는 설정만 반환합니다.

    Get-CsPrivacyConfiguration -Filter "site:*"

## 예제 4

예제 4에 표시된 명령은 개인 정보 보호 모드를 사용하도록 설정된 모든 개인 정보 보호 구성 설정에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsPrivacyConfiguration** cmdlet을 매개 변수 없이 호출하여 모든 개인 정보 보호 설정의 컬렉션을 반환합니다. 이 컬렉션은 EnablePrivacyMode 속성이 True와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsPrivacyConfiguration | Where-Object {$_.EnablePrivacyMode -eq $True}

## 자세한 정보

Lync Server는 사용자에게 다른 사람들과 자신의 다양한 현재 상태 정보를 공유할 기회를 제공합니다. 사진을 게시하고, 자세한 위치 정보를 제공하고, 조직의 모든 사람들에게 자신의 현재 상태 정보를 자동으로 공개할 수 있습니다(연락처 목록에 있는 사람에게만 공개하는 것이 아님).

어떤 사용자는 이 정보를 동료들에게 공개하게 되는 것을 흔쾌히 받아들이지만 이 데이터를 공유하기를 꺼리는 사용자도 있을 수 있습니다. 예를 들어 현재 상태 데이터에 자신의 사진을 포함하는 것을 원치 않는 사용자도 많습니다. 일반적으로 사용자는 공유하거나 공유하지 않을 정보를 제어할 수 있습니다. 예를 들어 사용자가 확인란을 선택하거나 선택 취소하여 위치 정보를 다른 사람과 공유할지 여부를 제어할 수 있습니다. 또한 개인 정보 구성 cmdlet을 통해 관리자는 사용자의 개인 정보 설정을 관리할 수 있습니다. 경우에 따라 관리자는 설정을 사용하거나 사용하지 않도록 설정할 수 있습니다. 예를 들어 AutoInitiateContacts 속성이 True로 설정된 경우 각 사용자의 연락처 목록에 팀원이 자동으로 추가됩니다. False로 설정된 경우에는 각 사용자의 연락처 목록에 팀원이 자동으로 추가되지 않습니다.

또는 Lync Server에서 기본값을 구성하고 사용자에게 이러한 값을 변경할 권한을 제공할 수 있습니다. 예를 들어 기본적으로 사용자의 위치 데이터가 게시되지만 사용자에게 위치 게시를 중지할 권한이 있습니다. PublishLocationDataByDefault 속성을 False로 설정하면 이러한 동작을 변경할 수 있습니다. 이 경우 위치 데이터가 기본적으로 게시되지 않지만 사용자는 여전히 필요할 경우 이 데이터를 게시할 수 있습니다.

개인 정보 구성 설정은 전역 범위, 사이트 범위 및 서비스 범위(사용자 서버 서비스에만 해당)에서 적용할 수 있습니다. **Get-CsPrivacyConfiguration** cmdlet을 사용하면 조직에서 현재 사용 중인 모든 개인 정보 보호 구성 설정에 대한 정보를 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsPrivacyConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPrivacyConfiguration"}

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
<td><p>와일드카드를 사용하여 개인 정보 보호 구성 설정의 컬렉션을 하나 이상 반환하는 데 사용됩니다. 예를 들어 사이트 범위에서 구성된 모든 설정을 반환하려면 -Filter &quot;site:*&quot; 구문을 사용하고, 서비스 범위에서 구성된 모든 설정을 반환하려면 -Filter &quot;service:*&quot; 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 개인 정보 보호 구성 설정의 고유 식별자입니다. 전역 설정을 반환하려면 -Identity global 구문을 사용합니다. 사이트 범위에 구성된 설정을 반환하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 서비스 수준에서 설정을 수정하려면 -Identity service:UserServer:atl-cs-001.litwareinc.com과 유사한 구문을 사용합니다.</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsPrivacyConfiguration</strong> cmdlet이 현재 조직에서 사용 중인 모든 개인 정보 보호 구성 설정을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 개인 정보 보호 구성 데이터를 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>해당 개인 정보 구성 설정을 검색할 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다.</p>
<p>예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Windows PowerShell의 원격 세션을 사용 중이고 비즈니스용 Skype Online에만 연결되는 경우 Tenant 매개 변수를 포함하지 않아도 됩니다. 대신, 연결 정보에 따라 테넌트 ID가 자동으로 채워집니다. Tenant 매개 변수는 하이브리드 배포에서 주로 사용됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsPrivacyConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsPrivacyConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PrivacyConfiguration 개체의 기존 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsPrivacyConfiguration](new-csprivacyconfiguration.md)  
[Remove-CsPrivacyConfiguration](remove-csprivacyconfiguration.md)  
[Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md)

