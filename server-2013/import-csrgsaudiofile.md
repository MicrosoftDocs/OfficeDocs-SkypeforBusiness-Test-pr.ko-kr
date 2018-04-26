---
title: Import-CsRgsAudioFile
TOCTitle: Import-CsRgsAudioFile
ms:assetid: ae9dfd76-9b3e-4c51-9692-39d1fe8e430b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412830(v=OCS.15)
ms:contentKeyID: 49304725
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Import-CsRgsAudioFile

 

_**마지막으로 수정된 항목:** 2015-03-09_

응답 그룹 응용 프로그램에서 사용할 새 오디오 파일을 가져옵니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Import-CsRgsAudioFile -Content <Byte[]> -FileName <String> -Identity <RgsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 오디오 파일(C:\\Media\\WhileYouWait.wav)을 가져와 워크플로의 CustomMusicOnHold 속성에 할당합니다. 이 작업을 수행하기 위해 첫 번째 명령은 **Import-CsRgsAudioFile**을 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에서 찾은 응답 그룹 응용 프로그램으로 오디오 파일을 가져옵니다. 이때 서비스 위치를 지정하는 Identity 매개 변수와 함께 FileName 매개 변수를 사용하여 가져올 파일의 파일 이름을 지정합니다.

이와 동시에 Content 매개 변수도 오디오 파일을 가져오는 데 사용됩니다. 가져올 파일의 경로를 뒤에 입력하고 **Get-Content** cmdlet을 호출하여 파일을 가져오면 됩니다. **Get-Content**를 사용할 때는 인코딩 유형을 바이트로 설정하고 ReadCount를 0으로 설정해야 합니다. ReadCount를 0으로 설정하면 한 번의 작업으로 전체 파일을 읽을 수 있습니다. 가져온 파일은 변수 $x에 저장됩니다.

두 번째 명령은 **Get-CsRgsWorkflow**를 사용하여 Help Desk Workflow라는 워크플로에 대한 개체 참조($y)를 만듭니다. 이 개체 참조를 만든 후 세 번째 명령은 CustomMusicOnHoldFile 속성 값을 $x(가져온 오디오 파일이 포함된 변수)로 설정합니다. 끝으로, 이 예제의 마지막 명령은 **Set-CsRgsWorkflow**를 사용하여 실제 Help Desk Workflow에 이러한 변경 내용을 기록합니다. **Set-CsRgsWorkflow**를 호출하지 않으면 수정 사항이 메모리에만 존재하고 Windows PowerShell을 닫거나 $x 또는 $y를 삭제하는 즉시 사라집니다.

    $x = Import-CsRgsAudioFile -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" -FileName "WhileYouWait.wav" -Content (Get-Content C:\Media\WhileYouWait.wav -Encoding byte -ReadCount 0)
    
    $y = Get-CsRgsWorkflow -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" -Name "Help Desk Workflow"
    $y.CustomMusicOnHoldFile = $x
    
    Set-CsRgsWorkflow $y

## 자세한 정보

응답 그룹 응용 프로그램에서는 적어도 두 가지 방법으로 오디오 파일(.WAV 또는 .WMA 형식만)을 사용할 수 있습니다. 예를 들어 발신자가 통화 대기 상태에 놓일 때마다 음악 또는 알림을 재생할 수 있습니다. 또한 응답 그룹 응용 프로그램에서 간혹 발신자와 "대화"해야 하는 경우도 있습니다. 예를 들어 IVR(대화형 음성 응답)을 사용하여 발신자에게 "기존 주문과 관련하여 전화하셨습니까?"와 같은 질문을 할 수 있습니다. 텍스트 음성 변환 기술을 사용하여 서비스에서 이러한 질문을 읽도록 하거나 실제 사람이 질문하는 오디오 녹음을 재생할 수 있습니다.

어떤 방법으로 오디오 파일을 사용하든 관계없이 파일 자체는 **Import-CsRgsAudioFile** cmdlet을 사용하여 응답 그룹 응용 프로그램으로 가져와야 합니다. 또한 오디오 파일이 응답 그룹 응용 프로그램에서 이미 사용 중인 경우에도 해당 파일을 사용하려고 할 때마다 **Import-CsRgsAudioFile**을 실행해야 합니다. 예를 들어 지정된 오디오 파일을 워크플로 A에서 사용자 지정 대기 음악 파일로 사용하고 있을 때 이 오디오 파일을 워크플로 B에서 사용자 지정 대기 음악으로 사용하려는 경우를 가정해 보겠습니다. 응답 그룹 응용 프로그램에서 오디오 파일을 이미 사용 중인 경우에도 워크플로 B에서 이 오디오 파일을 사용하려면 파일을 가져와야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Import-CsRgsAudioFile** cmdlet을 로컬로 실행할 수 있습니다. 또한 대상 컴퓨터 파일 저장소에 대한 쓰기 권한이 있어야 합니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Import-CsRgsAudioFile"}

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
<td><p><em>Content</em></p></td>
<td><p>필수</p></td>
<td><p>System.Byte[]</p></td>
<td><p>가져올 오디오 파일의 실제 콘텐츠입니다. <strong>Get-Content</strong> cmdlet을 호출하면 Content 속성이 채워집니다. <strong>Get-Content</strong> 호출 시 Encoding 매개 변수를 바이트로 설정하고 ReadCount 매개 변수를 0으로 설정합니다. 자세한 내용은 이 항목의 예제 섹션을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>FileName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>가져올 오디오 파일의 파일 이름입니다. 예를 들어 C:\Media\Welcome.wav 파일의 파일 이름은 Welcome.wav입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>오디오 파일을 가져올 서비스의 ID입니다. 응답 그룹 응용 프로그램을 호스트하는 서비스와 같아야 합니다(예: -Identity &quot;service:ApplicationServer:atl-cs-001.litwareinc.com&quot;).</p></td>
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

없음. **Import-CsRgsAudioFile**은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Rgs.Management.WritableSettings.AudioFile 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsRgsWorkflow](new-csrgsworkflow.md)  
[Set-CsRgsWorkflow](set-csrgsworkflow.md)

