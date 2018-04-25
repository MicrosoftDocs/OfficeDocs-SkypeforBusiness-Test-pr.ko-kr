---
title: 'Lync Server 2013: DNS 요약 - 단일 디렉터'
TOCTitle: DNS 요약 - 단일 디렉터
ms:assetid: 790ecb56-92cd-41f4-baf6-c290a707aa4d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205021(v=OCS.15)
ms:contentKeyID: 49304113
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 DNS 요약 - 단일 디렉터

 

_**마지막으로 수정된 항목:** 2015-03-09_

다음 표에는 단일 디렉터를 지원하는 데 필요한 DNS 레코드에 대한 요약 정보가 포함되어 있습니다. 디렉터 역할을 사용하려면 프런트 엔드 서버와 비슷한 DNS 레코드가 필요합니다. 필요한 레코드 수는 디렉터 인증서에 필요한 주체 대체 이름에 반영됩니다. 프런트 엔드 서버와 달리 디렉터는 사용자 계정을 호스트하거나 Mobility Service를 호스트하지 않습니다.

### 디렉터에 필요한 DNS 레코드

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
<td><p>sip.contoso.com</p></td>
<td><p>디렉터</p></td>
<td><p>에지 서버의 내부 에지 인터페이스의 인바운드 SIP(Session Initiation Protocol)</p></td>
</tr>
<tr class="odd">
<td><p>내부 DNS/A</p></td>
<td><p>dialin.contoso.com</p></td>
<td><p>디렉터</p></td>
<td><p>역방향 프록시에서 게시된 전화 접속 웹 서비스</p></td>
</tr>
<tr class="even">
<td><p>내부 DNS/A</p></td>
<td><p>meet.contoso.com</p></td>
<td><p>디렉터</p></td>
<td><p>역방향 프록시에서 게시된 모임 웹 서비스</p></td>
</tr>
<tr class="odd">
<td><p>내부 DNS/A</p></td>
<td><p>webdirexternal.contoso.com</p></td>
<td><p>디렉터</p></td>
<td><p>디렉터에 대한 역방향 프록시 웹 티켓 외부 웹 서비스에서 게시 및 정의됨</p></td>
</tr>
</tbody>
</table>

