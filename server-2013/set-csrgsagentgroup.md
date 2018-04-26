---
title: Set-CsRgsAgentGroup
TOCTitle: Set-CsRgsAgentGroup
ms:assetid: 48944530-29ec-4f5d-893f-37d3fd4aeb66
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425955(v=OCS.15)
ms:contentKeyID: 49303517
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsRgsAgentGroup

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 응답 그룹 에이전트 그룹을 수정합니다. 에이전트 그룹은 응답 그룹 큐에 할당된 에이전트의 컬렉션입니다. 에이전트는 특정 큐로 연결된 통화에 응답하도록 할당된 사용자입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsRgsAgentGroup -Instance <AgentGroup> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 Help Desk라는 응답 그룹 에이전트 그룹의 RoutingMethod 속성을 수정합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsAgentGroup** cmdlet을 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에서 Help Desk 에이전트 그룹(-Name "Help Desk")을 검색합니다. 검색한 후에는 에이전트 그룹 개체가 $x라는 변수에 저장됩니다.

예제의 두 번째 명령은 RoutingMethod 속성 값을 수정합니다. 예제의 마지막 명령은 **Set-CsRgsAgentGroup** cmdlet을 사용하여 실제 Help Desk 에이전트 그룹에 이러한 변경 내용을 기록합니다.

    $x = Get-CsRgsAgentGroup -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"
    $x.RoutingMethod = "RoundRobin"
    Set-CsRgsAgentGroup -Instance $x

## 예제 2

예제 2에서는 응답 그룹 에이전트 그룹에 할당된 메일 그룹을 변경하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 먼저 **Get-CsRgsAgentGroup**을 사용하여 수정할 에이전트 그룹, 즉 이 예제에서는 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 Help Desk 그룹(-Name "Help Desk ")을 반환합니다. **Get-CsRgsAgentGroup**이 이 그룹을 반환하면 결과 개체가 $x라는 변수에 저장됩니다.

이 예제의 두 번째 명령은 DistributionGroupAddress 속성에 새 값(helpdesk@litwareinc.com)을 할당합니다. 새 값이 할당되면 **Set-CsRgsAgentGroup**을 사용하여 ApplicationServer:atl-cs-001.litwareinc.com의 Help Desk 에이전트 그룹에 변경 내용을 기록합니다.

    $x = Get-CsRgsAgentGroup -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"
    $x.DistributionGroupAddress = "helpdesk@litwareinc.com"
    Set-CsRgsAgentGroup -Instance $x

## 예제 3

예제 3에 표시된 명령은 Help Desk라는 응답 그룹 에이전트 그룹에 새 에이전트를 추가합니다. 이 작업을 수행하기 위해 예제에서는 먼저 **Get-CsRgsAgentGroup**을 사용하여 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 Help Desk 그룹(-Name "Help Desk")을 반환합니다. 검색된 개체는 $x라는 변수에 저장됩니다.

두 번째 명령에서는 Add 메서드를 사용하여 AgentsByUri 속성에 새 에이전트를 추가합니다. 새 에이전트의 SIP 주소("sip:kenmyer@litwareinc.com")를 지정하여 이 작업을 수행합니다. 세 번째 명령은 **Set-CsRgsAgentGroup**을 사용하여 Help Desk 그룹에 변경 내용(즉, 새 에이전트 추가)을 기록합니다. **Set-CsRgsAgentGroup**을 호출하지 않으면 변경 내용이 메모리에만 적용되고 실제 에이전트 그룹에는 적용되지 않습니다.

    $x = Get-CsRgsAgentGroup -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"
    $x.AgentsByUri.Add("sip:kenmyer@litwareinc.com")
    Set-CsRgsAgentGroup -Instance $x

## 예제 4

예제 4에서는 ApplicationServer:atl-cs-001.litwareinc.com 서비스에 있는 응답 그룹 에이전트 그룹 Help Desk에서 에이전트가 제거됩니다. 이 작업을 수행하기 위해 예제에서는 먼저 **Get-CsRgsAgentGroup**을 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에서 Help Desk 그룹(-Name "Help Desk")을 반환합니다. 검색된 에이전트 그룹 개체는 $x라는 변수에 저장됩니다.

