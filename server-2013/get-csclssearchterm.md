---
title: Get-CsClsSearchTerm
TOCTitle: Get-CsClsSearchTerm
ms:assetid: 89a6cc1d-5cbe-42ef-b5a0-127068a0f78a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205061(v=OCS.15)
ms:contentKeyID: 49304305
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsClsSearchTerm

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용 가능한 중앙 로깅 검색어에 대한 정보를 반환합니다. 검색 용어를 사용하는 경우 중앙 추적 로그를 검색하는 기술 지원 담당자가 개인 식별이 가능한 정보를 사용할 수 있습니다. 검색어는 비즈니스용 Skype Online용입니다.

이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsClsSearchTerm [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsClsSearchTerm [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 현재 사용 중인 모든 검색어에 대한 정보를 반환합니다.

    Get-CsClsSearchTerm

## 예제 2

예제 2에서는 단일 검색어, 즉 중앙 로깅 구성 설정의 전역 컬렉션에 있는 Phone 검색어에 대한 정보를 반환합니다.

    Get-CsClsSearchTerm -Identity "global/Phone"

## 예제 3

예제 3에 표시된 명령은 모든 URI 검색어에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsClsSearchTerm** cmdlet을 호출합니다. 그러면 사용 가능한 모든 검색어의 컬렉션이 반환됩니다. 해당 컬렉션은 **Where-Object** cmdlet에 파이프되며, 이 cmdlet은 Type 속성이 URI와 같은(-eq) 용어만 선택합니다.

    Get-CsClsSearchTerm | Where-Object {$_.Type -eq "URI"}

## 예제 4

예제 4에서는 Inserts 속성에 문자열 값 "ItemE164"가 포함된 모든 검색어에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsClsSearchTerm** cmdlet을 사용하여 사용 가능한 모든 검색어의 컬렉션을 반환합니다. 해당 컬렉션은 **Where-Object** cmdlet에 파이프되며, 이 cmdlet은 Inserts 속성에 문자열 값 "ItemE164"가 포함된(-match) 용어를 선택합니다.

    Get-CsClsSearchTerm | Where-Object {$_.Inserts -match "ItemE164"}

## 자세한 정보

중앙 로깅 서비스( Microsoft Lync Server 2010에서 사용하는 OCSLogger 및 OCSTracer 도구를 대체함)는 관리자가 Lync Server 2013을 실행하는 모든 컴퓨터와 풀에 대한 로깅 및 추적을 관리할 수 있게 해 줍니다. 중앙 로깅을 사용하면 관리자가 단일 명령을 사용하여 하나 이상의 풀 및 컴퓨터에 대해 로깅을 시작, 중지 및 구성할 수 있습니다. 예를 들어 명령 하나를 사용하여 모든 주소록 서버에서 주소록 서비스 로깅을 사용하도록 설정할 수 있습니다. 이는 서버마다 개별적으로 관리해야 하는(개별적으로 시작하고 중지하는 것도 포함) OCSLogger 및 OCSTracer 도구와 다릅니다. 또한 중앙 로깅 서비스에서는 관리자가 Windows PowerShell 명령줄 인터페이스 및 [Search-CsClsLogging](search-csclslogging.md) cmdlet을 사용하여 명령에서 추적 로그를 검색하는 방법도 있습니다.

Lync Server 2013에서는 관리자가 검색어를 사용하여 로그 파일을 보는 지원 담당자가 보지 못하도록 개인 식별이 가능한 정보를 마스킹할 수 있습니다. 예를 들어 Ken Myer와 같은 사용자 이름은 지원 콘솔을 사용하여 볼 때 표시되지 않으며 FIRST1 LAST1로 표시될 수 있습니다. 마찬가지로 전화 번호 +12065551219는 PHONE1로 표시될 수 있습니다.

**Get-CsClsSearchTerm** cmdlet은 현재 사용 가능한 검색어에 대한 정보를 반환합니다. 이러한 검색어는 Inserts 속성을 기반으로 하는데, 이 속성은 마스킹할 정보와 개인 식별이 가능한 정보 대신 표시할 마스크를 지정합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsClsSearchTerm"}

**Lync Server 제어판:** **Get-CsClsSearchTerm** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>하나 이상의 검색어를 반환하기 위해 와일드카드를 사용할 수 있습니다. 예를 들어 모든 CallID 검색어를 반환하려면 해당 용어가 구성된 범위에 관계없이 다음 구문을 사용합니다.</p>
<p>-Filter &quot;*CallID*&quot;</p>
<p>Identity 매개 변수와 Filter 매개 변수를 같은 명령에 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 검색어의 고유 식별자입니다. 검색어는 구성되는 범위(용어가 포함된 중앙 로깅 구성 설정 컬렉션) 및 용어 이름의 두 부분으로 구성됩니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;site:Redmond/CallID&quot;</p>
<p>다음과 같이 검색어 범위만 지정할 수도 있습니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>이 경우에는 Redmond 사이트에서 사용하도록 구성된 모든 검색어가 반환됩니다.</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsSearchTerm</strong> cmdlet은 모든 중앙 로깅 검색어에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 검색어 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsClsSearchTerm** cmdlet은 파이프라인된 입력을 지원하지 않습니다.

## 반환 형식

**Get-CsClsSearchTerm** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.SearchTerm\#Decorated 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Set-CsClsSearchTerm](set-csclssearchterm.md)

