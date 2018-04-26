---
title: Set-CsPersistentChatCategory
TOCTitle: Set-CsPersistentChatCategory
ms:assetid: 61f44b61-c1bb-46a8-af12-8d1c543fcda5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204952(v=OCS.15)
ms:contentKeyID: 49303819
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsPersistentChatCategory

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 영구 채팅 범주를 수정합니다. 영구 채팅 범주는 영구 채팅방 컬렉션을 나타내며 각 채팅방은 범주와 연결해야 합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsPersistentChatCategory -Instance <Category> <COMMON PARAMETERS>

    Set-CsPersistentChatCategory -Identity <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AllowedMembers <PSListModifier>] [-AsObject <SwitchParameter>] [-ChatHistory <$true | $false>] [-Confirm [<SwitchParameter>]] [-Creators <PSListModifier>] [-DeniedMembers <PSListModifier>] [-Description <String>] [-FileUpload <$true | $false>] [-Invitations <$true | $false>] [-Name <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 영구 채팅 범주 atl-cs-001.litwareinc.com\\helpdesk에 대해 파일을 업로드할 수 없도록 설정합니다.

    Set-CsPersistentChatCategory -Identity "atl-cs-001.litwareinc.com\helpdesk" -FileUpload $False

## 예제 2

예제 2에서는 조직에서 현재 사용 중인 모든 영구 채팅 범주에 대해 파일을 업로드할 수 없도록 설정합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsPersistentChatCategory** cmdlet을 호출하여 모든 영구 채팅 범주의 컬렉션을 반환합니다. 이 컬렉션의 범주는 각 범주에 대해 파일을 업로드할 수 없도록 설정하는 **Set-CsPersistentChatCategory** cmdlet에 파이프됩니다.

    Get-CsPersistentChatCategory | Set-CsPersistentChatCategory-FileUpload $False

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

관리자는 영구 채팅 범주를 통해 영구 채팅방을 구성하고 관리할 수 있습니다. 즉, 관리자는 범주를 활용하여 관련 채팅방을 그룹화할 수 있습니다. 예를 들어 재무 부서에서 사용하는 모든 채팅방을 같은 범주에 그룹화할 수 있습니다. 마찬가지로 관리자는 범주를 통해 이러한 채팅방에 대한 사용 권한을 관리함으로써 채팅방 액세스가 허용되는 사용자와 거부되는 사용자, 그리고 범주 내에서 새 채팅방 만들기가 허용되는 사용자를 지정할 수 있습니다.

모든 채팅방은 범주에 속해야 하며, 범주를 할당하지 않고는 채팅방을 만들 수 없습니다. 즉, 먼저 범주를 하나 이상 만들어야 영구 채팅 구현에 채팅방을 추가할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsPersistentChatCategory"}

**Lync Server 제어판:** Lync Server 제어판을 사용하여 기존 영구 채팅 범주를 수정하려면 **영구 채팅** , **범주** 를 차례로 클릭한 다음 수정할 범주를 두 번 클릭합니다.

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
<td><p>채팅방 범주의 고유 식별자입니다. ID는 범주가 있는 영구 채팅 풀에 범주 이름이 붙는 형식으로 구성됩니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;atl-gc-001.litwareinc.com\ITChat&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.Category</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowedMembers</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>범주 내에서 채팅방에 액세스할 수 있는 사용자를 나열합니다. Members 목록에 새 사용자를 추가하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Members @{Add=&quot;sip:kenmyer@litwareinc.com&quot;}</p>
<p>다음과 같이 사용자 SIP 주소를 쉼표로 구분하면 여러 사용자를 추가할 수 있습니다.</p>
<p>-Members @{Add=&quot;sip:kenmyer@litwareinc.com&quot;, &quot;sip:pilar@litwareinc.com&quot;}</p>
<p>Members 목록에서 사용자를 제거하려면 Remove 메서드를 사용합니다.</p>
<p>-Members @{Remove=&quot;sip:kenmyer@litwareinc.com&quot;}</p>
<p>Members 목록에서 모든 사용자를 제거하려면 Members 속성의 값을 null로 설정합니다.</p>
<p>-AllowedMembers $Null</p>
<p>개별 사용자뿐 아니라 전체 OU에 대해서도 이러한 작업을 수행할 수 있습니다. 예를 들어 다음 명령을 실행하면 IT OU의 모든 사용자가 채팅방에 액세스할 수 있습니다.</p>
<p>-Members @{Add=&quot;OU=IT,DC=litwareinc,DC=com&quot;}</p>
<p>메일 그룹의 모든 사용자를 추가하려면 해당 메일 그룹의 Active Directory 고유 이름을 사용합니다.</p>
<p>-Members @{Add=&quot;CN=ChatSupportGroup,OU=IT,DC=litwareinc,DC=com&quot;}</p></td>
</tr>
<tr class="even">
<td><p><em>AsObject</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 AllowedMembers, DeniedMembers 및 Creators 목록에 사용자를 추가하거나 목록에서 사용자를 제거할 때 Active Directory 표시 이름이 사용됩니다. 이 매개 변수를 지정하지 않으면 이러한 목록을 관리할 때 SIP 주소가 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ChatHistory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>False($False)로 설정하면 새 범주에 대해 채팅 기록 기능이 사용하지 않도록 설정됩니다. 일반적으로는 한 번 게시된 후 다시 참조할 필요가 없는 공지 사항용으로 사용되는 채팅방에 대해서만 채팅 기록을 사용하지 않도록 설정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Creators</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>범주 내에서 채팅방을 만들 수 있는 사용자를 나열합니다. Creators 목록에 새 사용자를 추가하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Creators @{Add=&quot;sip:kenmyer@litwareinc.com&quot;}</p>
<p>다음과 같이 사용자 SIP 주소를 쉼표로 구분하면 여러 사용자를 추가할 수 있습니다.</p>
<p>-Creators @{Add=&quot;sip:kenmyer@litwareinc.com&quot;, &quot;sip:pilar@litwareinc.com&quot;}</p>
<p>Creators 목록에서 사용자를 제거하려면 Remove 메서드를 사용합니다.</p>
<p>-Creators @{Remove=&quot;sip:kenmyer@litwareinc.com&quot;}</p>
<p>Creators 목록에서 모든 사용자를 제거하려면 Creators 속성의 값을 null로 설정합니다.</p>
<p>-Creators $Null</p>
<p>개별 사용자뿐 아니라 전체 OU에 대해서도 이러한 작업을 수행할 수 있습니다. 예를 들어 다음 명령을 실행하면 IT OU의 모든 사용자가 채팅방을 만들 수 있습니다.</p>
<p>-Creators @{Add=&quot;OU=IT,DC=litwareinc,DC=com&quot;}</p>
<p>메일 그룹의 모든 사용자를 추가하려면 해당 메일 그룹의 Active Directory 고유 이름을 사용합니다.</p>
<p>-Creators @{Add=&quot;CN=ChatSupportGroup.OU=IT,DC=litwareinc,DC=com&quot;}</p></td>
</tr>
<tr class="even">
<td><p><em>DeniedMembers</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>범주 내에서 채팅방에 액세스할 수 없는 사용자를 나열합니다. DeniedMembers 목록에 새 사용자를 추가하려면 다음과 같은 구문을 사용합니다.</p>
<p>-DeniedMembers @{Add=&quot;sip:kenmyer@litwareinc.com&quot;}</p>
<p>다음과 같이 사용자 SIP 주소를 쉼표로 구분하면 여러 사용자를 추가할 수 있습니다.</p>
<p>-DeniedMembers @{Add=&quot;sip:kenmyer@litwareinc.com&quot;, &quot;sip:pilar@litwareinc.com&quot;}</p>
<p>DeniedMembers 목록에서 사용자를 제거하려면 Remove 메서드를 사용합니다.</p>
<p>-DeniedMembers @{Remove=&quot;sip:kenmyer@litwareinc.com&quot;}</p>
<p>DeniedMembers 목록에서 모든 사용자를 제거하려면 DeniedMembers 속성의 값을 null로 설정합니다.</p>
<p>-DeniedMembers $Null</p>
<p>개별 사용자뿐 아니라 전체 OU에 대해서도 이러한 작업을 수행할 수 있습니다. 예를 들어 다음 명령을 실행하면 IT OU의 모든 사용자에 대해 채팅방 액세스가 거부됩니다.</p>
<p>-DeniedMembers @{Add=&quot;OU=IT,DC=litwareinc,DC=com&quot;}</p>
<p>메일 그룹의 모든 사용자에 대해 액세스를 거부하려면 해당 메일 그룹의 Active Directory 고유 이름을 사용합니다.</p>
<p>-DeniedMembers @{Add=&quot;CN=ChatSupportGroup.OU=IT,DC=litwareinc,DC=com&quot;}</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>영구 채팅 범주에 추가로 포함되는 텍스트입니다. 예를 들어 Description을 통해 범주의 용도와 해당 범주 내에서 찾을 수 있는 채팅방의 유형을 설명할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>FileUpload</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True($True)로 설정하면 해당 범주의 채팅방에 파일을 업로드할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Invitations</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>False($False)로 설정하면 범주에 대해 초대가 사용하도록 설정됩니다. True로 설정하면 새 채팅방을 만들 때 AllowedMembers 목록의 사용자가 새 채팅방에 참가하라는 초대를 자동으로 받게 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>영구 채팅 범주에 지정된 이름입니다. 이름은 각 영구 채팅 풀에서 고유해야 합니다.</p></td>
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

**Set-CsPersistentChatCategory** cmdlet은 Microsoft.Rtc.Management.PersistentChat.Cmdlets.CategoryObject 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsPersistentChatCategory** cmdlet은 Microsoft.Rtc.Management.PersistentChat.Cmdlets.CategoryObject 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPersistentChatCategory](get-cspersistentchatcategory.md)  
[New-CsPersistentChatCategory](new-cspersistentchatcategory.md)  
[Remove-CsPersistentChatCategory](remove-cspersistentchatcategory.md)

