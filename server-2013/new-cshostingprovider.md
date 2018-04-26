---
title: New-CsHostingProvider
TOCTitle: New-CsHostingProvider
ms:assetid: 6874cc14-d250-43d4-8868-43cd8d202e9c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398490(v=OCS.15)
ms:contentKeyID: 49303903
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsHostingProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용할 새 호스팅 공급자를 만듭니다. 호스팅 공급자는 페더레이션할 도메인에 대해 메신저, 현재 상태 및 관련 서비스를 제공하는 타사 사설 조직입니다. Microsoft Lync Online 2010과 같은 호스팅 공급자는 일반인에게 서비스를 제공하지 않는다는 점에서 Yahoo\!, MSN 및 AOL과 같은 공용 공급자와 다릅니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsHostingProvider -Enabled <$true | $false> -Identity <XdsGlobalRelativeIdentity> -ProxyFqdn <String> [-AutodiscoverUrl <String>] [-IsLocal <$true | $false>] [-SipClientPort <UInt64>] [-VerificationLevel <AlwaysVerifiable | AlwaysUnverifiable | UseSourceVerification>] <COMMON PARAMETERS>

    New-CsHostingProvider -Enabled <$true | $false> -EnabledSharedAddressSpace <$true | $false> -HostsOCSUsers <$true | $false> -Identity <XdsGlobalRelativeIdentity> -ProxyFqdn <String> [-AutodiscoverUrl <String>] [-IsLocal <$true | $false>] [-SipClientPort <UInt64>] [-VerificationLevel <AlwaysVerifiable | AlwaysUnverifiable | UseSourceVerification>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 Fabrikam.com인 새 호스팅 공급자를 만듭니다. 명령은 ID를 지정할 뿐만 아니라 또 다른 두 필수 매개 변수인 ProxyFqdn(Fabrikam.com에서 사용하는 프록시 서버 지정) 및 Enabled(새 호스팅 공급자를 사용하도록 설정할지 지정)도 포함합니다. 필수 매개 변수를 그대로 두면 **New-CsHostingProvider** cmdlet이 계속하기 전에 값을 입력하라는 메시지를 표시합니다.

    New-CsHostingProvider -Identity Fabrikam.com -ProxyFqdn "proxyserver.fabrikam.com" -Enabled $True

## 예제 2

예제 2는 분할 도메인 시나리오에서 사용할 새 호스팅 공급자를 만드는 방법을 보여 줍니다. 분할 도메인은 일부 Lync Server 계정은 온-프레미스로 유지 관리되고 또 다른 일부 계정은 호스팅 공급자에 의해 유지 관리됨을 의미합니다. 이러한 유형의 호스팅 공급자를 만들려면 세 가지 필수 필드(Identity, ProxyFqdn 및 Enabled)를 포함해야 합니다. 또한 HostsOCSUsers 및 EnabledSharedAddressSpace 매개 변수를 포함하고 모두 True로 설정해야 합니다. Lync Server 이외 서비스(예: Microsoft Exchange)를 호스트하는 분할 도메인 공급자를 만들려면 동일한 두 매개 변수를 포함하되, HostsOCSUsers를 False로 설정합니다.

    New-CsHostingProvider -Identity Fabrikam.com -ProxyFqdn "proxyserver.fabrikam.com" -Enabled $True -HostsOCSUsers $True -EnabledSharedAddressSpace $True

## 자세한 정보

페더레이션은 두 조직에서 두 그룹 간의 통신을 용이하게 하는 트러스트 관계를 설정할 수 있는 수단입니다. 페더레이션이 설정되면 두 조직의 사용자가 서로 메신저 대화를 보내고, 현재 상태 알림에 가입하고, Lync 2013과 같은 SIP 응용 프로그램을 사용하여 통신할 수 있습니다. Lync Server를 사용하면 1) 사용자 조직과 다른 조직 간의 직접 페더레이션, 2) 사용자 조직과 공용 공급자 간의 페더레이션 및 3) 사용자 조직과 타사 호스팅 공급자 간의 페더레이션이라는 세 가지 유형의 페더레이션을 설정할 수 있습니다.

호스팅 공급자는 다른 조직에 SIP 통신 서비스를 제공하는 조직입니다. 예를 들어 Fabrikam, Inc.는 Contoso, Northwind Traders, Wingtip Toys 등의 사용자를 호스트할 수 있습니다. 호스팅 공급자와의 페더레이션 관계를 설정하면 해당 공급자가 호스트하는 조직과 효과적으로 페더레이션을 설정할 수 있습니다. 예를 들어 Fabrikam과 페더레이션한 경우 Contoso, Northwind Traders 및 Wingtip Toys의 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다.

분할 도메인 시나리오에서 호스팅 공급자를 사용할 수도 있습니다. 분할 도메인 시나리오에서 일부 Lync Server 사용자는 온-프레미스에서 호스트되는 계정, 즉 Lync Server의 로컬 구현에서 호스트되는 계정을 가지고 있고, 다른 사용자는 호스팅 공급자가 오프-프레미스에서 유지 관리하는 계정을 가지고 있습니다. 호스팅 공급자와 페더레이션하면 온-프레미스 사용자와 오프-프레미스 사용자가 서로 통신할 수 있습니다.

타사 호스팅 공급자와 페더레이션하려면 새 호스팅 공급자를 만들어서 활성화해야 합니다. 또한 타사 공급자가 사용자와 페더레이션 관계를 설정해야 합니다. **New-CsHostingProvider** cmdlet을 사용하여 세 가지 유형의 호스팅 공급자 관계를 설정할 수 있습니다.

