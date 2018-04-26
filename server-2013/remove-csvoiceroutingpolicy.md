---
title: Remove-CsVoiceRoutingPolicy
TOCTitle: Remove-CsVoiceRoutingPolicy
ms:assetid: 3729e908-5c0d-4970-bdff-5869ba2082c9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204799(v=OCS.15)
ms:contentKeyID: 49303297
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsVoiceRoutingPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 음성 라우팅 정책을 삭제합니다. 음성 라우팅 정책은 하이브리드 음성 사용자에 대한 PSTN 사용을 관리합니다. 비즈니스용 Skype Online에 있는 사용자는 하이브리드 음성을 통해 온-프레미스 Lync Server 2013 설치에서 제공되는 Enterprise Voice 기능을 사용할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsVoiceRoutingPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 음성 라우팅 정책 RedmondVoiceRoutingPolicy를 삭제합니다.

    Remove-CsVoiceRoutingPolicy -Identity "RedmondVoiceRoutingPolicy"

## 예제 2

예제 2에서는 사용자별 범위에서 구성된 모든 음성 라우팅 정책을 제거합니다. 이 작업을 수행하기 위해 먼저 Filter 매개 변수를 포함하여 **Get-CsVoiceRoutingPolicy** cmdlet을 호출합니다. 필터 값 "tag:\*"는 반환되는 데이터를 사용자별 범위에서 구성된 음성 라우팅 정책으로 제한합니다. 이러한 사용자별 정책은 **Remove-CsVoiceRoutingPolicy** cmdlet에 파이프된 다음 해당 cmdlet에 의해 제거됩니다.

    Get-CsVoiceRoutingPolicy -Filter "tag:*" | Remove-CsVoiceRoutingPolicy

## 예제 3

예제 3에서는 PSTN 사용 "Long Distance"를 포함하는 모든 음성 라우팅 정책을 제거합니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsVoiceRoutingPolicy** cmdlet을 호출하여 사용 가능한 모든 음성 라우팅 정책의 컬렉션을 반환합니다. 해당 컬렉션은 PstnUsages 속성에 "Long Distance" 사용이 포함된(-contains) 정책만 선택하는 Where-Object cmdlet에 파이프됩니다. 그런 다음 조건을 충족하는 정책은 PSTN 사용 "Long Distance"를 포함하는 각 음성 라우팅 정책을 제거하는 **Remove-CsVoiceRoutingPolicy**에 파이프됩니다.

    Get-CsVoiceRoutingPolicy | Where-Object {$_.PstnUsages -contains "Long Distance"} | Remove-CsVoiceRoutingPolicy

## 자세한 정보

음성 라우팅 정책은 "하이브리드" 시나리오, 즉 일부 사용자는 온-프레미스 버전 Microsoft Lync Server 2013에 있고 나머지 사용자는 비즈니스용 Skype Online에 있는 시나리오에서 사용됩니다. 비즈니스용 Skype Online 사용자에게 음성 라우팅 정책을 할당하면 해당 사용자가 온-프레미스 SIP 트렁크를 사용하여 공중 전화망에서 전화를 받고 공중 전화망으로 전화를 걸 수 있습니다.

단순히 사용자에게 음성 라우팅 정책을 할당한다고 해서 해당 사용자가 비즈니스용 Skype Online을 통해 PSTN 전화를 할 수 있는 것은 아닙니다. 먼저 이러한 사용자들이 Enterprise Voice를 사용하도록 설정해야 하며 적절한 음성 정책 및 다이얼 플랜을 사용자에게 할당해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsVoiceRoutingPolicy"}

**Lync Server 제어판:** **Remove-CsVoiceRoutingPolicy** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>제거할 음성 라우팅 정책의 고유 식별자입니다. 전역 정책을 &quot;제거&quot;하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity global</p>
<p>전역 정책은 실제로는 제거할 수 없습니다. 대신 전역 정책의 모든 속성이 기본값으로 다시 설정됩니다.</p>
<p>사용자별 정책을 제거하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;RedmondVoiceRoutingPolicy&quot;</p>
<p>정책 ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
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
<td><p>이 매개 변수가 있으면 현재 하나 이상의 사용자에게 할당된 경우에도 정책이 자동으로 제거됩니다.</p>
<p>이 매개 변수가 없으면 <strong>Remove-CsVoiceRoutingPolicy</strong> cmdlet에서 하나 이상의 사용자에 할당된 사용자별 정책을 자동으로 제거하지 않습니다. 대신 정책을 제거할 것인지 확인하는 확인 메시지가 표시됩니다. Y 키를 눌러 예라고 응답해야 명령이 계속되고 정책이 제거됩니다.</p></td>
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

**Remove-CsVoiceRoutingPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceRoutingPolicy 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsVoiceRoutingPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceRoutingPolicy 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsVoiceRoutingPolicy](get-csvoiceroutingpolicy.md)  
[Grant-CsVoiceRoutingPolicy](grant-csvoiceroutingpolicy.md)  
[New-CsVoiceRoutingPolicy](new-csvoiceroutingpolicy.md)  
[Set-CsVoiceRoutingPolicy](set-csvoiceroutingpolicy.md)

