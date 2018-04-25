---
title: Remove-CsPersistentChatAddin
TOCTitle: Remove-CsPersistentChatAddin
ms:assetid: e218e88a-326e-4405-ba58-4d34b41191b4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205350(v=OCS.15)
ms:contentKeyID: 49305304
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsPersistentChatAddin

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 영구 채팅 추가 기능을 제거합니다. 영구 채팅 추가 기능은 영구 채팅 클라이언트 내에 포함할 수 있는 사용자 지정된 웹 페이지입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsPersistentChatAddin -Identity <String> <COMMON PARAMETERS>

    Remove-CsPersistentChatAddin -Instance <Addin> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 atl-cs-001.litwareinc.com 풀에 있는 영구 채팅 추가 기능 ITChatAddin을 제거합니다.

    Remove-CsPersistentChatAddin -Identity "atl-cs-001.litwareinc.com\ITChatAddin"

## 예제 2

예제 2에 표시된 명령은 조직에서 현재 사용 중인 모든 영구 채팅 추가 기능을 제거합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPersistentChatAddin** cmdlet을 사용하여 현재 사용 중인 모든 영구 채팅 추가 기능의 컬렉션을 반환합니다. 이 컬렉션은 **Remove-CsPersistentChatAddin** cmdlet에 파이프되며, 해당 cmdlet은 컬렉션의 각 추가 기능을 삭제합니다.

    Get-CsPersistentChatAddin | Remove-CsPersistentChatAddin

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

영구 채팅방에 대한 확장 역할을 하는 추가 기능은 특정 채팅방과 연결된 외부 응용 프로그램입니다. 따라서 영구 채팅 자체에서는 항목이 기본 제공되지 않습니다. 예를 들어 지원 센터 채팅방에는 특정일의 지원 요청 상태가 표시되는 Silverlight 응용 프로그램 또는 웹 페이지로 연결되는 URL이 포함될 수 있습니다. Lync ServerWindows PowerShell 명령줄 인터페이스 cmdlet은 이러한 추가 기능을 만드는 기능을 제공하지 않으며, 대신 **CsPersistentChatAddin** cmdlet을 사용하여 채팅방에서 추가 기능을 연결하거나 연결을 해제합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsPersistentChatAddin"}

**Lync Server 제어판:** Lync Server 제어판을 사용하여 영구 채팅 추가 기능을 제거하려면 **영구 채팅** , **추가 기능** 을 차례로 클릭한 다음 제거할 추가 기능을 선택하고 **편집** , **삭제** 를 차례로 클릭합니다.

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
<td><p>제거할 영구 채팅 추가 기능의 고유 식별자입니다. ID는 추가 기능이 있는 영구 채팅 풀의 정규화된 도메인 이름, &quot;\&quot; 문자 및 추가 기능 이름으로 구성됩니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;atl-gc-001.litwareincom\ITPersistentChatAddin&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.Addin</p></td>
<td><p>개체에 대한 참조를 cmdlet에 전달할 수 있습니다.</p></td>
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
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다. 현재 하나 이상의 채팅방과 연결된 추가 기능의 제거를 시도하는 경우를 예로 들 수 있습니다.</p></td>
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

**Remove-CsPersistentChatAddin** cmdlet은 Microsoft.Rtc.Management.PersistentChat.Cmdlets.AddinObject 개체의 파이프라인된 인스턴스를 허용하며, 기존 추가 기능의 ID를 나타내는 문자열 값도 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsPersistentChatAddin** cmdlet은 Microsoft.Rtc.Management.PersistentChat.Cmdlets.AddinObject 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPersistentChatAddin](get-cspersistentchataddin.md)  
[New-CsPersistentChatAddin](new-cspersistentchataddin.md)  
[Set-CsPersistentChatAddin](set-cspersistentchataddin.md)

