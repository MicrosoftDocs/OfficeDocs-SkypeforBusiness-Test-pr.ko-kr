---
title: Set-CsPresencePolicy
TOCTitle: Set-CsPresencePolicy
ms:assetid: 2d1f157b-d35d-402b-904d-281c013d2c30
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425782(v=OCS.15)
ms:contentKeyID: 49303165
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsPresencePolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 현재 상태 정책을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsPresencePolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsPresencePolicy [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-MaxCategorySubscription <UInt16>] [-MaxPromptedSubscriber <UInt16>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 사용자별 현재 상태 정책 RedmondPresencePolicy를 수정합니다. 이 예제에서는 MaxPromptedSubscriber 속성의 값이 300으로 설정됩니다.

    Set-CsPresencePolicy -Identity "RedmondPresencePolicy" -MaxPromptedSubscriber 300

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령의 변형이지만, 이 경우 조직에서 사용하도록 구성된 모든 현재 상태 정책에 대해 MaxPromptedSubscriber 속성이 300으로 설정됩니다. 이 작업을 수행하기 위해 이 명령은 먼저 매개 변수 없이 **Get-CsPresencePolicy** cmdlet을 호출합니다. 그러면 조직에서 사용하도록 구성된 모든 현재 상태 정책 컬렉션이 반환됩니다. 이 컬렉션은 컬렉션에 포함된 각 정책의 MaxPromptedSubscriber 값을 300으로 변경하는 **Set-CsPresencePolicy** cmdlet에 파이프됩니다.

    Get-CsPresencePolicy | Set-CsPresencePolicy -MaxPromptedSubscriber 300

## 예제 3

예제 3에서는 300명을 초과하는 프롬프트 구독자를 허용하는 정책이 없도록 조직의 현재 상태 정책을 구성하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 이 명령은 먼저 매개 변수 없이 **Get-CsPresencePolicy** cmdlet을 호출하여 조직의 모든 현재 상태 정책 컬렉션을 반환합니다. 이 컬렉션은 MaxPromptedSubscriber 정책 값이 300보다 큰 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 정책에 대해 최대 프롬프트 구독자 수를 300명으로 설정하는 **Set-CsPresencePolicy** cmdlet에 파이프됩니다. 그러면 일부 정책에서 300명 미만인 구독자를 허용할 수 있지만 어떤 정책에서도 300명이 넘는 프롬프트 구독자 수는 허용하지 않게 됩니다.

    Get-CsPresencePolicy | Where-Object {$_.MaxPromptedSubscriber -gt 300} | Set-CsPresencePolicy -MaxPromptedSubscriber 300

## 자세한 정보

현재 상태 정보는 대화 상대가 메신저 대화에 참여할 수 있는지를 알려 주는 매우 유용한 정보입니다. 하지만 이와 동시에 현재 상태 정보와 관련하여 발생하는 비용이 있습니다. 현재 상태 구독 수가 많아질수록 현재 상태 정보를 업데이트하는 데 더 많은 네트워크 대역폭을 할당해야 합니다. 네트워크 대역폭이 문제가 되는 경우 사용자당 허용되는 현재 상태 구독 수를 제한할 수 있습니다.

**CsPresencePolicy** cmdlet을 사용하면 현재 상태 구독의 중요한 두 가지 요소인 프롬프트 구독자 및 범주 구독을 관리할 수 있습니다. 사용자가 다른 사람의 Lync 대화 상대 목록에 추가되면 기본적으로 이 목록에 추가되었음을 알리는 팝업 메시지가 나타납니다. 팝업을 해제할 때까지 각 알림에서 프롬프트 구독자로 간주합니다. 현재 상태 정책의 MaxPromptedSubscriber 속성을 사용하면 한 사용자에게 허용되는 확인되지 않은 알림 대화 상자의 최대 개수를 지정할 수 있습니다. 최대 개수에 도달하면 일부 대화 상자를 확인할 때까지 새 대화 상대 알림을 받을 수 없습니다.

범주 구독은 특정 범주의 정보에 대한 요청을 나타냅니다. 예를 들어 일정 데이터를 요청하는 응용 프로그램이 여기에 해당합니다. MaxCategorySubscription 속성을 통해 관리자는 한 사용자에게 허용되는 범주 구독 수를 제한할 수 있습니다.

Lync Server 버전 이전에는 프롬프트 구독자와 범주 구독을 전역적으로 관리했습니다. 하지만 이제는 **CsPresencePolicy** cmdlet을 사용하여 이러한 현재 상태 구독을 전역 범위, 사이트 범위 또는 사용자별 범위에서 관리할 수 있습니다. 이렇게 하면 대역폭 사용을 제어하는 동시에 사용자가 작업을 수행하는 데 필요한 현재 상태 정보에 액세스하도록 할 수 있습니다.

**Set-CsPresencePolicy** cmdlet을 통해 조직에서 사용하도록 구성된 모든 현재 상태 정책을 수정할 수 있습니다. 현재 상태 정책의 수정은 단순히 MaxPromptedSubscriber 속성 및/또는 MaxCategorySubscription 속성의 값을 변경하는 것을 의미합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsPresencePolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsPresencePolicy"}

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
<td><p>관리자가 현재 상태 정책과 함께 표시할 추가 텍스트를 제공하는 데 사용됩니다. 예를 들어 정책을 할당할 사용자에 대한 정보를 설명에 포함할 수 있습니다.</p></td>
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
<td><p>수정할 현재 상태 정책의 고유 식별자입니다. 전역 정책을 수정하려면 -Identity global 구문을 사용합니다. 사이트 범위에서 정책을 수정하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. 사용자별 정책을 수정하려면 -Identity &quot;RedmondPresencePolicy&quot;와 유사한 구문을 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>현재 상태 정책 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxCategorySubscription</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>한 번에 허용되는 최대 범주 구독 수입니다. 범주 구독은 특정 범주의 정보에 대한 요청을 나타냅니다. 예를 들어 일정 데이터를 요청하는 응용 프로그램이 여기에 해당합니다.</p>
<p>MaxCategorySubscription은 0에서 3000 사이의 정수 값으로 설정할 수 있으며, 기본값은 1000입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxPromptedSubscriber</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>사용자에게 한 번에 허용되는 최대 프롬프트 구독자 수입니다. 기본적으로 사용자가 다른 사용자의 대화 상대 목록에 추가될 때마다 사용자에게 이 사실을 알리고 상대방을 자신의 대화 상대 목록에 추가하거나 상대방이 자신의 현재 상태를 확인하지 못하게 차단하도록 선택할 수 있는 알림 대화 상자가 표시됩니다. 작업을 수행하고 대화 상자를 취소할 때까지는 각 알림에서 프롬프트 구독자로 간주합니다.</p>
<p>MaxPromptedSubscriber는 0에서 600(포함) 사이의 정수 값으로 설정할 수 있으며, 기본값은 200입니다. 이 값을 0으로 설정하면 사용자가 다른 사용자의 대화 상대 목록에 추가될 때 알림이 제공되지 않습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Presence.PresencePolicy 개체입니다. **Set-CsPresencePolicy** cmdlet은 현재 상태 정책 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsPresencePolicy** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Presence.PresencePolicy 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPresencePolicy](get-cspresencepolicy.md)  
[Grant-CsPresencePolicy](grant-cspresencepolicy.md)  
[New-CsPresencePolicy](new-cspresencepolicy.md)  
[Remove-CsPresencePolicy](remove-cspresencepolicy.md)

