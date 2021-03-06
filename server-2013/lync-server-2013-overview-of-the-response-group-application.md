﻿---
title: 'Lync Server 2013: 응답 그룹 응용 프로그램 개요'
TOCTitle: 응답 그룹 응용 프로그램 개요
ms:assetid: 6cc333e7-4029-4372-86b2-016040c415fb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398513(v=OCS.15)
ms:contentKeyID: 49303952
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 응답 그룹 응용 프로그램 개요

 

_**마지막으로 수정된 항목:** 2015-03-09_

발신자가 응답 그룹에 전화를 걸면 헌트 그룹 또는 IVR(대화형 음성 응답) 질문에 대한 발신자의 응답에 따라 에이전트로 통화가 라우팅됩니다. 응답 그룹 응용 프로그램에서는 표준 응답 그룹 라우팅 방법을 사용하여 통화 가능한 다음 에이전트로 통화를 라우팅합니다. 통화 라우팅 방법에는 직렬, 최장 유휴 시간, 병렬, 라운드 로빈 및 전화 교환 라우팅이 있습니다. 전화 교환 라우팅에서는 에이전트의 현재 상태에 관계없이 모든 수신 통화가 모든 에이전트에게 동시에 연결됩니다. 통화 가능한 에이전트가 없는 경우에는 에이전트가 전화를 받을 때까지 통화가 큐에서 대기 상태로 유지됩니다. 큐에 있는 동안 발신자에게는 통화 가능한 에이전트가 전화를 받을 때까지 음악이 들립니다. 큐가 꽉 찼거나 큐에서 대기 중인 통화가 시간 초과된 경우에는 발신자에게 메시지가 제공된 다음 통화가 끊어지거나 다른 대상으로 전송됩니다. 에이전트가 전화를 받은 경우 관리자가 응답 그룹을 구성한 방법에 따라 발신자에게 에이전트의 ID가 표시되거나 표시되지 않을 수 있습니다. 에이전트는 공식 에이전트일 수도 있고 비공식 에이전트일 수도 있습니다. 공식 에이전트는 그룹에 로그인해야 그룹으로 라우팅된 전화를 받을 수 있고, 비공식 에이전트는 그룹에 로그인/로그아웃하지 않아도 전화를 받을 수 있습니다.


> [!NOTE]
> 온-프레미스 사용자만 에이전트가 될 수 있습니다. 에이전트가 온-프레미스에서 온라인으로 이동되면 응답 그룹 통화가 해당 에이전트로 라우팅되지 않습니다.




> [!NOTE]
> 응답 그룹 응용 프로그램에서는 매치 메이킹이라는 내부 서비스를 사용하여 통화를 대기시키고 통화 가능한 에이전트를 찾습니다. 응답 그룹 응용 프로그램을 실행하는 각 컴퓨터에서 매칭 메이킹 서비스를 실행할 수 있지만 Lync Server 풀당 한 번에 하나의 매치 메이킹 서비스만 활성화되고 나머지는 수동 상태로 유지됩니다. 활성 매치 메이킹 서비스가 예상치 못한 중단으로 인해 사용할 수 없게 된 경우에는 수동 매치 메이킹 서비스 중 하나가 활성화됩니다. 응답 그룹 응용 프로그램은 통화 라우팅 및 대기가 중단 없이 계속되도록 최선을 다합니다. 하지만 매치 메이킹 서비스 전환이 발생한 경우에는 당시에 전송 중인 모든 통화가 손실됩니다. 예를 들어 프런트 엔드 서버가 다운되어 전환이 발생한 경우 해당 프런트 엔드 서버의 활성 매치 메이킹 서비스에 의해 처리 중인 모든 통화도 손실됩니다.



Lync Server 2013에서 응답 그룹을 관리하는 데에는 두 가지 관리 역할인 응답 그룹 관리자 및 응답 그룹 운영자가 제공됩니다. 응답 그룹 운영자는 응답 그룹의 모든 요소를 관리합니다. 응답 그룹 관리자는 특정 요소만 관리할 수 있으며, 자신이 소유한 응답 그룹에 대해서만 관리할 수 있습니다. 새로운 관리자 역할은 Enterprise Voice에 대해 사용하도록 설정된 모든 사용자로 특정 응답 그룹에 대한 제한된 책임을 위임할 수 있으므로 관리 비용을 줄이는 데 도움이 될 수 있습니다.

