---
title: 'Lync Server 2013: SQL Server에 대한 배포 권한'
TOCTitle: SQL Server에 대한 배포 권한
ms:assetid: 56ea0c02-bcf5-4d45-aa13-570531c29074
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398375(v=OCS.15)
ms:contentKeyID: 49303678
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 SQL Server에 대한 배포 권한

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013을 설치하고 배포할 때 Microsoft SQL Server 2012에는 특정 요구 사항이 있습니다. Windows와 SQL Server는 보안을 서로 다르게 정의하므로, Active Directory 도메인에 관리자로 로그인한다고 해서 SQL Server에 대한 사용 권한이 암시적으로 부여되지는 않습니다. 즉, 구성 중인 SQL Server 기반 서버에서 sysadmin 엔터티의 구성원이어야 합니다.

## 데이터베이스 및 Lync Server 설치에 필요한 사용 권한

다음 옵션은 Lync Server 2013 파일 및 SQL Server 데이터베이스 설치를 위한 세 가지 사용 권한 및 그룹 구성원 자격 연결에 대해 자세히 설명합니다. 조직의 요구 사항에 가장 적합한 시나리오를 선택하십시오.

### 사용 권한 및 그룹 구성원 연결

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>SQL Server 또는 Lync Server 2013 역할</th>
<th>역할의 일반적인 SQL Server 사용 권한 및 그룹 구성원</th>
<th>역할의 일반적인 Lync Server 2013 사용 권한 및 그룹 구성원 자격</th>
<th>사용 권한의 결과</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync Server 2013 관리자</p></td>
<td><p>SQL Server 로컬 Administrators 그룹 구성원 및 sysadmins SQL Server 보안 그룹 구성원 자격이 부여되어야 합니다.</p></td>
<td><p>RTCUniversalServerAdmins 그룹 구성원이어야 합니다.</p></td>
<td><p>Lync Server 2013 관리자가 Lync Server 2013 및 SQL Server 데이터베이스를 둘 다 설치할 수 있는 사용 권한을 가집니다.</p></td>
</tr>
<tr class="even">
<td><p>SQL Server 관리자</p></td>
<td><p>SQL Server sysadmin 그룹 구성원이거나 그와 동등한 권한을 가져야 하며, SQL Server 로컬 Administrators 그룹 구성원이어야 합니다.</p></td>
<td><p>RTCUniversalServerReadOnly 그룹 구성원이어야 합니다.</p></td>
<td><p>SQL Server 관리자가 Lync Server 2013 및 SQL Server 데이터베이스를 둘 다 설치할 수 있는 사용 권한을 가집니다.</p></td>
</tr>
<tr class="odd">
<td><p>설치 작업을 공유하는 두 관리자 모두</p></td>
<td><p>SQL Server 관리자가 sysadmins 그룹 구성원이거나 그와 동등한 권한을 가져야 하며, SQL Server 로컬 Administrators 그룹 구성원이어야 합니다.</p></td>
<td><p>Lync Server 2013 관리자가 RTCUniversalServerAdmins의 구성원이어야 합니다.</p></td>
<td><p>Lync Server 2013 관리자가 Lync Server 2013을 설치할 수는 있지만 데이터베이스를 설치할 수는 없습니다. SQL Server 관리자는 Lync Server 2013 관리자가 제공하는 Lync Server 관리 셸 and Windows PowerShell cmdlet을 사용하여 데이터베이스를 설치합니다. SQL Server 관리자가 사용하는 Lync Server 2013 관리 셸은 프런트 엔드 서버에 설치됩니다. 따라서 SQL Server 기반 서버에 Lync Server 2013 관리 도구를 설치할 필요가 없습니다.</p></td>
</tr>
</tbody>
</table>

