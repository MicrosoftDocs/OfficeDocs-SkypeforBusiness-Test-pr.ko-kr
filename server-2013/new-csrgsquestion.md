---
title: New-CsRgsQuestion
TOCTitle: New-CsRgsQuestion
ms:assetid: 0ed9f3b4-cbc5-41ca-8547-2300b579b119
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398186(v=OCS.15)
ms:contentKeyID: 49302811
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsRgsQuestion

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 응답 그룹 질문을 만듭니다. 응답 그룹 응용 프로그램에서는 질문을 사용하여 발신자에게 원하는 사항을 선택하도록 한 다음 해당 선택 사항을 기반으로 작업을 수행합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsRgsQuestion -Prompt <Prompt> [-AnswerList <PSListModifier>] [-InvalidAnswerPrompt <Prompt>] [-Name <String>] [-NoAnswerPrompt <Prompt>]

## 예제

## 예제 1

예제 1에 표시된 명령은 한 쌍의 응답 그룹 응답을 만든 다음 이러한 응답을 새 응답 그룹 질문에 연결합니다. 두 개의 응답을 만들려면 먼저 발신자가 제공한 응답을 기반으로 수행할 통화 작업을 지정해야 합니다. 따라서 이 예제의 처음 두 명령은 New Service Request와 Existing Service Request의 응답 그룹 큐 쌍에 대한 참조 개체를 만듭니다. 이러한 개체 참조가 만들어지면 다음 명령에서 **New-CsRgsPrompt**를 사용하여 변수 $w에 저장되는 텍스트 음성 변환 프롬프트를 만듭니다.

작업이 완료되면 다음 두 명령에서 해당 통화 작업 쌍, 즉 발신자를 New Service Request 큐로 전송하는 통화 작업과 발신자를 Existing Service Request 큐로 전송하는 통화 작업을 만듭니다. 통화 작업을 만든 후에는 **New-CsRgsAnswer** cmdlet을 사용하여 각각 $newRequest 변수 및 $existingRequest 변수에 저장되는 두 개의 응답 그룹 응답을 만듭니다.

두 개의 응답이 저장되면 **New-CsRgsPrompt**를 사용하여 새 질문에 대한 프롬프트를 만들 수 있습니다. 이 예제의 프롬프트는 발신자에게 새 서비스 요청의 경우 1을 누르거나 "New"라고 응답하고, 기존 서비스 요청의 경우 2를 누르거나 "Existing"이라고 응답하라는 안내하는 텍스트 음성 변환 프롬프트입니다. 이 프롬프트 자체는 $u 변수에 저장됩니다.

프롬프트를 만든 후에는 **New-CsRgsQuestion**을 호출하여 새 질문을 만들 수 있습니다. Prompt 매개 변수뿐 아니라 AnswerList 매개 변수도 질문과 연결된 두 개의 응답, 즉 $newRequest 및 $existingRequest 변수를 나타내는 데 사용됩니다.

    $new = Get-CsRgsQueue -Identity service:ApplicationServer:pool0.litwareinc.com -Name "New Service Request"
    $existing = Get-CsRgsQueue -Identity service:ApplicationServer:pool0.litwareinc.com -Name "Existing Service Request"
    
    $w = New-CsRgsPrompt -TextToSpeechPrompt "Please hold while we transfer your call."
    
    $y = New-CsRgsCallAction -Prompt $w -Action TransferToQueue -QueueID $new.Identity
    $z = New-CsRgsCallAction -Prompt $w -Action TransferToQueue -QueueID $existing.Identity
    
    $newRequest = New-CsRgsAnswer -Action $y -DtmfResponse 1 -VoiceResponseList "New" -Name "New Request"
    $existingRequest = New-CsRgsAnswer -Action $z -DtmfResponse 2 -VoiceResponseList "Existing" -Name "Existing Request"
    
    $u = New-CsRgsPrompt -TextToSpeechPrompt "Press 1 or say New for a new service request. Press 2 or say Existing for an existing service request."
    
    $question = New-CsRgsQuestion -Prompt $u -AnswerList $newRequest $newRequest, $existingRequest 

