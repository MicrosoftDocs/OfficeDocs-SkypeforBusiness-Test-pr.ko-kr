---
title: 'Lync Server 2013: 이전 배포에서 지원되는 클라이언트'
TOCTitle: 이전 배포에서 지원되는 클라이언트
ms:assetid: 69d427f8-57a5-4244-b2ed-f2eb7600285e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398499(v=OCS.15)
ms:contentKeyID: 49303916
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 이전 배포에서 지원되는 클라이언트

 

_**마지막으로 수정된 항목:** 2015-03-09_

동시 사용 시나리오에서 Lync Server 2013 클라이언트는 이전 버전의 Lync Server 및 Office Communications Server의 클라이언트와 상호 작용할 수 있습니다. 이전 릴리스와 달리 Lync Server 2010에서는 새로운 Lync 2013 클라이언트가 지원됩니다. 이를 통해 Lync Server 2010에서 업그레이드하는 조직은 Lync Server 업그레이드와 별개로 새 클라이언트를 롤아웃할 수 있습니다.

## 지원되는 서버 및 클라이언트 조합

다음 표에서는 지원되는 클라이언트 버전 및 서버 버전의 조합을 보여줍니다. Lync Server 2013에서는 두 개의 이전 클라이언트 버전이 지원되고 Lync Server 2010에서는 새로운 Lync 2013 클라이언트가 지원됩니다.


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
<td><p>지원됨</p></td>
<td><p>지원 안 됨</p></td>
</tr>
<tr class="even">
<td><p>Lync Web App 2013</p></td>
<td><p>지원됨</p></td>
<td><p>지원 안 됨</p></td>
<td><p>지원 안 됨</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2010</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨</p></td>
<td><p>지원 안 됨</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010 Attendant</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨</p></td>
<td><p>지원 안 됨</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2010 그룹 채팅</p></td>
<td><p>해당 없음</p></td>
<td><p>지원됨1</p></td>
<td><p>해당 없음</p></td>
</tr>
<tr class="even">
<td><p>Lync Web App 2010</p></td>
<td><p>지원 안 됨</p></td>
<td><p>지원됨</p></td>
<td><p>지원 안 됨</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2010 Attendee</p></td>
<td><p>지원 안 됨2</p></td>
<td><p>지원됨</p></td>
<td><p>지원 안 됨</p></td>
</tr>
<tr class="even">
<td><p>Office Communicator 2007 R2</p></td>
<td><p>상호 운용 가능3</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Office Communications Server 2007 R2 Attendant</p></td>
<td><p>지원 안 됨</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨</p></td>
</tr>
<tr class="even">
<td><p>Office Communicator 2007</p></td>
<td><p>지원 안 됨</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨</p></td>
</tr>
<tr class="odd">
<td><p>Office Live Meeting 2007</p></td>
<td><p>지원 안 됨</p></td>
<td><p>지원됨</p></td>
<td><p>지원됨</p></td>
</tr>
</tbody>
</table>


1Microsoft Lync Server 2010에서는 Lync Server 2010용의 타사 신뢰할 수 있는 응용 프로그램인 그룹 채팅 서버를 통해 그룹 채팅 기능을 사용할 수 있었습니다. Lync 2013 클라이언트는 Lync Server 2010, 그룹 채팅과 호환되지 않습니다.

2이제는 Lync Web App 2013이 컴퓨터 오디오 및 비디오를 비롯하여 모임 내의 모든 환경을 제공하며 Lync 2010 Attendee를 대체하는 솔루션으로 간주됩니다.

3Office Communicator 2007 R2의 현재 상태 및 메신저 기능은 Lync Server 2013과 호환되지만 회의 기능은 호환되지 않습니다. Office Communications Server 2007 R2로부터의 마이그레이션 중에 Office Communicator 2007 R2를 현재 상태 및 메신저 상호 운용성을 위해 사용할 수는 있지만 Lync Server 2013 2013 모임에 참가하려는 사용자는 Lync Web App 2013을 사용해야 합니다.


> [!NOTE]
> Lync Server 2013 클라이언트가 이전 버전의 Lync Server 및 Office Communications Server의 클라이언트와 동시에 사용되고 상호 작용하는 기능에 대한 자세한 내용은 계획 설명서에서 <A href="lync-server-2013-client-interoperability-in-lync-2013.md">Lync 2013 에서 클라이언트 상호 운용성</A>을 참조하십시오.


