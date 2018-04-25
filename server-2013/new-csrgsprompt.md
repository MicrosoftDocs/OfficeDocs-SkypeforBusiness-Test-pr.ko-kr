---
title: New-CsRgsPrompt
TOCTitle: New-CsRgsPrompt
ms:assetid: 6812acbf-ae56-43a6-a2d7-e28a930f81c7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398486(v=OCS.15)
ms:contentKeyID: 49303900
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsRgsPrompt

 

_**마지막으로 수정된 항목:** 2015-03-09_

응답 그룹 응용 프로그램의 새 워크플로 프롬프트를 만듭니다. 워크플로 프롬프트는 각각 재생되거나 소리 내어 읽는 방식으로 발신자에게 추가 정보를 제공하는 오디오 파일 또는 텍스트입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsRgsPrompt [-AudioFilePrompt <AudioFile>] [-TextToSpeechPrompt <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 워크플로 프롬프트 및 응답 그룹 큐를 새 통화 작업에 포함하는 방법을 보여 줍니다. 첫 번째 명령은 **Get-CsRgsQueue** cmdlet을 사용하여 Help Desk 응답 그룹 큐에 대한 개체 참조($queue)를 반환합니다. 그런 다음 두 번째 명령에서 **New-CsRgsPrompt** cmdlet을 사용하여 "Welcome to the help desk. Please hold."라는 새 텍스트 음성 변환 프롬프트를 만듭니다. 이 새 프롬프트는 $prompt 변수에 저장됩니다.

이 예제의 마지막 명령은 **New-CsRgsCallAction**을 사용하여 새 응답 그룹 통화 작업($z)을 만듭니다. 통화 작업을 만들 때 새로 만든 워크플로 프롬프트가 포함된 $prompt 개체 참조를 Prompt 매개 변수 값으로 사용합니다. 마찬가지로 $queue 개체 참조는 QueueID 매개 변수와 함께 사용됩니다. 이 명령을 실행하면 새 통화 작업 및 해당 새 워크플로 프롬프트가 응답 그룹 워크플로에 추가됩니다.

    $queue = Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk"
    
    $prompt = New-CsRgsPrompt -TextToSpeechPrompt "Welcome to the help desk. Please hold."
    
    $z = New-CsRgsCallAction -Prompt $prompt -Action TransferToQueue -QueueID $queue.Identity

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령의 변형입니다. 그러나 이 경우 새 워크플로 프롬프트는 텍스트 음성 변환 프롬프트뿐 아니라 오디오 파일 프롬프트도 포함합니다. 워크플로 프롬프트에 오디오 파일을 포함하기 위해 이 예제의 두 번째 명령은 **Import-CsRgsAudioFile** cmdlet을 사용하여 C:\\Media\\Welcome.wav 오디오 파일을 가져옵니다. 가져온 파일은 $audioFile 변수에 저장됩니다.

오디오 파일을 가져온 후에는 이 파일과 텍스트 음성 변환 프롬프트가 둘 다 새 워크플로 프롬프트($prompt)에 추가됩니다. 이 작업을 수행하기 위해 AudioFilePrompt 매개 변수는 $audioFile로 설정하고 TextToSpeechPrompt 매개 변수는 텍스트 값 "Welcome to the help desk. Please hold."로 설정합니다.

    $queue = Get-CsRgsQueue -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk Queue"
    
    $audioFile = Import-CsRgsAudioFile -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" -FileName "welcome.wav" -Content (Get-Content C:\Media\Welcome.wav -Encoding byte -ReadCount 0)
    
    $prompt = New-CsRgsPrompt -AudioFilePrompt $audioFile -TextToSpeechPrompt "Welcome to the help desk. Please hold."
    
    $z = New-CsRgsCallAction -Prompt $prompt -Action TransferToQueue -QueueID $queue.Identity

## 자세한 정보

발신자에게 현재 상황 및 이유를 설명하는 것은 응답 그룹 워크플로의 중요한 부분입니다. 예를 들어 전화에 응답한 다음 에이전트와 통화할 수 있을 때까지 통화 대기 상태로 즉시 전환되도록 워크플로를 구성할 수 있습니다. 이 경우 발신자에게 1) 전화가 연결되었으며, 2) 에이전트와 통화할 수 있을 때까지 통화 대기 상태에 놓이게 됨을 알려 주어야 합니다. 이러한 정보를 제공하는 것이 워크플로 프롬프트의 역할입니다.

