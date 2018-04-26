---
title: Remove-CsRgsHolidaySet
TOCTitle: Remove-CsRgsHolidaySet
ms:assetid: 6e1f4ec3-2f8a-4ab1-810b-3d64eecd2031
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398521(v=OCS.15)
ms:contentKeyID: 49303969
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsRgsHolidaySet

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 응답 그룹 휴일 집합을 제거합니다. 응답 그룹 휴일 집합은 휴일 컬렉션입니다. 예를 들어 미국 기반 큐에 대한 휴일 집합과 프랑스 기반 큐에 대한 휴일 집합을 만들 수 있습니다. 미국 기반 큐는 독립 기념일(7월 4일)에 대한 휴일을 포함할 수 있는 반면, 프랑스 기반 큐는 프랑스 혁명 기념일에 대한 휴일을 정의할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsRgsHolidaySet -Instance <HolidaySet> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 "2010 Holidays" 휴일 집합을 제거합니다. 이 작업을 수행하기 위해 이 명령은 먼저 휴일 집합의 위치를 지정하는 Identity 매개 변수와 휴일 집합의 이름을 지정하는 Name 매개 변수의 두 가지 매개 변수와 함께 **Get-CsRgsHolidaySet**를 호출합니다. 반환된 개체는 2010 Holidays 휴일 집합을 삭제하는 **Remove-CsRgsHolidaySet**에 파이프됩니다.

    Get-CsRgsHolidaySet -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" -Name "2010 Holidays" | Remove-CsRgsHolidaySet

## 예제 2

예제 2에서는 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 New Year’s Day 휴일을 포함하는 모든 휴일 집합을 삭제합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsHolidaySet**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 모든 휴일 집합의 컬렉션을 반환합니다. 이 컬렉션은 1) 각 휴일 집합의 Identity 속성을 선택하고, 2) HolidayList 속성 값을 "확장"하는 **Select-Object** cmdlet에 파이프됩니다. 값을 확장하면 기본 개체의 속성이 반환됩니다. 즉, 휴일의 경우 Name, StartDate 및 EndDate와 같은 속성이 반환됩니다. 여기서 선택한 정보(휴일 집합 ID 및 휴일 속성 값)는 Name이 "New Year's Day"와 같은(-eq) 휴일이 포함된 집합을 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 휴일 집합 컬렉션은 New Year's Day 휴일이 포함된 각 휴일 집합을 삭제하는 **Remove-CsRgsHolidaySet**에 파이프됩니다.

    Get-CsRgsHolidaySet -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com"  | Select-Object Identity -ExpandProperty HolidayList | Where-Object {$_.Name -eq "New Year's Day"}  | Remove-CsRgsHolidaySet 

## 예제 3

예제 3에 표시된 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 할당된 휴일이 5일 미만인 휴일 집합을 삭제합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsHolidaySet**를 호출하여 ApplicationServer:atl-cs-001.litwareinc.com에서 찾은 모든 휴일 집합의 컬렉션을 반환합니다. 이 컬렉션은 할당된 휴일 수($\_.Holidays.Count)가 5보다 작은 휴일 집합만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이러한 휴일 집합은 **Remove-CsRgsHolidaySet** cmdlet에 파이프되어 삭제됩니다.

    Get-CsRgsHolidaySet -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com"  | Where-Object {$_.HolidayList.Count -lt 5} | Remove-CsRgsHolidaySet

## 자세한 정보

발신자에게 가능한 최상의 환경을 제공하기 위해 응답 그룹 응용 프로그램은 응답 그룹 에이전트가 통화에 응답할 수 있는 시간과 응답할 수 없는 시간을 명확히 정의할 수 있는 기능을 제공합니다. 응답 그룹 응용 프로그램을 사용하면 에이전트가 통화에 응답할 수 있는 요일 및 시간을 나타내는 업무 시간을 정의할 수 있습니다. 예를 들어 조직에서 일반적으로 월요일~금요일, 오전 9시부터 오후 5까지 업무를 보는 경우 에이전트가 월요일~금요일, 오전 9시부터 오후 5시까지 전화를 받을 수 있음을 나타내는 업무 시간을 구성합니다. 또한 목요일 오후 8시나 일요일 오후 2시 30분 등에는 에이전트가 전화를 받을 수 없음을 나타내는 업무 시간을 구성할 수도 있습니다.

