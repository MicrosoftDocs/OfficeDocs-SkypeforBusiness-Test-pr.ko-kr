---
title: Remove-CsUserReplicatorConfiguration
TOCTitle: Remove-CsUserReplicatorConfiguration
ms:assetid: 26c3a357-558f-406f-8df3-059911f771f0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425738(v=OCS.15)
ms:contentKeyID: 49303097
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsUserReplicatorConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 User Replicator 구성 설정 컬렉션을 제거합니다. User Replicator는 Active Directory에서 최신 사용자 계정 정보를 주기적으로 검색하여 Lync Server에서 저장한 최신 사용자 데이터와 동기화합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsUserReplicatorConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 전역 User Replicator 구성 설정을 다시 설정합니다.

    Remove-CsUserReplicatorConfiguration -Identity global

## 자세한 정보

Lync Server는 사용자 계정 및 사용자 계정 데이터에 대한 자체 데이터베이스를 유지 관리하지만 Lync Server는 여전히 Active Directory를 사용자 정보의 기본적인 출처로 사용합니다. 예를 들어 새 Active Directory 사용자 계정을 만든 경우 해당 사용자 계정에 대한 기본 정보(예: Active Directory 표시 이름)를 제공해야 합니다. 그러나 사용자가 Lync Server를 사용하도록 설정된 경우에는 새 표시 이름을 지정할 필요가 없습니다. Lync Server는 Active Directory에 이미 저장된 표시 이름을 사용하기 때문입니다.

물론 Active Directory 표시 이름을 비롯하여 사용자 계정 정보는 이후에 변경될 수 있습니다. 예를 들어 결혼한 사용자가 성을 변경하여 자신의 표시 이름을 변경해야 할 수 있습니다. Lync Server 데이터베이스와 Active Directory를 동기화된 상태로 유지하려면 Lync Server에서 주기적으로 Active Directory에 연결하고, 최신 사용자 계정 업데이트를 검색한 다음, 그에 따라 Lync Server 사용자 데이터베이스를 수정해야 합니다. Active Directory와 Lync Server 간의 이러한 동기화는 User Replicator에 의해 수행됩니다.

Lync Server를 설치하면 전역 User Replicator 구성 설정 집합이 만들어집니다. 기본적으로 이러한 설정은 조직 전체에서 User Replicator를 관리하는 데 사용됩니다. User Replicator 관리는 Lync Server에서 동기화해야 하는 도메인을 확인하는 작업과 User Replicator가 Active Directory에서 사용자 계정 업데이트를 확인하는 주기를 지정하는 작업으로 구성됩니다. 기본적으로 User Replicator는 사용 가능한 모든 도메인을 검색하여 동기화합니다. 그러나 AdDomainNamingContextList 속성을 사용하면 특정 도메인 집합, 즉 AdDomainNamingContextList 속성에 표시된 도메인으로 동기화를 제한할 수 있습니다.

또한 Lync Online을 사용하는 경우에 한해 서비스 범위에서 추가 컬렉션을 만들 수도 있습니다.

변경해야 하는 경우 **Remove-CsUserReplicatorConfiguration** cmdlet을 사용하여 서비스 범위에서 만들어진 사용자 지정 설정을 제거할 수 있습니다. 전역 구성 설정에 대해 이 cmdlet을 실행할 수도 있습니다. 그러나 이 경우 전역 설정은 제거되지 않습니다. 대신 전역 컬렉션의 모든 속성이 기본값으로 다시 설정됩니다. User Replicator의 경우 동기화해야 하는 도메인 목록이 지워지고(이 경우 Replicator가 검색 가능한 모든 도메인과 동기화됨) 복제 간격 주기가 1분으로 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsUserReplicatorConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsUserReplicatorConfiguration"}

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
<td><p>제거할 User Replicator 구성 설정의 고유 식별자입니다. 서비스 범위에서 설정을 제거하려면 -Identity &quot;service:Registrar:atl-cs-001.litwareinc.com&quot;과 유사한 구문을 사용합니다. Lync Online을 사용하는 경우 서비스 범위의 설정만 제거할 수 있습니다. 전역 설정을 다시 설정하려면 -Identity global 구문을 사용합니다. Identity를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.UserReplicator.UserReplicatorConfiguration 개체입니다. **Remove-CsUserReplicatorConfiguration** cmdlet은 User Replicator 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsUserReplicatorConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserReplicator.UserReplicatorConfiguration 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUserReplicatorConfiguration](get-csuserreplicatorconfiguration.md)  
[New-CsUserReplicatorConfiguration](new-csuserreplicatorconfiguration.md)  
[Set-CsUserReplicatorConfiguration](set-csuserreplicatorconfiguration.md)

