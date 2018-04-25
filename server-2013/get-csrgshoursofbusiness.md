---
title: Get-CsRgsHoursOfBusiness
TOCTitle: Get-CsRgsHoursOfBusiness
ms:assetid: 2008d55c-fd53-4004-b6e6-08cdf0175af8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398284(v=OCS.15)
ms:contentKeyID: 49303023
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsRgsHoursOfBusiness

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 응답 그룹 업무 시간 컬렉션에 대한 정보를 반환합니다. 업무 시간 컬렉션은 응답 그룹 에이전트가 일반적으로 전화 통화에 응답할 수 있는 요일 및 시간을 나타내는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsRgsHoursOfBusiness [-Identity <RgsIdentity>] [-Name <String>] [-Owner <RgsIdentity>] [-ShowAll <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 사용하도록 구성된 모든 업무 시간 컬렉션에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 매개 변수 없이 **Get-CsRgsHoursOfBusiness**를 호출합니다.

    Get-CsRgsHoursOfBusiness

## 예제 2

예제 2에 표시된 명령은 atl-cs-001.litwareinc.com에서 사용하도록 구성된 모든 업무 시간 컬렉션을 반환합니다.

    Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com"

## 예제 3

예제 3에서는 atl-cs-001.litwareinc.com에서 "Help Desk Business Hours"라는 단일 컬렉션을 반환합니다.

    Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" -Name "Help Desk Business Hours"

## 예제 4

예제 4에 표시된 명령은 일요일에 대해 구성된 업무 시간이 있는 모든 업무 시간 컬렉션을 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsHoursOfBusiness**를 호출하여 atl-cs-001.litwareinc.com에서 찾은 모든 업무 시간 컬렉션을 반환합니다. 이 데이터는 SundayTimeRange1 속성과 SundayTimeRange2 속성 중 하나 또는 둘 다가 Null 값과 같지 않은 항목만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 시간 범위 속성이 Null이 아니라는 것은 해당 기간에 대해 업무 시간이 구성되어 있음을 의미합니다.

    Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" | Where-Object {$_.SundayTimeRange1 -ne $Null -or $_.SundayTimeRange2 -ne $Null}

## 예제 5

예제 5에 표시된 명령은 atl-cs-001.litwareinc.com에서 MondayTimeRange1 속성의 시작 시간이 오전 8시와 같거나 그 이전인 모든 업무 시간 컬렉션을 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsHoursOfBusiness**를 사용하여 atl-cs-001.litwareinc.com에서 모든 업무 시간 컬렉션을 반환합니다. 이 데이터는 MondayTimeRange1.OpenTime 속성 값이 오전 8시(08:00:00)보다 작거나 같은 컬렉션만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" | Where-Object {$_.MondayTimeRange1.OpenTime -le "08:00:00"}

## 예제 6

예제 6에 표시된 명령은 모든 공용 업무 시간 컬렉션(즉, 워크플로 간에 공유할 수 있는 컬렉션)을 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsRgsHoursOfBusiness**를 사용하여 atl-cs-001.litwareinc.com에서 찾은 모든 업무 시간 컬렉션을 반환합니다. 이 데이터는 Custom 속성이 False와 같은 컬렉션만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:atl-cs-001.litwareinc.com" | Where-Object {$_.Custom -eq $False}

## 자세한 정보

발신자에게 가능한 최상의 환경을 제공하기 위해 응답 그룹 응용 프로그램은 응답 그룹 에이전트가 통화에 응답할 수 있는 시간과 응답할 수 없는 시간을 명확히 정의할 수 있는 기능을 제공합니다. 응답 그룹 응용 프로그램을 사용하면 에이전트가 통화에 응답할 수 있는 요일 및 시간을 나타내는 업무 시간을 정의할 수 있습니다. 예를 들어 조직에서 일반적으로 월요일~금요일, 오전 9시부터 오후 5시까지 업무를 보는 경우 에이전트가 월요일~금요일, 오전 9시부터 오후 5시까지 전화를 받을 수 있음을 나타내는 업무 시간을 구성합니다. 또한 목요일 오후 8시나 일요일 오후 2시 30분 등에는 에이전트가 전화를 받을 수 없음을 나타내는 업무 시간을 구성할 수도 있습니다.

**Get-CsRgsHoursOfBusiness** cmdlet을 사용하면 조직에서 사용하도록 구성된 업무 시간 컬렉션에 대한 정보를 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsRgsHoursOfBusiness** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsRgsHoursOfBusiness"}

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
<td><p>업무 시간 컬렉션이 호스트되는 서비스의 ID 또는 컬렉션 자체의 전체 ID를 나타냅니다. 서비스 ID(예: service:ApplicationServer:atl-cs-001.litwareinc.com)를 지정하면 해당 서비스에서 호스트되는 모든 업무 시간 컬렉션이 반환되고, 컬렉션 ID를 지정하면 지정된 업무 시간 컬렉션만 반환됩니다. 업무 시간 컬렉션 ID는 서비스 ID와 GUID(Globally Unique Identifier)로 구성됩니다(예: service:ApplicationServer-ApplicationServer-1/1987d3c2-4544-489d-bbe3-59f79f530a83).</p>
<p>서비스 ID를 지정한 다음 Name 매개 변수와 컬렉션 이름을 포함하여 업무 시간 컬렉션을 반환할 수도 있습니다. 이렇게 하면 특정 업무 시간 컬렉션에 할당된 GUID를 몰라도 해당 컬렉션을 검색할 수 있습니다.</p>
<p>매개 변수 없이 호출한 경우 <strong>Get-CsRgsHoursOfBusiness</strong>는 조직에서 사용하도록 구성된 모든 업무 시간 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>업무 시간 컬렉션을 만들 당시 해당 컬렉션에 지정된 고유 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Owner</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Rgs.Management.RgsIdentity</p></td>
<td><p>업무 시간을 &quot;소유&quot;하는 풀의 정규화된 도메인 이름입니다. 업무 시간 컬렉션의 풀 ID와 소유자 풀 ID는 보통 같습니다. 그러나 재해 복구 절차에서와 같이 컬렉션을 일시적으로 이동해야 하는 경우에는 풀 ID가 변경됩니다. 이 경우에도 소유자 ID는 계속 원래 풀을 가리킵니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ShowAll</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>있는 경우 소유자 풀 ID와 풀 ID가 다른 컬렉션을 비롯하여 모든 리소스 그룹 업무 시간 컬렉션을 표시합니다. 기본적으로 Get-CsRgsHoursOfBusiness는 소유자 풀 ID와 풀 ID가 동일한 업무 시간 컬렉션에 대한 정보만 반환합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsRgsHoursOfBusiness**는 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Rgs.Management.WritableSettings.BusinessHours 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsRgsHoursOfBusiness](new-csrgshoursofbusiness.md)  
[Remove-CsRgsHoursOfBusiness](remove-csrgshoursofbusiness.md)  
[Set-CsRgsHoursOfBusiness](set-csrgshoursofbusiness.md)

