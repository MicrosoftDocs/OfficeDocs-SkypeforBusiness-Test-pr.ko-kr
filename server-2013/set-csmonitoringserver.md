---
title: Set-CsMonitoringServer
TOCTitle: Set-CsMonitoringServer
ms:assetid: 2c6d6660-7e41-4c56-9e04-27c3d1ea3b95
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425776(v=OCS.15)
ms:contentKeyID: 49303158
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsMonitoringServer

 

_**마지막으로 수정된 항목:** 2015-03-09_

모니터링 서버 데이터베이스 및 보고 팩에 대한 새 위치를 구성할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsMonitoringServer [-Identity <XdsGlobalRelativeIdentity>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-MonitoringDatabase <String>] [-ReportingUrl <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 모니터링 서버 보고서 팩의 새 URL을 구성합니다.

    Set-CsMonitoringServer -Identity "MonitoringServer:atl-cs-001.litwareinc.com" -ReportingUrl "https://atl-cs-001.litwareinc.com/reports"

## 자세한 정보

모니터링 서버는 두 가지 중요한 기능을 제공합니다. 첫째, 조직에서 Enterprise Voice가 사용되는 방식 및 빈도에 대한 정보를 유지 관리할 수 있습니다. 이 정보는 발신자, 발신자가 전화를 건 대상, 통화 지속 시간 등을 기록하는 CDR(통화 정보 기록)을 사용하여 추적됩니다. 실제 대화 자체는 기록되지 않습니다. 모니터링 서버를 사용하여 모니터링 서버 통화에 대한 QoE(체감 품질) 데이터를 추적할 수도 있습니다. 이름에서 알 수 있듯이 체감 품질 데이터는 패킷 손실, 통화 저하, 네트워크 비트 전송률, 지터 등의 항목을 측정하여 통화 품질에 대한 정보를 제공합니다.

모니터링 서버를 설치할 때 CDR 및 QoE 데이터를 저장하는 데 사용되는 SQL Server 데이터베이스의 위치를 지정해야 합니다. 필요에 따라 SQL Server Reporting Services 및 모니터링 서버 보고서 팩을 설치할 수도 있습니다. 두 항목을 통해 표준 모니터링 보고서를 생성하는 웹 사이트에 액세스할 수 있습니다.

일반적으로 모니터링 서버가 설치 및 구성된 후에는 백 엔드 데이터베이스의 위치나 보고 URL을 변경할 필요가 없습니다. 그러나 두 항목 중 하나(또는 둘 다)의 위치를 변경해야 하는 경우 **Set-CsMonitoringServer** cmdlet을 실행하여 변경할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsMonitoringServer** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsMonitoringServer"}

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>수정할 모니터링 서버의 서비스 위치입니다 예: -Identity &quot;MonitoringServer:atl-cs-001.litwareinc.com&quot;. 다음 명령을 사용하여 모든 모니터링 서버의 ID를 검색할 수 있습니다.</p>
<p>Get-CsService –MonitoringServer | Select-Object Identity</p>
<p>접두사 &quot;MonitoringServer:&quot;는 모니터링 서버를 지정할 때 생략할 수 있습니다(예: -Identity &quot;atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>MonitoringDatabase</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>새 모니터링 서버 데이터베이스의 서비스 위치입니다. 예: -MonitoringDatabase &quot;MonitoringDatabase:atl-sql-001.litwareinc.com&quot;. SQL Server 경로 이름이 아니라 데이터베이스 저장소의 서비스 위치를 사용해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ReportingUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>모니터링 서버 보고서의 URL입니다. SQL Server Reporting Services 및 모니터링 서버 보고서 팩을 설치하지 않으면 이러한 보고서를 사용할 수 없습니다.</p></td>
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

없음. **Set-CsMonitoringServer** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Set-CsMonitoringServer** cmdlet은 개체나 값을 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.Xds.DisplayMonitoringServer 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsService](get-csservice.md)

