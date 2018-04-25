---
title: Set-CsClsConfiguration
TOCTitle: Set-CsClsConfiguration
ms:assetid: 6cebd908-e829-4dee-82fd-1164bc8999ee
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ619182(v=OCS.15)
ms:contentKeyID: 49303957
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsClsConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 중앙 로깅 구성 설정 컬렉션을 수정합니다. 중앙 로깅을 사용하면 관리자가 여러 컴퓨터에서 추적을 동시에 활성화하거나 비활성화할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsClsConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsClsConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-CacheFileLocalFolders <String>] [-CacheFileLocalMaxDiskUsage <UInt32>] [-CacheFileLocalRetentionPeriod <UInt32>] [-CacheFileNetworkFolder <String>] [-ComponentThrottleLimit <UInt32>] [-ComponentThrottleSample <UInt32>] [-Confirm [<SwitchParameter>]] [-EtlFileFolder <String>] [-EtlFileRolloverMinutes <UInt32>] [-EtlFileRolloverSizeMB <UInt32>] [-Force <SwitchParameter>] [-MinimumClsAgentServiceVersion <UInt32>] [-Regions <PSListModifier>] [-Scenarios <PSListModifier>] [-SearchTerms <PSListModifier>] [-SecurityGroups <PSListModifier>] [-TmfFileSearchPath <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 중앙 로깅 구성 설정의 전역 컬렉션을 수정하여 ETL 파일의 최대 크기를 40메가바이트로 설정합니다.

    Set-CsClsConfiguration -Identity "global" -EtlRolloverFileSizeMB 40

## 예제 2

예제 2의 명령은 조직에서 사용 중인 모든 중앙 로깅 구성 설정에 대해 ETL 파일의 최대 크기를 수정합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsClsConfiguration** cmdlet을 호출하여 모든 중앙 로깅 설정의 컬렉션을 반환합니다. 이 컬렉션은 **Set-CsClsConfiguration** cmdlet에 파이프되고, Set-CsClsConfiguration cmdlet은 컬렉션의 각 항목에 대해 EtlRolloverFileSizeMB 속성 값을 40메가바이트로 변경합니다.

    Get-CsClsConfiguration | Set-CsClsConfiguration -EtlRolloverFileSizeMB 40

## 자세한 정보

중앙 로깅 서비스( Microsoft Lync Server 2010에서 사용하는 OCSLogger 및 OCSTracer 도구를 대체함)는 관리자가 Lync Server 2013을 실행하는 모든 컴퓨터와 풀에 대한 로깅 및 추적을 관리할 수 있게 해 줍니다. 중앙 로깅을 사용하면 관리자가 단일 명령을 사용하여 하나 이상의 풀 및 컴퓨터에 대해 로깅을 시작, 중지 및 구성할 수 있습니다. 예를 들어 명령 하나를 사용하여 모든 주소록 서버에서 주소록 서비스 로깅을 사용하도록 설정할 수 있습니다. 이는 서버마다 개별적으로 관리해야 하는(개별적으로 시작하고 중지하는 것도 포함) OCSLogger 및 OCSTracer 도구와 다릅니다. 또한 중앙 로깅 서비스에서는 관리자가 Windows PowerShell 명령줄 인터페이스 및 [Search-CsClsLogging](search-csclslogging.md) cmdlet을 사용하여 명령에서 추적 로그를 검색하는 방법도 있습니다.

중앙 로깅은 이전 버전의 Lync Server에서 제공되었던 것보다 대상이 상세하게 지정된 로깅 방식을 제공하는 미리 정의된 일련의 시나리오를 기반으로 작성되었습니다. 이러한 시나리오에 따라 서버 구성 요소 및 로깅이 자동으로 미리 결정되므로 RGS 시나리오를 사용하도록 설정하는 관리자는 오디오 회의 공급자 서비스가 아닌 응답 그룹 서비스와 관련된 정보만 기록할 수 있습니다.

[New-CsClsScenario](new-csclsscenario.md) cmdlet을 사용하여 사용자 지정 시나리오를 정의할 수도 있습니다.

중앙 로깅은 중앙 로깅 서비스 구성 설정 컬렉션을 사용하여 관리합니다. Lync Server 2013을 설치하면 이 구성 설정의 전역 집합이 설치됩니다. 관리자가 사이트 범위에서 사용자 지정 설정 컬렉션을 추가할 수도 있습니다. 이 설정을 수정하려면 **Set-CsClsConfiguration** cmdlet을 사용합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsClsConfiguration"}

**Lync Server 제어판:** **Set-CsClsConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>CacheFileLocalFolders</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>캐시 파일을 저장할 로컬 폴더에 대한 하나 이상의 전체 경로입니다. 경로를 여러 개 지정할 경우 세미콜론으로 구분하세요.</p></td>
</tr>
<tr class="even">
<td><p><em>CacheFileLocalMaxDiskUsage</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>캐시 파일에 사용할 수 있는 최대 디스크 공간(백분율)입니다. 기본값은 80입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>CacheFileLocalRetentionPeriod</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>캐시 파일을 로컬에 보존하는 최대 일수입니다. 기본값은 14입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CacheFileNetworkFolder</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>네트워크 캐시 폴더의 전체 UNC 경로입니다. 기본값은 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ComponentThrottleLimit</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>추적이 제한되기 전에 구성 요소가 추적 레코드를 생성할 수 있는 최대 속도입니다. 기본값은 초당 추적 호출 5000개입니다.</p>
<p>기본값은 5000입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ComponentThrottleSample</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>1분 사이에 ComponentThrottleLimit를 초과할 수 있는 최대 횟수입니다. 기본값은 3입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EtlFileFolder</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이벤트 로그 추적 파일이 저장되는 폴더의 전체 경로입니다. 기본값은 %TEMP%\Tracing입니다. %TEMP%는 CLS 서비스의 콘텐츠에서 평가되므로 실제로는 %WINDIR%\ServiceProfiles\NetworkService\AppData\Local로 확장됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EtlFileRolloverMinutes</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>새 이벤트 로그 추적 파일을 만들 때까지 경과될 수 있는 최대 시간(분)입니다. 이 새 파일은 기존 추적 파일이 지정된 롤오버 크기에 도달하지 않은 경우에도 생성됩니다. 기본값은 60입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EtlFileRolloverSizeMB</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>새 파일을 만들 때까지 이벤트 추적 로그 파일이 도달할 수 있는 최대 크기(메가바이트)입니다. 기본값은 20입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 중앙 로깅 구성 설정의 고유 ID입니다. 전역 설정을 참조하려면 다음 구문을 사용합니다.</p>
<p>-Identity global</p>
<p>사이트 설정을 참조하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity site:Redmond</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MinimumClsAgentServiceVersion</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>데이터 로깅에 사용할 중앙 로깅 서비스 에이전트의 최소 버전을 지정합니다. 에이전트 버전이 이 최소값보다 작은 컴퓨터는 로깅 작업에서 제외됩니다. 기본값은 Lync Server 2013에 해당하는 6입니다. 이 매개 변수는 비즈니스용 Skype Online에서 사용하기 위한 것입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Regions</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>중앙 로깅 구성 설정에 정의된 지역 컬렉션입니다. 지역은 New-CsClsRegion cmdlet을 사용하여 정의합니다.</p>
<p>이 매개 변수는 비즈니스용 Skype Online에서 사용하기 위한 것입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Scenarios</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>중앙 로깅을 사용하여 추적할 수 있는 구성 요소/상황 컬렉션입니다. 시나리오는 <strong>CsClsScenario</strong> cmdlet을 사용하여 관리합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SearchTerms</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>중앙 로깅 파일을 검색하는 기술 지원 담당자가 사용할 개인 식별 정보를 결정하는 데 필요한 용어 컬렉션입니다. 검색어는 <strong>CsClsSearchTerm</strong> cmdlet을 사용하여 관리합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SecurityGroups</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>로그 파일에 액세스할 수 있는 보안 그룹입니다.</p>
<p>이 매개 변수는 비즈니스용 Skype Online에서 사용하기 위한 것입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TmfFileSearchPath</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>TMF(추적 메시지 형식) 파일의 검색 경로입니다. TMF 파일은 이진 추적 메시지를 사람이 읽을 수 있는 형식으로 변환합니다.</p></td>
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

**Set-CsClsConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.CentralizedLoggingConfiguration 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsClsConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.CentralizedLoggingConfiguration 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClsConfiguration](get-csclsconfiguration.md)  
[New-CsClsConfiguration](new-csclsconfiguration.md)  
[Remove-CsClsConfiguration](remove-csclsconfiguration.md)

