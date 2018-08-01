---
title: 프런트 엔드 풀에 대한 DNS 요구 사항
TOCTitle: 프런트 엔드 풀에 대한 DNS 요구 사항
ms:assetid: ba28919c-fbbe-4c54-8bf9-2b0cd3fa39c7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412910(v=OCS.15)
ms:contentKeyID: 49304847
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 프런트 엔드 풀에 대한 DNS 요구 사항

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 섹션에서는 프런트 엔드 풀을 배포하는 데 필요한 DNS(도메인 이름 시스템) 레코드에 대해 설명합니다.

## 프런트 엔드 풀에 대한 DNS 레코드

다음 표에는 Lync Server 2013 프런트 엔드 풀을 배포하는 데 필요한 DNS 요구 사항이 지정되어 있습니다.

### 프런트 엔드 풀에 대한 DNS 요구 사항

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>배포 시나리오</th>
<th>DNS 요구 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>여러 프런트 엔드 서버 및 하나의 하드웨어 분산 장치가 포함된 프런트 엔드 풀(DNS 부하 분산이 해당 풀에 배포되었는지 여부는 상관없음)</p></td>
<td><p>DNS 부하 분산과 하드웨어 부하 분산 장치를 모두 사용할 때는 호스트(A) 레코드가 필요합니다. DNS 부하 분산용으로 프런트 엔드 풀의 FQDN(정규화된 도메인 이름)을 확인하는 내부 A 레코드를 만듭니다. 그리고 부하 분산 장치의 VIP(가상 IP) 주소에 대해 내부 웹 서비스용 내부 호스트(A) 레코드를 만듭니다. 토폴로지 작성기에 정의된 내부 웹 서비스 이름을 사용해야 합니다.</p>
<p>예를 들어 DNS 부하 분산과 하드웨어 부하 분산을 모두 사용하는 경우 풀의 각 프런트 엔드 서버에 대해 DNS 부하 분산용 A 레코드가 있고 하드웨어 부하 분산 장치의 가상 IP를 가리키는 내부 웹 서비스용 A 레코드가 있습니다.</p>
<ul>
<li><p>DNS 부하 분산:   Pool01.contoso.net   풀의 IP 주소   10.10.10.5</p>


> [!WARNING]
> 각 프런트 엔드 서버에는 고유 A 레코드도 있습니다.



<ol>
<li><p>FE01.contoso.net    10.10.10.1</p></li>
<li><p>FE02.contoso.net    10.10.10.2</p></li>
<li><p>FE03.contoso.net    10.10.10.3</p></li>
<li><p>FE04.contoso.net    10.10.10.4</p></li>
</ol></li>
<li><p>하드웨어 부하 분산:   WebInternal.contoso.net   HLB VIP의 IP 주소   192.168.10.5</p></li>
</ul>
<p>HTTP/HTTPS 트래픽을 제외한 모든 트래픽은 Pool01.contoso.net.record를 사용합니다. HTTP/HTTPS 트래픽은 정의된 내부 웹 서비스 주소인 192.168.10.5를 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p>DNS 부하 분산이 배포된 프런트 엔드 풀</p></td>
<td><p>풀의 FQDN을 풀에 있는 각 서버의 IP 주소로 확인하는 내부 A 레코드 집합. 풀에는 서버당 하나의 A 레코드가 포함될 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p>DNS 부하 분산이 배포된 프런트 엔드 풀</p></td>
<td><p>풀의 각 서버에 대한 FQDN을 해당 서버의 IP 주소로 확인하는 내부 A 레코드 집합. 자세한 내용은 계획 설명서에서 <a href="lync-server-2013-dns-load-balancing.md">Lync Server 2013의 DNS 부하 분산</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p>단일 프런트 엔드 서버와 전용 백 엔드 데이터베이스를 포함하지만 부하 분산 장치는 포함하지 않는 프런트 엔드 풀</p></td>
<td><p>프런트 엔드 풀의 FQDN을 단일 Enterprise Edition 프런트 엔드 서버의 IP 주소로 확인하는 내부 A 레코드</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>자동 클라이언트 로그인</p></td>
<td><p>지원되는 각 SIP 도메인에 대해 로그인을 위한 클라이언트 요청을 인증하고 리디렉션하는 프런트 엔드 풀의 FQDN에 매핑되는 _sipinternaltls._tcp.&lt;도메인&gt;(포트 5061)에 대한 SRV 레코드. 자세한 내용은 <a href="lync-server-2013-dns-requirements-for-automatic-client-sign-in.md">Lync Server 2013의 자동 클라이언트 로그인에 대한 DNS 요구 사항</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p>UC(통합 통신) 장치를 통한 장치 업데이트 웹 서비스 검색</p></td>
<td><p>장치 업데이트 웹 서비스를 호스트하는 프런트 엔드 풀의 IP 주소를 확인하는 ucupdates-r2.&lt;SIP 도메인&gt; 이름의 내부 A 레코드. UC 장치가 설정되었지만 사용자가 장치에 로그인하지 않은 상황에서 A 레코드를 사용하면 장치가 장치 업데이트 웹 서비스를 호스트하는 프런트 엔드 풀을 검색하고 업데이트를 가져올 수 있습니다. 그렇지 않으면 장치는 사용자가 처음 로그인할 때 인밴드 구축을 통해 이 정보를 가져옵니다.</p>


