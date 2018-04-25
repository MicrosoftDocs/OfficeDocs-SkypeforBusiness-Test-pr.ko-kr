---
title: New-CsPersistentChatRoom
TOCTitle: New-CsPersistentChatRoom
ms:assetid: b00d353b-5b5b-40d6-b952-3c35170fbf8a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205166(v=OCS.15)
ms:contentKeyID: 49304735
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsPersistentChatRoom

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 영구 채팅방을 만듭니다. 채팅방은 보통 특정 주제와 관련된 토론 포럼입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsPersistentChatRoom -Category <String> -Name <String> [-Addin <String>] [-Description <String>] [-Disabled <$true | $false>] [-Invitations <False | Inherit>] [-PersistentChatPoolFqdn <String>] [-Privacy <Open | Closed | Secret>] [-Type <Normal | Auditorium>]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-cs-001.litwareinc.com 풀에서 ITChatRoom이라는 새 영구 채팅방을 만듭니다. 이 예제에서는 IT 범주에 채팅방을 추가합니다.

    New-CsPersistentChatRoom -Name "ITChatRoom" -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com"-Category "IT"

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

영구 채팅 토론은 개별 채팅방에 게시되는 메시지 형식입니다. 즉, 채팅방은 특정 주제에 따른 토론 포럼이라 할 수 있습니다. 기본적으로 채팅방에 게시된 메시지는 계속 해당 채팅방에 남아 있으며 사용자는 언제든지 채팅방으로 돌아와 이전에 게시되었던 모든 메시지를 검토할 수 있습니다.

관리자는 **New-CsPersistentChatRoom** cmdlet을 사용하여 새 영구 채팅방을 만들 수 있습니다. **New-CsPersistentChatRoom** cmdlet을 사용해도 채팅방의 모든 속성을 사용할 수 있는 것은 아닙니다. 예를 들어 이 cmdlet을 사용하여 채팅방 관리자 또는 발표자를 할당할 수는 없습니다. 관리자나 발표자를 할당하려면 채팅방을 만든 다음 [Set-CsPersistentChatRoom](set-cspersistentchatroom.md) cmdlet을 사용하여 할당을 수행해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsPersistentChatRoom"}

**Lync Server 제어판:** Lync Server 제어판을 사용하여 새 영구 채팅방을 만들려면 **영구 채팅** , **방** , **새로 만들기** 를 차례로 클릭합니다.

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
<td><p>채팅방을 만들 범주입니다. 예를 들면 다음과 같습니다.</p>
<p>-Category &quot;IT&quot;</p>
<p>지정한 범주가 존재해야 하며, 그렇지 않으면 명령이 실패합니다. 영구 채팅방의 컬렉션인 범주는 <strong>New-CsPersistentChatCategory</strong> cmdlet을 사용하여 만들 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 영구 채팅방의 이름입니다. 이름은 각 영구 채팅 풀에서 고유해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Addin</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>채팅방과 연결된 영구 채팅 추가 기능(있는 경우)의 이름입니다. 영구 채팅 추가 기능은 영구 채팅 클라이언트 내에 포함할 수 있는 사용자 지정된 웹 페이지입니다. <strong>New-CsPersistentChatAddin</strong> cmdlet을 사용하여 추가 기능을 만들 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 새 채팅방에 대한 추가 정보를 제공할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Disabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 매개 변수가 있으면 새 채팅방이 사용하지 않도록 설정되며 처음 만들 때 사용할 수 없는 상태가 됩니다. 이 매개 변수를 사용하지 않으면 새 채팅방이 사용하도록 설정되며 즉시 사용 가능한 상태가 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Invitations</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoomInvitations</p></td>
<td><p>새 채팅방에 대한 초대를 범주에서 상속할지 여부를 지정합니다. True로 설정하면 새 채팅방을 만들 때 AllowedMembers 목록의 사용자가 새 채팅방에 참가하라는 초대를 자동으로 받게 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PersistentChatPoolFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>새 채팅방을 배치할 영구 채팅 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-PersistentChatPoolFqdn &quot;atl-gc-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Privacy</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoomPrivacy</p></td>
<td><p>새 채팅방의 개인 정보 설정입니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Open(모든 사용자가 디렉터리 검색을 수행하여 채팅방을 찾을 수 있으며 누구나 채팅방 활동에 참가할 수 있음)</p>
<p>* Secret(채팅방 구성원만이 디렉터리 검색을 수행하여 채팅방을 찾을 수 있으며 구성원만이 채팅방 활동에 참가할 수 있음)</p>
<p>* Closed(모든 사용자가 디렉터리 검색을 수행하여 채팅방을 찾을 수는 있지만 구성원만이 채팅방 활동에 참가할 수 있음)</p></td>
</tr>
<tr class="odd">
<td><p><em>Type</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoomType</p></td>
<td><p>새 채팅방을 일반 채팅방(모든 구성원이 메시지를 게시할 수 있음)으로 구성해야 하는지 아니면 강당(발표자만 메시지를 게시할 수 있음)으로 구성해야 하는지를 지정합니다. 예를 들면 다음과 같습니다.</p>
<p>-Type &quot;Auditorium&quot;</p>
<p>기본값은 Normal입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsPersistentChatRoom** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsPersistentChatRoom** cmdlet은 Microsoft.Rtc.Management.PersistentChat.Cmdlets.ChatRoomObject 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Clear-CsPersistentChatRoom](clear-cspersistentchatroom.md)  
[Get-CsPersistentChatRoom](get-cspersistentchatroom.md)  
[Remove-CsPersistentChatRoom](remove-cspersistentchatroom.md)  
[Set-CsPersistentChatRoom](set-cspersistentchatroom.md)

