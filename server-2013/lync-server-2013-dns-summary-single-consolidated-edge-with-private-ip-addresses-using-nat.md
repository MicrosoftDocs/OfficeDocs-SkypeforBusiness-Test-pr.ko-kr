---
title: 'Lync Server 2013: DNS 요약 - NAT 사용 개인 IP 주소의 단일 통합 에지'
TOCTitle: DNS 요약 - NAT 사용 개인 IP 주소의 단일 통합 에지
ms:assetid: a7e5d792-f397-45e5-af85-20d0f4bf405f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412787(v=OCS.15)
ms:contentKeyID: 49304641
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 DNS 요약 - NAT 사용 개인 IP 주소의 단일 통합 에지

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013에 원격 액세스하기 위한 DNS 레코드 요구 사항은 인증서 및 포트에 대한 요구 사항보다 훨씬 간단합니다. 또한 Lync 2013을 실행하는 클라이언트 구성 방법 및 페더레이션 사용 여부에 따라 많은 레코드를 선택적으로 사용할 수 있습니다.

Lync 2013 DNS 요구 사항에 대한 자세한 내용은 [Lync Server 2013에 대한 DNS 요구 사항 확인](lync-server-2013-determine-dns-requirements.md)을 참조하십시오.

분할 DNS가 구성되어 있지 않은 경우 Lync 2013을 실행하는 클라이언트의 자동 구성에 대한 자세한 내용은 [Lync Server 2013에 대한 DNS 요구 사항 확인](lync-server-2013-determine-dns-requirements.md)의 "분할 DNS 없는 자동 구성"을 참조하십시오.

다음 표에는 단일 통합 에지 토폴로지 그림에 표시된 단일 통합 에지 토폴로지를 지원하는 데 필요한 DNS 레코드가 요약되어 있습니다. 특정 DNS 레코드는 Lync 2013 및 Lync 2010 클라이언트의 자동 구성에만 필요합니다. GPO(그룹 정책 개체)를 사용하여 Lync 클라이언트를 구성하려는 경우 연결된 자동 구성 레코드가 필요하지 않습니다.

## 중요: 에지 서버 네트워크 어댑터 요구 사항

라우팅 문제를 방지하려면 에지 서버에 두 개 이상의 네트워크 어댑터가 있고 기본 게이트웨이가 외부 인터페이스와 연결된 네트워크 어댑터에만 설정되어 있어야 합니다. 예를 들어 [Lync Server 2013의 개인 IP 주소 및 NAT 사용 단일 통합 에지](lync-server-2013-single-consolidated-edge-with-private-ip-addresses-and-nat.md)의 단일 통합 에지 토폴로지 그림에 표시된 바와 같이 기본 게이트웨이가 외부 방화벽(10.45.16.1)을 가리킵니다.

다음과 같이 에지 서버에 네트워크 어댑터 두 개를 구성할 수 있습니다.

  - **네트워크 어댑터 1(내부 인터페이스)**
    
    172.25.33.10이 할당된 내부 인터페이스입니다.
    
    기본 게이트웨이가 정의되어 있지 않습니다.
    
    에지 내부 인터페이스가 포함된 네트워크에서 Lync Server 2013 또는 Lync Server 2013 클라이언트를 실행하는 서버가 포함된 네트워크까지의 경로가 있어야 합니다(예: 172.25.33.0에서 192.168.10.0까지의 경로).

  - **네트워크 어댑터 2(외부 인터페이스)**
    
    이 네트워크 어댑터에는 세 개의 개인 IP(예: 액세스 에지에 10.45.16.10, 웹 회의 에지에 10.45.16.20, AV 에지에 10.45.16.30)
    

    > [!NOTE]
    > 권장되지는 않지만 세 가지 에지 서비스 인터페이스 모두에 단일 IP 주소를 사용할 수 있습니다. 이렇게 하면 IP 주소가 저장되지만 각 서비스에 서로 다른 포트 번호가 필요합니다. 기본 포트 번호는 443/TCP로, 가장 원격에 있는 방화벽에서 트래픽이 허용되도록 합니다. 이 포트 값을 변경할 경우(예: 액세스 에지에 5061/TCP, 웹 회의 에지에 444/TCP, AV 에지에 443/TCP) 방화벽에서 5061/TCP 및 444/TCP를 통한 트래픽을 허용하지 않는 원격 사용자에게 문제가 될 수 있습니다. 또한 세 가지 고유 IP 주소를 사용할 경우 IP 주소를 기준으로 필터링할 수 있기 때문에 문제를 해결하기가 더 쉬워집니다.

    
    액세스 에지 IP 주소는 기본 게이트웨이가 통합 라우터로 설정된 기본 IP 주소입니다(10.45.16.1).
    
    웹 회의 및 A/V 에지 IP 주소는 보조 IP 주소입니다.


> [!TIP]
> 두 개의 네트워크 어댑터로 에지 서버 구성이 두 가지 옵션 중 하나입니다. 다른 옵션은 에지 서버의 내부에 한 개의 네트워크 어댑터 하나를 사용하고 외부에 세 개의 네트워크 어댑터를 사용하는 것입니다. 이 옵션을 사용할 때의 주요 이점은 에지 서버 서비스마다 고유한 네트워크 어댑터가 사용되므로 문제 해결이 필요한 경우 데이터 수집이 더 간략합니다.



