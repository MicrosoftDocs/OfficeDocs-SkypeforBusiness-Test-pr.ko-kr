---
title: Lync Server 복원 준비
TOCTitle: Lync Server 복원 준비
ms:assetid: 857e4e02-908e-433a-96c6-be1795a9cb61
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh202179(v=OCS.15)
ms:contentKeyID: 52056898
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 복원 준비

 

_**마지막으로 수정된 항목:** 2015-03-09_

오류 발생 후 서버 및 데이터베이스의 복원을 시작하기 전에 다음을 확인해야 합니다.

  - 복원이 필요한 대상

  - 복원에 필요한 하드웨어, 소프트웨어, 데이터 및 도구

## 복원할 대상 확인

이 항목에서는 서버, 풀 또는 중앙 관리 저장소 수준에서 발생하는 Lync Server 중단을 복원하는 방법에 대해 설명합니다. 중앙 관리 저장소에 오류가 발생하면 Lync Server 배포는 계속 작동하지만 구성을 변경할 수는 없습니다. 백 엔드 서버 또는 Standard Edition 서버에 오류가 발생하면 사용자 풀의 작동이 중지됩니다. 다른 서버에 오류가 발생할 경우에는 서버가 실행 중인 서버 역할 및 서버가 하나 이상의 데이터베이스를 호스트하는지 여부에 따라 오류의 영향이 달라집니다.

### 복원할 대상

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>오류가 발생한 항목</th>
<th>다음 섹션 참조:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Standard Edition 서버</p></td>
<td><p><a href="lync-server-2013-restoring-a-standard-edition-server.md">Standard Edition 서버 복원</a></p></td>
</tr>
<tr class="even">
<td><p>중앙 관리 저장소</p></td>
<td><p><a href="lync-server-2013-restoring-the-server-hosting-the-central-management-store.md">중앙 관리 저장소를 호스트하는 서버 복원</a></p></td>
</tr>
<tr class="odd">
<td><p>Enterprise Edition 백 엔드</p></td>
<td><p><a href="lync-server-2013-restoring-an-enterprise-edition-back-end-server.md">Enterprise Edition 백 엔드 서버 복원</a></p></td>
</tr>
<tr class="even">
<td><p>Enterprise Edition 미러링된 백 엔드 기본 서버</p></td>
<td><p><a href="lync-server-2013-restoring-a-mirrored-enterprise-edition-back-end-server-primary.md">미러링된 Enterprise Edition 백 엔드 서버 복원 - 기본</a></p></td>
</tr>
<tr class="odd">
<td><p>Enterprise Edition 미러링된 백 엔드 보조 서버</p></td>
<td><p><a href="lync-server-2013-restoring-a-mirrored-enterprise-edition-back-end-server-mirror.md">미러링된 Enterprise Edition 백 엔드 서버 복원 - 미러</a></p></td>
</tr>
<tr class="even">
<td><p>서버 역할을 실행하는 모든 Enterprise Edition 서버(예: 프런트 엔드 서버, 에지 서버, 디렉터, 중재 서버 또는 영구 채팅 서버)</p></td>
<td><p><a href="lync-server-2013-restoring-an-enterprise-edition-member-server.md">Enterprise Edition 구성원 서버 복원</a></p></td>
</tr>
<tr class="odd">
<td><p>전체 Lync Server 풀</p></td>
<td><p><a href="lync-server-2013-restoring-a-lync-server-pool.md">Lync Server 풀 복원</a></p></td>
</tr>
<tr class="even">
<td><p>Enterprise Edition 파일 저장소</p></td>
<td><p><a href="lync-server-2013-restoring-a-file-store.md">파일 저장소 복원</a></p></td>
</tr>
<tr class="odd">
<td><p>독립 실행형 모니터링 데이터베이스 또는 보관 데이터베이스</p></td>
<td><p><a href="lync-server-2013-restoring-monitoring-or-archiving-data.md">모니터링 또는 보관 데이터 복원</a></p></td>
</tr>
<tr class="even">
<td><p>독립 실행형 영구 채팅 데이터베이스</p></td>
<td><p><a href="lync-server-2013-restoring-persistent-chat-data.md">영구 채팅 데이터 복원</a></p></td>
</tr>
</tbody>
</table>