## 자세한 정보

통화를 처리하기 위해 응답 그룹 응용 프로그램에서는 종종 문을 작성하거나 질문을 제공한 다음 발신자의 응답을 기반으로 작업을 수행합니다. 예를 들어 서비스에서 발신자에게 영어로 통화하려면 1을 누르고, 스페인어로 통화하려면 2를 누르라고 요청할 수 있습니다. 이와 같은 질문이 제공된 후에는 시스템에서 발신자가 응답할 때까지 기다린 다음 적절한 작업을 수행해야 합니다. 즉, 발신자가 전화기 키패드의 1을 누른 경우 통화를 영어 큐로 전송하고, 키패드의 2를 누른 경우 스페인어 큐로 통화를 전송합니다.

질문을 만들려면 **New-CsRgsQuestion** cmdlet을 사용해야 합니다. 또한 응답 그룹 질문을 만들 때 적어도 프롬프트(즉, 실제 질문 자체)와 일련의 지원되는 응답을 제공해야 합니다. 예를 들어 1 또는 2를 누를 때의 옵션을 발신자에게 제공하려면 두 가지 응답이 있어야 합니다. 하나는 발신자가 1을 누를 때 수행할 작업을 지정하고, 다른 하나는 발신자가 2를 누를 때 수행할 작업을 지정합니다. 발신자에게 1, 2, 3, 4를 누를 수 있는 옵션을 제공할 경우 마찬가지로 네 가지 응답을 지정해야 합니다.

또한 **New-CsRgsQuestion**을 사용하면 발신자가 잘못된 응답을 제공하거나 응답하지 않은 경우에 사용할 프롬프트를 지정할 수 있습니다. 예를 들어 처음 시나리오에서 발신자가 3을 누른 경우 "죄송합니다. 올바른 응답이 아닙니다."라는 프롬프트가 제공될 수 있습니다. 그런 다음 원래 프롬프트가 재생됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdminsBy 그룹의 구성원은 **New-CsRgsQuestion** cmdlet을 로컬로 실행할 수 있습니다. 그러나 이 cmdlet은 메모리에만 나타나는 개체를 만들고 자체적으로 시스템을 변경하지 않기 때문에 기본적으로 누구든지 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsRgsQuestion"}

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
<td><p><em>Prompt</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.Prompt</p></td>
<td><p>발신자에게 제공할 질문입니다. 프롬프트는 <strong>New-CsRgsPrompt</strong> cmdlet을 사용하여 만들어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AnswerList</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>질문에 대한 유효한 응답 배열입니다. 예를 들어 지원 센터 질문에는 하드웨어 지원, 소프트웨어 설치, 네트워크 연결 등의 응답이 제공될 수 있습니다. 응답은 <strong>New-CsRgsAnswer</strong> cmdlet을 사용하여 만들어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InvalidAnswerPrompt</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.Prompt</p></td>
<td><p>발신자가 잘못된 응답을 선택한 경우에 실행할 응답입니다. InvalidAnswerPrompt는 <strong>New-CsRgsPrompt</strong> cmdlet을 사용하여 만들어야 합니다. InvalidAnswerPrompt를 재생한 후에는 응용 프로그램에서 원래 프롬프트를 반복합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>질문의 식별자입니다. 질문 이름은 고유하지 않아도 되며, 128자 이내여야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NoAnswerPrompt</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.Prompt</p></td>
<td><p>발신자가 초기 프롬프트에 응답하지 않은 경우에 실행할 응답입니다. NoAnswerPrompt는 <strong>New-CsRgsPrompt</strong> cmdlet을 사용하여 만들어야 합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsRgsQuestion**은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsRgsQuestion**은 Microsoft.Rtc.Management.WriteableSettings.Question 개체의 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsRgsAnswer](new-csrgsanswer.md)

