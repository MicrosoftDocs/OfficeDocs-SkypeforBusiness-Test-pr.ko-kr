---
title: Set-CsDialInConferencingAccessNumber
TOCTitle: Set-CsDialInConferencingAccessNumber
ms:assetid: 2b640607-ee83-4962-865d-ed74ddd17649
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425770(v=OCS.15)
ms:contentKeyID: 49303154
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsDialInConferencingAccessNumber

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 전화 접속 회의 액세스 번호의 속성 값을 수정합니다. 전화 접속 회의를 사용하면 사용자가 "일반" 전화기, 휴대폰 또는 PSTN(공중 전화망)의 다른 장치를 사용하여 전화 회의의 오디오 부분에 참가할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsDialInConferencingAccessNumber -Identity <UserIdParameter> [-DisplayName <String>] [-DisplayNumber <String>] [-LineUri <String>] [-PrimaryLanguage <String>] [-Regions <MultiValuedProperty>] [-ScopeToGlobal <SwitchParameter>] [-ScopeToSite <SwitchParameter>] [-SecondaryLanguages <MultiValuedProperty>] <COMMON PARAMETERS>

    Set-CsDialInConferencingAccessNumber -Identity <UserIdParameter> -Priority <Int32> -ReorderedRegion <String> <COMMON PARAMETERS>

    Set-CsDialInConferencingAccessNumber -Instance <AccessNumber> [-ScopeToGlobal <SwitchParameter>] [-ScopeToSite <SwitchParameter>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Identity가 sip:RedmondDialIn@litwareinc.com인 전화 접속 회의 액세스 번호의 DisplayName 속성을 수정합니다. 이 예제에서는 표시 이름이 "Redmond Dial-In Access Number"로 설정됩니다.

    Set-CsDialInConferencingAccessNumber -Identity "sip:RedmondDialIn@litwareinc.com" -DisplayName "Redmond Dial-In Access Number"

## 예제 2

예제 2에서는 Identity가 sip:RedmondDialIn@litwareinc.com인 전화 접속 회의 액세스 번호가 Redmond와 Seattle의 두 지역을 포함하도록 수정됩니다. 이 작업을 수행하기 위해 Region 매개 변수를 호출하고 뒤에 두 지역(쉼표로 구분된 두 개의 문자열 값)을 포함합니다. Redmond 및 Seattle 지역이 다이얼 플랜에 모두 정의되어 있지 않으면 이 명령은 실패합니다.

    Set-CsDialInConferencingAccessNumber -Identity "sip:RedmondDialIn@litwareinc.com" -Regions "Redmond", "Seattle"

## 예제 3

예제 3에서는 기본 언어가 프랑스어인 모든 전화 접속 회의 액세스 번호에 프랑스어(캐나다)가 보조 언어로 사용되도록 수정합니다. 이 작업을 수행하기 위해 먼저 **Get-CsDialInConferencingAccessNumber** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 전화 접속 액세스 번호 컬렉션을 반환합니다. 이 컬렉션은 PrimaryLanguage 속성이 프랑스어("fr-FR")와 같은 액세스 번호를 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 SecondaryLanguages 속성 값을 프랑스어(캐나다)("fr-CA")로 설정하는 **Set-CsDialInConferencingAccessNumber** cmdlet에 파이프됩니다.

    Get-CsDialInConferencingAccessNumber | Where-Object {$_.PrimaryLanguage -eq "fr-FR"}| Set-CsDialInConferencingAccessNumber -SecondaryLanguages "fr-CA"

## 예제 4

예제 4에 표시된 명령은 지정한 전화 접속 회의 액세스 번호의 Active Directory 표시 이름을 변경합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsDialInConferencingAccessNumber** cmdlet 및 Filter 매개 변수를 사용하여 DisplayName 속성이 "Default DialIn Access Number"와 같은 전화 접속 액세스 번호를 반환합니다. 이 액세스 번호는 표시 이름을 Litwareinc Conferencing으로 변경하는 **Set-CsDialInConferencingAccessNumber** cmdlet에 파이프됩니다.

    Get-CsDialInConferencingAccessNumber -Filter {DisplayName -eq "Default DialIn Access Number"} | Set-CsDialInConferencingAccessNumber -DisplayName "Litwareinc Conferencing"

## 예제 5

예제 5에서는 지정한 전화 접속 회의 액세스 번호의 표시 이름과 회선 URI(Uniform Resource Identifier)를 둘 다 수정합니다. 수정할 번호를 검색하기 위해 먼저 **Get-CsDialInConferencingAccessNumber** cmdlet 및 Filter 매개 변수를 사용합니다. 사용된 필터 값은 LineUri 속성이 TEL:+14255558715와 같은 액세스 번호에 대한 데이터만 반환되도록 제한합니다. 이 액세스 번호는 액세스 번호의 DisplayNumber 및 LineUri 속성을 둘 다 수정하는 **Set-CsDialInConferencingAccessNumber** cmdlet에 파이프됩니다.

    Get-CsDialInConferencingAccessNumber -Filter {LineUri -eq "TEL:+14255558715"} | Set-CsDialInConferencingAccessNumber -DisplayNumber "1-425-555-1298" -LineUri "tel:+14255551298"

## 예제 6

예제 6에서는 미국 영어를 기본 언어로 사용하지 않는 모든 전화 접속 회의 액세스 번호에 한 쌍의 보조 언어를 할당합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsDialInConferencingAccessNumber** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 전화 접속 회의 액세스 번호 컬렉션을 반환합니다. 이 컬렉션은 PrimaryLanguage 속성이 미국 영어(en-US)와 같지 않은 번호만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 -SecondaryLanguages 매개 변수를 사용하여 컬렉션의 각 번호에 보조 언어 프랑스어(fr-FR)와 이탈리아어(it-IT)를 할당하는 **Set-CsDialInConferencingAccessNumber** cmdlet에 파이프됩니다.

    Get-CsDialInConferencingAccessNumber | Where-Object {$_.PrimaryLanguage -ne "en-US"} | Set-CsDialInConferencingAccessNumber -SecondaryLanguages "fr-FR","it-IT"

## 예제 7

예제 7에 표시된 명령은 전화 접속 회의 액세스 번호 "sip:RedmondDialIn@litwareinc.com"에 Redmond 지역에서 가장 높은 우선 순위를 할당합니다. 그러면 이 번호가 모임 초대 및 전화 접속 회의 웹 페이지에 첫 번째로 나열됩니다. 우선 순위를 설정하기 위해 매개 변수 값 0과 함께 Priority 매개 변수를 포함합니다. 우선 순위가 가장 높은 액세스 번호의 Priority 값은 0이고, 우선 순위가 두 번째로 높은 번호의 Priority 값은 1입니다. 또한 Redmond 지역 내에서 액세스 번호 우선 순위가 변경됨을 나타내기 위해 ReorderedRegion 매개 변수를 포함합니다.

    Get-CsDialInConferencingAccessNumber -Identity ""sip:RedmondDialIn@litwareinc.com"" -Priority 0 -ReorderedRegion Redmond

## 자세한 정보

전화 접속 회의를 통해 사용자는 모든 종류의 전화기(예: 표준 "유선 전화", 휴대폰, VoIP(Voice over Internet Protocol) 전화 등)를 사용하여 전화 회의의 오디오 부분에 참가할 수 있습니다. 그러면 컴퓨터나 인터넷 연결이 없어도 모임에 참가할 수 있습니다. 전화 접속 사용자는 모든 오디오 기능을 이용할 수 있습니다. 즉, 다른 참가자에게 말하고 모든 내용을 들을 수 있습니다. 다만, 공유 슬라이드, 비디오 피드 또는 기타 시각적 요소를 볼 수는 없습니다.

사용자에게 전화 접속 회의 기능을 제공하려면 전화 접속 회의 액세스 번호를 만들어야 합니다. 사용자가 모임에 연결하기 위해 전화를 걸어야 하는 전화 번호입니다. 전화 접속 회의 액세스 번호는 **New-CsDialInConferencingAccessNumber** cmdlet을 사용하여 만듭니다. 새 전화 접속 회의 액세스 번호를 만들면 실제로 Active Directory 도메인 서비스에 새 연락처 개체가 만들어집니다. 이 연락처 개체는 액세스 번호와 모든 해당 속성을 나타내는 데 사용됩니다.

전화 접속 회의 번호를 만든 후 **Set-CsDialInConferencingAccessNumber** cmdlet을 사용하여 해당 번호의 속성을 수정할 수 있습니다. 예를 들어 전화 번호(LineUri) 자체 등을 변경하거나 해당 번호를 나타내는 연락처 개체의 표시 이름을 변경할 수 있습니다. 또한 **Set-CsDialInConferencingAccessNumber** cmdlet을 사용하여 번호의 범위를 수정할 수 있습니다. 예를 들어 이 cmdlet을 사용하여 전역 범위에 할당된 번호를 가져온 다음 사이트 범위에 다시 할당할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsDialInConferencingAccessNumber** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsDialInConferencingAccessNumber"}

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
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>전화 접속 회의 번호를 나타내는 연락처 개체의 SIP 주소입니다. Identity를 지정하는 경우 &quot;sip:&quot; 접두사를 포함해야 합니다(예: -Identity &quot; sip:RedmondDialIn@litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.AccessNumber</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Priority</em></p></td>
<td><p>필수</p></td>
<td><p>System.Int32</p></td>
<td><p>모임 초대 시 또는 전화 접속 회의 설정 웹 페이지에 액세스할 때 사용자에게 전화 접속 회의 번호가 제공되는 순서를 변경할 수 있습니다. 번호가 낮을수록 우선 순위가 높습니다. 목록의 시작 부분에 번호를 표시하려면 우선 순위를 0으로 설정합니다. 지정된 번호의 우선 순위를 변경하는 경우 ReorderedRegion 매개 변수를 사용하여 변경된 우선 순위를 적용할 지역도 지정해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ReorderedRegion</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>지역이 포함된 전화 접속 회의 번호의 우선 순위를 변경할 때 Priority 매개 변수와 함께 사용됩니다. ReorderedRegion 매개 변수는 우선 순위가 다시 조정되는 지역을 나타냅니다(예: -ReorderedRegion &quot;Redmond&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisplayName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>새 연락처 개체의 Active Directory 표시 이름입니다. 또한 이 이름은 Lync에 나타납니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>모임 초대 및 전화 접속 회의 설정 웹 페이지에 표시되는 전화 번호입니다. DisplayNumber는 원하는 형식으로 지정할 수 있습니다. 예를 들어 1-800-555-1234, 1-(800)-555-1234, 1.800.555.1234 등으로 지정할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LineUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>실제 전화 접속 회의 전화 번호입니다. LineUri는 tel: 접두사를 시작으로 더하기(+) 기호, 국가 번호, 지역 번호 및 전화 번호가 차례로 뒤에 오는 구문을 사용하여 지정해야 합니다 예: tel:+18005551234). 공백, 하이픈, 괄호 및 기타 문자는 허용되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>수정된 전화 접속 회의 액세스 번호를 나타내는 파이프라인을 통해 대화 상대 개체를 전달하는 데 사용됩니다. 기본적으로 <strong>Set-CsDialInConferencingAccessNumber</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PrimaryLanguage</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>전화 접속 회의 알림에 사용되는 기본 언어입니다. 이 언어는 사용 가능한 전화 접속 회의 언어 코드 중 하나를 사용하여 구성해야 합니다(예: 미국 영어의 경우 en-US, 프랑스어의 경우 fr-FR 등). 사용 가능한 언어 코드 목록을 반환하려면 Windows PowerShell 프롬프트에 다음 명령을 입력합니다.</p>
<p>Get-CsDialInConferencingLanguageList | Select-Object -ExpandProperty Languages.</p></td>
</tr>
<tr class="odd">
<td><p><em>Regions</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.MultiValuedProperty</p></td>
<td><p>전화 접속 번호에 연결된 다이얼 플랜 지역입니다. 지역이 하나 이상의 다이얼 플랜에 포함되지 않은 경우에는 전화 접속 회의 액세스 번호에 연결할 수 없습니다. 여러 개의 지역을 지정하려면 쉼표로 구분된 목록을 사용합니다(예: -Regions &quot;Northwest&quot;, &quot;Southwest&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>ScopeToGlobal</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 전화 접속 회의 번호가 전역 범위에 할당됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ScopeToSite</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 전화 접속 회의 번호의 범위가 연락처 개체의 등록자 풀이 있는 사이트로 지정됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SecondaryLanguages</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.MultiValuedProperty</p></td>
<td><p>전화 접속 회의 알림에 사용할 수 있는 선택적 언어 컬렉션입니다. 보조 언어는 쉼표로 구분된 언어 코드 목록으로 구성되어야 합니다. 예를 들어 -SecondaryLanguages &quot;fr-CA&quot;, &quot;fr-FR&quot; 구문은 프랑스어(캐나다)와 프랑스어를 보조 언어로 설정합니다.</p>
<p>하나의 액세스 번호에 최대 4개의 보조 언어를 연결할 수 있습니다.</p></td>
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

Microsoft.Rtc.Management.Xds.AccessNumber 개체입니다. **Set-CsDialInConferencingAccessNumber** cmdlet은 액세스 번호 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsDialInConferencingAccessNumber** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.Xds.AccessNumber 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsDialInConferencingAccessNumber](get-csdialinconferencingaccessnumber.md)  
[New-CsDialInConferencingAccessNumber](new-csdialinconferencingaccessnumber.md)  
[Remove-CsDialInConferencingAccessNumber](remove-csdialinconferencingaccessnumber.md)

