---
title: Get-CsPersistentChatAddin
TOCTitle: Get-CsPersistentChatAddin
ms:assetid: 0d6b3283-c73d-4b83-b0f8-8f03aa4bba14
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204670(v=OCS.15)
ms:contentKeyID: 49302796
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPersistentChatAddin

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 모든 영구 채팅 추가 기능에 대한 정보를 반환합니다. 영구 채팅 추가 기능은 영구 채팅 클라이언트 내에 포함할 수 있는 사용자 지정된 웹 페이지입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsPersistentChatAddin [-PersistentChatPoolFqdn <String>] <COMMON PARAMETERS>

    Get-CsPersistentChatAddin -Identity <String> <COMMON PARAMETERS>

    COMMON PARAMETERS:

## 예제

## 예제 1

예제 1에서는 조직에서 사용하도록 구성된 모든 영구 채팅 추가 기능에 대한 정보를 반환합니다.

    Get-CsPersistentChatAddin

## 예제 2

예제 2에서는 ID가 atl-cs-001.litwareinc.com\\ITPersistentChatAddin인 특정 영구 채팅 추가 기능에 대한 정보를 반환합니다.

    Get-CsPersistentChatAddin -Identity "atl-cs-001.litwareinc.com\ITPersistentChatAddin"

## 예제 3

예제 3에서는 atl-cs-001.litwareinc.com 풀에서 사용하도록 구성된 모든 영구 채팅 추가 기능에 대한 정보를 반환합니다.

    Get-CsPersistentChatAddin -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com"

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

영구 채팅방에 대한 확장 역할을 하는 추가 기능은 특정 채팅방과 연결된 외부 응용 프로그램입니다. 따라서 영구 채팅 자체에서는 항목이 기본 제공되지 않습니다. 예를 들어 지원 센터 채팅방에는 특정일의 지원 요청 상태가 표시되는 Silverlight 응용 프로그램 또는 웹 페이지로 연결되는 URL이 포함될 수 있습니다. Lync ServerWindows PowerShell 명령줄 인터페이스 cmdlet은 이러한 추가 기능을 만드는 기능을 제공하지 않으며, 대신 **CsPersistentChatAddin** cmdlet을 사용하여 채팅방에서 추가 기능을 연결하거나 연결을 해제합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPersistentChatAddin"}

**Lync Server 제어판:** Lync Server 제어판에서 영구 채팅 추가 기능 정보를 보려면 **영구 채팅** , **추가 기능** 을 차례로 클릭합니다.

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
<td><p>반환할 영구 채팅 추가 기능의 고유 식별자입니다. ID는 추가 기능이 있는 영구 채팅 풀의 정규화된 도메인 이름, &quot;\&quot; 문자 및 추가 기능 이름으로 구성됩니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;atl-gc-001.litwareincom\ITPersistentChatAddin&quot;</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsPersistentChatAddin</strong> cmdlet은 모든 영구 채팅 추가 기능에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PersistentChatPoolFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>영구 채팅 풀의 정규화된 도메인 이름입니다. 이 매개 변수를 사용하는 경우 지정된 풀에 있는 영구 채팅 추가 기능만 반환됩니다. 이 매개 변수를 사용하지 않는 경우에는 <strong>Get-CsPersistentChatAddin</strong> cmdlet이 모든 영구 채팅 풀의 추가 기능을 반환합니다. 예를 들면 다음과 같습니다.</p>
<p>-PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsPersistentChatAddin** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsPersistentChatAddin** cmdlet은 Microsoft.Rtc.Management.PersistentChat.Cmdlets.AddinObject 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsPersistentChatAddin](new-cspersistentchataddin.md)  
[Remove-CsPersistentChatAddin](remove-cspersistentchataddin.md)  
[Set-CsPersistentChatAddin](set-cspersistentchataddin.md)

