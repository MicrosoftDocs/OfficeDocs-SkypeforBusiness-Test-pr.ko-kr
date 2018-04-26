---
title: Remove-CsPresencePolicy
TOCTitle: Remove-CsPresencePolicy
ms:assetid: ecdbfef8-2b7c-4bd7-bf01-7fb230eefe9f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399070(v=OCS.15)
ms:contentKeyID: 49305440
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsPresencePolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 현재 상태 정책을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsPresencePolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 RedmondPresencePolicy인 사용자별 현재 상태 정책을 삭제합니다.

    Remove-CsPresencePolicy -Identity "RedmondPresencePolicy"

## 예제 2

예제 2에 표시된 명령은 사용자별 범위에서 구성된 모든 현재 상태 정책을 제거합니다. 이러한 정책은 ID가 접두사 "tag:"으로 시작합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPresencePolicy** cmdlet 및 Filter 매개 변수를 사용하여 모든 사용자별 현재 상태 정책을 반환합니다. 필터 값 "tag:\*"는 반환되는 데이터를 ID가 문자열 값 "tag:"으로 시작하는 정책으로 제한합니다. 필터링된 컬렉션은 컬렉션의 각 정책을 삭제하는 **Remove-CsPresencePolicy** cmdlet에 파이프됩니다.

    Get-CsPresencePolicy -Filter "tag:*" | Remove-CsPresencePolicy

## 예제 3

예제 3에서는 500명이 넘는 프롬프트 구독자를 허용하는 모든 현재 상태 정책을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsPresencePolicy** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 현재 상태 정책 컬렉션을 반환합니다. 이 컬렉션은 MaxPromptedSubscriber 속성이 500보다 큰 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 500명이 넘는 프롬프트 구독자를 허용하는 모든 현재 상태 정책을 삭제하는 **Remove-CsPresencePolicy** cmdlet에 파이프됩니다.

    Get-CsPresencePolicy | Where-Object {$_.MaxPromptedSubscriber -gt 500} | Remove-CsPresencePolicy

## 자세한 정보

현재 상태 정보는 대화 상대가 메신저 대화에 참여할 수 있는지를 알려 주는 매우 유용한 정보입니다. 하지만 이와 동시에 현재 상태 정보와 관련하여 발생하는 비용이 있습니다. 현재 상태 구독 수가 많아질수록 현재 상태 정보를 업데이트하는 데 더 많은 네트워크 대역폭을 할당해야 합니다. 네트워크 대역폭이 문제가 되는 경우 사용자당 허용되는 현재 상태 구독 수를 제한할 수 있습니다.

**CsPresencePolicy** cmdlet을 사용하면 현재 상태 구독의 중요한 두 가지 요소인 프롬프트 구독자 및 범주 구독을 관리할 수 있습니다. 사용자가 다른 사람의 Lync 대화 상대 목록에 추가되면 기본적으로 이 목록에 추가되었음을 알리는 팝업 메시지가 나타납니다. 팝업을 해제할 때까지 각 알림에서 프롬프트 구독자로 간주합니다. 현재 상태 정책의 MaxPromptedSubscriber 속성을 사용하면 한 사용자에게 허용되는 확인되지 않은 알림 대화 상자의 최대 개수를 지정할 수 있습니다. 최대 개수에 도달하면 일부 대화 상자를 해제할 때까지 새 대화 상대 알림을 받을 수 없습니다.

범주 구독은 특정 범주의 정보에 대한 요청을 나타냅니다. 예를 들어 일정 데이터를 요청하는 응용 프로그램이 여기에 해당합니다. MaxCategorySubscription 속성을 통해 관리자는 한 사용자에게 허용되는 범주 구독 수를 제한할 수 있습니다.

Lync Server 버전 이전에는 프롬프트 구독자와 범주 구독을 전역적으로 관리했습니다. 하지만 이제는 **CsPresencePolicy** cmdlet을 사용하여 이러한 현재 상태 구독을 전역 범위, 사이트 범위 또는 사용자별 범위에서 관리할 수 있습니다. 이렇게 하면 대역폭 사용을 제어하는 동시에 사용자가 작업을 수행하는 데 필요한 현재 상태 정보에 액세스하도록 할 수 있습니다.

사이트 범위 또는 사용자별 범위에서 만든 정책은 **Remove-CsPresencePolicy** cmdlet을 실행하여 언제든지 제거할 수 있습니다. 또한 이 cmdlet을 전역 정책에 대해 실행할 수도 있습니다. 그러나 전역 정책은 실제로 제거되지 않습니다. ( Lync Server에서는 전역 정책을 제거할 수 없습니다. 대신 전역 정책의 두 가지 속성(MaxPromptedSubscriber 및 MaxCategorySubscription)이 기본값으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsPresencePolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsPresencePolicy"}

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
<td><p>제거할 현재 상태 정책의 고유 식별자입니다. 사이트 범위에서 구성된 정책을 제거하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용하고, 사용자별 범위에서 구성된 정책을 제거하려면 -Identity &quot;RedmondPresencePolicy&quot;와 유사한 구문을 사용합니다.</p>
<p>전역 정책에 대해 <strong>Remove-CsPresencePolicy</strong> cmdlet을 실행할 수도 있습니다. 이 경우에는 -Identity global 구문을 사용합니다. 그러나 이 경우 전역 정책은 제거되지 않습니다. 대신 해당 정책 내의 속성이 기본값으로 다시 설정됩니다.</p></td>
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
<td><p>이 매개 변수가 있으면 <strong>Remove-CsPresencePolicy</strong> cmdlet이 사용자별 정책을 삭제합니다. 이는 해당 정책이 한 명 이상의 사용자에게 현재 할당된 경우에도 마찬가지입니다. 이 매개 변수가 없으면 아직 사용 중인 정책을 제거하기 전에 삭제 요청을 확인하는 메시지가 나타납니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Presence.PresencePolicy 개체입니다. **Remove-CsPresencePolicy** cmdlet은 현재 상태 정책 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsPresencePolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Presence.PresencePolicy 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPresencePolicy](get-cspresencepolicy.md)  
[Grant-CsPresencePolicy](grant-cspresencepolicy.md)  
[New-CsPresencePolicy](new-cspresencepolicy.md)  
[Set-CsPresencePolicy](set-cspresencepolicy.md)

