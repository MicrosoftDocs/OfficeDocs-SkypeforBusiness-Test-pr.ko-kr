---
title: 미디어 보기
TOCTitle: 미디어 보기
ms:assetid: 1a7b2e59-082e-4188-98ae-48ae9bd3494a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ687981(v=OCS.15)
ms:contentKeyID: 49885666
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 미디어 보기

 

_**마지막으로 수정된 항목:** 2015-03-09_

Media 보기에는 피어 투 피어 세션에 사용되는 단일 미디어 유형에 대한 정보가 저장됩니다. 둘 이상의 미디어 유형이 사용된 경우 하나의 세션이 테이블에 여러 레코드로 표시됩니다. 이 보기는 Microsoft Lync Server 2013에서 도입되었습니다.


> [!NOTE]
> Media 보기를 사용하여 세션의 미디어 기간을 계산해서는 안 됩니다. 이 보기에는 세션에 포함된 미디어 교환의 신호 세부 정보가 포함됩니다. 미디어 교환은 INVITE 요청에 의해 수행되며 StartTime은 INVITE가 전송된 시간을 나타냅니다. 미디어는 세션이 수락된 후에만 시작되므로 초대 시간이 반드시 미디어 시작 시간인 것은 아닙니다.



Media 보기는 아래에 나와 있는 열과 함께 [SessionDetails 보기](lync-server-2013-sessiondetails-view.md)의 모든 열을 포함합니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>열</th>
<th>데이터 형식</th>
<th>세부 정보</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Media</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>미디어 유형입니다. 자세한 내용은 <a href="lync-server-2013-medialist-table.md">Lync Server 2013의 MediaList 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>MediaStartTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>미디어 요청을 보낸 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediaEndTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>세션 종료 시간입니다.</p></td>
</tr>
</tbody>
</table>

