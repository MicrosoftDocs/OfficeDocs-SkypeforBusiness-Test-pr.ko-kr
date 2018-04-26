---
title: Set-CsHostingProvider
TOCTitle: Set-CsHostingProvider
ms:assetid: 709567e3-1af6-4829-b9ce-5f488f9db372
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398532(v=OCS.15)
ms:contentKeyID: 49303995
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsHostingProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

현재 조직에서 사용 중인 호스팅 공급자를 수정합니다. 호스팅 공급자는 페더레이션하려는 도메인에 메신저, 현재 상태 및 관련 서비스를 제공하는 타사 조직입니다. Microsoft Lync Online 2010과 같은 호스팅 공급자는 일반인에게 서비스를 제공하지 않는다는 점에서 Yahoo\!, MSN 및 AOL과 같은 공용 공급자와 다릅니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsHostingProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsHostingProvider [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AutodiscoverUrl <String>] [-Confirm [<SwitchParameter>]] [-Enabled <$true | $false>] [-EnabledSharedAddressSpace <$true | $false>] [-Force <SwitchParameter>] [-HostsOCSUsers <$true | $false>] [-IsLocal <$true | $false>] [-SipClientPort <UInt64>] [-VerificationLevel <AlwaysVerifiable | AlwaysUnverifiable | UseSourceVerification>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 Fabrikam.com인 호스팅 공급자를 수정합니다. 이 예제에서 VerificationLevel 속성은 AlwaysUnverifiable로 설정됩니다.

    Set-CsHostingProvider -Identity "Fabrikam.com" -VerificationLevel "AlwaysUnverifiable"

## 예제 2

예제 2는 예제 1에 나온 명령의 변형입니다. 여기서는 모든 호스팅 공급자에 대한 확인 수준이 AlwaysUnverifiable로 설정됩니다. 이 작업을 수행하기 위해 먼저 **Get-CsHostingProvider**를 사용하여 조직에서 사용하도록 구성된 모든 호스팅 공급자의 컬렉션을 반환합니다. 그러면 이 컬렉션은 컬렉션의 각 공급자에 대한 VerificationLevel 속성을 수정하는 **Set-CsHostingProvider**에 파이프됩니다.

    Get-CsHostingProvider | Set-CsHostingProvider -VerificationLevel "AlwaysUnverifiable"

## 예제 3

예제 3에서는 현재 분할 도메인 설정에서 사용하도록 구성된 모든 호스팅 공급자가 더 이상 분할 도메인 페더레이션에 사용되지 않도록 수정됩니다. 이 예제에서는 먼저 **Get-CsHostingProvider**를 호출하여 사용 가능한 모든 호스팅 공급자의 컬렉션을 반환합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. 여기서 1) HostsOCSUsers 속성이 True와 같고 2) EnabledSharedAddressSpace 속성이 True와 같은 공급자만 선택됩니다. 이 필터링된 컬렉션은 EnabledSharedAddressSpace 및 HostsOCSUsers 속성을 모두 False로 설정하는 **Set-CsHostingProvider**에 파이프됩니다. 이 작업이 수행되면 컬렉션의 모든 호스팅 공급자는 여전히 페더레이션에 사용되지만 분할 도메인 시나리오에서는 더 이상 사용되지 않습니다.

    Get-CsHostingProvider | Where-Object {$_.EnabledSharedAddressSpace -eq $True -and $_.HostsOCSUsers -eq $True} | Set-CsHostingProvider -EnabledSharedAddressSpace $False -HostsOCSUsers $False

## 자세한 정보

페더레이션은 두 조직에서 두 그룹 간의 통신을 용이하게 하는 트러스트 관계를 설정할 수 있는 수단입니다. 페더레이션이 설정되면 두 조직의 사용자가 서로 메신저 대화를 보내고, 현재 상태 알림에 가입하고, Microsoft Lync 2013와 같은 SIP 응용 프로그램을 사용하여 통신할 수 있습니다. Lync Server를 사용하면 1) 사용자 조직과 다른 조직 간의 직접 페더레이션, 2) 사용자 조직과 공용 공급자 간의 페더레이션 및 3) 사용자 조직과 타사 호스팅 공급자 간의 페더레이션이라는 세 가지 유형의 페더레이션을 설정할 수 있습니다.

호스팅 공급자는 다른 조직에 SIP 통신 서비스를 제공하는 조직입니다. 예를 들어 Fabrikam, Inc.는 Contoso, Northwind Traders, Wingtip Toys 등의 사용자를 호스트할 수 있습니다. 호스팅 공급자와의 페더레이션 관계를 설정하면 해당 공급자가 호스트하는 조직과 효과적으로 페더레이션을 설정할 수 있습니다. 예를 들어 Fabrikam과 페더레이션한 경우 Contoso, Northwind Traders 및 Wingtip Toys의 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다.

