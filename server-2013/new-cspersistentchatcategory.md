---
title: New-CsPersistentChatCategory
TOCTitle: New-CsPersistentChatCategory
ms:assetid: 37a6f55d-0fec-480f-8d96-60c313a48c74
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204803(v=OCS.15)
ms:contentKeyID: 49303313
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsPersistentChatCategory

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 영구 채팅 범주를 만듭니다. 영구 채팅 범주는 영구 채팅방의 컬렉션을 나타냅니다. 각 채팅방은 범주와 연결되어야 합니다. 범주를 만들 때는 해당 범주에 채팅방을 할당할 수 없으며, 대신 **Set-CsPersistentChatRoom** cmdlet을 사용하여 나중에 기존 채팅방을 범주에 할당해야 합니다. 그러나 새 채팅방을 만들 때 범주에 채팅방을 할당할 수는 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsPersistentChatCategory -Name <String> [-Description <String>] [-EnableFileUpload <SwitchParameter>] [-EnableInvitations <SwitchParameter>] [-PersistentChatPoolFqdn <String>] [-RemoveChatHistory <SwitchParameter>]

## 예제

## 예제 1

예제 1의 명령은 atl-cs-001.litwareinc.com 풀에서 HelpDesk라는 새 영구 채팅 범주를 만듭니다. 이 예제에서는 EnableFileUpload 매개 변수를 포함하여 파일을 업로드할 수 있도록 설정합니다.

    New-CsPersistentChatCategory -Name "HelpDesk" -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com" -EnableFileUpload 

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

관리자는 영구 채팅 범주를 통해 영구 채팅방을 구성하고 관리할 수 있습니다. 즉, 관리자는 범주를 활용하여 관련 채팅방을 그룹화할 수 있습니다. 예를 들어 재무 부서에서 사용하는 모든 채팅방을 같은 범주에 그룹화할 수 있습니다. 마찬가지로 관리자는 범주를 통해 이러한 채팅방에 대한 사용 권한을 관리함으로써 채팅방 액세스가 허용되는 사용자와 거부되는 사용자, 그리고 범주 내에서 새 채팅방 만들기가 허용되는 사용자를 지정할 수 있습니다.

모든 채팅방은 범주에 속해야 하며, 범주를 할당하지 않고는 채팅방을 만들 수 없습니다. 즉, 먼저 범주를 하나 이상 만들어야 영구 채팅 구현에 채팅방을 추가할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsPersistentChatCategory"}

**Lync Server 제어판:** Lync Server 제어판을 사용하여 새 영구 채팅 추가 범주를 만들려면 **영구 채팅** , **범주** , **새로 만들기**를 차례로 클릭합니다.

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
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>영구 채팅 범주에 지정된 이름입니다. 이름은 각 영구 채팅 풀에서 고유해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>영구 채팅 범주에 추가로 포함되는 텍스트입니다. 예를 들어 Description을 통해 범주의 용도와 해당 범주 내에서 찾을 수 있는 채팅방의 유형을 설명할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableFileUpload</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 해당 범주의 채팅방에 파일을 업로드할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableInvitations</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 포함하면 범주에 대해 초대가 사용하도록 설정됩니다. True로 설정하면 새 채팅방을 만들 때 AllowedMembers 목록의 사용자가 새 채팅방에 참가하라는 초대를 자동으로 받게 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PersistentChatPoolFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>범주를 만들 영구 채팅 풀의 정규화된 도메인 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>RemoveChatHistory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 포함하면 새 범주에 대해 채팅 기록 기능이 사용하지 않도록 설정됩니다. 일반적으로는 한 번 게시된 후 다시 참조하지 않는 공지 사항용으로 사용되는 채팅방에 대해서만 채팅 기록을 사용하지 않도록 설정합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsPersistentChatCategory** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsPersistentChatCategory** cmdlet은 Microsoft.Rtc.Management.PersistentChat.Cmdlets.CategoryObject 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsPersistentChatCategory](get-cspersistentchatcategory.md)  
[Remove-CsPersistentChatCategory](remove-cspersistentchatcategory.md)  
[Set-CsPersistentChatCategory](set-cspersistentchatcategory.md)

