---
title: Remove-CsVoiceRoute
TOCTitle: Remove-CsVoiceRoute
ms:assetid: 6687e538-e8f6-4bf0-b393-2c7b4a3f2f06
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398468(v=OCS.15)
ms:contentKeyID: 49303880
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsVoiceRoute

 

_**마지막으로 수정된 항목:** 2015-03-09_

음성 경로를 제거합니다. 음성 경로는 Enterprise Voice 사용자의 통화를 PSTN(공중 전화망) 또는 PBX(Private Branch Exchange)의 전화 번호로 경로 지정하는 방법을 Lync Server에 지정하는 명령을 포함합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsVoiceRoute -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

ID가 Route1인 음성 경로에 대한 설정을 제거합니다.

    Remove-CsVoiceRoute -Identity Route1

## 예제 2

이 명령은 조직에서 모든 음성 경로를 제거합니다. 먼저 **Get-CsVoiceRoute** cmdlet에 의해 모든 음성 경로가 검색됩니다. 그런 다음, 이러한 음성 경로는 각 음성 경로를 제거하는 **Remove-CsVoiceRoute** cmdlet에 파이프됩니다.

    Get-CsVoiceRoute | Remove-CsVoiceRoute

## 예제 3

이 명령은 문자열 "Redmond"를 포함하는 ID를 가진 모든 음성 경로를 제거합니다. 먼저 **Get-CsVoiceRoute** cmdlet이 Filter 매개 변수와 함께 호출됩니다. Filter 매개 변수 값은 문자열이 Identity 내의 아무 곳에나 위치할 수 있다는 것을 지정하는 와일드카드 문자(\*)로 둘러싸인 문자열 Redmond입니다. 문자열 Redmond를 포함하는 ID를 가진 모든 음성 경로가 검색되고 나면 이러한 음성 경로는 각 음성 경로를 제거하는 **Remove-CsVoiceRoute** cmdlet에 파이프됩니다.

    Get-CsVoiceRoute -Filter *Redmond* | Remove-CsVoiceRoute

## 자세한 정보

이 cmdlet을 사용하여 기존 음성 경로를 제거합니다. 음성 경로는 PSTN 사용법을 통해 음성 정책과 연관되므로 음성 경로를 제거해도 음성 정책과 관련된 값이 변경되지 않으며 삭제된 음성 경로의 패턴과 일치했던 번호의 경로 지정만 변경됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsVoiceRoute** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsVoiceRoute"}

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
<td><p>삭제할 음성 경로를 고유하게 식별하는 문자열입니다. (Test Route와 같이 경로 이름에 공백이 포함된 경우 전체 문자열을 큰따옴표로 묶어야 합니다.)</p>
<p></p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route 개체입니다. 음성 경로 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoiceRoute](new-csvoiceroute.md)  
[Set-CsVoiceRoute](set-csvoiceroute.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)  
[Test-CsVoiceRoute](test-csvoiceroute.md)

