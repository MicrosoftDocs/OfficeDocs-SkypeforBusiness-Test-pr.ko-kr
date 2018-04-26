---
title: New-CsClientVersionPolicyRule
TOCTitle: New-CsClientVersionPolicyRule
ms:assetid: d28df005-0db0-4b17-9ca0-9dc9ed063d73
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398905(v=OCS.15)
ms:contentKeyID: 49305124
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsClientVersionPolicyRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 클라이언트 버전 정책 규칙을 만듭니다. 클라이언트 버전 정책 규칙은 사용자가 특정 클라이언트 응용 프로그램을 사용하여 Lync Server에 로그온할 수 있는지 여부를 결정하는 데 도움이 됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsClientVersionPolicyRule -Identity <XdsIdentity> <COMMON PARAMETERS>

    New-CsClientVersionPolicyRule -Parent <String> -RuleId <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Action <Allow | AllowAndUpgrade | AllowWithUrl | Block | BlockAndUpgrade | BlockWithUrl>] [-ActionUrl <String>] [-BuildNumber <UInt16>] [-CompareOp <EQL | NEQ | GTR | GEQ | LSS | LEQ>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MajorVersion <UInt16>] [-MinorVersion <UInt16>] [-Priority <Int32>] [-QfeNumber <UInt16>] [-UserAgent <String>] [-UserAgentFullName <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1은 새 클라이언트 버전 정책 규칙을 만드는 방법을 보여 줍니다. 정책 규칙에는 알림을 할당할 범위와 36자로 된 GUID의 두 부분으로 구성된 ID가 있습니다. 새 클라이언트 버전 정책 규칙의 ID를 먼저 만들려면 .NET Framework 메서드인 NewGuid를 사용하여 새 GUID를 만들어야 합니다. 이 단계는 예제의 첫 번째 명령을 수행하는 단계이며, 결과 GUID는 변수 $x에 저장됩니다.

GUID를 만든 후에는 **New-CsClientVersionPolicyRule** cmdlet을 사용하여 새 규칙을 만들 수 있습니다. 이 명령은 네 가지 매개 변수를 사용합니다. 즉, 새 규칙의 범위(site:Redmond)를 나타내는 매개 변수 값을 사용하는 Parent, 매개 변수 값 $x를 사용하는 RuleId(새로 만든 GUID를 나타냄), MajorVersion(4), UserAgent(InHouse)를 사용합니다. 이 경우 UserAgent 매개 변수는 사내 클라이언트 응용 프로그램을 나타냅니다.

    $x = [guid]::NewGuid()
    
    New-CsClientVersionPolicyRule -Parent "site:Redmond" -RuleId $x -MajorVersion 4 -UserAgent InHouse

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령이 변형된 것입니다. 그러나 이 경우에는 새 규칙이 처음에 메모리에만 만들어지고 나중에 Lync Server에 추가됩니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 ID의 GUID 부분을 만듭니다. 두 번째 명령에서는 메모리에만 나타나는 새로운 클라이언트 버전 정책 규칙이 만들어집니다. InMemory 매개 변수는 규칙이 메모리에만 존재하고 Lync Server 인프라에 즉시 추가되지 않도록 합니다. 예제 1에서와 마찬가지로 Parent 및 RuleId 매개 변수를 사용하여 규칙 ID를 지정하는 두 부분인 새 규칙의 범위와 GUID를 지정합니다.

가상 규칙을 만든 후에는 다음 두 명령을 사용하여 MajorVersion 및 UserAgent 속성에 각각 값을 할당합니다. 해당 작업이 완료되면 예제의 마지막 명령 및 **Set-CsClientVersionPolicyRule** cmdlet을 사용하여 실제 클라이언트 버전 정책 규칙을 만들고 이 규칙을 Redmond 사이트에 할당합니다.

    $x = [guid]::NewGuid()
    
    $z = New-CsClientVersionPolicyRule -Parent "site:Redmond" -RuleId $x -InMemory
    $z.MajorVersion = 4 
    $z.UserAgent = "Inhouse"
    Set-CsClientVersionPolicyRule -Instance $z

## 자세한 정보

클라이언트 버전 정책 규칙은 Lync Server에 로그온할 수 있는 클라이언트 응용 프로그램을 결정하는 데 사용됩니다. 사용자가 Lync Server에 로그온하려고 하면 클라이언트 응용 프로그램이 서버에 SIP 헤더를 전송합니다. 이 헤더에는 소프트웨어의 주 버전, 부 버전, 빌드 번호 등 응용 프로그램 자체에 대한 자세한 정보가 포함되어 있습니다. 그 다음에는 버전 정보를 클라이언트 버전 규칙의 컬렉션과 대조하여 해당하는 특정 응용 프로그램에 적용되는 규칙이 있는지 확인합니다. 예를 들어 사용자가 Microsoft Office Communicator 2007 R2를 사용하여 로그온하려는 경우를 가정해 보겠습니다. 사용자가 Lync Server에 로그인하기 전에 시스템에서 Office Communicator 2007 R2에 적용되는 클라이언트 버전 규칙이 있는지 확인합니다. 규칙이 있으면 Lync Server에서 해당 규칙에 의해 지정된 작업을 수행합니다. 해당 동작은 다음 중 하나여야 합니다.

Allow. 사용자에게 로그온이 허용됩니다.

AllowAndUpgrade. 사용자에게 로그온이 허용되고, 이 사용자의 Communicator 2007 R2가 최신 버전의 Lync로 자동으로 업그레이드됩니다. 업그레이드는 시스템 구성 방법에 따라 Microsoft Update 또는 Windows Server Update Services를 사용하여 수행됩니다.

AllowWithUrl. 사용자에게 로그온이 허용되고, 최신 버전의 Lync를 다운로드하여 설치할 수 있는 URL로 이동되는 메시지가 표시됩니다. 이 URL은 Lync Server를 설치할 때 자동으로 만들어진 사이트가 아니라 사용자가 만든 웹 사이트를 가리켜야 합니다.

Block. 사용자에게 로그온이 허용되지 않습니다.

BlockAndUpgrade. 사용자에게 로그온이 허용되지는 않지만, 이 사용자의 Communicator 2007 R2가 최신 버전의 Lync로 자동으로 업그레이드됩니다. 그러면 사용자가 새 클라이언트 응용 프로그램을 사용하여 로그온할 수 있습니다. 업그레이드는 시스템 구성 방법에 따라 Microsoft Update 또는 Windows Server Update Services를 사용하여 수행됩니다.

BlockWithUrl. 사용자에게 로그온이 허용되지는 않지만, 최신 버전의 Lync를 다운로드하여 설치할 수 있는 URL로 이동되는 메시지가 표시됩니다. 이 URL은 Lync Server를 설치할 때 자동으로 만들어진 사이트가 아니라 사용자가 만든 웹 사이트를 가리켜야 합니다.

클라이언트 버전 정책 규칙은 전역 범위, 사이트 범위, 서비스 범위(등록자 서비스) 또는 사용자별 범위에서 구성할 수 있는 클라이언트 버전 정책에서 수집됩니다. 새 클라이언트 버전 규칙은 **New-CsClientVersionPolicyRule** cmdlet을 사용하여 만듭니다. 새 규칙을 만들 때는 해당 규칙의 ID도 지정해야 합니다. 이 ID는 범위(예: site:Redmond) 및 GUID(Globally Unique Identifier)로 구성됩니다. ID 자체를 조합하거나 범위(Parent 매개 변수) 및 GUID(RuleId 매개 변수)를 제공하고 **New-CsClientVerisonPolicyRule** cmdlet을 사용하여 사용자의 ID를 만들 수도 있습니다.

클라이언트 버전 정책은 페더레이션 사용자에게 적용되지 않습니다. 대신 페더레이션 사용자에게는 조직에서 사용되는 클라이언트 버전 정책이 적용됩니다. 예를 들어 페더레이션 사용자가 클라이언트 A를 사용하고, 이 클라이언트가 페더레이션 조직에서 허용된다고 가정해 보겠습니다. 페더레이션 조직에서 클라이언트 A 사용을 허용하는 한 이 사용자는 해당 클라이언트를 사용하여 조직과 통신할 수 있습니다. 이는 클라이언트 버전 정책이 클라이언트 A 사용을 차단하는 경우에도 마찬가지입니다. 조직에서 시행되는 클라이언트 버전 정책은 페더레이션 조직에서 사용되는 클라이언트 버전 정책을 무시하지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsClientVersionPolicyRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsClientVersionPolicyRule"}

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
<td><p>만들 클라이언트 버전 정책 규칙의 고유 식별자입니다. 클라이언트 버전 정책 규칙의 ID는 규칙이 구성된 범위 및 GUID(Globally Unique Identifier)로 구성됩니다. 즉, 규칙의 ID는 site:Redmond/1987d3c2-4544-489d-bbe3-59f79f530a83과 유사한 형태가 됩니다.</p>
<p>Identity 매개 변수를 사용하는 대신 Parent 및 RuleId 매개 변수를 사용하여 <strong>New-CsClientVerisonPolicyRule</strong> cmdlet을 통해 ID를 만들 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Parent</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 규칙의 범위 정보입니다. Parent 매개 변수를 사용하여 전역 정책의 새 규칙을 만들려면 -Parent global 구문을 사용하십시오. 사이트 정책의 새 규칙을 만들려면 -Parent &quot;site:Redmond&quot;와 유사한 구문을 사용하십시오. 서비스 정책의 새 규칙을 만들려면 -parent &quot;Registrar:atl-cs-001.litwareinc.com&quot;과 유사한 구문을 사용하십시오. 사용자별 정책의 새 규칙을 만들려면 -Parent &quot;RedmondClientVersionPolicy&quot;와 유사한 구문을 사용하십시오.</p>
<p>새 규칙을 만들 때는 Identity 매개 변수를 사용하거나 Parent 및 RuleId 매개 변수를 사용해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RuleId</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>규칙의 GUID(Globally Unique Identifier)입니다. Windows PowerShell에서 GUID를 만들려면</p>
<p>$x = [guid]::NewGuid() 명령을 사용하면 됩니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Action</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.Action</p></td>
<td><p>규칙이 트리거될 때마다, 즉 지정된 소프트웨어를 사용하여 로그온하려고 할 때마다 수행되는 동작입니다. 사용할 수 있는 값은 다음과 같습니다.</p>
<p>Allow. 사용자에게 로그온이 허용됩니다.</p>
<p>AllowWithUrl. 사용자에게 로그온이 허용되고, 최신 버전의 Lync를 다운로드하여 설치할 수 있는 URL을 가리키는 메시지가 표시됩니다.</p>
<p>AllowAndUpgrade. 사용자에게 로그온이 허용되고, 이 사용자의 Communicator가 최신 버전의 Lync로 자동으로 업그레이드됩니다.</p>
<p>Block. 사용자에게 로그온이 허용되지 않습니다.</p>
<p>BlockWithUrl. 사용자에게 로그온이 허용되지는 않지만, 최신 버전의 Lync를 다운로드하여 설치할 수 있는 URL로 이동되는 메시지가 표시됩니다.</p>
<p>BlockAndUpgrade. 사용자에게 로그온이 허용되지는 않지만, 이 사용자의 Communicator가 최신 버전의 Lync로 자동으로 업그레이드됩니다. 그러면 사용자가 새 클라이언트 응용 프로그램을 사용하여 로그온할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ActionUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>사용자가 최신 버전의 Lync를 다운로드할 수 있는 URL입니다. 이 속성은 Action을 BlockWithUrl 또는 AllowWithUrl로 설정한 경우에 필요합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>BuildNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>소프트웨어의 빌드 번호입니다. 예를 들어 사용하는 Communicator의 버전이 2.0.6362.111인 경우 BuildNumber는 6362입니다. 빌드 번호는 개발 과정에서 만들어지는 소프트웨어의 내부 버전을 나타내며, 사용 중인 버전이 시험판 버전이 아니라 최종 릴리스 버전인지 확인하는 데 도움이 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>CompareOp</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.CompareOp</p></td>
<td><p>로그온하려는 클라이언트 소프트웨어가 규칙에 지정된 버전보다 이전, 이후 또는 동시에 릴리스되었는지 여부를 확인하는 데 사용되는 비교 연산자입니다. 사용할 수 있는 값은 다음과 같습니다.</p>
<p>EQL(같음)</p>
<p>NEQ(같지 않음)</p>
<p>GTR(보다 큼)</p>
<p>GEQ(크거나 같음)</p>
<p>LSS(보다 작음)</p>
<p>LEQ(작거나 같음)</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 클라이언트 버전 규칙에 대한 추가 정보를 제공할 수 있습니다. 예를 들어 규칙을 변경해야 하는 경우 연락할 사람에 대한 정보를 설명에 포함할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>클라이언트 버전 규칙을 사용할지 여부를 나타냅니다. Enabled 속성을 False($False)로 설정한 경우에는 사용자가 지정된 소프트웨어로 로그온하려 할 때 규칙이 무시됩니다. 기본값은 True입니다.</p></td>
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
<td><p><em>MajorVersion</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>소프트웨어의 주 버전입니다. 예를 들어 사용하는 Communicator의 버전이 2.0.6362.111인 경우 MajorVersion은 2입니다. 주 버전은 소프트웨어의 기본 버전과 같습니다. 새 규칙을 만들 때마다 MajorVersion 속성에 값을 할당해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MinorVersion</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>소프트웨어의 부 버전입니다. 예를 들어 사용하는 Communicator의 버전이 2.0.6362.111인 경우 MinorVersion은 0입니다. 부 버전은 소프트웨어의 중간 버전과 같습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Priority</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>규칙의 상대적인 우선 순위입니다. 규칙은 우선 순위 순서에 따라 처리됩니다. 즉, 우선 순위가 0인 규칙이 먼저 처리되고 우선 순위가 1인 규칙이 두 번째로 처리되는 식입니다. 이미 사용 중인 우선 순위를 할당하면 새 규칙은 해당 우선 순위를 사용하고 다른 규칙은 그에 따라 순서가 다시 정해집니다.</p></td>
</tr>
<tr class="even">
<td><p><em>QfeNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>소프트웨어의 빠른 픽스 엔지니어링 번호입니다. 예를 들어 사용하는 Communicator의 버전이 2.0.6362.111인 경우 QfeNumber는 111입니다. QFE 번호는 소프트웨어의 공식 릴리스 후에 사용할 수 있는 계획된 응용 프로그램 업데이트를 나타냅니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserAgent</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>소프트웨어 클라이언트를 식별하는 데 사용되는 지정자입니다. 예를 들어 OC는 Communicator의 사용자 에이전트 지정입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserAgentFullName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 사용자 에이전트의 알기 쉬운 이름을 지정하는 데 사용됩니다. 예를 들어 관리자는 사용자 에이전트 UCCP를 사용하여 에이전트를 식별하는 대신 전체 이름(Microsoft Unified Communications Client)을 쓸 수 있습니다.</p></td>
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

없음. **New-CsClientVersionPolicyRule** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsClientVersionPolicyRule** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.Rule 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsClientVersionPolicyRule](get-csclientversionpolicyrule.md)  
[Remove-CsClientVersionPolicyRule](remove-csclientversionpolicyrule.md)  
[Set-CsClientVersionPolicyRule](set-csclientversionpolicyrule.md)

