---
title: Set-CsSimpleUrlConfiguration
TOCTitle: Set-CsSimpleUrlConfiguration
ms:assetid: f0334ae9-e6c1-4134-8749-af202169bb2a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412991(v=OCS.15)
ms:contentKeyID: 49305471
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsSimpleUrlConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 단순 URL 구성 컬렉션을 수정합니다. 단순 URL을 사용하면 사용자가 모임 및 전화 회의에 쉽게 참가하고, 관리자가 Lync Server 제어판에 쉽게 로그온할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsSimpleUrlConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsSimpleUrlConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-SimpleUrl <PSListModifier>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트에서 모든 단순 URL을 제거하지만 단순 URL의 실제 컬렉션은 제거하지 않습니다. 컬렉션은 계속 존재하지만 더 이상 어떤 URL도 포함하지 않습니다. 이 작업을 수행하기 위해 명령은 SimpleUrl 매개 변수를 사용하고 매개 변수 값을 null 값($Null)으로 설정합니다. 이렇게 하면 모든 단순 URL이 컬렉션에서 제거됩니다.

    Set-CsSimpleUrlConfiguration -Identity "site:Redmond" -SimpleUrl $Null

## 예제 2

예제 2에서는 단순 URL의 기존 컬렉션에 새 URL을 추가하는 방법을 보여 줍니다. 먼저 이 예제의 첫 번째 명령은 **New-CsSimpleUrlEntry** cmdlet을 사용하여 https://meet.fabrikam.com을 가리키는 URL 항목을 만듭니다. 이 URL 항목은 $urlEntry라는 변수에 저장됩니다.

두 번째 명령은 **New-CsSimpleUrl** cmdlet을 사용하여 메모리에만 나타나는 단순 URL의 인스턴스를 만듭니다. 이 예제에서 URL 구성 요소는 Meet로, 도메인은 fabrikam.com으로, ActiveUrl은 https://meet.fabrikam.com으로, SimpleUrl 속성은 $urlEntry로 설정되며 $urlEntry는 첫 번째 명령에서 만들어진 URL 항목입니다.

URL이 만들어지고 개체 참조 $simpleUrl에 저장되면 이 예제의 마지막 명령이 Redmond 사이트의 단순 URL 컬렉션에 새 URL을 추가합니다. 이 작업을 수행하기 위해 **Set-CsSimpleUrlConfiguration**과 함께 SimpleUrl 매개 변수 및 매개 변수 값 @{Add=$simpleUrl}을 사용합니다. 이 구문은 개체 참조 $simpleUrl에 저장된 URL을 SimpleUrl 속성에 추가하도록 지정합니다.

    $urlEntry = New-CsSimpleUrlEntry -Url "https://meet.fabrikam.com"
    $simpleUrl = New-CsSimpleUrl -Component "meet" -Domain "fabrikam.com" -SimpleUrlEntry $urlEntry -ActiveUrl "https://meet.fabrikam.com"
    
    Set-CsSimpleUrlConfiguration -Identity "site:Redmond" -SimpleUrl @{Add=$simpleUrl}

## 예제 3

예제 3에 표시된 명령은 단순 URL 컬렉션에서 단일 URL을 삭제하는 방법을 보여 줍니다. **Set-CsSimpleUrlConfiguration** cmdlet은 URL 개체를 처리해야 하므로 예제는 먼저 삭제할 URL과 똑같은 속성 값을 포함하는 새 개체를 만듭니다. 이 작업을 수행하기 위해 첫 번째 명령은 **New-CsSimpleUrlEntry** cmdlet을 사용하여 https://meet.fabrikam.com을 가리키는 URL 항목을 만듭니다. 이 URL 항목은 $urlEntry라는 변수에 저장됩니다.

URL 항목이 만들어지면 두 번째 명령이 **New-CsSimpleUrl** cmdlet을 사용하여 메모리에만 나타나는 단순 URL의 인스턴스를 만듭니다. 이 예제에서 URL 구성 요소는 Meet로, 도메인은 fabrikam.com으로, ActiveUrl은 https://meet.fabrikam.com으로, SimpleUrl 속성은 $urlEntry로 설정되며 $urlEntry는 첫 번째 명령에서 만들어진 URL 항목입니다. 이는 삭제할 URL과 동일한 속성 값을 가진 내부에만 나타나는 URL($simpleUrl)을 만듭니다.

예제의 마지막 명령은 Redmond 사이트의 단순 URL 컬렉션에서 URL을 삭제합니다. 이 작업을 수행하기 위해 **Set-CsSimpleUrlConfiguration** cmdlet, SimpleUrl 매개 변수 및 매개 변수 값 @Remove=$simpleUrl을 사용합니다. 이 구문은 개체 참조 $simpleUrl에 저장된 URL을 SimpleUrl 속성에서 제거하도록 지정합니다.

    $urlEntry = New-CsSimpleUrlEntry -Url "https://fabrikam.vdomain.com"
    $simpleUrl = New-CsSimpleUrl -Component "meet" -Domain "fabrikam.com" -SimpleUrlEntry $urlEntry -ActiveUrl "https://meet.fabrikam.com"
    
    Set-CsSimpleUrlConfiguration -Identity "site:Redmond" -SimpleUrl @{Remove=$simpleUrl}

