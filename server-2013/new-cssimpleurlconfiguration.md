---
title: New-CsSimpleUrlConfiguration
TOCTitle: New-CsSimpleUrlConfiguration
ms:assetid: 3140f15a-e448-42fe-b494-bf9caba32b35
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425813(v=OCS.15)
ms:contentKeyID: 49303225
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsSimpleUrlConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 단순 URL 구성 컬렉션을 만듭니다. 단순 URL을 사용하면 사용자가 모임 및 전화 회의에 쉽게 참가하고, 관리자가 Lync Server 제어판에 쉽게 로그인할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsSimpleUrlConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-SimpleUrl <PSListModifier>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트에 대한 새 단순한 URL 컬렉션을 만듭니다. 이 명령에는 Identity 외에 다른 매개 변수가 포함하지 않았으므로 새 컬렉션에는 단순한 URL이 포함되지 않습니다. Redmond 사이트에서 이미 단순한 URL 컬렉션을 호스트하고 있는 경우 이 명령이 실패합니다.

    New-CsSimpleUrlConfiguration -Identity "site:Redmond"

## 예제 2

예제 2에서는 단순한 URL 2개(모임 관리용 한 개, 전화 접속 회의용 한 개)를 포함하는 단순한 URL의 새 컬렉션을 만드는 방법을 보여 줍니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsSimpleUrlEntry** cmdlet을 사용하여 https://dialin.litwareinc.com을 가리키는 URL 항목을 만듭니다. 이 URL 항목은 $urlEntry라는 변수에 저장됩니다. 그러면 두 번째 명령이 https://meet.fabrikam.com에 연결되는 다른 URL 항목을 만듭니다.

다음으로, **New-CsSimpleUrl** cmdlet을 사용하여 메모리에만 나타나는 단순 URL의 인스턴스를 만듭니다. 이 예제에서는 URL Component를 Dialin으로, 도메인을 별표(\*)로, ActiveUrl을 https://dialin.fabrikam.com으로, SimpleUrl 속성을 $urlEntry로 설정합니다. 변수 $urlEntry는 첫 번째 명령에서 만든 URL 항목을 나타냅니다. 그런 다음 유사한 명령을 사용하여 meet.fabrikam.com에 대한 단순 URL을 만듭니다.

URL이 만들어지고 개체 참조 $simpleUrl 및 $simpleUrl2에 저장된 후에는 예제의 마지막 명령이 Redmond 사이트에 대한 새 단순 URL 컬렉션을 만들고 이 컬렉션에 새 메모리 내부 전용 URL 두 개를 추가합니다. **New-CsSimpleUrlConfiguration** cmdlet, SimpleUrl 매개 변수 및 매개 변수 값 @{Add=$simpleUrl, $simpleUrl2}를 사용하여 컬렉션에 새 URL을 추가합니다. 이 구문은 개체 참조 $simpleUrl 및 $simpleUrl2에 저장된 URL을 SimpleUrl 속성에 추가하도록 지정합니다.

    $urlEntry = New-CsSimpleUrlEntry -Url "https://dialin.fabrikam.com"
    $simpleUrl = New-CsSimpleUrl -Component "dialin" -Domain "*" -SimpleUrlEntry $urlEntry -ActiveUrl "https://dialin.fabrikam.com"
    
    $urlEntry2 = New-CsSimpleUrlEntry -Url "https://meet.fabrikam.com"
    $simpleUrl2 = New-CsSimpleUrl -Component "meet" -Domain "fabrikam.com" -SimpleUrlEntry $urlEntry2 
    
    New-CsSimpleUrlConfiguration -Identity "site:Redmond" -SimpleUrl @{Add=$simpleUrl,$simpleUrl2}

## 자세한 정보

Microsoft Office Communications Server 2007 R2에서는 모임의 URL이 다음과 유사했습니다.

https://imdf.litwareinc.com/Join?uri=sip%3Akenmyer%40litwareinc.com%3Bgruu%3Bopaque%3Dapp%3Aconf%3Afocus%3Aid%3A125f95a0b0184dcea706f1a0191202a8\&key=EcznhLh5K5t

그러나 이러한 URL은 한 눈에 파악하기 힘들고 다른 사람에게 전달하기도 어렵습니다. Lync Server 2010에서 도입된 단순 URL은 다음과 같은 URL을 사용자에게 제공하여 이러한 문제를 해결합니다.

https://meet.litwareinc.com/kenmyer/071200

단순 URL은 Office Communications Server에서 사용되는 URL의 향상된 기능입니다. 하지만 단순 URL은 자동으로 만들어지지 않으며 사용자가 직접 URL을 구성해야 합니다. 또한 각 URL에 대해 DNS(Domain Name System) 레코드를 만들고, 외부 액세스에 대한 역방향 프록시 규칙을 구성하고, 프런트 엔드 서버 인증서에 단순 URL을 추가하는 등의 작업을 수행해야 합니다.

Lync Server에서는 세 가지 유형의 단순 URL을 만들 수 있습니다.

Meet – 모임에 사용됩니다. 각 SIP 도메인에 대해 모임 URL이 하나 이상 있어야 합니다.

Admin – 관리자에게 Lync Server 제어판을 안내하는 데 사용됩니다.

Dialin – 전화 접속 회의 웹 페이지에 사용됩니다.

단순 URL은 단순 URL 구성 컬렉션에 저장됩니다. Lync Server를 설치하면 전역 컬렉션이 만들어지는데, 사이트 범위에서 사용자 지정 컬렉션을 만들 수도 있습니다. 이렇게 하면 사이트마다 다른 단순 URL을 사용할 수 있습니다.

단순 URL 구성 컬렉션은 **New-CsSimpleUrlConfiguration** cmdlet을 사용하여 만듭니다. 그런 다음 **New-CsSimpleUrl** cmdlet 및 **Set-CsSimpleUrlConfiguration** cmdlet과 같은 추가 cmdlet을 사용하여 단순 URL로 이러한 컬렉션을 채울 수 있습니다. 단순 URL 컬렉션을 업데이트한 후에는 **Enable-CsComputer** cmdlet을 실행해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsSimpleUrlConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsSimpleUrlConfiguration"}

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
<td><p>새 단순 URL 구성 컬렉션에 대한 고유 식별자입니다. 사이트 범위에서만 새 컬렉션을 만들 수 있으므로 Identity는 &quot;site:&quot; 접두사로 시작하고 그 뒤에 사이트 이름이 와야 합니다. 예를 들어 Redmond 사이트의 새 컬렉션을 만들려면 -Identity &quot;site:Redmond&quot; 구문을 사용합니다.</p></td>
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
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SimpleUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>이 컬렉션에 대해 구성된 단순한 URL입니다. 이러한 URL은 <strong>New-SimpleUrl</strong> cmdlet 및 <strong>New-SimpleUrlEntry</strong> cmdlet을 사용하여 만들어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>새 단순 URL 구성 설정이 만들어지는 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identification)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대한 테넌트 ID를 반환할 수 있습니다.</p>
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

없음.

## 반환 형식

**New-CsSimpleUrlConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SimpleUrl.SimpleUrlConfiguration 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsSimpleUrlConfiguration](get-cssimpleurlconfiguration.md)  
[New-CsSimpleUrl](new-cssimpleurl.md)  
[New-CsSimpleUrlEntry](new-cssimpleurlentry.md)  
[Remove-CsSimpleUrlConfiguration](remove-cssimpleurlconfiguration.md)  
[Set-CsSimpleUrlConfiguration](set-cssimpleurlconfiguration.md)

