---
title: 'Lync Server 2013: 인증서 요약 - 조정된 통합 에지, 공용 IP 주소의 DNS 부하 분산'
TOCTitle: 인증서 요약 - 조정된 통합 에지, 공용 IP 주소의 DNS 부하 분산
ms:assetid: e87ac448-ee8f-477a-9f33-ce066c1bf093
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205399(v=OCS.15)
ms:contentKeyID: 49305383
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 인증서 요약 - 조정된 통합 에지, 공용 IP 주소의 DNS 부하 분산

 

_**마지막으로 수정된 항목:** 2015-03-09_

Microsoft Lync Server 2013에서는 인증서를 사용하여 다른 서버를 상호 인증하고 서버 간에 그리고 서버에서 클라이언트로 데이터를 암호화합니다. 서버와 연결된 DNS(Domain Name System) 레코드와 인증서 SN(주체 이름) 및 SAN(주체 대체 이름) 이름이 일치해야 합니다. 서버, DNS 레코드 및 인증서 항목을 성공적으로 매핑하려면 사용할 서버에 대해 인증서의 DNS, SN 및 SAN 항목에 등록되는 정규화된 도메인 이름을 신중히 계획해야 합니다.

공용 CA(인증 기관)에서는 에지 서버의 외부 인터페이스에 할당된 인증서를 요청합니다. Unified Communications용 인증서를 성공적으로 제공했음을 입증한 공용 CA는 <http://support.microsoft.com/kb/929395> 문서에 나열되어 있습니다. 인증서를 요청하는 경우 Lync Server 배포 마법사에서 생성된 인증서 요청을 사용하거나 요청을 직접 만들거나 공용 CA에서 제공하는 프로세스를 통해 만들 수 있습니다. 인증서를 할당하면 인증서가 액세스 에지 서비스 인터페이스, 웹 회의 에지 서비스 인터페이스 및 오디오/비디오 인증 서비스에 할당됩니다. 오디오 및 비디오 스트림을 암호화할 때 인증서를 사용하지 않는 A/V 에지 서비스와 오디오/비디오 인증 서비스를 혼동하면 안 됩니다. 내부 에지 서버 인터페이스는 (조직) 내부 CA의 인증서 또는 공용 CA의 인증서를 사용할 수 있습니다. 내부 인터페이스 인증서에서는 SN만 사용되므로 SAN 항목이 필요하지 않거나 사용되지 않습니다.


> [!NOTE]
> 다음 표에는 참고를 위해 주체 대체 이름에 두 번째 SIP 항목(sip.fabrikam.com)이 표시됩니다. 조직 내 각 SIP 도메인의 경우 인증서 주체 대체 이름 목록에 나열된 해당 FQDN을 추가해야 합니다.



## 공용 IP 주소를 사용한 DNS 부하 분산을 통해 확장된 통합 에지


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
<th>SAN(주체 대체 이름)/순서</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>확장된 통합 에지(외부 에지)</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>webcon.contoso.com</p>
<p>sip.contoso.com</p>
<p>sip.fabrikam.com</p></td>
<td><p>인증서는 공용 CA에서 발급받아야 하며, AOL과의 공용 IM 연결을 배포해야 하는 경우 서버 EKU와 클라이언트 EKU가 있어야 합니다. 또한 확장된 에지 서버의 경우 인증서 개인 키를 내보낼 수 있어야 하며 인증서와 개인 키를 각 에지 서버로 복사해야 합니다. 인증서는 다음에 대한 외부 에지 인터페이스에 지정됩니다.</p>
<ul>
<li><p>액세스 에지</p></li>
<li><p>회의 에지</p></li>
<li><p>A/V 에지</p></li>
</ul>
<p>토폴로지 작성기의 정의에 기반하여 SAN이 인증서에 자동으로 추가됩니다. 지원해야 할 추가 SIP 도메인과 다른 항목이 있는 경우 SAN 항목을 추가할 수 있습니다. 주체 이름이 SAN에 복제되며 올바른 작동을 위해서는 이 이름이 필요합니다.</p></td>
</tr>
<tr class="even">
<td><p>확장된 통합 에지(내부 에지)</p></td>
<td><p>lsedge.contoso.net</p></td>
<td><p>SAN 불필요</p></td>
<td><p>인증서는 공용 또는 개인 CA에서 발급받을 수 있으며, 서버 EKU를 포함해야 합니다. 인증서가 내부 에지 인터페이스에 할당됩니다.</p></td>
</tr>
</tbody>
</table>


## 인증서 요약 - 공용 인스턴트 메시징 연결


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
<th>SAN(주체 대체 이름)/순서</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>외부/액세스 에지</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>sip.contoso.com</p>
<p>webcon.contoso.com</p>
<p>sip.fabrikam.com</p></td>
<td><p>인증서는 공용 CA에서 발급받아야 하며, AOL과의 공용 IM 연결을 배포해야 하는 경우 서버 EKU와 클라이언트 EKU가 있어야 합니다. 다음 에지용 외부 에지 인터페이스에 인증서가 할당됩니다.</p>
<ul>
<li><p>액세스 에지</p></li>
<li><p>회의 에지</p></li>
<li><p>A/V 에지</p></li>
</ul>
<p>토폴로지 작성기의 정의에 기반하여 SAN이 인증서에 자동으로 추가됩니다. 지원해야 할 추가 SIP 도메인과 다른 항목이 있는 경우 SAN 항목을 추가할 수 있습니다. 주체 이름이 SAN에 복제되며 올바른 작동을 위해서는 이 이름이 필요합니다.</p></td>
</tr>
</tbody>
</table>


## XMPP(Extensible Messaging and Presence Protocol)의 인증서 요약


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
<th>SAN(주체 대체 이름)/순서</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>에지 서버 또는 에지 풀의 액세스 에지 서비스에 할당</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>webcon.contoso.com</p>
<p>sip.contoso.com</p>
<p>sip.fabrikam.com</p>
<p>xmpp.contoso.com</p>
<p><strong>*.contoso.com</strong></p></td>
<td><p>처음 세 개 SAN 항목은 전체 에지 서버을 위한 일반 SAN 항목입니다. contoso.com은 루트 도메인 수준에서 XMPP 파트너와의 페더레이션에 필요한 항목입니다. 이 항목은 *.contoso.com이라는 접두사가 붙은 도메인에 대해 XMPP를 허용합니다.</p></td>
</tr>
</tbody>
</table>

