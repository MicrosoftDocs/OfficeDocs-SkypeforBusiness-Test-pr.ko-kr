---
title: New-CsUnassignedNumber
TOCTitle: New-CsUnassignedNumber
ms:assetid: 81b5d355-56d4-4325-8518-653de8e1fab4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398651(v=OCS.15)
ms:contentKeyID: 49304219
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsUnassignedNumber

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 지정되지 않은 번호 범위와 이러한 번호에 적용되는 경로 지정 규칙을 만듭니다. 이 cmdlet을 실행하면 지정되지 않은 번호 경로 지정 테이블에 항목이 추가됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsUnassignedNumber -AnnouncementName <String> -AnnouncementService <String> -Identity <XdsGlobalRelativeIdentity> -NumberRangeEnd <String> -NumberRangeStart <String> <COMMON PARAMETERS>

    New-CsUnassignedNumber -ExUmAutoAttendantPhoneNumber <String> -Identity <XdsGlobalRelativeIdentity> -NumberRangeEnd <String> -NumberRangeStart <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Priority <Int32>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 UNSet1이라는 이름으로 지정되지 않은 번호 범위를 만듭니다. NumberRangeStart(+14255551000) 및 NumberRangeEnd(+14255551100) 매개 변수를 사용하여 지정된 알림을 적용할 지정되지 않은 번호 범위를 정의합니다. 마지막으로, AnnouncementService 매개 변수에 알림 서비스의 서비스 ID를 지정한 다음 "Welcome Announcement" 값을 AnnouncementName 매개 변수에 전달하여 알림을 지정합니다. 이 이름을 가진 알림이 이미 시스템에 있어야 합니다.

    New-CsUnassignedNumber -Identity UNSet1 -NumberRangeStart "+14255551000" -NumberRangeEnd "+14255551100" -AnnouncementService ApplicationServer:redmond.litwareinc.com -AnnouncementName "Welcome Announcement"

## 예제 2

이 예제에서는 UNSet2라는 이름으로 지정되지 않은 번호 범위를 만듭니다. 예제 1과 마찬가지로 NumberRangeStart(+14255552100) 및 NumberRangeEnd(+14255552200) 매개 변수를 사용하여 지정된 알림을 적용할 지정되지 않은 번호 범위를 정의합니다. 단, 이 예제에서는 이 번호 범위가 알림 서비스를 사용하지 않고 Exchange UM 자동 전화 교환을 사용합니다. 자동 전화 교환은 음성 프롬프트를 통해 사용자가 적절한 대상에게 연결할 수 있도록 도와주는 조직의 기본 번호로 지정된 단일 번호입니다. ExUmAutoAttendantPhoneNumber 매개 변수에 전화 번호를 전달하여 이 명령을 수행합니다. Exchange UM을 설정해야 하며 이 번호는 Active Directory 도메인 서비스의 기존 연락처 개체 전화 번호여야 합니다. 연락처는 자동 전화 교환 연락처여야 합니다(연락처의 AutoAttendant 속성이 True여야 함).

    New-CsUnassignedNumber -Identity UNSet2 -NumberRangeStart "+14255552100" -NumberRangeEnd "+14255552200" -ExUmAutoAttendantPhoneNumber "+12065551234"

## 예제 3

예제 3은 예제 2와 거의 비슷합니다. 즉, UNSet2라는 이름으로 지정되지 않은 번호 범위를 만듭니다. 이 예제에서 다른 점은 Priority 매개 변수를 추가하고 값 2를 지정한 것입니다. 이는 이 번호 범위와 겹치는 지정되지 않은 번호 범위가 정의되어 있고 해당 번호의 우선 순위가 더 높은 경우(우선 순위 숫자가 더 낮음. 예: 1) 통화는 이 범위가 아닌 이전 범위의 설정에 따라 경로 지정됨을 의미합니다.

    New-CsUnassignedNumber -Identity UNSet2 -NumberRangeStart "+14255552100" -NumberRangeEnd "+14255552200" -ExUmAutoAttendantPhoneNumber "+12065551234" -Priority 2

## 자세한 정보

