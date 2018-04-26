---
title: 'Lync Server 2013: Endpoint 테이블'
TOCTitle: Endpoint 테이블
ms:assetid: 500f330d-4d7d-4e88-b1cc-fef9a9de6b5c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398327(v=OCS.15)
ms:contentKeyID: 49303611
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Endpoint 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

Endpoint 테이블은 데이터베이스에 기록되는 세션에 참여한 끝점에 대한 정보를 저장하는 지원 테이블입니다. 테이블의 각 레코드는 하나의 끝점을 나타냅니다.


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
<td><p><strong>EndpointKey</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>이 끝점을 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>이름</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Unique</p></td>
<td><p>끝점 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OS</strong></p></td>
<td><p>nvarchar(128)</p></td>
<td><p> </p></td>
<td><p>끝점의 OS(운영 체제)입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CPUName</strong></p></td>
<td><p>nvarchar(128)</p></td>
<td><p></p></td>
<td><p>끝점의 CPU 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CPUNumberOfCores</strong></p></td>
<td><p>smallint</p></td>
<td><p></p></td>
<td><p>끝점의 CPU 코어 수입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CPUProcessorSpeed</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>끝점의 CPU 프로세서 속도입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>VirtualizationFlag</strong></p></td>
<td><p>tinyint</p></td>
<td><p></p></td>
<td><p>시스템이 가상화된 환경에서 실행되고 있는지를 나타내는 비트 플래그입니다.</p>
<ul>
<li><p>0x0000 - 없음</p></li>
<li><p>0x0001 - HyperV</p></li>
<li><p>0x0002 - VMWare</p></li>
<li><p>0x0004 - 가상 PC</p></li>
<li><p>0x0008 - Xen PC</p></li>
</ul></td>
</tr>
</tbody>
</table>

