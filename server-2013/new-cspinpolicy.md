---
title: New-CsPinPolicy
TOCTitle: New-CsPinPolicy
ms:assetid: d64fb0f9-1cdc-4497-992a-d002abafe92e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398935(v=OCS.15)
ms:contentKeyID: 49305173
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsPinPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 클라이언트 개인식별번호(PIN) 정책을 만듭니다. PIN 인증을 통해 사용자는 사용자 이름 및 암호 대신 PIN을 제공하여 Lync Server에 액세스할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsPinPolicy -Identity <XdsIdentity> [-AllowCommonPatterns <$true | $false>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MaximumLogonAttempts <UInt32>] [-MinPasswordLength <UInt32>] [-PINHistoryCount <UInt64>] [-PINLifetime <UInt64>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **New-CsPinPolicy** cmdlet을 사용하여 ID가 site:Redmond인 새 PIN 정책을 만듭니다. 이 명령에는 단 하나의 선택 매개 변수인 -MinPasswordLength가 포함됩니다. 이 매개 변수는 MinPasswordLength 속성을 10으로 설정하는 데 사용됩니다. 나머지 모든 정책 속성은 기본값을 사용하여 구성됩니다.

    New-CsPinPolicy -Identity "site:Redmond" -MinPasswordLength 10

## 예제 2

예제 2에 표시된 명령은 ID가 site:Redmond인 새 정책을 만듭니다. 이 명령은 MinPasswordLength, PINHistoryCount 및 PINLifetime 매개 변수를 사용하여 새 정책의 세 가지 속성 값을 명시적으로 구성합니다.

    New-CsPinPolicy -Identity "site:Redmond" -MinPasswordLength 10 -PINHistoryCount 10 -PINLifetime 30

## 예제 3

예제 3에 표시된 명령은 새 PIN 정책을 메모리에만 만들고, 해당 정책의 속성 값을 수정한 다음, **Set-CsPinPolicy** cmdlet을 사용하여 메모리에만 나타나는 정책을 실제 PIN 정책으로 변환하는 방법을 보여 줍니다. 위의 첫 번째 줄에서 **New-CsPinPolicy** cmdlet 및 InMemory 매개 변수를 사용하여 ID가 site:Redmond이고 메모리에만 나타나는 정책을 만듭니다. 이 정책은 변수 $x에 저장됩니다. 변수에 정책을 할당하지 않으면 정책이 메모리에만 만들어진 다음 명령을 완료하는 즉시 사라집니다.

가상 정책을 변수 $x에 할당한 후에는 그다음 세 가지 명령을 사용하여 해당 정책의 속성 값을 수정합니다. 예를 들어 두 번째 줄은 MinPasswordLength 속성의 값을 10으로 설정합니다. 모든 속성을 구성한 후에는 **Set-CsPinPolicy** cmdlet을 사용하여 ID가 site:Redmond인 실제 정책을 만듭니다. 이 작업은 Instance 매개 변수를 사용하고 변수 $x를 매개 변수 값으로 전달하여 수행됩니다. **Set-CsPinPolicy** cmdlet을 호출한 후에는 **Get-CsPinPolicy** cmdlet을 사용하여 정책 및 해당 속성 값을 볼 수 있습니다.

    $x = New-CsPinPolicy -Identity "site:Redmond" -InMemory
    $x.MinPasswordLength = 10
    $x.PINHistoryCount = 10
    $x.PINLifetime = 30
    Set-CsPinPolicy -Instance $x

## 예제 4

예제 4에 사용된 명령은 기존 정책 site:Redmond에 있는 속성 값 중 하나를 사용하는 새 PIN 정책(site:Paris)을 만듭니다. 이 작업을 수행하기 위해 첫 번째 명령은 **Get-CsPinPolicy** cmdlet을 사용하여 PIN 정책 site:Redmond를 검색합니다. 이 정책에 대해 검색된 정보는 변수 $x에 저장됩니다.

두 번째 명령에서는 **New-CsPinPolicy** cmdlet을 사용하여 site:Paris 정책을 만듭니다. 그리고 MinPasswordLength 매개 변수를 사용하여 MinPasswordLength 속성의 값을 지정합니다. 그러나 이 명령은 하드 코드된 숫자 값을 사용하는 대신 $x.MinPasswordLength를 매개 변수 값으로 사용합니다. 그러면 **New-CsPinPolicy** cmdlet에서 최소 암호 길이를 site:Redmond 정책에 있는 MinPasswordLength 속성의 값으로 설정하게 됩니다. 최종적으로 MinPasswordLength 속성의 값이 기존 정책 site:Redmond에서 새 정책 site:Paris로 복사됩니다.

    $x = Get-CsPinPolicy -Identity "site:Redmond"
    New-CsPinPolicy -Identity "site:Paris" -MinPasswordLength $x.MinPasswordLength 

## 자세한 정보

Lync Server를 사용하면 사용자가 전화를 통해 시스템에 연결하거나 PSTN(공중 전화망) 전화 회의에 참가할 수 있습니다. 사용자는 일반적으로 사용자 이름 또는 암호를 입력하여 시스템에 로그온하거나 전화 회의에 참가하지만 영숫자 키패드가 없는 전화기를 사용하는 경우 사용자 이름 및 암호를 입력하기 어려울 수 있습니다. 따라서 Lync Server는 사용자에게 숫자로만 구성된 PIN을 제공할 수 있도록 지원합니다. PIN을 묻는 메시지가 표시되면 사용자 이름 및 암호 대신 PIN을 입력하여 로그온하거나 전화 회의에 참가할 수 있습니다.

Lync Server에서는 PIN 정책을 사용하여 PIN 인증 속성을 관리합니다. 예를 들어 PIN의 최소 길이를 지정하고 연속된 숫자(예: 123456와 같은 PIN) 등의 "공통 패턴"을 사용하는 PIN의 허용 여부를 결정할 수 있습니다. **New-CsPinPolicy** cmdlet을 사용하면 새 PIN 인증 정책을 만들 수 있습니다. 이러한 새 정책은 사이트 범위나 사용자별 범위에서 구성할 수 있습니다. 전역 PIN 정책도 있습니다. 그러나 전역 PIN 정책을 추가로 또 만들 수는 없습니다. 사용자는 기존 전역 정책을 수정할 수 밖에 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsPinPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsPinPolicy"}

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
<td><p>정책에 할당할 고유 ID를 나타냅니다. PIN 정책은 사이트 범위나 사용자별 범위에서 만들 수 있습니다. 사이트 범위의 정책을 만들려면 -Identity site:Redmond와 유사한 구문을 사용하십시오. 사용자별 범위의 정책을 만들려면 -Identity RedmondPinPolicy와 유사한 구문을 사용하십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowCommonPatterns</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>PIN 번호에 &quot;공통 패턴&quot;이 허용되는지 여부를 지정합니다. 공통 패턴은 반복 숫자(222222), 4번 이상 연속되는 숫자(123456) 및 사용자의 전화 번호 또는 내선 번호와 일치하는 PIN을 포함합니다. True($True)로 설정된 경우 공통 패턴(예: 연속 숫자를 포함하는 PIN 456789)이 허용되고, False($False)로 설정된 경우 공통 패턴이 허용되지 않습니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 PIN 정책에 동반될 설명 텍스트를 제공하는 데 사용됩니다. 예를 들어 정책을 할당할 사용자에 대한 정보를 설명에 포함할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaximumLogonAttempts</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>사용자의 PIN이 자동으로 잠기기 전에 허용되는 연속 로그온 실패 수를 지정합니다. 로그온 실패 수는 로컬 로그온 실패와 전역 로그온 실패의 두 가지 방법으로 계산됩니다. 사용자가 처음 로그온을 시도하면 새로운 30분 관찰 창이 시작되고 이러한 30분 창 중에 실패한 각 로그온은 로컬 로그온 실패 및 전역 로그온 실패로 기록됩니다. 사용자가 이러한 30분 관찰 창 중에 MaximumLogonAttempts에 도달하면 1시간 동안 일시적으로 시스템 액세스가 잠깁니다. 이 기간 동안에는 올바른 PIN을 입력해도 PIN 인증을 사용하여 로그온할 수 없게 됩니다.</p>
<p>잠금 기간이 만료되면 사용자의 로컬 로그온 시도가 0으로 재설정됩니다. 그러나 사용자의 전역 로그온 시도는 재설정되지 않습니다. 사용자가 계속해서 로그온에 실패하면 결국 허용되는 최대 전역 로그온 시도 수에 도달하게 됩니다. 이러한 지점에 도달한 사용자는 시스템에 의해 PIN이 잠기고, 관리자가 PIN의 잠금을 해제할 때까지 PIN 인증을 사용할 수 없게 됩니다.</p>
<p>허용되는 최대 로그온 시도 수는 PIN 크기에 따라 다릅니다. 따라서 Get-CsPinPolicy를 실행하면 MaximumLogonAttempts 속성이 기본값을 표시하지 않습니다. 기본적으로 4자리 PIN은 로컬 로그온 시도 횟수 10번과 전역 로그온 시도 횟수 100번이 허용됩니다. 5자리 PIN은 로컬 로그온 시도 25번과 전역 로그온 시도 1000번이 허용되며, 6자리 이상의 PIN은 로컬 로그온 시도 25번과 전역 로그온 시도 5000번이 허용됩니다. MaximumLogonAttempts 속성 값을 지정하면 허용되는 최대 로컬 로그온 시도 횟수에 해당 값이 사용되지만 전역 로그온 값은 MaximumLogonAttempts에 할당된 값에 관계없이 변경되지 않습니다.</p>
<p>사용자가 PIN 인증을 사용하여 로그온에 성공할 때마다 로컬 실패 로그온 시도 횟수가 0으로 설정됩니다. 전역 로그온 시도 횟수는 관리자가 사용자의 PIN 잠금을 해제할 때만 재설정됩니다.</p>
<p>MaximumLogonAttempts는 1에서 999(포함) 사이의 임의 정수로 설정할 수 있습니다. 그러나 이 속성은 수정하지 않는 것이 좋습니다. 이 속성을 기본값인 null로 설정하면 Lync Server 2013에서는 잠금 정책을 자동으로 계산합니다. 그러면 대개 최고 수준의 보안이 적용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MinPasswordLength</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>PIN에 허용되는 최소 길이, 즉 최소 자릿수입니다. 예를 들어 MinPasswordLength가 8로 설정된 경우 PIN 1259는 4자리밖에 없으므로 거부됩니다. PIN 길이는 4-24자리여야 합니다. 기본값은 5입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PINHistoryCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt64</p></td>
<td><p>사용자가 동일한 PIN을 다시 사용할 수 있는 주기를 지정합니다. 예를 들어 PINHistoryCount가 3으로 설정된 경우 사용자가 처음에 세 번 PIN을 재설정할 때까지는 새 PIN을 사용해야 합니다. 네 번째로 재설정할 때는 첫 번째 PIN을 다시 사용할 수 있습니다. 그리고 다섯 번째로 재설정할 때는 두 번째 PIN을 다시 사용하는 식입니다. PIN 기록 개수는 0-20(포함)의 임의의 정수로 설정할 수 있습니다. 0은 사용자가 동일한 PIN 번호를 계속 반복해서 사용할 수 있음을 의미합니다. 기본적으로 PINHistoryCount는 0로 설정됩니다.</p>
<p>PINLifetime이 0보다 큰 값으로 설정된 경우 PINHistoryCount도 0보다 커야 합니다. 예를 들어 PINLifetime을 30으로 설정하고 PINHistoryCount를 0으로 설정할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PINLifetime</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt64</p></td>
<td><p>PIN이 유효하게 유지되는 시간(일)을 나타냅니다. PIN 수명이 만료된 후에는 사용자가 새 PIN 번호를 선택해야 PIN 인증을 사용하여 시스템에 액세스할 수 있게 됩니다. PINLifetime은 0-999(포함)의 임의의 정수로 설정할 수 있습니다. 0은 PIN 번호가 만료되지 않음을 의미합니다. 기본적으로 PIN 수명은 0일로 설정되어 있습니다.</p>
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

없음. **New-CsPinPolicy** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Policy.UserPin.UserPolicy 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsPinPolicy](get-cspinpolicy.md)  
[Grant-CsPinPolicy](grant-cspinpolicy.md)  
[Remove-CsPinPolicy](remove-cspinpolicy.md)  
[Set-CsPinPolicy](set-cspinpolicy.md)

