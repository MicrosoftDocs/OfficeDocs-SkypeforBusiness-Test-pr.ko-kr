---
title: 'Lync Server 2013: 모바일 기능에 대한 인증서 요구 사항'
TOCTitle: 모바일 기능에 대한 인증서 요구 사항
ms:assetid: bb0e97af-cf60-4271-a0ab-654429d884ea
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690044(v=OCS.15)
ms:contentKeyID: 49304853
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 모바일 기능에 대한 인증서 요구 사항

 

_**마지막으로 수정된 항목:** 2015-03-09_

모바일 기능을 배포하고 모바일 클라이언트에 대해 자동 검색을 지원하는 경우에는 모바일 클라이언트로부터의 보안 연결을 지원하기 위해 인증서에 특정 주체 대체 이름 항목을 포함해야 합니다.

자동 검색용 주체 대체 이름 항목을 포함해야 하는 인증서는 다음과 같습니다.

  - 디렉터 풀

  - 프런트 엔드 풀

  - 역방향 프록시

이 섹션에서는 자동 검색을 위해 인증서에 필요한 주체 대체 이름 항목에 대해 설명합니다.


> [!NOTE]
> 내부 인증 기관을 통해 인증서를 다시 발급하는 과정은 일반적으로는 간단하지만, 역방향 프록시에서 사용되는 공용 인증서에 여러 주체 대체 이름 항목을 추가하려면 비용이 많이 들 수 있습니다. SIP 도메인이 여러 개인 경우 주체 대체 이름 추가 비용이 매우 크므로, 초기 자동 검색 서비스 요청에 대해 HTTPS(기본 구성) 대신 HTTP를 사용하도록 역방향 프록시를 구성할 수 있습니다. 자세한 내용은 <A href="lync-server-2013-technical-requirements-for-mobility.md">Lync Server 2013의 모바일 기능에 대한 기술 요구 사항</A>을 참조하십시오.



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
<td><p>SAN=lyncdiscoverinternal.&lt;SIP 도메인&gt;</p></td>
</tr>
<tr class="even">
<td><p>외부 자동 검색 서비스 URL</p></td>
<td><p>SAN=lyncdiscover.&lt;SIP 도메인&gt;</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> SAN=*.&lt;SIP 도메인&gt;을 사용해도 됩니다.



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
<td><p>SAN=lyncdiscoverinternal.&lt;SIP 도메인&gt;</p></td>
</tr>
<tr class="even">
<td><p>외부 자동 검색 서비스 URL</p></td>
<td><p>SAN=lyncdiscover.&lt;SIP 도메인&gt;</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> SAN=*.&lt;SIP 도메인&gt;을 사용해도 됩니다.



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
<td><p>SAN=lyncdiscover.&lt;SIP 도메인&gt;</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> 역방향 프록시의 SSL 수신기에 할당된 인증서에 이 SAN을 할당합니다.




> [!NOTE]
> 역방향 프록시 수신기는 외부 웹 서비스 URL에 대한 주체 대체 이름을 갖습니다(예: 선택적인 디렉터를 배포한 경우 SAN=lyncwebextpool01.contoso.com 및 dirwebexternal.contoso.com).


