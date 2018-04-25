---
title: New-CsDialPlan
TOCTitle: New-CsDialPlan
ms:assetid: 3889c696-1070-47bd-beb9-da7e18ec90f0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425860(v=OCS.15)
ms:contentKeyID: 49303322
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsDialPlan

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 다이얼 플랜을 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsDialPlan -Identity <XdsIdentity> [-City <String>] [-Confirm [<SwitchParameter>]] [-CountryCode <String>] [-Description <String>] [-DialinConferencingRegion <String>] [-ExternalAccessPrefix <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-NormalizationRules <PSListModifier>] [-OptimizeDeviceDialing <$true | $false>] [-SimpleName <String>] [-State <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Identity가 RedmondDialPlan인 새 다이얼 플랜을 만듭니다. (Identity 값에 범위가 없으면 사용자별 정책이라는 것을 나타냅니다. 사용자별 범위에서 만들어진 다이얼 플랜은 사용자 및 그룹에 직접 할당할 수 있습니다.) 다이얼 플랜의 다른 모든 속성에는 기본값이 할당됩니다.

    New-CsDialPlan -Identity RedmondDialPlan

## 예제 2

예제 2에 표시된 명령은 ID가 site:Redmond(즉, Redmond 사이트에서 사용자별 또는 서비스 수준 다이얼 플랜이 적용되지 않은 모든 사용자에게 다이얼 플랜이 적용됨)이고 SimpleName이 RedmondSiteDialPlan인 새 다이얼 플랜을 만들었습니다. 예제의 다음 줄은 해당 플랜과 연결된 새 정규화 규칙을 만듭니다. 다이얼 플랜에 대해 기본 정규화 규칙이 만들어지지만 대부분 자리 표시자로 만들어지므로 값 사용이 제한적입니다. 따라서 **New-CsDialPlan** cmdlet을 호출하여 새 다이얼 플랜을 만든 후 **New-CsVoiceNormalizationRule** cmdlet을 호출하여 조직에 적합한 명명된 규칙을 만들어야 합니다. 이 예제의 둘째 줄에서는 **New-CsVoiceNormalizationRule** cmdlet을 호출하고 이름이 SeattlePrefix인 Redmond 사이트 규칙을 만들고 이 규칙의 Pattern 및 Translation 속성을 지정합니다. 다이얼 플랜을 수정하기 위한 추가 단계는 필요하지 않습니다. 정규화 규칙에 대한 변경 내용은 정규화 규칙의 ID와 일치하는 ID를 가진 다이얼 플랜에 자동으로 적용됩니다. ID의 site:Redmond 부분은 다이얼 플랜 ID와 일치하고 SeattlePrefix는 정규화 규칙의 이름입니다. 여러 개의 정규화 규칙을 하나의 다이얼 플랜에 적용할 수 있으므로 각 정규화 규칙에는 지정된 범위 내에서 고유한 이름이 필요합니다.

    New-CsDialPlan -Identity site:Redmond -SimpleName RedmondSiteDialPlan
    New-CsVoiceNormalizationRule -Identity "site:Redmond/SeattlePrefix" -Pattern "^9(\d*){1,5}$" -Translation "+1206$1"

## 예제 3

예제 3에 표시된 명령은 ID가 RedmondDialPlan인 새 다이얼 플랜을 만들고 Description에 이 다이얼 플랜의 용도에 대한 설명을 지정합니다. (사용자별 범위에서 만들어진 다이얼 플랜은 사용자 및 그룹에 직접 할당할 수 있습니다.) 다른 모든 매개 변수에는 기본값이 할당됩니다.

    New-CsDialPlan -Identity RedmondDialPlan -Description "Dial plan for Redmond users"

## 자세한 정보

이 cmdlet은 새 다이얼 플랜(위치 프로필이라고도 함)을 만듭니다. 다이얼 플랜은 Enterprise Voice 사용자가 전화 통화를 할 수 있는 데 필요한 정보를 제공합니다. 또한 전화 접속 회의를 위해 회의 길잡이 응용 프로그램에서 다이얼 플랜이 사용됩니다. 다이얼 플랜은 적용되는 정규화 규칙 및 외부 통화를 위해 접두사를 사용해야 하는지 여부와 같은 사항을 결정합니다.

다이얼 플랜을 만들면 기본 음성 정규화 규칙이 자동으로 만들어집니다. 정규화 규칙은 **Set-CsVoiceNormalizationRule** cmdlet을 호출하여 수정할 수 있습니다. 새 정규화 규칙은 **New-CsVoiceNormalizationRule** cmdlet을 호출하여 다이얼 플랜에 추가할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsDialPlan** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsDialPlan"}

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
<td><p>다이얼 플랜을 식별하기 위해 범위 및 이름(사이트), 서비스 역할 및 FQDN 또는 이름(사용자별)을 지정하는 고유 식별자입니다. 예를 들어, 사이트 ID를 site:&lt;sitename&gt; 형식으로 입력할 수 있으며 여기서 sitename은 사이트의 이름입니다. 서비스 범위의 다이얼 플랜은 등록자 또는 PSTN 게이트웨이 서비스여야 하며 여기서 Identity 값의 형식은 Registrar:Redmond.litwareinc.com과 같습니다. 사용자별 ID는 고유 문자열 값으로 입력됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>City</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수는 이 cmdlet에 사용되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CountryCode</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수는 이 cmdlet에 사용되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>다이얼 플랜의 목적, 다이얼 플랜이 적용되는 사용자의 유형, 다이얼 플랜의 목적을 식별하는 데 도움이 되는 기타 정보와 같은 이 다이얼 플랜에 대한 설명입니다.</p>
<p>최대 문자 길이: 512</p></td>
</tr>
<tr class="even">
<td><p><em>DialinConferencingRegion</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 다이얼 플랜과 연관된 지역의 이름입니다. 전화 접속 회의에 다이얼 플랜을 사용할 경우 이 매개 변수 값을 지정합니다. 그러면 전화 회의 이끌이가 전화 회의를 설정할 때 올바른 액세스 번호를 할당할 수 있습니다. <strong>Get-CsNetworkRegion</strong> cmdlet을 호출하여 사용 가능한 지역을 검색할 수 있습니다.</p>
<p>최대 문자 길이: 512</p></td>
</tr>
<tr class="odd">
<td><p><em>ExternalAccessPrefix</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>통화를 조직 외부 통화로 지정하는 번호(또는 번호 집합)입니다. (예를 들어, 외부 회선에 전화를 걸려면 먼저 9를 누릅니다.) 이 접두사는 정규화 규칙에서 무시되며 번호의 나머지 부분에는 이러한 규칙이 적용됩니다.</p>
<p>이 값을 적용하려면 OptimizeDeviceDialing 매개 변수를 True로 설정해야 합니다.</p>
<p>이 매개 변수는 정규식 [0-9]{1,4}와 일치해야 합니다. 즉, 길이가 1-4자리인 0-9 값이어야 합니다.</p>
<p>기본값: 9</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경 작업을 수행하기 전에 모든 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NormalizationRules</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>이 다이얼 플랜에 적용되는 정규화 규칙의 목록입니다.</p>
<p>이 cmdlet을 사용하여 이 목록과 이러한 규칙을 직접 만들 수 있지만 규칙을 만들어 지정한 다이얼 플랜에 할당하는 <strong>New-CsVoiceNormalizationRule</strong> cmdlet을 사용하여 정규화 규칙을 만드는 것이 좋습니다.</p>
<p>새 다이얼 플랜이 만들어질 때마다 해당 사이트, 서비스 또는 사용자별 다이얼 플랜에 대한 기본 설정이 적용된 새 음성 정규화 규칙이 만들어집니다. 기본적으로 새 음성 정규화 규칙의 ID는 다이얼 플랜 ID와 슬래시, 그리고 Prefix All 이름으로 구성됩니다(예: site:Redmond/Prefix All).</p>
<p>기본값: {Description=;Pattern=^(\d11)$;Translation=+$1;Name=Prefix All;IsInternalExtension=False } 참고: 이 기본값은 자리 표시자일 뿐입니다. 다이얼 플랜을 유용하게 사용하려면 다이얼 플랜에 의해 만들어진 정규화 규칙을 수정하거나 사이트, 서비스 또는 사용자에 대한 새 규칙을 만들어야 합니다. <strong>New-CsVoiceNormalizationRule</strong> cmdlet을 호출하여 새 정규화 규칙을 만들고, <strong>Set-CsVoiceNormalizationRule</strong> cmdlet을 호출하여 정규화 규칙을 수정할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>OptimizeDeviceDialing</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 매개 변수를 True로 설정하면 조직 외부에서 걸려온 전화에 ExternalAccessPrefix 매개 변수의 접두사가 적용됩니다. ExternalAccessPrefix 매개 변수가 값이 지정된 경우에만 이 값을 True로 설정할 수 있습니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="even">
<td><p><em>SimpleName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>다이얼 플랜의 표시 이름입니다. 이 이름은 Lync Server 배포 내의 모든 다이얼 플랜에서 고유해야 합니다.</p>
<p>이 문자열은 최대 256자일 수 있습니다. 유효한 문자는 알파벳 문자 또는 숫자, 하이픈(-), 점(.), 더하기(+), 밑줄(_) 및 괄호(())입니다.</p>
<p>이 매개 변수는 값을 포함해야 합니다. 그러나 값을 지정하지 않고 <strong>New-CsDialPlan</strong> cmdlet을 호출하면 기본값이 제공됩니다. 전역 다이얼 플랜의 기본값은 Prefix All입니다. 사이트 수준 다이얼 플랜의 기본값은 사이트의 이름입니다. 서비스의 기본값은 서비스 이름(등록자 또는 PSTN 게이트웨이)과 밑줄, 그리고 서비스의 FQDN(정규화된 도메인 이름입니다)으로 구성됩니다(예: Registrar_pool0.litwareinc.com). 사용자별 다이얼 플랜의 기본값은 다이얼 플랜의 ID입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>State</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수는 이 cmdlet에 사용되지 않습니다.</p></td>
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

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsDialPlan](remove-csdialplan.md)  
[Set-CsDialPlan](set-csdialplan.md)  
[Get-CsDialPlan](get-csdialplan.md)  
[Grant-CsDialPlan](grant-csdialplan.md)  
[Test-CsDialPlan](test-csdialplan.md)  
[New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)  
[Set-CsVoiceNormalizationRule](set-csvoicenormalizationrule.md)  
[Remove-CsVoiceNormalizationRule](remove-csvoicenormalizationrule.md)  
[Get-CsVoiceNormalizationRule](get-csvoicenormalizationrule.md)

