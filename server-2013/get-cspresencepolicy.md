---
title: Get-CsPresencePolicy
TOCTitle: Get-CsPresencePolicy
ms:assetid: 65880bdb-4482-4cfb-83de-19b239784fe5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398463(v=OCS.15)
ms:contentKeyID: 49303855
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPresencePolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 현재 상태 정책에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsPresencePolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsPresencePolicy [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1의 명령은 조직의 사용자에 대해 구성된 모든 현재 상태 정책에 대한 정보를 반환합니다. 이 작업은 **Get-CsPresencePolicy** cmdlet을 매개 변수 없이 호출하여 수행합니다.

    Get-CsPresencePolicy

## 예제 2

예제 2에서는 하나의 사용자별 현재 상태, 즉 Identity가 RedmondPresencePolicy인 정책을 반환합니다.

    Get-CsPresencePolicy -Identity "RedmondPresencePolicy"

## 예제 3

예제 3에서는 사이트 범위에 구성된 모든 현재 상태 정책에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 Filter 매개 변수 및 필터 값 "site:\*"를 사용합니다. 이 필터 값은 반환되는 데이터를 ID가 문자열 값 "site:"으로 시작하는 모든 현재 상태 정책으로 제한합니다.

    Get-CsPresencePolicy -Filter "site:*"

## 예제 4

예제 4에서는 프롬프트된 구독자의 최대 수가 100명 이하로 제한되는 모든 현재 상태 정책에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsPresencePolicy** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 현재 상태 정책 컬렉션을 반환합니다. 그러면 이 컬렉션은 MaxPromptedSubscriber 속성이 100보다 작거나 같은 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsPresencePolicy | Where-Object {$_.MaxPromptedSubscriber -le 100}

## 자세한 정보

현재 상태 정보는 대화 상대가 메신저 대화에 참여할 수 있는지를 알려 주는 매우 유용한 정보입니다. 하지만 이와 동시에 현재 상태 정보와 관련하여 발생하는 비용이 있습니다. 현재 상태 구독 수가 많아질수록 현재 상태 정보를 업데이트하는 데 더 많은 네트워크 대역폭을 할당해야 합니다. 네트워크 대역폭이 문제가 되는 경우 사용자당 허용되는 현재 상태 구독 수를 제한할 수 있습니다.

**CsPresencePolicy** cmdlet을 사용하면 현재 상태 구독의 중요한 두 가지 요소인 프롬프트 구독자 및 범주 구독을 관리할 수 있습니다. 사용자가 다른 사람의 Lync 대화 상대 목록에 추가되면 기본적으로 이 목록에 추가되었음을 알리는 팝업 메시지가 나타납니다. 팝업을 해제할 때까지 각 알림에서 프롬프트 구독자로 간주합니다. 현재 상태 정책의 MaxPromptedSubscriber 속성을 사용하면 한 사용자에게 허용되는 확인되지 않은 알림 대화 상자의 최대 개수를 지정할 수 있습니다. 최대 개수에 도달하면 일부 대화 상자를 확인할 때까지 새 대화 상대 알림을 받을 수 없습니다.

범주 구독은 특정 범주의 정보에 대한 요청을 나타냅니다. 예를 들어 일정 데이터를 요청하는 응용 프로그램이 여기에 해당합니다. MaxCategorySubscription 속성을 통해 관리자는 한 사용자에게 허용되는 범주 구독 수를 제한할 수 있습니다.

Lync Server 버전 이전에는 프롬프트 구독자와 범주 구독을 전역적으로 관리했습니다. 하지만 이제는 **CsPresencePolicy** cmdlet을 사용하여 이러한 현재 상태 구독을 전역 범위, 사이트 범위 또는 사용자별 범위에서 관리할 수 있습니다. 이렇게 하면 대역폭 사용을 제어하는 동시에 사용자가 작업을 수행하는 데 필요한 현재 상태 정보에 액세스하도록 할 수 있습니다.

**Get-CsPresencePolicy** cmdlet은 조직에서 사용하도록 구성된 모든 현재 상태 정책에 대한 정보를 반환할 수 있는 수단을 제공합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsPresencePolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPresencePolicy"}

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>반환할 정책을 지정할 때 와일드카드를 사용할 수 있도록 합니다. 예를 들어 사이트 범위에서 구성된 모든 현재 상태 정책을 반환하려면 -Filter &quot;site:*&quot; 구문을 사용하고,</p>
<p>Filter와 Identity 매개 변수를 같은 명령에서 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 현재 상태 정책의 고유 식별자입니다. 전역 정책을 반환하려면 -Identity global 구문을 사용합니다. 사이트 범위에 구성된 정책을 반환하려면 -Identity &quot;site:Redmond&quot; 형태의 구문을 사용합니다. 사용자별 범위에 구성된 정책을 반환하려면 -Identity &quot;RedmondPresencePolicy&quot; 형태의 구문을 사용합니다. Identity를 지정할 때 와일드카드 문자를 사용할 수 없습니다.</p>
<p>Identity 또는 Filter 매개 변수 중 아무것도 지정되지 않은 경우 <strong>Get-CsPresencePolicy</strong> cmdlet은 조직에서 사용자에 대해 구성된 모든 현재 상태 정책을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 현재 상태 정책 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsPresencePolicy** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsPresencePolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Presence.PresencePolicy 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Grant-CsPresencePolicy](grant-cspresencepolicy.md)  
[New-CsPresencePolicy](new-cspresencepolicy.md)  
[Remove-CsPresencePolicy](remove-cspresencepolicy.md)  
[Set-CsPresencePolicy](set-cspresencepolicy.md)

