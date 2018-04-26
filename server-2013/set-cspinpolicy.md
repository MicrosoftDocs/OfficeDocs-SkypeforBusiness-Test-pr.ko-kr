---
title: Set-CsPinPolicy
TOCTitle: Set-CsPinPolicy
ms:assetid: f0e1afb9-4c71-45c5-8093-6cd12db3d697
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412997(v=OCS.15)
ms:contentKeyID: 49305480
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsPinPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 기존 클라이언트 개인식별번호(PIN) 정책을 수정합니다. PIN 인증을 통해 사용자는 사용자 이름 및 암호 대신 PIN을 제공하여 Lync Server에 액세스할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsPinPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsPinPolicy [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AllowCommonPatterns <$true | $false>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-MaximumLogonAttempts <UInt32>] [-MinPasswordLength <UInt32>] [-PINHistoryCount <UInt64>] [-PINLifetime <UInt64>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트에 할당된 PIN 정책을 수정합니다. 이 경우 명령은 MinPasswordLength 속성 값을 10으로 변경합니다. 이는 새 PIN이 10자리 이상을 포함해야 한다는 의미입니다.

    Set-CsPinPolicy -Identity site:Redmond -MinPasswordLength 10

## 예제 2

예제 2에서는 ID가 RedmondUsersPinPolicy인 사용자별 PIN 정책의 두 가지 속성을 수정합니다. 즉, MinPasswordLength 및 AllowCommonPatterns 속성의 값을 변경합니다.

    Set-CsPinPolicy -Identity RedmondUsersPinPolicy -MinPasswordLength 10 -AllowCommonPatterns $True

## 예제 3

예제 3에 표시된 명령은 조직에서 사용하도록 구성된 모든 PIN 정책의 MinPasswordLength 값을 변경합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsPinPolicy** cmdlet을 호출하여 기존의 모든 PIN 정책 컬렉션을 검색합니다. 이 컬렉션은 컬렉션의 각 정책에서 MinPasswordLength 속성 값을 수정하는 **Set-CsPinPolicy** cmdlet에 파이프됩니다.

    Get-CsPinPolicy | Set-CsPinPolicy -MinPasswordLength 10

## 자세한 정보

Lync Server를 사용하면 사용자가 전화를 통해 시스템에 연결하거나 PSTN(공중 전화망) 전화 회의에 참가할 수 있습니다. 일반적으로 사용자가 시스템에 로그온하거나 전화 회의에 참가하려면 사용자 이름 또는 암호를 입력해야 하지만 영숫자 키패드가 없는 전화기를 사용하는 경우 사용자 이름 및 암호를 입력하기 어려울 수 있습니다. 따라서 Lync Server는 사용자에게 숫자로만 구성된 PIN을 제공할 수 있도록 지원합니다. PIN을 묻는 메시지가 표시되면 사용자 이름 및 암호 대신 PIN을 입력하여 시스템에 로그온하거나 전화 회의에 참가할 수 있습니다.

Lync Server에서는 클라이언트 PIN 정책을 사용하여 PIN 인증 속성을 관리합니다. 예를 들어 PIN의 최소 길이를 지정하고 연속적인 숫자(예: 123456와 같은 PIN) 등의 "공통 패턴"을 사용하는 PIN의 허용 여부를 결정할 수 있습니다. PIN 정책은 전역, 사이트 및 사용자별 범위에서 구성할 수 있습니다. **Set-CsPinPolicy** cmdlet을 사용하여 이러한 정책의 속성 값을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsPinPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsPinPolicy"}

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
<td><p><em>AllowCommonPatterns</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>PIN 번호에 &quot;공통 패턴&quot;이 허용되는지 여부를 지정합니다. 공통 패턴은 반복 숫자(225577), 4번 이상 연속되는 숫자 및 사용자의 전화 번호 또는 내선 번호와 일치하는 PIN을 포함합니다. True로 설정된 경우 공통 패턴(예: 연속 숫자를 포함하는 PIN 123456)이 허용되고, False로 설정된 경우 공통 패턴이 허용되지 않습니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 PIN 정책에 동반될 추가 텍스트를 제공하는 데 사용됩니다. 예를 들어 정책을 할당할 사용자에 대한 정보를 설명에 포함할 수 있습니다.</p></td>
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
<td><p>생성될 때 정책에 할당된 고유 식별자입니다. PIN 정책은 전역, 사이트 또는 사용자별 범위에서 할당할 수 있습니다. 전역 인스턴스를 참조하려면 -Identity global 구문을 사용합니다. 사이트 범위에서 정책을 참조하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 사용자별 정책을 참조하려면 -Identity RedmondPinPolicy와 유사한 구문을 사용합니다.</p>
<p>ID를 지정하지 않으면 <strong>Set-CsPinPolicy</strong> cmdlet이 전역 정책을 수정하게 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>UserPinPolicy 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaximumLogonAttempts</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>사용자의 PIN이 자동으로 잠기기 전에 허용되는 연속 로그온 실패 수를 지정합니다. 로그온 실패 수는 로컬 로그온 실패와 전역 로그온 실패의 두 가지 방법으로 계산됩니다. 사용자가 처음 로그온을 시도하면 새로운 30분 관찰 창이 시작되고 이러한 30분 창 중에 실패한 각 로그온은 로컬 로그온 실패 및 전역 로그온 실패로 기록됩니다. 사용자가 이러한 30분 관찰 창 중에 MaximumLogonAttempts에 도달하면 1시간 동안 일시적으로 시스템 액세스가 잠깁니다. 이 기간 동안에는 올바른 PIN을 입력해도 PIN 인증을 사용하여 로그온할 수 없게 됩니다.</p>
<p>잠금 기간이 만료되면 사용자의 로컬 로그온 시도가 0으로 재설정됩니다. 그러나 사용자의 전역 로그온 시도는 재설정되지 않습니다. 사용자가 계속해서 로그온에 실패하면 결국 허용되는 최대 전역 로그온 시도 수에 도달하게 됩니다. 이러한 지점에 도달한 사용자는 시스템에 의해 PIN이 잠기고, 관리자가 PIN의 잠금을 해제할 때까지 PIN 인증을 사용할 수 없게 됩니다.</p>
<p>허용되는 최대 로그온 시도 수는 PIN 크기에 따라서도 달라집니다. 그러므로 <strong>Get-CsPinPolicy</strong> cmdlet을 실행할 때 MaximumLogonAttempts 속성이 기본값을 표시하지 않습니다. 기본적으로 4자리 PIN은 로컬 로그온 시도 횟수 10번과 전역 로그온 시도 횟수 100번을 허용합니다. 5자리 PIN은 로컬 로그온 시도 25번과 전역 로그온 시도 1000번을 허용하며, 6자리 이상의 PIN은 로컬 로그온 시도 25번과 전역 로그온 시도 5000번을 허용합니다. MaximumLogonAttempts 속성 값을 지정하면 허용되는 최대 로컬 로그온 시도 횟수에 해당 값이 사용되지만 전역 로그온 값은 MaximumLogonAttempts에 할당된 값에 관계없이 변경되지 않습니다.</p>
<p>사용자가 PIN 인증을 사용하여 로그온에 성공할 때마다 로컬 실패 로그온 시도 횟수가 0으로 설정됩니다. 전역 로그온 시도 횟수는 관리자가 사용자의 PIN 잠금을 해제할 때만 재설정됩니다.</p>
<p>MaximumLogonAttempts는 1에서 999(포함) 사이의 임의 정수로 설정할 수 있습니다. 그러나 이 속성은 수정하지 않는 것이 좋습니다. 이 속성을 기본값인 null로 설정하면 Lync Server 2013에서는 잠금 정책을 자동으로 계산합니다. 그러면 대개 최고 수준의 보안이 적용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MinPasswordLength</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>PIN 번호에 허용되는 최소 길이, 즉 최소 자릿수입니다. 예를 들어 MinPasswordLength가 8로 설정된 경우 PIN 1259는 4자리밖에 없으므로 거부됩니다. PIN 길이는 4-24자리여야 합니다. 기본값은 5입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PINHistoryCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt64</p></td>
<td><p>사용자가 동일한 PIN을 다시 사용할 수 있는 주기를 지정합니다. 예를 들어 PINHistoryCount가 3으로 설정된 경우 사용자가 처음에 세 번째로 PIN을 재설정할 때까지는 새 PIN을 사용해야 합니다. 네 번째로 재설정할 때는 첫 번째 PIN을 다시 사용할 수 있습니다. 그리고 다섯 번째로 재설정할 때는 두 번째 PIN을 사용하는 식입니다. PIN 기록 개수는 0-20(포함) 사이의 임의 정수가 될 수 있습니다. 0은 사용자가 동일한 PIN을 계속해서 다시 사용할 수 있다는 의미입니다. 기본적으로 PINHistoryCount는 0로 설정됩니다.</p>
<p>PINLifetime이 0보다 큰 값으로 설정된 경우 PINHistoryCount도 0보다 커야 합니다. 예를 들어 PINLifetime을 30으로 설정하고 PINHistoryCount를 0으로 설정할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PINLifetime</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt64</p></td>
<td><p>PIN이 유효한 상태로 남아 있는 기간(일)을 지정합니다. PIN 수명이 만료되면 사용자는 새 PIN을 선택해야 PIN 인증을 사용하여 시스템에 액세스할 수 있습니다. PINLifetime은 0-999(포함) 사이의 임의 정수입니다. 0은 PIN이 만료되지 않음을 의미합니다. 기본적으로 PIN 수명은 0일로 설정됩니다.</p>
<p>PINLifetime을 0보다 큰 값으로 설정한 경우 PINHistoryCount도 0보다 큰 값으로 설정해야 합니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.UserPin.UserPolicy 개체입니다. **Set-CsPinPolicy** cmdlet은 PIN 정책 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsPinPolicy**cmdlet은 값이나 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.UserPin.UserPolicy 개체의 인스턴스를 한 개 이상 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPinPolicy](get-cspinpolicy.md)  
[Grant-CsPinPolicy](grant-cspinpolicy.md)  
[New-CsPinPolicy](new-cspinpolicy.md)  
[Remove-CsPinPolicy](remove-cspinpolicy.md)

