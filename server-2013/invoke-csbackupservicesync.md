---
title: Invoke-CsBackupServiceSync
TOCTitle: Invoke-CsBackupServiceSync
ms:assetid: f3de25c2-a1ef-4781-8b33-74f5dc1e6f8d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205374(v=OCS.15)
ms:contentKeyID: 49305517
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Invoke-CsBackupServiceSync

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 풀과 지정된 백업 풀 간의 백업 동기화를 수동으로 호출합니다. 이렇게 하면 관리자가 Lync Server 복제를 기다리지 않고 데이터를 동기화할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Invoke-CsBackupServiceSync -PoolFqdn <Fqdn> [-BackupModule <String>] [-Force <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-cs-001.litwareinc.com 풀에 대해 백업 서비스를 동기화합니다.

    Invoke-CsBackupServiceSync -PoolFqdn "atl-cs-001.litwareinc.com"

## 자세한 정보

관리자는 **Invoke-CsBackupServiceSync** cmdlet을 사용하여 등록자 풀과 해당 백업 풀 간에 데이터를 동기화할 수 있습니다. **Invoke-CsBackupServiceSync** cmdlet은 두 풀을 동기화 상태로 만드는 데 필요한 만큼의 데이터만 복사합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Invoke-CsBackupServiceSync"}

**Lync Server 제어판:** **Invoke-CsBackupServiceSync** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>PoolFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>백업 서비스 동기화를 호출할 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>BackupModule</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>동기화할 데이터의 형식을 나타냅니다. 사용할 수 있는 값은 다음과 같습니다.</p>
<p>* UserServices.PresenceFocus</p>
<p>* ConfServices.DataConf</p>
<p>* CentralMgmt.CMSMaster</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열 값입니다. **Invoke-CsBackupServiceSync** cmdlet은 Lync Server 2013 풀의 정규화된 도메인 이름을 나타내는 파이프라인된 문자열 값을 허용할 수 있습니다.

## 반환 형식

없음

## 참고 항목

#### 기타 리소스

[Backup-CsPool](backup-cspool.md)

