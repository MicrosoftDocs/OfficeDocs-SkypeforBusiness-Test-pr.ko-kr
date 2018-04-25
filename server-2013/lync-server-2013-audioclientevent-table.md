---
title: 'Lync Server 2013: AudioClientEvent 테이블'
TOCTitle: AudioClientEvent 테이블
ms:assetid: fef73d8f-7261-4e5b-9769-82435b007979
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413086(v=OCS.15)
ms:contentKeyID: 49305647
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 AudioClientEvent 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

각 레코드에는 오디오 통화의 한 끝점에 대한 클라이언트 이벤트가 포함됩니다. 일반적으로 하나의 통화에는 발신자용 레코드와 수신자용 레코드의 두 레코드가 포함됩니다.


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
<td><p><strong>NetworkSendQualityEventRatio</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p> </p></td>
<td><p>'나쁨' 상태로 NetworkSendQuality 이벤트가 발생한 세션의 비율입니다.</p>
<p>지터 또는 패킷 손실 측면의 네트워크 품질이 심각하고 전송 중인 오디오 품질에 영향을 줍니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>NetworkReceiveQualityEventRatio</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p> </p></td>
<td><p>'나쁨' 상태로 ReceiveSendQuality 이벤트가 발생한 세션의 비율입니다.</p>
<p>지터 또는 패킷 손실 측면의 네트워크 품질이 심각하고 수신 중인 오디오 품질에 영향을 줍니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>NetworkDelayEventRatio</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p> </p></td>
<td><p>'나쁨' 상태로 Delay 이벤트가 발생한 세션의 비율입니다. 네트워크 지연 시간이 심각하고 대화형 통신을 방지하여 사용 환경에 영향을 줍니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>NetworkBandwidthLowEventRatio</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p> </p></td>
<td><p>'나쁨' 상태로 LowBandwidth 이벤트가 발생한 세션의 비율입니다. 허용 가능한 수준의 음성 환경을 위해 사용할 수 있는 대역폭이 부족합니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CPUInsufficientEventRatio</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p> </p></td>
<td><p>'나쁨' 상태로 CPU 부족 이벤트가 발생한 세션의 비율입니다. 사용 중인 현재 형식 및 응용 프로그램을 처리하는 데 필요한 CPU 주기가 부족합니다. 이로 인해 오디오 채널에 왜곡이 발생합니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceHalfDuplexAECEventRatio</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p> </p></td>
<td><p>'나쁨' 상태로 DeviceHalfDuplexAEC 이벤트가 발생한 세션의 비율입니다. 에코 방지를 위해 시스템이 반이중 방식으로 전환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceRenderNotFunctioningEventRatio</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p> </p></td>
<td><p>'나쁨' 상태로 DeviceRenderNotFunctioning 이벤트가 발생한 세션의 비율입니다. 세션에 현재 사용 중인 렌더링 장치가 올바르게 작동하지 않습니다. 이로 인해 한 방향 오디오 문제가 발생합니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceCaptureNotFunctioningEventRatio</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p> </p></td>
<td><p>'나쁨' 상태로 DeviceCaptureNotFunctioning 이벤트가 발생한 세션의 비율입니다. 세션에 현재 사용 중인 캡처 장치가 올바르게 작동하지 않습니다. 이로 인해 한 방향 오디오 문제가 발생합니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceGlitchesEventRatio</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p> </p></td>
<td><p>'나쁨' 상태로 DeviceGlitches 이벤트가 발생한 세션의 비율입니다. 오디오 렌더링에 심각한 결함이 발생하여 왜곡을 일으킵니다. 이러한 결함은 드라이버 문제, DPC(Deferred Procedure Call) 폭풍(드라이버) 및 높은 CPU 사용량으로 인해 발생할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceLowSNREventRatio</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p> </p></td>
<td><p>'나쁨' 상태로 DeviceLowSNR 이벤트가 발생한 세션의 비율입니다. 캡처 기능이 매우 나쁘고 잡음이 심하거나 사용자가 마이크에서 너무 멀리 떨어져서 말합니다. 이로 인해 왜곡이 발생합니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceLowSpeechLevelEventRatio</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p> </p></td>
<td><p>'나쁨' 상태로 DeviceLowSpeechLevel 이벤트가 발생한 세션의 비율입니다. 사용자의 음성 수준이 너무 낮고 시스템에서 이를 더 이상 늘릴 수 없습니다. 이로 인해 왜곡이 발생하거나 한 방향 오디오로 인식될 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceClippingEventRatio</strong></p></td>
<td><p>Decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>'나쁨' 상태로 DeviceClipping 이벤트가 발생한 세션의 비율입니다.</p>
<p>니어 엔드 음성이 마이크에 클리핑되면 클리핑으로 인해 파 엔드쪽에서 왜곡되어 들립니다. 이 값은 니어 엔드 마이크 클리핑을 방지하기 위해 중요합니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceEchoEventRatio</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p> </p></td>
<td><p>'나쁨' 상태로 DeviceEchoEvent 이벤트가 발생한 세션의 비율입니다. 장치 또는 설정으로 인해 시스템에서 보정할 수 있는 범위를 넘는 에코가 발생합니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceNearEndToEchoRatioEventRatio</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p> </p></td>
<td><p>'나쁨' 상태로 DeviceNearEndToEchoRatio 이벤트가 발생한 세션의 비율입니다. 사용자에게 쉽게 방해가 되는 수준을 제한하기 때문에 사용자 환경에 영향을 주는 캡처되는 에코에 비해 사용자의 음성 수준이 너무 낮습니다. 스피커 볼륨을 줄이고, 마이크를 조금 더 가까이 대고 말하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceMultipleEndpointsEventCount</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>세션 중에 '나쁨' 상태로 DeviceMultipleEndpoints 이벤트가 발생한 횟수입니다. 동일 세션에서 오디오 끝점이 여러 번 검색되었으며 렌더링 볼륨을 낮춰서 보정이 수행되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceHowlingEventCount</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>세션 중에 '나쁨' 상태로 DeviceHowlingEvent 이벤트가 발생한 횟수입니다. 오디오 피드백 루프(오디오 경로를 공유하는 여러 끝점에서 발생함)가 검색되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceRenderZeroVolumeEventRatio</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p></p></td>
<td><p>'나쁨' 상태로 DeviceRenderZeroVolume 이벤트가 발생한 세션의 백분율입니다. 렌더링 장치가 0 볼륨으로 설정되었습니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceRenderMuteEventRatio</strong></p></td>
<td><p>decimal(5.2)</p></td>
<td><p></p></td>
<td><p>'나쁨' 상태로 DeviceRenderMute 이벤트가 발생한 세션의 백분율입니다. 렌더링 장치가 음소거되었습니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
</tbody>
</table>

