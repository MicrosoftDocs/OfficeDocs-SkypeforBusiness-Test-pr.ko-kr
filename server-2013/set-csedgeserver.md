---
title: Set-CsEdgeServer
TOCTitle: Set-CsEdgeServer
ms:assetid: cbe140a4-8ce6-4e20-913b-b1ffb58e6698
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398859(v=OCS.15)
ms:contentKeyID: 49305050
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsEdgeServer

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 에지 서버에 대한 속성 값을 수정합니다. 에지 서버는 내부 네트워크와 인터넷 간의 연결을 제공하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsEdgeServer [-Identity <XdsGlobalRelativeIdentity>] [-AccessEdgeClientSipPort <UInt16>] [-AccessEdgeExternalSipPort <UInt16>] [-AccessEdgeInternalSipPort <UInt16>] [-Confirm [<SwitchParameter>]] [-DataPsomClientPort <UInt16>] [-DataPsomServerPort <UInt16>] [-Force <SwitchParameter>] [-MediaCommunicationPortCount <UInt16>] [-MediaCommunicationPortStart <UInt16>] [-MediaRelayAuthEdgePort <UInt16>] [-MediaRelayExternalTurnTcpPort <UInt16>] [-MediaRelayExternalTurnUdpPort <UInt16>] [-MediaRelayInternalTurnTcpPort <UInt16>] [-MediaRelayInternalTurnUdpPort <UInt16>] [-Registrar <String>] [-WhatIf [<SwitchParameter>]] [-XmppInternalPort <UInt16>] [-XmppListeningPort <UInt16>]

## 예제

## 예제 1

예제 1에 표시된 명령은 에지 서버 "EdgeServer:atl-edge-001.litwareinc.com"의 내부 및 외부 SIP 포트를 수정합니다.

    Set-CsEdgeServer -Identity "EdgeServer:atl-edge-001.litwareinc.com" -AccessEdgeInternalSipPort 5062 -AccessEdgeExternalSipPort 5062

## 예제 2

예제 2에서는 Redmond 사이트에 있는 모든 에지 서버의 내부 및 외부 SIP 포트를 수정합니다. 이 작업을 수행하기 위해 명령은 먼저**Get-CsService** cmdlet 및 EdgeServer 매개 변수를 사용하여 조직에서 현재 사용 중인 모든 에지 서버 컬렉션을 반환합니다. 이 컬렉션은 Redmond 사이트에서 SiteId 속성이 site:Redmond와 같은 에지 서버만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이 필터링된 컬렉션은 **For-Each-Object** cmdlet에 파이프됩니다. 이 cmdlet은 해당 컬렉션의 각 서버에 대해 **Set-CsEdgeServer** cmdlet을 실행하여 AccessInternalSipPort 및 AccessExternalSipPort 속성에 할당된 값을 변경합니다.

    Get-CsService -EdgeServer | Where-Object {$_.SiteId -eq "site:Redmond"} | ForEach-Object {Set-CsEdgeServer -Identity $_.Identity -AccessEdgeInternalSipPort 5062 -AccessEdgeExternalSipPort 5062}

## 자세한 정보

외부, 즉 인터넷과의 연결은 Lync Server에서 중요한 부분입니다. 인터넷에 연결되지 않은 경우 사용자는 내부 네트워크에 로그온하여 Lync Server에 액세스해야 합니다. 그러면 외부에서 근무하는 사용자가 소프트웨어를 사용하기가 어렵고 해당 도메인에 계정이 없는 사용자가 전화 회의에 참여할 수 없게 됩니다. 마찬가지로, 조직 외부와 연결되지 않으면 사용자가 페더레이션 파트너 또는 Yahoo\!, AOL 또는 MSN과 같은 공용 메신저 시스템의 계정을 가진 사람들과 메신저 대화를 교환할 수 없습니다.

