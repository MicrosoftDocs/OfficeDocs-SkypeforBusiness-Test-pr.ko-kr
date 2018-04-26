---
title: Get-CsVoiceRoutingPolicy
TOCTitle: Get-CsVoiceRoutingPolicy
ms:assetid: 60245b7d-4e95-4925-aae5-c0fa1e9f38fc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204940(v=OCS.15)
ms:contentKeyID: 49303793
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsVoiceRoutingPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 음성 라우팅 정책에 대한 정보를 반환합니다. 음성 라우팅 정책은 하이브리드 음성 사용자에 대한 PSTN 사용을 관리합니다. 비즈니스용 Skype Online에 있는 사용자는 하이브리드 음성을 통해 온-프레미스 Lync Server 2013 설치에서 제공되는 Enterprise Voice 기능을 사용할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsVoiceRoutingPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsVoiceRoutingPolicy [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1의 명령은 조직의 사용자에 대해 구성된 모든 음성 라우팅 정책에 대한 정보를 반환합니다.

    Get-CsVoiceRoutingPolicy

## 예제 2

예제 2에서는 ID가 RedmondVoiceRoutingPolicy인 단일 음성 라우팅 정책에 대한 정보가 반환됩니다.

    Get-CsVoiceRoutingPolicy -Identity "RedmondVoiceRoutingPolicy"

## 예제 3

예제 3에 표시된 명령은 사용자별 범위에서 구성된 모든 음성 라우팅 정책에 대한 정보를 반환합니다. 이를 위해 명령은 Filter 매개 변수 및 필터 값 "tag:\*"를 사용합니다. 이 필터 값은 반환되는 데이터를 ID가 문자열 값 "tag:"으로 시작하는 정책으로 제한합니다.

    Get-CsVoiceRoutingPolicy -Filter "tag:*"

## 예제 4

예제 4에서는 PSTN 사용 "Long Distance"를 포함하는 음성 라우팅 정책에 대한 정보만 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsVoiceRoutingPolicy** cmdlet을 호출합니다. 그러면 조직에서 사용하도록 구성된 모든 음성 라우팅 정책의 컬렉션이 반환됩니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프되며, 해당 cmdlet은 PstnUsages 속성이 "Long Distance" 사용을 포함하는(-contains) 정책만 선택합니다.

    Get-CsVoiceRoutingPolicy | Where-Object {$_.PstnUsages -contains "Long Distance"}

## 예제 5

예제 5는 예제 4에 표시된 명령의 변형입니다. 그러나 이 경우에는 PSTN 사용 "Long Distance"를 포함하지 않는 음성 라우팅 정책에 대한 정보만 반환합니다. 이 작업을 수행하기 위해 **Where-Object** cmdlet은 반환되는 데이터를 "Long Distance" 사용이 포함되지 않은 정책으로 제한하는 -notcontains 연산자를 사용합니다.

    Get-CsVoiceRoutingPolicy | Where-Object {$_.PstnUsages -notcontains "Long Distance"}

## 자세한 정보

음성 라우팅 정책은 "하이브리드" 시나리오, 즉 일부 사용자는 온-프레미스 버전 Lync Server에 있고 나머지 사용자는 비즈니스용 Skype Online에 있는 시나리오에서 사용됩니다. 비즈니스용 Skype Online 사용자에게 음성 라우팅 정책을 할당하면 해당 사용자가 온-프레미스 SIP 트렁크를 사용하여 공중 전화망에서 전화를 받고 공중 전화망으로 전화를 걸 수 있습니다.

단순히 사용자에게 음성 라우팅 정책을 할당한다고 해서 해당 사용자가 비즈니스용 Skype Online을 통해 PSTN 전화를 할 수 있는 것은 아닙니다. 먼저 이러한 사용자들이 Enterprise Voice를 사용하도록 설정해야 하며 적절한 음성 정책 및 다이얼 플랜을 사용자에게 할당해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsVoiceRoutingPolicy"}

**Lync Server 제어판:** Get-CsVoiceRoutingPolicy cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>하나 이상의 음성 라우팅 정책을 검색할 때 와일드카드를 사용할 수 있습니다. 예를 들어 사용자별 범위에서 구성된 모든 정책을 반환하려면 다음 구문을 사용합니다.</p>
<p>-Filter &quot;tag:*&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 음성 라우팅 정책의 고유 식별자입니다. 전역 정책을 반환하려면 다음 구문을 사용합니다.</p>
<p>-Identity global</p>
<p>사용자별 범위에서 구성된 정책을 반환하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;RedmondVoiceRoutingPolicy&quot;</p>
<p>Identity를 지정할 때 와일드카드 문자를 사용할 수 없습니다.</p>
<p>Identity 및 Filter 매개 변수를 둘 다 지정하지 않으면 <strong>Get-CsVoiceRoutingPolicy</strong> cmdlet은 조직에서 사용하도록 구성된 모든 음성 라우팅 정책을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 음성 정책 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsVoiceRoutingPolicy** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsVoiceRoutingPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceRoutingPolicy 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Grant-CsVoiceRoutingPolicy](grant-csvoiceroutingpolicy.md)  
[New-CsVoiceRoutingPolicy](new-csvoiceroutingpolicy.md)  
[Remove-CsVoiceRoutingPolicy](remove-csvoiceroutingpolicy.md)  
[Set-CsVoiceRoutingPolicy](set-csvoiceroutingpolicy.md)

