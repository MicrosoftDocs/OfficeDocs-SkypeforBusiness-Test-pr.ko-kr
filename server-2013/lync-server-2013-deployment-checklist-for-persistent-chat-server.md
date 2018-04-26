---
title: 'Lync Server 2013: 영구 채팅 서버용 배포 검사 목록'
TOCTitle: 영구 채팅 서버용 배포 검사 목록
ms:assetid: b1108f8f-88a2-4660-8086-d25ba76f7239
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412851(v=OCS.15)
ms:contentKeyID: 49304747
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 영구 채팅 서버용 배포 검사 목록

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013, 영구 채팅 서버를 배포하려면 올바른 순서로 배포해야 하며 필요한 모든 배포 단계를 완료해야 합니다.

## 배포 순서

영구 채팅 서버는 하나 이상의 Lync Server 2013, 프런트 엔드 풀 또는 하나의 Lync Server 2013, Standard Edition 서버를 비롯한 초기 토폴로지를 배포한 후 배포할 수 있습니다. 이 항목에서는 영구 채팅 서버를 기존 배포에 추가하여 배포하는 방법에 대해 설명합니다.

## 배포 프로세스

다음 표에는 영구 채팅 서버을 배포하는 기본 단계가 나와 있으며 자세한 내용을 볼 수 있는 링크도 제공됩니다.

