---
title: Lync Server 2013에서 Grant-CsOUPermission으로 인한 변경
TOCTitle: Lync Server 2013에서 Grant-CsOUPermission으로 인한 변경
ms:assetid: d744d352-1ad9-4447-8e2b-28e768d2ed1b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205310(v=OCS.15)
ms:contentKeyID: 49305184
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Grant-CsOUPermission으로 인한 변경

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 관리를 위임하기 위해 지정된 OU(조직 구성 단위)에 사용 권한을 추가하여 포리스트 준비로 만들어진 RTC 유니버설 그룹의 구성원이 Domain Admins 그룹의 구성원이 아니어도 OU에 액세스할 수 있습니다.

**Grant-CsOuPermission** cmdlet을 사용하면 다음 표에 지정된 대로 지정한 OU의 개체에 대한 사용 권한이 부여됩니다.

## User 개체에 대한 사용 권한 부여

OU의 User 개체에 대해 **Grant-CsOuPermission** cmdlet을 실행하면 다음 표에 나타난 것처럼 그룹이 사용 권한을 부여받습니다.

### User 개체에 대해 부여되는 사용 권한

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>그룹</th>
<th>사용 권한</th>
<th>적용 대상</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCHSUniversalServices</p></td>
<td><p>디렉터리 변경 내용 복제</p></td>
<td><p>이 개체만</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalServerReadOnlyGroup</p></td>
<td><p>콘텐츠 나열</p>
<p>모든 속성 읽기</p>
<p>사용 권한 읽기</p></td>
<td><p>이 개체만</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>콘텐츠 나열</p>
<p>모든 속성 읽기</p>
<p>사용 권한 읽기</p></td>
<td><p>이 개체만</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>RTCUserSearchPropertySet 읽기</p>
<p>RTCUserProvisioningPropertySet 읽기</p>
<p>RTCPropertySet 읽기</p>
<p>공용 정보 읽기</p>
<p>일반 정보 읽기</p>
<p>사용자 계정 제한 사항 읽기</p></td>
<td><p>하위 User 개체</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>RTCUserSearchPropertySet 쓰기</p>
<p>msExchUCVoiceMailSettings 쓰기</p>
<p>RTCUserProvisioningPropertySet 쓰기</p>
<p>RTCPropertySet 쓰기</p>
<p>proxyAddresses 쓰기</p></td>
<td><p>하위 User 개체</p></td>
</tr>
</tbody>
</table>


## Computer 개체에 대한 사용 권한 부여

OU의 Computer 개체에 대해 **Grant-CsOuPermission** cmdlet을 실행하면 다음 표에 나타난 것처럼 그룹이 사용 권한을 부여받습니다.

### Computer 개체에 대해 부여되는 사용 권한

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>그룹</th>
<th>사용 권한</th>
<th>적용 대상</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCHSUniversalServices</p></td>
<td><p>디렉터리 변경 내용 복제</p></td>
<td><p>이 개체만</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalServerReadOnlyGroup</p></td>
<td><p>콘텐츠 나열</p>
<p>모든 속성 읽기</p>
<p>사용 권한 읽기</p></td>
<td><p>이 개체만</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>콘텐츠 나열</p>
<p>모든 속성 읽기</p>
<p>사용 권한 읽기</p></td>
<td><p>이 개체만</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>공용 정보 읽기</p>
<p>Validated-DNS-Host-Name 읽기</p></td>
<td><p>하위 Computer 개체</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>공용 정보 읽기</p>
<p>Validated-DNS-Host-Name 읽기</p></td>
<td><p>하위 Computer 개체</p></td>
</tr>
</tbody>
</table>


## Contact 또는 AppContact 개체에 대한 사용 권한 부여

OU의 Contact 또는 AppContact 개체에 대해 **Grant-CsOuPermission** cmdlet을 실행하면 다음 표에 나타난 것처럼 그룹이 사용 권한을 부여받습니다.

