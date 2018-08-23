---
title: 모바일 기능에 대한 DNS 요구 사항
TOCTitle: 모바일 기능에 대한 DNS 요구 사항
ms:assetid: df6962bc-2a16-440e-a333-022ebd14f957
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690040(v=OCS.15)
ms:contentKeyID: 49305273
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 모바일 기능에 대한 DNS 요구 사항

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 모바일 기능을 배포할 때는 Microsoft Lync Server 2013 자동 검색 서비스에서 제공되는 새로운 URL을 사용할 수도 있고 기존 웹 서비스 URL을 사용할 수도 있습니다. 기존 URL을 사용하는 경우 사용자는 모바일 장치 설정에 URL을 수동으로 입력해야 합니다. 이 옵션은 보통 문제 해결용으로 사용됩니다. 새 URL을 사용하는 경우에는 모바일 클라이언트가 Lync Server 2013 리소스를 자동으로 검색할 수 있습니다. 자동 검색을 지원하는 경우에는 새 DNS(Domain Name System) 레코드를 추가해야 합니다. 이 섹션에서는 자동 검색에 필요한 DNS 레코드에 대해 설명합니다.

자동 검색을 지원하려면 각 SIP 도메인에 대해 다음 DNS 레코드를 만들어야 합니다.

  - 조직 네트워크 내에서 연결하는 모바일 사용자를 지원하기 위한 내부 DNS 레코드

  - 인터넷에서 연결하는 모바일 사용자를 지원하기 위한 외부(공용) DNS 레코드

내부 자동 검색 URL의 주소는 네트워크 외부에서 확인할 수 없어야 하며, 외부 자동 검색 URL의 주소는 네트워크 내에서 확인할 수 없어야 합니다. 그러나 외부 URL에 대해 이 요구 사항을 충족할 수 없는 경우에도 모바일 클라이언트의 기능에 영향이 있어서는 안 됩니다.

DNS 레코드는 CNAME 레코드 또는 A(호스트) 레코드일 수 있습니다.

**내부 DNS 레코드**

다음 내부 DNS 레코드 중 하나를 만들어야 합니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>레코드 유형</th>
<th>호스트 이름 또는 SRV 정의</th>
<th>확인 대상</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CNAME</p></td>
<td><p>lyncdiscoverinternal.<em>&lt;SIP 도메인&gt;</em></p></td>
<td><p>디렉터 풀의 내부 웹 서비스 FQDN(정규화된 도메인 이름)(있는 경우) 또는 프런트 엔드 풀(디렉터가 없는 경우)</p></td>
</tr>
<tr class="even">
<td><p>A(호스트)</p></td>
<td><p>lyncdiscoverinternal.<em>&lt;SIP 도메인&gt;</em></p></td>
<td><p>디렉터 풀의 내부 웹 서비스 IP 주소(부하 분산 장치를 사용하는 경우 VIP(가상 IP) 주소)(있는 경우) 또는 프런트 엔드 풀(디렉터가 없는 경우)</p></td>
</tr>
</tbody>
</table>


**외부 DNS 레코드**

다음 외부 DNS 레코드 중 하나를 만들어야 합니다.


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
<td><p>lyncdiscover. <em>&lt;SIP 도메인&gt;</em></p></td>
<td><p>디렉터 풀의 외부 웹 서비스 FQDN(있는 경우) 또는 프런트 엔드 풀(디렉터가 없는 경우)</p></td>
</tr>
<tr class="even">
<td><p>A(호스트)</p></td>
<td><p>lyncdiscover. <em>&lt;SIP 도메인&gt;</em></p></td>
<td><p>역방향 프록시의 외부(공용) IP 주소(부하 분산 장치를 사용하는 경우 VIP 주소)</p></td>
</tr>
<tr class="odd">
<td><p>SRV</p></td>
<td><p>_sipfederationtls._tcp. <em>&lt;SIP 도메인&gt;</em></p>
<p>액세스 에지 서비스의 호스트(A 또는 AAAA) 레코드로 확인됩니다.</p></td>
<td><p>푸시 알림 서비스 및 Apple 푸시 알림 서비스를 지원하려면 Microsoft Lync Mobile 클라이언트가 있는 SIP 도메인마다 SRV 레코드를 하나씩 만듭니다.</p>


> [!IMPORTANT]
> 이 요구 사항은 Apple 또는 Microsoft 기반 모바일 장치의 Microsoft Lync Mobile 클라이언트에만 적용됩니다. Andriod 및 Nokia Symbian 장치에서는 푸시 알림을 사용하지 않습니다.


</td>
</tr>
</tbody>
</table>



> [!NOTE]
> Lyncdiscover(자동 검색) 트래픽은 역방향 프록시를 통과합니다. SRV 레코드는 액세스 에지 서비스를 통해 확인되는 레코드를 가리킵니다.


