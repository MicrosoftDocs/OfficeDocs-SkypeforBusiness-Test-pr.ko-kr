---
title: Remove-CsUserServicesConfiguration
TOCTitle: Remove-CsUserServicesConfiguration
ms:assetid: 8eed6091-ab96-49d4-a0c0-d1f9180a0b90
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398722(v=OCS.15)
ms:contentKeyID: 49304352
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsUserServicesConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

User Services 구성 설정의 기존 컬렉션을 제거합니다. User Services 서비스는 현재 상태 정보를 유지 관리하고 전화 회의를 관리하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsUserServicesConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트(-Identity site:Redmond)에서 User Services 구성 설정을 제거합니다.

    Remove-CsUserServicesConfiguration -Identity site:Redmond

## 예제 2

예제 2에서는 서비스 범위에서 적용된 모든 User Services 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 명령은 Filter 매개 변수와 함께 **Get-CsUserServicesConfiguration** cmdlet을 호출합니다. 필터 값 "service:\*"는 서비스 범위에서 구성된 설정, 즉 ID가 "service:" 문자로 시작하는 설정에 대해 반환되도록 제한합니다. 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsUserServicesConfiguration** cmdlet에 파이프됩니다.

    Get-CsUserServicesConfiguration -Filter "service:*:" | Remove-CsUserServicesConfiguration

## 예제 3

예제 3에서는 사용자가 250개보다 많은 연락처를 소유하도록 허용하는 모든 User Services 구성 설정을 제거합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsUserServicesConfiguration** cmdlet을 호출하여 현재 사용 중인 모든 User Services 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 MaxContacts 속성 값이 250보다 큰 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 **Remove-CsUserServicesConfiguration** cmdlet에 파이프되어 제거됩니다.

    Get-CsUserServicesConfiguration | Where-Object {$_.MaxContacts -gt 250} | Remove-CsUserServicesConfiguration

## 자세한 정보

Lync Server는 User Services 서비스를 사용하여 사용자의 현재 상태 정보를 유지 관리하고 모임 및 전화 회의를 관리합니다. 그런 다음 **CsUserServicesConfiguration** cmdlet을 사용하여 전역, 사이트 및 서비스 범위에서 User Services 구성 설정을 관리합니다. User Services 구성 설정을 호스트할 수 있는 서비스는 User Services 서비스 자체뿐입니다. 이러한 설정은 사용자가 가질 수 있는 연락처 수, 사용자가 한 번에 예약할 수 있는 모임 수, 전화 회의가 활성 상태로 남아 있을 수 있는 시간 등을 결정합니다.

**Remove-CsUserServicesConfiguration** cmdlet을 사용하면 사이트 또는 서비스 범위에서 적용된 User Services 구성 설정을 삭제할 수 있습니다. 전역 컬렉션에 대해서도 이 cmdlet을 실행할 수 있습니다. 그러나 이 경우 전역 설정은 삭제되지 않습니다. 전역 설정은 삭제할 수 없기 때문입니다. 대신 전역 컬렉션 내의 모든 속성이 기본값으로 다시 설정됩니다. 예를 들어 전역 설정에서 MaxContacts 값을 500으로 변경한 다음 **Remove-CsUserServicesConfiguration** cmdlet을 실행하면 MaxContacts가 기본값 250으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsUserServicesConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsUserServicesConfiguration"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>제거할 User Services 구성 설정의 고유 식별자입니다. 사이트 범위에서 구성된 설정을 삭제하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 서비스 수준에서 설정을 삭제하려면 -Identity service:UserServer:atl-cs-001.litwareinc.com과 유사한 구문을 사용합니다.</p>
<p>전역 컬렉션에 대해 <strong>Remove-CsUserServicesConfiguration</strong> cmdlet을 실행할 수도 있습니다. 그러나 이 경우 전역 컬렉션은 삭제되지 않습니다. 대신 해당 컬렉션의 모든 속성이 기본값으로 다시 설정됩니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.UserServicesSettings 개체입니다. **Remove-CsUserServicesConfiguration** cmdlet은 User Services 설정 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsUserServicesConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.UserServicesSettings 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUserServicesConfiguration](get-csuserservicesconfiguration.md)  
[New-CsUserServicesConfiguration](new-csuserservicesconfiguration.md)  
[Set-CsUserServicesConfiguration](set-csuserservicesconfiguration.md)

