---
title: Lync Server 2013 소개
TOCTitle: Lync Server 소개
ms:assetid: 99dd6b65-e591-421f-852b-ee9fe9588998
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398795(v=OCS.15)
ms:contentKeyID: 49304491
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 소개

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 및 해당 클라이언트 소프트웨어(예: Lync 2013)를 사용하면 사용자가 실제 위치에 상관없이 새로운 방식으로 연결하고 연결 상태를 유지할 수 있습니다. Lync와 Lync Server는 단일 클라이언트 인터페이스에서 통신하는 서로 다른 방법을 제공하며 통합 플랫폼으로 배포되고 단일 관리 인프라를 통해 관리됩니다.

아래 표와 다음 섹션에서는 Lync Server이 사용자에게 제공하는 주요 기능 또는 *작업* 을 설명합니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>작업</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IM 및 현재 상태</p></td>
<td><p>IM(인스턴트 메시징) 및 현재 상태를 통해 사용자는 효율적이고 효과적으로 대화 상대를 찾아 통신할 수 있습니다.</p>
<p>IM은 대화 기록 기능이 있는 인스턴트 메시징 플랫폼을 제공하며 MSN/Windows Live, Yahoo!, AOL 및 Google Talk와 같은 공용 IM 네트워크 사용자와의 공용 IM 연결을 지원합니다.</p>


> [!IMPORTANT]
> <UL>
> <LI>
> <P>2012년 9월 1일 현재 신규 또는 갱신 계약에 대해 Microsoft Lync "PIC USL"(공용 메신저 연결 사용자 구독 라이선스)을 더 이상 구입할 수 없습니다. 유효 라이선스를 보유한 고객은 서비스 종료 날짜까지 Yahoo! Messenger와 계속 페더레이션할 수 있습니다. AOL 및 Yahoo!는 서비스 종료 날짜를 2014년 6월로 발표했습니다. 자세한 내용은 <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Lync Server 2013의 공용 메신저 연결 지원</A>을 참고하세요.</P>
> <LI>
> <P>PIC USL은 Lync Server 또는 Office Communications Server가 Yahoo! Messenger와 페더레이션하는 데 필요한 월별 사용자 단위 구독 라이선스입니다. Microsoft는 Yahoo!의 지원 여부에 따라 이 서비스를 제공할 수 있었으며 해당 서비스의 기본 계약은 곧 종료될 예정입니다.</P>
> <LI>
> <P>Lync는 전 세계의 여러 조직과 개별 사용자를 연결해 주는 매우 효율적인 도구입니다. Lync Standard CAL 외의 추가 사용자/장치 라이선스가 없어도 Windows Live Messenger와의 페더레이션이 가능합니다. Skype 페더레이션도 이 목록에 추가될 예정이므로 Lync 사용자는 메신저 및 음성을 통해 수많은 사람들과 연결할 수 있습니다.</P></LI></UL>



