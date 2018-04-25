---
title: 'Lync Server 2013: tblChat'
TOCTitle: tblChat
ms:assetid: b7fcf1b4-7a3f-4585-a6d9-95e7f030c7dc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg615031(v=OCS.15)
ms:contentKeyID: 49304820
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 tblChat

 

_**마지막으로 수정된 항목:** 2015-03-09_

tblChat에는 모든 채팅 메시지가 포함됩니다.

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
<td><p>channelId</p></td>
<td><p>int, null이 아님</p></td>
<td><p>노드 ID입니다.</p></td>
</tr>
<tr class="even">
<td><p>chatId</p></td>
<td><p>bigint, null이 아님</p></td>
<td><p>tblLastChatId 테이블에서 생성된 대화방 순서를 정의하는 고유한 일련 번호(노드 ID당)입니다.</p></td>
</tr>
<tr class="odd">
<td><p>chatDate</p></td>
<td><p>bigint, null이 아님</p></td>
<td><p>채팅 메시지의 타임스탬프입니다.</p></td>
</tr>
<tr class="even">
<td><p>userId</p></td>
<td><p>int, null이 아님</p></td>
<td><p>게시자의 사용자 ID입니다.</p></td>
</tr>
<tr class="odd">
<td><p>isAlert</p></td>
<td><p>bit, null이 아님</p></td>
<td><p>메시지가 경고 메시지인 경우 True입니다. 그렇지 않으면 False입니다.</p></td>
</tr>
<tr class="even">
<td><p>content</p></td>
<td><p>nvarchar(max), null이 아님</p></td>
<td><p>채팅 콘텐츠(일반 텍스트 버전)입니다. 콘텐츠는 일반적으로 일반 텍스트이지만 다음과 같은 예외가 있습니다.</p>
<ul>
<li><p>파일이 ma-filelink: 링크로 표시됩니다.</p></li>
<li><p>링크는 HTML 요소로 표시됩니다(콘텐츠 형식은 HTML로 간주 할 수 없음).</p></li>
<li><p>이야기는 &quot;[STORY]....&quot;와 비슷한 형식으로 인코딩됩니다.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>rtf</p></td>
<td><p>varchar(max)</p></td>
<td><p>채팅 콘텐츠(RTF 버전)입니다. 클라이언트에서 제공하지 않는 경우 Null이 될 수 있습니다.</p></td>
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
<td><p>&lt;channelID, chatD&gt;</p></td>
<td><p>기본 키입니다.</p></td>
</tr>
</tbody>
</table>

