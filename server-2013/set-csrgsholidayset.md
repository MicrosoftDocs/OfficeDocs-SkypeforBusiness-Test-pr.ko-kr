---
title: Set-CsRgsHolidaySet
TOCTitle: Set-CsRgsHolidaySet
ms:assetid: 90848409-25a0-4cc9-a0aa-f3331b5f93e9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398736(v=OCS.15)
ms:contentKeyID: 49304378
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsRgsHolidaySet

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 응답 그룹 휴일 집합의 속성 값을 수정합니다. 응답 그룹 휴일 집합은 휴일 컬렉션입니다. 예를 들어 미국 기반 큐에 대한 휴일 집합과 프랑스 기반 큐에 대한 휴일 집합을 만들 수 있습니다. 미국 기반 큐는 독립 기념일(7월 4일)에 대한 휴일을 포함할 수 있는 반면, 프랑스 기반 큐는 프랑스 혁명 기념일에 대한 휴일을 정의할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsRgsHolidaySet -Instance <HolidaySet> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 새 휴일(Christmas Day)을 만들어 기존 휴일 집합에 할당합니다. 이 작업을 수행하기 위해 이 예제의 첫 번째 명령은 **New-CsRgsHoliday** cmdlet을 사용하여 새 휴일(메모리에만 존재하고 변수 $x에 저장되는 "가상" 휴일)을 만듭니다. **New-CsRgsHoliday**는 휴일의 시작 날짜(12/25/2010)를 나타내는 StartDate, 휴일의 끝 날짜(12/25/2010)를 나타내는 EndDate 및 휴일에 지정할 고유 이름을 나타내는 Name의 세 가지 매개 변수를 사용합니다.

새 휴일이 만들어지면 두 번째 명령이 **Get-CsRgsHolidaySet**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 "2010 Holidays" 휴일 집합을 검색합니다. 이 휴일 집합은 변수 $y에 저장됩니다.

세 번째 명령은 Add 메서드를 사용하여 휴일 집합의 가상 복사본($y)에 새 휴일($x)을 추가합니다. 그런 다음 마지막 명령은 **Set-CsRgsHolidaySet**를 호출하여 ApplicationServer:atl-cs-001.litwareinc.com 서비스에 변경 내용을 기록하고 새 휴일을 추가합니다.

    $x = New-CsRgsHoliday -StartDate "12/25/2010" -EndDate "12/26/2010" -Name "Christmas Day"
    $y = Get-CsRgsHolidaySet -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" -Name "2010 Holidays"
    $y.HolidayList.Add($x)
    Set-CsRgsHolidaySet -Instance $y

## 예제 2

예제 2의 명령은 기존 휴일 집합에서 휴일(이 경우 Christmas Day)을 제거합니다. 이 작업을 수행하기 위해 이 예제의 첫 번째 명령은 **Get-CsRgsHolidaySet**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 2010 Holidays 휴일 집합(-Name "2010 Holidays")을 검색합니다. 검색된 데이터는 변수 $x에 저장됩니다.

두 번째 명령은 검색된 휴일 집합의 HolidayList 속성을 이름 속성이 "Christmas Day"와 같은 휴일 하나를 선택하는 **Where-Object** cmdlet에 파이프합니다. 이 단일 휴일은 $y 변수에 저장됩니다.

Christmas Day 휴일을 검색한 후에는 명령 3에서 Remove 메서드를 사용하여 휴일 집합에서 Christmas Day 휴일($y)을 제거합니다. 그런 다음 이 예제의 마지막 명령은 **Set-CsRgsHolidaySet**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com의 실제 2010 Holidays 휴일 집합에 이러한 변경 내용(즉, Christmas Day 휴일 제거)을 기록합니다.

    $x = Get-CsRgsHolidaySet -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "2010 Holidays"
    $y = $x.HolidayList | Where-Object {$_.Name -eq "Christmas Day"}
    $x.HolidayList.Remove($y)
    Set-CsRgsHolidaySet -Instance $x

## 예제 3

예제 3에 표시된 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 2010 Holidays 휴일 집합에서 모든 휴일을 삭제합니다. 이 작업을 수행하기 위해 이 예제의 첫 번째 명령은 **Get-CsRgsHolidaySet**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에서 해당 휴일 집합을 검색합니다. 이 휴일 집합은 변수 $x에 저장됩니다.