에지 서버는 내부 네트워크와 인터넷 간의 연결을 제공하는 데 사용됩니다. **Set-CsEdgeServer** cmdlet을 사용하여 에지 서버의 구성 설정을 수정할 수 있습니다. 이 작업에는 주로 네트워크 트래픽을 전송하는 데 사용되는 포트 번호 변경이 포함됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsEdgeServer** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsEdgeServer"}

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
<td><p><em>AccessEdgeClientSipPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>에지 서버와 클라이언트 장치 간 SIP 통신에 사용되는 포트입니다. 초기 값은 토폴로지 작성기에서 설정되지만 이 매개 변수에 대해 새 값을 지정하여 변경할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AccessEdgeExternalSipPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>외부 SIP 트래픽에 사용되는 포트입니다. 기본값은 5061입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AccessEdgeInternalSipPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>내부 SIP 트래픽에 사용되는 포트입니다. 기본값은 5061입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DataPsomClientPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>에지 서버와 클라이언트 장치 간 PSOM(영구적 공유 개체 모델) 통신에 사용되는 포트입니다. 초기 값은 토폴로지 작성기에서 설정되지만 이 매개 변수에 대해 새 값을 지정하여 변경할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DataPsomServerPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>에지 서버와 기타 서버 간 PSOM 통신에 사용되는 포트입니다.</p></td>
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
<td><p>수정할 에지 서버의 서비스 위치입니다(예: -Identity &quot;EdgeServer:atl-edge-001.litwareinc.com&quot;).</p>
<p>이제 에지 서버를 지정할 때 접두사 &quot;EdgeServer:&quot;를 사용하지 않아도 됩니다 (예: -Identity &quot;atl-cs-001.litwareinc.com&quot;).</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>MediaCommunicationPortCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>미디어 통신에 대해 외부 에지에 할당된 총 포트 수입니다. 기본값은 10000입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MediaCommunicationPortStart</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>외부 에지에서 미디어 통신에 대한 시작 포트 번호입니다. 기본값은 50000입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MediaRelayAuthEdgePort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>미디어 릴레이 인증에 사용되는 포트입니다. 기본값은 5062입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MediaRelayExternalTurnTcpPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>TCP(Transmission Control Protocol)를 사용한 내부 미디어 릴레이 트래픽에 사용되는 포트로, 에지 서버에 IP 주소가 하나인 경우 기본값은 444입니다. 에지 서버에 IP 주소가 여러 개인 경우에는 기본값이 443입니다. 이러한 값은 토폴로지 작성기에서 초기에 설정되지만 이 매개 변수에 대해 새 값을 지정하여 변경할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MediaRelayExternalTurnUdpPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>UDP(User Datagram Protocol)를 사용한 외부 미디어 릴레이 트래픽에 사용되는 포트입니다. 기본값은 3478입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MediaRelayInternalTurnTcpPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>TCP를 사용한 내부 미디어 릴레이 트래픽에 사용되는 포트입니다. 기본값은 443입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MediaRelayInternalTurnUdpPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>UDP를 사용한 내부 미디어 릴레이 트래픽에 사용되는 포트입니다. 기본값은 3478입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Registrar</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>에지 서버와 연결할 등록자의 서비스 위치입니다. (예: -Registrar &quot;Registrar:atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>XmppInternalPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>내부 XMPP 트래픽에 사용되는 포트입니다. XMPP(Extensible Messaging and Presence Protocol)는 XML을 사용하여 메시지를 교환하기 위한 개방형 표준 통신 프로토콜입니다. 허용 파트너는 해당 사용자가 Lync Server 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있는 메신저 및 현재 상태 공급자입니다. 기본값은 5098입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>XmppListeningPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>XMPP 트래픽용 수신 대기 포트입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Set-CsEdgeServer** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Set-CsEdgeServer** cmdlet은 개체나 값을 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.Xds.DisplayEdgeServer 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsService](get-csservice.md)

