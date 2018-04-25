---
title: Remove-CsMobilityPolicy
TOCTitle: Remove-CsMobilityPolicy
ms:assetid: d3dc4653-25ab-45ef-b325-fba01e45acca
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690048(v=OCS.15)
ms:contentKeyID: 49305133
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsMobilityPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 모바일 정책을 제거합니다. 모바일 정책은 사용자가 회사번호로 전화를 거는 기능을 관리하는데, 이 기능을 사용하면 휴대폰에서 자신의 휴대폰 번호 대신 회사 전화 번호를 사용하여 전화를 걸고 받을 수 있습니다. 모바일 정책을 사용하여 전화를 걸고 받을 때 Wi-Fi 연결을 사용하도록 지정할 수도 있습니다. 이 cmdlet은 Lync Server 2010용 2011년 11월 누적 업데이트에서 도입되었습니다.

## 구문

    Remove-CsMobilityPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1의 명령은 Redmond 사이트에 대해 구성된 모바일 정책을 제거합니다. 정책이 제거되면 Redmond 사이트 정책을 통해 관리되던 사용자가 전역 정책을 통해 관리됩니다.

    Remove-CsMobilityPolicy -Identity "site:Redmond"

## 예제 2

예제 2에서는 사용자별 범위에 구성된 모든 모바일 정책이 제거됩니다. 이를 위해 명령에서는 먼저 **Get-CsMobilityPolicy** cmdlet과 Filter 매개 변수를 사용하여 ID가 문자열 값 "Tag:"으로 시작하는 모든 정책을 검색합니다. 정의에 따라 이 기준을 충족하는 정책은 사용자별 정책입니다. 그런 다음 이 사용자별 정책 컬렉션은 컬렉션의 각 정책을 삭제하는 **Remove-CsMobilityPolicy** cmdlet에 파이프됩니다.

    Get-CsMobilityPolicy -Filter "tag:*" | Remove-CsMobilityPolicy

## 예제 3

예제 3에서는 회사번호로 전화 기능이 사용하도록 설정된 모든 모바일 정책을 삭제하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsMobilityPolicy** cmdlet을 사용하여 조직에서 현재 사용 중인 모든 모바일 정책 컬렉션을 검색합니다. 그런 다음 이 컬렉션은 EnableOutsideVoice 속성이 False로 설정된 정책만 선택하는 where-Object cmdlet에 파이프됩니다. 그러면 EnableOutsideVoice가 False인 모든 정책이 **Remove-CsMobilityPolicy** cmdlet에 파이프되고 이 cmdlet에 의해 제거됩니다.

    Get-CsMobilityPolicy | Where-Object {$_.EnableOutsideVoice -eq $False} | Remove-CsMobilityPolicy

## 자세한 정보

Lync Mobile은 사용자가 휴대폰에서 Lync를 실행할 수 있도록 하는 클라이언트 응용 프로그램입니다. 회사번호로 전화 기능을 사용하면 휴대폰에서 전화를 걸지만 해당 휴대폰 번호 대신 회사 전화 번호에서 전화가 걸려 온 것처럼 보이게 할 수 있습니다. 회사번호로 전화 기능을 사용하도록 설정된 사용자는 이를 위해 휴대폰에서 직접 전화를 걸거나 외부 전화 접속 회의 옵션을 사용하면 됩니다. 외부 전화 접속 회의의 경우 사용자는 Mobility Service 서버에서 자동으로 전화를 걸도록 할 수 있습니다. 그러면 서버에서는 통화를 설정한 다음 해당 휴대폰으로 다시 사용자에게 전화를 겁니다. 그리고 사용자가 응답하면 서버에서는 통화하는 상대방에게 전화를 겁니다. 이 두 기능은 모두 모바일 정책을 사용하여 관리할 수 있습니다.

Lync Server 2013이 설치된 모바일 장치에서는 표준 휴대폰 네트워크 또는 Wi-Fi 연결을 사용하여 전화를 걸거나 받을 수 있습니다. 모바일 정책을 통해 Wi-Fi 연결을 사용하도록 지정하고 셀룰러 네트워크를 통해서는 통화를 할 수 없도록 차단할 수 있습니다.

Lync Server를 설치하면 모든 사용자에게 적용되는 단일 전역 모바일 정책을 얻게 됩니다. 하지만 관리자는 **New-CsMobilityPolicy** cmdlet을 사용하여 사이트 또는 사용자별 범위에 사용자 지정 정책을 만들 수 있습니다.

사이트 범위나 사용자별 범위에 사용자 지정 정책을 만드는 경우 나중에 **Remove-CsMobilityPolicy** cmdlet을 사용하여 이러한 정책을 삭제할 수 있습니다. 사용자별 정책을 삭제하는 경우 이러한 정책이 할당된 사용자는 적절한 사이트 정책(있는 경우)이나 전역 정책을 통해 관리됩니다. 사이트 정책을 제거하면 이러한 정책을 통해 관리되는 사용자가 전역 정책을 통해 관리됩니다.

전역 정책에 대해서도 **Remove-CsMobilityPolicy** cmdlet을 실행할 수 있습니다. 하지만 이 경우 전역 정책이 실제로 삭제되는 대신 전역 정책의 속성이 기본값으로 다시 설정됩니다. 이렇게 되면 회사번호로 전화 기능이 사용하도록 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsMobilityPolicy** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>제거할 클라이언트 정책의 고유 식별자입니다. 전역 정책을 &quot;제거&quot;하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity global</p>
<p>하지만 전역 정책은 실제로는 제거할 수 없습니다. 대신 전역 정책의 모든 속성이 기본값으로 다시 설정됩니다.</p>
<p>사이트 정책을 제거하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>사용자별 정책을 제거하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;SalesDepartmentPolicy&quot;</p>
<p>정책 ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 현재 하나 이상의 사용자에게 할당된 경우에도 정책이 자동으로 제거됩니다. 이 매개 변수가 없으면 <strong>Remove-CsMobilityPolicy</strong> cmdlet에서 하나 이상의 사용자에게 할당된 사용자별 정책을 자동으로 제거하지 않습니다. 대신 정책을 제거할 것인지 확인하는 확인 메시지가 표시됩니다. Y 키를 눌러 예라고 응답해야 명령이 계속되고 정책이 제거됩니다.</p>
<p>이 매개 변수는 사용자별 정책에만 적용됩니다.</p></td>
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

Microsoft.Rtc.Management.WriteableConfig.Policy.Mobility.Mobility. **Remove-CsMobilityPolicy** cmdlet은 이동성 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsMobilityPolicy** cmdlet은 Microsoft.Rtc.Management.WriteableConfig.Policy.Mobility.Mobility 개체의 인스턴스를 삭제합니다.

