---
title: 'Lync Server 2013: 인증서 요약 - 역방향 프록시'
TOCTitle: 인증서 요약 - 역방향 프록시
ms:assetid: f2b9a53f-aead-413d-81e9-4a294a010fbb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205381(v=OCS.15)
ms:contentKeyID: 49305501
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 인증서 요약 - 역방향 프록시

 

_**마지막으로 수정된 항목:** 2015-03-09_

역방향 프록시에 대한 인증서 요구 사항은 에지 서버에서보다 훨씬 간단합니다. 제공된 순서도는 필요한 요구 사항을 나타냅니다. 함께 제공된 표에는 에지 서버 설명에서 살펴본 시나리오와 관련된 일반적인 인증서 주체 이름과 주체 대체 이름이 나와 있습니다. 에지 서버 시나리오에 대한 자세한 내용은 [Lync Server 2013의 외부 사용자 액세스에 대한 시나리오](lync-server-2013-scenarios-for-external-user-access.md)를 참조하십시오.

**역방향 프록시에 대한 인증서 순서도**

![에지 서버에 대한 인증서 순서도](images/JJ205381.026045d7-1b4b-4651-b32f-2d43a7161198(OCS.15).jpg "에지 서버에 대한 인증서 순서도")

### 역방향 프록시: 외부 인터페이스

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
<td><p>역방향 프록시</p></td>
<td><p>webext.contoso.com</p></td>
<td><p>webext.contoso.com</p>
<p>webdirext.contoso.com</p>
<p>dialin.contoso.com</p>
<p>meet.contoso.com</p>
<p>officewebapps01.contoso.com</p>
<p>lyncdiscover.contoso.com</p>
<p>(선택 사항):*.contoso.com</p></td>
<td><p>인증서는 공용 CA 및 서버 EKU를 사용하여 발급되어야 합니다. 서버에는 주소록 서비스, 회의용 메일 그룹 확장 Office Web Apps 및 Lync IP 주소 게시 규칙이 포함됩니다. 주체 대체 이름에는 다음이 포함됩니다.</p>
<ul>
<li><p>프런트 엔드 서버 또는 프런트 엔드 풀에 대한 외부 웹 서비스 FQDN</p></li>
<li><p>디렉터 또는 디렉터 풀에 대한 외부 웹 서비스 FQDN</p></li>
<li><p>전화 접속 회의 구성</p></li>
<li><p>온라인 모임 게시 규칙</p></li>
<li><p>회의용 Office Web Apps</p></li>
<li><p>Lyncdiscover(자동 검색)</p></li>
</ul>
<p>선택적 와일드카드는 모임 및 전화 접속 SAN을 모두 대체합니다.</p></td>
</tr>
</tbody>
</table>

