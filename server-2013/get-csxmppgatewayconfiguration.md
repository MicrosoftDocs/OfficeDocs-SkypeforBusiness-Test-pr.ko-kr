---
title: Get-CsXmppGatewayConfiguration
TOCTitle: Get-CsXmppGatewayConfiguration
ms:assetid: 4c9ee876-de89-420c-bda9-9901cef47799
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204869(v=OCS.15)
ms:contentKeyID: 49303581
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsXmppGatewayConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용 중인 XMPP 게이트웨이 구성 설정에 대한 정보를 반환합니다. XMPP(Extensible Messaging and Presence Protocol)는 XML을 사용하여 메시지를 교환하기 위한 개방형 표준 통신 프로토콜입니다. Lync Server 2013 사용자는 XMPP 게이트웨이를 통해 XMPP가 적용된 메신저 대화 및 현재 상태 공급자를 이용 중인 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsXmppGatewayConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsXmppGatewayConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 현재 사용 중인 XMPP 게이트웨이에 대한 정보를 반환합니다. Lync Server 2013에서는 게이트웨이 설정의 전역 컬렉션을 하나만 사용할 수 있으므로 전역 설정에 대한 정보를 가져오려는 경우에는 Identity 매개 변수를 포함할 필요가 없습니다.

    Get-CsXmppGatewayConfiguration

## 자세한 정보

XMPP(Extensible Messaging and Presence Protocol)는 인터넷에서 메시지를 보내는 데 사용되는 XML 기반 표준 통신 프로토콜입니다. XMPP(이전 이름은 Jabber)는 Google Talk, Facebook 채팅을 비롯한 여러 인터넷 메시징 및 통신 응용 프로그램에서 지원됩니다.

Lync 2013가 XMPP 네트워크의 사용자와 통신할 수 있도록 하는 XMPP 게이트웨이는 원래 Microsoft Lync Server 2010의 추가 기능으로 공개되었습니다. Lync Server 2013 소프트웨어에서는 이 기능이 기본 제공됩니다. 즉, 다음을 수행하는 경우 사용자가 XMPP 사용자와 통신할 수 있습니다.

  -   
    XMPP 게이트웨이 설정 구성

  -   
    Google Talk 등의 다른 XMPP 네트워크를 허용되는 XMPP 파트너로 구성

Lync Server 2013에서는 XMPP 구성 설정 전역 집합을 하나만 제공하므로 지정된 사이트나 지정된 등록자 풀에 대해 XMPP를 선택적으로 사용하거나 사용하지 않도록 설정할 수는 없습니다. 실제로 XMPP는 사용하거나 사용하지 않도록 설정할 수 없으며 항상 사용하도록 설정됩니다. 사용자가 XMPP 네트워크와 통신하지 못하도록 하려면 허용 XMPP 파트너를 모두 제거해야 합니다. 사용자는 XMPP 네트워크가 허용 파트너로 구성된 경우에만 해당 네트워크와 통신할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsXmppGatewayConfiguration"}

**Lync Server 제어판:** **Get-CsXmppGatewayConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>XMPP 게이트웨이 구성 설정의 컬렉션을 참조할 때 와일드카드 값을 사용할 수 있습니다. 이러한 설정에 대해서는 전역 인스턴스를 하나만 사용할 수 있으므로 Filter 매개 변수는 사용할 필요가 없습니다. 그러나 원하는 경우 다음 구문을 사용하여 전역 설정을 참조할 수 있습니다.</p>
<p>-Filter &quot;g*&quot;</p>
<p>이 구문은 ID가 &quot;g&quot; 문자로 시작되는 모든 XMPP 게이트웨이 구성 설정을 가져옵니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>XMPP 게이트웨이 구성 설정의 고유 식별자입니다. 이러한 설정에 대해서는 전역 인스턴스를 하나만 사용할 수 있으므로 <strong>Get-CsXmppGatewayConfiguration</strong> cmdlet을 호출할 때 Identity를 지정할 필요가 없습니다. 그러나 원하는 경우에는 다음 구문을 사용하여 전역 설정을 참조할 수 있습니다.</p>
<p>-Identity global</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 XMPP 게이트웨이 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsXmppGatewayConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsXmppGatewayConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.XmppGatewaySettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Set-CsXmppGatewayConfiguration](set-csxmppgatewayconfiguration.md)

