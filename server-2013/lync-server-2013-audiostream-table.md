---
title: 'Lync Server 2013: AudioStream 테이블'
TOCTitle: AudioStream 테이블
ms:assetid: 49ccbbc3-2f73-45fc-80a6-e612535cbc10
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425961(v=OCS.15)
ms:contentKeyID: 49303546
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 AudioStream 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

각 레코드는 하나의 오디오 스트림을 나타냅니다. 하나의 오디오 미디어 회선에는 일반적으로 두 개의 오디오 스트림이 포함됩니다.


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
<td><p><strong>ConferenceDateTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>기본</p></td>
<td><p><a href="lync-server-2013-medialine-table.md">Lync Server 2013의 MediaLine 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSeq</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p><a href="lync-server-2013-medialine-table.md">Lync Server 2013의 MediaLine 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediaLineLabel</strong></p></td>
<td><p>tinyint</p></td>
<td><p>기본</p></td>
<td><p><a href="lync-server-2013-medialine-table.md">Lync Server 2013의 MediaLine 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p><strong>StreamID</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>미디어 회선 내의 고유 ID입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>JitterInterArrival</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>RTCP(Real Time Control Protocol) 통계로부터 가져온 평균 네트워크 지터입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>JitterInterArrivalMax</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>통화 중 최대 네트워크 지터입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PacketLossRate</strong></p></td>
<td><p>decimal(5.4)</p></td>
<td><p> </p></td>
<td><p>통화 중 평균 패킷 손실 비율입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>PacketLossRateMax</strong></p></td>
<td><p>decimal(5.4)</p></td>
<td><p> </p></td>
<td><p>통화 중 관측된 최대 패킷 손실입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>BurstDensity</strong></p></td>
<td><p>decimal(9.4)</p></td>
<td><p> </p></td>
<td><p>통화 중 손실량이 많아지는 기간 동안의 평균 패킷 손실 밀도입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>BurstDuration</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>통화 중 손실량이 많아지는 기간 동안의 평균 패킷 손실 기간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>BurstGapDensity</strong></p></td>
<td><p>decimal(9.4)</p></td>
<td><p> </p></td>
<td><p>패킷 손실이 최고치인 기간 사이의 간격 중에 발생하는 평균 패킷 손실 밀도입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>BurstGapDuration</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>패킷 손실이 최고치인 기간 사이의 간격에 대한 평균 기간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PacketUtilization</strong></p></td>
<td><p>Int</p></td>
<td><p> </p></td>
<td><p>오디오 스트림에 대한 패킷 수입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>BandwidthEst</strong></p></td>
<td><p>Int</p></td>
<td><p> </p></td>
<td><p>오디오 스트림에 대한 대역폭 예상치입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DegradationAvg</strong></p></td>
<td><p>decimal(3.2)</p></td>
<td><p> </p></td>
<td><p>전체 통화에 대한 네트워크 MOS 저하입니다. 범위는 0.0에서 5.0까지입니다. 이 메트릭은 지터 및 패킷 손실로 인해 감소된 네트워크 MOS의 양을 보여 줍니다. 적정 품질을 위해서는 0.5 미만이어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DegradationMax</strong></p></td>
<td><p>decimal(3.2)</p></td>
<td><p> </p></td>
<td><p>통화 중 최대 네트워크 MOS 저하입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DegradationJitterAvg</strong></p></td>
<td><p>decimal(3.2)</p></td>
<td><p> </p></td>
<td><p>지터로 인해 발생한 네트워크 MOS 저하입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DegradationPacketLossAvg</strong></p></td>
<td><p>decimal(3.2)</p></td>
<td><p> </p></td>
<td><p>패킷 손실로 인해 발생한 네트워크 MOS 저하입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AudioPayloadDescription</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>통화에 사용된 오디오 코덱입니다. PayloadDescription 테이블을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>AudioSampleRate</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>오디오 스트림에 대한 샘플링 속도입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RoundTrip</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>RTCP 통계로부터의 왕복 시간입니다. 적정 품질을 위해서는 100ms 미만이어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RoundTripMax</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>오디오 스트림에 대한 최대 왕복 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OverallAvgNetworkMOS</strong></p></td>
<td><p>decimal(3.2)</p></td>
<td><p> </p></td>
<td><p>통화에 대한 평균 광대역 네트워크 MOS입니다. 이 메트릭은 패킷 손실, 지터 및 사용된 코덱에 따라 달라집니다. 범위는 [1.0 ~ 5.0]입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>OverallMinNetworkMOS</strong></p></td>
<td><p>decimal(3.2)</p></td>
<td><p> </p></td>
<td><p>통화에 대한 최소 광대역 네트워크 MOS입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SendListenMOS</strong></p></td>
<td><p>decimal(3.2)</p></td>
<td><p> </p></td>
<td><p>음성 수준, 잡음 수준 및 캡처 장치 특성을 포함하여 전송된 오디오에 대한 평균 예측 광대역 청취 MOS 점수입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>SendListenMOSMin</strong></p></td>
<td><p>decimal(3.2)</p></td>
<td><p> </p></td>
<td><p>통화에 대한 최소 SendListenMOS입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecvListenMOS</strong></p></td>
<td><p>decimal(3.2)</p></td>
<td><p> </p></td>
<td><p>음성 수준, 잡음 수준, 코덱, 네트워크 조건 및 캡처 장치 특성을 포함하여 수신된 오디오에 대한 평균 예측 광대역 청취 MOS 점수입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RecvListenMOSMin</strong></p></td>
<td><p>decimal(3.2)</p></td>
<td><p> </p></td>
<td><p>통화에 대한 최소 RecvListenMOS입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AudioFECUsed</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>통화에 오디오 FEC가 사용되었는지 여부를 나타내는 플래그입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RatioConcealedSamplesAvg</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p></p></td>
<td><p>일반 샘플에 대한 오디오 힐링으로 생성된 숨겨진 평균 샘플 비율입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RatioStretchedSamplesAvg</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p></p></td>
<td><p>일반 샘플에 대한 오디오 힐링으로 생성된 평균 늘임 샘플 비율입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RatioCompressedSamplesAvg</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p></p></td>
<td><p>일반 샘플에 대한 오디오 힐링으로 생성된 숨겨진 압축 샘플 비율입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Inbound</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>수신자 측에서 수신하는 스트림 데이터입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>Outbound</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>발신자 측에서 수신하는 스트림 데이터입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SenderIsCallerPAI</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>1은 스트림 방향이 발신자에서 수신자의 방향임을 의미합니다.</p>
<p>0은 스트림 방향이 수신자에서 발신자의 방향임을 의미합니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>JitterInterArrivalSD</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>지터 도착 시간에 대한 표준 편차입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConcealRatioMax</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>힐러가 숨긴 최대 패킷 비율입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConcealRatioSD</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>힐러가 숨긴 패킷 비율에 대한 표준 편차입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>HealerPacketDropRatio</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>수신된 총 패킷 수 대비 힐러가 삭제한 패킷 비율입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>HealerFECPacketUsedRatio</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>수신된 총 패킷 수 대비 사용된 정방향 오류 수정 비율입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MaxCompressedSamples</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>힐러가 압축한 총 오디오 패킷 수입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>LossCongestionPercent</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>통화가 손실 정체 상태인 시간 비율을 나타냅니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DelayCongestionPercent</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>통화 중 네트워크 패킷의 도착이 지연되어 정체가 발생한 비율을 나타냅니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ContentionDetectedPercent</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>통화가 네트워크 리소스를 경합하는 시간 비율을 나타냅니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>BandwidthEstMin</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>통화 중 측정된 최소 예상 대역폭 양입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>BandwidthEstMax</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>통화 중 측정된 최대 예상 대역폭 양입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>BandwidthEstStdDev</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>통화 중 측정된 예상 대역폭의 표준 편차입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>BandwidthEstAvge</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>통화 중 측정된 예상 대역폭 양의 평균입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayTotal</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>총 단방향 대기 시간입니다. 상대 단방향 대기 시간이 클라이언트와 서버 간의 지연을 측정합니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayAverage</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>평균 단방향 대기 시간입니다. 상대 단방향 대기 시간이 클라이언트와 서버 간의 지연을 측정합니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayMax</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>최대 단방향 대기 시간입니다. 상대 단방향 대기 시간이 클라이언트와 서버 간의 지연을 측정합니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayBurstOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>총 단방향 버스트 발생 수입니다. &quot;버스트&quot;가 발생한 전송은 데이터가 안정적 스트림이 아닌 예측 불가능한 버스트로 흐르는 전송입니다. 이 메트릭은 클라이언트와 서버 간의 데이터 흐름을 측정합니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayBurstDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>총 단방향 버스트 밀도입니다. &quot;버스트&quot;가 발생한 전송은 데이터가 안정적 스트림이 아닌 예측 불가능한 버스트로 흐르는 전송입니다. 이 메트릭은 클라이언트와 서버 간의 데이터 흐름을 측정합니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayBurstDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>총 단방향 버스트 기간입니다. &quot;버스트&quot;가 발생한 전송은 데이터가 안정적 스트림이 아닌 예측 불가능한 버스트로 흐르는 전송입니다. 이 메트릭은 클라이언트와 서버 간의 데이터 흐름을 측정합니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayGapOccurrences</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>총 단방향 갭 발생 수입니다. &quot;버스트&quot;가 발생한 전송은 데이터가 안정적 스트림이 아닌 예측 불가능한 버스트로 흐르는 전송입니다. 갭은 이러한 버스트 간의 지연을 나타냅니다. 이 메트릭은 클라이언트와 서버 간의 데이터 흐름을 측정합니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayGapDensity</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>총 단방향 갭 밀도입니다. &quot;버스트&quot;가 발생한 전송은 데이터가 안정적 스트림이 아닌 예측 불가능한 버스트로 흐르는 전송입니다. 갭은 이러한 버스트 간의 지연을 나타냅니다. 이 메트릭은 클라이언트와 서버 간의 데이터 흐름을 측정합니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayGapDuration</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>총 단방향 갭 기간입니다. &quot;버스트&quot;가 발생한 전송은 데이터가 안정적 스트림이 아닌 예측 불가능한 버스트로 흐르는 전송입니다. 갭은 이러한 버스트 간의 지연을 나타냅니다. 이 메트릭은 클라이언트와 서버 간의 데이터 흐름을 측정합니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DecodeStereoPercent</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>스테레오로 디코딩된 통화 비율입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AecRenderStereoPercent</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>음향 반향 취소기에 의해 스테레오로 렌더링된 통화 비율입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>AudioPostFECPLR</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>전달 오류 정정이 적용된 후의 패킷 손실 비율입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EncodeStereoPercent</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>스테레오로 인코딩된 통화 비율입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>AecCaptureStereoPercent</strong></p></td>
<td><p>float</p></td>
<td><p></p></td>
<td><p>음향 반향 취소기에 의해 스테레오로 캡처된 통화 비율입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
</tbody>
</table>

