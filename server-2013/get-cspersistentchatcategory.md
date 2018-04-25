---
title: Get-CsPersistentChatCategory
TOCTitle: Get-CsPersistentChatCategory
ms:assetid: 2ec14091-cb05-4c4c-b091-b7e88f5ca3cf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204771(v=OCS.15)
ms:contentKeyID: 49303191
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPersistentChatCategory

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용 중인 영구 채팅 범주에 대한 정보를 반환합니다. 영구 채팅 범주는 영구 채팅방 컬렉션을 나타내며 각 채팅방은 범주와 연결해야 합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsPersistentChatCategory [-PersistentChatPoolFqdn <String>] <COMMON PARAMETERS>

    Get-CsPersistentChatCategory -Identity <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AsObject <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 영구 채팅 범주에 대한 정보를 반환합니다.

    Get-CsPersistentChatCategory

## 예제 2

예제 2에서는 atl-cs-001.litwareinc.com 풀에서 사용하도록 구성된 모든 영구 채팅 범주에 대한 정보를 반환합니다.

    Get-CsPersistentChatCategory -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com"

## 예제 3

예제 3에서는 Invites 속성이 False로 설정된 모든 영구 채팅 범주에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsPersistentChatCategory** cmdlet을 사용하여 모든 영구 채팅 범주의 컬렉션을 반환합니다. 이 컬렉션은 Invites 속성이 False($False)로 설정된 범주만 선택하는 Where-Object cmdlet에 파이프됩니다.

    Get-CsPersistentChatCategory | Where-Object {$_.Invites -eq $False}

## 예제 4

예제 4에서는 Ken Myer가 작성자 중 한 명으로 포함되어 있는 모든 영구 채팅 범주에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsPersistentChatCategory** cmdlet을 사용하여 모든 영구 채팅 범주의 컬렉션을 반환합니다. 이 컬렉션은 Creators 속성에 "Ken Myer"라는 이름이 포함된(-contains) 모든 범주를 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsPersistentChatCategory | Where-Object {$_.Creators -contains "Ken Myer"}

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

관리자는 영구 채팅 범주를 통해 영구 채팅방을 구성하고 관리할 수 있습니다. 즉, 관리자는 범주를 활용하여 관련 채팅방을 그룹화할 수 있습니다. 예를 들어 재무 부서에서 사용하는 모든 채팅방을 같은 범주에 그룹화할 수 있습니다. 마찬가지로 관리자는 범주를 통해 이러한 채팅방에 대한 사용 권한을 관리함으로써 채팅방 액세스가 허용되는 사용자와 거부되는 사용자, 그리고 범주 내에서 새 채팅방 만들기가 허용되는 사용자를 지정할 수 있습니다.

모든 채팅방은 범주에 속해야 하며, 범주를 할당하지 않고는 채팅방을 만들 수 없습니다. 즉, 먼저 범주를 하나 이상 만들어야 영구 채팅 구현에 채팅방을 추가할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPersistentChatCategory"}

**Lync Server 제어판:** Lync Server 제어판에서 영구 채팅 범주를 보려면 **영구 채팅**, **범주**를 차례로 클릭합니다.

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
<td><p><em>AsObject</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 AllowedMembers, DeniedMembers 또는 Creators 목록에 포함된 사람을 사용자에게 표시할 때 Active Directory 표시 이름이 사용됩니다. 이 매개 변수를 지정하지 않으면 해당 사용자를 표시할 때 SIP 주소가 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PersistentChatPoolFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>영구 채팅 범주를 호스트하는 영구 채팅 풀의 정규화된 도메인 이름입니다. Name 매개 변수를 포함하지 않고 PoolFqdn 매개 변수를 사용하는 경우에는 지정한 풀의 모든 영구 채팅 범주에 대한 정보가 반환됩니다. Name 매개 변수와 PoolFqdn 매개 변수를 모두 포함하지 않으면 모든 영구 채팅 범주에 대한 정보가 반환됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsPersistentChatCategory** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsPersistentChatCategory** cmdlet은 Microsoft.Rtc.Management.PersistentChat.Cmdlets.CategoryObject 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsPersistentChatCategory](new-cspersistentchatcategory.md)  
[Remove-CsPersistentChatCategory](remove-cspersistentchatcategory.md)  
[Set-CsPersistentChatCategory](set-cspersistentchatcategory.md)

