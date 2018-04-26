---
title: Lync Server 2013에서 도메인 준비로 인한 변경
TOCTitle: Lync Server 2013에서 도메인 준비로 인한 변경
ms:assetid: 9191221e-6166-4c2b-837e-fa73d90fdf80
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398742(v=OCS.15)
ms:contentKeyID: 49304385
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 도메인 준비로 인한 변경

 

_**마지막으로 수정된 항목:** 2015-03-09_

다음 표에는 도메인 준비가 도메인 루트에 대해 만든 ACE(액세스 제어 항목)가 나열되어 있습니다. 다른 언급이 없는 경우 모든 ACE는 상속됩니다.

### 도메인 루트에 추가된 ACE

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>ACE</th>
<th>RTCUniversal-UserReadOnly-Group</th>
<th>RTCUniversal-ServerReadOnly-Group</th>
<th>RTCUniversal-UserAdmins</th>
<th>RTCHSUniversal-Services</th>
<th>Authenticated-Users</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>컨테이너 읽기(상속되지 않음)</p></td>
<td><p><strong>예</strong></p></td>
<td><p><strong>예</strong></p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="even">
<td><p>사용자 PropertySet User-Account-Restrictions 읽기</p></td>
<td><p><strong>예</strong></p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="odd">
<td><p>사용자 PropertySet Personal-Information 읽기</p></td>
<td><p><strong>예</strong></p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="even">
<td><p>사용자 PropertySet General-Information 읽기</p></td>
<td><p><strong>예</strong></p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="odd">
<td><p>사용자 PropertySet Public-Information 읽기</p></td>
<td><p><strong>예</strong></p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="even">
<td><p>사용자 PropertySet RTCUserSearchProperty-Set 읽기</p></td>
<td><p><strong>예</strong></p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p><strong>예</strong></p></td>
</tr>
<tr class="odd">
<td><p>사용자 PropertySet RTCPropertySet 읽기</p></td>
<td><p><strong>예</strong></p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="even">
<td><p>사용자 Property Proxy-Addresses 쓰기</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p><strong>예</strong></p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="odd">
<td><p>사용자 PropertySet RTCUserSearchProperty-Set 쓰기</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p><strong>예</strong></p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="even">
<td><p>사용자 PropertySet RTCPropertySet 쓰기</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p><strong>예</strong></p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="odd">
<td><p>모든 Active Directory 개체의 PropertySet DS-Replication-Get-Changes 읽기</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p><strong>예</strong></p></td>
<td><p>아니요</p></td>
</tr>
</tbody>
</table>


다음 표에는 도메인 준비가 세 개의 기본 제공 컨테이너인 사용자, 컴퓨터 및 도메인 컨트롤러에 만드는 ACE가 나열되어 있습니다. 다른 언급이 없는 경우 모든 ACE는 상속됩니다.

### 기본 제공 컨테이너에 추가된 ACE

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>ACE</th>
<th>RTCUniversal-UserReadOnly-Group</th>
<th>RTCUniversal-ServerReadOnly-Group</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>컨테이너 읽기(상속되지 않음)</p></td>
<td><p><strong>예</strong></p></td>
<td><p><strong>예</strong></p></td>
</tr>
</tbody>
</table>

