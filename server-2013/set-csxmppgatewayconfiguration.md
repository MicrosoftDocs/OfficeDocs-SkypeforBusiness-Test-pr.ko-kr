---
title: Set-CsXmppGatewayConfiguration
TOCTitle: Set-CsXmppGatewayConfiguration
ms:assetid: 2b90d563-a3fe-45bd-81da-210a7459411b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204769(v=OCS.15)
ms:contentKeyID: 49303168
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsXmppGatewayConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용 중인 XMPP 게이트웨이 구성 설정을 수정합니다. XMPP(Extensible Messaging and Presence Protocol)는 XML을 사용하여 메시지를 교환하기 위한 개방형 표준 통신 프로토콜입니다. Lync Server 2013 사용자는 XMPP 게이트웨이를 통해 XMPP가 적용된 메신저 및 현재 상태 공급자의 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsXmppGatewayConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsXmppGatewayConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-ConnectionLimit <UInt32>] [-DialbackPassphrase <String>] [-EnableLoggingAllMessageBodies <$true | $false>] [-Force <SwitchParameter>] [-KeepAliveInterval <UInt32>] [-PartnerConnectionLimit <UInt32>] [-StreamEstablishmentTimeout <UInt32>] [-StreamInactivityTimeout <UInt32>] [-SubscriptionRefreshInterval <UInt32>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 XMPP 게이트웨이 설정의 전역 컬렉션에 대한 ConnectionLimit 속성을 수정합니다.

    Set-CsXmppGatewayConfiguration -Identity "global" -ConnectionLimit 1200

## 자세한 정보

XMPP(Extensible Messaging and Presence Protocol)는 인터넷에서 메시지를 보내는 데 사용되는 XML 기반 표준 통신 프로토콜입니다. XMPP(이전 이름은 Jabber)는 Google Talk, Facebook 채팅을 비롯한 여러 인터넷 메시징 및 통신 응용 프로그램에서 지원됩니다.

Lync 2013가 XMPP 네트워크의 사용자와 통신할 수 있도록 하는 XMPP 게이트웨이는 원래 Microsoft Lync Server 2010의 추가 기능으로 공개되었습니다. Lync Server 2013 소프트웨어에서는 이 기능이 기본 제공됩니다. 즉, 다음을 수행하는 경우 사용자가 XMPP 사용자와 통신할 수 있습니다.

  -   
    XMPP 게이트웨이 설정 구성

  -   
    Google Talk 등의 다른 XMPP 네트워크를 허용되는 XMPP 파트너로 구성

Lync Server 2013에서는 XMPP 구성 설정 전역 집합을 하나만 제공하므로 지정된 사이트나 지정된 등록자 풀에 대해 XMPP를 선택적으로 사용하거나 사용하지 않도록 설정할 수는 없습니다. 실제로 XMPP는 사용하거나 사용하지 않도록 설정할 수 없으며 항상 사용하도록 설정됩니다. 사용자가 XMPP 네트워크와 통신하지 못하도록 하려면 허용 XMPP 파트너를 모두 제거해야 합니다. 사용자는 XMPP 네트워크가 허용 파트너로 구성된 경우에만 해당 네트워크와 통신할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsXmppGatewayConfiguration"}

**Lync Server 제어판:** **Set-CsXmppGatewayConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ConnectionLimit</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>모든 XMPP 파트너에 대해 허용되는 총 동시 연결 수입니다. 기본값은 1000입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DialbackPassphrase</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>TCP 다이얼백 연결을 통해 XMPP 파트너에 연결할 때 사용되는 암호입니다. TCP 다이얼백을 사용하는 경우 파트너는 XMPP 게이트웨이에 연결한 다음 전화를 끊습니다. 그러면 XMPP 게이트웨이에서 파트너에게 다시 전화를 걸며, 이 시점부터 통신 세션을 시작할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableLoggingAllMessageBodies</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync Server 2013에서 모든 메신저 대화의 실제 내용을 기록합니다. 개인 정보 보호를 위해 메시지 내용은 대개 삭제되며 통신 끝점에 대한 정보만 로그 파일에 포함됩니다.</p>
<p>기본값은 False입니다.</p></td>
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
<td><p>수정할 XMPP 게이트웨이 구성 설정의 고유 식별자입니다. 이러한 설정에 대해서는 전역 인스턴스를 하나만 사용할 수 있으므로 <strong>Set-CsXmppGatewayConfiguration</strong> cmdlet을 호출할 때 ID를 지정할 필요가 없습니다. 그러나 원하는 경우에는 다음 구문을 사용하여 전역 설정을 참조할 수 있습니다.</p>
<p>-Identity global</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>KeepAliveInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>파트너가 &quot;연결 유지&quot; 메시지를 보낼 때까지 경과할 수 있는 최대 시간(초)입니다. 연결 유지 메시지는 연결이 아직 활성 상태인지만을 확인합니다. 연결 유지 메시지를 받기 전에 시간 간격이 지나면 연결이 닫힙니다. 기본값은 300초입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PartnerConnectionLimit</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>단일 XMPP 파트너에 대해 허용되는 총 동시 연결 수입니다. 기본값은 20입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>StreamEstablishmentTimeout</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>XMPP 스트림을 설정하도록 XMPP 파트너에게 할당되는 최대 시간(초)입니다. 이 제한 시간이 지나면 연결이 자동으로 종료됩니다. 기본값은 60초입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>StreamInactivityTimeout</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>연결이 자동으로 종료될 때까지 XMPP 스트림이 비활성 상태로 유지될 수 있는 최대 시간(초)입니다. 기본값은 600초(10분)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SubscriptionRefreshInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>파트너가 현재 상태 구독을 새로 고칠 때까지 경과할 수 있는 총 시간(초)입니다. 기본값은 28800초(8시간)입니다.</p></td>
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

**Set-CsXmppGatewayConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.XmppGatewaySettings 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsXmppGatewayConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.XmppGatewaySettings 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsXmppGatewayConfiguration](get-csxmppgatewayconfiguration.md)

