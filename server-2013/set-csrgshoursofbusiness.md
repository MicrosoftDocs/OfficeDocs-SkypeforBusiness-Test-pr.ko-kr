---
title: Set-CsRgsHoursOfBusiness
TOCTitle: Set-CsRgsHoursOfBusiness
ms:assetid: be976e84-00aa-46d5-94d3-527c4c9f3963
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412929(v=OCS.15)
ms:contentKeyID: 49304884
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsRgsHoursOfBusiness

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 응답 그룹 업무 시간 집합을 구성합니다. 업무 시간 집합은 응답 그룹 에이전트가 일반적으로 전화 통화에 응답할 수 있는 요일 및 시간을 나타내는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsRgsHoursOfBusiness -Instance <BusinessHours> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Help Desk Business Hours 업무 시간 집합의 SaturdayHours1 및 SundayHours1 속성에 새 시간 범위 값을 할당하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 이 예제의 첫 번째 명령은 **New-CsRgsTimeRange**를 사용하여 시작 시간이 정오(12:00)이고 종료 시간이 오후 5시(17:00)인 새 시간 범위 개체(Weekend Hours)를 만듭니다. 이 개체는 $weekend 변수에 저장됩니다.

다음 명령은 ApplicationServer:atl-cs-001.litwareinc.com의 Help Desk Business Hours 업무 시간 집합에 대한 개체 참조($x)를 만듭니다. 이 명령이 완료되면 세 번째 명령과 네 번째 명령이 각각 SaturdayHours1 및 SundayHours1 속성을 $weekend에 저장된 시간 범위 값으로 설정합니다. 끝으로, 이 예제의 마지막 명령은 **Set-CsRgsHoursOfBusiness**를 사용하여 실제 업무 시간 집합에 이러한 변경 내용을 다시 기록합니다.

    $weekend = New-CsRgsTimeRange -Name "Weekend Hours" -OpenTime "12:00" -CloseTime "17:00"
    
    $x = Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" -Name "Help Desk Business Hours"
    $x.SaturdayHours1 = $weekend
    $x.SundayHours1 = $weekend
    Set-CsRgsHoursOfBusiness -Instance $x

## 예제 2

예제 2에 표시된 명령은 Help Desk Business Hours 업무 시간 집합의 SaturdayHours1 및 SaturdayHours2 속성에 대해 구성된 값을 삭제합니다. 이 작업을 수행하기 위해 첫 번째 명령은 ApplicationServer:atl-cs-001.litwareinc.com의 Help Desk Business Hours 업무 시간 집합에 대한 개체 참조($x)를 만듭니다. 개체 참조를 만든 후에는 두 번째 명령에서 SaturdayHours1 속성을 Null 값($Null)으로 설정합니다. 이렇게 하면 이전에 SaturdayHours1에 할당된 값이 효과적으로 지워집니다. 그런 다음 유사한 명령을 사용하여 이전에 SaturdayHours2에 할당된 모든 값을 삭제합니다.

이 예제의 마지막 명령은 **Set-CsRgsHoursOfBusiness**를 사용하여 실제 업무 시간 집합에 이러한 변경 내용을 다시 기록합니다. 명령 실행이 완료되면 Help Desk Business Hours에 할당된 Saturday 업무 시간이 더 이상 없습니다.

    $x = Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" -Name "Help Desk Business Hours"
    $x.SaturdayHours1 = $Null
    $x.SaturdayHours2 = $Null
    
    Set-CsRgsHoursOfBusiness -Instance $x

## 자세한 정보

발신자에게 가능한 최상의 환경을 제공하기 위해 응답 그룹 응용 프로그램은 응답 그룹 에이전트가 통화에 응답할 수 있는 시간과 응답할 수 없는 시간을 명확히 정의할 수 있는 기능을 제공합니다. 응답 그룹 응용 프로그램을 사용하면 업무 시간을 정의할 수 있습니다. 이러한 업무 시간은 에이전트가 통화에 응답할 수 있는 요일 및 시간을 나타냅니다. 예를 들어 조직에서 일반적으로 월요일~금요일, 오전 9시부터 오후 5시까지 업무를 보는 경우 에이전트가 월요일~금요일, 오전 9시부터 오후 5시까지 전화를 받을 수 있음을 나타내는 업무 시간을 구성합니다. 또한 목요일 오후 8시나 일요일 오후 2시 30분 등에는 에이전트가 전화를 받을 수 없음을 나타내는 업무 시간을 구성할 수도 있습니다.

