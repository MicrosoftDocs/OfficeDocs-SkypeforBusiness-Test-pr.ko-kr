---
title: New-CsRgsAnswer
TOCTitle: New-CsRgsAnswer
ms:assetid: aba521db-1741-4da3-aaf0-2d78fda4c4d2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412812(v=OCS.15)
ms:contentKeyID: 49304692
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsRgsAnswer

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 응답 그룹 응답을 만듭니다. 응답 그룹 응답은 발신자의 응답을 적절한 작업과 연결하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsRgsAnswer -Action <CallAction> [-DtmfResponse <String>] [-Name <String>] [-VoiceResponseList <PSListModifier>]

## 자세한 정보

통화를 처리하기 위해 응답 그룹 응용 프로그램에서는 종종 문을 작성하거나 질문을 제공한 다음 고객의 응답을 기반으로 작업을 수행합니다. 예를 들어 서비스에서 발신자에게 영어로 통화하려면 1을 누르고, 스페인어로 통화하려면 2를 누르라고 요청할 수 있습니다. 이와 같은 질문이 제공된 후에는 시스템에서 발신자가 응답할 때까지 기다린 다음 적절한 작업을 수행해야 합니다. 즉, 발신자가 전화기 키패드의 1을 누른 경우 통화를 영어 큐로 전송하고, 키패드의 2를 누른 경우 스페인어 큐로 통화를 전송합니다.

응답 그룹 응답은 발신자의 응답을 분석한 다음 적절한 작업을 수행하는 데 사용됩니다. 예를 들어 발신자에게 1 또는 2를 누를 수 있는 옵션이 제공된 경우 이 상황을 처리하려면 발신자가 1을 눌렀을 때 수행할 작업과 2를 눌렀을 때 수행할 작업을 지정하는 두 개의 응답 그룹 응답이 필요합니다. **New-CsRgsAnswer** cmdlet을 사용하여 이 두 응답을 만든 다음 해당 응답 그룹 질문(발신자에게 1 또는 2를 누르도록 요청한 질문)에 추가해야 합니다. 응답 그룹 응답은 허용되는 음성 응답 집합(예: "영어"라는 단어) 또는 적절한 전화기 키패드 응답(예: 1을 누름)을 포함해야 합니다. 또는 음성 응답이나 키패드 응답을 사용할 수 있는 옵션, 즉 "영어"라는 단어를 말하거나 키패드에서 1을 누를 수 있는 옵션을 고객에게 제공할 수 있습니다. 이러한 상황에서는 사용되는 음성 인식 언어는 상위 워크플로에 사용된 언어와 같습니다.

응답 그룹 응답은 저장했다가 다른 질문에 다시 사용할 수 없습니다. 예를 들어 발신자가 9를 누를 때마다 통화를 음성 메일로 전송하는 응답이 있으며 이 응답을 응답 그룹 질문과 연결했다고 가정해 보겠습니다. 나중에 9를 눌러 통화를 음성 메일로 전송할 수 있는 옵션을 발신자에게 제공하는 새 질문을 만든 경우 응답 그룹 응답의 새 인스턴스를 만들어야 합니다. 응답을 저장한 다음 저장된 응답을 반복해서 사용할 수 있는 방법이 없기 때문입니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **New-CsRgsAnswer** cmdlet을 로컬로 실행할 수 있습니다. 그러나 이 cmdlet은 메모리에만 나타나는 개체를 만들고 자체적으로 시스템을 변경하지 않기 때문에 기본적으로 누구든지 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsRgsAnswer"}

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
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.CallAction</p></td>
<td><p>발신자가 이 응답을 제공할 때마다 수행할 작업을 나타냅니다. Action 매개 변수는 <strong>New-CsRgsCallAction</strong> cmdlet을 통해 만든 개체 참조를 사용하여 지정해야 합니다. 자세한 내용은 이 항목의 예제 섹션을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>DtmfResponse</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>응답과 일치하기 위해 눌러야 하는 전화기 키패드의 키를 나타냅니다. 예를 들어 발신자에게 하드웨어의 경우 1을 누르라고 요청하려면 DtmfResponse를 -DtmfResponse 1과 같이 구성합니다.</p>
<p>하나의 응답이 음성 응답과 DTMF(Dual-Tone Multifrequency) 응답을 둘 다 포함할 수 있으며, 각 응답은 이 두 응답 유형 중 적어도 하나를 포함해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>응답 그룹 응답에 지정된 이름입니다. 이름은 고유하지 않아도 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>VoiceResponseList</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>발신자가 말할 수 있는 응답과 일치하는 키워드 배열입니다. 예를 들어 발신자에게 제공된 하나의 옵션이 &quot;하드웨어&quot;인 경우 VoiceResponseList 속성은 -VoiceResponseList &quot;Hardware&quot;로 설정될 수 있습니다. 쉼표로 구분된 값을 사용하여 여러 키워드를 지정할 수도 있습니다. 예를 들어 매개 변수 값을 -VoiceResponseList Hardware, Devices로 설정하면 하드웨어 또는 장치가 응답과 일치하게 됩니다. 음성 응답에는 큰따옴표를 사용할 수 없습니다. 음성 엔진에서 이 문자를 인식하지 못하기 때문입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsRgsAnswer**은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Rgs.Management.WritableSettings.Answer 개체의 새 인스턴스를 만듭니다.

## 예제

## 예제 1

예제 1에 표시된 명령은 응답 그룹 큐와 응답 그룹 통화 작업이 둘 다 연결된 새 응답 그룹 응답을 만드는 방법을 보여 줍니다. 이 예제의 첫 번째 명령은 **New-CsRgsPrompt** cmdlet을 사용하여 새 응답에 대한 TextToSpeechPrompt를 만듭니다. 그런 다음 **Get-CsRgsQueue** cmdlet을 호출하여 Help Desk 응답 그룹 큐에 대한 개체 참조($x)를 반환합니다. 이 개체 참조는 **New-CsRgsCallAction**을 사용하여 발신자를 Help Desk 큐로 전송하는 통화 작업을 만드는 다음 명령에서 사용됩니다. 이 통화 작업은 변수 $y에 저장됩니다.

이 예제의 마지막 명령은 $a 변수에 저장되는 응답 그룹 응답을 만듭니다. 이 응답은 DTMF 응답 1(전화기 키패드에서 1을 누름) 또는 음성 응답 "Yes"를 허용합니다.

이 응답을 만든 후 응답 그룹 질문에 연결할 수 있습니다. 자세한 내용은 [New-CsRgsQuestion](new-csrgsquestion.md) 도움말 항목을 참조하십시오.

    $w = New-CsRgsPrompt -TextToSpeechPrompt "Please hold while we transfer your call."
    $x = Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"
    
    $y = New-CsRgsCallAction -Prompt $w -Action TransferToQueue -QueueID $x.Identity
    
    $a = New-CsRgsAnswer -Action $y -DtmfResponse 1 -VoiceResponseList Yes -Name "New Service Request"

## 참고 항목

#### 기타 리소스

[New-CsRgsQuestion](new-csrgsquestion.md)

