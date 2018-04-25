---
title: Get-CsUserReplicatorConfiguration
TOCTitle: Get-CsUserReplicatorConfiguration
ms:assetid: 7318ae92-e07b-4817-9ec1-be9c7f35aa26
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398548(v=OCS.15)
ms:contentKeyID: 49304024
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsUserReplicatorConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

현재 조직에 사용되는 User Replicator 구성 설정에 대한 정보를 반환합니다. User Replicator는 Active Directory에서 최신 사용자 계정 정보를 주기적으로 검색하여 Lync Server에서 저장한 최신 사용자 데이터와 동기화합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsUserReplicatorConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsUserReplicatorConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1의 명령은 현재 조직에서 사용되는 모든 User Replicator 구성 설정에 대한 정보를 반환합니다.

    Get-CsUserReplicatorConfiguration

## 자세한 정보

Lync Server는 사용자 계정 및 사용자 계정 데이터에 대한 자체 데이터베이스를 유지 관리하지만 Lync Server는 여전히 Active Directory를 사용자 정보의 기본적인 출처로 사용합니다. 예를 들어 새 Active Directory 사용자 계정을 만든 경우 해당 사용자 계정에 대한 기본 정보(예: Active Directory 표시 이름)를 제공해야 합니다. 그러나 사용자가 Lync Server를 사용할 수 있는 경우 해당 사용자의 새 표시 이름을 지정할 필요가 없습니다. Lync Server는 Active Directory 도메인 서비스에 이미 저장된 표시 이름을 사용하기 때문입니다.

물론 Active Directory 표시 이름을 비롯하여 사용자 계정 정보는 이후에 변경될 수 있습니다. 예를 들어 결혼한 사용자가 성을 변경하여 자신의 표시 이름을 변경해야 할 수 있습니다. Lync Server 데이터베이스와 Active Directory를 동기화된 상태로 유지하려면 Lync Server에서 주기적으로 Active Directory를 확인하고, 최신 사용자 계정 업데이트를 검색한 다음, 그에 따라 사용자 데이터베이스를 수정해야 합니다. Active Directory와 Lync Server 간의 이러한 동기화는 User Replicator에 의해 수행됩니다.

Lync Server를 설치하면 전역 User Replicator 설정 집합이 만들어집니다. 기본적으로 이러한 설정은 조직 전체에서 User Replicator를 관리하는 데 사용됩니다. User Replicator 관리는 Lync Server에서 동기화해야 하는 도메인을 확인하는 작업과 User Replicator가 Active Directory에서 사용자 계정 업데이트를 확인하는 주기를 지정하는 작업으로 구성됩니다. 기본적으로 User Replicator는 사용 가능한 모든 도메인을 검색하여 동기화합니다. 그러나 AdDomainNamingContextList 속성을 사용하면 특정 도메인 집합, 즉 AdDomainNamingContextList 속성에 표시된 도메인으로 동기화를 제한할 수 있습니다.

Lync Server를 사용하는 경우 CsUserReplicatorConfiguration cmdlet을 사용하여 서비스 범위에서 구성 설정을 생성하고 관리할 수도 있습니다. 그러나 온-프레미스 버전의 Lync Server에서는 전역 범위에 할당된 단일 구성 설정 컬렉션으로 범위가 제한됩니다.

관리자는 **Get-CsUserReplicatorConfiguration** cmdlet을 사용하여 현재 조직에서 사용되는 모든 User Replicator 설정에 대한 정보를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsUserReplicatorConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsUserReplicatorConfiguration"}

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
<td><p>반환할 User Replicator 구성 설정의 컬렉션을 지정할 때 와일드카드를 사용할 수 있도록 합니다. 예를 들어 -Filter &quot;service:*&quot; 명령은 서비스 범위에 구성된 모든 설정을 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 User Replicator 구성 설정의 고유 식별자입니다. 서비스 범위의 설정을 반환하려면 -Identity &quot;service:Registrar:atl-cs-001.litwareinc.com&quot;과 유사한 구문을 사용합니다. 서비스 범위 설정은 Lync Online을 실행 중인 경우에만 사용할 수 있습니다. 전역 설정을 반환하려면 -Identity global 구문을 사용합니다. 이 매개 변수가 지정되지 않으면 현재 조직에서 사용되는 모든 User Replicator 구성 설정이 반환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 User Replicator 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsUserReplicatorConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsUserReplicatorConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserReplicator.UserReplicatorConfiguration 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsUserReplicatorConfiguration](new-csuserreplicatorconfiguration.md)  
[Remove-CsUserReplicatorConfiguration](remove-csuserreplicatorconfiguration.md)  
[Set-CsUserReplicatorConfiguration](set-csuserreplicatorconfiguration.md)