## 자세한 정보

Microsoft Office Communications Server 2007 R2에서는 모임의 URL이 다음과 유사했습니다.

https://imdf.litwareinc.com/Join?uri=sip%3Akenmyer%40litwareinc.com%3Bgruu%3Bopaque%3Dapp%3Aconf%3Afocus%3Aid%3A125f95a0b0184dcea706f1a0191202a8\&key=EcznhLh5K5t

그러나 이러한 URL은 한 눈에 파악하기 힘들고 다른 사람에게 전달하기도 어렵습니다. Lync Server에서 도입된 단순 URL은 다음과 같은 URL을 사용자에게 제공하여 이러한 문제를 해결합니다.

https://meet.litwareinc.com/kenmyer/071200

단순 URL은 이전 버전의 Office Communications Server에서 사용된 URL의 향상된 기능입니다. 하지만 단순 URL은 자동으로 만들어지지 않으며 사용자가 직접 URL을 구성해야 합니다. 또한 각 URL에 대해 DNS(Domain Name System) 레코드를 만들고, 외부 액세스에 대한 역방향 프록시 규칙을 구성하고, 프런트 엔드 서버 인증서에 단순 URL을 추가하는 등의 작업을 수행해야 합니다.

Lync Server에서는 세 가지 유형의 단순 URL을 만들 수 있습니다.

Meet – 모임에 사용됩니다. 각 SIP 도메인에 모임 URL이 하나 이상 있어야 합니다.

Admin - 관리자에게 Lync Server를 안내하는 데 사용됩니다.

Dialin - 전화 접속 회의 웹 페이지에 사용됩니다.

단순 URL은 단순 URL 구성 컬렉션에 저장됩니다. Lync Server를 설치하면 전역 컬렉션이 만들어지는데, 사이트 범위에서 사용자 지정 컬렉션을 만들 수도 있습니다. 이렇게 하면 각 사이트마다 다른 단순 URL을 사용할 수 있습니다.

단순 URL 구성 컬렉션은 **New-CsSimpleUrlConfiguration** cmdlet을 사용하여 만듭니다. 그런 다음 **New-CsSimpleUrl** cmdlet 및 **Set-CsSimpleUrlConfiguration** cmdlet과 같은 추가 cmdlet을 사용하여 단순 URL로 이러한 컬렉션을 채울 수 있습니다. 컬렉션이 만들어지면 **Set-CsSimpleUrlConfiguration** cmdlet을 다시 사용하여 이러한 컬렉션에 저장된 URL을 수정할 수 있습니다.

단순 URL을 컬렉션에 추가하는 과정은 매우 직관적입니다. 먼저 **New-CsSimpleUrl** cmdlet 및 **New-CsSimpleUrlEntry** cmdlet을 사용하여 메모리에만 나타나는 URL을 만듭니다. 그런 다음 Add 명령을 사용하여 기존 컬렉션에 새 URL을 추가합니다. 또는 Replace 메서드를 사용하여 기존의 모든 URL을 새 URL로 대체할 수 있습니다.

컬렉션에서 URL을 제거하는 과정은 약간 더 어렵습니다. 왜냐하면 먼저 기존 URL을 기반으로 해당 URL에 대한 새 개체 참조를 만든 다음 해당 개체 참조 및 Remove 메서드를 사용하여 URL을 삭제해야 하기 때문입니다.

단순 URL 컬렉션을 업데이트한 후에는 **Enable-CsComputer** cmdlet을 실행해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsSimpleUrlConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsSimpleUrlConfiguration"}

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
<td><p>수정할 단순 URL 컬렉션의 고유 식별자입니다. 전역 컬렉션을 수정하려면 -Identity global 구문을 사용합니다. 사이트 범위에서 컬렉션을 수정하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다.</p>
<p>이 매개 변수가 지정되지 않은 경우 전역 컬렉션이 수정됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>단순 URL 구성 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SimpleUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>이 컬렉션에 대해 구성된 단순 URL입니다. 이러한 URL은 <strong>New-SimpleUrl</strong> cmdlet 및 <strong>New-SimpleUrlEntry</strong> cmdlet을 사용하여 만들어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>해당 단순 URL 구성 설정을 수정할 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
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

Microsoft.Rtc.Management.WritableConfig.Settings.SimpleUrl.SimpleUrlConfiguration 개체입니다. **Set-CsSimpleUrlConfiguration** cmdlet은 단순 URL 구성 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음.

## 참고 항목

#### 기타 리소스

[Get-CsSimpleUrlConfiguration](get-cssimpleurlconfiguration.md)  
[New-CsSimpleUrl](new-cssimpleurl.md)  
[New-CsSimpleUrlConfiguration](new-cssimpleurlconfiguration.md)  
[New-CsSimpleUrlEntry](new-cssimpleurlentry.md)  
[Remove-CsSimpleUrlConfiguration](remove-cssimpleurlconfiguration.md)

