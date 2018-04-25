---
title: Set-CsClientVersionPolicyRule
TOCTitle: Set-CsClientVersionPolicyRule
ms:assetid: 2e061fa8-bb1a-4382-bb0d-298f81aefb3d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425790(v=OCS.15)
ms:contentKeyID: 49303174
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsClientVersionPolicyRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

현재 조직에서 사용하도록 구성된 클라이언트 버전 정책 규칙을 하나 이상 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsClientVersionPolicyRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsClientVersionPolicyRule [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Action <Allow | AllowAndUpgrade | AllowWithUrl | Block | BlockAndUpgrade | BlockWithUrl>] [-ActionUrl <String>] [-BuildNumber <UInt16>] [-CompareOp <EQL | NEQ | GTR | GEQ | LSS | LEQ>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-MajorVersion <UInt16>] [-MinorVersion <UInt16>] [-Priority <Int32>] [-QfeNumber <UInt16>] [-UserAgent <String>] [-UserAgentFullName <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Identity가 site:Redmond/74ba9211-8610-42f9-91ba-846cdee98820인 클라이언트 버전 정책 규칙을 비활성화합니다. 규칙을 비활성화하기 위해 이 명령은 Enabled 매개 변수와 매개 변수 값 $False를 포함합니다.

    Set-CsClientVersionPolicyRule -Identity site:Redmond/74ba9211-8610-42f9-91ba-846cdee98820 -Enabled $False

## 예제 2

예제 2에서는 Redmond 사이트에 할당된 모든 클라이언트 버전 정책 규칙에 일반 설명을 추가합니다. 이 작업을 수행하기 위해 이 명령은 먼저 Filter 매개 변수와 함께 **Get-CsClientVersionPolicyRule** cmdlet을 호출합니다. 필터 값 "site:Redmond\*"는 Redmond 사이트에 할당된 정책 규칙에 대한 데이터만 반환되도록 제한합니다. 이 컬렉션은 컬렉션의 각 항목에 "Client policy rules for Redmond"라는 Description을 할당하는 **Set-CsClientVersionPolicyRule** cmdlet에 파이프됩니다.

    Get-CsClientVersionPolicyRule -Filter "site:Redmond*" | Set-CsClientVersionPolicyRule -Description "Client policy rules for Redmond"

## 예제 3

예제 3에서는 UCCP(Unified Communications Client Platform)를 사용자 에이전트로 참조하는 모든 클라이언트 버전 정책 규칙에 대해 UCCP 클라이언트 사용을 차단합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsClientVersionPolicyRule** cmdlet을 호출하여 현재 사용 중인 모든 클라이언트 정책 규칙의 컬렉션을 검색합니다. 이 컬렉션은 UserAgent 속성이 UCCP와 같은(-eq) 규칙만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목에 대해 Action 속성을 Block으로 설정하는 **Set-CsClientVersionPolicyRule** cmdlet에 파이프됩니다.

    Get-CsClientVersionPolicyRule | Where-Object {$_.UserAgent -eq "UCCP"} | Set-CsClientVersionPolicyRule -Action "Block"

## 자세한 정보

클라이언트 버전 규칙은 Lync Server에 로그온할 수 있는 클라이언트 응용 프로그램을 결정하는 데 사용됩니다. 사용자가 Lync Server에 로그온하려고 하면 클라이언트 응용 프로그램이 서버에 SIP 헤더를 전송합니다. 이 헤더에는 소프트웨어의 주 버전, 부 버전, 빌드 번호 등 응용 프로그램 자체에 대한 자세한 정보가 포함되어 있습니다. 그런 다음 클라이언트 버전 규칙 컬렉션과 버전 정보를 비교하여 특정 응용 프로그램에 적용되는 규칙이 있는지 확인합니다. 예를 들어 사용자가 Microsoft Office Communicator 2007 R2를 사용하여 로그온하려는 경우를 가정해 보겠습니다. 사용자가 Lync Server에 로그인하기 전에 시스템에서 Office Communicator 2007 R2에 적용되는 클라이언트 버전 규칙이 있는지 확인합니다. 규칙이 있으면 Lync Server에서 해당 규칙에 의해 지정된 작업을 수행합니다. 작업은 다음 중 하나여야 합니다.

Allow. 사용자에게 로그온이 허용됩니다.

AllowAndUpgrade. 사용자에게 로그온이 허용되고, 이 사용자의 Communicator 2007 R2가 최신 버전의 Lync로 자동으로 업그레이드됩니다. 업그레이드는 시스템 구성 방법에 따라 Microsoft Update 또는 Windows Server Update Services를 사용하여 수행됩니다.

AllowWithUrl. 사용자에게 로그온이 허용되고, 최신 버전의 Lync를 다운로드하여 설치할 수 있는 URL로 이동되는 메시지가 표시됩니다. 이 URL은 Lync Server를 설치할 때 자동으로 만들어진 사이트가 아니라 사용자가 만든 웹 사이트를 가리켜야 합니다.

Block. 사용자에게 로그온이 허용되지 않습니다.

BlockAndUpgrade. 사용자에게 로그온이 허용되지는 않지만, 이 사용자의 Communicator 2007 R2가 최신 버전의 Lync로 자동으로 업그레이드됩니다. 그러면 사용자가 새 클라이언트 응용 프로그램을 사용하여 로그온할 수 있습니다. 업그레이드는 시스템 구성 방법에 따라 Microsoft Update 또는 Windows Server Update Services를 사용하여 수행됩니다.

BlockWithUrl. 사용자에게 로그온이 허용되지는 않지만, 최신 버전의 Lync를 다운로드하여 설치할 수 있는 URL로 이동되는 메시지가 표시됩니다. 이 URL은 Lync Server를 설치할 때 자동으로 만들어진 사이트가 아니라 사용자가 만든 웹 사이트를 가리켜야 합니다.

클라이언트 버전 규칙은 전역 범위, 사이트 범위, 서비스 범위(등록자 서비스) 또는 사용자별 범위에서 구성할 수 있는 클라이언트 버전 정책에 수집됩니다. **Set-CsClientVersionPolicyRule** cmdlet을 사용하면 기존 클라이언트 버전 규칙의 속성을 수정할 수 있습니다.

클라이언트 버전 정책은 페더레이션 사용자에게 적용되지 않습니다. 대신 페더레이션 사용자에게는 조직에서 사용되는 클라이언트 버전 정책이 적용됩니다. 예를 들어 페더레이션 사용자가 클라이언트 A를 사용하고, 이 클라이언트가 페더레이션 조직에서 허용된다고 가정해 보겠습니다. 페더레이션 조직에서 클라이언트 A 사용을 허용하는 한 이 사용자는 해당 클라이언트를 사용하여 조직과 통신할 수 있습니다. 이는 클라이언트 버전 정책이 클라이언트 A 사용을 차단하는 경우에도 마찬가지입니다. 조직에서 시행되는 클라이언트 버전 정책은 페더레이션 조직에서 사용되는 클라이언트 버전 정책을 무시하지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsClientVersionPolicyRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsClientVersionPolicyRule"}

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
<tr class="even">
<td><p><em>ActionUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>사용자가 최신 버전의 Lync를 다운로드할 수 있는 URL입니다. 이 속성은 Action을 BlockWithUrl 또는 AllowWithUrl로 설정한 경우에 필요합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>BuildNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>소프트웨어의 빌드 번호입니다. 예를 들어 사용하는 Communicator의 버전이 2.0.6362.111인 경우 BuildNumber는 6362입니다. 빌드 번호는 개발 과정에서 만들어지는 소프트웨어의 내부 버전을 나타내며, 사용 중인 버전이 시험판 버전이 아니라 최종 릴리스 버전인지 확인하는 데 도움이 됩니다.</p></td>
</tr>
<tr class="even">
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
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 클라이언트 버전 규칙에 대한 추가 정보를 제공할 수 있습니다. 예를 들어 규칙을 변경해야 하는 경우 연락할 사람에 대한 정보를 설명에 포함할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>클라이언트 버전 규칙의 사용 여부를 나타냅니다. Enabled 속성을 False로 설정하면 사용자가 지정된 소프트웨어로 로그온하려고 할 때 규칙이 무시됩니다. 기본값은 True입니다.</p></td>
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
<td><p>수정할 클라이언트 버전 정책 규칙의 고유 식별자입니다. 클라이언트 버전 규칙의 ID는 규칙이 구성된 범위와 GUID(Globally Unique Identifier)로 구성됩니다. 따라서 규칙 ID는 site:Redmond/1987d3c2-4544-489d-bbe3-59f79f530a83과 유사합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>규칙 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MajorVersion</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>소프트웨어의 주 버전입니다. 예를 들어 사용하는 Communicator의 버전이 2.0.6362.111인 경우 MajorVersion은 2입니다. 주 버전은 소프트웨어의 기본 버전과 같습니다.</p></td>
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
<td><p>규칙의 상대 우선 순위입니다. 규칙은 우선 순위 순서대로 처리되므로 우선 순위가 0인 규칙이 첫 번째로 처리되고 우선 순위가 1인 규칙이 두 번째로 처리됩니다. 이미 사용 중인 우선 순위를 할당하면 새 규칙이 해당 우선 순위를 사용하고 다른 규칙의 번호가 적절하게 다시 매겨집니다.</p></td>
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
<td><p>소프트웨어 클라이언트를 식별하는 데 사용되는 지정자입니다. 예를 들어 OC는 Communicator의 사용자 에이전트 지정입니다. <strong>Get-CsClientVersionConfiguration</strong> cmdlet은 각 사용자 에이전트 지정에 해당하는 대화명을 제공합니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.Rule 개체입니다. **Set-CsClientVersionPolicyRule** cmdlet은 클라이언트 버전 규칙 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsClientVersionPolicyRule** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.Rule 개체의 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClientVersionPolicyRule](get-csclientversionpolicyrule.md)  
[New-CsClientVersionPolicyRule](new-csclientversionpolicyrule.md)  
[Set-CsClientVersionPolicyRule](set-csclientversionpolicyrule.md)

