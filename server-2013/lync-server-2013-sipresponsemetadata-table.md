---
title: Lync Server 2013의 SIPResponseMetaData 테이블
TOCTitle: Lync Server 2013의 SIPResponseMetaData 테이블
ms:assetid: cf723737-4a75-4352-829b-f4954aa59716
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205294(v=OCS.15)
ms:contentKeyID: 49305084
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 SIPResponseMetaData 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

SIPResponseMetaDataTable에는 SIP 응답 코드 및 분류, 그리고 각 코드의 정의가 나열되어 있습니다. 이러한 코드는 SIP 장치 및 SIP 통신 세션에 영향을 미치는 이벤트에 대한 응답으로 생성됩니다. 예를 들어 SIP 장치가 요청을 전송했지만 서버에서 해당 요청을 거부한 경우 응답 코드 403이 생성됩니다.

이 테이블은 Microsoft Lync Server 2013에서 도입되었습니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>열</th>
<th>데이터 형식</th>
<th>키/인덱스</th>
<th>세부 정보</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ResponseCode</strong></p></td>
<td><p>int</p></td>
<td><p>Primary</p></td>
<td><p>SIP 응답 코드를 나타내는 숫자 값입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>Class</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>응답 코드의 일반 분류법입니다. 다음과 같이 분류됩니다.</p>
<ul>
<li><p>1 – 정보 제공용 응답</p></li>
<li><p>2 – 성공한 응답</p></li>
<li><p>3 – 리디렉션 응답</p></li>
<li><p>4 – 클라이언트 오류 응답</p></li>
<li><p>5 – 서버 오류 응답</p></li>
<li><p>6 – 전역 오류 응답</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Description</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>SIP 응답 코드의 설명입니다. 예를 들어 응답 코드 181의 설명은 다음과 같습니다.</p>
<p>통화를 전달하는 중</p></td>
</tr>
</tbody>
</table>

