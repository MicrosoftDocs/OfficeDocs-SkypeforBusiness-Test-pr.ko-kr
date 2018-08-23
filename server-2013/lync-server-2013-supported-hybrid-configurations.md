---
title: 'Lync Server 2013: 지원되는 하이브리드 구성'
TOCTitle: 지원되는 하이브리드 구성
ms:assetid: 5d456d6c-ad71-420c-b6d8-4d9cd0324f86
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945633(v=OCS.15)
ms:contentKeyID: 52056854
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 지원되는 Lync Server 2013 하이브리드 구성

 

_**마지막으로 수정된 항목:** 2015-03-09_

온-프레미스와 온라인에 있는 Microsoft Exchange Server 2010, Microsoft Exchange Server 2013, SharePoint Server와의 통합용으로 Lync Server 2013 배포를 구성할 수 있습니다. 아래 표에 나와 있는 기능은 별도로 명시하지 않는 한 모든 클라이언트에서 지원됩니다. 클라이언트 지원에 대한 자세한 내용은 클라이언트 비교 표 [Lync Server 2013 의 클라이언트 비교 표](lync-server-2013-desktop-client-comparison-tables.md) 및 [Lync Online 클라이언트](http://go.microsoft.com/fwlink/p/?linkid=281902)에서 Lync Online 클라이언트 비교 표를 참고하세요.

## Exchange Server와의 통합

아래 표에는 Microsoft Exchange Server와 통합할 때 하이브리드 배포에서 지원되는 기능이 나와 있습니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Exchange 온-프레미스</th>
<th>Exchange Online</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Lync Server 2013 온-프레미스</strong></p></td>
<td><ul>
<li><p>Outlook의 메신저 대화/현재 상태</p>
<p>자세한 내용은 <a href="lync-server-2013-im-and-presence.md">Lync Server 2013의 메신저 및 현재 상태</a>를 참고하세요.</p></li>
<li><p>Outlook을 통한 온라인 모임 예약 및 참가</p>
<p>자세한 내용은 <a href="lync-server-2013-integrating-with-microsoft-exchange-server-2013.md">Microsoft Lync Server 2013과 Microsoft Exchange Server 2013 통합</a>을 참고하세요.</p></li>
<li><p>Outlook Web App의 메신저 대화/현재 상태</p>
<p>자세한 내용은 <a href="lync-server-2013-configuring-lync-server-in-a-cross-premises-environment.md">크로스-프레미스 환경에서 Microsoft Lync Server 2013 구성</a>을 참고하세요.</p></li>
<li><p>Outlook Web App을 통한 온라인 모임 예약 및 참가</p></li>
<li><p>모바일 클라이언트의 메신저 대화/현재 상태</p></li>
<li><p>모바일 클라이언트에서 온라인 모임 참가</p>
<p>자세한 내용은 <a href="lync-server-2013-deploying-mobility.md">Lync Server 2013에서 모바일 기능 배포</a>를 참고하세요.</p></li>
<li><p>Outlook 일정 약속 있음/없음 정보를 기반으로 상태 게시</p></li>
<li><p>대화 상대 목록(통합 연락처 저장소를 통해)</p>
<p>자세한 내용은 <a href="lync-server-2013-configuring-lync-server-to-use-the-unified-contact-store.md">통합 연락처 저장소를 사용하도록 Microsoft Lync Server 2013 구성</a>을 참고하세요.</p>


> [!NOTE]
> Exchange 2013이 필요합니다.<BR>Lync 2013 데스크톱 클라이언트가 필요합니다.


</li>
<li><p>Lync 2013 클라이언트 및 Lync Web App의 고해상도 대화 상대 사진</p>
<p>자세한 내용은 <a href="lync-server-2013-configuring-the-use-of-high-resolution-photos.md">Microsoft Lync Server 2013에서 고해상도 사진 사용 구성</a>을 참고하세요.</p>


> [!NOTE]
> Exchange 2013이 필요합니다.


</li>
<li><p>모임 위임</p>
<p>두 사용자 모두 동일한 포리스트의 온라인으로 이동되었거나 둘 다 온-프레미스로 이동된 경우에만 지원됩니다.</p></li>
<li><p>부재 중 대화 내용과 통화 기록은 사용자의 Exchange 사서함에 기록됩니다.</p></li>
<li><p>Exchange에 콘텐츠 보관(메신저 대화 및 모임)</p>
<p>자세한 내용은 <a href="lync-server-2013-deployment-checklist-for-archiving.md">Lync Server 2013의 보관용 배포 검사 목록</a>을 참고하세요.</p>


> [!NOTE]
> Exchange 2013이 필요합니다.


</li>
<li><p>보관된 콘텐츠 검색</p>


> [!NOTE]
> Exchange 2013이 필요합니다.


</li>
<li><p>음성 사서함</p>
<p>자세한 내용은 <a href="lync-server-2013-deploying-on-premises-exchange-um-to-provide-lync-server-2013-voice-mail.md">Lync Server 2013 음성 메일을 제공하도록 온-프레미스 Exchange UM 배포</a>를 참고하세요.</p></li>
</ul></td>
<td><ul>
<li><p>Outlook의 메신저 대화/현재 상태</p>
<p>자세한 내용은 <a href="lync-server-2013-configuring-on-premises-lync-server-integration-with-exchange-online.md">Exchange Online과 온-프레미스 Lync Server 2013 통합 구성</a>을 참고하세요.</p></li>
<li><p>Outlook을 통한 온라인 모임 예약 및 참가</p></li>
<li><p>OWA의 메신저 대화/현재 상태</p>
<p>자세한 내용은 <a href="lync-server-2013-configuring-on-premises-lync-server-integration-with-exchange-online.md">Exchange Online과 온-프레미스 Lync Server 2013 통합 구성</a>을 참고하세요.</p></li>
<li><p>Outlook Web App에서 온라인 모임 예약 및 참가</p>
<p>자세한 내용은 <a href="lync-server-2013-configuring-on-premises-lync-server-integration-with-exchange-online.md">Exchange Online과 온-프레미스 Lync Server 2013 통합 구성</a>을 참고하세요.</p></li>
<li><p>모바일 클라이언트의 메신저 대화/현재 상태</p></li>
<li><p>모바일 클라이언트에서 온라인 모임 참가</p></li>
<li><p>Outlook 일정 약속 있음/없음 정보를 기반으로 상태 게시</p></li>
<li><p>대화 상대 목록(통합 연락처 저장소를 통해). 자세한 내용은 <a href="lync-server-2013-configuring-lync-server-to-use-the-unified-contact-store.md">통합 연락처 저장소를 사용하도록 Microsoft Lync Server 2013 구성</a>을 참고하세요.</p>


> [!NOTE]
> Lync Server 2013 전용. Lync 2013 데스크톱 클라이언트가 필요합니다.


</li>
<li><p>Lync 2013 클라이언트 및 Lync Web App의 고해상도 대화 상대 사진</p>
<p>자세한 내용은 <a href="lync-server-2013-configuring-the-use-of-high-resolution-photos.md">Microsoft Lync Server 2013에서 고해상도 사진 사용 구성</a>을 참고하세요.</p></li>
<li><p>모임 위임</p>
<p>두 사용자 모두 동일한 포리스트의 온라인으로 이동되었거나 둘 다 온-프레미스로 이동된 경우에만 지원됩니다.</p></li>
<li><p>부재 중 대화 내용과 통화 기록은 사용자의 Exchange 사서함에 기록됩니다.</p></li>
<li><p>Exchage에 콘텐츠 보관(메신저 대화 및 모임)</p>
<p>자세한 내용은 <a href="lync-server-2013-deployment-checklist-for-archiving.md">Lync Server 2013의 보관용 배포 검사 목록</a>을 참고하세요.</p></li>
<li><p>보관된 콘텐츠 검색. 자세한 내용은 <a href="http://go.microsoft.com/fwlink/p/?linkid=285448">SharePoint eDiscovery 센터에 대한 Exchange 구성</a>을 참고하세요.</p></li>
<li><p>음성 사서함. 자세한 내용은 <a href="lync-server-2013-providing-lync-server-users-voice-mail-on-hosted-exchange-um.md">호스팅된 Exchange UM에서 Lync Server 2013 사용자 음성 메일 제공</a>을 참고하세요.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Lync Online</strong></p></td>
<td><ul>
<li><p>Outlook의 메신저 대화 및 현재 상태</p></li>
<li><p>Outlook을 통한 온라인 모임 예약 및 참가</p></li>
<li><p>모바일 클라이언트의 메신저 대화/현재 상태</p></li>
<li><p>부재 중 대화 내용과 통화 기록은 사용자의 Exchange 사서함에 기록됩니다.</p></li>
<li><p>Lync 2013 클라이언트의 고해상도 대화 상대 사진</p>


> [!NOTE]
> Microsoft Exchange Server 2013이 필요합니다. 사용자가 비즈니스용 Skype Online으로 이동된 경우 Lync Web App에서는 지원되지 않습니다.


</li>
<li><p>모바일 클라이언트에서 온라인 모임 참가</p></li>
<li><p>Outlook 일정 약속 있음/없음 정보를 기반으로 상태 게시</p></li>
<li><p>모임 위임</p>
<p>두 사용자 모두 동일한 포리스트의 온라인으로 이동되었거나 둘 다 온-프레미스로 이동된 경우에만 지원됩니다.</p></li>
</ul></td>
<td><ul>
<li><p>Outlook의 메신저 대화/현재 상태</p></li>
<li><p>Outlook을 통한 온라인 모임 예약 및 참가</p></li>
<li><p>Outlook Web App의 메신저 대화/현재 상태</p></li>
<li><p>Outlook Web App에서 온라인 모임 예약 및 참가</p></li>
<li><p>모바일 클라이언트의 메신저 대화/현재 상태</p></li>
<li><p>모바일 클라이언트에서 온라인 모임 참가</p></li>
<li><p>Outlook 일정 약속 있음/없음 정보를 기반으로 상태 게시</p></li>
<li><p>부재 중 대화 내용과 통화 기록은 사용자의 Exchange 사서함에 기록됩니다.</p></li>
<li><p>대화 상대 목록(통합 연락처 저장소를 통해)</p>


> [!NOTE]
> Lync Server 2013 클라이언트가 필요합니다.


</li>
<li><p>Lync 2013 클라이언트 및 Lync Web App의 고해상도 대화 상대 사진</p></li>
<li><p>모임 위임</p>
<p>두 사용자 모두 동일한 포리스트의 온라인으로 이동되었거나 둘 다 온-프레미스로 이동된 경우에만 지원됩니다.</p></li>
<li><p>Exchange에 콘텐츠 보관(메신저 대화 및 모임)</p></li>
<li><p>보관된 콘텐츠 검색</p></li>
<li><p>음성 사서함</p></li>
</ul></td>
</tr>
</tbody>
</table>


## SharePoint와의 통합

아래 표에는 SharePoint와 통합할 때 Lync Server 2013 하이브리드 배포에서 지원되는 기능이 나와 있습니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>SharePoint 온-프레미스</th>
<th>SharePoint Online</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Lync Server 2013 온-프레미스</strong></p></td>
<td><ul>
<li><p>기술 검색</p></li>
<li><p>SharePoint의 현재 상태</p></li>
</ul></td>
<td><ul>
<li><p>SharePoint의 현재 상태</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Lync Online</strong></p></td>
<td><ul>
<li><p>SharePoint의 현재 상태</p></li>
</ul></td>
<td><ul>
<li><p>SharePoint의 현재 상태</p></li>
</ul></td>
</tr>
</tbody>
</table>

