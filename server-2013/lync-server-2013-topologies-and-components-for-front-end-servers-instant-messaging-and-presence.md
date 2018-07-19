---
title: 'Lync Server 2013: 프런트 엔드 서버, 메신저 및 현재 상태에 대한 토폴로지 및 구성 요소'
TOCTitle: 프런트 엔드 서버, 메신저 및 현재 상태에 대한 토폴로지 및 구성 요소
ms:assetid: f08ce7a1-d14e-4a54-9771-a82c870658bf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412996(v=OCS.15)
ms:contentKeyID: 49305476
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 의 프런트 엔드 서버, 메신저 및 현재 상태에 대한 토폴로지 및 구성 요소

 

_**마지막으로 수정된 항목:** 2015-05-04_

IM(메신저 대화) 및 현재 상태에 필요한 구성 요소는 다음과 같습니다.

  - 조직의 프런트 엔드 서버나 Standard Edition Server. IM 및 현재 상태 기능은 이 서버에서 항상 사용하도록 설정되어 있습니다.

  - 부하 분산(Enterprise Edition프런트 엔드 풀이 있는 경우). 자세한 내용은 [Lync Server 2013의 부하 분산 요구 사항](lync-server-2013-load-balancing-requirements.md)을 참조하세요.

## 프런트 엔드 풀 배포 계획

Lync Server 2013에서는 프런트 엔드 풀 아키텍처가 변경되었으며 이러한 변경은 프런트 엔드 풀을 계획하고 유지 관리하는 방식에 영향을 줍니다.

모든 Enterprise Edition프런트 엔드 풀에는 세 개 이상의 프런트 엔드 서버를 포함하는 것이 좋습니다. Lync Server에서 프런트 엔드 풀의 아키텍처에 분산 시스템 모델이 사용되어 풀의 세 프런트 엔드 서버에 각 사용자의 데이터가 유지됩니다. 이 새로운 아키텍처에 대한 자세한 내용은 [Lync Server 2013의 토폴로지 변경 내용](lync-server-2013-topology-changes.md)을 참조하세요.

세 Enterprise Edition프런트 엔드 서버을 배포하지 않으면서 재배 복구 기능을 원하는 경우 Lync ServerStandard Edition을 사용하고 연결된 백업 관계가 설정된 두 풀을 만드는 것이 좋습니다. 이렇게 하면 두 서버만으로 재해 복구 솔루션을 얻게 됩니다. 고가용성 및 재해 복구 토폴로지 및 기능에 대한 자세한 내용은 [Lync Server 2013의 고가용성 및 재해 복구 계획](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md)을 참조하세요.

## 프런트 엔드 풀 관리 계획

프런트 엔드 풀의 경우 이 섹션의 지침을 따르세요.

## 해당 풀의 작동 보장

프런트 엔드 풀의 새 분산 모델을 사용할 경우 풀이 작동하려면 풀의 서버 중 특정 수가 실행되어야 합니다. 풀에는 두 개의 손실 모드가 있습니다.

  - 특정 라우팅 그룹에 대한 복제본 서버의 부족에서 기인한 라우팅 그룹 수준 쿼럼 손실. 라우팅 그룹은 풀에 있는 사용자 집합입니다. 라우팅 그룹마다 풀에 세 개의 복제본이 있습니다. 하나는 기본 복제본이고 나머지 두 개는 보조 복제본입니다.

  - 풀에서 실행 중인 시드 서버가 부족하기 때문에 발생하는 풀 수준 쿼럼 손실

## 라우팅 그룹 수준 쿼럼 손실

새 프런트 엔드 풀을 처음 시작할 때 다음 표에서와 같이 85%의 서버가 반드시 실행 중이어야 합니다. 실행 중인 서버의 수가 이보다 적으면 서비스가 시작 상태로 정지되고 풀이 시작되지 않을 수 있습니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>풀에 있는 서버의 총 수</th>
<th>처음에 풀을 시작하기 위해 실행 중이어야 하는 서버의 개수</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2</p></td>
<td><p>1</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>3</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>3</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>4</p></td>
</tr>
<tr class="odd">
<td><p>6</p></td>
<td><p>5</p></td>
</tr>
<tr class="even">
<td><p>7</p></td>
<td><p>5</p></td>
</tr>
<tr class="odd">
<td><p>8</p></td>
<td><p>6</p></td>
</tr>
<tr class="even">
<td><p>9</p></td>
<td><p>7</p></td>
</tr>
<tr class="odd">
<td><p>10</p></td>
<td><p>8</p></td>
</tr>
<tr class="even">
<td><p>11</p></td>
<td><p>9</p></td>
</tr>
<tr class="odd">
<td><p>12</p></td>
<td><p>10</p></td>
</tr>
</tbody>
</table>


