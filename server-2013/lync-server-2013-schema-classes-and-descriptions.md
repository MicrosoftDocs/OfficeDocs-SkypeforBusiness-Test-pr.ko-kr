---
title: Lync Server 2013의 스키마 클래스 및 설명
TOCTitle: Lync Server 2013의 스키마 클래스 및 설명
ms:assetid: 7d43b920-ac37-40cc-adfe-be289bda6e9e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398625(v=OCS.15)
ms:contentKeyID: 49304163
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 스키마 클래스 및 설명

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 섹션에서는 Lync Server 2013에서 사용되는 모든 스키마 클래스에 대해 설명합니다.

## 스키마 클래스 및 설명


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>클래스</th>
<th>설명</th>
<th>참고 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Mail-Recipient</p></td>
<td><p>Exchange 통합 메시징(UM) 전자 메일 수신자입니다.</p></td>
<td><p>이 보조 클래스는 Exchange UM과 공유됨</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationContacts</p></td>
<td><p>이 클래스는 여러 응용 프로그램 대화 상대에 대한 컨테이너이고 자체적으로 특성을 포함하지는 않습니다.</p></td>
<td><p>Microsoft Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ApplicationServer</p></td>
<td><p>이 클래스는 UCAS(통합 통신 응용 프로그램 서비스) 인스턴스의 서비스 제어 지점에 대한 항목을 포함하고 있습니다.</p></td>
<td><p>Office Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationServerService</p></td>
<td><p>이 클래스는 특정 풀에서 해당 응용 프로그램 서비스까지의 연결을 제공합니다.</p></td>
<td><p>Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ApplicationServerSettings</p></td>
<td><p>msRTCSIP-ApplicationServer에 대한 이 보조 클래스는 응용 프로그램 서비스의 인스턴스에 대한 설정을 나타내는 특성을 포함하고 있습니다.</p></td>
<td><p>Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Archive(사용되지 않음)</p></td>
<td><p>msRTCSIP-GlobalContainer에 대한 이 보조 클래스는 보관과 관련된 모든 설정을 포함하고 있습니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ArchivingServer(사용되지 않음)</p></td>
<td><p>이 클래스는 단일 인스턴트 메시징 보관 서버를 나타냅니다. 이 클래스의 인스턴스는 컴퓨터(예: 인스턴트 메시징 보관 서비스가 설치된 컴퓨터)가 인스턴트 메시징 보관 서버로 활성화될 때 만들어집니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ConferenceDirectories</p></td>
<td><p>이 클래스는 전화 회의 디렉터리의 여러 인스턴스에 대한 컨테이너이고 자체적으로 특성을 포함하지는 않습니다.</p></td>
<td><p>Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ConferenceDirectory</p></td>
<td><p>이 클래스는 특정 전화 회의 디렉터리에 대한 설정을 나타내는 특성을 포함하고 있습니다.</p></td>
<td><p>Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ConnectionPoint</p></td>
<td><p>컴퓨터를 Lync Server를 실행하는 서버로 지정하기 위한 일반 SCP(서비스 제어 지점)입니다.</p></td>
<td><p>Lync 2010의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefaultCWABank</p></td>
<td><p>이 보조 클래스는 Microsoft Lync Web App 뱅크에 대한 설정을 포함하고 있습니다.</p></td>
<td><p>Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Domain</p></td>
<td><p>이 클래스는 SIP 등록자의 구성된 도메인을 정의하는 특성을 포함하고 있습니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-EdgeProxy</p></td>
<td><p>이 클래스 컨테이너는 단일 액세스 에지 서비스를 나타냅니다. 액세스 에지 서비스는 경계 네트워크에 배포되고 일반적으로 고객은 경계 네트워크에서 Active Directory 도메인 서비스에 액세스하는 것을 허용하지 않으므로 액세스 에지 서비스의 인스턴스는 인트라넷의 Active Directory 네트워크에 가입되어 있지 않습니다. 따라서 액세스 프록시는 자동으로 AD DS에 등록되지 않습니다. 관리자는 AD DS에서 각 액세스 에지 서비스 인스턴스가 존재할 경우 이를 수동으로 구성해야 합니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-EnterpriseMCUSettings</p></td>
<td><p>msRTCSIP-MCU에 대한 이 보조 클래스는 회의 서버에 대한 설정을 나타내는 특성을 포함하고 있습니다.</p></td>
<td><p>Microsoft Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-EnterpriseMediationServerSettings</p></td>
<td><p>msRTCSIP-MediationServer에 대한 이 보조 클래스는 중재 서버에 대한 설정을 나타내는 특성을 포함하고 있습니다.</p></td>
<td><p>Office Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-EnterpriseServerSettings</p></td>
<td><p>msRTCSIP-Server에 대한 이 보조 클래스는 SIP 서버에 대한 설정을 나타내는 특성을 포함하고 있습니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Federation</p></td>
<td><p>msRTCSIP-GlobalContainer에 대한 이 보조 클래스는 페더레이션과 관련된 모든 설정을 포함하고 있습니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-GlobalContainer</p></td>
<td><p>이 클래스는 Lync Server 배포 전체에 적용되는 모든 설정을 포함하고 있습니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-GlobalUserPolicy(사용되지 않음)</p></td>
<td><p>이 클래스는 단일 Office Communications Server 모임 정책을 나타냅니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-GlobalTopologySetting</p></td>
<td><p>로컬 전역 토폴로지 설정 개체입니다.</p></td>
<td><p>Lync Server 2010의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-GlobalTopologySettings</p></td>
<td><p>전역 토폴로지 설정 개체를 포함할 컨테이너입니다.</p></td>
<td><p>Lync Server 2010의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocalNormalizations</p></td>
<td><p>이 클래스는 위치 정규화 규칙의 인스턴스를 나타내는 컨테이너입니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocationContactMapping</p></td>
<td><p>이 클래스는 회의 길잡이 응용 프로그램에서 만들며 회의 전화 번호를 지역별로 분류하는 데 사용되는 특성을 포함하고 있습니다.</p></td>
<td><p>Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocationContactMappings</p></td>
<td><p>이 클래스는 위치 대화 상대 매핑의 여러 인스턴스에 대한 컨테이너이고 자체적으로 특성을 포함하지는 않습니다.</p></td>
<td><p>Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocationProfile</p></td>
<td><p>이 클래스는 특정 위치 프로필을 나타내는 컨테이너입니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocationProfiles(사용되지 않음)</p></td>
<td><p>이 클래스는 여러 위치 프로필에 대한 컨테이너이고 자체적으로 특성을 포함하지는 않습니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocalNormalizations(사용되지 않음)</p></td>
<td><p>이 클래스는 여러 로컬 정규화 규칙에 대한 컨테이너이고 자체적으로 특성을 포함하지는 않습니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCU</p></td>
<td><p>이 클래스는 단일 회의 서버를 나타냅니다.</p></td>
<td><p>Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUFactories</p></td>
<td><p>이 클래스는 여러 msRTCSIP-MCUFactory 클래스를 포함하며 자체적으로 특성을 포함하지는 않습니다.</p></td>
<td><p>Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCUFactory</p></td>
<td><p>이 클래스는 단일 미디어 유형에 대한 회의 서버 센터를 나타내는 컨테이너입니다. 이 특정 유형 및 공급업체에 대한 첫 번째 회의 서버가 활성화될 경우 이 클래스의 인스턴스가 만들어집니다.</p></td>
<td><p>Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUFactoryService</p></td>
<td><p>이 클래스는 특정 풀에서 해당 회의 서버 센터까지의 연결을 제공합니다.</p></td>
<td><p>Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MediationServer</p></td>
<td><p>이 클래스는 중재 서버의 서비스 제어 지점에 대한 항목을 포함하고 있습니다.</p></td>
<td><p>Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Meeting(사용되지 않음)</p></td>
<td><p>msRTCSIP-GlobalContainer에 대한 이 보조 클래스는 구성 가능한 모임 설정을 나타내는 특성을 포함하고 있습니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Mobility</p></td>
<td><p>전역 모바일 설정을 저장하는 컨테이너입니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MonitoringServer</p></td>
<td><p>이 클래스는 단일 모니터링 서버에 대한 설정을 나타내는 특성을 포함하고 있습니다.</p></td>
<td><p>Communications Server 2007 R2의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PhoneRoute(사용되지 않음)</p></td>
<td><p>이 클래스는 특정 게이트웨이 또는 게이트웨이 집합에 대한 최소 비용 경로의 인스턴스를 나타내는 컨테이너입니다. 모든 엔터프라이즈 풀 또는 Standard Edition을 실행하는 서버는 가장 비용 효과적인 방법으로 발신 전화를 PSTN(공중 전화망)으로 라우팅하기 위해 이 정보를 사용합니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PhoneRoutes(사용되지 않음)</p></td>
<td><p>이 클래스는 여러 최소 비용 경로에 대한 컨테이너이고 자체적으로 특성을 포함하지는 않습니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Policies(사용되지 않음)</p></td>
<td><p>이 클래스는 여러 Lync Server 정책 클래스를 포함하며 자체적으로 특성을 포함하지는 않습니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Pool</p></td>
<td><p>이 클래스는 단일 Lync Server 풀을 나타냅니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Pools</p></td>
<td><p>이 클래스는 여러 Lync Server 풀을 포함하며 자체적으로 특성을 포함하지는 않습니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PoolService</p></td>
<td><p>이 클래스는 풀의 서비스 제어 지점을 나타냅니다. 풀에서 호스팅되는 사용자는 이 클래스의 인스턴스를 가리키는 msRTCSIP-PrimaryHomeServer 특성을 가지고 있습니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Presence</p></td>
<td><p>전역 현재 상태 설정을 저장하는 컨테이너입니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Registrar</p></td>
<td><p>msRTCSIP-GlobalContainer에 대한 이 보조 클래스는 SIP 등록자 서버에서 유지 관리하는 사용자 설정을 나타내는 특성을 포함하고 있습니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-RouteUsage(사용되지 않음)</p></td>
<td><p>이 클래스는 전화 경로 사용의 인스턴스를 나타내는 컨테이너입니다. 전화 경로 사용 클래스는 특성 필드 및 설명 필드로 구성됩니다. 특정 필드는 사용 유형을 정의합니다. 설명 필드를 사용하면 관리자는 전화 경로에서 이 특성의 사용을 설명할 수 있습니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-RouteUsages(사용되지 않음)</p></td>
<td><p>이 클래스는 msRTCSIP-RouteUsage 클래스의 여러 인스턴스를 포함하며 자체적으로 특성을 포함하지는 않습니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Search</p></td>
<td><p>msRTCSIP-GlobalContainer에 대한 이 보조 클래스는 검색 결과의 범위를 제한 및 제어하는 특성을 포함하고 있습니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Server</p></td>
<td><p>이 클래스는 Lync Server를 실행하는 단일 서버를 나타냅니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Service</p></td>
<td><p>이 클래스는 전역 설정 컨테이너 및 msRTCSIP-Domain 개체를 포함하고 있습니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedMCU</p></td>
<td><p>이 클래스는 트러스트된 회의 서버에 대한 설정을 나타내는 특성을 포함하고 있습니다.</p></td>
<td><p>Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedMCUs</p></td>
<td><p>이 클래스는 msRTCSIP-TrustedMCU 클래스의 여러 인스턴스를 포함하며 자체적으로 특성을 포함하지는 않습니다.</p></td>
<td><p>Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedProxies</p></td>
<td><p>이 클래스는 여러 msRTCSIP-TrustedProxy 클래스를 포함하며 자체적으로 특성을 포함하지는 않습니다.</p></td>
<td><p>Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedProxy</p></td>
<td><p>이 클래스는 프록시 서버를 실행하는 서버를 나타내는 컨테이너입니다. AD DS에 가입된 컴퓨터에서 새 프록시 서버를 활성화할 경우 이 클래스의 인스턴스가 만들어집니다.</p></td>
<td><p>Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServer</p></td>
<td><p>이 클래스는 트러스트된 서버에 대한 설정을 나타내는 특성을 포함하고 있습니다.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedService</p></td>
<td><p>이 클래스는 GRUU(Globally Routable User Agent URI) 주소를 사용하여 라우팅할 수 있는 트러스트된 서비스를 나타내는 컨테이너입니다. 이 클래스의 인스턴스는 Lync Server에서 신뢰하는 새 서버가 활성화될 경우 만들어집니다. 이 트러스트된 서버는 Active Directory 도메인에 가입해야 합니다.</p></td>
<td><p>Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServices</p></td>
<td><p>이 클래스는 여러 GRUU 서버에 대한 컨테이너이고 자체적으로 특성을 포함하지는 않습니다.</p></td>
<td><p>Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedWebComponentsServer</p></td>
<td><p>이 클래스는 트러스트된 웹 구성 요소에 대한 설정을 나타내는 특성을 포함하고 있습니다.</p></td>
<td><p>Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedWebComponentsServers</p></td>
<td><p>이 클래스는 msRTCSIP-TrustedWebComponentServer 클래스의 여러 인스턴스를 포함하며 자체적으로 특성을 포함하지는 않습니다.</p></td>
<td><p>Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UnifiedCommunications(사용되지 않음)</p></td>
<td><p>msRTCSIP-GlobalContainer에 대한 이 보조 클래스는 통합 통신과 관련된 특성을 포함하고 있습니다.</p></td>
<td><p>Lync Server 2010에서 사용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-WebComponents</p></td>
<td><p>이 클래스는 IIS(Internet Information Server)의 서비스 제어 지점을 포함하고 있으며 서버를 웹 구성 요소 서버로 식별합니다.</p></td>
<td><p>Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-WebComponentsService</p></td>
<td><p>이 클래스는 특정 풀에서 해당 풀이 사용하는 웹 구성 요소까지의 연결을 제공합니다.</p></td>
<td><p>Communications Server 2007의 새로운 기능</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-WebComponentSettings</p></td>
<td><p>msRTCSIP-WebComponents에 대한 이 보조 클래스는 웹 구성 요소에 대한 설정을 나타내는 특성을 포함하고 있습니다.</p></td>
<td><p>Communications Server 2007의 새로운 기능</p></td>
</tr>
</tbody>
</table>

