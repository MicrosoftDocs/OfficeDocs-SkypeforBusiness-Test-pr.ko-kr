---
title: Remove-CsOutboundCallingNumberTranslationRule
TOCTitle: Remove-CsOutboundCallingNumberTranslationRule
ms:assetid: 41ca92c9-7c2e-44e0-8ec8-9f39843b73e7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204836(v=OCS.15)
ms:contentKeyID: 49303439
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsOutboundCallingNumberTranslationRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 아웃바운드 호출 번호 변환 규칙을 제거합니다. 아웃바운드 호출 번호 변환 규칙은 Lync Server 2013에서 사용하는 E.164 전화 번호를 E.164 번호를 지원하지 않는 트렁크 피어에서 사용할 수 있는 형식으로 변환합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsOutboundCallingNumberTranslationRule -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 site:Redmond/SevenDigit인 아웃바운드 호출 번호 변환 규칙을 제거합니다.

    Remove-CsOutboundCallingNumberTranslationRule -Identity "site:Redmond/SevenDigit"

## 예제 2

예제 2에서는 Redmond 사이트에 대해 구성된 모든 아웃바운드 호출 번호 변환 규칙을 제거합니다. 이 작업을 수행하기 위해 Identity 매개 변수를 포함하여 **Remove-CsOutboundCallingNumberTranslationRule** cmdlet을 호출합니다. 매개 변수 값 "site:Redmond"는 Redmond 사이트에 대해 구성된 모든 변환 규칙이 제거되도록 합니다.

    Remove-CsOutboundCallingNumberTranslationRule -Identity "site:Redmond"

## 예제 3

예제 3에서는 "^\\+1425(\\d{7})$" 패턴을 사용하는 모든 아웃바운드 호출 번호 변환 규칙을 삭제합니다. 이 작업을 수행하기 위해 먼저 **Get-CsOutboundCallingNumberTranslationRule** cmdlet을 사용하여 조직에서 사용되는 모든 변환 규칙의 컬렉션을 반환합니다. 이 컬렉션은 해당 Pattern 속성이 "^\\+1425(\\d{7})$"와 같은 규칙만 선택하는 Where-Object cmdlet에 파이프됩니다. 이렇게 필터링된 컬렉션은 컬렉션의 각 규칙을 삭제하는 **Remove-CsOutboundCallingNumberTranslationRule** cmdlet에 파이프됩니다.

    Get-CsOutboundCallingNumberTranslationRule | Where-Object {$_.Pattern -eq '^\+1425(\d{7})$'} | Remove-CsOutboundCallingNumberTranslationRule

## 자세한 정보

아웃바운드 호출 번호 변환 규칙은 Lync 2013에서 사용하는 E.164 전화 번호를 E.164 번호를 지원하지 않는 트렁크 피어가 사용할 수 있는 형식으로 변환합니다. 변환 규칙을 만들 때는 아웃바운드 E.164 번호를 나타내는 정규식(패턴)과 변환된 번호를 나타내는 정규식(변환)을 모두 지정합니다.

아웃바운드 호출 번호 변환 규칙은 트렁크 구성 설정의 컬렉션에 바인딩되어야 합니다. 새 변환 규칙을 만들 때는 트렁크 구성 설정의 ID와 새 규칙의 이름(예: site:Redmond/RedmondTranslationRule)을 모두 지정해야 합니다. 새 규칙을 만들 때 트렁크 구성 설정이 반드시 있어야 하는 것은 아닙니다. 예를 들어 site:Redmond/RedmondTranslationRule 규칙을 만드는데 Redmond 사이트에 대해 트렁크 구성 설정이 작성되지 않았다고 가정해 보겠습니다. 이 경우 Redmond 사이트가 유효한 사이트이면 트렁크 구성 설정이 사이트에 대해 자동으로 작성되며 새 변환 규칙이 해당 설정 컬렉션에 할당됩니다. 그러나 Redmond 사이트가 없으면 명령은 실패합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsOutboundCallingNumberTranslationRule"}

**Lync Server 제어판:**Lync Server 제어판을 사용하여 아웃바운드 호출 번호 변환 규칙을 제거하려면 음성 라우팅, 트렁크 구성을 차례로 클릭하고 이름 열에서 해당 항목을 두 번 클릭한 후에 트렁크 구성 편집 대화 상자에서 아래쪽의 레이블이 호출 번호 변환 역할인 섹션으로 스크롤합니다. 그런 다음 삭제할 규칙을 선택하고 제거를 클릭합니다.

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
<td><p>제거할 아웃바운드 변환 규칙의 고유한 식별자입니다. ID는 범위와 그 뒤에 오는 각 범위 내의 고유한 이름으로 구성됩니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;site:Redmond/OutboundRule1&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
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

**Remove-CsOutboundCallingNumberTranslationRule** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.CallingNumberTranslationRule\#Decorated 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsOutboundCallingNumberTranslationRule** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.CallingNumberTranslationRule\#Decorated 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsOutboundCallingNumberTranslationRule](get-csoutboundcallingnumbertranslationrule.md)  
[New-CsOutboundCallingNumberTranslationRule](new-csoutboundcallingnumbertranslationrule.md)  
[Set-CsOutboundCallingNumberTranslationRule](set-csoutboundcallingnumbertranslationrule.md)

