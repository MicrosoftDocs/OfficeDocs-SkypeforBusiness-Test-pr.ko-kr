---
title: New-CsUserReplicatorConfiguration
TOCTitle: New-CsUserReplicatorConfiguration
ms:assetid: eb4dee9e-9ba4-4726-8f7c-b355433ed594
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399059(v=OCS.15)
ms:contentKeyID: 49305412
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsUserReplicatorConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

User Replicator 구성 설정의 새 컬렉션을 만듭니다. User Replicator는 Active Directory에서 최신 사용자 계정 정보를 주기적으로 검색하여 Lync Server에서 저장한 최신 사용자 데이터와 동기화합니다. 이 cmdlet은 Lync Online에서 사용하기 위해 만들어졌으며 온-프레미스 버전의 Lync Server에서는 작동하지 않습니다.

## 구문

    New-CsUserReplicatorConfiguration -Identity <XdsIdentity> [-ADDomainNamingContextList <PSListModifier>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-ReplicationCycleInterval <TimeSpan>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Registrar:atl-cs-001.litwareinc.com 서비스에 대한 User Replicator 구성 설정의 새 컬렉션을 만듭니다. 추가 매개 변수를 지정하지 않았으므로 새 컬렉션에서 기본 User Replicator 값을 사용합니다.

    New-CsUserReplicatorConfiguration -Identity "service:Registrar:atl-cs-001.litwareinc.com"

## 예제 2

예제 2에서도 Registrar:atl-cs-001.litwareinc.com 서비스에 대한 User Replicator 구성 설정의 새 컬렉션을 만듭니다. 그러나 이 예제에서는 동기화할 두 도메인의 고유 이름 fabrikam.com 및 contoso.com과 함께 ADDomainNamingContextList를 추가합니다. 이러한 새 User Replicator 구성 설정 컬렉션은 다른 도메인을 사용할 수 있는 경우에도 이러한 두 도메인에 대해서만 구성할 수 있습니다.

    New-CsUserReplicatorConfiguration -Identity "service:Registrar:atl-cs-001.litwareinc.com" -ADDomaiNamingContextList @{Add="dc=fabrikam,dc=com","dc=contoso.com"}

## 자세한 정보

Lync Server는 사용자 계정 및 사용자 계정 데이터에 대한 자체 데이터베이스를 유지 관리하지만 Lync Server는 여전히 Active Directory를 사용자 정보의 기본적인 출처로 사용합니다. 예를 들어 새 Active Directory 사용자 계정을 만든 경우 해당 사용자 계정에 대한 기본 정보(예: Active Directory 표시 이름)를 제공해야 합니다. 사용자가 Lync Server를 사용할 수 있는 경우 새 표시 이름을 지정할 필요가 없습니다. Lync Server이 Active Directory에 이미 저장된 표시 이름을 사용하기 때문입니다.

Active Directory 표시 이름과 같은 사용자 계정 정보는 시간이 지남에 따라 변경될 수 있습니다. 예를 들어 결혼한 사용자가 성을 변경하여 자신의 표시 이름을 변경해야 할 수 있습니다. Lync Server 데이터베이스와 Active Directory를 동기화된 상태로 유지하려면 Lync Server에서 주기적으로 Active Directory를 확인하고, 최신 사용자 계정 업데이트를 검색한 다음, 그에 따라 Lync Server 사용자 데이터베이스를 수정해야 합니다. Active Directory와 Lync Server 간의 이러한 동기화는 User Replicator에 의해 수행됩니다.

Lync Server를 설치하면 User Replicator 구성 설정의 전역 집합이 자동으로 만들어집니다. 기본적으로 이러한 설정은 전체 조직에서 User Replicator를 관리하는 데 사용됩니다. User Replicator 관리는 Lync Server에서 동기화해야 하는 도메인을 확인하는 작업과 User Replicator가 Active Directory에서 사용자 계정 업데이트를 확인하는 주기를 지정하는 작업으로 구성됩니다. 또한 Lync Online을 사용하는 경우에 한해 서비스 범위에서 추가 컬렉션을 만들 수도 있습니다.

새 User Replicator 구성 설정은 **New-CsUserReplicatorConfiguration** cmdlet을 사용하여 만듭니다. 이러한 설정은 서비스 범위에서 Lync Online용으로만 만들 수 있습니다. 온-프레미스 버전의 Lync Server에 대한 새 User Replicator 설정은 만들 수 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsUserReplicatorConfiguration** cmdlet을 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsUserReplicatorConfiguration"}

``` 
```

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
<td><p>만들 User Replicator 구성 설정의 고유 식별자입니다. 설정은 등록자 서비스에 한해 서비스 범위에서만 만들 수 있습니다. 즉, 새 설정의 ID는 -Identity &quot;service:Registrar:atl-cs-001.litwareinc.com&quot;과 유사해야 합니다.</p>
<p>이는 Lync Server에만 적용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ADDomainNamingContextList</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>User Replicator와 동기화해야 하는 Active Directory 도메인의 고유 이름입니다. 예를 들어 목록에 도메인을 추가하려면</p>
<p>-ADDomainNamingContextList @{Add=&quot;dc=fabrikam,dc=com&quot;}과 유사한 구문을 사용합니다.</p>
<p><strong>New-CsUserReplicatorConfiguration</strong> cmdlet을 호출할 때 하나 이상의 도메인 이름을 추가할 수 있습니다. 이 작업을 수행하려면 쉼표를 사용하여 도메인 이름을 구분하면 됩니다.</p>
<p>-ADDomainNamingContextList @{Add=&quot;dc=fabrikam,dc=com&quot;,&quot;dc=contoso,dc=com&quot;}</p>
<p></p>
<p>이 속성을 null 값으로 설정하면 User Replicator가 사용할 수 있는 모든 도메인을 검색하여 이러한 도메인과 동기화합니다. 이 속성이 null이 아닐 경우 복제기가 ADDomainNamingContextList에 지정된 도메인과만 동기화합니다.</p></td>
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
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ReplicationCycleInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>Active Directory에서 사용자 계정 업데이트를 확인하기 전에 User Replicator가 대기하는 시간을 나타냅니다. 복제 주기 간격은 1초에서 23시간 59분 59초 사이의 시간일 수 있으며, 기본값은 1분입니다. 간격은 시:분:초 형식을 사용하여 표시해야 합니다. 예를 들어 -ReplicationCycleInterval 01:15:00 구문은 시간 간격을 1시간 15분으로 설정합니다.</p></td>
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

없음. **New-CsUserReplicatorConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsUserReplicatorConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserReplicator.UserReplicatorConfiguration 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsUserReplicatorConfiguration](get-csuserreplicatorconfiguration.md)  
[Remove-CsUserReplicatorConfiguration](remove-csuserreplicatorconfiguration.md)  
[Set-CsUserReplicatorConfiguration](set-csuserreplicatorconfiguration.md)

