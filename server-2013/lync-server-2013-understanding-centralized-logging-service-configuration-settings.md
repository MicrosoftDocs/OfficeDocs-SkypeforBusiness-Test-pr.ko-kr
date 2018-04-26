---
title: 중앙화된 로깅 서비스 구성 설정 이해
TOCTitle: 중앙화된 로깅 서비스 구성 설정 이해
ms:assetid: 3c34e600-0b91-43dc-b4cc-90b6a70ee12e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688029(v=OCS.15)
ms:contentKeyID: 49885728
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 중앙화된 로깅 서비스 구성 설정 이해

 

_**마지막으로 수정된 항목:** 2015-03-09_

중앙 로깅 서비스는 로깅 서비스가 수집하는 항목, 수집 방법, 수집 위치 및 로깅 설정을 정의하도록 구성됩니다. 이러한 설정은 전역(즉, 전체 배포) 또는 사이트(즉, 배포에서 명명된 사이트)별로 정의합니다. 사용자가 정의하는 모든 로깅에는 로그를 시작, 중지, 플러시 및 검색하기 위한 명령에 사용하는 identity에 적합한 설정이 사용됩니다.

## 현재 중앙 로깅 서비스 구성을 표시하려면

Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

명령줄 프롬프트에 다음을 입력합니다.

    Get-CsClsConfiguration


> [!TIP]
> <CODE>-Identity</CODE> 및 범위(예: “Site:Redmond”)를 정의하여 반환된 구성 설정의 범위를 좁히거나 넓혀서 Redmond 사이트에 대한 CsClsConfiguration만 반환할 수 있습니다. 구성의 특정 부분에 대한 세부 정보가 필요하면 출력을 다른 Windows PowerShell cmdlet으로 파이프할 수 있습니다. 예를 들어 “Redmond” 사이트에 대한 구성에 정의된 시나리오에 대한 세부 정보를 보려면 <CODE>Get-CsClsConfiguration -Identity "site:Redmond" | Select-Object -ExpandPropery Scenarios</CODE>를 입력합니다.



![Get-CsClsConfiguration의 샘플 출력.](images/JJ688029.23f98ddc-fc48-499a-b6c5-752611f2a0b0(OCS.15).jpg "Get-CsClsConfiguration의 샘플 출력.")

cmdlet의 결과에는 중앙 로깅 서비스의 현재 구성이 표시됩니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>구성 설정</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Identity</strong></p></td>
<td><p>이 구성의 범위 및 이름을 식별합니다. 전역 구성 한 개와 사이트당 한 개의 구성만 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>Scenarios</strong></p></td>
<td><p>이 구성에 대해 정의된 모든 시나리오를 나열합니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SearchTerms</strong></p></td>
<td><p>구성에 대해 정의된 검색어입니다. 온-프레미스 배포가 아닌 Office 365용입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>SecurityGroups</strong></p></td>
<td><p>사용자가 위치한 사이트를 기반으로 컴퓨터를 볼 수 있는 사용자(즉, 보안 그룹의 구성원)를 제어하는 정의된 보안 그룹입니다. 이 문맥에서 사이트란 토폴로지 작성기에 정의된 사이트를 의미합니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Regions</strong></p></td>
<td><p>정의된 지역은 특정 지역(예: EMEA)에서 SecurityGroups를 수집하는 데 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>EtlFileFolder</strong></p></td>
<td><p>컴퓨터에서 로그 파일을 기록할 위치에 대해 정의된 경로입니다. CLSAgent는 네트워크 서비스의 컨텍스트에 따라 로그 파일을 기록하고 실행됩니다. 여기에서 %TEMP%는 %WINDIR%\ServiceProfiles\NetworkService\AppData\Local로 확장됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EtlFileRolloverSizeMB</strong></p></td>
<td><p>이 매개 변수는 새 이벤트 추적 로그(.etl) 파일을 만들기 전 로그 파일의 최대 크기를 나타냅니다. EtlFileRolloverMinutes에 설정된 최대 시간에 아직 도달하지 않았어도 정의된 크기에 도달하면 새 로그 파일이 만들어집니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>EtlFileRolloverMinutes</strong></p></td>
<td><p>새 .etl 파일을 만들기 전에 로그에서 경과될 수 있도록 정의된 최대 시간(분)입니다. 할 수 있도록 EtlFileRolloverSizeMB에 설정된 최대 크기에 아직 도달하지 않았어도 타이머 시간이 초과되면 새 로그 파일이 만들어집니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>TmfFileSearchPath</strong></p></td>
<td><p>추적 메시지 형식 파일을 검색할 위치입니다. 추적 메시지 형식 파일은 바이너리 파일을 사람이 읽을 수 있는 형식으로 변환하는 데 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CacheFileLocalFolders</strong></p></td>
<td><p>컴퓨터에서 캐시 파일을 기록할 위치에 대해 정의된 경로입니다. CLSAgent는 네트워크 서비스의 컨텍스트에 따라 캐시 파일을 기록하고 실행됩니다. 여기서 %TEMP%는 %WINDIR%\ServiceProfiles\NetworkService\AppData\Local로 확장됩니다. 기본적으로 캐시 파일과 로그 파일은 동일한 디렉터리에 기록됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CacheFileNetworkFolder</strong></p></td>
<td><p>로깅 작업 중 캐시 파일을 수신하기 위한 UNC(범용 명명 규칙) 경로를 정의할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CacheFileLocalRetentionPeriod</strong></p></td>
<td><p>캐시 파일을 보존할 수 있는 최대 시간(일)으로 정의됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CacheFileMaxDiskUsage</strong></p></td>
<td><p>캐시 파일이 사용할 수 있는 디스크 공간 비율로 정의됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ComponentThrottleLimit</strong></p></td>
<td><p>자동 스로틀 리미터가 트리거되기 전 구성 요소가 생성할 수 있는 초당 최대 추적 수로 정의됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ComponentThrottleSample</strong></p></td>
<td><p>ComponentThrottleLimit를 초과할 수 있는 횟수(60초 이내)입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>MinimumClsAgentServiceVersion</strong></p></td>
<td><p>실행할 수 있는 CLSAgent의 최소 버전입니다. 이 요소는 Office 365용입니다.</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 개념

[중앙화된 로깅 서비스 개요](lync-server-2013-overview-of-the-centralized-logging-service.md)  

#### 기타 리소스

[Set-CsClsConfiguration](set-csclsconfiguration.md)  
[Remove-CsClsConfiguration](remove-csclsconfiguration.md)  
[New-CsClsConfiguration](new-csclsconfiguration.md)  
[Get-CsClsConfiguration](get-csclsconfiguration.md)

