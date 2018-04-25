---
title: 'Lync Server 2013: Lync 2013 에서 클라이언트 상호 운용성'
TOCTitle: Lync 2013 에서 클라이언트 상호 운용성
ms:assetid: 0f126571-91a2-45d5-855c-1e4ddb45fc04
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204672(v=OCS.15)
ms:contentKeyID: 49302814
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync 2013 에서 클라이언트 상호 운용성

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 항목에서는 Microsoft Lync Server 2013 클라이언트를 이전 버전의 Lync Server 및 Office Communications Server 클라이언트와 함께 사용하고 이들 클라이언트가 상호 작용하는 기능에 대해 설명합니다.

## 서버 및 클라이언트 호환성

다음 표에서는 클라이언트 버전 및 서버 버전의 지원되는 조합을 보여줍니다. 이 표에는 클라이언트가 표시된 서버에 연결을 시도할 때 로그인이 지원되는지 여부가 나와 있습니다. Lync Server 2013에서는 이전 클라이언트 버전을 지원합니다. 또한, 이전 릴리스와는 달리 Lync Server 2010에서는 새 Lync 2013 클라이언트를 지원합니다. 따라서 Lync Server 2010에서 업그레이드하는 조직이 Lync Server 업그레이드와 독립적으로 새 클라이언트를 제공할 수 있습니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>클라이언트</th>
<th>Lync Server 2013</th>
<th>Lync Server 2010</th>
<th>Office Communications Server 2007 R2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨5</p></td>
<td><p>지원 안 됨</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 Basic</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨</p></td>
<td><p>지원 안 됨</p></td>
</tr>
<tr class="odd">
<td><p>Lync Web App 2013</p></td>
<td><p>지원됨</p></td>
<td><p>지원 안 됨</p></td>
<td><p>지원 안 됨</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨</p></td>
<td><p>지원 안 됨</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2010 Attendant</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨</p></td>
<td><p>지원 안 됨</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010 그룹 채팅</p></td>
<td><p>지원됨1</p></td>
<td><p>지원됨2</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="odd">
<td><p>Lync Web App 2010</p></td>
<td><p>지원 안 됨</p></td>
<td><p>지원됨</p></td>
<td><p>지원 안 됨</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010 Attendee</p></td>
<td><p>지원 안 됨3</p></td>
<td><p>지원됨</p></td>
<td><p>지원 안 됨</p></td>
</tr>
<tr class="odd">
<td><p>Office Communicator 2007 R2</p></td>
<td><p>상호 운용 가능4</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Office Communications Server 2007 R2 Attendant</p></td>
<td><p>지원 안 됨</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨</p></td>
</tr>
<tr class="odd">
<td><p>Office Communicator 2007</p></td>
<td><p>지원 안 됨</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨</p></td>
</tr>
<tr class="even">
<td><p>Office Live Meeting 2007</p></td>
<td><p>지원 안 됨</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨</p></td>
</tr>
<tr class="odd">
<td><p>Lync Windows 스토어 앱</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨</p></td>
<td><p>지원 안 됨</p></td>
</tr>
</tbody>
</table>


1자세한 내용은 [Lync Server 2010, 그룹 채팅 또는 Office Communications Server 2007 R2 그룹 채팅에서 Lync Server 2013, 영구 채팅 서버로 마이그레이션](migration-from-lync-server-2010-group-chat-or-office-communications-server-2007-r2-group-chat-to-lync-server-2013-persistent-chat-server.md)을 참고하세요.

2Microsoft Lync Server 2010에서는 Lync Server 2010용의 타사 신뢰할 수 있는 응용 프로그램인 그룹 채팅 서버를 통해 그룹 채팅 기능을 사용할 수 있었습니다. Lync 2013 클라이언트는 Lync Server 2010, 그룹 채팅과 호환되지 않습니다.

3현재 Lync Web App 2013은 컴퓨터 오디오 및 비디오를 비롯한 모든 모임 환경을 제공하며 Lync 2010 Attendee를 대체할 솔루션으로 간주됩니다. 지원되지 않는 브라우저(Internet Explorer 6 또는 Internet Explorer 7) 및 Windows XP를 사용하는 경우에만 Lync 2010 Attendee가 Lync Server 2013에 연결됩니다.

