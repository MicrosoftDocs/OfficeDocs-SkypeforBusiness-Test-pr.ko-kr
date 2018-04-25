---
title: 'Lync Server 2013: 알림 응용 프로그램 배포 프로세스'
TOCTitle: 알림 응용 프로그램 배포 프로세스
ms:assetid: 72c66249-c4ce-48ce-b1b9-90ebf77d7805
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398545(v=OCS.15)
ms:contentKeyID: 49304016
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 알림 응용 프로그램 배포 프로세스

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 섹션에서는 알림 응용 프로그램 배포 시 수행하는 단계를 간략하게 설명합니다. 알림을 구성하기 전에 Enterprise Voice를 배포해야 합니다. 알림 응용 프로그램에 필요한 구성 요소는 Enterprise Voice 배포 시 설치 및 사용하도록 설정됩니다.

### 알림 배포 프로세스

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
<th>역할</th>
<th>배포 설명서</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>알림 설정 구성</p></td>
<td><ul>
<li><p>오디오 파일을 녹음하여 업로드하거나 TTS(텍스트 음성 변환)를 사용하여 알림을 만듭니다.</p></li>
<li><p>지정되지 않은 번호 표의 지정되지 않은 번호 범위를 구성하여 적절한 알림과 연결합니다.</p></li>
</ul></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p>
<p>CsViewOnlyAdministrator</p></td>
<td><p><a href="lync-server-2013-create-an-announcement.md">Lync Server 2013에서 알림 만들기</a></p>
<p><a href="lync-server-2013-configure-the-unassigned-number-table.md">Lync Server 2013에서 지정되지 않은 번호 테이블 구성</a></p></td>
</tr>
<tr class="even">
<td><p>알림 배포 확인</p></td>
<td><p>알림 듣기를 테스트하여 구성이 제대로 작동하는지 확인합니다.</p></td>
<td><p>-</p></td>
<td><p><a href="lync-server-2013-optional-verify-announcement-deployment.md">(선택 사항) Lync Server 2013에서 알림 배포 확인</a></p></td>
</tr>
</tbody>
</table>

