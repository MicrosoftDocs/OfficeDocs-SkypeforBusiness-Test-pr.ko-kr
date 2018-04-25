---
title: Lync Server 2013의 CDR 보기 목록
TOCTitle: Lync Server 2013의 CDR 보기 목록
ms:assetid: 2f72aead-d1da-4185-b75c-f6c31d76a6b3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688009(v=OCS.15)
ms:contentKeyID: 49885703
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 CDR 보기 목록

 

_**마지막으로 수정된 항목:** 2015-03-09_

보기를 사용하면 CDR 데이터베이스에서 데이터를 반환하는 데 사용되는 가장 일반적인 시나리오에 대한 정보에 쉽게 액세스할 수 있습니다. 사용자 지정 보고서를 작성할 때는 실제 CDR 데이터베이스 테이블을 사용하는 대신 보기를 사용하는 것이 좋습니다. 데이터베이스 보기는 이후 Lync Server 릴리스와도 이전 버전과의 호환성을 유지할 가능성이 높기 때문입니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>보기 이름</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-clientversions-view.md">ClientVersions 보기</a></p></td>
<td><p>통신 세션에서 사용되는 클라이언트 소프트웨어/장치에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-conferencemessagecount-view.md">ConferenceMessageCount 보기</a></p></td>
<td><p>전화 회의에서 사용자가 보낸 메시지 수에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-conferences-view.md">회의 보기</a></p></td>
<td><p>시작 시간, 종료 시간, 전화 회의 이끌이 등의 전화 회의 정보를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-conferencesessiondetails-view.md">ConferenceSessionDetails 보기</a></p></td>
<td><p>시작/종료 시간, 사용자 ID, 응답 코드, 진단 ID를 포함하여 모든 전화 회의 세션에 대한 세션 세부 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-conferenceuris-view.md">ConferenceUris 보기</a></p></td>
<td><p>전화 회의에서 사용되는 전화 회의 URI에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-errorreport-view.md">ErrorReport 보기</a></p></td>
<td><p>세션 중 발생한 오류에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-filetransfers-view.md">FileTransfers 보기</a></p></td>
<td><p>파일 이름 및 전송 수락/거절/취소 여부를 포함하여 파일 전송 세션에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-focusjoinsandleaves-view.md">FocusJoinsAndLeaves 보기</a></p></td>
<td><p>전화 회의 참가 및 나가기 활동에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-mcujoinsandleaves-view.md">McuJoinsAndLeaves 보기</a></p></td>
<td><p>전화 회의 참가 및 나가기 활동에 대한 결합된 정보를 반환합니다(각 전화 회의 참가는 해당하는 전화 회의 나가기와 쌍으로 지정됨).</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-mcus-view.md">Mcus 보기</a></p></td>
<td><p>전화 회의 서버에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-media-view.md">미디어 보기</a></p></td>
<td><p>피어 투 피어 통신 세션에서 사용되는 미디어 유형에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-progressreport-view.md">ProgressReport 보기</a></p></td>
<td><p>완료된 세션에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-registration-view.md">등록 보기</a></p></td>
<td><p>Lync Server 등록에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-sessiondetails-view.md">SessionDetails 보기</a></p></td>
<td><p>VoIP 간 전화 통화, 두 사용자 간의 IM 세션 또는 기타 피어 투 피어 통신 세션을 포함하여 피어 투 피어 세션에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-user-view.md">사용자 보기</a></p></td>
<td><p>통신 세션에 참가한 사용자에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-voipdetails-view.md">VoIPDetails 보기</a></p></td>
<td><p>VoIP(Voice over IP) 사용자가 한 명 이상 포함된 피어 투 피어 세션에 대한 정보를 반환합니다.</p></td>
</tr>
</tbody>
</table>

