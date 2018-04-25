---
title: Set-CsPersistentChatConfiguration
TOCTitle: Set-CsPersistentChatConfiguration
ms:assetid: 97d23d2e-878c-4573-bfce-0ddddc5a190e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205122(v=OCS.15)
ms:contentKeyID: 49304466
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsPersistentChatConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

영구 채팅 구성 설정의 기존 컬렉션을 수정합니다. 영구 채팅 구성 설정은 영구 채팅 서비스를 관리하는 데 사용됩니다. 예를 들어 이러한 설정을 통해 채팅방에 참가할 수 있는 최대 사용자 수를 지정할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsPersistentChatConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsPersistentChatConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-DefaultChatHistory <Int16>] [-Force <SwitchParameter>] [-MaxFileSizeKB <UInt32>] [-ParticipantUpdateLimit <UInt32>] [-RoomManagementUrl <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 전역 영구 채팅 구성 설정의 DefaultChatHistory 속성을 100으로 설정합니다.

    Set-CsPersistentChatConfiguration -Identity "global" -DefaultChatHistory 100

## 예제 2

예제 2에서는 모든 영구 채팅 구성 설정에 대해 DefaultChatHistory 속성을 100으로 설정합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPersistentChatConfiguration** cmdlet을 사용하여 조직의 모든 영구 채팅 구성 설정 컬렉션을 반환합니다. 이 컬렉션은 **Set-CsPersistentChatConfiguration** cmdlet에 파이프되며, 해당 cmdlet은 컬렉션의 모든 항목에 대한 DefaultChatHistory 속성을 수정합니다.

    Get-CsPersistentChatConfiguration | Set-CsPersistentChatConfiguration -DefaultChatHistory 100

## 예제 3

예제 3에서는 사이트 범위에 적용된 모든 영구 채팅 구성 설정의 DefaultChatHistory 속성을 수정하는 방법을 보여줍니다. 이 작업을 수행하기 위해 명령은 먼저 Filter 매개 변수를 포함하여 **Get-CsPersistentChatConfiguration** cmdlet을 호출합니다. 매개 변수 값 "site:\*"는 반환되는 데이터를 사이트 범위에서 구성된 설정 컬렉션으로 제한합니다. 이러한 설정은 **Set-CsPersistentChatConfiguration** cmdlet에 파이프되며, 해당 cmdlet은 각 설정 컬렉션의 DefaultChatHistory 속성을 100으로 변경합니다.

    Get-CsPersistentChatConfiguration -Filter "site:*" | Set-CsPersistentChatConfiguration -DefaultChatHistory 100

## 예제 4

예제 4에서는 기본 채팅 기록이 현재 100보다 큰 모든 영구 채팅 구성 설정 컬렉션에 대해 DefaultChatHistory 속성을 수정합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPersistentChatConfiguration** cmdlet을 사용하여 조직에서 사용 중인 모든 영구 채팅 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프되며, 해당 cmdlet은 DefaultChatHistory 속성이 100보다 큰(-gt) 설정만 선택합니다. 필터링된 컬렉션은 **Set-CsPersistentChatConfiguration** cmdlet에 파이프되며, 이 cmdlet은 필터링된 컬렉션의 각 항목을 가져온 다음 DefaultChatHistory 속성의 값을 100으로 설정합니다.

    Get-CsPersistentChatConfiguration | Where-Object {$_.DefaultChatHistory -gt 100} | Set-CsPersistentChatConfiguration -DefaultChatHistory 100

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

영구 채팅 서비스는 일부분 영구 채팅 구성 설정을 통해 관리됩니다. 이 설정은 채팅방에 로그온할 때 즉시 사용할 수 있는 이전에 게시된 채팅 메시지의 수(채팅 기록) 또는 서비스로 업로드하거나 서비스에서 다운로드할 수 있는 최대 파일 크기 등을 지정합니다. 이러한 설정은 전역, 사이트 또는 서비스 범위에서 구성할 수 있습니다. 즉, 개별 영구 채팅 풀에 사용자 지정 설정 컬렉션을 할당할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsPersistentChatConfiguration"}

**Lync Server 제어판:** Lync Server 제어판을 사용하여 기존 영구 채팅 구성 설정 컬렉션을 수정하려면 **영구 채팅** , **영구 채팅 구성** 을 차례로 클릭한 다음 수정할 컬렉션을 두 번 클릭합니다.

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DefaultChatHistory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int16</p></td>
<td><p>채팅방에서 즉시 사용 가능한 기본 채팅 메시지 수입니다. 이 값은 즉시 사용 가능한 메시지의 수를 나타낼 뿐이며 검색 가능한 총 메시지 수에 대해 제한을 적용하지는 않습니다.</p>
<p>DefaultChatHistory는 1에서 500(포함) 사이의 값으로 설정할 수 있습니다. 기본값은 30입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 영구 채팅 구성 설정의 고유 식별자입니다. 사이트 범위에서 구성된 설정 컬렉션을 수정하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>서비스 범위에서 구성된 컬렉션을 수정하려면 다음 구문을 사용합니다.</p>
<p>-Identity &quot;service:PersistentChatServer:atl-gc-001.litwareinc.com&quot;</p>
<p>전역 컬렉션을 수정하려면 다음 구문을 사용합니다.</p>
<p>-Identity &quot;global&quot;</p>
<p>Identity 매개 변수를 포함하지 않으면 <strong>Set-CsPersistentChatConfiguration</strong> cmdlet이 전역 설정을 자동으로 수정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
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

**Set-CsPersistentChatConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatConfiguration 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsPersistentChatConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatConfiguration 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPersistentChatConfiguration](get-cspersistentchatconfiguration.md)  
[New-CsPersistentChatConfiguration](new-cspersistentchatconfiguration.md)  
[Remove-CsPersistentChatConfiguration](remove-cspersistentchatconfiguration.md)

