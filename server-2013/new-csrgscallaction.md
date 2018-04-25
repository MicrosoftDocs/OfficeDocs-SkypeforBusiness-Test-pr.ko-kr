---
title: New-CsRgsCallAction
TOCTitle: New-CsRgsCallAction
ms:assetid: 07b70bbd-8e2e-426f-8c30-29f74b07b55b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398136(v=OCS.15)
ms:contentKeyID: 49302716
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsRgsCallAction

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 응답 그룹 통화 작업을 만듭니다. 응답 그룹 응용 프로그램에서는 통화 작업을 사용하여 전화가 걸려 온 경우 시스템에서 수행할 작업을 결정합니다. 예를 들어 통화 작업은 다른 큐로 통화를 전송하거나, 특정 응답 그룹 질문을 묻거나, 통화를 종료하도록 지정할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsRgsCallAction -Action <Terminate | TransferToQueue | TransferToQuestion | TransferToUri | TransferToVoicemailUri | TransferToPstn> [-Prompt <Prompt>] [-Question <Question>] [-QueueID <RgsIdentity>] [-Uri <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 새 응답 그룹 통화 작업을 만든 다음 기존 응답 큐에 할당하는 방법을 보여 줍니다. 이 예제의 통화 작업은 큐 오버플로에 도달한 경우 수행되는 작업을 결정합니다. 이 작업을 수행하기 위해 먼저 **Get-CsRgsQueue**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에서 Help Desk Overflow라는 응답 그룹 응용 프로그램 큐를 검색합니다. 이 큐의 정보는 $x라는 변수에 저장되어 있습니다. 그런 다음 유사한 명령을 사용하여 $z라는 변수에 정보가 저장되어 있는 Help Desk 큐를 검색합니다.

큐를 검색한 후에는 **New-CsRgsPrompt** cmdlet을 사용하여 새 통화 작업을 실행할 텍스트 음성 변환 프롬프트를 만듭니다. 이 새 통화 작업은 **New-CsRgsCallAction** cmdlet을 실행하여 만듭니다. 이 통화 작업에는 Prompt(통화 작업에서 사용할 프롬프트), Action(새 통화 작업이 트리거된 경우에 발생하는 작업을 나타내며, 여기서 TransferToQueue 매개 변수 값은 통화가 다른 응답 큐로 전송됨을 의미함) 및 QueueID(통화가 전송되는 대체 큐로서, $x.Identity는 Help Desk Overflow라는 큐의 ID를 나타냄)의 세 가지 매개 변수가 할당됩니다. 새 통화 작업은 메모리에 만들어진 다음 변수 $y에 저장됩니다.

통화 작업을 만든 후에는 OverflowAction 속성 값을 새로 만든 통화 작업이 포함된 변수 $y로 설정하여 새 통화 작업을 Help Desk 큐에 할당할 수 있습니다. Help Desk 큐가 "오버플로", 즉 허용되는 최대 발신자 수에 도달한 경우 이후의 통화는 Help Desk Overflow 큐에 자동으로 전송됩니다.

끝으로, 이 예제의 마지막 명령은 **Set-CsRgsQueue**를 호출하여 ApplicationServer:atl-cs-001.litwareinc.com의 실제 Help Desk Overflow 큐 인스턴스에 변경 내용을 기록합니다.

    $x = Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk Overflow"
    $z = Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"
    
    $w = New-CsRgsPrompt -TextToSpeechPrompt "Please hold while we transfer your call."
    $y = New-CsRgsCallAction -Prompt $w -Action TransferToQueue -QueueID $x.Identity
    $z.OverflowAction = $y
    Set-CsRgsQueue $z

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령과 유사합니다. 그러나 예제 2에서는 새 통화 작업이 PSTN 전화 번호로 통화를 전송합니다. 이 작업을 수행하기 위해 새 통화 작업의 Action 속성을 TransferToPSTN으로 설정하고, Uri 속성을 "sip:+14255551298@litwareinc.com"으로 설정합니다.

    $w = New-CsRgsPrompt -TextToSpeechPrompt "Please hold while we transfer your call."
    $y = New-CsRgsCallAction -Prompt $w -Action TransferToPSTN -Uri "sip:+14255551298@litwareinc.com"
    $z = Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk Queue"
    $z.OverflowAction = $y
    Set-CsRgsQueue $z

## 자세한 정보

응답 그룹 응용 프로그램과 연결된 전화 번호로 전화가 걸려 오면 응용 프로그램에서 전화가 걸려 온 번호에 해당하는 워크플로를 확인합니다. 워크플로를 찾은 후에는 휴일이나 업무 시간 이후에 전화를 받았는지 여부를 확인합니다. 휴일이나 업무 시간 외에 전화를 받은 경우 이러한 전화에 대해 지정된 작업을 수행합니다. 예를 들어 통화가 바로 음성 메일로 전송될 수 있습니다. 업무 시간 중에 전화를 받은 경우에는 응답 그룹 응용 프로그램에서 업무 시간에 받은 통화에 대해 미리 구성된 작업을 수행합니다. 이러한 작업은 모두 미리 결정되며 **New-CsRgsCallAction** cmdlet을 사용하여 만듭니다. **New-CsRgsCallAction**을 사용하면 통화를 응답 그룹 큐에 배치하거나, 음성 메일, SIP 주소 또는 PSTN(공중 전화망) 전화 번호로 전달하거나, IVR(대화형 음성 응답) 질문으로 전송하거나, 종료할 수 있습니다.

**New-CsRgsCallAction**을 사용하는 경우 워크플로, 큐 또는 다른 응답 그룹 응용 프로그램 요소의 속성을 직접 수정할 수는 없습니다. 새로 만든 통화 작업은 처음에 메모리에만 존재하고 개체 참조 변수(예: $x)에 저장되기 때문입니다. 워크플로의 DefaultAction 속성과 같은 특정 항목을 수정하려면 해당 속성에 개체 참조를 할당합니다(예:

\-DefaultAction $x).

DefaultAction 속성에 할당할 수 있는 통화 작업은 TransferToQueue와 TransferToQuestion 두 가지뿐입니다. TransferToQueue와 TransferToQuestion을 제외하고 다른 모든 통화 작업은 휴일이나 업무 시간 외에 발생하는 작업에 적용됩니다. 또한 TransferToQuestion 외의 모든 통화 작업은 큐 시간 초과 및 오버플로에 사용될 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **New-CsRgsCallAction** cmdlet을 로컬로 실행할 수 있습니다. 그러나 이 cmdlet은 메모리에만 나타나는 개체를 만들고 자체적으로 시스템을 변경하지 않기 때문에 기본적으로 누구든지 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsRgsCallAction"}

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
<td><p><em>Action</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.Action</p></td>
<td><p>수행할 통화 작업을 나타냅니다. Action은 다음 값 중 하나로 설정해야 합니다.</p>
<p>Terminate – 통화가 종료됩니다.</p>
<p>TransferToQueue – 통화가 응답 그룹 큐로 전송됩니다.</p>
<p>TransferToQuestion – 통화가 응답 그룹 질문으로 전송됩니다.</p>
<p>TransferToUri – 통화가 지정된 SIP URI(Uniform Resource Identifier)로 전송됩니다.</p>
<p>TransferToVoiceMailUri – 통화가 음성 메일로 전송됩니다.</p>
<p>TransferToPSTN - 통화가 PSTN(공중 전화망) 전화로 전송됩니다.</p>
<p>새 통화 작업을 만들 때마다 Action을 지정해야 하며, 기본값은 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Prompt</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.Prompt</p></td>
<td><p>통화 작업을 수행하기 전에 재생할 프롬프트(예: &quot;통화가 전송될 때까지 기다리십시오.&quot;)입니다. 프롬프트는 <strong>New-CsRgsPrompt</strong> cmdlet을 사용하여 만들어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Question</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.Question</p></td>
<td><p>Action이 TransferToQuestion으로 설정된 경우에 물어볼 질문입니다. 질문은 <strong>New-CsRgsQuestion</strong> cmdlet을 사용하여 만들어야 합니다.</p>
<p>Action이 TransferToQuestion으로 설정된 경우 이 매개 변수가 필요합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>QueueID</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>Action이 TransferToQueue로 설정된 경우 통화를 전송할 대상 응답 그룹 큐의 ID입니다. QueueID는 <strong>Get-CsRgsQueue</strong>를 사용하여 해당 큐의 ID를 검색하는 방법으로 지정하는 것이 가장 좋습니다.</p>
<p>Action이 TransferToQueue로 설정된 경우 이 매개 변수가 필요합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Uri</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>통화를 전송할 대상 SIP 주소, 음성 메일 URI 또는 PSTN 전화 번호입니다.</p>
<p>Action이 TransferToUri, TransferToVoiceMailUri 또는 TransferToPSTN으로 설정된 경우 이 매개 변수가 필요합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsRgsCallAction**은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsRgsCallAction**은 Microsoft.Rtc.Rgs.Management.WritableSettings.CallAction 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsRgsQueue](new-csrgsqueue.md)  
[Set-CsRgsQueue](set-csrgsqueue.md)

