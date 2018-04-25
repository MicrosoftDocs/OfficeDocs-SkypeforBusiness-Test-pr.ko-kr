---
title: Set-CsOutboundCallingNumberTranslationRule
TOCTitle: Set-CsOutboundCallingNumberTranslationRule
ms:assetid: e9a7190a-a50d-4d01-8f33-66ed88a52b9e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205400(v=OCS.15)
ms:contentKeyID: 49305401
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsOutboundCallingNumberTranslationRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 아웃바운드 호출 번호 변환 규칙을 수정합니다. 아웃바운드 호출 번호 변환 규칙은 Lync Server 2013에서 사용하는 E.164 전화 번호를 E.164 번호를 지원하지 않는 트렁크 피어에서 사용할 수 있는 형식으로 변환합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsOutboundCallingNumberTranslationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsOutboundCallingNumberTranslationRule [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-Pattern <String>] [-Priority <Int32>] [-Translation <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 site:Redmond/SevenDigit인 아웃바운드 호출 번호 변환 규칙의 Priority를 변경합니다. 이 예제에서는 Priority를 0으로 설정합니다.

    Set-CsOutboundCallingNumberTranslationRule -Identity "site:Redmond/SevenDigit" -Priority 0

## 자세한 정보

아웃바운드 호출 번호 변환 규칙은 Lync 2013에서 사용하는 E.164 전화 번호를 E.164 번호를 지원하지 않는 트렁크 피어가 사용할 수 있는 형식으로 변환합니다. 변환 규칙을 만들 때는 아웃바운드 E.164 번호를 나타내는 정규식(패턴)과 변환된 번호를 나타내는 정규식(변환)을 모두 지정합니다.

아웃바운드 호출 번호 변환 규칙은 트렁크 구성 설정의 컬렉션에 바인딩되어야 합니다. 새 변환 규칙을 만들 때는 트렁크 구성 설정의 ID와 새 규칙의 이름(예: site:Redmond/RedmondTranslationRule)을 모두 지정해야 합니다. 새 규칙을 만들 때 트렁크 구성 설정이 반드시 있어야 하는 것은 아닙니다. 예를 들어 site:Redmond/RedmondTranslationRule 규칙을 만드는데 Redmond 사이트에 대해 트렁크 구성 설정이 작성되지 않았다고 가정해 보겠습니다. 이 경우 Redmond 사이트가 유효한 사이트이면 트렁크 구성 설정이 사이트에 대해 자동으로 작성되며 새 변환 규칙이 해당 설정 컬렉션에 할당됩니다. 그러나 Redmond 사이트가 없으면 명령은 실패합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsOutboundCallingNumberTranslationRule"}

**Lync Server 제어판:**Lync Server 제어판을 사용하여 기존 아웃바운드 호출 번호 변환 규칙을 편집하려면 음성 라우팅, 트렁크 구성을 차례로 클릭하고 수정할 규칙이 포함된 구성 설정을 두 번 클릭합니다. 그런 다음 트렁크 구성 편집 대화 상자에서 아래쪽의 레이블이 호출 번호 변환 규칙인 섹션으로 스크롤하여 수정할 규칙을 두 번 클릭합니다.

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
<td><p>관리자가 변환 규칙과 함께 표시할 추가 텍스트를 제공할 수 있습니다. 이 설명은 관리자가 규칙의 목적을 명확하게 파악하는 데 유용합니다.</p></td>
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
<td><p>수정할 변환 규칙의 고유한 식별자입니다. ID는 범위와 그 뒤에 오는 각 범위 내의 고유한 이름으로 구성됩니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;site:Redmond/OutboundRule1&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Pattern</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>변환을 적용할 숫자 패턴을 나타내는 정규식입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Priority</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>규칙에 할당되는 우선 순위입니다. 숫자가 둘 이상의 아웃바운드 변환 규칙 패턴과 일치하면 규칙이 우선 순위에 따라 적용됩니다. 규칙은 할당된 우선 순위대로 처리됩니다. 즉, 맨 먼저 처리할 규칙의 우선 순위는 0이고 두 번째로 처리할 규칙의 우선 순위는 1인 식입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Translation</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>아웃바운드 호출에 대해 번호를 준비하기 위해 패턴과 일치하는 번호에 적용할 정규식입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>실제로 명령을 수행하지는 않고 명령을 실행했을 때 발생할 결과에 대해 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Set-CsOutboundCallingNumberTranslationRule** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.CallingNumberTranslationRule\#Decorated 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsOutboundCallingNumberTranslationRule** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.CallingNumberTranslationRule\#Decorated 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsOutboundCallingNumberTranslationRule](get-csoutboundcallingnumbertranslationrule.md)  
[New-CsOutboundCallingNumberTranslationRule](new-csoutboundcallingnumbertranslationrule.md)  
[Remove-CsOutboundCallingNumberTranslationRule](remove-csoutboundcallingnumbertranslationrule.md)