지정되지 않은 번호란 조직에 지정되었지만 특정 사용자 또는 전화에는 지정되지 않은 전화 번호입니다. 지정되지 않은 번호로 전화가 걸려올 때 적절한 대상으로 통화를 경로 지정하도록 Lync Server를 설정할 수 있습니다. 이 cmdlet은 경로 지정을 정의하는 설정을 만듭니다.

이 cmdlet을 실행하기 전에 시스템에 알림이 정의되어 있거나 Exchange 통합 메시징(UM) 자동 전화 교환이 설정되어 있어야 합니다. 알림이 정의되어 있는지 확인하려면 **Get-CsAnnouncement** cmdlet을 호출합니다. 새 알림을 만들려면 **New-CsAnnouncement** cmdlet을 호출합니다. 또한 Exchange UM 자동 전화 교환 설정을 확인하려면 **Get-CsExUmContact** cmdlet을 실행합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsUnassignedNumber** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 지정된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsUnassignedNumber"}

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
<td><p>System.String</p></td>
<td><p>이 번호 범위로 걸려 온 전화를 처리하는 데 사용할 알림의 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AnnouncementService</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>알림 서비스의 FQDN(정규화된 도메인 이름) 또는 서비스 ID입니다. 이 매개 변수는 ExUmAutoAttendantPhoneNumber 매개 변수에 대한 값을 지정하지 않은 경우에만 필요합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExUmAutoAttendantPhoneNumber</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 범위의 전화를 경로 지정할 Exchange UM 자동 전화 교환 전화 번호입니다. 이 필드는 알림 서비스를 사용하지 않는 경우(AnnouncementService 또는 AnnouncementName 매개 변수에 값을 지정하지 않은 경우)에만 필요합니다. 이 매개 변수에 값을 지정하려면 Exchange UM 자동 전화 교환 대화 상대가 이미 설정되어 있어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>만드는 지정되지 않은 번호 범위의 고유한 이름입니다. 지정되지 않은 번호 범위는 모두 전역 범위를 가지므로 여기에 지정되는 이름은 Lync Server 배포 전체에서 고유해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NumberRangeEnd</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>지정되지 않은 번호 범위의 마지막 번째 번호입니다. NumberRangeStart에 제공된 번호보다 크거나 같아야 합니다. 하나의 번호로 범위를 지정하려면 NumberRangeStart와 NumberRangeEnd에 같은 번호를 사용합니다.</p>
<p>이 번호는 정규식 (tel:)?(\+)?[1-9]\d{0,17}(;ext=[1-9]\d{0,9})?와 일치해야 합니다. 즉, 번호가 문자열 tel:(이 문자열을 지정하지 않으면 자동으로 추가됨), 더하기 기호(+) 및 숫자 1-9로 시작할 수 있습니다. 전화 번호는 최대 17자리이며 ;ext= 뒤에 내선 번호가 오는 형식으로 내선 번호를 추가할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NumberRangeStart</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>지정되지 않은 번호 범위의 첫 번째 번호입니다. NumberRangeEnd에 제공된 값보다 작거나 같아야 합니다.</p>
<p>이 번호는 정규식 (tel:)?(\+)?[1-9]\d{0,17}(;ext=[1-9]\d{0,9})?와 일치해야 합니다. 즉, 번호가 문자열 tel:(이 문자열을 지정하지 않으면 자동으로 추가됨), 더하기 기호(+) 및 숫자 1-9로 시작할 수 있습니다. 전화 번호는 최대 17자리이며 ;ext= 뒤에 내선 번호가 오는 형식으로 내선 번호를 추가할 수 있습니다.</p></td>
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
<td><p><em>Priority</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>지정되지 않은 번호 범위가 겹칠 수 있습니다. 번호가 둘 이상의 범위에 속하는 경우 우선 순위가 가장 높은 범위가 적용됩니다.</p></td>
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

Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsUnassignedNumber](remove-csunassignednumber.md)  
[Set-CsUnassignedNumber](set-csunassignednumber.md)  
[Get-CsUnassignedNumber](get-csunassignednumber.md)  
[New-CsAnnouncement](new-csannouncement.md)  
[Get-CsAnnouncement](get-csannouncement.md)  
[Get-CsExUmContact](get-csexumcontact.md)

