---
title: FileTransfers 보기
TOCTitle: FileTransfers 보기
ms:assetid: e52c3ad0-152e-4a18-af1c-1aff0d205151
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721914(v=OCS.15)
ms:contentKeyID: 49886024
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# FileTransfers 보기

 

_**마지막으로 수정된 항목:** 2015-03-09_

FileTranfer 보기는 피어 투 피어 파일 전송 세션에 대한 정보를 저장합니다. 이 보기는 Microsoft Lync Server 2013에 새로 도입되었습니다.


> [!NOTE]
> FileTransfers 보기에는 아래 나열된 열 외에도 <A href="lync-server-2013-sessiondetails-view.md">SessionDetails 보기</A>의 모든 열이 포함되어 있습니다.




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
<td><p><strong>FileName</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>전송된 파일 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>Cookie</strong></p></td>
<td><p>nvarchar(128)</p></td>
<td><p>이 항목과 연결 중인 모든 후속 작업 메시지를 식별하기 위해 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FileIdentity</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p>동일한 파일 이름과 관련된 여러 파일 전송을 구분하는 고유 식별자입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>Accept</strong></p></td>
<td><p>bit</p></td>
<td><p>TRUE 또는 NULL일 수 있습니다. TRUE인 경우 Reject 및 Cancel이 NULL이 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Reject</strong></p></td>
<td><p>bit</p></td>
<td><p>TRUE 또는 NULL일 수 있습니다. TRUE인 경우 Accept 및 Cancel이 NULL이 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>Cancel</strong></p></td>
<td><p>bit</p></td>
<td><p>TRUE 또는 NULL일 수 있습니다. TRUE인 경우 Accept 및 Reject가 NULL이 됩니다.</p></td>
</tr>
</tbody>
</table>

