---
title: Set-CsPersistentChatRoom
TOCTitle: Set-CsPersistentChatRoom
ms:assetid: 3774931e-74a9-4189-9dde-3baae2293138
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204801(v=OCS.15)
ms:contentKeyID: 49303304
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsPersistentChatRoom

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 영구 채팅방 하나를 수정합니다. 채팅방은 보통 특정 주제와 관련된 토론 포럼입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsPersistentChatRoom -Instance <ChatRoom> <COMMON PARAMETERS>

    Set-CsPersistentChatRoom -Identity <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Addin <String>] [-AsObject <SwitchParameter>] [-Category <String>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Disabled <$true | $false>] [-Force <SwitchParameter>] [-Invitations <False | Inherit>] [-Managers <PSListModifier>] [-Members <PSListModifier>] [-Name <String>] [-Presenters <PSListModifier>] [-Privacy <Open | Closed | Secret>] [-Type <Normal | Auditorium>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 atl-cs-001.litwareinc.com\\ITChatRoom인 영구 채팅방을 사용하지 않도록 설정합니다.

    Set-CsPersistentChatRoom -Identity "atl-cs-001.litwareinc.com\ITChatRoom" -Disabled $True

## 예제 2

예제 2에서는 atl-cs-001.litwareinc.com 풀에 있는 모든 영구 채팅방을 사용하지 않도록 설정합니다. 이 작업을 수행하기 위해 먼저 **Get-CsPersistentChatRoom** cmdlet 및 Identity 매개 변수를 사용하여 atl-cs-001.litwareinc.com 풀에 대해 구성된 모든 채팅방을 반환합니다. 이러한 채팅방은 각 채팅방의 Disabled 속성을 True($True)로 설정하는 **Set-CsPersistentChatRoom** cmdlet에 파이프됩니다.

    Get-CsPersistentChatRoom -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com" | Set-CsPersistentChatRoom -Disabled $True

## 예제 3

예제 3에서는 조직의 모든 영구 채팅방을 사용하지 않도록 설정합니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsPersistentChatRoom** cmdlet을 호출하여 모든 영구 채팅방의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 채팅방을 사용하지 않도록 설정하는 **Set-CsPersistentChatRoom** cmdlet에 파이프됩니다.

    Get-CsPersistentChatRoom | Set-CsPersistentChatRoom -Disabled $True

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

영구 채팅 토론은 개별 채팅방에 게시되는 메시지 형식입니다. 즉, 채팅방은 특정 주제에 따른 토론 포럼이라 할 수 있습니다. 기본적으로 채팅방에 게시된 메시지는 계속 해당 채팅방에 남아 있으며 사용자는 언제든지 채팅방으로 돌아와 이전에 게시되었던 모든 메시지를 검토할 수 있습니다.

**Set-CsPersistentChatRoom** cmdlet을 사용하면 조직에서 사용하도록 구성된 임의의 채팅방 또는 모든 채팅방을 수정할 수 있습니다. 여기에는 관리자와 발표자를 채팅방에 할당하는 작업도 포함됩니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsPersistentChatRoom"}

**Lync Server 제어판:**Lync Server 제어판을 사용하여 기존 영구 채팅방을 수정하려면 **영구 채팅**, **채팅방**을 차례로 클릭한 다음 수정할 채팅방을 두 번 클릭합니다.

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
<td><p>System.String</p></td>
<td><p>수정할 영구 채팅방의 고유 식별자입니다. 채팅방의 ID는 채팅방이 구성된 영구 채팅 풀과 채팅방의 이름으로 구성됩니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;atl-gc-001.litwareinc.com\RedmondChatRoom&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoom</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Addin</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>채팅방과 연결된 영구 채팅 추가 기능(있는 경우)의 이름입니다. 영구 채팅 추가 기능은 영구 채팅 클라이언트 내에 포함할 수 있는 사용자 지정된 웹 페이지입니다. <strong>New-CsPersistentChatAddin</strong> cmdlet을 사용하여 추가 기능을 만들 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AsObject</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 Managers 또는 Presenters 목록에 사용자를 추가하거나 목록에서 사용자를 제거할 때 Active Directory 표시 이름이 사용됩니다. 이 매개 변수를 지정하지 않으면 이러한 목록을 관리할 때 SIP 주소가 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Category</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>채팅방이 속하는 범주입니다. 예를 들면 다음과 같습니다.</p>
<p>-Category &quot;IT&quot;</p>
<p>지정한 범주가 존재해야 하며, 그렇지 않으면 명령이 실패합니다. 채팅방의 컬렉션인 범주는 <strong>New-CsPersistentChatCategory</strong> cmdlet을 사용하여 만들 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 새 채팅방에 대한 추가 정보를 제공할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Disabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True($True)로 설정하면 새 채팅방이 사용하지 않도록 설정되며 처음 만들 때 사용할 수 없는 상태가 됩니다. 이 매개 변수를 사용하지 않으면 새 채팅방이 사용하도록 설정되며 즉시 사용 가능한 상태가 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Invitations</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoomInvitations</p></td>
<td><p>채팅방 초대를 범주로부터 상속할지 여부를 지정합니다. True로 설정하면 새 채팅방을 만들 때 Members 목록의 사용자가 새 채팅방에 참가하라는 초대를 자동으로 받게 됩니다. False로 설정하면 채팅방에 대해 초대가 사용되지 않습니다. Inherit로 설정하면 채팅방은 해당 범주에 대해 지정된 초대 설정을 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Managers</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>채팅방 구성원 자격을 정의하고 채팅방에 대한 기타 설정을 구성하도록 허용되는 사용자의 목록입니다.</p>
<p>Managers 목록에 새 사용자를 추가하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Managers @{Add=&quot;sip:kenmyer@litwareinc.com&quot;}</p>
<p>다음과 같이 사용자 SIP 주소를 쉼표로 구분하면 여러 사용자를 추가할 수 있습니다.</p>
<p>-Managers @{Add=&quot;sip:kenmyer@litwareinc.com&quot;, &quot;sip:pilar@litwareinc.com&quot;}</p>
<p>Managers 목록에서 사용자를 제거하려면 Remove 메서드를 사용합니다.</p>
<p>-Managers @{Remove=&quot;sip:kenmyer@litwareinc.com&quot;}</p>
<p>Managers 목록에서 모든 사용자를 제거하려면 Managers 속성의 값을 null로 설정합니다.</p>
<p>-Managers $Null</p>
<p>개별 사용자뿐 아니라 전체 OU에 대해서도 이러한 작업을 수행할 수 있습니다. 예를 들어 다음 명령은 IT OU의 모든 사용자를 Managers 목록에 추가합니다.</p>
<p>-Managers @{Add=&quot;OU=IT,DC=litwareinc,DC=com&quot;}</p>
<p>메일 그룹의 모든 사용자를 채팅방 관리자로 지정하려면 해당 메일 그룹의 Active Directory 고유 이름을 사용합니다.</p>
<p>-Managers @{Add=&quot;CN=ChatSupportGroup,OU=IT,DC=litwareinc,DC=com&quot;}</p></td>
</tr>
<tr class="even">
<td><p><em>Members</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>채팅방 액세스가 허용되는 사용자의 목록입니다. Members 속성이 null이면 채팅방은 해당하는 영구 채팅 범주의 구성원 자격 목록을 상속합니다.</p>
<p>Members 목록에 새 사용자를 추가하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Members @{Add=&quot;sip:kenmyer@litwareinc.com&quot;}</p>
<p>다음과 같이 사용자 SIP 주소를 쉼표로 구분하면 여러 사용자를 추가할 수 있습니다.</p>
<p>-Members @{Add=&quot;sip:kenmyer@litwareinc.com&quot;, &quot;sip:pilar@litwareinc.com&quot;}</p>
<p>Members 목록에서 사용자를 제거하려면 Remove 메서드를 사용합니다.</p>
<p>-Members @{Remove=&quot;sip:kenmyer@litwareinc.com&quot;}</p>
<p>Members 목록에서 모든 사용자를 제거하려면 Members 속성의 값을 null로 설정합니다.</p>
<p>-Members $Null</p>
<p>개별 사용자뿐 아니라 전체 OU에 대해서도 이러한 작업을 수행할 수 있습니다. 예를 들어 다음 명령은 IT OU의 모든 사용자를 Members 목록에 추가합니다.</p>
<p>-Members @{Add=&quot;OU=IT,DC=litwareinc,DC=com&quot;}</p>
<p>메일 그룹의 모든 사용자를 채팅방 구성원으로 지정하려면 해당 메일 그룹의 Active Directory 고유 이름을 사용합니다.</p>
<p>-Members @{Add=&quot;CN=ChatSupportGroup,OU=IT,DC=litwareinc,DC=com&quot;}</p></td>
</tr>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>영구 채팅방의 이름입니다. 이름은 각 영구 채팅 풀에서 고유해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Presenters</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>강당 채팅방에서 메시지 게시가 허용되는 사용자의 목록입니다.</p>
<p>Presenters 목록에 새 사용자를 추가하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Presenters @{Add=&quot;sip:kenmyer@litwareinc.com&quot;}</p>
<p>다음과 같이 사용자 SIP 주소를 쉼표로 구분하면 여러 사용자를 추가할 수 있습니다.</p>
<p>-Presenters @{Add=&quot;sip:kenmyer@litwareinc.com&quot;, &quot;sip:pilar@litwareinc.com&quot;}</p>
<p>Presenters 목록에서 사용자를 제거하려면 Remove 메서드를 사용합니다.</p>
<p>-Presenters @{Remove=&quot;sip:kenmyer@litwareinc.com&quot;}</p>
<p>Presenters 목록에서 모든 사용자를 제거하려면 Presenters 속성의 값을 null로 설정합니다.</p>
<p>-Presenters $Null</p>
<p>개별 사용자뿐 아니라 전체 OU에 대해서도 이러한 작업을 수행할 수 있습니다. 예를 들어 다음 명령은 IT OU의 모든 사용자를 Presenters 목록에 추가합니다.</p>
<p>-Presenters @{Add=&quot;OU=IT,DC=litwareinc,DC=com&quot;}</p>
<p>메일 그룹의 모든 사용자를 채팅방 발표자로 지정하려면 해당 메일 그룹의 Active Directory 고유 이름을 사용합니다.</p>
<p>-Presenters @{Add=&quot;CN=ChatSupportGroup,OU=IT,DC=litwareinc,DC=com&quot;}</p></td>
</tr>
<tr class="odd">
<td><p><em>Privacy</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoomPrivacy</p></td>
<td><p>채팅방의 개인 정보 설정입니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Open(모든 사용자가 디렉터리 검색을 수행하여 채팅방을 찾을 수 있으며 누구나 채팅방 활동에 참가할 수 있음)</p>
<p>* Secret(채팅방 구성원만이 디렉터리 검색을 수행하여 채팅방을 찾을 수 있으며 구성원만이 채팅방 활동에 참가할 수 있음)</p>
<p>* Closed(모든 사용자가 디렉터리 검색을 수행하여 채팅방을 찾을 수는 있지만 구성원만이 채팅방 활동에 참가할 수 있음)</p></td>
</tr>
<tr class="even">
<td><p><em>Type</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoomType</p></td>
<td><p>채팅방이 일반 채팅방(모든 구성원이 메시지를 게시할 수 있음)으로 구성되는지 아니면 강당(발표자만 메시지를 게시할 수 있음)으로 구성되는지를 지정합니다. 예를 들면 다음과 같습니다.</p>
<p>-Type &quot;Auditorium&quot;</p>
<p>기본값은 Normal입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Set-CsPersistentChatRoom** cmdlet은 Microsoft.Rtc.Management.PersistentChat.Cmdlets.ChatRoomObject 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsPersistentChatRoom** cmdlet은 Microsoft.Rtc.Management.PersistentChat.Cmdlets.ChatRoomObject 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Clear-CsPersistentChatRoom](clear-cspersistentchatroom.md)  
[Get-CsPersistentChatRoom](get-cspersistentchatroom.md)  
[New-CsPersistentChatRoom](new-cspersistentchatroom.md)  
[Remove-CsPersistentChatRoom](remove-cspersistentchatroom.md)

