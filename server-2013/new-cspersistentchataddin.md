---
title: New-CsPersistentChatAddin
TOCTitle: New-CsPersistentChatAddin
ms:assetid: 0566f4c2-0903-4dd1-87bc-784f0bdb4391
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204641(v=OCS.15)
ms:contentKeyID: 49302672
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsPersistentChatAddin

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 영구 채팅 추가 기능을 구성할 수 있도록 합니다. 영구 채팅 추가 기능은 영구 채팅 클라이언트 내에 포함할 수 있는 사용자 지정된 웹 페이지입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsPersistentChatAddin -Name <String> -Url <String> [-PersistentChatPoolFqdn <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-cs-001.litwareinc.com 풀에 대해 이름이 ITPersistentChatAddin인 새 영구 채팅 추가 기능을 만듭니다. URL 매개 변수 및 매개 변수 값 http://atl-cs-001.litwareinc.com/itchat이 추가 기능의 웹 페이지 위치를 지정합니다.

    New-CsPersistentChatAddin -Name "ITPersistentChatAddin" -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com" -Url "http://atl-cs-001.litwareinc.com/itchat"

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 대화방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

영구 채팅방에 대한 확장 역할을 하는 추가 기능은 특정 대화방과 연결된 외부 응용 프로그램입니다. 따라서 영구 채팅 자체에서는 항목이 기본 제공되지 않습니다. 예를 들어 지원 센터 대화방에는 특정일의 지원 요청 상태가 표시되는 Silverlight 응용 프로그램 또는 웹 페이지로 연결되는 URL이 포함될 수 있습니다. Lync Server 관리 셸은 이러한 추가 기능을 만드는 기능을 제공하지 않으며, 대신 **CsPersistentChatAddin** cmdlet을 사용하여 대화방에서 추가 기능을 연결하거나 연결을 해제합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsPersistentChatAddin"}

**Lync Server 제어판:**Lync Server 제어판을 사용하여 새 영구 채팅 추가 기능을 만들려면 **영구 채팅**, **추가 기능**, **새로 만들기**를 차례로 클릭합니다.

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
<th>유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>영구 채팅 추가 기능에 지정할 이름입니다. 이름은 각 영구 채팅 서버 풀에서 고유해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Url</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>영구 채팅 추가 기능이 표시할 웹 페이지의 URL입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PersistentChatPoolFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>영구 채팅 서버 풀의 정규화된 도메인 이름입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsPersistentChatAddin** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsPersistentChatAddin** cmdlet은 Microsoft.Rtc.Management.PersistentChat.Cmdlets.AddinObject 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsPersistentChatAddin](get-cspersistentchataddin.md)  
[Remove-CsPersistentChatAddin](remove-cspersistentchataddin.md)  
[Set-CsPersistentChatAddin](set-cspersistentchataddin.md)

