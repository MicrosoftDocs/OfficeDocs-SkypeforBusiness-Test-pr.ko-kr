---
title: Set-CsPersistentChatState
TOCTitle: Set-CsPersistentChatState
ms:assetid: 9b82fe41-214d-4376-b026-bb1434d04118
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205109(v=OCS.15)
ms:contentKeyID: 49304511
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsPersistentChatState

 

_**마지막으로 수정된 항목:** 2015-03-09_

영구 채팅 서비스 풀의 상태를 수정합니다. 영구 채팅 풀은 Normal(풀이 기본 데이터베이스를 사용함) 또는 FailedOver(풀이 토폴로지에 정의된 백업 데이터베이스를 사용함)의 두 가지 상태 중 하나일 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsPersistentChatState [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsPersistentChatState [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-PoolState <FailedOver | Normal>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 영구 채팅 서버 atl-gc-001.litwareinc.com에 대해 풀 상태를 FailedOver로 설정합니다.

    Set-CsPersistentChatState -Identity "PersistentChatServer:atl-gc-001.litwareinc.com" -PoolState "FailedOver"

## 자세한 정보

[Get-CsPersistentChatState](get-cspersistentchatstate.md) cmdlet은 영구 채팅 풀 하나 이상의 상태를 반환합니다. 영구 채팅 풀은 Normal 상태(풀이 기본 데이터베이스를 사용함) 또는 FailedOver 상태(풀이 백업 데이터베이스를 사용함)일 수 있습니다. **Set-CsPersistentChatState** cmdle을 사용하면 영구 채팅 풀의 상태를 변경할 수 있습니다. 풀 상태를 변경하면 Lync Server 2013에서는 풀의 개별 서버 상태를 자동으로 변경합니다. 개별 채팅 서버의 상태를 변경하려면 [Set-CsPersistentChatActiveServer](set-cspersistentchatactiveserver.md) cmdlet을 사용합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsPersistentChatState"}

**Lync Server 제어판:** **Set-CsPersistentChatState** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>새 서비스 상태를 적용할 영구 채팅 풀의 서비스 ID입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity PersistentChatServer:atl-persistentchat-001.litwareinc.com</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PoolState</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PoolState</p></td>
<td><p>영구 채팅 풀의 현재 상태입니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Normal</p>
<p>* FailedOver</p>
<p>기본값은 Normal입니다.</p></td>
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

**Set-CsPersistentChatState** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatstate 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsPersistentChatState** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatState 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPersistentChatState](get-cspersistentchatstate.md)  
[Set-CsPersistentChatActiveServer](set-cspersistentchatactiveserver.md)

