---
title: Remove-CsMeetingConfiguration
TOCTitle: Remove-CsMeetingConfiguration
ms:assetid: a5d4c758-25f6-4cdb-a5b7-dbb0fb1d8488
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412775(v=OCS.15)
ms:contentKeyID: 49304615
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsMeetingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

**Remove-CsMeetingConfiguration** cmdlet을 사용하면 모임 구성 설정의 기존 컬렉션을 삭제할 수 있습니다. 모임 구성 설정은 사용자가 만들 수 있는 모임 유형을 지정할 뿐만 아니라 익명 사용자 및 전화 접속 회의 사용자가 이러한 모임에 참가하는 방법까지도 제어하도록 지원합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsMeetingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 site:Redmond인 모임 구성 설정을 제거합니다. 이러한 설정이 Redmond 사이트에서 제거되면 해당 사이트의 사용자가 전역 모임 구성 설정을 자동으로 상속하게 됩니다.

    Remove-CsMeetingConfiguration -Identity site:Redmond

## 예제 2

예제 2에 표시된 명령은 사이트 범위에 구성된 모든 모임 설정을 제거합니다. 이 작업을 수행하기 위해 먼저 Filter 매개 변수와 함께 **Get-CsMeetingConfiguration** cmdlet을 호출합니다. 필터 값 "site:\*"는 ID가 "site:" 문자로 시작하는 설정만 선택되도록 합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsMeetingConfiguration** cmdlet에 파이프됩니다.

    Get-CsMeetingConfiguration -Filter "site:*" | Remove-CsMeetingConfiguration

## 예제 3

예제 3에서는 AdmitAnonymousUsersbyDefault 속성이 True인 모임 구성 설정의 각 컬렉션을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 현재 사용 중인 모든 모임 구성 설정 컬렉션을 반환하는 **Get-CsMeetingConfiguration** cmdlet을 호출합니다. 이 컬렉션은 AdmitAnonymousUsersByDefault 속성이 True와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 해당 컬렉션의 각 항목을 제거하는 **Remove-CsMeetingConfiguration** cmdlet에 파이프됩니다.

    Get-CsMeetingConfiguration | Where-Object {$_.AdmitAnonymousUsersByDefault -eq $True} | Remove-CsMeetingConfiguration

## 자세한 정보

온라인 모임(전화 회의라고도 함)은 Lync Server의 필수적인 부분입니다. **CsMeetingConfiguration** cmdlet을 통해 관리자는 사용자가 만들 수 있는 모임 유형을 제어할 뿐만 아니라 모임에서 익명 사용자 및 전화 접속 회의 사용자를 처리하는 방법도 결정할 수 있습니다. 예를 들어 PSTN(공중 전화망)을 통해 전화 접속한 사용자가 모임에 자동으로 입장하도록 모임을 구성할 수 있습니다. 또는 전화 접속 사용자가 모임에 자동으로 입장하지는 않지만 대신 모임 대기실로 경로 지정되도록 모임을 구성할 수 있습니다. 이러한 전화 접속 사용자는 발표자가 모임에 입장하도록 허용할 때까지 대기실에서 대기 상태로 유지됩니다.

모임 구성 설정은 전역, 사이트 또는 서비스 범위에 할당할 수 있습니다. 사이트 또는 서비스 범위에서 새 설정을 만든 경우 나중에 **Remove-CsMeetingConfiguration** cmdlet을 사용하여 이러한 설정을 제거할 수 있습니다. 전역 모임 설정에 대해 **Remove-CsMeetingConfiguration** cmdlet을 실행할 수도 있습니다. 그러나 전역 설정은 제거할 수 없으므로 이 경우 설정이 제거되지 않습니다. 대신 전역 컬렉션의 모든 속성이 기본값으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsMeetingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsMeetingConfiguration"}

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
<td><p>제거할 모임 구성 설정의 고유 식별자입니다. 전역 설정을 &quot;제거&quot;하려면 -Identity global 구문을 사용합니다. 앞서 말했듯이 전역 설정은 실제로 제거할 수 없습니다. 속성을 기본값으로 다시 설정할 수만 있습니다. 사이트 범위에서 설정을 제거하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 서비스 설정을 제거하려면 -Identity service:UserServer:atl-cs-001.litwareinc.com 구문을 사용합니다.</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
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
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>삭제할 모임 구성 설정에 대한 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.MeetingConfiguration 개체입니다. **Remove-CsMeetingConfiguration** cmdlet은 모임 구성 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsMeetingConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.MeetingConfiguration 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsMeetingConfiguration](get-csmeetingconfiguration.md)  
[New-CsMeetingConfiguration](new-csmeetingconfiguration.md)  
[Set-CsMeetingConfiguration](set-csmeetingconfiguration.md)

