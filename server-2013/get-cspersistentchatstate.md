---
title: Get-CsPersistentChatState
TOCTitle: Get-CsPersistentChatState
ms:assetid: 598086c9-a8c7-4b81-84ba-1807f1183024
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204915(v=OCS.15)
ms:contentKeyID: 49303720
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPersistentChatState

 

_**마지막으로 수정된 항목:** 2015-03-09_

영구 채팅 서비스 풀 하나 이상의 상태를 반환합니다. 영구 채팅 풀은 Normal(풀이 기본 데이터베이스를 사용함) 또는 FailedOver(풀이 토폴로지에 정의된 백업 데이터베이스를 사용함)의 두 가지 상태 중 하나일 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsPersistentChatState [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsPersistentChatState [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 영구 채팅 서버의 상태를 반환합니다.

    Get-CsPersistentChatState

## 예제 2

    Get-CsPersistentChatState -Identity "PersistentChatServer:atl-gc-001.litwareinc.com"

## 예제 3

예제 3에서는 litwareinc.com 도메인의 모든 영구 채팅 서버에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수와 필터 값 "\*.litwareinc.com"을 포함합니다. 이 필터 값을 포함하면 **Get-CsPersistentChatState** cmdlet은 ID가 문자열 값 ".litwareinc.com"으로 끝나는 모든 영구 채팅 서버에 대한 정보를 반환합니다.

    Get-CsPersistentChatState -Filter "*.litwareinc.com"

## 예제 4

예제 4에 표시된 명령은 현재 장애 조치(failover)된 모든 영구 채팅 서버의 상태 정보를 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 매개 변수 없이 **Get-CsPersistentChatState** cmdlet을 호출합니다. 그러면 조직의 모든 영구 채팅 서버 컬렉션이 반환됩니다. 그런 다음 해당 컬렉션은 PoolState 속성이 "FailedOver"와 같은(-eq) 서버만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsPersistentChatState | Where-Object {$_.PoolState -eq "FailedOver"}

## 자세한 정보

**Get-CsPersistentChatState** cmdlet은 영구 채팅 풀 하나 이상의 상태를 반환합니다. 영구 채팅 풀은 Normal 상태(풀이 기본 데이터베이스를 사용함) 또는 FailedOver 상태(풀이 백업 데이터베이스를 사용함)일 수 있습니다. [Set-CsPersistentChatState](set-cspersistentchatstate.md) cmdlet을 사용하면 영구 채팅 풀의 상태를 변경할 수 있습니다. 풀 상태를 변경하면 Lync Server 2013에서는 풀의 개별 서버 상태를 자동으로 변경합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPersistentChatState"}

**Lync Server 제어판:** **Get-CsPersistentChatState** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>하나 이상의 영구 채팅 상태를 검색할 때 와일드카드를 사용할 수 있습니다. 예를 들어 litwareinc.com 도메인에 대해 모든 영구 채팅 상태를 반환하려면 다음 구문을 사용합니다.</p>
<p>-Filter &quot;*.litwareinc.com&quot;</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>영구 채팅 풀의 고유 식별자입니다. 예를 들면 다음과 같습니다.</p>
<p>–Identity &quot;PersistentChatServer:atl-gc-001.litwareinc.com&quot;</p>
<p>이 매개 변수를 생략하면 <strong>Get-CsPersistentChatState</strong> cmdlet은 모든 영구 채팅 상태에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 영구 채팅 상태 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsPersistentChatState** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsPersistentChatState** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatState 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Set-CsPersistentChatState](set-cspersistentchatstate.md)

