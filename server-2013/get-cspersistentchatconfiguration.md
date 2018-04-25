---
title: Get-CsPersistentChatConfiguration
TOCTitle: Get-CsPersistentChatConfiguration
ms:assetid: a15ce45f-00cc-49af-9ef4-3991d891d37e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205140(v=OCS.15)
ms:contentKeyID: 49304575
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPersistentChatConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용 중인 영구 채팅 구성 설정에 대한 정보를 반환합니다. 영구 채팅 구성 설정은 영구 채팅 서비스를 관리하는 데 사용됩니다. 예를 들어 이러한 설정을 통해 채팅방에 참가할 수 있는 최대 사용자 수를 지정할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsPersistentChatConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsPersistentChatConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용 중인 모든 영구 채팅 구성 설정에 대한 정보를 반환합니다.

    Get-CsPersistentChatConfiguration

## 예제 2

예제 2에서는 지정된 영구 채팅 구성 설정 집합, 즉 Redmond 사이트에 적용된 설정에 대한 정보를 반환합니다.

    Get-CsPersistentChatConfiguration -Identity "site:Redmond"

## 예제 3

예제 3에서는 사이트 범위에 적용된 모든 영구 채팅 구성 설정에 대한 정보를 반환합니다. 이 작업은 Filter 매개 변수와 필터 값 "service:\*"를 포함하여 수행됩니다.

    Get-CsPersistentChatConfiguration -Filter "service:*"

## 예제 4

예제 4에서는 기본 채팅 기록이 30보다 큰 값으로 설정된 모든 영구 채팅 구성 설정에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPersistentChatConfiguration** cmdlet을 사용하여 모든 영구 채팅 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프되며, 해당 cmdlet은 DefaultChatHistory 속성이 30보다 큰(-gt) 설정만 선택합니다.

    Get-CsPersistentChatConfiguration | Where-Object {$_.DefaultChatHistory -gt 30}

## 예제 5

예제 5에서는 채팅방 관리 URL이 정의되지 않은 모든 영구 채팅 구성 설정에 대한 정보를 반환하는 방법을 보여줍니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPersistentChatConfiguration** cmdlet을 사용하여 모든 영구 채팅 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프되며, 해당 cmdlet은 RoomManagementUrl 속성이 null 값($Null)인 모든 설정을 선택합니다.

    Get-CsPersistentChatConfiguration | Where-Object {$_.RoomManagementUrl -eq $Null}

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

영구 채팅 서비스는 일부분 영구 채팅 구성 설정을 통해 관리됩니다. 이 설정은 채팅방에 로그온할 때 즉시 사용할 수 있는 이전에 게시된 채팅 메시지의 수(채팅 기록) 또는 서비스로 업로드하거나 서비스에서 다운로드할 수 있는 최대 파일 크기 등을 지정합니다. 이러한 설정은 전역, 사이트 또는 서비스 범위에서 구성할 수 있습니다. 즉, 개별 영구 채팅 풀에 사용자 지정 설정 컬렉션을 할당할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPersistentChatConfiguration"}

**Lync Server 제어판:**Lync Server 제어판에서 영구 채팅 구성 정보를 보려면 **영구 채팅**, **영구 채팅 구성**을 차례로 클릭합니다.

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>반환할 영구 채팅 구성 설정의 컬렉션을 지정할 때 와일드카드를 사용할 수 있습니다. 예를 들어 다음 구문은 서비스 범위에 구성된 모든 설정을 반환합니다.</p>
<p>-Filter &quot;service:*&quot;</p>
<p>Filter와 Identity 매개 변수를 같은 명령에서 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 영구 채팅 구성 설정의 고유 식별자입니다. 전역 컬렉션을 반환하려면 다음 구문을 사용합니다.</p>
<p>-Identity &quot;global&quot;</p>
<p>사이트 범위에서 구성된 설정 컬렉션을 반환하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>서비스 범위에서 구성된 컬렉션을 반환하려면 다음 구문을 사용합니다.</p>
<p>-Identity &quot;service:PersistentChatServer:atl-gc-001.litwareinc.com&quot;</p>
<p>Identity 매개 변수에는 와일드카드를 사용할 수 없습니다.</p>
<p>Identity 매개 변수와 Filter 매개 변수를 둘 다 명령에 포함하지 않으면 <strong>Get-CsPersistentChatConfiguration</strong> cmdlet은 조직에서 사용 중인 모든 영구 채팅 구성 설정에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 영구 채팅 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsPersistentChatConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsPersistentChatConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatConfiguration 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsPersistentChatConfiguration](new-cspersistentchatconfiguration.md)  
[Remove-CsPersistentChatConfiguration](remove-cspersistentchatconfiguration.md)  
[Set-CsPersistentChatConfiguration](set-cspersistentchatconfiguration.md)

