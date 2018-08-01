---
title: 'Lync Server 2013: 보관용 배포 검사 목록'
TOCTitle: 보관용 배포 검사 목록
ms:assetid: 7479734d-be01-40d9-ad82-320a09d19d04
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205009(v=OCS.15)
ms:contentKeyID: 49304059
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 보관용 배포 검사 목록

 

_**마지막으로 수정된 항목:** 2015-03-09_

보관은 Lync Server 2013 배포의 각 프런트 엔드 서버에 자동으로 설치되지만 사용하려면 먼저 설정해야 합니다. 이 섹션에 요약된 설정에 필요한 단계에 따라 보관을 배포할 수 있습니다.

## 배포 순서

보관 설정 방법은 선택한 저장소 옵션에 따라 달라집니다.

  - 배포에 포함된 모든 사용자에 대해 Microsoft Exchange 통합을 사용하는 경우 사용자에 대해 Lync Server 2013 보관 정책을 구성할 필요가 없습니다. 대신 Exchange 2013에 있고 사서함이 원본 위치 유지로 설정된 사용자에 대해 보관을 지원하려면 Exchange 원본 위치 유지 정책을 구성해야 합니다. 이러한 정책의 구성 방법에 대한 자세한 내용은 Exchange 2013 제품 설명서를 참조하십시오.

  - 배포에 포함된 모든 사용자에 대해 Microsoft Exchange 통합을 사용하지 않는 경우, 해당 사용자에 대한 데이터를 보관할 수 있으려면 먼저 사용자에 대한 정책 및 설정을 구성하는 것뿐만 아니라 토폴로지에 Lync Server 보관 데이터베이스( SQL Server 데이터베이스)를 추가한 후 토폴로지를 게시해야 합니다. 보관 데이터베이스는 토폴로지를 처음 배포할 때 함께 배포하거나 하나 이상의 프런트 엔드 풀 또는 Standard Edition 서버를 배포한 후에 배포할 수 있습니다. 이 문서에서는 기존 배포에 보관 데이터베이스를 추가하여 배포하는 방법에 대해 설명합니다.

하나의 프런트 엔드 풀 또는 Standard Edition 서버에서 보관을 사용하도록 설정한 경우 배포에 포함된 다른 모든 프런트 엔드 풀 및 Standard Edition 서버에 대해서도 보관을 사용하도록 설정해야 합니다. 통신을 보관해야 하는 사용자가 다른 풀에서 호스팅되는 그룹 IM 대화 또는 모임에 초대될 수 있기 때문입니다. 대화 또는 모임이 호스팅되는 풀에 보관이 설정되어 있지 않으면 전체 세션이 보관되지 않을 수 있습니다. 이러한 경우 보관이 설정된 사용자의 IM은 보관할 수 있지만 회의 콘텐츠 파일 및 회의 입장 또는 퇴장 이벤트가 보관되지 않습니다.


> [!IMPORTANT]
> 조직에서 준수를 위해 보관이 중요한 경우 보관을 배포하고, 정책 및 기타 옵션을 적절한 수준으로 구성하고, 적절한 모든 사용자에 대해 보관을 사용하도록 설정한 후에 Lync Server 2013에서 이러한 사용자를 사용하도록 설정해야 합니다.



## 보관 배포 프로세스

다음 표에서는 기존 토폴로지에 보관을 배포하는 데 필요한 단계에 대한 개요를 제공합니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>단계</th>
<th>절차</th>
<th>역할 및 그룹 구성원 자격</th>
<th>설명서</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>하드웨어 및 소프트웨어 필수 구성 요소 설치</strong></p></td>
<td><ul>
<li><p>Exchange 2013을 일부 사용자 또는 모든 사용자의 보관 저장소로 사용해서 Microsoft Exchange 통합을 사용하려면 기존 Exchange 2013 배포가 필요합니다.</p></li>
<li><p>일부 또는 모든 사용자의 보관 저장소로 별도의 보관 데이터베이스(SQL Server 데이터베이스 사용)를 사용하려는 경우 해당 서버에서 보관 데이터를 저장할 SQL Server</p></li>
</ul>


> [!NOTE]
> 보관은 엔터프라이즈 풀의 프런트 엔드 서버 및 Standard Edition 서버에서 실행됩니다. 이러한 서버를 설치하는 데 필요한 것 외에 추가 하드웨어 또는 소프트웨어 요구 사항은 없습니다.


