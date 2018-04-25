---
title: Remove-CsVoiceNormalizationRule
TOCTitle: Remove-CsVoiceNormalizationRule
ms:assetid: 6a1bf26c-d95b-4a03-8d2d-c17159dcb9be
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398501(v=OCS.15)
ms:contentKeyID: 49303917
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsVoiceNormalizationRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

음성 정규화 규칙을 제거합니다. 음성 정규화 규칙은 전화 걸기 요구 사항(예: 외부 회선에 액세스하기 위해 9번 걸기)을 Lync Server에 사용되는 E.164 전화 번호 형식으로 변환하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsVoiceNormalizationRule -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 ID가 site:Redmond/SeattleRule1인 음성 정규화 규칙을 제거합니다.

    Remove-CsVoiceNormalizationRule -Identity site:Redmond/SeattleRule1

## 예제 2

이 예제에서는 사이트 Redmond에서 모든 음성 정규화 규칙을 제거합니다.

    Remove-CsVoiceNormalizationRule -Identity site:Redmond

## 자세한 정보

이 cmdlet은 명명된 음성 정규화 규칙을 제거합니다. 이러한 규칙은 전화 권한 부여 및 통화 경로 지정의 필수 부분입니다. 이러한 규칙은 번호를 내부 Lync Server 형식에서 표준(E.164) 형식으로 변환하기 위한 요구 사항을 정의합니다. 정규식을 이해하면 변환될 숫자 패턴을 정의하는 데 도움이 됩니다.

이 cmdlet을 사용하여 제거한 규칙은 조직의 다이얼 플랜에서 삭제되므로 **Get-CsVoiceNormalizationRule** cmdlet에 의해 반환되지 않으며 **Get-CsDialPlan** cmdlet을 호출하여 반환되는 NormalizationRules 속성에 표시되지 않습니다. 즉, **Remove-CsVoiceNormalizationRule** cmdlet을 호출하여 정규화 규칙이 없는 다이얼 플랜을 남겨둘 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsVoiceNormalizationRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsVoiceNormalizationRule"}

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
<td><p>제거할 규칙의 고유한 ID입니다. 지정한 ID에 범위, 슬래시 및 이름이 순서대로 포함된 경우(예: site:Redmond/Rule1, 여기서 site:Redmond는 범위, Rule1은 이름) 고유한 해당 ID가 있는 하나의 규칙이 제거됩니다. ID에 전달되는 값에 범위(site:Redmond)만 포함된 경우 해당 범위의 모든 정규화 규칙이 제거됩니다.</p></td>
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
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule 개체입니다. 음성 정규화 규칙 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule 유형의 개체를 삭제합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)  
[Set-CsVoiceNormalizationRule](set-csvoicenormalizationrule.md)  
[Get-CsVoiceNormalizationRule](get-csvoicenormalizationrule.md)  
[Test-CsVoiceNormalizationRule](test-csvoicenormalizationrule.md)  
[Remove-CsDialPlan](remove-csdialplan.md)  
[Get-CsDialPlan](get-csdialplan.md)