휴일 집합을 검색한 후에는 Clear 메서드를 사용하여 HolidayList 속성에 저장된 모든 값을 제거합니다. 이 속성이 제거된 후 이 예제의 마지막 명령은 **Set-CsRgsHolidaySet** cmdlet을 사용하여 2010 Holidays 휴일 집합에 이러한 변경 내용을 다시 기록합니다.

    $x = Get-CsRgsHolidaySet -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name "2010 Holidays"
    $x.HolidayList.Clear()
    Set-CsRgsHolidaySet -Instance $x

## 자세한 정보

발신자에게 가능한 최상의 환경을 제공하기 위해 응답 그룹 응용 프로그램은 응답 그룹 에이전트가 통화에 응답할 수 있는 시간과 응답할 수 없는 시간을 명확히 정의할 수 있는 기능을 제공합니다. 응답 그룹 응용 프로그램을 사용하면 에이전트가 통화에 응답할 수 있는 요일 및 시간을 나타내는 업무 시간을 정의할 수 있습니다. 예를 들어 조직에서 일반적으로 월요일~금요일, 오전 9시부터 오후 5까지 업무를 보는 경우 에이전트가 월요일~금요일, 오전 9시부터 오후 5시까지 전화를 받을 수 있음을 나타내는 업무 시간을 구성합니다. 또한 목요일 오후 8시나 일요일 오후 2시 30분 등에는 에이전트가 전화를 받을 수 없음을 나타내는 업무 시간을 구성할 수도 있습니다.

그러나 대부분의 조직에는 특정 주에 업무를 보지 않는 예외가 있습니다. 예를 들어 미국의 경우 크리스마스 또는 추수 감사절이 조직의 휴무일일 수 있습니다. 이러한 예외적인 휴무를 허용하기 위해 응답 그룹 응용 프로그램에서는 일반적으로 조직의 업무일이지만 어떠한 이유로 업무를 보지 않는 특정 날짜를 휴일로 지정할 수 있습니다. **New-CsRgsHoliday** cmdlet을 사용하여 만든 개별 휴일은 휴일 집합에 포함됩니다. 예를 들어 미국의 휴일은 US\_Holidays라는 휴일 집합에 포함되고, 일본의 휴일은 Japanese\_Holidays라는 휴일 집합에 포함될 수 있습니다. 그런 다음 휴일 집합이 응답 그룹 워크플로에 할당될 수 있습니다.

**Set-CsRgsHolidaySet** cmdlet을 사용하면 기존 휴일 집합을 수정할 수 있습니다. 대부분의 경우 이는 휴일을 집합에 추가하거나 집합에서 제거하는 작업을 의미합니다. **Set-CsRgsHolidaySet**를 사용하여 휴일 집합을 직접 변경할 수는 없습니다. 대신 **Get-CsRgsHolidaySet** cmdlet을 사용하여 기존 휴일 집합에 대한 개체 참조를 만들어야 합니다. 이 경우 개체 참조는 기존 휴일 집합을 참조하는 변수입니다. 휴일 집합에 대한 변경 내용이 메모리에 적용되면 **Set-CsRgsHolidaySet**를 사용하여 실제 휴일 집합에 해당 변경 내용을 기록합니다. **Set-CsRgsHolidaySet**를 호출하지 않으면 변경 내용이 메모리에만 존재하고 Windows PowerShell을 닫거나 개체 참조를 삭제하는 즉시 사라집니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsRgsHolidaySet** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsRgsHolidaySet"}

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
<td><p><em>Instance</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.HolidaySet</p></td>
<td><p>수정할 응답 그룹 휴일 집합에 대한 개체 참조입니다. 일반적으로 개체 참조는 <strong>Get-CsRgsHolidaySet</strong> cmdlet을 사용하여 반환된 값을 변수에 할당하는 방식으로 검색합니다. 예를 들어 이 명령은 Help Desk 휴일 집합에 대한 개체 참조를 반환하여 해당 개체 참조를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-CsRgsHolidaySet -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name &quot;Help Desk&quot;</p>
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
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
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

Microsoft.Rtc.Rgs.Management.WritableSettings.HolidaySet 개체입니다. **Remove-CsRgsHolidaySet**는 응답 그룹 휴일 집합 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsRgsHolidaySet**는 개체나 값을 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Rgs.Management.WritableSettings.HolidaySet 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsRgsHolidaySet](get-csrgsholidayset.md)  
[New-CsRgsHoliday](new-csrgsholiday.md)  
[New-CsRgsHolidaySet](new-csrgsholidayset.md)  
[Remove-CsRgsHolidaySet](remove-csrgsholidayset.md)

