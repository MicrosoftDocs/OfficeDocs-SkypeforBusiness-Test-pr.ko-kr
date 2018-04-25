---
title: Set-CsDialPlan
TOCTitle: Set-CsDialPlan
ms:assetid: 80277dc6-8853-4cbd-87cb-e64f9e135d5f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398644(v=OCS.15)
ms:contentKeyID: 49304190
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsDialPlan

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 다이얼 플랜을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsDialPlan [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsDialPlan [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-City <String>] [-Confirm [<SwitchParameter>]] [-CountryCode <String>] [-Description <String>] [-DialinConferencingRegion <String>] [-ExternalAccessPrefix <String>] [-Force <SwitchParameter>] [-NormalizationRules <PSListModifier>] [-OptimizeDeviceDialing <$true | $false>] [-SimpleName <String>] [-State <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Set-CsDialPlan** cmdlet을 사용하여 ID가 RedmondDialPlan인 다이얼 플랜을 수정합니다. 이 경우 수정할 유일한 속성은 Description입니다. Description 매개 변수 다음에 새 설명에 대한 텍스트를 지정하여 수정합니다.

    Set-CsDialPlan -Identity RedmondDialPlan -Description "This plan is for Redmond-based users only."

## 예제 2

이 예제에서는 **Set-CsDialPlan** cmdlet을 사용하여 조직에 사용하도록 구성된 모든 다이얼 플랜에 대한 ExternalAccessPrefix 속성 값을 변경합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsDialPlan** cmdlet을 사용하여 조직의 모든 다이얼 플랜 컬렉션을 반환합니다. 그런 다음, 컬렉션의 각 프로필에 대한 ExternalAccessPrefix 속성에 값 8을 할당하는 **Set-CsDialPlan** cmdlet에 해당 컬렉션이 파이프됩니다.

    Get-CsDialPlan | Set-CsDialPlan -ExternalAccessPrefix 8

## 자세한 정보

이 cmdlet은 기존 다이얼 플랜(위치 프로필이라고도 함)을 수정합니다. 다이얼 플랜은 Enterprise Voice 사용자가 전화 통화를 할 수 있는 데 필요한 정보를 제공합니다. 또한 전화 접속 회의를 위해 회의 길잡이 응용 프로그램에서 다이얼 플랜이 사용됩니다. 다이얼 플랜은 어떤 정규화 규칙이 적용되는지, 외부 통화를 위해 접두사를 사용해야 하는지 여부 등을 결정합니다.

참고: 이 cmdlet을 사용하여 다이얼 플랜의 정규화 규칙을 수정할 수 있지만 **New-CsVoiceNormalizationRule** cmdlet, **Set-CsVoiceNormalizationRule** cmdlet 또는 **Remove-CsVoiceNormalizationRule** cmdlet을 대신 사용하는 것이 좋습니다. 이러한 cmdlet을 사용하면 변경 사항이 해당 다이얼 플랜에 반영됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsDialPlan** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsDialPlan"}

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
<td><p><em>City</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수는 이 cmdlet에 사용되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>CountryCode</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수는 이 cmdlet에 사용되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>다이얼 플랜의 목적, 다이얼 플랜이 적용되는 사용자의 유형, 다이얼 플랜의 목적을 식별하는 데 도움이 되는 기타 정보와 같은 이 다이얼 플랜에 대한 설명입니다.</p>
<p>최대 문자 길이: 512</p></td>
</tr>
<tr class="odd">
<td><p><em>DialinConferencingRegion</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 다이얼 플랜과 연관된 지역의 이름입니다. 전화 접속 회의에 다이얼 플랜을 사용할 경우 이 매개 변수 값을 지정합니다. 그러면 전화 회의 이끌이가 전화 회의를 설정할 때 올바른 액세스 번호를 할당할 수 있습니다. <strong>Get-CsNetworkRegion</strong> cmdlet을 호출하여 사용 가능한 지역을 검색할 수 있습니다.</p>
<p>최대 문자 길이: 512</p></td>
</tr>
<tr class="even">
<td><p><em>ExternalAccessPrefix</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>통화를 조직 외부 통화로 지정하는 번호(또는 번호 집합)입니다. (예를 들어, 외부 회선에 전화를 걸려면 먼저 9를 누릅니다.) 이 접두사는 정규화 규칙에서 무시되며 번호의 나머지 부분에는 이러한 규칙이 적용됩니다.</p>
<p>이 값을 적용하려면 OptimizeDeviceDialing 매개 변수를 True로 설정해야 합니다.</p>
<p>이 매개 변수 값은 정규식 [0-9]{1,4}와 일치해야 합니다. 즉, 길이가 1-4자리인 0-9 범위의 숫자 값이어야 합니다.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경을 수행하기 전에 확인 메시지가 표시되지 않도록 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 다이얼 플랜을 식별하기 위해 범위 또는 이름(사용자별 플랜의 경우)을 지정하는 고유한 식별자입니다. 예를 들어, 사이트 ID를 site:&lt;sitename&gt; 형식으로 입력할 수 있으며 여기서 sitename은 사이트의 이름입니다. 서비스 범위의 다이얼 플랜은 등록자 또는 PSTN 게이트웨이 서비스가 될 수 있으며 여기서 Identity 값의 형식은 Registrar:Redmond.litwareinc.com과 같습니다. 사용자별 ID는 고유한 문자열 값으로 입력됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>위치 프로필</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.<strong>Get-CsDialPlan</strong> cmdlet을 호출하여 이 개체 참조를 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NormalizationRules</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>이 다이얼 플랜에 적용되는 정규화 규칙의 목록입니다.</p>
<p>이 cmdlet을 사용하여 이 목록과 이러한 규칙을 직접 수정할 수 있지만 규칙을 만들어 지정한 다이얼 플랜에 할당하는 <strong>New-CsVoiceNormalizationRule</strong> cmdlet을 사용하여 정규화 규칙을 만들고 <strong>Set-CsVoiceNormalizationRule</strong> cmdlet을 사용하여 수정하는 것이 좋습니다.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>OptimizeDeviceDialing</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 매개 변수를 True로 설정하면 조직 외부에서 걸려온 전화에 ExternalAccessPrefix 매개 변수의 접두사가 적용됩니다. ExternalAccessPrefix 매개 변수가 값이 지정된 경우에만 이 값을 True로 설정할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SimpleName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>다이얼 플랜의 이름입니다. 다이얼 플랜 이름은 Lync Server 배포 내의 모든 다이얼 플랜에서 고유해야 합니다.</p>
<p>이 문자열은 최대 256자일 수 있습니다. 유효한 문자는 알파벳 문자 또는 숫자, 하이픈(-), 점(.), 더하기(+), 밑줄(_) 및 괄호(())입니다.</p>
<p></p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile 개체입니다. 다이얼 플랜 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsDialPlan** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[New-CsDialPlan](new-csdialplan.md)  
[Remove-CsDialPlan](remove-csdialplan.md)  
[Get-CsDialPlan](get-csdialplan.md)  
[Grant-CsDialPlan](grant-csdialplan.md)  
[Test-CsDialPlan](test-csdialplan.md)  
[New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)  
[Set-CsVoiceNormalizationRule](set-csvoicenormalizationrule.md)  
[Remove-CsVoiceNormalizationRule](remove-csvoicenormalizationrule.md)  
[Get-CsVoiceNormalizationRule](get-csvoicenormalizationrule.md)

