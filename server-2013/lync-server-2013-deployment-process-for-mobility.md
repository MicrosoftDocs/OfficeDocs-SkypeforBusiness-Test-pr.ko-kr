---
title: 'Lync Server 2013: 모바일 기능 배포 프로세스'
TOCTitle: 모바일 기능 배포 프로세스
ms:assetid: 5a1cebda-c14b-4ff4-9c36-f7caa868160f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690023(v=OCS.15)
ms:contentKeyID: 49303731
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 모바일 기능 배포 프로세스

 

_**마지막으로 수정된 항목:** 2015-03-09_

    Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013. It is noted accordingly.

이 섹션에서는 Lync Server 2013 모바일 기능을 배포하기 위해 수행해야 하는 단계를 순서대로 설명합니다.

### 모바일 기능 배포 프로세스

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>단계</th>
<th>절차</th>
<th>사용 권한</th>
<th>배포 설명서</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DNS(Domain Name System) 레코드 만들기</p></td>
<td><ul>
<li><p>내부 자동 검색 서비스 URL을 확인하기 위한 내부 DNS CNAME 또는 A(호스트, IPv6의 경우 AAAA) 레코드를 만듭니다.</p></li>
<li><p>외부 자동 검색 서비스 URL을 확인하기 위한 외부 DNS CNAME 또는 A(호스트, IPv6의 경우 AAAA) 레코드를 만듭니다.</p></li>
</ul></td>
<td><p>DomainAdmins</p>
<p>DnsAdmins</p></td>
<td><p><a href="lync-server-2013-creating-dns-records-for-the-autodiscover-service.md">Lync Server 2013에서 자동 검색 서비스용 DNS 레코드 만들기</a></p></td>
</tr>
<tr class="even">
<td><p>인증서 수정</p></td>
<td><p>모바일 사용자에 대한 보안 연결을 지원하기 위해 다음 인증서에 주체 대체 이름 항목을 추가합니다.</p>
<ul>
<li><p>디렉터 인증서</p></li>
<li><p>프런트 엔드 풀 인증서</p></li>
<li><p>역방향 프록시 인증서</p></li>
</ul></td>
<td><p>로컬 관리자</p></td>
<td><p><a href="lync-server-2013-modifying-certificates-for-mobility.md">Lync Server 2013에서 모바일 기능용으로 인증서 수정</a></p></td>
</tr>
<tr class="odd">
<td><p>역방향 프록시 구성</p></td>
<td><ul>
<li><p>주체 대체 이름으로 업데이트된 인증서를 SSL(Secure Sockets Layer) 수신기에 지정합니다.</p></li>
<li><p>외부 자동 검색 서비스 URL에 대해 웹 게시 규칙을 다시 구성합니다.</p></li>
<li><p>프런트 엔드 풀에서 외부 Lync Server 2013 웹 서비스에 대한 웹 게시 규칙이 있는지 확인합니다.</p></li>
</ul>
<p>또는</p>
<ul>
<li><p>초기 자동 검색 요청에 대해 HTTP를 사용하고 인증서에서 주체 대체 이름 목록을 업데이트하지 않으려는 경우 포트 80(HTTP)에 대해 새 웹 게시 규칙을 구성하거나 기존 게시 규칙을 다시 구성합니다.</p></li>
</ul></td>
<td><p>로컬 관리자</p></td>
<td><p><a href="lync-server-2013-configuring-the-reverse-proxy-for-mobility.md">Lync Server 2013에서 모바일 기능에 대해 역방향 프록시 구성</a></p></td>
</tr>
<tr class="even">
<td><p>Mcx Mobility Service를 사용하여 Lync 2010 Mobile에 대한 모바일 배포 테스트</p></td>
<td><p><strong>Test-CsMcxP2PIM</strong>을 실행하여 사용자 간의 인스턴트 메시지 전송을 테스트합니다.</p>
<p>전체 옵션 목록은 Lync Server 관리 셸 cmdlet 설명서에서 <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsMcxP2PIM">Test-CsMcxP2PIM</a>를 참조하십시오.</p></td>
<td><p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-verifying-your-mobility-deployment.md">Lync Server 2013에서 모바일 기능 배포 확인</a></p></td>
</tr>
<tr class="odd">
<td><p>UCWA 웹 구성 요소를 사용하여 Lync 2013 모바일 클라이언트에 대한 모바일 배포 테스트</p></td>
<td><p><strong>Test-CsUcwaConference</strong> cmdlet을 사용하여 미리 정의된 테스트 사용자 또는 실제 사용자 쌍이 UCWA를 사용해 회의를 만들고 회의에 참가할 수 있는지를 테스트 및 확인합니다.</p>
<p>전체 옵션 목록은 Lync Server 관리 셸 cmdlet 설명서에서 <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsUcwaConference">Test-CsUcwaConference</a>를 참조하십시오.</p></td>
<td><p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-verifying-your-mobility-deployment.md">Lync Server 2013에서 모바일 기능 배포 확인</a></p></td>
</tr>
<tr class="even">
<td><p>푸시 알림 구성</p></td>
<td><ul>
<li><p>Lync Server 2013에지 서버에 대해 Lync Server 온라인 호스팅 공급자를 추가하고 호스팅 공급자 페더레이션을 구성합니다.</p></li>
<li><p>Lync Server 2010에지 서버에 대해 Lync Server 온라인 호스팅 공급자를 추가하고 호스팅 공급자 페더레이션을 구성합니다.</p></li>
<li><p>Office Communications Server 2007 R2에지 서버에 대해 페더레이션 파트너를 추가합니다.</p></li>
<li><p>Wi-Fi 네트워크를 통해 푸시 알림을 지원하려면 TCP 포트 5223에 대한 아웃바운드 방화벽 규칙을 구성합니다.</p></li>
<li><p><strong>Set-CsPushNotificationConfiguration</strong> cmdlet을 사용하여 APNS(Apple 푸시 알림 서비스) 및 MPNS(Microsoft 푸시 알림 서비스)에 대해 푸시 알림을 사용하도록 설정합니다. 이 기능은 기본적으로 사용되지 않습니다.</p></li>
<li><p><strong>Test-CsFederatedPartner</strong> cmdlet을 사용하여 페더레이션 구성을 테스트하고 <strong>Test-CsMCXPushNotification</strong> cmdlet을 사용하여 푸시 알림을 테스트합니다.</p>


> [!NOTE]
> 푸시 알림은 Apple 장치 및 Windows Phone에서 Lync 2010 Mobile 클라이언트에 대해 사용됩니다.<BR>푸시 알림은 Windows Phone의 Lync 2013 모바일 클라이언트에만 필요합니다.


</li>
</ul></td>
<td><p>RtcUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-configuring-for-push-notifications.md">Lync Server 2013의 푸시 알림 구성</a></p></td>
</tr>
<tr class="odd">
<td><p>모바일 기능 정책 구성</p></td>
<td><p><strong>Set-CsMobilityPolicy</strong> cmdlet을 사용하여 다음을 허용하거나 거부합니다.</p>
<ul>
<li><p>Call via Work(회사번호로 전화)</p></li>
<li><p>IP 오디오 및 IP 비디오 사용</p></li>
<li><p>IP 오디오 및/또는 IP 비디오에 대해 Wi-Fi 필요</p></li>
</ul></td>
<td><p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configuring-mobility-policy.md">Lync Server 2013에서 모바일 정책 구성</a></p></td>
</tr>
</tbody>
</table>

