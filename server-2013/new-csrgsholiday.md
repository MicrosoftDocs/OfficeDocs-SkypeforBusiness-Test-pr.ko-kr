---
title: New-CsRgsHoliday
TOCTitle: New-CsRgsHoliday
ms:assetid: 021c6286-207d-4924-b477-15c9a98d6fda
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398075(v=OCS.15)
ms:contentKeyID: 49302620
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsRgsHoliday

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 응답 그룹 휴일을 만듭니다. 응답 그룹 응용 프로그램에서 휴일은 큐에 할당된 에이전트가 평소에는 업무일이지만 이 날만 특별히 근무하지 않고 통화에 응답할 수 없는 날짜를 나타냅니다. 예를 들어 미국에서 추수 감사절이 휴무일로 지정된 경우 2013년 11월 22일을 휴일로 구성할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsRgsHoliday -EndDate <DateTime> -StartDate <DateTime> [-Name <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 새 휴일(Christmas Day)을 만들어 기존 휴일 집합에 할당하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 이 예제의 첫 번째 명령은 **New-CsRgsHoliday** cmdlet을 사용하여 새 휴일(메모리에만 존재하고 변수 $christmasDay에 저장되는 "가상" 휴일)을 만듭니다. **New-CsRgsHoliday**는 휴일의 시작 날짜(12/25/2013 12:00 AM)를 나타내는 StartDate, 휴일의 끝 날짜(12/26/2013 12:00 AM)를 나타내는 EndDate 및 휴일에 지정할 고유 이름을 나타내는 Name의 세 가지 매개 변수를 사용합니다.

새 휴일이 만들어지면 두 번째 명령이 **Get-CsRgsHolidaySet**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 "2013 Holidays" 휴일 집합을 검색합니다. 이 휴일 집합은 변수 $y에 저장됩니다.

세 번째 명령은 Add 메서드를 사용하여 휴일 집합의 가상 복사본($y)에 새 휴일($christmasDay)을 추가합니다. 그런 다음 마지막 명령은 **Set-CsRgsHolidaySet**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com 서비스에 변경 내용(즉, 새 휴일 추가)을 기록합니다.

    $christmasDay = New-CsRgsHoliday -StartDate "12/25/2013 12:00 AM" -EndDate "12/26/2013 12:00 AM" -Name "Christmas Day"
    $y = Get-CsRgsHolidaySet -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com"  -Name "2013 Holidays"
    $y.HolidayList.Add($christmasDay)
    Set-CsRgsHolidaySet -Instance $y

## 자세한 정보

응답 그룹 응용 프로그램에서는 업무 시간 컬렉션을 사용하여 에이전트가 일반적으로 전화 통화에 응답할 수 있는 요일 및 시간을 나타냅니다. 예를 들어 지원 센터가 일반적으로 매주 월요일 오전 7시부터 오후 7시까지 운영되는 경우 지원 센터에 대한 업무 시간 컬렉션을 만들고 일반적인 월요일의 업무 시작 시간을 오전 7시로, 업무 종료 시간을 오후 7시로 구성합니다.

그러나 지원 센터가 매주 월요일 오전 7시부터 오후 7시까지 운영되는 규칙에는 예외가 있을 수 있습니다. 예를 들어 미국의 독립 기념일은 공휴일이므로 7월 4일에는 지원 센터 직원이 근무하지 않을 수도 있습니다. 2013년 7월 4일 목요일에 지원 센터가 운영되지 않는다는 사실을 적용하려면 이 날짜에 대한 휴일을 만들어 지원 센터 휴일 집합에 추가해야 합니다.

휴일을 만들려면 **New-CsRgsHoliday** cmdlet을 사용해야 합니다. 휴일은 단순히 에이전트가 전화에 응답할 수 없는 날짜이므로 특정 기념일이나 경조사를 "휴일"에 반드시 포함해야 하는 것은 아닙니다. **New-CsRgsHoliday**는 휴일 집합에 휴일을 직접 추가하지 않습니다. 대신 이 cmdlet은 메모리에만 존재하는 새 휴일을 만듭니다. 따라서 메모리에만 나타나는 이 인스턴스를 가리키는 개체 참조(예: $x)를 만들어야 합니다. 메모리에 휴일을 만든 후에는 **Get-CsRgsHolidaySet** cmdlet을 사용하여 적절한 휴일 집합을 검색하고 **Set-CsRgsHolidaySet** cmdlet을 사용하여 해당 집합에 새 휴일을 추가합니다.

휴일 집합은 일반적으로 여러 휴일을 포함할 수 있지만 이러한 휴일을 한 번에 하나씩 해당 집합에 추가해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **New-CsRgsHoliday** cmdlet을 로컬로 실행할 수 있습니다. 그러나 이 cmdlet은 메모리에만 나타나는 개체를 만들고 자체적으로 시스템을 변경하지 않기 때문에 기본적으로 누구든지 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsRgsHoliday\\b"}

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
<td><p><em>EndDate</em></p></td>
<td><p>필수</p></td>
<td><p>System.DateTime</p></td>
<td><p>휴일의 끝 날짜입니다. 끝 날짜의 형식은 국가 및 언어 옵션에 따라 다릅니다. 예를 들어 미국의 경우 끝 날짜 2013년 7월 4일은 -EndDate &quot;7/5/2013 12:00 AM&quot;과 같은 형식입니다. 이는 2013년 7월 5일 오전 12시에 휴일이 종료됨을 의미합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>StartDate</em></p></td>
<td><p>필수</p></td>
<td><p>System.DateTime</p></td>
<td><p>휴일의 시작 날짜입니다. 시작 날짜의 형식은 국가 및 언어 옵션에 따라 다릅니다. 예를 들어 미국의 경우 시작 날짜 2013년 7월 4일은 -StartDate &quot;7/4/2013 12:00 AM&quot;과 같은 형식입니다. 이는 2013년 7월 4일 오전 12시에 휴일이 시작됨을 나타냅니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>휴일을 휴일 집합과 구별하는 데 사용되는 고유 이름입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsRgsHoliday**는 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsRgsHoliday**는 Microsoft.Rtc.Rgs.Management.WritableSettings.Holiday 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsRgsHolidaySet](new-csrgsholidayset.md)  
[Set-CsRgsHolidaySet](set-csrgsholidayset.md)

