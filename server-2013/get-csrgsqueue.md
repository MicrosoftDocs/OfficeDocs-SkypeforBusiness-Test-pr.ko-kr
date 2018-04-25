---
title: Get-CsRgsQueue
TOCTitle: Get-CsRgsQueue
ms:assetid: a2e786b7-5096-4011-8108-2b56ae768c1d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412759(v=OCS.15)
ms:contentKeyID: 49304594
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsRgsQueue

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용 중인 응답 그룹 큐에 대한 정보를 검색합니다. 응답 그룹 응용 프로그램을 사용하면 응답 그룹 에이전트가 통화에 응답할 수 있을 때까지 전화 통화가 큐에 배치되고 통화는 대기 상태가 됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsRgsQueue [-Identity <RgsIdentity>] [-Name <String>] [-Owner <RgsIdentity>] [-ShowAll <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 응답 그룹 큐에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 매개 변수 없이 **Get-CsRgsQueue**를 호출합니다.

    Get-CsRgsQueue

## 예제 2

예제 2에 표시된 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에 있는 모든 응답 그룹 큐에 대한 정보를 반환합니다.

    Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com

## 예제 3

예제 3에서는 ApplicationServer:atl-cs-001.litwareinc.com 서비스에 있는 "Help Desk"라는 단일 응답 그룹 큐에 대한 정보를 반환합니다.

    Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"

## 예제 4

예제 4의 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 각 응답 그룹 큐의 TimeoutAction 속성에 대한 자세한 정보를 표시합니다. 이 작업을 수행하기 위해 먼저 **Get-CsRgsQueue**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에서 찾은 모든 큐에 대한 정보를 반환합니다. 이 정보는 TimeoutAction 속성에 저장된 값을 "확장"하는 **Select-Object** cmdlet에 전달됩니다. TimeoutAction 값을 확장하면 이 속성 값을 구성하는 포함된 개체의 개별 속성 Prompt, TargetQuestion, Target, TargetQueueID 및 TargetUri가 표시됩니다.

    Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com | Select-Object -ExpandProperty TimeoutAction

## 예제 5

예제 5에서는 ApplicationServer:atl-cs-001.litwareinc.com에서 OverflowCandidate 속성이 NewestCall로 설정된 모든 응답 그룹 큐에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsQueue**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에서 찾은 모든 응답 그룹 큐의 컬렉션을 반환합니다. 이 컬렉션은 OverflowCandidate 속성이 "NewestCall"과 같은 큐만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com | Where-Object {$_.OverflowCandidate -eq "NewestCall"}

## 자세한 정보

발신자가 응답 그룹 응용 프로그램과 연결된 전화 번호로 전화를 걸면 일반적으로 통화를 계속하기 위해 발신자가 응답해야 하는 질문(예: "하드웨어 지원을 받으려면 1번을, 소프트웨어 지원을 받으려면 2번을 누르십시오.")으로 통화가 전송되거나 응답 그룹 에이전트가 통화에 응답할 수 있을 때까지 통화가 큐에 배치됩니다.

응답 그룹 응용 프로그램을 사용하면 모든 전화 통화에 대해 단일 큐를 지정하는 대신 서로 다른 워크플로 및 에이전트 그룹과 연결될 수 있는 여러 큐를 만들 수 있습니다. 따라서 큐에서 동시에 대기 중인 지정된 통화 수와 같은 이벤트 또는 지정된 시간(초) 동안 통화 대기 중인 발신자에 대해 큐가 다른 방식으로 응답할 수 있습니다.

**Get-CsRgsQueue** cmdlet을 사용하면 조직에서 사용하도록 구성된 응답 그룹 큐에 대한 정보를 가져올 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsRgsQueue** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsRgsQueue"}

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
<td><p>응답 그룹 큐가 호스트되는 서비스의 ID 또는 큐 자체의 전체 ID를 나타냅니다. 서비스 ID(예: service:ApplicationServer:atl-cs-001.litwareinc.com)를 지정하면 해당 서비스에서 호스트되는 모든 응답 그룹 큐가 반환되고, 큐 ID를 지정하면 지정된 응답 그룹 큐만 반환됩니다. 큐 ID는 서비스 ID와 GUID(Globally Unique Identifier)로 구성됩니다(예: service:ApplicationServer:atl-cs-001.litwareinc.com /1987d3c2-4544-489d-bbe3-59f79f530a83).</p>
<p>서비스 ID를 지정한 다음 Name 매개 변수와 큐 이름을 포함하여 단일 응답 그룹 큐를 반환할 수도 있습니다. 이렇게 하면 특정 응답 그룹 큐에 할당된 GUID를 몰라도 해당 큐를 검색할 수 있습니다.</p>
<p>매개 변수 없이 호출한 경우 <strong>Get-CsRgsQueue</strong>는 조직에서 사용하도록 구성된 모든 응답 그룹 큐를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>응답 그룹 큐를 만들 당시 해당 큐에 지정된 고유 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Owner</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>큐를 &quot;소유&quot;하는 풀의 정규화된 도메인 이름입니다. 큐의 풀 ID와 소유자 풀 ID는 보통 같습니다. 그러나 재해 복구 절차에서와 같이 큐를 일시적으로 이동해야 하는 경우에는 풀 ID가 변경됩니다. 이 경우에도 소유자 ID는 계속 원래 풀을 가리킵니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ShowAll</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>있는 경우 소유자 풀 ID와 풀 ID가 다른 큐를 비롯하여 모든 리소스 그룹 큐를 표시합니다. 기본적으로 Get-CsRgsQueue는 소유자 풀 ID와 풀 ID가 동일한 큐에 대한 정보만 반환합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열. **Get-CsRgsQueue**는 응답 그룹 큐의 ID를 나타내는 문자열 값을 허용합니다.

## 반환 형식

**Get-CsRgsQueue**는 Microsoft.Rtc.Rgs.Management.WritableSettings.Queue 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsRgsQueue](new-csrgsqueue.md)  
[Remove-CsRgsQueue](remove-csrgsqueue.md)  
[Set-CsRgsQueue](set-csrgsqueue.md)