## 하드웨어, 소프트웨어 및 도구 수집

서버를 복원할 때는 새 컴퓨터 또는 정상 상태의 컴퓨터로 시작해야 합니다. 또한 다음과 같은 하드웨어 및 소프트웨어를 사용할 수 있어야 합니다.

  - 오류가 발생한 서버와 FQDN(정규화된 도메인 이름)이 동일한 신규 서버 또는 깨끗한 서버.
    

    > [!IMPORTANT]
    > 운영 체제를 설치할 때는 Active Directory 도메인 서비스에서 컴퓨터 계정을 삭제하지 않도록 주의하고 해당 계정의 그룹 권한이 보존되어 있는지 확인합니다.



  - 운영 체제의 설치 소프트웨어. 운영 체제를 설치하려면 조직에서 설정된 서버 배포 절차 및 구성을 사용합니다. 서비스를 복원할 때 이러한 절차 및 구성 요구 사항을 사용할 수 있어야 합니다.

  - SQL Server 2012 또는 SQL Server 2008 R2용 설치 소프트웨어. 데이터베이스 서버를 설치하려면 적합한 버전의 SQL Server 및 조직에서 설정된 데이터베이스 서버 배포 절차와 구성을 사용합니다. 서비스를 복원할 때 이러한 절차 및 구성 요구 사항을 사용할 수 있어야 합니다.
    

    > [!NOTE]
    > 서버에 SQL Server 2012 또는 SQL Server 2008 R2를 미리 설치한 경우가 아니면, 로컬 구성 저장소가 설치된 경우 Lync Server 배포 마법사는 각 Standard Edition 서버 및 다른 모든 Lync Server 서버에 SQL Server 2012 Express를 자동으로 설치합니다.



  - 시스템 이미지 작성을 위한 소프트웨어.
    

    > [!TIP]
    > 운영 체제 및 SQL Server를 설치한 후에는 복원을 시작하기 전에 시스템의 이미지 복사본을 만들어 복원 중 오류가 발생할 경우에 대비하여 이 이미지를 롤백 지점으로 사용할 수 있게 하는 것이 좋습니다.



  - Lync Server 2013 설치 소프트웨어. Lync Server 배포 마법사는 \\setup\\amd64\\Setup.exe의 Lync Server 설치 폴더 또는 미디어에 있습니다.

복원 중에는 다음 도구를 사용합니다.

  - Lync Server 관리 셸 cmdlet

  - Import-CsUserData

  - Windows 폴더 복원을 위한 도구

  - 토폴로지 작성기

  - SQL Server 데이터베이스 유틸리티(예: SQL Server Management Studio)

## 서버 복원 준비

서버를 복원하기 전에 다음 단계를 수행해야 합니다.

1.  운영 체제를 설치합니다.

2.  서버가 백 엔드 서버인 경우 SQL Server 2012 또는 SQL Server 2008 R2를 설치합니다.

3.  인증서를 복원하거나 다시 등록합니다. 인증서에 대한 자세한 내용은 [Lync Server 2013의 백업 및 복원 요구 사항: 데이터](lync-server-2013-backup-and-restoration-requirements-data.md)에서 "추가 백업 요구 사항"을 참조하십시오.

4.  복원을 시작하기 전에 복원 중 오류가 발생할 것에 대비하여 롤백 지점으로 사용할 시스템 이미지를 만듭니다.


> [!NOTE]
> 이 항목의 이 절차와 관련 항목에 설명된 Lync Server 배포 마법사 및 cmdlet은 필요한 모든 ACL(액세스 제어 목록)을 설정합니다.



복원을 시작하기 전에 복원하려는 구성 요소에 필요한 하드웨어 및 소프트웨어를 사용할 수 있는지 확인합니다. 운영 체제 및 SQL Server를 설치한 후 다음 복원 절차의 단계 대부분은 원격으로 실행할 수 있습니다. 다른 부분은 해당 절차에서 설명합니다.

또한 복원을 시작하기 전에 이 문서의 워크시트에 있는 정보와 같이 조직의 백업 및 복원 계획과 마지막 백업 정보를 사용할 수 있도록 준비해야 합니다. 자세한 내용은 [백업 및 복원 워크시트](lync-server-2013-backup-and-restoration-worksheets.md)를 참조하십시오.

