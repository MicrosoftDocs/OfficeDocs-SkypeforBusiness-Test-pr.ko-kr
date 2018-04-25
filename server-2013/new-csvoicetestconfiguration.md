---
title: New-CsVoiceTestConfiguration
TOCTitle: New-CsVoiceTestConfiguration
ms:assetid: da312c27-bc89-46c3-a6c9-c098ed4e7df7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398961(v=OCS.15)
ms:contentKeyID: 49305210
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsVoiceTestConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 경로 및 규칙에 대해 전화 번호를 테스트하는 데 사용할 수 있는 테스트 시나리오를 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsVoiceTestConfiguration -Name <String> <COMMON PARAMETERS>

    New-CsVoiceTestConfiguration -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-DialedNumber <String>] [-ExpectedRoute <String>] [-ExpectedTranslatedNumber <String>] [-ExpectedUsage <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-TargetDialplan <String>] [-TargetVoicePolicy <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 기본값을 사용하여 ID가 TestConfig1인 새 음성 테스트 구성을 만듭니다.

    New-CsVoiceTestConfiguration -Identity TestConfig1

## 예제 2

이 예제에서는 TestConfig1이라는 새 음성 테스트 구성을 만들고 TargetDialplan 매개 변수를 site:Redmond1로 설정합니다. 이렇게 하면 Redmond1 사이트의 다이얼 플랜 설정에 대해 예상된 번호, 사용법 및 경로의 테스트가 실행됩니다.

이 예제에서는 Identity 매개 변수를 지정하지 않고 TestConfig1을 선언했습니다. Identity는 위치 매개 변수이므로 이 cmdlet은 cmdlet 이름 뒤에 오는 명령의 첫 번째 값을 Identity로 인식합니다.

    New-CsVoiceTestConfiguration TestConfig1 -TargetDialplan site:Redmond1

## 예제 3

이 예제에서는 TestConfig1이라는 새 음성 테스트 구성을 만듭니다. 이 구성은 기본값을 사용하여 +5551212의 예상 출력(ExpectedTranslatedNumber)에 대해 DialedNumber 5551212를 테스트합니다. 예상 출력은 이 개체에 대해 테스트가 실행될 때 사용되는 다이얼 플랜과 연관된 정규화 규칙에 기초합니다. 해당 테스트는 **Test-CsVoiceTestConfiguration** cmdlet을 사용하여 실행해야 합니다.

    New-CsVoiceTestConfiguration -Identity TestConfig1 -DialedNumber 5551212 -ExpectedTranslatedNumber +5551212

## 자세한 정보

음성 경로 및 음성 정책을 구현하기 전에 예상된 결과가 나오는지 확인하기 위해 다양한 전화 번호에서 테스트하는 것이 좋습니다. 이 cmdlet으로 테스트 시나리오를 만들어 이 테스트를 수행할 수 있습니다.

**New-CsVoiceTestConfiguration** cmdlet은 지정한 전화 번호를 테스트할 음성 경로, 사용법, 다이얼 플랜 및 음성 정책을 정의합니다. 다른 cmdlet을 사용하여 이러한 모든 정보를 정의 및 검색할 수 있습니다. 자세한 내용은 이 항목의 매개 변수 설명을 참조하십시오.

이 cmdlet으로 만든 구성은 **Test-CsVoiceTestConfiguration** cmdlet을 사용하여 테스트합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsVoiceTestConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsVoiceTestConfiguration"}

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>이 테스트 시나리오를 고유하게 식별하는 문자열입니다.</p>
<p>이 문자열의 길이는 최대 32자일 수 있고 임의의 영숫자 외에 백슬래시(\), 점(.) 또는 밑줄(_)을 포함할 수 있습니다.</p>
<p>이 개체를 전역 범위에서만 만들 수 있으므로 이 매개 변수의 값은 범위를 포함하지 않습니다. 따라서 고유한 이름만 필요합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수는 Identity와 동일한 값을 포함합니다. Identity 매개 변수가 지정된 경우 Name 매개 변수를 명령에 포함할 수 없습니다. 마찬가지로 Name 매개 변수가 지정된 경우 Identity를 지정할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DialedNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>정책, 사용법 등을 테스트하는 데 사용할 전화 번호입니다.</p>
<p>512자 이하여야 합니다.</p>
<p>기본값: 1234</p></td>
</tr>
<tr class="odd">
<td><p><em>ExpectedRoute</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>구성 테스트 도중 사용할 것으로 예상되는 음성 경로의 이름입니다. 대상 다이얼 플랜 및 음성 정책에 따라 다른 경로를 사용할 경우 테스트에 실패합니다. <strong>Get-CsVoiceRoute</strong> cmdlet을 호출하여 사용 가능한 음성 경로를 검색할 수 있습니다.</p>
<p>256자 이하여야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExpectedTranslatedNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>변환 후 보게 될 것으로 예상되는 형식의 전화 번호입니다. 정규화 후의 DialedNumber 매개 변수 값입니다. <strong>Test-CsVoiceTestConfiguration</strong> cmdlet을 실행하고 나서 DialedNumber가 ExpectedTranslatedNumber의 값이 아닌 경우 테스트는 실패로 보고됩니다.</p>
<p>512자 이하여야 합니다.</p>
<p>기본값: +1234</p></td>
</tr>
<tr class="odd">
<td><p><em>ExpectedUsage</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>구성 테스트 도중 사용할 것으로 예상되는 PSTN 사용법의 이름입니다. 대상 다이얼 플랜 및 음성 정책에 따라 다른 PSTN 사용법을 사용할 경우 테스트에 실패합니다. <strong>Get-CsPstnUsage</strong> cmdlet을 호출하여 사용 가능한 사용법을 검색할 수 있습니다.</p>
<p>256자 이하여야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경 내용을 적용하기 전에 표시될 수 있는 확인 메시지를 숨깁니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetDialplan</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 테스트에 사용할 다이얼 플랜의 ID입니다. <strong>Get-CsDialPlan</strong> cmdlet을 호출하여 다이얼 플랜을 검색할 수 있습니다.</p>
<p>40자 이하여야 합니다.</p>
<p>기본값: Global</p></td>
</tr>
<tr class="odd">
<td><p><em>TargetVoicePolicy</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 테스트를 실행할 음성 정책의 ID입니다. <strong>Get-CsVoicePolicy</strong> cmdlet을 호출하여 음성 정책을 검색할 수 있습니다.</p>
<p>40자 이하여야 합니다.</p>
<p>기본값: Global</p></td>
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

없음.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsVoiceTestConfiguration](remove-csvoicetestconfiguration.md)  
[Set-CsVoiceTestConfiguration](set-csvoicetestconfiguration.md)  
[Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)  
[Test-CsVoiceTestConfiguration](test-csvoicetestconfiguration.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)  
[Get-CsPstnUsage](get-cspstnusage.md)  
[Get-CsDialPlan](get-csdialplan.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)

