---
title: Get-CsSimpleUrlConfiguration
TOCTitle: Get-CsSimpleUrlConfiguration
ms:assetid: 59f5528b-d1f4-4da9-9dfe-102c96c6d7c2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398392(v=OCS.15)
ms:contentKeyID: 49303727
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsSimpleUrlConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 단순 URL에 대한 정보를 반환합니다. 단순 URL을 사용하면 사용자가 모임 및 회의에 쉽게 참가하고, 관리자가 Lync Server 제어판에 쉽게 로그온할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsSimpleUrlConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsSimpleUrlConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>] [-Tenant <Guid>]

## 예제

## 예제 1

예제 1에서는 조직에서 현재 사용되고 있는 모든 단순 URL 구성 컬렉션에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 **Get-CsSimpleUrlConfiguration** cmdlet을 추가 매개 변수 없이 호출합니다.

    Get-CsSimpleUrlConfiguration

## 예제 2

예제 2에서는 단일의 단순한 URL 구성 컬렉션인, Identity가 site:Redmond인 구성에 대한 정보가 반환됩니다.

    Get-CsSimpleUrlConfiguration -Identity "site:Redmond"

## 예제 3

예제 3에서는 사이트 범위에 할당된 모든 단순 URL 구성 컬렉션에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 **Get-CsSimpleUrlConfiguration** cmdlet을 Filter 매개 변수와 함께 호출합니다. 필터 값 "site:\*"는 반환되는 데이터를 ID가 문자열 값 "site:"으로 시작하는 컬렉션으로 제한합니다.

    Get-CsSimpleUrlConfiguration -Filter "site:*"

## 예제 4

예제 4에서는 조직에서 사용하도록 구성된 각 단순 URL에 대한 세부 정보를 표시합니다. 이 작업을 수행하기 위해 먼저 **Get-CsSimpleUrlConfiguration** cmdlet을 호출하여 전체 단순 URL 정보 집합을 반환합니다. 이 데이터는 ExpandProperty 매개 변수를 사용하여 SimpleUrl 속성 값을 "확장"하는 **Select-Object** cmdlet에 파이프됩니다. 속성 값을 확장하면 해당 속성에 저장된 모든 데이터가 읽기 쉬운 형식으로 표시됩니다.

    Get-CsSimpleUrlConfiguration | Select-Object -ExpandProperty SimpleUrl

## 예제 5

예제 5에 표시된 명령은 조직에서 현재 사용 중인 모임 관리에 대한 모든 단순 URL을 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsSimpleUrlConfiguration** cmdlet을 추가 매개 변수 없이 호출합니다. 이 명령은 단순 URL 정보의 전체 집합을 반환합니다. 이 데이터는 ExpandProperty 매개 변수를 사용하여 SimpleUrl 속성 값을 확장하는 **Select-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 Component 속성이 "Meet"과 같은 단순 URL만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsSimpleUrlConfiguration | Select-Object -ExpandProperty SimpleUrl | Where-Object {$_.Component -eq "Meet"}

## 자세한 정보

Microsoft Office Communications Server 2007 R2에서는 모임의 URL이 다음과 유사했습니다.

https://imdf.litwareinc.com/Join?uri=sip%3Akenmyer%40litwareinc.com%3Bgruu%3Bopaque%3Dapp%3Aconf%3Afocus%3Aid%3A125f95a0b0184dcea706f1a0191202a8\&key=EcznhLh5K5t

그러나 이러한 URL은 한 눈에 파악하기 힘들고 다른 사람에게 전달하기도 어렵습니다. Lync Server 2010에서 도입된 단순 URL은 다음과 같은 URL을 사용자에게 제공하여 이러한 문제를 해결합니다.

https://meet.litwareinc.com/kenmyer/071200

단순 URL은 Office Communications Server에서 사용되는 URL의 향상된 기능입니다. 하지만 단순 URL은 자동으로 만들어지지 않으며 사용자가 직접 URL을 구성해야 합니다. 또한 각 URL에 대해 DNS(Domain Name System) 레코드를 만들고, 외부 액세스에 대한 역방향 프록시 규칙을 구성하고, 프런트 엔드 서버 인증서에 단순 URL을 추가하는 등의 작업을 수행해야 합니다.

Lync Server에서는 세 가지 유형의 단순 URL을 만들 수 있습니다.

Meet – 모임에 사용됩니다. 각 SIP 도메인에 모임 URL이 하나 이상 있어야 합니다.

Admin - 관리자에게 Lync Server 제어판을 안내하는 데 사용됩니다.

Dialin - 전화 접속 회의 웹 페이지에 사용됩니다.

단순 URL은 단순 URL 구성 컬렉션에 저장됩니다. Lync Server를 설치하면 전역 컬렉션이 만들어지는데, 사이트 범위에서 사용자 지정 컬렉션을 만들 수도 있습니다. 이렇게 하면 사이트마다 다른 단순 URL을 사용할 수 있습니다.

**Get-CsSimpleUrlConfiguration** cmdlet을 사용하면 조직에서 현재 사용 중인 모든 단순 URL 구성 컬렉션에 대한 정보를 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsSimpleUrlConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsSimpleUrlConfiguration"}

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
<td><p>반환할 단순 URL 컬렉션을 지정하기 위해 와일드카드 문자를 사용할 수 있습니다. 예를 들어 사이트 범위에서 적용된 모든 구성 설정의 컬렉션을 반환하려면 -Filter &quot;site:*&quot; 구문을 사용합니다.</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 단순 URL 컬렉션의 고유 식별자입니다. 전역 컬렉션을 반환하려면 -Identity global 구문을 사용합니다. 사이트 범위에서 컬렉션을 반환하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용하려면 Filter 매개 변수를 대신 사용합니다.</p>
<p><strong>Get-CsSimpleUrlConfiguration</strong> cmdlet을 매개 변수 없이 호출하면 조직에서 사용하도록 구성된 모든 단순 URL이 반환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 단순 URL 구성 데이터를 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>해당 단순 URL 구성 설정을 검색할 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Get-CsSimpleUrlConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SimpleUrl.SimpleUrlConfiguration 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsSimpleUrlConfiguration](new-cssimpleurlconfiguration.md)  
[Remove-CsSimpleUrlConfiguration](remove-cssimpleurlconfiguration.md)  
[Set-CsSimpleUrlConfiguration](set-cssimpleurlconfiguration.md)

