---
title: 'Lync Server 2013: 인증서 요약 - 조정된 디렉터 풀, 하드웨어 부하 분산 장치'
TOCTitle: 인증서 요약 - 조정된 디렉터 풀, 하드웨어 부하 분산 장치
ms:assetid: 45940add-8027-418d-b79a-9033b494762f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204846(v=OCS.15)
ms:contentKeyID: 49303502
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 인증서 요약 - 조정된 디렉터 풀, 하드웨어 부하 분산 장치

 

_**마지막으로 수정된 항목:** 2015-03-09_

하드웨어 부하 분산 장치를 포함하는 디렉터에 대한 인증서 요구 사항은 디렉터 풀이 수신할 수 있는 서비스에 대한 주체 이름 및 주체 대체 이름이 포함된 기본 인증서를 사용하는 것입니다. 인증서는 풀의 각 디렉터에 대해 요청됩니다. 또한 서버 인증 목적을 위해 각 서버에 설치된 서버 OAuth Token 인증서가 있습니다.

### 하드웨어 부하 분산 장치를 사용하여 확장된 디렉터의 인증서

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
<th>SN(주체 이름)</th>
<th>SAN(주체 대체 이름)</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>기본값</p></td>
<td><p>dirpool01.contoso.net</p></td>
<td><p>dirpool01.contoso.net</p>
<p>dir01.contoso.net</p>
<p>dialin.contoso.com</p>
<p>meet.contoso.com</p>
<p>lyncdiscoverinternal.contoso.com</p>
<p>lyncdiscover.contoso.com</p>
<p>(선택적으로) *.contoso.com</p></td>
<td><p>디렉터 인증서는 내부에서 관리되는 CA(인증 기관) 또는 공용 CA에서 요청될 수 있습니다.</p>
<p>디렉터는 경계에 있는 역방향 프록시 또는 에지 서버의 요청에 응답합니다.</p>
<p>또는 단순 URL에 대한 와일드카드 항목</p></td>
</tr>
<tr class="even">
<td><p>OAuthTokenIssuer</p></td>
<td><p>dir01.contoso.net</p></td>
<td><p>항목 없음</p></td>
<td>

> [!IMPORTANT]
> 최소 키 길이는 1024이지만 최소 권장 키 길이가 2048비트라는 경고가 표시될 수 있습니다.



<p>OAuthTokenIssuer 인증서는 대규모 환경에서 서버 인증 목적을 위한 단일 목적 인증서이며 내부 CA 또는 공용 CA에서 요청될 수 있습니다. 필수 인증서입니다.</p></td>
</tr>
</tbody>
</table>

