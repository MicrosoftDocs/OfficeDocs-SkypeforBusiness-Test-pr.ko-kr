---
title: Lync Server 2013의 VideoMetricsThreshold 테이블
TOCTitle: Lync Server 2013의 VideoMetricsThreshold 테이블
ms:assetid: 2e2f4711-35ba-48c6-b15b-5aba61c4eb75
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204778(v=OCS.15)
ms:contentKeyID: 49303177
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 VideoMetricsThreshold 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

VideoMetricsThreshold 테이블은 비디오 통화에 사용되는 체감 품질 메트릭에 대한 최적의 값과 적절한 값을 포함합니다.


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
<td><p><strong>CallType</strong></p></td>
<td><p>int</p></td>
<td><p>Primary</p></td>
<td><p>건 전화의 유형입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>VideoPostFECPLROptimal</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p></p></td>
<td><p>기본값은 0.05입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>VideoPostFECPLRAcceptable</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p></p></td>
<td><p>기본값은 0.10입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>VideoLocalFrameLostPercentageAverageOptimal</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p></p></td>
<td><p>기본값은 5.0입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>VideoLocalFrameLostPercentageAverageAcceptable</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p></p></td>
<td><p>기본값은 10.0입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RecvFrameRateAverageOptimal</strong></p></td>
<td><p>decimal(9.4)</p></td>
<td><p></p></td>
<td><p>기본값은 12.0000입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecvFramerateAverageAcceptable</strong></p></td>
<td><p>decimal(9.4)</p></td>
<td><p></p></td>
<td><p>기본값은 7.0000입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>LowFrameRateCallPercentOptimal</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p></p></td>
<td><p>기본값은 5.0입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LowFrameRateCallPercentAcceptable</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p></p></td>
<td><p>기본값은 10.0입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>LowResolutionCallPercentOptimal</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p></p></td>
<td><p>기본값은 5.0입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LowResolutionCallPercentAcceptable</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p></p></td>
<td><p>기본값은 10.0입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>VideoPacketLossRateOptimal</strong></p></td>
<td><p>foat</p></td>
<td><p></p></td>
<td><p>기본값은 0.05입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>VideoPacketLossRateAcceptable</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>기본값은 0.10입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>VideoFrameRateAvgOptimal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>기본값은 12입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>VideoFrameRateAvgAcceptable</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>기본값은 7입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DynamicCapabilityPercentOptimal</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p></p></td>
<td><p>기본값은 5.00입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DynamicCapabilityPercentAcceptable</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p></p></td>
<td><p>기본값은 10.00입니다.</p></td>
</tr>
</tbody>
</table>

