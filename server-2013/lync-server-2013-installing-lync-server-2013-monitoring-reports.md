---
title: Lync Server 2013 모니터링 보고서 설치
TOCTitle: Lync Server 2013 모니터링 보고서 설치
ms:assetid: 6f417569-b100-442c-ad48-fdd794626cf7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204989(v=OCS.15)
ms:contentKeyID: 49303981
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 모니터링 보고서 설치

 

_**마지막으로 수정된 항목:** 2015-03-09_

Microsoft Lync Server 2013 모니터링 보고서는 조직에서 발생하는 통신 세션의 품질 및 수량에 대한 다양한 정보를 제공합니다. 하지만 모니터링 보고서는 Lync Server 2013을 설치할 때 자동으로 설치되지 않습니다. 대신 모니터링 보고서는 Lync Server를 컴퓨터에 설치한 후에만 별도로 설치해야 합니다.


> [!NOTE]
> 모니터링 보고서는 모니터링 데이터베이스가 설치된 동일 컴퓨터에 설치하는 것이 좋습니다. 그러면 보고서 액세스를 위한 권한 지정 프로세스를 간소화할 수 있습니다. 모니터링 저장소를 호스팅하는 컴퓨터에 모니터링 보고서를 설치하면 한 컴퓨터의 데이터베이스가 다른 컴퓨터에서 실행되는 Reporting Services와 상호 작용하도록 허용하는 권한을 구성할 필요가 없습니다.



Lync Server 모니터링 보고서에는 회의, 피어 투 피어 IM 세션, 사용자 등록, 응답 그룹 응용 프로그램 등에 대한 자세한 정보를 제공할 수 있도록 디자인된 30개 이상의 보고서가 포함되어 있습니다. 2013 버전의 경우 Lync Server 모니터링 보고서에는 다양한 향상된 기능이 포함됩니다.

  - **새로운 음성 품질 보고서**. 이러한 새 보고서에는 서로 다른 유형의 통화(예: 유선 통화와 무선 통화) 간 품질을 비교하는 [Lync Server 2013의 미디어 품질 비교 보고서](lync-server-2013-media-quality-comparison-report.md) 및 사용자가 회의에 참가하는 데 필요한 시간과 관련된 정보를 제공하는 [회의 참가 시간 보고서](lync-server-2013-conference-join-time-report.md)가 포함됩니다.

  - **비디오 및 응용 프로그램 공유 세션을 모두 분석하고 문제 해결하기 위한 향상된 보고서.** [Lync Server 2013의 미디어 품질 요약 보고서](lync-server-2013-media-quality-summary-report.md)는 비디오 및 응용 프로그램 공유 통화를 분석하기 위한 방법을 제공하고, [Lync Server 2013의 서버 성능 보고서](lync-server-2013-server-performance-report.md)는 이러한 통화를 생성하는 서버의 성능을 자세히 보여줍니다. 비디오 및 응용 프로그램 공유 메트릭도 이제는 [Lync Server 2013의 피어 투 피어 세션 정보 보고서](lync-server-2013-peer-to-peer-session-detail-report.md) 및 [전화 회의 정보 보고서](lync-server-2013-conference-detail-report.md)에서 보고됩니다.

  - **향상된 보고서 성능**. 여기에는 빠르고 간편한 보고서 탐색뿐만 아니라 신속한 응답 및 데이터 검색 시간이 포함됩니다.

개별 보고서에 대한 자세한 내용은 모니터링 보고서 설명서에서 찾을 수 있습니다.


> [!NOTE]
> Lync Server 2013에는 QoE 통화 정보 하위 보고서라는 새로운 보고서도 포함되어 있습니다. 하지만 이 보고서는 주로 내부용으로만 사용되며, 직접 액세스할 수 없습니다.



