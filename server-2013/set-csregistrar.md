---
title: Set-CsRegistrar
TOCTitle: Set-CsRegistrar
ms:assetid: e0c31acc-179c-4423-910e-8bd7807e6489
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398993(v=OCS.15)
ms:contentKeyID: 49305295
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsRegistrar

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 등록자에 대한 속성을 수정하는 데 사용됩니다. 등록자는 로그온 요청을 인증하고 사용자 상태에 대한 정보를 유지 관리하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsRegistrar [-Identity <XdsGlobalRelativeIdentity>] [-ArchivingDatabase <String>] [-ArchivingServer <String>] [-BackupRegistrar <String>] [-Confirm [<SwitchParameter>]] [-EdgeServer <String>] [-EnableAutomaticFailover <$true | $false>] [-FailbackDetectionInterval <TimeSpan>] [-FailureDetectionInterval <TimeSpan>] [-Force <SwitchParameter>] [-LyssWcfMtlsPort <UInt16>] [-MirrorArchivingDatabase <String>] [-MirrorMonitoringDatabase <String>] [-MonitoringDatabase <String>] [-MonitoringServer <String>] [-Registrar <String>] [-SipHealthPort <UInt16>] [-SipPort <UInt16>] [-SipServerTcpPort <UInt16>] [-UserServer <String>] [-WebPort <UInt16>] [-WebServer <String>] [-WhatIf [<SwitchParameter>]] [-WinFabClientConnectionPort <UInt16>] [-WinFabFederationPort <UInt16>] [-WinFabIPCPort <UInt16>] [-WinFabLeaseAgentPort <UInt16>] [-WinFabReplicationPort <UInt16>] [-XmppGatewaySipPort <UInt16>]

## 예제

## 예제 1

예제 1에 표시된 명령은 Registrar:atl-cs-001.litwareinc.com 등록자의 SIP 포트를 5072로 설정합니다.

    Set-CsRegistrar -Identity "Registrar:atl-cs-001.litwareinc.com" -SipPort 5072

## 예제 2

예제 2에서는 조직에서 사용하는 모든 등록자의 SIP 포트를 5072로 설정합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsService** cmdlet 및 Registrar 매개 변수를 사용하여 현재 사용 중인 모든 등록자 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 등록자를 가져오고 **Set-CsRegistrar** cmdlet을 실행하여 SIP 포트를 5072로 변경하는 **ForEach-Object** cmdlet에 파이프됩니다.

    Get-CsService -Registrar | ForEach-Object {Set-CsRegistrar -Identity $_.Identity -SipPort 5072}

## 예제 3

예제 3에서는 Registrar:atl-cs-001.litwareinc.com 등록자에 대해 백업 등록자(BackupRegistrar)와 자동 장애 조치(failover)(EnableAutomaticFailover)를 둘 다 구성합니다.

    Set-CsRegistrar -Identity "Registrar:atl-cs-001.litwareinc.com" -BackupRegistrar "Registrar:dublin-cs-001.litwareinc.com" -EnableAutomaticFailover $True

## 자세한 정보

등록자는 Lync Server의 가장 중요한 구성 요소라고 할 수 있습니다. 등록자 없이는 사용자가 시스템에 로그온할 수 없으며 Lync Server에서 사용자와 사용자의 현재 상태를 추적할 수 없기 때문입니다. 사용자가 Lync Server에 로그온하면 로그온한 끝점(컴퓨터, 휴대폰 또는 기타 장치)에서 등록 서버에 REGISTER 요청을 보냅니다. 그러면 서버에서 클라이언트 장치에 인증 자격 증명을 요구하여 응답합니다. 클라이언트가 이 요구를 충족하면, 즉 클라이언트에서 유효한 자격 증명 집합을 제공하면 사용자가 인증되고 IP 주소, 포트 및 사용자 이름과 같은 정보가 등록 데이터베이스에 로깅됩니다. 이 정보는 사용자가 로그오프하면 데이터베이스에서 제거됩니다. 로그온한 시점부터 로그오프할 때까지 등록자는 상태 정보를 최신 상태로 유지하면서 사용자가 주고받는 메시지의 경로 지정을 지원합니다.