분할 도메인 시나리오에서 호스팅 공급자를 사용할 수도 있습니다. 분할 도메인 시나리오에서 일부 Lync Server 사용자는 온-프레미스에서 호스트되는 계정, 즉 Lync Server의 로컬 구현에서 호스팅되는 계정을 가지고 있고, 다른 사용자는 호스팅 공급자가 오프-프레미스에서 유지 관리하는 계정을 가지고 있습니다. 호스팅 공급자와 페더레이션하면 온-프레미스 사용자와 오프-프레미스 사용자가 서로 통신할 수 있습니다.

타사 호스팅 공급자와 페더레이션하려면 새 호스팅 공급자를 만들어서 활성화해야 합니다. 또한 타사 공급자가 사용자와 페더레이션 관계를 설정해야 합니다. 호스팅 공급자가 만들어진 후 **Set-CsHostingProvider** cmdlet을 사용하여 공급자의 속성을 수정할 수 있습니다. 예를 들어 이 cmdlet을 사용하여 공급자 프록시 서버의 FQDN(정규화된 도메인 이름)을 변경하거나 cmdlet을 사용하여 해당 공급자에 대한 확인 수준을 변경할 수 있습니다.

에지 서버가 DNS(Domain Name System) 서버 라우팅이 아닌 기본 라우팅을 사용하도록 구성된 경우 호스팅 공급자와 페더레이션할 수 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsHostingProvider** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsHostingProvider"}

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
<td><p><em>AutodiscoverUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 계정을 호스트하는 호스팅 공급자가 사용하는 자동 검색 서비스의 URL입니다. 자동 검색 서비스는 Microsoft Lync Mobile 등의 클라이언트 응용 프로그램에서 사용자의 홈 풀 같은 리소스에 액세스하는 방법을 결정할 수 있도록 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>도메인과 호스팅 공급자 간에 네트워크 연결이 사용되는지 여부를 나타냅니다. 이 값이 True로 설정되어야 두 조직 간에 메시지를 교환할 수 있습니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnabledSharedAddressSpace</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True인 경우 호스팅 공급자가 분할 도메인 시나리오에서 사용되고 있음을 나타냅니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>HostsOCSUsers</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True인 경우 호스팅 공급자가 Lync Server 계정을 호스트하는 데 사용됨을 나타냅니다. False인 경우 공급자가 Microsoft Exchange Server 계정과 같은 다른 계정 유형을 호스트함을 나타냅니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>수정할 호스팅 공급자의 고유 식별자입니다. Identity는 호스팅 공급자의 FQDN(예: fabrikam.com)일 수도 있고, 서비스를 제공하는 회사의 이름(Fabrikam, Inc.)일 수도 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>호스팅 공급자 표시 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>IsLocal</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True인 경우 호스팅 공급자에서 사용하는 프록시 서버가 귀하의 자체 Lync Server 토폴로지에 포함됨을 나타냅니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SipClientPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt64</p></td>
<td><p>공급자가 SIP 클라이언트와 통신하는 데 사용되는 포트로, 기본값은 443입니다. Get-CsHostingProvider cmdlet을 실행할 때는 기본적으로 SipClientPort가 표시되지 않습니다. SipClientPort를 표시하려면 다음과 같은 명령을 사용합니다.</p>
<p>Get-CsHostingProvider | Select-Object *</p></td>
</tr>
<tr class="odd">
<td><p><em>VerificationLevel</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Edge.VerificationLevelType</p></td>
<td><p>호스팅 공급자와 주고받는 메시지의 허용된 확인 수준을 지정합니다. VerificationLevel은 다음 값 중 하나로 설정되어야 합니다.</p>
<p>AlwaysVerifiable. 호스팅 공급자에서 보낸 모든 메시지는 확인할 수 있는 것으로 간주됨을 나타냅니다. 이는 호스팅 공급자에서 보낸 메시지는 거부되지 않음을 의미합니다.</p>
<p>AlwaysUnverifiable. 호스팅 공급자에서 보낸 모든 메시지는 확인할 수 없는 것으로 간주됨을 나타냅니다. 따라서 메시지는 호스팅 공급자의 사용자가 귀하의 대화 상대 목록에 있는 경우에만 통과됩니다.</p>
<p>UseSourceVerification. 호스팅 공급자에서 보낸 메시지에 포함된 확인 수준을 사용합니다. 이 수준이 지정되지 않은 경우 메시지가 확인할 수 없는 것으로 간주되어 거부됩니다.</p>
<p>기본값은 AlwaysVerifiable입니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayHostingProvider 개체입니다. **Set-CsHostingProvider**는 호스팅 공급자 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsHostingProvider**는 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayHostingProvider 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Disable-CsHostingProvider](disable-cshostingprovider.md)  
[Enable-CsHostingProvider](enable-cshostingprovider.md)  
[Get-CsHostingProvider](get-cshostingprovider.md)  
[New-CsHostingProvider](new-cshostingprovider.md)  
[Remove-CsHostingProvider](remove-cshostingprovider.md)

