---
title: New-CsRgsTimeRange
TOCTitle: New-CsRgsTimeRange
ms:assetid: e8abc3cc-2b13-479d-83d6-2f542fa12e45
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399040(v=OCS.15)
ms:contentKeyID: 49305386
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsRgsTimeRange

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 응답 그룹 시간 범위를 만듭니다. 시간 범위는 응답 그룹 응용 프로그램에서 업무일의 시작 시간과 종료 시간을 지정하는 데 사용됩니다. 예를 들어 지원 센터 에이전트가 일요일에는 정오부터 오후 5시까지만 근무하는 경우 시작 시간이 정오이고 종료 시간이 오후 5시인 일요일의 시간 범위를 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsRgsTimeRange -CloseTime <TimeSpan> -OpenTime <TimeSpan> [-Name <String>]

## 예제

## 예제 1

예제 1에서는 **New-CsRgsTimeRange** cmdlet을 사용하여 기존 업무 시간 집합의 속성을 수정하는 방법을 보여 줍니다. 이 예제에서는 먼저 **New-CsRgsTimeRange**를 호출하여 "Sunday hours"라는 새 시간 범위를 만듭니다. 이 시간 범위는 시작 시간을 오전 8시 30분(8:30)으로 설정하고 종료 시간을 오후 1시 30분(13:30)으로 설정합니다. 이 명령에서 만든 메모리 내부 시간 범위는 $sundayHours 변수에 저장됩니다.

시간 범위를 구성한 후 이 예제의 두 번째 명령은 **Get-CsRgsHoursOfBusiness**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 Help Desk Hours라는 업무 시간 컬렉션을 반환합니다. 반환된 컬렉션은 변수 $y에 저장됩니다.

컬렉션을 검색한 후 세 번째 명령은 SundayHours1 속성 값을 $sundayHours(새로 만든 시간 범위를 포함하는 개체 참조)로 설정합니다. 그런 다음 이 명령이 완료되면 **Set-CsRgsHoursOfBusiness**를 사용하여 Help Desk Hours 업무 시간 컬렉션에 이러한 변경 내용을 기록합니다. **Set-CsRgsHoursOfBusiness**를 호출하지 못한 경우에는 새로 만든 시간 범위가 메모리에만 존재하고 Windows PowerShell을 닫거나 $sundayHours 변수를 삭제하는 즉시 사라집니다. 이 경우 Help Desk Hours 업무 시간 컬렉션이 업데이트되지 않습니다.

    $sundayHours = New-CsRgsTimeRange -Name "Sunday hours" -OpenTime "08:30" -CloseTime "13:30"
    $y = Get-CsRgsHoursOfBusiness -Identity Service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk Hours" 
    $y.SundayHours1 = $sundayHours
    Set-CsRgsHoursOfBusiness -Instance $y

## 예제 2

예제 2에서는 새 응답 그룹 시간 범위를 만든 다음 새 업무 시간 집합에서 이 시간 범위를 사용합니다. 이 예제의 첫 번째 명령은 **New-CsRgsTimeRange** cmdlet을 사용하여 Sunday Hours라는 새 시간 범위를 만듭니다. 이 범위의 OpenTime은 오전 8시 30분("8:30")으로 설정되고, CloseTime은 오후 1시 30분("13:30" - 24시간제 형식 사용 시 13시 30분)으로 설정됩니다. 결과 시간 범위 개체는 $sundayHours 변수에 저장됩니다.

두 번째 명령은 **New-CsRgsBusinessHours** cmdlet을 사용하여 Help Desk Hours라는 새 업무 시간 컬렉션을 만듭니다. 이 명령에서 $sundayHours 변수는 SundayHours1 속성의 시간 범위를 지정합니다.

    $sundayHours = New-CsRgsTimeRange -Name "Sunday hours" -OpenTime "08:30" -CloseTime "13:30"
    New-CsRgsHoursOfBusiness -Parent Service:ApplicationServer:atl-cs-001.litwareinc.com -Name "Help Desk Hours" -SundayHours1 $sundayHours

## 자세한 정보

응답 그룹 응용 프로그램에서는 업무 시간 컬렉션을 사용하여 에이전트가 일반적으로 전화에 응답할 수 있는 요일 및 시간을 추적합니다. 예를 들어 지원 센터가 매주 월요일 오전 7시부터 오후 7시까지 운영된다고 가정해 보겠습니다. 이 경우 두 가지 작업을 수행해야 합니다. 즉, **New-CsRgsHoursOfBusiness** cmdlet을 사용하여 지원 센터에 대한 업무 시간 컬렉션을 만들고, 지원 센터가 오전 7시에 시작하여 오후 7시에 종료됨을 나타내도록 MondayTimeRange1 속성을 수정해야 합니다.

기존 업무 시간 컬렉션을 수정하려면 **Set-CsRgsHoursOfBusiness** cmdlet을 사용해야 합니다. 그러나 이 cmdlet을 사용하여 시간 범위 속성을 직접 수정할 수는 없습니다. 예를 들어 **Set-CsRgsHoursOfBusiness**에는 MondayTimeRange1 속성에 해당하는 매개 변수가 없습니다. 대신 업무 시간 컬렉션을 수정하려면 **Get-CsRgsHoursOfBusiness**를 사용하여 해당 컬렉션을 검색하고, 컬렉션 변경 내용을 메모리에만 적용한 다음, **Set-CsRgsHoursOfBusiness**를 사용하여 실제 업무 시간 컬렉션에 이러한 변경 내용을 기록해야 합니다.

업무 시간 컬렉션에 대한 변경 작업에는 지정된 날짜의 시작 및/또는 종료 시간 변경이 포함되는 경우가 많습니다. 시작 시간 및 종료 시간을 수정하려면 **New-CsRgsTimeRange** cmdlet을 사용하여 이러한 시간을 지정해야 합니다. 이 cmdlet을 호출하면 결과 값이 개체 참조 변수에 저장됩니다. 그런 다음 이 변수는 업무 시간 컬렉션 내에서 시작 시간 및 종료 시간을 설정하는 데 사용됩니다.

또한 **New-CsRgsTimeRange**를 사용하여 새 업무 시간 컬렉션을 만들 때마다 시작 시간 및 종료 시간을 지정해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **New-CsRgsTimeRange** cmdlet을 로컬로 실행할 수 있습니다. 그러나 이 cmdlet은 메모리에만 나타나는 개체를 만들고 자체적으로 시스템을 변경하지 않기 때문에 기본적으로 누구든지 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsRgsTimeRange"}

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
<td><p><em>CloseTime</em></p></td>
<td><p>필수</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>업무 시간이 종료되는 시간입니다. CloseTime은 24시간제 형식으로 지정해야 합니다. 예를 들어 업무 시간이 오후 9시에 종료됨을 나타내려면 -CloseTime &quot;21:00&quot; 형식을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OpenTime</em></p></td>
<td><p>필수</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>업무 시간이 시작되는 시간입니다. OpenTime은 24시간제 형식으로 지정해야 합니다. 예를 들어 업무 시간이 오후 1시 30분에 시작됨을 나타내려면 -OpenTime &quot;13:30&quot; 형식을 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>만들려는 시간 범위의 고유 식별자입니다. Name은 최대 128자로 제한됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음**. New-CsRgsTimeRange**는 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsRgsTimeRange**는 Microsoft.Rtc.Rgs.Management.WritableSettings.TimeRange 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsRgsHoursOfBusiness](new-csrgshoursofbusiness.md)  
[Set-CsRgsHoursOfBusiness](set-csrgshoursofbusiness.md)

