---
title: Set-CsVoiceTestConfiguration
TOCTitle: Set-CsVoiceTestConfiguration
ms:assetid: 7b95fc95-ec0e-4bb3-aed1-e8b72e305999
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398614(v=OCS.15)
ms:contentKeyID: 49304137
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsVoiceTestConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 경로 및 규칙에 대해 전화 번호를 테스트하는 데 사용할 수 있는 테스트 시나리오를 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsVoiceTestConfiguration [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsVoiceTestConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-DialedNumber <String>] [-ExpectedRoute <String>] [-ExpectedTranslatedNumber <String>] [-ExpectedUsage <String>] [-Force <SwitchParameter>] [-TargetDialplan <String>] [-TargetVoicePolicy <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 TestConfig1에 대한 음성 테스트 구성의 전화 건 번호를 14255551212로 설정합니다. 정규화가 예상대로 발생하고 올바른 경로 및 다이얼 플랜이 적용되는지 확인하기 위해 음성 정책에 대해 이 번호가 검사됩니다.

    Set-CsVoiceTestConfiguration -Identity TestConfig1 -DialedNumber 14255551212

## 예제 2

이 예제에서는 음성 테스트 구성 TestConfig1에 대한 설정을 수정합니다. 이 명령은 TargetDialplan을 site:Redmond1에 대한 다이얼 플랜으로 설정합니다. 다이얼 플랜의 변경이 정규화 규칙의 변경을 의미할 수 있으므로 해당 다이얼 플랜에 대한 정규화 규칙에서 예상되는 사항을 반영하기 위해 ExpectedTranslationNumber도 변경되었습니다.

    Set-CsVoiceTestConfiguration -Identity TestConfig1 -TargetDialplan site:Redmond1 -ExpectedTranslatedNumber "+912065551212"

## 자세한 정보

음성 경로 및 음성 정책을 구현하기 전에 예상된 결과가 제공되는지 확인하기 위해 다양한 전화 번호에서 테스트하는 것이 좋습니다. 이 cmdlet으로 테스트 시나리오를 수정하여 이 작업을 수행할 수 있습니다.

**Set-CsVoiceTestConfiguration** cmdlet은 지정한 전화 번호를 테스트할 음성 경로, 사용법, 다이얼 플랜 및 음성 정책을 수정합니다. 이 항목의 매개 변수 설명에 지정된 다른 cmdlet을 사용하여 이러한 모든 정보를 정의 및 검색할 수 있습니다.

이 cmdlet으로 수정한 구성은 **Test-CsVoiceTestConfiguration** cmdlet을 사용하여 테스트합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsVoiceTestConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoiceTestConfiguration"}

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
<td><p>SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DialedNumber</em></p></td>
<td><p>선택</p></td>
<td><p>String</p></td>
<td><p>정책, 사용법 등을 테스트하는 데 사용할 전화 번호입니다.</p>
<p>512자 이하여야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExpectedRoute</em></p></td>
<td><p>선택</p></td>
<td><p>String</p></td>
<td><p>구성 테스트 도중 사용할 것으로 예상되는 음성 경로의 이름입니다. 대상 다이얼 플랜 및 음성 정책에 따라 다른 경로를 사용할 경우 테스트에 실패합니다. <strong>Get-CsVoiceRoute</strong> cmdlet을 호출하여 사용 가능한 음성 경로를 검색할 수 있습니다.</p>
<p>256자 이하여야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExpectedTranslatedNumber</em></p></td>
<td><p>선택</p></td>
<td><p>String</p></td>
<td><p>변환 후 보게 될 것으로 예상되는 형식의 전화 번호입니다. 정규화 후의 DialedNumber 매개 변수 값입니다. <strong>Test-CsVoiceTestConfiguration</strong> cmdlet을 실행하고 나서 DialedNumber가 ExpectedTranslatedNumber의 값이 아닌 경우 테스트는 실패로 보고됩니다.</p>
<p>512자 이하여야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExpectedUsage</em></p></td>
<td><p>선택</p></td>
<td><p>String</p></td>
<td><p>구성 테스트 도중 사용할 것으로 예상되는 PSTN 사용법의 이름입니다. 대상 다이얼 플랜 및 음성 정책에 따라 다른 PSTN 사용법을 사용할 경우 테스트에 실패합니다. <strong>Get-CsPstnUsage</strong> cmdlet을 호출하여 사용 가능한 사용법을 검색할 수 있습니다.</p>
<p>256자 이하여야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>XdsGlobalRelativeIdentity</p></td>
<td><p>수정할 테스트 시나리오를 고유하게 식별하는 문자열입니다.</p>
<p>이 개체를 전역 범위에서만 만들 수 있으므로 이 매개 변수의 값은 범위를 포함하지 않습니다. 따라서 이름만 필요합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>TestConfiguration</p></td>
<td><p>해당 구성에 적용할 변경 내용과 함께 기존 음성 테스트 구성을 포함하는 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration 유형의 개체입니다. 이 유형의 개체는 <strong>Get-CsVoiceTestConfiguraton</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TargetDialplan</em></p></td>
<td><p>선택</p></td>
<td><p>String</p></td>
<td><p>이 테스트에 사용할 다이얼 플랜의 ID입니다. <strong>Get-CsDialPlan</strong> cmdlet을 호출하여 다이얼 플랜을 검색할 수 있습니다.</p>
<p>40자 이하여야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetVoicePolicy</em></p></td>
<td><p>선택</p></td>
<td><p>String</p></td>
<td><p>이 테스트를 실행할 음성 정책의 ID입니다. <strong>Get-CsVoicePolicy</strong> cmdlet을 호출하여 음성 정책을 검색할 수 있습니다.</p>
<p>40자 이하여야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration 개체입니다. 음성 테스트 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration 개체 유형을 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoiceTestConfiguration](new-csvoicetestconfiguration.md)  
[Remove-CsVoiceTestConfiguration](remove-csvoicetestconfiguration.md)  
[Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)  
[Test-CsVoiceTestConfiguration](test-csvoicetestconfiguration.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)  
[Get-CsPstnUsage](get-cspstnusage.md)  
[Get-CsDialPlan](get-csdialplan.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)

