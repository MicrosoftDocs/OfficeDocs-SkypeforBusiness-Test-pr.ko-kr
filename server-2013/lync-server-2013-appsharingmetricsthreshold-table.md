---
title: Lync Server 2013의 AppSharingMetricsThreshold 테이블
TOCTitle: AppSharingMetricsThreshold 테이블
ms:assetid: 782cfab9-01a6-4843-aea1-28f47b0b51f7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205018(v=OCS.15)
ms:contentKeyID: 49304095
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 AppSharingMetricsThreshold 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

AppSharingMetricsThreshold 테이블에는 응용 프로그램 공유에 사용되는 QoE(체감 품질) 메트릭에 대한 최적값 및 허용 가능한 값이 포함되어 있습니다. 이러한 임계값은 응용 프로그램 공유 환경을 불량으로 분류해야 하는지 여부를 확인하는 데 사용됩니다.

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
<td><p>수행된 통화 유형입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>AppliedBandwidthLimitOptimal</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>응용 프로그램 공유에 대한 최적의 대역폭 제한입니다. 기본값은 1000000입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AppliedBandwidthLimitAcceptable</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>응용 프로그램 공유에 대한 허용 가능한 대역폭 제한입니다. 기본값은 500000입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>SpoiledTilePercentTotalOptimal</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>응용 프로그램 공유 품질을 분류하기 위한 &quot;잘못된&quot; 타일에 대한 최적 비율입니다. 이 값은 공유자의 콘텐츠 중 뷰어에 도달하지 못한 비율입니다. 공유자가 그래픽 원본에서 타일을 삭제하거나 ASMCU 타일이 각각의 공유자에서 타일을 삭제하면 콘텐츠가 삭제(또는 잘못됨)될 수 있습니다. 기본값은 11%입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SpoiledTilePercentTotalAcceptable</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p></p></td>
<td><p>응용 프로그램 공유 품질을 분류하기 위한 &quot;잘못된&quot; 타일에 대한 허용 가능한 비율입니다. 이 값은 공유자의 콘텐츠 중 뷰어에 도달하지 못한 비율입니다. 공유자가 그래픽 원본에서 타일을 삭제하거나 ASMCU 타일이 각각의 공유자에서 타일을 삭제하면 콘텐츠가 삭제(또는 잘못됨)될 수 있습니다. 기본값은 36%입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>JitterInterArrivalOptimal</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>이 열은 Microsoft Lync Server 2013에서 사용되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>JitterInterArrivalAcceptable</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>이 열은 Microsoft Lync Server 2013에서 사용되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayBurstDensityOptimal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>이 열은 Microsoft Lync Server 2013에서 사용되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayBurstDensityAcceptable</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>이 열은 Microsoft Lync Server 2013에서 사용되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RDPTileProcessingLatencyBurstDensityOptimal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>이 열은 Microsoft Lync Server 2013에서 사용되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RDPTileProcessingLatencyBurstDensityAcceptable</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>이 열은 Microsoft Lync Server 2013에서 사용되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayAverageOptimal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>응용 프로그램 공유에 포함된 두 개의 미디어 끝점 사이의 상대적 단방향 지연 시간에 대한 최적 값입니다. 이 값은 단일 홉 지연 시간 측정값입니다. 기본값은 1.0초입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayAverageAcceptable</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>응용 프로그램 공유에 포함된 두 개의 미디어 끝점 사이의 상대적 단방향 지연 시간에 대한 최적 값입니다. 이 값은 단일 홉 지연 시간 측정값입니다. 기본값은 1.75초입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RDPTileProcessingLatencyAverageOptimal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>보기 세션 기간 중 AS 회의 서버의 평균 RDP 타일 처리 지연 시간에 대한 최적 값입니다. 이 메트릭은 네트워크 지연 시간을 포함하지 않습니다.</p>
<p>평균 값이 높으면 보기 환경의 지연 시간이 길다는 것을 나타냅니다. 부하가 높은 회의 서버는 평균 대기 시간이 높을 수 있습니다. 기본값은 200ms입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RDPTileProcessingLatencyAverageAcceptable</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>보기 세션 기간 중 AS 회의 서버의 평균 RDP 타일 처리 지연 시간에 대한 허용 가능한 값입니다. 이 메트릭은 네트워크 지연 시간을 포함하지 않습니다.</p>
<p>평균 값이 높으면 보기 환경의 지연 시간이 길다는 것을 나타냅니다. 부하가 높은 회의 서버는 평균 대기 시간이 높을 수 있습니다. 기본값은 200ms입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
</tbody>
</table>

