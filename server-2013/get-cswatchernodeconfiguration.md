---
title: Get-CsWatcherNodeConfiguration
TOCTitle: Get-CsWatcherNodeConfiguration
ms:assetid: 20dae017-375c-4361-8d65-b56f4c09b375
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204739(v=OCS.15)
ms:contentKeyID: 49303032
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsWatcherNodeConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용 중인 감시자 노드 구성 설정에 대한 정보를 반환합니다. 감시자 노드는 주기적으로 Microsoft System Center Operations Manager 2007 R2 및 Lync Server 2013 가상 트랜잭션을 사용하여 Lync Server 구성 요소가 예상대로 작동하고 있는지를 확인하는 컴퓨터입니다. 감시자 노드 구성 설정을 통해 감시자 노드와 연결된 풀을 확인할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsWatcherNodeConfiguration [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsWatcherNodeConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 현재 조직에서 사용하도록 구성된 모든 감시자 노드에 대한 정보를 반환합니다.

    Get-CsWatcherNodeConfiguration

## 예제 2

예제 2에서는 풀과 연결된 감시자 노드에 대한 정보를 반환합니다.

    Get-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com"

## 예제 3

예제 3에 표시된 명령은 테스트 사용자에 SIP 주소가 sip:kenmyer@litwareinc.com인 사용자가 포함되는 모든 감시자 노드에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsWatcherNodeConfiguration** cmdlet을 사용하여 조직의 모든 감시자 노드 컬렉션을 반환합니다. 해당 컬렉션은 TestUsers 속성에 SIP 주소 sip:kenmyer@litwareinc.com이 포함된 노드만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsWatcherNodeConfiguration | Where-Object {$_.TestUsers -contains "sip:kenmyer@litwareinc.com"}

## 예제 4

예제 4에서는 PSTN 테스트 유형을 포함하는 모든 감시자 노드에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsWatcherNodeConfiguration** cmdlet을 호출하여 조직의 모든 감시자 노드 컬렉션을 반환합니다. 해당 컬렉션은 ExtendedTests 속성에 문자열 값 "TestType=PSTN"이 포함된(-matches) 감시자 노드만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsWatcherNodeConfiguration | Where-Object {$_.ExtendedTests -match "TestType=PSTN"}

## 자세한 정보

Microsoft System Center Operations Manager를 사용하여 Lync Server 2013을 모니터링하는 경우에는 "감시자 노드", 즉 주기적으로 가상 트랜잭션을 자동 실행하여 Lync Server가 예상대로 작동하고 있는지를 확인하는 컴퓨터를 설정할 수 있습니다. 감시자 노드는 풀에 할당되며 **CsWatcherNodeConfiguration** cmdlet을 사용하여 관리됩니다. System Center Operations Manager를 사용 중이라면 감시자 노드를 설치할 필요가 없습니다. 감시자 노드를 사용하지 않고도 시스템을 모니터링할 수 있으며, 감시자 노드 사용 시와의 차이는 실행하려는 가상 트랜잭션이 Operations Manager를 통해 자동으로 호출되지 않으므로 해당 트랜잭션을 수동으로 호출해야 한다는 것뿐입니다.

**Get-CsWatcherNodeConfiguration** cmdlet은 조직에서 사용하도록 구성된 모든 감시자 노드에 대한 정보를 반환합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsWatcherNodeConfiguration"}

**Lync Server 제어판:** **Get-CsWatcherNodeConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>하나 이상의 감시자 노드를 반환하기 위해 와일드카드 문자를 사용할 수 있습니다. 예를 들어 litwareinc.com 도메인에 대한 모든 감시자 노드를 반환하려면 다음 구문을 사용합니다.</p>
<p>-Filter &quot;*.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>감시자 노드가 할당된 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;atl-cs-001.litwareinc.com&quot;</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsWatcherNodeConfiguration</strong> cmdlet은 조직에서 사용하도록 구성된 모든 감시자 노드에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 감시자 노드 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsWatcherNodeConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsWatcherNodeConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.WatcherNode.TargetPool\#Decorated 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md)  
[Remove-CsWatcherNodeConfiguration](remove-cswatchernodeconfiguration.md)  
[Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md)  
[Test-CsWatcherNodeConfiguration](test-cswatchernodeconfiguration.md)