새로운 관리자 역할을 사용하기 위해 Lync Server 2013응답 그룹 응용 프로그램에서는 관리 또는 비관리의 **워크플로 유형** 이 도입되었습니다. 다음 표에서는 관리 및 비관리 응답 그룹에 대해 설명합니다.

### 관리 및 비관리 응답 그룹

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>응답 그룹 유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>비관리</p></td>
<td><ul>
<li><p>비관리 응답 그룹은 지정된 관리자가 없습니다. 응답 그룹 관리자만 이러한 응답 그룹을 구성할 수 있습니다.</p></li>
<li><p>여러 비관리 응답 그룹이 큐 또는 에이전트 그룹을 공유할 수 있습니다.</p></li>
<li><p>이전 버전의 응답 그룹을 Lync Server 2013으로 마이그레이션할 때는 유형이 비관리로 설정됩니다.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>관리</p></td>
<td><ul>
<li><p>응답 그룹 관리자는 비관리 응답 그룹의 모든 요소를 구성할 수 있습니다.</p></li>
<li><p>응답 그룹 관리자는 자신에게 명시적으로 지정되지 않은 응답 그룹을 보거나 수정할 수 없습니다.</p></li>
<li><p>응답 그룹 관리자는 자신에게 명시적으로 지정된 응답 그룹의 일부 설정만 구성할 수 있습니다.</p></li>
<li><p>관리 응답 그룹은 다른 응답 그룹(관리 또는 비관리)과 큐 또는 에이전트 그룹을 공유할 수 없습니다.</p></li>
</ul></td>
</tr>
</tbody>
</table>


다음 표에서는 응답 그룹 관리자가 자신에게 지정된 응답 그룹에 대해 수행할 수 있고 수행할 수 없는 작업에 대해 설명합니다.

### 응답 그룹 관리자 기능

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>구성 가능:</th>
<th>만들기, 삭제 또는 구성 가능:</th>
<th>수행 불가:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ul>
<li><p>에이전트</p></li>
<li><p>시작 메시지</p></li>
<li><p>응답 그룹 이름</p></li>
<li><p>설명</p></li>
<li><p>표시 번호</p></li>
<li><p>업무 시간</p></li>
<li><p>대기 음악</p></li>
<li><p>상태(활성/비활성)</p></li>
<li><p>헌트 그룹 워크플로 및 IVR(대화형 음성 응답) 워크플로</p></li>
</ul></td>
<td><ul>
<li><p>에이전트 그룹</p></li>
<li><p>큐</p></li>
<li><p>휴일 집합</p></li>
</ul></td>
<td><ul>
<li><p>모든 유형의 워크플로 만들기 또는 삭제</p></li>
<li><p><strong>SIP URI</strong> , <strong>전화 번호</strong> 또는 <strong>워크플로 유형</strong> 과 같은 핵심 응답 그룹 설정 수정</p></li>
</ul></td>
</tr>
</tbody>
</table>


응답 그룹 관리자는 다음 도구를 사용하여 자신에게 지정된 응답 그룹을 관리할 수 있습니다.

  - Lync Server 제어판
    

    > [!NOTE]
    > 응답 그룹 관리자는 이 도구를 사용하여 응답 그룹 설정만 관리할 수 있습니다. 다른 Lync Server 설정은 관리자에게 제공되지 않습니다.



  - 응답 그룹 구성 도구

  - Lync Server 관리 셸

응답 그룹은 부서 또는 작업 그룹 환경에 맞게 올바르게 확장되며(자세한 내용은 [Lync Server 2013의 응답 그룹 용량 계획](lync-server-2013-capacity-planning-for-response-group.md) 참조) 완전히 새로운 전화 통신 설치에 배포할 수 있습니다. Enterprise Voice 배포 및 로컬 통신 사업자 네트워크에서 들어오는 통화를 지원합니다. 에이전트는 Lync 2013, Lync 2010, Lync 2010 Attendant 또는 Lync Phone Edition을 사용하여 여기에 통화를 라우팅할 수 있습니다.

응답 그룹 응용 프로그램은 Enterprise Voice의 구성 요소 중 하나입니다. Enterprise Voice를 배포하면 응답 그룹 응용 프로그램이 설치되고 자동으로 활성화됩니다.

