---
title: New-CsOutboundTranslationRule
TOCTitle: New-CsOutboundTranslationRule
ms:assetid: aa6011e5-c48d-4fcc-ba65-bdec341234ed
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412803(v=OCS.15)
ms:contentKeyID: 49304670
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsOutboundTranslationRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 아웃바운드 변환 규칙을 만듭니다. 아웃바운드 변환 규칙은 PBX(Private Branch Exchange) 시스템과 상호 작용하기 위해 전화 번호를 로컬 전화 번호 형식으로 변환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsOutboundTranslationRule -Name <String> -Parent <String> <COMMON PARAMETERS>

    New-CsOutboundTranslationRule -Identity <XdsIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Pattern <String>] [-Priority <Int32>] [-Translation <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 사이트 Redmond에 대해 Prefix Redmond라는 새 아웃바운드 변환 규칙을 만듭니다. 다른 매개 변수가 지정되지 않았으므로 이 규칙은 기본값을 사용하여 만들어집니다. 규칙 이름(Prefix Redmond)에 공백이 포함되어 있으므로 Identity 매개 변수에 전달된 값은 큰따옴표로 묶습니다. 규칙 이름에 공백이 포함되지 않은 경우 Identity를 큰따옴표로 묶을 필요가 없습니다.

    New-CsOutboundTranslationRule -Identity "site:Redmond/Prefix Redmond"

## 예제 2

이 예제에서는 SeattleSevenDigit라는 새 전역 아웃바운드 전환 규칙을 만듭니다. 참고: Parent 및 Name을 지정하는 대신에 -Identity global/SeattleSevenDigit를 지정하여 이와 동일한 규칙을 만들 수 있습니다. 이 규칙이 E.164 형식의 번호를 7자리 형식으로 변환하는 데 사용됨을 설명하는 Description을 포함했습니다. 또한 Pattern 및 Translation 값이 지정되었습니다. 이러한 값은 Pattern에 정규식으로 지정한 E.164 번호(이 경우 +1425로 시작하는 12자리)에서 처음 5자리를 제거하여 7자리 번호로 변환합니다. 예를 들어 +14255551212 번호는 5551212 번호로 변환됩니다.

    New-CsOutboundTranslationRule -Parent global -Name SeattleSevenDigit -Description "Convert to seven digits" -Pattern '^\+1425(\d{7})$' -Translation '$1'

## 자세한 정보

새 아웃바운드 변환 규칙을 만들려면 이 cmdlet을 호출하십시오. Lync Server는 전화 번호를 E.164 형식으로 정규화합니다. 그러나 이 형식으로 작동할 수 없는 PBX(Private Branch Exchange) 시스템도 많습니다. 아웃바운드 변환 규칙은 이 번호를 중재 서버 또는 게이트웨이로 전송하기 전에 로컬 전화 번호 형식으로 변환합니다.

각 아웃바운드 변환 규칙은 트렁크 구성과 연결됩니다. 둘 이상의 아웃바운드 변환 규칙을 각 구성과 연결할 수 있습니다. 따라서 각 규칙의 ID는 범위와 이 범위 내에서 고유한 이름으로 구성됩니다(범위/이름 형식, 예: site:Redmond/OBR1). 규칙은 동일한 범위의 트렁크 구성과 자동으로 연결됩니다. **New-CsOutboundTranslationRule** cmdlet을 호출하고 트렁크 구성이 아직 정의되지 않은 범위를 지정하면 지정된 범위, 아웃바운드 변환 규칙 및 기본값과 함께 트렁크 구성이 만들어집니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsOutboundTranslationRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsOutboundTranslationRule"}

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
<td><p>아웃바운드 변환 규칙에 대한 고유 식별자입니다. Identity는 규칙이 적용되는 범위와 규칙 이름을 포함하며 전역, 사이트 또는 서비스(PSTNGateway에만 해당) 범위에서 사용되어야 합니다. 예를 들어 site:Redmond/OutboundRule1 및 PstnGateway:Redmond.litwareinc.com/OutboundRule2와 같은 형식을 사용합니다.</p>
<p>Identity 매개 변수를 지정한 경우 Name 또는 Parent 매개 변수 값을 지정할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>아웃바운드 변환 규칙의 이름입니다. Name을 제공하지 않은 경우 범위와 이름으로 구성된 Identity를 지정해야 합니다. 반면, Name을 제공한 경우 Parent 매개 변수도 함께 제공해야 하지만 Identity는 지정할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Parent</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>아웃바운드 변환 규칙의 범위입니다. 이 매개 변수에 값이 지정된 경우 Name 매개 변수에도 값을 지정해야 합니다. 그러나 Identity 매개 변수는 지정할 수 없습니다. Parent 및 Name 매개 변수가 지정되지 않은 경우 Identity가 있어야 합니다.</p></td>
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
<td><p>아웃바운드 변환 규칙에 대한 설명입니다. 이 설명은 규칙의 용도를 식별하는 데 도움이 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Pattern</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>변환을 적용할 숫자 패턴을 나타내는 정규식입니다.</p>
<p>기본값: ^\+(\d*)$</p></td>
</tr>
<tr class="odd">
<td><p><em>Priority</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>번호가 하나 이상의 아웃바운드 변환 규칙 패턴과 일치하는 경우 규칙이 우선 순위에 따라 적용됩니다. 이 매개 변수를 사용하여 규칙에 우선 순위를 할당할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Translation</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>아웃바운드 경로 지정에 대해 번호를 준비하기 위해 패턴과 일치하는 번호에 적용할 정규식입니다.</p>
<p>기본값: $1</p></td>
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

없음.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsOutboundTranslationRule](remove-csoutboundtranslationrule.md)  
[Set-CsOutboundTranslationRule](set-csoutboundtranslationrule.md)  
[Get-CsOutboundTranslationRule](get-csoutboundtranslationrule.md)

