---
title: Set-CsVoiceNormalizationRule
TOCTitle: Set-CsVoiceNormalizationRule
ms:assetid: 68850abb-4ac7-4ae1-bb6e-d991385f92a4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398491(v=OCS.15)
ms:contentKeyID: 49303902
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsVoiceNormalizationRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

음성 정규화 규칙을 수정합니다. 음성 정규화 규칙은 전화 걸기 요구 사항(예: 외부 회선에 액세스하기 위해 9번 걸기)을 Lync Server에 사용되는 E.164 전화 번호 형식으로 변환하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsVoiceNormalizationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsVoiceNormalizationRule [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-IsInternalExtension <$true | $false>] [-Pattern <String>] [-Priority <Int32>] [-Translation <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제는 사이트 Redmond에서 규칙 Prefix Redmond의 설명을 "Add a prefix to all numbers on site Redmond(사이트 Redmond의 모든 번호에 접두사 추가)"로 설정합니다.

    Set-CsVoiceNormalizationRule -Identity "site:Redmond/Prefix Redmond" -Description "Add a prefix to all numbers on site Redmond"

## 예제 2

이 예제에서는 ID가 global/SeattleFourDigit인 음성 정규화 규칙을 수정합니다. 규칙에 대한 수정 사항을 반영하기 위해 새 Description이 지정되었습니다. 또한 이 규칙의 기존 패턴과 일치하는 번호를 동일하지만 접두사 +1206556이 있는 번호로 변환하기 위해 규칙을 수정하는 Translation 값이 지정되었습니다. 예를 들어, 기존 패턴이 4자리 번호와 일치하고 번호 1234를 입력한 경우 이 규칙은 해당 내선 번호를 +12065561234로 변환합니다.

    Set-CsVoiceNormalizationRule -Identity global/SeattleFourDigit -Description "Translate an internal four-digit extension" -Translation '+1206556$1'

## 예제 3

예제 3에서는 정규화 규칙의 이름을 변경합니다. 이름을 변경하면 해당 ID의 이름 부분도 변경됩니다. **Set-CsVoiceNormalizationRule** cmdlet에는 Name 매개 변수가 없으므로 이름을 변경하기 위해 먼저 **Get-CsVoiceNormalizationRule** cmdlet을 호출하여 ID가 global/RedmondFourDigit인 규칙을 검색하고 반환된 개체를 변수 $a에 할당합니다. 그런 다음 문자열 RedmondRule을 개체의 Name 속성에 할당합니다. 다음으로 이 변수를 **Set-CsVoiceNormalizationRule** cmdlet의 Instance 매개 변수에 전달하여 영구적으로 변경합니다.

    $a = Get-CsVoiceNormalizationRule -Identity global/RedmondFourDigit
    $a.name = "RedmondRule"
    Set-CsVoiceNormalizationRule -Instance $a

## 자세한 정보

이 cmdlet은 명명된 음성 정규화 규칙을 수정합니다. 이러한 규칙은 전화 권한 부여 및 통화 경로 지정의 필수 부분입니다. 이러한 규칙은 번호를 내부 Lync Server 형식에서 표준(E.164) 형식으로 변환하기 위한 요구 사항을 정의합니다. 정규식을 이해하면 변환될 숫자 패턴을 정의하는 데 도움이 됩니다.

이 cmdlet을 사용하여 수정한 규칙은 다이얼 플랜의 일부이며, **Get-CsVoiceNormalizationRule** cmdlet을 통해 액세스할 수 있는 것 외에도 **Get-CsDialPlan** cmdlet 호출을 통해 반환되는 NormalizationRules 속성을 통해 액세스할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsVoiceNormalizationRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoiceNormalizationRule"}

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
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>정규화 규칙에 대한 간단한 설명입니다.</p>
<p>최대 문자열 길이: 512자</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>규칙에 대한 고유한 식별자입니다. 지정한 ID에는 범위, 슬래시 및 이름이 순서대로 포함되어야 합니다. 예를 들어, site:Redmond/Rule1에서 site:Redmond는 범위이고 Rule1은 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>정규화 규칙</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다. 이 개체는 NormalizationRule 유형이어야 하며 <strong>Get-CsVoiceNormalizationRule</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>IsInternalExtension</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True인 경우 이 규칙을 적용한 결과는 회사 내부의 번호가 됩니다. False인 경우 규칙을 적용한 결과는 외부 번호가 됩니다. 관련 다이얼 플랜의 OptimizeDeviceDialing 속성 값이 False로 설정된 경우 이 값은 무시됩니다.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>Pattern</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 규칙을 적용하기 위해 전화 건 번호가 일치해야 하는 정규식입니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Priority</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>규칙이 적용되는 순서입니다. 번호는 둘 이상의 규칙과 일치할 수 있습니다. 이 매개 변수는 번호에 대해 규칙이 테스트되는 순서를 설정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Translation</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>E.164 형식으로 변환하기 위해 번호에 적용되는 정규식 패턴입니다.</p>
<p></p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule 개체입니다. **Set-CsVoiceNormalizationRule** cmdlet은 음성 정규화 규칙 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsVoiceNormalizationRule** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)  
[Remove-CsVoiceNormalizationRule](remove-csvoicenormalizationrule.md)  
[Get-CsVoiceNormalizationRule](get-csvoicenormalizationrule.md)  
[Test-CsVoiceNormalizationRule](test-csvoicenormalizationrule.md)  
[Set-CsDialPlan](set-csdialplan.md)  
[Get-CsDialPlan](get-csdialplan.md)