호스팅 공급자와 직접 페더레이션. 이러한 유형의 관계를 만들려면 세 가지 필수 매개 변수 Identity, ProxyFqdn 및 Enabled를 포함해야 합니다.

호스트되는 Lync Server 서비스와 분할된 도메인. 이러한 유형의 관계를 만들려면 세 가지 필수 매개 변수를 포함해야 합니다. 또한 EnabledSharedAddressSpace 및 HostsOCSUsers 속성을 모두 True로 설정해야 합니다.

호스트되는 비 Lync Server 서비스(예: Microsoft Exchange)와 분할된 도메인. 이러한 유형의 관계를 만들려면 세 가지 필수 매개 변수를 포함해야 합니다. 또한 EnabledSharedAddressSpace를 True로 설정하고 HostsOCSUsers를 False로 설정해야 합니다.

새 호스팅 공급자를 만들 때는 해당 공급자의 ID와 프록시 FQDN(정규화된 도메인 이름)이 고유해야 합니다. ID 및/또는 프록시 FQDN을 공유하는 두 호스팅 공급자 또는 호스팅 공급자와 공용 공급자를 가질 수는 없습니다.

에지 서버가 DNS(Domain Name System) 서버 경로 지정이 아닌 기본 경로 지정을 사용하도록 구성된 경우 호스팅 공급자와 페더레이션할 수 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsHostingProvider** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsHostingProvider"}

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
<td><p><em>Enabled</em></p></td>
<td><p>필수</p></td>
<td><p>System.Boolean</p></td>
<td><p>도메인과 호스팅 공급자 간에 네트워크 연결이 사용되는지 여부를 나타냅니다. 이 값이 True로 설정되어야 두 조직 간에 메시지를 교환할 수 있습니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnabledSharedAddressSpace</em></p></td>
<td><p>필수</p></td>
<td><p>System.Boolean</p></td>
<td><p>True인 경우 호스팅 공급자가 분할 도메인 시나리오에서 사용되고 있음을 나타냅니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>HostsOCSUsers</em></p></td>
<td><p>필수</p></td>
<td><p>System.Boolean</p></td>
<td><p>True인 경우 호스팅 공급자가 Lync Server 계정을 호스트하는 데 사용됨을 나타냅니다. False인 경우 공급자가 Microsoft Exchange 계정과 같은 다른 계정 유형을 호스트함을 나타냅니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>만들 호스팅 공급자의 고유한 식별자입니다. Identity는 문자열 값입니다. 예를 들어 호스팅 공급자의 FQDN(예: fabrikam.com)일 수도 있고, 서비스를 제공하는 회사의 이름(예: Fabrikam Hosting, Inc.)일 수도 있습니다.</p>
<p>호스팅 공급자 ID는 고유해야 합니다. 기존 공급자와 동일한 ID를 가진 새 호스팅 공급자를 만들려고 하면 명령이 실패하게 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ProxyFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>호스팅 공급자가 사용하는 프록시 서버의 FQDN입니다. 이 값은 수정할 수 없습니다. 호스팅 공급자가 나중에 프록시 서버를 변경하는 경우 또는 처음에 FQDN을 잘못 지정한 경우 해당 공급자에 대한 항목을 삭제한 다음 다시 만들어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AutodiscoverUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 계정을 호스트하는 호스팅 공급자가 사용하는 자동 검색 서비스의 URL입니다. 자동 검색 서비스는 클라이언트 응용 프로그램에서 사용자의 홈 풀 같은 리소스에 액세스하는 방법을 결정할 수 있도록 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>IsLocal</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True인 경우 호스팅 공급자에서 사용하는 프록시 서버가 사용자의 Lync Server 토폴로지에 포함된다는 의미입니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipClientPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt64</p></td>
<td><p>공급자가 SIP 클라이언트와 통신하는 데 사용되는 포트로, 기본값은 443입니다. <strong>Get-CsHostingProvider</strong> cmdlet을 실행할 때는 기본적으로 SipClientPort가 표시되지 않습니다. SipClientPort를 표시하려면 다음과 같은 명령을 사용합니다.</p>
<p>Get-CsHostingProvider | Select-Object *</p></td>
</tr>
<tr class="even">
<td><p><em>VerificationLevel</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Edge.VerificationLevelType</p></td>
<td><p>호스팅 공급자와 주고받는 메시지의 허용된 확인 수준을 지정합니다. VerificationLevel은 다음 값 중 하나로 설정되어야 합니다.</p>
<p>AlwaysVerifiable. 호스팅 공급자에서 보낸 모든 메시지는 확인할 수 있는 것으로 간주됨을 나타냅니다. 이는 호스팅 공급자에서 보낸 메시지는 거부되지 않음을 의미합니다.</p>
<p>AlwaysUnverifiable. 호스팅 공급자에서 보낸 모든 메시지는 확인할 수 없는 것으로 간주됨을 나타냅니다. 따라서 메시지는 호스팅 공급자의 사용자가 귀하의 대화 상대 목록에 있는 경우에만 통과됩니다.</p>
<p>UseSourceVerification. 호스팅 공급자에서 보낸 메시지에 포함된 확인 수준을 사용합니다. 이 수준이 지정되지 않은 경우 메시지가 확인할 수 없는 것으로 간주되어 거부됩니다.</p>
<p>기본값은 AlwayVerifiable입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsHostingProvider** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayHostingProvider 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Disable-CsHostingProvider](disable-cshostingprovider.md)  
[Enable-CsHostingProvider](enable-cshostingprovider.md)  
[Get-CsHostingProvider](get-cshostingprovider.md)  
[Remove-CsHostingProvider](remove-cshostingprovider.md)  
[Set-CsHostingProvider](set-cshostingprovider.md)

