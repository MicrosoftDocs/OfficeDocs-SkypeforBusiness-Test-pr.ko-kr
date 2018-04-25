---
title: 'Lync Server 2013: 내부 서버에 대한 인증서 요구 사항'
TOCTitle: 내부 서버에 대한 인증서 요구 사항
ms:assetid: 0444cdbd-538c-43b1-b9a1-9d7d6cf818d6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398094(v=OCS.15)
ms:contentKeyID: 49302656
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 내부 서버에 대한 인증서 요구 사항

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server를 실행하고 인증서가 필요한 내부 서버에는 Standard Edition 서버, Enterprise Edition 프런트 엔드 서버, 중재 서버 및 디렉터가 포함됩니다. 다음 표에서는 이러한 서버에 대한 인증서 요구 사항을 보여 줍니다. Lync Server 인증서 마법사를 사용하여 이러한 인증서를 요청할 수 있습니다.


> [!TIP]
> 와일드카드 인증서는 프런트 엔드 풀, 프런트 엔드 서버 또는 디렉터의 단순 URL과 연관된 주체 대체 이름에 대해 지원됩니다. 와일드카드 인증서 지원에 대한 자세한 내용은 <A href="lync-server-2013-wildcard-certificate-support.md">Lync Server 2013의 와일드카드 인증서 지원</A>을 참고하세요.



