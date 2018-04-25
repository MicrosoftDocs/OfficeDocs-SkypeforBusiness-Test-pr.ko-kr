---
title: Get-CsXmppAllowedPartner
TOCTitle: Get-CsXmppAllowedPartner
ms:assetid: 6d031b38-325a-4196-998f-c473390f2055
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204981(v=OCS.15)
ms:contentKeyID: 49303960
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsXmppAllowedPartner

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직과의 통신 권한이 부여된 XMPP 파트너에 대한 정보를 반환합니다. XMPP(Extensible Messaging and Presence Protocol)는 XML을 사용하여 메시지를 교환하기 위한 개방형 표준 통신 프로토콜입니다. 허용 파트너는 Lync Server 2013 사용자와 메신저 대화 및 현재 상태 정보를 교환하도록 권한이 부여된 메신저 및 현재 상태 공급자입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsXmppAllowedPartner [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsXmppAllowedPartner [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1의 명령은 조직에서 사용하도록 구성된 모든 XMPP 허용 파트너에 대한 정보를 반환합니다.

    Get-CsXmppAllowedPartner

## 예제 2

예제 2에서는 단일 XMPP 허용 파트너, 즉 ID가 xmpp.contoso.com인 파트너에 대한 정보를 반환합니다.

    Get-CsXmppAllowedPartner -Identity "xmpp.contoso.com"

## 예제 3

예제 3에서는 ID가 문자열 값 ".org"로 끝나는 모든 XMPP 허용 파트너(예: xmpp.contoso.org, xmpp.fabrikam.org)에 대한 정보를 반환합니다.

    Get-CsXmppAllowedPartner - Filter "*.org"

## 예제 4

예제 4에 표시된 명령은 SASL(Simple Authentication and Security Layer) 협상이 필요한 모든 XMPP 허용 파트너에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsXmppAllowedPartner** cmdlet을 사용하여 모든 XMPP 허용 파트너에 대한 정보를 반환합니다. 반환된 파트너는 **Where-Object** cmdlet에 파이프되며, 이 cmdlet은 SaslNegotiation 속성이 Required인 파트너만 선택합니다.

    Get-CsXmppAllowedPartner | Where-Object {$_.SaslNegotiation -eq "Required"}

## 자세한 정보

XMPP(Extensible Messaging and Presence Protocol)는 인터넷에서 메시지를 보내는 데 사용되는 XML 기반 표준 통신 프로토콜입니다. XMPP(이전 이름은 Jabber)는 Google Talk, Facebook 채팅을 비롯한 여러 인터넷 메시징 및 통신 응용 프로그램에서 지원됩니다.

사용자가 XMPP 네트워크의 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있도록 하려면 해당 네트워크가 XMPP 허용 파트너로 구성되어 있어야 합니다. 또한 XMPP 액세스를 허용하는 외부 액세스 정책을 사용자에게 할당해야 합니다. 기본적으로 사용자는 허용 파트너 목록에 있는 모든 XMPP 네트워크의 사용자와 통신하도록 허용됩니다. 사용자가 지정된 네트워크의 사용자와 통신하지 못하도록 하려면 허용 파트너 목록에서 해당 네트워크를 삭제해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsXmppAllowedPartner"}

**Lync Server 제어판:**Lync Server 제어판에서 XMPP 허용 파트너에 대한 정보를 보려면 외부 사용자 액세스, XMPP 페더레이션 파트너를 차례로 클릭합니다.

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
<td><p>반환할 XMPP 허용 파트너의 ID를 지정할 때 와일드카드를 사용할 수 있습니다. 예를 들어 &quot;*.org&quot; 필터 값은 ID가 &quot;.org&quot; 문자열 값으로 끝나는 모든 XMPP 허용 파트너의 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>반환할 XMPP 허용 파트너의 FQDN(정규화된 도메인 이름)입니다(예: fabrikam.com). 이 매개 변수 및 Filter 매개 변수가 둘 다 지정되지 않은 경우 조직에서 사용하도록 구성된 모든 XMPP 파트너가 반환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 XMPP 허용 파트너 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsXmppAllowedPartner** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsXmppAllowedPartner** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.XmppAllowedPartner\#Decorated 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsXmppAllowedPartner](new-csxmppallowedpartner.md)  
[Remove-CsXmppAllowedPartner](remove-csxmppallowedpartner.md)  
[Set-CsXmppAllowedPartner](set-csxmppallowedpartner.md)

