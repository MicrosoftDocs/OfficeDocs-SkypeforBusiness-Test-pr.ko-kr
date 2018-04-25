---
title: Search-CsClsLogging
TOCTitle: Search-CsClsLogging
ms:assetid: a2eddada-a494-4bc6-b7d0-9b511dfc4ac1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ619189(v=OCS.15)
ms:contentKeyID: 49304597
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Search-CsClsLogging

 

_**마지막으로 수정된 항목:** 2015-03-09_

중앙 로깅 서비스 로그 파일 검색에 필요한 명령줄 옵션을 제공합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Search-CsClsLogging [-AsXml <SwitchParameter>] [-CallId <String>] [-Components <String[]>] [-Computers <String[]>] [-ConferenceId <String>] [-CorrelationIds <String[]>] [-EndTime <DateTime>] [-IP <IPAddress>] [-LogLevel <String>] [-MatchAll <SwitchParameter>] [-MatchAny <SwitchParameter>] [-OutputFilePath <String>] [-Phone <String>] [-Pools <String[]>] [-SipContents <String>] [-SkipNetworkLogs <SwitchParameter>] [-StartTime <DateTime>] [-Uri <String>]

## 예제

## 예제 1

예제 1의 명령은 컴퓨터 atl-cs-001.litwareinc.com에 있는 로그 파일에서 IP 주소 192.168.0.242를 검색합니다.

    Search-CsClsLogging -Computers "atl-cs-001.litwareinc.com" -IP "192.168.0.242"

## 예제 2

예제 2에서는 IP 주소 192.168.0.242 및 URI sip:kenmyer@litwareinc.com이 모두 일치하는 항목을 검색합니다. MatchAll 매개 변수는 모든 조건이 일치할 때만 해당 항목을 일치로 기록하도록 지정합니다.

    Search-CsClsLogging -Computers "atl-cs-001.litwareinc.com" -IP "192.168.0.242" -Uri "sip:kenmyer@litwareinc.com" -MatchAll

## 예제 3

예제 3의 명령은 IP 주소 192.168.0.242 또는 URI sip:kenmyer@litwareinc.com 중 하나가 일치하는 항목을 검색합니다. MatchAny 매개 변수는 기준 중 하나만 만족해도 해당 항목을 일치로 기록하도록 지정합니다.

    Search-CsClsLogging -Computers "atl-cs-001.litwareinc.com" -IP "192.168.0.242" -Uri "sip:kenmyer@litwareinc.com" -MatchAny

## 자세한 정보

중앙 로깅 서비스( Microsoft Lync Server 2010에서 사용하는 OCSLogger 및 OCSTracer 도구를 대체함)는 관리자가 Lync Server 2013을 실행하는 모든 컴퓨터와 풀에 대한 로깅 및 추적을 관리할 수 있게 해 줍니다. 중앙 로깅을 사용하면 관리자가 단일 명령을 사용하여 하나 이상의 풀 및 컴퓨터에 대해 로깅을 시작, 중지 및 구성할 수 있습니다. 예를 들어 명령 하나를 사용하여 모든 주소록 서버에서 주소록 서비스 로깅을 사용하도록 설정할 수 있습니다. 이는 서버마다 개별적으로 관리해야 하는(개별적으로 시작하고 중지하는 것도 포함) OCSLogger 및 OCSTracer 도구와 다릅니다. 또한 중앙 로깅 서비스에서는 관리자가 Windows PowerShell 명령줄 인터페이스 및 [Search-CsClsLogging](search-csclslogging.md) cmdlet을 사용하여 명령에서 추적 로그를 검색하는 방법도 있습니다.

중앙 로깅은 이전 버전의 Lync Server에서 제공되었던 것보다 대상이 상세하게 지정된 로깅 방식을 제공하는 미리 정의된 일련의 시나리오를 기반으로 작성되었습니다. 이러한 시나리오에 따라 서버 구성 요소 및 로깅이 자동으로 미리 결정되므로 RGS 시나리오를 사용하도록 설정하는 관리자는 오디오 회의 공급자 서비스가 아닌 응답 그룹 서비스와 관련된 정보만 기록할 수 있습니다.

**Search-CsClsLogging** cmdlet은 중앙 로깅 서비스로 생성된 로그 파일을 검색하기 위한 명령줄 옵션을 제공합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Search-CsClsLogging"}