이후에 풀을 시작할 때마다 위 표에서와 같이 85%의 서버가 시작되어야 합니다. 풀 수준 쿼럼 손실에 해당하지 않을 정도로 충분한 서버가 시작될 수 있지만 이 수만큼 서버를 시작할 수 없는 경우 **Reset-CsPoolRegistrarState –ResetType QuorumLossRecovery** cmdlet을 사용하여 이 풀이 라우팅 그룹 수준 쿼럼 손실에서 복구되도록 설정하고 계속 진행할 수 있습니다. 이 cmdlet을 사용하는 방법에 대한 자세한 내용은 [Reset-CsPoolRegistrarState](https://docs.microsoft.com/en-us/powershell/module/skype/Reset-CsPoolRegistrarState)를 참조하세요.


> [!NOTE]
> Lync Server에서는 기본 SQL 데이터베이스를 미러링 모니터 서버로 사용하므로, 기본 데이터베이스를 종료하고 미러 복사본으로 전환한 후 위 표에 따라 충분한 프런트 엔드 서버을 종료하여 부족한 수를 실행하면 전체 풀이 중지됩니다. 자세한 내용은 <A href="http://go.microsoft.com/fwlink/?linkid=393672">데이터베이스 미러링 모니터 서버</A>를 참조하세요.



## 풀 수준 쿼럼 손실

프런트 엔드 풀이 제대로 작동하려면 풀 수준 쿼럼 손실 상태에 있어서는 안 됩니다. 실행 중인 서버의 수가 다음 표에 나와 있는 작동 수준에 미치지 못하면 풀에 있는 나머지 서버가 모든 Lync Server 서비스를 중지합니다. 다음 표에 나와 있는 숫자는 풀의 백 엔드 서버가 실행 중인 것으로 가정합니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>풀의 총 프런트 엔드 서버 수</th>
<th>풀이 작동하기 위해 실행 중이어야 하는 서버 수</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2</p></td>
<td><p>1</p></td>
</tr>
<tr class="even">
<td><p>3-4</p></td>
<td><p>2</p></td>
</tr>
<tr class="odd">
<td><p>5-6</p></td>
<td><p>3</p></td>
</tr>
<tr class="even">
<td><p>7</p></td>
<td><p>4</p></td>
</tr>
<tr class="odd">
<td><p>8-9</p></td>
<td><p>처음 7개 서버 중 4개</p></td>
</tr>
<tr class="even">
<td><p>10-12</p></td>
<td><p>처음 9개 서버 중 5개</p></td>
</tr>
</tbody>
</table>


위 표에서 "첫 번째 서버"는 풀을 처음 시작했을 때 날짜순으로 가장 먼저 표시된 서버를 말합니다. 이러한 서버를 확인하기 위해 **Get-CsComputer** cmdlet과 함께 **–PoolFqdn** 옵션을 사용할 수 있습니다. 이 cmdlet은 서버를 토폴로지에 나타나는 순서대로 표시하며, 목록 맨 위에 있는 서버가 첫 번째 서버입니다.

## 두 프런트 엔드 서버로 구성된 프런트 엔드 풀

두 프런트 엔드 서버만 포함하는 프런트 엔드 풀을 배포하는 것은 바람직하지 않습니다. 하지만 어쩔 수 없이 이러한 풀을 배포해야 하는 경우에는 다음 지침을 따르세요.

  - 두 프런트 엔드 서버 중 하나의 작동이 중단된 경우 실패한 서버를 가능한 빨리 가동 상태로 복구해야 합니다. 마찬가지로 두 서버 중 하나를 업그레이드해야 하는 경우 업그레이드를 완료하자 마자 온라인 상태로 되돌려야 합니다.

  - 어떤 이유로든 동시에 두 서버의 작동을 중단해야 하는 경우에는 풀의 중단 시간이 끝나자 마자 다음을 수행합니다.
    
      - 가장 좋은 방법은 두 프런트 엔드 서버를 동시에 다시 시작하는 것입니다.
    
      - 두 서버를 동시에 다시 시작할 수 없으면 작동이 중단된 순서의 역순으로 복구해야 합니다.
    
      - 이 순서대로 복구할 수 없으면 풀을 복구하기 전에 다음 cmdlet을 사용합니다.
        
            Reset-CsPoolRegistrarState -ResetType QuorumLossRecovery -PoolFQDN <FQDN>

## 풀 작동을 보장하기 위한 추가 단계

프런트 엔드 풀이 계속해서 작동하도록 하기 위해 몇 가지 다른 요소를 살펴보아야 합니다.

  - 처음으로 사용자를 풀로 이동할 때는 프런트 엔드 서버 중 세 개 이상이 실행 중이어야 합니다.

  - 재해 복구 용도로 이 풀과 다른 풀 간 연결 관계를 설정하는 경우 해당 관계를 설정한 후 데이터를 백업 풀과 올바르게 동기화하려면 어느 시점에는 세 프런트 엔드 서버가 동시에 실행 중이어야 합니다. 풀 연결과 재해 복구 기능에 대한 자세한 내용은 [Lync Server 2013의 고가용성 및 재해 복구 계획](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md)을 참조하세요.

## 풀 업그레이드의 안정성 개선

프런트 엔드 풀에서 서버를 업그레이드하거나 패치해야 할 경우 [Lync Server 2013에서 프런트 엔드 서버 업그레이드 또는 업데이트](lync-server-2013-upgrade-or-update-front-end-servers.md)에 나와 있는 워크플로와 다음 지침을 따르세요.

  - 업그레이드를 위해 [Lync Server 2013에서 프런트 엔드 서버 업그레이드 또는 업데이트](lync-server-2013-upgrade-or-update-front-end-servers.md)의 워크플로를 따라 업그레이드 도메인 사이를 이동할 때 **Get-CsPoolUpgradeReadinessState** cmdlet을 사용하고 준비 상태인지 확인해야 합니다. 준비 상태에 도달한 후에 각 업그레이드 도메인 간 20분의 대기를 추가하면 업그레이드 안정성이 개선됩니다. 이 20분 동안 **준비 안 됨** 상태가 되면 20분 타이머를 다시 시작합니다. 또한 20분 간격 시작 전과 후에 **Get-CsPoolFabricState** cmdlet을 실행하여 라우팅 그룹의 기본 및 보조 복제본에 어떤 변경 사항도 없음을 확인할 수 있습니다.

  - 마지막으로 패치한 업그레이드 도메인의 서버가 중지되었거나 다시 시작되지 않을 경우 다음 업그레이드 도메인으로 이동하지 마세요. 업그레이드 내의 서버를 시작할 수 없는 경우에도 마찬가지입니다. **Get-CsPoolFabricState**를 실행하여 모든 라우팅 그룹에 하나의 기본 및 최소 하나의 보조 복제본이 있는지 확인합니다. 이렇게 하면 모든 사용자에게 서비스가 있는지 여부를 확인할 수 있습니다.

  - 일부 사용자에게만 서비스가 있고 다른 사용자에게는 없는 경우에는 –Verbose 옵션과 함께 **Get-CsPoolFabricState**를 실행하여 복제본이 없는 라우팅 그룹을 확인합니다. 문제 해결을 위한 첫 단계로 전체 풀을 다시 시작하지 마세요. 이 cmdlet에 대한 자세한 내용은 [Get-CsPoolFabricState](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsPoolFabricState)를 참조하세요.

  - Windows Fabric 설치/제거를 위해 이벤트 뷰어 또는 성능 모니터 창의 모든 인스턴스가 닫혀 있는지 확인합니다.

## 프런트 엔드 풀 구성 변경

프런트 엔드 서버를 풀에 추가하거나 풀에서 이러한 서버를 제거하고 새 토폴로지를 게시할 때마다 다음 지침을 따르세요.

  - 새 토폴로지가 게시된 후에는 풀에서 각 프런트 엔드 서버를 다시 시작해야 합니다. 이들 서버를 한 번에 하나씩 다시 시작합니다.

  - 구성 변경 중에 전체 풀의 작동이 중단된 경우 새 토폴로지를 게시한 후 다음 cmdlet을 실행합니다.
    
        Reset-CsPoolRegistrarState -PoolFQDN <PoolFQDN> -ResetType ServiceReset

프런트 엔드 서버가 실패하고 몇 일 동안 대체될 가능성이 낮다면 해당 서버를 토폴로지에서 제거합니다. 토폴로지를 다시 사용할 수 있게 될 때 새 프런트 엔드 서버를 토폴로지에 추가합니다.

