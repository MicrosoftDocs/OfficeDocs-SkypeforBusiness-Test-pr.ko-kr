---
title: Get-CsPoolUpgradeReadinessState
TOCTitle: Get-CsPoolUpgradeReadinessState
ms:assetid: 127c718e-8949-4bcd-b954-5182b8730820
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204689(v=OCS.15)
ms:contentKeyID: 49302869
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPoolUpgradeReadinessState

 

_**마지막으로 수정된 항목:** 2015-03-09_

비즈니스용 Skype Online 등록자 풀을 업그레이드할 수 있는지 여부를 나타내는 정보를 반환합니다. 풀의 업그레이드 준비 상태는 해당 풀에 대해 구성된 업그레이드 도메인을 기준으로 합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsPoolUpgradeReadinessState [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 로컬 등록자 풀의 업그레이드 준비 상태를 반환합니다. 이 명령은 풀 내에 있는 프런트 엔드 서버에서 실행해야 합니다.

    Get-CsPoolUpgradeReadinessState

## 자세한 정보

**Get-CsPoolUpgradeReadinessState** cmdlet은 Lync Server 2013 풀의 업그레이드 준비에 대한 정보를 반환합니다. 반환되는 정보에는 풀에 할당된 프런트 엔드 서버의 수, 현재 활성 상태인 프런트 엔드 서버의 수, 업그레이드 도메인의 이름, 그리고 풀의 현재 상태에서 업그레이드가 허용되는지를 나타내는 True/False 값이 포함됩니다. 이 cmdlet은 확인 대상 풀의 프런트 엔드 서버에서 로컬로 실행해야 합니다. **Get-CsPoolUpgradeReadinessState** cmdlet을 원격으로 실행할 수 있도록 설정하는 옵션은 없습니다.

**Lync Server 제어판:** **Get-CsPoolUpgradeReadinessState** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsPoolUpgradeReadinessState** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsPoolUpgradeReadinessState** cmdlet은 Microsoft.Rtc.Management.Hadr.PoolUpgradeState 개체의 인스턴스를 반환합니다.

