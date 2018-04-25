---
title: Set-CsPersistentChatPolicy
TOCTitle: Set-CsPersistentChatPolicy
ms:assetid: b724bc13-d4fe-4529-9a48-e4cec8b7dce2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205192(v=OCS.15)
ms:contentKeyID: 49304807
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsPersistentChatPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 영구적 채팅 정책을 수정합니다. 영구적 채팅 정책은 사용자의 영구 채팅방 액세스가 허용되는지 여부를 결정합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsPersistentChatPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsPersistentChatPolicy [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-EnablePersistentChat <$true | $false>] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 영구 채팅에서 전역 영구적 채팅 정책을 사용하도록 설정합니다.

    Set-CsPersistentChatPolicy -Identity "global" -EnablePersistentChat $True

## 예제 2

예제 2에서는 영구 채팅에서 조직의 모든 영구적 채팅 정책을 사용하도록 설정합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsPersistentChatPolicy** cmdlet을 사용하여 모든 영구적 채팅 정책의 컬렉션을 반환합니다. 이 컬렉션은 **Set-CsPersistentChatPolicy** cmdlet에 파이프되며, 해당 cmdlet은 컬렉션에 있는 각 정책의 EnablePersistentChat 매개 변수를 True($True)로 설정합니다.

    Get-CsPersistentChatPolicy | Set-CsPersistentChatPolicy -EnablePersistentChat $True

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

기본적으로 사용자에게는 영구 채팅 서비스 액세스 권한이 부여되지 않습니다. 사용자의 서비스 사용을 허용하는 영구적 채팅 정책을 통해 사용자가 관리되는 경우에만 이 액세스 권한을 부여할 수 있습니다. Lync 2013를 설치하면 모든 사용자가 전역 영구적 채팅 정책을 통해 관리되며, 이 정책에서는 영구 채팅이 사용할 수 없도록 설정됩니다. 모든 사용자에게 서비스 액세스 권한을 제공하려면 전역 정책의 EnablePersistentChat 속성을 True로 설정하면 됩니다. 사이트 또는 사용자별 범위에서 추가 정책을 만들어 일부 사용자에게는 영구 채팅 액세스 권한을 제공하고 나머지 사용자에 대해서는 액세스를 거부할 수도 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsPersistentChatPolicy"}

**Lync Server 제어판:** Lync Server 제어판을 사용하여 기존 영구적 채팅 정책을 수정하려면 **영구 채팅** , **영구적 채팅 정책** 을 차례로 클릭한 다음 수정할 정책을 두 번 클릭합니다.

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 정책과 함께 표시할 설명 텍스트를 제공할 수 있습니다. 예를 들어 정책을 할당할 사용자에 대한 정보를 설명에 포함할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnablePersistentChat</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 정책이 적용되는 사용자가 영구 채팅을 사용할 수 있습니다. 기본값인 False로 설정하면 정책이 적용되는 사용자가 영구 채팅을 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 영구적 채팅 정책의 고유 ID입니다. 전역 정책을 수정하려면 다음 구문을 사용합니다.</p>
<p>-Identity global</p>
<p>사이트 범위 정책을 수정하려면 다음 구문을 사용합니다.</p>
<p>-Identity site:Redmond</p>
<p>사용자별 정책을 수정하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity RedmondPolicy</p>
<p>Identity 매개 변수를 포함하지 않으면 <strong>Set-CsPersistentChatPolicy</strong> cmdlet이 전역 정책을 자동으로 수정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
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

**Set-CsPersistentChatPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.PersistentChat.PersistentChatPolicy 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsPersistentChatPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.PersistentChat.PersistentChatPolicy 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPersistentChatPolicy](get-cspersistentchatpolicy.md)  
[Grant-CsPersistentChatPolicy](grant-cspersistentchatpolicy.md)  
[New-CsPersistentChatPolicy](new-cspersistentchatpolicy.md)  
[Remove-CsPersistentChatPolicy](remove-cspersistentchatpolicy.md)

