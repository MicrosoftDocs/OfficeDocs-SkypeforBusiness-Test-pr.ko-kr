---
title: Lync Server 2013에서 Grant-CsSetupPermission으로 인한 변경
TOCTitle: Lync Server 2013에서 Grant-CsSetupPermission으로 인한 변경
ms:assetid: c5801f48-14e3-4fdd-8f14-d52e7af07a57
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205250(v=OCS.15)
ms:contentKeyID: 49304980
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Grant-CsSetupPermission으로 인한 변경

 

_**마지막으로 수정된 항목:** 2015-03-09_

설치를 위임하기 위해 특정 Active Directory OU(조직 구성 단위)의 RTCUniversalServerAdmins 유니버설 그룹에 사용 권한을 부여할 수 있습니다. 그러면 해당 OU의 RTCUniversalServerAdmins 그룹 구성원은 Domain Admins 그룹의 구성원이 아니더라도 지정된 도메인에서 Lync Server 2013을 설치할 수 있습니다.

**Grant-CsSetupPermission** cmdlet을 실행하면 다음 표에 지정된 것과 같이 OU의 RTCUniversalServerAdmins 그룹에 사용 권한을 부여할 수 있습니다.

### OU의 개체에 부여되는 사용 권한

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>사용 권한의 적용 대상</th>
<th>부여받는 사용 권한</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCUniversalServerAdmins</p></td>
<td><p>특수 액세스 권한:</p>
<ul>
<li><p>servicePrincipalName 읽기</p></li>
<li><p>servicePrincipalName 쓰기</p></li>
<li><p>트리 삭제</p></li>
<li><p>디렉터리 변경 내용 복제</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>하위 serviceConnectionPoint 개체</p></td>
<td><p>특수 액세스 권한:</p>
<ul>
<li><p>사용 권한 읽기</p></li>
<li><p>사용 권한 쓰기</p></li>
<li><p>자식 항목 만들기</p></li>
<li><p>자식 항목 삭제</p></li>
<li><p>콘텐츠 나열</p></li>
<li><p>속성 쓰기</p></li>
<li><p>속성 읽기</p></li>
<li><p>트리 삭제</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>하위 msRTCSIP-Server 개체</p></td>
<td><p>특수 액세스 권한:</p>
<ul>
<li><p>속성 쓰기</p></li>
<li><p>속성 읽기</p></li>
<li><p>트리 삭제</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>하위 msRTCSIP-WebComponents 개체</p></td>
<td><p>특수 액세스 권한:</p>
<ul>
<li><p>속성 쓰기</p></li>
<li><p>속성 읽기</p></li>
<li><p>트리 삭제</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>하위 msRTCSIP-MCU 개체</p></td>
<td><p>특수 액세스 권한:</p>
<ul>
<li><p>속성 쓰기</p></li>
<li><p>속성 읽기</p></li>
<li><p>트리 삭제</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>하위 msRTCSIP-MediationServer 개체</p></td>
<td><p>특수 액세스 권한:</p>
<ul>
<li><p>속성 쓰기</p></li>
<li><p>속성 읽기</p></li>
<li><p>트리 삭제</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>하위 msRTCSIP-ApplicationServer 개체</p></td>
<td><p>특수 액세스 권한:</p>
<ul>
<li><p>속성 쓰기</p></li>
<li><p>속성 읽기</p></li>
<li><p>트리 삭제</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>하위 msRTCSIP-ConnectionPoint 개체</p></td>
<td><p>특수 액세스 권한:</p>
<ul>
<li><p>속성 쓰기</p></li>
<li><p>속성 읽기</p></li>
<li><p>트리 삭제</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>하위 Computer 개체</p></td>
<td><p>serviceConnectionPoint에 대한 특수 액세스 권한:</p>
<ul>
<li><p>자식 개체 만들기</p></li>
<li><p>자식 개체 삭제</p></li>
<li><p>트리 삭제</p></li>
</ul>
<p>공개 정보에 대한 특수 액세스 권한:</p>
<ul>
<li><p>속성 읽기</p></li>
</ul>
<p>DNS 호스트 이름에 대한 특수 액세스 권한:</p>
<ul>
<li><p>속성 읽기</p></li>
</ul></td>
</tr>
</tbody>
</table>

