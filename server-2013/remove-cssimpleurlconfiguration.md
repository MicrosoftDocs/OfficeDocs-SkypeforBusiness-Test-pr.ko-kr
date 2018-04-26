---
title: Remove-CsSimpleUrlConfiguration
TOCTitle: Remove-CsSimpleUrlConfiguration
ms:assetid: 6cf483ed-7a53-47b0-b87a-6ef70493ba32
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398515(v=OCS.15)
ms:contentKeyID: 49303958
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsSimpleUrlConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용 중인 단순 URL 구성 컬렉션 중 하나 이상을 제거합니다. 단순 URL을 사용하면 사용자가 모임 및 전화 회의에 쉽게 참가하고, 관리자가 Lync Server 제어판에 쉽게 로그온할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsSimpleUrlConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트에 적용된 단순 URL 구성 컬렉션을 삭제합니다. 이 명령은 지정된 사이트에 할당된 단순 URL을 모두 삭제합니다.

    Remove-CsSimpleUrlConfiguration -Identity "site:Redmond"

## 예제 2

예제 2에서는 사이트 범위에서 적용된 단순 URL 구성 컬렉션을 모두 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsSimpleUrlConfiguration** cmdlet 및 Filter 매개 변수를 사용하여 사이트 범위에서 구성된 모든 단순 URL 컬렉션을 반환합니다. 필터 값 "site:\*"는 반환된 데이터를 문자열 값 "site:"으로 시작하는 ID를 가진 컬렉션으로 제한합니다. 필터링된 컬렉션은 해당 컬렉션의 각 항목을 삭제하는 **Remove-CsSimpleUrlConfiguration** cmdlet에 파이프됩니다.

    Get-CsSimpleUrlConfiguration -Filter "site:*" | Remove-CsSimpleUrlConfiguration 

## 자세한 정보

Microsoft Office Communications Server 2007 R2에서는 모임의 URL이 다음과 유사했습니다.

https://imdf.litwareinc.com/Join?uri=sip%3Akenmyer%40litwareinc.com%3Bgruu%3Bopaque%3Dapp%3Aconf%3Afocus%3Aid%3A125f95a0b0184dcea706f1a0191202a8\&key=EcznhLh5K5t

그러나 이러한 URL은 한 눈에 파악하기 힘들고 다른 사람에게 전달하기도 어렵습니다. Lync Server 2010에서 도입된 단순 URL은 다음과 같은 URL을 사용자에게 제공하여 이러한 문제를 해결합니다.

https://meet.litwareinc.com/kenmyer/071200

단순 URL은 Office Communications Server에서 사용되는 URL의 향상된 기능입니다. 하지만 단순 URL은 자동으로 만들어지지 않으며 사용자가 직접 URL을 구성해야 합니다. 또한 각 URL에 대해 DNS(Domain Name System) 레코드를 만들고, 외부 액세스에 대한 역방향 프록시 규칙을 구성하고, 프런트 엔드 서버 인증서에 단순 URL을 추가하는 등의 작업을 수행해야 합니다.

Lync Server에서는 세 가지 유형의 단순 URL을 만들 수 있습니다.

Meet - 모임에 사용됩니다. 각 SIP 도메인에 모임 URL이 하나 이상 있어야 합니다.

Admin - 관리자에게 Lync Server를 안내하는 데 사용됩니다.

Dialin - 전화 접속 회의 웹 페이지에 사용됩니다.

단순 URL은 단순 URL 구성 컬렉션에 저장됩니다. Lync Server를 설치하면 전역 컬렉션이 만들어지는데, 사이트 범위에서 사용자 지정 컬렉션을 만들 수도 있습니다. 이렇게 하면 사이트마다 다른 단순 URL을 사용할 수 있습니다.

단순 URL 구성 컬렉션은 **New-CsSimpleUrlConfiguration** cmdlet을 사용하여 만듭니다. 그런 다음 **New-CsSimpleUrlEntry** cmdlet 및 **Set-CsSimpleUrlConfiguration** cmdlet과 같은 추가 cmdlet을 사용하여 단순 URL로 이러한 컬렉션을 채울 수 있습니다. 나중에 사이트 범위의 컬렉션 중 하나 이상을 삭제하려면 **Remove-CsSimpleUrlConfiguration** cmdlet을 사용하면 됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsSimpleUrlConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsSimpleUrlConfiguration"}

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
<td><p>제거할 단순 URL 컬렉션의 고유 식별자입니다. 사이트 범위에서 컬렉션을 제거하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p>
<p>-Identity global 구문을 사용하여 이 cmdlet을 전역 컬렉션에 대해 실행할 수도 있습니다. 그러나 이 경우 전역 컬렉션은 삭제되지 않습니다. 대신 해당 전역 내의 모든 단순 URL이 삭제됩니다.</p></td>
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
<td><p>단순 URL 구성 설정을 삭제할 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
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

Microsoft.Rtc.Management.WritableConfig.Settings.SimpleUrl.SimpleUrlConfiguration 개체입니다. **Remove-CsSimpleUrlConfiguration** cmdlet은 단순 URL 구성 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음.

## 참고 항목

#### 기타 리소스

[Get-CsSimpleUrlConfiguration](get-cssimpleurlconfiguration.md)  
[New-CsSimpleUrlConfiguration](new-cssimpleurlconfiguration.md)  
[Set-CsSimpleUrlConfiguration](set-cssimpleurlconfiguration.md)

