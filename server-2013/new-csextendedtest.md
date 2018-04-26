---
title: New-CsExtendedTest
TOCTitle: New-CsExtendedTest
ms:assetid: d4756daa-a4ce-4d74-926b-89754cf7e0b2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205275(v=OCS.15)
ms:contentKeyID: 49305140
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsExtendedTest

 

_**마지막으로 수정된 항목:** 2015-03-09_

감시자 노드 구성에 할당할 수 있는 PSTN 또는 오디오 회의 공급자 테스트를 만듭니다. 감시자 노드는 주기적으로 Microsoft System Center Operations Manager 및 Lync Server 2013 가상 트랜잭션을 사용하여 Lync Server 구성 요소가 예상대로 작동하고 있는지를 확인하는 컴퓨터입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsExtendedTest -Name <String> -TestType <AudioConferencingProvider | PSTN> [-TestUsers <PSListModifier>]

## 예제

## 예제 1

예제 1에 표시된 명령은 TestType이 PSTN인 새 확장 테스트를 만든 다음 atl-cs-001.litwareinc.com 풀용 새 감시자 노드에 해당 확장 테스트를 추가합니다. 예제의 첫 번째 명령에서는 **New-CsExtendedTest** cmdlet을 사용하여 이름이 PSTN Test인 확장 테스트를 만듭니다. 이 테스트에는 테스트 사용자 sip:kenmyer@litwareinc.com 및 sip:pilar@litwareinc.com이 포함됩니다. 이 두 테스트 사용자는 **Set-CsTestUserCredential** cmdlet을 사용하여 이미 구성된 상태여야 합니다. 이렇게 만들어지는 확장 테스트 개체는 $x 변수에 저장됩니다.

두 번째 명령에서는 atl-cs-001.litwareinc.com용으로 새로 만들어진 감시자 노드에 새 확장 테스트를 추가합니다. 이 작업은 ExtendedTests 매개 변수 및 @{Add=$x} 구문을 사용하여 수행합니다.

    $x = New-CsExtendedTest -TestUsers "sip:kenmyer@litwareinc.com", "sip:pilar@litwareinc.com" -Name "PSTN Test" -TestType "PSTN"
    
    New-CsWatcherNodeConfiguration -TargetFqdn "atl-cs-001.litwareinc.com" -PortNumber 5061 -TestUsers "sip:kenmyer@litwareinc.com","sip:pilar@litwareinc.com" -ExtendedTests @{Add=$x}

## 자세한 정보

Microsoft System Center Operations Manager를 사용하여 Lync Server 2013를 모니터링하는 경우에는 "감시자 노드", 즉 주기적으로 가상 트랜잭션을 자동 실행하여 Lync Server가 예상대로 작동하고 있는지를 확인하는 컴퓨터를 설정할 수 있습니다. 감시자 노드는 풀에 할당되며 CsWatcherNodeConfiguration cmdlet을 사용하여 관리됩니다. System Center Operations Manager를 사용 중이라면 감시자 노드를 설치할 필요가 없습니다. 감시자 노드를 사용하지 않고도 시스템을 모니터링할 수 있으며, 감시자 노드 사용 시와의 차이는 실행하려는 가상 트랜잭션이 Operations Manager를 통해 자동으로 호출되지 않으므로 해당 트랜잭션을 수동으로 호출해야 한다는 것뿐입니다.

감시자 노드를 구성할 때는 PSTN 또는 오디오 회의 공급자 테스트를 "확장 테스트"로 추가할 수 있습니다. 이러한 확장 테스트는 감시자 노드 컴퓨터를 통해 실행되는 표준 테스트 집합 대신 또는 해당 집합에 추가로 사용할 수 있습니다. 확장 테스트는 **New-CsExtendedTest** cmdlet을 사용하여 만든 다음 적절한 감시자 노드에 추가해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsExtendedTest"}

**Lync Server 제어판:** **New-CsExtendedTest** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>확장 테스트에 지정할 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TestType</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.WatcherNode.TestType</p></td>
<td><p>확장 테스트가 수행할 테스트의 유형입니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* PSTN</p>
<p>* AudioConferencingProvider</p>
<p>TestType은 확장 테스트당 하나만 지정할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TestUsers</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>테스트 사용자로 사용할 사용자 계정의 SIP 주소입니다. 다음과 같이 계정을 쉼표로 구분하여 여러 계정을 지정할 수 있습니다.</p>
<p>–TestUsers &quot;sip:kenmyer@litwareinc.com&quot;, &quot;sip:pilar@litwareinc.com&quot;</p>
<p>PSTN TestType을 사용할 때는 테스트 사용자를 두 명 이상 지정해야 합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsExtendedTest** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsExtendedTest** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.WatcherNode.ExtendedTest 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md)  
[Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md)

