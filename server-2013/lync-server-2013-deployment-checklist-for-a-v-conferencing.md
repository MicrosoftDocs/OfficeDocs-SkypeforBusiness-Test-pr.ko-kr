---
title: Lync Server 2013의 A/V 회의에 대한 배포 검사 목록
TOCTitle: Lync Server 2013의 A/V 회의에 대한 배포 검사 목록
ms:assetid: 6d47426f-6559-407b-9ac1-2453f0b7a2a2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ619183(v=OCS.15)
ms:contentKeyID: 49303959
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 A/V 회의에 대한 배포 검사 목록

 

_**마지막으로 수정된 항목:** 2015-03-09_

다른 Lync Server 2013 구성 요소의 배포와 같이 A/V 회의 배포를 위해서는 토폴로지 작성기를 사용해서 회의를 지원하는 토폴로지를 만들고 게시해야 합니다.

## 배포 순서

초기 토폴로지를 배포할 때 회의를 동시에 배포하거나 하나 이상의 프런트 엔드 풀 또는 Standard Edition 서버를 배포한 후에 보관 서버를 배포할 수 있습니다.

## 회의 배포 프로세스

다음 표에서는 기존 토폴로지에 회의를 배포하는 데 필요한 단계에 대한 개요를 제공합니다.


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
<th>작업</th>
<th>역할 및 그룹 구성원 자격</th>
<th>설명서</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>하드웨어 및 소프트웨어 필수 구성 요소 설치</strong></p></td>
<td><p>회의는 프런트 엔드 풀 및 Standard Edition 서버의 프런트 엔드 서버에서 실행됩니다. 해당 서버를 설치하는 데 필요한 것 외에는 추가 하드웨어 또는 소프트웨어 요구 사항이 없습니다.</p>


> [!NOTE]
> Lync Server 2013에서는 Office Web Apps 및 Office Web Apps 서버를 사용하여 PowerPoint 프레젠테이션의 공유 및 렌더링을 처리합니다. Office Web Apps 서버 설치 및 구성에 대한 자세한 내용은 <A href="lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md">Office Online Server 및 Lync Server 2013과 통합 구성</A>를 참조하십시오.


</td>
<td><p>로컬 Administrators 그룹의 구성원인 도메인 사용자</p></td>
<td><p>지원 가능성 설명서의 <a href="lync-server-2013-supported-hardware.md">Lync Server 2013에서 지원되는 하드웨어</a></p>
<p>지원 가능성 설명서의 <a href="lync-server-2013-server-software-and-infrastructure-support.md">Lync Server 2013의 서버 소프트웨어 및 인프라 지원</a></p>
<p>계획 설명서의 <a href="lync-server-2013-determining-your-system-requirements.md">Lync Server 2013의 시스템 요구 사항 확인</a></p>
<p>계획 설명서의 <a href="lync-server-2013-technical-requirements-for-archiving.md">Lync Server 2013의 보관에 대한 기술 요구 사항</a></p>
<p></p></td>
</tr>
<tr class="even">
<td><p><strong>회의를 지원하는 적절한 내부 토폴로지 만들기</strong></p></td>
<td><p>토폴로지 작성기를 실행하여 토폴로지에 회의를 추가한 후 토폴로지를 게시합니다.</p></td>
<td><p>토폴로지를 정의하려면 로컬 Users 그룹의 구성원 계정 필요</p>
<p>토폴로지를 게시하려면 Domain Admins 그룹 및 RTCUniversalServerAdmins 그룹의 구성원이고 Lync Server 2013 파일 저장소에 사용할 파일 공유에 대한 모든 권한(읽기/쓰기/수정)(토폴로지 작성기에서 필요한 DACL을 구성하는 데 필요함)을 가진 계정 필요</p></td>
<td><p>배포 설명서의 <a href="lync-server-2013-define-and-configure-a-topology-in-topology-builder.md">Lync Server 2013에 대한 토폴로지 작성기에서 토폴로지 정의 및 구성</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>회의 정책 및 지원 구성</strong></p></td>
<td><p>Lync Server 2013 제어판 또는 Lync Server 관리 셸을 사용하여 회의 설정을 구성합니다.</p></td>
<td><p>RTCUniversalServerAdmins 그룹(Windows PowerShell만) 또는 사용자를 CSAdministrator 역할에 지정</p></td>
<td><p>작업 설명서의 <a href="lync-server-2013-conferencing-policies.md">Lync Server 2013의 회의 정책</a></p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 기타 리소스

[Lync Server 2013의 회의 개요](lync-server-2013-overview-of-conferencing.md)  
[Lync Server 2013에서 회의 요구 사항 정의](lync-server-2013-defining-your-requirements-for-conferencing.md)

