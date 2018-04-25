---
title: Remove-CsUnassignedNumber
TOCTitle: Remove-CsUnassignedNumber
ms:assetid: 13095593-92d3-4790-99a5-5df4610652cb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398209(v=OCS.15)
ms:contentKeyID: 49302873
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsUnassignedNumber

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정되지 않은 기존의 번호 범위와 이러한 번호에 적용되는 경로 지정 규칙을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsUnassignedNumber -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 ID가 UNSet1인 지정되지 않은 번호 설정을 제거합니다.

    Remove-CsUnassignedNumber -Identity UNSet1

## 예제 2

예제 2에서는 지정된 알림의 이름에 문자열 Welcome이 포함되어 있는 지정되지 않은 번호 설정을 모두 제거합니다. 이 명령은 먼저 지정되지 않은 모든 번호 설정의 컬렉션을 반환하는 **Get-CsUnassignedNumber** cmdlet을 호출합니다. 그런 다음 이 컬렉션은 AnnouncementName에 문자열 Welcome이 포함된(-match) 지정되지 않은 번호 설정으로 컬렉션의 범위를 좁히는 **Where-Object** cmdlet에 전달됩니다. 마지막으로 범위가 좁혀진 컬렉션은 컬렉션에 남아 있는 모든 항목을 제거하는 **Remove-CsUnassignedNumber** cmdlet에 전달됩니다.

    Get-CsUnassignedNumber | Where-Object {$_.AnnouncementName -match "Welcome"} | Remove-CsUnassignedNumber

## 자세한 정보

지정되지 않은 번호란 조직에 지정되었지만 특정 사용자 또는 전화에 지정되지 않은 전화 번호입니다. 지정되지 않은 번호로 전화가 오면 적절한 대상으로 통화를 경로 지정하도록 Lync Server를 설정할 수 있습니다. 이 cmdlet은 해당 경로 지정을 정의하는 설정을 제거합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsUnassignedNumber** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsUnassignedNumber"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>제거할 지정되지 않은 번호의 범위에 대한 고유한 이름입니다.</p></td>
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
<td><p>변경 작업을 수행하기 전에 표시되는 모든 확인 메시지를 표시하지 않습니다.</p></td>
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

Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange 개체입니다. 지정되지 않은 숫자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsUnassignedNumber](new-csunassignednumber.md)  
[Set-CsUnassignedNumber](set-csunassignednumber.md)  
[Get-CsUnassignedNumber](get-csunassignednumber.md)  
[Get-CsAnnouncement](get-csannouncement.md)  
[Get-CsExUmContact](get-csexumcontact.md)

