---
title: New-CsPersistentChatConfiguration
TOCTitle: New-CsPersistentChatConfiguration
ms:assetid: df83eebe-c20c-4e22-a5d4-1546a7f06e25
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205330(v=OCS.15)
ms:contentKeyID: 49305280
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsPersistentChatConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

사이트 또는 서비스 범위에서 새 영구 채팅 구성 설정 컬렉션을 만듭니다. 영구 채팅 구성 설정은 영구 채팅 서비스를 관리하는 데 사용됩니다. 예를 들어 이러한 설정을 통해 채팅방에 참가할 수 있는 최대 사용자 수를 지정할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsPersistentChatConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-DefaultChatHistory <Int16>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MaxFileSizeKB <UInt32>] [-ParticipantUpdateLimit <UInt32>] [-RoomManagementUrl <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트에 적용되는 영구 채팅 구성 설정 집합을 새로 만듭니다. 이 예제에서 ParticipantUpdateLimit 속성은 100으로 설정됩니다.

    New-CsPersistentChatConfiguration -Identity "site:Redmond" -ParticipantUpdateLimit 100

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

영구 채팅 서비스는 일부분 영구 채팅 구성 설정을 통해 관리됩니다. 이 설정은 채팅방에 로그온할 때 즉시 사용할 수 있는 이전에 게시된 채팅 메시지의 수(채팅 기록) 또는 서비스로 업로드하거나 서비스에서 다운로드할 수 있는 최대 파일 크기 등을 지정합니다. 이러한 설정은 전역, 사이트 또는 서비스 범위에서 구성할 수 있습니다. 즉, 개별 영구 채팅 풀에 사용자 지정 설정 컬렉션을 할당할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsPersistentChatConfiguration"}

**Lync Server 제어판:** Lync Server 제어판을 사용하여 새 영구 채팅 구성 설정 컬렉션을 만들려면 **영구 채팅** , **영구 채팅 구성** , **새로 만들기** 를 차례로 클릭한 다음 **사이트 구성** 또는 **풀 구성** 을 클릭합니다.

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>새로 만들 영구 채팅 구성 설정의 고유 식별자입니다. 새 구성 설정은 사이트 또는 서비스 범위(영구 채팅 서버 서비스에만 해당)에서 만들 수 있습니다. 사이트 범위에서 새 설정을 만들려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>서비스 범위에서 새 설정을 만들려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;service:PersistentChatServer:atl-gc-001.litwarein.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DefaultChatHistory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int16</p></td>
<td><p>채팅방에서 즉시 사용 가능한 기본 채팅 메시지 수입니다. 이 값은 즉시 사용 가능한 메시지의 수를 나타낼 뿐이며 검색 가능한 총 메시지 수에 대해 제한을 적용하지는 않습니다.</p>
<p>DefaultChatHistory는 1에서 500(포함) 사이의 값으로 설정할 수 있습니다. 기본값은 30입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxFileSizeKB</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>웹 서비스에서 업로드 또는 다운로드할 수 있는 최대 파일 크기(KB)입니다. 기본값은 20000KB입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ParticipantUpdateLimit</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>활성 참가자 목록 업데이트를 사용할 수 없을 때까지 채팅방에 참가할 수 있는 최대 사용자 수입니다. 기본값은 75입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>RoomManagementUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>웹 페이지 관리자가 개별 채팅방을 관리하는 데 사용할 수 있는 URL입니다.</p></td>
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

없음. **New-CsPersistentChatConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsPersistentChatConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatConfiguration 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsPersistentChatConfiguration](get-cspersistentchatconfiguration.md)  
[Remove-CsPersistentChatConfiguration](remove-cspersistentchatconfiguration.md)  
[Set-CsPersistentChatConfiguration](set-cspersistentchatconfiguration.md)

