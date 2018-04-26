---
title: Remove-CsRgsHoursOfBusiness
TOCTitle: Remove-CsRgsHoursOfBusiness
ms:assetid: 753b2cd7-709b-455b-85a3-8b80ea35d4e0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398568(v=OCS.15)
ms:contentKeyID: 49304051
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsRgsHoursOfBusiness

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 응답 그룹 업무 시간 집합을 제거합니다. 업무 시간은 응답 그룹 에이전트가 일반적으로 전화 통화에 응답할 수 있는 요일 및 시간을 나타내는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsRgsHoursOfBusiness -Instance <BusinessHours> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 모든 업무 시간 집합을 제거합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsHoursOfBusiness**를 호출하여 ApplicationServer:atl-cs-001.litwareinc.com 서비스에서 찾은 모든 업무 시간 집합을 반환합니다. 이러한 집합은 전달된 각 업무 시간 집합을 삭제하는 **Remove-CsRgsHoursOfBusiness** cmdlet에 파이프됩니다.

    Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" | Remove-CsRgsHoursOfBusiness

## 예제 2

예제 2에서는 단일 업무 시간 집합, 즉 Help Desk Business Hours라는 컬렉션을 ApplicationServer:atl-cs-001.litwareinc.com에서 제거합니다.

    Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" -Name "Help Desk Business Hours" | Remove-CsRgsHoursOfBusiness

## 예제 3

예제 3에서는 일요일에 대해 구성된 업무 시간이 있는 모든 업무 시간 집합을 삭제합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsHoursOfBusiness**를 호출하여 ApplicationServer:atl-cs-001.litwareinc.com에서 찾은 모든 업무 시간 집합을 반환합니다. 이러한 집합은 SundayTimeRange1 속성이 Null 값과 같지 않거나, SundayTimeRange2 속성이 Null 값과 같지 않은 항목만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 시간 범위 속성이 Null이 아니라는 것은 해당 시간 간격에 대해 업무 시간이 구성되어 있음을 의미합니다. 이러한 조건 중 하나 이상을 충족하는 업무 시간 집합은 **Remove-CsRgsHoursOfBusiness** cmdlet에 파이프되어 제거됩니다.

    Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" | Where-Object {$_.SundayTimeRange1 -ne $Null -or $_.SundayTimeRange2 -ne $Null} | Remove-CsRgsHoursOfBusiness

## 예제 4

예제 4에 표시된 명령은 모든 사용자 지정 업무 시간 집합(즉, 워크플로 간에 공유할 수 없는 집합)을 삭제합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsHoursOfBusiness**를 사용하여 ApplicationServer:atl-cs-001.litwareinc.com에서 찾은 모든 업무 시간 집합을 반환합니다. 이 데이터는 Custom 속성이 True와 같은 집합만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이러한 집합은 **Remove-CsRgsHoursOfBusiness**에 파이프되어 삭제됩니다.

    Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" | Where-Object {$_.Custom -eq $True} | Remove-CsRgsHoursOfBusiness -Force

## 자세한 정보

발신자에게 가능한 최상의 환경을 제공하기 위해 응답 그룹 응용 프로그램은 응답 그룹 에이전트가 통화에 응답할 수 있는 시간과 응답할 수 없는 시간을 명확히 정의할 수 있는 기능을 제공합니다. 응답 그룹 응용 프로그램을 사용하면 업무 시간을 정의할 수 있습니다. 이러한 업무 시간은 에이전트가 통화에 응답할 수 있는 요일 및 시간을 나타냅니다. 예를 들어 조직에서 일반적으로 월요일~금요일, 오전 9시부터 오후 5시까지 업무를 보는 경우 에이전트가 월요일~금요일, 오전 9시부터 오후 5시까지 전화를 받을 수 있음을 나타내는 업무 시간을 구성합니다. 또한 목요일 오후 8시나 일요일 오후 2시 30분 등에는 에이전트가 전화를 받을 수 없음을 나타내는 업무 시간을 구성할 수도 있습니다.

새 업무 시간 집합은 **New-CsRgsHoursOfBusiness** cmdlet을 사용하여 만들 수 있으며, 나중에 **Remove-CsRgsHoursOfBusiness** cmdlet을 사용하여 제거할 수도 있습니다. **Remove-CsRgsHoursOfBusiness**를 호출하면 전체 시간 집합이 제거되고 더 이상 사용할 수 없게 되므로 주의해야 합니다. 예를 들어 지원 센터가 일요일에 더 이상 운영되지 않는 등의 이유로 특정 날짜의 업무 시간만 제거하려면 **Set-CsRgsHoursOfBusiness**를 사용하여 해당 값만 컬렉션에서 제거해야 합니다.

활성 워크플로에서 현재 사용 중인 업무 시간 집합을 삭제하려고 하면 기본적으로 **Remove-CsRgsHoursOfBusiness**에서 컬렉션을 제거할지 확인하는 메시지를 표시합니다. 이 프롬프트에 응답할 때까지 아무 작업도 수행되지 않습니다. 업무 시간 집합이 활성 워크플로에 현재 할당되어 있는 경우에도 이 프롬프트를 무시하고 업무 시간 집합을 자동으로 삭제하려면 Force 매개 변수를 추가합니다. 예를 들면 다음과 같습니다.

Get-CsRgsHoursOfBusiness –Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" | Remove-CsRgsHoursOfBusiness –Force

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsRgsHoursOfBusiness** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsRgsHoursOfBusiness"}

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
<td><p>제거할 업무 시간 집합을 가리키는 개체 참조입니다. 워크플로 개체를 <strong>Remove-CsRgsHoursOfBusiness</strong>에 파이프할 때 Instance 매개 변수를 삭제할 수 있습니다.</p>
<p>Instance 매개 변수를 사용하려면 다음과 같은 명령을 사용합니다.</p>
<p>$x = Get-CsRgsHoursOfBusiness –Identity ApplicationServer:atl-cs-001.litwareinc.com /1987d3c2-4544-489d-bbe3-59f79f530a83</p>
<p>Remove-CsRgsHoursOfBusiness –Instance $x</p>
<p>Instance 매개 변수를 사용하는 경우 한 번에 하나의 업무 시간 집합만 제거할 수 있습니다. 이는 개체 참조($x)가 여러 업무 시간 개체를 포함할 수 없음을 의미합니다.</p></td>
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
<td><p>업무 시간 집합을 강제로 삭제합니다. 이 매개 변수가 있으면 활성 워크플로에 현재 할당된 경우에도 경고 없이 집합이 삭제됩니다. 이 매개 변수가 없으면 활성 워크플로에 현재 할당된 업무 시간 집합을 삭제할지 확인하는 메시지가 표시됩니다.</p></td>
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

Microsoft.Rtc.Rgs.Management.WritableSettings.BusinessHours object. **Remove-CsRgsHoursOfBusiness**는 응답 그룹 업무 시간 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

Microsoft.Rtc.Rgs.Management.WritableSettings.BusinessHours 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsRgsHoursOfBusiness](get-csrgshoursofbusiness.md)  
[New-CsRgsHoursOfBusiness](new-csrgshoursofbusiness.md)  
[Set-CsRgsHoursOfBusiness](set-csrgshoursofbusiness.md)

