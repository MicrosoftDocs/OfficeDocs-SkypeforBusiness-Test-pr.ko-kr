---
title: Grant-CsMobilityPolicy
TOCTitle: Grant-CsMobilityPolicy
ms:assetid: c5ca6d6c-e442-4375-b8fd-1016a0aef33b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690038(v=OCS.15)
ms:contentKeyID: 49304968
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Grant-CsMobilityPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자 또는 사용자 그룹에게 사용자별 모바일 정책을 부여합니다. 모바일 정책은 사용자가 Lync Mobile을 사용할 수 있는지 여부를 결정합니다. 또한 이러한 정책은 사용자가 회사번호로 전화를 거는 기능을 관리하는데, 이 기능을 사용하면 휴대폰에서 자신의 휴대폰 번호 대신 회사 전화 번호를 사용하여 전화를 걸고 받을 수 있습니다. 모바일 정책을 사용하여 전화를 걸고 받을 때 Wi-Fi 연결을 사용하도록 지정할 수도 있습니다. 이 cmdlet은 Lync Server 2010용 2011년 11월 누적 업데이트에서 도입되었습니다.

## 구문

    Grant-CsMobilityPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1의 명령은 한 명의 사용자 Ken Myer에게 사용자별 모바일 정책 RedmondMobilityPolicy를 할당합니다.

    Grant-CsMobilityPolicy -Identity "Ken Myer" -PolicyName "RedmondMobilityPolicy"

## 예제 2

예제 2에서는 모바일 정책 RedmondMobilityPolicy를 현재 정책 NorthAmericaMobilityPolicy를 통해 관리되고 있는 사용자에게 할당합니다. 이를 위해 이 명령에서는 먼저 **Get-CsUser** cmdlet과 Filter 매개 변수를 사용하여 정책 NorthAmericaMobilityPolicy가 할당된 모든 사용자를 검색합니다. 또한 이를 위해 필터 값 {MobilityPolicy –eq "NorthAmericaMobilityPolicy"}를 사용합니다. 사용자 계정 컬렉션을 검색한 후 이러한 계정은 각 사용자에게 정책 RedmondMobilityPolicy를 할당하는 **Grant-CsMobilityPolicy** cmdlet에 파이프됩니다.

    Get-CsUser -Filter {MobilityPolicy -eq "NorthAmericaMobilityPolicy"} | Grant-CsMobilityPolicy -PolicyName "RedmondMobilityPolicy"

## 예제 3

예제 3에서는 모바일 정책 RedmondMobilityPolicy를 Redmond 시에 위치한 모든 사용자에게 할당합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUser** cmdlet과 함께 LdapFilter 매개 변수를 호출합니다. 필터 값 "l=Redmond"는 Redmond에 위치한 모든 사용자를 반환합니다. 여기서 "l"은 Active Directory 특성인 "locality"를 나타냅니다. 사용자 계정을 검색한 후에는 이러한 계정이 **Grant-CsMobilityPolicy** cmdlet에 파이프됩니다. 또한 **Grant-CsMobilityPolicy** cmdlet은 각 사용자에게 정책 RedmondMobilityPolicy를 할당합니다.

    Get-CsUser -LdapFilter "l=Redmond" | Grant-CsMobilityPolicy -PolicyName "RedmondMobilityPolicy"

## 예제 4

예제 4에서는 atl-cs-001.litwareinc.com에 있는 Lync Server 계정을 가진 사용자에게 RedmondMobilityPolicy를 할당합니다. 이를 위해 명령에서는 먼저 **Get-CsUser** cmdlet과 Filter 매개 변수를 사용하여 지정된 등록자 풀에 있는 모든 사용자 계정을 검색합니다. 이 작업을 수행하려면 필터 값 {RegistrarPool –eq "atl-cs-001.litwareinc.com"}을 사용해야 합니다. 사용자 계정 컬렉션을 검색한 후에는 이러한 계정이 각 사용자에게 정책 RedmondMobilityPolicy를 할당하는 **Grant-CsMobilityPolicy** cmdlet에 파이프됩니다.

    Get-CsUser -Filter {RegistrarPool -eq "atl-cs-001.litwareinc.com"} | Grant-CsMobilityPolicy -PolicyName "RedmondMobilityPolicy"

## 자세한 정보