### 영구 채팅 서버 배포 프로세스

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>작업</th>
<th>절차</th>
<th>필요한 역할 및 그룹 구성원 자격</th>
<th>관련 항목</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>하드웨어 및 소프트웨어 필수 구성 요소 설치</strong></p></td>
<td><p>시스템 요구 사항을 충족하는 하드웨어에 다음을 설치합니다.</p>
<ul>
<li><p>영구 채팅 서버프런트 엔드 서버에 다음을 설치합니다.</p></li>
</ul>
<ul>
<li><p>시스템 요구 사항을 충족하는 운영 체제</p></li>
<li><p>Lync Server 2013을 실행하는 컴퓨터에 대한 소프트웨어 필수 구성 요소</p></li>
<li><p>영구 채팅 서버 데이터베이스를 호스팅하는 서버의 SQL Server</p></li>
</ul>
<p>영구 채팅 서버 준수가 필요한 경우</p>
<ul>
<li><p>영구 채팅 서버 준수 데이터베이스를 호스팅하는 서버의 SQL Server</p></li>
</ul></td>
<td><p>로컬 Administrators 그룹의 구성원인 모든 사용자</p></td>
<td><p>지원 가능성 설명서의 <a href="lync-server-2013-supported-hardware.md">Lync Server 2013에서 지원되는 하드웨어</a></p>
<p>지원 가능성 설명서의 <a href="lync-server-2013-server-software-and-infrastructure-support.md">Lync Server 2013의 서버 소프트웨어 및 인프라 지원</a></p>
<p><a href="lync-server-2013-determining-your-system-requirements.md">Lync Server 2013의 시스템 요구 사항 확인</a></p>
<p><a href="lync-server-2013-technical-requirements-for-persistent-chat-server.md">Lync Server 2013의 영구 채팅 서버에 대한 기술 요구 사항</a></p></td>
</tr>
<tr class="even">
<td><p><strong>영구 채팅 서버(및 선택적으로 영구 채팅 준수)를 지원하는 데 필요한 적절한 내부 토폴로지 만들기</strong></p></td>
<td><p>토폴로지 작성기를 실행하여 토폴로지에 영구 채팅 서버 풀을 추가합니다.</p>
<ul>
<li><p>토폴로지에 영구 채팅 서버 구성 요소 추가</p></li>
<li><p>영구 채팅 서버 저장소(및 재해 복구용 백업 SQL Server)를 위한 SQL Server 데이터베이스 만들기</p></li>
<li><p>영구 채팅 서버 파일을 위해 Lync 파일 저장소 정의 또는 기존 Lync 파일 저장소 사용</p></li>
<li><p>이 영구 채팅 서버 풀로 요청을 라우팅할 수 있는 Lync Server 2013 풀 연결</p></li>
</ul>
<p>영구 채팅 준수가 필요한 경우</p>
<ul>
<li><p>영구 채팅 준수 저장소 추가</p></li>
<li><p>영구 채팅 서버 풀 정의 확인란을 클릭하여 준수를 사용하도록 설정</p></li>
<li><p>토폴로지 게시</p></li>
</ul>
<p>Standard Edition에 영구 채팅 서버를 설치하는 경우 영구 채팅 서버 풀의 FQDN(정규화된 도메인 이름)이 Standard Edition 서버와 일치하고 SQL Server 데이터베이스가 Standard Edition 서버의 SQL Server Express 인스턴스에 배치되어야 합니다.</p></td>
<td><p>토폴로지를 정의하려면 로컬 Users 그룹의 구성원 계정 필요</p>
<p>토폴로지를 게시하려면 Domain Admins 그룹 및 RTCUniversalServerAdmins 그룹의 구성원이고 영구 채팅 서버 파일을 위한 Lync 파일 저장소에 대한 모든 권한(읽기/쓰기/수정)(Topology Builder에서 필요한 DACL을 구성하는 데 필요함)을 가진 계정 필요</p></td>
<td><p>배포 설명서의 <a href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Lync Server 2013에서 배포에 영구 채팅 서버 추가</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>영구 채팅 서버</strong> 배포</p></td>
<td><p>영구 채팅 서버를 실행하는 모든 컴퓨터에서 Lync Server 설치 프로그램을 실행합니다. 영구 채팅 서버 설치는 Lync Server 2013 배포 마법사에 통합되어 있습니다. 이 마법사는 다음에 대한 안내를 제공합니다.</p>
<ul>
<li><p>로컬 관리 저장소 배포</p></li>
<li><p>영구 채팅 서버 서비스 설치</p></li>
<li><p>인증서 요청 및 할당</p></li>
<li><p>서비스 실행 및 시작</p></li>
</ul></td>
<td><p>로컬 Administrators 그룹의 구성원인 모든 사용자</p></td>
<td><p>배포 설명서의 <a href="lync-server-2013-deploying-persistent-chat-server.md">Lync Server 2013에서 영구 채팅 서버 배포</a></p></td>
</tr>
<tr class="even">
<td><p><strong>영구 채팅 관리자 만들기</strong></p></td>
<td><p>CsPersistentChatAdministrator 보안 그룹에 사용자를 추가합니다.</p></td>
<td><p>로컬 관리자 구성원인 모든 사용자</p></td>
<td><p>배포 설명서의 <a href="lync-server-2013-adding-a-persistent-chat-administrator.md">Lync Server 2013에서 영구 채팅 관리자 추가</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>영구 채팅 서버 구성</strong></p></td>
<td><p>다음과 같이 사용자를 구성합니다.</p>
<ul>
<li><p>사용자가 영구 채팅 서버에 액세스할 수 있도록 정책을 설정해야 합니다. 기본적으로 모든 사용자에 대해 정책이 해제되어 있으며 전역/사이트/풀/사용자 범위에서 정책을 정의할 수 있습니다.</p></li>
<li><p>구성 설정</p></li>
</ul></td>
<td><p>사용자는 CsPersistentChatAdministrator의 구성원이어야 하며, 정책을 변경하려면 사용자가 최소한 CsUserAdministrator에 속해 있어야 합니다.</p></td>
<td><p>배포 설명서의 <a href="lync-server-2013-configuring-persistent-chat-server.md">Lync Server 2013에서 영구 채팅 서버 구성</a></p></td>
</tr>
</tbody>
</table>



> [!IMPORTANT]
> 하나 이상의 영구 채팅 서버 풀을 배포할 수 있습니다. 특정 지역에서 생성된 데이터가 해당 지역에 유지되어야 하는 규제에 따라 Microsoft에서는 여러 영구 채팅 서버 풀을 지원합니다. 예를 들어 시카고에 영구 채팅 서버 풀을 배포하고 스위스의 데이터 관련 규정을 준수하기 위해 취리히에 또 하나를 배포할 경우 액세스 권한이 부여된 사용자는 두 영구 채팅 서버 풀 모두에 있는 방에 연결할 수 있습니다.


