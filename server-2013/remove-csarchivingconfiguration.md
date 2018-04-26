---
title: Remove-CsArchivingConfiguration
TOCTitle: Remove-CsArchivingConfiguration
ms:assetid: d83b8935-079e-47d0-ba48-c95dd07965c0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398951(v=OCS.15)
ms:contentKeyID: 49305215
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsArchivingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 보관 설정 컬렉션을 제거합니다. 보관 설정은 메신저 대화 세션의 자동 저장을 설정 또는 해제하고 보관할 수 없는 메신저 대화를 선택적으로 차단하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsArchivingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Remove-CsArchivingConfiguration** cmdlet을 사용하여 ID가 site:Redmond인 보관 구성 설정을 삭제합니다.

    Remove-CsArchivingConfiguration -Identity site:Redmond

## 예제 2

예제 2에 표시된 명령은 사이트 범위에서 구성된 모든 보관 구성 설정을 제거합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsArchivingConfiguration** cmdlet 및 Filter 매개 변수를 사용하여 사이트 범위에서 구성된 모든 설정 컬렉션을 반환합니다. 이때 반환되는 데이터를 ID가 "site:" 문자로 시작하는 설정으로 제한하기 위해 필터 값 "site:\*"를 사용합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsArchivingConfiguration** cmdlet에 파이프됩니다.

    Get-CsArchivingConfiguration -Filter "site:*" | Remove-CsArchivingConfiguration

## 예제 3

예제 3에서는 EnableArchiving 속성이 "None"으로 설정된 모든 보관 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 추가 매개 변수 없이 **Get-CsArchivingConfiguration** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 보관 설정 컬렉션을 반환합니다. 이 컬렉션은 EnableArchiving 속성이 "None"과 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsArchivingConfiguration** cmdlet에 파이프됩니다.

    Get-CsArchivingConfiguration | Where-Object {$_.EnableArchiving -eq "None"} | Remove-CsArchivingConfiguration

## 자세한 정보

대부분의 조직에서는 조직의 사용자가 참가하는 모든 메신저 대화 세션 및 전화 회의의 대화 내용을 보관하는 것이 유용하다는 것을 인지하고 있습니다. 다른 조직의 경우 그러한 대화 내용을 보관하는 것이 의무이기도 합니다. 예를 들어 법에 따라 모든 전자 통신의 복사본을 보관해야 하는 금융 분야의 조직 대부분이 이에 해당합니다.

Lync Server에서는 메신저 대화 및 웹 회의 세션 보관과 관련된 유연한 기능을 제공합니다. 보관 서버를 배포한 경우 여러 가지 **CsArchivingConfiguration** cmdlet을 사용하여 메신저 대화 세션 보관을 설정 및 해제하고 보관 데이터베이스를 관리할 수 있습니다. 또한 보관에 실패한 경우 메신저 대화를 일시 중단하여 모든 전자 통신의 레코드를 유지할 수 있습니다.

Lync Server를 설치하면 전역 보관 설정의 컬렉션이 만들어집니다. 이러한 설정은 기본적으로 전체 조직에 적용됩니다. 또는 **New-CsArchivingConfiguration** cmdlet을 사용하여 사이트별로 사용자 지정 구성 설정을 만들 수 있습니다. **New-CsArchivingConfiguration** cmdlet을 사용하여 만든 사이트별 설정은 나중에 **Remove-CsArchivingConfiguration** cmdlet을 사용하여 제거할 수 있습니다. 사이트에 대한 설정을 제거하면 영향을 받는 사이트에 전역 설정이 적용됩니다.

전역 보관 설정에 대해 **Remove-CsArchivingConfiguration** cmdlet을 실행할 수도 있습니다. 그러나 전역 설정은 삭제할 수 없으므로 이 경우 설정이 제거되지 않습니다. 대신 모든 전역 속성이 기본값으로 다시 설정됩니다. 예를 들어 전역 범위에서 메신저 대화 세션 보관을 설정하고 나중에 다음 명령을 실행하는 경우를 가정해 보겠습니다.

Remove-CsArchivingConfiguration -Identity global

이 명령을 실행하면 전역 설정의 속성 값이 다시 설정됩니다. 즉, EnableArchiving이 기본값 None으로 돌아갑니다. 그러면 전역 범위에서 보관이 해제됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsArchivingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsArchivingConfiguration"}

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
<td><p>제거할 보관 구성 설정 컬렉션의 고유 식별자입니다. 전역 컬렉션을 제거하려면 -Identity global 구문을 사용하십시오. 전역 설정은 실제로 제거할 수 없습니다. 속성을 기본값으로 다시 설정할 수만 있습니다. 사이트 컬렉션을 제거하려면 -Identity site:Redmond와 유사한 구문을 사용하십시오. 개별 등록자 풀에 대해 구성된 설정을 제거하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;service:Registrar:atl-cs-001.litwareinc.com&quot;</p>
<p>풀 수준 설정은 Lync Server 2013에서만 사용할 수 있습니다.</p>
<p>정책 ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Archiving.ArchivingSettings 개체입니다. **Remove-CsArchivingConfiguration** cmdlet은 보관 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Remove-CsArchivingConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Archiving.ArchivingSettings 개체의 인스턴스를 제거합니다.

## 참고 항목

#### 기타 리소스

[Get-CsArchivingConfiguration](get-csarchivingconfiguration.md)  
[New-CsArchivingConfiguration](new-csarchivingconfiguration.md)  
[Set-CsArchivingConfiguration](set-csarchivingconfiguration.md)  
[Set-CsArchivingServer](set-csarchivingserver.md)