Lync Server 모니터링 보고서를 설치하는 방법은 두 가지입니다. Lync Server 배포 마법사를 사용하거나 Lync Server 2013 설치 파일에 포함된 Windows PowerShell 스크립트를 사용할 수 있습니다. 보고서 설치를 위해 사용하는 방법에 관계없이 먼저 다음과 같은 사항을 확인해야 합니다.

  - 모니터링 데이터베이스의 사용자 계정에 데이터베이스 역할을 추가할 수 있는 권한이 있어야 합니다.

  - SQL Server Reporting Services에 대해 콘텐츠 관리자 역할을 보유해야 합니다. 이 역할은 보고서를 SQL Server Reporting Services에 배포할 수 있는 권한을 부여합니다.

배포 마법사를 사용하여 모니터링 보고서를 설치하려면 다음 단계를 완료합니다.

1.  **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 배포 마법사**를 클릭합니다.

2.  배포 마법사에서 **모니터링 보고서 배포**를 클릭하여 모니터링 보고서 배포 마법사를 시작합니다.

3.  모니터링 보고서 배포 마법사의 **모니터링 데이터베이스 지정** 페이지에서 모니터링 저장소를 호스팅하는 컴퓨터의 정규화된 도메인 이름이 **모니터링 데이터베이스** 드롭다운 목록에 표시되는지 확인합니다. 모니터링 저장소가 여러 개 있는 경우 드롭다운 목록에서 적합한 서버를 선택해야 합니다. 올바른 SQL Server 인스턴스가 **SSRS(SQL Server Reporting Services) 인스턴스** 상자(예: **atl-sql-001.litwareinc.com/archinst**)에 표시되는지 확인한 후 **다음**을 클릭합니다.

4.  **자격 증명 지정** 페이지의 **사용자 이름** 상자에 모니터링 보고서에 액세스할 때 사용할 계정의 도메인 이름 및 사용자 이름을 입력합니다(예: **litwareinc\\kenmyer**). 이 형식(도메인\\사용자 이름)을 사용하지 않을 경우 오류가 발생합니다.
    
    **암호** 상자에 사용자 계정 암호를 입력하고 **다음**을 클릭합니다. 이 계정에는 특수한 권한이 필요하지 않습니다. 설치가 완료되면 계정에 필요한 로그온 및 데이터베이스 권한이 자동으로 부여됩니다.

5.  **읽기 전용 그룹 지정** 페이지에서 사용자 그룹 상자에 SQL Server Reporting Services에 대한 읽기 전용 액세스 권한을 부여할 보안 그룹의 이름을 입력합니다. 예를 들어 보고서에 읽기 전용 관리자 액세스 권한을 부여하려면 **RTCUniversalReadOnlyAdmins**를 입력합니다. **다음**을 클릭합니다.

6.  **명령 실행** 페이지에서 **마침**을 클릭합니다.

모니터링 보고서는 script DeployReports.ps1을 실행하여 Lync Server 관리 셸에서 설치할 수도 있습니다. 이 Windows PowerShell 스크립트는 \\Setup\\ReportingSetup 폴더의 Lync Server 설치 미디어에서 찾을 수 있습니다. DeployReports.ps1을 사용하여 모니터링 보고서를 설치하려면 관리 셸 프롬프트에 다음과 비슷한 명령을 입력합니다.

    D:\Setup\AMD64\Setp\ReportingSetup\DeployReports.ps1 -storedUserName "litwareinc\kenmyer" -storedPassword "p@ssw0rd" -readOnlyGroupName "RTCUniversalReadOnlyAdmins" -reportServerSqlInstance "atl-sql-001.litwareinc.com" -monitoringDatabaseId "MonitoringDatabase:atl-sql-001.litwareinc.com"

