---
title: Get-CsService
TOCTitle: Get-CsService
ms:assetid: f687d41b-2cb3-4c32-ae28-90e25cdd0d6a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413038(v=OCS.15)
ms:contentKeyID: 49305550
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsService

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 인프라에서 사용 중인 서비스 및 서버 역할에 대한 정보를 반환합니다. 서비스는 Lync Server 풀에 배포된 역할의 인스턴스입니다. 예를 들어 모두 모니터링 서비스를 실행하는 컴퓨터 풀이 있을 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsService [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsService [-ApplicationServer <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-ApplicationDatabase <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-ArchivingServer <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-ArchivingDatabase <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-BackupServer <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-CentralManagement <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-CentralManagementDatabase <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-ConferencingServer <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-Director <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-EdgeServer <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-TrustedApplicationPool <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-FileStore <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-PersistentChatServer <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-PersistentChatComplianceDatabase <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-PersistentChatDatabase <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-LegalInterceptServer <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-ManagementServer <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-MediationServer <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-MonitoringServer <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-MonitoringDatabase <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-PstnGateway <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-Registrar <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-UserServer <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-UserDatabase <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-WacServer <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-WebServer <SwitchParameter>] <COMMON PARAMETERS>

    Get-CsService [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-PoolFqdn <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 현재 실행 중인 모든 Lync Server 서비스 및 서버 역할에 대한 정보를 반환합니다.

    Get-CsService

## 예제 2

예제 2는 응용 프로그램 서비스에 대한 정보만 반환합니다. 적절한 매개 변수를 사용하면 다른 서비스/서버 역할에 대한 정보를 반환할 수 있습니다. 예를 들어 Get-CsService -FileStore 명령은 파일 저장소에 대한 정보를

    Get-CsService -ApplicationServer

## 예제 3

예제 3에서는 atl-cs-001.litwareinc.com 풀에 있는 각 서비스의 ID를 다시 보고합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsService** cmdlet 및 PoolFqdn 매개 변수를 호출하여 atl-cs-001.litwareinc.com 풀에 있는 해당 서비스 및 서버 역할만 반환합니다. 이 컬렉션은 컬렉션의 각 항목 ID를 다시 보고하는 **Select-Object** cmdlet에 파이프됩니다.

    Get-CsService -PoolFqdn "atl-cs-001.litwareinc.com" | Select-Object Identity

## 예제 4

예제 4에서는 Redmond 사이트에 있는 모든 서비스/서버 역할에 대해 정보가 반환됩니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsService** cmdlet을 호출하여 조직에서 현재 사용 중인 모든 서비스 및 서버 역할의 컬렉션을 반환합니다. 이 데이터는 SiteID 속성이 site:Redmond와 같은 항목만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsService | Where-Object {$_.SiteID -eq "site:Redmond"}

## 예제 5

예제 5에 표시된 명령은 등록자를 종속 서비스로 표시하는 모든 서비스에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 **Get-CsService** cmdlet을 호출하여 현재 사용 중인 모든 서비스 및 서버 역할의 컬렉션을 반환합니다. 이 컬렉션은 DependentServiceList 속성에 "Registrar"라는 문자열 값이 포함된 각 항목을 선택하는 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet 조건은 -like 연산자와 와일드카드 값 "\*Registrar\*"를 사용하여 지정합니다.

    Get-CsService | Where-Object {$_.DependentServiceList -like "*Registrar*"}

## 자세한 정보

Lync Server의 기능은 일반적으로 서비스 또는 서버 역할로 표시됩니다. 예를 들어 조직에서 발생하는 모든 메신저 대화 세션의 대화 내용을 자동으로 저장하도록 Lync Server를 구성할 수 있습니다. 이렇게 구성하려면 보관 서버 서버 역할을 설치해야 합니다. 서비스 및 서버 역할은 Lync Server를 설치할 때 함께 구성하거나 소프트웨어를 실행한 후에 구성할 수 있습니다.

**Get-CsService** cmdlet을 사용하면 조직에서 실행 중인 서버 역할 및 서비스에 대한 정보를 반환할 수 있습니다. **Get-CsService** cmdlet을 추가 매개 변수 없이 호출하면 모든 서비스 및 서버 역할에 대한 세부 정보가 반환됩니다. 또는 -PoolFqdn 매개 변수를 사용하여 반환되는 데이터를 지정된 풀로 제한할 수 있습니다. 그리고 스위치 매개 변수를 원하는 만큼 사용하여 반환되는 데이터를 특정 유형의 서비스로 제한할 수 있습니다. 참고로, 스위치 매개 변수는 매개 변수 값이 필요 없는 매개 변수입니다. 예를 들어 Get-CsService -ArchivingServer 명령은 모든 보관 서버에 대한

Get-CsService –ArchivingServer

이러한 스위치 매개 변수는 각 명령에 하나만 사용할 수 있습니다. 보관 서버와 모니터링 서버 모두에 대한 정보를 반환하도록 하는

Get-CsService –ArchivingServer –MonitoringServer

여러 서버 역할에 대한 정보를 반환해야 하는 경우 **Get-CsService** cmdlet을 사용하여 서비스 데이터의 전체 컬렉션을 반환한 다음 해당 데이터를 **Where-Object** cmdlet에 파이프할 수 있습니다.

Get-CsService | Where-Object {$\_.Role –eq "ArchivingServer" –or $\_.Role –eq "MonitoringServer"}

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsService** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsService"}

## 매개 변수


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>매개 변수</th>
<th>필수</th>
<th>유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>ApplicationDatabase</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 응용 프로그램 데이터베이스에 대한 정보를 반환합니다. 응용 프로그램 데이터베이스는 응용 프로그램 서비스에서 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ApplicationServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>응용 프로그램 서비스에 대한 정보를 반환합니다. 응용 프로그램 서비스를 사용하여 Microsoft Unified Communications Managed API(UCMA)로 만들어진 응용 프로그램을 실행할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ArchivingDatabase</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 보관 데이터베이스에 대한 정보를 반환합니다. 보관 데이터베이스는 인스턴트 메시지 세션의 대화 내용을 저장합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ArchivingServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 보관 서버에 대한 정보를 반환합니다. 보관 서버를 사용하면 인스턴트 메시지 세션의 대화 내용을 저장할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>BackupServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 백업 서버에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CentralManagement</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 중앙 관리 서비스에 대한 정보를 반환합니다. 중앙 관리 서비스는 Lync Server 서비스를 실행 중인 컴퓨터에 구성 데이터를 전송하는 데 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>CentralManagementDatabase</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 중앙 관리 저장소에 대한 정보를 반환합니다. 중앙 관리 저장소는 Lync Server에 대한 구성 정보를 유지 관리합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ConferencingServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 A/V 회의 서비스에 대한 정보를 반환합니다. A/V 회의 서비스는 모임 및 전화 회의를 수행하는 데 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Director</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 디렉터에 대한 정보를 반환합니다. 디렉터는 사용자 요청 및 사용자 인증을 처리할 권한이 있지만 사용자 계정을 포함할 수는 없습니다. 디렉터는 일반적으로 외부 사용자의 요청을 처리하는 데 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EdgeServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 에지 서버에 대한 정보를 반환합니다. 에지 서버는 내부 네트워크와 인터넷 사이의 연결을 제공합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>FileStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 파일 저장소에 대한 정보를 반환합니다. 파일 저장소는 알림 서비스에서 사용하는 오디오 파일 등의 Lync Server 파일을 유지 관리하는 데 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>와일드카드를 사용하여 반환할 서비스를 하나 이상 지정하는 데 사용됩니다. Identity 매개 변수와 Filter 매개 변수를 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>반환할 특정 서비스 또는 서버 역할의 고유 식별자입니다(예: -Identity &quot;Registrar:atl-cs-001.litwareinc.com&quot;).</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>LegalInterceptServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 합법적 가로채기 서버에 대한 정보를 반환합니다. 합법적 가로채기 서버는 Office 365에서 메신저 메시지 통신의 실시간 가로채기 기능을 제공합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ManagementServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 중앙 관리 서버에 대한 정보를 반환합니다. 중앙 관리 서버는 일반적으로 프런트 엔드 서버와 함께 배치되며 중앙 관리 저장소의 정보 액세스를 담당합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MediationServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 중재 서버에 대한 정보를 반환합니다. 중재 서버는 Enterprise Voice 네트워크와 PSTN(공중 전화망) 사이에 브리지를 제공하도록 도와 줍니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MonitoringDatabase</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 모니터링 데이터베이스에 대한 정보를 반환합니다. 모니터링 데이터베이스는 Enterprise Voice 전화 사용량과 통화 품질 정보를 저장합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MonitoringServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 모니터링 서버에 대한 정보를 반환합니다. 모니터링 서버는 Enterprise Voice 전화 사용량과 통화 품질을 추적하는 데 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PersistentChatComplianceDatabase</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>영구 채팅 준수 정보 유지 관리에 사용되는 데이터베이스에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PersistentChatDatabase</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>영구 채팅 정보 유지 관리에 사용되는 데이터베이스에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PersistentChatServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 영구 채팅 서버에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PoolFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>서비스 또는 서버 역할을 호스트하는 풀의 FQDN(정규화된 도메인 이름)입니다. 서비스 관련 매개 변수를 지정하지 않고 PoolFqdn 매개 변수를 사용하면 해당 풀에 있는 모든 서비스 또는 서버 역할이 반환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PstnGateway</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 PSTN(공중 전화망) 게이트웨이에 대한 정보를 반환합니다. PSTN 게이트웨이는 Enterprise Voice 장치의 신호를 PSTN 장치가 인식할 수 있는 신호로 변환하고, PSTN 장치의 신호를 Enterprise Voice 장치가 인식할 수 있는 신호로 변환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Registrar</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 등록자에 대한 정보를 반환합니다. 등록자는 사용자를 인증하고 사용자의 현재 상태를 추적하는 데 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TrustedApplicationPool</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 신뢰할 수 있는 응용 프로그램 풀에 대한 정보를 반환합니다. 신뢰할 수 있는 응용 프로그램 풀은 신뢰할 수 있는 응용 프로그램을 실행하는 컴퓨터를 호스트합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserDatabase</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 사용자 데이터베이스에 대한 정보를 반환합니다. 사용자 데이터베이스는 사용자 서버 서비스에 필요한 데이터를 저장합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 사용자 서비스 서비스에 대한 정보를 반환합니다. 사용자 서비스 서비스는 사용자 복제, 인밴드 프로비전, 현재 상태 정보 게시 및 알림, 대화 상대 카드 교환 등의 기능을 제공합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WacServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Microsoft Lync Server에서 사용하는 Office Online 서버에 대한 정보를 반환합니다. Office Online 서버의 이전 명칭은 &quot;WacServer&quot;였습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WebServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>조직에서 사용되는 웹 서비스 서비스에 대한 정보를 반환합니다. 웹 서비스 서비스는 주소록 서비스와 같은 웹 기반 응용 프로그램을 호스트합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsService** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsService** cmdlet은 cmdlet을 호출할 때 사용되는 매개 변수에 따라 다른 개체를 반환합니다. 예를 들어 MonitoringDatabase 매개 변수를 포함하면 **Get-CsService** cmdlet은 Microsoft.Rtc.Management.Xds.DisplayMonitoringDatabase 개체의 인스턴스를 반환합니다. 다른 매개 변수를 사용할 경우 반환되는 개체를 확인하려면 다음 매개 변수 중 하나를 사용하여 **Get-CsService** cmdlet을 호출한 다음 반환되는 개체를 **Get-Member** cmdlet에 파이프합니다(예: Get-CsService -Registrar | Get-Member).

## 참고 항목

#### 기타 리소스

[Set-CsApplicationServer](set-csapplicationserver.md)  
[Set-CsArchivingServer](set-csarchivingserver.md)  
[Set-CsConferenceServer](set-csconferenceserver.md)  
[Set-CsDirector](set-csdirector.md)  
[Set-CsEdgeServer](set-csedgeserver.md)  
[Set-CsManagementServer](set-csmanagementserver.md)  
[Set-CsMediationServer](set-csmediationserver.md)  
[Set-CsMonitoringServer](set-csmonitoringserver.md)  
[Set-CsRegistrar](set-csregistrar.md)  
[Set-CsUserServer](set-csuserserver.md)  
[Set-CsWebServer](set-cswebserver.md)

