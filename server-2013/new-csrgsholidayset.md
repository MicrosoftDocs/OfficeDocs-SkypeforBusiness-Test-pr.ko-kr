---
title: New-CsRgsHolidaySet
TOCTitle: New-CsRgsHolidaySet
ms:assetid: 5c110dcf-f596-44ae-8d40-bfafc6701550
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398403(v=OCS.15)
ms:contentKeyID: 49303755
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsRgsHolidaySet

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 응답 그룹 휴일 집합을 만듭니다. 응답 그룹 휴일 집합은 휴일 컬렉션입니다. 예를 들어 미국 기반 큐에 대한 휴일 집합과 프랑스 기반 큐에 대한 휴일 집합을 만들 수 있습니다. 미국 기반 큐는 독립 기념일(7월 4일)에 대한 휴일을 포함할 수 있는 반면, 프랑스 기반 큐는 프랑스 혁명 기념일에 대한 휴일을 정의할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsRgsHolidaySet -HolidayList <Collection> -Name <String> -Parent <RgsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 2013 Holidays라는 새 휴일 집합을 만든 다음 이 휴일 집합에 새 휴일(New Year's Day)을 할당합니다. 이 작업을 수행하기 위해 첫 번째 명령은 **New-CsRgsHoliday**를 사용하여 New Year's Day에 대한 휴일을 만듭니다. **New-CsRgsHoliday**는 휴일의 시작 날짜(1/1/2013 12:00 A.M.)를 나타내는 StartDate, 휴일의 끝 날짜(1/2/2013 12:00 A.M.)를 나타내는 EndDate 및 휴일에 할당된 이름을 저장하는 데 사용되는 Name의 세 가지 매개 변수를 사용합니다. 결과 휴일 개체는 변수 $x에 저장됩니다.

새 휴일이 메모리에 만들어진 후에는 **New-CsRgsHolidaySet**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com 서비스에 새 휴일 집합을 만듭니다. 이 휴일 집합에는 2013 Holidays라는 이름이 지정되고(-Name "2013 Holidays") $x: -HolidayList ($x) 변수에 저장된 휴일이 할당됩니다. 휴일 집합에 여러 휴일을 할당하려면 새 휴일을 만들어 각 휴일을 고유 변수에 할당하기만 하면 됩니다. 그런 다음 이 모든 변수 이름을 HolidayList에 전달되는 매개 변수 값으로 포함할 수 있습니다.

\-HolidayList($x, $y, $z)

    $x = New-CsRgsHoliday -StartDate "1/1/2013 12:00 AM" -EndDate "1/2/2013 12:00 AM" -Name "New Year's Day"
    New-CsRgsHolidaySet -Parent "service:ApplicationServer:atl-cs-001.litwareinc.com" -Name "2013 Holidays" -HolidayList($x)

## 자세한 정보

발신자에게 가능한 최상의 환경을 제공하기 위해 응답 그룹 응용 프로그램은 응답 그룹 에이전트가 통화에 응답할 수 있는 시간과 응답할 수 없는 시간을 명확히 정의할 수 있는 기능을 제공합니다. 응답 그룹 응용 프로그램을 사용하면 업무 시간을 정의할 수 있습니다. 이러한 업무 시간은 에이전트가 통화에 응답할 수 있는 요일 및 시간을 나타냅니다. 예를 들어 조직에서 일반적으로 월요일~금요일, 오전 9시부터 오후 5까지 업무를 보는 경우 에이전트가 월요일~금요일, 오전 9시부터 오후 5시까지 전화를 받을 수 있음을 나타내는 업무 시간을 구성합니다. 또한 목요일 오후 8시나 일요일 오후 2시 30분 등에는 에이전트가 전화를 받을 수 없음을 나타내는 업무 시간을 구성할 수도 있습니다.

그러나 대부분의 조직에는 특정 주에 업무를 수행하지 않는 예외가 있습니다. 예를 들어 미국의 경우 크리스마스 또는 추수 감사절이 조직의 휴무일일 수 있습니다. 예외적인 휴무를 허용하기 위해 응답 그룹 응용 프로그램에서는 일반적으로 조직의 업무일이지만 이유에 관계없이 업무를 수행하지 않는 특정 날짜를 휴일로 지정할 수 있습니다. **New-CsRgsHoliday** cmdlet을 사용하여 만든 개별 휴일은 휴일 집합에 포함됩니다. 예를 들어 미국의 휴일은 US\_Holidays라는 휴일 집합에 포함되고, 일본의 휴일은 Japanese\_Holidays라는 휴일 집합에 포함될 수 있습니다. 그런 다음 휴일 및 해당 휴일 집합이 응답 그룹 워크플로에 할당될 수 있습니다.

**New-CsRgsHolidaySet** cmdlet을 사용하면 조직에서 사용할 새 휴일 집합을 구성할 수 있습니다. 새 휴일 집합을 만들 때는 하나 이상의 휴일을 포함해야 하며, 이러한 개별 휴일은 **New-CsRgsHoliday** cmdlet을 사용하여 만들어야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsRgsHolidaySet** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsRgsHolidaySet"}

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
<td><p><em>HolidayList</em></p></td>
<td><p>필수</p></td>
<td><p>System.Collections.ObjectModel.Collection</p></td>
<td><p>휴일 집합에 추가할 하나 이상의 휴일입니다. 휴일은 <strong>New-CsRgsHoliday</strong> cmdlet을 사용하여 만든 다음 개체 참조에 저장해야 합니다. 이러한 개체 참조는 휴일을 휴일 집합에 추가하기 위해 Holidays 매개 변수로 전달됩니다. 예를 들어 이 명령은 New Year’s Day라는 휴일을 만든 다음 $x라는 개체 참조에 결과 값을 저장합니다.</p>
<p>$x = New-CsRgsHoliday -StartDate &quot;1/1/2013 12:00 AM&quot; -EndDate &quot;1/2/2013 12:00 AM&quot; -Name &quot;New Year's Day&quot;</p>
<p>날짜 및 시간을 지정하는 데 사용되는 형식은 사용자의 국가 및 언어 옵션에 따라 다릅니다. 이 항목에 표시된 예제에서는 영어(미국)를 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>휴일 집합에 할당할 고유 이름입니다. Parent 속성과 Name 속성을 조합하면 휴일 집합의 GUID(Globally Unique Identifier)를 참조하지 않고도 휴일 집합을 고유하게 식별할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Parent</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>새 휴일 집합을 호스트할 서비스입니다(예: -Parent &quot;service:ApplicationServer:atl-cs-001.litwareinc.com&quot;).</p></td>
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
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
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

없음. **New-CsRgsHolidaySet**는 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsRgsHolidaySet**는 Microsoft.Rtc.Rgs.Management.WritableSettings.HolidaySet 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsRgsHolidaySet](get-csrgsholidayset.md)  
[New-CsRgsHoliday](new-csrgsholiday.md)  
[Remove-CsRgsHolidaySet](remove-csrgsholidayset.md)  
[Set-CsRgsHolidaySet](set-csrgsholidayset.md)

