---
title: Lync Server 2013의 스키마 특성 및 설명
TOCTitle: Lync Server 2013의 스키마 특성 및 설명
ms:assetid: b009df76-9c22-471d-b57a-bda009a98261
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412841(v=OCS.15)
ms:contentKeyID: 49304729
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 스키마 특성 및 설명

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 섹션에서는 Lync Server 2013에서 사용되는 모든 스키마 특성에 대해 설명합니다. 특성과 관련된 클래스는 [Lync Server 2013의 클래스별 스키마 특성](lync-server-2013-schema-attributes-by-class.md)을 참조하십시오. Lync Server 2013의 새로운 클래스 및 특성 목록은 [Lync Server 2013의 스키마 변경 사항](lync-server-2013-schema-changes-in-lync-server-2013.md)을 참조하십시오.

연결된 쌍인 특성은 정방향 연결 또는 역방향 연결로 지정됩니다. 다른 개체를 참조하는 특성은 정방향 연결이고 첫 번째 개체를 다시 참조하는 대상 개체의 특성은 역방향 연결입니다. 정방향 연결은 업데이트할 수 있고 역방향 연결은 읽기 전용입니다.

일부 특성은 비트 마스크 값을 가집니다. 이러한 특성의 경우 각 설정이 비트로 표시되며 표시된 10진수 값이 비트 위치를 나타냅니다. 비트 위치는 비트 0으로 시작됩니다. 예를 들어 1(2진수)은 비트 0으로 설정되고 10000(2진수)은 비트 4로 설정됩니다. 각 비트는 속성을 나타냅니다. 다음은 몇 가지 예입니다.

  - 10000(2진수)은 10진수 값 16입니다(비트 4가 설정됨).

  - 100000000(2진수)은 10진수 값 256입니다(비트 8이 설정됨).

  - 1100(2진수)은 10진수 값 12입니다(비트 2 및 3이 설정되며 두 비트가 나타내는 속성이 활성화됨).

  - 1111000001(2진수)은 10진수 값 961입니다(비트 0, 6, 7, 8 및 9가 설정되며 이러한 각 비트에 대한 속성이 활성화됨).

