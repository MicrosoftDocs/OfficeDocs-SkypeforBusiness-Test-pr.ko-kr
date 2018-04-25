---
title: Set-CsDirector
TOCTitle: Set-CsDirector
ms:assetid: 74eb6f17-812f-47df-84ee-fa6e42990f2e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398565(v=OCS.15)
ms:contentKeyID: 49304065
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsDirector

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 디렉터 속성을 수정합니다. 사용자 요청을 인증하기 위해 디렉터를 사용할 수 있지만, 디렉터는 사용자 계정을 호스트하지 않습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsDirector [-Identity <XdsGlobalRelativeIdentity>] [-ArchivingServer <String>] [-Confirm [<SwitchParameter>]] [-EdgeServer <String>] [-Force <SwitchParameter>] [-MirrorMonitoringDatabase <String>] [-MonitoringDatabase <String>] [-MonitoringServer <String>] [-SipHealthPort <UInt16>] [-SipPort <UInt16>] [-SipServerTcpPort <UInt16>] [-WebPort <UInt16>] [-WebServer <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 디렉터 Director:atl-cs-001.litwareinc.com과 연결된 보관 서버를 변경합니다. 이 예제에서는 보관 서버를 ArchivingServer:dublin-cs-001.litwareinc.com으로 전환합니다.

    Set-CsDirector -Identity "Director:atl-cs-001.litwareinc.com" -ArchivingServer "ArchivingServer:dublin-cs-001.litwareinc.com"

## 예제 2

예제 2에서는 조직에서 현재 사용되고 있는 모든 디렉터의 SIP 포트를 변경합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsService** cmdlet 및 Director 매개 변수를 사용하여 조직에 있는 모든 디렉터의 컬렉션을 반환합니다. 이 컬렉션은 **ForEach-Object** cmdlet에 파이프됩니다. **ForEach-Object** cmdlet은 컬렉션의 각 사이트에 대해 **Set-CsDirector** cmdlet을 실행하여 SipPort 속성 값을 5072로 변경합니다.

    Get-CsService -Director | ForEach-Object {Set-CsDirector -Identity $_.Identity -SipPort 5072}

## 자세한 정보

디렉터는 사용자 계정을 실제로 호스트하지 않으면서 사용자를 인증하고 사용자 요청에 응답합니다. 일반적으로 디렉터는 에지 서버를 통해 네트워크에 대한 외부 액세스를 허용하는 조직에 사용됩니다. 이 시나리오에서 디렉터는 인증 요청을 처리하여 프런트 엔드 서버에 대한 긴장을 완화할 뿐만 아니라 서비스 거부 공격과 다른 악의적인 트래픽으로부터 내부 네트워크를 보호할 수 있습니다. 디렉터는 여러 프런트 엔드 서버가 중앙 사이트에 배포된 경우에도 유용합니다. 이 경우 디렉터는 모든 사용자 요청을 수신한 다음 해당 요청을 적절한 서버 풀로 보냅니다. 이 작업을 통해 프런트 엔드 서버에 대한 부담이 완화될 수 있습니다.

**Set-CsDirector** cmdlet을 사용하면 조직에서 현재 사용되고 있는 디렉터의 속성 값을 수정할 수 있습니다. 이 작업에는 디렉터와 연결된 보관 서버 또는 에지 서버 등의 변경이나 SIP 트래픽을 보내고 받는 데 사용되는 포트 변경이 포함됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsDirector** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsDirector"}

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
<td><p><em>ArchivingServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>디렉터와 연결할 보관 서버의 서비스 위치입니다(예: -ArchivingServer &quot;ArchivingServer:atl-cs-001.litwareinc.com&quot;).</p></td>
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
<td><p>디렉터와 연결할 에지 서버의 서비스 위치입니다(예: -EdgeServer &quot;EdgeServer:atl-edge-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>수정할 디렉터의 서비스 위치입니다(예: -Identity &quot;Director:atl-cs-001.litwareinc.com&quot;).</p>
<p>디렉터를 지정할 때 접두사 &quot;Director:&quot;를 생략할 수 있습니다(예: -Identity &quot;atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>MirrorMonitoringDatabase</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>디렉터와 연결할 미러 모니터링 데이터베이스의 서비스 위치입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MonitoringDatabase</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>디렉터와 연결할 모니터링 데이터베이스의 서비스 위치입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MonitoringServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>디렉터와 연결할 모니터링 서버의 서비스 위치입니다(예: -MonitoringServer &quot;MonitoringServer:atl-cs-001.litwareinc.com&quot;).</p></td>
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
<td><p><em>WebPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>웹 서비스와 통신하는 데 사용되는 포트입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WebServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>디렉터와 연결할 서버의 웹 서비스 위치입니다(예: -WebServer &quot;WebServer:atl-cs-001.litwareinc.com&quot;).</p></td>
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

없음. **Set-CsDirector** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Set-CsDirector** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.Xds.DisplayDirector 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsService](get-csservice.md)