### Contact 또는 AppContact 개체에 대해 부여되는 사용 권한

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>그룹</th>
<th>사용 권한</th>
<th>적용 대상</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCHSUniversalServices</p></td>
<td><p>디렉터리 변경 내용 복제</p></td>
<td><p>이 개체만</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalServerReadOnlyGroup</p></td>
<td><p>콘텐츠 나열</p>
<p>모든 속성 읽기</p>
<p>사용 권한 읽기</p></td>
<td><p>이 개체만</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>콘텐츠 나열</p>
<p>모든 속성 읽기</p>
<p>사용 권한 읽기</p></td>
<td><p>이 개체만</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>RTCUserSearchPropertySet 읽기</p>
<p>RTCUserProvisioningPropertySet 읽기</p>
<p>RTCPropertySet 읽기</p>
<p>공용 정보 읽기</p>
<p>일반 정보 읽기</p>
<p>개인 정보 읽기</p>
<p>사용자 계정 제한 사항 읽기</p></td>
<td><p>하위 Contact 개체</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>RTCUserSearchPropertySet 쓰기</p>
<p>otherIpPhone 쓰기</p>
<p>displayName 쓰기</p>
<p>description 쓰기</p>
<p>telephoneNumber 쓰기</p>
<p>msExchUCVoiceMailSettings 쓰기</p>
<p>RTCUserProvisioningPropertySet 쓰기</p>
<p>RTCPropertySet 쓰기</p>
<p>proxyAddresses 쓰기</p></td>
<td><p>하위 Contact 개체</p></td>
</tr>
</tbody>
</table>


## Device 개체에 대한 사용 권한 부여

OU의 Device 개체에 대해 **Grant-CsOuPermission** cmdlet을 실행하면 다음 표에 나타난 것처럼 그룹이 사용 권한을 부여받습니다.

### Device 개체에 대해 부여되는 사용 권한

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>그룹</th>
<th>사용 권한</th>
<th>적용 대상</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCHSUniversalServices</p></td>
<td><p>디렉터리 변경 내용 복제</p></td>
<td><p>이 개체만</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalServerReadOnlyGroup</p></td>
<td><p>콘텐츠 나열</p>
<p>모든 속성 읽기</p>
<p>사용 권한 읽기</p></td>
<td><p>이 개체만</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>콘텐츠 나열</p>
<p>모든 속성 읽기</p>
<p>사용 권한 읽기</p></td>
<td><p>이 개체만</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>RTCUserSearchPropertySet 읽기</p>
<p>RTCUserProvisioningPropertySet 읽기</p>
<p>RTCPropertySet 읽기</p>
<p>공용 정보 읽기</p>
<p>개인 정보 읽기</p>
<p>일반 정보 읽기</p>
<p>사용자 계정 제한 사항 읽기</p></td>
<td><p>하위 Contact 개체</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>자식 항목 만들기</p>
<p>자식 항목 삭제</p>
<p>트리 삭제</p></td>
<td><p>Contact</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>displayName 쓰기</p>
<p>description 쓰기</p>
<p>telephoneNumber 쓰기</p></td>
<td><p>하위 User 개체</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>RTCUserSearchPropertySet 쓰기</p>
<p>otherIpPhone 쓰기</p>
<p>displayName 쓰기</p>
<p>description 쓰기</p>
<p>telephoneNumber 쓰기</p>
<p>msExchUCVoiceMailSettings 쓰기</p>
<p>RTCUserProvisioningPropertySet 쓰기</p>
<p>RTCPropertySet 쓰기</p>
<p>proxyAddresses 쓰기</p></td>
<td><p>하위 Contact 개체</p></td>
</tr>
</tbody>
</table>


## InetOrgPerson 개체에 대한 사용 권한 부여

OU의 InetOrgPerson 개체에 대해 **Grant-CsOuPermission** cmdlet을 실행하면 다음 표에 나타난 것처럼 그룹이 사용 권한을 부여받습니다.

### InetOrgPerson 개체에 대해 부여되는 사용 권한

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>그룹</th>
<th>사용 권한</th>
<th>적용 대상</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCHSUniversalServices</p></td>
<td><p>디렉터리 변경 내용 복제</p></td>
<td><p>이 개체만</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalServerReadOnlyGroup</p></td>
<td><p>콘텐츠 나열</p>
<p>모든 속성 읽기</p>
<p>사용 권한 읽기</p></td>
<td><p>이 개체만</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>콘텐츠 나열</p>
<p>모든 속성 읽기</p>
<p>사용 권한 읽기</p></td>
<td><p>이 개체만</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>RTCUserSearchPropertySet 읽기</p>
<p>RTCUserProvisioningPropertySet 읽기</p>
<p>RTCPropertySet 읽기</p>
<p>개인 정보 읽기</p>
<p>공용 정보 읽기</p>
<p>일반 정보 읽기</p>
<p>사용자 계정 제한 사항 읽기</p></td>
<td><p>하위 inetOrgPerson 개체</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>RTCUserSearchPropertySet 쓰기</p>
<p>RTCUserProvisioningPropertySet 쓰기</p>
<p>RTCPropertySet 쓰기</p>
<p>proxyAddresses 쓰기</p></td>
<td><p>하위 inetOrgPerson 개체</p></td>
</tr>
</tbody>
</table>

