---
title: 'Lync Server 2013: 응급 전화에 대한 요구 사항 정의'
TOCTitle: 응급 전화에 대한 요구 사항 정의
ms:assetid: 5c12b517-9be6-41d0-83e2-11c78793620c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398404(v=OCS.15)
ms:contentKeyID: 49303757
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 응급 전화에 대한 요구 사항 정의

 

_**마지막으로 수정된 항목:** 2015-03-09_

Microsoft Lync Server 2013 E9-1-1 배포를 시작하기 전에 먼저 다음 섹션에 설명된 질문에 답변할 수 있어야 합니다. 필요한 계획은 배포하도록 선택한 E9-1-1 솔루션 유형에 따라 달라집니다(예: SIP 트렁크 E9-1-1 서비스 공급자 또는 ELIN(Emergency Location Identification Number) 게이트웨이). 다음 표에서는 이 계획 설명서에서 이러한 각 솔루션을 검토하는 데 필요한 섹션을 보여줍니다.

### E9-1-1 솔루션 유형별 계획 단계

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>SIP 트렁크 서비스 공급자</th>
<th>ELIN 게이트웨이</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-defining-the-scope-of-the-e9-1-1-deployment.md">Lync Server 2013에서 E9-1-1 배포 범위 정의</a></p></td>
<td><p><a href="lync-server-2013-defining-the-scope-of-the-e9-1-1-deployment.md">Lync Server 2013에서 E9-1-1 배포 범위 정의</a></p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-defining-the-network-elements-used-to-determine-location.md">Lync Server 2013에서 위치를 확인하는 데 사용되는 네트워크 요소 정의</a></p></td>
<td><p><a href="lync-server-2013-defining-the-network-elements-used-to-determine-location.md">Lync Server 2013에서 위치를 확인하는 데 사용되는 네트워크 요소 정의</a></p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-enabling-users-for-e9-1-1.md">Lync Server 2013에서 사용자가 E9-1-1을 사용하도록 설정</a></p></td>
<td><p><a href="lync-server-2013-enabling-users-for-e9-1-1.md">Lync Server 2013에서 사용자가 E9-1-1을 사용하도록 설정</a></p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-managing-locations-for-sip-trunk-service-providers.md">Lync Server 2013에서 SIP 트렁크 서비스 공급자 위치 관리</a></p></td>
<td><p><a href="lync-server-2013-managing-locations-for-elin-gateways.md">Lync Server 2013에서 ELIN 게이트웨이 위치 관리</a></p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-defining-the-user-experience-for-manually-acquiring-a-location.md">Lync Server 2013에서 위치를 수동으로 가져오기 위한 사용자 환경 정의</a></p></td>
<td><p><a href="lync-server-2013-defining-the-user-experience-for-manually-acquiring-a-location.md">Lync Server 2013에서 위치를 수동으로 가져오기 위한 사용자 환경 정의</a></p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-designing-the-sip-trunk-for-e9-1-1.md">Lync Server 2013에서 E9-1-1용 SIP 트렁크 디자인</a></p></td>
<td><p><a href="lync-server-2013-including-the-security-desk.md">Lync Server 2013에서 보안 데스크 통합</a></p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-including-the-security-desk.md">Lync Server 2013에서 보안 데스크 통합</a></p></td>
<td><p><a href="lync-server-2013-defining-the-location-policy.md">Lync Server 2013에 대한 위치 정책 정의</a></p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-choosing-an-e9-1-1-service-provider.md">Lync Server 2013에 대한 E9-1-1 서비스 공급자 선택</a></p></td>
<td><p><a href="lync-server-2013-assigning-location-policy-scope.md">Lync Server 2013에서 위치 정책 범위 할당</a></p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-defining-the-location-policy.md">Lync Server 2013에 대한 위치 정책 정의</a></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-assigning-location-policy-scope.md">Lync Server 2013에서 위치 정책 범위 할당</a></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## 이 단원의 내용

  - [Lync Server 2013에서 E9-1-1 배포 범위 정의](lync-server-2013-defining-the-scope-of-the-e9-1-1-deployment.md)

  - [Lync Server 2013에서 위치를 확인하는 데 사용되는 네트워크 요소 정의](lync-server-2013-defining-the-network-elements-used-to-determine-location.md)

  - [Lync Server 2013에서 사용자가 E9-1-1을 사용하도록 설정](lync-server-2013-enabling-users-for-e9-1-1.md)

  - [Lync Server 2013에서 SIP 트렁크 서비스 공급자 위치 관리](lync-server-2013-managing-locations-for-sip-trunk-service-providers.md)

  - [Lync Server 2013에서 ELIN 게이트웨이 위치 관리](lync-server-2013-managing-locations-for-elin-gateways.md)

  - [Lync Server 2013에서 위치를 수동으로 가져오기 위한 사용자 환경 정의](lync-server-2013-defining-the-user-experience-for-manually-acquiring-a-location.md)

  - [Lync Server 2013에서 E9-1-1용 SIP 트렁크 디자인](lync-server-2013-designing-the-sip-trunk-for-e9-1-1.md)

  - [Lync Server 2013에서 보안 데스크 통합](lync-server-2013-including-the-security-desk.md)

  - [Lync Server 2013에 대한 E9-1-1 서비스 공급자 선택](lync-server-2013-choosing-an-e9-1-1-service-provider.md)

  - [Lync Server 2013에 대한 위치 정책 정의](lync-server-2013-defining-the-location-policy.md)

  - [Lync Server 2013에서 위치 정책 범위 할당](lync-server-2013-assigning-location-policy-scope.md)

