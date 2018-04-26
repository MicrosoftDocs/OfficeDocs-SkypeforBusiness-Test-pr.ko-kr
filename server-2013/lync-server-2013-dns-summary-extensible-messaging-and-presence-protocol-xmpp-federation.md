---
title: DNS 요약 - XMPP(Extensible Messaging and Presence Protocol) 페더레이션
TOCTitle: DNS 요약 - XMPP(Extensible Messaging and Presence Protocol) 페더레이션
ms:assetid: 0f720a2a-8ab5-43cc-882a-ab595ed3cec7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ618368(v=OCS.15)
ms:contentKeyID: 49302827
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# DNS 요약 - XMPP(Extensible Messaging and Presence Protocol) 페더레이션

 

_**마지막으로 수정된 항목:** 2015-03-09_

배포에 대해 XMPP(Extensible Messaging and Presence Protocol)를 구성하려면 레코드를 에지 서버 또는 에지 풀의 액세스 에지 서비스로 확인하는 외부 DNS(Domain Name System) 서버의 DNS 레코드 두 개를 만듭니다.

## Extensible Messaging and Presence Protocol에 대한 DNS 요약


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
<td><p>액세스 에지 서비스 또는 에지 풀의 XMPP 프록시 외부 인터페이스입니다. 글로벌 정책, 사용자가 있는 사이트에 대한 사이트 정책 또는 Lync 사용 가능 사용자에게 적용되는 사용자 정책을 통해 외부 액세스 정책을 구성함으로써 XMPP 연락처와의 연결이 허용되는 모든 내부 SIP 도메인(Lync 사용 가능 사용자 포함)에 대해 필요한 만큼 반복합니다. 허용되는 XMPP 도메인은 XMPP 페더레이션 파트너 정책에서도 구성해야 합니다. 자세한 내용은 <strong>참고 항목</strong>의 항목을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p>외부 DNS/A</p></td>
<td><p>xmpp.contoso.com(예)</p></td>
<td><p>XMPP 프록시를 호스트하는 에지 서버 또는 에지 풀의 액세스 에지 서비스 IP 주소</p></td>
<td><p>XMPP 프록시 서비스를 호스트하는 액세스 에지 서비스 또는 에지 풀을 가리킵니다. 일반적으로 사용자가 만드는 SRV 레코드는 이 호스트(A 또는 AAAA) 레코드를 가리킵니다.</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 작업

[Lync Server 2013에서 XMPP 페더레이션 설정](lync-server-2013-setting-up-xmpp-federation.md)  

#### 개념

[Lync Server 2013에 대한 DNS 요구 사항 확인](lync-server-2013-determine-dns-requirements.md)