### Lync Server 2013의 스키마 특성

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>특성</th>
<th>설명</th>
<th>참고 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>dnsHostName</p></td>
<td><p>이제 <strong>msRTCSIP-Pool</strong> 및 <strong>msRTCSIP-MonitoringServer</strong> 클래스와 연결된 Active Directory 도메인 서비스의 기존 특성입니다. 이 특성은 풀 또는 모니터링 서버의 FQDN(정규화된 도메인 이름)을 지정합니다.</p>
<p>각 세그먼트의 유효한 값은 63자이며 전체 FQDN의 유효한 값은 255자입니다.</p></td>
<td><p>Microsoft Office Live Communications Server 2005의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msDS-SourceObjectDN</p></td>
<td><p>이 특성은 이 개체에 해당하는 다른 포리스트에 있는 개체의 DN(고유 이름)에 대한 문자열 표시를 포함합니다. 이 특성은 메일 그룹 확장 및 자동 전화 교환에 사용됩니다. 이 특성은 Windows Server 2003 R2용 기본 Active Directory 스키마에 정의됩니다.</p>
<p>AD DS를 Windows Server 2003 R2로 업그레이드할 필요가 없도록 Active Directory 스키마 준비는 이 특성 정의를 사용하여 Windows Server 2003 스키마를 확장합니다.</p></td>
<td><p>Microsoft Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msExchUCVoiceMailSettings</p></td>
<td><p>이 다중 값 특성은 음성 메일 설정을 유지합니다. 이 특성은 Exchange 통합 메시징(UM)과 공유됩니다.</p></td>
<td><p>Microsoft Lync Server 2010의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msExchUserHoldPolicies</p></td>
<td><p>이 다중 값 특성은 사용자에게 적용되는 유지 정책에 대한 식별자를 포함합니다. 유지 정책은 사용자의 사서함 항목을 유지 기간 동안 보존합니다. 이 특성은 Exchange 2013과 공유됩니다.</p></td>
<td><p>Lync Server 2013의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-AcpInfo</p></td>
<td><p>이 특성은 사용자의 오디오 회의 공급자 정보를 저장합니다.</p></td>
<td><p>Lync Server 2010의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationDestination</p></td>
<td><p>이 특성은 응용 프로그램 대화 상대에 대한 트러스트된 서비스 항목을 가리킵니다.</p></td>
<td><p>Microsoft Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ApplicationList</p></td>
<td><p>이 특성은 응용 프로그램 서버에 있는 호스팅된 응용 프로그램의 목록을 포함합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationOptions</p></td>
<td><p>이 특성은 응용 프로그램 대화 상대에 대한 옵션을 지정합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ApplicationPrimaryLanguage</p></td>
<td><p>이 특성은 응용 프로그램 대화 상대에 대한 기본 언어를 포함합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationSecondaryLanguages</p></td>
<td><p>이 다중 값 특성은 응용 프로그램 대화 상대에 대한 보조 언어를 포함합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ApplicationServerBL</p></td>
<td><p>이 특성은 이 풀에 속한 응용 프로그램 서버의 목록을 포함합니다. 이 역방향 연결 특성에 대응하는 정방향 연결은 <strong>msRTCSIP-ApplicationServerPoolLink</strong>입니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationServerPoolLink</p></td>
<td><p>이 특성은 이 응용 프로그램 서버가 속한 풀을 가리킵니다. 이 특성은 정방향 연결이며 대응하는 역방향 연결은 <strong>msRTCSIP-ApplicationServerBL</strong>입니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ArchiveDefault(구식 항목)</p></td>
<td><p>-</p></td>
<td><p>Live Communications Server 2005의 새로운 기능</p>
<p>Office Communications Server 2007에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ArchiveDefaultFlags(구식 항목)</p></td>
<td><p>이 특성은 포리스트 경계 내에서 모든 사용자 통신을 보관할 것인지 여부를 나타내는 전역 기본값을 지정합니다. 이 특성은 보관 에이전트 계층에서 적용되며 이 특성 값의 범위는 다음과 같습니다.</p>
<ul>
<li><p><strong>TRUE</strong>: 모든 사용자 보관</p></li>
<li><p><strong>FALSE</strong>: 모든 사용자 보관 안 함.</p></li>
</ul>
<p>이 특성은 포리스트 경계 내에서 내부 네트워크의 사용자 통신을 보관하는 방법을 전역적으로 제어합니다.</p>
<p><strong>Live Communications Server 2005 동작(현재는 폐기됨)</strong></p>
<p>이 특성 값의 범위는 다음과 같습니다.</p>
<ul>
<li><p>0: 메시지 본문 보관[비트 0]</p></li>
<li><p>1: 메시지 본문 보관 안 함[비트 0]</p></li>
</ul>
<p><strong>Office Communications Server 2007 동작</strong></p>
<p>이 특성 값의 범위는 다음과 같습니다.</p>
<ul>
<li><p>0: ArchiveFederationDefaultWithoutBody(폐기됨)</p></li>
<li><p>1-2: ArchiveInternalCommunications</p></li>
<li><p>3-4: ArchiveFederatedCommunications</p></li>
<li><p>5: RecordPresenceRegistrations</p></li>
<li><p>6: RecordIMCallDetails</p></li>
<li><p>7: RecordGroupIMCallDetails</p></li>
<li><p>8: RecordFileTransferInstances</p></li>
<li><p>9: RecordAudioCallDetails</p></li>
<li><p>10: RecordVideoCallDetails</p></li>
<li><p>11: RecordRemoteAssistanceCallDetails</p></li>
<li><p>12: RecordApplicationSharingDetails</p></li>
<li><p>13: RecordMeetingInstantiations</p></li>
<li><p>14: RecordMeetingJoins</p></li>
<li><p>15: RecordDataJoins</p></li>
<li><p>16: RecordAVJoins</p></li>
</ul></td>
<td><p>Live Communications Server 2005의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ArchiveFederationDefault(구식 항목)</p></td>
<td><p>-</p></td>
<td><p>Live Communications Server 2005의 새로운 기능</p>
<p>Office Communications Server 2007에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ArchiveFederationDefaultFlags(구식 항목)</p></td>
<td><p>-</p></td>
<td><p>Live Communications Server 2005의 새로운 기능</p>
<p>Office Communications Server 2007에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ArchivingEnabled</p></td>
<td><p>이 특성은 단일 사용자의 통신을 보관할 것인지 제어하기 위해 비트 필드로 사용되는 정수입니다. 이 제어는 보관 에이전트 계층에 의해 적용됩니다. 글로벌 카탈로그 복제를 위해 표시됩니다.</p>
<p>이 특성의 범위는 단일 사용자 또는 연락처에 따라 다릅니다. Lync Server의 유효한 값 및 관련 비트 위치는 다음과 같습니다.</p>
<ul>
<li><p>0: 보관 안 함(비트 설정 안 함)</p></li>
<li><p>1: 폐기됨(비트 위치 0)</p></li>
<li><p>2: 폐기됨(비트 위치 1)</p></li>
<li><p>4: 내부 통신 보관(비트 위치 2)</p></li>
<li><p>8: 페더레이션 통신 보관(비트 위치 3)</p></li>
</ul>
<p>Live Communications Server 2005에서 이전의 유효한 값은 다음과 같습니다.</p>
<ul>
<li><p>0: <strong>msRTCSIP-ArchiveDefault</strong> 및 <strong>msRTCSIP-ArchiveFederation</strong>에서 정의된 기본값을 이 우선 순위에 따라 사용</p>
<ul>
<li><p>1: 보관</p></li>
<li><p>2: 보관 안 함</p></li>
<li><p>3: 메시지 본문을 제외한 모든 통신 보관</p></li>
</ul></li>
</ul></td>
<td><p>Live Communications Server 2005의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ArchivingServerData(구식 항목)</p></td>
<td><p>이 특성은 나중에 사용하기 위해 예약되어 있습니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ArchivingServerVersion(구식 항목)</p></td>
<td><p>이 특성은 보관 서비스의 버전을 정의합니다. 이 특성은 각 공식 제품 릴리스마다 일관되게 증가하는 정수 유형입니다. 사용 가능한 유효한 값은 다음과 같습니다.</p>
<ul>
<li><p>정의되지 않음: Live Communications Server 2003</p>
<p>                 Live Communications Server 2005</p>
<p>                 Live Communications Server 2005 SP1</p></li>
<li><p>3: Office Communications Server 2007</p></li>
<li><p>4: Office Communications Server 2007 R2</p></li>
</ul></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-BackEndServer</p></td>
<td><p>이 특성은 풀에 대한 백 엔드 서버의 FQDN을 지정합니다. 각 풀에 백 엔드 서버는 하나만 있을 수 있으므로 단일 값 특성입니다.</p>
<p>각 세그먼트의 유효한 값은 63자이며 전체 FQDN의 유효한 값은 255자입니다.</p></td>
<td><p>Live Communications Server 2005의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ConferenceDirectoryHomePool</p></td>
<td><p>이 특성은 전화 회의 디렉터리를 호스팅하는 풀의 식별자를 포함합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ConferenceDirectoryId</p></td>
<td><p>이 특성은 전화 회의 디렉터리의 식별자를 포함합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ConferenceDirectoryTargetPool</p></td>
<td><p>이 특성은 전화 회의 디렉터리를 이동할 풀의 식별자를 포함합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Default</p></td>
<td><p>이 부울 특성은 전화 사용이 기본 사용인지 여부를 정의합니다. 이 특성이 <strong>TRUE</strong>로 설정된 경우 전화 사용은 기본 사용이며 관리자가 삭제할 수 없습니다. 이 특성이 <strong>FALSE</strong>로 설정된 경우 전화 사용을 삭제할 수 있습니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefaultCWAExternalURL</p></td>
<td><p>이 특성은 조직 외부의 사용자에 대한 Communicator Web Access URL을 식별합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DefaultCWAInternalURL</p></td>
<td><p>이 특성은 조직 내부의 사용자에 대한 Communicator Web Access URL을 식별합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefaultLocationProfileLink(구식 항목)</p></td>
<td><p>이 단일 값 특성은 할당되는 위치 프로필 클래스 개체의 DN(고유 이름)을 포함합니다.</p>
<p>정방향 연결: <strong>연결 ID 11036</strong></p>
<p>대응하는 역방향 연결은 <strong>msRTCSIP-ServerReferenceBL</strong>입니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DefaultPolicy(구식 항목)</p></td>
<td><p>이 부울 특성은 정책이 기본 정책인지 여부를 정의합니다. <strong>TRUE</strong>로 설정된 경우 이 정책은 기본 정책입니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefaultRouteToEdgeProxy(구식 항목)</p></td>
<td><p>이 특성은 액세스 에지 서비스를 실행 중인 에지 서버의 FQDN(직접 액세스할 수 있는 경우) 또는 액세스 에지 서비스를 실행 중인 서버 풀의 하드웨어 부하 분산 장치의 FQDN을 지정합니다. 액세스 에지 서비스를 실행하는 서버를 하나 이상의 디렉터를 통해서만 액세스할 수 있는 경우 이 특성은 FQDN과 함께 선택적으로 디렉터의 포트 번호를 지정하거나 디렉터 풀을 서비스하는 하드웨어 부하 분산 장치의 포트 번호를 지정합니다.</p>
<p>각 세그먼트의 유효한 값은 63자이며 전체 FQDN의 유효한 값은 255자입니다.</p></td>
<td><p>Live Communications Server 2005의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DefaultRouteToEdgeProxyPort(구식 항목)</p></td>
<td><p>이 특성은 액세스 에지 서비스를 실행 중인 서버에 연결하는 데 사용해야 하는 포트 번호를 나타냅니다.</p>
<p>유효한 값은 사용될 포트 번호를 지정하는 정수 값입니다. 기본값은 5061입니다.</p></td>
<td><p>Live Communications Server 2005의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefPresenceSubscriptionTimeout(구식 항목)</p></td>
<td><p>이 특성은 기본 현재 상태 구독 제한 시간을 나타냅니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DefRegistrationTimeout(구식 항목)</p></td>
<td><p>이 특성은 기본 등록 제한 시간 범위를 나타냅니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefRoamingDataSubscriptionTimeout(구식 항목)</p></td>
<td><p>이 특성은 기본 로밍 데이터 구독 제한 시간 범위를 나타냅니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DeploymentLocator</p></td>
<td><p>이 특성은 분할 도메인 토폴로지에서 사용되며 FQDN(정규화된 도메인 이름)을 포함합니다.</p></td>
<td><p>Lync Server 2010의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Description(구식 항목)</p></td>
<td><p>이 단일 값 유니코드 문자열 특성은 해당 전화 경로 또는 정규화 규칙에 대한 간단한 설명을 포함합니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DomainData</p></td>
<td><p>이 특성은 나중에 사용하기 위해 예약되어 있습니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DomainName</p></td>
<td><p>이 특성은 등록자에 대한 구성된 도메인을 나타냅니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-EdgeProxyData</p></td>
<td><p>이 특성은 나중에 사용하기 위해 예약되어 있습니다.</p></td>
<td><p>Live Communications Server 2005의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-EdgeProxyFQDN</p></td>
<td><p>이 특성은 액세스 에지 서비스를 실행하는 서버의 FQDN을 지정합니다.</p>
<p>각 세그먼트의 유효한 값은 63자이며 전체 FQDN의 유효한 값은 255자입니다.</p></td>
<td><p>Live Communications Server 2005의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-EnableBestEffortNotify(구식 항목)</p></td>
<td><p>이 특성은 서버에서 클라이언트의 SUBSCRIBE 요청에 대한 응답으로 NOTIFY 요청 대신 BENOTIFY(Best Effort NOTIFY) 요청을 생성할 것인지 여부를 제어합니다. BENOTIFY는 구독 알림 핸드셰이크의 성능을 향상시킨 확장 기능으로, 서버에서 일반적인 NOTIFY 요청 대신 BENOTIFY 요청을 생성합니다. 이 경우 BENOTIFY 요청은 NOTIFY 요청에서 필요로 하는 200 OK 응답을 요구하지 않는다는 성능상의 이점이 있습니다.</p>
<p>유효한 값은 <strong>TRUE</strong> 또는 <strong>FALSE</strong>입니다.</p>


