---
title: Set-CsRoutingConfiguration
TOCTitle: Set-CsRoutingConfiguration
ms:assetid: ab69c6e8-262a-4ecb-b1af-513383c494fe
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412811(v=OCS.15)
ms:contentKeyID: 49304689
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsRoutingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

음성 경로의 목록을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsRoutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsRoutingConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-EnableLocationBasedRouting <$true | $false>] [-Force <SwitchParameter>] [-Route <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 경로 지정 구성 내의 음성 경로를 수정하기 위해 여러 단계를 거칩니다. 먼저 **Get-CsRoutingConfiguration** cmdlet을 호출하여 경로 지정 구성 개체를 검색합니다. 검색된 개체(하나만 있음)를 변수 $a에 할당합니다.

이 예제의 둘째 줄에서는 음성 경로 개체의 컬렉션인 변수 $a에서 Route 속성의 내용을 검색합니다. 그런 다음, 문자열 LocalRoute와 일치하는 Name을 가진 모든 음성 경로 개체에 대한 컬렉션을 검색하기 위해 해당 컬렉션을 **Where-Object** cmdlet에 파이프합니다. 해당 개체는 변수 $b에 할당됩니다.

다음으로 값 $False를 속성 SuppressCallerId에 할당하여 LocalRoute 음성 경로를 수정합니다. 해당 개체를 업데이트하여 변수 $a에서 개체를 업데이트했습니다. 그러나 해당 개체는 여전히 메모리에만 있습니다. 마지막 단계에서는 $a를 **Set-CsRoutingConfiguration** cmdlet의 Instance 매개 변수에 전달하여 이러한 변경 내용을 저장해야 합니다.

이 방법을 사용하여 경로 지정 구성을 수정하지 않는 것이 좋습니다. 경로 지정 구성을 수정하려면 다음과 같은 **Set-CsVoiceRoute** cmdlet을 사용하여 개별 음성 경로를 변경하기만 하면 됩니다.

Set-CsVoiceRoute -Identity LocalRoute -SuppressCallerId $False

한 줄의 명령으로 예제 1에 표시된 것과 동일한 작업을 수행할 수 있습니다.

    $a = Get-CsRoutingConfiguration
    $b = $a.Route | Where-Object {$_.Name -match "LocalRoute"}
    $b.SuppressCallerId = $False
    Set-CsRoutingConfiguration -Instance $a

## 자세한 정보

음성 경로는 Enterprise Voice 사용자의 통화를 PSTN(공중 전화망) 또는 PBX(Private Branch Exchange)의 전화 번호로 경로 지정하는 방법을 Lync Server에 지정하는 명령을 포함합니다. 이 cmdlet을 사용하여 Lync Server 배포 내에 정의된 모든 음성 경로의 설정을 수정할 수 있습니다.

이 cmdlet은 사용하지 않는 것이 좋습니다. 경로 지정 구성을 수정하려면 **Set-CsVoiceRoute** cmdlet을 호출하여 개별 음성 경로를 수정합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsRoutingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsRoutingConfiguration"}

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
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableLocationBasedRouting</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>True로 설정하면 전화를 거는 사용자와 받는 사용자의 위치를 모두 고려하여 음성 라우팅을 관리합니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Xds ID</p></td>
<td><p>경로 지정 구성의 범위입니다. Global이어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>PSTN 경로 지정 설정</p></td>
<td><p>라우팅 구성(Microsoft.Rtc.Management.WritablConfig.Policy.Voice.PstnRoutingSettings) 개체입니다. 이 유형의 개체는 <strong>Get-CsRoutingConfiguration</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Route</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>Lync Server 배포에 대해 정의된 모든 음성 경로(Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route 개체)의 목록입니다.</p>
<p><strong>Set-CsVoiceRoute</strong> cmdlet을 사용하여 개별 음성 경로 개체를 수정해야 합니다. 이 목록의 경로를 수정할 때 이 방법을 사용하는 것이 좋습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.WritableConfig.Management.Policy.Voice.PSTNRoutingSettings 개체입니다. 경로 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsRoutingConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnRoutingSettings 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[New-CsRoutingConfiguration](new-csroutingconfiguration.md)  
[Remove-CsRoutingConfiguration](remove-csroutingconfiguration.md)  
[Get-CsRoutingConfiguration](get-csroutingconfiguration.md)  
[Set-CsVoiceRoute](set-csvoiceroute.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)

