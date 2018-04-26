---
title: Set-CsPersistentChatActiveServer
TOCTitle: Set-CsPersistentChatActiveServer
ms:assetid: 88c0af42-cb47-4c34-bf54-9c134dcbb843
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205065(v=OCS.15)
ms:contentKeyID: 49304292
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsPersistentChatActiveServer

 

_**마지막으로 수정된 항목:** 2013-03-07_

활성 영구 채팅 서버의 목록을 관리합니다. 활성 서버는 완전하게 작동하며 새 클라이언트 연결을 허용할 수 있는 지정된 영구 채팅 서비스 풀 내의 영구 채팅 서버입니다. 풀에서 활성 서버로 표시되지 않은 서버는 대개 작동하기는 하지만 현재 새 클라이언트 연결을 허용할 수는 없을 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsPersistentChatActiveServer -ActiveServers <PSListModifier> <COMMON PARAMETERS>

    Set-CsPersistentChatActiveServer -Swap <SwitchParameter> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Identity <XdsGlobalRelativeIdentity>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-gc-001.litwareinc.com 서버를 활성 영구 채팅 서버 컬렉션에 추가합니다.

    Set-CsPersistentChatActiveServer -Identity "global" -ActiveServers @{Add="atl-gc-001.litwareinc.com"}

## 예제 2

예제 2에서는 활성 영구 채팅 서버 컬렉션에서 atl-gc-001.litwareinc.com 서버를 제거합니다.

    Set-CsPersistentChatActiveServer -Identity "global" -ActiveServers @{Remove="atl-gc-001.litwareinc.com"}

## 예제 3

예제 3에 표시된 명령은 모든 활성 영구 채팅 서버를 제거합니다. 일반적으로 장애 복구(failback) 또는 장애 조치(failover) 시나리오에서 모든 활성 서버를 제거합니다.

    Set-CsPersistentChatActiveServer -Identity "global" -ActiveServers $Null

## 자세한 정보

관리자는 **Set-CsPersistentChatActiveServer** cmdlet을 사용하여 영구 채팅 풀에서 하나 이상의 서버에 대해 영구 채팅 서비스를 사용하거나 사용하지 않도록 설정할 수 있습니다. 활성 서버 목록에 표시되는 서버는 새 클라이언트 연결을 수락할 수 있으며 목록에 표시되지 않는 서버는 새 클라이언트 연결을 수락할 수 없습니다. 그러나 서버가 목록에서 제거되기 전에 설정된 클라이언트 연결은 계속 사용 가능합니다. 영구 채팅 서버에서 영구 채팅 서비스를 사용하도록 설정하려면 해당 서버를 활성 서버 목록에 추가합니다. 서비스를 사용하지 않도록 설정하려면 활성 서버 목록에서 서버를 제거합니다.

풀의 모든 서버에 대해 영구 채팅 서비스를 사용하거나 사용하지 않도록 설정하려면 **Set-CsPersistentChatState** cmdlet을 사용합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsPersistentChatActiveServer"}

**Lync Server 제어판:** **Set-CsPersistentChatActiveServer** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>ActiveServers</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>활성 영구 채팅 서버를 나타내는 정규화된 도메인 이름의 컬렉션입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Swap</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 지정된 풀의 모든 영구 채팅 서버에 대해 활성 상태를 전환합니다. 즉, 활성 서버는 비활성으로 표시되고 비활성 서버는 활성으로 표시됩니다.</p></td>
</tr>
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
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>활성 서버 컬렉션의 고유 ID입니다. 영구 채팅 서버에 대해서는 전역 컬렉션을 하나만 사용할 수 있습니다.</p></td>
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

없음. **Set-CsPersistentChatActiveServer** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음.

## 참고 항목

#### 기타 리소스

[Set-CsPersistentChatState](set-cspersistentchatstate.md)

