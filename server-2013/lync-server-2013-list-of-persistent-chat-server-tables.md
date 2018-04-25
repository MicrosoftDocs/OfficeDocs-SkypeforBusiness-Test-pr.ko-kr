---
title: 'Lync Server 2013: 영구 채팅 서버 테이블 목록'
TOCTitle: 영구 채팅 서버 테이블 목록
ms:assetid: 26c9e271-3516-4d90-b930-70fec4e359ea
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg558628(v=OCS.15)
ms:contentKeyID: 49303099
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 영구 채팅 서버 테이블 목록

 

_**마지막으로 수정된 항목:** 2015-03-09_

영구 채팅 데이터베이스 스키마는 다음 테이블로 구성됩니다.

## Active Directory 동기화


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>테이블</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-tbladcookie.md">Lync Server 2013의 tblADCookie</a></p></td>
<td><p>현재 LDAP(Lightweight Directory Access Protocol) 동기화 쿠키가 포함됩니다. 각 행은 영구 채팅 서버에서 현재 변경 사항을 모니터링 중인 Active Directory 도메인 서비스 도메인에 해당합니다. 영구 채팅 서버와 관련된 Active Directory 도메인만 이 테이블에 표시됩니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblprincipalmemberdifference.md">Lync Server 2013의 tblPrincipalMemberDifference</a></p></td>
<td><p>이후 Active Directory 동기화 단계에서 아직 처리되지 않은 그룹 구성원 자격 변경 내용(추가 및 제거된 구성원)을 포함하며 Active Directory 동기화의 첫 단계에서 사용되는 임시 테이블(tblADUpdates 테이블 포함) 중 하나입니다.</p>
<p>구성원 자격 변경 내용은 tblPrincipal 테이블에 나열되어 있거나 해당 테이블에 구성원이 이미 나열된 그룹에 대해서만 저장 또는 처리되거나 두 작업이 모두 수행됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tbladupdates.md">Lync Server 2013의 tblADUpdates</a></p></td>
<td><p>이후 Active Directory 동기화 단계에서 아직 처리되지 않은 Active Directory 도메인 서비스에 대한 변경 내용을 포함하며 Active Directory 동기화의 첫 번째 단계에서 사용되는 임시 테이블(tblPrincipalMemberDifference 테이블 포함) 중 하나입니다.</p>
<p>Active Directory에 대한 변경 내용은 tblPrincipal 테이블에 이미 나열된 사용자에 대해서만 저장 또는 처리되거나 두 작업이 모두 수행됩니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblprincipalmembers.md">Lync Server 2013의 tblPrincipalMembers</a></p></td>
<td><p>사용자 구성원 자격을 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblprincipalmeta.md">Lync Server 2013의 tblPrincipalMeta</a></p></td>
<td><p>Active Directory에서 새로 고쳐야 하는 사용자를 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblskippedaffiliations.md">Lync Server 2013의 tblSkippedAffiliations</a></p></td>
<td><p>일반적으로 Active Directory 액세스 오류 등의 일부 오류로 인해 새로 고칠 수 없는 정보를 포함합니다.</p>
<p>이 테이블은 정보 제공을 위한 것입니다. 해당 콘텐츠는 사용되지 않습니다.</p>
<p>올바르게 새로 고칠 수 없는 정보가 포함된 사용자는 tblPrincipalMeta 테이블에 보관되며 다시 새로 고칠 수 있습니다.</p></td>
</tr>
</tbody>
</table>


