---
title: Get-CsAnnouncement
TOCTitle: Get-CsAnnouncement
ms:assetid: d692b377-8df2-4668-b9d3-06458dd4d96d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398937(v=OCS.15)
ms:contentKeyID: 49305178
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAnnouncement

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 Lync Server 알림에 대한 정보를 반환합니다. 사용자가 유효하지만 할당되지 않은 전화 번호로 전화를 걸면 알림이 재생됩니다. 알림은 메시지(예: "이 번호는 일시적으로 사용할 수 없습니다.") 또는 통화 중 신호일 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsAnnouncement [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsAnnouncement [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 사용하도록 구성된 모든 알림을 반환합니다. 이 작업은 매개 변수 없이 **Get-CsAnnouncement** cmdlet을 호출하여 수행합니다.

    Get-CsAnnouncement

## 예제 2

예제 2에 표시된 명령은 ID가 ApplicationServer:redmond.litwareinc.com/1951f734-c80f-4fb2-965d-51807c792b90인 단일 알림을 반환합니다. 보다 쉬운 방법으로 특정 알림을 검색할 수 있는 다른 방법은 예제 5에 나와 있습니다.

    Get-CsAnnouncement -Identity "ApplicationServer:redmond.litwareinc.com/1951f734-c80f-4fb2-965d-51807c792b90" 

## 예제 3

예제 3에 표시된 명령은 ApplicationServer:redmond.litwareinc.com 서비스에서 사용하도록 구성된 모든 알림에 대한 정보를 반환합니다.

    Get-CsAnnouncement -Identity "ApplicationServer:redmond.litwareinc.com"

## 예제 4

예제 4에서는 모든 도메인에서 Redmond 사이트에서 사용하도록 구성된 모든 알림에 대해 정보를 반환합니다. 이 작업은 Filter 매개 변수와 필터 값 "\*ApplicationServer:Redmond\*"를 포함하여 수행합니다. 이 필터 값은 반환되는 데이터를 ID가 문자열 값 "ApplicationServer:Redmond"를 포함하는 알림으로 제한합니다. 정의에 따라 이러한 알림이 Redmond 사이트에서 사용하도록 구성된 알림입니다.

    Get-CsAnnouncement -Filter "*ApplicationServer:Redmond*"

## 예제 5

예제 5에서는 특정 알림 또는 알림 집합(여기서는 Welcome Announcement)을 반환하는 다른 방법을 보여 줍니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsAnnouncement** cmdlet을 호출하여 조직에서 사용 중인 모든 알림 컬렉션을 반환합니다. 이 컬렉션은 Name이 "Welcome Announcement"와 같은(-eq) 알림을 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsAnnouncement | Where-Object {$_.Name -eq "Welcome Announcement"}

## 예제 6

예제 6은 예제 5와 유사하지만 단일 알림을 반환하는 또 다른 방법을 보여 줍니다. 이 예제에서도 마찬가지로 **Get-CsAnnouncement** cmdlet을 호출하지만 이번에는 ID를 ApplicationServer:redmond.litwareinc.com으로 지정합니다. 그러면 해당 서비스와 연결된 모든 알림 컬렉션이 반환됩니다. 예제 5와 마찬가지로 이 컬렉션은 Name이 "Welcome Announcement"와 같은(-eq) 알림을 선택하는 **Where-Object** cmdlet에 파이프됩니다. 알림 이름은 응용 프로그램 서비스 내에서 고유해야 하므로 이 명령은 단일 항목만 반환합니다.

    Get-CsAnnouncement -Identity "ApplicationServer:redmond.litwareinc.com" | Where-Object {$_.Name -eq "Welcome Announcement"}

## 예제 7

이 예제는 모든 알림을 검색한 다음 알림 컬렉션을 **Where-Object** cmdlet에 파이프한다는 점에서 예제 5와 유사합니다. 그러나 예제 5에서는 일치하는 이름을 찾는 –eq 연산자를 사용했지만 이 예제에서는 –like 연산자와 와일드카드 값을 사용하여 문자열 Welcome으로 시작하는 모든 알림을 찾습니다.

    Get-CsAnnouncement | Where-Object {$_.Name -like "Welcome*"}

## 예제 8

예제 8에서는 기본 알림 또는 오디오 파일에 대한 대안으로 TTS(텍스트 음성 변환) 프롬프트를 사용하지만 기본 언어로 영어(미국)를 사용하지 않는 모든 알림에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsAnnouncement** cmdlet을 호출하여 현재 구성된 모든 알림 컬렉션을 반환합니다. 이 컬렉션은 TextToSpeechPrompt 속성이 비어 있지 않고($Null과 같지 않고) Language 속성이 en-US와 같지 않은(-ne) 모든 알림을 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsAnnouncement | Where-Object {($_.TextToSpeechPrompt -ne $Null) -and ($_.Language -ne "en-US")}

## 자세한 정보

조직에서는 사용자 또는 전화에 할당되지 않았지만 전화를 걸 수 있는 유효한 전화 번호를 소유할 수 있습니다. 기본적으로 누군가 이러한 번호 중 하나로 전화를 걸면 통화 중 신호음이 울리고 오류가 발생하여 SIP 클라이언트로 통화가 반환될 수 있습니다. 관리자는 할당되지 않은 번호에 알림 설정을 적용하여 메시지를 재생하거나, 통화 중 신호를 반환하거나, 통화를 리디렉션할 수 있습니다. 이 cmdlet은 이러한 알림 설정을 하나 이상 검색합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsAnnouncement** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsAnnouncement"}

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수를 사용하면 조직에 구성된 모든 알림의 ID에 대해 와일드카드 검색을 수행할 수 있습니다. 즉, 와일드카드 문자(*)를 사용하여 ID의 일부를 필터링할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 알림의 식별자입니다. 이 매개 변수와 Filter 매개 변수를 생략하면 조직에 구성된 알림의 모든 인스턴스가 표시됩니다. 다음 두 가지 방법 중 하나를 사용하여 Identity 매개 변수 값을 지정할 수 있습니다.</p>
<p>- 검색할 알림에 대한 응용 프로그램 서비스의 ID를 입력합니다. 지정된 서비스 ID로 구성된 모든 알림이 검색됩니다 (예: ApplicationServer:Redmond.litwareinc.com).</p>
<p>- 검색할 단일 알림의 전체 ID를 입력합니다. 이 값은 항상 &lt;serviceID&gt;/&lt;GUID&gt; 형식입니다. 여기서 serviceID는 알림 서비스를 실행하는 응용 프로그램 서버의 ID이고, GUID는 이 알림과 연결된 GUID(Globally Unique Identifier)입니다 (예: ApplicationServer:Redmond.litwareinc.com/bef5fa3b-3c97-4af0-abe7-611deee7616c).</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 알림 정보를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.AnnouncementServiceSettings.Announcement 개체의 인스턴스를 하나 이상 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsAnnouncement](new-csannouncement.md)  
[Remove-CsAnnouncement](remove-csannouncement.md)  
[Set-CsAnnouncement](set-csannouncement.md)  
[Import-CsAnnouncementFile](import-csannouncementfile.md)

