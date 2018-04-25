---
title: Stop-CsClsLogging
TOCTitle: Stop-CsClsLogging
ms:assetid: 63d0f0d6-5eec-4a16-b834-37611c584f52
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ619180(v=OCS.15)
ms:contentKeyID: 49303842
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Stop-CsClsLogging

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 중앙 로깅 서비스 시나리오를 중지합니다. 중앙 로깅을 사용하면 관리자가 여러 컴퓨터에서 Lync Server 2013 추적을 동시에 활성화하거나 비활성화할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Stop-CsClsLogging -Scenario <String> [-AsXml <SwitchParameter>] [-Computers <String[]>] [-Pools <String[]>]

## 예제

## 예제 1

예제 1의 명령은 토폴로지의 모든 서버에서 CPS 로깅 시나리오를 중지합니다.

    Stop-CsClsLogging -Scenario "cps"

## 예제 2

예제 2에서는 풀 atl-cs-001.litwareinc.com의 모든 서버에서 CPS 로깅 시나리오가 중지됩니다.

    Stop-CsClsLogging -Scenario "cps" -Pools "atl-cs-001.litwareinc.com"

## 자세한 정보

중앙 로깅 서비스( Microsoft Lync Server 2010에서 사용하는 OCSLogger 및 OCSTracer 도구를 대체함)는 관리자가 Lync Server 2013을 실행하는 모든 컴퓨터와 풀에 대한 로깅 및 추적을 관리할 수 있게 해 줍니다. 중앙 로깅을 사용하면 관리자가 단일 명령을 사용하여 하나 이상의 풀 및 컴퓨터에 대해 로깅을 시작, 중지 및 구성할 수 있습니다. 예를 들어 명령 하나를 사용하여 모든 주소록 서버에서 주소록 서비스 로깅을 사용하도록 설정할 수 있습니다. 이는 서버마다 개별적으로 관리해야 하는(개별적으로 시작하고 중지하는 것도 포함) OCSLogger 및 OCSTracer 도구와 다릅니다. 또한 중앙 로깅 서비스에서는 관리자가 Windows PowerShell 명령줄 인터페이스 및 [Search-CsClsLogging](search-csclslogging.md) cmdlet을 사용하여 명령에서 추적 로그를 검색하는 방법도 있습니다.

중앙 로깅은 이전 버전의 Lync Server에서 제공되었던 것보다 대상이 상세하게 지정된 로깅 방식을 제공하는 미리 정의된 일련의 시나리오를 기반으로 작성되었습니다. 이러한 시나리오에 따라 서버 구성 요소 및 로깅이 자동으로 미리 결정되므로 RGS 시나리오를 사용하도록 설정하는 관리자는 오디오 회의 공급자 서비스가 아닌 응답 그룹 서비스와 관련된 정보만 기록할 수 있습니다.

[New-CsClsScenario](new-csclsscenario.md) cmdlet을 사용하여 사용자 지정 시나리오를 정의할 수도 있습니다.

[Start-CsClsLogging](start-csclslogging.md) cmdlet을 사용하면 관리자가 컴퓨터 또는 컴퓨터 집합에서 지정된 시나리오 로깅을 시작할 수 있습니다. 기본 설정에 따라 로깅 작업은 지속 제한 시간이 만료될 때까지 실행됩니다. 하지만 **Stop-CsClsLogging** cmdlet을 사용하면 언제든지 로깅 작업을 수동으로 중지할 수 있습니다.

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
<td><p><em>Scenario</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>중지할 중앙 로깅 시나리오의 이름입니다. 이 명령을 사용하여 사용 가능한 시나리오(및 이름)를 반환합니다.</p>
<p>Get-CsClsScenario | Select-Object Name</p></td>
</tr>
<tr class="even">
<td><p><em>AsXml</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 XML을 사용하여 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Computers</em></p></td>
<td><p>선택</p></td>
<td><p>System.String[]</p></td>
<td><p>관리자가 지정된 서버 또는 서버 집합에서 로깅을 중지합니다. 단일 서버의 로깅을 중지하려면 해당 서버의 정규화된 도메인 이름을 지정합니다. 예를 들면 다음과 같습니다.</p>
<p>-Computers &quot;atl-server-001.litwareinc.com&quot;</p>
<p>컴퓨터 FQDN을 쉼표로 구분하여 여러 서버를 지정할 수 있습니다.</p>
<p>-Computers &quot;atl-server-001.litwareinc.com&quot;,&quot;red-server-002.litwareinc.com&quot;</p>
<p>Computers 매개 변수 또는 Pools 매개 변수를 포함하지 않으면 <strong>Stop-CsClsLogging</strong> cmdlet이 토폴로지의 모든 풀을 대상으로 명령을 실행합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Pools</em></p></td>
<td><p>선택</p></td>
<td><p>System.String[]</p></td>
<td><p>관리자가 풀의 각 서버에서 로깅을 중지합니다. 풀의 로깅을 중지하려면 해당 풀의 정규화된 도메인 이름을 지정합니다. 예를 들면 다음과 같습니다.</p>
<p>-Pools &quot;atl-cs-001.litwareinc.com&quot;</p>
<p>풀 FQDN을 쉼표로 구분하여 여러 풀을 지정할 수 있습니다.</p>
<p>-Pools &quot;atl-cs-001.litwareinc.com&quot;,&quot;red-cs-002.litwareinc.com&quot;</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Stop-CsClsLogging** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

문자열 값 또는 XML 출력. **Stop-CsClsLogging** cmdlet은 개체를 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Search-CsClsLogging](search-csclslogging.md)  
[Show-CsClsLogging](show-csclslogging.md)  
[Start-CsClsLogging](start-csclslogging.md)  
[Sync-CsClsLogging](sync-csclslogging.md)  
[Update-CsClsLogging](update-csclslogging.md)

