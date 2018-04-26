---
title: Remove-CsWatcherNodeConfiguration
TOCTitle: Remove-CsWatcherNodeConfiguration
ms:assetid: 599c6d58-da3d-4f0b-bc1f-22ac3e33ec7f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204926(v=OCS.15)
ms:contentKeyID: 49303721
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsWatcherNodeConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

감시자 노드 구성 설정의 기존 컬렉션을 제거합니다. 감시자 노드는 주기적으로 System Center Operations Manager 및 Lync Server 2013 가상 트랜잭션을 사용하여 Lync Server 구성 요소가 예상대로 작동하고 있는지를 확인하는 컴퓨터입니다. 이 cmdlet은 Lync Server 2013에 도입되었습니다.

## 구문

    Remove-CsWatcherNodeConfiguration -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-cs-001.litwareinc.com 풀에 적용된 감시자 노드 구성 설정을 제거합니다.

    Remove-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com"

## 예제 2

예제 2에서는 조직에서 사용하도록 구성된 모든 감시자 노드를 제거합니다. 이 작업을 수행하기 위해 먼저 **Get-CsWatcherNodeConfiguration** cmdlet을 사용하여 모든 감시자 노드의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 감시자 노드를 제거하는 **Remove-CsWatcherNodeConfiguration** cmdlet에 파이프되며, 그러면 조직의 각 감시자 노드가 제거됩니다.

    Get-CsWatcherNodeConfiguration | Remove-CsWatcherNodeConfiguration

## 예제 3

예제 3에서는 sip:kenmyer@litwareinc.com 사용자가 테스트 사용자로 포함된 모든 감시자 노드를 제거합니다. 이 작업을 수행하기 위해 먼저 **Get-CsWatcherNodeConfiguration** cmdlet을 호출하여 현재 사용 중인 모든 감시자 노드의 컬렉션을 반환합니다. 이 컬렉션은 TestUsers 속성에 sip:kenmyer@litwareinc.com 사용자가 포함된(-contains) 설정만 선택하는 Where-Object cmdlet에 파이프됩니다. 이렇게 필터링된 컬렉션은 필터링된 컬렉션의 각 항목을 제거하는 **Remove-CsWatcherNodeConfiguration** cmdlet에 파이프됩니다.

    Get-CsWatcherNodeConfiguration | Where-Object {$_.TestUsers -contains "sip:kenmyer@litwareinc.com"} | Remove-CsWatcherNodeConfiguration

## 자세한 정보

Microsoft System Center Operations Manager를 사용하여 Lync Server 2013을 모니터링하는 경우에는 "감시자 노드", 즉 주기적으로 가상 트랜잭션을 자동 실행하여 Lync Server가 예상대로 작동하고 있는지를 확인하는 컴퓨터를 설정할 수 있습니다. 감시자 노드는 풀에 할당되며 **CsWatcherNodeConfiguration** cmdlet을 사용하여 관리됩니다. System Center Operations Manager를 사용 중이라면 감시자 노드를 설치할 필요가 없습니다. 감시자 노드를 사용하지 않고도 시스템을 모니터링할 수 있으며, 감시자 노드 사용 시와의 차이는 실행하려는 가상 트랜잭션이 Operations Manager를 통해 자동으로 호출되지 않으므로 해당 트랜잭션을 수동으로 호출해야 한다는 것뿐입니다.

나중에 감시자 노드를 해제하려는 경우에는 **Remove-CsWatcherNodeConfiguration** cmdlet을 사용하면 됩니다. [Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md) cmdlet을 사용하여 감시자 노드를 일시적으로 사용하지 않도록 설정했다가 나중에 다시 사용하도록 설정할 수도 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsWatcherNodeConfiguration"}

**Lync Server 제어판:** **Remove-CsWatcherNodeConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>삭제할 감시자 노드가 할당된 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;atl-cs-001.litwareinc.com&quot;</p></td>
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
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
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

**Remove-CsWatcherNodeConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.WatcherNode.TargetPool\#Decorated 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 Remove-CsWatcherNodeConfiguration cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.WatcherNode.TargetPool\#Decorated 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsWatcherNodeConfiguration](get-cswatchernodeconfiguration.md)  
[New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md)  
[Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md)  
[Test-CsWatcherNodeConfiguration](test-cswatchernodeconfiguration.md)

