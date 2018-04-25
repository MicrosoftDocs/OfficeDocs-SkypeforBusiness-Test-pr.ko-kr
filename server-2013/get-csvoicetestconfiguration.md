---
title: Get-CsVoiceTestConfiguration
TOCTitle: Get-CsVoiceTestConfiguration
ms:assetid: c23235db-500c-4303-8c75-b4ae341b3807
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412957(v=OCS.15)
ms:contentKeyID: 49304933
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsVoiceTestConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 경로 및 규칙에 대해 전화 번호를 테스트하는 데 사용할 수 있는 테스트 시나리오를 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsVoiceTestConfiguration [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsVoiceTestConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

모든 음성 테스트 구성 설정을 검색합니다.

    Get-CsVoiceTestConfiguration

## 예제 2

이 예제에서는 모든 음성 테스트 구성 설정을 검색하고 각각의 Identity, DialedNumber 및 ExpectedTranslatedNumber 매개 변수만 표시합니다. **Get-CsVoiceTestConfiguration** cmdlet에서 반환하는 설정은 **Select-Object** cmdlet에 파이프되고 이 cmdlet은 출력 범위를 Identity, DialedNumber 및 ExpectedTranslatedNumber 속성으로 좁힙니다.

    Get-CsVoiceTestConfiguration | Select-Object Identity, DialedNumber, ExpectedTranslatedNumber

## 예제 3

이 예제에서는 Filter 매개 변수를 사용하여 ID에 문자열 "test"가 포함된 모든 음성 테스트 구성 설정을 검색합니다. 필터 값의 시작 부분과 끝 부분에 있는 와일드카드 문자(\*)는 문자열 "test"가 ID 내의 아무 곳에나 위치할 수 있고 그 앞과 뒤에 임의의 문자가 온다는 것을 나타냅니다. 예를 들어 이 명령은 TestConfig, VoiceNumberTest 및 VoiceTest1과 같은 이름을 가진 음성 테스트 구성을 반환합니다.

    Get-CsVoiceTestConfiguration -Filter *test*

## 자세한 정보

이 cmdlet은 지정한 전화 번호를 테스트할 음성 경로, 사용법, 다이얼 플랜 및 음성 정책을 검색합니다. 음성 경로 및 음성 정책을 구현하기 전에 예상된 결과가 제공되는지 확인하기 위해 다양한 전화 번호에서 테스트하는 것이 좋습니다. 이 cmdlet을 사용하여 테스트 구성을 검색한 다음, **Test-CsVoiceConfiguration** cmdlet을 통해 해당 시나리오를 실행하여 이 테스트를 수행할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsVoiceTestConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsVoiceTestConfiguration"}

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수는 정의된 음성 테스트 구성의 와일드카드 검색을 수행하는 방법을 제공합니다. 자세한 내용은 이 항목의 예제를 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>검색할 테스트 구성을 고유하게 식별하는 문자열입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 음성 테스트 구성을 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration 유형의 개체를 하나 이상 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoiceTestConfiguration](new-csvoicetestconfiguration.md)  
[Remove-CsVoiceTestConfiguration](remove-csvoicetestconfiguration.md)  
[Set-CsVoiceTestConfiguration](set-csvoicetestconfiguration.md)  
[Test-CsVoiceTestConfiguration](test-csvoicetestconfiguration.md)

