---
title: 'Lync Server 2013: MediaLine 테이블'
TOCTitle: MediaLine 테이블
ms:assetid: 414b1d63-ae97-4c27-bac0-c9ad0f808ff0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425920(v=OCS.15)
ms:contentKeyID: 49303435
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 MediaLine 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

각 레코드는 하나의 미디어 회선을 나타냅니다. 하나의 오디오 세션은 일반적으로 하나의 오디오 미디어 회선을 포함합니다. 회의 장치를 사용하거나 갤러리 보기를 사용할 경우 2개의 비디오 미디어 회선이 세션에 포함될 수도 있지만, 하나의 A/V(오디오 및 비디오) 세션은 일반적으로 오디오 미디어 회선 1개와 비디오 미디어 회선 1개가 포함됩니다.


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
<td><p><a href="lync-server-2013-session-table.md">Lync Server 2013의 Session 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSeq</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p><a href="lync-server-2013-session-table.md">Lync Server 2013의 Session 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediaLineLabel</strong></p></td>
<td><p>tinyint</p></td>
<td><p>기본</p></td>
<td><p>0은 기본 오디오, 1은 기본 비디오, 2는 파노라마 비디오, 3은 응용 프로그램/데스크톱 공유입니다. 이 레이블은 단일 세션 내에서 고유해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConnectivityIce</strong></p></td>
<td><p>tinyint</p></td>
<td><p> </p></td>
<td><p>이 열은 제공되었지만 Microsoft Lync Server 2013에서 사용되지 않습니다. 미디어 회선에 사용되는 연결에 대한 정보는 CallerConnectivityICE 및 CalleeConnectivityICE 열에 표시되어 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerIceWarningFlags</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>비트 플래그로 설명된 ICE(Interactive Connectivity Establishment) 프로세스에 대한 정보입니다. 자세한 내용은 다운로드할 수 있는 <em>체감 품질 모니터링 서버 프로토콜 사양</em> 을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeIceWarningFlags</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>CallerIceWarningFlags와 동일하지만 수신자 측에 있습니다. 자세한 내용은 다운로드할 수 있는 <em>체감 품질 모니터링 서버 프로토콜 사양</em> 을 참고하세요.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Security</strong></p></td>
<td><p>tinyint</p></td>
<td><p> </p></td>
<td><p>사용 중인 보안 프로필입니다. 0은 NONE, 1은 SRTP, 2는 V1입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>Transport</strong></p></td>
<td><p>tinyint</p></td>
<td><p> </p></td>
<td><p>0은 UDP, 1은 TCP입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>발신자의 IP 주소입니다. 자세한 내용은 <a href="lync-server-2013-ipaddress-table.md">Lync Server 2013의 IPAddress 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerPort</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>발신자가 사용한 포트입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerSubnet</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>발신자의 서브넷입니다. 자세한 내용은 <a href="lync-server-2013-ipaddress-table.md">Lync Server 2013의 IPAddress 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerInside</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>1은 발신자가 회사 네트워크 내에 있음을 의미하고 0은 발신자가 네트워크 외부에 있음을 의미합니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerMacAddress</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p><a href="lync-server-2013-macaddress-table.md">Lync Server 2013의 MacAddress 테이블</a>에 참조된 발신자의 MAC 주소입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerRelayIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>발신자가 사용하는 Lync Server A/V 에지 서비스의 IP 주소입니다. 자세한 내용은 <a href="lync-server-2013-ipaddress-table.md">Lync Server 2013의 IPAddress 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerRelayPort</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>A/V 에지 서비스에서 발신자가 사용한 포트입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerCaptureDev</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>발신자가 사용한 캡처 장치입니다. <a href="lync-server-2013-device-table.md">Lync Server 2013의 Device 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerRenderDev</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>발신자가 사용한 렌더링 장치입니다. <a href="lync-server-2013-device-table.md">Lync Server 2013의 Device 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerCaptureDevDriver</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>발신자의 캡처 장치에 대한 드라이버입니다. <a href="lync-server-2013-devicedriver-table.md">Lync Server 2013의 DeviceDriver 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerRenderDevDriver</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>발신자의 렌더링 장치에 대한 드라이버입니다. <a href="lync-server-2013-devicedriver-table.md">Lync Server 2013의 DeviceDriver 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerNetworkConnectionType</strong></p></td>
<td><p>tinyint</p></td>
<td><p>외래</p></td>
<td><p>발신자가 네트워크에 연결한 방식을 나타냅니다. 값은 <a href="lync-server-2013-networkconnectiondetail-table.md">Lync Server 2013의 NetworkConnectionDetail 테이블</a>에서 수집됩니다. 일반적으로 값은 유선 연결의 경우 0, Wi-Fi 연결의 경우 1, 이더넷 연결의 경우 3입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerBssid</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>무선이 사용된 경우 발신자의 BSSID입니다. <a href="lync-server-2013-macaddress-table.md">Lync Server 2013의 MacAddress 테이블</a>에서 참조됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerVPN</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>발신자의 링크입니다. 1은 VPN(가상 사설망), 0은 비VPN입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerLinkSpeed</strong></p></td>
<td><p>decimal(18.0)</p></td>
<td><p></p></td>
<td><p>발신자의 끝점에 대한 네트워크 연결 속도(bps)입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>통화 수신자의 IP 주소입니다. 자세한 내용은 <a href="lync-server-2013-ipaddress-table.md">Lync Server 2013의 IPAddress 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleePort</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>통화 수신자가 사용한 포트입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeSubnet</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>수신자의 서브넷입니다. 자세한 내용은 <a href="lync-server-2013-ipaddress-table.md">Lync Server 2013의 IPAddress 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeInside</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>1은 통화 수신자가 회사 네트워크 내에 있음을 의미하고 0은 통화 수신자가 네트워크 외부에 있음을 의미합니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeMacAddress</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>수신자의 Mac 주소입니다. <a href="lync-server-2013-macaddress-table.md">Lync Server 2013의 MacAddress 테이블</a>에서 참조됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeRelayIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>통화 수신자가 사용하는 A/V 에지 서비스의 IP 주소입니다. 자세한 내용은 <a href="lync-server-2013-ipaddress-table.md">Lync Server 2013의 IPAddress 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeRelayPort</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>A/V 에지 서비스에서 통화 수신자가 사용한 포트입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeCaptureDev</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>통화 수신자가 사용한 캡처 장치입니다. <a href="lync-server-2013-device-table.md">Lync Server 2013의 Device 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeRenderDev</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>통화 수신자가 사용한 렌더링 장치입니다. <a href="lync-server-2013-device-table.md">Lync Server 2013의 Device 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeCaptureDevDriver</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>통화 수신자의 캡처 장치에 대한 드라이버입니다. <a href="lync-server-2013-devicedriver-table.md">Lync Server 2013의 DeviceDriver 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeRenderDevDriver</strong></p></td>
<td><p>varchar(256)</p></td>
<td><p>외래</p></td>
<td><p>통화 수신자의 렌더링 장치에 대한 드라이버입니다. <a href="lync-server-2013-devicedriver-table.md">Lync Server 2013의 DeviceDriver 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeNetworkConnectionType</strong></p></td>
<td><p>tinyint</p></td>
<td><p>외래</p></td>
<td><p>수신자가 네트워크에 연결한 방식을 나타냅니다. 값은 <a href="lync-server-2013-networkconnectiondetail-table.md">Lync Server 2013의 NetworkConnectionDetail 테이블</a>에서 수집됩니다. 일반적으로 값은 유선 연결의 경우 0, Wi-Fi 연결의 경우 1, 이더넷 연결의 경우 3입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeBssid</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>무선이 사용된 경우 발신자의 BSSID입니다. <a href="lync-server-2013-macaddress-table.md">Lync Server 2013의 MacAddress 테이블</a>에서 참조됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeVPN</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>통화 수신자의 링크입니다. 1은 VPN(가상 사설망), 0은 비VPN입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeLinkSpeed</strong></p></td>
<td><p>decimal(18.0)</p></td>
<td><p> </p></td>
<td><p>통화 수신자의 끝점에 대한 네트워크 연결 속도(bps)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConversationalMOS</strong></p></td>
<td><p>decimal(3.2)</p></td>
<td><p> </p></td>
<td><p>오디오 세션의 협대역 대화 MOS입니다(두 오디오 스트림을 모두 기반으로 함).</p></td>
</tr>
<tr class="even">
<td><p><strong>AppliedBandwidthLimit</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>다양한 정책 설정(TURN, API, SDP, 정책 서버 등)이 제공된 지정된 송신측 스트림에 적용되는 실제 대역폭입니다. 이 대역폭은 대역폭 예상에 따라 유효 대역폭이 더 낮을 수 있으므로 유효 대역폭과 혼동해서는 안됩니다. 이 대역폭은 기본적으로 대역폭 예상치로 지정된 한도를 제외하고 송신 스트림이 사용할 수 있는 최대 대역폭입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AppliedBandwidthSourceKey</strong></p></td>
<td><p>smallint</p></td>
<td><p></p></td>
<td><p>적용 중인 대역폭 용량의 원본입니다. 이 원본은 대역폭 제한이 시작되는 위치(&quot;정책 서버&quot;, &quot;TURN 서버&quot; 또는 &quot;형식&quot; 등)를 설명합니다. <a href="lync-server-2013-appliedbandwidthsource-table.md">Lync Server 2013의 AppliedBandwidthSource 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p><strong>발신자</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>발신자의 메트릭이 수신되었는지 여부를 나타냅니다. 1은 예, null 값은 아니요입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>수신자</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>통화 수신자의 메트릭이 수신되었는지 여부를 나타냅니다. 1은 예, null 값은 아니요입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>MidCallReport</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>보고서가 세션의 일부 또는 전체 세션에 해당하는지 여부를 나타냅니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClassifiedPoorCall</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>통화가 불량 통화(값 1) 또는 정상 통화(0)로 분류되었는지 여부를 나타냅니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerConnectivityICE</strong></p></td>
<td><p>tinyInt</p></td>
<td><p></p></td>
<td><p>발신자가 ICE 프로토콜(Internet Connectivity Establishment)을 사용하여 네트워크에 연결되었는지 여부를 나타냅니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeConnectivityICE</strong></p></td>
<td><p>tinyint</p></td>
<td><p></p></td>
<td><p>발신자가 ICE 프로토콜(Internet Connectivity Establishment)을 사용하여 네트워크에 연결되었는지 여부를 나타냅니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerReflexiveLocalIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>통화를 시작한 사용자의 재귀적 IP 주소입니다. NAT(Network Address Translation)를 사용하는 조직에서 재귀적 IP 주소는 프록시 서버의 IP 주소입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerWiFiDriverDevicesDesc</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>통화를 시작한 사용자가 사용한 WiFi 드라이버에 대한 장치 설명입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerWiFiDriverVersion</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>통화를 시작한 사용자가 사용한 WiFi 드라이버의 버전 번호입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleReflexiveLocalIPAddr</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>통화를 수신한 사용자의 재귀적 IP 주소입니다. NAT(Network Address Translation)를 사용하는 조직에서 재귀적 IP 주소는 프록시 서버의 IP 주소입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeWiFiDriverDevicesDesc</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>통화를 수신한 사용자가 사용한 WiFi 드라이버에 대한 장치 설명입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeWiFiDriverVersion</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>통화를 수신한 사용자가 사용한 WiFi 드라이버의 버전 번호입니다.</p>
<p>이 열은 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
</tbody>
</table>