<p>현재 상태는 <strong>대화 가능</strong> 또는 <strong>다른 용무 중</strong> 과 같은 일반 상태와 <strong>곧 돌아오겠음</strong> 및 <strong>방해 금지</strong> 와 같은 보다 상세한 상태를 사용하여 사용자의 개인 상태 및 통신 의사를 설정하고 표시합니다. 이 향상된 현재 상태 정보를 통해 다른 사용자가 효과적인 통신을 즉시 선택할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p>회의</p></td>
<td><p>Lync Server은 예약 모임과 즉석 모임 모두에 대해 IM 회의, 오디오 회의, 웹 회의, 비디오 회의 및 응용 프로그램 공유를 지원합니다. 이러한 모임 유형이 모두 단일 클라이언트로 지원됩니다. 또한 Lync Server에서는 PSTN(공중 전화망) 사용자가 전화 회의의 오디오 부분에 참가할 수 있도록 전화 접속 회의를 지원합니다.</p>
<p>전화 회의는 실시간으로 원활하게 변경되고 확대될 수 있습니다. 예를 들어 단일 전화 회의가 소수의 사용자 간에 인스턴트 메시지로 시작되어 데스크톱 공유를 지원하고 대화의 흐름을 중단하지 않고도 더 많은 대상이 즉시 쉽게 참가할 수 있는 오디오 회의로 확대될 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p>Enterprise Voice</p></td>
<td><p><em>Enterprise Voice</em> 는 Lync Server에서 제공되는 VoIP(Voice over Internet Protocol)로서, 기존 PBX(Private Branch Exchange) 시스템을 향상시키거나 대체하는 음성 옵션을 제공합니다. IP PBX의 전체 전화 기능 외에도 Enterprise Voice는 향상된 현재 상태, IM, 공동 작업 및 모임과 통합됩니다. 통화 응답, 대기, 재개, 전송, 착신 전환 및 전달과 같은 기능이 직접 지원되며 개인 설정된 단축 키가 연락처 목록으로 대체되고 자동 인터폰이 IM으로 대체됩니다.</p>
<p>Enterprise Voice는 CAC(통화 허용 제어), 지점 지속 가능성 및 확장된 데이터 복구 옵션을 통해 고가용성을 지원합니다.</p></td>
</tr>
<tr class="even">
<td><p>원격 사용자 지원</p></td>
<td><p><em>에지 서버</em> 라는 서버를 배포하여 원격 사용자에 대한 연결을 제공함으로써 현재 조직 방화벽 외부에 있는 사용자에게 전체 Lync Server 기능을 제공할 수 있습니다. 이러한 원격 사용자는 Lync 2013이 설치된 개인 컴퓨터, 전화 또는 웹 인터페이스를 사용하여 전화 회의에 연결할 수 있습니다.</p>
<p>또한 에지 서버를 배포하면 파트너 또는 공급업체 조직과 <em>페더레이션</em> 할 수 있습니다. 페더레이션 관계를 설정하면 사용자가 대화 상대 목록에 페더레이션 사용자를 추가하고, 이러한 사용자와 현재 상태 정보 및 인스턴트 메시지를 교환하고, 이러한 사용자를 음성 통화, 화상 통화 및 전화 회의에 초대할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p>모바일 클라이언트 지원</p></td>
<td><p>또한 Lync Server Mobility Service를 사용하면 사용자가 지원되는 Apple iOS, Android, Windows Phone 또는 Nokia 모바일 장치를 통해 인스턴트 메시지 주고받기, 대화 상대 보기, 현재 상태 보기 등의 작업을 수행할 수 있습니다. 또한 모바일 장치에서는 클릭하여 회의 참가, 회사번호로 전화, 단일 번호 연결, 음성 메일, 부재 중 통화 등의 일부 Enterprise Voice 기능도 지원됩니다. 응용 프로그램의 백그라운드 실행을 지원하지 않는 모바일 장치에 대해 푸시 알림도 지원됩니다.</p></td>
</tr>
<tr class="even">
<td><p>다른 제품과 통합</p></td>
<td><p>Lync Server는 여러 가지 다른 제품과 통합되어 사용자 및 관리자에게 추가적인 이점을 제공합니다.</p>
<p>Outlook에 통합된 모임 도구를 사용하여 이끌이는 모임을 예약하거나 한 번의 클릭으로 즉석 전화 회의를 시작하고 참가자가 모임에 쉽게 참가하도록 할 수 있습니다.</p>
<p>현재 상태 정보는 Outlook과 SharePoint에 통합됩니다.</p>
<p>Exchange UM(통합 메시징)은 여러 가지 통합 기능을 제공합니다. 사용자는 Lync Server 내에서 새로운 음성 사서함이 있는지 확인할 수 있습니다. Outlook 메시지에서 재생 단추를 클릭하여 오디오 음성 메일을 듣거나 알림 메시지에 음성 메일의 기록을 볼 수 있습니다.</p>
<p>또한 Lync Server 2013과 Exchange 2013을 함께 사용하면 두 제품 클라이언트에서 모두 액세스할 수 있는 통합 연락처 저장소, Exchange 2013 데이터베이스에 저장되는 고해상도 연락처 사진 등 여러 가지 새로운 기능을 사용할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p>간단한 배포</p></td>
<td><p>서버와 클라이언트의 계획과 배포를 지원하기 위해 Lync Server에 토폴로지 작성기가 제공됩니다.</p>
<p></p>
<p>토폴로지 작성기는 Lync Server의 설치 구성 요소입니다. 토폴로지 작성기를 사용하여 계획된 토폴로지를 만들고 조정하고 게시할 수 있습니다. 또한 서버 설치를 시작하기 전에 토폴로지의 유효성을 검사할 수 있습니다. Lync Server를 개별 서버에 설치할 때 설치 프로그램에서 토폴로지에 지정된 대로 서버를 배포합니다.</p></td>
</tr>
<tr class="even">
<td><p>관리 용이성</p></td>
<td><p>Lync Server를 배포하면 다음과 같은 강력하고 효율적인 관리 도구를 얻을 수 있습니다.</p>
<ul>
<li><p>중앙 구성 관리 - 변경 내용을 중앙 집중식으로 관리하고 전체 배포에 빠르게 적용할 수 있도록 합니다.</p></li>
<li><p>Lync Server 제어판 - 웹 기반의 새로운 관리자용 그래픽 사용자 인터페이스입니다. 웹 기반 UI를 통해 Lync Server 관리자는 전문 관리 소프트웨어를 컴퓨터에 설치하지 않고도 회사 네트워크 어디에서나 시스템을 관리할 수 있습니다.</p></li>
<li><p>Windows PowerShell 명령줄 인터페이스을 기반으로 하는 Lync Server 관리 셸 명령줄 관리 도구 - 제품의 모든 면을 관리할 수 있는 다양한 명령 집합을 제공하며, Lync Server 관리자가 친숙한 도구를 사용하여 반복 작업을 자동화할 수 있도록 합니다.</p></li>
</ul></td>
</tr>
</tbody>
</table>


IM 및 현재 상태 기능은 모든 Lync Server 배포 시 자동으로 설치되지만 회의, Enterprise Voice 및 원격 사용자 액세스는 조직의 요구 사항에 따라 배포 여부를 선택할 수 있습니다.

## 이 단원의 내용

  - [Lync Server 2013의 메신저 및 현재 상태](lync-server-2013-im-and-presence.md)

  - [Lync Server 2013의 회의](lync-server-2013-conferencing.md)

  - [Lync Server 2013의 Enterprise Voice](lync-server-2013-enterprise-voice.md)

  - [Lync Server 2013의 확장성](lync-server-2013-scalability.md)

