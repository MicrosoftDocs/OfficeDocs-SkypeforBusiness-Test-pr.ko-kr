---
title: 'Lync Server 2013: DNS 요약 - DNS 및 HLB 부하 분산됨'
TOCTitle: DNS 요약 - DNS 및 HLB 부하 분산됨
ms:assetid: d2132695-1956-4190-a98e-cd7255cbded6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205273(v=OCS.15)
ms:contentKeyID: 49305111
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 DNS 요약 - DNS 및 HLB 부하 분산됨

 

_**마지막으로 수정된 항목:** 2015-03-09_

다음 표에는 DNS 부하 분산 및 하드웨어 부하 분산 디렉터를 지원하는 데 필요한 DNS 레코드가 요약되어 있습니다. 디렉터의 역할에는 프런트 엔드 서버와 유사한 DNS 레코드가 필요합니다. 필요한 레코드 수는 디렉터 인증서에 필요한 주체 대체 이름에 반영되어 있습니다. 프런트 엔드 서버와의 차이점은 디렉터 풀의 경우 사용자 계정이나 Mobility Service를 호스트하지 않는다는 것입니다.

### DNS 부하 분산 및 하드웨어 부하 분산 장치를 사용하는 디렉터 풀에 필요한 DNS 레코드

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
<td><p>내부 DNS/A</p></td>
<td><p>dir01.contoso.net</p></td>
<td><p>디렉터</p></td>
<td><p>서버 간의 복제에 사용되는 디렉터 호스트 레코드</p></td>
</tr>
<tr class="even">
<td><p>내부 DNS/A</p></td>
<td><p>dirpool01.contoso.net</p></td>
<td><p>디렉터 풀</p></td>
<td><p>서버 간 DNS 부하 분산 디렉터 풀에 대한 호스트 레코드</p></td>
</tr>
<tr class="odd">
<td><p>내부 DNS/A</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>디렉터 풀</p></td>
<td><p>에지 서버 내부 인터페이스의 인바운드 SIP(Session Initiation Protocol)</p></td>
</tr>
<tr class="even">
<td><p>내부 DNS/A</p></td>
<td><p>dialin.contoso.com</p></td>
<td><p>디렉터 풀 HLB VIP</p></td>
<td><p>역방향 프록시의 하드웨어 부하 분산되어 게시된 전화 접속 웹 서비스</p></td>
</tr>
<tr class="odd">
<td><p>내부 DNS/A</p></td>
<td><p>meet.contoso.com</p></td>
<td><p>디렉터 풀 HLB VIP</p></td>
<td><p>역방향 프록시에서 게시된 하드웨어 부하 분산 모임 웹 서비스</p></td>
</tr>
<tr class="even">
<td><p>내부 DNS/A</p></td>
<td><p>webdirexternal.contoso.com</p></td>
<td><p>디렉터 풀 HLB VIP</p></td>
<td><p>역방향 프록시에서 게시 및 정의된 디렉터 풀용 하드웨어 부하 분산 웹 티켓 외부 웹 서비스</p></td>
</tr>
</tbody>
</table>