**Lync Server 제어판:** **Search-CsClsLogging** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>AsXml</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 검색된 각 컴퓨터의 반환 코드 정보가 문자열 값이 아닌 XML 형식으로 반환됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CallId</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>검색할 호출 식별자입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Components</em></p></td>
<td><p>선택</p></td>
<td><p>System.String[]</p></td>
<td><p>쉼표로 구분된, 검색할 구성 요소 목록입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Computers</em></p></td>
<td><p>선택</p></td>
<td><p>System.String[]</p></td>
<td><p>쉼표로 구분된, 검색할 컴퓨터 목록입니다. 예를 들면 다음과 같습니다.</p>
<p>-Computers &quot;server-cs-001.litwareinc.com&quot;, &quot;server-cs-002.litwareinc.com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>ConferenceId</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>검색할 회의 ID입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CorrelationIds</em></p></td>
<td><p>선택</p></td>
<td><p>System.String[]</p></td>
<td><p>쉼표로 구분된, 검색할 상관 관계 ID 목록입니다. 상관 관계는 각 요청과 연관된 32비트 정수입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EndTime</em></p></td>
<td><p>선택</p></td>
<td><p>System.DateTime</p></td>
<td><p>로그 항목 검색 종료 날짜 및 시간입니다. 현지 표준 시간대로 지정됩니다. StartTime을 지정하지 않으면 현재 시간 5분 후로 기본 설정되며 그렇지 않으면 StartTime 30분 후로 기본 설정됩니다. 예를 들어 Lync Server 2013 버전을 실행하는 컴퓨터에서 다음 구문은 검색을 2012년 8월 31일 오전 8시 이전에 기록된 항목까지로 제한합니다.</p>
<p>-StartTime &quot;8/31/2012 8:00AM&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>IP</em></p></td>
<td><p>선택</p></td>
<td><p>System.Net.IPAddress</p></td>
<td><p>검색할 IP 주소입니다. 이는 실제 IP 주소여야 합니다. IP 주소를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LogLevel</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>반환할 로그 항목의 최소 유형을 지정합니다. 허용되는 값은 다음과 같습니다.</p>
<p>* Fatal</p>
<p>* Error</p>
<p>* Warning</p>
<p>* Info</p>
<p>* Verbose</p>
<p>* Debug</p>
<p>* All</p>
<p>&quot;반환할 항목의 최소 유형&quot;이란 <strong>Search-CsClsLogging</strong> cmdlet이 해당 심각도 수준의 모든 로그 항목과 그보다 높은 수준의 모든 로그 항목을 반환한다는 의미입니다. 예를 들어 LogLevel을 Warning으로 설정하면 이 cmdlet은 Warning으로 표시된 항목 외에 Fatal 및 Error로 표시된 항목까지 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MatchAll</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 사용할 경우 포함된 모든 기준을 만족해야 합니다. 이는 SQL Server의 AND 쿼리와 유사합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MatchAny</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 사용할 경우 포함된 기준 중 하나만 만족하면 됩니다. 이는 SQL Server의 OR 쿼리와 유사합니다. 기본값입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OutputFilePath</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수가 있으면 검색 결과를 포함하는 텍스트 파일이 작성될 위치의 전체 경로가 지정됩니다. 그렇지 않으면 콘솔에 작성됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Phone</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>검색할 전화 번호입니다. 이 전화 번호는 E.164 형식을 사용하여 입력해야 하며, 여기에 와일드카드 문자를 사용해서는 안 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Pools</em></p></td>
<td><p>선택</p></td>
<td><p>System.String[]</p></td>
<td><p>쉼표로 구분된, 검색할 풀 목록입니다. 예를 들면 다음과 같습니다.</p>
<p>-Pools &quot;atl-cs-001.litwareinc.com&quot;, &quot;red-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>SipContents</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>SIP 메시지 본문 내에서 검색할 임의의 텍스트입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SkipNetworkLogs</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 사용할 경우 <strong>Search-CsClsLogging</strong> cmdlet이 네트워크 로그 검색을 생략합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>StartTime</em></p></td>
<td><p>선택</p></td>
<td><p>System.DateTime</p></td>
<td><p>로그 항목 검색 시작 날짜 및 시간입니다. 현지 표준 시간대로 지정됩니다. EndTime 30분 전으로 기본 설정됩니다. 예를 들어 Lync Server 2013 버전을 실행하는 컴퓨터에서 다음 구문은 검색을 2012년 8월 1일 오전 8시부터 기록된 항목까지로 제한합니다.</p>
<p>-StartTime &quot;8/1/2012 8:00AM&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Uri</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>검색할 URI입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Search-CsClsLogging** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

문자열 값 또는 XML

## 참고 항목

#### 기타 리소스

[Show-CsClsLogging](show-csclslogging.md)  
[Start-CsClsLogging](start-csclslogging.md)  
[Stop-CsClsLogging](stop-csclslogging.md)  
[Sync-CsClsLogging](sync-csclslogging.md)  
[Update-CsClsLogging](update-csclslogging.md)

