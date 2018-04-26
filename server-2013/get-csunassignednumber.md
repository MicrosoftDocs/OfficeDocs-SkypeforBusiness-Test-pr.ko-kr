---
title: Get-CsUnassignedNumber
TOCTitle: Get-CsUnassignedNumber
ms:assetid: a8e5cfc1-e7a0-4917-9cd9-f541fedb3a61
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412792(v=OCS.15)
ms:contentKeyID: 49304656
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsUnassignedNumber

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 할당되지 않은 번호 범위 및 이러한 번호에 적용되는 경로 지정 규칙을 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsUnassignedNumber [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsUnassignedNumber [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 사용하도록 구성된 모든 할당되지 않은 번호의 컬렉션을 반환합니다.

    Get-CsUnassignedNumber

## 예제 2

예제 2에서는 Identity 매개 변수를 사용하여 ID가 UNSet1인 할당되지 않은 번호에 대한 데이터만 검색되도록 제한합니다. ID가 고유해야 하므로 이 명령은 지정한 할당되지 않은 번호 범위만 반환합니다.

    Get-CsUnassignedNumber -Identity UNSet1

## 예제 3

이 예제에서는 Filter 매개 변수를 사용하여 Identity 값에 Redmond 문자열이 포함된 모든 할당되지 않은 번호 설정 컬렉션을 반환합니다. 예를 들어 이 명령은 Redmond Numbers, Unassigned Redmond Numbers, UNRedmond 등의 ID를 가진 할당되지 않은 번호 설정을 반환합니다.

    Get-CsUnassignedNumber -Filter *Redmond*

## 예제 4

예제 4에서는 **Get-CsUnassignedNumber** cmdlet 및 **Where-Object** cmdlet을 사용하여 알림 이름에 Welcome 단어가 포함된 모든 할당되지 않은 번호 설정 컬렉션을 검색합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUnassignedNumber** cmdlet을 사용하여 모든 할당되지 않은 번호 설정을 검색합니다. 이 컬렉션은 할당된 알림 이름에 Welcome 단어가 있는 할당되지 않은 번호에 대한 데이터만 반환하도록 제한하는 필터를 적용하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsUnassignedNumber | Where-Object {$_.AnnouncementName -match "Welcome"}

## 자세한 정보

할당되지 않은 번호란 조직에 할당되었지만 특정 사용자 또는 전화에 할당되지 않은 전화 번호입니다. 할당되지 않은 번호로 전화가 걸려올 때 적절한 대상으로 통화를 경로 지정하도록 Lync Server를 설정할 수 있습니다. 이 cmdlet은 이러한 경로 지정을 정의하는 하나 이상의 할당되지 않은 번호 범위를 검색합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsUnassignedNumber** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsUnassignedNumber"}

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
<td><p>지정된 와일드카드 문자열과 일치하는 ID를 가진 할당되지 않은 번호 설정만 포함하도록 결과의 범위를 좁힐 수 있는 와일드카드 검색을 수행합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>검색할 할당되지 않은 번호 범위의 고유한 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 할당되지 않은 번호 정보를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange 유형의 개체를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsUnassignedNumber](new-csunassignednumber.md)  
[Remove-CsUnassignedNumber](remove-csunassignednumber.md)  
[Set-CsUnassignedNumber](set-csunassignednumber.md)

