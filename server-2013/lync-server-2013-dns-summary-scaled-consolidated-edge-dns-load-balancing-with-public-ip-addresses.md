---
title: 'Lync Server 2013: DNS 요약 - 조정된 통합 에지, 공용 IP 주소의 DNS 부하 분산'
TOCTitle: DNS 요약 - 조정된 통합 에지, 공용 IP 주소의 DNS 부하 분산
ms:assetid: dc8f096a-a0a4-4f71-8930-88ff8fc089d9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205319(v=OCS.15)
ms:contentKeyID: 49305249
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 DNS 요약 - 조정된 통합 에지, 공용 IP 주소의 DNS 부하 분산

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013에 원격 액세스하기 위한 DNS 레코드 요구 사항은 인증서 및 포트에 대한 요구 사항보다 훨씬 간단합니다. 또한 Lync 2013을 실행하는 클라이언트 구성 방법 및 페더레이션 사용 여부에 따라 많은 레코드를 선택적으로 사용할 수 있습니다.

Lync 2013 DNS 요구 사항에 대한 자세한 내용은 [Lync Server 2013에 대한 DNS 요구 사항 확인](lync-server-2013-determine-dns-requirements.md)을 참조하십시오.

분할 DNS가 구성되어 있지 않은 경우 Lync 2013 클라이언트의 자동 구성을 구성하는 방법에 대한 자세한 내용은 [Lync Server 2013에 대한 DNS 요구 사항 확인](lync-server-2013-determine-dns-requirements.md)의 "분할 DNS 없는 자동 구성" 섹션을 참조하십시오.

다음 표에는 단일 통합 에지 토폴로지 그림에 표시된 단일 통합 에지 토폴로지를 지원하는 데 필요한 DNS 레코드가 요약되어 있습니다. 특정 DNS 레코드는 Lync 2013 클라이언트의 자동 구성에만 필요합니다. GPO(그룹 정책 개체)를 사용하여 Lync 클라이언트를 구성하려는 경우 연결된 레코드가 필요하지 않습니다.

## 중요: 에지 서버 네트워크 어댑터 요구 사항

라우팅 문제를 방지하려면 에지 서버가 있고 기본 게이트웨이가 외부 인터페이스와 연결된 네트워크 어댑터에만 설정되어 있어야 합니다. 예를 들어 [Lync Server 2013의 조정된 통합 에지, 공용 IP 주소의 DNS 부하 분산](lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md)의 확대된 통합 에지 시나리오 그림에 표시된 바와 같이 기본 게이트웨이가 외부 방화벽을 가리킵니다.

다음과 같이 각 에지 서버에 두 개의 네트워크 어댑터를 구성할 수 있습니다.

  - **네트워크 어댑터 1 - 노드 1(내부 인터페이스)**
    
    172.25.33.10이 할당된 내부 인터페이스입니다.
    
    기본 게이트웨이가 정의되어 있지 않습니다.
    
    에지 내부 인터페이스가 포함된 네트워크에서 Lync Server 2013 또는 Lync Server 2013 클라이언트를 실행하는 서버가 포함된 네트워크까지의 경로가 있어야 합니다(예: 172.25.33.0에서 192.168.10.0까지의 경로).

  - **네트워크 어댑터 1 - 노드 2(내부 인터페이스)**
    
    172.25.33.11이 할당된 내부 인터페이스입니다.
    
    기본 게이트웨이가 정의되어 있지 않습니다.
    
    에지 내부 인터페이스가 포함된 네트워크에서 Lync Server 2013 또는 Lync Server 2013 클라이언트를 실행하는 서버가 포함된 네트워크까지의 경로가 있어야 합니다(예: 172.25.33.0에서 192.168.10.0까지의 경로).

  - **네트워크 어댑터 2 노드 1(외부 인터페이스)**
    
    3개의 전용 IP 주소가 이 네트워크 어댑터에 할당됩니다. 예를 들면 액세스 에지 서비스에 대해 131.107.155.10, 웹 회의 에지 서비스에 대해 131.107.155.20, A/V 에지 서비스에 대해 131.107.155.30이 할당됩니다.
    
    액세스 에지 서비스 공용 IP 주소는 기본 게이트웨이가 공용 라우터로 설정된 기본 IP 주소입니다(131.107.155.1).
    
    웹 회의 에지 서비스 및 A/V 에지 서비스 개인 IP 주소는 Windows Server에서 **로컬 영역 연결 속성**의 **인터넷 프로토콜 버전 4(TCP/IPv4)** 및 **인터넷 프로토콜 버전 6(TCP/IPv6)** 속성의 **고급** 섹션에 있는 추가 IP 주소입니다.
    

    > [!NOTE]
    > 권장되지는 않지만 세 개의 모든 에지 서비스 인터페이스에 대해 단일 IP 주소를 사용할 수도 있습니다. 이 경우 IP 주소를 절약할 수 있지만 서비스마다 다른 포트 번호가 필요합니다. 기본 포트 번호는 대부분의 원격 방화벽에서 트래픽을 허용하는 443/TCP입니다. 예를 들어 포트 번호를 액세스 에지 서비스에 대해 5061/TCP로 변경하고, 웹 회의 에지 서비스에 대해 444/TCP로 변경하고, A/V 에지 서비스에 대해 443/TCP로 변경할 경우 방화벽에서 5061/TCP와 444/TCP를 통한 트래픽을 허용하지 않는 원격 사용자에게 문제가 발생할 수 있습니다. 또한 세 개의 고유 IP 주소를 사용하면 IP 주소로 필터링할 수 있기 때문에 문제 해결에도 더 유리합니다.



  - **네트워크 어댑터 2 노드 2(외부 인터페이스)**
    
    세 개의 전용 IP 주소가 이 네트워크 어댑터에 할당됩니다. 예를 들면 액세스 에지 서비스에 대해 131.107.155.11, 웹 회의 에지 서비스에 대해 131.107.155.21, A/V 에지 서비스에 대해 131.107.155.31이 할당됩니다.
    
    액세스 에지 서비스 공용 IP 주소는 기본 게이트웨이가 공용 라우터로 설정된 기본 IP 주소입니다(131.107.155.1).
    
    웹 회의 에지 서비스 및 A/V 에지 서비스 개인 IP 주소는 Windows Server에서 **로컬 영역 연결 속성**의 **인터넷 프로토콜 버전 4(TCP/IPv4)** 및 **인터넷 프로토콜 버전 6(TCP/IPv6)** 속성의 **고급** 섹션에 있는 추가 IP 주소입니다.


