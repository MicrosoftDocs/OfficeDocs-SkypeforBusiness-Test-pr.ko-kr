---
title: 감시자 노드 설치 및 구성
TOCTitle: 감시자 노드 설치 및 구성
ms:assetid: 61f6deea-e3ef-4468-9be8-a65705815ebb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204943(v=OCS.15)
ms:contentKeyID: 49303814
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 감시자 노드 설치 및 구성

 

_**마지막으로 수정된 항목:** 2015-03-09_

*감시자 노드*는 주기적으로 Lync Server 가상 트랜잭션을 실행하는 컴퓨터입니다. *가상 트랜잭션*은 중요한 최종 사용자 시나리오(시스템에 로그인하는 기능 또는 메신저 대화를 교환할 수 있는 기능 등)가 예상한 대로 작동하는지 확인하는 Windows PowerShell cmdlet입니다. Lync Server 2013에 대해 System Center Operations Manager는 다음 표에 표시된 가상 트랜잭션을 실행할 수 있습니다. 이 표에서는 세 가지 서로 다른 가상 트랜잭션 유형을 보여줍니다.

  - **기본값**. 감시자 노드가 기본적으로 실행하는 가상 트랜잭션입니다. 새 감시자 노드를 만들 때는 해당 노드가 실행할 가상 트랜잭션을 지정할 수 있으며, **New-CsWatcherNodeConfiguration** cmdlet에서 사용되는 테스트 매개 변수가 바로 이 목적으로 사용됩니다. 감시자 노드를 만들 때 테스트 매개 변수를 사용하지 않으면 자동으로 모든 기본 가상 트랜잭션이 실행되며 기본값이 아닌 가상 트랜잭션은 실행되지 않습니다. 즉, 감시자 노드가 Test-CsAddressBookService 테스트를 실행하도록 구성된 경우 Test-CsExumConnectivity 테스트는 실행되도록 구성되지 않습니다.

  - **기본값이 아님**. 이름 그대로 기본값이 아닌 가상 트랜잭션은 감시자 노드가 기본적으로 실행하지 않는 테스트입니다. 하지만 감시자 노드가 기본값이 아닌 가상 트랜잭션을 실행하도록 설정할 수는 있습니다. 이러한 설정은 **New-CsWatcherNodeConfiguration** cmdlet을 사용하여 감시자 노드를 만들 때 또는 그 이후 언제라도 지정할 수 있습니다. 기본값이 아닌 가상 트랜잭션은 대부분의 경우 추가 설정 단계가 필요합니다. 자세한 내용은 [가상 트랜잭션에 대한 특별 설치 지침](lync-server-2013-special-setup-instructions-for-synthetic-transactions.md)을 참고하세요.

  - **확장**. 확장 테스트는 특별한 유형의 기본값이 아닌 가상 트랜잭션입니다. 다른 가상 트랜잭션과 달리 확장 테스트는 한 번의 테스트 과정 중에 여러 번 실행할 수 있습니다. 이러한 특성은 풀의 여러 PSTN(공중 전화망) 음성 경로와 같은 동작을 확인할 때 유용할 수 있습니다. 이 테스트는 단순히 확장 테스트의 여러 인스턴스를 감시자 노드에 추가하여 구성할 수 있습니다.

다른 가상 트랜잭션을 감시자 노드에 추가하는 과정에 대한 자세한 내용은 [감시자 노드 관리](lync-server-2013-managing-watcher-nodes.md)를 참고하세요. Lync Server 관리 셸을 사용하면 감시자 노드에서 가상 트랜잭션을 제거할 수 있습니다.

