---
title: Remove-CsRegistrarConfiguration
TOCTitle: Remove-CsRegistrarConfiguration
ms:assetid: 67ee01a1-fdfe-4994-b03a-57a332aa45be
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398482(v=OCS.15)
ms:contentKeyID: 49303897
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsRegistrarConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

등록자 구성 설정의 기존 컬렉션을 제거합니다. 등록자는 로그온 요청을 인증하고 사용자 상태에 대한 정보를 유지 관리하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsRegistrarConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트에 할당된 등록자 구성 설정을 삭제합니다. 이러한 설정을 삭제하면 Redmond 사이트의 등록자는 자동으로 전역 등록자 설정을 사용합니다.

    Remove-CsRegistrarConfiguration -Identity site:Redmond

## 예제 2

예제 2에서는 서비스 범위에 할당된 모든 등록자 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsRegistrarConfiguration** cmdlet을 Filter 매개 변수와 함께 호출합니다. 필터 값 "service:\*"는 반환된 데이터를 ID가 문자 "service:"으로 시작하는 설정으로 제한합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsRegistrarConfiguration** cmdlet에 파이프됩니다.

    Get-CsRegistrarConfiguration -Filter "service:*" | Remove-CsRegistrarConfiguration

## 예제 3

예제 3에서는 EnableDHCPServer 속성이 True인 모든 등록자 구성 설정이 삭제됩니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsRegistrarConfiguration** cmdlet을 매개 변수 없이 호출하여 현재 사용되고 있는 모든 등록자 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 EnableDHCPServer 속성이 True와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsRegistrarConfiguration** cmdlet에 파이프됩니다.

    Get-CsRegistrarConfiguration | Where-Object {$_.EnableDHCPServer -eq $True} | Remove-CsRegistrarConfiguration

## 자세한 정보

등록자는 Lync Server의 가장 중요한 구성 요소라고 할 수 있습니다. 등록자 없이는 사용자가 시스템에 로그온할 수 없으며 Lync Server에서 사용자와 사용자의 현재 상태를 추적할 수 없기 때문입니다. 사용자가 Lync Server에 로그온하면 로그온한 끝점에서 등록자에 REGISTER 요청을 보냅니다. 그러면 서버에서 클라이언트 장치의 인증 자격 증명을 요구하여 응답합니다. 클라이언트가 시도를 전달하면, 즉 클라이언트가 올바른 자격 증명 집합을 제공하면 사용자가 인증되고 IP 주소, 포트 및 사용자 이름과 같은 끝점 정보가 등록 데이터베이스에 로깅됩니다. 사용자가 로그오프하면 이 정보가 데이터베이스에서 제거됩니다. 로그온한 시점부터 로그오프할 때까지 등록자는 상태 정보를 최신 상태로 유지하면서 사용자가 주고받는 메시지의 경로 지정을 지원합니다.

등록자 구성 설정은 끝점과 끝점 구독을 관리하는 데 사용됩니다. 이러한 설정은 전역, 사이트 또는 서비스 범위에서 적용할 수 있습니다. 서비스 범위 설정은 등록자 서비스에서만 사용할 수 있습니다.

**Remove-CsRegistrarConfiguration** cmdlet을 사용하면 사이트 또는 서비스 범위에서 적용된 등록자 구성 설정을 제거할 수 있습니다. 등록자는 삭제 또는 제거되지 않고 해당 등록자를 관리하는 구성 설정만 제거됩니다. 이러한 설정이 사이트 또는 서비스 범위에 없는 경우 전역 설정을 사용하여 등록자를 관리합니다.

**Remove-CsRegistrarConfiguration** cmdlet을 전역 등록자 구성 설정에 대해서도 실행할 수 있습니다. 그러나 이 경우 전역 설정은 제거되지 않습니다. 전역 설정은 삭제할 수 없기 때문입니다. 대신 해당 컬렉션의 모든 속성이 기본값으로 다시 설정됩니다. 예를 들어, MinEndpointExpiration 속성 값을 500으로 변경한 경우 해당 값은 다시 300으로 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsRegistrarConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsRegistrarConfiguration e"}

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
<td><p>제거할 등록자 구성 설정의 고유 식별자입니다. 사이트 범위에서 구성된 설정을 제거하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 서비스 수준에서 설정을 제거하려면 -Identity service:Registar:atl-cs-001.litwareinc.com과 같은 구문을 사용합니다.</p>
<p><strong>Remove-CsRegistrarConfiguration</strong> cmdlet은 전역 설정에 대해서도 실행할 수 있습니다(-Identity global). 그러나 이 경우 전역 설정은 제거되지 않습니다. 대신 전역 컬렉션의 모든 속성이 기본값으로 다시 설정됩니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Registrar.RegistrarSettings 개체입니다. **Remove-CsRegistrarConfiguration** cmdlet은 등록자 설정 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsRegistrarConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Registrar.RegistrarSettings 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsRegistrarConfiguration](get-csregistrarconfiguration.md)  
[New-CsRegistrarConfiguration](new-csregistrarconfiguration.md)  
[Set-CsRegistrarConfiguration](set-csregistrarconfiguration.md)