응답 그룹 응용 프로그램은 두 가지 워크플로 프롬프트를 지원합니다. 첫째, 오디오 파일을 미리 녹음한 다음 재생할 수 있습니다. 이렇게 하려면 프롬프트("잠시 기다려 주십시오. 전화해 주셔서 감사합니다.")를 .WAV 또는 .WMA 형식으로 녹음한 다음 **Import-CsRgsAudioFile** cmdlet을 사용하여 파일을 가져와 워크플로 프롬프트에 할당해야 합니다. 또는 읽을 텍스트를 제공하기만 해도 됩니다. 프롬프트가 필요한 경우 응답 그룹 응용 프로그램에서 텍스트 음성 변환 기능을 사용하여 텍스트를 소리내어 "읽을" 수 있습니다. 텍스트 음성 변환 프롬프트는 녹음하여 가져올 오디오 파일이 없기 때문에 쉽게 구성할 수 있습니다. 그러나 오디오 파일 프롬프트는 일반적으로 높은 품질이 요구됩니다.

텍스트 음성 변환 프롬프트에 사용되는 언어는 상위 워크플로에 사용된 언어와 같아야 합니다.

**New-CsRgsPrompt** cmdlet을 사용하면 워크플로 프롬프트를 만들 수 있습니다. 프롬프트를 사용해야 할 때마다 새로 만들어야 합니다. 프롬프트를 저장하고 다시 사용할 방법이 없기 때문입니다. 마찬가지로 오디오 파일도 다시 가져와야 합니다. 새 워크플로 프롬프트를 만드는 경우 텍스트 음성 변환 프롬프트를 제공해야 합니다. 원하는 경우 오디오 파일 프롬프트를 제공할 수도 있습니다. 텍스트 음성 변환 프롬프트와 오디오 파일 프롬프트를 둘 다 제공한 경우에는 응답 그룹 응용 프로그램에서 기본적으로 오디오 파일을 사용하며, 오디오 파일을 사용할 수 없는 경우에만 텍스트 음성 변환 프롬프트를 사용합니다. 새 프롬프트가 메모리에 만들어지면 일반적으로 해당 개체 참조가 응답 그룹 통화 작업에 추가됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **New-CsRgsPrompt** cmdlet을 로컬로 실행할 수 있습니다. 그러나 이 cmdlet은 메모리에만 나타나는 개체를 만들고 자체적으로 시스템을 변경하지 않기 때문에 기본적으로 누구든지 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsRgsPrompt"}

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
<td><p><em>AudioFilePrompt</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.AudioFile</p></td>
<td><p>워크플로가 활성화된 경우에 재생할 오디오 파일입니다. 오디오 파일은 <strong>Import-CsRgsAudioFile</strong> cmdlet을 사용하여 가져와야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TextToSpeechPrompt</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>워크플로가 활성화된 경우에 읽을 TTS(텍스트 음성 변환) 프롬프트입니다. 오디오 파일을 지정하지 않은 경우에만 사용되는 TTS 프롬프트는 최대 4096자를 포함할 수 있습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsRgsPrompt**는 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsRgsPrompt**는 Microsoft.Rtc.Management.WritableSettings.Prompt 개체의 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Import-CsRgsAudioFile](import-csrgsaudiofile.md)  
[New-CsRgsCallAction](new-csrgscallaction.md)

