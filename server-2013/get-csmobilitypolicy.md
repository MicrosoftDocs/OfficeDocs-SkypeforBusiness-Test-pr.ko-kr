---
title: Get-CsMobilityPolicy
TOCTitle: Get-CsMobilityPolicy
ms:assetid: 51ef83de-9cc2-4df8-b4f1-8d816b8de431
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690017(v=OCS.15)
ms:contentKeyID: 49303635
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsMobilityPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용 중인 모바일 정책에 대한 정보를 검색할 수 있습니다. 모바일 정책은 사용자가 Lync Mobile을 사용할 수 있는지 여부를 결정합니다. 또한 이러한 정책은 사용자가 회사번호로 전화를 거는 기능을 관리하는데, 이 기능을 사용하면 휴대폰에서 자신의 휴대폰 번호 대신 회사 전화 번호를 사용하여 전화를 걸고 받을 수 있습니다. 모바일 정책을 사용하면 전화를 걸거나 받을 때 Wi-Fi 연결을 사용하도록 지정할 수도 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsMobilityPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsMobilityPolicy [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 이동성 정책에 대한 정보를 반환합니다.

    Get-CsMobilityPolicy

## 예제 2

예제 2에서는 Identity가 site:Redmond인 단일 이동성 정책에 대한 정보를 반환합니다.

    Get-CsMobilityPolicy -Identity "site:Redmond"

## 예제 3

예제 3에서는 모든 사용자별 이동성 정책에 대한 정보가 반환됩니다. 이 작업을 수행하기 위해 필터 값 "tag:\*"와 함께 Filter 매개 변수가 포함됩니다. 이렇게 하면 해당 ID가 문자열 값 "tag:"로 시작하는 모든 정책이 반환됩니다. 정의에 따라 ID가 이 문자열 값으로 시작하는 모든 정책은 사용자별 정책입니다.

    Get-CsMobilityPolicy -Filter "tag:*"

## 예제 4

예제 4에 표시된 명령은 반환되는 데이터를 회사번호로 전화 기능이 사용하지 않도록 설정된 모바일 정책으로 제한합니다. 이 작업을 수행하기 위해 이 명령은 먼저 매개 변수 없이 **Get-CsMobilityPolicy** cmdlet을 호출합니다. 그러면 조직에서 사용하도록 구성된 모든 모바일 정책 컬렉션이 반환됩니다. 이 컬렉션은 EnableOutsideVoice 속성이 False와 같은(-eq) 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsMobilityPolicy | Where-Object {$_.EnableOutsideVoice -eq $False}

## 자세한 정보

Lync Mobile은 사용자가 휴대폰에서 Lync를 실행할 수 있도록 하는 클라이언트 응용 프로그램입니다. 회사번호로 전화 기능을 사용하면 휴대폰에서 전화를 걸지만 해당 휴대폰 번호 대신 회사 전화 번호에서 전화가 걸려 온 것처럼 보이게 할 수 있습니다. 회사번호로 전화 기능을 사용하도록 설정된 사용자는 이를 위해 휴대폰에서 직접 전화를 걸거나 외부 전화 접속 회의 옵션을 사용하면 됩니다. 외부 전화 접속 회의의 경우 사용자는 Lync Server Mobility Service 서버에서 자동으로 전화를 걸도록 할 수 있습니다. 그러면 서버에서는 통화를 설정한 다음 해당 휴대폰으로 다시 사용자에게 전화를 겁니다. 그리고 사용자가 응답하면 서버에서는 통화하는 상대방에게 전화를 겁니다. 두 기능은 모두 모바일 정책을 사용하여 관리할 수 있습니다.

Lync Server 2013이 설치된 모바일 장치에서는 표준 휴대폰 네트워크 또는 Wi-Fi 연결을 사용하여 전화를 걸거나 받을 수 있습니다. 모바일 정책을 통해 Wi-Fi 연결을 사용하도록 지정하고 셀룰러 네트워크를 통해서는 통화를 할 수 없도록 차단할 수 있습니다.

이동성 정책은 전역, 사이트 또는 사용자별 범위에서 구성할 수 있으며, 이러한 정책에 대한 정보는 **Get-CsMobilityPolicy** cmdlet을 사용하여 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsMobilityPolicy** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p>반환할 하나 이상의 정책을 나타낼 때 와일드카드 문자를 사용할 수 있도록 합니다. 예를 들어 사이트 범위에서 구성된 모든 정책을 반환하려면 다음 구문을 사용합니다.</p>
<p>-Filter &quot;site:*&quot;</p>
<p>모든 사용자별 정책 컬렉션을 반환하려면 다음 구문을 사용합니다.</p>
<p>-Filter &quot;tag:*&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 이동성 정책의 고유 식별자입니다. 전역 정책을 참조하려면 다음 구문을 사용합니다.</p>
<p>-Identity global</p>
<p>사이트 정책을 참조하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity site:Redmond</p>
<p>사용자별 정책을 참조하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity SalesDepartmentPolicy</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsMobilityPolicy</strong> cmdlet이 조직에서 사용 중인 모든 모바일 정책 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 이동성 정책 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Get-CsMobilityPolicy** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsMobilityPolicy** cmdlet은 Microsoft.Rtc.Management.WriteableConfig.Policy.Mobility.Mobility 개체의 인스턴스를 반환합니다.

