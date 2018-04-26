---
title: Remove-CsPersistentChatMessage
TOCTitle: Remove-CsPersistentChatMessage
ms:assetid: 0cb53905-4608-44a9-ba3d-ba51fc90d65e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204668(v=OCS.15)
ms:contentKeyID: 49302791
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsPersistentChatMessage

 

_**마지막으로 수정된 항목:** 2015-03-09_

영구 채팅 데이터베이스에 있는 하나 이상의 영구 채팅 메시지를 기본 메시지 또는 관리자가 제공한 메시지로 바꿉니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsPersistentChatMessage -ReplaceMessage <String> [-CaseSensitive <$true | $false>] [-EndDate <DateTime>] [-Filter <String>] [-MatchClause <And | Or | Exact>] [-StartDate <DateTime>] [-UserUri <String>] <COMMON PARAMETERS>

    Remove-CsPersistentChatMessage -Remove <SwitchParameter> [-CaseSensitive <$true | $false>] [-EndDate <DateTime>] [-Filter <String>] [-MatchClause <And | Or | Exact>] [-StartDate <DateTime>] [-UserUri <String>] <COMMON PARAMETERS>

    Remove-CsPersistentChatMessage [-CaseSensitive <$true | $false>] [-EndDate <DateTime>] [-Filter <String>] [-MatchClause <And | Or | Exact>] [-StartDate <DateTime>] [-UserUri <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: -Identity <String> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-persistentchat-001.litwareinc.com 서버의 ITChatRoom 채팅방에서 2012년 4월 1일 또는 그 이전에 게시된 모든 영구 채팅 메시지를 제거합니다.

    Remove-CsPersistentChatMessage -Identity "atl-persistentchat-001.litwareinc.com\ITChatRoom" -EndDate "4/1/2012"

## 예제 2

예제 2에서는 atl-persistentchat-001.litwareinc.com 서버의 ITChatRoom 채팅방에서 사용자 kenmyer@litwareinc.com이 게시한 모든 영구 채팅 메시지를 제거합니다.

    Remove-CsPersistentChatMessage -Identity "atl-persistentchat-001.litwareinc.com\ITChatRoom" -UserUri "sip:kenmyer@litwareinc.com"

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

영구 채팅 토론은 개별 채팅방에 게시되는 메시지 형식입니다. 즉, 채팅방은 특정 주제에 따른 토론 포럼이라 할 수 있습니다. 기본적으로 채팅방에 게시된 메시지는 계속 해당 채팅방에 남아 있으며 사용자는 언제든지 채팅방으로 돌아와 이전에 게시되었던 모든 메시지를 검토할 수 있습니다.

그러나 관리자가 채팅방에서 메시지를 제거해야 하는 경우가 있습니다. 사용자가 예정된 회사 모임과 관련하여 잘못된 정보가 포함된 일련의 메시지를 게시한 경우를 예로 들 수 있습니다. 이 경우 관리자는 **Remove-CsPersisentChatMessage** cmdlet을 사용하여 채팅 메시지 하나를 제거하거나 메시지를 게시한 사용자, 해당 메시지에 포함된 키워드 등의 조건을 기준으로 전체 채팅 메시지 집합을 제거할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsPersistentChatMessage"}

**Lync Server 제어판:** **Remove-CsPersistentChatMessage** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>삭제할 메시지가 포함된 채팅방의 고유 식별자입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;atl-persistentchat-001.litwareinc.com\ITChatRoom&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Remove</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 대체 메시지를 남기지 않고 영구 채팅 메시지를 제거합니다.</p>
<p>같은 명령에서 Remove 매개 변수와 ReplaceMessage 매개 변수를 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ReplaceMessage</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 대체 메시지 텍스트를 지정할 수 있습니다. 기본적으로 대체 메시지는 &quot;This message was replaced by the Persistent Chat administrator.(이 메시지는 영구 채팅 관리자에 의해 대체되었습니다.)&quot;입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CaseSensitive</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 매개 변수가 있으면 제거할 메시지를 검색할 때 대/소문자를 구분해야 함을 나타냅니다. 즉, 대문자 &quot;A&quot;는 소문자 &quot;a&quot;와 다른 문자로 간주됩니다. 기본적으로 검색에서는 대/소문자를 구분하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EndDate</em></p></td>
<td><p>선택</p></td>
<td><p>System.DateTime</p></td>
<td><p>지정된 날짜 또는 그 이전에 게시된 메시지를 필터링할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>삭제할 메시지를 식별하는 데 사용할 수 있는 키워드입니다. 예를 들어 키워드 &quot;Fabrikam&quot;이 포함된 모든 메시지를 검색하려면 다음 구문을 사용합니다.</p>
<p>-Filter &quot;Fabrikam&quot;</p>
<p>여러 키워드를 검색하려면 모든 키워드를 한 문자열에 포함하고 공백으로 구분합니다.</p>
<p>-Filter &quot;Fabrikam Contoso TailspinToys&quot;</p>
<p>기본적으로 <strong>Remove-CsPersistentChatMessage</strong> cmdlet은 지정된 키워드를 모두 사용하여 메시지를 찾습니다. 제공된 키워드 중 하나만 사용하여 메시지를 찾으려면 MatchClause 매개 변수를 사용하고 매개 변수 값을 &quot;Or&quot;로 설정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MatchClause</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.RemoveOcsMessageChatCmdlet+AndOr</p></td>
<td><p><strong>Remove-CsPersistentChatMessage</strong> cmdlet이 여러 키워드를 처리하는 방법을 지정합니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* All(지정된 키워드를 모두 포함하는 메시지가 일치함)</p>
<p>* Or(지정된 키워드 중 하나 이상을 포함하는 메시지는 일치하는 것으로 간주됨)</p>
<p>* Exact(단어 순서를 포함하여 지정된 구와 정확히 일치하는 메시지가 일치함)</p>
<p>예를 들어 다음 구문은 메시지 텍스트에 &quot;For internal use only&quot; 구가 정확하게 포함된 메시지를 검색합니다.</p>
<p>-Filter &quot;For internal use only&quot; –MatchClause &quot;Exact&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>StartDate</em></p></td>
<td><p>선택</p></td>
<td><p>System.DateTime</p></td>
<td><p>지정된 날짜 또는 그 이후에 게시된 메시지를 필터링할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>제거할 메시지를 게시한 사용자의 SIP 주소입니다.</p></td>
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

없음. **Remove-CsPersistentChatMessage** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음.

## 참고 항목

#### 기타 리소스

[Clear-CsPersistentChatRoom](clear-cspersistentchatroom.md)

