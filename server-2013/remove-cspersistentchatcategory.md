---
title: Remove-CsPersistentChatCategory
TOCTitle: Remove-CsPersistentChatCategory
ms:assetid: 09d2c1e6-07b6-47c2-b48f-f0c8bdfa1507
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204660(v=OCS.15)
ms:contentKeyID: 49302746
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsPersistentChatCategory

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 영구 채팅 범주를 제거합니다. 영구 채팅 범주는 영구 채팅방 컬렉션을 나타내며 각 채팅방은 범주와 연결해야 합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다. 범주는 비어 있지 않으면 제거할 수 없습니다. 즉, 범주를 제거하려면 해당 범주 내의 모든 채팅방을 먼저 제거해야 합니다.

## 구문

    Remove-CsPersistentChatCategory -Identity <String> <COMMON PARAMETERS>

    Remove-CsPersistentChatCategory -Instance <Category> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 "atl-cs-001.litwareinc.com\\helpdesk"인 영구 채팅 범주를 제거합니다.

    Remove-CsPersistentChatCategory -Identity "atl-cs-001.litwareinc.com\helpdesk"

## 예제 2

예제 2에서는 조직에서 현재 사용 중인 모든 영구 채팅 범주가 제거됩니다. 이를 위해 명령은 먼저 **Get-CsPersistentChatCategory** cmdlet을 사용하여 모든 영구 채팅 범주의 컬렉션을 검색합니다. 이 컬렉션은 **Remove-CsPersistentChatCategory** cmdlet에 파이프되며, 이 cmdlet은 컬렉션의 각 범주를 삭제합니다.

    Get-CsPersistentChatCategory | Remove-CsPersistentChatCategory

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

관리자는 영구 채팅 범주를 통해 영구 채팅방을 구성하고 관리할 수 있습니다. 즉, 관리자는 범주를 활용하여 관련 채팅방을 그룹화할 수 있습니다. 예를 들어 재무 부서에서 사용하는 모든 채팅방을 같은 범주에 그룹화할 수 있습니다. 마찬가지로 관리자는 범주를 통해 이러한 채팅방에 대한 사용 권한을 관리함으로써 채팅방 액세스가 허용되는 사용자와 거부되는 사용자, 그리고 범주 내에서 새 채팅방 만들기가 허용되는 사용자를 지정할 수 있습니다.

모든 채팅방은 범주에 속해야 하며, 범주를 할당하지 않고는 채팅방을 만들 수 없습니다. 즉, 먼저 범주를 하나 이상 만들어야 영구 채팅 구현에 채팅방을 추가할 수 있습니다.

**Remove-CsPersistentChatCategory** cmdlet을 사용하면 영구 채팅 범주를 제거할 수 있습니다. 범주는 비어 있어야 제거할 수 있습니다. 즉, 범주 자체를 제거하려면 해당 범주 내의 모든 채팅방을 먼저 제거해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsPersistentChatCategory"}

**Lync Server 제어판:** Lync Server 제어판을 사용하여 영구 채팅 범주를 제거하려면 **영구 채팅** , **범주** 를 차례로 클릭한 다음 제거할 범주를 선택하고 **편집** , **삭제** 를 차례로 클릭합니다.

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
<td><p>제거할 영구 채팅 범주의 고유 식별자입니다. ID는 PoolFqdn과 범주 이름으로 구성됩니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;atl-cs-001.litwareinc.com\helpdesk&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.Category</p></td>
<td><p>개체에 대한 참조를 cmdlet에 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Remove-CsPersistentChatCategory** cmdlet은 Microsoft.Rtc.Management.PersistentChat.Cmdlets.CategoryObject 개체의 파이프라인된 인스턴스를 허용합니다. 이 cmdlet은 기존 영구 채팅 범주의 ID를 나타내는 문자열 값도 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsPersistentChatCategory** cmdlet은 Microsoft.Rtc.Management.PersistentChat.Cmdlets.CategoryObject 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPersistentChatCategory](get-cspersistentchatcategory.md)  
[New-CsPersistentChatCategory](new-cspersistentchatcategory.md)  
[Set-CsPersistentChatCategory](set-cspersistentchatcategory.md)

