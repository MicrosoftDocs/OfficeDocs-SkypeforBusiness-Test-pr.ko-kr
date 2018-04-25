---
title: Remove-CsPersistentChatComplianceConfiguration
TOCTitle: Remove-CsPersistentChatComplianceConfiguration
ms:assetid: 2d54eabf-fbb5-435b-9a71-d6b03beb09a5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204767(v=OCS.15)
ms:contentKeyID: 49303166
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsPersistentChatComplianceConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

영구 채팅 준수 구성 설정의 기존 컬렉션을 제거합니다. 관리자는 영구 채팅 준수를 통해 새 메시지, 새 이벤트(예: 사용자가 채팅방에 들어오거나 채팅방에서 나감), 파일 업로드/다운로드, 채팅 기록에 대해 실행된 검색 등 영구 채팅 항목 및 작업의 보관 파일을 유지 관리할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsPersistentChatComplianceConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트에 적용된 영구 채팅 준수 구성 설정을 제거합니다.

    Remove-CsPersistentChatComplianceConfiguration -Identity "site:Redmond"

## 예제 2

예제 2에서는 사이트 범위에 적용된 모든 영구 채팅 준수 구성 설정을 제거합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsPersistentChatComplianceConfiguration** cmdlet 및 Filter 매개 변수를 사용하여 사이트 범위에 할당된 모든 설정을 검색합니다. 이 작업은 필터 값 "site:\*"를 사용하여 수행합니다. 검색된 사이트 범위 설정은 이 설정을 제거하는 **Remove-CsPersistentChatComplianceConfiguration** cmdlet에 파이프됩니다.

    Get-CsPersistentChatComplianceConfiguration -Filter "site:*" | Remove-CsPersistentChatComplianceConfiguration

## 예제 3

예제 3에서는 AddUserDetails 및 AddChatRoomDetails 속성이 모두 True로 설정된 모든 영구 채팅 준수 구성 설정을 제거하는 방법을 보여줍니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsPersistentChatComplianceConfiguration** cmdlet을 사용하여 모든 영구 채팅 준수 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 AddUserDetails 속성 및 AddChatRoomDetails 속성이 True($True)와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsPersistentChatComplianceConfiguration** cmdlet에 파이프됩니다.

    Get-CsPersistentChatComplianceConfiguration | Where-Object {$_.AddUserDetals -eq $True -and $_.AddChatRoomDetails -eq $True} | Remove-CsPersistentChatComplianceConfiguration

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

의료 및 금융 업계의 조직을 비롯한 대부분의 조직은 모든 전자 통신의 보관 파일을 유지 관리해야 합니다. 여기에는 영구 채팅 서비스를 사용하여 진행했을 수 있는 대화도 포함됩니다. Lync Server 2013에서는 영구 채팅방에서 대화한 모든 내용의 상세한 보관 파일을 유지하는 준수 데이터베이스를 별도로 만들 수 있습니다. 영구 채팅 준수는 사이트 범위 또는 서비스 범위에서 사용하거나 사용하지 않도록 설정할 수 있습니다. 즉, 지정된 영구 채팅 풀에 대해 준수를 사용하거나 사용하지 않도록 설정할 수 있습니다. 또한 영구 채팅 준수는 Windows PowerShell 명령줄 인터페이스를 통해서만 관리할 수 있으며 Lync Server 2013 제어판에서는 영구 채팅 준수 관리용 옵션을 사용할 수 없습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsPersistentChatComplianceConfiguration"}

**Lync Server 제어판:** **Remove-CsPersistentChatComplianceConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>제거할 영구 채팅 준수 설정의 고유 식별자입니다. 사이트 범위에서 구성된 설정 컬렉션을 제거하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>서비스 범위에서 구성된 컬렉션을 제거하려면 다음 구문을 사용합니다.</p>
<p>-Identity &quot;service:PersistentChatServer:atl-gc-001.litwareinc.com&quot;</p>
<p>Identity 매개 변수에는 와일드카드를 사용할 수 없습니다.</p>
<p>전역 설정 컬렉션에 대해 <strong>Remove-CsPersistentChatComplianceConfiguration</strong> cmdlet을 실행할 수도 있습니다. 그러나 이 경우 전역 컬렉션은 제거되지 않습니다. 대신 해당 컬렉션 내의 모든 속성이 기본값으로 다시 설정됩니다.</p></td>
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

**Remove-CsPersistentChatComplianceConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatComplianceConfiguration 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsPersistentChatComplianceConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatComplianceConfiguration 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPersistentChatComplianceConfiguration](get-cspersistentchatcomplianceconfiguration.md)  
[New-CsPersistentChatComplianceConfiguration](new-cspersistentchatcomplianceconfiguration.md)  
[Set-CsPersistentChatComplianceConfiguration](set-cspersistentchatcomplianceconfiguration.md)

