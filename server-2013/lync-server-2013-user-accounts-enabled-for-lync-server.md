---
title: Lync Server 2013에 사용되는 사용자 계정
TOCTitle: Lync Server 2013에 사용되는 사용자 계정
ms:assetid: 8021087e-5084-4a39-9fef-ab9376c6d371
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182543(v=OCS.15)
ms:contentKeyID: 49304203
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 사용되는 사용자 계정

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 섹션의 항목에서는 Lync Server 2013 제어판을 사용하여 수행할 수 있는 사용자 설정 구성에 대한 단계별 절차를 제공합니다.


> [!IMPORTANT]
> Lync Server 제어판을 사용해서는 Active Directory Domain Admins 그룹의 구성원인 사용자를 관리할 수 없습니다. Domain Admins 사용자의 경우 Lync Server 제어판을 사용해서 읽기 전용 검색 작업만 수행할 수 있습니다. Domain Admins 사용자에 대해 쓰기 작업을 수행하려면(예: Lync Server 제어판을 사용하거나 사용하지 않도록 설정, 풀 또는 정책 지정, 전화 통신 설정, SIP 주소 변경) Domain Admins 사용자로 로그온된 상태에서 Windows PowerShell cmdlet을 사용해야 합니다. Windows PowerShell cmdlet을 사용하여 사용자를 관리하는 방법에 대한 자세한 내용은 <A href="lync-server-2013-lync-server-management-shell.md">Lync Server 관리 셸</A>을 참조하십시오.



사용자 검색 또는 사용자 검색 결과 필터링과 관련된 Lync Server 2013 관리 작업을 수행할 때는 Active Directory 도메인 서비스에 특성으로 존재하지만 Microsoft Exchange Server를 배포할 때까지 전역 카탈로그에 복제되지 않는 일부 사용자 속성이 있습니다. Lync Server가 아닌 Microsoft Exchange는 설치된 전역 카탈로그에 대한 복제에 다음 특성을 표시합니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>사용자 정보</th>
<th>주소 및 전화</th>
<th>조직</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>이니셜</p></td>
<td><p>나머지 주소</p>
<p>국가/지역</p>
<p>호출기</p>
<p>팩스</p>
<p>휴대폰</p></td>
<td><p>직함</p>
<p>회사</p>
<p>부서</p>
<p>사무실</p></td>
</tr>
</tbody>
</table>


## 이 단원의 내용

  - [Lync Server 2013에 사용할 수 있는 사용자 계정에 대한 정보 보기](lync-server-2013-viewing-information-about-user-accounts-enabled-for-lync-server.md)

  - [Lync Server 2013에 사용자 사용 또는 사용 안 함](lync-server-2013-enabling-and-disabling-users-for-lync-server.md)

  - [사용자에 대한 Enterprise Voice 관리](lync-server-2013-managing-enterprise-voice-for-users.md)

  - [사용자 계정 속성 수정](lync-server-2013-modifying-user-account-properties.md)

  - [Lync Server 2013에서 외부 액세스 정책 관리](lync-server-2013-manage-external-access-policy-for-your-organization.md)

  - [사용자별 정책 할당](lync-server-2013-assigning-per-user-policies.md)

## 참고 항목

#### 개념

[사용자 관리 Cmdlet](lync-server-2013-user-management-cmdlets.md)  

#### 기타 리소스

[Lync Server 2013에서 사용자 관리](lync-server-2013-managing-users-in-lync-server.md)

