---
title: 'Lync Server 2013: AudioSignal 테이블'
TOCTitle: AudioSignal 테이블
ms:assetid: 0013c8c6-cdf9-4d70-bc2a-cddd1560f66b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398064(v=OCS.15)
ms:contentKeyID: 49302601
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 AudioSignal 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

각 레코드는 하나의 끝점에 대한 오디오 신호 품질 기준을 나타냅니다. 일반적으로 각 통화에는 발신자용 레코드와 수신자용 레코드의 두 레코드가 포함됩니다.


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
<td><p><strong>FromCaller</strong></p></td>
<td><p>bit</p></td>
<td><p>기본</p></td>
<td><p>0: 수신자 데이터</p>
<p>1: 발신자 데이터</p></td>
</tr>
<tr class="odd">
<td><p><strong>SendSignalLevel</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>포스트 아날로그 게인 컨트롤 오디오 신호 수준을 나타냅니다. 이 메트릭의 단위는 dBmo입니다. 적정 품질을 위해서는 최소 30 dBmo여야 합니다. 이 메트릭은 A/V 회의 서버 또는 IP 전화에서 보고되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RecvSignalLevel</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>SendSignalLevel을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SendNoiseLevel</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>포스트 아날로그 게인 컨트롤 오디오 신호 수준을 나타냅니다. 이 메트릭의 단위는 dBmo입니다. 적정 품질을 위해서는 35 dBmo 미만이어야 합니다. 이 메트릭은 A/V 회의 서버 또는 IP 전화에서 보고되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RecvNoiseLevel</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>SendNoiseLevel을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EchoReturn</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>에코 반환 손실 향상 메트릭입니다. 이 메트릭의 단위는 dB입니다. 값이 낮으면 에코가 적습니다. 이 메트릭은 A/V 회의 서버 또는 IP 전화에서 보고되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>AudioSpeakerGlitchRate</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>스피커 렌더링에 대한 5분당 평균 결함 비율입니다. 적정 품질을 위해서는 5분당 1 미만이어야 합니다. A/V 회의 서버, 중재 서버 또는 IP 전화에서 보고되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AudioMicGlitchRate</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>마이크 캡처에 대한 5분당 평균 결함 비율입니다. 적정 품질을 위해서는 5분당 1 미만이어야 합니다. A/V 회의 서버, 중재 서버 또는 IP 전화에서 보고되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>AudioTimestampDriftRateMic</strong></p></td>
<td><p>decimal(9.2)</p></td>
<td><p> </p></td>
<td><p>CPU 클럭 대비 마이크 장치의 클럭 드리프트 비율입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AudioTimestampDriftRateSpk</strong></p></td>
<td><p>decimal(9.2)</p></td>
<td><p> </p></td>
<td><p>CPU 클럭 대비 스피커 장치의 클럭 드리프트 비율입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>AudioTimestampErrorMicMs</strong></p></td>
<td><p>decimal(9.2)</p></td>
<td><p> </p></td>
<td><p>CPU 클럭 대비 스피커 장치의 클럭 드리프트 비율입니다.</p>
<p>통화의 최근 20초 동안 발생한 평균 마이크 캡처 스트림 타임스탬프 오류(밀리초)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AudioTimestampErrorSpkMs</strong></p></td>
<td><p>decimal(9.2)</p></td>
<td><p> </p></td>
<td><p>통화의 최근 20초 동안 발생한 평균 스피커 렌더링 스트림 타임스탬프 오류(밀리초)입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>VsEntryCauses</strong></p></td>
<td><p>smallint</p></td>
<td><p> </p></td>
<td><p>음성 스위치는 중단 기능이 감소된 반이중 모드입니다. 음성 스위치 항목의 원인은 다음과 같습니다.</p>
<p>ENTER_VS_BADTS 0x01</p>
<p>ENTER_VS_ECHO 0x02</p>
<p>ENTER_VS_FORCEORCONVERGENCE 0x04</p>
<p>ENTER_VS_DNLP 0x08</p>
<p>이러한 개별 원인이 복합적으로 발생할 수도 있습니다. ENTER_VS_FORCEORCONVERGENCE는 테스트 목적으로만 regkey로 설정할 수 있습니다.</p>
<p>이 열의 데이터 형식은 Microsoft Lync Server 2013에서 변경되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EchoEventCauses</strong></p></td>
<td><p>tinyint</p></td>
<td><p> </p></td>
<td><p>에코 이벤트의 원인은 다음과 같습니다.</p>
<p>ECHO_EVENT_BAD_TIMESTAMP 0x01</p>
<p>ECHO_EVENT_POSTAEC_ECHO 0x02</p>
<p>ECHO_EVENT_ANLP 0x04</p>
<p>ECHO_EVENT_DNLP 0x08</p>
<p>ECHO_EVENT_MIC_CLIPPING 0x10</p>
<p>ECHO_EVENT_BAD_STATE 0x20</p>
<p>이러한 개별 원인이 복합적으로 발생할 수도 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>EchoPercentMicIn</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p> </p></td>
<td><p>마이크 캡처 스트림에서 에코가 감지되는 시간의 비율입니다. 일반적으로 헤드셋이나 핸드셋에 대한 값은 낮으며, 스피커폰이나 독립 실행형 스피커에 대한 값은 이보다 높습니다. 온보드 음향 반향 취소를 지원하는 장치의 경우 값이 높으면 에코 누출을 나타냅니다. 기타 장치의 경우 장치 품질을 평가하기 위해 이 메트릭을 사용해서는 안 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EchoPercentSend</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p></p></td>
<td><p>전송된 스트림에서 에코가 감지되는 시간의 비율입니다. 전송 스트림에서 에코 비율이 높으면 에코 누출을 나타낼 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RxAGCSignalLevel</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>중재 서버에서 게이트웨이로부터 수신된 신호 수준입니다. 중재 서버에만 적용됩니다. 이 메트릭의 단위는 dBoV입니다. 적정 품질을 위해 허용되는 범위는 [-30 ~ -18] dBoV입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RxAGCNoiseLevel</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>중재 서버에서 게이트웨이로부터 수신된 신호 수준입니다. 중재 서버에만 적용됩니다. 이 메트릭의 단위는 dBoV입니다. 적정 품질을 위해 허용되는 범위는 -50 dBoV 미만입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RxAvgAGCGain</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>중재 서버 쪽의 AGC(자동 게인 컨트롤)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>InitialSignalLevelRMS</strong></p></td>
<td><p>float</p></td>
<td><p> </p></td>
<td><p>통화 초반의 최대 30초 동안 수신되는 신호의 RMS(제곱 평균)입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RecvSignalLevelCh1</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>채널 1에서 수신되는 신호 수준입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecvSignalLevelCh2</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>채널 2에서 수신되는 신호 수준입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RecvNoiseLevelCh1</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>채널 1에서 수신되는 노이즈 수준입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RecvNoiseLevelCh2</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>채널 2에서 수신되는 노이즈 수준입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>SendSignalLevelCh1</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>채널 1에서 송신되는 신호 수준입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SendSignalLevelCh2</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>채널 2에서 송신되는 신호 수준입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>SendNoiseLevelCh1</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>채널 1에서 송신되는 노이즈 수준입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SendNoiseLevelCh2</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>채널 2에서 송신되는 노이즈 수준입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
</tbody>
</table>

