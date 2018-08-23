---
title: DNS 요약 - SIP, XMPP 페더레이션 및 공용 IM
TOCTitle: DNS 요약 - SIP, XMPP 페더레이션 및 공용 IM
ms:assetid: 1ed24fb8-a849-44c0-a52e-7aef7527e644
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ618369(v=OCS.15)
ms:contentKeyID: 49303008
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# DNS 요약 - SIP, XMPP 페더레이션 및 공용 IM

 

_**마지막으로 수정된 항목:** 2015-03-09_

Office Communications Server 또는 Lync Server 파트너와의 페더레이션을 정의하는 데 필요한 DNS(Domain Name System) 레코드는 다른 잠재적 파트너의 도메인 자동 DNS 검색을 허용할지에 대한 결정에 따라 결정됩니다. \_sipfederationtls.\_tcp. *\<SIP 도메인 이름\>* SRV 레코드를 게시하는 경우 다른 모든 SIP 페더레이션 도메인이 사용자의 페더레이션을 "검색"할 수 있습니다. Lync Server 제어판의 허용 도메인 및 차단된 도메인 설정을 사용하거나, Lync Server 관리 셸 및 **Get**, **Set**, **New**, **Remove-CsAllowedDomain**/**-CsBlockedDomain** PowerShell cmdlet을 사용하여 허용 도메인 또는 차단된 도메인 구성을 설정하는 방법으로 사용자와 통신할 수 있는 페더레이션 도메인을 제어할 수 있습니다. 이러한 설정을 구성하는 방법 및 PowerShell cmdlet을 사용하는 방법에 대한 자세한 내용은 이 항목 끝부분의 **관련 항목**을 참고하세요.

DNS 레코드 요약 표에는 공개(검색 가능) 페더레이션에 필요한 항목이 나와 있습니다. 페더레이션 검색을 구현하지 않으려는 경우 \_sipfederationtls.\_tcp. *\<SIP 도메인 이름\>* 레코드를 구성하지 않으면 됩니다.


> [!IMPORTANT]
> _sipfederationtls._tcp. <EM>&lt;SIP 도메인 이름&gt;</EM> SRV 레코드는 사용해야 하지만 검색 가능한 페더레이션은 설정하지 않으려는 특정 시나리오도 있습니다. 이와 같은 시나리오의 한 가지 예로 사용자를 위해 모바일 기능을 배포한 경우를 들 수 있습니다. 모바일 PNCH(푸시 알림 클리어링 하우스)는 Apple iPhone 또는 Lync 2010 Mobile 클라이언트를 사용하는 iPad 또는 Lync 2010 Mobile 또는 Lync 2013 모바일 클라이언트를 사용하는 Windows Phone에서 Microsoft Lync Mobile 클라이언트에 대해 사용되는 특수한 유형의 페더레이션입니다. 모바일 기능 및 푸시 알림의 경우에는 _sipfederationtls._tcp. <EM>&lt;SIP 도메인 이름&gt;</EM> SRV 레코드가 사용됩니다. 이 문제를 완화하고 검색 가능성을 제어하려면 <STRONG>파트너 도메인 검색 사용</STRONG> 설정 선택을 취소하여 검색을 해제합니다.



배포에 대해 XMPP(Extensible Messaging and Presence Protocol)를 구성하려면 레코드를 에지 서버 또는 에지 풀의 액세스 에지 서비스로 확인하는 외부 DNS(Domain Name System) 서버의 DNS 레코드 두 개를 만듭니다.

공용 IM 연결에 대한 DNS(Domain Name System)를 구성할 때는 외부 사용자를 지원하는 구성에서 공용 IM 연결을 지원함을 확인할 수 있습니다. 에지 서버 또는 에지 풀을 이미 구성한 경우 공용 IM 연결을 지원하는 데 필요한 DNS 레코드가 있어야 합니다.

## DNS 요약 - SIP 페더레이션


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>위치/유형/포트</th>
<th>FQDN</th>
<th>IP 주소/FQDN 호스트 레코드</th>
<th>매핑 대상/설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>외부 DNS/SRV/5061</p></td>
<td><p>_sipfederationtls._tcp.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>액세스 에지 서비스 외부 인터페이스: 다른 잠재적 페더레이션 파트너가 사용자 페더레이션에 대해 자동 DNS 검색을 수행하는 데 필요하며, &quot;허용 SIP 도메인&quot;이라고도 합니다(이전 릴리스에서는 확장 페더레이션). Lync를 사용하도록 설정된 사용자가 있는 모든 SIP 도메인에 대해 필요한 만큼 반복합니다.</p>


> [!IMPORTANT]
> 이 SRV 레코드는 모바일 기능 및 푸시 알림 클리어링 하우스에 필요합니다. SIP 도메인이 둘 이상인 경우 Lync Mobile 클라이언트를 포함할 각 도메인에 대해 SRV 레코드를 만들고 게시합니다. 배포에서 지원하는 각 SIP 도메인에 대해 명시적인 SRV 레코드가 없으면 푸시 알림 서비스 및 Apple 푸시 알림 서비스는 정상적으로 작동하지 않을 수 있습니다.


</td>
</tr>
</tbody>
</table>


## DNS 요약 - XMPP(Extensible Messaging and Presence Protocol)


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>위치/형식/포트</th>
<th>FQDN</th>
<th>IP 주소/FQDN 호스트 레코드</th>
<th>매핑 대상/설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>외부 DNS/SRV/5269</p></td>
<td><p>_xmpp-server._tcp.contoso.com</p></td>
<td><p>xmpp.contoso.com</p></td>
<td><p>액세스 에지 서비스 또는 에지 풀의 XMPP 프록시 외부 인터페이스입니다. 글로벌 정책, 사용자가 있는 사이트에 대한 사이트 정책 또는 Lync 사용 가능 사용자에게 적용되는 사용자 정책을 통해 외부 액세스 정책을 구성함으로써 XMPP 연락처와의 연결이 허용되는 모든 내부 SIP 도메인(Lync 사용 가능 사용자 포함)에 대해 필요한 만큼 반복합니다. 허용되는 XMPP 도메인은 XMPP 페더레이션 파트너 정책에서도 구성해야 합니다. 자세한 내용은 <strong>참고 항목</strong>의 항목을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p>외부 DNS/A</p></td>
<td><p>xmpp.contoso.com(예)</p></td>
<td><p>XMPP 프록시를 호스트하는 proxy 에지 풀 또는 에지 서버에서 액세스 에지 서비스의 IP 주소</p></td>
<td><p>XMPP 프록시 서비스를 호스트하는 액세스 에지 서비스 또는 에지 풀을 가리킵니다. 일반적으로 사용자가 만드는 SRV 레코드는 이 호스트(A 또는 AAAA) 레코드를 가리킵니다.</p></td>
</tr>
</tbody>
</table>


## DNS 요약 – 공용 IM 연결


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>위치/형식/포트</th>
<th>FQDN/DNS 레코드</th>
<th>IP 주소/FQDN</th>
<th>매핑 대상/설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>외부 DNS/A</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>액세스 에지 서비스 인터페이스</p></td>
<td><p>액세스 에지 서비스 외부 인터페이스(Contoso). Lync 사용이 가능한 사용자를 포함하는 모든 SIP 도메인에 대해 필요에 따라 반복합니다.</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 작업

[Lync Server 2013에서 XMPP 페더레이션 설정](lync-server-2013-setting-up-xmpp-federation.md)  
[Lync Server 2013의 푸시 알림 구성](lync-server-2013-configuring-for-push-notifications.md)  
[Lync Server 2013에서 페더레이션 파트너 검색을 사용하거나 사용하지 않도록 설정](lync-server-2013-enable-or-disable-discovery-of-federation-partners.md)  

#### 개념

[Lync Server 2013의 외부 사용자 액세스에 대한 시나리오](lync-server-2013-scenarios-for-external-user-access.md)  
[Lync Server 2013에 대한 DNS 요구 사항 확인](lync-server-2013-determine-dns-requirements.md)  

#### 기타 리소스

[Lync Server 2013에서 조직의 SIP 페더레이션된 도메인 관리](lync-server-2013-manage-sip-federated-domains-for-your-organization.md)

