---
title: Set-CsVoiceRoute
TOCTitle: Set-CsVoiceRoute
ms:assetid: b786aec0-946e-4ce5-812e-25e5d8cfa4d5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412893(v=OCS.15)
ms:contentKeyID: 49304814
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsVoiceRoute

 

_**마지막으로 수정된 항목:** 2015-03-09_

음성 경로를 수정합니다. 음성 경로는 Enterprise Voice 사용자의 통화를 PSTN(공중 전화망) 또는 PBX(Private Branch Exchange)의 전화 번호로 경로 지정하는 방법을 Lync Server에 지정하는 명령을 포함합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsVoiceRoute [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsVoiceRoute [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AlternateCallerId <String>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-NumberPattern <String>] [-Priority <Int32>] [-PstnGatewayList <PSListModifier>] [-PstnUsages <PSListModifier>] [-SuppressCallerId <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 명령은 Route1 음성 경로의 Description을 "Test Route"로 설정합니다.

    Set-CsVoiceRoute -Identity Route1 -Description "Test Route"

## 예제 2

이 예제의 명령은 ID가 Route1인 음성 경로를 수정하여 PSTN 사용법 Long Distance를 이 음성 경로에 대한 사용법 목록에 추가합니다. Long Distance는 **Get-CsPstnUsage** cmdlet을 호출하여 검색할 수 있는 전역 PSTN 사용법 목록에 포함되어야 합니다.

    Set-CsVoiceRoute -Identity Route1 -PstnUsages @{add="Long Distance"}

## 예제 3

이 예제에서는 Route1이라는 음성 경로를 수정하여 해당 경로의 PSTN 사용법 목록을 조직의 모든 기존 사용법으로 채웁니다. 이 예제의 첫 번째 명령은 전역 PSTN 사용법의 목록을 검색합니다. **Get-CsPstnUsage** cmdlet에 대한 호출이 괄호로 묶여 있으므로 먼저 PSTN 사용법 정보가 포함된 개체가 검색됩니다. 전역 PSTN 사용법이 하나만 있으므로 개체가 하나만 검색됩니다. 그런 다음, 이 개체의 Usage 속성이 검색됩니다. PSTN 사용법 목록을 포함하는 해당 속성은 변수 $x에 할당됩니다. 이 예제의 둘째 줄에서는 ID가 Route1인 음성 경로를 수정하기 위해 **Set-CsVoiceRoute** cmdlet을 호출합니다. PstnUsages 매개 변수에 @{replace=$x} 값이 전달됩니다. 이 값은 이 경로의 PstnUsages 목록에 있는 모든 내용을 첫 줄에서 검색된 PSTN 사용법 목록을 포함하는 $x의 내용으로 대체하도록 지시합니다.

    $x = (Get-CsPstnUsage).Usage
    Set-CsVoiceRoute -Identity Route1 -PstnUsages @{replace=$x}

## 예제 4

이 명령 집합은 ID가 Route1인 음성 경로의 Name 속성을 RouteA로 변경합니다. Name 속성을 변경하면 Identity 속성이 자동으로 변경됩니다(이 경우에는 RouteA로).

첫째 줄에서는 ID가 Route1인 음성 경로를 검색하기 위해 **Get-CsVoiceRoute** cmdlet을 호출합니다. 반환된 개체는 변수 $x에 저장됩니다. 다음으로 해당 개체의 Name 속성이 문자열 값 "RouteA"에 할당됩니다. 마지막으로 변경을 수행하기 위해 변수 $x에 포함된 개체가 **Set-CsVoiceRoute** cmdlet의 Instance 매개 변수에 전달됩니다.

    $x = Get-CsVoiceRoute -Identity Route1
    $x.Name = "RouteA"
    Set-CsVoiceRoute -Instance $x

## 예제 5

이 예제에서는 Route1이라는 음성 경로를 수정하여 해당 경로의 PSTN 게이트웨이 목록(PstnGatewayList)을 ID가 PstnGateway:192.168.0.100인 게이트웨이의 서버 역할로 채웁니다. 이 예제의 첫째 줄에서는 **Get-CsVoiceRoute** cmdlet을 호출하여 수정할 음성 경로(여기서는 Route1)를 검색합니다. 다음으로 Route1의 PstnGatewayList 속성에서 Add 메서드를 호출합니다. 추가할 서비스의 Identity를 Add 메서드에 전달합니다. 마지막으로 **Set-CsVoiceRoute** cmdlet을 호출하고 Instance 매개 변수에 변수 $y를 전달하면 $y에 저장된 Route1이 새로 추가된 PSTN 게이트웨이로 업데이트됩니다.

    $y = Get-CsVoiceRoute -Identity Route1
    $y.PstnGatewayList.Add("PstnGateway:192.168.0.100")
    Set-CsVoiceRoute -Instance $y

## 자세한 정보

이 cmdlet을 사용하여 기존 음성 경로를 수정합니다. 음성 경로는 PSTN(공중 전화망) 사용을 통해 음성 정책과 연결됩니다. 음성 경로는 지정된 음성 경로를 통해 경로 지정되는 전화 번호를 식별하는 정규식을 포함합니다. 정규식과 일치하는 전화 번호가 이 경로를 통해 경로 지정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsVoiceRoute** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoiceRoute"}

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
<td><p>이 전화 경로의 목적에 대한 설명입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>음성 경로의 고유한 ID입니다. (Test Route와 같이 경로 이름에 공백이 포함된 경우 전체 문자열을 괄호로 묶어야 합니다.)</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>경로</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다. 이 개체의 유형은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route여야 하며, <strong>Get-CsVoiceRoute</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NumberPattern</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 경로가 적용되는 전화 번호를 지정하는 정규식입니다. 이 패턴과 일치하는 번호는 나머지 경로 지정 설정에 따라 경로 지정됩니다. 예를 들어 기본 번호 패턴 [0-9]{10}은 0-9 사이의 숫자를 포함하는 10자리 번호를 지정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Priority</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>여러 음성 경로를 확인할 수 있는 숫자입니다. 우선 순위는 둘 이상의 경로를 사용할 수 있는 경우 적용할 경로의 순서를 결정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PstnGatewayList</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>중재 서버는 여러 개의 게이트웨이와 연관될 수 있습니다. 이 매개 변수는 이 음성 경로와 연관된 게이트웨이의 목록을 포함합니다. 이 목록의 각 구성원은 PSTN 게이트웨이 또는 중재 서버의 서비스 ID여야 합니다. 중재 서버가 Microsoft Office Communications Server 2007 또는 Microsoft Office Communications Server 2007 R2를 사용하도록 구성된 경우에만 값이 중재 서버를 참조할 수 있습니다. Lync Server의 경우 PSTN 게이트웨이를 사용해야 합니다. 서비스 ID는 ServiceRole:FQDN 형식의 문자열입니다. 여기서 ServiceRole은 서비스 역할의 이름(PSTNGateway)이고, FQDN은 풀의 FQDN(정규화된 도메인 이름) 또는 서버의 IP 주소입니다(예: MediationServer:redmondpool.litwareinc.com). 서비스 ID는 Get-CsService | Select-Object Identity 명령을 호출하여 검색할 수 있습니다.</p>
<p>음성 경로를 변경하고 PstnGatewayList 목록을 빈 상태로 두거나 목록의 모든 항목을 제거하면 사용자가 PSTN으로 통화할 수 없음을 알리는 경고 메시지가 나타납니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PstnUsages</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>이 음성 경로에 적용할 수 있는 PSTN 사용(예: Local 또는 Long Distance)의 목록입니다. PSTN 사용은 이전 사용이어야 합니다. <strong>Get-CsPstnUsage</strong> cmdlet을 호출하여 PSTN 사용을 검색할 수 있습니다.</p>
<p>음성 경로를 변경하고 PstnUsages 목록을 빈 상태로 두거나 목록의 모든 PSTN 사용법을 제거하면 사용자가 PSTN으로 통화할 수 없음을 알리는 경고 메시지가 나타납니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SuppressCallerId</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>아웃바운드 호출에서 호출자 ID가 표시되는지 여부를 결정합니다. 이 매개 변수가 True로 설정된 경우 호출자 ID가 표시되지 않습니다. 실제 ID 대신에 AlternateCallerId의 값이 표시됩니다. SuppressCallerId를 True로 설정한 경우 AlternateCallerId 값을 제공해야 합니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route 개체입니다. **Set-CsVoiceRoute** cmdlet은 음성 경로 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsVoiceRoute** cmdlet은 값이나 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoiceRoute](new-csvoiceroute.md)  
[Remove-CsVoiceRoute](remove-csvoiceroute.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)  
[Test-CsVoiceRoute](test-csvoiceroute.md)  
[Get-CsPstnUsage](get-cspstnusage.md)  
[Get-CsService](get-csservice.md)

