---
title: Set-CsPresenceProvider
TOCTitle: Set-CsPresenceProvider
ms:assetid: 3f2e30d1-edb5-4839-a24f-11b77b699a1d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204833(v=OCS.15)
ms:contentKeyID: 49303415
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsPresenceProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 현재 상태 공급자를 수정합니다. 현재 상태 공급자는 사용자 서비스 구성 설정 컬렉션의 PresenceProviders 속성을 나타냅니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsPresenceProvider [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsPresenceProvider [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 **Set-CsPresenceProvider** cmdlet을 사용하여 기존 현재 상태 공급자의 FQDN을 수정하는 방법을 보여줍니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **Get-CsPresenceProvider** cmdlet을 사용하여 ID가 "global/contoso.com"인 현재 상태 공급자에 대한 개체 참조를 만듭니다. 이 개체 참조는 변수 $x에 저장됩니다.

두 번째 명령에서는 개체 참조의 FQDN 속성이 현재 상태 공급자의 새 FQDN인 contoso2.com으로 설정됩니다. FQDN 속성을 구성하고 나면 Instance 속성과 함께 **Set-CsPresenceProvider** cmdlet을 사용하여 이러한 변경 내용을 User Services 구성 설정의 전역 컬렉션에 씁니다.

    $x = Get-CsPresenceProvider -Identity "global/contoso.com" 
    $x.Fqdn = "contoso2.com"
    Set-CsPresenceProvider -Instance $x

## 자세한 정보

**CsPresenceProvider** cmdlet은 사용자 서비스 구성 설정에 포함된 PresenceProviders 속성을 관리하는 데 사용됩니다. 이 설정의 가장 중요한 용도는 권한이 부여된 현재 상태 공급자 컬렉션을 포함하는 현재 상태 정보를 유지 관리하는 것입니다. 해당 컬렉션은 PresenceProviders 속성에 저장됩니다.

**Set-CsPresenceProvider** cmdlet을 사용하면 현재 조직에서 사용하도록 구성되어 있는 현재 상태 공급자의 FQDN을 수정할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsPresenceProvider"}

**Lync Server 제어판:** **Set-CsPresenceProvider** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<th>형식</th>
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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 현재 상태 공급자의 고유 식별자입니다. 현재 상태 공급자의 ID는 두 부분, 즉 service:UserServer:atl-cs-001.litwareinc.com과 같은 규칙이 적용된 범위(상위 항목)와 공급자 Fqdn으로 구성됩니다. 전역 범위에서 현재 상태 공급자를 수정하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;global/fabrikam.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
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

**Set-CsPresenceProvider** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PresenceProvider\#Decorated 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsPresenceProvider** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PresenceProvider\#Decorated 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPresenceProvider](get-cspresenceprovider.md)  
[Get-CsUserServicesConfiguration](get-csuserservicesconfiguration.md)  
[New-CsPresenceProvider](new-cspresenceprovider.md)  
[Remove-CsPresenceProvider](remove-cspresenceprovider.md)

