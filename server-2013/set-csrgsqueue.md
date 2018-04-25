---
title: Set-CsRgsQueue
TOCTitle: Set-CsRgsQueue
ms:assetid: c1656757-c1d9-4e63-947d-99bd331da210
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412947(v=OCS.15)
ms:contentKeyID: 49304927
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsRgsQueue

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 응답 그룹 큐를 수정합니다. 응답 그룹 응용 프로그램을 사용하면 응답 그룹 에이전트가 통화에 응답할 수 있을 때까지 전화 통화가 큐에 배치되고 발신자는 통화 대기 상태가 됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsRgsQueue -Instance <Queue> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 Help Desk 응답 그룹 큐에 대한 OverflowCandidate 속성을 수정합니다. 이 작업을 수행하기 위해 이 예제의 첫 번째 명령은 **Get-CsRgsQueue**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에서 지정된 큐(-Name "Help Desk")를 검색합니다. 그런 다음 검색된 큐는 변수 $x에 저장됩니다.

큐를 검색한 후에는 이 예제의 두 번째 명령에서 이 가상 큐의 OverflowCandidate 속성 값을 NewestCall로 설정합니다. 이 명령이 완료되는 즉시 이 예제의 마지막 명령은 **Set-CsRgsQueue**를 사용하여 실제 Help Desk 큐에 이러한 변경 내용을 기록합니다. 이 시점까지는 변경 내용이 메모리에만 적용됩니다. 즉, **Set-CsRgsQueue**를 호출할 때까지 ApplicationServer:atl-cs-001.litwareinc.com의 실제 응답 그룹 큐가 변경되지 않은 상태로 유지됩니다.

    $x = Get-CsRgsQueue -Identity Service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"
    $x.OverflowCandidate = "NewestCall"
    Set-CsRgsQueue -Instance $x

## 예제 2

예제 2에 표시된 명령은 새 응답 그룹 통화 작업을 만들어 기존 응답 그룹 큐에 할당하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 먼저 **Get-CsRgsQueue**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에서 Help Desk Overflow 응답 그룹 큐를 검색합니다. 이 큐에 대한 정보는 변수 $x에 저장됩니다.

큐를 검색한 후에는 **New-CsRgsPrompt** cmdlet을 사용하여 새 텍스트 음성 변환 프롬프트를 만듭니다. 이 프롬프트는 $w라는 변수에 저장됩니다. 그런 다음 **New-CsRgsCallAction** cmdlet을 사용하여 새 통화 작업을 만듭니다. 이 통화 작업에는 Prompt(통화 작업에서 사용할 프롬프트), Action(새 통화 작업이 트리거된 경우에 발생하는 작업을 나타내며, 여기서 TransferToQueue 매개 변수 값은 통화가 다른 응답 큐로 전송됨을 의미함) 및 QueueID(통화가 전송되는 대체 큐로서, $x.Identity는 Help Desk Overflow라는 큐의 ID를 나타냄)의 세 가지 매개 변수가 할당됩니다. 이 새 통화 작업은 메모리에 만들어진 다음 변수 $y에 저장됩니다.

다음 명령은 수정할 큐(이 예제에서는 ApplicationServer:atl-cs-001.litwareinc.com의 Help Desk 큐)를 검색합니다. Get-CsRgsQueue에서 이 큐를 검색한 후에는 변수 $z에 큐 개체가 저장됩니다.

이러한 작업이 모두 완료되면 OverflowAction 속성 값을 새로 만든 통화 작업이 포함된 변수인 $y로 설정하여 새 통화 작업을 Help Desk 큐에 할당할 수 있습니다.

통화 작업이 할당된 후 이 예제의 마지막 명령은 **Set-CsRgsQueue**를 호출하여 ApplicationServer:atl-cs-001.litwareinc.com의 실제 Help Desk 큐 인스턴스에 변경 내용을 기록합니다.

    $x = Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk Overflow Queue"
    $w = New-CsRgsPrompt -TextToSpeechPrompt "Please hold while we transfer your call."
    $y = New-CsRgsCallAction -Prompt $w -Action TransferToQueue -QueueID $x.Identity
    $z = Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"
    $z.OverflowAction = $y
    Set-CsRgsQueue -Instance $z

## 자세한 정보

발신자가 응답 그룹 응용 프로그램과 연결된 전화 번호로 전화를 걸면 일반적으로 통화를 계속하기 위해 발신자가 응답해야 하는 질문(예: "하드웨어 지원을 받으려면 1번을, 소프트웨어 지원을 받으려면 2번을 누르십시오.")으로 통화가 전송되거나 에이전트가 통화에 응답할 수 있을 때까지 통화가 큐에 배치됩니다.

응답 그룹 응용 프로그램을 사용하면 모든 전화 통화에 대해 단일 큐를 지정하는 대신 서로 다른 워크플로 및 에이전트 그룹과 연결될 수 있는 여러 큐를 만들 수 있습니다. 따라서 큐에서 동시에 대기 중인 X개의 통화와 같은 이벤트 또는 X초 동안 통화 대기 중인 발신자에 대해 큐가 다른 방식으로 응답할 수 있습니다.

**Set-CsRgsQueue**를 사용하면 기존 응답 그룹 큐를 수정할 수 있습니다. **Set-CsRgsQueue**를 사용하여 큐를 직접 수정할 수는 없습니다. 예를 들어 이 cmdlet은 오버플로 임계값 또는 오버플로 작업을 변경할 수 있는 매개 변수를 포함하지 않습니다. 큐를 수정하려면 먼저 **Get-CsRgsQueue**를 사용하여 해당 큐를 검색한 다음 변수에 저장하는 방식으로 큐에 대한 개체 참조를 만들어야 합니다. 그런 다음 큐 속성에 새 값을 할당하여 메모리 내에서 큐를 수정합니다. 모든 변경 내용을 적용한 후에는 **Set-CsRgsQueue**를 호출하여 실제 응답 그룹 큐에 이러한 변경 내용을 다시 기록합니다. **Set-CsRgsQueue**를 호출하지 않으면 변경 내용이 메모리에만 적용되고 Windows PowerShell을 닫거나 개체 참조 변수를 삭제하는 즉시 사라집니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsRgsQueue** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsRgsQueue"}

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
<td><p>수정할 응답 그룹 큐에 대한 개체 참조입니다. 일반적으로 개체 참조는 <strong>Get-CsRgsQueue</strong> cmdlet을 사용하여 반환된 값을 변수에 할당하는 방식으로 검색합니다. 예를 들어 이 명령은 Help Desk 큐에 대한 개체 참조를 반환하여 해당 개체 참조를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name &quot;Help Desk&quot;</p></td>
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

Microsoft.Rtc.Rgs.Management.WritableSettings.Queue object. **Set-CsRgsQueue**는 응답 그룹 워크플로 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsRgsQueue**는 개체나 값을 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Rgs.Management.WritableSettings.Queue 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsRgsQueue](get-csrgsqueue.md)  
[New-CsRgsQueue](new-csrgsqueue.md)  
[Remove-CsRgsQueue](remove-csrgsqueue.md)

