---
title: Test-CsVoiceTestConfiguration
TOCTitle: Test-CsVoiceTestConfiguration
ms:assetid: 1c87ef27-0542-49b0-9125-512fd6ed187d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398260(v=OCS.15)
ms:contentKeyID: 49302984
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsVoiceTestConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

음성 경로 지정 및 정책이 예상대로 작동하는지 확인하기 위해 테스트 음성 구성을 실행합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsVoiceTestConfiguration -TestCaseInputObject <TestConfiguration> [-Dialplan <LocationProfile>] [-RouteSettings <PstnRoutingSettings>] [-VoicePolicy <VoicePolicy>] <COMMON PARAMETERS>

    Test-CsVoiceTestConfiguration -DialedNumber <String> -Dialplan <LocationProfile> -VoicePolicy <VoicePolicy> [-RouteSettings <PstnRoutingSettings>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>]

## 예제

## 예제 1

이 예제에서는 구성 TestConfig1에 대해 음성 구성 테스트를 실행합니다. 먼저 ID가 TestConfig1인 구성을 검색하기 위해 **Get-CsVoiceTestConfiguration** cmdlet이 실행됩니다. 그런 다음, 해당 구성 개체는 **Test-CsVoiceTestConfiguration** cmdlet에 파이프됩니다.

    Get-CsVoiceTestConfiguration -Identity TestConfig1 | Test-CsVoiceTestConfiguration

## 예제 2

예제 2는 Get 작업의 결과가 Test cmdlet에 직접 파이프되는 대신에 먼저 $a 변수에 개체가 저장된 다음, TestCaseInputObject 매개 변수에 값으로 전달되어 테스트 구성으로 사용된다는 점을 제외하고는 예제 1과 동일합니다.

    $a = Get-CsVoiceTestConfiguration -Identity TestConfig1
    Test-CsVoiceTestConfiguration -TestCaseInputObject $a

## 예제 3

이 예제에서는 먼저 **New-CsVoiceTestConfiguration** cmdlet을 사용하여 정의할 필요 없이 테스트 구성을 실행합니다. 이전에 만들어진 TestConfiguration 개체를 전달하는 대신 이 예제에서는 테스트할 전화 건 번호와 테스트를 수행할 다이얼 플랜 및 음성 정책을 지정하여 원하는 대로 테스트를 설정하는 방법을 보여 줍니다.

이 예제의 첫째 줄에서는 **Get-CsDialPlan** cmdlet을 호출하여 전역 다이얼 플랜을 검색합니다. 검색된 다이얼 플랜 개체는 변수 $dp에 할당됩니다. 둘째 줄에서는 **Get-CsVoicePolicy** cmdlet을 호출하여 전역 음성 정책을 검색하고 해당 정책을 $vp 변수에 할당하여 음성 정책에 대한 동일한 작업을 수행합니다.

마침내 테스트를 실행할 준비가 되었습니다. 테스트할 전화 번호를 DialedNumber 매개 변수에 전달하고, 첫째 줄에서 검색한 다이얼 플랜($dp에 저장됨)을 Dialplan 매개 변수에 전달하고, 둘째 줄에서 검색한 음성 정책($vp에 저장됨)을 VoicePolicy 매개 변수에 전달하여 **Test-CsVoiceTestConfiguration** cmdlet을 호출합니다.

예제 3의 출력에는 예상 결과에 대한 상태가 포함되지 않습니다. 실제 결과를 예상과 비교 테스트하려면 **New-CsVoiceTestConfiguration** cmdlet을 사용하여 예상을 정의하고 예제 1과 2에서처럼 **Test-CsVoiceTestConfiguration** cmdlet을 호출해야 합니다.

    $dp = Get-CsDialPlan -Identity Global
    $vp = Get-CsVoicePolicy -Identity Global
    Test-CsVoiceTestConfiguration -DialedNumber 4255551212 -Dialplan $dp -VoicePolicy $vp

## 자세한 정보

음성 경로 및 음성 정책을 구현하기 전에 예상된 결과가 제공되는지 확인하기 위해 다양한 전화 번호에서 테스트하는 것이 좋습니다. 이 cmdlet을 해당 매개 변수 설정과 함께 실행하면 이러한 테스트를 실행할 수 있습니다.

