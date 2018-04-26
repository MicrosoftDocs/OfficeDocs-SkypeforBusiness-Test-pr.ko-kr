---
title: Set-CsAccessEdgeConfiguration
TOCTitle: Set-CsAccessEdgeConfiguration
ms:assetid: f3108b59-1ab2-4288-a470-57d741e7e569
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413017(v=OCS.15)
ms:contentKeyID: 49305510
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsAccessEdgeConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

액세스 에지 서비스를 실행 중인 컴퓨터의 기존 액세스 에지 구성 설정 컬렉션 속성 값을 수정합니다. 이러한 컴퓨터에서 실행 중인 액세스 에지 서비스(에지 서버라고도 함)는 내부 네트워크 외부의 사용자가 내부 네트워크 내부의 사용자와 통신할 수 있는 방법을 제공합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsAccessEdgeConfiguration [-AllowAnonymousUsers <$true | $false>] [-AllowFederatedUsers <$true | $false>] [-AllowOutsideUsers <$true | $false>] [-CertificatesDeletedPercentage <UInt32>] [-DiscoveredPartnerReportPeriodMinutes <UInt32>] [-DiscoveredPartnerStandardRate <UInt32>] [-EnableArchivingDisclaimer <$true | $false>] [-EnableDiscoveredPartnerContactsLimit <$true | $false>] [-EnableUserReplicator <$true | $false>] [-Identity <XdsIdentity>] [-KeepCrlsUpToDateForPeers <$true | $false>] [-MarkSourceVerifiableOnOutgoingMessages <$true | $false>] [-MaxAcceptedCertificatesStored <UInt32>] [-MaxContactsPerDiscoveredPartner <UInt32>] [-MaxRejectedCertificatesStored <UInt32>] [-OutgoingTlsCountForFederatedPartners <UInt32>] <COMMON PARAMETERS>

    Set-CsAccessEdgeConfiguration [-AllowAnonymousUsers <$true | $false>] [-AllowFederatedUsers <$true | $false>] [-AllowOutsideUsers <$true | $false>] [-CertificatesDeletedPercentage <UInt32>] [-DefaultRouteFqdn <String>] [-DiscoveredPartnerReportPeriodMinutes <UInt32>] [-DiscoveredPartnerStandardRate <UInt32>] [-EnableArchivingDisclaimer <$true | $false>] [-EnableDiscoveredPartnerContactsLimit <$true | $false>] [-EnableUserReplicator <$true | $false>] [-IsPublicProvider <$true | $false>] [-KeepCrlsUpToDateForPeers <$true | $false>] [-MarkSourceVerifiableOnOutgoingMessages <$true | $false>] [-MaxAcceptedCertificatesStored <UInt32>] [-MaxContactsPerDiscoveredPartner <UInt32>] [-MaxRejectedCertificatesStored <UInt32>] [-OutgoingTlsCountForFederatedPartners <UInt32>] [-UseDefaultRouting <SwitchParameter>] [-VerificationLevel <AlwaysVerifiable | AlwaysUnverifiable | UseSourceVerification>] <COMMON PARAMETERS>

    Set-CsAccessEdgeConfiguration [-AllowAnonymousUsers <$true | $false>] [-AllowFederatedUsers <$true | $false>] [-AllowOutsideUsers <$true | $false>] [-BeClearingHouse <$true | $false>] [-CertificatesDeletedPercentage <UInt32>] [-DiscoveredPartnerReportPeriodMinutes <UInt32>] [-DiscoveredPartnerStandardRate <UInt32>] [-DiscoveredPartnerVerificationLevel <AlwaysVerifiable | AlwaysUnverifiable | UseSourceVerification>] [-EnableArchivingDisclaimer <$true | $false>] [-EnableDiscoveredPartnerContactsLimit <$true | $false>] [-EnablePartnerDiscovery <$true | $false>] [-EnableUserReplicator <$true | $false>] [-KeepCrlsUpToDateForPeers <$true | $false>] [-MarkSourceVerifiableOnOutgoingMessages <$true | $false>] [-MaxAcceptedCertificatesStored <UInt32>] [-MaxContactsPerDiscoveredPartner <UInt32>] [-MaxRejectedCertificatesStored <UInt32>] [-OutgoingTlsCountForFederatedPartners <UInt32>] [-UseDnsSrvRouting <SwitchParameter>] <COMMON PARAMETERS>

    Set-CsAccessEdgeConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 액세스 에지 구성 설정의 두 속성을 수정합니다. 즉, AllowAnonymousUsers 속성은 True로 설정하고 VerificationLevel 속성은 UseSourceVerification으로 설정합니다.

    Set-CsAccessEdgeConfiguration -AllowAnonymousUsers $True -VerificationLevel "UseSourceVerification"

## 예제 2

