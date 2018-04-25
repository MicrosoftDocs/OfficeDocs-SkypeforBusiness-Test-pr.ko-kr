---
title: Lync Server 2013 서버 하드웨어 플랫폼
TOCTitle: 서버 하드웨어 플랫폼
ms:assetid: c964c1c0-0153-472b-88ad-a38866e0df0c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398835(v=OCS.15)
ms:contentKeyID: 49305015
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 서버 하드웨어 플랫폼

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 관리 도구를 실행하는 Lync Server 2013 서버 역할 및 컴퓨터에는 64비트 하드웨어가 필요합니다.

Lync Server 2013 배포에 사용되는 특정 하드웨어는 크기 및 사용 요구 사항에 따라 달라질 수 있습니다. 이 섹션에서는 권장 하드웨어에 대해 설명합니다. 이러한 사항은 요구 사항이 아닌 권장 사항이지만 이러한 권장 사항을 충족하지 않는 하드웨어를 사용할 경우 심각한 성능 문제 및 기타 문제가 야기될 수 있습니다.

## 권장 하드웨어 플랫폼

최상의 성능을 위해 다음 표의 요구 사항을 충족하는 하드웨어가 장착된 서버에서 Lync Server를 실행하는 것이 좋습니다. 다소 성능이 저하된 하드웨어를 사용하는 경우 작동 문제 또는 성능 저하 문제가 발생할 수 있습니다. 참고로, 이러한 하드웨어 요구 사항은 이전 버전의 Lync Server보다 높습니다. 이는 Lync Server 2013의 모든 프런트 엔드 서버가 SQL Server를 실행하기 때문입니다.


> [!NOTE]
> NIC 팀이 지원되고 Lync Server에 투명하게 표시되어야 합니다. 자세한 내용은 <A href="http://go.microsoft.com/fwlink/p/?linkid=389910">Communications Server 또는 Lync Server 및 네트워크 어댑터 팀</A>을 참고하세요.



### 프런트 엔드 서버, 백 엔드 서버, Standard Edition 서버, 영구 채팅 서버, 영구 채팅 저장소 및 영구 채팅 준수 저장소(영구 채팅 서버를 위한 백 엔드 서버 역할)에 권장되는 하드웨어

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>하드웨어 구성 요소</th>
<th>권장</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>64비트 듀얼 프로세서, 헥사 코어, 2.26GHz 이상</p>
<p>Intel Itanium 프로세서는 Lync Server 역할에 지원되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p>메모리</p></td>
<td><p>32GB</p></td>
</tr>
<tr class="odd">
<td><p>디스크</p></td>
<td><ul>
<li><p>72GB 이상의 사용 가능한 디스크 공간이 있는 10,000 RPM 하드 디스크 드라이브 8개 이상</p>
<p>이 중 두 개는 RAID 1을 사용하고 6개는 RAID 10을 사용합니다.</p>
<p>-또는-</p></li>
<li><p>8개의 10,000 RPM 기계식 디스크 드라이브와 유사한 성능을 제공하는 SDD(반도체 드라이브)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>네트워크</p></td>
<td><ul>
<li><p>1개의 이중 포트 네트워크 어댑터, 1Gbps 이상(2개 권장, 단일 MAC 주소와 단일 IP 주소를 사용하여 팀으로 구성해야 함)</p></li>
</ul></td>
</tr>
</tbody>
</table>


### 에지 서버, 독립 실행형 중재 서버, 디렉터를 위한 권장 하드웨어

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>하드웨어 구성 요소</th>
<th>권장</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><ul>
<li><p>64비트 듀얼 프로세서, 쿼드 코어, 2.0GHz 이상</p>
<p>-또는-</p></li>
<li><p>64비트 4웨이 프로세서, 듀얼 코어, 2.0GHz 이상</p></li>
</ul>
<p>Intel Itanium 프로세서는 Lync Server 역할에 지원되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p>메모리</p></td>
<td><p>16GB</p></td>
</tr>
<tr class="odd">
<td><p>디스크</p></td>
<td><ul>
<li><p>72GB 이상의 사용 가능한 디스크 공간이 있는 10,000 RPM 하드 디스크 드라이브 4개 이상</p>
<p>이 디스크는 2x RAID 1 구성이어야 합니다.</p>
<p>-또는-</p></li>
<li><p>4개의 10,000 RPM 기계식 디스크 드라이브와 유사한 성능을 제공하는 SDD(반도체 드라이브)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>네트워크</p></td>
<td><ul>
<li><p>1개의 이중 포트 네트워크 어댑터, 1Gbps 이상(2개 권장, 단일 MAC 주소와 단일 IP 주소를 사용하여 팀으로 구성해야 함). 에지 서버에서는 2개의 인터페이스가 필요합니다.</p></li>
</ul></td>
</tr>
</tbody>
</table>

