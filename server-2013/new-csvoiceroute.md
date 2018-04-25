---
title: New-CsVoiceRoute
TOCTitle: New-CsVoiceRoute
ms:assetid: 1118f74f-b06c-41d2-8b1b-5cc1e1957b77
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398197(v=OCS.15)
ms:contentKeyID: 49302841
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsVoiceRoute

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 음성 경로를 만듭니다. 음성 경로는 Enterprise Voice 사용자의 통화를 PSTN(공중 전화망) 또는 PBX(Private Branch Exchange)의 전화 번호로 경로 지정하는 방법을 Lync Server에 지정하는 명령을 포함합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsVoiceRoute -Name <String> <COMMON PARAMETERS>

    New-CsVoiceRoute -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AlternateCallerId <String>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-NumberPattern <String>] [-Priority <Int32>] [-PstnGatewayList <PSListModifier>] [-PstnUsages <PSListModifier>] [-SuppressCallerId <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제의 명령은 ID가 Route1인 새 음성 경로를 만듭니다. 다른 모든 속성은 기본값으로 설정됩니다.

    New-CsVoiceRoute -Identity Route1

## 예제 2

이 예제의 명령은 ID가 Route1인 새 음성 경로를 만듭니다. 또한 사용법 목록에 PSTN 사용법 Long Distance를 추가하고, PSTN 게이트웨이 목록에 서비스 ID PstnGateway:redmondpool.litwareinc.com을 추가합니다.

    New-CsVoiceRoute -Identity Route1 -PstnUsages @{add="Long Distance"} -PstnGatewayList @{add="PstnGateway:redmondpool.litwareinc.com"}

## 예제 3

이 예제에서는 Route1이라는 새 음성 경로를 만들고 해당 경로의 PSTN 사용법 목록을 조직의 모든 기존 사용법으로 채웁니다. 이 예제의 첫 번째 명령은 전역 PSTN 사용법의 목록을 검색합니다. **Get-CsPstnUsage** cmdlet에 대한 호출이 괄호로 묶여 있으므로 먼저 PSTN 사용법 정보가 포함된 개체가 검색됩니다. ('global' PSTN 사용법이 한 개만 있으므로 개체가 한 개만 검색됩니다.) 그런 다음, 이 개체의 Usage 속성이 검색됩니다. 사용법 목록을 포함하는 해당 속성은 변수 $x에 할당됩니다. 이 예제의 둘째 줄에서는 새 음성 경로를 만들기 위해 **New-CsVoiceRoute** cmdlet이 호출됩니다. 이 음성 경로는 Route1이라는 ID를 가집니다. PstnUsages 매개 변수에 @{add=$x} 값이 전달됩니다. 이 값은 첫 줄에서 검색한 전화 사용법 목록에 포함된 $x의 내용을 이 경로의 PSTN 사용법 목록에 추가하도록 지시합니다.

    $x = (Get-CsPstnUsage).Usage
    New-CsVoiceRoute -Identity Route1 -PstnUsages @{add=$x}

## 자세한 정보

이 cmdlet을 사용하여 새 음성 경로를 만듭니다. 모든 음성 경로는 전역 범위에서 만들어집니다. 그러나 여러 개의 전역 음성 경로를 정의할 수 있습니다. 고유한 경로 이름이 필요한 Identity 매개 변수를 통해 이 작업을 수행합니다.

음성 경로는 PSTN 사용법을 통해 음성 정책과 연결됩니다. 음성 경로는 지정된 음성 경로를 통해 경로 지정되는 전화 번호를 식별하는 정규식을 포함합니다. 정규식과 일치하는 전화 번호가 이 경로를 통해 경로 지정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsVoiceRoute** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsVoiceRoute"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>음성 경로를 고유하게 식별하는 이름입니다. 음성 경로는 전역 범위에서만 정의할 수 있으므로 Identity는 단순히 경로에 제공할 이름입니다. 경로 이름에 공백을 포함할 수 있지만(예: Test Route) <strong>New-CsVoiceRoute</strong> cmdlet에 대한 호출에서 전체 문자열을 큰따옴표로 묶어야 합니다.</p>
<p>Identity가 지정된 경우 Name은 비워두어야 합니다. Identity 값이 Name에 할당됩니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>음성 경로의 고유한 이름입니다. 이 매개 변수가 설정된 경우 값이 음성 경로 Identity에 자동으로 적용됩니다. Identity 및 Name을 둘 다 지정할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AlternateCallerId</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>SuppressCallerId 매개 변수가 True로 설정된 경우 전화를 건 사람의 실제 번호가 아니라 AlternateCallerId 매개 변수 값이 전화를 받는 사람에게 표시됩니다. 이 번호는 유효한 번호여야 하고 조직 내의 사업부(예: 지원 또는 인사)를 나타내는 데 사용할 수 있습니다.</p>
<p>SuppressCallerId 매개 변수가 False로 설정된 경우 AlternateCallerId 매개 변수는 무시됩니다.</p>
<p>이 값은 정규식 (\+)?[1-9]\d*(;ext=[1-9]\d*)?와 일치해야 합니다. 즉, 값은 더하기 기호(+)로 시작할 수 있지만 반드시 그럴 필요는 없으며 임의의 숫자로 구성되어야 하고 뒤에 ;ext=로 시작하는 내선 번호와 임의의 숫자가 올 수 있습니다. (내선 번호를 포함할 경우 문자열을 큰따옴표로 묶어야 합니다.)</p></td>
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
<td><p>이 음성 경로의 목적에 대한 설명입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경 작업을 수행하기 전에 표시되는 모든 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NumberPattern</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 경로가 적용되는 전화 번호를 지정하는 정규식입니다. 이 패턴과 일치하는 번호는 나머지 경로 지정 설정에 따라 경로 지정됩니다.</p>
<p>기본값: [0-9]{10}</p></td>
</tr>
<tr class="odd">
<td><p><em>Priority</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>번호는 여러 음성 경로로 확인될 수 있습니다. 우선 순위는 둘 이상의 경로를 사용할 수 있는 경우 적용할 경로의 순서를 결정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PstnGatewayList</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>Lync Server에서 중재 서버는 여러 개의 게이트웨이와 연관될 수 있습니다. 이 매개 변수는 이 음성 경로와 연관된 게이트웨이의 목록을 포함합니다. 이 목록의 각 구성원은 PSTN 게이트웨이 또는 중재 서버의 서비스 ID여야 합니다. 중재 서버가 Microsoft Office Communications Server 2007 또는 Microsoft Office Communications Server 2007 R2를 사용하도록 구성된 경우에만 값이 중재 서버를 참조할 수 있습니다. Lync Server의 경우 PSTN 게이트웨이를 사용해야 합니다. 서비스 ID는 &lt;ServiceRole&gt;:&lt;FQDN&gt; 형식의 문자열입니다. 여기서 ServiceRole은 서비스 역할의 이름(PSTNGateway)이고, FQDN은 풀의 FQDN(정규화된 도메인 이름) 또는 서버의 IP 주소입니다(예: PSTNGateway:redmondpool.litwareinc.com). 서비스 ID는 Get-CsService | Select-Object Identity 명령을 호출하여 검색할 수 있습니다.</p>
<p>이 목록은 기본적으로 비어 있습니다. 그러나 새 음성 경로를 만들 때 이 매개 변수를 비워 두면 경고 메시지가 표시됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PstnUsages</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>이 음성 경로에 적용할 수 있는 PSTN 사용법(예: Local, Long Distance 등)의 목록입니다. PSTN 사용법은 기존 사용법이어야 합니다. (<strong>Get-CsPstnUsage</strong> cmdlet을 호출하여 PSTN 사용법을 검색할 수 있습니다.)</p>
<p>이 목록은 기본적으로 비어 있습니다. 그러나 새 음성 경로를 만들 때 이 매개 변수를 비워 두면 경고 메시지가 표시됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SuppressCallerId</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>아웃바운드 호출에서 호출자 ID가 표시되는지 여부를 결정합니다. 이 매개 변수가 True로 설정된 경우 호출자 ID가 표시되지 않습니다. 실제 ID 대신에 AlternateCallerId의 값이 표시됩니다. SuppressCallerId를 True로 설정하는 경우 AlternateCallerId의 값을 지정해야 합니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsVoiceRoute](remove-csvoiceroute.md)  
[Set-CsVoiceRoute](set-csvoiceroute.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)  
[Test-CsVoiceRoute](test-csvoiceroute.md)  
[Get-CsPstnUsage](get-cspstnusage.md)  
[Get-CsService](get-csservice.md)

