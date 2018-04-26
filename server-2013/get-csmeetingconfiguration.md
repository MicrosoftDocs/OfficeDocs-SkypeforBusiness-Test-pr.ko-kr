---
title: Get-CsMeetingConfiguration
TOCTitle: Get-CsMeetingConfiguration
ms:assetid: 3aa2d905-0ce0-4675-8543-c7bb9b4a3d1a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425875(v=OCS.15)
ms:contentKeyID: 49303353
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsMeetingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

**Get-CsMeetingConfiguration** cmdlet을 사용하면 조직에서 현재 사용 중인 모임 구성 설정에 대한 정보를 반환할 수 있습니다. 모임 구성 설정은 사용자가 만들 수 있는 모임("전화 회의"라고도 함) 유형을 지정하고 익명 사용자 및 전화 접속 회의 사용자가 이러한 모임에 참가하는 방법을 제어하도록 도와줍니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsMeetingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsMeetingConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>] [-Tenant <Guid>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 현재 사용 중인 모든 모임 구성 설정 컬렉션을 반환합니다.

    Get-CsMeetingConfiguration

## 예제 2

예제 2에서는 Identity가 site:Redmond인 한 개의 모임 구성 설정 컬렉션만 반환됩니다.

    Get-CsMeetingConfiguration -Identity site:Redmond

## 예제 3

예제 3에서는 서비스 범위에서 구성된 모든 모임 구성 설정을 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수와 필터 값 "service:\*"를 포함합니다. 이 필터 값은 Identity 속성이 "service:" 문자로 시작하는 설정에 대한 데이터만 반환되도록 제한합니다.

    Get-CsMeetingConfiguration -Filter "service:*"

## 예제 4

예제 4에서는 익명 사용자가 기본적으로 입장하도록 허용되는 모든 모임 구성 설정에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsMeetingConfiguration** cmdlet을 사용하여 현재 사용 중인 모든 모임 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 AdmitAnonymousByDefault 속성이 True와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsMeetingConfiguration | Where-Object {$_.AdmitAnonymousUsersByDefault -eq $True}

## 자세한 정보

모임("전화 회의"라고도 함)은 Lync Server의 필수적인 부분입니다. **CsMeetingConfiguration** cmdlet을 통해 관리자는 사용자가 만들 수 있는 모임 유형을 제어하고 모임에서 익명 사용자 및 전화 접속 회의 사용자를 처리하는 방법을 결정할 수 있습니다. 예를 들어 PSTN(공중 전화망)을 통해 전화 접속한 사용자가 모임에 자동으로 입장하도록 모임을 구성할 수 있습니다. 또는 전화 접속 사용자가 모임에 자동으로 입장하지는 않지만 대신 모임 대기실로 경로 지정되도록 모임을 구성할 수 있습니다. 이러한 전화 접속 사용자는 발표자가 모임에 입장하도록 허용할 때까지 대기실에서 대기 상태로 유지됩니다.

**Get-CsMeetingConfiguration** cmdlet을 사용하면 조직에서 현재 사용 중인 모임 구성 설정 컬렉션에 대한 정보를 가져올 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsMeetingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsMeetingConfiguration"}

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
<td><p>한 개 또는 여러 개의 모임 구성 설정 컬렉션을 반환하기 위해 와일드카드 문자를 사용할 수 있습니다. 사이트 범위에서 구성된 모든 설정 컬렉션을 반환하려면 -Filter site:* 구문을 사용합니다. Identity(필터링할 수 있는 유일한 속성)에 문자열 값 &quot;EMEA&quot;가 포함된 모든 설정 컬렉션을 반환하려면 -Filter *EMEA* 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 모임 구성 설정 컬렉션의 고유 식별자를 나타냅니다. 전역 설정을 참조하려면 -Identity global 구문을 사용합니다. 사이트 범위에서 구성된 컬렉션을 참조하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 서비스 범위에서 구성된 설정은 -Identity service:UserServer:atl-cs-001.litwareinc.com과 유사한 구문을 사용하여 검색할 수 있습니다.</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsMeetingConfiguration</strong> cmdlet에서 조직에서 사용 중인 모든 모임 설정의 컬렉션을 반환합니다.</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용해야 하는 경우 대신 Filter 매개 변수를 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 모임 구성 데이터를 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>해당 모임 구성 설정을 검색할 Office 365 테넌트 계정의 GUID(Globally Unique Identifier)입니다.</p>
<p>예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Windows PowerShell의 원격 세션을 사용 중이고 비즈니스용 Skype Online에만 연결되는 경우 Tenant 매개 변수를 포함하지 않아도 됩니다. 대신, 연결 정보에 따라 테넌트 ID가 자동으로 채워집니다. Tenant 매개 변수는 하이브리드 배포에서 주로 사용됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsMeetingConfiguration** cmdlet은 파이프라인된 데이터를 허용하지 않습니다.

## 반환 형식

**Get-CsMeetingConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.MeetingConfiguration 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsMeetingConfiguration](new-csmeetingconfiguration.md)  
[Remove-CsMeetingConfiguration](remove-csmeetingconfiguration.md)  
[Set-CsMeetingConfiguration](set-csmeetingconfiguration.md)

