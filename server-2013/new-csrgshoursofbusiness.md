---
title: New-CsRgsHoursOfBusiness
TOCTitle: New-CsRgsHoursOfBusiness
ms:assetid: 21869ba6-526e-4c70-b84d-de73536d8a43
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398291(v=OCS.15)
ms:contentKeyID: 49303039
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsRgsHoursOfBusiness

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 응답 그룹 응용 프로그램 업무 시간 집합을 만듭니다. 업무 시간 집합은 응답 그룹 에이전트가 일반적으로 전화 통화에 응답할 수 있는 요일 및 시간을 나타내는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsRgsHoursOfBusiness -Name <String> -Parent <RgsIdentity> [-Confirm [<SwitchParameter>]] [-Custom <$true | $false>] [-Force <SwitchParameter>] [-FridayHours1 <TimeRange>] [-FridayHours2 <TimeRange>] [-InMemory <SwitchParameter>] [-MondayHours1 <TimeRange>] [-MondayHours2 <TimeRange>] [-SaturdayHours1 <TimeRange>] [-SaturdayHours2 <TimeRange>] [-SundayHours1 <TimeRange>] [-SundayHours2 <TimeRange>] [-ThursdayHours1 <TimeRange>] [-ThursdayHours2 <TimeRange>] [-TuesdayHours1 <TimeRange>] [-TuesdayHours2 <TimeRange>] [-WednesdayHours1 <TimeRange>] [-WednesdayHours2 <TimeRange>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ApplicationServer:atl-cs-001.litwareinc.com에 Help Desk Business Hours라는 새 업무 시간 집합을 만듭니다. 이 예제에는 이 집합에 대한 업무 시간이 구성되어 있지 않습니다.

    New-CsRgsHoursOfBusiness -Parent "service:ApplicationServer:atl-cs-001.litwareinc.com" -Name "Help Desk Business Hours" 

## 예제 2

예제 2에서는 ApplicationServer:atl-cs-001.litwareinc.com에 Help Desk Business Hours라는 새 업무 시간 집합을 만듭니다. 이 예제에서는 월요일부터 금요일까지 각 요일에 대해 업무 시간이 구성됩니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsRgsTimeRange** 명령을 사용하여 OpenTime이 오전 8시(8:00)이고 CloseTime이 오후 6시(18:00)인 시간 범위를 만듭니다. 이 시간 범위는 $weekday라는 변수에 저장됩니다.

그러면 예제의 두 번째 명령이 새 업무 시간 집합을 만듭니다. 집합의 Parent 및 Name을 지정하는 것 외에 추가 매개 변수(예: MondayHours1)를 사용하여 월요일부터 금요일까지의 평일 업무 시간을 구성합니다. 이러한 업무 시간은 각 요일에 대해 시간 범위 변수 $weekday를 사용하여 오전 8시부터 오후 6시까지로 설정됩니다.

    $weekday = New-CsRgsTimeRange -Name "Weekday Hours" -OpenTime "8:00" -CloseTime "18:00" 
    
    New-CsRgsHoursOfBusiness -Parent "service:ApplicationServer:atl-cs-001.litwareinc.com" -Name "Help Desk Business Hours" -MondayHours1 $weekday -TuesdayHours1 $weekday -WednesdayHours1 $weekday -ThursdayHours1 $weekday -FridayHours1 $weekday

## 자세한 정보

발신자에게 가능한 최상의 환경을 제공하기 위해 응답 그룹 응용 프로그램은 응답 그룹 에이전트가 통화에 응답할 수 있는 시간과 응답할 수 없는 시간을 명확히 정의할 수 있는 기능을 제공합니다. 응답 그룹 응용 프로그램을 사용하면 업무 시간을 정의할 수 있습니다. 이러한 업무 시간은 에이전트가 통화에 응답할 수 있는 요일 및 시간을 나타냅니다. 예를 들어 조직에서 일반적으로 월요일~금요일, 오전 9시부터 오후 5까지 업무를 보는 경우 에이전트가 월요일~금요일, 오전 9시부터 오후 5시까지 전화를 받을 수 있음을 나타내는 업무 시간을 구성합니다. 또한 목요일 오후 8시나 일요일 오후 2시 30분 등에는 에이전트가 전화를 받을 수 없음을 나타내는 업무 시간을 구성할 수도 있습니다.

새 업무 시간 집합은 **New-CsRgsHoursOfBusiness** cmdlet을 사용하여 만듭니다. 업무 시간 집합에서 업무 시간을 구성할 때 각 요일에 Hours1 속성과 Hours2 속성이 둘 다 있다는 점을 주의해야 합니다. 예를 들어 지원 센터가 오전 8시부터 오후 5시까지 운영되는 경우 해당 Hours1 속성에만 값을 할당하면 되지만, 지원 센터가 오전 8시부터 오후 2시까지 운영되고, 다시 오후 5시부터 오후 11시까지 운영되는 경우에는 오전 8시에서 오후 2시 사이의 시간 범위를 Hours1에 할당하고, 오후 5시에서 오후 11시 사이의 시간 범위를 Hours2에 할당해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsRgsHoursOfBusiness** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsRgsHoursOfBusiness"}

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
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>업무 시간 집합에 할당할 고유 이름입니다. Parent 속성 및 Name 속성을 결합하면 컬렉션의 GUID(Globally Unique Identifier)를 참조하지 않고도 업무 시간 집합을 고유하게 식별할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Parent</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>새 업무 시간 집합을 호스트할 서비스입니다예를 들면 다음과 같습니다. -Parent &quot;service:ApplicationServer:atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Custom</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 지정된 워크플로에서만 업무 시간을 사용할 수 있습니다. False(기본값)로 설정하면 여러 워크플로 간에 업무 시간을 공유할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>FridayHours1</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.TimeRange</p></td>
<td><p>금요일에 열고 닫는 시간의 첫 번째 집합입니다. 모든 금요일에 오전 9시부터 오후 5시까지 영업한다면 시간 범위를 하나만 구성하면 되지만, 오전 8시부터 정오까지 영업하고 점심 시간 동안 닫은 다음 오후 1시부터 오후 5시까지 다시 영업한다면 금요일에 대해 두 가지 시간 범위를 만들어야 합니다.</p>
<p>금요일에 영업을 하지 않는 경우에는 FridayHours1과 FridayHours2 둘 다 값을 구성하지 않아야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>FridayHours2</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.TimeRange</p></td>
<td><p>금요일에 열고 닫는 시간의 두 번째 집합입니다. 모든 금요일에 오전 9시부터 오후 5시까지 영업한다면 시간 범위를 하나만 구성하면 되지만, 오전 8시부터 정오까지 영업하고 점심 시간 동안 닫은 다음 오후 1시부터 오후 5시까지 다시 영업한다면 금요일에 대해 두 가지 시간 범위를 만들어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MondayHours1</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.TimeRange</p></td>
<td><p>월요일에 열고 닫는 시간의 첫 번째 집합입니다. 모든 월요일에 오전 9시부터 오후 5시까지 영업한다면 시간 범위를 하나만 구성하면 되지만, 오전 8시부터 정오까지 영업하고 점심 시간 동안 닫은 다음 오후 1시부터 오후 5시까지 다시 영업한다면 월요일에 대해 두 가지 시간 범위를 만들어야 합니다.</p>
<p>월요일에 영업을 하지 않는 경우에는 MondayHours1과 MondayHours2 둘 다 값을 구성하지 않아야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MondayHours2</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.TimeRange</p></td>
<td><p>월요일에 열고 닫는 시간의 두 번째 집합입니다. 모든 월요일에 오전 9시부터 오후 5시까지 영업한다면 시간 범위를 하나만 구성하면 되지만, 오전 8시부터 정오까지 영업하고 점심 시간 동안 닫은 다음 오후 1시부터 오후 5시까지 다시 영업한다면 월요일에 대해 두 가지 시간 범위를 만들어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SaturdayHours1</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.TimeRange</p></td>
<td><p>토요일에 열고 닫는 시간의 첫 번째 집합입니다. 모든 토요일에 오전 9시부터 오후 5시까지 영업한다면 시간 범위를 하나만 구성하면 되지만, 오전 8시부터 정오까지 영업하고 점심 시간 동안 닫은 다음 오후 1시부터 오후 5시까지 다시 영업한다면 토요일에 대해 두 가지 시간 범위를 만들어야 합니다.</p>
<p>토요일에 영업을 하지 않는 경우에는 SaturdayHours1과 SaturdayHours2 둘 다 값을 구성하지 않아야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SaturdayHours2</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.TimeRange</p></td>
<td><p>토요일에 열고 닫는 시간의 두 번째 집합입니다. 모든 토요일에 오전 9시부터 오후 5시까지 영업한다면 시간 범위를 하나만 구성하면 되지만, 오전 8시부터 정오까지 영업하고 점심 시간 동안 닫은 다음 오후 1시부터 오후 5시까지 다시 영업한다면 토요일에 대해 두 가지 시간 범위를 만들어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SundayHours1</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.TimeRange</p></td>
<td><p>일요일에 열고 닫는 시간의 첫 번째 집합입니다. 모든 일요일에 오전 9시부터 오후 5시까지 영업한다면 시간 범위를 하나만 구성하면 되지만, 오전 8시부터 정오까지 영업하고 점심 시간 동안 닫은 다음 오후 1시부터 오후 5시까지 다시 영업한다면 일요일에 대해 두 가지 시간 범위를 만들어야 합니다.</p>
<p>일요일에 영업을 하지 않는 경우에는 SundayHours1과 SundayHours2 둘 다 값을 구성하지 않아야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SundayHours2</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.TimeRange</p></td>
<td><p>일요일에 열고 닫는 시간의 두 번째 집합입니다. 모든 일요일에 오전 9시부터 오후 5시까지 영업한다면 시간 범위를 하나만 구성하면 되지만, 오전 8시부터 정오까지 영업하고 점심 시간 동안 닫은 다음 오후 1시부터 오후 5시까지 다시 영업한다면 일요일에 대해 두 가지 시간 범위를 만들어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ThursdayHours1</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.TimeRange</p></td>
<td><p>목요일에 열고 닫는 시간의 첫 번째 집합입니다. 모든 목요일에 오전 9시부터 오후 5시까지 영업한다면 시간 범위를 하나만 구성하면 되지만, 오전 8시부터 정오까지 영업하고 점심 시간 동안 닫은 다음 오후 1시부터 오후 5시까지 다시 영업한다면 목요일에 대해 두 가지 시간 범위를 만들어야 합니다.</p>
<p>목요일에 영업을 하지 않는 경우에는 ThursdayHours1과 ThursdayHours2 둘 다 값을 구성하지 않아야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ThursdayHours2</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.TimeRange</p></td>
<td><p>목요일에 열고 닫는 시간의 두 번째 집합입니다. 모든 목요일에 오전 9시부터 오후 5시까지 영업한다면 시간 범위를 하나만 구성하면 되지만, 오전 8시부터 정오까지 영업하고 점심 시간 동안 닫은 다음 오후 1시부터 오후 5시까지 다시 영업한다면 목요일에 대해 두 가지 시간 범위를 만들어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TuesdayHours1</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.TimeRange</p></td>
<td><p>화요일에 열고 닫는 시간의 첫 번째 집합입니다. 모든 화요일에 오전 9시부터 오후 5시까지 영업한다면 시간 범위를 하나만 구성하면 되지만, 오전 8시부터 정오까지 영업하고 점심 시간 동안 닫은 다음 오후 1시부터 오후 5시까지 다시 영업한다면 화요일에 대해 두 가지 시간 범위를 만들어야 합니다.</p>
<p>화요일에 영업을 하지 않는 경우에는 TuesdayHours1과 TuesdayHours2 둘 다 값을 구성하지 않아야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TuesdayHours2</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.TimeRange</p></td>
<td><p>화요일에 열고 닫는 시간의 두 번째 집합입니다. 모든 화요일에 오전 9시부터 오후 5시까지 영업한다면 시간 범위를 하나만 구성하면 되지만, 오전 8시부터 정오까지 영업하고 점심 시간 동안 닫은 다음 오후 1시부터 오후 5시까지 다시 영업한다면 화요일에 대해 두 가지 시간 범위를 만들어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WednesdayHours1</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.TimeRange</p></td>
<td><p>수요일에 열고 닫는 시간의 첫 번째 집합입니다. 모든 수요일에 오전 9시부터 오후 5시까지 영업한다면 시간 범위를 하나만 구성하면 되지만, 오전 8시부터 정오까지 영업하고 점심 시간 동안 닫은 다음 오후 1시부터 오후 5시까지 다시 영업한다면 수요일에 대해 두 가지 시간 범위를 만들어야 합니다.</p>
<p>수요일에 영업을 하지 않는 경우에는 WednesdayHours1과 WednesdayHours2 둘 다 값을 구성하지 않아야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WednesdayHours2</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.WritableSettings.TimeRange</p></td>
<td><p>수요일에 열고 닫는 시간의 두 번째 집합입니다. 모든 수요일에 오전 9시부터 오후 5시까지 영업한다면 시간 범위를 하나만 구성하면 되지만, 오전 8시부터 정오까지 영업하고 점심 시간 동안 닫은 다음 오후 1시부터 오후 5시까지 다시 영업한다면 수요일에 대해 두 가지 시간 범위를 만들어야 합니다.</p></td>
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

없음. **New-CsRgsHoursOfBusiness**는 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Rgs.Management.WritableSettings.BusinessHours 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsRgsHoursOfBusiness](get-csrgshoursofbusiness.md)  
[New-CsRgsTimeRange](new-csrgstimerange.md)  
[Remove-CsRgsHoursOfBusiness](remove-csrgshoursofbusiness.md)  
[Set-CsRgsHoursOfBusiness](set-csrgshoursofbusiness.md)