위 명령에 사용된 매개 변수는 다음 표에서 설명합니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>매개 변수 이름</th>
<th>필수</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>storedUserName</p></td>
<td><p>예</p></td>
<td><p>모니터링 저장소에 액세스하는 데 사용되는 사용자 계정입니다(domain\username 형식). 예:</p>
<pre><code>-storedUserName &quot;litwareinc\kenmyer&quot;</code></pre>
<p>이 계정은 이전에 지정된 SQL Server 및 SQL Server Reporting Services 권한이 있어야 하며, 그렇지 않으면 스크립트가 실패합니다.</p></td>
</tr>
<tr class="even">
<td><p>storedPassword</p></td>
<td><p>예</p></td>
<td><p>모니터링 저장소에 액세스하는 데 사용되는 사용자 계정의 암호입니다.</p></td>
</tr>
<tr class="odd">
<td><p>readOnlyGroupName</p></td>
<td><p>아니요</p></td>
<td><p>모니터링 보고서에 대한 읽기 전용 액세스 권한을 부여할 구성원의 도메인 또는 로컬 보안 그룹입니다. 지정된 그룹이 없으면 스크립트가 실패합니다. 나중에 이러한 권한을 취소하려는 경우 또는 다른 사용자 또는 다른 그룹에 액세스 권한을 부여하려는 경우 SQL Service Reporting Services 보고서 관리자를 사용해서 작업을 수행할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p>reportSqlServerInstance</p></td>
<td><p>아니요</p></td>
<td><p>Reporting Services를 호스팅하는 SQL Server 인스턴스입니다. 보고 인스턴스는 보고서 서버의 정규화된 도메인 이름을 사용하여 지정해야 합니다. 예:</p>
<pre><code>-reportServerSqlInstance atl-sql-001.litwareinc.com</code></pre>
<p>이 매개 변수를 포함하지 않을 경우 스크립트는 모니터링 데이터베이스를 호스팅하는 동일한 SQL Server 인스턴스에서 Reporting Services를 호스팅하는 것으로 가정합니다.</p></td>
</tr>
<tr class="odd">
<td><p>monitoringDatabaseId</p></td>
<td><p>아니요</p></td>
<td><p>모니터링 데이터베이스에 대한 서비스 ID입니다. 다음 명령을 실행하여 모니터링 데이터베이스에 대한 ID를 반환할 수 있습니다.</p>
<pre><code>Get-CsService -MonitoringDatabase</code></pre></td>
</tr>
</tbody>
</table>


모니터링 보고서를 설치한 후에는 Set-CsReportingConfiguration cmdlet을 사용해서 이러한 보고서에 액세스하는 데 사용되는 URL을 구성해야 합니다. 이 작업은 다음 Windows PowerShell 명령을 실행하여 Lync Server 관리 셸에서 수행할 수 있습니다. 보고 URL을 구성할 때 HTTPS 프로토콜 사용은 권장 사항이며 필수 항목이 아닙니다.

    Set-CsReportingConfiguration -Identity "MonitoringDatabase:atl-sql-001.litwareinc.com" -ReportingURL "https://atl-sql-001.litwareinc.com:443/Reports_ARCHINST"

위 명령에서 ReportingUrl 속성은 SQL Server 2008 R2 Reporting Services에서 사용되는 보고서 관리자 URL로 설정되어야 합니다. 보고서 관리자 URL은 SQL Server Reporting Services가 설치된 컴퓨터에서 다음 단계를 완료하여 확인할 수 있습니다.

1.  시작, 모든 프로그램, Microsoft SQL Server 2008 R2, 구성 도구를 차례로 클릭한 후 Reporting Services 구성 관리자를 클릭합니다.

2.  Reporting Services 구성 연결 대화 상자에서 Reporting Services 컴퓨터 이름이 서버 이름 상자에 표시되는지 확인합니다. 보고서 서버 인스턴스 드롭다운 목록에서 SQL Server 인스턴스를 선택한 후 연결을 클릭합니다.

3.  Reporting Services 구성 관리자에서 보고서 관리자 URL을 클릭합니다. 하나 이상의 URL이 보고서 관리자 URL 창에 표시됩니다. 이러한 URL은 모두 보고 URL로 사용할 수 있습니다. ReportingUrl에는 HTTPS 프로토콜을 사용하는 것이 좋습니다.

모니터링 데이터베이스에 대해 미러 데이터베이스를 설정한 경우 모니터링 보고서도 미러 데이터베이스에 연결해야 합니다. 자세한 내용은 [모니터링 보고서와 미러 데이터베이스 연결](lync-server-2013-associating-monitoring-reports-with-a-mirror-database.md) 문서를 참고하세요.

