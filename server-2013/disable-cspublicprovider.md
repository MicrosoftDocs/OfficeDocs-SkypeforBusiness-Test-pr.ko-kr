---
title: Disable-CsPublicProvider
TOCTitle: Disable-CsPublicProvider
ms:assetid: df1338ea-fe6d-45da-a39c-86108bb54ef5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398984(v=OCS.15)
ms:contentKeyID: 49305267
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Disable-CsPublicProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 공용 공급자를 사용하지 않도록 설정합니다. 공용 공급자는 메신저, 현재 상태 및 관련 서비스를 일반 대중에 제공하는 조직입니다. Lync Server에는 Yahoo, AIM(AOL) 및 Messenger(MSN)가 함께 제공되는데, 이러한 공용 공급자는 구성되어 있지만 사용하도록 설정되어 있지는 않습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Disable-CsPublicProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Disable-CsPublicProvider [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 Messenger인 공용 공급자를 사용하지 않도록 설정합니다. MSN이 이미 사용하지 않도록 설정된 경우 이 명령을 실행하면 오류가 반환됩니다.

    Disable-CsPublicProvider -Identity "Messenger"

## 예제 2

예제 2에서는 현재 사용 중인 모든 공용 공급자를 사용하지 않도록 설정합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPublicProvider** cmdlet을 사용하여 조직에서 현재 사용 중인 모든 공용 공급자 컬렉션을 반환합니다. 이 컬렉션은 Enabled 속성이 True와 같은 공급자만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 공급자를 사용하지 않도록 설정하는 **Disable-CsPublicProvider** cmdlet에 파이프됩니다.

    Get-CsPublicProvider | Where-Object {$_.Enabled -eq $True} | Disable-CsPublicProvider

## 예제 3

예제 3에 표시된 명령은 현재 사용 중이고 확인 수준이 AlwaysVerifiable로 설정된 모든 공용 공급자를 사용하지 않도록 설정합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPublicProvider** cmdlet을 호출하여 조직에서 현재 사용 중인 모든 공용 공급자 컬렉션을 반환합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. 여기서 1) VerificationLevel 속성이 AlwaysVerifiable과 같고 2) Enabled 속성이 True와 같은 공급자만 선택됩니다. -and 연산자는 지정된 조건을 모두 충족하는 개체만 선택하도록 **Where-Object** cmdlet에 지시합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 공급자를 사용하지 않도록 설정하는 **Disable-CsPublicProvider** cmdlet에 파이프됩니다.

    Get-CsPublicProvider | Where-Object {$_.VerificationLevel -ne "AlwaysVerifiable" -and $_.Enabled -eq $True} | Disable-CsPublicProvider

## 자세한 정보

페더레이션은 두 조직에서 두 그룹 간의 통신을 용이하게 하는 트러스트 관계를 설정할 수 있는 수단입니다. 페더레이션이 설정되면 두 조직의 사용자가 서로 인스턴스 메시지를 보내고, 현재 상태 알림에 가입하고, Lync 2013과 같은 SIP 응용 프로그램을 사용하여 통신할 수 있습니다. Lync Server를 사용하면 1) 사용자 조직과 다른 조직 간의 직접 페더레이션, 2) 사용자 조직과 공용 공급자 간의 페더레이션 및 3) 사용자 조직과 타사 호스팅 공급자 간의 페더레이션이라는 세 가지 유형의 페더레이션을 설정할 수 있습니다.

공용 공급자는 일반인에게 SIP(Session Initiation Protocol) 통신 서비스를 제공하는 조직입니다. 공용 공급자와의 페더레이션 관계를 설정하면 해당 공급자가 호스트하는 계정을 가진 사용자와의 페더레이션을 효과적으로 설정할 수 있습니다. 예를 들어 Messenger(MSN)와 페더레이션한 경우 사용자가 Messenger 계정을 가진 다른 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다.

공용 공급자와 페더레이션하려면 새 공용 공급자를 만들고 사용하도록 설정해야 합니다. 또한 해당 공용 공급자가 사용자와 페더레이션 관계를 만들어야 합니다. 공용 공급자를 만들 때 해당 페더레이션 관계를 사용할지 또는 사용하지 않을지 선택할 수 있는 옵션이 제공됩니다. 공용 공급자를 사용하도록 설정하면 조직의 사용자가 공용 공급자 계정을 가진 다른 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다. 반면, 공용 공급자를 사용하지 않도록 설정하면 공용 공급자 계정을 가진 다른 사용자와의 통신 기능이 일시 중단되고 해당 공급자를 다시 사용하도록 설정할 때까지 이 상태가 유지됩니다. 공급자 관계를 일시적으로 중단하려면 **Disable-CsPublicProvider** cmdlet을 사용하고, 공급자를 완전히 삭제하려면 **Remove-CsPublicProvider** cmdlet을 사용하면 됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Disable-CsPublicProvider** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Disable-CsPublicProvider"}

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
<td><p>사용하지 않도록 설정할 공용 공급자의 고유 식별자입니다. Identity는 일반적으로 서비스를 제공하는 웹 사이트(예: Yahoo!, AOL, MSN 등)의 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>공용 공급자 표시 개체</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider 개체입니다. **Disable-CsPublicProvider** cmdlet은 공용 공급자 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider 개체의 인스턴스를 비활성화합니다.

## 참고 항목

#### 기타 리소스

[Enable-CsPublicProvider](enable-cspublicprovider.md)  
[Get-CsPublicProvider](get-cspublicprovider.md)  
[New-CsPublicProvider](new-cspublicprovider.md)  
[Remove-CsPublicProvider](remove-cspublicprovider.md)  
[Set-CsPublicProvider](set-cspublicprovider.md)

