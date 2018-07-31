---
title: 'Lync Server 2013: 응답 그룹 배포 프로세스'
TOCTitle: 응답 그룹 배포 프로세스
ms:assetid: d390c8a1-dc6e-44d8-b386-2be1fca9877c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205270(v=OCS.15)
ms:contentKeyID: 49305128
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 응답 그룹 배포 프로세스

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 섹션에서는 응답 그룹 응용 프로그램 배포 시 수행하는 단계를 간략하게 설명합니다.

### 응답 그룹 배포 프로세스

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
<th>사용 권한</th>
<th>배포 설명서</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>응답 그룹 응용 프로그램 설치</p></td>
<td><p>Enterprise Voice를 배포하면 기본적으로 응답 그룹 응용 프로그램이 설치 및 활성화됩니다.</p></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-deploying-enterprise-voice.md">Lync Server 2013에서 Enterprise Voice 배포</a></p></td>
</tr>
<tr class="even">
<td><p>응답 그룹용 구성 요소 설치</p></td>
<td><p>Lync Server cmdlet, Lync Server 제어판, 응답 그룹 구성 도구, 에이전트의 로그인/로그아웃 콘솔 및 응답 그룹 클라이언트 웹 서비스가 웹 서비스의 일부로 설치됩니다. 웹 서비스는 Enterprise Edition 풀 또는 Standard Edition 서버를 배포할 때 설치됩니다.</p></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-deploying-lync-server.md">Lync Server 2013 배포</a></p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 및 Enterprise Voice에 대해 사용자 설정</p></td>
<td><p>Lync Server 및 Enterprise Voice의 에이전트가 될 사용자를 설정합니다. 사용자를 에이전트 그룹에 추가하려면 먼저 사용자를 사용하도록 설정해야 합니다. 일반적으로 사용자는 Enterprise Edition 또는 Standard Edition 서버 배포 시 Lync Server에 대해 사용하도록 설정됩니다. 또한 Enterprise Voice 배포 시 Enterprise Voice에 대해 사용하도록 설정됩니다.</p></td>
<td><p>RTCUniversalUserAdmins</p>
<p>CsUserAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-disable-or-re-enable-user-account-for-lync-server.md">사용자 계정에서 Lync Server를 사용하거나 사용하지 않도록 설정</a></p>
<p><a href="lync-server-2013-enable-users-for-enterprise-voice.md">Lync Server 2013에서 사용자가 Enterprise Voice를 사용할 수 있도록 설정</a></p></td>
</tr>
<tr class="even">
<td><p>에이전트 그룹, 큐 및 워크플로로 구성된 응답 그룹 만들기 및 구성</p></td>
<td><ol>
<li><p>Lync Server 제어판 또는 Lync Server 관리 셸을 사용하여 다음을 수행합니다.</p>
<ol>
<li><p>에이전트 그룹 만들기 및 구성</p></li>
<li><p>큐 만들기 및 구성</p></li>
</ol></li>
<li><p>선택적으로 Lync Server 관리 셸을 사용하여 미리 정의된 응답 그룹 업무 시간 및 휴일을 만들 수 있습니다.</p></li>
<li><p>응답 그룹 구성 도구 또는 Lync Server 관리 셸을 사용하여, 사용자 지정 응답 그룹 업무 시간 및 휴일을 비롯한 워크플로(헌트 그룹 또는 IVR(대화형 음성 응답) 통화 흐름)를 만듭니다.</p>

> [!NOTE]
> Lync Server 제어판을 통해 응답 그룹 구성 도구에 액세스할 수 있습니다.


</li>
</ol></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p>
<p>CsResponseGroupManager</p></td>
<td><p><a href="lync-server-2013-create-response-group-agent-groups.md">Lync Server 2013에서 응답 그룹 에이전트 그룹 만들기</a></p>
<p><a href="lync-server-2013-create-response-group-queues.md">Lync Server 2013에서 응답 그룹 큐 만들기</a></p>
<p><a href="lync-server-2013-optional-define-response-group-business-hours.md">(선택 사항) Lync Server 2013에서 응답 그룹 업무 시간 정의</a></p>
<p><a href="lync-server-2013-optional-define-response-group-holiday-sets.md">(선택 사항) Lync Server 2013에서 응답 그룹 휴일 집합 정의</a></p>
<p><a href="lync-server-2013-create-or-modify-a-workflow.md">Lync Server 2013에서 워크플로 만들기 또는 수정</a></p></td>
</tr>
<tr class="odd">
<td><p>(선택 사항) 응용 프로그램 수준 설정의 사용자 지정</p></td>
<td><p>Lync Server 관리 셸을 사용하여 기본 대기 음악 구성, 기본 대기 음악 오디오 파일, 에이전트의 되걸기 유예 기간, 통화 컨텍스트 구성 등을 사용자 지정할 수 있습니다.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-managing-application-level-response-group-settings.md">Lync Server 2013에서 응용 프로그램 수준 응답 그룹 설정 관리</a></p></td>
</tr>
<tr class="even">
<td><p>(선택 사항) 응답 그룹 관리 위임</p></td>
<td><p>사용자를 CsResponseGroupManager 역할에 할당하여 응답 그룹 구성 작업을 위임합니다. 그런 다음 응답 그룹 관리자는 할당받은 응답 그룹을 구성할 수 있습니다.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-planning-for-role-based-access-control.md">Lync Server 2013의 역할 기반 액세스 제어 계획</a></p></td>
</tr>
<tr class="odd">
<td><p>응답 그룹 배포 확인</p></td>
<td><p>헌트 그룹 및 대화형 음성 응답 워크플로에 대한 통화 응답을 테스트하여 구성이 예상대로 작동하는지 확인합니다.</p></td>
<td><p>-</p></td>
<td><p>-</p></td>
</tr>
</tbody>
</table>

