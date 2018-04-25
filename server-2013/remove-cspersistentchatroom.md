---
title: Remove-CsPersistentChatRoom
TOCTitle: Remove-CsPersistentChatRoom
ms:assetid: 04cadd5d-13dc-4de5-b0b5-8c2f9bbbc7a7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204639(v=OCS.15)
ms:contentKeyID: 49302663
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsPersistentChatRoom

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 영구 채팅방을 제거합니다. 채팅방은 보통 특정 주제와 관련된 토론 포럼입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsPersistentChatRoom -Identity <String> <COMMON PARAMETERS>

    Remove-CsPersistentChatRoom -Instance <ChatRoom> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 영구 채팅방 RedmondChatRoom을 제거합니다.

    Remove-CsPersistentChatRoom -Identity "atl-gc-001.litwareinc.com\RedmondChatRoom"

## 예제 2

예제 2에서는 조직에서 사용 중인 모든 영구 채팅방이 제거됩니다. 이를 위해 명령은 먼저 매개 변수 없이 **Get-CsPersistentChatRoom** cmdlet을 호출하여 사용 가능한 모든 채팅방의 컬렉션을 반환합니다. 이 컬렉션은 **Remove-CsPersistentChatRoom** cmdlet에 파이프되며, 이 cmdlet은 컬렉션의 각 채팅방을 삭제합니다.

    Get-CsPersistentChatRoom  | Remove-CsPersistentChatRoom

## 예제 3

예제 3에서는 "닫힌" 채팅방을 모두 제거합니다. 닫힌 채팅방이란 사용자가 디렉터리 검색을 수행하여 채팅방을 찾을 수는 있지만 구성원만이 채팅방 활동에 참가할 수 있음을 의미합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPersistentChatRoom** cmdlet 및 Privacy 매개 변수를 사용하여 모든 닫힌 채팅방의 컬렉션을 반환합니다. 이 컬렉션은 **Remove-CsPersistentChatConfiguration** cmdlet에 파이프되며, 이 cmdlet은 컬렉션의 각 채팅방을 삭제합니다.

    Get-CsPersistentChatRoom -Privacy "Closed"  | Remove-CsPersistentChatRoom

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

영구 채팅 토론은 개별 채팅방에 게시되는 메시지 형식입니다. 즉, 채팅방은 특정 주제에 따른 토론 포럼이라 할 수 있습니다. 기본적으로 채팅방에 게시된 메시지는 계속 해당 채팅방에 남아 있으며 사용자는 언제든지 채팅방으로 돌아와 이전에 게시되었던 모든 메시지를 검토할 수 있습니다.

관리자는 **Remove-CsPersistentChatRoom** cmdlet을 사용하여 조직에서 사용하도록 구성된 영구 채팅방을 하나 이상 제거할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsPersistentChatRoom"}

**Lync Server 제어판:** Lync Server 제어판을 사용하여 기존 영구 채팅방을 삭제하려면 **영구 채팅** , **방** 을 차례로 클릭하고 삭제할 채팅방을 선택합니다. 채팅방을 삭제하려면 **편집** , **삭제** 를 차례로 클릭합니다.

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
<td><p>제거되는 영구 채팅방의 고유 식별자입니다. 채팅방의 ID는 다음과 같이 채팅방이 구성된 영구 채팅 풀과 채팅방 이름으로 구성됩니다.</p>
<p>-Identity &quot;atl-gc-001.litwareinc.com\RedmondChatRoom&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoom</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
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

**Remove-CsPersistentChatRooms** cmdlet은 Microsoft.Rtc.Management.PersistentChat.Cmdlets.ChatRoomObject 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsPersistentChatRoom** cmdlet은 Microsoft.Rtc.Management.PersistentChat.Cmdlets.ChatRoomObject 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Clear-CsPersistentChatRoom](clear-cspersistentchatroom.md)  
[Get-CsPersistentChatRoom](get-cspersistentchatroom.md)  
[New-CsPersistentChatRoom](new-cspersistentchatroom.md)  
[Set-CsPersistentChatRoom](set-cspersistentchatroom.md)

