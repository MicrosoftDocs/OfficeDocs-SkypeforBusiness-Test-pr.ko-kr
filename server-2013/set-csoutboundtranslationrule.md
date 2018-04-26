---
title: Set-CsOutboundTranslationRule
TOCTitle: Set-CsOutboundTranslationRule
ms:assetid: fbf82146-7884-418c-8239-66c0ca0f2ba6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413073(v=OCS.15)
ms:contentKeyID: 49305635
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsOutboundTranslationRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 아웃바운드 변환 규칙을 수정합니다. 아웃바운드 변환 규칙은 PBX(Private Branch Exchange) 시스템과 상호 작용하기 위해 전화 번호를 로컬 전화 번호 형식으로 변환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsOutboundTranslationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsOutboundTranslationRule [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-Pattern <String>] [-Priority <Int32>] [-Translation <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 ID가 site:Redmond/Prefix Redmond인 전역 아웃바운드 변환 규칙을 수정합니다. 이 규칙이 E.164 형식의 번호를 7자리 전화 번호로 변환하는 데 사용됨을 설명하는 Description을 포함했습니다. 또한 Pattern 및 Translation 값을 지정하여 이러한 속성의 기존 값을 수정합니다. 이러한 값은 Pattern에 정규식으로 지정한 E.164 번호(이 경우 +1425로 시작하는 12자리)에서 처음 5자리를 제거하여 7자리 번호로 변환합니다. 예를 들어 +14255551212 번호는 5551212 번호로 변환됩니다.

    Set-CsOutboundTranslationRule -Identity "site:Redmond/Prefix Redmond" -Description "Convert to seven digits" -Pattern '^\+1425(\d{7})$' -Translation '$1'

## 예제 2

이 예제에서는 아웃바운드 변환 규칙의 Name 속성을 수정합니다. 그러면 이 규칙의 ID가 변경됩니다. 이 예제의 첫 번째 명령은 **Get-CsOutboundTranslationRule** cmdlet을 호출합니다. 지정된 ID를 가진 변환 규칙 하나를 반환하도록 ID를 site:Redmond\\OBR1로 지정합니다. 그런 다음 이 규칙을 표시하는 대신 $a 변수에 할당합니다. 이 예제의 둘째 줄은 문자열 "Outbound Rule 1"을 site:Redmond/OBR1 규칙에 대한 참조를 포함하는 $a 변수의 Name 속성에 할당합니다. 이 예제의 마지막 줄에서는 **Set-CsOutboundTranslationRule** cmdlet을 호출합니다. 이때 Instance 매개 변수를 지정하여 $a 변수로 전달합니다. 이제 ID 값이 site:Redmond/OBR1인 **Get-CsOutboundTranslationRule** cmdlet을 호출하면 아무 항목도 반환되지 않습니다. 이 ID를 가진 규칙이 ID가 site:Redmond/Outbound Rule 1인 동일한 규칙으로 대체되어 해당 규칙이 더 이상 존재하지 않기 때문입니다.

    $a = Get-CsOutboundTranslationRule -Identity "site:Redmond/OBR1"
    $a.Name = "Outbound Rule 1"
    Set-CsOutboundTranslationRule -Instance $a

## 자세한 정보

Lync Server는 전화 번호를 E.164 형식으로 정규화합니다. 그러나 이 형식으로 작동할 수 없는 PBX(Private Branch Exchange) 시스템도 많습니다. 아웃바운드 변환 규칙은 이 번호를 중재 서버 또는 게이트웨이로 전송하기 전에 로컬 전화 번호 형식으로 변환합니다. 이 cmdlet을 호출하여 기존 아웃바운드 변환 규칙을 수정할 수 있습니다.

각 아웃바운드 변환 규칙은 트렁크 구성과 연결됩니다. 즉, 이 cmdlet을 사용하여 규칙을 수정하면 해당 트렁크 구성이 영향을 받습니다. 둘 이상의 아웃바운드 변환 규칙을 각 구성과 연결할 수 있습니다. 따라서 각 규칙의 ID는 범위와 이 범위 내에서 고유한 이름으로 구성됩니다(범위/이름 형식, 예: site:Redmond/OBR1). 규칙은 동일한 범위의 트렁크 구성과 자동으로 연결됩니다. 트렁크 구성에서 아웃바운드 변환 규칙을 변경하려면 **Set-CsOutboundTranslationRule** cmdlet을 호출하는 것이 좋습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsOutboundTranslationRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsOutboundTranslationRule"}

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
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>아웃바운드 변환 규칙에 대한 설명입니다. 이 설명은 관리자가 규칙의 목적을 명확하게 파악하는 데 유용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Xds ID</p></td>
<td><p>수정할 아웃바운드 변환 규칙의 고유 식별자입니다. ID는 범위와 각 범위 내에서 고유한 이름이 뒤에 나오는 형식으로 구성됩니다(예: site:Redmond/OutboundRule1).</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>변환 규칙</p></td>
<td><p>아웃바운드 변환 규칙에 대한 개체 참조입니다. 이 개체의 유형은 Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule이어야 하며, <strong>Get-CsOutboundTranslationRule</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Pattern</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>변환을 적용할 숫자 패턴을 나타내는 정규식입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Priority</em></p></td>
<td><p>선택</p></td>
<td><p>Int32</p></td>
<td><p>번호가 하나 이상의 아웃바운드 변환 규칙 패턴과 일치하는 경우 규칙이 우선 순위에 따라 적용됩니다. 이 매개 변수를 사용하여 규칙에 우선 순위를 할당할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Translation</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>아웃바운드 경로 지정에 대해 번호를 준비하기 위해 패턴과 일치하는 번호에 적용할 정규식입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule 개체입니다. 아웃바운드 변환 규칙 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule 유형의 개체를 수정합니다.

## 참고 항목

#### 기타 리소스

[New-CsOutboundTranslationRule](new-csoutboundtranslationrule.md)  
[Remove-CsOutboundTranslationRule](remove-csoutboundtranslationrule.md)  
[Get-CsOutboundTranslationRule](get-csoutboundtranslationrule.md)

