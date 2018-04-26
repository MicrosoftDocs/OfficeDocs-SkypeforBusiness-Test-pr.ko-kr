---
title: Remove-CsBackupServiceConfiguration
TOCTitle: Remove-CsBackupServiceConfiguration
ms:assetid: 56bbf0a2-20cf-4f1e-b305-3521659eb909
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204903(v=OCS.15)
ms:contentKeyID: 49303690
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsBackupServiceConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013의 백업 서비스 구성 설정 속성을 기본값으로 다시 설정합니다. 이러한 설정에는 백업 서비스에 대해 동시에 수행할 수 있는 Windows Communication Framework 호출의 최대 수와 백업 서비스 동기화 간격에 대한 정보가 포함됩니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsBackupServiceConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Lync Server 2013의 백업 서비스 구성 설정을 다시 설정합니다. Lync Server 2013에서는 백업 설정의 전역 컬렉션을 하나만 사용하지만, Identity 매개 변수를 포함해야 합니다. 그렇지 않으면 **Remove-CsBackupServiceConfiguration** cmdlet 실행 시 계속하려면 Identity를 지정하라는 메시지가 표시됩니다.

    Remove-CsBackupServiceConfiguration -Identity "global"

## 자세한 정보

백업 서비스 구성 설정은 Lync Server 2013에서 풀 백업을 관리하는 데 사용됩니다. Lync Server에서는 백업 구성 설정의 전역 컬렉션을 하나만 사용할 수 있습니다. 즉, 모든 풀을 같은 동기화 일정으로 백업해야 하며 풀 A 백업 권한이 부여된 사용자와 그룹은 풀 B, C, D, E도 백업할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsBackupServiceConfiguration"}

**Lync Server 제어판:** **Remove-CsBackupServiceConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>백업 서비스 구성 설정의 고유 ID입니다. 이러한 설정에 대해 전역 인스턴스를 하나만 사용할 수 있기는 하지만, <strong>Remove-CsBackupServiceConfiguration</strong> cmdlet을 호출할 때 다음과 같이 Identity를 지정해야 합니다.</p>
<p>-Identity global</p></td>
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

**Remove-CsBackupServiceConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.BackupService.BackupServiceConfiguration 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsBackupServiceConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.BackupService.BackupServiceConfiguration 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsBackupServiceConfiguration](get-csbackupserviceconfiguration.md)  
[Set-CsBackupServiceConfiguration](set-csbackupserviceconfiguration.md)

