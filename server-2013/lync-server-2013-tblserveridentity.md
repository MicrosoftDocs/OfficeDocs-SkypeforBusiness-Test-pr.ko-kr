---
title: 'Lync Server 2013: tblServerIdentity'
TOCTitle: tblServerIdentity
ms:assetid: 5411c9bc-b0b3-41fc-8b7e-fa71cccd770b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg558648(v=OCS.15)
ms:contentKeyID: 49303650
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 tblServerIdentity

 

_**마지막으로 수정된 항목:** 2015-03-09_

tblServerIdentity에는 영구 채팅 서버 풀의 활성 채팅 서버가 포함됩니다.

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
<td><p>serverID</p></td>
<td><p>int, null이 아님</p></td>
<td><p>서버 ID입니다. 중앙 관리 저장소의 인스턴스 ID에 해당합니다.</p></td>
</tr>
<tr class="even">
<td><p>serverAddress</p></td>
<td><p>nvarchar(256), null이 아님</p></td>
<td><p>Windows Communication Foundation 주소를 사용 중인 서버 주소입니다.</p></td>
</tr>
<tr class="odd">
<td><p>serverLastPingTime</p></td>
<td><p>datetime</p></td>
<td><p>실행 중임에 대한 증거를 제공하기 위해 채널 서버가 이 행을 마지막으로 업데이트한 시간입니다.</p></td>
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
<td><p>serverID</p></td>
<td><p>기본 키입니다.</p></td>
</tr>
</tbody>
</table>

