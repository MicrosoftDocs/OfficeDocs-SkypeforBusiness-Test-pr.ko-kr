---
title: Remove-CsImFilterConfiguration
TOCTitle: Remove-CsImFilterConfiguration
ms:assetid: 0c6f5f69-ae41-46d6-b817-fa1c6751c615
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398171(v=OCS.15)
ms:contentKeyID: 49302779
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsImFilterConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 메신저 필터 구성을 제거합니다. 메신저 필터 설정은 사용자가 하이퍼링크를 포함하는 메신저 대화를 보낼 수 없도록 하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsImFilterConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Remove-CsImFilterConfiguration** cmdlet을 사용하여 ID가 site:Redmond인 메신저 필터 구성을 제거합니다. 메신저 필터 구성이 사이트에서 제거되면 해당 사이트는 자동으로 전역 설정을 대신 사용하기 시작합니다.

    Remove-CsImFilterConfiguration -Identity site:Redmond

## 예제 2

예제 2에서는 사이트 범위의 모든 메신저 필터 구성이 제거됩니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsImFilterConfiguration** cmdlet 및 Filter 매개 변수를 사용하여 사이트 범위의 모든 구성을 반환합니다. 와일드카드 문자열 site:\*는 ID가 문자열 값 site:로 시작하는 구성만 반환하도록 **Get-CsImFilterConfiguration** cmdlet에 지시합니다. 그런 다음 필터링된 정책 컬렉션은 컬렉션의 각 구성을 삭제하는 **Remove-CsImFilterConfiguration** cmdlet에 파이프됩니다.

    Get-CsImFilterConfiguration -Filter site:* | Remove-CsImFilterConfiguration

## 자세한 정보

메신저 대화를 보낼 때 사용자가 해당 메시지의 텍스트에 URI(Uniform Resource Identifier)를 포함하여 대화의 다른 참가자가 특정 웹 사이트 또는 공유를 참조하도록 할 수 있습니다. 또한 특정 접두사가 포함된 하이퍼링크가 차단되거나 비활성화되도록 Lync Server를 구성할 수 있습니다. 즉, 참가자가 단순히 링크를 클릭하여 URI가 참조하는 사이트로 이동할 수 없고 수동으로 링크를 복사하여 브라우저에 붙여 넣어야 합니다.

**Remove-CsImFilterConfiguration** cmdlet은 지정한 ID(예: 특정 사이트)에 대한 메신저 필터 구성을 제거합니다. Global ID에 대해 이 cmdlet을 실행하면 전역 구성이 기본 설정으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsImFilterConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsImFilterConfiguration"}

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
<td><p>제거할 구성의 고유 ID입니다. 이 ID는 Global 또는 Site:&lt;사이트 이름&gt;이며, 여기서 &lt;사이트 이름&gt;은 설정이 적용되는 사이트 이름을 나타냅니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration 개체입니다. 메신저 필터 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsImFilterConfiguration](new-csimfilterconfiguration.md)  
[Set-CsImFilterConfiguration](set-csimfilterconfiguration.md)  
[Get-CsImFilterConfiguration](get-csimfilterconfiguration.md)

