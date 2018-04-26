---
title: Get-CsRgsAgentGroup
TOCTitle: Get-CsRgsAgentGroup
ms:assetid: 2e3c7004-9017-48a4-91d8-5c271fb8a1ab
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425793(v=OCS.15)
ms:contentKeyID: 49303179
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsRgsAgentGroup

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 응답 그룹 에이전트 그룹에 대한 정보를 반환합니다. 에이전트 그룹은 응답 그룹 큐에 할당된 에이전트의 컬렉션입니다. 에이전트는 큐로 연결되는 통화에 응답하도록 할당된 사용자입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsRgsAgentGroup [-Identity <RgsIdentity>] [-Name <String>] [-Owner <RgsIdentity>] [-ShowAll <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 사용하도록 구성된 모든 응답 그룹 에이전트 그룹을 반환합니다. 이 작업을 수행하기 위해 매개 변수 없이 **Get-CsRgsAgentGroup**을 호출합니다.

    Get-CsRgsAgentGroup

## 예제 2

예제 2에 표시된 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 사용하도록 구성된 모든 응답 그룹 에이전트 그룹을 반환합니다.

    Get-CsRgsAgentGroup -Identity service:ApplicationServer:atl-cs-001.litwareinc.com

## 예제 3

예제 3에 표시된 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 Help Desk라는 단일 응답 그룹 에이전트 그룹을 반환합니다.

    Get-CsRgsAgentGroup -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"

## 예제 4

예제 4에서는 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 라운드 로빈 경로 지정 방법을 사용하는 모든 응답 그룹 에이전트 그룹에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsAgentGroup**을 사용하여 ApplicationServer:atl-cs-001.litwareinc.com의 모든 에이전트 그룹 컬렉션을 반환합니다. 이 컬렉션은 RoutingMethod 속성이 "RoundRobin"과 같은 그룹만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsRgsAgentGroup -Identity service:ApplicationServer:atl-cs-001.litwareinc.com | Where-Object {$_.RoutingMethod -eq "RoundRobin"}

## 예제 5

예제 5에 사용된 명령은 예제 4에 사용된 명령의 변형입니다. 그러나 이 경우에는 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 라운드 로빈 경로 지정 방법을 사용하지 않는 모든 응답 그룹 에이전트 그룹에 대한 정보가 반환됩니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsAgentGroup**을 호출하여 ApplicationServer:atl-cs-001.litwareinc.com의 모든 에이전트 그룹 컬렉션을 반환합니다. 이 컬렉션은 RoutingMethod 속성이 "RoundRobin"과 같지 않은 에이전트 그룹만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsRgsAgentGroup -Identity Service:ApplicationServer:atl-cs-001.litwareinc.com | Where-Object {$_.RoutingMethod -ne "RoundRobin"}

## 자세한 정보

응답 그룹 응용 프로그램과 연결된 전화 번호로 전화가 걸려 오면 먼저 응용 프로그램에서 전화가 걸려 온 번호에 해당하는 워크플로를 확인합니다. 이 워크플로의 구성에 따라 IVR(대화형 음성 응답) 질문 집합(발신자에게 "하드웨어 지원에 대한 질문입니까, 소프트웨어 지원에 대한 질문입니까?"라는 질문을 비롯한 하나 이상의 질문이 제공됨)으로 통화가 경로 지정될 수 있습니다. 또는 통화가 응답 그룹 큐에 배치될 수 있습니다. 즉, 지정된 담당자가 통화에 응답할 수 있을 때까지 발신자가 통화 대기 상태에 놓입니다. 통화에 응답하도록 지정된 담당자를 에이전트라고 하며, 전체 에이전트 집합을 응답 그룹 에이전트 그룹이라고 합니다. 에이전트 그룹은 워크플로 및 해당 직무와 연결됩니다. 예를 들어 지원 센터 담당자는 Help Desk 에이전트 그룹으로 그룹화되고, 고객 지원 에이전트는 Customer Support 에이전트 그룹으로 그룹화될 수 있습니다.

**Get-CsRgsAgentGroup** cmdlet을 사용하면 조직에서 현재 사용 중인 응답 그룹 에이전트 그룹에 대한 정보를 가져올 수 있습니다. 이러한 정보에는 각 에이전트 그룹에 할당된 사용자에 대한 정보가 포함됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsRgsAgentGroup** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsRgsAgentGroup"}

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
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>응답 그룹 에이전트 그룹이 호스트되는 서비스의 ID 또는 에이전트 그룹 자체의 전체 ID를 나타냅니다. 서비스 ID(예: service:ApplicationServer:atl-cs-001.litwareinc.com)를 지정하면 해당 서비스에서 호스트되는 모든 에이전트 그룹이 반환되고, 그룹 ID를 지정하면 지정된 에이전트 그룹만 반환됩니다. 에이전트 그룹 ID는 서비스 ID와 GUID(Globally Unique Identifier)로 구성됩니다(예: service:ApplicationServer:atl-cs-001.litwareinc.com/1987d3c2-4544-489d-bbe3-59f79f530a83).</p>
<p>서비스 ID를 지정한 다음 Name 매개 변수와 에이전트 그룹 이름을 포함하여 단일 그룹을 반환할 수도 있습니다. 이렇게 하면 특정 에이전트 그룹에 할당된 GUID를 몰라도 해당 그룹을 검색할 수 있습니다.</p>
<p>매개 변수 없이 호출한 경우 <strong>Get-CsRgsAgentGroup</strong>은 조직에서 사용하도록 구성된 모든 에이전트 그룹의 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>에이전트 그룹을 만들 당시 해당 그룹에 지정된 고유 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Owner</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>에이전트 그룹을 &quot;소유&quot;하는 풀의 정규화된 도메인 이름입니다. 에이전트 그룹의 풀 ID와 소유자 풀 ID는 보통 같습니다. 그러나 재해 복구 절차에서와 같이 그룹을 일시적으로 이동해야 하는 경우에는 풀 ID가 변경됩니다. 이 경우에도 소유자 ID는 계속 원래 풀을 가리킵니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ShowAll</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>있는 경우 소유자 풀 ID와 풀 ID가 다른 그룹을 비롯하여 모든 리소스 그룹 에이전트 그룹을 표시합니다. 기본적으로 Get-CsRgsAgentGroup은 소유자 풀 ID와 풀 ID가 동일한 에이전트 그룹에 대한 정보만 반환합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열. **Get-CsRgsAgentGroup**은 응답 그룹 에이전트 그룹의 ID를 나타내는 문자열 값을 허용합니다.

## 반환 형식

**Get-CsRgsAgentGroup**은 Microsoft.Rtc.Rgs.Management.WritableSettings.AgentGroup 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsRgsAgentGroup](new-csrgsagentgroup.md)  
[Remove-CsRgsAgentGroup](remove-csrgsagentgroup.md)  
[Set-CsRgsAgentGroup](set-csrgsagentgroup.md)

