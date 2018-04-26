---
title: Remove-CsRgsQueue
TOCTitle: Remove-CsRgsQueue
ms:assetid: 7613e72c-f330-4560-88d4-a7386cd18975
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398576(v=OCS.15)
ms:contentKeyID: 49304066
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsRgsQueue

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 응답 그룹 큐를 삭제합니다. 응답 그룹 응용 프로그램을 사용하면 응답 그룹 에이전트가 통화에 응답할 수 있을 때까지 전화 통화가 큐에 배치되고 발신자는 통화 대기 상태가 됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsRgsQueue -Instance <Queue> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 모든 응답 그룹 큐를 삭제합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsQueue**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에서 찾은 모든 큐의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 큐를 삭제하는 **Remove-CsRgsQueue**에 파이프됩니다.

    Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com | Remove-CsRgsQueue

## 예제 2

예제 2에서는 ApplicationServer:atl-cs-001.litwareinc.com 서비스에 있는 "Help Desk Queue"라는 단일 응답 그룹 큐를 삭제합니다. 이 큐를 삭제하기 위해 Identity 및 Name 매개 변수와 함께 **Get-CsRgsQueue**를 호출합니다. 이 호출에서 반환된 단일 큐는 **Remove-CsRgsQueue**에 파이프되어 삭제됩니다.

    Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk Queue" | Remove-CsRgsQueue

## 예제 3

예제 3에서는 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 OverflowCandidate 속성이 NewestCall로 설정된 모든 응답 그룹 큐를 삭제합니다. 이 작업을 수행하기 위해 먼저 **Get-CsRgsQueue**를 호출하여 ApplicationServer:atl-cs-001.litwareinc.com에서 찾은 모든 응답 그룹 큐의 컬렉션을 반환합니다. 이 컬렉션은 OverflowCandidate 속성이 "NewestCall"과 같은 큐만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 큐를 삭제하는 **Remove-CsRgsQueue**에 파이프됩니다.

    Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com | Where-Object {$_.OverflowCandidate -eq "NewestCall"} | Remove-CsRgsQueue

## 자세한 정보

발신자가 응답 그룹 응용 프로그램과 연결된 전화 번호로 전화를 걸면 일반적으로 통화를 계속하기 위해 발신자가 응답해야 하는 질문(예: "하드웨어 지원을 받으려면 1번을, 소프트웨어 지원을 받으려면 2번을 누르십시오.")으로 통화가 전송되거나 응답 그룹 에이전트가 통화에 응답할 수 있을 때까지 통화가 큐에 배치됩니다.

응답 그룹 응용 프로그램을 사용하면 모든 전화 통화에 대해 단일 큐를 지정하는 대신 서로 다른 워크플로 및 에이전트 그룹과 연결될 수 있는 여러 큐를 만들 수 있습니다. 따라서 큐에서 동시에 대기 중인 지정된 통화 수와 같은 이벤트 또는 지정된 시간 동안 통화 대기 중인 발신자에 대해 큐가 다른 방식으로 응답할 수 있습니다.

새 큐를 만들 수 있을 뿐만 아니라 기존 큐를 제거할 수도 있습니다. 기존 큐를 제거하는 것이 바로 **Remove-CsRgsQueue** cmdlet의 기능입니다. 기본적으로 활성 워크플로에 현재 할당된 큐를 제거하려고 하면 큐를 삭제할지 확인하는 메시지가 표시됩니다. 이 프롬프트에 응답할 때까지 Windows PowerShell이 일시 중지되고 아무 큐도 삭제되지 않습니다. 프롬프트를 무시하고 활성 워크플로에서 사용 중인 큐를 삭제하려면 Force 매개 변수를 추가합니다. 예를 들면 다음과 같습니다.

Get-CsRgsQueue –Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" | Remove-CsRgsQueue –Force

**Remove-CsRgsQueue**는 큐를 삭제하기 전에 항상 활성 워크플로에서 해당 큐를 사용 중인지 확인합니다. 그러나 시간 초과되거나 오버플로된 큐에서 사용하고 있는지 여부는 확인하지 않습니다. 따라서 다른 큐에 필요한 큐가 삭제될 수 있습니다. 이러한 경우를 방지하기 위해 **Remove-CsRgsQueue**를 실행하여 큐를 삭제하기 전에 **Get-CsRgsQueue** cmdlet을 사용하여 다른 응답 그룹 큐의 OverflowAction 및 TimeoutAction 속성을 확인할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsRgsQueue** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsRgsQueue"}

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
<td><p><em>Instance</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.Queue</p></td>
<td><p>제거할 큐를 가리키는 개체 참조입니다. 워크플로 개체를 <strong>Remove-CsRgsQueue</strong>에 파이프할 때 Instance 매개 변수를 삭제할 수 있습니다.</p>
<p>Instance 매개 변수를 사용하려면 다음과 같은 명령을 사용합니다.</p>
<p>$x = Get-CsRgsQueue –Identity ApplicationServer:atl-cs-001.litwareinc.com /1987d3c2-4544-489d-bbe3-59f79f530a83</p>
<p>Remove-CsRgsQueue –Instance $x</p>
<p>Instance 매개 변수를 사용하는 경우 한 번에 하나의 큐만 제거할 수 있습니다. 이는 개체 참조($x)가 여러 큐 개체를 포함할 수 없음을 의미합니다.</p></td>
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
<td><p>응답 그룹 큐를 강제로 삭제합니다. 이 매개 변수가 있으면 활성 워크플로에 할당된 경우에도 경고 없이 큐가 삭제됩니다. 이 매개 변수가 없으면 활성 워크플로에서 현재 사용 중인 큐를 삭제할지 확인하는 메시지가 표시됩니다.</p></td>
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

Microsoft.Rtc.Rgs.Management.WritableSettings.Queue object. **Remove-CsRgsQueue**는 응답 그룹 워크플로 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Remove-CsRgsQueue**는 Microsoft.Rtc.Rgs.Management.WritableSettings.Queue 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsRgsQueue](get-csrgsqueue.md)  
[New-CsRgsQueue](new-csrgsqueue.md)  
[Set-CsRgsQueue](set-csrgsqueue.md)

