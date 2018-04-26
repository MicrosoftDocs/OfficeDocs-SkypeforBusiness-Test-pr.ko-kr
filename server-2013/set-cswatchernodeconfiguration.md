---
title: Set-CsWatcherNodeConfiguration
TOCTitle: Set-CsWatcherNodeConfiguration
ms:assetid: 001b49ab-de17-4161-9d0c-9d5d9626558f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204620(v=OCS.15)
ms:contentKeyID: 49302602
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsWatcherNodeConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

감시자 노드 구성 설정의 기존 컬렉션을 수정합니다. 감시자 노드는 주기적으로 Microsoft System Center Operations Manager 및 Lync Server 2013 가상 트랜잭션을 사용하여 Lync Server 구성 요소가 예상대로 작동하고 있는지를 확인하는 컴퓨터입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsWatcherNodeConfiguration [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsWatcherNodeConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Enabled <$true | $false>] [-ExtendedTests <PSListModifier>] [-Force <SwitchParameter>] [-PortNumber <UInt16>] [-Tests <PSListModifier>] [-TestUsers <PSListModifier>] [-UseInternalWebUrls <$true | $false>] [-WhatIf [<SwitchParameter>]] [-XmppTestReceiverMailAddress <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-cs-001.litwareinc.com 풀에 적용된 감시자 노드 구성 설정에 새 오디오 회의 공급자 테스트를 추가합니다. 이를 위해 예제의 첫 번째 명령은 **New-CsExtendedTest** cmdlet을 사용하여 새 테스트를 만듭니다. 이 메모리 내 전용 테스트는 $x 변수에 저장됩니다. 두 번째 명령에서는 **Set-CsWatcherNodeConfiguration** cmdlet이 ExtendedTests 매개 변수 및 @{Add=$x} 구문을 사용하여 새 테스트를 감시자 노드 구성 설정에 추가합니다.

    $x = New-CsExtendedTest -TestUsers "sip:kenmyer@litwareinc.com", "sip:pilar@litwareinc.com" -Name "Audio Conferencing Test" -TestType "AudioConferencingProvider"
    
    Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -ExtendedTests @{Add=$x}

## 예제 2

예제 2의 명령은 감시자 노드 구성 설정 컬렉션에서 확장 테스트를 제거하는 방법을 보여줍니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **Get-CsWatcherNodeConfiguration** cmdlet을 사용하여 atl-cs-001.litwareinc.com 풀의 감시자 노드 설정에 대한 개체 참조를 반환합니다. 이 개체 참조는 $x 변수에 저장됩니다.

두 번째 명령에서는 RemoveAt() 메서드를 사용하여 개체 참조 $x에서 첫 번째 확장 테스트를 제거합니다. 확장 테스트는 배열에서 항목으로 저장되며, 첫 번째 항목에 인덱스 번호 0이 지정되고 두 번째 항목에는 인덱스 번호 1이 지정되는 식으로 차례대로 번호가 지정됩니다. RemoveAt(0) 구문은 확장 테스트 집합에서 첫 번째 항목, 즉 인덱스 번호가 0인 항목을 제거합니다. 두 번째 확장 테스트를 제거하려면 RemoveAt(1) 구문을 사용합니다.

개체 참조가 업데이트되고 나면 최종 명령이 **Set-CsWatcherNodeConfiguration** cmdlet 및 Instance 매개 변수를 사용하여 개체 참조에 대한 변경 내용을 atl-cs-001.litwareinc.com 풀의 실제 감시자 노드 설정에 다시 씁니다.

    $x = Get-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com"
    
    $x.ExtendedTests.RemoveAt(0)
    
    Set-CsWatcherNodeConfiguration -Instance $x

## 예제 3

예제 3에서는 atl-cs-001.litwareinc.com 감시자 노드에 대해 구성된 모든 확장 테스트가 제거됩니다. ExtendedTests 매개 변수와 매개 변수 값 $Null을 포함하여 이 작업을 수행합니다.

    Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -ExtendedTests $Null

## 자세한 정보

Microsoft System Center Operations Manager를 사용하여 Lync Server 2013을 모니터링하는 경우에는 "감시자 노드", 즉 주기적으로 가상 트랜잭션을 자동 실행하여 Lync Server가 예상대로 작동하고 있는지를 확인하는 컴퓨터를 설정할 수 있습니다. 감시자 노드는 풀에 할당되며 **CsWatcherNodeConfiguration** cmdlet을 사용하여 관리됩니다. System Center Operations Manager를 사용 중이라면 감시자 노드를 설치할 필요가 없습니다. 감시자 노드를 사용하지 않고도 시스템을 모니터링할 수 있으며, 감시자 노드 사용 시와의 차이는 실행하려는 가상 트랜잭션이 Operations Manager를 통해 자동으로 호출되지 않으므로 해당 트랜잭션을 수동으로 호출해야 한다는 것뿐입니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsWatcherNodeConfiguration"}

**Lync Server 제어판:** **Set-CsWatcherNodeConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>감시자 노드를 사용하거나 사용하지 않도록 설정합니다. 기본값은 True($True)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExtendedTests</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>하나 이상의 ExtendedTest 개체 인스턴스에 대한 개체 참조입니다. 이러한 개체는 <strong>New-CsExtendedTest</strong> cmdlet을 사용하여 만들어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>감시자 노드 구성 설정과 연결된 풀의 정규화된 도메인 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>PS 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PortNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>등록자 서비스에서 사용하는 SIP 포트입니다.</p></td>
</tr>
<tr class="even">
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
<p>감시자 노드에 대해 추가 테스트를 사용하도록 설정하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Tests @{Add=&quot;ExumConnectivity&quot;,&quot;JoinLauncher&quot;,&quot;UnifiedContactStore&quot;}</p>
<p>감시자 노드에서 하나 이상의 테스트를 사용하지 않도록 설정하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Tests @{Remove=&quot;ABS&quot;,&quot;ABWQ&quot;}</p>
<p>감시자 노드에 대해 모든 테스트를 사용하지 않도록 설정하려면 Tests 매개 변수의 값을 $Null로 설정합니다.</p>
<p>-Tests $Null</p></td>
</tr>
<tr class="odd">
<td><p><em>TestUsers</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>감시자 노드에서 사용되는 테스트 사용자의 SIP 주소입니다. 노드에 테스트 사용자를 더 추가하려면 다음과 같은 구문을 사용합니다.</p>
<p>-TestUsers @{Add=&quot;sip:aidan@litwareinc.com&quot;}</p>
<p>감시자 노드에서 테스트 사용자를 제거하려면 다음과 같은 구문을 사용합니다.</p>
<p>-TestUsers @{Remove=&quot;sip:aidan@litwareinc.com&quot;</p>
<p>기존 사용자를 새 사용자로 바꾸려면 Replace 메서드를 사용합니다. 예를 들어 다음 구문은 sip:pilar@litwareinc.com 사용자를 새 사용자인 sip:aidan@litwareinc.com으로 바꿉니다.</p>
<p>-TestUsers @{Replace=&quot;sip:pilar@litwareinc.com&quot;,&quot;sip:aidan@litwareinc.com&quot;}</p>
<p>감시자 노드당 테스트 사용자는 항상 두 명 이상 있어야 합니다. 사용자가 두 명인 경우 그중 한 명을 제거하여 노드에 테스트 사용자가 한 명만 남도록 하려고 하면 명령이 실패합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UseInternalWebUrls</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True($True)로 설정하면 외부 웹 URL이 아닌 내부 웹 URL을 사용하도록 감시자 노드에 명령합니다. 이렇게 하면 조직의 방화벽으로 보호되어 있는 사용자의 URL 유효성을 확인할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>XmppTestReceiverMailAddress</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>XMPP 게이트웨이를 테스트할 때 사용할 XMPP 전자 메일 주소입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Set-CsWatcherNodeConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.WatcherNode.TargetPool\#Decorated 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsWatcherNodeConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.WatcherNode.TargetPool\#Decorated 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsWatcherNodeConfiguration](get-cswatchernodeconfiguration.md)  
[New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md)  
[Remove-CsWatcherNodeConfiguration](remove-cswatchernodeconfiguration.md)  
[Test-CsWatcherNodeConfiguration](test-cswatchernodeconfiguration.md)

