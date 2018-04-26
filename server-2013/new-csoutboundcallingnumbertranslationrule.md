---
title: New-CsOutboundCallingNumberTranslationRule
TOCTitle: New-CsOutboundCallingNumberTranslationRule
ms:assetid: 959591bb-4a6b-4b7f-9666-da1fa0f9cd43
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205097(v=OCS.15)
ms:contentKeyID: 49304433
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsOutboundCallingNumberTranslationRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 아웃바운드 호출 번호 변환 규칙을 만듭니다. 아웃바운드 호출 번호 변환 규칙은 Lync Server 2013에서 사용하는 E.164 전화 번호를 E.164 번호를 지원하지 않는 트렁크 피어에서 사용할 수 있는 형식으로 변환합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsOutboundCallingNumberTranslationRule -Name <String> -Parent <String> <COMMON PARAMETERS>

    New-CsOutboundCallingNumberTranslationRule -Identity <XdsIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Pattern <String>] [-Priority <Int32>] [-Translation <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 문자열 값 +1206으로 시작하는 E.164 번호(예: +12065551219)를 7자리 값(예: +1206이 삭제된 5551219)으로 변환하는 새 아웃바운드 호출 번호 변환 규칙을 만듭니다.

    New-CsOutboundCallingNumberTranslationRule -Parent "site:Redmond" -Name SevenDigit -Description "Converts a dialed number to seven digits" -Pattern '^\+1206(\d{7})$' -Translation '$1'

## 자세한 정보

아웃바운드 호출 번호 변환 규칙은 Lync 2013에서 사용하는 E.164 전화 번호를 E.164 번호를 지원하지 않는 트렁크 피어가 사용할 수 있는 형식으로 변환합니다. 변환 규칙을 만들 때는 아웃바운드 E.164 번호를 나타내는 정규식(패턴)과 변환된 번호를 나타내는 정규식(변환)을 모두 지정합니다.

아웃바운드 호출 번호 변환 규칙은 트렁크 구성 설정의 컬렉션에 바인딩되어야 합니다. 새 변환 규칙을 만들 때는 트렁크 구성 설정의 ID와 새 규칙의 이름(예: site:Redmond/RedmondTranslationRule)을 모두 지정해야 합니다. 새 규칙을 만들 때 트렁크 구성 설정이 반드시 있어야 하는 것은 아닙니다. 예를 들어 site:Redmond/RedmondTranslationRule 규칙을 만드는데 Redmond 사이트에 대해 트렁크 구성 설정이 작성되지 않았다고 가정해 보겠습니다. 이 경우 Redmond 사이트가 유효한 사이트이면 트렁크 구성 설정이 사이트에 대해 자동으로 작성되며 새 변환 규칙이 해당 설정 컬렉션에 할당됩니다. 그러나 Redmond 사이트가 없으면 명령은 실패합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsOutboundCallingNumberTranslationRule"}

**Lync Server 제어판:**Lync Server 제어판을 사용하여 새 아웃바운드 호출 번호 변환 규칙을 만들려면 음성 라우팅, 트렁크 구성을 차례로 클릭하고 이름 열에서 해당 항목을 두 번 클릭합니다. 그런 다음 트렁크 구성 편집 대화 상자에서 아래쪽의 레이블이 호출 번호 변환 규칙인 섹션으로 스크롤하여 새로 만들기를 클릭합니다.

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
<td><p>새 변환 규칙의 고유 식별자입니다. 이름은 범위(상위 항목), &quot;/&quot; 문자 및 해당 범위 내의 고유한 이름으로 구성됩니다. 예를 들어 Redmond 사이트용으로 작성된 이름이 RedmondDialing인 규칙의 ID는 다음과 같습니다.</p>
<p>-Identity &quot;site:Redmond/RedmondDialing&quot;</p>
<p>Identity 매개 변수를 사용하는 경우에는 명령에 Parent 또는 Name 매개 변수를 포함할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 변환 규칙의 이름입니다. 이름은 지정된 범위에 대해 고유해야 합니다. 예를 들면 다음과 같습니다.</p>
<p>-Name &quot;RedmondDialing&quot;</p>
<p>Name 매개 변수를 사용하는 경우에는 Parent 매개 변수도 사용해야 합니다. Name 매개 변수를 Identity 매개 변수와 같은 명령에서 사용할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Parent</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 변환 규칙을 구성할 범위입니다. 전역 범위에서 규칙을 구성하려면 다음 구문을 사용합니다.</p>
<p>-Parent &quot;global&quot;</p>
<p>사이트 범위에서 규칙을 구성하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Parent &quot;site:Redmond&quot;</p>
<p>서비스 범위에서 규칙을 구성하려면(PstnGateway 서비스에만 해당됨) 다음과 같은 구문을 사용합니다.</p>
<p>-Parent &quot;service:PstnGateway:192.168.0.100&quot;</p>
<p>Parent 매개 변수를 사용하는 경우에는 Name 매개 변수도 사용해야 합니다. Parent 매개 변수를 Identity 매개 변수와 같은 명령에서 사용할 수는 없습니다.</p></td>
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
<td><p>관리자가 변환 규칙과 함께 표시할 추가 텍스트를 제공할 수 있습니다. 이 설명은 관리자가 규칙의 목적을 명확하게 파악하는 데 유용합니다.</p></td>
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
<td><p>개체를 실제로 영구 변경 내용으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수를 사용하여 호출된 이 cmdlet의 출력을 변수에 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 내용을 커밋할 수 있습니다.</p></td>
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

없음. **New-CsOutboundCallingNumberTranslationRule** cmdlet은 파이프라인된 데이터를 허용하지 않습니다.

## 반환 형식

**New-CsOutboundCallingNumberTranslationRule** cmdlet 은 Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.CallingNumberTranslationRule\#Decorated 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsOutboundCallingNumberTranslationRule](get-csoutboundcallingnumbertranslationrule.md)  
[Remove-CsOutboundCallingNumberTranslationRule](remove-csoutboundcallingnumbertranslationrule.md)  
[Set-CsOutboundCallingNumberTranslationRule](set-csoutboundcallingnumbertranslationrule.md)

