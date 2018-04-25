---
title: Remove-CsUCPhoneConfiguration
TOCTitle: Remove-CsUCPhoneConfiguration
ms:assetid: 1b2d9601-3206-48d9-a846-4486b606aad0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398249(v=OCS.15)
ms:contentKeyID: 49302967
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsUCPhoneConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 Lync Phone Edition 구성 설정 컬렉션을 제거합니다. 이러한 설정에는 필요한 보안 모드, 지정한 기간 동안 사용하지 않을 경우 전화를 자동으로 잠글지 여부 등이 포함됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsUCPhoneConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트(-Identity site:Redmond)에 대한 UC 전화 구성 설정을 제거합니다. 사이트 범위에서 설정을 제거하면 해당 사이트에 포함된 사용자의 UC 전화가 전역 전화 구성 설정으로 제어됩니다.

    Remove-CsUCPhoneConfiguration -Identity site:Redmond

## 예제 2

예제 2에서는 사이트 범위에서 구성된 모든 UC 전화 설정을 제거합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsUCPhoneConfiguration** cmdlet 및 Filter 매개 변수를 사용하여 사이트 범위에서 구성된 모든 설정을 반환합니다. 필터 값 "site:\*"는 Identity 속성(필터링할 수 있는 유일한 속성)이 문자열 값 "site:"으로 시작하는 설정에 대한 데이터만 반환되도록 제한합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsUCPhoneConfiguration** cmdlet에 파이프됩니다.

    Get-CsUCPhoneConfiguration -Filter site:* | Remove-CsUCPhoneConfiguration

## 예제 3

예제 3에서는 전화 잠금을 적용하지 않는 모든 UC 전화 설정을 제거합니다. 이 작업을 수행하기 위해 이 명령은 먼저 매개 변수 없이 **Get-CsUCPhoneConfiguration** cmdlet을 사용하여 먼저 조직에서 현재 사용 중인 모든 UC 전화 설정 컬렉션을 반환합니다. 이 컬렉션은 EnforceLockProperty가 False와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 제거하는 **Remove-CsUCPhoneConfiguration** cmdlet에 파이프됩니다.

    Get-CsUCPhoneConfiguration | Where-Object {$_.EnforcePhoneLock -eq $False} | Remove-CsUCPhoneConfiguration

## 예제 4

예제 4에서는 SIP 보안 모드가 Low 또는 Medium으로 설정된 모든 UC 전화 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 먼저 **Get-CsUCPhoneConfiguration** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 UC 전화 설정 컬렉션을 반환합니다. 이 컬렉션은 SIPSecurityMode가 High와 같지 않은 설정만 선택하는 방식으로 SIPSecurityMode 속성이 Low 또는 Medium으로 설정된 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. SIPSecurityMode에 사용 가능한 값은 Low, Medium 및 High입니다. 그런 다음 필터링된 컬렉션은 SIPSecurityMode가 High와 같지 않은 모든 설정을 삭제하는 **Remove-CsUCPhoneConfiguration** cmdlet에 파이프됩니다.

    Get-CsUCPhoneConfiguration | Where-Object {$_.SIPSecurityMode -ne "High"} | Remove-CsUCPhoneConfiguration

## 자세한 정보

Lync Phone Edition은 전화와 Lync Server의 병합을 나타냅니다. Lync Phone Edition은 VoIP(Voice over Internet Protocol) 전화로 작동할 수 있는 특정 하드웨어(즉, Lync 호환 전화)를 사용합니다. 또한 이 하드웨어는 Lync와 같은 끝점 역할을 할 수도 있습니다. 현재 상태를 설정하고, Lync 대화 상대의 상태를 확인하고, 새 대화 상대를 검색하고, Lync를 사용하여 수행하던 기타 여러 작업을 수행할 수 있습니다.

Lync Server에는 Lync Phone Edition을 실행하는 전화를 관리하는 데 사용할 수 있는 다양한 cmdlet이 제공됩니다. 예를 들어 전화에 로그온하는 데 사용되는 개인식별번호(PIN)의 최소 길이 및 전화가 지정된 시간 동안 비활성 상태일 경우 자동으로 잠글지 여부 등을 제어할 수 있습니다.

UC(Unified Communications) 전화 구성 설정은 전역 범위 또는 사이트 범위에 적용할 수 있습니다. 사이트 범위에서 적용된 설정이 전역 범위에서 적용된 설정보다 우선합니다. Lync Server를 처음 설치하면 단일 UC 전화 구성 설정 집합이 생성되어 전역 범위에 적용됩니다. 그러나 이후에 언제든지 **New-CsUCPhoneConfiguration** cmdlet을 사용하여 사이트 범위에서 적용된 설정 컬렉션을 만들 수 있습니다. 이렇게 하면 각 개별 사이트의 고유한 요구 사항에 맞게 UC 전화 관리를 조정할 수 있습니다.

**New-CsUCPhoneConfiguration** cmdlet을 사용하여 만든 설정은 나중에 **Remove-CsUCPhoneConfiguration** cmdlet을 사용하여 제거할 수 있습니다. 사이트에서 설정을 제거하면 해당 사이트에서 Lync Phone Edition을 실행하는 전화가 관리되지 않는 상태로 유지되는 것이 아니라 해당 전화에 자동으로 전역 설정이 적용됩니다.

전역 설정에 대해 **Remove-CsUCPhoneConfiguration** cmdlet을 실행할 수도 있습니다. 하지만 이 경우에는 전역 설정이 실제로 제거되지 않습니다. 전역 UC 전화 설정은 제거할 수 없습니다. 대신, 전역 설정의 속성이 기본값으로 다시 설정됩니다. 예를 들어 전화 잠금 시간 간격을 30분으로 변경한 경우 전역 설정을 "제거"하면 간격이 기본값인 10분으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsUCPhoneConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsUCPhoneConfiguration"}

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
<td><p>제거할 UC 전화 구성 설정 컬렉션의 고유 식별자입니다. 사이트 컬렉션을 제거하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. 전역 컬렉션을 제거(다시 설정)하려면 -Identity global 구문을 사용합니다. 정책 ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.UcPhoneSettings 개체입니다. **Remove-CsUCPhoneConfiguration** cmdlet은 UC 전화 설정 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.UcPhoneSettings 개체의 인스턴스를 제거합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUCPhoneConfiguration](get-csucphoneconfiguration.md)  
[New-CsUCPhoneConfiguration](new-csucphoneconfiguration.md)  
[Set-CsUCPhoneConfiguration](set-csucphoneconfiguration.md)