4Office Communicator 2007 R2의 현재 상태 및 메신저 기능은 Lync Server 2013과 호환되지만 회의 기능은 호환되지 않습니다. Office Communications Server 2007 R2로부터의 마이그레이션 중에 Office Communicator 2007 R2를 현재 상태 및 메신저 상호 운용성을 위해 사용할 수는 있지만 Lync Server 2013 2013 모임에 참가하려는 사용자는 Lync Web App 2013을 사용해야 합니다.

5 제한 사항은 이 항목 뒷부분에 나오는 "Lync Server 2010 모임에서 Lync 2013 클라이언트에 대한 회의 기능 지원"을 참고하세요.

## 클라이언트 간 상호 운용성

Lync Server 2013 릴리스에서는 여러 클라이언트 버전이 피어 투 피어 시나리오와 회의 시나리오에서 모두 원활하게 상호 작용할 수 있습니다. 이 섹션에서는 사용자가 다른 버전의 클라이언트 및 서버를 사용 중인 다른 사용자와 상호 작용할 때의 기능 사용 가능성에 대해 설명합니다.

## 피어 투 피어 기능 지원

피어 투 피어 기능은 서로 다른 서버 버전에 있으며 서로 다른 클라이언트 버전을 사용 중인 사용자에 대해 지원됩니다. 최종 사용자 환경 및 사용 가능한 기능은 사용자의 클라이언트 기능 및 사용자가 로그인한 서버의 버전과 일치합니다. 즉, 다음과 같습니다.

  - 사용자가 이전 클라이언트를 사용하여 Lync Server 2013에 로그인한 경우 이전과 동일한 환경이 제공됩니다. 사용자 클라이언트를 업그레이드할 때까지는 Lync Server 2013에 도입된 새로운 기능을 사용할 수 없습니다. 비디오 갤러리 보기, HD 비디오, PowerPoint 공유, 회의 입장 시 모든 참석자의 오디오 및 비디오를 음소거하는 옵션 등이 여기에 해당됩니다. 새로운 기능은 [Lync Server 2013의 새로운 회의 기능](lync-server-2013-new-conferencing-features.md) 및 [Lync Server 2013의 새로운 클라이언트 기능](lync-server-2013-what-s-new-for-clients.md)에 설명되어 있습니다.

  - 사용자가 Lync 2013 클라이언트를 사용하여 Lync Server 2010에 로그인한 경우 사용자가 Lync Server 2013으로 이동할 때까지는 Lync Server 2010에서 지원되지 않는 새로운 기능을 사용할 수 없습니다.

다음 표에서는 클라이언트가 Lync Server 2013 또는 Lync Server 2010에 로그인한 피어 투 피어 세션에서 사용 가능한 기능을 비교합니다.


> [!NOTE]
> Lync Web App 및 Lync 2010 Attendee는 회의 전용 클라이언트로, 이 표에는 포함되어 있지 않습니다.




<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>클라이언트</th>
<th>메신저 대화</th>
<th>현재 상태</th>
<th>음성</th>
<th>비디오</th>
<th>응용 프로그램 공유</th>
<th>파일 전송</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 Basic</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2010</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010 Attendant</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Lync 2010 Mobile</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Lync Phone Edition</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Office Communicator 2007 R2</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예1</p></td>
<td><p>예</p></td>
</tr>
<tr class="even">
<td><p>공용 메신저(AOL, Yahoo!)</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>공용 메신저(MSN, Windows Live Messenger)</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>



> [!IMPORTANT]
> <UL>
> <LI>
> <P>2012년 9월 1일 현재 신규 또는 갱신 계약에 대해 Microsoft Lync PIC USL(공용 메신저 연결 사용자 구독 라이선스)을 더 이상 구입할 수 없습니다. 유효 라이선스를 보유한 고객은 서비스 종료 날짜까지 Yahoo! Messenger와 계속해서 페더레이션할 수 있습니다. AOL 및 Yahoo!는 서비스 종료 날짜를 2014년 6월로 발표했습니다. 자세한 내용은 <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Lync Server 2013의 공용 메신저 연결 지원</A>을 참고하세요.</P>
> <LI>
> <P>PIC USL은 Lync Server 또는 Office Communications Server가 Yahoo! Messenger와 페더레이션하는 데 필요한 월별 사용자 단위 구독 라이선스입니다. Microsoft는 Yahoo!의 지원 여부에 따라 이 서비스를 제공할 수 있었으며 해당 서비스의 기본 계약은 갱신되지 않을 예정입니다.</P>
> <LI>
> <P>Lync는 전 세계의 여러 조직과 개별 사용자를 연결해 주는 매우 효율적인 도구입니다. Lync Standard CAL 외의 추가 사용자/장치 라이선스가 없어도 Windows Live Messenger와의 페더레이션이 가능합니다. Skype 페더레이션도 이 목록에 추가될 예정이므로 Lync 사용자는 메신저 및 음성을 통해 수많은 사람들과 연결할 수 있습니다.</P></LI></UL>



