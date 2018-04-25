---
title: Get-CsClsConfiguration
TOCTitle: Get-CsClsConfiguration
ms:assetid: 5fef2e35-e23c-453d-97e5-cb9c4e7bfef7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ619179(v=OCS.15)
ms:contentKeyID: 49303791
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsClsConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용 중인 중앙 로깅 구성 설정에 관한 정보를 반환합니다. 관리자는 중앙 로깅을 통해 여러 컴퓨터에서 이벤트 추적을 동시에 사용하거나 사용하지 않도록 설정할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsClsConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsClsConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1의 명령은 현재 조직에서 사용 중인 모든 중앙 로깅 구성 설정에 관한 정보를 반환합니다.

    Get-CsClsConfiguration

## 예제 2

예제 2에서는 중앙 로깅 구성 설정의 단일 컬렉션에 대해 정보가 반환됩니다. 여기서는 Redmond 사이트에 적용되는 컬렉션입니다.

    Get-CsClsConfiguration -Identity "site:Redmond"

## 예제 3

예제 3은 Redmond 사이트에 사용할 수 있는 중앙 로깅 시나리오의 세부 정보를 표시합니다. 이를 위해 이 예제의 명령은 먼저 Redmond 사이트의 모든 중앙 로깅 속성 값을 검색합니다. 이 속성 값은 Select-Object cmdlet으로 파이프되고, Select-Object cmdlet은 ExpandProperty 매개 변수를 사용하여 Scenarios 속성에 있는 값을 "확장"합니다. 속성을 확장할 때는 해당 속성에 저장된 모든 정보를 읽기 쉬운 형태로 표시하기만 합니다.

    Get-CsClsConfiguration -Identity "site:Redmond" | Select-Object -ExpandProperty Scenarios

## 예제 4

예제 4에서는 ETL 파일 롤오버 간격이 1시간보다 긴 모든 중앙 로깅 구성 설정에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsClsConfiguration** cmdlet을 호출합니다. 그러면 조직 내 모든 중앙 로깅 구성 설정 컬렉션이 반환됩니다. 이 컬렉션은 **Where-Object** cmdlet으로 파이프되고, 해당 cmdlet은 EtlFileRolloverMinutes 속성이 60분보다 큰(-gt) 설정만 가려냅니다.

    Get-CsClsConfiguration | Where-Object {$_.EtlFileRolloverMinutes -gt 60}

## 예제 5

예제 5의 명령은 예제 4의 명령과 유사합니다. 단, 여기서는 "HybridVoice" 시나리오가 포함된 중앙 로깅 구성 설정에 대한 정보만 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsClsConfiguration** cmdlet을 사용하여 모든 중앙 로깅 구성 설정의 컬렉션을 반환합니다. 반환된 컬렉션은 **Where-Object** cmdlet으로 파이프되고, 해당 cmdlet은 Name 속성에 문자열 값 "HybridVoice"가 포함된(-match) 시나리오가 하나 이상 있는 설정만 선택합니다.

    Get-CsClsConfiguration | Where-Object {$_.Scenarios.Name -match "HybridVoice"}

## 자세한 정보

중앙 로깅 서비스( Microsoft Lync Server 2010에서 사용하는 OCSLogger 및 OCSTracer 도구를 대체함)는 관리자가 Lync Server 2013을 실행하는 모든 컴퓨터와 풀에 대한 로깅 및 추적을 관리할 수 있게 해 줍니다. 중앙 로깅을 사용하면 관리자가 단일 명령을 사용하여 하나 이상의 풀 및 컴퓨터에 대해 로깅을 시작, 중지 및 구성할 수 있습니다. 예를 들어 명령 하나를 사용하여 모든 주소록 서버에서 주소록 서비스 로깅을 사용하도록 설정할 수 있습니다. 이는 서버마다 개별적으로 관리해야 하는(개별적으로 시작하고 중지하는 것도 포함) OCSLogger 및 OCSTracer 도구와 다릅니다. 또한 중앙 로깅 서비스에서는 관리자가 Windows PowerShell 명령줄 인터페이스 및 [Search-CsClsLogging](search-csclslogging.md) cmdlet을 사용하여 명령에서 추적 로그를 검색하는 방법도 있습니다.

중앙 로깅은 이전 버전의 Lync Server에서 제공되었던 것보다 대상이 상세하게 지정된 로깅 방식을 제공하는 미리 정의된 일련의 시나리오를 기반으로 작성되었습니다. 이러한 시나리오에 따라 서버 구성 요소 및 로깅이 자동으로 미리 결정되므로 RGS 시나리오를 사용하도록 설정하는 관리자는 오디오 회의 공급자 서비스가 아닌 응답 그룹 서비스와 관련된 정보만 기록할 수 있습니다.

[New-CsClsScenario](new-csclsscenario.md) cmdlet을 사용하여 사용자 지정 시나리오를 정의할 수도 있습니다.

중앙 로깅은 중앙 로깅 서비스 구성 설정 컬렉션을 사용하여 관리합니다. Microsoft Lync Server 2013을 설치하면 이 구성 설정의 전역 집합이 설치됩니다. 관리자가 사이트 범위에서 사용자 지정 설정 컬렉션을 추가할 수도 있습니다. **Get-CsClsConfiguration** cmdlet을 사용하면 관리자가 현재 조직에서 사용 중인 모든 중앙 로깅 구성 설정에 관한 정보를 반환할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsClsConfiguration"}

**Lync Server 제어판:** **Get-CsClsConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>하나 이상의 중앙 로깅 구성 설정 컬렉션을 반환하도록 와일드카드 문자를 사용합니다. 예를 들어 사이트 범위에서 구성된 모든 설정의 컬렉션을 반환하려면 다음 구문을 사용합니다.</p>
<p>-Filter &quot;site:*&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 중앙 로깅 구성 설정 컬렉션의 고유 ID를 나타냅니다. 전역 설정을 참조하려면 다음 구문을 사용합니다.</p>
<p>-Identity &quot;global&quot;</p>
<p>사이트 범위에서 구성된 컬렉션을 참조하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용해야 하는 경우 대신 Filter 매개 변수를 포함합니다.</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsClsConfiguration</strong> cmdlet이 조직에서 사용 중인 모든 중앙 로깅 구성 설정의 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아닌 중앙 관리 저장소의 로컬 복제본에서 중앙 로깅 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsClsConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsClsConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.CentralizedLoggingConfiguration 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsClsConfiguration](new-csclsconfiguration.md)  
[Remove-CsClsConfiguration](remove-csclsconfiguration.md)  
[Set-CsClsConfiguration](set-csclsconfiguration.md)