감시자 노드에서 사용할 수 있는 가상 트랜잭션에는 다음 항목이 포함됩니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Cmdlet 이름(테스트 이름)</th>
<th>설명</th>
<th>가상 트랜잭션 유형</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Test-CsAddressBookService(ABS)</p></td>
<td><p>사용자가 자신의 대화 상대 목록에 없는 사용자를 조회할 수 있는지 확인합니다.</p></td>
<td><p>기본값</p></td>
</tr>
<tr class="even">
<td><p>Test-CsAddressBookWebQuery(ABWQ)</p></td>
<td><p>사용자가 HTTP를 통해 자신의 대화 상대 목록에 없는 사용자를 조회할 수 있는지 확인합니다.</p></td>
<td><p>기본값</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsIM(IM)</p></td>
<td><p>사용자가 피어 투 피어 메신저를 보낼 수 있는지 확인합니다.</p></td>
<td><p>기본값</p></td>
</tr>
<tr class="even">
<td><p>Test-CsP2PAV(P2PAV)</p></td>
<td><p>사용자가 피어 투 피어 음성 통화를 걸 수 있는지 확인합니다(신호만).</p></td>
<td><p>기본값</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsPresence(Presence)</p></td>
<td><p>사용자가 다른 사용자의 현재 상태를 볼 수 있는지 확인합니다.</p></td>
<td><p>기본값</p></td>
</tr>
<tr class="even">
<td><p>Test-CsRegistration(Registration)</p></td>
<td><p>사용자가 Lync에 로그인할 수 있는지 확인합니다.</p></td>
<td><p>기본값</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsAudioConferencingProvider(ACP)</p></td>
<td><p>Lync Server 2013의 온-프레미스 버전에는 사용되지 않습니다.</p></td>
<td><p>확장</p></td>
</tr>
<tr class="even">
<td><p>Test-CsPstnPeerToPeerCall(PSTN)</p></td>
<td><p>사용자가 기업 외부에 있는 사용자와 통화를 걸거나 받을 수 있는지 확인합니다(PSTN 번호).</p></td>
<td><p>기본값이 아님, 확장</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsAVConference(AvConference)</p></td>
<td><p>사용자가 오디오/비디오 회의를 만들고 참가할 수 있는지 확인합니다.</p></td>
<td><p>기본값</p></td>
</tr>
<tr class="even">
<td><p>Test-CsAVEdgeConnectivity(AVEdgeConnectivity)</p></td>
<td><p>A/V 에지 서버가 피어 투 피어 통화 및 회의 통화에 대한 연결을 허용할 수 있는지 확인합니다.</p></td>
<td><p>기본값이 아님</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsDataConference(DataConference)</p></td>
<td><p>사용자가 화이트보드 및 설문 조사와 같은 활동을 포함하여 데이터 공동 작업 회의 및 온라인 모임에 참가할 수 있는지 확인합니다.</p></td>
<td><p>기본값이 아님</p></td>
</tr>
<tr class="even">
<td><p>Test-CsExumConnectivity(ExumConnectivity)</p></td>
<td><p>사용자가 Exchange 통합 메시징(UM)에 연결할 수 있는지 확인합니다.</p></td>
<td><p>기본값이 아님</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsGroupIM(GroupIM)</p></td>
<td><p>사용자가 회의 중 메신저 대화를 보내고 3명 이상의 사용자가 포함된 메신저 대화에 참가할 수 있는지 확인합니다.</p></td>
<td><p>기본값</p></td>
</tr>
<tr class="even">
<td><p>Test-CsGroupIM -TestJoinLauncher(JoinLauncher)</p></td>
<td><p>사용자가 웹 주소 링크를 통해 예약된 모임을 만들고 참가할 수 있는지 확인합니다.</p></td>
<td><p>기본값이 아님</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsMCXP2PIM(MCXP2PIM)</p></td>
<td><p>모바일 장치 사용자가 등록하고 메신저 대화를 보낼 수 있는지 확인합니다.</p></td>
<td><p>기본값이 아님</p></td>
</tr>
<tr class="even">
<td><p>Test-CsPersistentChatMessage(PersistentChatMessage)</p></td>
<td><p>사용자가 영구 채팅 서비스를 사용하여 메시지를 교환할 수 있는지 확인합니다.</p></td>
<td><p>기본값이 아님</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsUnifiedContactStore(UnifiedContactStore)</p></td>
<td><p>통합 연락처 저장소를 사용해서 사용자의 연락처에 액세스할 수 있는지 확인합니다. 통합 연락처 저장소는 Lync 2013, Outlook 및/또는 Outlook Web Access를 사용해서 액세스할 수 있는 단일 연락처 집합을 사용자가 유지 관리할 수 있는 방법을 제공해줍니다.</p></td>
<td><p>기본값이 아님</p></td>
</tr>
<tr class="even">
<td><p>Test-CsXmppIM(XmppIM)</p></td>
<td><p>XMPP(Extensible Messaging and Presence Protocol) 게이트웨이에서 메신저 대화를 전송할 수 있는지 확인합니다.</p></td>
<td><p>기본값이 아님</p></td>
</tr>
</tbody>
</table>