이 cmdlet은 원하는 결과를 확인하거나 실제 결과를 예상 결과와 비교하기 위해 음성 경로, 사용법, 다이얼 플랜 및 음성 정책에 대해 전화 번호를 테스트합니다. 적절한 매개 변수를 개별적으로 입력하거나 **New-CsVoiceTestConfiguration** cmdlet을 사용하여 테스트할 음성 구성을 정의할 수 있습니다.

DialedNumber, DialPlan 및 VoicePolicy 값을 입력하면 변환된 번호, 해당 변환을 만드는 데 사용된 정규화 규칙, 사용된 경로 및 PSTN 사용 현황이 출력에 포함됩니다. TestCaseInputObject 매개 변수 값을 입력한 경우에는 결과가 **New-CsVoiceTestConfiguration** cmdlet을 사용하여 만들 때 테스트 개체에 제공한 예상 결과와 일치하는지 여부에 대한 상태를 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Test-CsVoiceTestConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsVoiceTestConfiguration"}

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
<td><p><em>DialedNumber</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>테스트를 실행할 전화 번호입니다. 다이얼 플랜, 경로 및 정책에 기초하여 이 번호는 출력으로 정규화 및 표시됩니다.</p>
<p>TestCaseInputObject 매개 변수를 값과 함께 제공하지 않은 경우 이 매개 변수가 필요합니다. DialedNumber 및 TestCaseInputObject를 제공할 수 없습니다. (TestCaseInputObject는 해당 개체 내에 DialedNumber가 이미 포함되어 있습니다.)</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Dialplan</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile</p></td>
<td><p>테스트를 실행할 때 사용할 다이얼 플랜의 다이얼 플랜 개체에 대한 참조입니다. <strong>Get-CsDialPlan</strong> cmdlet을 호출하여 다이얼 플랜 개체를 검색할 수 있습니다.</p>
<p>DialedNumber 매개 변수를 지정한 경우 이 매개 변수도 필요합니다. TestCaseInputObject 매개 변수를 사용하는 경우 이 매개 변수를 사용하지 마십시오. 함께 사용할 경우 이 매개 변수의 개체가 TestCaseInputObject에 지정된 다이얼 플랜과 일치해야 하므로 매개 변수 사용이 중복됩니다.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>TestCaseInputObject</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration</p></td>
<td><p>테스트할 음성 구성에 대한 참조를 포함하는 개체입니다. <strong>Get-CsVoiceTestConfiguration</strong> cmdlet을 호출하여 이 개체 참조를 검색할 수 있습니다.</p>
<p>cmdlet을 이 매개 변수와 함께 호출할 경우 DialedNumber를 지정할 수 없습니다. 또한 음성 테스트 구성 개체의 값과 중복되므로 Dialplan 또는 VoicePolicy를 지정하지 않아야 합니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>VoicePolicy</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoicePolicy</p></td>
<td><p>테스트를 실행할 때 사용할 음성 정책의 음성 정책 개체에 대한 참조입니다. <strong>Get-CsVoicePolicy</strong> cmdlet을 호출하여 음성 정책 개체를 검색할 수 있습니다.</p>
<p>DialedNumber 매개 변수를 지정한 경우 이 매개 변수도 필요합니다. TestCaseInputObject 매개 변수를 사용하는 경우 이 매개 변수를 사용하지 마십시오. 함께 사용할 경우 이 매개 변수의 개체가 TestCaseInputObject에 지정된 음성 정책과 일치해야 하므로 매개 변수 사용이 중복됩니다.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>RouteSettings</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnRoutingSettings</p></td>
<td><p>Lync Server 설치에서 사용할 수 있는 모든 음성 경로를 포함하는 개체에 대한 참조입니다. <strong>Get-CsRoutingConfiguration</strong> cmdlet을 호출하여 이 개체를 검색할 수 있습니다.</p>
<p>이 매개 변수를 DialedNumber 매개 변수나 TestCaseInputObject 매개 변수와 함께 사용할 수 있습니다.</p>
<p></p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration 개체입니다. 음성 테스트 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.Voice.OcsVoiceTestResult 유형의 개체를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoiceTestConfiguration](new-csvoicetestconfiguration.md)  
[Remove-CsVoiceTestConfiguration](remove-csvoicetestconfiguration.md)  
[Set-CsVoiceTestConfiguration](set-csvoicetestconfiguration.md)  
[Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)  
[Get-CsDialPlan](get-csdialplan.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)  
[Get-CsRoutingConfiguration](get-csroutingconfiguration.md)

