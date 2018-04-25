---
title: Remove-CsMediaConfiguration
TOCTitle: Remove-CsMediaConfiguration
ms:assetid: 8af2b8cb-4d58-4f8a-9acb-9b5104880bc9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398705(v=OCS.15)
ms:contentKeyID: 49304314
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsMediaConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 미디어 구성 설정 컬렉션을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsMediaConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 site:Redmond1인 미디어 구성 컬렉션을 삭제하기 위해 **Remove-CsMediaConfiguration** cmdlet이 사용됩니다. 미디어 설정이 사이트 범위에서 제거될 경우 해당 사이트는 자동으로 전역 미디어 설정을 사용하기 시작합니다.

    Remove-CsMediaConfiguration -Identity site:Redmond1

## 예제 2

예제 2에서는 대화에 포함된 모든 상대방에게 암호화를 요구하는 미디어 구성 컬렉션을 모두 제거하기 위해 세 개의 cmdlet인 **Get-CsMediaConfiguration** cmdlet, **Where-Object** cmdlet 및 **Remove-CsMediaConfiguration** cmdlet이 사용됩니다. 이 작업을 수행하기 위해 먼저 **Get-CsMediaConfiguration** cmdlet을 사용하여 조직에 있는 모든 미디어 구성 컬렉션을 반환합니다. 그런 다음, EncryptionLevel 속성이 RequireEncryption과 같은(-eq) 컬렉션으로 파이프라인 데이터를 제한하는 필터가 적용되는 **Where-Object** cmdlet에 해당 정보가 파이프됩니다. 마지막으로 필터링된 데이터 집합의 각 항목을 삭제하는 **Remove-CsMediaConfiguration** cmdlet에 해당 데이터 집합이 전달됩니다.

    Get-CsMediaConfiguration | Where-Object {$_.EncryptionLevel -eq "RequireEncryption"} | Remove-CsMediaConfiguration

## 예제 3

이 예제에서는 서비스 범위에 정의된 모든 미디어 구성(구성이 특정 서비스에 적용된다는 것을 의미)이 제거됩니다. 이를 수행하기 위해 먼저 Filter service:\*를 사용하여 **Get-CsMediaConfiguration** cmdlet을 호출합니다. 이 필터는 ID가 service로 시작하는 모든 미디어 구성 컬렉션(서비스 범위에 있는 모든 컬렉션)을 검색합니다. 그런 다음, 해당 컬렉션 집합을 모두 제거하는 **Remove-CsMediaConfiguration** cmdlet에 컬렉션 집합이 파이프됩니다.

    Get-CsMediaConfiguration -Filter service:* | Remove-CsMediaConfiguration

## 자세한 정보

이 cmdlet은 미디어 설정의 컬렉션을 제거합니다. 이러한 설정은 클라이언트 끝점 간의 오디오 및 비디오 통화와 관련됩니다.

또한 이 cmdlet을 사용하여 전역 미디어 설정을 제거할 수 있습니다. 그러나 이 경우 설정은 실제로 제거되지 않으며 기본값으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsMediaConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsMediaConfiguration"}

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
<td><p>제거할 미디어 구성 설정에 대한 고유한 식별자입니다. 이 식별자는 이 구성이 적용되는 범위(전역, 사이트 또는 서비스)를 지정합니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings 개체입니다. 미디어 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsMediaConfiguration](new-csmediaconfiguration.md)  
[Set-CsMediaConfiguration](set-csmediaconfiguration.md)  
[Get-CsMediaConfiguration](get-csmediaconfiguration.md)

