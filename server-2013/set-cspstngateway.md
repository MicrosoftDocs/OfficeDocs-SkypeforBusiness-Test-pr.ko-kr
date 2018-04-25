---
title: Set-CsPstnGateway
TOCTitle: Set-CsPstnGateway
ms:assetid: 5d61e7e5-dacb-4dd3-bdd5-b757d98181d3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398408(v=OCS.15)
ms:contentKeyID: 49303769
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsPstnGateway

 

_**마지막으로 수정된 항목:** 2015-03-09_

PSTN(공중 전화망) 게이트웨이 속성을 수정합니다. PSTN 게이트웨이를 통해 외부 PSTN 네트워크의 장치와 내부 Enterprise Voice 네트워크의 장치 사이에 통화의 경로를 지정할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsPstnGateway [-Identity <XdsGlobalRelativeIdentity>] [-AlternateByPassId <String>] [-Confirm [<SwitchParameter>]] [-Default <$true | $false>] [-Force <SwitchParameter>] [-GatewaySipClientTcpPort <UInt16>] [-GatewaySipClientTlsPort <UInt16>] [-MediationServer <String>] [-RepresentativeMediaIP <String>] [-Routable <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 게이트웨이 PstnGateway:192.168.0.240을 기본 게이트웨이로 구성합니다. 이는 PstnGateway:192.168.0.240을 사용하여 Office Communications Server 2007 R2에서 전송된 통화를 처리할 수 있음을 의미합니다.

    Set-CsPstnGateway -Identity "PstnGateway:192.168.0.240" -Default $True

## 예제 2

예제 2에서는 조직의 모든 PSTN 게이트웨이를 구성하여 이러한 각 게이트웨이를 아웃바운드 경로 지정에서 사용할 수 있는지 확인합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsService** cmdlet 및 PstnGateway 매개 변수를 사용하여 현재 사용 중인 모든 PSTN 게이트웨이의 컬렉션을 반환합니다. 이 컬렉션은 **ForEach-Object** cmdlet에 파이프됩니다. **ForEach-Object** cmdlet은 컬렉션의 각 게이트웨이에 대해 **Set-CsPstnGateway** cmdlet을 실행하여 각 게이트웨이의 Routable 속성을 True로 설정합니다.

    Get-CsService -PstnGateway | ForEach-Object {Set-CsPstnGateway -Identity $_.Identity -Routable $True}

## 자세한 정보

PSTN 게이트웨이를 사용하면 Enterprise Voice 사용자가 PSTN 네트워크의 사용자와 전화를 걸고 받을 수 있습니다. 이러한 게이트웨이는 중재 서버와 PSTN 네트워크 사이의 다리 역할을 합니다.

PSTN 게이트웨이는 일반적으로 시 분할 멀티플렉스 PBX(Public Branch Exchange) 전화 시스템을 사용하는 경우에 필요합니다. 이 경우 Enterprise Voice 통화를 PSTN 네트워크로 경로 지정하려면 PSTN 게이트웨이와 중재 서버를 둘 다 사용해야 합니다. 반면, IP-PBX 시스템을 사용하는 경우에는 PBX와 중재 서버 사이에 직접 SIP 연결을 만들 수 있으므로 PSTN 게이트웨이가 필요하지 않습니다.

PSTN 게이트웨이를 설치 및 구성한 후에는 **Set-CsPstnGateway** cmdlet을 사용하여 게이트웨이를 관리할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsPstnGateway** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsPstnGateway"}

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
<td><p><em>AlternateByPassId</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>대체 우회 ID를 나타내는 GUID(Globally Unique Identifier)입니다. 이 ID는 Lync Server에 의해 자동으로 생성되며 헤어핀 통화를 제거하는 데 사용됩니다. 시스템 구성 방식에 따라 개별 서브넷을 정의하고 모든 사이트 및 영역과 연결하지 않고도 헤어핀 통화가 중재 서버를 자동으로 건너뛰도록 허용할 수도 있습니다.</p>
<p>이렇게 하려면 일반적으로 우회에서 네트워크 구성 사이트 및 영역을 사용하도록 전역적으로 설정한 다음 PSTN 게이트웨이의 트렁크 구성에서 우회를 활성화해야 합니다.</p>
<p>헤어핀 통화는 PSTN 네트워크의 인바운드 통화가 착신 전환이나 동시 울림을 통해 해당 네트워크로 다시 경로 지정될 때 발생합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Default</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 이 게이트웨이가 Office Communications Server 2007 R2에서 전송된 통화를 처리합니다. 단일 중재 서버에서 관리되는 게이트웨이 컬렉션에는 하나의 기본 게이트웨이만 있을 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>cmdlet을 실행할 때 나타날 수 있는 확인 프롬프트 또는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>GatewaySipClientTcpPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>TCP(Transmission Control Protocol)를 사용하여 중재 서버와 통신하는 데 사용되는 수신 포트입니다. 기본값은 5066입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>GatewaySipClientTlsPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>TLS(전송 계층 보안) 프로토콜을 사용하여 중재 서버와 통신하는 데 사용되는 수신 포트입니다. 기본값은 5067입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>수정할 PSTN 게이트웨이의 서비스 ID입니다(예: -Identity &quot;PstnGateway:192.168.0.240&quot;).</p>
<p>PSTN 게이트웨이를 지정할 때 접두사 &quot;PstnGatewayServer:&quot;를 생략할 수 있습니다(예: -Identity &quot;atl-cs-001.litwareinc.com&quot;).</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>MediationServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>PSTN 게이트웨이와 연결할 중재 서버의 서비스 ID입니다. 예: -MediationServer &quot;MediationServer:atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>RepresentativeMediaIP</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>게이트웨이와 연결된 미디어 프로세서의 IP 주소입니다(프로세서 위치가 신호 처리 주소와 다른 경우). 미디어 우회와 CAC(통화 허용 제어)는 둘 다 게이트웨이의 미디어 프로세서 위치를 기반으로 합니다. 기본적으로 이 위치는 신호 처리 주소와 같습니다. 두 위치가 다른 경우, 예를 들어 미디어 프로세서는 원격 사이트에 있고 신호 처리 피어는 중앙 사이트에 있는 경우 미디어 프로세서의 IP 주소를 사용하여 RepresentativeMediaIP를 구성해야 합니다.</p>
<p>같은 사이트에 각각 고유의 IP 주소를 가진 여러 미디어 프로세서를 배포한 경우에는 이러한 IP 주소를 사용하여 RepresentativeMediaIP 속성을 구성할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Routable</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 게이트웨이가 아웃바운드 경로 지정 경로에서 사용될 수 있습니다.</p></td>
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

없음. **Get-CsPstnGateway** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Set-CsPstnGateway** cmdlet은 값이나 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.Xds.DisplayPstnGateway 개체의 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsService](get-csservice.md)