### NAT를 사용하며 전용 IP 주소를 갖는 단일 통합 에지 토폴로지에 필요한 DNS 레코드(예)

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
<th>FQDN/DNS 레코드</th>
<th>IP 주소/FQDN</th>
<th>매핑 대상/설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>외부 DNS/A</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>131.107.155.10</p></td>
<td><p>액세스 에지 외부 인터페이스(Contoso). Lync를 사용하도록 설정된 사용자의 모든 SIP 도메인에 대해 필요한 만큼 반복하십시오.</p></td>
</tr>
<tr class="even">
<td><p>외부 DNS/A</p></td>
<td><p>webcon.contoso.com</p></td>
<td><p>131.107.155.20</p></td>
<td><p>웹 회의 에지 외부 인터페이스</p></td>
</tr>
<tr class="odd">
<td><p>외부 DNS/A</p></td>
<td><p>av.contoso.com</p></td>
<td><p>131.107.155.30</p></td>
<td><p>A/V 에지 외부 인터페이스</p></td>
</tr>
<tr class="even">
<td><p>외부 DNS/SRV/443</p></td>
<td><p>_sip._tls.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>액세스 에지 외부 인터페이스. Lync 2013 및 Lync 2010 클라이언트가 외부적으로 작동하도록 자동 구성하는 데 필요합니다. Lync를 사용하도록 설정된 사용자의 모든 SIP 도메인에 대해 필요한 만큼 반복하십시오.</p></td>
</tr>
<tr class="odd">
<td><p>외부 DNS/SRV/5061</p></td>
<td><p>_sipfederationtls._tcp.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>SIP 액세스 에지 외부 인터페이스. &quot;허용 SIP 도메인&quot;(이전 버전에서는 향상된 페더레이션이라고 함)이라는 페더레이션 파트너의 자동 DNS 검색에 필요합니다. Lync를 사용하도록 설정된 사용자의 모든 SIP 도메인에 대해 필요한 만큼 반복하십시오.</p></td>
</tr>
<tr class="even">
<td><p>내부 DNS/A</p></td>
<td><p>lsedge.contoso.net</p></td>
<td><p>172.25.33.10</p></td>
<td><p>통합 에지 내부 인터페이스</p></td>
</tr>
</tbody>
</table>



> [!IMPORTANT]
> 앞의 표에 나열되어 있는 레코드는 분할 DNS를 사용하지 않을 경우 레코드가 있어야 할 영역을 강조하기 위해 <EM>.net</EM> 확장명 또는 <EM>.com</EM> 확장명으로 표시되어 있습니다. 분할 DNS를 사용하는 경우에는 모든 레코드가 같은 <EM>.com</EM> 영역에 있으므로 내부 버전인지 아니면 외부 DNS 영역 버전인지만 구분하면 됩니다. 자세한 내용은 <A href="lync-server-2013-determine-dns-requirements.md">Lync Server 2013에 대한 DNS 요구 사항 확인</A>에서 "분할 DNS"를 참조하십시오.



## 페더레이션에 필요한 레코드


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
<td><p>SIP 액세스 에지 외부 인터페이스. &quot;허용 SIP 도메인&quot;(이전 버전에서는 향상된 페더레이션이라고 함)이라는 잠재적인 페더레이션 파트너의 자동 DNS 검색에 필요합니다. Lync를 사용하도록 설정된 사용자의 모든 SIP 도메인에 대해 필요한 만큼 반복하십시오.</p>

> [!IMPORTANT]
> 이 SRV 레코드는 모바일 기능 및 푸시 알림 클리어링 하우스에 필요합니다.

</td>
</tr>
</tbody>
</table>


## DNS 요약 ? 공용 IM 연결


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
<td><p>액세스 에지 외부 인터페이스(Contoso). Lync를 사용하도록 설정된 사용자의 모든 SIP 도메인에 대해 필요한 만큼 반복하십시오.</p></td>
</tr>
</tbody>
</table>


## 확장 가능 메시징 및 현재 상태 프로토콜에 대한 DNS 요약


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
<td><p>외부 DNS/SRV/5269</p></td>
<td><p>_xmpp-server._tcp.contoso.com</p></td>
<td><p>xmpp.contoso.com</p></td>
<td><p>액세스 에지 서비스 또는 에지 풀의 XMPP 프록시 외부 인터페이스입니다. Lync를 사용하도록 설정된 사용자의 모든 SIP 도메인에 대해 필요한 만큼 반복하십시오. 이 SIP 도메인에서는 전역 정책, 사용자가 위치한 곳의 사이트 정책, Lync를 사용하도록 설정된 사용자에게 적용되는 사용자 정책을 통해 외부 액세스 정책을 구성하여 XMPP 대화 상대와의 연락이 허용됩니다. 또한 허용되는 XMPP 도메인을 XMPP 페더레이션 파트너 정책에서 구성해야 합니다. 자세한 내용은 <strong>참고 항목</strong>의 항목을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p>외부 DNS/A</p></td>
<td><p>xmpp.contoso.com(예)</p></td>
<td><p>XMPP 프록시를 호스트하는 proxy 에지 풀 또는 에지 서버에서 액세스 에지 서비스의 IP 주소</p></td>
<td><p>XMPP 프록시 서비스를 호스트하는 액세스 에지 서비스 또는 에지 풀을 가리킵니다. 일반적으로 사용자가 만드는 SRV 레코드는 이 호스트(A 또는 AAAA) 레코드를 가리킵니다.</p></td>
</tr>
</tbody>
</table>