> [!NOTE]
> Live Communications Server 2003은 BENOTIFY 요청을 지원하지 않습니다. Live Communications Server 2005 및 타사 서버에서 실행되는 Live Communications Server 2003 서버 API로 작성된 서버 응용 프로그램과 상호 운용하기 위해 BENOTIFY 요청 값을 <STRONG>FALSE</STRONG>로 설정하여 BENOTIFY 요청을 비활성화할 수 있습니다. BENOTIFY는 현재 IETF(Internet Engineering Task Force) SIP 표준화 프로세스에 포함되어 있지 않습니다.


</td>
<td><p>Live Communications Server 2005의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-EnableFederation(구식 항목)</p></td>
<td><p>이 특성은 사용자가 다른 조직의 사용자와 통신하도록 허용할 것인지를 구성할 때 IT 관리자가 사용하는 전역 스위치입니다. 이 특성은 관리자가 개별 사용자의 <strong>FederationEnabled</strong> 특성을 덮어쓸 수 있도록 합니다. 이 특성은 웜, 바이러스 또는 해당 회사에 대한 공격으로 발생할 수 있는 인터넷 공격으로부터 내부 네트워크를 보호하는 데 유용합니다.</p>
<p>유효한 값 및 관련 비트 위치는 다음과 같습니다.</p>
<ul>
<li><p>1: 공용 IM 연결을 사용하도록 설정(비트 위치 0)</p></li>
<li><p>2: 예약되어 있음(비트 위치 1)</p></li>
<li><p>4: 예약되어 있음(비트 위치 2)</p></li>
<li><p>8: 예약되어 있음(비트 위치 3)</p></li>
<li><p>16: 원격 통화 제어 사용[전화 통신](비트 위치 4)</p></li>
<li><p>64: AllowOrganizeMeetingWithAnonymousParticipants(사용자가 익명 사용자를 모임에 초대하도록 허용)(비트 위치 6)</p></li>
<li><p>128: UCEnabled(사용자가 통합 통신(UC라고도 함)을 사용하도록 설정)(비트 위치 7)</p></li>
<li><p>256: EnabledForEnhancedPresence(사용자가 공용 IM 연결을 사용하도록 설정)(비트 위치 8)</p></li>
<li><p>512: RemoteCallControlDualMode(비트 위치 9)</p></li>
</ul></td>
<td><p>Live Communications Server 2005의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-EnterpriseServices</p></td>
<td><p>이 특성은 지정된 서버에서 엔터프라이즈 서비스가 로드되는지 여부를 나타냅니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ExtensionData</p></td>
<td><p>이 특성은 나중에 사용하기 위해 예약되어 있습니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ExternalAccessCode</p></td>
<td><p>이 특성은 외부 액세스에 대한 전화 걸기 코드를 포함합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-FederationEnabled</p></td>
<td><p>이 특성은 단일 사용자의 페더레이션 사용 여부를 제어합니다. 이 특성은 엔터프라이즈 서비스 계층에서 적용되며 글로벌 카탈로그 복제를 위해 표시됩니다.</p>
<p>유효한 값은 <strong>TRUE</strong> 또는 <strong>FALSE</strong>입니다.</p></td>
<td><p>Live Communications Server 2005의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-FrontEndServers</p></td>
<td><p>이 특성은 풀과 연결된 모든 Enterprise Edition Server의 도메인 이름으로 이루어진 다중 값 목록입니다.</p>
<p>역방향 연결: <strong>연결 ID 11023</strong></p>
<p>이 역방향 연결에 대응하는 정방향 연결은 <strong>msRTCSIP-PoolAddress</strong>입니다.</p></td>
<td><p>Live Communications Server 2005의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Gateways(구식 항목)</p></td>
<td><p>이 다중 값 문자열 특성은 게이트웨이 및 포트(게이트웨이별) 목록을 포함합니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-GlobalSettingsData(구식 항목)</p></td>
<td><p>이 특성은 이름:값 쌍을 저장합니다. 이미 정의된 이름:값 쌍은 <strong>현재 상태 폴링 허용</strong> 설정을 위한 것입니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-GroupingID</p></td>
<td><p>이 특성은 주소록 항목을 그룹화하는 데 사용되는 그룹의 고유 식별자입니다.</p></td>
<td><p>Lync Server 2010의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-HomeServer(구식 항목)</p></td>
<td><p>-</p></td>
<td><p>Live Communications Server 2003의 새로운 기능(사용되지 않음).</p>
<p>Live Communications Server 2005에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-HomeServerString(구식 항목)</p></td>
<td><p>-</p></td>
<td><p>Live Communications Server 2003의 새로운 기능</p>
<p>Live Communications Server 2005에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-HomeUsers(구식 항목)</p></td>
<td><p>-</p></td>
<td><p>Live Communications Server 2003의 새로운 기능(사용되지 않음).</p>
<p>Live Communications Server 2005에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-InternetAccessEnabled</p></td>
<td><p>이 특성은 단일 사용자의 외부 사용자 액세스 사용 여부를 제어합니다. 이 특성은 엔터프라이즈 서비스 계층에서 적용되며 글로벌 카탈로그 복제를 위해 표시됩니다.</p>
<p>유효한 값은 <strong>TRUE</strong> 또는 <strong>FALSE</strong>입니다.</p></td>
<td><p>Live Communications Server 2005의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-IsMaster(구식 항목)</p></td>
<td><p>-</p></td>
<td><p>Live Communications Server 2003의 새로운 기능</p>
<p>Live Communications Server 2005에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Line</p></td>
<td><p>이 단일 값 특성은 전화 통신을 위해 Lync에서 사용하는 장치 ID(사용자가 제어하는 전화의 SIP URI 또는 TEL URI)를 포함합니다. 이 특성은 글로벌 카탈로그 복제를 위해 표시되며 인덱싱됩니다. 사용자가 Enterprise Voice를 사용할 수 있는 경우 이 특성은 사용자의 전화 번호에 대한 E.164 정규화 버전을 저장합니다.</p></td>
<td><p>Microsoft Office Live Communications Server 2005 SP1의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LineServer</p></td>
<td><p>이 단일 값 특성은 CSTA-SIP 게이트웨이 서버의 SIP URI를 포함합니다. 이 특성은 글로벌 카탈로그 복제를 위해 표시되며 인덱싱되지 않습니다.</p></td>
<td><p>Microsoft Office Live Communications Server 2005 SP1의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocalNormalizationData(구식 항목)</p></td>
<td><p>이 특성은 나중에 사용하기 위해 예약되어 있습니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocalNormalizationLinks(구식 항목)</p></td>
<td><p>이 다중 값 특성은 해당 위치 프로필에 연결된 로컬 정규화 DN(고유 이름)의 목록을 포함합니다. 이 특성의 유형은 DN 바이너리입니다. 위치 프로필과 로컬 정규화 규칙 사이에는 일대다 관계가 존재합니다. 로컬 정규화 DN으로 구성된 목록의 순서는 관리자가 지정한 순서로 유지되어야 합니다. 순서 인덱스를 지정하는 DN 바이너리의 바이너리 부분에서 순서를 유지합니다.</p>
<p>정방향 연결: <strong>연결 ID 11034</strong></p>
<p>이 정방향 연결 특성에 대응하는 역방향 연결은 <strong>msRTCSIP-LocationProfileBL</strong>입니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocalNormalizationOptions</p></td>
<td><p>이 특성은 정규화 규칙에 대한 옵션 목록을 포함합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocationName(구식 항목)</p></td>
<td><p>이 단일 값 특성은 해당 프로필이 나타나는 위치를 지정하는 위치 프로필의 이름을 포함합니다. 여러 위치 프로필이 존재할 수 있으므로 관리자는 다른 프로필 간에 구별하는 방법이 필요합니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-locationProfileBL(구식 항목)</p></td>
<td><p>이 다중 값 특성은 위치 프로필 고유 이름의 목록을 포함합니다. 이 특성은 하나 이상의 위치 프로필에 대한 역방향 연결을 지정합니다.</p>
<p>역방향 연결: <strong>연결 ID 11035</strong></p>
<p>이 특성은 정방향 연결 <strong>msRTCSIP-LocalNormalizationLinks</strong>에 대응합니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocationProfileData(구식 항목)</p></td>
<td><p>이 특성은 나중에 사용하기 위해 예약되어 있습니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocationProfileOptions</p></td>
<td><p>이 특성은 위치 프로필에 대한 옵션을 포함합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MappingContact</p></td>
<td><p>이 다중 값 특성은 응용 프로그램 대화 상대의 목록을 포함합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MappingLocation</p></td>
<td><p>이 다중 값 특성은 위치 프로필의 목록을 포함합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MaxNumOutstandingSearchPerServer(구식 항목)</p></td>
<td><p>이 특성은 서버당 해결되지 않은 최대 검색 요청 수를 나타냅니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MaxNumSubscriptionsPerUser(구식 항목)</p></td>
<td><p>이 특성은 사용자당 최대 구독 수를 나타냅니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MaxPresenceSubscriptionTimeout(구식 항목)</p></td>
<td><p>이 특성은 최대 구독 제한 시간 범위를 나타냅니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MaxRegistrationsTimeout(구식 항목)</p></td>
<td><p>이 특성은 최대 등록 제한 시간 범위를 나타냅니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MaxRoamingDataSubscriptionTimeout(구식 항목)</p></td>
<td><p>이 특성은 최대 로밍 데이터 구독 제한 시간 범위를 나타냅니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUData</p></td>
<td><p>이 특성은 나중에 사용하기 위해 예약되어 있습니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCUFactoryAddress</p></td>
<td><p>이 특성은 속해 있는 MCU(Multipoint Control Unit) 센터로 되돌아가는 링크를 지정하는 컴퓨터 클래스 아래의 서비스 제어 지점 특성입니다. 모든 Microsoft MCU에 대해 이 서비스 제어 지점 및 특성이 만들어집니다. 풀 수준 설정을 검색하기 위해 각 Microsoft MCU는 속해 있는 풀의 백 엔드 서버를 찾아야 합니다.</p>
<p>이 특성 값은 MCU 센터의 DN(고유 이름)입니다. 이 특성은 단일 값 특성이며 글로벌 카탈로그 복제를 위해 표시됩니다.</p>
<p>정방향 연결: <strong>연결 ID 11026</strong></p>
<p>이 정방향 연결 특성에 대응하는 역방향 연결은 <strong>msRTCSIP-MCUServers</strong>입니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUFactoryData</p></td>
<td><p>이 특성은 예약된 다중 문자열 특성입니다. 이 특성에 저장된 설정은 이름=값 쌍으로 표시됩니다. 현재 정의된 이름=값 쌍은 다음과 같습니다.</p>
<ul>
<li><p>FactoryURL = &lt;URL&gt;</p></li>
</ul></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCUFactoryPath</p></td>
<td><p>이 특성은 풀과 연결된 단일 MCU 센터의 DN(고유 이름)을 포함하는 단일 값 특성입니다.</p>
<p>정방향 연결: <strong>연결 ID 11024</strong></p>
<p>이 정방향 연결 특성에 대응하는 역방향 연결은 <strong>msRTCSIP-PoolAddresses</strong>입니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUFactoryProviderID</p></td>
<td><p>이 특성은 MCU 센터 공급자의 GUID를 지정하는 단일 값 문자열입니다. GUID 값에 따라 MCU 센터는 해당 MCU 유형을 처리할지 여부를 결정합니다. GUID 값이 <strong>{F0810510-424F-46ef-84FE-6CC720DF1791}</strong>인 경우 MCU 센터 프로세스(Lync Server에서 기본적으로 사용 가능)가 처리합니다. 다른 GUID 값의 경우 MCU 센터 프로세스는 MCU 유형을 처리하지 않습니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCUServers</p></td>
<td><p>이 특성은 DN(고유 이름)의 다중 값 목록입니다. 이 특성은 해당 MCU 센터에 연결된 동일한 유형 및 공급업체의 모든 MCU 서버로 구성된 목록을 포함합니다. 각 세그먼트의 유효한 값은 63자이며 전체 FQDN의 유효한 값은 255자입니다.</p>
<p>역방향 연결: 연결 ID 11027</p>
<p>이 역방향 연결에 대응하는 정방향 연결은 <strong>msRTCSIP-MCUFactoryAddress</strong>입니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUType</p></td>
<td><p>이 특성은 MCU가 처리할 수 있는 미디어를 지정하는 단일 값 문자열입니다.</p>
<p>지원되는 유효한 유형은 다음과 같습니다.</p>
<ul>
<li><p>meeting</p></li>
<li><p>audio-video</p></li>
<li><p>chat</p></li>
<li><p>phone-conf</p></li>
</ul></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCUVendor</p></td>
<td><p>이 특성은 MCU 공급업체의 이름을 지정하는 단일 값 문자열입니다. 모든 Microsoft MCU는 이 특성을 <strong>Microsoft Corporation</strong>으로 지정합니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MeetingFlags(구식 항목)</p></td>
<td><p>이 특성은 모든 사용자나 연락처 개체에 대해 전역적으로 활성화되는 여러 다른 모임 옵션을 정의합니다. 이 특성은 정수 유형의 비트 마스크 값입니다.</p>
<p>유효한 값 및 관련 비트 위치는 다음과 같습니다.</p>
<ul>
<li><p>0: AllowOrganizeMeetingWithAnonymousParticipants가 None(사용자가 익명 사용자를 모임에 초대하도록 허용하지 않음)(비트 설정 안 함)</p></li>
<li><p>4: AllowOrganizeMeetingWithAnonymousParticipants가 Everyone(모든 사용자가 익명 사용자를 모임에 초대하도록 허용)(비트 위치 2)</p></li>
<li><p>8: AllowOrganizeMeetingWithAnonymousParticipants가 UsePerUserSetting(사용자가 사용자별 설정에 따라 익명 사용자를 모임에 초대하도록 허용(비트 위치 3)</p></li>
<li><p>16: UserPerUserMeetingPolicy(사용자별로 모임 정책 정의)(비트 위치 4)</p></li>
</ul></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MeetingPolicy(구식 항목)</p></td>
<td><p>이 특성은 관리자가 해당 사용자에 대해 단일 값 특성으로 할당한 정책의 DN(고유 이름)을 지정합니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MinPresenceSubscriptionTimeout(구식 항목)</p></td>
<td><p>이 특성은 최소 현재 상태 구독 제한 시간 범위를 나타냅니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MinRegistrationTimeout(구식 항목)</p></td>
<td><p>이 특성은 최소 등록 제한 시간 범위를 나타냅니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MinRoamingDataSubscriptionTimeout(구식 항목)</p></td>
<td><p>이 특성은 최소 로밍 데이터 구독 제한 시간 범위를 나타냅니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MirrorBackEndServer</p></td>
<td><p>이 특성은 프런트 엔드 풀에서 사용하는 미러링된 SQL Server 백 엔드를 저장하는 데 사용됩니다.</p></td>
<td><p>Lync Server 2013의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MobilityFlags</p></td>
<td><p>이 특성은 이동성 설정을 정의하는 옵션과 플래그를 포함합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MobilityPolicy</p></td>
<td><p>이 특성은 이동성 정책 개체에 대한 DN을 포함합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-NumDevicesPerUser(구식 항목)</p></td>
<td><p>이 특성은 사용자가 SIP 통신을 위해 등록하고 현재 상태를 구독할 수 있는 허용되는 장치 수를 나타냅니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-OptionFlags</p></td>
<td><p>이 특성은 사용자나 연락처 개체에 대해 활성화되는 옵션을 지정합니다. 이 특성은 정수 유형의 비트 마스크 값입니다. 각 옵션은 비트로 표시됩니다. 이 특성은 글로벌 카탈로그 복제를 위해 표시됩니다.</p>
<p>유효한 값 및 관련 비트 위치는 다음과 같습니다.</p>
<ul>
<li><p>1: 공용 IM(인스턴트 메시징) 연결을 사용하도록 설정(비트 위치 0)</p></li>
<li><p>2: 예약되어 있음(비트 위치 1)</p></li>
<li><p>4: 예약되어 있음(비트 위치 2)</p></li>
<li><p>8: 예약되어 있음(비트 위치 3)</p></li>
<li><p>16: 원격 통화 제어 사용[전화 통신](비트 위치 4)</p></li>
<li><p>64: AllowOrganizeMeetingWithAnonymousParticipants(사용자가 익명 사용자를 모임에 초대하도록 허용)(비트 위치 6)</p></li>
<li><p>128: UCEnabled(사용자가 UC를 사용하도록 설정)(비트 위치 7)</p></li>
<li><p>256: EnabledForEnhancedPresence(사용자가 공용 IM 연결을 사용하도록 설정)(비트 위치 8)</p></li>
<li><p>512: RemoteCallControlDualMode(비트 위치 9)</p></li>
</ul></td>
<td><p>Live Communications Server 2005 SP1의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-OriginatorSID</p></td>
<td><p>이 특성은 Windows NT 서버 주체 계정에서 사용자의 ObjectSID가 리소스 또는 중앙 포리스트에 있는 해당 사용자 또는 연락처 개체의 이 특성에 복사될 때 Single Sign-On을 사용하도록 설정하기 위해 리소스 또는 중앙 포리스트 토폴로지에서 사용됩니다. Communicator Web Access는 이 특성이나 사용자의 ObjectSID를 사용하여 AD DS에서 사용자를 검색합니다. 이 특성은 글로벌 카탈로그 복제를 위해 표시됩니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-OwnerUrn</p></td>
<td><p>이 특성은 응용 프로그램 대화 상대 소유자의 URN(Uniform Resource Name)입니다.</p></td>
<td><p>Lync Server 2010의 새로운 기능</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Pattern(구식 항목)</p></td>
<td><p>이 단일 값 문자열 특성은 전화 번호를 E.164 형식으로 일치시키기 위해 사용되는 패턴을 포함합니다. 전화 번호가 이 패턴과 일치할 경우 전화를 건 번호에 변환이 적용됩니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PhoneRouteBL(구식 항목)</p></td>
<td><p>이 다중 값 특성은 전화 경로 DN(고유 이름)의 목록을 포함합니다. 이 특성은 하나 이상의 전화 경로에 대한 역방향 연결을 지정합니다.</p>
<p>역방향 연결: <strong>연결 ID 11033</strong></p>
<p>이 특성은 정방향 연결 <strong>msRTCSIP-RouteUsageLinks</strong>에 대응합니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PhoneRouteData(구식 항목)</p></td>
<td><p>이 특성은 나중에 사용하기 위해 예약되어 있습니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PhoneRouteName(구식 항목)</p></td>
<td><p>이 단일 값 유니코드 문자열 특성은 관리자가 쉽게 참조할 수 있도록 전화 경로의 이름을 지정합니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PhoneUsageData(구식 항목)</p></td>
<td><p>이 특성은 나중에 사용하기 위해 예약되어 있습니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PolicyContent(구식 항목)</p></td>
<td><p>이 특성은 단일 값 유니코드 문자열입니다. 이 문자열 특성은 XML 형식의 정책 정의를 포함합니다. XML 스키마 정의는 여러 다른 정책 유형에서 공통되며 설정만 각 정책 유형에서 다릅니다.</p>
<p>아래에 XSD(XML 스키마 정의)가 정의되어 있습니다.</p>
<pre><code>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;
&lt;xs:schema id=&quot;instance&quot;  xmlns:xs=&quot;http://www.w3.org/2001/XMLSchema&quot; xmlns:msdata=&quot;urn:schemas-microsoft-com:xml-msdata&quot;&gt;
  &lt;xs:element name=&quot;instance&quot; msdata:IsDataSet=&quot;true&quot;&gt;
    &lt;xs:complexType&gt;
      &lt;xs:choice maxOccurs=&quot;unbounded&quot;&gt;
        &lt;xs:element name=&quot;property&quot; nillable=&quot;true&quot;&gt;
          &lt;xs:complexType&gt;
            &lt;xs:simpleContent msdata:ColumnName=&quot;property_Text&quot; msdata:Ordinal=&quot;1&quot;&gt;
              &lt;xs:extension base=&quot;xs:string&quot;&gt;
                &lt;xs:attribute name=&quot;name&quot; type=&quot;xs:string&quot; /&gt;
              &lt;/xs:extension&gt;
            &lt;/xs:simpleContent&gt;
          &lt;/xs:complexType&gt;
        &lt;/xs:element&gt;
      &lt;/xs:choice&gt;
    &lt;/xs:complexType&gt;
  &lt;/xs:element&gt;
&lt;/xs:schema&gt;</code></pre></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PolicyData(구식 항목)</p></td>
<td><p>이 특성은 나중에 사용하기 위해 예약되어 있습니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PolicyType(구식 항목)</p></td>
<td><p>이 단일 값 유니코드 문자열 특성은 정책 유형을 포함합니다. 유효한 정책 유형은 다음과 같습니다.</p>
<ul>
<li><p>meeting</p></li>
<li><p>telephony</p></li>
</ul></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PoolAddress</p></td>
<td><p>이 특성은 컴퓨터가 속한 풀로 되돌아가는 링크를 지정합니다. 이 특성은 해당 컴퓨터가 Lync Server의 Standard Edition을 실행하는지 아니면 Enterprise Edition을 실행하는지 상관없이 설정됩니다. 이 특성은 글로벌 카탈로그 복제를 위해 표시됩니다.</p>
<p>유효한 값은 풀의 도메인 이름입니다.</p>
<p>정방향 연결: <strong>연결 ID 11022</strong></p>
<p>이 정방향 연결 특성에 대응하는 역방향 연결은 <strong>msRTCSIP-FrontEndServers</strong>입니다.</p></td>
<td><p>Live Communications Server 2005의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PoolAddresses</p></td>
<td><p>이 특성은 MCU 센터가 연결된 풀의 DN(고유 이름)으로 구성된 목록을 포함하는 다중 값 특성입니다.</p>
<p>역방향 연결: <strong>연결 ID 11025</strong></p>
<p>이 역방향 연결에 대응하는 정방향 연결은 <strong>msRTCSIP-MCUFactoryPath</strong>입니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PoolData</p></td>
<td><p>이 특성은 나중에 사용하기 위해 예약되어 있습니다.</p></td>
<td><p>Live Communications Server 2005 SP1의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PoolDisplayName</p></td>
<td><p>이 특성은 관리 콘솔에서 표시되는 임의의 풀 이름을 지정합니다. 이 이름은 관리자가 변경할 수 있습니다.</p>
<p>유효한 값은 풀 이름을 나타내는 문자열입니다.</p></td>
<td><p>Live Communications Server 2005의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PoolDomainFQDN</p></td>
<td><p>이 특성은 단일 값 문자열 값입니다. 관리자가 프런트 엔드 풀이 작성된 Active Directory 도메인 구조를 따르지 않는 FQDN(예: DNS(Domain Name System) 네임스페이스에서 가입 해제된 SIP 네임스페이스)을 사용하여 프런트 엔드 풀을 만들려는 경우 이 특성 값은 풀의 도메인 FQDN을 나타냅니다.</p>
<p>프런트 엔드 풀 도메인 FQDN을 풀이 상주하는 Active Directory 도메인으로 도메인 이름 부분에 매핑하는 것이 좋습니다. 따라서 이 특성에 값이 없을 경우 프런트 엔드 풀 FQDN은 기본적으로 <strong>dnsHostName</strong> 특성에 지정된 대로 Active Directory 도메인 이름 구조입니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PoolFunctionality</p></td>
<td><p>풀과 연결된 모든 Lync Server Enterprise Edition Server의 도메인 이름으로 이루어진 다중 값 목록입니다. 정수 유형의 이 특성은 IM(인스턴트 메시징) 및 현재 상태와 모임을 풀에서 지원하는지 여부를 정의합니다.</p>
<p>사용 가능한 유효한 값 유형은 다음과 같습니다.</p>
<ul>
<li><p>정의되지 않음: IM 및 현재 상태 서비스(Live Communications Server 2005 및 2003)</p></li>
<li><p>1: IM 및 현재 상태 서비스(Lync Server)</p></li>
<li><p>2: IM 및 현재 상태와 모임 서비스(Lync Server)</p></li>
</ul></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PoolType</p></td>
<td><p>이 특성은 서버 풀이 Standard Edition Server 또는 Enterprise Edition Server를 실행 중인지 지정합니다. 이 특성은 정수 유형의 비트 마스크 값입니다. 각 옵션은 비트로 표시됩니다.</p>
<p>유효한 값 및 관련 비트 위치는 다음과 같습니다.</p>
<ul>
<li><p>1: Standard Edition Server, 사용자 호스트(비트 위치 0)</p></li>
<li><p>2: Enterprise Edition Server, 사용자 호스트(비트 위치 1)</p></li>
<li><p>4: Standard Edition Server, 응용 프로그램 호스트(비트 위치 2)</p></li>
<li><p>8: Enterprise Edition Server, 응용 프로그램 호스트(비트 위치 3)</p></li>
</ul>
<p>Lync Server은 응용 프로그램만 호스트하는 풀을 지원하지 않으므로 유효한 값은 다음뿐입니다.</p>
<ul>
<li><p>5: Standard Edition Server, 사용자 및 응용 프로그램 호스트(비트 위치 0 및 2)</p></li>
<li><p>10: Enterprise Edition Server, 사용자 및 응용 프로그램 호스트(비트 위치 1 및 3)</p></li>
</ul></td>
<td><p>Live Communications Server 2005의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PoolVersion</p></td>
<td><p>이 특성은 풀 버전을 정의합니다. 이 특성은 각 주요 제품 릴리스마다 증가하는 정수 유형입니다.</p>
<p>사용 가능한 유효한 값 유형은 다음과 같습니다.</p>
<ul>
<li><p>0: Live Communications Server 2003</p></li>
<li><p>1: Live Communications Server 2005</p></li>
<li><p>2: Live Communications Server 2005 SP1</p></li>
<li><p>3: Office Communications Server 2007</p></li>
<li><p>4: Office Communications Server 2007 R2</p></li>
<li><p>5: Lync Server 2010</p></li>
</ul></td>
<td><p>Live Communications Server 2005 SP1.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PresenceFlags</p></td>
<td><p>이 특성은 현재 상태 설정을 정의하는 옵션과 플래그를 포함합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PresencePolicy</p></td>
<td><p>이 특성은 현재 상태 정책 개체에 대한 DN을 포함합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PrimaryHomeServer</p></td>
<td><p>이 특성은 User나 Contact가 SIP 메시징을 사용하도록 합니다. 중앙 포리스트 토폴로지에서는 사용자 개체가 아닌 연락처 개체가 SIP를 사용하므로 이 특성은 연락처 클래스에 추가됩니다.</p>
<p>유효한 값은 사용자가 홈으로 지정된 Standard Edition 서버 또는 Enterprise Edition 프런트 엔드 풀의 DN입니다.</p></td>
<td><p>Live Communications Server 2005의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PrimaryUserAddress</p></td>
<td><p>이 특성은 지정된 사용자의 SIP 주소를 포함합니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PrivateLine</p></td>
<td><p>이 특성은 전용 회선 장치의 장치 ID를 포함합니다.</p></td>
<td><p>Lync Server 2010의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Routable</p></td>
<td><p>이 특성은 Lync Server가 GRUU 주소를 사용하여 해당 서비스에 라우팅할 권한을 부여받는지 여부를 결정하는 데 사용되는 부울 특성입니다. 이 값이 <strong>TRUE</strong>로 설정된 경우 Lync Server는 해당 서비스에 라우팅할 수 있습니다. 이 값이 <strong>FALSE</strong>로 설정된 경우 Lync Server는 해당 서비스에 라우팅할 수 없습니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-RouteUsageAttribute(구식 항목)</p></td>
<td><p>이 단일 값 유니코드 문자열 특성은 전화 경로에 대한 사용을 한정하는 특성을 정의합니다. 전화 경로 선택은 두 개의 요소, 즉 전화 경로에 할당된 사용 특성 및 호출자의 허용되는 정책 사용 특성에 따라 결정됩니다. 호출자의 허용되는 사용과 일치하는 사용 특성을 가진 첫 번째 전화 경로가 선택됩니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-RouteUsageLinks(구식 항목)</p></td>
<td><p>이 다중 값 DN(고유 이름) 특성은 경로 사용 고유 이름의 목록을 포함합니다.</p>
<p>정방향 연결: <strong>연결 ID 11032</strong></p>
<p>이 특성은 역방향 연결 <strong>msRTCSIP-PhoneRouteBL</strong>에 대응하는 정방향 연결입니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-RoutingPoolDN</p></td>
<td><p>이 특성은 이 MCU 또는 트러스트된 서비스에 보내는 모든 SIP 트래픽이 통과해야 하는 풀을 가리키는 DN을 포함합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-RuleName(구식 항목)</p></td>
<td><p>이 단일 값 유니코드 문자열 특성은 관리자가 쉽게 참조할 수 있도록 정규화 규칙의 이름을 지정합니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-SchemaVersion</p></td>
<td><p>이 특성은 조직에 현재 배포된 스키마 버전을 나타냅니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-SearchMaxRequests(구식 항목)</p></td>
<td><p>이 특성은 사용자가 Communicator를 사용하여 연락처를 검색할 경우 디렉터리 검색에서 반환되는 검색 결과 수를 제한합니다. 이 특성은 클라이언트가 제공한 값을 재정의합니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-SearchMaxResults(구식 항목)</p></td>
<td><p>이 특성은 반환되는 검색 요청 수를 제한합니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ServerBL</p></td>
<td><p>이 다중 값 특성은 DN(고유 이름)의 목록을 포함하는 역방향 연결입니다. 이러한 DN은 풀이나 <strong>TrustedService</strong> 개체를 가리킵니다.</p>
<p>이 특성은 정방향 연결 <strong>msRTCSIP-TrustedServiceLinks</strong>에 대응합니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ServerData</p></td>
<td><p>이 특성은 나중에 사용하기 위해 예약되어 있습니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ServerReferenceBL(구식 항목)</p></td>
<td><p>이 다중 값 특성은 고유 이름의 목록을 포함합니다. 이러한 고유 이름은 기본 위치 프로필이 할당될 수 있는 다른 서버 개체를 참조하는 역방향 연결입니다.</p>
<p>역방향 연결: <strong>연결 ID 11037</strong></p>
<p>이 역방향 연결에 대응하는 정방향 연결은 <strong>msRTCSIP-DefaultLocationProfileLink</strong>입니다.</p>
<p>이 역방향 연결 특성은 풀과 중재 서버만 참조합니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ServerVersion</p></td>
<td><p>이 특성은 서버의 버전 정보를 정의합니다. 이 버전 번호는 모든 서버 역할에 적용됩니다. 이 특성은 각 공식 제품 릴리스마다 일관되게 증가하는 정수입니다.</p>
<p>사용 가능한 유효한 값은 다음과 같습니다.</p>
<ul>
<li><p>정의되지 않음: Live Communications Server 2003</p>
<p>                 Live Communications Server 2005</p>
<p>                 Live Communications Server 2005 SP1</p></li>
<li><p>3: Office Communications Server 2007</p></li>
<li><p>4: Office Communications Server 2007 R2</p></li>
<li><p>5: Lync Server 2010</p></li>
<li><p>6: Lync Server 2013</p></li>
</ul></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-SourceObjectType</p></td>
<td><p>정수 유형의 이 단일 값 특성은 다음과 같이 <strong>msDS-SourceObjectDN</strong>이 가리키는 개체의 유형을 지정합니다.</p>
<ul>
<li><p>null | 0x00000001: 다른 포리스트의 Windows NT Server 주체 사용자 개체를 나타냅니다.</p></li>
<li><p>다음 특성은 메일 그룹 확장에 대한 다른 포리스트의 그룹 유형을 나타냅니다.</p>
<ul>
<li><p>0x00000002: ADS_GROUP_TYPE_GLOBAL_GROUP</p></li>
<li><p>0x00000004: ADS_GROUP_TYPE_DOMAIN_LOCAL_GROUP</p></li>
<li><p>0x00000004: ADS_GROUP_TYPE_LOCAL_GROUP</p></li>
<li><p>0x00000008: ADS_GROUP_TYPE_UNIVERSAL_GROUP</p></li>
<li><p>0x80000000: ADS_GROUP_TYPE_SECURITY_ENABLED</p></li>
<li><p>0x90000000: 동일한 포리스트 또는 다른 포리스트의 자동 전화 교환 또는 구독자 액세스 개체를 나타냅니다.</p></li>
</ul></li>
</ul></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-SubscriptionAuthRequired(구식 항목)</p></td>
<td><p>-</p></td>
<td><p>Live Communications Server 2003의 새로운 기능</p>
<p>Live Communications Server 2005에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TargetHomeServer</p></td>
<td><p>이 특성을 사용하면 한 Lync Server 풀에서 다른 풀로 사용자나 연락처 개체를 이동할 수 있습니다. 중앙 포리스트 토폴로지에서는 유저 개체가 아닌 사용자 개체가 SIP를 사용하므로 이 특성은 연락처 클래스에 추가됩니다.</p>
<p>유효한 값은 사용자가 이동될 대상 Standard Edition Server나 프런트 엔드 풀의 DN입니다.</p></td>
<td><p>Live Communications Server 2005의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TargetPhoneNumber(구식 항목)</p></td>
<td><p>이 단일 값 문자열 특성은 <strong>msRTCSIP-Gateways</strong>에 정의된 특정 게이트웨이로 라우팅할 전화 번호 패턴이나 범위를 포함합니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TargetUserPolicies</p></td>
<td><p>이 특성은 Lync Server 사용자에 대한 대상 정책의 이름-값 쌍을 저장합니다.</p></td>
<td><p>Lync Server 2010의 새로운 기능</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TenantId</p></td>
<td><p>이 특성은 테넌트의 고유 식별자를 저장합니다.</p></td>
<td><p>Lync Server 2010의 새로운 기능</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Translation(구식 항목)</p></td>
<td><p>이 특성은 Lync Server의 음성 기능에 사용되며 일치하는 항목이 발견된 경우 전화를 건 번호에 적용할 변환 문자열을 포함합니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedMCUData</p></td>
<td><p>이 특성은 나중에 사용하기 위해 예약되어 있습니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedMCUFQDN</p></td>
<td><p>이 특성은 MCU의 FQDN을 포함하는 문자열 값입니다. 이 특성은 단일 값 특성입니다. 각 세그먼트의 유효한 값은 63자이며 전체 FQDN의 유효한 값은 255자입니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedProxyData</p></td>
<td><p>이 특성은 나중에 사용하기 위해 예약되어 있습니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedProxyFQDN</p></td>
<td><p>이 특성은 프록시 서버를 실행하는 서버의 FQDN을 포함하는 문자열 값입니다. 이 특성은 단일 값입니다. 각 세그먼트의 유효한 값은 63자이며 전체 FQDN의 유효한 값은 255자입니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServerData</p></td>
<td><p>이 특성은 나중에 사용하기 위해 예약되어 있습니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedServerFQDN</p></td>
<td><p>이 특성은 트러스트된 서버의 FQDN을 나타내는 단일 값 특성입니다.</p></td>
<td><p>Live Communications Server 2005의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServerVersion</p></td>
<td><p>이 특성은 트러스트된 서버 목록에 있는 서버의 버전 번호를 지정합니다.</p>
<p>사용 가능한 유효한 값은 다음과 같습니다.</p>
<ul>
<li><p>NULL: Live Communications Server 2003</p></li>
<li><p>2: Live Communications Server 2005</p></li>
<li><p>3: Office Communications Server 2007</p></li>
<li><p>4: Office Communications Server 2007 R2</p></li>
<li><p>5: Lync Server 2010</p></li>
<li><p>6: Lync Server 2013</p></li>
</ul></td>
<td><p>Live Communications Server 2005의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedServiceFlags</p></td>
<td><p>이 특성은 트러스트된 서비스에 대해 활성화되는 옵션을 정의합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServiceLinks</p></td>
<td><p>이 다중 값 특성은 미디어 릴레이 인증 서비스와 같은 트러스트된 서비스 개체를 참조하는 DN(고유 이름)의 목록을 포함합니다. A/V 회의 서비스를 실행하는 에지 서버와 물리적으로 함께 배치되는 미디어 릴레이 인증 서비스는 원격 사용자를 위한 오디오 시나리오를 지원하기 위해 풀과 연결되어야 합니다.</p>
<p>이 정방향 연결 특성에 대응하는 역방향 연결은 <strong>msRTCSIP-ServerBL</strong>입니다.</p></td>
<td><p>UC</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedServicePort</p></td>
<td><p>이 특성은 해당 GRUU 서비스에 연결하는 데 사용되는 포트 번호를 정의하는 정수입니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServiceType</p></td>
<td><p>이 특성은 나타내는 GRUU 서비스의 유형을 정의하는 문자열 값입니다.</p>
<p>유효한 GRUU 서비스 유형은 다음과 같습니다.</p>
<ul>
<li><p>MediationServer</p></li>
<li><p>Gateway</p></li>
<li><p>MRAS(Media Relay Authentication Service)</p></li>
<li><p>QoSM</p></li>
<li><p>msRTCSIP-UserExtension CWA</p></li>
</ul></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedWebComponentsServerData</p></td>
<td><p>이 특성은 나중에 사용하기 위해 예약되어 있습니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedWebComponentsServerFQDN</p></td>
<td><p>이 특성은 Lync Server 웹 서비스를 실행하는 IIS의 FQDN을 포함하는 문자열 값입니다. 이 특성은 단일 값 특성입니다. 각 세그먼트의 유효한 값은 63자이며 전체 FQDN의 유효한 값은 255자입니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UCFlags(구식 항목)</p></td>
<td><p>이 특성은 모든 사용자 또는 연락처 개체에 대해 전역적으로 활성화되는 여러 다른 UC 옵션을 정의합니다. 이 특성은 정수 유형의 비트 마스크 값입니다. 각 옵션은 비트의 현재 상태로 표시됩니다.</p>
<p>유효한 값 및 관련 비트 위치는 다음과 같습니다.</p>
<ul>
<li><p>4: UsePerUserUCPolicy(비트 위치 2)</p></li>
</ul>
<p>이 비트가 설정될 경우 사용자별로 UC 정책이 정의됩니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-UCPolicy(구식 항목)</p></td>
<td><p>이 단일 값 특성은 관리자가 해당 사용자에 대해 할당한 UC 정책의 DN(고유 이름)을 포함합니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UserDomainList(구식 항목)</p></td>
<td><p>이 특성은 SIP 기능이 설정된 사용자를 호스팅하는 포리스트의 모든 도메인 목록을 제공합니다. 기본값은 빈 목록이며, 이것은 포리스트의 모든 도메인에서 SIP가 사용된다는 것을 나타냅니다.</p>
<p>유효한 값은 개별 도메인의 도메인 이름을 나타내는 여러 개의 문자열입니다.</p></td>
<td><p>Live Communications Server 2005의 새로운 기능</p>
<p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-UserEnabled</p></td>
<td><p>이 특성은 사용자가 현재 Lync Server를 사용하도록 설정되었는지 여부를 결정합니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UserExtension</p></td>
<td><p>이 다중 값 특성은 &quot;이름=값&quot; 형식으로 이름-값 쌍의 목록을 포함합니다. 이 특성은 글로벌 카탈로그 복제를 위해 표시됩니다.</p></td>
<td><p>Live Communications Server 2005 SP1의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-UserLocationProfile</p></td>
<td><p>이 특성은 위치 프로필 개체를 가리키는 DN(고유 이름)을 포함합니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UserPolicies</p></td>
<td><p>이 특성은 사용자 정책의 이름-값 쌍을 저장합니다.</p></td>
<td><p>Lync Server 2010의 새로운 기능</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-UserPolicy</p></td>
<td><p>이 특성은 여러 다른 유형의 전역 사용자 정책을 가리키는 바이너리(DN_WITH_BINARY)를 가진 고유 이름의 목록이 포함된 다중 값 특성입니다. 바이너리 부분은 DN 부분이 가리키는 정책의 유형을 나타냅니다.</p>
<p>유효한 바이너리 값은 다음과 같습니다.</p>
<ul>
<li><p>0x00000001: 모임 정책</p></li>
<li><p>0x00000002: UC 정책</p></li>
<li><p>0x00000005: 현재 상태 정책</p></li>
</ul></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UserRoutingGroupId</p></td>
<td><p>이것은 SIP 라우팅 그룹 ID입니다. 동일한 그룹의 사용자는 동일한 프런트 엔드 서버에 등록됩니다.</p></td>
<td><p>Lync Server 2013의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-WebComponentsData</p></td>
<td><p>이 특성은 다중 값 특성이며 이 특성은 나중에 사용하기 위해 예약되어 있습니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-WebComponentsPoolAddress</p></td>
<td><p>이 단일 값 특성은 웹 구성 요소가 속하는 풀 또는 Standard Edition Server를 가리킵니다.</p>
<p>정방향 연결: <strong>연결 ID 11028</strong></p>
<p>이 정방향 연결 특성에 대응하는 역방향 연결은 <strong>msRTCSIP-WebComponentsServers</strong>입니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-WebComponentsServers</p></td>
<td><p>이 특성은 고유 이름의 다중 값 목록입니다. 이 특성은 해당 풀과 연결된 모든 웹 서버의 목록을 포함합니다.</p>
<p>역방향 연결: <strong>연결 ID 11029</strong></p>
<p>이 역방향 연결에 대응하는 정방향 연결은 <strong>msRTCSIP-WebComponentsPoolAddress</strong>입니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-WMIInstanceId(구식 항목)</p></td>
<td><p>-</p></td>
<td><p>Live Communications Server 2003의 새로운 기능</p>
<p>Live Communications Server 2005에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>OtherIPPhone</p></td>
<td><p>이 기존 Active Directory 특성은 전화 통신에서 전화의 대체 TCP/IP 주소 목록을 지정하는 데 사용됩니다.</p></td>
<td><p>Windows Server 2008 운영 체제의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>PhoneOfficeOther</p></td>
<td><p>이 기존 Active Directory 특성은 통합 메시징 자동 전화 교환 및 구독자 액세스 번호에 호출을 라우팅하기 위해서 연락처 개체의 경우에 한하여 Lync Server의 음성 구성 요소에 사용됩니다. 비조건부 호출 전달 주소가 이 다중 값 특성에 저장됩니다. 자동 전화 교환 및 구독자 액세스의 특수한 목적을 위해 이 계정이 작성됩니다. 관리자가 이 계정의 특성을 수정해서는 안 됩니다.</p></td>
<td><p>Windows 2000 운영 체제의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>ProxyAddresses</p></td>
<td><p>이 기존 Active Directory 다중 값 특성은 Windows 2000에서 소개된 기본 Active Directory 스키마의 일부입니다. 이 특성은 사용자 전자 메일의 다양한 X400, X500 및 SMTP 주소를 포함합니다. Live Communications Server 2003 이상에서 사용자의 SIP URI는 &quot;sip:&quot; 태그를 사용하여 이 목록에 추가됩니다.</p>
<p>다음 응용 프로그램은 이 특성에서 사용자의 SIP URI를 검색합니다.</p>
<ul>
<li><p>Microsoft Office Outlook 2003 메시징 및 공동 작업 클라이언트</p></li>
<li><p>Microsoft Office SharePoint Server 2007</p></li>
</ul></td>
<td><p>Windows 2000 운영 체제의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>TelephoneNumber</p></td>
<td><p>이 기존 Active Directory 특성은 사용자의 전화 번호를 포함합니다.</p></td>
<td><p>Windows 2000 운영 체제의 새로운 기능</p></td>
</tr>
</tbody>
</table>