예제 2에 표시된 명령은 에지 서버의 경로 지정 방법을 기본 경로 지정으로 변경합니다. 이 작업을 수행하기 위해 이 명령은 UseDefaultRouting 매개 변수 및 DefaultRouteFqdn 매개 변수와 에지 서버의 정규화된 도메인 이름을 지정하는 매개 변수 값을 포함해야 합니다.

    Set-CsAccessEdgeConfiguration -UseDefaultRouting -DefaultRouteFqdn "atl-edge-001.litwareinc.com"

## 예제 3

예제 3에서는 에지 서버의 경로 지정 방법을 DNS 서버 경로 지정으로 변경합니다. 이렇게 하려면 UseDnsSrvRouting(매개 변수 값 사용 안 함) 및 EnablePartnerDiscovery(매개 변수 값 $True 사용)의 두 매개 변수를 사용해야 합니다.

    Set-CsAccessEdgeConfiguration -UseDnsSrvRouting -EnablePartnerDiscovery $True

## 자세한 정보

에지 서버(액세스 프록시 서버라고도 함)는 Lync Server의 기능을 내부 네트워크에 로그온하지 않은 사용자에게 확장하는 방법을 제공합니다. 예를 들어 원격 사용자(내부 네트워크가 아니라 인터넷을 통해 Lync Server에 로그온하는 인증된 사용자)가 있으면 이러한 사용자에게 액세스 권한을 제공할 수 있도록 에지 서버를 설정해야 합니다. 마찬가지로 다른 조직과 페더레이션을 설정하거나 사용자에게 공용 메신저 서비스(예: Yahoo\!, AOL 또는 MSN) 계정이 있는 사용자와 통신할 수 있는 권한을 제공하려면 에지 서버가 필요합니다. 액세스 에지 서버는 경계 네트워크에 있으며, 내부 네트워크 내부의 사용자와 외부의 사용자 간에 SIP 연결을 만들고 유효성을 검사하는 데 사용됩니다.

