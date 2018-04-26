---
title: 'Lync Server 2013: 프런트 엔드 풀에 대한 DNS 요구 사항'
TOCTitle: 프런트 엔드 풀에 대한 DNS 요구 사항
ms:assetid: 02d2aa6b-9e01-437b-a2df-00590280150d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398082(v=OCS.15)
ms:contentKeyID: 49302633
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 프런트 엔드 풀에 대한 DNS 요구 사항

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 절차를 성공적으로 완료하려면 서버 또는 도메인에 최소한 Domain Admins 그룹의 구성원 또는 DnsAdmins 그룹의 구성원으로 로그온해야 합니다.

토폴로지 작성기에 토폴로지를 게시하기 전에 필요한 DNS(Domain Name System) 레코드를 구성해야 합니다. 또한 Lync Server 2013 배포의 구성에 사용된 일부 FQDN(정규화된 도메인 이름)은 실제 서버 FQDN이 아니라 논리 서버 FQDN이므로 게시하기 전에 추가 DNS 구성이 필요합니다.


> [!WARNING]
> Lync Server 2013은 단일 레이블 도메인을 지원하지 않습니다. 예를 들어 <STRONG>contoso.local</STRONG>이라는 루트 도메인으로 구성된 포리스트는 지원되지만 <STRONG>local</STRONG>이라는 루트 도메인은 지원되지 않습니다. 자세한 내용은 Microsoft 기술 자료 문서 300684, "단일 레이블 DNS 이름이 지정된 도메인에 대해 Windows를 구성하는 방법에 대한 정보"(<A class=uri href="http://support.microsoft.com/kb/300684/ko-kr">http://support.microsoft.com/kb/300684/ko-kr</A>)를 참조하십시오.




> [!IMPORTANT]
> 지정하는 이름은 서버에 구성된 컴퓨터 이름과 동일해야 합니다. 기본적으로 도메인에 가입되지 않은 컴퓨터의 컴퓨터 이름은 FQDN이 아닌 짧은 이름입니다. 토폴로지 작성기에서는 짧은 이름이 아닌 FQDN을 사용합니다. Lync Server, 에지 서버 및 풀을 실행하는 서버의 FQDN을 할당할 때는 <STRONG>표준 문자</STRONG>(A-Z, a-z, 0-9 및 하이픈 포함)만 사용하십시오. 유니코드 문자나 밑줄은 사용하지 마십시오. FQDN의 비표준 문자는 외부 DNS 및 공용 CA(인증 기관)에서 지원되지 않는 경우가 많습니다(인증서의 SN에 FQDN을 할당해야 하는 경우).



토폴로지를 배포한 후 작동하기 전에 특정 기능에 대한 요구 사항에 따라 다음 Active Directory 및 DNS 레코드가 만들어졌는지 확인합니다.

  - 토폴로지에 있는 각 서버 역할은 Active Directory 개체로 게시됩니다(컴퓨터를 도메인에 가입시키면 됨).

  - 각 서버에 대한 DNS A 레코드가 있어야 합니다.

  - 클라이언트에 대해 자동 로그온을 사용하려면 각 SIP 도메인에 대해 \_sipinternaltls\_tcp *\<SIP 도메인\>* 형식의 DNS SRV 레코드가 있어야 합니다. 클라이언트에 대해 수동 구성을 사용하려는 경우에는 이 레코드가 필요하지 않습니다.

  - 구성된 각 단순 URL(모임 및 전화 접속)에 대한 DNS A 레코드가 있어야 합니다(일반적으로 meet, dialin, lwa, scheduler의 4가지). 또한 Lync Server 2013 제어판에 액세스하기 위한 특수 URL인 관리 단순 URL이 있어야 합니다.

  - SQL Server를 실행 중인 서버가 도메인에 가입되어 있어야 하며 토폴로지 작성기가 게시를 수행하는 컴퓨터에서 연결할 수 있어야 합니다.

아래 표는 계획 섹션에 설명된 참조 아키텍처를 따릅니다. 자세한 내용은 계획 설명서에서 [Lync Server 2013의 외부 사용자 액세스에 대한 시나리오](lync-server-2013-scenarios-for-external-user-access.md)를 참조하십시오.

### 프런트 엔드 풀에 필요한 DNS 레코드

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>위치</th>
<th>유형</th>
<th>FQDN</th>
<th>매핑 대상/설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>내부 DNS</p></td>
<td><p>A</p></td>
<td><p>pool01.contoso.net</p></td>
<td><p>Pool01(DNS 부하 분산). 풀 내에 있는 각 프런트 엔드 서버의 IP 주소에 대한 DNS A 레코드가 필요합니다(풀 FQDN에 매핑됨).</p></td>
</tr>
<tr class="even">
<td><p>내부 DNS</p></td>
<td><p>A</p></td>
<td><p>pool01.contoso.net</p></td>
<td><p>Pool01(하드웨어 부하 분산 장치의 VIP(가상 IP))</p></td>
</tr>
<tr class="odd">
<td><p>내부 DNS</p></td>
<td><p>A</p></td>
<td><p>fe01.contoso.net</p>
<p>fe02.contoso.net</p>
<p>fe03.contoso.net</p>
<p>…</p></td>
<td><p>Pool01 프런트 엔드 서버(노드 1)</p>
<p>Pool01 프런트 엔드 서버(노드 2)</p>
<p>Pool01 프런트 엔드 서버(노드 3)</p>
<p>…</p></td>
</tr>
<tr class="even">
<td><p>내부 DNS</p></td>
<td><p>A</p></td>
<td><p>fe02.contoso.net</p></td>
<td><p>Pool01 프런트 엔드 서버(노드 2)</p></td>
</tr>
<tr class="odd">
<td><p>내부 DNS</p></td>
<td><p>A</p></td>
<td><p>lsweb.contoso.net</p></td>
<td><p>클라이언트-서버 웹 트래픽용 Pool01(VIP)</p></td>
</tr>
<tr class="even">
<td><p>내부 DNS</p></td>
<td><p>A</p></td>
<td><p>sqlbe.contoso.net</p></td>
<td><p>SQL Server 2008 R2를 실행하는 Pool01 백 엔드 서버</p></td>
</tr>
<tr class="odd">
<td><p>내부 DNS</p></td>
<td><p>A</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Lync Phone Edition 또는 DNS SRV 레코드 없는 클라이언트 자동 로그온 및 엄격한 도메인 일치에 필요합니다. 모든 경우에 반드시 필요한 것은 아닙니다.</p></td>
</tr>
<tr class="even">
<td><p>내부 DNS</p></td>
<td><p>A</p></td>
<td><p>sip.fabrikam.com</p></td>
<td><p>두 번째 SIP 도메인을 가정합니다. Lync Phone Edition, DNS SRV 레코드 없는 클라이언트 자동 로그온 및 엄격한 도메인 일치에 필요합니다. 모든 경우에 반드시 필요한 것은 아닙니다.</p></td>
</tr>
<tr class="odd">
<td><p>내부 DNS</p></td>
<td><p>A</p></td>
<td><p>dialin.contoso.com</p></td>
<td><p>내부적으로 게시된 전화 접속 회의용 단순 URL - 프런트 엔드 서버 또는 디렉터(설치된 경우)가 단순 URL 쿼리에 응답</p></td>
</tr>
<tr class="even">
<td><p>내부 DNS</p></td>
<td><p>A</p></td>
<td><p>meet.contoso.com</p></td>
<td><p>내부적으로 게시된 전화 회의용 단순 URL - 프런트 엔드 서버 또는 디렉터(설치된 경우)가 단순 URL 쿼리에 응답</p></td>
</tr>
<tr class="odd">
<td><p>내부 DNS</p></td>
<td><p>A</p></td>
<td><p>admin.contoso.com</p>
<p>관리</p></td>
<td><p>선택적 레코드, 내부적으로 게시된 Lync Server 2013 제어판용 단순 URL - 프런트 엔드 서버 또는 디렉터(설치된 경우)가 단순 URL 쿼리에 응답. 도메인 이름 없이 호스트 이름만 사용하는 것이 좋습니다.</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> VIP = 하드웨어 부하 분산 장치의 가상 IP 주소



## 프런트 엔드 풀용 DNS SRV 레코드


<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>위치</th>
<th>유형</th>
<th>FQDN</th>
<th>대상 FQDN</th>
<th>포트</th>
<th>매핑 대상/설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>내부 DNS</p></td>
<td><p>SRV</p></td>
<td><p>_sipinternaltls._tcp.contoso.com</p></td>
<td><p>pool01.contoso.com</p></td>
<td><p>5061</p></td>
<td><p>Lync 2013 클라이언트의 자동 구성이 내부적으로 작동하는 데 필요</p></td>
</tr>
<tr class="even">
<td><p>내부 DNS</p></td>
<td><p>SRV</p></td>
<td><p>_sipinternaltls._tcp.fabrikam.com</p></td>
<td><p>pool01.fabrikam.com</p></td>
<td><p>5061</p></td>
<td><p>Lync 2013 클라이언트의 자동 구성이 내부적으로 작동하는 데 필요</p></td>
</tr>
<tr class="odd">
<td><p>내부 DNS</p></td>
<td><p>SRV</p></td>
<td><p>_ntp._udp.contoso.com</p></td>
<td><p>dc01.contoso.com</p></td>
<td><p>123</p></td>
<td><p>Lync Phone Edition을 실행하는 장치에 필요한 NTP(Network Time Protocol) 원본. 내부적으로 도메인 컨트롤러를 가리켜야 합니다. 도메인 컨트롤러가 정의되어 있지 않은 경우에는 NTP 서버 time.windows.com을 사용합니다.</p></td>
</tr>
</tbody>
</table>

