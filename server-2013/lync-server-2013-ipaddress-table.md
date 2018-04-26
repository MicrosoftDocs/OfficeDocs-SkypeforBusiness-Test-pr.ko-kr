---
title: Lync Server 2013의 IPAddress 테이블
TOCTitle: Lync Server 2013의 IPAddress 테이블
ms:assetid: 8ec018b9-158e-4bbe-ad46-869e60315555
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205077(v=OCS.15)
ms:contentKeyID: 49304345
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 IPAddress 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

IPAddress 테이블은 QoE(체감 품질) 데이터베이스의 모든 위치에서 사용되는 고유한 IP 주소 식별자에 IP 주소를 매핑합니다. 이 테이블은 Microsoft Lync Server 2013에서 도입되었습니다.


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
<td><p><strong>IPAddressKey</strong></p></td>
<td><p>int</p></td>
<td><p>Primary</p></td>
<td><p>지정된 IP 주소의 고유 식별자입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>IPAddress</strong></p></td>
<td><p>varchar(50)</p></td>
<td><p>Unique</p></td>
<td><p>IpAddressKey에 매핑되는 고유 IP 주소(예: 189.168.1.1)입니다. IPv4 또는 IPv6 주소일 수 있습니다.</p></td>
</tr>
</tbody>
</table>

