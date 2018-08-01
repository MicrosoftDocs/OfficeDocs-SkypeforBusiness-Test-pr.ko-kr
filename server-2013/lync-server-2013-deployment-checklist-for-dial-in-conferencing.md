---
title: Lync Server 2013 전화 접속 회의 배포 검사 목록
TOCTitle: 전화 접속 회의 배포 검사 목록
ms:assetid: 9c8d3ebe-0d70-4a61-9bd0-522286cddd9a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412726(v=OCS.15)
ms:contentKeyID: 49304522
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 의 전화 접속 회의 배포 검사 목록

 

_**마지막으로 수정된 항목:** 2015-03-09_

전화 접속 회의에 필요한 구성 요소는 회의 작업을 배포할 때 배포됩니다. 전화 접속 회의를 구성하려면 먼저 Enterprise Voice 또는 중재 서버와 PSTN(공중 전화망) 게이트웨이를 배포해야 합니다.

사용자가 PSTN을 통해 오디오/비디오 회의에 참가하려면 다음 표에 설명된 모든 단계를 수행해야 합니다.


> [!NOTE]
> Office Communications Server 2007 R2에서 마이그레이션하는 경우에는 전화 접속 회의를 배포하기 전에 최신 업데이트를 Office Communications Server 2007 R2 환경에 적용해야 합니다.



### 전화 접속 회의 배포 프로세스

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
<td><p><strong>중재 서버 및 PSTN 게이트웨이를 비롯하여 회의 작업이 포함된 토폴로지를 만들고 프런트 엔드 풀 또는 Standard Edition 서버를 배포합니다.</strong></p></td>
<td><ol>
<li><p>토폴로지 작성기를 실행하여 토폴로지를 구성합니다. 토폴로지를 구성할 때 전화 접속 회의 옵션을 선택합니다.</p></li>
<li><p>토폴로지를 게시하고 프런트 엔드 풀 또는 Standard Edition 서버를 배포합니다.</p></li>
<li><p>필요한 경우 독립 실행형 중재 서버를 만들어 PSTN 게이트웨이와 연결합니다.</p>


> [!NOTE]
> 이 단계는 Enterprise Voice를 배포하지 않고 중재 서버를 Enterprise Edition프런트 엔드 서버 또는 Standard Edition 서버와 함께 배치하지 않은 경우에만 필요합니다. Enterprise Voice를 배포하는 경우에는 Enterprise Voice 배포의 일부로 중재 서버 및 PSTN 게이트웨이를 설치 및 구성하고, 중재 서버를 배치하는 경우에는 프런트 엔드 풀 또는 Standard Edition 서버 배포의 일부로 중재 서버를 설치 및 구성합니다.


