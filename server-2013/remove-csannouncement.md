---
title: Remove-CsAnnouncement
TOCTitle: Remove-CsAnnouncement
ms:assetid: a3c62d15-1b0a-49d3-973f-abc06c730bb2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412766(v=OCS.15)
ms:contentKeyID: 49304596
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsAnnouncement

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 Lync Server 알림을 제거합니다. 사용자가 유효하지만 할당되지 않은 전화 번호로 전화를 걸면 알림이 재생됩니다. 알림은 메시지(예: "이 번호는 일시적으로 사용할 수 없습니다.") 또는 통화 중 신호일 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsAnnouncement -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 "ApplicationServer:Redmond.litwareinc.com/1951f734-c80f-4fb2-965d-51807c792b90"인 알림을 제거합니다. ID는 고유해야 하므로 이 명령은 최대 하나의 알림만 제거합니다.

    Remove-CsAnnouncement -Identity "ApplicationServer:Redmond.litwareinc.com/1951f734-c80f-4fb2-965d-51807c792b90"

## 예제 2

예제 2에서는 ApplicationServer:Redmond.litwareinc.com 서비스에 적용된 모든 알림을 삭제합니다. 이 작업을 수행하기 위해 Identity 매개 변수와 함께 **Remove-CsAnnouncement** cmdlet을 호출합니다. 고유한 알림을 식별하는 추가 GUID 없이 매개 변수 값 "ApplicationServer:Redmond.litwareinc.com"을 지정하면 지정된 서비스에 대해 구성된 모든 알림이 제거됩니다.

    Remove-CsAnnouncement -Identity "ApplicationServer:Redmond.litwareinc.com"

## 자세한 정보

조직에서는 사용자 또는 전화에 할당되지 않았지만 전화를 걸 수 있는 유효한 전화 번호를 소유할 수 있습니다. 기본적으로 누군가 이러한 번호 중 하나로 전화를 걸면 통화 중 신호음이 울리고 오류가 발생하여 SIP 클라이언트로 통화가 반환될 수 있습니다. 관리자는 할당되지 않은 번호에 알림 설정을 적용하여 메시지를 재생하거나, 통화 중 신호를 반환하거나, 통화를 리디렉션할 수 있습니다. 이 cmdlet은 이러한 알림 설정을 하나 이상 제거합니다.

할당되지 않은 번호 범위와 연결된 알림을 제거하려고 하면 기본적으로 알림을 제거할지 묻는 메시지가 표시됩니다. 알림을 삭제하면 해당 범위의 AnnouncementName 속성이 Null로 표시되고 이러한 번호에 연결되었을 때 알림이 재생되지 않으며 통화 중 신호음만 울립니다. 그러나 AnnouncementId 속성 값(제거된 알림의 GUID)은 그대로 표시됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsAnnouncement** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsAnnouncement"}

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
<td><p>제거할 알림의 고유 식별자입니다. 다음 두 가지 방법 중 하나를 사용하여 Identity 매개 변수 값을 지정할 수 있습니다.</p>
<p>- 제거할 알림에 대한 응용 프로그램 서비스의 ID를 입력합니다. 지정된 서비스 ID로 구성된 모든 알림이 제거됩니다 (예: ApplicationServer:Redmond.litwareinc.com).</p>
<p>- 제거할 단일 알림의 전체 ID를 입력합니다. 이 값은 항상 &lt;serviceID&gt;/&lt;GUID&gt; 형식입니다. 여기서 serviceID는 알림 서비스를 실행하는 응용 프로그램 서버의 ID이고, GUID는 이 알림과 연결된 GUID(Globally Unique Identifier)입니다 (예: ApplicationServer:Redmond.litwareinc.com/bef5fa3b-3c97-4af0-abe7-611deee7616c).</p>
<p></p></td>
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

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.AnnouncementServiceSettings.Announcement 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[New-CsAnnouncement](new-csannouncement.md)  
[Set-CsAnnouncement](set-csannouncement.md)  
[Get-CsAnnouncement](get-csannouncement.md)

