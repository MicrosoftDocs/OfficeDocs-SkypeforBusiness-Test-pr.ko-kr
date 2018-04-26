---
title: Get-CsPoolFabricState
TOCTitle: Get-CsPoolFabricState
ms:assetid: 9fe6cce5-4142-47b3-94ac-4cb8b94ec215
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ619188(v=OCS.15)
ms:contentKeyID: 49304552
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPoolFabricState

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 풀의 Windows 패브릭 상태를 반환합니다. Windows 패브릭은 안정성, 분산 기능 및 확장성이 우수한 응용 프로그램을 작성하기 위한 Microsoft의 기술입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsPoolFabricState -PoolFqdn <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Type <All | MCUFactory | ConferenceDirectory | Routing | LYSS>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1의 명령은 풀 atl-cs-001.litwareinc.com의 패브릭 상태를 반환합니다. Type 매개 변수를 사용하지 않았기 때문에 풀의 모든 서비스에 대한 상태 정보가 반환됩니다.

    Get-CsPoolFabricState -PoolFqdn "atl-cs-001.litwareinc.com"

## 예제 2

예제 2는 풀 atl-cs-001.litwareinc.com에 있는 단일 서비스인 MCU 센터 서비스의 패브릭 상태를 반환합니다. 이를 위해 Type 매개 변수 값을 "MCU"로 설정합니다.

    Get-CsPoolFabricState -PoolFqdn "atl-cs-001.litwareinc.com" -Type MCU

## 자세한 정보

**Get-CsPoolFabricState** cmdlet은 Lync Server 2013 풀의 Windows 패브릭 상태를 반환합니다. 여기에는 MCU 센터, 회의 디렉터리, 라우팅, Lync Server 저장소 서비스 중 일부 또는 전체에 대한 Windows 패브릭 복제본 인스턴스 관련 정보가 포함됩니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPoolFabricState"}

**Lync Server 제어판:** **Get-CsPoolFabricState** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>System.String</p></td>
<td><p>확인할 풀의 정규화된 도메인 이름입니다. 이 cmdlet을 호출할 때는 풀의 FQDN을 제공해야 합니다. 예를 들면 다음과 같습니다.</p>
<p>-PoolFqdn &quot;atl-cs-001.litwareinc.com”</p></td>
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
<td><p><em>Type</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.HADR.GetOcsPoolFabricStateCmdlet+FabricEnumerationType</p></td>
<td><p>반환할 서비스 유형을 지정합니다. 허용되는 값은 다음과 같습니다.</p>
<p>* All(모든 서비스의 정보 반환)</p>
<p>* MCUFactory(MCU 센터 서비스의 정보 반환)</p>
<p>* ConferenceDirectory(회의 디렉터리 서비스의 정보 반환)</p>
<p>LYSS( Lync Server 저장소 서비스의 정보 반환)</p>
<p>명령당 하나의 유형만 지정할 수 있습니다.</p></td>
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

없음. **Get-CsPoolFabricState** cmdlet은 파이프라인된 입력을 지원하지 않습니다.

## 반환 형식

패브릭 상태를 나타내는 문자열 값. **Get-CsPoolFabricState** cmdlet은 개체를 반환하지 않습니다.

