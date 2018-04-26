---
title: Clear-CsPersistentChatRoom
TOCTitle: Clear-CsPersistentChatRoom
ms:assetid: 6b7801d8-d924-4e97-9b17-ceb6a263a7a7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204976(v=OCS.15)
ms:contentKeyID: 49303937
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Clear-CsPersistentChatRoom

 

_**마지막으로 수정된 항목:** 2015-03-09_

영구 채팅방에서 가장 오래된 항목부터 지정된 종료 날짜까지의 모든 콘텐츠를 제거합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Clear-CsPersistentChatRoom -Identity <String> <COMMON PARAMETERS>

    Clear-CsPersistentChatRoom -Instance <ChatRoom> <COMMON PARAMETERS>

    COMMON PARAMETERS: -EndDate <DateTime> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제에 표시된 명령은 영구 채팅방 ITChatRoom에서 2012년 3월 1일 또는 그 전에 채팅방에 추가된 모든 콘텐츠를 제거합니다.

    Clear-CsPersistentChatRoom -Identity "atl-cs-001.litwareinc.com\ITChatRoom" -EndDate "3/1/2012"

## 예제 2

예제 2에서는 조직의 모든 채팅방에서 2012년 3월 1일 또는 그 전에 추가된 콘텐츠를 제거합니다. 이를 위해 명령은 먼저 매개 변수 없이 **Get-CsPersistentChatRoom** cmdlet을 호출하여 조직의 모든 채팅방 컬렉션을 반환합니다. 해당 컬렉션은 **Clear-CsPersistentChatRoom** cmdlet에 파이프되며, 이 cmdlet은 컬렉션의 각 채팅방에서 2012년 3월 1일 또는 그 전에 추가된 콘텐츠를 제거합니다. 다른 채팅방의 콘텐츠를 지우려 할 때마다 표시되는 확인 메시지를 표시하지 않으려면 다음 구문을 사용하여 Confirm 매개 변수를 추가해야 합니다.

\-Confirm:$False

    Get-CsPersistentChatRoom | Clear-CsPersistentChatRoom -EndDate "3/1/2012" -Confirm:$False

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

영구 채팅 토론은 개별 채팅방에 게시되는 메시지 형식입니다. 즉, 채팅방은 특정 주제에 따른 토론 포럼이라 할 수 있습니다. 기본적으로 채팅방에 게시된 메시지는 계속 해당 채팅방에 남아 있으며 사용자는 언제든지 채팅방으로 돌아와 이전에 게시되었던 모든 메시지를 검토할 수 있습니다.

그러나 관리자가 채팅방에서 메시지를 모두 또는 일부분 지워야 하는 경우가 있습니다. 데이터베이스의 공간을 확보하거나 채팅방의 주제가 변경되는 경우를 예로 들 수 있습니다. 어떤 경우이든 **Clear-CsPersistentChatRoom** cmdlet을 사용하면 채팅방의 모든 메시지 또는 지정된 기간 동안 게시된 모든 메시지(예: 2012년 8월 1일 이전에 게시된 모든 메시지)를 삭제할 수 있습니다.

**참고**. 대상이 상세하게 지정된 메시지 집합(예: 특정 사용자가 게시한 모든 메시지)을 제거하려면 [Remove-CsPersistentChatMessage](remove-cspersistentchatmessage.md) cmdlet을 사용하세요.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Clear-CsPersistentChatRoom"}

**Lync Server 제어판:** **Clear-CsPersistentChatRoom** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>EndDate</em></p></td>
<td><p>필수</p></td>
<td><p>System.DateTime</p></td>
<td><p>콘텐츠를 제거할 기간의 마지막 날짜를 나타냅니다. 예를 들어 EndDate를 3/1/2012(영어(미국) 형식으로 2012년 3월 1일)로 지정하면 2012년 3월 1일 또는 그 전에 추가된 모든 영구 채팅 콘텐츠가 삭제됩니다.</p>
<p><strong>Clear-CsPersistentChatRoom</strong> cmdlet을 실행할 때는 EndDate를 지정해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>콘텐츠를 제거할 채팅방의 ID입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;atl-cs-001.litwareinc.com\ITChatRoom&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoom</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다. 이 매개 변수의 값을 False로 설정하면 cmdlet 실행 시 확인 메시지가 표시되지 않습니다.</p>
<p>-Confirm:$False</p></td>
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

**Clear-CsPersistentChatRoom** cmdlet은 Microsoft.Rtc.Management.GroupChat.Cmdlets.ChatRoomObject 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음.

## 참고 항목

#### 기타 리소스

[Remove-CsPersistentChatMessage](remove-cspersistentchatmessage.md)