## 사용자, 회원 정보, 노드, 범위 및 역할


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>테이블</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-tblprincipaltype.md">Lync Server 2013의 tblPrincipalType</a></p></td>
<td><p>tblPrincipal 테이블에 포함된 항목을 분류하기 위한 사용자 유형을 포함합니다. 이 테이블은 정적 테이블입니다. 이 테이블은 데이터베이스 생성 중에 설정되며 변경되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblprincipal.md">Lync Server 2013의 tblPrincipal</a></p></td>
<td><p>모든 사용자 정보(사용자, 폴더, 그룹 등)를 포함합니다. 영구 채팅 서버는 이 정보를 플랫 이기종 목록으로 처리합니다. 여러 열은 각 사용자 유형을 기반으로 합니다.</p>
<p>이러한 사용자 중 대부분은 Active Directory에 저장된 개체의 캐시된 복사본입니다. 이러한 Active Directory 개체의 Principal 테이블에서 캐시된 복사본을 생성하는 과정을 <em>프로비저닝</em> 이라고 합니다.</p>
<p>일부 사용자는 다른 사용자보다 적극적으로 작성되며 일부 Active Directory 개체는 모두 함께 무시됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblprincipalaffiliations.md">Lync Server 2013의 tblPrincipalAffiliations</a></p></td>
<td><p>Active Directory 보안 그룹, Active Directory 컨테이너 등에서 구성원 자격을 설명하는 사용자 정보를 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblnode.md">Lync Server 2013의 tblNode</a></p></td>
<td><p>Lync Server 제어판에서 관리하는 범주 노드를 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblroletype.md">Lync Server 2013의 tblRoleType</a></p></td>
<td><p>역할 유형 및 연관된 권한 집합을 포함합니다. 이 조회 테이블은 정적 테이블입니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblscopeprincipal.md">Lync Server 2013의 tblScopePrincipal</a></p></td>
<td><p>노드에 할당된 범위를 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblprincipalrole.md">Lync Server 2013의 tblPrincipalRole</a></p></td>
<td><p>노드에 할당된 역할을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblsiopwhitelist.md">Lync Server 2013의 tblSiopWhiteList</a></p></td>
<td><p>노드와 연결할 수 있는 등록된 추가 기능을 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblenumattribute.md">Lync Server 2013의 tblEnumAttribute</a></p></td>
<td><p>tblNode 테이블에서 사용된 하드코드된 &quot;Visibility&quot; 및 &quot;Behavior&quot; 특성만 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblenumvalue.md">Lync Server 2013의 tblEnumValue</a></p></td>
<td><p>tblNode 테이블에서 사용된 하드코드된 &quot;Visibility&quot; 및 &quot;Behavior&quot; 특성의 값을 포함합니다.</p></td>
</tr>
</tbody>
</table>


## 초대, 채팅 및 기타 클라이언트 지원


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>테이블</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-tblprincipalinvites.md">Lync Server 2013의 tblPrincipalInvites</a></p></td>
<td><p>자동 초대가 설정된 모든 노드에 대해 시스템에서 프로비전된 모든 사용자에 대한 초대를 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblchat.md">Lync Server 2013의 tblChat</a></p></td>
<td><p>모든 채팅 메시지를 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tbllastinviteid.md">Lync Server 2013의 tblLastInviteId</a></p></td>
<td><p>각 사용자에 대해 생성(및 tblPrincipalInvites 테이블에서 사용)된 마지막 초대 ID가 포함됩니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tbllastchatid.md">Lync Server 2013의 tblLastChatId</a></p></td>
<td><p>각 사용자에 대해 생성(및 tblChat 테이블에서 사용)된 마지막 채팅 ID가 포함됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblpreference.md">Lync Server 2013의 tblPreference</a></p></td>
<td><p>레거시 클라이언트에서만 사용되는 사용자 클라이언트 기본 설정을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblfiletoken.md">Lync Server 2013의 tblFileToken</a></p></td>
<td><p>파일 전송 목적의 임시 토큰을 포함합니다. 파일을 업로드하거나 다운로드할 때마다 영구 채팅 서비스에서 클라이언트가 웹 서비스 파일 저장소에 액세스하기 위해 사용하는 토큰이 생성됩니다.</p></td>
</tr>
</tbody>
</table>


## 서버 지원


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>테이블</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-tblserveridentity.md">Lync Server 2013의 tblServerIdentity</a></p></td>
<td><p>영구 채팅 서버 풀의 활성 서버를 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tbladminlock.md">Lync Server 2013의 tblAdminLock</a></p></td>
<td><p>일부 관리자 명령을 실행하기 위한 관리자 잠금을 포함합니다. tblSystemRevision 테이블에서 시스템 수정 버전 항목은 각 잠금이 해제된 후 증분됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblsystemrevision.md">Lync Server 2013의 tblSystemRevision</a></p></td>
<td><p>tblAdminLock 테이블과 함께 여러 서버 간에 일관성을 확보하기 위해 사용된 수정 버전 번호 항목을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblactivepeers.md">Lync Server 2013의 tblActivePeers</a></p></td>
<td><p>영구 채팅 서비스 간의 현재 피어 투 피어 연결을 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblconfig.md">Lync Server 2013의 tblConfig</a></p></td>
<td><p>지원되지 않는 영구 채팅 서버 구성을 포함합니다.</p></td>
</tr>
</tbody>
</table>

