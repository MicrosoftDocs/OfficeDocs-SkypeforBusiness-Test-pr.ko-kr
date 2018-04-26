---
title: Import-CsAnnouncementFile
TOCTitle: Import-CsAnnouncementFile
ms:assetid: 66da2361-e325-4085-8b6f-47a8423edaab
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398472(v=OCS.15)
ms:contentKeyID: 49303874
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Import-CsAnnouncementFile

 

_**마지막으로 수정된 항목:** 2015-03-09_

알림 파일을 알림 서비스 오디오 라이브러리로 가져옵니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Import-CSAnnouncementFile -Content <Byte[]> -FileName <String> -Parent <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이러한 명령은 오디오 파일을 알림 서비스 파일 저장소로 가져옵니다. 오디오 파일을 바이트 배열로서 가져와야 하므로 먼저 **Get-Content** cmdlet을 호출하여 오디오 파일을 개별 바이트 배열로 검색해야 합니다. **Get-Content**는 알림에 사용할 파일의 이름(경로 포함)을 전달하는 Windows PowerShell 기본 제공 cmdlet입니다. 이제 전체 파일을 한 번에 읽기 위해 0 값을 ReadCount 매개 변수에 전달합니다. 그런 다음 Byte 값을 Encoding 매개 변수에 전달하여 파일 내용을 바이트 배열로 가져오도록 **Get-Content**에 지시합니다. 이 배열을 변수 $a에 할당합니다.

두 번째 줄에서는 **Import-CsAnnouncementFile** cmdlet을 호출하여 실제로 파일을 가져옵니다. 서비스 ID ApplicationServer:redmond.litwareinc.com을 Parent 매개 변수에 전달한 다음 이름(WelcomeMessage.wav)을 FileName 매개 변수에 전달합니다. Windows 운영 체제에 유효한 파일 이름이면 어떤 것이든 사용할 수 있지만 .wav 또는 .wma 확장명으로 끝나야 합니다. 끝으로, 변수 $a를 Content 매개 변수 값으로 전달하여 바이트 배열을 읽습니다.

    $a = Get-Content ".\GreetingFile.wav" -ReadCount 0 -Encoding Byte
    Import-CsAnnouncementFile -Parent ApplicationServer:redmond.litwareinc.com -FileName "WelcomeMessage.wav" -Content $a

## 예제 2

예제 2는 **Get-Content** 명령을 직접 호출하여 변수에 할당하지 않고 Content 매개 변수에 대한 값으로 괄호 안에 포함한 것을 제외하고 예제 1과 동일합니다.

    Import-CsAnnouncementFile -Parent ApplicationServer:redmond.litwareinc.com -FileName "WelcomeMessage.wav" -Content (Get-Content ".\GreetingFile.wav" -ReadCount 0 -Encoding Byte)

## 예제 3

예제 3은 예제 1의 또 다른 변형입니다. 이 예제에서는 Content 매개 변수를 사용하는 대신 먼저 **Get-Content** cmdlet을 호출한 다음 결과를 **Import-CsAnnouncementFile**에 전달한다는 점이 다릅니다. 이 방법은 원격 세션에서 알림 파일을 가져오는 데 가장 적합한 방법입니다.

    Get-Content ".\GreetingFile.wav" -ReadCount 0 -Encoding Byte | Import-CsAnnouncementFile -Parent ApplicationServer:redmond.litwareinc.com -FileName "WelcomeMessage.wav"

## 자세한 정보

이 cmdlet은 오디오 파일을 바이트 배열로 알림 서비스 오디오 라이브러리로 가져옵니다. 이렇게 하면 지정되지 않은 번호에 대한 알림으로 파일을 재생할 수 있습니다.

이 cmdlet을 실행하면 오디오 파일을 라이브러리로 가져옵니다. 파일을 가져온 후 **New-CsAnnouncement** cmdlet 또는 **Set-CsAnnouncement** cmdlet을 호출하고, 파일 이름 및 연결된 서비스를 매개 변수로 전달하면 파일을 알림에서 사용할 수 있습니다. 이때 **New-CsUnassignedNumber** 또는 **Set-CsUnassignedNumber** cmdlet을 호출하여 알림을 특정 번호 범위에 할당할 수 있습니다.

가져온 파일은 WAV 또는 WMA 파일이어야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Import-CsAnnouncementFile** cmdlet을 로컬로 실행할 수 있습니다. 그러나 대상 컴퓨터의 파일 저장소에 대한 쓰기 권한이 있는 사용자는 누구나 cmdlet을 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Import-CsAnnouncementFile"}

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
<td><p>바이트 배열로서 오디오 파일의 내용입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>FileName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>파일을 파일 저장소에 저장할 때 사용할 이름입니다. <strong>New-CsAnnouncement</strong> 또는 <strong>Set-CsAnnouncement</strong> cmdlet을 호출할 때 AudioFilePrompt 매개 변수에 이 이름을 사용하여 파일을 알림에 할당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Parent</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>연결된 알림 서비스를 실행하는 응용 프로그램 서버의 서비스 ID입니다.</p></td>
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
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
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

바이트\[\]. 오디오 파일의 바이트 배열을 허용합니다. 바이트 배열은 단일 레코드로 파이프되어야 합니다. 예제 3을 참조하십시오.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다.

