---
title: Lync Server 2013의 자동 클라이언트 로그인에 대한 DNS 요구 사항
TOCTitle: Lync Server 2013의 자동 클라이언트 로그인에 대한 DNS 요구 사항
ms:assetid: 3bcd4bb3-a022-4ffa-b005-1a95ad2b1796
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425884(v=OCS.15)
ms:contentKeyID: 49303367
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 자동 클라이언트 로그인에 대한 DNS 요구 사항

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 섹션에서는 자동 클라이언트 로그인에 필요한 DNS(Domain Name System) 레코드에 대해 설명합니다. Standard Edition 서버 또는 프런트 엔드 풀을 배포할 때는 클라이언트가 자동 검색을 사용하여 적절한 Standard Edition 서버 또는 프런트 엔드 풀에 로그인하도록 구성할 수 있습니다. 클라이언트에서 Lync Server 2013에 수동으로 연결하도록 하려면 이 항목을 건너뛸 수 있습니다.

자동 클라이언트 로그인을 지원하려면 다음을 수행해야 합니다.

  - 클라이언트 로그인 요청을 분산시키고 인증하는 단일 서버 또는 풀을 지정합니다. 사용자를 호스팅하는 조직 내의 기존 서버나 풀일 수도 있고, 이 목적을 위해 어떤 사용자도 호스팅하고 있지 않은 전용 서버나 풀을 지정할 수도 있습니다. 고가용성을 위해서는 이 기능에 프런트 엔드 풀을 지정하는 것이 좋습니다.

  - 이 서버 또는 풀에 대한 자동 클라이언트 로그인을 지원하는 내부 DNS SRV 레코드를 만듭니다.
    

    > [!NOTE]
    > 다음의 레코드 요구 사항에서 SIP 도메인은 사용자에게 할당된 SIP URI의 호스트 부분을 나타냅니다. 예를 들어 SIP URI의 형식이 *@contoso.com인 경우에는 contoso.com이 SIP 도메인입니다. SIP 도메인은 대개 내부 Active Directory 도메인과 다릅니다. 조직에서 여러 SIP 도메인을 지원할 수도 있습니다.



클라이언트에 대해 자동 구성을 사용하려면 Lync 클라이언트의 로그인 요청을 분산시키는 프런트 엔드 풀 또는 Standard Edition 서버의 FQDN(정규화된 도메인 이름)에 다음 레코드 중 하나를 매핑하는 내부 DNS SRV 레코드를 만들어야 합니다.

  - \_sipinternaltls.\_tcp.*\<도메인\>* - 내부 TLS 연결용

로그인 요청을 분산할 프런트 엔드 풀 또는 Standard Edition 서버에 대해 하나의 SRV 레코드만 만들면 됩니다.

다음 표에서는 contoso.com 및 retail.contoso.com이라는 SIP 도메인을 지원하는 Contoso라는 가상 회사에 필요한 일부 예제 레코드를 보여 줍니다.

### SIP 도메인이 여러 개인 자동 클라이언트 로그인에 필요한 DNS 레코드의 예

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>로그인 요청을 분산하는 데 사용되는 프런트 엔드 풀의 FQDN</th>
<th>SIP 도메인</th>
<th>DNS SRV 레코드</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>pool01.contoso.com</p></td>
<td><p>contoso.com</p></td>
<td><p>pool01.contoso.com에 매핑되는 _sipinternaltls._tcp.contoso.com 도메인(포트 5061)에 대한 SRV 레코드</p></td>
</tr>
<tr class="even">
<td><p>pool01.contoso.com</p></td>
<td><p>retail.contoso.com</p></td>
<td><p>pool01.contoso.com에 매핑되는 _sipinternaltls._tcp.retail.contoso.com 도메인(포트 5061)에 대한 SRV 레코드</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> 기본적으로 DNS 레코드에 대한 쿼리는 SRV 레코드 및 사용자 이름에 있는 도메인 간의 엄격한 도메인 이름 일치를 따릅니다. 접미사 일치를 대신 사용하도록 클라이언트 DNS 쿼리를 설정하려면 DisableStrictDNSNaming 그룹 정책을 구성하면 됩니다. 자세한 내용은 계획 설명서에서 <A href="lync-server-2013-planning-for-clients-and-devices.md">Lync Server 2013에서 클라이언트 및 장치 계획</A>을 참조하십시오.



## 자동 클라이언트 로그인에 필요한 인증서 및 DNS 레코드의 예

이 예에서는 앞의 표에 있는 것과 같은 예제 이름을 사용합니다. Contoso 조직은 contoso.com 및 retail.contoso.com이라는 SIP 도메인을 지원하고 이 조직의 모든 사용자는 다음 중 한 형태의 SIP URI를 갖게 됩니다.

  - *\<사용자\>*@retail.contoso.com

  - *\<사용자\>*@contoso.com

