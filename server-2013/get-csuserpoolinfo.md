---
title: Get-CsUserPoolInfo
TOCTitle: Get-CsUserPoolInfo
ms:assetid: 7be81a85-c536-4d5c-b866-af7380e45c0f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398615(v=OCS.15)
ms:contentKeyID: 49304143
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsUserPoolInfo

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자가 할당된 등록자 풀, 백업 등록자 풀 및 사용자 서비스 풀에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsUserPoolInfo -Identity <UserIdParameter> [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

이 명령은 SIP 주소가 sip:kenmyer@litwareinc.com인 단일 사용자에 대한 사용자 풀 정보를 반환합니다.

    Get-CsUserPoolInfo "sip:kenmyer@litwareinc.com"

## 예제 2

예제 2에서는 Lync Server를 사용하도록 설정된 모든 사용자에 대한 사용자 풀 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsUser** cmdlet을 호출하여 Lync Server를 사용하는 모든 사용자의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 사용자에 대한 풀 정보를 표시하는 **Get-CsUserPoolInfo** cmdlet에 파이프됩니다.

    Get-CsUser | Get-CsUserPoolInfo

## 예제 3

예제 3에 표시된 명령은 예제 2에서 사용된 명령의 변형입니다. 예제 2에서는 Lync Server에 대해 활성화된 모든 사용자에 대한 풀 정보를 반환합니다. 그러나 Lync Server를 사용하도록 설정되었지만 등록자 풀에 할당되지 않은 사용자가 있을 수 있습니다. 예제 2에 표시된 명령은 이러한 조건을 충족하는 각 사용자에 대해 오류 메시지를 표시합니다. 예제 3에서는 이러한 오류 메시지를 표시하지 않습니다.

오류 메시지를 표시하지 않기 위해 예제 3에서는 다시 **Get-CsUser** cmdlet을 사용하여 Lync Server를 사용하는 모든 사용자의 컬렉션을 반환합니다. 이 컬렉션은 RegistrarPool 속성이 Null 값과 같지 않은 사용자, 즉 등록자 풀이 할당된 사용자만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 필터링된 컬렉션의 각 사용자에 대한 풀 정보를 표시하는 **Get-CsUserPoolInfo** cmdlet에 파이프됩니다.

    Get-CsUser | Where-Object {$_.RegistrarPool -ne $Null} | Get-CsUserPoolInfo

## 예제 4

예제 4에서는 redmond-cs-001.litwareinc.com이라는 기본 풀에 할당된 모든 사용자에 대해 풀 정보를 표시합니다. 이 작업을 수행하기 위해 Filter 매개 변수를 포함하여 **Get-CsUser** cmdlet을 호출합니다. 필터 값 {RegistrarPool -eq "redmond-cs-001.litwareinc.com"}은 RegistrarPool 속성의 정규화된 도메인 이름이 redmond-cs-001.litwareinc.com인 사용자만 반환합니다. 이 컬렉션은 컬렉션의 각 사용자에 대한 풀 정보를 검색하는 **Get-CsUserPoolInfo** cmdlet에 파이프됩니다.

    Get-CsUser -Filter {RegistrarPool -eq "redmond-cs-001.litwareinc.com"} | Get-CsUserPoolInfo

## 예제 5

예제 5에 표시된 명령은 백업 등록자 풀이 할당되지 않은 모든 사용자에 대한 풀 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUser** cmdlet을 호출하여 Lync Server를 사용하도록 설정된 모든 사용자의 컬렉션을 반환합니다. 이 정보는 컬렉션의 각 사용자에 대한 풀 정보를 검색하는 **Get-CsUserPoolInfo** cmdlet에 파이프됩니다. 그런 다음 이 풀 정보는 BackupClusterFqdn 속성이 Null 값과 같은 사용자에 대한 데이터만 표시하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsUser | Get-CsUserPoolInfo | Where-Object {$_.BackupPoolFqdn -eq $Null}

## 자세한 정보

Lync Server를 사용하도록 설정된 사용자는 등록자 풀에 속해 있어야 합니다. 이 풀은 사용자를 인증하고 사용자의 현재 상태 및 위치를 추적하는 역할을 합니다. 사용자가 할당된 등록자 풀을 확인하려면 다음과 같은 명령을 사용하여 해당 정보를 검색할 수 있습니다.

    Get-CsUser "Ken Myer" | Select-Object RegistrarPool

대부분의 경우 필요한 정보는 사용자의 등록자 풀을 확인하는 것이 전부일 수 있습니다. 그러나 다른 경우에는 사용자가 할당된 백업 등록자 풀(기본 등록자 풀을 사용할 수 없는 경우 사용되는 풀), 이러한 풀을 구성하는 개별 컴퓨터 이름 및 사용자가 할당된 사용자 서비스 풀과 같은 내용을 확인할 수 있습니다. 이러한 유형의 세부 정보는 **Get-CsUserPoolInfo** cmdlet을 실행하여 가져올 수 있습니다.

Lync Server 2013에서는 사용자의 주 풀 및 복제본 풀에 있는 주 프런트 엔드 서버에 대한 정보를 반환하도록 Get-CsUserPoolInfo cmdlet이 수정되었습니다. 풀에 프런트 엔드 서버가 여러 개 있으면 각 사용자가 라우팅 그룹에 할당되며, 라우팅 그룹은 주 프런트 엔드 서버 및 복제본 프런트 엔드 서버에 할당됩니다. 사용자는 로그온할 때 기본적으로 주 프런트 엔드 서버에 등록되며, Get-CsUserPoolInfo 출력에서 해당 서버는 PrimaryPoolPrimaryRegistrar로 나열됩니다. 사용자의 주 풀이 장애 조치(failover)된 경우에는 해당 사용자가 백업(복제본) 풀의 주 프런트 엔드 서버에 등록됩니다. 해당 서버는 출력에 BackupPoolPrimaryRegistrar로 나열됩니다.

복제본 정보는 사용자의 주 풀에 백업 풀이 할당된 경우에만 표시됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsUserPoolInfo** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsUserPoolInfo"}

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
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>사용자 풀 정보를 검색할 사용자의 ID를 나타냅니다. ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 도메인 서비스 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 계정을 참조할 수도 있습니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어, Identity &quot;* Smith&quot;는 문자열 값 &quot; Smith&quot;로 끝나는 성을 가진 사용자에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 사용자 풀 정보를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Get-CsUserPoolInfo** cmdlet은 Lync Server를 사용하도록 설정된 사용자 계정의 SamAccountName을 나타내는 파이프라인된 문자열 값을 허용합니다. 또한 Active Directory 사용자 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Get-CsUserPoolInfo** cmdlet은 Microsoft.Rtc.Management.Xds.GetOCsUserPoolInfoCmdlet+UserInformation 개체의 인스턴스를 반환합니다.

