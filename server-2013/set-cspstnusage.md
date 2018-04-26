---
title: Set-CsPstnUsage
TOCTitle: Set-CsPstnUsage
ms:assetid: ecba9ed6-4845-4035-933e-0c540d530b72
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399069(v=OCS.15)
ms:contentKeyID: 49305439
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsPstnUsage

 

_**마지막으로 수정된 항목:** 2015-03-09_

허용된 PSTN(공중 전화망) 사용법을 식별하는 문자열 집합을 수정합니다. 이 cmdlet을 사용하여 PSTN 사용법 목록에 사용법을 추가하거나 목록에서 사용법을 제거할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsPstnUsage [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsPstnUsage [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Usage <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 명령은 문자열 "International"을 사용 가능한 PSTN 사용법의 현재 목록에 추가합니다.

    Set-CsPstnUsage -Identity global -Usage @{add="International"}

## 예제 2

이 명령은 사용 가능한 PSTN 사용법 목록에서 문자열 "Local"을 제거합니다.

    Set-CsPstnUsage -Identity global -Usage @{remove="Local"}

## 예제 3

이 예제의 명령은 예제 2의 명령과 동일한 작업을 수행합니다. 즉, "Local" PSTN 사용법을 제거합니다. 이 예제에서는 Identity 매개 변수가 지정되지 않은 명령을 보여 줍니다. **Set-CsPstnUsage** cmdlet에 사용할 수 있는 유일한 ID는 Global ID이며 Identity 매개 변수를 생략하면 기본적으로 Global이 사용됩니다.

    Set-CsPstnUsage -Usage @{remove="Local"}

## 예제 4

이 명령은 사용법 목록의 모든 항목을 International 및 Restricted 값으로 대체합니다. 이전의 모든 기본 사용법은 제거됩니다.

    Set-CsPstnUsage -Usage @{replace="International","Restricted"}

## 자세한 정보

PSTN 사용법은 호출 권한 부여에 사용되는 문자열 값입니다. PSTN 사용법은 음성 정책을 경로에 연결합니다. **Set-CsPstnUsage** cmdlet을 사용하여 사용법 목록에서 전화 사용법을 추가하거나 제거합니다. 이 목록은 전역적이므로 Lync Server 배포 전체에서 정책 및 경로에 사용될 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsPstnUsage** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsPstnUsage"}

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
<td><p>변경 내용을 적용하기 전에 표시될 수 있는 확인 메시지를 숨깁니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>이러한 설정이 적용되는 범위입니다. 이 cmdlet의 ID는 항상 Global입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>PSTN 사용법</p></td>
<td><p>PSTN 사용법 개체에 대한 참조입니다. 이 개체의 유형은 PstnUsages여야 하며, <strong>Get-CsPstnUsage</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Usage</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>허용되는 사용법 문자열의 목록을 포함합니다. 이러한 항목은 임의의 문자열 값일 수 있습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnUsages 개체입니다. PSTN 사용법 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값이나 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnUsages 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPstnUsage](get-cspstnusage.md)

