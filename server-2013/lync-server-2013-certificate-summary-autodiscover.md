---
title: 인증서 요약 - 자동 검색
TOCTitle: 인증서 요약 - 자동 검색
ms:assetid: 16ac96bb-882a-4141-b75c-9530637548d9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945616(v=OCS.15)
ms:contentKeyID: 52056792
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 인증서 요약 - 자동 검색

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 자동 검색 서비스는 디렉터 및 프런트 엔드 풀 서버에서 실행되며, DNS에서 게시되는 경우 Lync 클라이언트가 서버 및 사용자 서비스를 찾는 데 사용될 수 있습니다. 모바일 기능을 배포하지 않은 상태로 Lync Server 2010에서 업그레이드하는 경우 클라이언트가 자동 검색을 사용하려면 자동 검색 서비스를 실행하는 모든 디렉터 및 프런트 엔드 서버에서 인증서 주체 대체 이름 목록을 수정해야 합니다. 또한 역방향 프록시에 대한 외부 웹 서비스 게시 규칙에 사용되는 인증서에서도 주체 대체 이름 목록을 수정해야 할 수 있습니다.

자동 검색 서비스를 게시하는 포트(포트 80 또는 포트 443)에 따라 역방향 프록시에서 주체 대체 이름 목록을 사용할지 여부를 결정합니다.

  - **포트 80에 게시**   자동 검색 서비스에 대한 초기 쿼리가 포트 80에서 수행되는 경우에는 인증서를 변경할 필요가 없습니다. Lync를 실행하는 모바일 장치는 외부에서 포트 80의 역방향 프록시에 액세스한 다음 내부에서 포트 8080의 디렉터 또는 프런트 엔드 서버로 브리지되기 때문입니다. 자세한 내용은 [Lync Server 2013의 모바일 기능에 대한 기술 요구 사항](lync-server-2013-technical-requirements-for-mobility.md)의 "포트 80을 사용하는 초기 자동 검색 프로세스" 섹션을 참조하십시오.

  - **포트 443에 게시**   외부 웹 서비스 게시 규칙에서 사용하는 인증서의 주체 대체 이름 목록에 조직 내의 각 SIP 도메인에 대한 *lyncdiscover.\<SIP 도메인\>* 항목이 포함되어 있어야 합니다.
    

    > [!IMPORTANT]
    > HTTP보다는 HTTPS를 사용하는 것이 좋습니다. HTTPS는 인증서를 사용하여 트래픽을 암호화합니다. HTTP는 암호화 기능을 제공하지 않으며 모든 데이터는 일반 텍스트로 전송됩니다.



내부 인증 기관을 통해 인증서를 다시 발급하는 과정은 일반적으로는 간단합니다. 그러나 웹 서비스 게시 규칙에서 사용되는 공용 인증서의 경우 여러 주체 대체 이름 항목을 추가하려면 비용이 많이 들 수 있습니다. 이 문제를 해결하기 위해 포트 80을 통한 초기 자동 검색 연결이 지원됩니다. 이 연결은 초기 자동 검색 이후 포트 8080의 디렉터 또는 프런트 엔드 서버로 리디렉션됩니다.


> [!NOTE]
> Lync Server 2013 인프라가 내부 CA(인증 기관)에서 발급한 내부 인증서를 사용하며 모바일 장치의 무선 연결을 지원하려는 경우 내부 CA의 루트 인증서 체인을 모바일 장치에 설치하거나, Lync Server 2013 인프라에서 공용 인증서로 변경해야 합니다.



이 항목에서는 디렉터, 프런트 엔드 서버 및 역방향 프록시에 필요한 추가된 주체 대체 이름에 대해 설명합니다. 추가된 SAN(주체 대체 이름)만 참조로 제공됩니다. 인증서의 다른 항목에 대한 지침은 계획 섹션을 참조하십시오. 자세한 내용은 [Lync Server 2013의 디렉터 시나리오](lync-server-2013-scenarios-for-the-director.md), [Lync Server 2013의 외부 사용자 액세스에 대한 시나리오](lync-server-2013-scenarios-for-external-user-access.md) 및 [Lync Server 2013의 역방향 프록시에 대한 시나리오](lync-server-2013-scenarios-for-reverse-proxy.md)를 참조하십시오.

다음 표에는 디렉터 풀, 프런트 엔드 풀 및 역방향 프록시에 대한 자동 검색 SAN 항목의 정의가 나와 있습니다.

### 디렉터 풀 인증서 요구 사항

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>설명</th>
<th>주체 대체 이름 항목</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>내부 자동 검색 서비스 URL</p></td>
<td><p>SAN=lyncdiscoverinternal.<em>&lt;내부 도메인 이름&gt;</em></p></td>
</tr>
<tr class="even">
<td><p>외부 자동 검색 서비스 URL</p></td>
<td><p>SAN=lyncdiscover.<em>&lt;SIP 도메인&gt;</em></p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> 새 SAN 항목으로 새롭게 업데이트된 인증서를 기본 인증서에 지정합니다. 또는 SAN=*.<EM>&lt;SIP 도메인&gt;</EM>을 사용할 수 있습니다.



### 프런트 엔드 풀 인증서 요구 사항

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>설명</th>
<th>주체 대체 이름 항목</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>내부 자동 검색 서비스 URL</p></td>
<td><p>SAN=lyncdiscoverinternal.<em>&lt;내부 도메인 이름&gt;</em></p></td>
</tr>
<tr class="even">
<td><p>외부 자동 검색 서비스 URL</p></td>
<td><p>SAN=lyncdiscover.<em>&lt;SIP 도메인&gt;</em></p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> 새 SAN 항목으로 새롭게 업데이트된 인증서를 기본 인증서에 지정합니다. 또는 SAN=*.<EM>&lt;SIP 도메인&gt;</EM>을 사용할 수 있습니다.



### 역방향 프록시(공용 CA) 인증서 요구 사항

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>설명</th>
<th>주체 대체 이름 항목</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>외부 자동 검색 서비스 URL</p></td>
<td><p>SAN=lyncdiscover.<em>&lt;SIP 도메인&gt;</em></p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> 새 SAN 항목으로 새롭게 업데이트된 인증서를 역방향 프록시의 SSL 수신기에 지정합니다.


