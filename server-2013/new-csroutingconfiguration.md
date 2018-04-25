---
title: New-CsRoutingConfiguration
TOCTitle: New-CsRoutingConfiguration
ms:assetid: ead67e35-b145-4041-ba3e-4b26c47cce1d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399056(v=OCS.15)
ms:contentKeyID: 49305416
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsRoutingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 cmdlet은 경로 지정 구성 개체에 대한 기본 설정을 포함하는 개체를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsRoutingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableLocationBasedRouting <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Route <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 명령은 기본 경로 지정 구성 값을 포함하는 개체를 만들고 해당 개체를 변수 $x에 할당합니다. 이 cmdlet을 다르게 사용하면 오류가 반환됩니다.

    $x = New-CsRoutingConfiguration -Identity global -InMemory

## 자세한 정보

경로 지정 구성은 Lync Server 배포 내에 정의된 모든 음성 경로에 대한 컨테이너입니다. 새 음성 경로를 만들려면 **New-CsVoiceRoute** cmdlet을 사용합니다.

경로 지정 구성은 전역 수준에서만 정의할 수 있습니다. 또한 개별적으로 이름이 지정된 경로 지정 구성을 가질 수 없습니다. 전체 Lync Server 배포에 대한 음성 경로 목록이 하나만 있습니다. Windows PowerShell의 Lync Server 구현에서는 New 동사로 시작하는 cmdlet을 호출하여 이미 존재하는 개체를 만들려고 하면 오류 메시지가 나타납니다. Lync Server의 모든 구현에는 Global ID를 가진 기본 경로 지정 구성 개체가 포함되어 있습니다. 이는 만들 수 있는 유일한 음성 경로 목록이 이미 있다는 것을 의미합니다. 따라서 **New-CsRoutingConfiguration** cmdlet을 호출하면 항상 오류 메시지가 반환되고 새 경로 지정 구성이 만들어지지 않습니다.

단, 이 cmdlet을 호출하면서 InMemory 매개 변수를 지정할 경우는 예외입니다. 이 경우에는 음성 경로의 기본 목록을 포함하는 개체가 메모리에만 만들어집니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsRoutingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsRoutingConfiguration"}

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
<td><p>경로 지정 구성의 범위입니다. 이 값은 Global이어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableLocationBasedRouting</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 전화를 거는 사용자와 받는 사용자의 위치를 모두 고려하여 음성 라우팅을 관리합니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경 내용을 적용하기 전에 표시될 수 있는 확인 메시지를 숨깁니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Route</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>Lync Server 배포에 대해 정의된 모든 음성 경로(Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route 개체)의 목록입니다.</p>
<p><strong>New-CsVoiceRoute</strong> cmdlet을 사용하여 음성 경로 개체를 만들 수 있습니다. 이 목록에 음성 경로를 추가하기 위해 이 방법을 사용하는 것이 좋습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnRoutingSettings 유형의 메모리 내부 개체를 만들 수 있습니다.

## 참고 항목

#### 기타 리소스

[Remove-CsRoutingConfiguration](remove-csroutingconfiguration.md)  
[Set-CsRoutingConfiguration](set-csroutingconfiguration.md)  
[Get-CsRoutingConfiguration](get-csroutingconfiguration.md)  
[New-CsVoiceRoute](new-csvoiceroute.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)

