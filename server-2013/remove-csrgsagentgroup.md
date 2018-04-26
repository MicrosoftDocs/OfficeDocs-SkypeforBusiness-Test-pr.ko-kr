---
title: Remove-CsRgsAgentGroup
TOCTitle: Remove-CsRgsAgentGroup
ms:assetid: dc185da9-0ae0-4f89-8ef8-7cb680d5dc51
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398969(v=OCS.15)
ms:contentKeyID: 49305232
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsRgsAgentGroup

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 응답 그룹 에이전트 그룹을 제거합니다. 에이전트 그룹은 응답 그룹 큐에 할당된 에이전트의 컬렉션입니다. 에이전트는 특정 큐로 연결된 통화에 응답하도록 할당된 사용자입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsRgsAgentGroup -Instance <AgentGroup> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 사용하도록 구성된 모든 응답 그룹 에이전트 그룹을 삭제합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsAgentGroup**을 사용하여 ApplicationServer:atl-cs-001.litwareinc.com의 모든 에이전트 그룹을 반환합니다. 이러한 그룹은 **Remove-CsRgsAgentGroup** cmdlet에 파이프되어 제거됩니다.

    Get-CsRgsAgentGroup -Identity service:ApplicationServer:atl-cs-001.litwareinc.com | Remove-CsRgsAgentGroup

## 예제 2

예제 2에서는 Help Desk라는 단일 응답 그룹 에이전트 그룹을 제거합니다. 이 작업을 수행하기 위해 먼저 **Get-CsRgsAgentGroup**을 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에서 Help Desk 에이전트 그룹(-Name "Help Desk")을 반환합니다. 이 그룹은 서비스에서 그룹을 제거하는 **Remove-CsRgsAgentGroup**에 파이프됩니다.

    Get-CsRgsAgentGroup -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk" | Remove-CsRgsAgentGroup

## 예제 3

예제 3에서는 ApplicationServer:atl-cs-001.litwareinc.com에서 라운드 로빈 경로 지정 방법을 사용하지 않는 모든 응답 그룹 에이전트 그룹을 삭제합니다. 이 작업을 수행하기 위해 먼저 **Get-CsRgsAgentGroup**을 호출하여 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 모든 에이전트 그룹의 컬렉션을 반환합니다. 이 컬렉션은 RoutingMethod 속성이 RoundRobin과 같지 않은 그룹만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsRgsAgentGroup**에 파이프됩니다.

    Get-CsRgsAgentGroup -Identity service:ApplicationServer:atl-cs-001.litwareinc.com | Where-Object {$_.RoutingMethod -ne "RoundRobin"} | Remove-CsRgsAgentGroup

## 자세한 정보

응답 그룹 응용 프로그램과 연결된 전화 번호로 전화가 걸려 오면 서비스에서 먼저 전화가 걸려 온 번호에 해당하는 워크플로를 확인합니다. 이 워크플로의 구성에 따라 IVR(대화형 음성 응답) 질문 집합(발신자에게 "하드웨어 지원에 대한 질문입니까, 소프트웨어 지원에 대한 질문입니까?"라는 질문을 비롯한 하나 이상의 질문이 제공됨)으로 통화가 경로 지정될 수 있습니다. 또는 통화가 응답 그룹 큐에 배치될 수 있습니다. 즉, 담당자가 통화에 응답할 수 있을 때까지 발신자가 통화 대기 상태에 놓입니다. 통화에 응답하도록 지정된 담당자를 에이전트라고 하며, 에이전트의 집합적인 그룹을 응답 그룹 에이전트 그룹이라고 합니다. 에이전트 그룹은 워크플로 및 해당 직무와 연결됩니다. 예를 들어 지원 센터 담당자는 Help Desk 에이전트 그룹으로 그룹화되고, 고객 지원 에이전트는 Customer Support 에이전트 그룹으로 그룹화될 수 있습니다.

새 에이전트 그룹은 **New-CsRgsAgentGroup** cmdlet을 사용하여 만듭니다. 에이전트 그룹을 삭제하려면 **Remove-CsRgsAgentGroup** cmdlet을 호출하면 됩니다. 이 cmdlet은 전체 그룹과 해당 그룹의 모든 에이전트를 삭제합니다. 그룹에서 하나의 에이전트만 제거하려면 대신 **Set-CsRgsAgentGroup** cmdlet을 사용합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsRgsAgentGroup** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsRgsAgentGroup"}

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
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.AgentGroup</p></td>
<td><p>제거할 에이전트 그룹을 가리키는 개체 참조입니다. 워크플로 개체를 <strong>Remove-CsRgsAgentGroup</strong>에 파이프할 때 Instance 매개 변수를 삭제할 수 있습니다.</p>
<p>Instance 매개 변수를 사용하려면 다음과 같은 명령을 사용합니다.</p>
<p>$x = Get-CsRgsAgentGroup –Identity ApplicationServer:atl-cs-001.litwareinc.com /1987d3c2-4544-489d-bbe3-59f79f530a83</p>
<p>Remove-CsRgsAgentGroup –Instance $x</p>
<p>Instance 매개 변수를 사용하는 경우 한 번에 하나의 에이전트 그룹만 제거할 수 있습니다. 이는 개체 참조($x)가 여러 에이전트 그룹 개체를 포함할 수 없음을 의미합니다.</p></td>
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
<td><p>에이전트 그룹을 강제로 제거합니다. 이 매개 변수가 있으면 활성 워크플로에서 사용하는 경우에도 경고 없이 에이전트 그룹이 삭제됩니다. 이 매개 변수가 없으면 활성 워크플로에서 현재 사용 중인 에이전트 그룹을 삭제할지 확인하는 메시지가 표시됩니다.</p></td>
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

Microsoft.Rtc.Rgs.Management.WritableSettings.AgentGroup object. **Remove-CsRgsAgentGroup**은 응답 그룹 에이전트 그룹 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Remove-CsRgsAgentGroup**은 Microsoft.Rtc.Rgs.Management.WritableSettings.AgentGroup 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsRgsAgentGroup](get-csrgsagentgroup.md)  
[New-CsRgsAgentGroup](new-csrgsagentgroup.md)  
[Set-CsRgsAgentGroup](set-csrgsagentgroup.md)

