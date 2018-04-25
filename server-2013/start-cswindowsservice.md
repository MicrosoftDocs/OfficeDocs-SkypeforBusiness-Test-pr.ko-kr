---
title: Start-CsWindowsService
TOCTitle: Start-CsWindowsService
ms:assetid: 7491b91f-d342-4f9a-878b-d20b35294a9c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398561(v=OCS.15)
ms:contentKeyID: 49304061
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Start-CsWindowsService

 

_**마지막으로 수정된 항목:** 2015-03-09_

**Start-CsWindowsService** cmdlet을 사용하면 Lync Server 서비스를 시작할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Start-CsWindowsService [-ComputerName <String>] [-Name <String>] <COMMON PARAMETERS>

    Start-CsWindowsService [-InputObject <NTService>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-NoWait <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 로컬 컴퓨터의 모든 Lync Server 서비스를 시작합니다. 이 작업은 **Start-CsWindowsService** cmdlet을 매개 변수 없이 호출하여 수행합니다. 이미 시작된 서비스를 시작하려고 시도할 경우 오류가 발생합니다.

    Start-CsWindowsService

## 예제 2

예제 2에서는 로컬 컴퓨터에서 응답 그룹 응용 프로그램 서비스를 시작합니다. 이 작업을 수행하기 위해 명령에 Name 매개 변수와 서비스 이름 RTCRGS가 사용됩니다.

    Start-CsWindowsService -Name "RTCRGS"

## 예제 3

예제 3의 명령도 응답 그룹 응용 프로그램 서비스를 시작합니다. 단, 이 경우 서비스가 원격 컴퓨터 atl-cs-001.litwareinc.com에서 시작됩니다. 원격 컴퓨터의 서비스를 시작하려면 ComputerName 매개 변수 뒤에 원격 컴퓨터의 FQDN을 포함합니다.

    Start-CsWindowsService -Name "RTCRGS" -ComputerName atl-cs-001.litwareinc.com

## 예제 4

예제 4의 명령은 로컬 컴퓨터에서 현재 실행 중이 아닌 모든 Lync Server 서비스를 검색한 다음 이러한 각 비활성 서비스를 시작합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsWindowsService** cmdlet을 호출하여 모든 Lync Server 서비스의 컬렉션을 반환합니다. 이 컬렉션은 Status 속성이 Running과 같지 않은 서비스만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이 필터링된 컬렉션은 컬렉션의 각 서비스를 시작하는 **Start-CsWindowsService** cmdlet에 파이프됩니다.

    Get-CsWindowsService | Where-Object {$_.Status -ne "Running"} | Start-CsWindowsService

## 자세한 정보

많은 Lync Server 구성 요소가 표준 Windows 서비스로 실행됩니다. 예를 들어 회의 길잡이 응용 프로그램은 실제로 RTCCAA라는 서비스입니다. Lync Server 서비스 중 하나가 현재 중지되어 있는 경우 **Start-CsWindowsService** cmdlet을 사용하여 다시 시작할 수 있습니다.

그러나 **Start-CsWindowsService** cmdlet은 Lync Server 서비스만 시작할 수 있습니다. 이 cmdlet을 사용하여 Lync Server 이외의 서비스(예: 인쇄 스풀러)를 시작하려고 하면 오류가 발생합니다.

기능 면에서 **Start-CsWindowsService** cmdlet은 일반적인 Windows PowerShell**Start-Service** cmdlet과 상당히 비슷합니다. 원하는 경우 **Start-Service** cmdlet을 사용하여 Lync Server 서비스를 시작할 수 있습니다. 반면 **Start-CsWindowsService** cmdlet에는 원격 컴퓨터의 서비스를 쉽게 시작할 수 있는 ComputerName 매개 변수가 포함되어 있습니다. ComputerName 매개 변수를 넣고 그 뒤에 원격 컴퓨터의 FQDN(정규화된 도메인 이름)을 입력하기만 하면 됩니다. **Start-Service** cmdlet에는 비교 가능한 매개 변수가 없습니다. 또한 cmdlet의 Report 매개 변수를 사용하면 **Start-CsWindowsService**를 호출할 때 발생하는 오류의 로그를 유지할 수 있습니다.

다른 Windows 서비스와 마찬가지로 일부 Lync Server 서비스는 다른 서비스에 종속됩니다. 예를 들어 Lync Server 전화 회의 길잡이 서비스는 응용 프로그램 서비스가 이미 실행되고 있어야 실행할 수 있습니다. 다른 서비스에 종속되는 서비스를 시작하려고 시도하면 **Start-CsWindowsService** cmdlet에서 해당되는 두 서비스를 모두 시작합니다. 즉, 전화 회의 길잡이 서비스를 시작하려고 하면 cmdlet은 먼저 응용 프로그램 서비스를 시작한 다음 전화 회의 길잡이 서비스를 시작합니다. 그러나 **Start-CsWindowsService** cmdlet은 서비스의 종속 서비스를 자동으로 시작하지 않습니다. 즉, 응용 프로그램 서비스를 시작한다고 해서 전화 회의 길잡이 서비스까지 자동으로 실행되지는 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Start-CsWindows** cmdlet을 로컬로 실행할 수 있습니다. 또한 이 cmdlet을 실행하려면 대상 컴퓨터에 대한 로컬 관리자 권한이 있어야 합니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Start-CsWindowsService"}

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
<td><p>시작할 서비스를 호스트하는 원격 컴퓨터의 이름입니다. 이 매개 변수가 포함되지 않으면 <strong>Start-CsWindowsService</strong> cmdlet은 로컬 컴퓨터에 지정된 서비스를 시작합니다. 원격 컴퓨터는 FQDN(예: atl-cs-001.litwareinc.com)을 사용하여 참조해야 합니다.</p></td>
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
<td><p><em>InputObject</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.Core.NTService</p></td>
<td><p>서비스 이름이 아닌 개체 참조를 사용하여 서비스를 시작할 수 있도록 합니다. 예를 들어 <strong>Get-CsWindowsService</strong> cmdlet을 사용하여 서비스에 대한 정보를 반환하거나 반환된 개체를 $x라는 변수에 저장하는 경우 다음 명령을 사용하여 서비스를 시작할 수 있습니다.</p>
<p>$x = Get-CsWindowsService -Name &quot;RTCCPS&quot;</p>
<p>Start-CsWindowsService -InputObject $x.Name</p></td>
</tr>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>시작하려는 Lync Server 서비스의 이름입니다. 서비스 표시 이름이 아니라 서비스 이름(예: RTCCAA)을 사용해야 합니다. Name 매개 변수에는 단일 서비스 이름만 전달할 수 있으며 서비스 이름에는 와일드카드를 사용할 수 없습니다. 서비스 이름은 <strong>Get-CsWindowsService</strong> cmdlet을 사용하여 검색할 수 있습니다.</p>
<p><strong>Start-CsWindowsService</strong> cmdlet은 Lync Server 서비스만 시작할 수 있으므로 이 cmdlet을 사용하여 다른 Windows 서비스를 시작할 수는 없습니다. 이러한 서비스의 경우 Windows PowerShell  <strong>Start-Service</strong> cmdlet을 사용할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NoWait</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>있는 경우 명령이 실행된 다음 즉시 Windows PowerShell 프롬프트로 제어가 반환됩니다. 없는 경우 명령이 완료되고 상태 보고서가 화면에 기록될 때까지 제어권이 반환되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>오류 정보를 저장할 수 있는 HTML 파일의 경로입니다. 이 매개 변수가 포함된 경우 이 cmdlet 실행 중에 발생하는 모든 오류는 지정된 파일(예: C:\Logs\Service_report.html)에 기록됩니다.</p></td>
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

Microsoft.Rtc.Management.Deployment.Core.NTService 개체입니다. **Start-CsWindowsService** cmdlet은 Windows 서비스 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Start-CsWindowsService** cmdlet은 Microsoft.Rtc.Management.Deployment.Core.NTService 개체의 인스턴스를 시작합니다.

## 참고 항목

#### 기타 리소스

[Get-CsWindowsService](get-cswindowsservice.md)  
[Stop-CsWindowsService](stop-cswindowsservice.md)