그러나 대부분의 조직에는 특정 주에 업무를 수행하지 않는 예외가 있습니다. 예를 들어 미국의 경우 크리스마스 또는 추수 감사절이 조직의 휴무일일 수 있습니다. 이러한 예외적인 휴무를 허용하기 위해 응답 그룹 응용 프로그램에서는 일반적으로 조직의 업무일이지만 이유에 관계없이 업무를 수행하지 않는 특정 날짜를 휴일로 지정할 수 있습니다 **New-CsRgsHoliday** cmdlet을 사용하여 만든 개별 휴일은 휴일 집합에 포함됩니다. 예를 들어 미국의 휴일은 US\_Holidays라는 휴일 집합에 포함되고, 일본의 휴일은 Japanese\_Holidays라는 휴일 집합에 포함될 수 있습니다. 그런 다음 휴일 및 휴일 집합이 응답 그룹 워크플로에 할당될 수 있습니다.

**Remove-CsRgsHolidaySet** cmdlet을 사용하여 관리자는 응답 그룹 휴일 집합을 제거할 수 있습니다. 활성 워크플로에 현재 할당된 휴일 집합을 제거하려고 하면 기본적으로 cmdlet이 일시 중지되고 워크플로를 삭제할지 묻는 메시지가 표시됩니다. 이 프롬프트에 응답할 때까지 명령이 실행되지 않으며 휴일 집합이 제거되지 않습니다. 이 프롬프트를 무시하고 활성 워크플로에서 현재 사용 중인 경우에도 휴일 집합을 제거하려면 Force 매개 변수를 추가합니다.

Get-CsRgsHolidaySet -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" -Name "2010 Holidays" | Remove-CsRgsHolidaySet –Force

**Remove-CsRgsHolidaySet**를 호출하면 전체 휴일 집합이 제거되고 더 이상 사용할 수 없게 되므로 주의해야 합니다. 예를 들어 추수 감사절에도 근무하기 때문에 이러한 단일 휴일을 휴일 집합에서 제거하려면 **Set-CsRgsHolidaySet**를 사용하여 지정한 휴일만 제거해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsRgsHolidaySet** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsRgsHolidaySet"}

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
<td><p>제거할 휴일 집합을 가리키는 개체 참조입니다. 워크플로 개체를 <strong>Remove-CsRgsHolidaySet</strong>에 파이프할 때 Instance 매개 변수를 삭제할 수 있습니다.</p>
<p>Instance 매개 변수를 사용하려면 다음과 같은 명령을 사용합니다.</p>
<p>$x = Get-CsRgsHolidaySet –Identity ApplicationServer:atl-cs-001.litwareinc.com /1987d3c2-4544-489d-bbe3-59f79f530a83</p>
<p>Remove-CsRgsHolidaySet –Instance $x</p>
<p>Instance 매개 변수를 사용하는 경우 한 번에 하나의 휴일 집합만 제거할 수 있습니다. 이는 개체 참조($x)가 여러 휴일 집합 개체를 포함할 수 없음을 의미합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수는 테스트용으로만 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>휴일 집합을 강제로 제거합니다. 이 매개 변수가 있으면 활성 워크플로에서 사용하는 경우에도 경고 없이 휴일 집합이 삭제됩니다. 이 매개 변수가 없으면 활성 워크플로에 현재 할당된 휴일 집합을 삭제할지 확인하는 메시지가 표시됩니다.</p></td>
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

**Remove-CsRgsHolidaySet**는 Microsoft.Rtc.Rgs.Management.WritableSettings.HolidaySet 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsRgsHolidaySet](get-csrgsholidayset.md)  
[New-CsRgsHolidaySet](new-csrgsholidayset.md)  
[Set-CsRgsHolidaySet](set-csrgsholidayset.md)

