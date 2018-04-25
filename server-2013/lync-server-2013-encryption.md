---
title: Lync Server 2013의 암호화
TOCTitle: Lync Server 2013의 암호화
ms:assetid: d18c74a6-385b-407b-98eb-0d525fa38fea
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn481135(v=OCS.15)
ms:contentKeyID: 59679298
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 암호화

 

_**마지막으로 수정된 항목:** 2015-03-09_

Microsoft Lync Server 2013은 TLS 및 MTLS를 사용하여 메신저 대화를 암호화합니다. 모든 서버 간 트래픽에는 트래픽이 내부 네트워크로 국한되는지 내부 네트워크 경계를 교차하는지 여부에 상관없이 MTLS가 있어야 합니다. TLS는 선택 사항이지만 중재 서버와 미디어 게이트웨이 간에 권장됩니다. 이 연결에 TLS가 구성되어 있는 경우 MTLS가 필요합니다. 따라서 게이트웨이는 중재 서버에서 트러스트된 CA의 인증서로 구성해야 합니다.

클라이언트 간 트래픽에 대한 요구 사항은 해당 트래픽이 내부 회사 방화벽을 교차하는지 여부에 따라 달라집니다. 엄밀히 말해, 내부 트래픽은 메신저 대화가 암호화되는 경우 TLS를, 암호화되지 않는 경우 TCP를 사용할 수 있습니다.

다음 표에는 각 트래픽 유형에 대한 프로토콜 요구 사항이 요약되어 있습니다.

### 트래픽 보호

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>트래픽 유형</th>
<th>보호 주체</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>서버 간</p></td>
<td><p>MTLS</p></td>
</tr>
<tr class="even">
<td><p>클라이언트-서버</p></td>
<td><p>TLS</p></td>
</tr>
<tr class="odd">
<td><p>메신저 대화 및 현재 상태</p></td>
<td><p>TLS(TLS에 대해 구성된 경우)</p></td>
</tr>
<tr class="even">
<td><p>오디오 및 비디오, 미디어의 데스크톱 공유</p></td>
<td><p>SRTP</p></td>
</tr>
<tr class="odd">
<td><p>데스크톱 공유(신호)</p></td>
<td><p>TLS</p></td>
</tr>
<tr class="even">
<td><p>웹 회의</p></td>
<td><p>TLS</p></td>
</tr>
<tr class="odd">
<td><p>모임 콘텐츠 다운로드, 주소록 다운로드, 메일 그룹 확장</p></td>
<td><p>HTTPS</p></td>
</tr>
</tbody>
</table>


## 미디어 암호화

미디어 트래픽은 RTP 트래픽에 기밀성, 인증, 반복 공격 보호를 제공하는 RTP(Real-Time Transport Protocol) 프로필인 SRTP(보안 RTP)를 사용해 암호화됩니다. SRTP는 서버 요청의 성공적인 인증에 대한 응답으로 미디어 참가자를 대신해 미디어 중계 인증 서비스가 생성한 세션 키를 사용합니다. 세션 키는 프런트 엔드 서버가 미디어 중계 인증 서비스에 제공한 협상된 사용자 이름과 암호에 의해 보안이 유지되며, TLS 보안 SIP 채널을 통해 참가자에게 전송됩니다. 미디어 중계 서비스가 사용한 사용자 이름 및 암호로 보안 세션 키의 암호를 해독하고 참가자의 TLS 인증서 및 보안 SIP 채널을 사용하여 안전한 방식으로 제공된 경우,참가자는 SRTP 시스템을 해독할 수 있습니다. 또한 중재 서버 및 이것의 내부 홉 간 미디어 흐름도 SRTP를 사용하여 암호화됩니다. 중재 서버 및 미디어 게이트웨이 간 양방향 미디어 흐름은 암호화되지 않습니다. 중재 서버는 미디어 게이트웨이에 대한 암호화를 지원하지만, 게이트웨이가 MTLS 및 인증서 저장소를 지원해야 합니다.


> [!NOTE]
> Windows Live Messenger의 새 버전에서 A/V(오디오/비디오)가 지원됩니다. Windows Live Messenger를 사용하여 A/V 페더레이션을 구현할 경우 Lync Server 암호화 수준도 수정해야 합니다. 기본적으로 암호화 수준은 필수입니다. 이 설정은 Lync Server 관리 셸을 사용하여 지원됨으로 변경해야 합니다. 자세한 내용은 배포 설명서의 <A href="lync-server-2013-deploying-external-user-access.md">Lync Server 2013에서 외부 사용자 액세스 배포</A>를 참고하세요.



Microsoft Lync 2013 및 Windows Live 클라이언트 간에는 오디오 및 비디오 미디어 트래픽이 암호화되지 않습니다.

## FIPS

Lync Server 2013 및 Microsoft Exchange Server 2013은 Windows Server 운영 체제가 시스템 암호화에 FIPS 140-2 알고리즘을 사용하도록 구성된 경우, FIPS(Federal Information Processing Standard) 140-2 알고리즘의 지원을 받아 작동합니다. FIPS 지원을 받으려면 Lync Server 2013을 실행하는 각 서버가 이를 지원하도록 구성되어야 합니다. FIPS 호환 알고리즘 사용 및 FIPS 지원을 받는 방법에 대한 자세한 내용은 Microsoft 기술 자료 문서 811833, Windows XP 이상 버전의 Windows에서 “시스템 암호화: 암호화, 해시, 서명을 위해 FIPS 호환 알고리즘 사용" 보안 설정을 사용할 경우 효과([http://go.microsoft.com/fwlink/p/?linkid=3052\&kbid=811833](http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=811833))를 참고하세요. FIPS 140-2 지원 및 Exchange 2010의 제한 사항에 대한 자세한 내용은 SP1 및 FIPS 호환 알고리즘에 대한 지원([http://go.microsoft.com/fwlink/p/?LinkId=205335](http://go.microsoft.com/fwlink/p/?linkid=205335)의 Exchange 2010)을 참고하세요.

