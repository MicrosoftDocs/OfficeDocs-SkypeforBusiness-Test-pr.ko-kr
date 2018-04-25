---
title: Get-CsWindowsService
TOCTitle: Get-CsWindowsService
ms:assetid: 9b119dac-c3e6-4031-8ae4-972fca1ef728
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398803(v=OCS.15)
ms:contentKeyID: 49304507
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsWindowsService

 

_**마지막으로 수정된 항목:** 2015-03-09_

**Get-CsWindowsService**는 Windows 서비스로 실행되는 Lync Server 구성 요소에 대한 세부 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsWindowsService [-ComputerName <String>] [-ExcludeActivityLevel <SwitchParameter>] [-Name <String>] [-Report <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 로컬 컴퓨터에서 실행되는 모든 Lync Server 서비스에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 **Get-CsWindowsService** cmdlet을 매개 변수 없이 호출합니다.

    Get-CsWindowsService

## 예제 2

예제 2에서는 로컬 컴퓨터의 Lync Server 서비스에 대한 정보를 반환합니다. 그러나 이 경우 데이터는 목록 형식으로 표시됩니다. 무엇보다 이 명령을 사용하여 각 서비스의 모든 속성 값을 볼 수 있습니다. 기본 표 형식 보기에는 속성 값의 하위 집합만 표시됩니다. 이 작업을 수행하기 위해 먼저 **Get-CsWindowsService** cmdlet을 호출합니다. 그런 다음 결과 정보를 **Format-List** cmdlet에 파이프합니다.

    Get-CsWindowsService | Format-List

## 예제 3

예제 3에서는 이름 RTCSrv가 포함된 단일 Lync Server 서비스에 대한 정보를 반환합니다.

    Get-CsWindowsService -Name "RTCSrv"

## 예제 4

예제 4에서는 RTCSrv 서비스에서 처리되는 모든 서비스 역할에 대한 세부 정보가 표시됩니다. 이 작업을 수행하기 위해 먼저 **Get-CsWindowsService** cmdlet을 사용하여 RTCSrv 서비스에 대한 정보를 반환합니다. 이 정보는 ExpandProperty 매개 변수를 사용하여 RTCSrv 서비스에서 처리하는 모든 역할을 표시하는 **Select-Object** cmdlet에 파이프됩니다. 이 명령은 서비스에 역할 이름이 없는 경우 오류 메시지를 반환합니다.

    Get-CsWindowsService -Name "RTCSrv" | Select-Object -ExpandProperty RoleName

## 예제 5

예제 5에 표시된 명령은 원격 컴퓨터 atl-cs-001.litwareinc.com에 설치된 Lync Server 서비스에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 ComputerName 매개 변수와 원격 컴퓨터의 FQDN을 차례로 포함합니다.

    Get-CsWindowsService -Computer atl-cs-001.litwareinc.com

## 예제 6

예제 6에서는 로컬 컴퓨터에 설치된 모든 Lync Server 서비스에 대한 정보를 반환합니다. 또한 Report 매개 변수를 포함하여 오류 정보를 C:\\Logs\\Services.html 파일에 저장합니다. **Get-CsWindowsService** cmdlet이 서비스 데이터를 검색하는 동안 문제가 발생하면 해당 문제에 대한 정보가 Services.html에 기록됩니다.

    Get-CsWindowsService -Report C:\Logs\Services.html

## 예제 7

예제 7에서는 현재 실행되고 있는 로컬 컴퓨터의 Lync Server 서비스에 대한 정보만 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsWindowsService** cmdlet을 호출하여 실행되거나 실행되고 있지 않은 모든 Lync Server 서비스의 컬렉션을 반환합니다. 이 컬렉션은 Status 속성이 Running과 같은 서비스만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsWindowsService | Where-Object {$_.Status -eq "Running"}

## 예제 8

예제 8에서는 해당 서비스의 실제 이름(이 경우 RTCASMCU)을 알 수 없는 경우에도 특정 서비스에 대한 정보를 검색할 수 있는 방법을 보여 줍니다. 이 작업을 수행하기 위해 먼저 **Get-CsWindowsService** cmdlet을 매개 변수 없이 호출합니다. 그러면 로컬 컴퓨터에 있는 모든 Lync Server 서비스의 컬렉션이 반환됩니다. 이 컬렉션은 DisplayName 속성이 문자열 값 "Application Sharing"을 포함하는(-like) 서비스 하나를 선택하는 **Where-Object** cmdlet에 파이프됩니다. 최종적으로 Lync Server  응용 프로그램 공유 회의 서비스에 대한 정보가 표시됩니다.

    Get-CsWindowsService | Where-Object {$_.DisplayName -like "*Application Sharing*"}

## 예제 9

예제 9에서는 Application Server 역할을 호스트하는 서비스에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsWindowsService** cmdlet을 호출하여 로컬 컴퓨터에 있는 모든 Lync Server 서비스의 컬렉션을 반환합니다. 이 컬렉션은 RoleName 속성에 ApplicationServer가 포함된(-contains) 서비스를 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsWindowsService | Where-Object {$_.RoleName -contains "ApplicationServer"}

## 자세한 정보

많은 Lync Server 구성 요소가 표준 Windows 서비스로 실행됩니다. 예를 들어 Lync Server  회의 길잡이 응용 프로그램은 실제로 RTCCAA라는 서비스입니다. **Get-CsWindowsService** cmdlet을 사용하면 Lync Server 서비스와 이러한 서비스에 대한 세부 정보만 검색할 수 있습니다. 이는 cmdlet이 Lync Server에 포함되지 않은 서비스를 무시하도록 설계되었기 때문입니다.

**Get-CsWindowsService** cmdlet이 Lync Server가 아닌 서비스를 자동으로 필터링한다는 사실은 Windows PowerShell과 함께 제공되는 일반 **Get-Service** cmdlet에 비해 이 cmdlet이 제공하는 하나의 장점입니다. 이와 함께 Lync Server 서비스에 대한 정보를 검색해야 하는 경우 **Get-CsWindowsService** cmdlet을 사용하는 다른 중요한 이유가 있습니다. **Get-CsWindowsService** cmdlet은 **Get-Service** cmdlet이 반환하지 않는 유용한 데이터를 반환합니다. 예를 들어 Lync Server 전화 회의 길잡이 서비스에 대한 정보를 반환할 때 **Get-CsWindowsService** cmdlet은 서비스(서비스 활동 수준)에서 처리되는 동시 통화 수를 다시 보고합니다. 그러나 **Get-Service** cmdlet은 해당 데이터를 보고하지 않습니다.

기본적으로 **Get-CsWindowsService** cmdlet은 로컬 컴퓨터에 대해 실행됩니다. 그러나 ComputerName 매개 변수를 포함하면 원격 컴퓨터에서 실행되는 Lync Server 서비스에 대한 정보를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsWindowsService** cmdlet을 로컬로 실행할 수 있습니다. 또한 이 cmdlet을 실행하려면 대상 컴퓨터에서 Performance Monitor Users 그룹의 구성원이어야 합니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsWindowsService"}

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
<td><p><em>ComputerName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>서비스 정보를 검색할 대상 원격 컴퓨터의 이름입니다. 이 매개 변수를 포함하지 않으면 <strong>Get-CsWindowsService</strong> cmdlet이 로컬 컴퓨터에서 실행되는 Lync Server 서비스에 대한 정보를 반환합니다. 원격 컴퓨터는 FQDN(정규화된 도메인 이름)(예: atl-mcs-001.litwareinc.com)을 사용하여 참조해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExcludeActivityLevel</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 포함하면 <strong>Get-CsWindowsService</strong> cmdlet이 서비스 작업 수준이 아니라 서비스 상태만 반환하게 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>정보를 가져올 서비스의 이름입니다. 서비스 표시 이름이 아니라 서비스 이름(예: RTCCAA)을 사용해야 합니다. Name 매개 변수에 단일 서비스 이름만 전달할 수 있습니다. 또한 서비스 이름에 와일드카드를 사용할 수 없습니다.</p>
<p><strong>Get-CsWindowsService</strong> cmdlet은 Lync Server 서비스에 대한 정보만 반환할 수 있습니다. 이 cmdlet을 사용하여 다른 Windows 서비스에 대한 정보를 반환할 수 없습니다. 이러한 서비스의 경우 Windows PowerShell  <strong>Get-Service</strong> cmdlet을 사용할 수 있습니다.</p>
<p>이 매개 변수를 포함하지 않으면 <strong>Get-CsWindowsService</strong> cmdlet이 모든 Lync Server 서비스에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>오류 정보를 저장할 수 있는 HTML 파일의 경로입니다. 이 매개 변수가 포함된 경우 이 cmdlet 실행 중에 발생하는 모든 오류는 지정된 파일(예: C:\Logs\Service_report.html)에 기록됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsWindowsService** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsWindowsService** cmdlet은 Microsoft.Rtc.Management.Deployment.Core.NTService 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Start-CsWindowsService](start-cswindowsservice.md)  
[Stop-CsWindowsService](stop-cswindowsservice.md)

