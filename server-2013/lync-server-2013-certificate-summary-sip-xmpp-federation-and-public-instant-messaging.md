---
title: 인증서 요약 - SIP, XMPP 페더레이션 및 공용 IM
TOCTitle: 인증서 요약 - SIP, XMPP 페더레이션 및 공용 IM
ms:assetid: 933d6351-cfa6-4432-b3ed-1aff3ac92065
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ618372(v=OCS.15)
ms:contentKeyID: 49304401
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 인증서 요약 - SIP, XMPP 페더레이션 및 공용 IM

 

_**마지막으로 수정된 항목:** 2015-03-09_

일반적으로 Microsoft Lync Server 2013, Lync Server 2010 및 Office Communications Server와 페더레이션에 필요한 인증서는 사용자가 구성 및 요청하여 에지 서버에 할당하는 인증서로 충족될 수 있습니다.

XMPP(Extensible Messaging and Presence Protocol) 파트너와 통신을 설정하고 연결하기 위한 인증서 요구 사항에 따라 XMPP 도메인에 대한 항목을 추가해야 합니다. SAN(주체 대체 이름)으로 인증서에 포함되는 레코드는 XMPP 통신에 참여할 수 있는 도메인이 됩니다. 이 도메인은 전체 도메인에 XMPP를 사용하도록 설정하려는 경우 루트 수준 도메인(예: contoso.com)이 될 수 있고, 일부 사용자에 대해 XMPP를 사용하도록 설정하는 경우 선택한 자식 도메인(예: corp.contoso.com, finance.contoso.com)이 될 수 있습니다.

공용 IM 연결을 위한 인증서를 구성하려면 이러한 인증서가 다른 SIP 페더레이션 유형 또는 표준 에지 서버 인증서와 다르지 않다는 점에 유의해야 합니다. 단, AOL(America Online)의 경우 클라이언트 EKU(확장된 키 사용)도 포함하려면 인증서(에지 풀의 경우)가 필요합니다. 클라이언트 EKU가 인증서에 추가되면 에지 서버에 할당되는 외부 공용 인증서의 일부가 됩니다.

에지 서버 배포에 대한 올바른 인증서 요구 사항을 충족했는지 확인하려면 **참고 항목** 섹션에 있는 항목을 검토하세요.



<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>구성 요소</th>
<th>주체 이름</th>
<th>SAN(주체 대체 이름)</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>외부/액세스 에지</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>sip.contoso.com</p>
<p>webcon.contoso.com</p>
<p>contoso.com</p>


> [!NOTE]
> contoso.com XMPP 네임스페이스 지원



<p>sip.fabrikam.com</p>


> [!NOTE]
> fabrikam.com SIP 네임스페이스 지원



<p>fabrikam.com</p>


> [!NOTE]
> fabrikam.com XMPP 네임스페이스 지원


</td>
<td><p>인증서는 공용 CA에서 발급한 것이어야 하며, AOL을 사용하여 공용 IM 연결을 배포하려는 경우 서버 EKU 및 클라이언트 EKU가 있어야 합니다. 다음 항목에 대한 외부 에지 서버 인터페이스에 인증서가 할당됩니다.</p>
<ul>
<li><p>액세스 에지 서비스</p></li>
<li><p>웹 회의 에지 서비스</p></li>
<li><p>A/V 에지 서비스</p></li>
</ul>


> [!NOTE]
> 기술적으로 인증서는 A/V 에지에 할당되지 않습니다. 보안 통신과 인증은 MRAS(미디어 릴레이 인증 서비스)를 통해 관리됩니다. MRAS는 에지 서버 내부 인터페이스에 할당된 인증서를 사용합니다.



<p>토폴로지 작성기의 정의에 기반하여 SAN이 인증서에 자동으로 추가됩니다. 지원해야 할 추가 SIP 도메인과 다른 항목이 있는 경우 SAN 항목을 추가할 수 있습니다. 주체 이름이 SAN에 복제되며 올바른 작동을 위해서는 이 이름이 필요합니다.</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 작업

[Lync Server 2013의 예제 XMPP 구성 - Google Talk와 XMPP 페더레이션](lync-server-2013-example-xmpp-configuration-–-xmpp-federation-with-google-talk.md)  

#### 개념

[Lync Server 2013의 에지 서버 인증서 계획](lync-server-2013-plan-for-edge-server-certificates.md)  
[인증서 요약 - Lync Server 2013의 NAT 사용 개인 IP 주소의 단일 통합 에지](lync-server-2013-certificate-summary-single-consolidated-edge-with-private-ip-addresses-using-nat.md)  
[Lync Server 2013의 인증서 요약 - 공용 IP 주소의 단일 통합 에지](lync-server-2013-certificate-summary-single-consolidated-edge-with-public-ip-addresses.md)  
[Lync Server 2013의 인증서 요약 - 조정된 통합 에지, NAT 사용 개인 IP 주소의 DNS 부하 분산](lync-server-2013-certificate-summary-scaled-consolidated-edge-dns-load-balancing-with-private-ip-addresses-using-nat.md)  
[Lync Server 2013의 인증서 요약 - 조정된 통합 에지, 공용 IP 주소의 DNS 부하 분산](lync-server-2013-certificate-summary-scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md)  
[Lync Server 2013의 인증서 요약 - 하드웨어 부하 분산 장치를 사용하는 조정된 통합 에지](lync-server-2013-certificate-summary-scaled-consolidated-edge-with-hardware-load-balancers.md)