에이전트 그룹이 검색되면 Remove 메서드를 사용하여 그룹에서 에이전트(SIP 주소가 "sip:kenmyer@litwareinc.com"인 에이전트)를 제거합니다. 세 번째 명령은 **Set-CsRgsAgentGroup**을 호출하여 그룹의 변경 내용(즉, 에이전트 제거)을 기록합니다. **Set-CsRgsAgentGroup**을 호출하지 않으면 변경 내용이 메모리에만 적용되고 실제 에이전트 그룹에는 적용되지 않습니다. **Set-CsRgsAgentGroup**을 호출한 경우에만 에이전트가 제거됩니다.

    $x = Get-CsRgsAgentGroup -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"
    $x.AgentsByUri.Remove("sip:kenmyer@litwareinc.com")
    Set-CsRgsAgentGroup -Instance $x

## 자세한 정보

응답 그룹 응용 프로그램과 연결된 전화 번호로 전화가 걸려 오면 서비스에서 먼저 전화가 걸려 온 번호에 해당하는 워크플로를 확인합니다. 이 워크플로의 구성에 따라 IVR(대화형 음성 응답) 질문 집합(발신자에게 "하드웨어 지원에 대한 질문입니까, 소프트웨어 지원에 대한 질문입니까?"라는 질문을 비롯한 하나 이상의 질문이 제공됨)으로 통화가 경로 지정될 수 있습니다. 또는 통화가 응답 그룹 큐에 배치될 수 있습니다. 즉, 지정된 담당자가 통화에 응답할 수 있을 때까지 발신자가 통화 대기 상태에 놓입니다. 통화에 응답하도록 지정된 담당자를 에이전트라고 하며, 에이전트의 집합적인 그룹을 응답 그룹 에이전트 그룹이라고 합니다. 에이전트 그룹은 워크플로에 연결되어 있고 직무 등의 항목에도 연결되어 있습니다. 예를 들어 지원 센터 담당자는 Help Desk 에이전트 그룹으로 그룹화되고, 고객 지원 에이전트는 Customer Support 에이전트 그룹으로 그룹화될 수 있습니다.

새 에이전트 그룹은 **New-CsRgsAgentGroup** cmdlet을 사용하여 만듭니다. 에이전트 그룹을 만든 후 변경하려면 **Set-RgsAgentGroup** cmdlet을 사용합니다. 이 cmdlet은 특히 그룹에서 개별 에이전트를 추가하거나 제거하는 데 유용합니다. **Set-CsRgsAgentGroup**은 에이전트 그룹의 속성을 직접 수정하지 않습니다. 그룹을 수정하려면 먼저 해당 그룹에 대한 개체 참조를 만들어야 합니다. **Get-CsRgsAgentGroup**을 호출하여 그룹을 검색한 다음 반환된 개체를 변수에 저장하면 됩니다. 개체 참조를 만든 후 메모리에서 그룹 속성을 변경합니다. 수정을 완료하면 **Set-CsRgsAgentGroup**을 호출하여 실제 응답 그룹 에이전트 그룹에 변경 내용을 기록해야 합니다. **Set-CsRgsAgentGroup**을 호출하지 않으면 변경 내용이 메모리에만 존재하고 Windows PowerShell을 닫거나 개체 참조 변수를 삭제하는 즉시 사라집니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsRgsAgentGroup** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsRgsAgentGroup"}

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
<td><p>수정할 응답 그룹 에이전트 그룹에 대한 개체 참조입니다. 일반적으로 개체 참조는 <strong>Get-CsRgsAgentGroup</strong> cmdlet을 사용하여 반환된 값을 변수에 할당하는 방식으로 검색합니다. 예를 들어 이 명령은 Help Desk 에이전트 그룹에 대한 개체 참조를 반환하여 해당 개체 참조를 $x라는 변수에 저장합니다.</p>
<p>$x($x = Get-CsRgsAgentGroup -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name &quot;Help Desk&quot;)라는 변수에 저장합니다.</p>
<p></p></td>
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

Microsoft.Rtc.Rgs.Management.WritableSettings.AgentGroup object. **Set-CsRgsAgentGroup**은 응답 그룹 에이전트 그룹 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsRgsAgentGroup**은 개체나 값을 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Rgs.Management.WritableSettings.AgentGroup 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsRgsAgentGroup](get-csrgsagentgroup.md)  
[New-CsRgsAgentGroup](new-csrgsagentgroup.md)  
[Remove-CsRgsAgentGroup](remove-csrgsagentgroup.md)

