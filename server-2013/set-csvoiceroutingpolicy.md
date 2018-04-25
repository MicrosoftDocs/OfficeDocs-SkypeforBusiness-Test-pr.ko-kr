---
title: Set-CsVoiceRoutingPolicy
TOCTitle: Set-CsVoiceRoutingPolicy
ms:assetid: cff51726-88c6-4cdf-aaad-a7246c4408c5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205313(v=OCS.15)
ms:contentKeyID: 49305098
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsVoiceRoutingPolicy

 

_**마지막으로 수정된 항목:** 2015-05-28_

기존 음성 라우팅 정책을 수정합니다. 음성 라우팅 정책은 하이브리드 음성 사용자에 대한 PSTN 사용을 관리합니다. 비즈니스용 Skype Online에 있는 사용자는 하이브리드 음성을 통해 온-프레미스 Lync Server 2013 설치에서 제공되는 Enterprise Voice 기능을 사용할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsVoiceRoutingPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsVoiceRoutingPolicy [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-Name <String>] [-PstnUsages <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 사용자별 음성 라우팅 정책 RedmondVoiceRoutingPolicy에 PSTN 사용 "Long Distance"를 추가합니다.

    Set-CsVoiceRoutingPolicy -Identity "RedmondVoiceRoutingPolicy" -PstnUsages @{Add="Long Distance"}

## 예제 2

예제 2에서는 사용자별 음성 라우팅 정책 RedmondVoiceRoutingPolicy에서 PSTN 사용 "Local"을 제거합니다.

    Set-CsVoiceRoutingPolicy -Identity "RedmondVoiceRoutingPolicy" -PstnUsages @{Remove="Local"}

## 예제 3

예제 3에서는 PSTN 사용 "Local"을 해당 사용이 포함된 모든 음성 라우팅 정책에서 제거합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsVoiceRoutingPolicy** cmdlet을 호출하여 사용 가능한 모든 음성 라우팅 정책의 컬렉션을 반환합니다. 해당 컬렉션은 Where-Object cmdlet에 파이프되며, 이 cmdlet은 PstnUsages 속성에 "Local" 사용이 포함된(-contains) 정책만 선택합니다. 이러한 정책은 **Set-CsVoiceRoutingPolicy** cmdlet에 파이프되며, 해당 cmdlet은 각 정책에서 Local 사용을 삭제합니다.

    Get-CsVoiceRoutingPolicy | Where-Object {$_.PstnUsages -contains "Local"} | Set-CsVoiceRoutingPolicy -PstnUsages @{Remove="Local"}

## 자세한 정보

음성 라우팅 정책은 "하이브리드" 시나리오, 즉 일부 사용자는 온-프레미스 버전 Lync Server에 있고 나머지 사용자는 비즈니스용 Skype Online에 있는 시나리오에서 사용됩니다. 비즈니스용 Skype Online 사용자에게 음성 라우팅 정책을 할당하면 해당 사용자가 온-프레미스 SIP 트렁크를 사용하여 공중 전화망에서 전화를 받고 공중 전화망으로 전화를 걸 수 있습니다.

단순히 사용자에게 음성 라우팅 정책을 할당한다고 해서 해당 사용자가 비즈니스용 Skype Online을 통해 PSTN 전화를 할 수 있는 것은 아닙니다. 먼저 이러한 사용자들이 Enterprise Voice를 사용하도록 설정해야 하며 적절한 음성 정책 및 다이얼 플랜을 사용자에게 할당해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoiceRoutingPolicy"}

**Lync Server 제어판:** Set-CsVoiceRoutingPolicy cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<th>형식</th>
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
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 음성 라우팅 정책과 함께 표시할 설명 텍스트를 제공할 수 있습니다. 예를 들어 정책을 할당할 사용자에 대한 정보를 설명에 포함할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>생성될 때 정책에 할당된 고유 식별자입니다. 음성 라우팅 정책은 전역 범위 또는 사용자별 범위에 할당할 수 있습니다. 전역 인스턴스를 참조하려면 다음 구문을 사용합니다.</p>
<p>-Identity global</p>
<p>사용자별 정책을 참조하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;RedmondVoiceRoutingPolicy&quot;</p>
<p>ID를 지정하지 않으면 <strong>Set-CsVoiceRoutingPolicy</strong> cmdlet이 전역 정책을 수정하게 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 정책을 설명하는 알기 쉬운 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PstnUsages</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>이 음성 라우팅 정책에 적용할 수 있는 PSTN 사용(예: Local 또는 Long Distance)의 목록입니다. PSTN 사용은 기존 사용이어야 합니다. <strong>Get-CsPstnUsage</strong> cmdlet을 호출하여 PSTN 사용을 검색할 수 있습니다.</p></td>
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

**Set-CsVoiceRoutingPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceRoutingPolicy 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsVoiceRoutingPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceRoutingPolicy 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsVoiceRoutingPolicy](get-csvoiceroutingpolicy.md)  
[Grant-CsVoiceRoutingPolicy](grant-csvoiceroutingpolicy.md)  
[New-CsVoiceRoutingPolicy](new-csvoiceroutingpolicy.md)  
[Remove-CsVoiceRoutingPolicy](remove-csvoiceroutingpolicy.md)

