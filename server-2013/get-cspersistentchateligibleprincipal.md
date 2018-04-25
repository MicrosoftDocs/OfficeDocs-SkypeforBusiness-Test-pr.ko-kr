---
title: Get-CsPersistentChatEligiblePrincipal
TOCTitle: Get-CsPersistentChatEligiblePrincipal
ms:assetid: 541de778-3aca-4d3f-9d46-d9b6d8212987
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204891(v=OCS.15)
ms:contentKeyID: 49303651
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPersistentChatEligiblePrincipal

 

_**마지막으로 수정된 항목:** 2015-03-09_

영구 채팅 범주 또는 채팅방에 대해 적합한 보안 주체를 반환합니다. 적합한 보안 주체에는 채팅방 범주에 대해 허용되는 구성원/관리자와 허용되는 발표자(채팅방에만 해당)가 포함됩니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsPersistentChatEligiblePrincipal -Category <String> <COMMON PARAMETERS>

    Get-CsPersistentChatEligiblePrincipal -Room <String> [-Presenters <SwitchParameter>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Filter <String>] [-PersistentChatPoolFqdn <String>] [-ResultSize <Int32>]

## 예제

## 예제 1

예제 1에 표시된 명령은 영구 채팅 범주 ITChat의 적합한 보안 주체에 대한 정보를 반환합니다.

    Get-CsPersistentChatEligiblePrincipal -PersistentChatPoolFqdn "atl-persistentchat-001.litwareinc.com" -Category "ITChat"

## 예제 2

예제 2에서는 HelpDeskChatRoom 채팅방의 모든 적합한 발표자에 대한 정보를 반환합니다.

    Get-CsPersistentChatEligiblePrincipal -PersistentChatPoolFqdn "atl-persistentchat-001.litwareinc.com" -Room "HelpDeskChatRoom" -Presenters

## 예제 3

예제 3은 예제 2에 표시된 명령의 변형입니다. 그러나 이 예제에서는 사용자 계정을 나타내지 않는 영구 채팅 발표자에 대한 정보만 반환합니다. 이 작업을 수행하기 위해 **Get-CsPersistentChatEligiblePrincipal** cmdlet을 사용하여 HelpDeskChatRoom 채팅방의 모든 발표자를 반환합니다. 그런 다음 해당 컬렉션은 PersistentChatPrincipalType 속성이 "user"가 아닌(-ne) 발표자만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsPersistentChatEligiblePrincipal -PersistentChatPoolFqdn "atl-persistentchat-001.litwareinc.com" -Room "HelpDeskChatRoom" -Presenters | Where-Object {$_.PersistentChatPrincipalType -ne "user"}

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

채팅 범주를 사용하면 특정 사용자를 생성자, 즉 해당 범주 내에서 채팅방을 만들 수 있는 사용자로 지정할 수 있습니다. 마찬가지로 채팅방에서는 특정 사용자를 관리자 및/또는 발표자로 지정하는 옵션이 제공됩니다. 그러나 이러한 역할을 할당받으려면 해당하는 사용자가 지정된 범주/채팅방의 AllowedMembers 목록에 표시되어 있어야 합니다. [Get-CsPersistentChatRoom](get-cspersistentchatroom.md) cmdlet 및 [Get-CsPersistentChatCategory](get-cspersistentchatcategory.md) cmdlet을 사용하면 채팅방이나 범주의 허용 구성원 목록을 검색할 수 있습니다. 그러나 보안 그룹, OU 또는 도메인이 허용 구성원 목록에 추가된 경우에는 해당 보안 그룹, OU 또는 도메인의 사용자 이름이 표시되지 않습니다. 예를 들어 FinanceManagers 보안 그룹이 허용 목록에 있으면 FinanceManagers에 속하는 사용자의 이름이 표시되지 않으며 그룹 이름만 표시됩니다.

범주 또는 채팅방의 허용 구성원 목록에 있는 모든 사용자 이름뿐 아니라 해당 그룹 내의 모든 사용자 이름도 확인하려면 **Get-CsPersistentChatEligiblePrincipal** cmdlet을 대신 사용합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPersistentChatEligiblePrincipal"}

Lync Server 제어판: **Get-CsPersistentChatEligiblePrincipal** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Category</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>적합한 보안 주체를 반환할 그룹 채팅 범주의 이름입니다. <strong>Get-CsPersistentChatEligiblePrincipal</strong> cmdlet을 호출할 때는 Category 또는 Room 매개 변수를 사용해야 합니다. 그러나 같은 명령에서 두 매개 변수를 모두 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Room</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>적합한 보안 주체를 반환할 그룹 채팅방의 이름입니다. <strong>Get-CsPersistentChatEligiblePrincipal</strong> cmdlet을 호출할 때는 Category 또는 Room 매개 변수를 사용해야 합니다. 그러나 같은 명령에서 두 매개 변수를 모두 사용할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>와일드카드 검색을 사용하여 적합한 보안 주체를 필터링하는 방법을 제공합니다. 예를 들면 다음과 같습니다.</p>
<p>-Filter &quot;*smith*&quot;</p>
<p>Filter 매개 변수는 사용자 SIP 주소만 필터링할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PersistentChatPoolFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>영구 채팅 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-PersistentChatPoolFqdn &quot;atl-persistentchat-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>Presenters</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 명령에 포함하면 영구 채팅방에 대해 적합한 발표자가 반환되고, 포함하지 않으면 <strong>Get-CsPersistentChatEligiblePrincipal</strong> cmdlet은 적합한 구성원 및 관리자를 반환합니다.</p>
<p>이 매개 변수는 Room 매개 변수와 함께 사용해야 하며 강당으로 구성된 채팅방에 대한 정보만 반환할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ResultSize</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>cmdlet에서 반환되는 레코드 수를 제한하는 데 사용됩니다. 예를 들어 포리스트에 있는 사용자 수에 상관없이 7명의 영구 채팅 보안 주체를 반환하려면 ResultSize 매개 변수를 포함하고 매개 변수 값을 7로 설정합니다. 반환될 7명의 보안 주체를 지정하는 방법은 없습니다.</p>
<p>결과 크기는 0에서 2147483647(포함) 사이의 임의 정수로 설정할 수 있습니다. 0으로 설정할 경우 명령이 실행되지만 데이터가 반환되지 않습니다. ResultSize를 7로 설정했지만 포리스트에 보안 주체가 3개만 있는 경우 3개의 보안 주체가 반환된 다음 오류 없이 완료됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsPersistentChatEligiblePrincipal** cmdlet은 파이프라인된 데이터를 허용하지 않습니다.

## 반환 형식

**Get-CsPersistentChatEligiblePrincipal** cmdlet은 Microsoft.Rtc.Management.GroupChat.Cmdlets.ADPersistentChatPrincipal 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Set-CsPersistentChatCategory](set-cspersistentchatcategory.md)  
[New-CsPersistentChatRoom](new-cspersistentchatroom.md)

