---
title: Disable-CsHostingProvider
TOCTitle: Disable-CsHostingProvider
ms:assetid: 67d67111-aa04-4241-8f41-e8059fd1649c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398481(v=OCS.15)
ms:contentKeyID: 49303896
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Disable-CsHostingProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용 중인 호스팅 공급자를 비활성화합니다. 호스팅 공급자는 페더레이션하려는 도메인에 메신저, 현재 상태 및 관련 서비스를 제공하는 타사 조직입니다. Microsoft Lync Online 2010과 같은 호스팅 공급자는 일반인에게 서비스를 제공하지 않는다는 점에서 Yahoo\!, MSN 및 AOL과 같은 공용 공급자와 다릅니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Disable-CsHostingProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Disable-CsHostingProvider [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 호스팅 공급자 Fabrikam.com을 비활성화합니다. Fabrikam.com이 이미 비활성화된 경우 이 명령은 오류 메시지를 반환합니다.

    Disable-CsHostingProvider -Identity "Fabrikam.com"

## 예제 2

예제 2에서는 현재 활성화된 모든 호스팅 공급자를 비활성화합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsHostingProvider** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 호스팅 공급자의 컬렉션을 반환합니다. 이 컬렉션은 MarkForMonitoring 속성이 True와 같은 도메인만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 해당 컬렉션의 각 공급자를 비활성화하는 **Disable-CsHostingProvider** cmdlet에 파이프됩니다.

    Get-CsHostingProvider | Where-Object {$_.Enabled -eq $True} | Disable-CsHostingProvider

## 예제 3

예제 3에서는 확인 수준이 AlwaysVerifiable과 같지 않은 활성화된 모든 호스팅 공급자를 비활성화합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsHostingProvider** cmdlet을 사용하여 조직에서 사용하도록 구성된 모든 호스팅 공급자의 컬렉션을 반환합니다. 이 컬렉션은 1) VerificationLevel 속성이 AlwaysVerifiable과 같고, 2) Enabled 속성이 True와 같은 공급자만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 해당 컬렉션의 각 공급자를 비활성화하는 **Disable-CsHostingProvider** cmdlet에 파이프됩니다.

    Get-CsHostingProvider | Where-Object {$_.VerificationLevel -ne "AlwaysVerifiable" -and $_.Enabled -eq $True} | Disable-CsHostingProvider

## 자세한 정보

페더레이션은 두 조직에서 두 그룹 간의 통신을 용이하게 하는 트러스트 관계를 설정할 수 있는 수단입니다. 페더레이션이 설정되면 두 조직의 사용자가 서로 메신저 대화를 보내고, 현재 상태 알림에 가입하고, Lync 2013과 같은 SIP 응용 프로그램을 사용하여 통신할 수 있습니다. Lync Server를 사용하면 1) 사용자 조직과 다른 조직 간의 직접 페더레이션, 2) 사용자 조직과 공용 공급자 간의 페더레이션 및 3) 사용자 조직과 타사 호스팅 공급자 간의 페더레이션이라는 세 가지 유형의 페더레이션을 설정할 수 있습니다.

호스팅 공급자는 다른 조직에 SIP 통신 서비스를 제공하는 조직입니다. 예를 들어 Fabrikam, Inc.는 Contoso, Northwind Traders, Wingtip Toys 등의 사용자를 호스트할 수 있습니다. 호스팅 공급자와의 페더레이션 관계를 설정하면 해당 공급자가 호스트하는 조직과 효과적으로 페더레이션을 설정할 수 있습니다. 예를 들어 Fabrikam과 페더레이션한 경우 Contoso, Northwind Traders 및 Wingtip Toys의 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다.

분할 도메인 시나리오에서 호스팅 공급자를 사용할 수도 있습니다. 분할 도메인 시나리오에서 일부 Lync Server 사용자는 온-프레미스에서 호스트되는 계정, 즉 Lync Server의 로컬 구현에서 호스트되는 계정을 가지고 있고, 다른 사용자는 호스팅 공급자가 오프-프레미스에서 유지 관리하는 계정을 가지고 있습니다. 호스팅 공급자와 페더레이션하면 온-프레미스 사용자와 오프-프레미스 사용자가 서로 통신할 수 있습니다.

타사 호스팅 공급자와 페더레이션하려면 새 호스팅 공급자를 만들어서 활성화해야 합니다. 또한 타사 공급자도 사용자와 페더레이션 관계를 만들어야 합니다. 공급자를 만들 때 호스팅 공급자를 활성화할 수 있습니다. 또는 나중에 **Enable-CsHostingProvider** cmdlet을 사용하여 해당 공급자를 활성화할 수 있습니다. 또한 **Disable-CsHostingProvider** cmdlet을 사용하여 언제든지 관계를 비활성화할 수 있습니다. 그러나 유효한 페더레이션 파트너로 남아 있는 호스팅 공급자를 비활성화하면 공급자가 다시 활성화될 때까지 조직과 공급자 간의 모든 통신 활동이 일시 중지됩니다.

에지 서버가 DNS(Domain Name System) 서버 라우팅이 아닌 기본 라우팅을 사용하도록 구성된 경우 호스팅 공급자와 페더레이션할 수 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Disable-CsHostingProvider** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Disable-CsHostingProvider"}

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
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>비활성화할 호스팅 공급자의 고유한 식별자입니다. Identity는 호스팅 공급자의 FQDN(정규화된 도메인 이름)(예: fabrikam.com)일 수도 있고, 서비스를 제공하는 회사의 이름일 수도 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>호스팅 공급자 표시 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayHostingProvider 개체입니다. **Disable-CsHostingProvider** cmdlet은 호스팅 공급자 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayHostingProvider 개체의 인스턴스를 비활성화합니다.

## 참고 항목

#### 기타 리소스

[Enable-CsHostingProvider](enable-cshostingprovider.md)  
[Get-CsHostingProvider](get-cshostingprovider.md)  
[New-CsHostingProvider](new-cshostingprovider.md)  
[Remove-CsHostingProvider](remove-cshostingprovider.md)  
[Set-CsHostingProvider](set-cshostingprovider.md)