System Center Operations Manager를 사용하기 위해 감시자 노드를 설치할 필요가 없습니다. 이러한 노드를 설치하지 않아도 문제가 발생하면 Lync Server 2013 구성 요소로부터 실시간 경고를 받을 수 있습니다. 이 구성 요소 및 사용자 관리 팩에서는 감시자 노드가 사용되지 않습니다. 하지만 모니터링 활성화 관리 팩을 사용해서 종단 간 시나리오를 모니터링하려면 감시자 노드가 필요합니다.


> [!NOTE]
> 관리자는 또한 Operations Manager를 사용하거나 설치할 필요 없이 가상 트랜잭션을 수동으로 실행할 수 있습니다. 다양한 Test-Cs cmdlet에 대한 자세한 내용은 <A href="https://docs.microsoft.com/en-us/powershell/module/skype/?view=skype-ps">Lync Server 2013 Cmdlet 인덱스</A>를 참고하세요.



배포 크기에 따라 가상 트랜잭션에는 많은 양의 컴퓨터 메모리 및 프로세서 시간이 사용될 수 있습니다. 따라서 전용 컴퓨터를 감시자 노드로 사용하는 것이 좋습니다. 예를 들어 프런트 엔드 서버를 감시자 노드로 사용하도록 구성해서는 안됩니다. 감시자 노드는 다음 하드웨어 사양을 충족해야 합니다.


> [!NOTE]
> 레거시 Microsoft Lync Server 2010 감시자 노드는 Lync Server 2013 감시자 노드와 동일한 컴퓨터에 함께 배치할 수 없습니다. 그 이유는 Lync Server 2010 및 Lync Server 2013의 핵심 시스템 파일을 동일한 컴퓨터에 설치할 수 없기 때문입니다.<BR>하지만 Lync Server 2013 감시자 노드는 Lync Server 2013 및 Lync Server 2010을 모두 동시에 모니터링할 수 있습니다. 두 제품 버전 모두 기본 가상 트랜잭션이 지원됩니다.



Lync Server 2013 감시자 노드는 다음 사항을 확인하기 위해 기업 내부 또는 외부에 배포할 수 있습니다.

  -   
    기업 내부의 사용자 풀에 대한 연결

  -   
    기업 외부에서 근무하는 원격 사용자를 위한 경계 네트워크를 통한 연결

  -   
    지점 사무소 기기에 대한 연결

  -   
    기업 내부 및 경계 네트워크를 통한 Lync Server 2010 연결

관리를 간소화할 수 있도록 기업 내부 및 외부에서 다양한 인증 옵션을 사용할 수 있습니다. 자세한 내용은 [가상 트랜잭션을 실행하도록 감시자 노드 구성](lync-server-2013-configuring-a-watcher-node-to-run-synthetic-transactions.md)을 참고하세요.

감시자 노드로 작동하도록 컴퓨터를 구성하려면 System Center Operations Manager를 설치하고 Lync Server 2013 관리 팩을 가져온 후 다음 단계를 완료해야 합니다.

Lync Server 2013 핵심 파일 및 System Center 에이전트 파일을 설치하기 전에 감시자 노드 컴퓨터가 Lync Server 2013 설치를 위한 필수 구성 요소를 충족하는지 확인해야 합니다. 또한 감시자 노드 컴퓨터에는 다음과 같은 항목도 설치되어 있어야 합니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>하드웨어 구성 요소</th>
<th>최소 요구 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>다음 중 하나가 필요합니다.</p>
<ul>
<li><p>64비트 프로세서, 쿼드 코어, 2.33GHz 이상</p></li>
<li><p>64비트 2방향 프로세서, 이중 코어, 2.33GHz 이상</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>메모리</p></td>
<td><p>8GB</p></td>
</tr>
<tr class="odd">
<td><p>네트워크 운영 체제</p></td>
<td><ul>
<li><p>1개의 네트워크 어댑터, 1Gbps</p></li>
<li><p>Windows Server 2008 R2, Windows Server 2012 또는</p>
<p>Windows Server 2012 R2</p></li>
</ul></td>
</tr>
</tbody>
</table>


  - 전체 버전의 .NET Framework 4.5

  - Windows Identity Foundation

  - Windows PowerShell 3.0

이러한 모든 필수 구성 요소가 충족되었으면 다음을 통해 감시자 노드를 구성할 수 있습니다.

  - 감시자 노드 컴퓨터에 Lync Server 2013 핵심 파일 설치

  - 감시자 노드 컴퓨터에 System Center Operations Manager 에이전트 설치

  - Watchernode.msi executable 파일 실행

  - **CsWatcherNodeConfiguration** cmdlet을 사용하여 감시자 노드에 사용할 테스트 사용자 구성

