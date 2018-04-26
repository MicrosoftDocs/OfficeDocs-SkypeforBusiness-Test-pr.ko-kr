---
title: DNS 요약 - Lync Server 2013에서 자동 검색
TOCTitle: DNS 요약 - Lync Server 2013에서 자동 검색
ms:assetid: b336a2ae-0e58-4b74-b606-aedbbd411587
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945644(v=OCS.15)
ms:contentKeyID: 52056922
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# DNS 요약 - Lync Server 2013에서 자동 검색

 

_**마지막으로 수정된 항목:** 2015-03-09_

자동 검색은 HTTP 또는 HTTPS를 통한 통신을 수락하는 유동적인 서비스입니다. 이러한 방식을 사용하려면 자동 검색 서비스를 호스트하는 서버에서 사용하는 DNS(Domain Name System) 및 인증서를 올바르게 구성해야 합니다. 인증서 요구 사항은 [인증서 요약 - 자동 검색](lync-server-2013-certificate-summary-autodiscover.md)에 나와 있습니다.


> [!IMPORTANT]
> Lync Server 클라이언트의 DNS 조회 논리에서는 특정 확인 순서를 사용합니다. DNS에는 항상 lyncdiscoverinternal.&lt;도메인&gt; 및 lyncdiscover.&lt;도메인&gt;을 모두 포함해야 합니다. lyncdiscoverinternal.&lt;도메인&gt; 레코드를 제외하면 내부 클라이언트가 의도한 서비스에 연결하지 못하거나 잘못된 자동 검색 응답을 받게 됩니다.



### 내부 DNS 레코드

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>레코드 유형</th>
<th>호스트 이름</th>
<th>확인 대상</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CNAME</p></td>
<td><p>Lyncdiscoverinternal.<em>&lt;내부 도메인 이름&gt;</em></p></td>
<td><p>디렉터 풀의 내부 웹 서비스 FQDN(있는 경우) 또는 프런트 엔드 풀(디렉터가 없는 경우)</p></td>
</tr>
<tr class="even">
<td><p>A(호스트, IPv6의 경우 AAAA)</p></td>
<td><p>lyncdiscoverinternal.<em>&lt;내부 도메인 이름&gt;</em></p></td>
<td><p>디렉터 풀의 내부 웹 서비스 IP 주소(부하 분산 장치를 사용하는 경우 VIP(가상 IP) 주소)(있는 경우) 또는 프런트 엔드 풀(디렉터가 없는 경우)</p></td>
</tr>
</tbody>
</table>


다음 외부 DNS 레코드 중 하나를 만들어야 합니다.

### 외부 DNS 레코드

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>레코드 유형</th>
<th>호스트 이름</th>
<th>확인 대상</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CNAME</p></td>
<td><p>lyncdiscover.<em>&lt;SIP 도메인&gt;</em></p></td>
<td><p>디렉터 풀의 외부 웹 서비스 FQDN(있는 경우) 또는 프런트 엔드 풀(디렉터가 없는 경우)</p></td>
</tr>
<tr class="even">
<td><p>A(호스트, IPv6의 경우 AAAA)</p></td>
<td><p>lyncdiscover.<em>&lt;SIP 도메인&gt;</em></p></td>
<td><p>역방향 프록시의 외부(공용) IP 주소</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> 외부 트래픽은 역방향 프록시를 통과합니다.




> [!NOTE]
> 모바일 장치는 서로 다른 도메인에서 여러 SSL(Secure Sockets Layer) 인증서를 지원할 수 없습니다. 따라서 HTTPS를 통해서는 다른 도메인으로의 CNAME 리디렉션이 지원되지 않습니다. 예를 들어 director.contoso.net 주소로 리디렉션되는 lyncdiscover.contoso.com의 DNS CNAME 레코드는 HTTPS에서 지원되지 않습니다. 이러한 토폴로지에서는 HTTP를 통해 CNAME 리디렉션이 확인되도록 모바일 장치 클라이언트가 첫 번째 요청에 대해 HTTP를 사용해야 합니다. 후속 요청에서는 HTTPS를 사용합니다. 이 시나리오를 지원하려면 포트 80(HTTP)에 대한 웹 게시 규칙을 사용하여 역방향 프록시를 구성해야 합니다. 자세한 내용은 <A href="lync-server-2013-configuring-the-reverse-proxy-for-mobility.md">Lync Server 2013에서 모바일 기능에 대해 역방향 프록시 구성</A>에서 "포트 80에 대해 웹 게시 규칙을 만들려면"을 참조하십시오. 동일한 도메인으로의 CNAME 리디렉션은 HTTPS를 통해 지원됩니다. 이 경우 대상 도메인의 인증서에 원래 도메인이 포함됩니다.



## 참고 항목

#### 작업

[Lync Server 2013에서 모바일 기능에 대해 역방향 프록시 구성](lync-server-2013-configuring-the-reverse-proxy-for-mobility.md)  

#### 개념

[인증서 요약 - 자동 검색](lync-server-2013-certificate-summary-autodiscover.md)

