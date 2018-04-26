---
title: Set-CsCallParkServiceMusicOnHoldFile
TOCTitle: Set-CsCallParkServiceMusicOnHoldFile
ms:assetid: af5e7573-4bfd-47b1-a92b-83b06a537158
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412836(v=OCS.15)
ms:contentKeyID: 49304731
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsCallParkServiceMusicOnHoldFile

 

_**마지막으로 수정된 항목:** 2015-03-09_

대기된 통화에서 발신자가 대기하는 동안 재생되는 오디오 파일을 변경합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsCallParkServiceMusicOnHoldFile -Content <Byte[]> -Service <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 SoothingMusic.wma 파일을 통화 대기 중인 전화 건 사람에게 재생할 오디오 파일로 설정합니다. 이 예제의 첫째 줄은 **Get-Content** cmdlet에 대한 호출입니다. 이 cmdlet은 파일의 내용을 읽고 할당하는데, 이 경우에는 $a 변수에 할당합니다. **Get-Content** cmdlet이 전체 파일을 한 줄씩 읽는 것(오디오 파일에는 적용되지 않음)이 아니라 한 번에 읽도록 ReadCount 매개 변수에 0 값을 전달합니다. Encoding 매개 변수는 byte로 설정됩니다. 따라서 **Get-Content** cmdlet은 변수 $a에 읽어들일 내용이 .wma 형식의 오디오 파일이 아니라 바이트 배열이라는 것을 알게 됩니다.

이 예제의 둘째 줄에서는 실제로 오디오 파일을 할당합니다. **Set-CsCallParkServiceMusicOnHoldFile** cmdlet을 호출하고 통화 대기 서비스를 실행하는 서비스 ID를 지정합니다. 그런 다음, 변수 $a에 읽어들인 오디오 파일 내용을 Content 매개 변수에 전달합니다. 이러한 내용은 바이트 형식이어야 합니다.

    $a = Get-Content -ReadCount 0 -Encoding byte "C:\MoHFiles\soothingmusic.wma"
    Set-CsCallParkServiceMusicOnHoldFile -Service ApplicationServer:pool0.litwareinc.com -Content $a

## 자세한 정보

통화 대기는 사용자가 수신 전화 통화를 "대기"시킬 수 있는 서비스입니다. 통화를 대기시키면 통화가 지정된 범위의 번호로 전송되고 즉시 대기 상태가 됩니다. 통화 대기 서비스의 구성 설정에 따라 통화를 대기하는 동안 대기 음악이 발신자에게 재생될 수 있습니다. 이 cmdlet을 사용하여 대기 중인 전화 건 사람에게 재생되는 오디오 파일(대기 음악)을 변경합니다.

대기 음악은 통화 대기 서비스의 EnableMusicOnHold 속성이 True로 설정된 경우에만 재생됩니다. **Get-CsCpsConfiguration** cmdlet을 호출하여 이 속성을 확인할 수 있습니다. **New-CsCpsConfiguration** cmdlet을 사용하여 통화 대기 구성을 만들 때나 **Set-CsCpsConfiguration** cmdlet을 호출하여 통화 대기 구성이 종료된 후 이 속성을 설정할 수 있습니다. 기본적으로 이 속성은 True입니다.

Lync Server에는 기본 통화 대기 서비스 대기 음악 파일이 제공됩니다. 오디오 파일을 할당하지 않은 경우 기본 파일이 사용됩니다.

오디오 파일의 형식은 Windows Media 오디오 9, 44kHz, 16비트, 모노, CBR 또는 32kbps여야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsCallParkServiceMusicOnHoldFile** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsCallParkServiceMusicOnHoldFile"}

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
<td><p>바이트 형식으로 되어 있는 오디오 파일의 내용입니다.</p>
<p><strong>Get-Content</strong> cmdlet을 사용하여 바이트 형식으로 되어 있는 오디오 파일의 내용을 검색합니다. 자세한 내용은 이 항목의 예제 섹션을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>Service</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>통화 대기 서비스가 상주하는 서비스의 ID(예: ApplicationServer:pool0.litwareinc.com)입니다.</p></td>
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
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

바이트\[\]. 대기 음악 파일이 포함된 바이트 배열의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[New-CsCpsConfiguration](new-cscpsconfiguration.md)  
[Remove-CsCpsConfiguration](remove-cscpsconfiguration.md)  
[Set-CsCpsConfiguration](set-cscpsconfiguration.md)  
[Get-CsCpsConfiguration](get-cscpsconfiguration.md)

