---
title: Get-CsPersistentChatRoom
TOCTitle: Get-CsPersistentChatRoom
ms:assetid: 9826c44b-35a6-473e-97d4-952415d640d1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205123(v=OCS.15)
ms:contentKeyID: 49304468
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPersistentChatRoom

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 영구 채팅방에 대한 정보를 반환합니다. 채팅방은 보통 특정 주제와 관련된 토론 포럼입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsPersistentChatRoom [-Addin <String>] [-Category <String>] [-ChatContentExceedsMB <Int32>] [-Disabled <$true | $false>] [-Filter <String>] [-Invitations <False | Inherit>] [-Manager <String>] [-Member <String>] [-PersistentChatPoolFqdn <String>] [-Privacy <Open | Closed | Secret>] [-ResultSize <Int32>] [-SearchDescription <SwitchParameter>] [-Type <Normal | Auditorium>] <COMMON PARAMETERS>

    Get-CsPersistentChatRoom [-Identity <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AsObject <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 영구 채팅방에 대한 정보를 반환합니다.

    Get-CsPersistentChatRoom

## 예제 2

예제 2에서는 단일 영구 채팅방, 즉 ID가 atl-cs-001.litwareinc.com\\ITChatRoom인 채팅방에 대한 정보를 반환합니다.

    Get-CsPersistentChatRoom -Identity "atl-cs-001.litwareinc.com\ITChatRoom"

## 예제 3

예제 3에서는 atl-cs-001.litwareinc.com 풀용으로 구성된 모든 영구 채팅방에 대한 정보를 반환합니다.

    Get-CsPersistentChatRoom -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com"

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

영구 채팅 토론은 개별 채팅방에 게시되는 메시지 형식입니다. 즉, 채팅방은 특정 주제에 따른 토론 포럼이라 할 수 있습니다. 기본적으로 채팅방에 게시된 메시지는 계속 해당 채팅방에 남아 있으며 사용자는 언제든지 채팅방으로 돌아와 이전에 게시되었던 모든 메시지를 검토할 수 있습니다.

**Get-CsPersistentChatRoom** cmdlet을 사용하면 조직에서 사용하도록 구성된 모든 채팅방에 대한 정보를 반환할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPersistentChatRoom"}

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
<td><p><em>Addin</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>지정한 채팅방 추가 기능과 연결된 채팅방을 반환합니다.</p>
<p>추가 기능은 명령당 하나만 지정할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AsObject</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 Managers 또는 Presenters 목록에 포함된 사람을 사용자에게 표시할 때 Active Directory 표시 이름이 사용됩니다. 이 매개 변수를 지정하지 않으면 해당 사용자를 표시할 때 SIP 주소가 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Category</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>지정된 범주의 모든 영구 채팅방에 대한 정보를 반환합니다. 예를 들면 다음과 같습니다.</p>
<p>-Category &quot;ITChat&quot;</p>
<p>Category 매개 변수를 사용할 때는 단일 범주만 지정할 수 있습니다. 또한 Category 매개 변수를 사용하는 명령에서는 PersistentChatPoolFqdn, Filter 또는 Identity 매개 변수를 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ChatContentExceedsMB</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>누적 채팅 콘텐츠가 지정된 값(MB)을 초과하는 채팅방을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Disabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>활성 채팅방(매개 변수 값 $False 사용) 또는 사용하지 않도록 설정된 채팅방(매개 변수 값 $True 사용)을 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>영구 채팅방의 이름 및/또는 설명을 기준으로 해당 채팅방에 대한 정보를 반환할 수 있습니다. 특정 이름의 채팅방에 대한 정보를 반환하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Filter {Name –like &quot;ITChat&quot;}</p>
<p>이 구문은 이름이 ITChat인 채팅방에 대한 정보만 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>반환되는 영구 채팅방의 고유 식별자입니다. 채팅방의 ID는 다음과 같이 채팅방이 구성된 영구 채팅 풀과 채팅방 이름으로 구성됩니다.</p>
<p>-Identity &quot;atl-gc-001.litwareinc.com\RedmondChatRoom&quot;</p>
<p>Identity 매개 변수를 사용하는 명령에서는 Category, Filter 또는 PersistentChatPoolFqdn 매개 변수를 사용할 수 없습니다. 매개 변수 없이 <strong>Get-CsPersistentChatRoom</strong> cmdlet을 호출하면 조직에서 사용하도록 구성된 모든 채팅방에 대한 정보가 반환됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Invitations</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoomInvitations</p></td>
<td><p>초대를 사용하는 채팅방(매개 변수 값 Inherit 사용) 또는 사용하지 않는 채팅방(매개 변수 값 False 사용)을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Manager</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>지정한 사용자가 관리하는 채팅방을 반환합니다. 예를 들면 다음과 같습니다.</p>
<p>-Manager &quot;sip:kenmyer@litwareinc.com&quot;</p>
<p>관리자는 명령당 한 명만 지정할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Member</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>지정한 사용자가 구성원인 채팅방을 반환합니다. 예를 들면 다음과 같습니다.</p>
<p>-Member &quot;sip:kenmyer@litwareinc.com&quot;</p>
<p>구성원은 명령당 한 명만 지정할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PersistentChatPoolFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>지정한 영구 채팅 풀에 구성된 모든 영구 채팅방에 대한 정보를 반환합니다. 예를 들면 다음과 같습니다.</p>
<p>-PersistentChatPoolFqdn &quot;atl-gc-001.litwareinc.com&quot;</p>
<p>PersistentChatPoolFqdn 매개 변수를 사용하는 명령에서는 Category, Filter 또는 Identity 매개 변수를 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Privacy</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoomPrivacy</p></td>
<td><p>지정한 개인 정보 설정을 충족하는 채팅방을 반환할 수 있습니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Open(모든 사용자가 디렉터리 검색을 수행하여 채팅방을 찾을 수 있으며 누구나 채팅방 활동에 참가할 수 있음)</p>
<p>* Secret(채팅방 구성원만이 디렉터리 검색을 수행하여 채팅방을 찾을 수 있으며 구성원만이 채팅방 활동에 참가할 수 있음)</p>
<p>* Closed(모든 사용자가 디렉터리 검색을 수행하여 채팅방을 찾을 수는 있지만 구성원만이 채팅방 활동에 참가할 수 있음)</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>cmdlet에서 반환되는 레코드 수를 제한할 수 있게 합니다. 예를 들어, 포리스트에 있는 채팅방 수에 상관없이 7개의 채팅방을 반환하려면 ResultSize 매개 변수를 포함하고 매개 변수 값을 7로 설정합니다. 반환될 7개의 채팅방을 지정하는 방법은 없습니다.</p>
<p>결과 크기는 0에서 2147483647(포함) 사이의 임의 정수로 설정할 수 있습니다. 0으로 설정할 경우 명령이 실행되지만 데이터가 반환되지 않습니다. ResultSize를 7로 설정했지만 포리스트에 채팅방이 3개만 있는 경우 3개의 채팅방이 반환된 다음 오류 없이 완료됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SearchDescription</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>채팅방 이름 또는 채팅방 설명의 지정된 텍스트 값을 검색할 수 있습니다. 이름과 설명을 모두 검색하려면 SearchDescription 매개 변수와 Filter 매개 변수를 모두 포함합니다. 예를 들면 다음과 같습니다.</p>
<p>-SearchDescription –Filter &quot;IT chat room&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>Type</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoomType</p></td>
<td><p>채팅방을 유형 기준으로 반환합니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Normal(모든 구성원이 메시지를 게시할 수 있는 채팅방)</p>
<p>* Auditorium(발표자만 메시지를 게시할 수 있는 채팅방)</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsPersistentChatRoom** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsPersistentChatRoom** cmdlet은 Microsoft.Rtc.Management.PersistentChat.Cmdlets.ChatRoomObject 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Clear-CsPersistentChatRoom](clear-cspersistentchatroom.md)  
[New-CsPersistentChatRoom](new-cspersistentchatroom.md)  
[Remove-CsPersistentChatRoom](remove-cspersistentchatroom.md)  
[Set-CsPersistentChatRoom](set-cspersistentchatroom.md)

