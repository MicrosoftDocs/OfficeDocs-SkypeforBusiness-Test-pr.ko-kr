---
title: New-CsAnnouncement
TOCTitle: New-CsAnnouncement
ms:assetid: 6e3699c6-cd2b-4842-99bc-3cf2578fbd65
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398522(v=OCS.15)
ms:contentKeyID: 49303970
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsAnnouncement

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 Lync Server 알림을 생성합니다. 사용자가 유효하지만 할당되지 않은 전화 번호로 전화를 걸면 알림이 재생됩니다. 알림은 메시지(예: "이 번호는 일시적으로 사용할 수 없습니다.") 또는 통화 중 신호일 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsAnnouncement -Parent <String> <COMMON PARAMETERS>

    New-CsAnnouncement -Identity <XdsIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: -Name <String> [-AudioFilePrompt <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Language <String>] [-TargetUri <String>] [-TextToSpeechPrompt <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 TTS 프롬프트를 영어(미국)로 재생할 새 알림을 만드는 방법을 보여 줍니다. 첫 번째 매개 변수는 Identity로 지정합니다. Identity는 서비스 범위에 있어야 하고 그 뒤에 응용 프로그램 서버의 서비스 ID가 와야 합니다(ApplicationServer:redmond.litwareinc.com). 다음으로 알림에 Name을 제공합니다(이 경우 Help Desk Announcement). TTS 프롬프트를 이 알림에 할당하기 위해 TextToSpeechPrompt 매개 변수를 사용하고 그 뒤에 알림 텍스트가 포함된 문자열을 입력합니다. 알림에 TTS 프롬프트를 사용할 경우 언어를 지정해야 합니다. 여기서는 Language 매개 변수, 미국 영어를 나타내는 문자열(en-US)을 차례로 포함합니다.

알림 ID는 알림이 저장되는 서비스 및 36자 GUID(Globally Unique Identifier)의 두 부분으로 구성됩니다. 사용자가 새 알림을 생성하고 GUID가 자동으로 생성 및 적용된 후 전체 ID가 표시됩니다. 이 ID는 service:ApplicationServer:redmond.litwareinc.com/1951f734-c80f-4fb2-965d-51807c792b90과 유사합니다.

    New-CsAnnouncement -Identity ApplicationServer:redmond.litwareinc.com -Name "Help Desk Announcement" -TextToSpeechPrompt "Welcome to the Help Desk." -Language "en-US"

## 예제 2

예제 2는 필수 매개 변수 Identity 및 Name 입력으로 시작된다는 점에서 예제 1과 비슷합니다. 그러나 이 예제에서는 TTS 프롬프트 대신 오디오 파일을 재생할 알림이 필요합니다. 이를 위해 AudioFilePrompt 매개 변수를 포함하고 오디오 파일 이름(WelcomeMessage.wav)이 포함된 문자열을 전달합니다. 이 알림을 재생하려면 이 파일이 파일 저장소에 있어야 합니다. **Import-CsAnnouncementFile** cmdlet을 호출하여 오디오 파일을 파일 저장소에 추가할 수 있습니다.

    New-CsAnnouncement -Identity ApplicationServer:redmond.litwareinc.com -Name "Welcome Announcement" -AudioFilePrompt "WelcomeMessage.wav"

## 예제 3

예제 2와 같이 이 예제에서는 번호에 도달할 때 오디오 파일을 재생하는 알림을 생성합니다. 그러나 이 예제에서는 Identity, Name 및 AudioFilePrompt 매개 변수 이외에 TargetUri 매개 변수도 지정합니다. 알림이 재생된 후 발신자가 전달될 사용자 또는 전화의 SIP URI를 이 매개 변수에 전달합니다.

    New-CsAnnouncement -Identity ApplicationServer:redmond.litwareinc.com -Name "Forward Announcement" -AudioFilePrompt "WelcomeMessage.wav" -TargetUri sip:kmyer@litwareinc.com

## 예제 4

사용자의 SIP 주소를 기반으로 통화를 전달하지 않고 통화가 전화 번호로 전달된다는 점을 제외하면 예제 4는 예제 3과 동일합니다.

    New-CsAnnouncement -Identity ApplicationServer:redmond.litwareinc.com -Name "Forward Announcement" -AudioFilePrompt "WelcomeMessage.wav" -TargetUri "sip:+14255551212@litwareinc.com;user=phone"

## 예제 5

이 예제에서는 프롬프트나 대상 URI를 지정하지 않고 Identity 및 Name만 포함합니다. 이는 이 알림과 연결된 지정되지 않은 번호에 통화가 연결된 경우 발신자가 통화 중 신호음을 듣게 될 것임을 의미합니다.

    New-CsAnnouncement -Identity ApplicationServer:redmond.litwareinc.com -Name "Busy"

## 자세한 정보

조직에서는 사용자 또는 전화에 할당되지 않았지만 전화를 걸 수 있는 유효한 전화 번호를 소유할 수 있습니다. 기본적으로 누군가 이러한 번호 중 하나로 전화를 걸면 통화 중 신호음이 울리고 오류가 발생하여 SIP 클라이언트로 통화가 반환될 수 있습니다. 관리자는 할당되지 않은 번호에 알림 설정을 적용하여 메시지를 재생하거나, 통화 중 신호를 반환하거나, 통화를 리디렉션할 수 있습니다. 이 cmdlet은 이러한 알림 설정을 생성합니다.

**New-CsUnassignedNumber** 또는 **Set-CsUnassignedNumber** cmdlet을 호출하여 지정되지 않은 번호에 알림을 할당할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsAnnouncement** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsAnnouncement"}

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
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>알림에 대한 고유한 식별자입니다. 이 값의 경우 응답 그룹 응용 프로그램을 실행하는 응용 프로그램 서버의 ID를 입력해야 합니다(예: ApplicationServer:redmond.litwareinc.com).</p>
<p>단일 서비스에 두 개 이상의 알림이 할당될 수 있습니다. 따라서 Identity를 고유한 값으로 만들기 위해 GUID(Globally Unique Identifier)가 자동으로 생성되고 사용자가 알림을 생성할 때 Identity에 할당됩니다. 새 알림에는 service:&lt;서비스 ID&gt;/&lt;GUID&gt; 형식의 ID가 포함됩니다(예: service: ApplicationServer:redmond.litwareinc.com/bef5fa3b-3c97-4af0-abe7-611deee7616c). 이 cmdlet을 호출할 때는 GUID를 제공할 필요가 없습니다. 대신 서비스 ID를 제공하면 GUID가 자동 생성되어 Identity에 추가됩니다.</p>
<p>GUID를 제공할 필요가 없지만 제공할 수도 있습니다. 지정되지 않은 번호 범위에 알림이 할당된 다음 삭제된 경우 그렇게 할 수 있습니다. 일치하는 ID(GUID 포함)로 새 알림을 생성할 수 있는데, 이 경우 지정되지 않은 번호 범위를 업데이트할 필요가 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>알림에 대한 설명 이름입니다. 이 이름은 서비스 내에서 고유해야 합니다. <strong>New-CsUnassignedNumber</strong> cmdlet 또는 <strong>Set-CsUnassignedNumber</strong> cmdlet에 대한 호출에서 이 이름을 사용하여 지정되지 않은 번호 범위와 연결된 알림을 지정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Parent</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>Identity가 서비스 ID와 GUID를 수락한다는 점을 제외하고 이 매개 변수는 Identity와 동일하지만, Parent는 서비스 ID만 수락하고 GUID는 자동으로 생성됩니다. Identity와 Parent를 모두 지정할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioFilePrompt</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>알림을 위해 재생할 오디오 파일 이름입니다. 오디오 파일은 파일 저장소에 저장됩니다. 오디오 파일을 파일 저장소에 저장하려면 <strong>Import-CsAnnouncementFile</strong> cmdlet을 사용합니다.</p>
<p>올바른 파일 형식: WAV 및 WMA</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Language</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>TTS(텍스트 음성 변환) 프롬프트를 재생하는 데 사용되는 언어입니다. TextToSpeechPrompt에 값이 입력된 경우 이 매개 변수가 필요합니다.</p>
<p>값은 사용할 언어 및 로캘을 나타내는 문자열로 입력됩니다. 유효한 값 목록은 ca-ES(카탈로니아어, 스페인), da-DK(덴마크어, 덴마크), de-DE(독일어, 독일), en-AU(영어, 오스트레일리아), en-CA(영어, 캐나다), en-GB(영어, 영국), en-IN(영어, 인도), en-US(영어, 미국), es-ES(스페인어, 스페인), es-MX(스페인어, 멕시코), fi-FI(핀란드어, 핀란드), fr-CA(프랑스어, 캐나다), fr-FR(프랑스어, 프랑스), it-IT(이탈리아어, 이탈리아), ja-JP(일본어, 일본), ko-KR(한국어, 대한민국), nb-NO(노르웨이어, 복말, 노르웨이), nl-NL(네덜란드어, 네덜란드), pl-PL(폴란드어, 폴란드), pt-BR(포르투갈어, 브라질), pt-PT(포르투갈어, 포르투갈), ru-RU(러시아어,러시아), sv-SE(스웨덴어, 스웨덴), zh-CN(중국어, 중국), zh-HK(중국어, 중국), zh-TW(중국어, 대만)이며 괄호 안에 언어와 로캘이 포함되어 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TargetUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>알림이 재생된 후 발신자를 전송할 대상 URI(Uniform Resource Identifier)입니다. 이 값은 SIP 주소로서 sip: 및 그 뒤에 SIP 주소가 오는 형식으로 입력해야 합니다. sip:kmyer@litwareinc.com을 예로 들 수 있습니다. SIP 주소는 전화 번호 또는 음성 메일일 수 있습니다(예: 전화 번호의 경우 sip:+14255551212@litwareinc.com;user=phone, 음성 메일의 경우 sip:kmyer@litwareinc.com;opaque=app:voicemail).</p></td>
</tr>
<tr class="even">
<td><p><em>TextToSpeechPrompt</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>TTS(텍스트 음성 변환) 프롬프트입니다. 오디오로 변환되고 알림으로 재생되는 문자열입니다.</p>
<p>단일 알림에 대해 AudioFilePrompt와 TextToSpeechPrompt를 둘 다 지정한 경우에는 오디오 파일이 우선 적용되고 TTS 프롬프트가 무시된다는 경고가 표시됩니다.</p>
<p></p></td>
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

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.AnnouncementServiceSettings.Announcement 유형의 개체를 생성합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsAnnouncement](remove-csannouncement.md)  
[Set-CsAnnouncement](set-csannouncement.md)  
[Get-CsAnnouncement](get-csannouncement.md)  
[Import-CsAnnouncementFile](import-csannouncementfile.md)  
[New-CsUnassignedNumber](new-csunassignednumber.md)  
[Set-CsUnassignedNumber](set-csunassignednumber.md)

