---
title: Remove-CsPersistentChatPolicy
TOCTitle: Remove-CsPersistentChatPolicy
ms:assetid: d6bfe22b-084b-4d7f-8e4a-58f738493b31
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205301(v=OCS.15)
ms:contentKeyID: 49305179
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsPersistentChatPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 영구적 채팅 정책을 제거합니다. 영구적 채팅 정책은 사용자의 영구 채팅방 액세스가 허용되는지 여부를 결정합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsPersistentChatPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 RedmondPersistentChatPolicy인 사용자별 영구적 채팅 정책을 제거합니다.

    Remove-CsPersistentChatPolicy -Identity "RedmondPersistentChatPolicy"

## 예제 2

예제 2에서는 사이트 범위에 적용된 모든 영구적 채팅 정책을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPersistentChatPolicy** cmdlet 및 Filter 매개 변수를 사용하여 사이트 범위에서 구성된 모든 영구적 채팅 정책을 반환합니다. 이 작업에서는 필터 값 "site:\*"가 사용됩니다. 이러한 정책은 **Remove-CsPersistentChatPolicy** cmdlet에 파이프되며 해당 cmdlet에 의해 삭제됩니다.

    Get-CsPersistentChatPolicy -Filter "site:*" | Remove-CsPersistentChatPolicy

## 예제 3

예제 3에서는 영구 채팅이 사용하도록 설정된 모든 영구적 채팅 정책을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsPersistentChatPolicy** cmdlet을 호출합니다. 그러면 조직에서 사용하도록 구성된 모든 영구적 채팅 정책의 컬렉션이 반환됩니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프되며, 해당 cmdlet은 EnablePersistentChat 속성이 True($True)와 같은 정책만 선택합니다. 해당 컬렉션은 **Remove-CsPersistentChatPolicy** cmdlet에 파이프되며, 이 cmdlet은 컬렉션의 각 정책을 삭제합니다.

    Get-CsPersistentChatPolicy | Where-Object {$_.EnablePersistentChat -eq $True} | Remove-CsPersistentChatPolicy

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

기본적으로 사용자에게는 영구 채팅 서비스 액세스 권한이 부여되지 않습니다. 사용자의 서비스 사용을 허용하는 영구적 채팅 정책을 통해 사용자가 관리되는 경우에만 이 액세스 권한을 부여할 수 있습니다. Lync 2013를 설치하면 모든 사용자가 전역 영구적 채팅 정책을 통해 관리되며, 이 정책에서는 영구 채팅이 사용할 수 없도록 설정됩니다. 모든 사용자에게 서비스 액세스 권한을 제공하려면 전역 정책의 EnablePersistentChat 속성을 True로 설정하면 됩니다. 사이트 또는 사용자별 범위에서 추가 정책을 만들어 일부 사용자에게는 영구 채팅 액세스 권한을 제공하고 나머지 사용자에 대해서는 액세스를 거부할 수도 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsPersistentChatPolicy"}

**Lync Server 제어판:** Lync Server 제어판을 사용하여 영구적 채팅 정책을 제거하려면 **영구 채팅** , **영구적 채팅 정책** 을 차례로 클릭하고 제거할 정책을 선택한 후에 **편집** , **삭제** 를 차례로 클릭합니다.

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>삭제할 영구적 채팅 정책의 고유 ID입니다. 사이트 범위 정책을 제거하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity site:Redmond</p>
<p>사용자별 정책을 삭제하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity RedmondPolicy</p>
<p><strong>Remove-CsPersistentChatPolicy</strong> cmdlet을 전역 영구적 채팅 정책에 대해서도 실행할 수 있지만 전역 정책이 실제로 삭제되지는 않습니다. 대신 전역 정책의 모든 속성이 기본값으로 다시 설정됩니다.</p></td>
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
<td><p>이 매개 변수가 있으면 <strong>Remove-CsPersistentChatPolicy</strong> cmdlet이 사용자별 정책을 삭제합니다. 이는 해당 정책이 한 명 이상의 사용자에게 현재 할당된 경우에도 마찬가지입니다. 이 매개 변수가 없으면 아직 사용 중인 정책을 제거하기 전에 삭제 요청을 확인하는 메시지가 나타납니다.</p></td>
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

**Remove-CsPersistentChatPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.PersistentChat.PersistentChatPolicy 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsPersistentChatPolicy** cmdlet이 Microsoft.Rtc.Management.WritableConfig.Policy.PersistentChat.PersistentChatPolicy 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPersistentChatPolicy](get-cspersistentchatpolicy.md)  
[Grant-CsPersistentChatPolicy](grant-cspersistentchatpolicy.md)  
[New-CsPersistentChatPolicy](new-cspersistentchatpolicy.md)  
[Set-CsPersistentChatPolicy](set-cspersistentchatpolicy.md)

