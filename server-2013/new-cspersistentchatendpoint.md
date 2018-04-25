---
title: New-CsPersistentChatEndpoint
TOCTitle: New-CsPersistentChatEndpoint
ms:assetid: 3a3a7acc-3239-4140-8005-ef72ab2f61e1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204811(v=OCS.15)
ms:contentKeyID: 49303349
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsPersistentChatEndpoint

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 영구 채팅 끝점을 만듭니다. 영구 채팅 끝점은 Lync Server 2013 영구 채팅 풀의 URL을 제공하는 Active Directory 대화 상대 개체입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsPersistentChatEndpoint -PersistentChatPoolFqdn <Fqdn> -SipAddress <String> [-Confirm [<SwitchParameter>]] [-DisplayName <String>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-pcpool-001.litwareinc.com 풀에 대해 새 영구 채팅 끝점을 만듭니다. 이 새 끝점의 SIP 주소는 "atl-pcpool-001.litwareinc.com"이고 표시 이름은 "Persistent Chat Endpoint 1"입니다.

    New-CsPersistentChatEndpoint -SipAddress "sip:pce@litwareinc.com" -PersistentChatPoolFqdn "atl-pcpool-001.litwareinc.com" -DisplayName "Persistent Chat Endpoint 1"

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

그러나 Microsoft Lync 2010 등의 레거시 클라이언트를 실행하는 사용자가 있는 경우 해당 사용자는 레거시 클라이언트가 풀을 가리키도록 지정할 때 기본 영구 채팅 URI를 사용하기가 어려울 수 있습니다. 이러한 경우 관리자는 **New-CsPersistentChatEndpoint** cmdlet을 사용하여 풀에 대해 추가 대화 상대 개체, 즉 확인 및 사용이 보다 간편한 URI를 제공하는 대화 상대 개체를 만들 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsPersistentChatEndpoint"}

**Lync Server 제어판:** **New-CsPersistentChatEndpoint** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>PersistentChatPoolFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>새 끝점을 연결할 영구 채팅 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-PersistentChatPoolFqdn &quot;atl-pc-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>SipAddress</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>끝점이 Lync 2013 등의 SIP 장치를 사용하여 통신하도록 허용하는 고유 식별자입니다. SIP 주소에는 다음과 같이 sip: 접두사 및 유효한 SIP 도메인을 사용해야 합니다.</p>
<p>-SipAddress &quot;sip:pcEndpoint1@litwareinc.com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisplayName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>새 연락처 개체의 Active Directory 표시 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>새 영구 채팅 끝점을 나타내는 대화 상대 개체를 파이프라인을 통해 전달하는 데 사용됩니다. 기본적으로 <strong>New-CsPersistentChatEndpoint</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
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

없음. **New-CsPersistentChatEndpoint** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsPersistentChatEndpoint** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSPersistentChatContact 클래스의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsPersistentChatEndpoint](get-cspersistentchatendpoint.md)  
[Remove-CsPersistentChatEndpoint](remove-cspersistentchatendpoint.md)

