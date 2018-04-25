---
title: Set-CsUnassignedNumber
TOCTitle: Set-CsUnassignedNumber
ms:assetid: e7f52423-58d1-410a-9071-731bde45d3d4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399033(v=OCS.15)
ms:contentKeyID: 49305374
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsUnassignedNumber

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존의 할당되지 않은 번호 범위 및 이러한 번호에 적용되는 경로 지정 규칙을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsUnassignedNumber [-Identity <XdsGlobalRelativeIdentity>] [-Instance <PSObject>] [-NumberRangeEnd <String>] [-NumberRangeStart <String>] <COMMON PARAMETERS>

    Set-CsUnassignedNumber -ExUmAutoAttendantPhoneNumber <String> [-Identity <XdsGlobalRelativeIdentity>] [-Instance <PSObject>] [-NumberRangeEnd <String>] [-NumberRangeStart <String>] <COMMON PARAMETERS>

    Set-CsUnassignedNumber -AnnouncementName <String> -AnnouncementService <String> [-Identity <XdsGlobalRelativeIdentity>] [-Instance <PSObject>] [-NumberRangeEnd <String>] [-NumberRangeStart <String>] <COMMON PARAMETERS>

    Set-CsUnassignedNumber [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Priority <Int32>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 이름이 UNSet1인 할당되지 않은 번호 범위를 수정합니다. 먼저 Identity 매개 변수에 수정하려는 할당되지 않은 숫자 범위의 이름 UNSet1을 전달합니다. 그런 다음 NumberRangeStart(+14255551000) 및 NumberRangeEnd(+14255551900) 매개 변수를 사용하여 지정된 알림 또는 자동 전화 교환을 적용할 지정되지 않은 번호 범위를 정의합니다.

    Set-CsUnassignedNumber -Identity UNSet1 -NumberRangeStart "+14255551000" -NumberRangeEnd "+14255551900"

## 예제 2

이 예제에서는 이름에 문자열 "Welcome"이 포함된 알림을 사용하는 모든 할당되지 않은 번호 범위 설정의 알림을 수정합니다. 먼저 **Get-CsUnassignedNumber** cmdlet을 호출하여 모든 할당되지 않은 번호 설정을 검색합니다. 이 설정 컬렉션을 AnnouncementName 속성에 문자열 Welcome이 포함된(-match) 설정으로 컬렉션 범위를 좁히는 **Where-Object** cmdlet에 파이프합니다. 그런 다음 이러한 설정을 **Set-CsUnassignedNumber** cmdlet에 파이프합니다. 여기서 AnnouncementService 매개 변수를 사용하여 알림 서비스의 응용 프로그램 서버 ID(ApplicationServer:redmond.litwareinc.com)를 수정하고 AnnouncementName 매개 변수를 사용하여 새 알림 이름(Help Desk Announcement)을 지정합니다. 새 알림이 이름은 다르지만 서비스 ID가 같은 경우 이름과 함께 서비스 ID를 계속 지정해야 합니다.

    Get-CsUnassignedNumber | Where-Object {$_.AnnouncementName -match "Welcome"} | Set-CsUnassignedNumber -AnnouncementService ApplicationServer:redmond.litwareinc.com -AnnouncementName "Help Desk Announcement"

## 자세한 정보

할당되지 않은 번호란 조직에 할당되었지만 특정 사용자 또는 전화에 할당되지 않은 전화 번호입니다. 할당되지 않은 번호로 전화가 걸려올 때 적절한 대상으로 통화를 경로 지정하도록 Lync Server를 설정할 수 있습니다. 이 cmdlet은 이러한 경로 지정을 정의하는 설정을 수정합니다.

이 cmdlet을 사용하여 일부 설정을 수정하려면 시스템에 이미 알림이 정의되어 있거나 Exchange UM 자동 전화 교환이 설정되어 있어야 합니다. 알림이 정의되어 있는지 확인하려면 **Get-CsAnnouncement** cmdlet을 호출합니다. 새 알림을 만들려면 **New-CsAnnouncement** cmdlet을 호출합니다. 또한 Exchange UM 자동 전화 교환 설정을 확인하려면 **Get-CsExUmContact** cmdlet을 실행합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsUnassignedNumber** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsUnassignedNumber"}

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
<td><p><em>AnnouncementName</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>이 번호 범위로 걸려 온 전화를 처리하는 데 사용할 알림의 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AnnouncementService</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>알림 서버의 FQDN(정규화된 도메인 이름) 또는 서비스 ID입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExUmAutoAttendantPhoneNumber</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>이 범위의 전화를 경로 지정할 Exchange UM 자동 전화 교환 전화 번호입니다. 이 매개 변수에 값을 할당하려면 Exchange UM 자동 전화 교환 대화 상대가 이미 설정되어 있어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>변경 내용을 적용하기 전에 표시될 수 있는 확인 메시지를 숨깁니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Xds 글로벌 상대 ID</p></td>
<td><p>수정할 할당되지 않은 번호 범위의 고유 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>DisplayAnnouncementVacantNumberRange</p></td>
<td><p>할당되지 않은 번호 설정이 포함된 개체에 대한 참조입니다. 이 개체의 유형은 Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange여야 하며, <strong>Get-CsUnassignedNumber</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NumberRangeEnd</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>할당되지 않은 번호 범위의 마지막 번째 번호입니다. NumberRangeStart에 제공된 번호보다 크거나 같아야 합니다. 하나의 번호로 범위를 지정하려면 NumberRangeStart와 NumberRangeEnd에 같은 번호를 사용합니다.</p>
<p>이 번호는 정규식 (tel:)?(\+)?[1-9]\d{0,17}(;ext=[1-9]\d{0,9})?와 일치해야 합니다. 즉, 번호가 문자열 tel:(이 문자열을 지정하지 않으면 자동으로 추가됨), 더하기 기호(+) 및 숫자 1-9로 시작할 수 있습니다. 전화 번호는 최대 17자리이며 ;ext= 뒤에 내선 번호가 오는 형식으로 내선 번호를 추가할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NumberRangeStart</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>할당되지 않은 번호 범위의 첫 번째 번호입니다. NumberRangeEnd에 제공된 값보다 작거나 같아야 합니다.</p>
<p>이 번호는 정규식 (tel:)?(\+)?[1-9]\d{0,17}(;ext=[1-9]\d{0,9})?와 일치해야 합니다. 즉, 번호가 문자열 tel:(이 문자열을 지정하지 않으면 자동으로 추가됨), 더하기 기호(+) 및 숫자 1-9로 시작할 수 있습니다. 전화 번호는 최대 17자리이며 ;ext= 뒤에 내선 번호가 오는 형식으로 내선 번호를 추가할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Priority</em></p></td>
<td><p>선택</p></td>
<td><p>Int32</p></td>
<td><p>할당되지 않은 번호 범위가 겹칠 수 있습니다. 번호가 둘 이상의 범위에 속하는 경우 우선 순위가 가장 높은 범위가 적용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange 개체입니다. 할당되지 않은 숫자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsUnassignedNumber](new-csunassignednumber.md)  
[Remove-CsUnassignedNumber](remove-csunassignednumber.md)  
[Get-CsUnassignedNumber](get-csunassignednumber.md)  
[New-CsAnnouncement](new-csannouncement.md)  
[Get-CsAnnouncement](get-csannouncement.md)  
[Get-CsExUmContact](get-csexumcontact.md)

