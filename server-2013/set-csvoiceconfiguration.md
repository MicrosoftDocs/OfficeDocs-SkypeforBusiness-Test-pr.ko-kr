---
title: Set-CsVoiceConfiguration
TOCTitle: Set-CsVoiceConfiguration
ms:assetid: dbab35ac-9a55-41d2-a726-9a26b2ff8e85
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398967(v=OCS.15)
ms:contentKeyID: 49305245
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsVoiceConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

음성 테스트 구성 목록을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsVoiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsVoiceConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-VoiceTestConfigurations <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 음성 구성 내의 테스트 음성 구성을 수정하기 위해 여러 단계를 거칩니다. 먼저 **Get-CsVoiceConfiguration** cmdlet을 호출하여 음성 구성 개체를 검색합니다. 검색된 개체(하나만 있음)를 변수 $a에 할당합니다.

이 예제의 둘째 줄에서는 음성 테스트 구성 개체의 컬렉션인 변수 $a에서 VoiceTestConfigurations 속성의 내용을 검색합니다. 그런 다음 해당 컬렉션을 문자열 TestConfig2와 일치하는 Name을 가진 모든 음성 테스트 구성 개체에 대한 컬렉션을 검색하는 **Where-Object**에 파이프합니다. 해당 개체는 변수 $b에 할당됩니다.

다음으로 새 값을 DialedNumber 및 ExpectedTranslatedNumber 속성에 할당하여 TestConfig2 음성 테스트 구성 개체를 수정합니다. 해당 개체를 업데이트하여 변수 $a에서 개체를 업데이트했습니다. 그러나 해당 개체는 여전히 메모리에만 있습니다. 마지막 단계에서는 $a를 **Set-CsVoiceConfiguration** cmdlet의 Instance 매개 변수에 전달하여 이러한 변경 내용을 저장해야 합니다.

이 방법을 사용하여 음성 구성을 수정하지 않는 것이 좋습니다. 음성 구성을 수정하려면 다음과 같은 **Set-CsVoiceTestConfiguration** cmdlet을 사용하여 개별 음성 테스트 구성을 변경하면 됩니다.

Set-CsVoiceTestConfiguration -Identity TestConfig2 -DialedNumber 5551212 -ExpectedTranslatedNumber +5551212

한 줄의 명령으로 예제 1에 표시된 것과 동일한 작업을 수행할 수 있습니다.

    $a = Get-CsVoiceConfiguration
    $b = $a.VoiceTestConfigurations | Where-Object {$_.Name -eq "TestConfig2"}
    $b.DialedNumber = "5551212"
    $b.ExpectedTranslatedNumber = "+5551212"
    Set-CsVoiceConfiguration -Instance $a

## 자세한 정보

음성 테스트 구성은 특정 음성 정책, 경로 및 다이얼 플랜에 대해 전화 번호를 테스트하는 데 사용됩니다. 이 cmdlet을 사용하면 Lync Server 배포에 대한 모든 음성 테스트 구성을 포함하는 목록에서 음성 테스트 구성을 수정할 수 있습니다.

이 cmdlet은 VoiceConfiguration 유형의 개체를 수정합니다. 이 개체는 음성 테스트 구성의 컨테이너 개체일 뿐입니다. 따라서 이 cmdlet을 사용하지 않는 것이 좋습니다. 음성 구성을 수정하려면 **Set-CsVoiceTestConfiguration** cmdlet을 호출하여 개별 음성 테스트 구성을 수정합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsVoiceConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoiceConfiguration"}

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>변경 내용을 적용하기 전에 표시될 수 있는 확인 메시지를 숨깁니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Xds ID</p></td>
<td><p>이 개체의 범위입니다. 이 매개 변수에 가능한 값은 Global뿐입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>음성 구성</p></td>
<td><p>음성 구성(Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration) 개체에 대한 참조입니다. 이 유형의 개체는 <strong>Get-CsVoiceConfiguration</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>VoiceTestConfigurations</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>Lync Server 배포에 대해 정의된 모든 음성 테스트 구성(Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration 개체)의 목록입니다.</p>
<p><strong>Set-CsVoiceTestConfiguration</strong> cmdlet을 사용하여 개별 음성 테스트 구성 개체를 수정해야 합니다. 이 목록의 구성을 수정할 때 이 방법을 사용하는 것이 좋습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration 개체입니다. **Set-CsVoiceConfiguration** cmdlet은 음성 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsVoiceConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsVoiceConfiguration](remove-csvoiceconfiguration.md)  
[Get-CsVoiceConfiguration](get-csvoiceconfiguration.md)  
[New-CsVoiceTestConfiguration](new-csvoicetestconfiguration.md)  
[Set-CsVoiceTestConfiguration](set-csvoicetestconfiguration.md)  
[Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)

