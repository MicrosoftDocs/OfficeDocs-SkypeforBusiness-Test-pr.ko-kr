---
title: Invoke-CsPoolFailOver
TOCTitle: Invoke-CsPoolFailOver
ms:assetid: b5c30438-0553-41f4-b856-68c1ec0deff7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205189(v=OCS.15)
ms:contentKeyID: 49304791
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Invoke-CsPoolFailOver

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 풀에 대한 장애 조치(failover)를 호출합니다. 장애 조치(failover)란 풀에 장애가 발생하여 해당 풀의 현재 사용자가 백업 풀로 로그온될 때 수행되는 프로세스를 지칭합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Invoke-CsPoolFailOver -PoolFqdn <Fqdn> [-Confirm [<SwitchParameter>]] [-DisasterMode <SwitchParameter>] [-FlushStorageService <SwitchParameter>] [-Force <SwitchParameter>] [-WaitTime <TimeSpan>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-cs-001.litwareinc.com 풀에 대해 풀 장애 조치(failover)를 호출합니다.

    Invoke-CsPoolFailOver -PoolFqdn "atl-cs-001.litwareinc.com"

## 예제 2

예제 2에서는 atl-cs-001.litwareinc.com 풀에 대해 재해 모드 장애 조치(failover)를 호출합니다.

    Invoke-CsPoolFailOver -PoolFqdn "atl-cs-001.litwareinc.com" -DisasterMode

## 자세한 정보

관리자는 사용자가 로그온되어 있던 등록자 풀이 갑자기 사용할 수 없는 상태가 되면 풀 장애 조치(failover) 프로세스를 통해 신속하게 서비스를 사용자에게 다시 제공할 수 있습니다. 풀에서 장애가 발생하면 사용자는 Lync Server 2013에서 자동으로 로그오프됩니다. 사용자가 즉시 다시 로그온을 시도하는 경우 지정된 백업 풀로 리디렉션됩니다.

이러한 사용자에게 서비스를 다시 제공하려는 경우 관리자는 현재 사용할 수 없는 풀에 대해 **Invoke-CsPoolFailOver** cmdlet을 실행하면 됩니다. 이렇게 하면 사용자가 지정된 백업 풀을 사용하여 Lync Server에 로그온할 수 있으며 모든 Lync Server 서비스 및 기능에 액세스할 수 있습니다. 이 경우 사용자가 백업 풀로 이동되는 것은 아니며 홈 풀이 복원될 때까지 해당 풀에 로그온하여 풀을 사용하도록 허용될 뿐입니다. 예를 들어 풀 A에 장애가 발생하면 사용자는 풀 A가 복원될 때까지 풀 B(전체 기능 포함)에 로그온할 수 있습니다.

장애가 발생한 풀이 다시 가동 및 실행되면 관리자는 **Invoke-CsPoolFailBack** cmdlet을 실행하여 해당 풀의 사용자를 "장애 복구(failback)"할 수 있습니다. 현재 백업 풀에 로그온되어 있는 사용자는 서비스가 복원된 후 홈 풀로 다시 리디렉션됩니다.

풀 장애 조치(failover)는 장애가 발생한 풀에 백업 풀을 할당한 경우에만 호출할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Invoke-CsPoolFailover"}

**Lync Server 제어판:** **Invoke-CsPoolFailOver** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>장애 조치(failover)되는 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
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
<td><p>이 매개 변수가 있는 경우 장애 조치(failover)가 &quot;재해 모드&quot;에서 수행됨을 나타냅니다. 풀에 더는 액세스할 수 없는 경우 해당 풀의 사용자에게 전체 기능을 다시 제공하는 유일한 방법은 DisasterMode 매개 변수를 사용하여 풀을 장애 조치(failover)하는 것입니다.</p>
<p>이 매개 변수가 없으면 풀이 계속 작동하며 실행 중인 상태이고 관리자가 장애 조치(failover)를 수행하도록 선택했다는 의미입니다. 서버에서 하드웨어 또는 소프트웨어 업그레이드를 수행하기 위해 풀을 일시적으로 장애 조치(failover)한 경우를 예로 들 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>FlushStorageService</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 <strong>Invoke-CsPoolFailOver</strong> cmdlet은 풀의 모든 사용자를 장애 조치(failover)하고 <a href="invoke-csstorageserviceflush.md">Invoke-CsStorageServiceFlush</a> cmdlet을 사용하여 풀의 각 프런트 엔드 서버에 있는 저장소 서비스 데이터베이스를 플러시합니다. 데이터베이스를 플러시할 때는 대기 중인 모든 데이터를 디스크에 쓴 다음 데이터베이스 캐시를 지웁니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WaitTime</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>데이터가 장애 조치(failover)된 풀에서 백업 풀로 동기화되었다고 가정할 때까지 cmdlet이 대기할 시간을 초 단위로 지정합니다.</p></td>
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

없음. **Invoke-CsPoolFailOver** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음.

## 참고 항목

#### 기타 리소스

[Invoke-CsPoolFailBack](invoke-cspoolfailback.md)