내부 서버에는 내부 엔터프라이즈 CA(인증 기관)를 사용하는 것이 좋지만 공용 CA를 사용할 수도 있습니다. UC(통합 통신) 인증서에 대한 특정 요구 사항을 준수하고 Microsoft와의 파트너 관계를 통해 Lync Server 인증서 마법사에서 작동하는 인증서를 제공하는 공용 CA 목록은 Microsoft 기술 자료 문서 929395, "Exchange Server 및 Communications Server에 대한 통합 통신 인증서 파트너"( [http://go.microsoft.com/fwlink/?linkid=202834\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=202834%26clcid=0x412))를 참고하세요.

Exchange 2013 등의 다른 응용 프로그램 및 서버와 통신하려면 다른 응용 프로그램 및 제품에 의해 지원되는 인증서가 필요합니다. 2013 릴리스의 경우 Lync Server 2013 및 기타 Microsoft 서버 제품( Exchange 2013 및 SharePoint Server 포함)은 서버 간 인증 및 권한 부여에 대해 OAuth(Open Authorization) 프로토콜을 지원합니다. 자세한 내용은 배포 설명서 또는 작업 설명서의 [Lync Server 2013에서 서버 간 인증(Oauth) 및 파트너 응용 프로그램 관리](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md)를 참고하세요.

Windows 7 운영 체제, Windows Server 2008 운영 체제, Windows Server 2008 R2 운영 체제, Windows Vista 운영 체제, Microsoft Lync Phone Edition을 실행하는 클라이언트의 연결에 대해 Lync Server 2013에는 SHA-256 암호화 해시 기능을 사용하여 서명한 인증서에 대한 지원이 포함되어 있습니다(반드시 지원해야 하는 것은 아님). SHA-256을 사용한 외부 액세스를 지원하기 위해 SHA-256을 사용하여 공용 CA에서 외부 인증서가 발급됩니다.

다음 표에서는 프런트 엔드 풀 및 Standard Edition 서버에 대한 서버 역할별 인증서 요구 사항을 보여 줍니다. 이는 모두 표준 웹 서버 인증서로서, 개인 키를 사용하고 내보낼 수 없습니다.

인증서 마법사를 사용하여 인증서를 요청하면 서버 EKU(확장된 키 사용)가 자동으로 구성됩니다.


> [!NOTE]
> 컴퓨터 저장소의 각 인증서 이름은 고유해야 합니다.




> [!NOTE]
> DNS에 sipinternal.contoso.com 또는 sipexternal.contoso.com을 구성한 경우 이를 인증서의 주체 대체 이름에 추가해야 합니다.



### Standard Edition 서버용 인증서

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>인증서</th>
<th>주체 이름/ 일반 이름</th>
<th>주체 대체 이름</th>
<th>예</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>기본값</p></td>
<td><p>풀의 FQDN(정규화된 도메인 이름)</p></td>
<td><p>풀의 FQDN 및 서버의 FQDN</p>
<p>SIP 도메인이 여러 개 있고 자동 클라이언트 구성을 활성화한 경우 인증서 마법사는 지원되는 각 SIP 도메인 FQDN을 검색하고 추가합니다.</p>
<p>이 풀이 클라이언트의 자동 로그온 서버이고 그룹 정책에 엄격한 DNS(Domain Name System) 일치가 필요한 경우에는 각 SIP 도메인에 sip.sipdomain에 대한 항목도 필요합니다.</p></td>
<td><p>SN=se01.contoso.com, SAN=se01.contoso.com</p>
<p>이 풀이 클라이언트의 자동 로그온 서버이고 그룹 정책에 엄격한 DNS 일치가 필요한 경우 SAN=sip.contoso.com, SAN=sip.fabrikam.com도 필요합니다.</p></td>
<td><p>Standard Edition 서버에서는 서버 FQDN이 풀 FQDN과 같습니다.</p>
<p>이 마법사는 설치 시 지정한 SIP 도메인을 검색한 다음 주체 대체 이름에 자동으로 추가합니다.</p>
<p>서버 간 인증에도 이 인증서를 사용할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p>웹 내부</p></td>
<td><p>서버의 FQDN</p></td>
<td><p>각각 다음과 같습니다.</p>
<ul>
<li><p>내부 웹 FQDN(서버의 FQDN과 같음)</p></li>
<li><p>모임 단순 URL</p></li>
<li><p>전화 접속 단순 URL</p></li>
<li><p>관리 단순 URL</p>
<p></p></li>
<li><p>또는 단순 URL에 대한 와일드카드 항목</p></li>
</ul>
<p></p></td>
<td><p>SN=se01.contoso.com, SAN=se01.contoso.com, SAN=meet.contoso.com, SAN=meet.fabrikam.com, SAN=dialin.contoso.com, SAN=admin.contoso.com</p>
<p>와일드카드 인증서 사용:</p>
<p>SN=se01.contoso.com; SAN=se01.contoso.com; SAN=*.contoso.com</p></td>
<td><p>토폴로지 작성기에서 내부 웹 FQDN을 덮어쓸 수 없습니다.</p>
<p>모임 단순 URL이 여러 개인 경우 모두 주체 대체 이름으로 포함해야 합니다.</p>
<p>와일드카드 항목은 단순 URL 항목에 대해 지원됩니다.</p></td>
</tr>
<tr class="odd">
<td><p>웹 외부</p></td>
<td><p>서버의 FQDN</p></td>
<td><p>각각 다음과 같습니다.</p>
<ul>
<li><p>외부 웹 FQDN</p></li>
<li><p>전화 접속 단순 URL</p></li>
<li><p>SIP 도메인에 대한 모임 단순 URL</p></li>
<li><p>또는 단순 URL에 대한 와일드카드 항목</p></li>
</ul></td>
<td><p>SN=se01.contoso.com, SAN=webcon01.contoso.com, SAN=meet.contoso.com, SAN=meet.fabrikam.com, SAN=dialin.contoso.com</p>
<p>와일드카드 인증서 사용:</p>
<p>SN=se01.contoso.com; SAN=webcon01.contoso.com; SAN=*.contoso.com</p></td>
<td><p>모임 단순 URL이 여러 개인 경우 모두 주체 대체 이름으로 포함해야 합니다.</p>
<p>와일드카드 항목은 단순 URL 항목에 대해 지원됩니다.</p></td>
</tr>
</tbody>
</table>


### 프런트 엔드 풀의 프런트 엔드 서버용 인증서

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>인증서</th>
<th>주체 이름/ 일반 이름</th>
<th>주체 대체 이름</th>
<th>예</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>기본값</p></td>
<td><p>풀의 FQDN</p></td>
<td><p>풀의 FQDN 및 서버의 FQDN</p>
<p>SIP 도메인이 여러 개 있고 자동 클라이언트 구성을 활성화한 경우 인증서 마법사는 지원되는 각 SIP 도메인 FQDN을 검색하고 추가합니다.</p>
<p>이 풀이 클라이언트의 자동 로그온 서버이고 그룹 정책에 엄격한 DNS 일치가 필요한 경우에는 각 SIP 도메인에 sip.sipdomain에 대한 항목도 필요합니다.</p></td>
<td><p>SN=eepool.contoso.com, SAN=eepool.contoso.com, SAN=ee01.contoso.com</p>
<p>이 풀이 클라이언트의 자동 로그온 서버이고 그룹 정책에 엄격한 DNS 일치가 필요한 경우 SAN=sip.contoso.com, SAN=sip.fabrikam.com도 필요합니다.</p></td>
<td><p>이 마법사는 설치 시 지정한 SIP 도메인을 검색한 다음 주체 대체 이름에 자동으로 추가합니다.</p>
<p>서버 간 인증에도 이 인증서를 사용할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p>웹 내부</p></td>
<td><p>풀의 FQDN</p></td>
<td><p>각각 다음과 같습니다.</p>
<ul>
<li><p>내부 웹 FQDN(서버의 FQDN과 다름)</p></li>
<li><p>서버 FQDN</p></li>
<li><p>Lync 풀 FQDN</p></li>
<li><p>모임 단순 URL</p></li>
<li><p>전화 접속 단순 URL</p></li>
<li><p>관리 단순 URL</p></li>
<li><p>또는 단순 URL에 대한 와일드카드 항목</p></li>
</ul>
<p></p></td>
<td><p>SN=ee01.contoso.com, SAN=ee01.contoso.com, SAN=meet.contoso.com, SAN=meet.fabrikam.com, SAN=dialin.contoso.com, SAN=admin.contoso.com</p>
<p>와일드카드 인증서 사용:</p>
<p>SN=ee01.contoso.com; SAN=ee01.contoso.com; SAN=*.contoso.com</p></td>
<td><p>모임 단순 URL이 여러 개인 경우 모두 주체 대체 이름으로 포함해야 합니다.</p>
<p>와일드카드 항목은 단순 URL 항목에 대해 지원됩니다.</p></td>
</tr>
<tr class="odd">
<td><p>웹 외부</p></td>
<td><p>풀의 FQDN</p></td>
<td><p>각각 다음과 같습니다.</p>
<ul>
<li><p>외부 웹 FQDN</p></li>
<li><p>전화 접속 단순 URL</p></li>
<li><p>관리 단순 URL</p></li>
<li><p>또는 단순 URL에 대한 와일드카드 항목</p></li>
</ul></td>
<td><p>SN=ee01.contoso.com, SAN=webcon01.contoso.com, SAN=meet.contoso.com, SAN=meet.fabrikam.com, SAN=dialin.contoso.com</p>
<p>와일드카드 인증서 사용:</p>
<p>SN=ee01.contoso.com; SAN=webcon01.contoso.com; SAN=*.contoso.com</p></td>
<td><p>모임 단순 URL이 여러 개인 경우 모두 주체 대체 이름으로 포함해야 합니다.</p>
<p>와일드카드 항목은 단순 URL 항목에 대해 지원됩니다.</p></td>
</tr>
</tbody>
</table>


### 디렉터용 인증서

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>인증서</th>
<th>주체 이름/ 일반 이름</th>
<th>주체 대체 이름</th>
<th>예</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>기본값</p></td>
<td><p>디렉터 풀의 FQDN</p></td>
<td><p>디렉터의 FQDN 및 디렉터 풀의 FQDN</p>
<p>이 풀이 클라이언트의 자동 로그온 서버이고 그룹 정책에 엄격한 DNS 일치가 필요한 경우에는 각 SIP 도메인에 sip.sipdomain에 대한 항목도 필요합니다.</p></td>
<td><p>SN=dir-pool.contoso.com, SAN=dir-pool.contoso.com, SAN=dir01.contoso.com</p>
<p>이 디렉터 풀이 클라이언트의 자동 로그온 서버이고 그룹 정책에 엄격한 DNS 일치가 필요한 경우 SAN=sip.contoso.com, SAN=sip.fabrikam.com도 필요합니다.</p></td>
</tr>
<tr class="even">
<td><p>웹 내부</p></td>
<td><p>서버의 FQDN</p></td>
<td><p>각각 다음과 같습니다.</p>
<ul>
<li><p>내부 웹 FQDN(서버의 FQDN과 같음)</p></li>
<li><p>모임 단순 URL</p></li>
<li><p>전화 접속 단순 URL</p></li>
<li><p>관리 단순 URL</p></li>
<li><p>또는 단순 URL에 대한 와일드카드 항목</p></li>
</ul>
<p></p></td>
<td><p>SN=dir01.contoso.com, SAN=dir01.contoso.com, SAN=meet.contoso.com, SAN=meet.fabrikam.com, SAN=dialin.contoso.com, SAN=admin.contoso.com</p>
<p>SN=dir01.contoso.com; SAN=dir01.contoso.com SAN=*.contoso.com</p></td>
</tr>
<tr class="odd">
<td><p>웹 외부</p></td>
<td><p>서버의 FQDN</p></td>
<td><p>각각 다음과 같습니다.</p>
<ul>
<li><p>외부 웹 FQDN</p></li>
<li><p>전화 접속 단순 URL</p></li>
<li><p>관리 단순 URL</p></li>
<li><p>또는 단순 URL에 대한 와일드카드 항목</p></li>
</ul></td>
<td><p>디렉터 외부 웹 FQDN은 프런트 엔드 풀 또는 프런트 엔드 서버와 달라야 합니다.</p>
<p>SN=dir01.contoso.com; SAN=directorwebcon01.contoso.com SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com</p>
<p>SN=dir01.contoso.com; SAN=directorwebcon01.contoso.com SAN=*.contoso.com</p></td>
</tr>
</tbody>
</table>


독립 실행형 중재 서버 풀이 있는 경우 풀의 각 중재 서버에 다음 표에 나열된 인증서가 필요합니다. 중재 서버를 프런트 엔드 서버와 함께 배치한 경우에는 이 항목의 앞부분에서 설명한 "프런트 엔드 풀의 프런트 엔드 서버용 인증서" 표만으로 충분합니다.

### 독립 실행형 중재 서버용 인증서

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>인증서</th>
<th>주체 이름/ 일반 이름</th>
<th>주체 대체 이름</th>
<th>예</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>기본값</p></td>
<td><p>풀의 FQDN</p></td>
<td><p>풀의 FQDN</p>
<p>풀 구성원 서버의 FQDN</p></td>
<td><p>SN=medsvr-pool.contoso.net; SAN=medsvr-pool.contoso.net; SAN=medsvr01.contoso.net</p></td>
</tr>
</tbody>
</table>


### SBA(Survivable Branch Appliance)용 인증서

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>인증서</th>
<th>주체 이름/ 일반 이름</th>
<th>주체 대체 이름</th>
<th>예</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>기본값</p></td>
<td><p>SBA의 FQDN</p></td>
<td><p>SIP.&lt;SIP 도메인&gt;(SIP 도메인당 하나의 항목 필요)</p></td>
<td><p>SN=sba01.contoso.net, SAN=sip.contoso.com, SAN=sip.fabrikam.com</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 개념

[Lync Server 2013의 와일드카드 인증서 지원](lync-server-2013-wildcard-certificate-support.md)

