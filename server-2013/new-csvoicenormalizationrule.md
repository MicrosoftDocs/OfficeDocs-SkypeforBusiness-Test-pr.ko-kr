---
title: New-CsVoiceNormalizationRule
TOCTitle: New-CsVoiceNormalizationRule
ms:assetid: 189809ff-559e-476a-a32c-8b3812371883
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398240(v=OCS.15)
ms:contentKeyID: 49302945
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsVoiceNormalizationRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 음성 정규화 규칙을 만듭니다. 음성 정규화 규칙은 전화 걸기 요구 사항(예: 외부 회선에 액세스하기 위해 9번 걸기)을 Lync Server에 사용되는 E.164 전화 번호 형식으로 변환하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsVoiceNormalizationRule -Name <String> -Parent <String> <COMMON PARAMETERS>

    New-CsVoiceNormalizationRule -Identity <XdsIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-IsInternalExtension <$true | $false>] [-Pattern <String>] [-Priority <Int32>] [-Translation <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 Redmond 사이트를 위한 Prefix Redmond라는 새 음성 정규화 규칙을 만듭니다. 다른 매개 변수가 지정되지 않았으므로 이 규칙은 기본값을 사용하여 만들어집니다. 규칙 이름(Prefix Redmond)에 공백이 포함되어 있으므로 Identity 매개 변수에 전달되는 값은 큰따옴표로 묶습니다. 규칙 이름에 공백이 포함되지 않은 경우 Identity를 큰따옴표로 묶을 필요가 없습니다.

Redmond 사이트에 대한 다이얼 플랜이 존재해야 이 명령이 성공합니다. **New-CsDialPlan** cmdlet을 호출하여 새 다이얼 플랜을 만들 수 있습니다.

    New-CsVoiceNormalizationRule -Identity "site:Redmond/Prefix Redmond"

## 예제 2

이 예제에서는 ID가 SeattleUser인 사용자별 다이얼 플랜에 적용되는 SeattleFourDigit라는 새 음성 정규화 규칙을 만듭니다. (참고: Parent 및 Name을 지정하는 대신에 -Identity SeattleUser/SeattleFourDigit를 지정하여 이와 동일한 규칙을 만들 수 있습니다.) 이 규칙이 4자리 내선 번호만 사용하여 내부적으로 전화를 거는 번호를 변환한다는 것을 설명하기 위해 Description을 포함했습니다. 또한 Pattern 및 Translation 값이 지정되었습니다. 이러한 값은 4자리 숫자(Pattern에서 정규식으로 지정된)를 동일한 4자리 숫자로 변환하지만 Translation 값이 접두사로 추가됩니다(+1206555). 예를 들어, 내선 번호 1234에 전화를 걸 경우 이 규칙은 해당 내선 번호를 +12065551234로 변환합니다.

Pattern 및 Translation 값은 작은따옴표로 묶여 있습니다. 이러한 값에는 작은따옴표가 필요합니다. 이 예제에서는 큰따옴표가 작동하지 않으며 따옴표로 묶지 않은 값은 유효하지 않습니다.

예제 1과 마찬가지로 지정된 범위의 다이얼 플랜이 존재해야 합니다. 이 경우에는 ID가 SeattleUser인 다이얼 플랜이 존재해야 합니다.

    New-CsVoiceNormalizationRule -Parent SeattleUser -Name SeattleFourDigit -Description "Dialing with internal four-digit extension" -Pattern '^(\d{4})$' -Translation '+1206555$1'

## 자세한 정보

이 cmdlet은 명명된 음성 정규화 규칙을 만듭니다. 이러한 규칙은 전화 권한 부여 및 통화 경로 지정의 필수 부분입니다. 이러한 규칙은 번호를 내부 Lync Server 형식에서 표준(E.164) 형식으로 변환하기 위한 요구 사항을 정의합니다. 정규식을 이해하면 변환될 숫자 패턴을 정의하는 데 도움이 됩니다.

이 cmdlet을 사용하여 만든 규칙은 다이얼 플랜의 일부이며, **Get-CsVoiceNormalizationRule** cmdlet을 통해 액세스할 수 있는 것 외에도 **Get-CsDialPlan** cmdlet 호출을 통해 반환되는 NormalizationRules 속성을 통해 액세스할 수 있습니다. 정규화 규칙 ID에 지정된 범위와 일치하는 ID가 있는 다이얼 플랜이 존재하지 않으면 정규화 규칙을 만들 수 없습니다. 예를 들어 site:Redmond에 대한 다이얼 플랜이 존재하지 않는 경우 ID가 site:Redmond/RedmondNormalizationRule인 정규화 규칙을 만들 수 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsVoiceNormalizationRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsVoiceNormalizationRule"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>규칙에 대한 고유한 식별자입니다. 지정한 ID에는 범위, 슬래시 및 이름이 순서대로 포함되어야 합니다. 예를 들어, site:Redmond/Rule1에서 site:Redmond는 범위이고 Rule1은 이름입니다. 이 이름 부분은 자동으로 Name 속성에 저장됩니다. Identity와 Name 값은 동일한 명령에 지정할 수 없습니다.</p>
<p>음성 정규화 규칙은 전역, 사이트, 서비스 범위(등록자 및 PSTN 게이트웨이에만 해당) 및 사용자별 범위에 만들 수 있습니다. 새 규칙을 만들려면 정규화 규칙의 범위와 일치하는 ID를 가진 다이얼 플랜이 이미 있어야 합니다. 다이얼 플랜 목록을 검색하려면 <strong>Get-CsDialPlan</strong> cmdlet을 호출합니다.</p>
<p>Parent 매개 변수가 지정되지 않은 경우 Identity 매개 변수가 필요합니다. 같은 명령에 Identity 매개 변수와 Parent 매개 변수를 함께 포함할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>규칙의 이름입니다. Parent 매개 변수에 값이 지정된 경우 이 매개 변수가 필요합니다. Parent 매개 변수에 값이 지정되지 않은 경우 이름은 기본적으로 Identity 매개 변수에 지정된 이름입니다. 예를 들어 ID가 site:Redmond/RedmondRule인 규칙을 만들 경우 이름은 기본적으로 RedmondRule입니다. Name 매개 변수와 Identity 매개 변수를 같은 명령에서 사용할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Parent</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 정규화 규칙이 만들어질 범위입니다. 이 값은 global 또는 site:&lt;사이트 이름&gt;이어야 합니다. 여기서 &lt;사이트 이름&gt;은 Lync Server 사이트, PSTN 게이트웨이 또는 등록자 서비스(예: PSTNGateway:redmond.litwareinc.com) 또는 사용자별 규칙을 지정하는 문자열입니다. 지정된 범위의 다이얼 플랜이 존재해야 하며 그렇지 않으면 명령이 실패합니다.</p>
<p>Identity 매개 변수가 지정되지 않은 경우 Parent 매개 변수가 필요합니다. 같은 명령에 Identity 매개 변수와 Parent 매개 변수를 함께 포함할 수는 없습니다. Parent 매개 변수를 포함할 경우 Name 매개 변수도 필요합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>정규화 규칙에 대한 알기 쉬운 설명입니다.</p>
<p>최대 문자열 길이: 512자</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경 작업을 수행하기 전에 표시되는 모든 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>IsInternalExtension</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True인 경우 이 규칙을 적용한 결과는 조직 내부의 번호가 됩니다. False인 경우 규칙을 적용한 결과는 외부 번호가 됩니다. 관련 다이얼 플랜의 OptimizeDeviceDialing 속성 값이 False로 설정된 경우 이 값은 무시됩니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="odd">
<td><p><em>Pattern</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 규칙을 적용하기 위해 전화 건 번호가 일치해야 하는 정규식입니다.</p>
<p>기본값: ^(\d{11})$(기본값은 최대 11자의 임의의 숫자 집합을 나타냅니다.)</p></td>
</tr>
<tr class="even">
<td><p><em>Priority</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>규칙이 적용되는 순서입니다. 전화 번호는 둘 이상의 규칙과 일치할 수 있습니다. 이 매개 변수는 번호에 대해 규칙이 테스트되는 순서를 설정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Translation</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>E.164 형식으로 변환하기 위해 번호에 적용되는 정규식 패턴입니다.</p>
<p>기본값: +$1(기본값은 더하기 기호 [+]가 접두사로 번호에 추가됩니다.)</p></td>
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

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsVoiceNormalizationRule](remove-csvoicenormalizationrule.md)  
[Set-CsVoiceNormalizationRule](set-csvoicenormalizationrule.md)  
[Get-CsVoiceNormalizationRule](get-csvoicenormalizationrule.md)  
[Test-CsVoiceNormalizationRule](test-csvoicenormalizationrule.md)  
[New-CsDialPlan](new-csdialplan.md)  
[Get-CsDialPlan](get-csdialplan.md)

