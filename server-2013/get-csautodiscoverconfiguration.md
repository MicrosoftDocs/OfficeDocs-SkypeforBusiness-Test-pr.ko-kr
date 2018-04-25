---
title: Get-CsAutodiscoverConfiguration
TOCTitle: Get-CsAutodiscoverConfiguration
ms:assetid: 221d26d6-0f77-4873-8872-d600913eb98b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690014(v=OCS.15)
ms:contentKeyID: 49303046
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAutodiscoverConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

현재 조직에서 사용 중인 자동 검색 구성 설정에 대한 정보를 반환할 수 있습니다. 자동 검색 서비스를 사용하면 Lync Web App 등의 클라이언트 응용 프로그램에서 사용자의 홈 풀 또는 전화 접속 회의 참가용 URL 같은 주요 리소스를 찾을 수 있습니다. 이 cmdlet은 Lync Server 2010용 2011년 11월 누적 업데이트에서 도입되었습니다.

## 구문

    Get-CsAutodiscoverConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsAutodiscoverConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령에서는 조직에서 현재 사용 중인 모든 자동 검색 구성 설정을 반환합니다.

    Get-CsAutoDiscoverConfiguration

## 예제 2

예제 2에서는 자동 검색 구성 설정 컬렉션이 하나(전역 컬렉션)만 반환됩니다.

    Get-CsAutoDiscoverConfiguration -Identity "global"

## 예제 3

예제 3에 표시된 명령은 사이트 범위에 할당된 모든 자동 검색 구성 설정을 반환합니다. 이를 위해 Filter 매개 변수와 함께 필터 값 "site:\*"를 포함합니다. 이 필터 값은 해당 ID가 문자열 값 "site:"으로 시작하는 설정만 반환되도록 합니다. 정의에 따라 ID가 "site:"으로 시작하는 설정은 사이트 범위에서 구성된 설정입니다.

    Get-CsAutoDiscoverConfiguration -Filter "site:*"

## 예제 4

예제 4에 표시된 명령에서는 fabrikam.com에 대한 자동 검색 URL이 포함된 모든 자동 검색 구성 설정을 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsAutoDiscoverConfiguration** cmdlet을 사용하여 조직에서 현재 사용 중인 모든 자동 검색 설정 컬렉션을 반환합니다. 그런 다음 이 컬렉션은 WebLinks 속성에 문자열 값 "fabrikam.com"이 포함된 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsAutoDiscoverConfiguration | Where-Object {$_.WebLinks -like "*fabrikam.com"}

## 자세한 정보

클라이언트 응용 프로그램에서 Lync Server를 최대한 효과적으로 사용하도록 하려면 이러한 응용 프로그램에서 주요 Lync Server 구성 요소의 위치를 인식하고 있어야 합니다. 예를 들어 인증된 사용자가 해당 홈 풀을 찾을 수 있어야 합니다. 즉, 이러한 사용자는 해당 홈 풀을 통해서만 인증될 수 있습니다. 마찬가지로, 인증되지 않은 사용자가 전화 회의에 참가하는 데 사용되는 URL을 찾는 등의 작업을 수행할 수 있어야 합니다.

모든 사용자가 조직의 방화벽 외부에서 로그온한 경우에는 이러한 위치를 검색하기가 비교적 쉽습니다. 하지만 사용자가 Lync Web App과 같은 응용 프로그램을 사용하여 외부 위치에서 시스템에 액세스하게 되면 이처럼 비교적 단순한 작업도 점점 더 복잡해집니다.

이는 분할 도메인 시나리오에서 특히 심하게 나타나는데, 이러한 시나리오의 경우 조직의 일부 사용자는 온-프레미스 버전의 Lync Server에 계정을 가지고 있지만 다른 사용자는 비즈니스용 Skype Online에 계정을 가지고 있습니다. 이 경우 사용자 계정이 각기 다른 Active Directory 포리스트에 있을 수 있는데, 이렇게 되면 특정한 문제가 발생할 수 있습니다. 예를 들어 미국의 사용자가 유럽에서 로그온하는 경우 시스템에서는 이 사용자의 포리스트를 인식한 다음 로그온 요청을 적절한 풀에 조회할 수 있어야 합니다.

자동 검색 서비스는 바로 이러한 문제를 해결하기 위해 Lync Server 2011년 11월 누적 업데이트에 도입되었습니다. 클라이언트 응용 프로그램이 Lync Server에 액세스를 시도하면 자동 검색 서비스에서는 클라이언트 SIP 주소를 구문 분석한 다음 해당 요청을 적절한 풀로 리디렉션합니다. 클라이언트 응용 프로그램은 HTTP 요청을 자동 검색 URL로 보내는 방식으로 자동 검색 서비스에 연결되는데, 자동 검색 서비스가 올바르게 작동하려면 관리자가 이러한 URL을 구성해야 합니다. 참고적으로, URL을 구성하는 것 외에도 관리자는 이러한 URL에 해당하는 DNS 레코드를 만들어야 합니다.

자동 검색 URL은 자동 검색 구성 설정에 할당되며, 이를 통해 이러한 설정을 전역 범위나 사이트 범위에 할당할 수 있습니다. **Get-CsAutoDiscoverConfiguration** cmdlet을 사용하면 조직에서 현재 사용 중인 자동 검색 설정 및 자동 검색 URL에 대한 정보를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsAutoDiscoverConfiguration** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p>와일드카드를 사용하여 반환할 자동 검색 구성 설정의 ID를 지정하는 데 사용됩니다. 예를 들어 이 구문은 사이트 범위에서 구성된 모든 설정을 반환합니다.</p>
<p>-Filter &quot;site:*&quot;</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 자동 검색 구성 설정 컬렉션의 고유 식별자입니다. 전역 컬렉션을 검색하려면 다음 구문을 사용합니다.</p>
<p>-Identity &quot;global&quot;</p>
<p>사이트 범위에서 구성된 설정을 검색하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>이 매개 변수를 포함하지 않으면 <strong>Get-CsAutoDiscoverConfiguration</strong> cmdlet이 조직에서 현재 사용 중인 모든 자동 검색 구성 설정을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 자동 검색 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Get-CsAutoDiscoverConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsAutoDiscoverConfiguration** cmdlet은 Microsoft.Rtc.Management.WriteableConfig.Settings.AutoDiscoverConfiguration.AutoDiscoverConfiguration 개체의 인스턴스를 반환합니다.

