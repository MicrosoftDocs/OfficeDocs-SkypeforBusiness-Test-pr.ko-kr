---
title: Remove-CsHostingProvider
TOCTitle: Remove-CsHostingProvider
ms:assetid: 309e472b-683c-47ed-9536-3b7aa50119d2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425809(v=OCS.15)
ms:contentKeyID: 49303214
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsHostingProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용 중인 하나 이상의 호스팅 공급자를 제거합니다. 호스팅 공급자는 페더레이션하려는 도메인에 메신저 대화, 현재 상태 및 관련 서비스를 제공하는 타사 조직입니다. Microsoft Lync Online 2010과 같은 호스팅 공급자는 일반인에게 서비스를 제공하지 않는다는 점에서 Yahoo\!, MSN 및 AOL과 같은 공용 공급자와 다릅니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsHostingProvider -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 Fabrikam.com인 호스팅 공급자를 삭제합니다. 호스팅 공급자가 삭제되면 Fabrikam.com 및 Fabrikam.com과 관련된 모든 도메인과의 페더레이션이 종료됩니다.

    Remove-CsHostingProvider -Identity "Fabrikam.com"

## 예제 2

예제 2는 조직에서 사용하도록 구성된 모든 호스팅 공급자를 삭제합니다. 이를 수행하기 위해 이 명령은 먼저 **Get-CsHostingProvider** cmdlet을 사용하여 현재 사용 중인 모든 호스팅 공급자의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsHostingProvider** cmdlet에 파이프됩니다. 이 명령이 완료되면 사용하도록 구성된 호스팅 공급자가 더 이상 없게 됩니다.

    Get-CsHostingProvider | Remove-CsHostingProvider

## 예제 3

예제 3에서는 공급자 ID에 문자열 값 "Fabrikam"이 포함된 모든 호스팅 공급자를 삭제합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsHostingProvider** cmdlet 및 Filter 매개 변수를 호출합니다. 필터 값 "\*Fabrikam\*"는 ID에 "Fabrikam"이 포함된 모든 호스팅 공급자에 대한 데이터만 반환하도록 제한합니다. 예를 들어 이 명령은 Fabrikam.com, Fabrikam.net 및 FabrikamUsers.com과 같은 공급자를 반환합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsHostingProvider** cmdlet에 파이프됩니다.

    Get-CsHostingProvider -Filter "*Fabrikam*" | Remove-CsHostingProvider

## 예제 4

예제 4에서는 확인 수준이 AlwaysVerifiable로 설정되지 않은 모든 호스팅 공급자가 삭제됩니다. 이 작업을 수행하기 위해 먼저 추가 매개 변수 없이 **Get-CsHostingProvider** cmdlet을 호출합니다. 그러면 조직에서 사용하도록 구성된 모든 호스팅 공급자의 컬렉션이 반환됩니다. 결과 컬렉션은 VerificationLevel 속성이 AlwaysVerifiable과 같지 않은 공급자만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 해당 컬렉션의 각 공급자를 제거하는 **Remove-CsHostingProvider** cmdlet에 파이프됩니다.

    Get-CsHostingProvider | Where-Object {$_.VerificationLevel -ne "AlwaysVerifiable"} | Remove-CsHostingProvider

## 예제 5

예제 5에서는 현재 사용할 수 없는 모든 호스팅 공급자를 제거합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsHostingProvider** cmdlet을 사용하여 조직에서 사용하도록 구성된 모든 호스팅 공급자의 컬렉션을 반환합니다. 이 컬렉션은 사용할 수 없는, 즉 Enabled 속성이 False와 같은 공급자만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 사용할 수 없는 각 호스팅 공급자를 삭제하는 **Remove-CsHostingProvider** cmdlet에 파이프됩니다.

    Get-CsHostingProvider | Where-Object {$_.Enabled -eq $False} | Remove-CsHostingProvider

## 자세한 정보

페더레이션은 두 조직에서 두 그룹 간의 통신을 용이하게 하는 트러스트 관계를 설정할 수 있는 수단입니다. 페더레이션이 설정되면 두 조직의 사용자가 서로 메신저 대화를 보내고, 현재 상태 알림에 가입하고, Lync 2013과 같은 SIP 응용 프로그램을 사용하여 통신할 수 있습니다. Lync Server를 사용하면 1) 사용자 조직과 다른 조직 간의 직접 페더레이션, 2) 사용자 조직과 공용 공급자 간의 페더레이션 및 3) 사용자 조직과 타사 호스팅 공급자 간의 페더레이션이라는 세 가지 유형의 페더레이션을 설정할 수 있습니다.

호스팅 공급자는 다른 조직에 SIP 통신 서비스를 제공하는 조직입니다. 예를 들어 Fabrikam, Inc.는 Contoso, Northwind Traders, Wingtip Toys 등의 사용자를 호스트할 수 있습니다. 호스팅 공급자와의 페더레이션 관계를 설정하면 해당 공급자가 호스트하는 조직과 효과적으로 페더레이션을 설정할 수 있습니다. 예를 들어 Fabrikam과 페더레이션한 경우 Contoso, Northwind Traders 및 Wingtip Toys의 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다.

분할 도메인 시나리오에서 호스팅 공급자를 사용할 수도 있습니다. 분할 도메인 시나리오에서는 일부 사용자에게 온 프레미스, 즉 로컬 Lync Server 구현에서 호스트되는 계정이 있습니다. 다른 사용자는 호스팅 공급자가 오프-프레미스에서 유지 관리하는 계정을 가지고 있습니다. 호스팅 공급자와 페더레이션하면 온-프레미스 사용자와 오프-프레미스 사용자가 서로 통신할 수 있습니다.

타사 호스팅 공급자와 페더레이션하려면 새 호스팅 공급자를 만들어서 활성화해야 합니다. 또한 타사 공급자도 사용자와 페더레이션 관계를 만들어야 합니다. 나중에 이 관계를 종료할 경우 **Remove-CsHostingProvider** cmdlet을 사용하여 호스팅 공급자를 삭제할 수 있습니다. 호스팅 공급자를 삭제하면 공급자가 페더레이션 파트너 목록에서 제거됩니다. 이때 관계를 다시 설정하기 위한 유일한 방법은 공급자를 다시 만드는 것입니다. 관계를 잠시 동안 일시 중단하려면 **Disable-CsHostingProvider** cmdlet을 사용합니다. 호스팅 공급자를 사용하지 않도록 설정하는 경우 공급자가 페더레이션 파트너 목록에서 삭제되지 않고 사용할 수 없는 것으로만 표시되며 사용자 조직과 해당 공급자 간에 통신을 사용할 수 없습니다. 관계를 다시 설정하려면 **Enable-CsHostingProvider** cmdlet을 사용하여 공급자를 다시 사용하도록 설정하면 됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsHostingProvider** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsHostingProvider"}

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>제거할 호스팅 공급자의 고유한 식별자입니다. Identity는 문자열 값입니다. 예를 들어 호스팅 공급자의 정규화된 도메인 이름(예: fabrikam.com)일 수도 있고, 서비스를 제공하는 회사의 이름(예: Fabrikam Hosting, Inc.)일 수도 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayHostingProvider 개체입니다. **Remove-CsHostingProvider** cmdlet은 호스팅 공급자 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayHostingProvider 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Disable-CsHostingProvider](disable-cshostingprovider.md)  
[Enable-CsHostingProvider](enable-cshostingprovider.md)  
[Get-CsHostingProvider](get-cshostingprovider.md)  
[New-CsHostingProvider](new-cshostingprovider.md)  
[Set-CsHostingProvider](set-cshostingprovider.md)

