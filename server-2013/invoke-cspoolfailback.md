---
title: Invoke-CsPoolFailBack
TOCTitle: Invoke-CsPoolFailBack
ms:assetid: 4e58d0b5-4353-4de8-b242-2a4553c3371e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204873(v=OCS.15)
ms:contentKeyID: 49303583
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Invoke-CsPoolFailBack

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 풀에 대해 장애 복구(failback) 프로세스를 호출합니다. 장애 복구(failback)는 풀이 장애 조치(failover)되어 해당 풀의 사용자가 백업 풀로 "장애 조치"된 후에 사용됩니다. 즉, 장애가 발생한 풀에 로그온되어 있던 사용자가 자동으로 백업 풀로 로그온됩니다. 장애가 발생한 풀이 복원되면 장애 복구(failback) 프로세스에서 장애 조치(failover)된 사용자를 다시 원래 풀로 로그온시킵니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Invoke-CsPoolFailBack -PoolFqdn <Fqdn> [-Confirm [<SwitchParameter>]] [-DisasterMode <SwitchParameter>] [-Force <SwitchParameter>] [-WaitTime <TimeSpan>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 atl-cs-001.litwareinc.com 풀에 대해 장애 복구(failback)를 호출합니다.

    Invoke-CsPoolFailback -PoolFqdn "atl-cs-001.litwareinc.com"

## 자세한 정보

관리자는 사용자가 로그온되어 있던 등록자 풀이 갑자기 사용할 수 없는 상태가 되면 풀 장애 조치(failover) 프로세스를 통해 신속하게 서비스를 사용자에게 다시 제공할 수 있습니다. 풀에서 장애가 발생하면 사용자는 Lync Server 2013에서 자동으로 로그오프됩니다. 사용자가 즉시 다시 로그온을 시도하는 경우 지정된 백업 풀로 리디렉션됩니다.

이러한 사용자에게 서비스를 다시 제공하려는 경우 관리자는 현재 사용할 수 없는 풀에 대해 **Invoke-CsPoolFailOver** cmdlet을 실행하면 됩니다. 이렇게 하면 사용자가 지정된 백업 풀을 사용하여 Lync Server에 로그온할 수 있으며 모든 Lync Server 서비스 및 기능에 액세스할 수 있습니다. 이 경우 사용자가 백업 풀로 이동되는 것은 아니며 홈 풀이 복원될 때까지 해당 풀에 로그온하여 풀을 사용하도록 허용될 뿐입니다. 예를 들어 풀 A에 장애가 발생하면 사용자는 풀 A가 복원될 때까지 풀 B(전체 기능 포함)에 로그온할 수 있습니다.

장애가 발생한 풀이 다시 가동 및 실행되면 관리자는 **Invoke-CsPoolFailBack** cmdlet을 실행하여 해당 풀의 사용자를 "장애 복구(failback)"할 수 있습니다. 현재 백업 풀에 로그온되어 있는 사용자는 서비스가 복원된 후 홈 풀로 다시 리디렉션됩니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Invoke-CsPoolFailback"}

**Lync Server 제어판:** **Invoke-CsPoolFailback** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>장애 복구(failback)할 풀의 정규화된 도메인 이름입니다(예: -PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;).</p>
<p>장애 복구(failback) 중에 사용되는 풀 FQDN은 장애 조치(failover) 중에 사용되는 FQDN과 같아야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisasterMode</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>현재 백업 풀을 사용할 수 없더라도 관리자가 풀 장애 복구(failback)를 호출할 수 있습니다. 이 매개 변수를 사용하면 백업 풀에 장애 조치(failover)된 사용자가 생성한 데이터가 손실됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WaitTime</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>데이터를 동기화할 때까지 cmdlet이 대기할 최대 시간을 지정합니다. 시간 값은 시간:분:초 형식을 사용하여 표시해야 합니다. 예를 들어 다음 구문은 대기 시간을 1분 30초(00시간:01분:30초)로 설정합니다.</p>
<p>00:01:30</p>
<p>기본값은 15초입니다.</p></td>
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

없음. **Invoke-CsPoolFailBack** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음.

## 참고 항목

#### 기타 리소스

[Invoke-CsPoolFailOver](invoke-cspoolfailover.md)

