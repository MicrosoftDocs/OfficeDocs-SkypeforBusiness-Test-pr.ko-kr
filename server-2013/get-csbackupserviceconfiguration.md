---
title: Get-CsBackupServiceConfiguration
TOCTitle: Get-CsBackupServiceConfiguration
ms:assetid: 8e81a76c-4019-490d-9cd5-895cc2cc0863
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205087(v=OCS.15)
ms:contentKeyID: 49304341
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsBackupServiceConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013의 백업 서비스 구성 설정을 검색합니다. 이러한 설정에는 백업 서비스에 대해 동시에 수행할 수 있는 Windows Communication Framework 호출의 최대 수와 백업 서비스 동기화 간격에 대한 정보가 포함됩니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsBackupServiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsBackupServiceConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 Lync Server 2013에 대한 백업 서비스 구성 정보를 검색합니다. 백업 서비스 구성 설정의 전역 집합은 하나뿐이므로 이 명령을 실행할 때는 Identity 매개 변수를 포함하지 않아도 됩니다.

    Get-CsBackupServiceConfiguration

## 자세한 정보

백업 서비스 구성 설정은 Lync Server 2013에서 풀 백업을 관리하는 데 사용됩니다. Lync Server에서는 백업 구성 설정의 전역 컬렉션을 하나만 사용할 수 있습니다. 즉, 모든 풀을 같은 동기화 일정으로 백업해야 하며 풀 A 백업 권한이 부여된 사용자와 그룹은 풀 B, C, D, E도 백업할 수 있습니다.

Get-CsBackupServiceConfiguration은 Lync Server 2013 서버 역할을 실행하는 모든 컴퓨터나 Windows PowerShell의 원격 인스턴스에서 실행될 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsBackupServiceConfiguration"}

**Lync Server 제어판:** **Get-CsBackupServiceConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>백업 서비스 구성 설정의 컬렉션을 참조할 때 와일드카드 값을 사용할 수 있습니다. 이러한 설정에 대해서는 전역 인스턴스를 하나만 사용할 수 있으므로 Filter 매개 변수는 사용할 필요가 없습니다. 그러나 원하는 경우 다음 구문을 사용하여 전역 설정을 참조할 수 있습니다.</p>
<p>-Filter &quot;g*&quot;</p>
<p>이 구문은 ID가 &quot;g&quot; 문자로 시작되는 모든 전화 회의 백업 서비스 구성 설정을 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>백업 서비스 구성 설정의 고유한 ID입니다. 이러한 설정에 대해서는 전역 인스턴스를 하나만 사용할 수 있으므로 <strong>Get-CsBackupServiceConfiguration</strong> cmdlet을 호출할 때 ID는 지정할 필요가 없습니다. 그러나 다음 구문을 사용하여 전역 설정을 참조할 수 있습니다.</p>
<p>-Identity global</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 백업 서비스 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsBackupServiceConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsBackupServiceConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.BackupService.BackupServiceConfiguration 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsBackupServiceConfiguration](remove-csbackupserviceconfiguration.md)  
[Set-CsBackupServiceConfiguration](set-csbackupserviceconfiguration.md)