</li>
</ol></td>
<td><p>DomainAdmins</p>
<p>RTCUniversalServerAdmins</p>
<p>Administrator</p></td>
<td><ul>
<li><p><a href="lync-server-2013-deploying-lync-server.md">Lync Server 2013 배포</a></p></li>
<li><p>독립 실행형 중재 서버 풀을 만드는 방법: <a href="lync-server-2013-deploying-mediation-servers-and-defining-peers.md">Lync Server 2013에서 중재 서버 배포 및 피어 정의</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>다이얼 플랜을 구성합니다.</strong></p></td>
<td><p>다이얼 플랜은 특정 위치에서 걸려온 전화 번호를 전화 권한 부여 및 통화 라우팅을 위해 단일 표준(E.164) 형식으로 변환하는 전화 번호 정규화 규칙 집합입니다. 다른 위치에서 걸려온 동일한 전화 번호는 해당 다이얼 플랜에 따라 각 위치에 적절한 다른 E.164 번호로 확인될 수 있습니다. Enterprise Voice를 배포할 때 다이얼 플랜을 설정한 경우 다이얼 플랜이 전화 접속 회의에도 적용되는지 확인해야 합니다. Enterprise Voice를 배포하지 않은 경우에는 전화 접속 회의에 대한 다이얼 플랜을 설정해야 합니다.</p>
<p>Lync Server 2013 제어판 또는 Lync Server 관리 셸을 사용하여 다음과 같이 다이얼 플랜을 설정합니다.</p>
<ol>
<li><p>전화 접속 액세스 번호 라우팅에 대한 하나 이상의 다이얼 플랜을 만듭니다.</p></li>
<li><p>각 풀에 기본 다이얼 플랜을 할당합니다. <strong>전화 접속 회의 지역</strong>을 다이얼 플랜이 적용되는 지리적 위치로 설정합니다. 이 지역은 다이얼 플랜을 전화 접속 액세스 번호와 연결합니다.</p></li>
</ol></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-dial-plans-for-dial-in-conferencing.md">Lync Server 2013에서 전화 접속 회의에 대한 다이얼 플랜 구성</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>다이얼 플랜에 지역이 할당되었는지 확인합니다.</strong></p></td>
<td><p><strong>Get-CsDialPlan</strong> 및 <strong>Set-CsDialPlan</strong> cmdlet을 실행하여 모든 다이얼 플랜에 지역이 할당되었는지 확인합니다.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-make-sure-dial-plans-have-assigned-regions.md">Lync Server 2013의 다이얼 플랜에 할당된 지역이 있는지 확인</a></p></td>
</tr>
<tr class="even">
<td><p><strong>(선택 사항) 사용자 PIN(개인 식별 번호) 요구 사항을 확인하거나 수정합니다.</strong></p></td>
<td><p>Lync Server 2013 제어판 또는 Lync Server 관리 셸을 사용하여 회의 <strong>PIN 정책</strong>을 보거나 수정합니다. 최소 PIN 길이, 최대 로그온 시도 횟수, PIN 만료 날짜 및 공통 패턴 허용 여부를 지정할 수 있습니다.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-optional-verify-pin-policy-settings.md">(선택 사항) Lync Server 2013에서 PIN 정책 설정 확인</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>전화 접속 회의를 지원하도록 회의 정책을 구성합니다.</strong></p></td>
<td><p>Lync Server 2013 제어판 또는 Lync Server 관리 셸을 사용하여 <strong>회의 정책</strong> 설정을 구성합니다. 다음 사항을 지정합니다.</p>
<ul>
<li><p>PSTN 전화 회의 전화 접속 사용 여부</p></li>
<li><p>사용자가 익명 참가자를 초대할 수 있는지 여부</p></li>
<li><p>인증되지 않은 사용자가 전화 접속 전화를 사용하여 전화 회의에 참가할 수 있는지 여부. 전화 접속 전화를 사용하면 전화 회의 서버에서 사용자에게 전화를 걸고 사용자는 이 전화에 응답하여 회의에 참가할 수 있습니다.</p></li>
</ul></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-conferencing-policy-for-dial-in.md">Lync Server 2013에서 전화 접속에 대한 회의 정책 구성</a></p></td>
</tr>
<tr class="even">
<td><p><strong>전화 접속 액세스 번호를 구성합니다.</strong></p></td>
<td><p>Lync Server 2013 제어판 또는 Lync Server 관리 셸을 사용하여 사용자가 전화 회의에 전화 접속하는 액세스 번호를 설정하고 이 액세스 번호를 적절한 다이얼 플랜과 연결하는 지역을 지정합니다. 이끌이의 다이얼 플랜에 지정된 지역에 대한 처음 3개의 액세스 번호가 전화 회의 초대에 포함됩니다. 모든 액세스 번호는 전화 접속 회의 설정 페이지에서 확인할 수 있습니다.</p>


> [!NOTE]
> 전화 접속 액세스 번호를 만든 후 사용자가 올바른 액세스 번호를 보다 쉽게 식별할 수 있도록 <STRONG>Set-CsDialInConferencingAccessNumber</STRONG> cmdlet을 사용하여 Active Directory 연락처 개체의 표시 이름을 수정할 수 있습니다.


