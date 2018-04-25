---
title: New-CsVoiceRoutingPolicy
TOCTitle: New-CsVoiceRoutingPolicy
ms:assetid: 9e5bd6f6-902f-4911-ab88-9abb581df7fd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205135(v=OCS.15)
ms:contentKeyID: 49304545
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsVoiceRoutingPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 음성 라우팅 정책을 만듭니다. 음성 라우팅 정책은 하이브리드 음성 사용자에 대한 PSTN 사용을 관리합니다. 비즈니스용 Skype Online에 있는 사용자는 하이브리드 음성을 통해 온-프레미스 Lync Server 2013 설치에서 제공되는 Enterprise Voice 기능을 사용할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsVoiceRoutingPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Name <String>] [-PstnUsages <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 RedmondVoiceRoutingPolicy인 새 사용자별 음성 라우팅 정책을 만듭니다. 이 정책에는 단일 PSTN 사용(Long Distance)이 할당됩니다.

    New-CsVoiceRoutingPolicy -Identity "RedmondVoiceRoutingPolicy" -Name "RedmondVoiceRoutingPolicy" -PstnUsages "Long Distance"

## 예제 2

예제 2는 예제 1에 표시된 명령의 변형입니다. 그러나 이 경우에는 새 정책에 PSTN 사용 3개(Long Distance, Local, Internal)가 할당됩니다. 여러 사용을 할당하려는 경우 각 사용을 쉼표로 구분하면 됩니다.

    New-CsVoiceRoutingPolicy -Identity "RedmondVoiceRoutingPolicy" -Name "RedmondVoiceRoutingPolicy" -PstnUsages "Long Distance", "Local", "Internal"

## 자세한 정보

음성 라우팅 정책은 "하이브리드" 시나리오, 즉 일부 사용자는 온-프레미스 버전 Lync Server에 있고 나머지 사용자는 비즈니스용 Skype Online에 있는 시나리오에서 사용됩니다. 비즈니스용 Skype Online 사용자에게 음성 라우팅 정책을 할당하면 해당 사용자가 온-프레미스 SIP 트렁크를 사용하여 공중 전화망에서 전화를 받고 공중 전화망으로 전화를 걸 수 있습니다.

단순히 사용자에게 음성 라우팅 정책을 할당한다고 해서 해당 사용자가 비즈니스용 Skype Online을 통해 PSTN 전화를 할 수 있는 것은 아닙니다. 먼저 이러한 사용자들이 Enterprise Voice를 사용하도록 설정해야 하며 적절한 음성 정책 및 다이얼 플랜을 사용자에게 할당해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsVoiceRoutingPolicy"}

**Lync Server 제어판:** New-CsVoiceRoutingPolicy cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>새 음성 라우팅 정책에 할당할 고유 식별자입니다. 새 정책은 사용자별 범위에서만 만들 수 있으므로 ID는 항상 정책에 할당되는 &quot;이름&quot;입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;RedmondVoiceRoutingPolicy&quot;</p></td>
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
<td><p>관리자가 음성 라우팅 정책과 함께 표시할 설명 텍스트를 제공할 수 있습니다. 예를 들어 정책을 할당할 사용자에 대한 정보를 설명에 포함할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
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

없음. **New-CsVoiceRoutingPolicy** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsVoiceRoutingPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceRoutingPolicy 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsVoiceRoutingPolicy](get-csvoiceroutingpolicy.md)  
[Grant-CsVoiceRoutingPolicy](grant-csvoiceroutingpolicy.md)  
[Remove-CsVoiceRoutingPolicy](remove-csvoiceroutingpolicy.md)  
[Set-CsVoiceRoutingPolicy](set-csvoiceroutingpolicy.md)