</td>
<td><p>로컬 Administrators 그룹의 구성원인 도메인 사용자</p></td>
<td><p>지원 가능성 설명서의 <a href="lync-server-2013-supported-hardware.md">Lync Server 2013에서 지원되는 하드웨어</a></p>
<p>지원 가능성 설명서의 <a href="lync-server-2013-server-software-and-infrastructure-support.md">Lync Server 2013의 서버 소프트웨어 및 인프라 지원</a></p>
<p>계획 설명서의 <a href="lync-server-2013-technical-requirements-for-archiving.md">Lync Server 2013의 보관에 대한 기술 요구 사항</a></p>
<p>배포 설명서의 <a href="lync-server-2013-setting-up-systems-and-infrastructure-for-archiving.md">Lync Server 2013에서 보관에 대한 시스템 및 인프라 설정</a></p>
<p>지원 가능성 설명서의 <a href="lync-server-2013-exchange-and-sharepoint-integration-support.md">Lync Server 2013의 Exchange Server 및 SharePoint 통합 지원</a></p></td>
</tr>
<tr class="even">
<td><p><strong>보관 지원을 위한 적합한 내부 토폴로지 만들기(배포에 포함된 모든 사용자에 대해 Microsoft Exchange 통합을 사용하지 않는 경우만 해당)</strong></p></td>
<td><p>토폴로지 작성기를 실행하여 Lync Server 2013 보관 데이터베이스( SQL Server 데이터베이스)를 토폴로지에 추가한 후 토폴로지를 게시합니다.</p></td>
<td><p>보관 데이터베이스를 사용하도록 토폴로지를 정의하려는 경우 로컬 Users 그룹의 구성원인 계정</p>
<p>토폴로지를 게시하려면 Domain Admins 그룹 및 RTCUniversalServerAdmins 그룹의 구성원이고 Lync Server 2013 파일 저장소에 사용할 파일 공유에 대한 모든 권한(읽기/쓰기/수정)(Topology Builder에서 필요한 DACL을 구성하는 데 필요함)을 가진 계정 필요</p></td>
<td><p>배포 설명서의 <a href="lync-server-2013-adding-archiving-databases-to-an-existing-lync-server-2013-deployment.md">기존 Lync Server 2013 배포에 보관 데이터베이스 추가</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>서버 간 인증 구성( Microsoft Exchange 통합을 사용하는 경우만 해당)</strong></p></td>
<td><p>Lync Server 2013 및 Exchange 2013 사이의 인증을 사용하도록 서버를 구성합니다. 보관을 사용하도록 설정하기 전에 <strong>Test-CsExchangeStorageConnectivity testuser_sipUri -Folder Dumpster</strong>를 실행하여 Exchange 보관 저장소 연결에 대한 유효성을 검사하는 것이 좋습니다.</p></td>
<td><p>서버에서 인증서를 관리하기 위한 적합한 권한이 있는 계정</p></td>
<td><p>배포 설명서 또는 작업 설명서의 <a href="lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md">Lync Server 2013에서 서버 간 인증(Oauth) 및 파트너 응용 프로그램 관리</a></p></td>
</tr>
<tr class="even">
<td><p><strong>보관 정책 및 구성 설정</strong></p></td>
<td><p>Microsoft Exchange 통합, 글로벌 정책 및 사이트/사용자 정책(모든 데이터 저장소에 대해 Microsoft Exchange 통합을 사용하지 않을 경우)과 중요 모드 및 데이터 내보내기와 제거와 같은 특정 보관 옵션의 사용 여부를 포함하는 보관 구성</p>
<p>Microsoft Exchange 통합을 사용할 경우 Exchange 원본 위치 유지 정책을 적절하게 구성합니다.</p></td>
<td><p>RTCUniversalServerAdmins 그룹(Windows PowerShell만) 또는 사용자를 CSArchivingAdministrator 또는 CSAdministrator 역할에 지정</p></td>
<td><p>배포 설명서의 <a href="lync-server-2013-configuring-support-for-archiving.md">Lync Server 2013에서 보관에 대한 지원 구성</a></p>
<p>Exchange 제품 설명서( Microsoft Exchange 통합을 사용하는 경우).</p></td>
</tr>
</tbody>
</table>


## Lync Server 및 Microsoft Exchange를 서로 다른 포리스트에 배포

Microsoft Exchange Server가 Lync Server와 동일한 포리스트에 배포되지 않은 경우 Lync Server이 배포된 포리스트에 다음 Exchange Active Directory 특성이 동기화되었는지 확인해야 합니다.

1.  msExchUserHoldPolicies

2.  proxyAddresses

이 특성은 다중 값 특성입니다. 이 특성을 동기화할 때는 기존 값이 손실되지 않도록 값을 대체하지 않고 병합해야 합니다.