1Office Communicator 2007 R2에서는 데스크톱 공유만 가능하며 프로그램 공유는 불가능합니다.

## Lync Server 2010 모임에서 Lync 2013 클라이언트에 대한 회의 기능 지원

Lync 2013 클라이언트를 사용하여 Lync Server 2010 모임에 참가하는 사용자는 Lync 2013 클라이언트 기능에 액세스할 수 있지만 다음과 같은 예외가 적용됩니다.

  - 모임 창에서 사람 아이콘을 가리켜 액세스할 수 있는 **참가자** 관리 옵션에서는 **모임 메신저 없음** 옵션이 작동하지 않습니다.

  - 비디오 회의에서는 갤러리 보기가 작동하지 않습니다. 사용자에게는 모든 발표자 대신 활성 발표자만 표시됩니다. **레이아웃 선택** 옵션 목록에서는 **갤러리 보기**를 사용할 수 없습니다.

  - 비디오 회의에서는 참가자 목록이 기본적으로 표시됩니다.

  - 참가자 목록에서 사용자를 마우스 오른쪽 단추로 클릭하면 **비디오 스포트라이트 잠금** 및 **갤러리에 고정** 참가자 관리 옵션을 사용할 수 없습니다.

## Lync Server 2013 모임의 회의 기능 지원

Lync Server 2013에서는 사용자 계정을 Lync Server 2013으로 이동하고 Lync 2013 클라이언트를 사용하여 로그인한 후 사용할 수 있는 새 회의 기능을 제공합니다. 비디오 갤러리 보기, HD 비디오, PowerPoint 공유, 회의 입장 시 모든 참석자의 오디오 및 비디오를 음소거하는 옵션 등이 여기에 해당됩니다. 새로운 기능은 [Lync Server 2013의 새로운 회의 기능](lync-server-2013-new-conferencing-features.md) 및 [Lync Server 2013의 새로운 클라이언트 기능](lync-server-2013-what-s-new-for-clients.md)에 설명되어 있습니다.

Lync Server 2013 모임에서 특정 회의 기능은 서로 다른 서버 버전에 있으며 서로 다른 클라이언트 및 클라이언트 버전을 사용 중인 사용자에 대해 지원됩니다. 클라이언트가 Lync Server 2013 모임에 참가하면 사용자는 이 표에 나와 있는 기능에 액세스할 수 있습니다.


<table style="width:100%;">
<colgroup>
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
</colgroup>
<thead>
<tr class="header">
<th>클라이언트</th>
<th>피어 투 피어 메신저 대화</th>
<th>음성</th>
<th>비디오</th>
<th>응용 프로그램 공유</th>
<th>PowerPoint</th>
<th>파일 전송</th>
<th>화이트보드</th>
<th>폴링</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 Basic</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
</tr>
<tr class="odd">
<td><p>Lync Web App</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예2</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예3</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>예</p></td>
</tr>
<tr class="odd">
<td><p>Office Communicator 2007 R24</p></td>
<td><p>예</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


1Office Communicator 2007 R2에서는 데스크톱 공유만 가능하며 프로그램 공유는 불가능합니다.

2Lync Server 2013에서는 업데이트된 메커니즘을 사용하여 PowerPoint 파일을 업로드합니다. 원래 Lync Server 2010에서 예약된 모임에 참가하는 Lync Web App 사용자는 PowerPoint 프레젠테이션을 보고 탐색할 수는 있지만 PowerPoint 파일을 업로드할 수는 없습니다.