</td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-dial-in-conferencing-access-numbers.md">Lync Server 2013에서 전화 접속 회의 액세스 번호 구성</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>(선택 사항) 전화 접속 회의 설정을 확인합니다.</strong></p></td>
<td><p><strong>Get-CsDialinConferencingAccessNumber</strong> cmdlet을 사용하여 액세스 번호에 사용되지 않는 전화 접속 회의 지역이 있는 다이얼 플랜 및 할당된 지역이 없는 액세스 번호에 대한 다이얼 플랜을 검색합니다.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p>
<p>CsViewOnlyAdministrator</p>
<p>CsHelpDesk</p></td>
<td><p><a href="lync-server-2013-optional-verify-dial-in-conferencing-settings.md">(선택 사항) Lync Server 2013에서 전화 접속 회의 설정 확인</a></p></td>
</tr>
<tr class="even">
<td><p><strong>(선택 사항) DTMF 명령의 키 매핑을 수정합니다.</strong></p></td>
<td><p><strong>Set-CsDialinConferencingDtmfConfiguration</strong> cmdlet을 사용하여 DTMF(Dual-Tone Multifrequency) 명령에 사용되는 키를 수정합니다. 참가자는 이 키를 사용하여 전화 회의 설정(예: 음소거 및 음소거 해제 또는 잠금 및 잠금 해제)을 제어할 수 있습니다.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-optional-modify-key-mapping-for-dtmf-commands.md">(선택 사항) Lync Server 2013에서 DTMF 명령에 대한 키 매핑 수정</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>(선택 사항) 전화 회의 참가 및 나가기 알림 동작을 수정합니다.</strong></p></td>
<td><p><strong>Set-CsDialinConferencingConfiguration</strong>을 사용하여 참가자가 전화 회의에 참가하고 나갈 때 알림 작동 방식을 변경합니다.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-optional-enable-and-disable-conference-join-and-leave-announcements.md">(선택 사항) Lync Server 2013에서 회의 참가/나가기 알림 활성화/비활성화</a></p></td>
</tr>
<tr class="even">
<td><p><strong>(선택 사항) 전화 접속 회의를 확인합니다.</strong></p></td>
<td><p><strong>Test-CsDialInConferencing</strong> cmdlet을 사용하여 지정된 풀에 대한 액세스 번호가 올바르게 작동하는지 테스트합니다.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-optional-verify-dial-in-conferencing.md">(선택 사항) Lync Server 2013에서 전화 접속 회의 확인</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>Lync 2013용 온라인 모임 추가 기능을 배포합니다.</strong></p></td>
<td><p>사용자가 전화 접속 회의를 지원하는 전화 회의를 예약할 수 있도록 Lync 2013용 온라인 모임 추가 기능을 배포합니다. Lync 2013용 온라인 모임 추가 기능은 Lync 2013을 설치할 때 자동으로 설치됩니다.</p></td>
<td><p>Administrators</p></td>
<td><p><a href="lync-server-2013-deploy-the-online-meeting-add-in-for-lync-2013.md">Lync 2013용 온라인 모임 추가 기능 배포</a></p></td>
</tr>
<tr class="even">
<td><p><strong>사용자 계정 설정을 구성합니다.</strong></p></td>
<td><p>Lync Server 2013 제어판 또는 Lync Server 관리 셸을 사용하여 전화 <strong>줄 URI</strong>를 정규화된 고유 전화 번호(예: tel:+14255550200)로 구성합니다.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsAdministrator</p>
<p>CsUserAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-user-account-settings.md">Lync Server 2013에서 사용자 계정 설정 구성</a></p></td>
</tr>
<tr class="odd">
<td><p>(권장 사항) 회의 디렉터리 구성</p></td>
<td><p><strong>New-CsConferenceDirectory</strong> cmdlet을 사용하여 풀에 있는 모든 999명의 사용자에 대해 하나의 디렉터리를 만듭니다.</p></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-dial-in-conferencing-requirements.md">Lync Server 2013의 전화 접속 회의 요구 사항</a> <a href="recommended-create-conference-directories.md">(권장) 전화 회의 디렉터리 만들기</a></p></td>
</tr>
<tr class="even">
<td><p><strong>(선택 사항) 사용자를 전화 접속 회의에 초대하고 초기 PIN을 설정합니다.</strong></p></td>
<td><p><strong>Set-CsPinSendCAWelcomeMail</strong> 스크립트를 사용하여 사용자의 초기 PIN을 설정하고 초기 PIN 및 전화 접속 회의 설정 페이지 링크가 포함된 환영 전자 메일을 보냅니다.</p></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-optional-welcome-users-to-dial-in-conferencing.md">(선택 사항) Lync Server 2013에서 사용자에게 전화 접속 회의 시작 메시지 보내기</a></p></td>
</tr>
</tbody>
</table>

