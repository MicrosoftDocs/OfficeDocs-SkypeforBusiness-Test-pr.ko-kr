---
title: Reset-CsPoolRegistrarState
TOCTitle: Reset-CsPoolRegistrarState
ms:assetid: 1bdbd5d7-cc72-46c5-ac20-ddc0d5723fe0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ619172(v=OCS.15)
ms:contentKeyID: 49302977
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Reset-CsPoolRegistrarState

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 등록자 풀의 등록자 및 Windows 패브릭 서비스를 재설정합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Reset-CsPoolRegistrarState -PoolFqdn <Fqdn> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-MachineFqdn <Fqdn>] [-NoReStart <SwitchParameter>] [-ResetLocalDatabases <SwitchParameter>] [-ResetType <ServiceReset | QuorumLossRecovery | FullReset | MachineStateRemoved>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 나와 있는 명령은 등록자 풀 atl-cs-001.litwareinc.com의 서비스 재설정을 수행합니다. 이 명령을 실행한 후 서비스 재설정을 진행할지 여부를 묻는 메시지가 나타납니다.

    Reset-CsPoolRegistrarState -PoolFqdn "atl-cs-001.litwareinc.com" -ResetType ServiceReset

## 예제 2

예제 2에서도 등록자 풀 atl-cs-001.litwareinc.com의 서비스 재설정을 수행합니다. 그러나 이 경우에는 Confirm 매개 변수의 매개 변수 값을 $False(-Confirm:$False)로 지정하여 사용했습니다. 이렇게 하면 일반적으로 **Reset-CsPoolRegistrarState** cmdlet을 호출할 때 나타나는 확인 프롬프트가 나타나지 않습니다. 따라서 서비스 재설정을 진행할지 여부를 묻는 메시지가 나타나지 않으며, 대신 사용자가 Enter 키를 누르는 즉시 명령이 실행됩니다.

    Reset-CsPoolRegistrarState -PoolFqdn "atl-cs-001.litwareinc.com" -ResetType ServiceReset -Confirm:$False

## 예제 3

예제 3에서는 atl-cs-001.litwareinc.com 풀에서 쿼럼 손실 복구 재설정이 수행됩니다. 쿼럼 손실 복구 재설정은 대개 활성 프런트 엔드 서버 수가 쿼럼 상태 미만으로 떨어질 때 즉, 풀의 프런트 엔드 서버의 85% 미만이 현재 활성 상태일 때 사용됩니다. 쿼럼 손실 상태의 이러한 서비스만 백업 저장소에서 사용자 데이터를 다시 로드해야 합니다. 다른 서비스는 이 명령의 영향을 받지 않습니다.

    Reset-CsPoolRegistrarState -PoolFqdn "atl-cs-001.litwareinc.com" -ResetType QuorumLossRecovery

## 예제 4

예제 4에서는 atl-cs-001.litwareinc.com에 대해 전체 재설정이 수행됩니다. 전체 재설정 중에 프런트 엔드 및 Windows Fabric 서비스가 중지되고 항목 집합(LyncServer-MachineSet.xml 및 Settings.xml 파일 포함)이 제거됩니다. 이러한 항목이 제거된 후 프런트 엔드 및 Windows Fabric 서비스가 다시 시작됩니다.

풀을 다시 시작하려고 할 때 FullReset 옵션을 사용하면 오류가 생기는 경우가 종종 있으며, 실제로 풀이 다시 시작되지 않습니다. 따라서 다른 ResetType 옵션 중 하나를 사용하여 풀을 다시 시작해 보는 것이 좋습니다. 이 방법도 실패하면 FullReset 옵션을 사용하기 전에 Microsoft 지원 담당자에게 문의하세요.

    Reset-CsPoolRegistrarState -PoolFqdn "atl-cs-001.litwareinc.com" -ResetType FullReset

## 예제 5

예제 5는 예제 4에 표시된 명령의 변형입니다. 그러나 예제 5에는 NoReStart 매개 변수가 포함되어 **Reset-CsPoolRegistrarState** cmdlet이 풀이 재설정될 때 중지되는 Windows Fabric 서비스 등의 서비스를 다시 시작하지 못합니다. 이러한 서비스를 수동으로 다시 시작하는 것은 관리자에게 달려 있습니다.

예제 4에서 설명한 대로 풀을 다시 시작하려고 할 때 FullReset 옵션을 사용하면 오류가 생기는 경우가 종종 있으며, 실제로 풀이 다시 시작되지 않습니다. 따라서 다른 ResetType 옵션 중 하나를 사용하여 풀을 다시 시작해 보는 것이 좋습니다. 이 방법도 실패하면 FullReset 옵션을 사용하기 전에 Microsoft 지원 담당자에게 문의하세요.

    Reset-CsPoolRegistrarState -PoolFqdn "atl-cs-001.litwareinc.com" -ResetType FullReset -NoReStart

## 자세한 정보

**Reset-CsPoolRegistrarState** cmdlet을 사용하면 등록자 풀의 Windows 패브릭 서비스(FabricHostSvc) 및 Lync Server 등록자 서비스(RtcSrv)를 재설정할 수 있습니다. 이는 풀이 응답이 없거나 풀을 시작할 수 없을 때 필요할 수 있습니다. 이 경우 대개 등록자 서비스가 시작 보류 상태로 정지됩니다. 이 cmdlet을 실행하면 기본 설정에 따라 풀의 모든 관련 서비스가 중지되었다가 다시 시작됩니다. NoReStart 매개 변수를 사용하면 **Reset-CsPooRegistrarState** cmdlet이 서비스를 중지하고 다시 시작하지 않습니다. 그 다음 사용자가 이러한 서비스 전부(또는 일부)를 수동으로 다시 시작할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Reset-CsPoolRegistrarState"}

**Lync Server 제어판:** **Reset-CsPoolRegistrarState** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>PoolFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>재설정할 등록자 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
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
<td><p><em>MachineFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>풀에서 제거할 컴퓨터의 정규화된 도메인 이름입니다. 이 매개 변수는 MachineStateRemoved 재설정을 수행할 때만 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NoReStart</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 cmdlet 실행 시 중지되는 서비스(예: RtcSrv 및 FabricHostSvc)를 다시 시작하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ResetLocalDatabases</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 로컬 Lync Server 서비스와 함께 로컬 Lync Server 데이터베이스도 중지했다가 다시 시작합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ResetType</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Hadr.ResetPoolFabricStateCmdlet+PoolResetType</p></td>
<td><p>수행할 재설정의 유형입니다. 허용되는 값은 다음과 같습니다.</p>
<p>* <strong>ServiceReset</strong> – RtcSrv 및 fabricHostSvc 서비스를 중지했다가 다시 시작합니다. <code>ResetType</code>을 지정하지 않으면 서비스 재설정이 수행됩니다.</p>
<p>* <strong>QuorumLossRecovery</strong> – 현재 쿼럼 손실 상태인 라우팅 그룹에 대해 백업 저장소에서 사용자 데이터를 다시 로드합니다. 쿼럼 손실은 데이터베이스와 해당 복제본을 모두 사용할 수 없을 때 발생합니다. 이 방식으로 재설정을 하면 데이터베이스에 아직 쓰지 않은 데이터가 손실될 수 있습니다.</p>
<p><code>QuorumLossRecovery</code> 옵션은 복제본 수준 쿼럼 손실에서 풀을 복구하는 데 도움이 될 수 있지만 풀이 풀 수준 쿼럼 손실보다 심각한 수준에 있으면 제대로 작동하지 않습니다. 자세한 내용은 <a href="lync-server-2013-topologies-and-components-for-front-end-servers-instant-messaging-and-presence.md">Lync Server 2013 의 프런트 엔드 서버, 메신저 및 현재 상태에 대한 토폴로지 및 구성 요소</a>를 참조하세요.</p>
<p>* <strong>FullReset</strong> – <code>QuorumLossRecovery</code>와 동일한 유형의 재설정을 수행하지만 추가로 로컬 Lync Server 데이터베이스를 다시 작성합니다. 이 재설정 방식은 시간이 오래 걸리고 리소스 소모가 클 수 있습니다. 풀에서 프런트 엔드 서버의 수를 변경한 경우에만 이 옵션을 사용합니다(예: 2에서 임의, 1에서 임의, 임의에서 2 또는 임의에서 1로 변경). <strong>문제 해결 또는 서비스 시작 문제를 해결을 위한 용도로 이 옵션을 사용하지 마세요.</strong></p>
<p>ServiceReset 또는 FullReset 옵션과 함께 이 cmdlet을 사용하면 로그인되어 있는 사용자가 영향을 받지만, QuorumLossRecovery 옵션을 사용하면 사용자가 영향을 받지 않습니다.</p>
<div class="alert">

> [!IMPORTANT]
> 풀을 다시 시작하려고 할 때 FullReset 옵션을 사용하면 오류가 생기는 경우가 종종 있으며, 실제로 풀이 다시 시작되지 않습니다. 따라서 다른 ResetType 옵션 중 하나를 사용하여 풀을 다시 시작해 보는 것이 좋습니다. 이 방법도 실패하면 FullReset 옵션을 사용하기 전에 Microsoft 지원 담당자에게 문의하세요. 일반적으로 FullReset은 프런트 엔드 서버가 하나인 풀에서 프런트 엔드 서버가 여러 개인 풀로 변경할 때에만 사용됩니다.


</div>
<p><code>* MachineStateRemoved</code> -- 풀에서 지정된 서버를 삭제합니다. 이 재설정 방식은 해당 서버(또는 데이터베이스)가 영구적으로 손실된 경우에만 사용합니다.</p></td>
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

없음. **Reset-CsPoolRegistrarState** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

문자열 값. **Reset-CsPoolRegistrarState** cmdlet은 개체를 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Get-CsPoolFabricState](get-cspoolfabricstate.md)

