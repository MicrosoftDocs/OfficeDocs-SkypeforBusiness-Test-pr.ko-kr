---
title: Get-CsClsScenario
TOCTitle: Get-CsClsScenario
ms:assetid: 8f0c5f52-c000-4e27-82a2-534a50b11a98
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205091(v=OCS.15)
ms:contentKeyID: 49304357
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsClsScenario

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 중앙 로깅 구성 시나리오에 대한 정보를 반환합니다. 시나리오는 관리자가 추적을 위해 사용하거나 사용하지 않도록 설정할 수 있는 특정 Lync Server 2013 구성 요소 또는 상황(예: 메신저 대화 및 현재 상태)을 나타냅니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsClsScenario [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsClsScenario [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 현재 사용 중인 모든 중앙 로깅 시나리오에 대한 정보를 반환합니다.

    Get-CsClsScenario

## 예제 2

예제 2에서는 단일 중앙 로깅 시나리오, 즉 전역 설정 컬렉션에 포함된 VoiceMail 시나리오에 대한 정보를 반환합니다.

    Get-CsClsScenario -Identity "global/VoiceMail"

## 예제 3

예제 3에서는 현재 사용 중인 모든 기본 시나리오에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsClsScenario** cmdlet을 호출합니다. 그러면 사용 가능한 모든 시나리오의 컬렉션이 반환됩니다. 해당 컬렉션은 **Where-Object** cmdlet에 파이프되며, 이 cmdlet은 "AsMcu"라는 공급자를 포함(-match)하는 시나리오만 선택합니다.

    Get-CsClsScenario | Where-Object {$_.Provider.Name -match "AsMcu"}

## 예제 4

예제 4에서는 전역 VoiceMail 시나리오의 Provider 속성에 대한 자세한 정보를 반환합니다. 이 작업을 수행하기 위해 cmdlet은 먼저 **Get-CsClsScenario** cmdlet을 사용하여 전역 VoiceMail 시나리오에 대한 모든 속성 값을 반환합니다. 해당 정보는 Select-Object cmdlet에 파이프되며, 이 cmdlet은 ExpandProperty 매개 변수를 사용하여 Provider 속성의 값을 "확장"합니다. 그러면 Provider 속성에 저장된 모든 데이터가 쉽게 읽을 수 있는 형식으로 화면에 표시됩니다.

    Get-CsClsScenario -Identity "global/VoiceMail" | Select-Object -ExpandProperty Provider

## 자세한 정보

중앙 로깅 서비스( Microsoft Lync Server 2010에서 사용하는 OCSLogger 및 OCSTracer 도구를 대체함)는 관리자가 Lync Server 2013을 실행하는 모든 컴퓨터와 풀에 대한 로깅 및 추적을 관리할 수 있게 해 줍니다. 중앙 로깅을 사용하면 관리자가 단일 명령을 사용하여 하나 이상의 풀 및 컴퓨터에 대해 로깅을 시작, 중지 및 구성할 수 있습니다. 예를 들어 명령 하나를 사용하여 모든 주소록 서버에서 주소록 서비스 로깅을 사용하도록 설정할 수 있습니다. 이는 서버마다 개별적으로 관리해야 하는(개별적으로 시작하고 중지하는 것도 포함) OCSLogger 및 OCSTracer 도구와 다릅니다. 또한 중앙 로깅 서비스에서는 관리자가 Windows PowerShell 명령줄 인터페이스 및 [Search-CsClsLogging](search-csclslogging.md) cmdlet을 사용하여 명령에서 추적 로그를 검색하는 방법도 있습니다.

중앙 로깅은 이전 버전의 Lync Server에서 제공되었던 것보다 대상이 상세하게 지정된 로깅 방식을 제공하는 미리 정의된 일련의 시나리오를 기반으로 작성되었습니다. 이러한 시나리오에 따라 서버 구성 요소 및 로깅이 자동으로 미리 결정되므로 RGS 시나리오를 사용하도록 설정하는 관리자는 오디오 회의 공급자 서비스가 아닌 응답 그룹 서비스와 관련된 정보만 기록할 수 있습니다.

**Get-CsClsScenario** cmdlet을 사용하면 조직에서 사용 가능한 모든 중앙 로깅 시나리오에 대한 정보를 반환할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsClsScenario"}

Lync Server 제어판: **Get-CsClsScenario** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>하나 이상의 시나리오를 반환하기 위해 와일드카드를 사용할 수 있습니다. 예를 들어 모든 HybridVoice 시나리오를 반환하려면 해당 시나리오가 구성된 범위에 관계없이 다음 구문을 사용합니다.</p>
<p>-Filter &quot;*HybridVoice*&quot;</p>
<p>Identity 매개 변수와 Filter 매개 변수를 같은 명령에 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 시나리오의 고유 식별자입니다. 시나리오는 구성되는 범위(시나리오가 포함된 중앙 로깅 구성 설정 컬렉션) 및 시나리오 이름의 두 부분으로 구성됩니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;site:Redmond/AddressBook&quot;</p>
<p>다음과 같이 시나리오 범위만 지정할 수도 있습니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>이 경우에는 Redmond 사이트에서 사용하도록 구성된 모든 시나리오가 반환됩니다.</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsClsScenario</strong> cmdlet은 모든 중앙 로깅 시나리오에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 시나리오 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsScenario** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsScenario** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Scenario\#Decorated 개체의 인스턴스를 반환합니다.

