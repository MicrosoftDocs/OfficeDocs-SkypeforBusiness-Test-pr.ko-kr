---
title: 포트 요약 - 공용 인스턴트 메시징 연결
TOCTitle: 포트 요약 - 공용 인스턴트 메시징 연결
ms:assetid: f46756ec-1401-4ca2-a4a4-5cd28bcfdc7f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ618376(v=OCS.15)
ms:contentKeyID: 49305529
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 포트 요약 - 공용 인스턴트 메시징 연결

 

_**마지막으로 수정된 항목:** 2015-03-09_

공용 인스턴트 메시징 연결을 지원하는 데 필요한 포트 및 프로토콜용으로 방화벽을 구성하려는 경우, 공용 IM 공급자의 연락처가 Lync 클라이언트에 연락하거나 Lync에서 공용 IM 연락처에 연락할 수 있는 기능을 고려하여 SIP/MTLS/TCP 5061은 양방향이라는 점을 일단 염두에 두어야 합니다.

Windows Live Messenger는 Lync 클라이언트와의 오디오/비디오 통신에 참가할 수 있습니다. 일반적으로 방화벽에 사용하는 매우 유사한 방화벽 포트 및 프로토콜 구성에서 Lync 클라이언트를 외부 사용자로 지원할 수 있는 것은 바로 이때문입니다.


> [!IMPORTANT]
> Lync는 전 세계의 여러 조직과 개별 사용자를 연결해 주는 매우 효율적인 도구입니다. Lync Standard CAL(클라이언트 액세스 라이선스) 외의 추가 사용자/장치 라이선스가 없어도 Windows Live Messenger와의 페더레이션이 가능합니다. Skype 페더레이션도 이 목록에 추가될 예정이므로 Lync 사용자는 IM 및 음성을 통해 수많은 사람들과 연결할 수 있습니다.<BR>Messenger 클라이언트 연락처와의 페더레이션은 중국 본토를 제외하고는 2013년 3월 15일에 공식적으로 종료됩니다. 이전에 Messenger를 사용했던 페더레이션 사용자에게는 Skype가 페더레이션 클라이언트로 제공됩니다.



## 방화벽 요약 - 공용 인스턴트 메시징 연결


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>역할/프로토콜/TCP 또는 UDP/포트</th>
<th>원본 IP 주소</th>
<th>대상 IP 주소</th>
<th>참고</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>액세스/SIP(MTLS)/TCP/5061</p></td>
<td><p>공용 IM 연결 파트너</p></td>
<td><p>에지 서버 액세스 인터페이스</p></td>
<td><p>SIP를 사용한 페더레이션 및 공용 IM 연결용</p></td>
</tr>
<tr class="even">
<td><p>액세스/SIP(MTLS)/TCP/5061</p></td>
<td><p>에지 서버 액세스 인터페이스</p></td>
<td><p>공용 IM 연결 파트너</p></td>
<td><p>SIP를 사용한 페더레이션 및 공용 IM 연결용</p></td>
</tr>
<tr class="odd">
<td><p>액세스/SIP(TLS)/TCP/443</p></td>
<td><p>클라이언트</p></td>
<td><p>에지 서버 액세스 인터페이스</p></td>
<td><p>외부 사용자 액세스를 위한 클라이언트-서버 SIP 트래픽</p></td>
</tr>
<tr class="even">
<td><p>A/V/RTP/TCP/50,000-59,999</p></td>
<td><p>에지 서버 액세스 인터페이스</p></td>
<td><p>Live Messenger 클라이언트</p></td>
<td><p>공용 IM 연결이 구성된 경우 Windows Live Messenger와의 A/V 세션에 사용됨</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>에지 서버 액세스 인터페이스</p></td>
<td><p>Live Messenger 클라이언트</p></td>
<td><p>Windows Live Messenger와의 공용 IM 연결 시 필수</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Live Messenger 클라이언트</p></td>
<td><p>에지 서버 액세스 인터페이스</p></td>
<td><p>Windows Live Messenger와의 공용 IM 연결 시 필수</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 개념

[Lync Server 2013의 외부 사용자 액세스에 대한 시나리오](lync-server-2013-scenarios-for-external-user-access.md)  
[Lync Server 2013에 대한 외부 A/V 방화벽 및 포트 요구 사항 확인](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md)

