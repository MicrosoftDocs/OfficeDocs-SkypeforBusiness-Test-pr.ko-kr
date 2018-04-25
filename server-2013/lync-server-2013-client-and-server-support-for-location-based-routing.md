---
title: 'Lync Server 2013: 위치 기반 라우팅을 위한 클라이언트 및 서버 지원'
TOCTitle: 위치 기반 라우팅을 위한 클라이언트 및 서버 지원
ms:assetid: 26c2ca3d-026d-4dd7-94fa-15ebb4406953
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994024(v=OCS.15)
ms:contentKeyID: 52056808
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 위치 기반 라우팅을 위한 클라이언트 및 서버 지원

 

_**마지막으로 수정된 항목:** 2015-03-09_

위치 기반 라우팅은 Lync Server에 의해 적용됩니다. Lync Server는 사용자가 회사 네트워크 안에서 연결 중인 네트워크 사이트를 식별할 수 있습니다. 원격 사용자의 경우 회사 네트워크 밖에 있기 때문에 그 위치를 알 수 없습니다.

## Lync Server 지원

위치 기반 라우팅을 사용하려면 지정된 토폴로지의 모든 프런트 엔드 풀 및 Standard Edition 서버에 Lync Server 2013 CU1을 배포해야 합니다. 토폴로지의 특정 Lync 구성 요소에 Lync Server 2013 CU1이 설치되어 있지 않으면 위치 기반 라우팅 제한을 완전히 적용할 수 없습니다.

다음 표에서는 위치 기반 라우팅이 지원되는 서버 역할과 버전의 조합을 보여줍니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>풀 버전</th>
<th>중재 서버 버전</th>
<th>지원됨</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync Server 2013 2013년 2월 누적 업데이트</p></td>
<td><p>Lync Server 2013 2013년 2월 누적 업데이트</p></td>
<td><p>예</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2013 2013년 2월 누적 업데이트</p></td>
<td><p>Lync Server 2013</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2013 2013년 2월 누적 업데이트</p></td>
<td><p>Lync Server 2010</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2013 2013년 2월 누적 업데이트</p></td>
<td><p>Office Communications Server 2007 R2</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2013</p></td>
<td><p>모두</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2010</p></td>
<td><p>모두</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="odd">
<td><p>Office Communications Server 2007 R2</p></td>
<td><p>모두</p></td>
<td><p>아니요</p></td>
</tr>
</tbody>
</table>


## Lync 클라이언트 지원

다음 표에서는 위치 기반 라우팅이 지원하는 클라이언트를 보여줍니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>클라이언트 유형</th>
<th>지원됨</th>
<th>세부 정보</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013</p></td>
<td><p>예</p></td>
<td><p>Lync 2013 2013년 2월 누적 업데이트 포함</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010</p></td>
<td><p>예</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>Office Communicator 2007 R2</p></td>
<td><p>아니요</p></td>
<td> </td>
</tr>
<tr class="even">
<td><p>Lync Phone Edition</p></td>
<td><p>예</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>Lync Attendant</p></td>
<td><p>예</p></td>
<td> </td>
</tr>
<tr class="even">
<td><p>Windows 8용 Lync</p></td>
<td><p>아니요</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>Lync Mobile 2013</p></td>
<td><p>아니요</p></td>
<td><p>위치 기반 라우팅이 설정된 사용자의 경우 Lync Mobile 2013 클라이언트에 대해 VoIP를 사용하지 않도록 설정해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p>Lync Mobile 2010</p></td>
<td><p>예</p></td>
<td> </td>
</tr>
</tbody>
</table>

  


> [!NOTE]
> Lync Mobile 2013 클라이언트용 VoIP를 사용하지 않도록 설정하려면 위치 기반 라우팅이 설정된 모든 사용자에 대해 IP 오디오/비디오 설정을 해제한 모바일 정책을 할당합니다. 모바일 정책에 대한 자세한 내용은 <A href="new-csmobilitypolicy.md">New-CsMobilityPolicy</A>를 참고하세요.



## 참고 항목

#### 기타 리소스

[Lync Server 2013의 위치 기반 라우팅 계획](lync-server-2013-planning-for-location-based-routing.md)

