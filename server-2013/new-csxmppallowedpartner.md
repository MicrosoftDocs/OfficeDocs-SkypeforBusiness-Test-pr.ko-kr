---
title: New-CsXmppAllowedPartner
TOCTitle: New-CsXmppAllowedPartner
ms:assetid: 02f8525a-d8ec-49d8-805b-e76c5449c553
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204631(v=OCS.15)
ms:contentKeyID: 49302634
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsXmppAllowedPartner

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 XMPP 허용 파트너를 만듭니다. XMPP(Extensible Messaging and Presence Protocol)는 XML을 사용하여 메시지를 교환하기 위한 개방형 표준 통신 프로토콜입니다. 허용 파트너는 해당 사용자가 Lync Server 2013 사용자와 메신저 대화 및 현재 상태 정보를 교환하도록 권한이 부여된 메신저 및 현재 상태 공급자입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsXmppAllowedPartner -Domain <String> <COMMON PARAMETERS>

    New-CsXmppAllowedPartner -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AdditionalDomains <PSListModifier>] [-Confirm [<SwitchParameter>]] [-ConnectionLimit <UInt32>] [-Description <String>] [-EnableKeepAlive <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-PartnerType <Federated | PublicVerified | PublicUnverified>] [-ProxyFqdn <String>] [-SaslNegotiation <Required | Optional | NotSupported>] [-SupportDialbackNegotiation <$true | $false>] [-TlsNegotiation <Required | Optional | NotSupported>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 새 XMPP 허용 파트너 contoso.com을 만듭니다. 이 예제에서는 PartnerType 속성이 "PublicVerified"로 설정됩니다.

    New-CsXmppAllowedPartner -Identity "contoso.com" -PartnerType "PublicVerified"

## 예제 2

예제 2에서는 ID가 fabrikam.com인 새 XMPP 허용 파트너를 만듭니다. 여기서는 하위 도메인 research.fabrikam2.com을 지원할 수 있도록 루트 도메인 fabrikam.com 외에 AdditionalDomains 속성이 포함됩니다.

    New-CsXmppAllowedPartner -Identity "fabrikam.com" -AdditionalDomains "research.fabrikam2.com"

## 자세한 정보

XMPP(Extensible Messaging and Presence Protocol)는 인터넷에서 메시지를 보내는 데 사용되는 XML 기반 표준 통신 프로토콜입니다. XMPP(이전 이름은 Jabber)는 Google Talk, Facebook 채팅을 비롯한 여러 인터넷 메시징 및 통신 응용 프로그램에서 지원됩니다.

사용자가 XMPP 네트워크의 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있도록 하려면 해당 네트워크가 XMPP 허용 파트너로 구성되어 있어야 합니다. 또한 XMPP 액세스를 허용하는 외부 액세스 정책을 사용자에게 할당해야 합니다. 기본적으로 사용자는 허용 파트너 목록에 있는 모든 XMPP 네트워크의 사용자와 통신하도록 허용됩니다. 사용자가 지정된 네트워크의 사용자와 통신하지 못하도록 하려면 허용 파트너 목록에서 해당 네트워크를 삭제해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsXmppAllowedPartner"}

**Lync Server 제어판:**Lync Server 제어판을 사용하여 새 XMPP 허용 파트너를 만들려면 외부 사용자 액세스, XMPP 페더레이션 파트너, 새로 만들기를 차례로 클릭합니다.

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
<td><p><em>Domain</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>XMPP 허용 파트너의 주 도메인입니다. 예를 들면 다음과 같습니다.</p>
<p>-Domain &quot;fabrikam.com&quot;</p>
<p>Domain 매개 변수 또는 Identity 매개 변수를 사용하여 주 도메인을 지정할 수 있지만 같은 명령에 두 매개 변수를 모두 사용할 수는 없습니다.</p>
<p>AdditionalDomains 매개 변수를 사용하여 추가 도메인을 지정할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>XMPP 허용 파트너의 주 도메인입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;fabrikam.com&quot;</p>
<p>Domain 매개 변수 또는 Identity 매개 변수를 사용하여 주 도메인을 지정할 수 있지만 같은 명령에 두 매개 변수를 모두 사용할 수는 없습니다.</p>
<p>AdditionalDomains 매개 변수를 사용하여 추가 도메인을 지정할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AdditionalDomains</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>허용 파트너에 속하는 추가 XMPP 도메인입니다. 다음과 같이 쉼표를 사용하여 각 도메인 이름을 구분하는 방법으로 여러 도메인을 지정할 수 있습니다.</p>
<p>-AdditionalDomains &quot;fabrikam2.com&quot;,&quot;fabrikam3.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ConnectionLimit</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>특정 파트너에게 허용되는 최대 동시 연결 수를 지정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 XMPP 허용 파트너와 관련하여 추가 텍스트를 제공할 수 있도록 합니다. 예를 들어 Description에는 파트너에 대한 연락처 정보를 포함할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableKeepAlive</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>XMPP 파트너가 연결이 활성 상태인지를 확인하기 위해 &quot;연결 유지&quot; 패킷을 주기적으로 전송해야 하는지 여부를 나타냅니다.</p>
<p>기본값은 True입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 내용으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수를 사용하여 호출된 이 cmdlet의 출력을 변수에 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 내용을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PartnerType</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.PartnerType</p></td>
<td><p>Lync Server 2013와 XMPP 파트너 간의 관계를 지정합니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Federated(XMPP 파트너가 페더레이션 도메인에 포함됨)</p>
<p>* PublicVerified</p>
<p>* PublicUnverified</p>
<p>기본값은 PublicUnverified입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ProxyFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>XMPP 파트너가 사용하는 프록시 서버의 정규화된 도메인 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SaslNegotiation</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.SaslNegotiation</p></td>
<td><p>서버 인증에 사용되는 프로토콜인 SASL(Simple Authentication and Security Layer) 프로토콜에 대한 지원을 나타냅니다.</p>
<p>사용 가능한 값은 다음과 같습니다.</p>
<p>* Required(SASL 협상을 지원해야 함)</p>
<p>* Optional(SASL이 사용 가능한 경우 사용됨)</p>
<p>* NotSupported(SASL 협상이 지원되지 않음)</p>
<p>기본값은 Required입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SupportDialbackNegotiation</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>다이얼백 협상을 지원할지 여부를 나타냅니다. 다이얼백 협상을 사용하는 경우 서버 A에서 서버 B에 연결할 때 통신이 즉시 설정되지 않습니다. 대신 서버 B에서 먼저 서버 A가 속하는 것으로 추정되는 도메인의 신뢰할 수 있는 DNS 서버에 연결하여 서버 A의 ID를 확인합니다.</p>
<p>다이얼백 협상은 SASL 또는 TLS만큼 안전하지 않으며, 인증서를 사용하여 서버 ID를 확인할 수 없는 상황에서 주로 사용됩니다.</p>
<p>기본값은 True입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TlsNegotiation</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.TlsNegotiation</p></td>
<td><p>서버 간 데이터 스트림을 암호화하는 데 사용되는 프로토콜인 전송 계층 보안 프로토콜에 대한 지원을 나타냅니다.</p>
<p>사용 가능한 값은 다음과 같습니다.</p>
<p>* Required(TLS 협상을 지원해야 함)</p>
<p>* Optional(TLS가 사용 가능한 경우 사용됨)</p>
<p>* NotSupported(TLS 협상이 지원되지 않음). 기본값은 Required입니다.</p>
<p></p></td>
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

없음. **New-CsXmppAllowedPartner** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsXmppAllowedPartner** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.XmppAllowedPartner\#Decorated 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsXmppAllowedPartner](get-csxmppallowedpartner.md)  
[Remove-CsXmppAllowedPartner](remove-csxmppallowedpartner.md)  
[Set-CsXmppAllowedPartner](set-csxmppallowedpartner.md)

