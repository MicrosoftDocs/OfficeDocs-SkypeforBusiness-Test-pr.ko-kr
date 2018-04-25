---
title: Get-CsRgsHolidaySet
TOCTitle: Get-CsRgsHolidaySet
ms:assetid: eef7c046-088f-4334-808a-9036470919b1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412983(v=OCS.15)
ms:contentKeyID: 49305458
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsRgsHolidaySet

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 응답 그룹 휴일 집합에 대한 정보를 반환합니다. 응답 그룹 휴일 집합은 휴일 컬렉션입니다. 예를 들어 미국 기반 큐에 대한 휴일 집합과 프랑스 기반 큐에 대한 휴일 집합을 만들 수 있습니다. 미국 기반 큐는 독립 기념일(7월 4일)에 대한 휴일을 포함할 수 있는 반면, 프랑스 기반 큐는 프랑스 혁명 기념일에 대한 휴일을 정의할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsRgsHolidaySet [-Identity <RgsIdentity>] [-Name <String>] [-Owner <RgsIdentity>] [-ShowAll <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 사용하도록 구성된 모든 휴일 집합에 대한 정보를 반환합니다.

    Get-CsRgsHolidaySet

## 예제 2

예제 2에 표시된 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에 대해 구성된 모든 휴일 집합에 대한 정보를 반환합니다.

    Get-CsRgsHolidaySet -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com"

## 예제 3

예제 3에서는 Name "2013 Holidays"를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 단일 휴일 집합을 반환합니다. 이름은 각 서비스에 고유하기 때문에 이 명령은 두 개 이상의 항목을 반환하지 않습니다.

    Get-CsRgsHolidaySet -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" -Name "2013 Holidays"

## 예제 4

예제 4에서는 ApplicationServer:atl-cs-001.litwareinc.com 서비스의 "2013 Holidays" 휴일 집합에서 찾은 휴일에 대한 자세한 정보를 표시합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsHolidaySet**를 사용하여 지정된 휴일 집합을 검색합니다. 이 집합은 -ExpandProperty 매개 변수를 사용하여 집합의 각 휴일에 대한 자세한 정보를 표시하는 **Select-Object** cmdlet에 전달됩니다.

    Get-CsRgsHolidaySet -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" -Name "2013 Holidays"| Select-Object -ExpandProperty HolidayList

## 예제 5

예제 5에 표시된 명령은 ApplicationServer:atl-cs-001.litwareinc.com에서 Christmas Day라는 휴일이 포함된 각 휴일 집합의 ID를 보고합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsHolidaySet**를 호출하여 ApplicationServer:atl-cs-001.litwareinc.com에서 찾은 모든 휴일 집합의 컬렉션을 반환합니다. 이 컬렉션은 Identity 속성을 선택하고 Holidays 속성을 확장하는 **Select-Object**에 파이프됩니다.

그런 다음 이 두 가지 정보(Identity와 Holidays 속성의 확장 값)는 **Where-Object** cmdlet에 파이프됩니다. 그러면 **Where-Object**에서 휴일의 Name이 Christmas Day와 같은 항목을 선택합니다. 끝으로, 필터링된 컬렉션은 **ForEach-Object** cmdlet에 파이프됩니다. 이 cmdlet은 컬렉션의 각 ID를 가져온 후 **Get-CsRgsHolidaySet**를 사용하여 해당 휴일 집합을 하나씩 검색합니다. 그러면 Christmas Day 휴일이 포함된 모든 휴일 집합 목록이 반환됩니다.

    Get-CsRgsHolidaySet -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" | Select-Object Identity -ExpandProperty HolidayList | Where-Object {$_.Name -eq "Christmas Day"} | ForEach-Object {Get-CsRgsHolidaySet -Identity $_.Identity}

## 자세한 정보

발신자에게 가능한 최상의 환경을 제공하기 위해 응답 그룹 응용 프로그램은 응답 그룹 에이전트가 통화에 응답할 수 있는 시간과 응답할 수 없는 시간을 명확히 정의할 수 있는 기능을 제공합니다. 응답 그룹 응용 프로그램을 사용하면 업무 시간을 정의할 수 있습니다. 이러한 업무 시간은 에이전트가 통화에 응답할 수 있는 요일 및 시간을 나타냅니다. 예를 들어 조직에서 일반적으로 월요일~금요일, 오전 9시부터 오후 5시까지 업무를 보는 경우 에이전트가 월요일~금요일, 오전 9시부터 오후 5시까지 전화를 받을 수 있음을 나타내는 업무 시간을 구성합니다. 또한 목요일 오후 8시나 일요일 오후 2시 30분 등에는 에이전트가 전화를 받을 수 없음을 나타내는 업무 시간을 구성할 수도 있습니다.

그러나 대부분의 조직에는 특정 주에 업무를 보지 않는 예외가 있습니다. 예를 들어 미국의 경우 크리스마스 또는 추수 감사절이 조직의 휴무일일 수 있습니다. 이러한 예외적인 휴무를 허용하기 위해 응답 그룹 응용 프로그램에서는 일반적으로 조직의 업무일이지만 어떠한 이유로 업무를 보지 않는 특정 날짜를 휴일로 지정할 수 있습니다. **New-CsRgsHoliday** cmdlet을 사용하여 만든 개별 휴일은 휴일 집합에 포함됩니다. 예를 들어 미국의 휴일은 US\_Holidays라는 휴일 집합에 포함되고, 일본의 휴일은 Japanese\_Holidays라는 휴일 집합에 포함될 수 있습니다. 그런 다음 휴일 집합이 응답 그룹 워크플로에 할당될 수 있습니다.

**Get-CsRgsHolidaySet**를 사용하면 조직에서 사용하도록 구성된 응답 그룹 휴일 집합에 대한 정보를 가져올 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsRgsHolidaySet** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsRgsHolidaySet"}

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
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>휴일 집합이 호스트되는 서비스의 ID 또는 휴일 집합의 전체 ID를 나타냅니다. 서비스 ID(예: service:ApplicationServer:atl-cs-001.litwareinc.com)를 지정하면 해당 서비스에서 호스트되는 모든 휴일 집합이 반환되고, 휴일 집합 ID를 지정하면 지정된 집합만 반환됩니다. 휴일 집합 ID는 서비스 ID와 GUID(Globally Unique Identifier)로 구성됩니다(예: service:ApplicationServer:atl-cs-001.litwareinc.com/1987d3c2-4544-489d-bbe3-59f79f530a83).</p>
<p>서비스 ID를 지정한 다음 Name 매개 변수와 휴일 집합 이름을 포함하여 단일 휴일 집합을 반환할 수도 있습니다. 이렇게 하면 특정 휴일 집합에 할당된 GUID를 몰라도 해당 집합을 검색할 수 있습니다.</p>
<p>매개 변수 없이 호출한 경우 <strong>Get-CsRgsHolidaySet</strong>는 조직에서 사용하도록 구성된 모든 휴일 집합의 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>휴일 집합을 만들 당시 해당 집합에 지정된 고유 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Owner</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>휴일 집합을 &quot;소유&quot;하는 풀의 정규화된 도메인 이름입니다. 휴일 집합의 풀 ID와 소유자 풀 ID는 보통 같습니다. 그러나 재해 복구 절차에서와 같이 휴일 집합을 일시적으로 이동해야 하는 경우에는 풀 ID가 변경됩니다. 이 경우에도 소유자 ID는 계속 원래 풀을 가리킵니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ShowAll</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>있는 경우 소유자 풀 ID와 풀 ID가 다른 집합을 비롯하여 모든 응답 그룹 휴일 집합을 표시합니다. 기본적으로 Get-CsRgsHolidaySet는 소유자 풀 ID와 풀 ID가 동일한 에이전트 집합에 대한 정보만 반환합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsRgsHolidaySet**는 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsRgsHolidaySet**는 Microsoft.Rtc.Rgs.Management.WritableSettings.HolidaySet 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsRgsHolidaySet](new-csrgsholidayset.md)  
[Remove-CsRgsHolidaySet](remove-csrgsholidayset.md)  
[Set-CsRgsHolidaySet](set-csrgsholidayset.md)

