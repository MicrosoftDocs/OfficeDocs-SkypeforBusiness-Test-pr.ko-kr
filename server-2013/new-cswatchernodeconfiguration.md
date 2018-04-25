---
title: New-CsWatcherNodeConfiguration
TOCTitle: New-CsWatcherNodeConfiguration
ms:assetid: c7f78c92-7965-4879-9efa-1b5adcd1881b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205254(v=OCS.15)
ms:contentKeyID: 49305001
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsWatcherNodeConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 감시자 노드 구성 설정 컬렉션을 풀에 할당합니다. 감시자 노드는 주기적으로 Microsoft System Center Operations Manager 및 Lync Server 2013 가상 트랜잭션을 사용하여 Lync Server 구성 요소가 예상대로 작동하고 있는지를 확인하는 컴퓨터입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsWatcherNodeConfiguration -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

    New-CsWatcherNodeConfiguration -TargetFqdn <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: -PortNumber <UInt16> [-Confirm [<SwitchParameter>]] [-Enabled <$true | $false>] [-ExtendedTests <PSListModifier>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Tests <PSListModifier>] [-TestUsers <PSListModifier>] [-UseInternalWebUrls <$true | $false>] [-WhatIf [<SwitchParameter>]] [-XmppTestReceiverMailAddress <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 풀 atl-cs-001.litwareinc.com에 대한 감시자 노드 구성 설정의 새 컬렉션을 만듭니다. 이를 위해 예제의 처음 두 명령은 감시자 노드 테스트 사용자 쌍(sip:kenmyer@litwareinc.com 및 sip:pilar@litwareinc.com)을 만듭니다. 테스트 사용자가 만들어지면 예제의 세 번째 명령이 새로 만든 두 사용자를 사용하여 확장된 PSTN 테스트를 새로 만듭니다. 이 새 테스트(해당 시점에서는 메모리에만 존재함)는 $x 변수에 저장됩니다.

마지막으로 예제의 네 번째 명령이 atl-cs-001.litwareinc.com에 대해 감시자 노드 구성 설정을 만듭니다. 이러한 새 설정은 포트 5061, 새 테스트 사용자 두 명 및 변수 $x에 저장되어 있는 확장 테스트를 사용합니다.

    Set-CsTestUserCredential -SipAddress "sip:kenmyer@litwareinc.com" -UserName "litwareinc\kenmyer" -Password "07Apples"
    
    Set-CsTestUserCredential -SipAddress "sip:pilar@litwareinc.com" -UserName "litwareinc\pilar" -Password "07Apples"
    
    $x = New-CsExtendedTest -TestUsers "sip:kenmyer@litwareinc.com", "sip:pilar@litwareinc.com" -Name "PSTN Test" -TestType "PSTN"
    
    New-CsWatcherNodeConfiguration -TargetFqdn "atl-cs-001.litwareinc.com" -PortNumber 5061 -TestUsers "sip:kenmyer@litwareinc.com","sip:pilar@litwareinc.com"} -ExtendedTests @{Add=$x}

## 자세한 정보

Microsoft System Center Operations Manager를 사용하여 Lync Server 2013을 모니터링하는 경우에는 "감시자 노드", 즉 주기적으로 가상 트랜잭션을 자동 실행하여 Lync Server가 예상대로 작동하고 있는지를 확인하는 컴퓨터를 설정할 수 있습니다. 감시자 노드는 풀에 할당되며 **CsWatcherNodeConfiguration** cmdlet을 사용하여 관리됩니다. System Center Operations Manager를 사용 중이라면 감시자 노드를 설치할 필요가 없습니다. 감시자 노드를 사용하지 않고도 시스템을 모니터링할 수 있으며, 감시자 노드 사용 시와의 차이는 실행하려는 가상 트랜잭션이 Operations Manager를 통해 자동으로 호출되지 않으므로 해당 트랜잭션을 수동으로 호출해야 한다는 것뿐입니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsWatcherNodeConfiguration"}

**Lync Server 제어판:** **New-CsWatcherNodeConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>감시자 노드 구성 설정과 연결할 풀의 정규화된 도메인 이름입니다. Identity 매개 변수 또는 TargetFqdn 매개 변수를 사용하여 풀을 지정할 수는 있지만 같은 명령에서 두 매개 변수를 모두 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PortNumber</em></p></td>
<td><p>필수</p></td>
<td><p>System.UInt16</p></td>
<td><p>등록자 서비스에서 사용하는 SIP 포트입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TargetFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>감시자 노드 구성 설정과 연결할 풀의 정규화된 도메인 이름입니다. TargetFqdn 매개 변수 또는 Identity 매개 변수를 사용하여 풀을 지정할 수는 있지만 같은 명령에서 두 매개 변수를 모두 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>감시자 노드를 사용하거나 사용하지 않도록 설정합니다. 기본값은 True($True)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExtendedTests</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>감시자 노드 구성에 할당할 수 있는 PSTN 또는 오디오 회의 공급자 테스트입니다. 이러한 테스트는 <strong>New-CsExtendedTest</strong> cmdlet을 사용하여 만들고 $x 등의 변수에 저장해야 합니다. 그런 후에 다음과 같은 구문을 사용하여 테스트를 감시자 노드에 할당할 수 있습니다.</p>
<p>–ExtendedTests @{Add=$x}</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Tests</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>감시자 노드를 통해 실행할 가상 트랜잭션입니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Registration</p>
<p>* IM</p>
<p>* GroupIM</p>
<p>* P2PAV</p>
<p>* AvConference</p>
<p>* Presence</p>
<p>* ABS</p>
<p>* ABWQ</p>
<p>* MCXP2PIM</p>
<p>* ExumConnectivity</p>
<p>* JoinLauncher</p>
<p>* PersistentChatMessage</p>
<p>* DataConference</p>
<p>* XmppIM</p>
<p>* UnifiedContactStore</p>
<p>* AVEdgeConnectivity</p>
<p>새 감시자 노드를 만들 때 테스트를 구성하려면 다음 구문을 사용합니다. 각 테스트는 쉼표를 사용하여 구분합니다.</p>
<p>-Tests &quot;ABS&quot;,&quot;ABWQ&quot;,&quot;IM&quot;,&quot;GroupIM&quot;,&quot;XmppIM&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>TestUsers</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>감시자 노드에 할당할 테스트 사용자의 SIP 주소입니다. 이러한 사용자 계정은 <strong>Set-CsTestUserCredential</strong> cmdlet을 사용하여 이전에 구성된 상태여야 합니다. 테스트 사용자를 추가하려면 다음과 같은 구문을 사용합니다. 각 사용자 주소는 쉼표로 구분합니다.</p>
<p>–TestUsers &quot;sip:kenmyer@litwareinc.com&quot;,&quot;sip:pilar@litwareinc.com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>UseInternalWebUrls</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True($True)로 설정하면 외부 웹 URL이 아닌 내부 웹 URL을 사용하도록 감시자 노드에 명령합니다. 이렇게 하면 조직의 방화벽으로 보호되어 있는 사용자의 URL 유효성을 확인할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>XmppTestReceiverMailAddress</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>XMPP 게이트웨이를 테스트할 때 사용할 XMPP 전자 메일 주소입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsWatcherNodeConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsWatcherNodeConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.WatcherNode.TargetPool\#Decorated 개체의 새 인스턴스를 만듭니다.

