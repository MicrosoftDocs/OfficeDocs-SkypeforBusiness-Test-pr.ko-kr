---
title: Remove-CsPinPolicy
TOCTitle: Remove-CsPinPolicy
ms:assetid: 60bebb77-4181-4c5c-9c0e-dd1ece71f1d2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398431(v=OCS.15)
ms:contentKeyID: 49303800
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsPinPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 개인식별번호(PIN) 정책을 제거합니다. PIN 인증 및 PIN 정책은 사용자가 사용자 이름 및 암호 대신 PIN을 제공하여 Lync Server에 액세스할 수 있도록 합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsPinPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID RedmondUsersPinPolicy가 포함된 사용자별 PIN 정책을 제거합니다.

    Remove-CsPinPolicy -Identity RedmondUsersPinPolicy

## 예제 2

예제 2에 표시된 명령은 사이트 범위에서 구성된 모든 PIN 정책을 제거합니다. 이 작업을 수행하기 위해 **Get-CsPinPolicy** cmdlet을 Filter 매개 변수와 함께 사용하여 ID가 문자 "site:"으로 시작되는 모든 정책의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 정책을 삭제하는 **Remove-CsPinPolicy** cmdlet에 파이프됩니다.

    Get-CsPinPolicy -Filter "site:*" | Remove-CsPinPolicy

## 예제 3

예제 3에서는 **Get-CsPinPolicy** cmdlet, **Where-Object** cmdlet 및 **Remove-CsPinPolicy** cmdlet을 사용하여 AllowCommonPatterns 속성이 True인 모든 PIN 정책을 삭제합니다. 이를 위해 먼저 **Get-CsPinPolicy** cmdlet을 사용하여 조직에서 사용하도록 구성된 모든 PIN 정책의 컬렉션을 반환합니다. 이 컬렉션은 AllowCommonPatterns가 True와 같은 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 해당 컬렉션의 각 정책을 삭제하는 **Remove-CsPinPolicy** cmdlet에 파이프됩니다.

    Get-CsPinPolicy | Where-Object {$_.AllowCommonPatterns -eq $True} | Remove-CsPinPolicy

## 예제 4

예제 4에 표시된 명령은 사용자별 및 사이트 범위에서 구성된 모든 PIN 정책을 삭제합니다. 이 작업을 수행하기 위해 **Get-CsPinPolicy** cmdlet을 사용하여 조직에서 사용하도록 구성된 모든 PIN 정책의 컬렉션을 반환한 다음 전체 컬렉션을 **Remove-CsPinPolicy** cmdlet에 파이프합니다. 전역 정책도 이 컬렉션에 포함됩니다. 그러나 전역 정책은 삭제되지 않습니다. 대신에 해당 전역 정책의 모든 속성이 기본값으로 다시 설정됩니다.

    Get-CsPinPolicy | Remove-CsPinPolicy

## 자세한 정보

Lync Server를 사용하면 사용자가 전화를 통해 시스템에 연결하거나 PSTN(공중 전화망) 전화 회의에 참가할 수 있습니다. 일반적으로 사용자가 시스템에 로그온하거나 전화 회의에 참가하려면 사용자 이름 또는 암호를 입력해야 하지만 영숫자 키패드가 없는 전화기를 사용하는 경우 사용자 이름 및 암호를 입력하기 어려울 수 있습니다. 따라서 Lync Server는 사용자에게 숫자로만 구성된 PIN을 제공할 수 있도록 지원합니다. PIN을 묻는 메시지가 표시되면 사용자 이름 및 암호 대신 PIN을 입력하여 시스템에 로그온하거나 전화 회의에 참가할 수 있습니다.

Lync Server에서는 PIN 정책을 사용하여 PIN 인증 속성을 관리합니다. 예를 들어 PIN의 최소 길이를 지정하고 연속된 숫자(예: 123456과 같은 PIN) 등의 "공통 패턴"을 사용하는 PIN의 허용 여부를 결정할 수 있습니다. Lync Server를 설치할 때 생성된 전역 PIN 정책 외에 사이트 또는 사용자별 범위에서 적용되는 사용자 지정 PIN 정책을 만들 수 있습니다.

**Remove-CsPinPolicy** cmdlet을 사용하여 사이트 범위나 사용자별 범위에서 구성된 PIN 정책을 제거할 수 있습니다. 사이트 범위 정책이나 사용자별 정책을 제거하면 해당 정책이 삭제되고 더 이상 사용할 수 없게 됩니다. 또한 해당 정책이 할당된 사용자는 정책 계층에서 다음 수준의 정책을 자동으로 상속합니다(전역, 사이트, 서비스, 사용자별). 예를 들어, 사이트 정책을 제거하면 이전에 해당 정책의 영향을 받은 모든 사용자의 해당 PIN 설정은 전역 정책의 관리를 받습니다.

전역 정책에 대해 **Remove-CsPinPolicy** cmdlet을 실행할 수도 있습니다. 그러나 이 경우 정책은 제거되지 않습니다. 전역 정책은 삭제할 수 없기 때문입니다. 대신에 해당 전역 정책의 모든 속성이 기본값으로 다시 설정됩니다. 예를 들어 11자리의 최소 PIN 길이를 사용하도록 전역 정책을 구성했다고 가정합니다. 전역 정책을 제거하면 최소 PIN 길이가 5자리의 기본 길이로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsPinPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsPinPolicy"}

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
<td><p>생성될 때 정책에 할당된 고유 식별자입니다. PIN 정책은 전역, 사이트 또는 사용자별 범위에서 할당할 수 있습니다. 전역 인스턴스를 참조하려면 -Identity global 구문을 사용합니다. 사이트 범위의 정책을 참조하려면 -Identity site:Redmond 구문을 사용합니다. 사용자별 범위의 정책을 참조하려면 -Identity RedmondPINPolicy와 같은 구문을 사용합니다.</p>
<p></p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.UserPin.UserPolicy 개체입니다. **Remove-CsPinPolicy** cmdlet은 PIN 정책 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Remove-CsPinPolicy** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WriteableConfig.Policy.UserPin.UserPolicy 개체의 인스턴스를 하나 이상 제거합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPinPolicy](get-cspinpolicy.md)  
[Grant-CsPinPolicy](grant-cspinpolicy.md)  
[New-CsPinPolicy](new-cspinpolicy.md)  
[Set-CsPinPolicy](set-cspinpolicy.md)