Lync Server에서 액세스 에지 서버는 구성 설정의 전역 컬렉션 하나를 사용하여 관리합니다. **Set-CsAccessEdgeConfiguration** cmdlet을 사용하면 이러한 전역 설정을 수정할 수 있습니다. 에지 서버에 대해 선택한 경로 지정 유형에 따라 수정할 수 있는 속성이 달라집니다. 예를 들어 DNS(Domain Name System) 서비스 경로 지정을 사용하도록 선택하면 속성 값 BeClearinghouse 및 EnablePartnerDiscovery가 표시되고 이를 변경할 수 있습니다. 기본 경로 지정을 사용하면 이 두 속성 값을 사용할 수 없게 됩니다. 대신 속성 값 VerificationLevel 및 IsPublicProvider가 표시되고 이를 변경할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsAccessEdgeConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsAccessEdgeConfiguration"}

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
<td><p><em>AllowAnonymousUsers</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>익명 사용자(즉, 인증되지 않은 사용자)가 방화벽을 통과하도록 허용하여 모임 및 전화 회의에 참가할 수 있도록 할지 여부를 나타냅니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowFederatedUsers</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>내부 사용자가 페더레이션 도메인의 사용자와 통신할 수 있는지 여부를 나타냅니다. 이 속성은 내부 사용자가 분할 도메인 시나리오의 사용자와 통신할 수 있는지 여부도 결정합니다. 분할 도메인에서는 일부 사용자만 온-프레미스에서 호스트하는 계정을 갖고, 다른 사용자는 오프-프레미스에서 호스트하는 계정을 갖습니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowOutsideUsers</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>사용자가 인터넷을 통해 Lync Server에 액세스할 수 있는지 여부를 나타냅니다. 여기에는 시스템에 로그온하려는 익명 사용자와 원격 사용자가 모두 포함됩니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>BeClearingHouse</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>에지 서버가 다른 조직과 직접 연결되어 있는지 여부를 나타냅니다. 기본값은 False입니다. Microsoft 지원 담당자가 지시하지 않은 경우 이 매개 변수를 변경하지 않는 것이 좋습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>CertificatesDeletedPercentage</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>기본값은 20입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DefaultRouteFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>페더레이션 요청에 사용되는 서버의 FQDN(정규화된 도메인 이름)입니다. 기본 경로 지정을 사용하는 경우 이 매개 변수가 필요합니다.</p>
<p>호스팅 공급자와 공용 공급자를 모두 삭제해야 새 기본 경로를 할당할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DiscoveredPartnerReportPeriodMinutes</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>기본값은 60입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DiscoveredPartnerStandardRate</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>기본값은 20입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DiscoveredPartnerVerificationLevel</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Edge.VerificationLevelType</p></td>
<td><p>검색된 파트너와 주고 받는 메시지에 대한 확인 수준을 설정합니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* AlwaysVerifiable</p>
<p>* AlwaysUnverifiable</p>
<p>* UseSourceVerification</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableArchivingDisclaimer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 에지 서버에서 페더레이션 파트너 및 클리어링 하우스 파트너로 보관 알림 헤더를 보냅니다. 페더레이션 또는 클리어링 하우스 사용자의 대화 창에 이 알림(사람들에게 메신저 대화가 보관될 수 있음을 알리는 메시지)이 표시될 수 있습니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableDiscoveredPartnerContactsLimit</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>기본값은 True($True)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnablePartnerDiscovery</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync Server에서 DNS 기록을 사용하여 AllowedDomains 목록에 나열되지 않은 파트너 도메인을 검색합니다. False로 설정하면 Lync Server에서 AllowedDomains 목록에 있는 도메인과만 페더레이션합니다. DNS 서비스 경로 지정을 사용하는 경우 이 매개 변수가 필요합니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableUserReplicator</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>기본값은 False($False)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 액세스 에지 구성 설정의 고유 식별자입니다. 이러한 설정의 전역 인스턴스는 하나만 사용할 수 있으므로 <strong>Set-CsAccessEdgeConfiguration</strong> cmdlet을 호출할 때 ID를 포함하지 않아도 됩니다. 그러나 원하는 경우 -Identity global 구문을 사용하여 전역 설정을 수정할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>액세스 에지 설정 DNS SRV 경로 지정 표시 개체 또는 액세스 에지 설정 기본 경로 표시 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>IsPublicProvider</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>기본 경로 지정에 공용 메신저 라이선스가 필요한 경우 True로 설정해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>KeepCrlsUpToDateForPeers</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>에지 서버에서 페더레이션 도메인 인증서에 대한 CRL(인증서 해지 목록)을 정기적으로 검사할지 여부를 결정합니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MarkSourceVerifiableOnOutgoingMessages</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 보내는 메시지가 확인 가능으로 표시됩니다. 그러면 페더레이션 도메인에서 각 메시지의 확인 수준을 결정할 수 있습니다. False로 설정하면 보내는 메시지가 모두 확인 불가능으로 표시됩니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxAcceptedCertificatesStored</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>에지 서버에서 캐시하는 최대 허용 인증서 수입니다. 기본값은 1000입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxContactsPerDiscoveredPartner</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>검색된 파트너당 허용되는 최대 연락처 수입니다. 기본값은 1000입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxRejectedCertificatesStored</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>에지 서버에서 캐시하는 최대 거부 인증서 수입니다. 기본값은 500입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OutgoingTlsCountForFederatedPartners</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>각 페더레이션 파트너에 사용할 수 있는 최대 TLS(전송 계층 보안) 연결 수를 지정합니다. 최소 TLS 연결 수는 1이고, 최대 수는 4입니다. 기본적으로 OutgoingTlsCountForFederatedPartners는 4로 설정됩니다. Microsoft 지원 담당자가 지시하지 않은 경우 이 매개 변수를 변경하지 않는 것이 좋습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UseDefaultRouting</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>관리자가 페더레이션 요청을 보내고 받는 데 사용되는 서버의 정규화된 도메인 이름을 지정해야 함을 나타냅니다. UseDefaultRouting 매개 변수를 포함하는 경우 DefaultRouteFqdn 매개 변수도 포함해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UseDnsSrvRouting</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>페더레이션 요청을 보내고 받을 때 에지 서버가 DNS SRV 기록을 사용하도록 나타냅니다. 이것이 기본 경로 지정 방법입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>VerificationLevel</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Edge.VerificationLevelType</p></td>
<td><p>기본 경로 지정을 사용하는 경우 VerificationLevel 속성을 사용하여 들어오는 메시지의 확인 수준을 모니터링 및 평가합니다. 사용할 수 있는 값은 다음과 같습니다.</p>
<p>AlwaysVerifiable: 기본 경로에서 받은 모든 요청이 확인됨으로 표시됩니다. 확인 헤더가 없는 경우 메시지에 자동으로 확인 헤더가 추가됩니다.</p>
<p>AlwaysUnverifiable: 받는 사람(메시지를 받을 사용자)이 메시지를 보낸 사용자에 대해 ACE(액세스 제어 항목) 허용으로 구성된 경우에만 메시지가 전달됩니다.</p>
<p>UseSourceVerification: 메시지 확인은 메시지에 포함된 확인 수준을 기반으로 합니다. 확인 헤더가 없는 경우 메시지가 확인되지 않음으로 표시됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Set-CsAccessEdgeConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Set-CsAccessEdgeConfiguration** cmdlet은 개체나 값을 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Get-CsAccessEdgeConfiguration](get-csaccessedgeconfiguration.md)