3 모임이 Lync Server 2013에서 예약되었으며 Lync 2013 클라이언트를 통해 PowerPoint 슬라이드를 업로드한 경우에는 Lync 2010 사용자에게 슬라이드에 대한 보기 전용 권한이 제공됩니다. 반대로, Lync 2010 사용자가 PowerPoint 슬라이드를 업로드한 경우에는 Lync Server 2013 슬라이드를 볼 수 있으며, Office Web Apps Server가 구성된 경우 해상도가 더 높은 디스플레이, 애니메이션, 슬라이드 전환, 포함된 비디오 같은 새 기능에 액세스할 수 있습니다. 자세한 내용은 [Office Online Server 및 Lync Server 2013과 통합 구성](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md)을 참고하세요.

4Office Communicator 2007 R2의 현재 상태 및 메신저 기능은 Lync Server 2013과 호환되지만 회의 기능은 호환되지 않습니다. Office Communications Server 2007 R2로부터의 마이그레이션 중에 Office Communicator 2007 R2를 현재 상태 및 메신저 상호 운용성을 위해 사용할 수는 있지만 Lync Server 2013 2013 모임에 참가하려는 사용자는 Lync Web App 2013을 사용해야 합니다.

## 예약 추가 기능 지원

다양한 예약 추가 기능에 대한 서버 지원은 서버 및 클라이언트 버전 호환성과 일치합니다. 일반적으로는 다음과 같은 예약 추가 기능이 Lync Server 2013에서 지원됩니다. 그러나 이전 버전 추가 기능에는 회의 입장 시 모든 참석자의 오디오 및 비디오를 음소거하는 옵션과 같은 새로운 Lync 2013 추가 기능이 제공되지 않습니다.

  - **Lync 2013용 온라인 모임 추가 기능**   Lync 2010용 온라인 모임 추가 기능과 같은 기능을 제공하며, 모임 이끌이가 참석자의 오디오 및 비디오를 기본적으로 음소거하는 회의를 예약하도록 허용하는 참석자 음소거 컨트롤을 추가로 제공합니다. 관리자는 사용자 지정 로고, 지원 URL, 법적 고지 사항 URL 또는 사용자 지정 바닥글 텍스트를 추가하여 조직의 모임 초대를 사용자 지정할 수도 있습니다.

  - **Lync 2010용 온라인 모임 추가 기능**   Lync 모임 예약 기능을 제공하며 Office Live Meeting 회의 예약 기능을 제거합니다.

  - **Office Communicator 2007 R2 회의 추가 기능**   Office Live Meeting 회의와 Office Communicator 2007 R2 회의를 모두 예약하는 기능을 제공합니다.


> [!NOTE]
> Live Meeting 회의는 Lync Server 2013에서 예약할 수 없습니다.




<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>예약 클라이언트</th>
<th>Lync Server 2013</th>
<th>Lync Server 2010</th>
<th>Office Communications Server 2007 R2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013용 온라인 모임 추가 기능(Office 2013, Outlook 2010 및 Outlook 2007과 함께 사용 가능)</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨(새 추가 기능은 사용할 수 없음)</p></td>
<td><p>지원 안 됨</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 웹 스케줄러</p></td>
<td><p>지원됨</p></td>
<td><p>지원 안 됨</p></td>
<td><p>지원 안 됨</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2010용 온라인 모임 추가 기능</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨</p></td>
<td><p>지원 안 됨</p></td>
</tr>
<tr class="even">
<td><p>Office Communicator 2007 R2 회의 추가 기능</p></td>
<td><p>지원 안 됨</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨</p></td>
</tr>
</tbody>
</table>


## 모임 참가 지원

Lync Server 2013에서 지원하는 모든 클라이언트는 Lync 2013 모임에 참가할 수 있습니다. Lync Web App은 서버의 웹 구성 요소이므로, Lync Web App을 사용하여 Lync Server 2013 모임에 참가하는 경우에는 항상 최신 Lync Web App 버전이 사용됩니다.

Lync 2013 클라이언트는 Lync 2010 및 Office Communications Server 2007 R2에서 호스트되는 모임에 참가할 수 있지만 사용 가능한 기능은 제한됩니다. 모임 내 기능은 모임이 호스트되는 서버의 버전에 따라 제한됩니다.

## 참고 항목

#### 개념

[Lync Server 2013용 Lync Windows 스토어 앱 요구 사항](lync-server-2013-lync-windows-store-app-requirements.md)  
[Lync Server 2013의 새로운 회의 기능](lync-server-2013-new-conferencing-features.md)  
[Lync Server 2013의 새로운 클라이언트 기능](lync-server-2013-what-s-new-for-clients.md)