업무 시간 집합은 **New-CsRgsHoursOfBusiness** cmdlet을 사용하여 만듭니다. 이러한 집합을 만든 후에는 **Set-CsRgsHoursOfBusiness** cmdlet을 사용하여 수정할 수 있습니다. 일반적으로 이는 하나 이상의 요일에 대한 업무 시간을 변경하는 작업을 의미합니다. 예를 들어 지원 센터가 이전에는 금요일 오후 5시까지 운영되었지만 지금은 금요일 오후 7시까지 운영되는 경우 금요일의 업무 시간을 수정해야 합니다. 또한 지원 센터가 이전에는 토요일에 운영되었지만 지금은 토요일이 휴무일인 경우 마찬가지로 토요일 업무 시간을 수정해야 합니다. 특정 날짜에 그룹을 사용할 수 없음을 나타내려면 해당 날짜의 업무 시간을 Null 값으로 설정하면 됩니다(-SundayTimeRange1 $Null).

업무 시간 집합에서 업무 시간을 구성할 때 각 요일에 Hours1 속성과 Hours2 속성이 둘 다 있다는 점을 주의해야 합니다. 예를 들어 지원 센터가 오전 8시부터 오후 5시까지 운영되는 경우 해당 Hours1 속성에만 값을 할당하면 되지만, 지원 센터가 오전 8시부터 오후 2시까지 운영되고, 다시 오후 5시부터 오후 11시까지 운영되는 경우에는 오전 8시에서 오후 2시 사이의 시간 범위를 Hours1에 할당하고, 오후 5시에서 오후 11시 사이의 시간 범위를 Hours2에 할당해야 합니다.

**Set-CsRgsHoursOfBusiness**는 업무 시간 집합을 직접 수정하지 않습니다. 대신 **Get-CsRgsHoursOfBusiness**를 사용하여 수정할 집합에 대한 개체 참조를 만들어야 합니다. 개체 참조를 만들려면 업무 시간 집합의 복사본을 검색하여 변수에 저장하기만 하면 됩니다. 개체 참조를 만든 후에는 메모리에만 나타나는 이 개체의 속성을 수정합니다. 그런 다음 수정이 완료되면 **Set-CsRgsHoursOfBusiness**를 사용하여 실제 업무 시간 집합에 이러한 변경 내용을 기록합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsRgsHoursOfBusiness** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsRgsHoursOfBusiness"}

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
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.BusinessHours</p></td>
<td><p>수정할 업무 시간 집합에 대한 개체 참조입니다. 일반적으로 개체 참조는 <strong>Get-CsRgsHoursOfBusiness</strong> cmdlet을 사용하여 반환된 값을 변수에 할당하는 방식으로 검색합니다. 예를 들어 이 명령은 Help Desk 업무 시간 집합에 대한 개체 참조를 반환하여 해당 개체 참조를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-CsRgsHoursOfBusiness -Identity service:ApplicationServer:atl-cs-001.litwareinc.com -Name &quot;Help Desk&quot;</p></td>
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

Microsoft.Rtc.Rgs.Management.WritableSettings.BusinessHours object. **Set-CsRgsHoursOfBusiness**는 응답 그룹 업무 시간 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

Microsoft.Rtc.Rgs.Management.WriteableSettings.BusinessHours 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsRgsHoursOfBusiness](get-csrgshoursofbusiness.md)  
[New-CsRgsHoursOfBusiness](new-csrgshoursofbusiness.md)  
[New-CsRgsTimeRange](new-csrgstimerange.md)  
[Remove-CsRgsHoursOfBusiness](remove-csrgshoursofbusiness.md)

