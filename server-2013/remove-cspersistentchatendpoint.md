---
title: Remove-CsPersistentChatEndpoint
TOCTitle: Remove-CsPersistentChatEndpoint
ms:assetid: 0211850c-b4e7-4bb2-9a82-bfbfbd7de7b7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204626(v=OCS.15)
ms:contentKeyID: 49302618
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsPersistentChatEndpoint

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 영구 채팅 끝점을 제거합니다. 영구 채팅 끝점은 Lync Server 2013 영구 채팅 풀의 URL을 제공하는 Active Directory 대화 상대 개체입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsPersistentChatEndpoint -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 "sip:pce@litwareinc.com"인 영구 채팅 끝점을 삭제합니다. 이 예제에서는 SIP 주소가 ID로 사용됩니다.

    Remove-CsPersistentChatEndpoint -Identity "sip:pce@litwareinc.com"

## 예제 2

예제 2에서는 atl-pcpool-001.litwareinc.com 풀에 대해 구성된 모든 영구 채팅 끝점을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPersistentChatEndpoint** cmdlet 및 PoolFqdn 매개 변수를 사용하여 atl-pcpool-001.litwareinc.com 풀에 대한 모든 끝점을 반환합니다. 해당 컬렉션의 끝점은 Remove-CsPersistentChatEndpoint cmdlet에 파이프된 다음 **Remove-CsPersistentChatEndpoint** cmdlet에 의해 제거됩니다.

    Get-CsPersistentChatEndpoint -PoolFqdn "atl-pcpool-001.litwareinc.com" | Remove-CsPersistentChatEndpoint

## 예제 3

예제 3에 표시된 명령은 조직에서 사용하도록 구성된 모든 영구 채팅 끝점을 삭제합니다. 이를 위해 명령은 먼저 **Get-CsPersistentChatEndpoint** cmdlet을 호출하여 모든 영구 채팅 끝점 컬렉션을 반환합니다. 이 컬렉션은 **Remove-CsPersistentChatEndpoint** cmdlet에 파이프되며, 이 cmdlet은 컬렉션의 각 끝점을 삭제합니다.

    Get-CsPersistentChatEndpoint | Remove-CsPersistentChatEndpoint

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

그러나 Microsoft Lync 2010 등의 레거시 클라이언트를 실행하는 사용자가 있는 경우 해당 사용자는 레거시 클라이언트가 풀을 가리키도록 지정할 때 기본 영구 채팅 URI를 사용하기가 어려울 수 있습니다. 이러한 경우 관리자는 [New-CsPersistentChatEndpoint](new-cspersistentchatendpoint.md) cmdlet을 사용하여 풀에 대해 추가 대화 상대 개체, 즉 확인 및 사용이 보다 간편한 URI를 제공하는 대화 상대 개체를 만들 수 있습니다. 이러한 끝점은 나중에 **Remove-CsPersistentChatEndpoint** cmdlet을 사용하여 제거하면 됩니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsPersistentChatEndpoint"}

Lync Server 제어판: **Remove-CsPersistentChatEndpoint** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>제거할 영구 채팅 끝점의 고유 식별자입니다. 끝점 ID는 보통 다음과 같이 끝점의 SIP 주소나 표시 이름을 사용하여 지정됩니다.</p>
<p>-Identity &quot;sip:pcEndpoint1@litwareinc.com&quot;</p>
<p>그러나 다음과 같이 끝점의 전체 ID를 사용할 수도 있습니다.</p>
<p>-Identity &quot;CN={33e5014b-dcba-46b5-9bf7-48f4d5fca69d}, CN=Application Contacts,CN=RTC Service,CN=Services,CN=Configuration,DC=litwareinc,DC=com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
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

**Remove-CsPersistentChatEndpoint** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSPersistentChatContact 클래스의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. **Remove-CsPersistentChatEndpoint** cmdlet은 개체나 데이터를 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Get-CsPersistentChatEndpoint](get-cspersistentchatendpoint.md)  
[New-CsPersistentChatEndpoint](new-cspersistentchatendpoint.md)

