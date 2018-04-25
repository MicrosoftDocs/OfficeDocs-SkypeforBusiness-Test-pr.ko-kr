---
title: Set-CsUserReplicatorConfiguration
TOCTitle: Set-CsUserReplicatorConfiguration
ms:assetid: 7164960f-8e88-4c8d-9a12-1814aa2b9047
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398540(v=OCS.15)
ms:contentKeyID: 49304007
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsUserReplicatorConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 User Replicator 구성 설정 컬렉션을 수정합니다. User Replicator는 Active Directory 도메인 서비스에서 최신 사용자 계정 정보를 주기적으로 검색하여 Lync Server에서 저장한 최신 사용자 데이터와 동기화합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsUserReplicatorConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsUserReplicatorConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-ADDomainNamingContextList <PSListModifier>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-ReplicationCycleInterval <TimeSpan>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 전역 User Replicator 설정의 ReplicationCycleInterval 값을 5분(0시간: 05분: 00초)으로 설정합니다.

    Set-CsUserReplicatorConfiguration -Identity global -ReplicationCycleInterval "00:05:00"

## 예제 2

예제 2의 명령은 ADDomainNamingContextList 속성의 값을 지웁니다. 이 작업은 ADDomainNamingContextList 매개 변수를 포함하고 이 매개 변수 값을 null로 설정하여 수행합니다. 이 값을 null로 설정하면 User Replicator가 자동으로 사용 가능한 모든 도메인을 검색하고 동기화합니다.

    Set-CsUserReplicatorConfiguration -Identity global -ADDomainNamingContextList $Null

## 예제 3

예제 3에서는 전역 User Replicator 설정의 ADDomainNamingContextList 속성에 이름이 추가됩니다. 이를 위해 @{Add=} 구문과 추가되는 도메인의 고유 이름이 사용됩니다. 이 명령이 실행되면 fabrikam.com이 도메인 이름 목록에 추가됩니다. 목록에 fabrikam.com만 있도록 전역 설정을 구성하려면

\-ADDomainNamingContextList @{Replace="dc=fabrikam,dc=com"} 구문을 사용합니다.

AdDomainNamingContextList 속성이 null 값이 아닌 다른 값으로 설정된 경우 User Replicator가 속성 값에 나열된 도메인과만 동기화됩니다. 배포에 다른 도메인이 있는 경우에도 마찬가지입니다.

    Set-CsUserReplicatorConfiguration -Identity global -ADDomainNamingContextList @{Add="dc=fabrikam,dc=com"}

## 예제 4

예제 4에서는 전역 User Replicator 구성 설정의 ADDomainNamingContextList 속성에서 fabrikam.com 도메인을 제거합니다. 이 작업을 수행하기 위해 @{Remove=} 구문과 도메인의 DN(고유 이름)(dc=fabrikam,dc=com)이 사용됩니다.

    Set-CsUserReplicatorConfiguration -Identity global -ADDomainNamingContextList @{Remove="dc=fabrikam,dc=com"}

## 자세한 정보

Lync Server는 사용자 계정 및 사용자 계정 데이터에 대한 자체 데이터베이스를 유지 관리하지만 Lync Server는 여전히 AD DS를 사용자 정보의 기본적인 출처로 사용합니다. 예를 들어 새 Active Directory 사용자 계정을 만든 경우 해당 사용자 계정에 대한 기본 정보(예: Active Directory 표시 이름)를 제공해야 합니다. 사용자가 Lync Server를 사용할 수 있는 경우 새 표시 이름을 지정할 필요가 없습니다. Lync Server는 AD DS에 이미 저장된 표시 이름을 사용하기 때문입니다.

Active Directory 표시 이름과 같은 사용자 계정 정보는 시간이 지남에 따라 변경될 수 있습니다. 예를 들어 결혼한 사용자가 성을 변경하여 자신의 표시 이름을 변경해야 할 수 있습니다. Lync Server 데이터베이스와 AD DS를 동기화된 상태로 유지하려면 Lync Server에서 주기적으로 AD DS를 확인하고, 최신 사용자 계정 업데이트를 검색한 다음, 그에 따라 Lync Server 사용자 데이터베이스를 수정해야 합니다. AD DS와 Lync Server 간의 이러한 동기화는 User Replicator에 의해 수행됩니다.

Lync Server를 설치하면 전역 User Replicator 설정 집합이 만들어집니다. 기본적으로 이러한 설정은 조직 전체에서 User Replicator를 관리하는 데 사용됩니다. User Replicator 관리는 Lync Server에서 동기화해야 하는 도메인을 확인하는 작업과 User Replicator가 AD DS에서 사용자 계정 업데이트를 확인하는 주기를 지정하는 작업으로 구성됩니다. 기본적으로 User Replicator는 사용 가능한 모든 도메인을 검색하여 동기화합니다. 그러나 AdDomainNamingContextList 속성을 사용하면 특정 도메인 집합, 즉 AdDomainNamingContextList 속성에 표시된 도메인으로 동기화를 제한할 수 있습니다.

또한 Lync Online을 사용하는 경우에 한해 서비스 범위에서 추가 컬렉션을 만들 수도 있습니다.

**Set-CsUserReplicatorConfiguration** cmdlet을 사용하면 현재 조직에서 사용되는 모든 User Replicator 설정을 수정할 수 있습니다. 이 cmdlet을 사용하여 User Replicator가 동기화되어야 하는 도메인 목록에서 도메인을 추가 또는 삭제하고 복제 주기의 시간 간격을 수정할 수도 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsUserReplicatorConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsUserReplicatorConfiguration"}

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
<td><p><em>ADDomainNamingContextList</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>User Replicator와 동기화해야 하는 Active Directory 도메인의 고유 이름입니다. 예를 들어 목록에 도메인을 추가하려면</p>
<p>-ADDomainNamingContextList @{Add=&quot;dc=fabrikam,dc=com&quot;}과 유사한 구문을 사용합니다.</p>
<p>이 속성을 null 값으로 설정하면 User Replicator가 사용할 수 있는 모든 도메인을 검색하여 이러한 도메인과 동기화합니다. 이 속성이 null이 아닐 경우 User Replicator가 ADDomainNamingContextList에 지정된 도메인과만 동기화합니다.</p></td>
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
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 User Replicator 구성 설정의 고유 식별자입니다. 전역 설정을 수정하려면 -Identity global 구문을 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>User Replicator 구성 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ReplicationCycleInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>AD DS에서 사용자 계정 업데이트를 확인하기 전에 User Replicator가 대기하는 시간을 나타냅니다. 복제 주기 간격은 1초에서 23시간 59분 59초 사이의 시간일 수 있으며, 기본값은 1분입니다. 간격은 시간:분:초 형식으로 표현해야 합니다. 예를 들어 다음 구문은 시간 간격을 1시간 15분으로 설정합니다.</p>
<p>-ReplicationCycleInterval 01:15:00</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.UserReplicator.UserReplicatorConfiguration 개체입니다. **Set-CsUserReplicatorConfiguration** cmdlet은 User Replicator 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsUserReplicatorConfiguration** cmdlet은 개체나 값을 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserReplicator.UserReplicatorConfiguration 개체의 전역 인스턴스만 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUserReplicatorConfiguration](get-csuserreplicatorconfiguration.md)  
[New-CsUserReplicatorConfiguration](new-csuserreplicatorconfiguration.md)  
[Remove-CsUserReplicatorConfiguration](remove-csuserreplicatorconfiguration.md)