Lync Mobile은 사용자가 휴대폰에서 Lync를 실행할 수 있도록 하는 클라이언트 응용 프로그램입니다. 회사번호로 전화 기능을 사용하면 휴대폰에서 전화를 걸지만 해당 휴대폰 번호 대신 회사 전화 번호에서 전화가 걸려 온 것처럼 보이게 할 수 있습니다. 회사번호로 전화 기능을 사용하도록 설정된 사용자는 이를 위해 휴대폰에서 직접 전화를 걸거나 외부 전화 접속 회의 옵션을 사용하면 됩니다. 외부 전화 접속 회의의 경우 사용자는 Mobility Service 서버에서 자동으로 전화를 걸도록 할 수 있습니다. 그러면 서버에서는 통화를 설정한 다음 해당 휴대폰으로 다시 사용자에게 전화를 겁니다. 그리고 사용자가 응답하면 서버에서는 통화하는 상대방에게 전화를 겁니다. 이 두 기능은 모두 모바일 정책을 사용하여 관리할 수 있습니다.

Lync Server 2013이 설치된 모바일 장치에서는 표준 휴대폰 네트워크 또는 Wi-Fi 연결을 사용하여 전화를 걸거나 받을 수 있습니다. 모바일 정책을 통해 Wi-Fi 연결을 사용하도록 지정하고 셀룰러 네트워크를 통해서는 통화를 할 수 없도록 차단할 수 있습니다.

Lync Server를 설치하면 모든 사용자에게 적용되는 단일 전역 모바일 정책을 얻게 됩니다. 하지만 관리자는 **New-CsMobilityPolicy** cmdlet을 사용하여 사이트 또는 사용자별 범위에 사용자 지정 정책을 만들 수 있습니다.

사이트 범위에서 새 정책을 만들면 해당 정책이 적절한 사이트에 자동으로 할당됩니다. 하지만 사용자별 범위에서 모바일 정책을 만드는 경우 이러한 정책은 존재하기는 하지만 사용자에게 자동으로 할당되지 않습니다. 대신 **Grant-CsMobilityPolicy** cmdlet을 사용하여 한 명 이상의 사용자에게 사용자별 정책을 명확하게 할당해야 합니다.

**Get-CsUser** cmdlet을 실행할 때는 기본적으로 모바일 정책이 나타나지 않습니다. 따라서 다음과 같은 명령을 실행해서는 사용자에게 할당된 사용자별 모바일 정책을 확인할 수 없습니다.

Get-CsUser "Ken Myer"

대신 사용자에 대한 모든 속성 값(모바일 정책 포함)을 확인하려면 다음과 같은 명령을 사용해야 합니다.

Get-CsUser "Ken Myer" | Select-Object \*

또는 다음과 같은 명령을 사용하면 사용자의 표시 이름과 모바일 정책만 볼 수 있습니다.

Get-CsUser "Ken Myer" | Select-Object DisplayName, MobilityPolicy

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Grant-CsMobilityPolicy** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>사용자별 모바일 정책을 할당할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 일반적으로 네 가지 형식 중 하나를 사용하여 지정하는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 그리고 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 지정할 수도 있습니다.</p>
<p>또한 표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 문자열 값 &quot;Smith&quot;로 끝나는 모든 사용자에게 정책을 할당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PolicyName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>할당할 정책의 &quot;이름&quot;입니다. PolicyName은 간단히 말해 정책 ID에서 정책 범위(&quot;tag:&quot; 접두사)를 뺀 부분입니다. 예를 들어 Identity가 tag:Redmond인 정책의 PolicyName은 Redmond이고, Identity가 tag:RedmondUsersMobilityPolicy인 정책의 PolicyName은 RedmondUsersMobilityPolicy입니다. 사용자별 정책을 할당하려면 다음과 같은 구문을 사용합니다.</p>
<p>-PolicyName RedmondUsersMobilityPolicy</p>
<p>사용자에게 이전에 할당한 사용자별 정책을 할당 취소하려면 PolicyName을 null 값($Null)으로 설정합니다.</p>
<p>-PolicyName $Null</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>새 정책을 할당할 때 연결할 도메인 컨트롤러의 FQDN(정규화된 도메인 이름)을 지정하는 데 사용됩니다. 이 매개 변수를 지정하지 않으면 <strong>Grant-CsMobilityPolicy</strong> cmdlet은 사용 가능한 첫 번째 도메인 컨트롤러에 연결합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>정책을 할당할 사용자를 나타내는 사용자 개체를 파이프라인을 통해 전달하는 데 사용됩니다. 기본적으로 <strong>Grant-CsMobilityPolicy</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>실제로 명령을 수행하지는 않고 명령을 실행했을 때 발생할 결과에 대해 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Grant-CsMobilityPolicy** cmdlet은 사용자 계정의 ID를 나타내는 문자열 값의 파이프라인된 입력을 허용합니다. 또한 이 cmdlet은 사용자 개체의 파이프라인된 입력도 허용합니다.

## 반환 형식

기본적으로 **Grant-CsMobilityPolicy** cmdlet은 개체나 값을 반환하지 않습니다. 그러나 PassThru 매개 변수를 포함한 경우 이 cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSUserOrAppContact 개체의 파이프라인 인스턴스를 반환할 수 있습니다.

