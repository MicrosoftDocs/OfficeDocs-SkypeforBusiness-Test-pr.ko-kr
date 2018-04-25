---
title: Lync Server 2013의 NetworkConnectionDetail 테이블
TOCTitle: Lync Server 2013의 NetworkConnectionDetail 테이블
ms:assetid: b48cc9a6-5232-48b5-bd20-53b68229336b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205185(v=OCS.15)
ms:contentKeyID: 49304780
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 NetworkConnectionDetail 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

NetworkConnectionDetail 테이블은 네트워크 연결 유형을 체감 품질 데이터베이스의 다른 곳에 사용되는 네트워크 연결 식별자에 매핑합니다. 이 테이블은 Microsoft Lync Server 2013에서 도입되었습니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>열</strong></th>
<th><strong>데이터 형식</strong></th>
<th><strong>키/인덱스</strong></th>
<th><strong>세부 정보</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>NetworkConnectionDetailKey</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Primary</p></td>
<td><p>네트워크 연결 유형의 고유 식별자입니다</p></td>
</tr>
<tr class="even">
<td><p><strong>NetworkConnectionDetail</strong></p></td>
<td><p>varchar(256)</p></td>
<td><p>Unique</p></td>
<td><p>NetworkConnectionDetailKey에 해당하는 네트워크 연결 유형입니다. 허용되는 값은 다음과 같습니다.</p>
<ol>
<li><p>0 -- 유선</p></li>
<li><p>1 -- WiFi</p></li>
<li><p>2 -- 이더넷</p></li>
</ol></td>
</tr>
</tbody>
</table>

