---
title: Get-CsOutboundCallingNumberTranslationRule
TOCTitle: Get-CsOutboundCallingNumberTranslationRule
ms:assetid: 65589388-f935-4d25-ae74-362be97c8597
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204962(v=OCS.15)
ms:contentKeyID: 49303859
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsOutboundCallingNumberTranslationRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하기 위해 만들어진 아웃바운드 호출 번호 변환 규칙에 대한 정보를 반환합니다. 아웃바운드 호출 번호 변환 규칙은 Lync Server 2013에서 사용하는 E.164 전화 번호를 E.164 번호를 지원하지 않는 트렁크 피어에서 사용할 수 있는 형식으로 변환합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsOutboundCallingNumberTranslationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsOutboundCallingNumberTranslationRule [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 현재 조직에서 사용하도록 구성된 모든 아웃바운드 호출 번호 변환 규칙에 대한 정보를 반환합니다.

    Get-CsOutboundCallingNumberTranslationRule

## 예제 2

예제 2에서는 ID가 "site:Redmond/SevenDigit"인 아웃바운드 호출 번호 변환 규칙에 대한 정보만 반환합니다.

    Get-CsOutboundCallingNumberTranslationRule -Identity "site:Redmond/SevenDigit"

## 예제 3

예제 3에서는 Redmond 사이트에 대해 구성된 모든 아웃바운드 호출 번호 변환 규칙에 대한 정보를 반환합니다. 이 작업은 Identity 매개 변수의 값을 Redmond 사이트의 ID(site:Redmond)로 설정하여 수행합니다.

    Get-CsOutboundCallingNumberTranslationRule -Identity "site:Redmond"

## 예제 4

예제 4에 표시된 명령은 Redmond 사이트에 있으며 Priority가 0과 같은 아웃바운드 호출 번호 변환 규칙에 대한 정보만 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsOutboundCallingNumberTranslationRule** cmdlet 및 Identity 매개 변수를 사용하여 Redmond 사이트에 할당된 모든 변환 규칙의 컬렉션을 반환합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프되며, 해당 cmdlet은 Priority가 0과 같은 규칙만 선택합니다.

    Get-CsOutboundCallingNumberTranslationRule -Identity "site:Redmond" | Where-Object {$_.Priority -eq 0}

## 자세한 정보

아웃바운드 호출 번호 변환 규칙은 Lync 2013에서 사용하는 E.164 전화 번호를 E.164 번호를 지원하지 않는 트렁크 피어가 사용할 수 있는 형식으로 변환합니다. 변환 규칙을 만들 때는 아웃바운드 E.164 번호를 나타내는 정규식(패턴)과 변환된 번호를 나타내는 정규식(변환)을 모두 지정합니다.

아웃바운드 호출 번호 변환 규칙은 트렁크 구성 설정의 컬렉션에 바인딩되어야 합니다. 새 변환 규칙을 만들 때는 트렁크 구성 설정의 ID와 새 규칙의 이름(예: site:Redmond/RedmondTranslationRule)을 모두 지정해야 합니다. 새 규칙을 만들 때 트렁크 구성 설정이 반드시 있어야 하는 것은 아닙니다. 예를 들어 site:Redmond/RedmondTranslationRule 규칙을 만드는데 Redmond 사이트에 대해 트렁크 구성 설정이 작성되지 않았다고 가정해 보겠습니다. 이 경우 Redmond 사이트가 유효한 사이트이면 트렁크 구성 설정이 사이트에 대해 자동으로 작성되며 새 변환 규칙이 해당 설정 컬렉션에 할당됩니다. 그러나 Redmond 사이트가 없으면 명령은 실패합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsOutboundCallingNumberTranslationRule"}

**Lync Server 제어판:**Lync Server 제어판에서 아웃바운드 호출 번호 변환 역할을 보려면 음성 라우팅, 트렁크 구성을 차례로 클릭하고 이름 열에서 해당 항목을 두 번 클릭한 후에 트렁크 구성 편집 대화 상자에서 아래쪽의 레이블이 호출 번호 변환 규칙인 섹션으로 스크롤합니다.

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>와일드카드 문자열과 일치하는 ID가 포함된 아웃바운드 변환 규칙만 반환할 수 있는 와일드카드 검색을 수행합니다. 예를 들어 다음 구문은 문자열 값 &quot;Redmond&quot;가 포함된 모든 변환 규칙을 반환합니다.</p>
<p>-Filter &quot;*Redmond*&quot;</p>
<p>사이트 범위에서 구성된 모든 변환 규칙을 반환하려면 다음 구문을 사용합니다.</p>
<p>-Filter &quot;site:*&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 아웃바운드 호출 번호 변환 규칙의 고유 식별자입니다. ID는 범위와 그 뒤에 오는 각 범위 내의 고유한 이름으로 구성됩니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;site:Redmond/OutboundRule1&quot;</p>
<p>Redmond 사이트 등의 특정 범위에 대해 구성된 모든 변환 규칙을 반환하려면 ID를 범위 자체로 설정하기만 하면 됩니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>Identity 매개 변수와 Filter 매개 변수를 모두 지정하지 않으면 <strong>Get-CsOutboundCallingNumberTranslationRule</strong> cmdlet은 모든 아웃바운드 호출 번호 변환 규칙에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 아웃바운드 호출 번호 변환 규칙 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsOutboundCallingNumberTranslationRule** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsOutboundCallingNumberTranslationRule** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.CallingNumberTranslationRule\#Decorated 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsOutboundCallingNumberTranslationRule](new-csoutboundcallingnumbertranslationrule.md)  
[Remove-CsOutboundCallingNumberTranslationRule](remove-csoutboundcallingnumbertranslationrule.md)  
[Set-CsOutboundCallingNumberTranslationRule](set-csoutboundcallingnumbertranslationrule.md)

