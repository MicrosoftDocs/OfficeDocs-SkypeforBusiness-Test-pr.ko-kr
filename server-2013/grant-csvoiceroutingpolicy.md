---
title: Grant-CsVoiceRoutingPolicy
TOCTitle: Grant-CsVoiceRoutingPolicy
ms:assetid: a7c7b6c4-925a-464c-a3ee-8373f4eb46b2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205141(v=OCS.15)
ms:contentKeyID: 49304639
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Grant-CsVoiceRoutingPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자별 음성 라우팅 정책을 한 명 이상의 사용자에게 할당합니다. 음성 라우팅 정책은 하이브리드 음성 사용자에 대한 PSTN 사용을 관리합니다. 비즈니스용 Skype Online에 있는 사용자는 하이브리드 음성을 통해 온-프레미스 Lync Server 2013 설치에서 제공되는 Enterprise Voice 기능을 사용할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Grant-CsVoiceRoutingPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Active Directory 표시 이름이 "Ken Myer"인 사용자에게 사용자별 음성 라우팅 정책 RedmondVoiceRoutingPolicy를 할당합니다.

    Grant-CsVoiceRoutingPolicy -Identity "Ken Myer" -PolicyName "RedmondVoiceRoutingPolicy"

## 예제 2

예제 2에서는 이전에 사용자 Ken Myer에게 할당되었던 모든 사용자별 음성 라우팅 정책의 할당을 취소합니다. 그러면 Ken Myer는 전역 음성 라우팅 정책을 통해 관리됩니다. 사용자별 정책을 할당 취소하려면 PolicyName을 null 값($Null)으로 설정합니다.

    Grant-CsVoiceRoutingPolicy -Identity "Ken Myer" -PolicyName $Null

## 예제 3

예제 3에서는 사용자별 음성 라우팅 정책 RedmondVoiceRoutingPolicy를 Active Directory의 Redmond OU에 있는 모든 사용자에게 할당합니다. 이 작업을 수행하기 위해 명령은 먼저 OU 매개 변수를 포함하여 **Get-CsUser** cmdlet을 호출합니다. 매개 변수 값 "OU=Redmond,dc=litwareinc,dc=com"은 반환되는 데이터를 Redmond OU의 사용자 계정으로 제한합니다. 해당 사용자 계정은 **Grant-CsVoiceRoutingPolicy** cmdlet에 파이프되며, 이 cmdlet은 각 사용자에게 음성 라우팅 정책 RedmondVoiceRoutingPolicy를 할당합니다.

    Get-CsUser -OU "OU=Redmond,dc=litwareinc,dc=com" | Grant-CsVoiceRoutingPolicy -PolicyName "RedmondVoiceRoutingPolicy"

## 자세한 정보

음성 라우팅 정책은 "하이브리드" 시나리오, 즉 일부 사용자는 온-프레미스 버전 Lync Server에 있고 나머지 사용자는 비즈니스용 Skype Online에 있는 시나리오에서 사용됩니다. 비즈니스용 Skype Online 사용자에게 음성 라우팅 정책을 할당하면 해당 사용자가 온-프레미스 SIP 트렁크를 사용하여 공중 전화망에서 전화를 받고 공중 전화망으로 전화를 걸 수 있습니다.

단순히 사용자에게 음성 라우팅 정책을 할당한다고 해서 해당 사용자가 비즈니스용 Skype Online을 통해 PSTN 전화를 할 수 있는 것은 아닙니다. 먼저 이러한 사용자들이 Enterprise Voice를 사용하도록 설정해야 하며 적절한 음성 정책 및 다이얼 플랜을 사용자에게 할당해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Grant-CsVoiceRoutingPolicy"}

**Lync Server 제어판:** Grant-CsVoiceRoutingPolicy cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>사용자별 음성 라우팅 정책을 할당할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 보통 네 가지 형식 중 하나를 사용하여 지정되는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다.</p>
<p>사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 지정할 수도 있습니다.</p>
<p>또한 표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 &quot; Smith&quot; 문자열 값으로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PolicyName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>할당할 정책의 &quot;이름&quot;입니다. PolicyName은 간단히 말해 정책 ID에서 정책 범위(&quot;tag:&quot; 접두사)를 뺀 부분입니다. 예를 들어 ID가 tag:Redmond인 정책의 PolicyName은 Redmond와 같습니다. 마찬가지로 ID가 tag:RedmondVoiceRoutingPolicy인 정책의 PolicyName은 RedmondVoiceRoutingPolicy와 같습니다.</p>
<p>사용자에게 이전에 할당한 사용자별 정책을 할당 취소하려면 PolicyName을 null 값($Null)으로 설정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>사용자 정보를 검색하기 위해 지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-dc-001) 또는 FQDN(정규화된 도메인 이름)(예: atl-dc-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>음성 라우팅 정책을 할당할 사용자 계정을 나타내는 사용자 개체를 파이프라인을 통해 전달하는 데 사용됩니다. 기본적으로 <strong>Grant-CsVoiceRoutingPolicy</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
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

문자열 값 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Grant-CsVoiceRoutingPolicy** cmdlet은 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값 입력을 허용합니다. 또한 이 cmdlet은 사용자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

기본적으로 **Grant-CsVoiceRoutingPolicy** cmdlet은 값 또는 개체를 반환하지 않습니다. 그러나 PassThru 매개 변수를 포함할 경우 이 cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSUserOrAppContact의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsVoiceRoutingPolicy](get-csvoiceroutingpolicy.md)  
[New-CsVoiceRoutingPolicy](new-csvoiceroutingpolicy.md)  
[Remove-CsVoiceRoutingPolicy](remove-csvoiceroutingpolicy.md)  
[Set-CsVoiceRoutingPolicy](set-csvoiceroutingpolicy.md)

