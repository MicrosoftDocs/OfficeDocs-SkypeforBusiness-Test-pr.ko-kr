---
title: Set-CsMediationServer
TOCTitle: Set-CsMediationServer
ms:assetid: 13efdd9d-ba26-4c93-b0b9-b6e4739bb630
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398213(v=OCS.15)
ms:contentKeyID: 49302888
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsMediationServer

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 중재 서버에 대한 속성을 수정할 수 있습니다. 중재 서버는 내부 Enterprise Voice 인프라와 PSTN(공중 전화망) 게이트웨이 또는 SIP 직통 전화 간에 트래픽을 경로 지정하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsMediationServer [-Identity <XdsGlobalRelativeIdentity>] [-AudioPortCount <UInt16>] [-AudioPortStart <UInt16>] [-Confirm [<SwitchParameter>]] [-EdgeServer <String>] [-Force <SwitchParameter>] [-Registrar <String>] [-SipClientTcpPort <UInt16>] [-SipClientTlsPort <UInt16>] [-SipServerPort <UInt16>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 중재 서버 MediationServer:atl-cs-001.litwareinc.com에 대해 SIP 게이트웨이 TCP 수신 포트를 5072로 설정합니다. 포트를 변경한 후에는 Lync Server 중재 서비스를 다시 시작해야 합니다.

    Set-CsMediationServer -Identity "MediationServer:atl-cs-001.litwareinc.com" -SipClientTcpPort 5072

## 예제 2

예제 2에서는 중재 서버 MediationServer:atl-cs-001.litwareinc.com의 오디오 포트 설정을 구성합니다. 이 예제에서 시작 오디오 포트는 60000으로 설정되고 오디오에 할당되는 총 포트 수는 1000개입니다.

    Set-CsMediationServer -Identity "MediationServer:atl-cs-001.litwareinc.com" -AudioPortStart 60000 -AudioPortCount 1000

## 자세한 정보

중재 서버는 내부 Enterprise Voice 구성과 PSTN 게이트웨이, IP-PBX 또는 SIP 직통 전화 사이의 브리지 역할을 하므로 VoIP(Voice over Internet Protocol) 장치를 사용하는 Enterprise Voice 사용자가 표준 유선 전화나 휴대폰을 사용하는 사람과 통신할 수 있습니다. **Set-CsMediationServer** cmdlet을 사용하면 기존 중재 서버를 변경할 수 있습니다. 특히 클라이언트 장치, 프런트 엔드 서버 및 게이트웨이 피어와 통신하는 데 사용되는 포트를 수정할 수 있습니다. 필요한 경우 **Set-CsMediationServer** cmdlet을 사용하여 중재 서버를 새 등록자나 새 에지 서버와 연결할 수도 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsMediationServer** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsMediationServer"}

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
<td><p><em>AudioPortCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>오디오 트래픽을 보내고 받는 데 할당된 총 포트 수입니다. 열려는 실제 포트는 AudioPortStart에 대해 구성된 값으로 시작하고 AudioPortCount에 대해 지정된 포트 수까지 계속됩니다. 예를 들어 AudioPortStart가 60000으로 설정되고 AudioPortCount가 100으로 설정된 경우 포트 60000부터 60099까지 오디오 트래픽에 사용됩니다.</p>
<p>적어도 다음 7개의 미디어 포트가 단일 오디오 통화를 릴레이하는 데 필요합니다.</p>
<p>게이트웨이 포트 두 개 - 하나는 RTP(Real-Time Transport Protocol) 트래픽에 사용되고 나머지 하나는 RTCP(Real-time Transmission Control Protocol) 트래픽에 사용됩니다.</p>
<p>UDP(User Datagram Protocol) 릴레이 포트 두 개 - 하나는 RTP 트래픽용이고, 나머지 하나는 RTCP 트래픽용입니다.</p>
<p>TCP(Transmission Control Protocol) 릴레이 포트 한 개 - TCP 릴레이 포트 하나로 RTP 트래픽과 RTCP 트래픽을 둘 다 처리할 수 있습니다.</p>
<p>네트워크 인터페이스당 로컬 포트 두 개 - 하나는 RTP 트래픽용이고, 나머지 하나는 RTCP 트래픽용입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioPortStart</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>오디오 트래픽을 보내고 받는 데 할당된 포트 범위의 첫 번째 포트입니다(예: –AudioPortStart 60000).</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EdgeServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>중재 서버와 연결할 에지 서버의 서비스 ID입니다(예: -EdgeServer &quot;EdgeServer:atl-edge-001.litwareinc.com&quot;).</p></td>
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
<td><p>수정할 중재 서버의 서비스 위치입니다(예: -Identity &quot;MediationServer:atl-cs-001.litwareinc.com&quot;).</p>
<p>접두사 &quot;MediationServer:&quot;는 중재 서버를 지정할 때 생략할 수 있습니다 (예: -Identity &quot;atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>Registrar</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>중재 서버와 연결할 등록자의 서비스 위치입니다(예: -Registrar &quot;Registrar:atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>SipClientTcpPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>TCP를 사용하여 게이트웨이 피어와 통신하는 데 사용되는 수신 포트입니다. TCP 포트는 기본적으로 정의되지 않습니다. 그러나 PSTN 게이트웨이를 만들면 포트 번호가 5068인 TCP 포트가 자동으로 생성됩니다. SipClientTcpPort를 변경한 경우 새 포트를 실제로 사용하려면 중재 서버 서비스를 다시 시작해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipClientTlsPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>TLS(전송 계층 보안)를 사용하여 게이트웨이 피어와 통신하는 데 사용되는 수신 포트입니다. 기본적으로 SipClientTlsPort는 포트 5067을 사용하도록 구성됩니다. SipClientTlsPort를 변경한 경우 새 포트를 실제로 사용하려면 중재 서버 서비스를 다시 시작해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SipServerPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>프런트 엔드 서버와 통신하는 데 사용되는 수신 포트입니다. 기본적으로 SipServerPort는 포트 5070을 사용하도록 구성됩니다. SipClientTlsPort를 변경한 경우 새 포트를 실제로 사용하려면 중재 서버 서비스를 다시 시작해야 합니다.</p></td>
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

없음. **Set-CsMediationServer** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Set-CsMediationServer** cmdlet은 개체나 값을 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.Xds.DisplayMediationServer 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsService](get-csservice.md)