> [!IMPORTANT]
> Lync Server 2010에 기존 장치 업데이트 웹 서비스가 배포되어 있는 경우 이름이 ucupdates.<EM>&lt;SIP 도메인&gt;</EM>인 내부 A 레코드가 이미 만들어져 있습니다. Microsoft Office Communications Server 2007 R2의 경우 이름이 ucupdates-r2.<EM>&lt;SIP 도메인&gt;</EM>인 DNS A 레코드를 추가로 만들어야 합니다.


</td>
</tr>
<tr class="odd">
<td><p>HTTP 트래픽을 지원하는 역방향 프록시</p></td>
<td><p>외부 웹 팜 FQDN을 역방향 프록시의 외부 IP 주소로 확인하는 외부 A 레코드. 클라이언트와 UC 장치는 이 레코드를 사용하여 역방향 프록시에 연결합니다. 자세한 내용은 계획 설명서에서 <a href="lync-server-2013-determine-dns-requirements.md">Lync Server 2013에 대한 DNS 요구 사항 확인</a>을 참조하십시오.</p></td>
</tr>
</tbody>
</table>


다음 표에서는 내부 웹 팜 FQDN에 필요한 DNS 레코드의 예를 보여 줍니다.

### 내부 웹 팜 FQDN에 필요한 DNS 레코드의 예

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>내부 웹 팜 FQDN</th>
<th>풀 FQDN</th>
<th>DNS A 레코드</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>webcon.contoso.com</p></td>
<td><p>ee-pool.contoso.com</p></td>
<td><p>프런트 엔드 서버가 사용하는 부하 분산 장치의 VIP 주소로 확인되는 ee-pool.contoso.com에 대한 DNS A 레코드</p>
<p>프런트 엔드 서버가 사용하는 부하 분산 장치의 VIP 주소로 확인되는 webcon.contoso.com에 대한 DNS A 레코드</p></td>
</tr>
<tr class="even">
<td><p>ee-pool.contoso.com</p></td>
<td><p>ee-pool.contoso.com</p></td>
<td><p>프런트 엔드 풀에서 Enterprise Edition 프런트 엔드 서버가 사용하는 부하 분산 장치의 VIP(가상 IP) 주소로 확인되는 ee-pool.contoso.com에 대한 DNS A 레코드</p>
<p>이 풀에서 DNS 부하 분산을 사용하는 경우에는 프런트 엔드 풀과 내부 웹 팜의 FQDN이 동일할 수 없습니다.</p></td>
</tr>
</tbody>
</table>