**Set-CsRegistrar** cmdlet을 사용하면 조직에서 사용하는 하나 이상의 등록자에 대한 속성을 수정할 수 있습니다. 예를 들어 포트 설정을 변경하거나 등록자를 사용할 수 없는 경우 수행해야 하는 작업을 지정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsRegistrar** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsRegistrar\\b"}

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
<td><p><em>ArchivingDatabase</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>보관 서비스에서 사용하는 데이터베이스의 서비스 ID입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ArchivingServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>등록자와 연결할 보관 서버의 서비스 위치입니다(예: -ArchivingServer &quot;ArchivingServer:atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>BackupRegistrar</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>등록자를 사용할 수 없는 경우에 사용할 이 등록자의 서비스 위치입니다(예: -BackupRegistrar &quot;Registrar:dublin-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EdgeServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>등록자와 연결할 에지 서버의 서비스 위치입니다(예: -EdgeServer &quot;EdgeServer:atl-edge-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>EnableAutomaticFailover</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True이면 기본 등록자를 사용할 수 없을 때마다 백업 등록자를 사용하고, False이면 기본 등록자를 사용할 수 없는 경우 백업 등록자를 사용하지 않습니다.</p>
<p>이 매개 변수는 백업 등록자에 등록된 사용자에게도 영향을 줍니다. 이 매개 변수를 True로 설정하면 이러한 사용자는 백업 등록자에서 삭제된 후 기본 등록자를 사용할 수 있을 때 이 등록자에 다시 등록됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>FailbackDetectionInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>이전에 사용할 수 없던 등록자를 현재 사용할 수 있는지 확인하기 전에 시스템이 대기하게 될 시간을 지정합니다. EnableAutomaticFailover를 True로 설정한 경우 등록자를 사용할 수 없게 될 때마다 시스템이 백업 등록자로 장애 조치(failover)됩니다. 따라서 시스템은 실패한 등록자에 로그온된 사용자를 가져가 백업 등록자에 로그온시킵니다.</p>
<p>FailbackDetectionInterval 속성은 시스템이 원래 등록자를 다시 사용할 수 있는지 확인하기 전에 대기하게 될 시간을 지정합니다. 다시 사용할 수 있는 경우 Lync Server가 해당 등록자로 &quot;장애 복구(failback)&quot;를 시도합니다. 장애 복구(failback)는 처음에 사용한 등록자로 다시 전환함을 의미합니다. 즉, 사용자를 다시 원래 등록자에 로그온시킵니다.</p>
<p>Failback(장애 복구)은 자동 프로세스로만 수행됩니다. 한 등록자에서 다른 등록자로 수동으로 Failback(장애 복구)을 수행할 수는 없습니다.</p>
<p>검색 간격은 30초에서 84,400초(24시간) 사이의 임의 값으로 설정할 수 있습니다. 시간 간격을 지정할 때는 시간:분:초 형식을 사용합니다. 예를 들어 - FailbackDetectionInterval 01:15:00은 간격을 1시간 15분으로 설정합니다.</p>
<p>백업 등록자를 지정하지 않은 경우에는 이 매개 변수를 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>FailureDetectionInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>등록자를 사용할 수 없음을 결정하기 전에 시스템에서 대기할 시간 간격을 지정합니다. EnableAutomaticFailover가 True로 설정된 경우 시스템이 백업 등록자에 대해 사용자 로그온을 시도합니다.</p>
<p>검색 간격은 30초에서 84,400초(24시간) 사이의 임의 값으로 설정할 수 있습니다. 시간 간격을 지정할 때는 시간:분:초 형식을 사용합니다. 예를 들어 - FailureDetectionInterval 01:15:00은 간격을 1시간 15분으로 설정합니다.</p>
<p>백업 등록자를 지정하지 않은 경우에는 이 매개 변수를 사용할 수 없습니다.</p></td>
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
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>수정할 등록자의 서비스 위치입니다(예: -Identity &quot;Registrar:atl-cs-001.litwareinc.com&quot;).</p>
<p>이제 등록자를 지정할 때 접두사 &quot;Registrar:&quot;를 남겨 둘 수 있습니다(예: -Identity &quot;atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>LyssWcfMtlsPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>LYSS(Lync 저장소 서비스)에서 사용하는 포트입니다. 기본값은 5077입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MirrorArchivingDatabase</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>보관 서비스에서 사용하는 미러 데이터베이스의 서비스 ID입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MirrorMonitoringDatabase</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>모니터링 서비스에서 사용하는 미러 데이터베이스의 서비스 ID입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MonitoringDatabase</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>등록자와 연결된 모니터링 데이터베이스의 서비스 ID입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MonitoringServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>등록자와 연결할 모니터링 서버의 서비스 위치입니다(예: -MonitoringServer &quot;MonitoringServer:atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Registrar</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>등록자의 서비스 위치입니다</p></td>
</tr>
<tr class="odd">
<td><p><em>SipHealthPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>서버 상태를 모니터링하는 데 사용되는 포트입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SipPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>SIP(Session Initiation Protocol) 트래픽에 사용되는 포트입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipServerTcpPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>SIP 수신 대기 포트입니다. 기본값은 5060입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>등록자와 연결할 사용자 서비스 서버의 서비스 위치입니다(예: -UserServer &quot;UserServer:atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>WebPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>웹 서버와 통신하는 데 사용되는 포트입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WebServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>등록자와 연결할 웹 서버의 서비스 위치입니다(예: -WebServer &quot;WebServer:atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WinFabClientConnectionPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>Windows Fabric에 대한 클라이언트 연결에 사용되는 포트입니다. 기본값은 5092입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WinFabFederationPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>Windows Fabric 페더레이션에 사용되는 포트입니다. 페더레이션이란 Windows Fabric에서 메시지를 라우팅하는 프로세스를 지칭합니다. 기본값은 5090입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WinFabIPCPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>Windows Fabric에서 IPC(프로세스 간 통신)에 사용하는 포트입니다. IPC는 프로세스의 여러 스레드가 데이터를 교환할 수 있도록 하는 기술입니다. 기본값은 5093입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WinFabLeaseAgentPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>Windows Fabric 임대 에이전트가 사용하는 포트입니다. 임대 에이전트는 커널 수준 임대 드라이버와 상호 작용하는 데 사용됩니다. 기본값은 5091입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WinFabReplicationPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>Windows Fabric 복제에 사용되는 포트입니다. Lync Server 2013에서는 Windows Fabric을 사용하여 등록자 풀 내의 모든 프런트 엔드 서버로 전화 회의 디렉터리를 복제합니다. 기본값은 5094입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>XmppGatewaySipPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>등록자와 연결된 XMPP 게이트웨이에서 사용하는 포트입니다. XMPP(Extensible Messaging and Presence Protocol)는 XML을 사용하여 메시지를 교환하기 위한 개방형 표준 통신 프로토콜입니다. 허용 파트너는 해당 사용자가 Lync Server 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있는 메신저 및 현재 상태 공급자입니다. 기본값은 5098입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Set-CsRegistrar** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Set-CsRegistrar** cmdlet은 개체나 값을 반환하지 않습니다. 대신 이 명령은 Microsoft.Rtc.Management.Xds.DisplayRegistrar 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsService](get-csservice.md)

