---
title: Set-CsAnnouncement
TOCTitle: Set-CsAnnouncement
ms:assetid: 286cb990-844e-4b87-bdaf-4a75456d8c60
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425752(v=OCS.15)
ms:contentKeyID: 49303120
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsAnnouncement

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 Lync Server 알림의 속성 값을 수정합니다. 알림은 사용자가 올바르지만 할당되지 않은 전화 번호로 전화를 걸 때 재생됩니다. 알림은 메시지(예: "이 번호는 일시적으로 사용할 수 없습니다.") 또는 통화 중 신호일 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsAnnouncement [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsAnnouncement [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AudioFilePrompt <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Language <String>] [-Name <String>] [-TargetUri <String>] [-TextToSpeechPrompt <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Help Desk Announcement에 새 오디오 파일을 할당합니다. 이 작업을 수행하기 위해 이 명령은 먼저 매개 변수 없이 **Get-CsAnnouncement** cmdlet을 사용하여 현재 사용할 수 있는 모든 알림 컬렉션을 반환합니다. 그런 다음 이 컬렉션은 Name이 "Help Desk Announcement"와 같은(-eq) 알림을 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이 알림은 AudioFilePrompt 속성 값을 helpdesk.wav로 설정하는 **Set-CsAnnouncement** cmdlet에 파이프됩니다.

이 알림에 이미 사용자에게 할당된 TextToSpeechPrompt 값이 있는 경우 이 명령은 TextToSpeechPrompt 값이 무시된다는 경고를 생성합니다.

    Get-CsAnnouncement | Where-Object {$_.Name -eq "Help Desk Announcement"} | Set-CsAnnouncement -AudioFilePrompt "helpdesk.wav"

## 예제 2

예제 2에서는 Help Desk Announcement 알림의 TextToSpeechPrompt 속성이 null 값으로 설정됩니다. 이렇게 하면 속성 값이 효과적으로 지워집니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsAnnouncement** cmdlet을 사용하여 현재 사용할 수 있는 모든 알림의 컬렉션을 반환합니다. 이 컬렉션은 Name이 "Help Desk Announcement"와 같은(-eq) 알림을 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이 알림은 TextToSpeechPrompt 속성을 null 값($Null)으로 설정하는 **Set-CsAnnouncement** cmdlet에 파이프됩니다.

    Get-CsAnnouncement | Where-Object {$_.Name -eq "Help Desk Announcement"} | Set-CsAnnouncement -TextToSpeechPrompt $Null

## 예제 3

이 예제는 이름이 Help Desk Announcement인 알림의 TargetUri를 업데이트합니다. 먼저 **Get-CsAnnouncement** cmdlet을 사용하여 현재 사용할 수 있는 모든 알림의 컬렉션을 반환합니다. 이 컬렉션은 Name이 "Help Desk Announcement"와 같은(-eq) 알림을 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이 알림은 TargetUri 속성을 음성 사서함 위치(sip:kmyer@litwareinc.com;opaque=app:voicemail)로 설정하는 **Set-CsAnnouncement** cmdlet에 파이프됩니다.

    Get-CsAnnouncement | Where-Object {$_.Name -eq "Help Desk Announcement"} | Set-CsAnnouncement -TargetUri "sip:kmyer@litwareinc.com;opaque=app:voicemail"

## 자세한 정보

조직에서는 사용자 또는 전화에 할당되지 않았지만 전화를 걸 수 있는 유효한 전화 번호를 소유할 수 있습니다. 기본적으로 누군가 이러한 번호 중 하나로 전화를 걸면 통화 중 신호음이 울리고 오류가 발생하여 SIP 클라이언트로 통화가 반환될 수 있습니다. 관리자는 할당되지 않은 번호에 알림 설정을 적용하여 메시지를 재생하거나, 통화 중 신호를 반환하거나, 통화를 리디렉션할 수 있습니다. 이 cmdlet은 이러한 알림 설정을 수정합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsAnnouncement** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsAnnouncement"}

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
<td><p>문자열</p></td>
<td><p>알림을 위해 재생할 오디오 파일 이름입니다. 오디오 파일은 파일 저장소에 저장됩니다. 오디오 파일을 파일 저장소에 저장하려면 <strong>Import-CsAnnouncementFile</strong> cmdlet을 사용합니다.</p>
<p>올바른 파일 형식: WAV 및 WMA</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>XdsIdentity</p></td>
<td><p>알림에 대한 고유한 식별자입니다. 이 값은 항상 &lt;serviceID&gt;/&lt;GUID&gt; 형식입니다. 여기서 serviceID는 알림 서비스를 실행 중인 응용 프로그램 서버의 ID이며 GUID는 이러한 알림 설정과 연결된 GUID(Globally Unique Identifier)입니다(예: ApplicationServer:redmond.litwareinc.com/bef5fa3b-3c97-4af0-abe7-611deee7616c).</p>
<p>GUID는 복잡해서 명령줄에 잘못 입력할 가능성이 있으므로 <strong>Get-CsAnnouncement</strong> cmdlet을 사용하여 알림을 검색하고 <strong>Set-CsAnnouncement</strong> cmdlet에 파이프하여 수정하는 것이 좋습니다. 자세한 내용은 예제 섹션을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>알림</p></td>
<td><p>변경할 Announcement 개체에 대한 참조입니다. 이 개체는 <strong>Get-CsAnnouncement</strong> cmdlet을 호출하여 검색할 수 있는 Microsoft.Rtc.Management.WritableConfig.Settings.AnnouncementServiceSettings.Announcement 유형이어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Language</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>TTS 프롬프트를 재생할 때 사용할 언어입니다. TextToSpeechPrompt에 값을 입력한 경우 이 매개 변수가 필요합니다.</p>
<p>값은 사용할 언어 및 로캘을 나타내는 문자열로 입력됩니다. 유효한 값 목록은 ca-ES(카탈로니아어, 스페인), da-DK(덴마크어, 덴마크), de-DE(독일어, 독일), en-AU(영어, 오스트레일리아), en-CA(영어, 캐나다), en-GB(영어, 영국), en-IN(영어, 인도), en-US(영어, 미국), es-ES(스페인어, 스페인), es-MX(스페인어, 멕시코), fi-FI(핀란드어, 핀란드), fr-CA(프랑스어, 캐나다), fr-FR(프랑스어, 프랑스), it-IT(이탈리아어, 이탈리아), ja-JP(일본어, 일본), ko-KR(한국어, 대한민국), nb-NO(노르웨이어, 복말, 노르웨이), nl-NL(네덜란드어, 네덜란드), pl-PL(폴란드어, 폴란드), pt-BR(포르투갈어, 브라질), pt-PT(포르투갈어, 포르투갈), ru-RU(러시아어,러시아), sv-SE(스웨덴어, 스웨덴), zh-CN(중국어, 중국), zh-HK(중국어, 중국), zh-TW(중국어, 대만)이며 괄호 안에 언어와 로캘이 포함되어 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>알림의 이름을 변경하려면 이 매개 변수에 값을 입력합니다. 이름은 서비스 내에서 고유해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetUri</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>알림이 재생된 후 발신자에게 전송되는 URI입니다. 이 값은 SIP 주소여야 하여 sip: 뒤에 SIP 주소가 오는 형식이어야 합니다. sip:kmyer@litwareinc.com을 예로 들 수 있습니다. SIP 주소는 전화 번호 또는 음성 메일일 수 있습니다(예: 전화 번호의 경우 sip:+14255551212@litwareinc.com;user=phone, 음성 메일의 경우 sip:kmyer@litwareinc.com;opaque=app:voicemail).</p></td>
</tr>
<tr class="odd">
<td><p><em>TextToSpeechPrompt</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>TTS(텍스트 음성 변환) 프롬프트입니다. 오디오로 변환되고 알림으로 재생되는 문자열입니다.</p>
<p>단일 알림에 대해 AudioFilePrompt와 TextToSpeechPrompt를 둘 다 지정한 경우에는 오디오 파일이 우선 적용되고 TTS 프롬프트가 무시된다는 경고가 표시됩니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Settings.AnnouncementServiceSettings.Announcement 개체입니다. 알림 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsAnnouncement** cmdlet은 개체나 값을 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.AnnouncementServiceSettings.Announcement 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[New-CsAnnouncement](new-csannouncement.md)  
[Remove-CsAnnouncement](remove-csannouncement.md)  
[Get-CsAnnouncement](get-csannouncement.md)  
[Import-CsAnnouncementFile](import-csannouncementfile.md)

