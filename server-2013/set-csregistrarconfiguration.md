---
title: Set-CsRegistrarConfiguration
TOCTitle: Set-CsRegistrarConfiguration
ms:assetid: 9616b967-09dd-470d-8d0a-acce1ff4fbf9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398764(v=OCS.15)
ms:contentKeyID: 49304442
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsRegistrarConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존의 등록자 구성 설정 컬렉션에서 속성 값을 수정합니다. 등록자는 로그온 요청을 인증하고 사용자 상태에 대한 정보를 유지 관리하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsRegistrarConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsRegistrarConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-BackupStoreUnavailableThreshold <TimeSpan>] [-Confirm [<SwitchParameter>]] [-DefaultEndpointExpiration <Int32>] [-EnableDHCPServer <$true | $false>] [-Force <SwitchParameter>] [-MaxEndpointExpiration <Int32>] [-MaxEndpointsPerUser <UInt16>] [-MaxUserCount <UInt64>] [-MinEndpointExpiration <Int32>] [-PoolState <FailedOver | Active | FailingOver | FailingBack>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트(-Identity site:Redmond)에 적용된 등록자 구성 설정을 수정합니다. 이 예제에서는 EnableDHCPServer 속성 값을 True로 설정합니다.

    Set-CsRegistrarConfiguration -Identity site:Redmond -EnableDHCPServer $True

## 예제 2

예제 2에서는 사용자에게 8개보다 많은 끝점을 허용하는 모든 등록자 구성 설정이 수정됩니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsRegistrarConfiguration** cmdlet을 매개 변수 없이 호출합니다. 그러면 조직에서 사용 중인 모든 진단 구성 설정의 컬렉션이 반환됩니다. 그런 다음 이 컬렉션이 MaxEndpointsPerUser 속성이 8보다 큰(-gt) 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 마지막으로 필터링된 컬렉션은 해당 컬렉션의 각 항목에 대해 최대 끝점 수를 8로 설정하는 **Set-CsRegistrarConfiguration** cmdlet에 파이프됩니다.

    Get-CsRegistrarConfiguration | Where-Object {$_.MaxEndpointsPerUser -gt 8} | Set-CsRegistrarConfiguration -MaxEndpointsPerUser 8

## 예제 3

예제 3에 표시된 명령은 조직에서 등록자 구성 설정 컬렉션이 속하는 각 사이트에 대해 DHCP를 통한 클라이언트 등록을 사용하지 않도록 설정합니다. 이 작업을 수행하기 위해 명령은 **Get-CsRegistrarConfiguration** cmdlet을 Filter 매개 변수와 함께 호출합니다. 매개 변수 값 "site:\*"는 사이트 범위에 구성된 설정에 대한 데이터만 반환하도록 제한합니다. 그런 다음 이 컬렉션이 EnableDHCPServer 매개 변수 및 매개 변수 값 $False를 사용하여 클라이언트가 DHCP 서버를 사용하여 등록자를 찾지 못하게 하는 **Set-CsRegistrarConfiguration** cmdlet에 파이프됩니다.

    Get-CsRegistrarConfiguration -Filter "site:*"| Set-CsRegistrarConfiguration -EnableDHCPServer $False

## 자세한 정보

등록자는 Lync Server의 가장 중요한 구성 요소라고 할 수 있습니다. 등록자 없이는 사용자가 시스템에 로그온할 수 없으며 Lync Server에서 사용자와 사용자의 현재 상태를 추적할 수 없기 때문입니다. 사용자가 Lync Server에 로그온하면 로그온한 끝점에서 등록자에 REGISTER 요청을 보냅니다. 그러면 서버에서 클라이언트 장치의 인증 자격 증명을 요구하여 응답합니다. 클라이언트가 시도를 전달하면, 즉 클라이언트가 올바른 자격 증명 집합을 제공하면 사용자가 인증되고 IP 주소, 포트 및 사용자 이름과 같은 끝점 정보가 등록 데이터베이스에 로깅됩니다. 사용자가 로그오프하면 이 정보가 데이터베이스에서 제거됩니다. 로그온한 시점부터 로그오프할 때까지 등록자는 상태 정보를 최신 상태로 유지하면서 사용자가 주고받는 메시지의 경로 지정을 지원합니다.

등록자 구성 설정은 끝점과 끝점 구독을 관리하는 데 사용됩니다. 이러한 설정은 전역, 사이트 또는 서비스 범위에서 적용할 수 있습니다. 서비스 범위 설정은 등록자 서비스에만 사용할 수 있습니다. **Set-CsRegistrarConfiguration** cmdlet을 사용하여 조직에서 현재 사용 중인 등록자 구성 컬렉션의 일부 또는 정부를 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsRegistrarConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsRegistrarConfiguration"}

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
<td><p><em>BackupStoreUnavailableThreshold</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>시스템이 백업 저장소를 사용할 수 없다고 결정할 때까지 대기하는 시간을 지정합니다. 이 시간이 지나면 사용자가 지속 가능 모드로 전환됩니다. 기본값은 30분(00:30:00)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DefaultEndpointExpiration</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>끝점이 로그온하면 만료 시간 제한을 요청할 수 있습니다. 이는 끝점이 서버에 연결하여 연장을 요청하기 전까지 시스템에 로그온 상태로 있을 수 있는 시간 간격을 지정합니다. DefaultEndpointExpiration 속성은 특정 시간 제한 값을 요청하지 않은 클라이언트의 만료 시간 제한 간격을 나타냅니다.</p>
<p>DefaultEndpointExpiration은 300(5분)-900(15분) 사이여야 합니다. 기본값은 600(10분)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableDHCPServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>끝점이 DHCP 서버를 사용하여 등록자를 찾을 수 있는지 여부를 지정합니다. True일 경우 클라이언트가 처음 시작할 때 DHCP 알림 메시지를 보내고, DHCP 서버가 사용자를 로그온시키는 데 사용할 수 있는 등록자의 FQDN(정규화된 도메인 이름)을 보내 응답합니다.</p></td>
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
<td><p>수정할 등록자 구성 설정의 고유한 식별자입니다. 전역 설정을 수정하려면 -Identity global 구문을 사용합니다. 사이트 범위에 구성된 설정을 수정하려면 -Identity site:Redmond 구문을 사용합니다. 서비스 수준에서 설정을 수정하려면 -Identity service:Registrar:atl-cs-001.litwareinc.com과 유사한 구문을 사용합니다. 등록자 설정은 등록자 서비스에만 적용할 수 있습니다. 다른 서비스에 이러한 설정을 적용하려고 하면 오류 메시지가 발생합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>등록자 설정 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxEndpointExpiration</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>끝점이 로그온하면 만료 시간 제한을 요청할 수 있습니다. 이는 끝점이 서버에 연결하여 연장을 요청하기 전까지 시스템에 로그온 상태로 있을 수 있는 시간 간격을 지정합니다. MaxEndpointExpiration 속성은 클라이언트에게 부여할 수 있는 최대 시간을 나타냅니다. 예를 들어 최대 시간이 600초로 설정되어 있고 클라이언트가 800초의 시간 제한 간격을 요청하는 경우 클라이언트에게 부여되는 최대 허용 만료 기간은 600초입니다.</p>
<p>MaxEndpointExpiration은 300(5분)-900(15분) 사이여야 합니다. 기본값은 900입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxEndpointsPerUser</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>사용자가 시스템에 동시에 연결할 수 있는 최대 끝점 수를 지정합니다. 예를 들어 컴퓨터와 휴대폰을 동시에 사용하여 Lync Server에 로그온한 사용자는 2개의 끝점을 사용하는 것입니다. MaxEndPointsPerUser는 1에서 64(포함) 사이의 값으로 설정해야 합니다. 기본값은 8입니다.</p>
<p>사용자에게 끝점을 64개까지 허용할 수는 있지만 최대 끝점 수가 8을 초과하지 않는 것이 좋습니다. 9 이상의 값은 드물지만 Microsoft 지원 담당자가 제안한 경우 이전 버전과의 호환성을 위해 사용됩니다. 새 배포의 경우 최대 끝점 수가 8을 초과해서는 안됩니다.</p>
<p>최대 끝점 수는 개별 사용자에게 여러 클라이언트에서 로그인을 제공하기 위한 것입니다. 따라서 이 설정은 전체 부서와 같은 사용자 그룹이 아닌 개별 사용자를 위해 만들어졌습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxUserCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt64</p></td>
<td><p>등록자에 동시에 로그온할 수 있는 최대 사용자 수를 나타냅니다. MaxUserCount는 2000에서 100000(포함) 사이의 정수 값으로 설정할 수 있습니다. 기본값은 12000입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MinEndpointExpiration</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>끝점이 로그온하면 만료 시간 제한을 요청할 수 있습니다. 이는 끝점이 서버에 연결하여 연장을 요청하기 전까지 시스템에 로그온 상태로 있을 수 있는 시간 간격을 지정합니다. MinEndpointExpiration 속성은 클라이언트에게 부여할 수 있는 최소 시간을 나타냅니다. 예를 들어 최소 시간이 600초로 설정되어 있고 클라이언트가 200초의 시간 제한 간격을 요청하는 경우 클라이언트에게 부여되는 최소 허용 만료 기간은 600초입니다.</p>
<p>MinEndpointExpiration은 300(5분)-900(15분) 사이여야 합니다. 기본값은 300입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PoolState</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Registrar.PoolState</p></td>
<td><p>등록자 풀의 현재 상태입니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Active</p>
<p>* FailedOver</p>
<p>* FailingOver</p>
<p>* FailedBack</p>
<p>기본값은 Active입니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Registrar.RegistrarSettings 개체입니다. **Set-CsRegistrarConfiguration** cmdlet은 등록자 설정 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsRegistrarConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Registrar.RegistrarSettings 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsRegistrarConfiguration](get-csregistrarconfiguration.md)  
[New-CsRegistrarConfiguration](new-csregistrarconfiguration.md)  
[Remove-CsRegistrarConfiguration](remove-csregistrarconfiguration.md)

