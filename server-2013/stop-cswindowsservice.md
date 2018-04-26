---
title: Stop-CsWindowsService
TOCTitle: Stop-CsWindowsService
ms:assetid: 60318b9f-2291-4b99-a271-d206e4074b70
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398426(v=OCS.15)
ms:contentKeyID: 49303794
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Stop-CsWindowsService

 

_**마지막으로 수정된 항목:** 2015-03-09_

**Stop-CsWindowsService**를 사용하여 Lync Server 서비스를 중지할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Stop-CsWindowsService [-ComputerName <String>] [-Name <String>] <COMMON PARAMETERS>

    Stop-CsWindowsService [-InputObject <NTService>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Graceful <SwitchParameter>] [-LeaveClsAgentRunning <SwitchParameter>] [-LeaveWebServerRunning <SwitchParameter>] [-NoWait <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 로컬 컴퓨터의 응답 그룹 응용 프로그램 서비스를 중지합니다. 응답 그룹 응용 프로그램 서비스는 Name 매개 변수 및 해당 서비스 이름 RTCRGS를 포함하여 식별됩니다.

    Stop-CsWindowsService -Name "RTCRGS"

## 예제 2

예제 2도 응답 그룹 응용 프로그램 서비스를 중지합니다. 그러나 이 예제에서는 해당 서비스가 원격 컴퓨터 atl-cs-001.litwareinc.com에 있습니다. 원격 컴퓨터의 서비스를 중지하려면 ComputerName 매개 변수 뒤에 원격 컴퓨터의 FQDN을 포함합니다.

    Stop-CsWindowsService -Name "RTCRGS" -ComputerName atl-cs-001.litwareinc.com

## 예제 3

예제 3에서는 서비스 이름(이 경우 RTCCPS)을 모르는 경우에도 서비스를 중지할 수 있는 방법을 보여 줍니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsWindowsService** cmdlet을 매개 변수 없이 호출하여 로컬 컴퓨터에 있는 모든 Lync Server 서비스의 컬렉션을 반환합니다. 그런 다음 이 컬렉션 전체가 DisplayName 속성에 "Call Park" 문자열이 포함된 서비스만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그리고 필터링된 컬렉션이 통화 대기 응용 프로그램 서비스를 중지하는 **Stop-CsWindowsService** cmdlet에 파이프됩니다.

    Get-CsWindowsService | Where-Object {$_.DisplayName -like "*Call Park*"} | Stop-CsWindowsService

## 자세한 정보

많은 Lync Server 구성 요소가 표준 Windows 서비스로 실행됩니다. 예를 들어 회의 길잡이 응용 프로그램은 실제로 RTCCAA라는 서비스입니다. Lync Server를 중지하려면 **Stop-CsWindowsService** cmdlet을 사용하면 됩니다.

**Stop-CsWindowsService** cmdlet은 Lync Server 서비스만 중지할 수 있습니다. 이 cmdlet을 사용하여 Lync Server 이외의 서비스(예: 인쇄 스풀러)를 중지하려고 하면 오류가 발생합니다.

기능 면에서 **Stop-CsWindowsService** cmdlet은 일반적인 Windows PowerShell**Stop-Service** cmdlet과 상당히 비슷합니다. 원하는 경우 **Stop-Service** cmdlet을 사용하여 Lync Server 서비스를 중지할 수 있습니다. 그러나 **Stop-CsWindowsService** cmdlet에는 원격 컴퓨터의 서비스를 쉽게 중지할 수 있는 ComputerName 매개 변수가 포함되어 있습니다. ComputerName 매개 변수를 넣고 그 뒤에 원격 컴퓨터의 FQDN(정규화된 도메인 이름)을 입력하기만 하면 됩니다. **Stop-Service** cmdlet에는 비교 가능한 매개 변수가 없습니다. 또한 **Stop-CsWindowsService** cmdlet에는 해당 cmdlet을 호출할 때 발생할 수 있는 모든 오류를 기록하는 데 사용되는 Report 매개 변수가 있습니다.

**Stop-CsWindowsService** cmdlet은 이름으로 알 수 있듯이 사용자가 중지하도록 요청한 모든 서비스를 중지합니다. 여기에는 사용자가 중지하려는 서비스가 실행 중인 경우에만 실행할 수 있는 서비스인 종속 서비스가 포함됩니다. 기본적으로 종속 서비스가 있는 서비스를 중지하려고 하면 **Stop-CsWindowsService** cmdlet이 해당 서비스뿐만 아니라 모든 종속 서비스까지도 중지하게 됩니다. 이는 예기치 않은 결과를 가져올 수 있으므로 **Stop-CsWindowsService** cmdlet을 호출할 때는 Graceful 매개 변수를 포함해야 합니다. Graceful 매개 변수를 포함하면 **Stop-CsWindowsService** cmdlet이 새 요청 수신 서비스를 차단합니다. 기존 서비스 요청은 모두 그대로 유지되고 새 요청만 거부됩니다. 기존 요청이 완료되면 이러한 요청이 대체되지 않습니다. 결국 기존 요청이 모두 채워진 다음 서비스가 종료됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Stop-CsWindowsService** cmdlet을 로컬로 실행할 수 있습니다. 또한 이 cmdlet을 실행하려면 대상 컴퓨터에 대한 로컬 관리자 권한이 있어야 합니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Stop-CsWindowsService"}

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
<td><p>중지할 서비스를 실행 중인 원격 컴퓨터의 이름입니다. 이 매개 변수가 포함되지 않은 경우 <strong>Stop-CsWindowsService</strong> cmdlet이 로컬 컴퓨터의 지정된 서비스를 중지하게 됩니다. 원격 컴퓨터는 FQDN(예: atl-mcs-001.litwareinc.com)을 사용하여 참조해야 합니다.</p></td>
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
<td><p><em>Graceful</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>서비스를 즉시 종료하지 않고 기존 서비스 요청이 모두 채워질 때까지 기다립니다. 그러나 새 서비스 요청은 모두 거부됩니다. 기존 요청이 모두 채워져야 서비스가 완전히 종료됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InputObject</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.Core.NTService</p></td>
<td><p>서비스 이름이 아닌 개체 참조를 사용하여 서비스를 중지할 수 있습니다. 예를 들어 <strong>Get-CsWindowsService</strong> cmdlet을 사용하여 서비스에 대한 정보를 반환하는 경우 및 반환된 개체를 $x라는 변수에 저장하는 경우</p>
<p>$x = Get-CsWindowsService –Name &quot;RTCCPS&quot;</p>
<p>Stop-CsWindowsService -InputObject $x.Name 명령을 사용하여 서비스를 중지할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LeaveClsAgentRunning</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 중앙 로깅 에이전트 서비스를 제외한 모든 Lync Server 서비스가 중지됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LeaveWebServerRunning</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 지정한 컴퓨터에서 웹 서버 서비스 외의 모든 서비스를 종료합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>중지하려는 Lync Server 서비스의 이름입니다. 서비스 표시 이름이 아니라 서비스 이름(예: RTCCAA)을 사용해야 합니다. Name 매개 변수에는 단일 서비스 이름만 전달할 수 있으며 서비스 이름에는 와일드카드를 사용할 수 없습니다. <strong>Get-CsWindowsService</strong> cmdlet을 사용하여 서비스 이름을 검색할 수 있습니다.</p>
<p><strong>Stop-CsWindowsService</strong> cmdlet은 Lync Server 서비스만 중지할 수 있으므로 이 cmdlet을 사용하여 다른 Windows 서비스를 중지할 수는 없습니다. 이러한 서비스의 경우 Windows PowerShell <strong>Stop-Service</strong> cmdlet을 사용할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NoWait</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>있는 경우 명령이 실행된 다음 즉시 Windows PowerShell 프롬프트로 제어가 반환됩니다. 없는 경우 명령이 완료되고 상태 보고서가 화면에 기록될 때까지 제어권이 반환되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>오류 정보를 기록할 수 있는 HTML 파일의 경로입니다. 이 매개 변수가 포함된 경우 이 cmdlet 실행 중에 발생하는 모든 오류는 지정된 파일(예: C:\Logs\Service_report.html)에 기록됩니다.</p></td>
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

Microsoft.Rtc.Management.Deployment.Core.NTService 개체입니다. **Stop-CsWindowsService** cmdlet은 Windows 서비스 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Stop-CsWindowsService** cmdlet은 Microsoft.Rtc.Management.Deployment.Core.NTService 개체의 인스턴스를 중지합니다.

## 참고 항목

#### 기타 리소스

[Get-CsWindowsService](get-cswindowsservice.md)  
[Start-CsWindowsService](start-cswindowsservice.md)

