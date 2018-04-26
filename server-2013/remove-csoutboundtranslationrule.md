---
title: Remove-CsOutboundTranslationRule
TOCTitle: Remove-CsOutboundTranslationRule
ms:assetid: 73e0bd0d-2458-464a-9e6e-1868143aadc8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398556(v=OCS.15)
ms:contentKeyID: 49304036
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsOutboundTranslationRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 아웃바운드 변환 규칙을 제거합니다. 아웃바운드 변환 규칙은 PBX(Private Branch Exchange) 시스템과 상호 작용하기 위해 전화 번호를 로컬 전화 번호 형식으로 변환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsOutboundTranslationRule -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 사이트 Redmond(이름: Prefix Redmond)에 대한 기존의 아웃바운드 변환 규칙을 제거합니다. ID는 고유하므로 이 명령은 단일 규칙을 삭제합니다.

    Remove-CsOutboundTranslationRule -Identity "site:Redmond/Prefix Redmond"

## 예제 2

이 예제에서는 모든 사이트 수준 아웃바운드 변환 규칙을 제거합니다. 먼저 **Get-CsOutboundTranslationRule** cmdlet을 필터 site:\*와 함께 호출하여 site:으로 시작하는 ID 값이 포함된 모든 규칙의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션에서 각 규칙을 제거하는 **Remove-CsOutboundTranslationRule** cmdlet에 파이프됩니다.

    Get-CsOutboundTranslationRule -Filter site:* | Remove-CsOutboundTranslationRule

## 자세한 정보

기존 아웃바운드 변환 규칙을 제거하려면 이 cmdlet을 호출합니다. Lync Server는 전화 번호를 E.164 형식으로 정규화합니다. 그러나 이 형식으로 작동할 수 없는 PBX(Private Branch Exchange) 시스템도 많습니다. 아웃바운드 변환 규칙은 이 번호를 중재 서버 또는 게이트웨이로 전송하기 전에 로컬 전화 번호 형식으로 변환합니다.

각 아웃바운드 변환 규칙은 트렁크 구성과 연결됩니다. 이는 이 cmdlet을 사용하여 규칙을 제거하면 해당 범위의 트렁크 구성에서 규칙이 제거됨을 의미합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsOutboundTranslationRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsOutboundTranslationRule"}

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
<td><p>제거할 아웃바운드 변환 규칙의 고유한 식별자입니다. Identity는 범위와 그 뒤에 오는 각 범위 내의 고유한 이름으로 구성됩니다(예: site:Redmond/OutboundRule1).</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule 개체입니다. 아웃바운드 변환 규칙 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsOutboundTranslationRule](new-csoutboundtranslationrule.md)  
[Set-CsOutboundTranslationRule](set-csoutboundtranslationrule.md)  
[Get-CsOutboundTranslationRule](get-csoutboundtranslationrule.md)

