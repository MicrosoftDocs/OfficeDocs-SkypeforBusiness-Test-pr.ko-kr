---
title: Get-CsReportingConfiguration
TOCTitle: Get-CsReportingConfiguration
ms:assetid: e777a154-354a-49da-8140-79f80416bc49
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205356(v=OCS.15)
ms:contentKeyID: 49305362
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsReportingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용 중인 보고 구성 설정에 대한 정보를 반환합니다. 보고 구성 설정은 Lync Server 2013 모니터링 보고서에 액세스하는 데 사용되는 URL을 지정하는 데 사용됩니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsReportingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsReportingConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 현재 사용 중인 모든 보고 구성 설정에 대한 정보를 반환합니다.

    Get-CsReportingConfiguration

## 예제 2

예제 2에서는 단일 보고 구성 설정 컬렉션, 즉 ID가 "Service:MonitoringDatabase:atl-sql-001.litwareinc.com"인 설정에 대한 정보를 반환합니다.

    Get-CsReportingConfiguration -Identity "Service:MonitoringDatabase:atl-sql-001.litwareinc.com"

## 예제 3

예제 3에서는 ID가 ".litwareinc.com"으로 끝나는 모든 보고 구성 설정에 대한 정보를 반환합니다. 이를 위해 명령은 Filter 매개 변수 및 필터 값 "\*.litwareinc.com"을 사용합니다.

    Get-CsReportingConfiguration -Filter "*.litwareinc.com"

## 예제 4

예제 4에서는 보고 URL에 문자열 값 "\_ARCHINST"를 포함하는 모든 보고 구성 설정에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsReportingConfiguration** cmdlet을 사용하여 현재 사용 중인 모든 보고 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프되며, 해당 cmdlet은 ReportingUrl에 문자열 값 "\_ARCHINST"가 포함된(-like) 설정만 선택합니다.

    Get-CsReportingConfiguration | Where-Object {$_.ReportingUrl -like "*_ARCHINST*"}

## 자세한 정보

보고 구성 설정은 Lync Server 모니터링 보고서의 홈 페이지를 지정하는 데 사용됩니다. 모니터링 보고서를 사용하지 않는 경우에는 보고 구성 설정을 수정할 필요가 없습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsReportingConfiguration

**Lync Server 제어판:** **Get-CsReportingConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>반환할 보고 구성 설정을 지정할 때 와일드카드 문자를 사용할 수 있습니다. 예를 들어 다음 구문은 서비스 범위에서 구성된 모든 설정을 반환합니다.</p>
<p>-Filter &quot;service:*&quot;</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>보고 구성 설정과 연결된 모니터링 데이터베이스의 서비스 ID입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;Service:MonitoringDatabase:atl-sql-001.litwareinc.com&quot;</p>
<p>명령에 Identity 매개 변수 또는 Filter 매개 변수를 포함하지 않으면 <strong>Get-CsReportingConfiguration</strong> cmdlet은 조직에서 사용 중인 모든 보고 구성 설정을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 보고 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsReportingConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsReportingConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Reporting.ReportingConfiguration 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsReportingConfiguration](new-csreportingconfiguration.md)  
[Remove-CsReportingConfiguration](remove-csreportingconfiguration.md)  
[Set-CsReportingConfiguration](set-csreportingconfiguration.md)