> [!TIP]
> 두 개의 네트워크 어댑터로 에지 서버 구성이 두 가지 옵션 중 하나입니다. 다른 옵션은 에지 서버의 내부에 한 개의 네트워크 어댑터 하나를 사용하고 외부에 세 개의 네트워크 어댑터를 사용하는 것입니다. 이 옵션을 사용할 때의 주요 이점은 에지 서버 서비스마다 고유한 네트워크 어댑터가 사용되므로 문제 해결이 필요한 경우 데이터 수집이 더 간략합니다.



### 확장된 통합 에지에 필요한 DNS 레코드, 공용 IP 주소로 DNS 부하 분산(예)

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
<td><p>131.107.155.10과 131.107.155.11</p></td>
<td><p>액세스 에지 서비스 외부 인터페이스(Contoso). Lync 사용이 가능한 사용자를 포함하는 모든 SIP 도메인에 대해 필요에 따라 반복합니다.</p></td>
</tr>
<tr class="even">
<td><p>외부 DNS/A</p></td>
<td><p>webcon.contoso.com</p></td>
<td><p>131.107.155.20과 131.107.155.21</p></td>
<td><p>웹 회의 에지 서비스 외부 인터페이스</p></td>
</tr>
<tr class="odd">
<td><p>외부 DNS/A</p></td>
<td><p>av.contoso.com</p></td>
<td><p>131.107.155.30과 131.107.155.31</p></td>
<td><p>A/V 에지 서비스 외부 인터페이스</p></td>
</tr>
<tr class="even">
<td><p>외부 DNS/SRV/443</p></td>
<td><p>_sip._tls.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>액세스 에지 서비스 외부 인터페이스입니다. Lync 2013 및 Lync 2010 클라이언트의 자동 구성이 외부에서 작동하는 데 필요합니다. Lync 사용이 가능한 사용자를 포함하는 모든 SIP 도메인에 대해 필요에 따라 반복합니다.</p></td>
</tr>
<tr class="odd">
<td><p>외부 DNS/SRV/5061</p></td>
<td><p>_sipfederationtls._tcp.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>액세스 에지 서비스 외부 인터페이스. 페더레이션 파트너에 대한 자동 DNS 검색에 필요하며, 이를 &quot;허용 SIP 도메인&quot;(이전 릴리스에서는 확장 페더레이션이라고 함)이라고 합니다. Lync 사용이 가능한 사용자를 포함하는 모든 SIP 도메인에 대해 필요에 따라 반복합니다.</p></td>
</tr>
<tr class="even">
<td><p>내부 DNS/A</p></td>
<td><p>lsedge.contoso.net</p></td>
<td><p>172.25.33.10과 172.25.33.11</p></td>
<td><p>통합 에지 내부 인터페이스</p></td>
</tr>
</tbody>
</table>


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
<td><p>SIP 액세스 에지 서비스 외부 인터페이스. 다른 잠재적 페더레이션 파트너와의 페더레이션에 대한 자동 DNS 검색에 필요하며, 이를 “허용 SIP 도메인”(이전 릴리스에서는 확장 페더레이션이라고 함)이라고 합니다.</p>


> [!IMPORTANT]
> Lync 사용이 가능한 사용자와 푸시 알림 서비스 또는 Apple 푸시 알림 서비스를 사용하는 Microsoft Lync Mobile 클라이언트를 포함하는 모든 SIP 도메인에 대해 필요에 따라 반복합니다.


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
<td><p>액세스 에지 서비스 외부 인터페이스(Contoso). Lync 사용이 가능한 사용자를 포함하는 모든 SIP 도메인에 대해 필요에 따라 반복합니다.</p></td>
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
<td><p>액세스 에지 서비스 또는 에지 풀의 XMPP 프록시 외부 인터페이스입니다. XMPP 연락처를 사용하는 연락처에서 글로벌 정책, 사용자가 위치한 사이트 정책 또는 Lync 사용자에게 적용된 사용자 정책을 통해 외부 액세스 정책의 구성에서 허용되는 경우 Lync 사용이 가능한 사용자를 포함하는 모든 내부 SIP 도메인에 대해 필요에 따라 반복합니다. 허용된 XMPP 도메인이 XMPP 페더레이션 파트너 정책에도 구성되어야 합니다. 자세한 내용은 <strong>참고 항목</strong>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p>외부 DNS/A</p></td>
<td><p>xmpp.contoso.com(예)</p></td>
<td><p>XMPP 프록시를 호스트하는 proxy 에지 풀 또는 에지 서버에서 액세스 에지 서비스의 IP 주소</p></td>
<td><p>XMPP 프록시 서비스를 호스트하는 액세스 에지 서비스 또는 에지 풀을 가리킵니다. 일반적으로 사용자가 만드는 SRV 레코드는 이 호스트(A 또는 AAAA) 레코드를 가리킵니다.</p></td>
</tr>
</tbody>
</table>

