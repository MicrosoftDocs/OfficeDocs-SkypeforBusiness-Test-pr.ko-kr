---
title: Remove-CsVoiceTestConfiguration
TOCTitle: Remove-CsVoiceTestConfiguration
ms:assetid: abe27005-8325-47d7-8c7c-12bb831b87c7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412813(v=OCS.15)
ms:contentKeyID: 49304694
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsVoiceTestConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 경로 및 규칙에 대해 전화 번호를 테스트하는 데 사용된 음성 테스트 구성을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsVoiceTestConfiguration -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 ID가 TestConfig1인 음성 테스트 구성 설정을 제거합니다.

    Remove-CsVoiceTestConfiguration -Identity TestConfig1

## 예제 2

이 예제에서는 문자열 test를 포함하는 Identity를 가진 모든 구성에 대한 음성 테스트 구성 설정을 모두 제거합니다. 먼저 **Get-CsVoiceTestConfiguration** cmdlet을 Filter 매개 변수와 함께 호출하여 문자열 "test"가 Identity의 해당 값에 아무 곳에나 포함된 음성 테스트 구성을 모두 검색합니다. 그런 다음 결과로 얻어진 구성 집합이 **Remove-CsVoiceTestConfiguration** cmdlet에 파이프된 다음 제거됩니다.

    Get-CsVoiceTestConfiguration -Filter *test* | Remove-CsVoiceTestConfiguration

## 자세한 정보

음성 경로 및 음성 정책을 구현하기 전에 예상된 결과가 제공되는지 확인하기 위해 다양한 전화 번호에서 테스트하는 것이 좋습니다. 이러한 테스트가 완료되고 다시 필요하지 않은 경우 이 cmdlet을 사용하여 테스트를 제거합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsVoiceTestConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsVoiceTestConfiguration"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>제거할 테스트 구성을 고유하게 식별하는 문자열입니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration 개체입니다. 음성 테스트 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoiceTestConfiguration](new-csvoicetestconfiguration.md)  
[Set-CsVoiceTestConfiguration](set-csvoicetestconfiguration.md)  
[Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)  
[Test-CsVoiceTestConfiguration](test-csvoicetestconfiguration.md)

