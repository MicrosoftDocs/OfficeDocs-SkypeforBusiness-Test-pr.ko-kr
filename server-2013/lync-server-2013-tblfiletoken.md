---
title: 'Lync Server 2013: tblFileToken'
TOCTitle: tblFileToken
ms:assetid: 49e7dd79-1607-443c-818a-88c160e4ed06
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg558646(v=OCS.15)
ms:contentKeyID: 49303539
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 tblFileToken

 

_**마지막으로 수정된 항목:** 2015-03-09_

tblFileToken에는 파일 전송 목적의 임시 토큰이 포함됩니다.

### 열

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>열</th>
<th>유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>fileToken</p></td>
<td><p>nvarchar(50), null이 아님</p></td>
<td><p>고유한 토큰(GUID)입니다.</p></td>
</tr>
<tr class="even">
<td><p>fileTokenUserID</p></td>
<td><p>int, null이 아님</p></td>
<td><p>파일을 전송 중인 사용자의 ID입니다.</p></td>
</tr>
<tr class="odd">
<td><p>fileTokenChannelID</p></td>
<td><p>GUID, null이 아님</p></td>
<td><p>대화방 노드의 GUID입니다.</p></td>
</tr>
<tr class="even">
<td><p>fileTokenExpireDate</p></td>
<td><p>datetime, null이 아님</p></td>
<td><p>만료 시간입니다. 고정되지 않은 한 토큰이 30분 후 만료됩니다(이 열의 다음 설명 참조).</p></td>
</tr>
<tr class="odd">
<td><p>fileTokenComplianceFileUrl</p></td>
<td><p>nvarchar(256)</p></td>
<td><p>전송된 파일의 URL입니다(준수 서비스용).</p></td>
</tr>
<tr class="even">
<td><p>fileTokenComplianceThumbnailUrl</p></td>
<td><p>nvarchar(256)</p></td>
<td><p>전송된 파일에 대한 축소판 그림의 URL입니다(준수 서비스용).</p></td>
</tr>
<tr class="odd">
<td><p>fileTokenComplianceTime</p></td>
<td><p>datetime2</p></td>
<td><p>실제 파일 전송 작업의 타임스탬프입니다(준수 서비스용).</p></td>
</tr>
<tr class="even">
<td><p>fileTokenComplianceIsUpload</p></td>
<td><p>bit</p></td>
<td><p>업로드인 경우 True, 다운로드인 경우 False입니다(준수 서비스용).</p></td>
</tr>
<tr class="odd">
<td><p>fileTokenCompliancePinned</p></td>
<td><p>bit, null이 아님</p></td>
<td><p>토큰이 고정된 경우 True입니다. 준수 서비스가 여기에서 관련 필드를 검색할 수 있을 때까지 토큰을 테이블에 유지하기 위해 사용됩니다.</p></td>
</tr>
</tbody>
</table>


### 키

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>열</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>fileToken</p></td>
<td><p>기본 키입니다.</p></td>
</tr>
<tr class="even">
<td><p>fileTokenChannelID</p></td>
<td><p>tblNode.nodeGuid 테이블에서 조회 기능이 있는 외래 키입니다.</p></td>
</tr>
</tbody>
</table>

