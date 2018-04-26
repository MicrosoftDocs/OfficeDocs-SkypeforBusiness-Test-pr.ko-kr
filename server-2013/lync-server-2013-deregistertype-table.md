---
title: 'Lync Server 2013: DeRegisterType 테이블'
TOCTitle: DeRegisterType 테이블
ms:assetid: 09148118-6209-4fd7-a494-99118689a245
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398142(v=OCS.15)
ms:contentKeyID: 49302738
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 DeRegisterType 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

DeRegisterType 테이블은 'client initiated', 'registration expired' 또는 'client stopped responding'과 같은 사용 가능한 사용자의 등록 해제 유형 목록을 저장하는 정적 테이블입니다.


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
<td><p><strong>DeRegisterTypeId</strong></p></td>
<td><p>tinyint</p></td>
<td><p>기본</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>DeRegisterReason</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>허용되는 값:</p>
<ul>
<li><p>0 - 알 수 없음</p></li>
<li><p>1 - 클라이언트가 등록 취소 시작</p></li>
<li><p>2 - 등록 만료</p></li>
<li><p>3 - 클라이언트 작동 중단</p></li>
<li><p>4 - 사용자 특성 변경</p></li>
<li><p>5 - 선호 등록자 변경</p></li>
<li><p>6 - 레거시 클라이언트가 서바이벌 모드임</p></li>
</ul></td>
</tr>
</tbody>
</table>

