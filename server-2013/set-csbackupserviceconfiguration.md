---
title: Set-CsBackupServiceConfiguration
TOCTitle: Set-CsBackupServiceConfiguration
ms:assetid: 72ed064e-5f67-481f-802a-74846cecb189
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205006(v=OCS.15)
ms:contentKeyID: 49304019
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsBackupServiceConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013의 백업 서비스 구성 설정을 검색합니다. 이러한 설정에는 백업 서비스에 대해 동시에 수행할 수 있는 Windows Communication Framework 호출의 최대 수와 백업 서비스 동기화 간격에 대한 정보가 포함됩니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsBackupServiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsBackupServiceConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AuthorizedLocalAccounts <String>] [-AuthorizedUniversalGroups <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-MaxBatchesPerCmsSync <Int32>] [-MaxBatchesPerUserStoreSync <Int32>] [-MaxConcurrentCalls <Int32>] [-MaxDataConfPackageSizeKB <Int32>] [-SyncInterval <TimeSpan>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Active Directory 보안 그룹 Schema Admins를 백업 서비스 설정의 전역 컬렉션에 대한 AuthorizedUniversalGroup 속성에 할당합니다.

    Set-CsBackupServiceConfiguration -Identity "global" -AuthorizedUniversalGroup "Schema Admins"

## 예제 2

예제 2에서는 백업 서비스 설정 전역 컬렉션의 MaxConcurrentCalls 속성을 12로 설정합니다.

    Set-CsBackupServiceConfiguration -Identity "global" -MaxConcurrentCalls 12

## 예제 3

예제 3에서는 백업 서비스 설정 전역 컬렉션의 SyncInterval 속성을 수정합니다. 이 예제에서는 SyncInterval을 10분(00시간:10분:00초)으로 설정합니다.

    Set-CsBackupServiceConfiguration -Identity "global" -SyncInterval "00:10:00"

## 자세한 정보

백업 서비스 구성 설정은 Lync Server 2013에서 풀 백업을 관리하는 데 사용됩니다. Lync Server에서는 백업 구성 설정의 전역 컬렉션을 하나만 사용할 수 있습니다. 즉, 모든 풀을 같은 동기화 일정으로 백업해야 하며 풀 A 백업 권한이 부여된 사용자와 그룹은 풀 B, C, D, E도 백업할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsBackupServiceConfiguration"}

**Lync Server 제어판:** **Set-CsBackupServiceConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>AuthorizedLocalAccounts</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>백업 서비스 실행 권한이 부여된 로컬 사용자/로컬 그룹의 이름입니다. 기본값은 Network Service입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AuthorizedUniversalGroups</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>백업 서비스 실행 권한이 부여된 유니버설 그룹의 이름입니다. 기본값은 Schema admins입니다.</p></td>
</tr>
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
<td><p>백업 서비스 구성 설정의 고유 식별자입니다. 이러한 설정에 대해서는 전역 인스턴스를 하나만 사용할 수 있으므로 <strong>Set-CsBackupServiceConfiguration</strong> cmdlet을 호출할 때 ID를 지정할 필요가 없습니다. 그러나 원하는 경우에는 다음 구문을 사용하여 전역 설정을 참조할 수 있습니다.</p>
<p>-Identity global</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxBatchesPerCmsSync</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>CMS 백업 모듈이 각 내보내기 주기 동안 내보내는 최대 배치 수입니다. 기본값은 500입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxBatchesPerUserStoreSync</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>사용자 저장소 백업 모듈이 각 내보내기 주기 동안 내보내는 최대 배치 수입니다. 기본값은 500입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxConcurrentCalls</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>백업 서비스에 대해 동시에 수행할 수 있는 WCF(Windows Communication Foundation) 호출의 최대 수입니다. 기본값은 10입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxDataConfPackageSizeKB</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>데이터 회의 모듈이 각 내보내기 주기 동안 내보내는 데이터 패키지의 최대 크기(KB)입니다. 기본값은 102400입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SyncInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>풀을 해당 백업 풀과 동기화할 때까지 서비스가 대기하는 시간을 지정합니다. 기본값은 2분(00:02:00 또는 00시간 02분 00초)입니다. SyncInterval은 5초(00:00:05)에서 3시간(03:00:00)(포함) 사이의 값으로 구성할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>실제로 명령을 수행하지는 않고 명령을 실행했을 때 발생할 결과에 대해 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Set-CsBackupServiceConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.BackupService.BackupServiceConfiguration 개체의 파이프된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsBackupServiceConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.BackupService.BackupServiceConfiguration 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsBackupServiceConfiguration](get-csbackupserviceconfiguration.md)  
[Remove-CsBackupServiceConfiguration](remove-csbackupserviceconfiguration.md)

