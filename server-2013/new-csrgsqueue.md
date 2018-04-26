---
title: New-CsRgsQueue
TOCTitle: New-CsRgsQueue
ms:assetid: e013533b-6845-44c6-ae5e-e75187b43181
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398989(v=OCS.15)
ms:contentKeyID: 49305285
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsRgsQueue

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 응답 그룹 큐를 만듭니다. 응답 그룹 응용 프로그램을 사용하면 응답 그룹 에이전트가 통화에 응답할 수 있을 때까지 전화 통화가 큐에 배치되고 발신자는 통화 대기 상태가 됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsRgsQueue -Name <String> -Parent <RgsIdentity> [-AgentGroupIDList <Collection>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-OverflowAction <CallAction>] [-OverflowCandidate <NewestCall | OldestCall>] [-OverflowThreshold <Int16>] [-TimeoutAction <CallAction>] [-TimeoutThreshold <Int32>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ApplicationServer:atl-cs-001.litwareinc.com 서비스의 새 응답 그룹 큐를 만듭니다. 이 예제의 첫 번째 명령은 **New-CsRgsCallAction** cmdlet을 사용하여 큐에 대한 통화 작업을 만듭니다. 이 예제에서는 오버플로 임계값을 초과할 때마다 통화가 음성 메일로 자동 전송되는 통화 작업을 만들기 위해 Action 매개 변수를 TransferToVoicemailUri로 설정하고 URI 속성을 음성 메일 SIP URI "sip:+14255551298@litwareinc.com"으로 설정합니다.

통화 작업이 구성되고 변수 $x에 저장되면 **New-CsRgsQueue**를 사용하여 Help Desk라는 새 큐를 만듭니다. 이 명령은 OverflowAction을 지정하는 것 외에 OverflowCandidate 및 OverflowThreshold 속성 값도 구성합니다.

    $x = New-CsRgsCallAction -Action TransferToVoicemailUri -Uri "sip:+14255551298@litwareinc.com"
    
    New-CsRgsQueue -Parent service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk" -OverflowCandidate "OldestCall" -OverflowAction $x -OverflowThreshold 25

## 자세한 정보

발신자가 응답 그룹 응용 프로그램과 연결된 전화 번호로 전화를 걸면 일반적으로 통화를 계속하기 위해 발신자가 응답해야 하는 질문(예: "하드웨어 지원을 받으려면 1번을, 소프트웨어 지원을 받으려면 2번을 누르십시오.")으로 통화가 전송되거나 에이전트가 통화에 응답할 수 있을 때까지 통화가 큐에 배치됩니다.

응답 그룹 응용 프로그램을 사용하면 모든 전화 통화에 대해 단일 큐를 지정하는 대신 서로 다른 워크플로 및 에이전트 그룹과 연결될 수 있는 여러 큐를 만들 수 있습니다. 따라서 큐에서 동시에 대기 중인 지정된 통화 수와 같은 이벤트 또는 지정된 시간 동안 통화 대기 중인 발신자에 대해 큐가 다른 방식으로 응답할 수 있습니다.

**New-CsRgsQueue** cmdlet을 사용하면 관리자가 새 응답 그룹 큐를 쉽게 만들 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsRgsQueue** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsRgsQueue"}

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
<td><p>큐에 할당할 고유 이름입니다. Parent 속성과 Name 속성을 조합하면 응답 그룹 큐의 GUID(Globally Unique Identifier)를 참조하지 않고도 응답 그룹 큐를 고유하게 식별할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Parent</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>새 큐를 호스트할 서비스입니다(예: -Parent &quot;service:ApplicationServer:atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>AgentGroupIDList</em></p></td>
<td><p>선택</p></td>
<td><p>System.Collections.ObjectModel.Collection</p></td>
<td><p>큐에 추가할 응답 그룹 에이전트 그룹의 ID입니다. 에이전트 그룹 ID는 <strong>Get-CsRgsAgentGroup</strong> cmdlet을 사용하여 검색할 수 있습니다. 자세한 내용은 이 항목의 예제 섹션을 참조하십시오.</p>
<p>할당된 에이전트 그룹이 없거나 에이전트가 없는 에이전트 그룹만 할당된 큐에 통화가 경로 지정된 경우에는 통화가 자동으로 끊어집니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 응답 그룹 큐에 대한 추가 정보를 제공하는 데 사용됩니다.</p></td>
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
<td><p><em>OverflowAction</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.CallAction</p></td>
<td><p>오버플로 임계값에 도달한 경우에 수행할 작업입니다. OverflowAction은 <strong>New-CsRgsCallAction</strong> cmdlet을 사용하여 만들어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>OverflowCandidate</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.OverflowCandidate</p></td>
<td><p>오버플로 임계값에 도달한 경우에 작업할 통화를 나타냅니다. OverflowCandidate 속성은 다음 두 값 중 하나로 설정되어야 합니다.</p>
<p>NewestCall</p>
<p>OldestCall</p>
<p>기본값은 NewestCall입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OverflowThreshold</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int16</p></td>
<td><p>오버플로 작업이 트리거되기 전에 큐에 동시에 있을 수 있는 통화 수입니다. OverflowThreshold는 0에서 1000(포함) 사이의 정수 값일 수 있습니다. 기본값은 Null이며, 이는 지정된 시간에 통화가 무제한으로 큐에 포함될 수 있음을 의미합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TimeoutAction</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.CallAction</p></td>
<td><p>시간 초과 임계값에 도달한 경우에 수행할 작업입니다. TimeoutAction은 <strong>New-CsRgsCallAction</strong> cmdlet을 사용하여 만들어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TimeoutThreshold</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>통화가 시간 초과되기 전까지 큐에 있을 수 있는 시간(초)입니다. 시간이 초과되면 TimeoutAction 매개 변수에 의해 지정된 작업이 수행됩니다.</p>
<p>시간 초과 임계값은 10초에서 65535초(약 18시간)(포함) 사이의 정수 값일 수 있습니다. 기본값은 Null이며, 이는 큐가 시간 초과되지 않음을 의미합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsRgsQueue**는 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsRgsQueue**는 Microsoft.Rtc.Rgs.Management.WritableSettings.Queue 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsRgsQueue](get-csrgsqueue.md)  
[Remove-CsRgsQueue](remove-csrgsqueue.md)  
[Set-CsRgsQueue](set-csrgsqueue.md)

