---
title: New-CsRgsAgentGroup
TOCTitle: New-CsRgsAgentGroup
ms:assetid: faaf46f9-1063-4d64-a36f-872e657cd869
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413065(v=OCS.15)
ms:contentKeyID: 49305616
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsRgsAgentGroup

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 응답 그룹 에이전트 그룹을 만듭니다. 에이전트 그룹은 응답 그룹 큐에 할당된 에이전트의 컬렉션입니다. 에이전트는 특정 큐로 연결된 통화에 응답하도록 할당된 사용자입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsRgsAgentGroup -Name <String> -Parent <RgsIdentity> [-AgentAlertTime <Int16>] [-AgentsByUri <Collection>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-DistributionGroupAddress <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-ParticipationPolicy <Informal | Formal>] [-RoutingMethod <LongestIdle | Serial | Parallel | RoundRobin | Attendant>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Help Desk Group이라는 새 응답 그룹 에이전트 그룹을 만듭니다. 이 새 그룹은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에 포함됩니다. 그룹을 만들기 위해 이 명령은 Parent 및 Name 매개 변수와 함께 **New-CsRgsAgentGroup**을 호출합니다. 그 밖에 다른 그룹 매개 변수는 지정되어 있지 않은데, 이는 그룹에서 모든 기본 속성 값을 사용함을 의미합니다. 이 그룹에 할당된 에이전트가 없으므로 새 에이전트 그룹으로 경로 지정된 모든 통화는 자동으로 끊어집니다.

    New-CsRgsAgentGroup -Parent service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk Group"

## 예제 2

예제 2에서는 새 응답 그룹 에이전트 그룹을 만들고 이와 동시에 해당 그룹에 에이전트 쌍을 할당합니다. 이 작업을 수행하기 위해 이 명령은 Parent 및 Name 매개 변수와 함께 **New-CsRgsAgentGroup**을 호출합니다. 또한 이 예제에는 AgentsByUri 매개 변수와 함께 "sip:kenmyer@litwareinc.com","sip:pilarackerman@litwareinc.com" 매개 변수 값이 포함되어 있습니다. 이 값은 에이전트 그룹에 추가할 쉼표로 구분된 SIP 주소 목록입니다.

    New-CsRgsAgentGroup -Parent service: ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk Group" -AgentsByUri "sip:kenmyer@litwareinc.com","sip:pilarackerman@litwareinc.com"

## 자세한 정보

응답 그룹 응용 프로그램과 연결된 전화 번호로 전화가 걸려 오면 먼저 응용 프로그램에서 전화가 걸려 온 번호에 해당하는 워크플로를 확인합니다. 이 워크플로의 구성에 따라 IVR(대화형 음성 응답) 질문 집합(발신자에게 "하드웨어 지원에 대한 질문입니까, 소프트웨어 지원에 대한 질문입니까?"라는 질문을 비롯한 하나 이상의 질문이 제공됨)으로 통화가 경로 지정될 수 있습니다. 또는 통화가 응답 그룹 큐에 배치될 수 있습니다. 즉, 지정된 담당자가 통화에 응답할 수 있을 때까지 발신자가 통화 대기 상태에 놓입니다. 통화에 응답하도록 지정된 담당자를 에이전트라고 하며, 에이전트의 집합적인 그룹을 응답 그룹 에이전트 그룹이라고 합니다. 에이전트 그룹은 큐와 연결되며, 추가로 유사한 해당 직무와도 연결됩니다. 예를 들어 지원 센터 담당자는 Help Desk 에이전트 그룹으로 그룹화되고, 고객 지원 에이전트는 Customer Support 에이전트 그룹으로 그룹화될 수 있습니다.

여러 그룹이 큐에 할당된 경우 응답 그룹 응용 프로그램에서는 먼저 해당 큐에 할당된 첫 번째 그룹에 속한 모든 에이전트로 전화를 연결합니다. 아무 에이전트도 응답하지 않으면 큐에 할당된 다음 그룹에 속한 모든 에이전트로 전화를 연결합니다.

새 에이전트 그룹은 **New-CsRgsAgentGroup** cmdlet을 사용하여 만듭니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsRgsAgentGroup** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object  {$_.Cmdlets -match "New-CsRgsAgentGroup"}

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
<td><p>에이전트 그룹에 할당할 고유 이름입니다. Parent 속성과 Name 속성을 조합하면 에이전트 그룹의 GUID(Globally Unique Identifier)를 참조하지 않고도 에이전트 그룹을 고유하게 식별할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Parent</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>새 에이전트 그룹을 호스트할 서비스입니다(예: -Parent &quot;service:ApplicationServer:atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>AgentAlertTime</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int16</p></td>
<td><p>통화가 다음 에이전트로 자동으로 경로 지정될 때까지 응답하지 않은 상태로 유지될 수 있는 시간(초)을 나타냅니다. AgentAlertTime은 10초에서 600초(10분) 사이의 정수 값으로 설정할 수 있습니다(끝의 두 값 포함). 기본값은 20초입니다. <strong>참고:</strong> 에이전트 알림 시간 설정은 180초를 초과할 수 없으며, 180초를 초과할 경우 클라이언트 응용 프로그램에서는 SIP 트랜잭션 타이머가 해당 최대 대기 시간에 도달했기 때문에 통화를 거부하게 됩니다. 이를 방지하려면 알림 시간 값을 180초 미만으로 설정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AgentsByUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.Collections.ObjectModel.Collection</p></td>
<td><p>에이전트 그룹에 개별적으로 에이전트를 추가하는 데 사용됩니다. 새 에이전트는 해당 SIP 주소로 식별됩니다.</p>
<p>Enterprise Voice를 사용하도록 설정된 사용자만 선택할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 에이전트 그룹에 대한 추가 설명 정보를 제공하는 데 사용됩니다. 예를 들어 Description은 그룹에서 예정된 전화 통화를 받지 못한 경우에 연락할 사람에 대한 정보를 포함할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DistributionGroupAddress</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>메일 그룹의 모든 구성원을 에이전트 그룹에 추가하는 데 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ParticipationPolicy</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.ParticipationPolicy</p></td>
<td><p>에이전트가 그룹에 예정된 전화 통화를 받기 위해 시스템에 공식적으로 로그온해야 하는지 여부를 나타냅니다. ParticipationPolicy가 Informal(기본값)로 설정된 경우에는 로그인이 필요하지 않고, Formal로 설정된 경우에는 로그인이 필요합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RoutingMethod</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.RoutingMethod</p></td>
<td><p>새 통화를 에이전트로 경로 지정하는 데 사용되는 방법을 지정합니다. RoutingMethod는 다음 값 중 하나로 설정해야 합니다.</p>
<p>LongestIdle - 오랜 시간 동안 유휴 상태였던 에이전트(즉, Lync 작업에 참여하지 않은 에이전트)로 통화가 경로 지정됩니다.</p>
<p>RoundRobin – 통화가 목록의 다음 에이전트로 경로 지정됩니다.</p>
<p>Serial - 통화가 항상 목록의 첫 번째 에이전트로 경로 지정되며, 이 에이전트가 응답할 수 없거나 할당된 시간 내에 응답하지 않은 경우에만 다른 에이전트로 경로 지정됩니다.</p>
<p>Parallel - 현재 상태가 통화 중이거나 응답할 수 없음을 나타내는 에이전트를 제외하고, 통화가 모든 에이전트로 동시에 경로 지정됩니다.</p>
<p>Attendant – 현재 상태가 통화 중이거나 응답할 수 없음을 나타내는 에이전트를 포함하여 통화가 모든 에이전트로 동시에 경로 지정됩니다. 단, 자신의 현재 상태를 방해 금지로 설정한 에이전트는 제외됩니다.</p>
<p>기본 경로 지정 방법은 Parallel입니다.</p></td>
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

없음. **New-CsRgsAgentGroup**은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsRgsAgentGroup**은 Microsoft.Rtc.Rgs.Management.WritableSettings.AgentGroup 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsRgsAgentGroup](get-csrgsagentgroup.md)  
[Remove-CsRgsAgentGroup](remove-csrgsagentgroup.md)  
[Set-CsRgsAgentGroup](set-csrgsagentgroup.md)

