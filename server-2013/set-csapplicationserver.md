---
title: Set-CsApplicationServer
TOCTitle: Set-CsApplicationServer
ms:assetid: 74b3f941-df06-4fde-9487-eba081233723
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398562(v=OCS.15)
ms:contentKeyID: 49304062
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsApplicationServer

 

_**마지막으로 수정된 항목:** 2015-03-09_

응용 프로그램 서비스를 실행하는 하나 이상의 서버에 대한 구성 속성을 수정할 수 있습니다. 이러한 서버(응용 프로그램 서버라고도 함)는 통화 대기 응용 프로그램과 같이 Microsoft Unified Communications Managed API(UCMA) 집합을 사용하여 개발된 소프트웨어 프로그램을 호스트합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsApplicationServer [-Identity <XdsGlobalRelativeIdentity>] [-ApplicationDatabase <String>] [-AppSharingPortCount <UInt16>] [-AppSharingPortStart <UInt16>] [-AtsSipPort <UInt16>] [-AudioPortCount <UInt16>] [-AudioPortStart <UInt16>] [-CaaSipPort <UInt16>] [-CasSipPort <UInt16>] [-Confirm [<SwitchParameter>]] [-CpsSipPort <UInt16>] [-Force <SwitchParameter>] [-PdpSipPort <UInt16>] [-PdpTurnPort <UInt16>] [-Registrar <String>] [-RgsSipPort <UInt16>] [-RgsWcfMtlsPort <UInt16>] [-VideoPortCount <UInt16>] [-VideoPortStart <UInt16>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 응용 프로그램 서버 ApplicationServer:atl-cs-001.litwareinc.com의 회의 알림 응용 프로그램에 대한 SIP 포트를 5074로 구성합니다.

    Set-CsApplicationServer -Identity "ApplicationServer:atl-cs-001.litwareinc.com" -CasSipPort 5074 

## 예제 2

예제 2에서는 응용 프로그램 서버 ApplicationServer:atl-cs-001.litwareinc.com에 대한 오디오 포트를 구성합니다. 이 예제에서는 시작 오디오 포트를 49500으로 설정하고 오디오 트래픽용으로 총 5500개 포트를 별도로 설정합니다.

    Set-CsApplicationServer -Identity "ApplicationServer:atl-cs-001.litwareinc.com" -AudioPortStart 49500 -AudioPortCount 5500 

## 예제 3

예제 3에서는 회의 알림 응용 프로그램의 SIP 포트를 조직의 모든 응용 프로그램 서버에 대해 5074로 설정합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsService** cmdlet을 사용하여 현재 사용되고 있는 모든 응용 프로그램 서버의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 서버를 가져온 다음 **Set-CsApplicationServer** cmdlet을 사용하여 회의 알림 응용 프로그램 SIP 포트를 5074로 설정하는 **ForEach-Object** cmdlet에 파이프됩니다.

    Get-CsService -ApplicationServer | ForEach-Object {Set-CsApplicationServer -Identity $_.Identity -CasSipPort 5074} 

## 자세한 정보

응용 프로그램 서비스는 핵심 서버 구성 요소의 일부가 아닌 몇 가지 Lync Server 프로그램을 호스트합니다. 이러한 프로그램에는 응답 그룹 응용 프로그램, 회의 길잡이 응용 프로그램, 회의 알림 응용 프로그램 등이 있습니다. 응용 프로그램 서비스는 이러한 프로그램을 Lync Server 환경에 완전히 통합합니다.

**Set-CsApplicationServer** cmdlet을 사용하여 관리자는 조직에 배포된 임의의 또는 모든 응용 프로그램 서버에 대한 구성 설정을 수정할 수 있습니다. 예를 들어 오디오, 비디오 또는 응용 프로그램 공유 트래픽에 사용되는 포트를 수정하거나 회의 길잡이 응용 프로그램 또는 회의 알림 응용 프로그램과 같은 개별 응용 프로그램에서 사용되는 포트에 새 값을 할당할 수 있습니다. 포트를 변경할 때마다 해당 서비스를 다시 시작해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsApplicationServer** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsApplicationServer"}

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
<td><p><em>ApplicationDatabase</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>응용 프로그램 데이터베이스의 서비스 위치입니다(예: -ApplicationDatabase &quot;ApplicationDatabase:atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>AppSharingPortCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>응용 프로그램 공유를 위해 할당된 전체 포트 수입니다. 포트는 AppSharingPortStart에 구성된 값부터 시작하여 AppSharingPortCount에 지정된 포트 수만큼 열립니다. 예를 들어 AppSharingPortStart가 60000으로 설정되고 AppSharingPortCount가 100으로 설정된 경우 포트 60000부터 60099까지 응용 프로그램 공유에 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AppSharingPortStart</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>응용 프로그램 공유를 위해 할당된 포트 범위의 첫 번째 포트입니다(예: –AppSharingPortStart 60000).</p></td>
</tr>
<tr class="even">
<td><p><em>AtsSipPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>오디오 테스트 서비스에 사용되는 포트입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AudioPortCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>오디오 트래픽을 보내고 받는 데 할당된 총 포트 수입니다. 열려는 실제 포트는 AudioPortStart에 대해 구성된 값으로 시작하고 AudioPortCount에 대해 지정된 포트 수까지 계속됩니다. 예를 들어 AudioPortStart가 60000으로 설정되고 AudioPortCount가 100으로 설정된 경우 포트 60000부터 60099까지 오디오 트래픽에 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioPortStart</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>오디오 트래픽을 보내고 받는 데 할당된 포트 범위의 첫 번째 포트입니다(예: –AudioPortStart 60000).</p></td>
</tr>
<tr class="odd">
<td><p><em>CaaSipPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>회의 길잡이 응용 프로그램에서 사용자를 전화 접속 회의에 연결할 때 사용하는 SIP 포트입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CasSipPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>회의 알림 응용 프로그램에서 전화 회의 중에 알림(예: &quot;Ken Myer가 지금 퇴장합니다.&quot;)을 재생하는 데 사용하는 SIP 포트입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CpsSipPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>통화 대기 서비스에서 사용하는 SIP 포트입니다. 통화 대기 서비스를 사용하면 한 전화에서 통화를 보류 중으로 전환한 다음 다른 전화에서 해당 통화가 검색되도록 할 수 있습니다.</p></td>
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
<td><p>수정할 응용 프로그램 서버의 서비스 위치입니다(예: -Identity &quot;ApplicationServer:atl-cs-001.litwareinc.com&quot;).</p>
<p>접두사 &quot;ApplicationServer:&quot;는 응용 프로그램 서버를 지정할 때 생략할 수 있습니다(예: -Identity &quot;atl-cs-001.litwareinc.com&quot;).</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>PdpSipPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>정책 결정 지점 서버에서 사용하는 SIP 포트입니다. 정책 결정 지점 서버는 대역폭 관리에 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PdpTurnPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>정책 결정 지점 서버에서 사용하는 Turn 트래픽 포트입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Registrar</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>정책 결정 지점 Server와 연결된 등록자의 정규화된 도메인 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>RgsSipPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>응답 그룹 응용 프로그램에서 사용하는 SIP 포트입니다. 응답 그룹 응용 프로그램을 사용하면 수신 전화 통화를 조직의 지원 팀과 같은 특정 사용자 그룹으로 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RgsWcfMtlsPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>응답 그룹 응용 프로그램에서 사용하는 WCF(Windows Communication Foundation) MTLS(Mutual TLS) 트래픽에 사용되는 포트입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>VideoPortCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>비디오 트래픽을 보내고 받는 데 할당된 포트의 총 수입니다. 포트는 VideoPortStart에 구성된 값부터 시작하여 VideoPortCount에 지정된 포트 수만큼 열립니다. 예를 들어 VideoPortStart가 60000으로 설정되고 VideoPortCount가 100으로 설정된 경우 포트 60000부터 60099까지 비디오 트래픽에 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>VideoPortStart</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>비디오 트래픽을 보내고 받는 데 할당된 포트 범위의 첫 번째 포트입니다(예: -VideoPortStart 60000).</p></td>
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

없음. **Set-CsApplicationServer** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Set-CsApplicationServer** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.Xds.DisplayAplicationServer 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsServerApplication](get-csserverapplication.md)

