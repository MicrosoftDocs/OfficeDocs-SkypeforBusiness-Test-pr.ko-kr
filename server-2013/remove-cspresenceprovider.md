---
title: Remove-CsPresenceProvider
TOCTitle: Remove-CsPresenceProvider
ms:assetid: 7e8b540e-484f-4003-8665-18e2b3974f33
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205036(v=OCS.15)
ms:contentKeyID: 49304172
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsPresenceProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

이전에 조직에서 사용하도록 구성된 현재 상태 공급자를 제거합니다. 현재 상태 공급자는 사용자 서비스 구성 설정 컬렉션의 PresenceProviders 속성을 나타냅니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsPresenceProvider -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 "global/fabrikam.com"인 현재 상태 공급자를 제거합니다.

    Remove-CsPresenceProvider -Identity "global/fabrikam.com"

## 예제 2

예제 2에서는 조직에서 사용하도록 구성된 모든 현재 상태 공급자를 제거합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsPresenceProvider** cmdlet을 호출합니다. 그러면 구성되어 있는 모든 현재 상태 공급자의 컬렉션이 반환됩니다. 해당 컬렉션은 **Remove-CsPresenceProvider** cmdlet에 파이프되며, 이 cmdlet은 컬렉션의 각 항목(각 공급자)을 삭제합니다.

    Get-CsPresenceProvider | Remove-CsPresenceProvider

## 예제 3

예제 3에서는 Fqdn에 문자열 값 "fabrikam.com"이 포함된 모든 현재 상태 공급자를 삭제하는 방법을 보여줍니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPresenceProvider** cmdlet을 사용하여 사용 가능한 모든 현재 상태 공급자의 컬렉션을 반환합니다. 해당 컬렉션은 **Where-Object** cmdlet에 파이프되며, 이 cmdlet은 Fqdn 속성에 문자열 값 "fabrikam.com"이 포함된(-match) 공급자만 선택합니다. 이렇게 필터링된 컬렉션은 **Remove-CsPresenceProvider** cmdlet에 파이프되며, 이 cmdlet은 필터링된 컬렉션의 각 공급자를 삭제합니다.

    Get-CsPresenceProvider | Where-Object {$_.Fqdn -match "fabrikam.com"} | Remove-CsPresenceProvider

## 자세한 정보

**CsPresenceProvider** cmdlet은 사용자 서비스 구성 설정에 포함된 PresenceProviders 속성을 관리하는 데 사용됩니다. 이 설정의 가장 중요한 용도는 권한이 부여된 현재 상태 공급자 컬렉션을 포함하는 현재 상태 정보를 유지 관리하는 것입니다. 해당 컬렉션은 PresenceProviders 속성에 저장됩니다.

**Remove-CsPresenceProvider** cmdlet을 사용하면 하나 이상의 User Services 구성 설정 컬렉션 PresenceProviders 속성에서 현재 상태 공급자를 제거할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsPresenceProvider"}

**Lync Server 제어판:** **Remove-CsPresenceProvider** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>제거할 현재 상태 공급자의 고유 식별자입니다. 단일 공급자를 제거하려면 범위와 공급자 Fqdn이 모두 포함된 공급자의 실제 ID를 사용합니다.</p>
<p>-Identity &quot;global/fabrikam.com&quot;</p>
<p>특정 범위에서 구성된 모든 현재 상태 공급자를 제거하려면 범위를 ID로 사용하기만 하면 됩니다. 다음 구문은 전역 범위에서 구성된 모든 공급자를 제거합니다.</p>
<p>-Identity &quot;global&quot;</p></td>
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

**Remove-CsPresenceProvider** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PresenceProvider\#Decorated 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsPresenceProvider** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PresenceProvider\#Decorated 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPresenceProvider](get-cspresenceprovider.md)  
[Get-CsUserServicesConfiguration](get-csuserservicesconfiguration.md)  
[New-CsPresenceProvider](new-cspresenceprovider.md)  
[Set-CsPresenceProvider](set-cspresenceprovider.md)

