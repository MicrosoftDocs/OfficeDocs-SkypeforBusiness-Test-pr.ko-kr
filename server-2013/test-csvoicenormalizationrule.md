---
title: Test-CsVoiceNormalizationRule
TOCTitle: Test-CsVoiceNormalizationRule
ms:assetid: e2d27ce1-883f-4679-a288-f35846842258
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399003(v=OCS.15)
ms:contentKeyID: 49305311
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsVoiceNormalizationRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

음성 정규화 규칙에 대해 전화 번호를 테스트하고 정규화 규칙이 적용된 후 번호를 반환합니다. 음성 정규화 규칙은 전화 걸기 요구 사항(예: 외부 회선에 액세스하려면 9를 눌러야 함)을 Lync Server에 사용되는 E.164 전화 번호 형식으로 변환하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsVoiceNormalizationRule -DialedNumber <PhoneNumber> -NormalizationRule <NormalizationRule>

## 예제

## 예제 1

이 예제에서는 ID가 "global/11 digit number rule"인 음성 정규화 규칙에 대해 음성 정규화 테스트를 실행합니다. 먼저 **Get-CsVoiceNormalizationRule** cmdlet을 실행하여 ID가 "global/11 digit number rule"인 규칙을 검색합니다. 이 규칙 개체는 전화 번호 14255559999에 대해 규칙을 테스트하는 **Test-CsVoiceNormalizationRule** cmdlet에 파이프됩니다. 그러면 음성 정규화 규칙 "global/11 digit number rule"이 적용된 후 DialedNumber가 출력됩니다. 이 규칙이 DialedNumber 값에 적용되지 않는 경우(예: 정규화 규칙이 11자리 숫자 패턴과 일치하는데 7자리 숫자를 제공한 경우)에는 값이 반환되지 않습니다.

    Get-CsVoiceNormalizationRule -Identity "global/11 digit number rule" | Test-CsVoiceNormalizationRule -DialedNumber 14255559999

## 예제 2

예제 2는 Get 작업의 결과를 Test cmdlet에 직접 파이프하는 대신, 먼저 개체를 $a 변수에 저장한 다음 테스트를 실행하는 음성 정규화 규칙으로 사용할 NormalizationRule 매개 변수에 값으로 전달한다는 점을 제외하고는 예제 1과 동일합니다.

    $a = Get-CsVoiceNormalizationRule -Identity "global/11 digit number rule"
    Test-CsVoiceNormalizationRule -DialedNumber 5551212 -NormalizationRule $a

## 예제 3

이 예제에서는 Lync Server 배포 내에 정의된 모든 음성 정규화 규칙에 대해 음성 정규화 테스트를 실행합니다. 먼저 매개 변수 없이 **Get-CsVoiceNormalizationRule** cmdlet을 실행하여 모든 음성 정규화 규칙을 검색합니다. 반환되는 규칙 컬렉션은 전화 번호 2065559999에 대해 컬렉션의 각 규칙을 테스트하는 **Test-CsVoiceNormalizationRule** cmdlet에 반환됩니다. 그러면 테스트한 각 규칙에 하나씩 변환된 번호 목록이 출력됩니다. DialedNumber 값에 규칙이 적용되지 않는 경우(예: 정규화 규칙이 11자리 숫자 패턴과 일치하는데 7자리 숫자를 제공한 경우)에는 목록에서 해당 규칙의 줄이 빈 줄로 표시됩니다.

    Get-CsVoiceNormalizationRule | Test-CsVoiceNormalizationRule -DialedNumber 2065559999

## 자세한 정보

이 cmdlet을 사용하면 음성 정규화 규칙을 지정된 전화 번호에 적용한 결과를 볼 수 있습니다. 음성 정규화 규칙은 전화 권한 부여 및 통화 경로 지정의 필수 부분입니다. 이러한 규칙은 번호를 일반적으로 사용자가 입력하는 형식에서 표준(E.164) 형식으로 변환하기 위한 요구 사항을 정의합니다. 전화 걸기 문제를 해결하거나 규칙이 지정된 번호에 대해 예상대로 작동하는지 확인하려면 이 cmdlet을 사용하십시오.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Test-CsVoiceNormalizationRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsVoiceNormalizationRule"}

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
<td><p><em>DialedNumber</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Voice.PhoneNumber</p></td>
<td><p>NormalizationRule 매개 변수에 지정된 정규화 규칙을 테스트할 전화 번호입니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.Voice.PhoneNumber</p></td>
</tr>
<tr class="even">
<td><p><em>NormalizationRule</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule</p></td>
<td><p>DialedNumber 매개 변수에 지정된 번호를 테스트할 정규화 규칙에 대한 참조를 포함하는 개체입니다.</p>
<p><strong>Get-CsVoiceNormalizationRule</strong> cmdlet을 호출하여 음성 정규화 규칙을 검색할 수 있습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule 개체입니다. 음성 정규화 규칙 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

Microsoft.Rtc.Management.Voice.NormalizationRuleTestResult 유형의 개체를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)  
[Remove-CsVoiceNormalizationRule](remove-csvoicenormalizationrule.md)  
[Set-CsVoiceNormalizationRule](set-csvoicenormalizationrule.md)  
[Get-CsVoiceNormalizationRule](get-csvoicenormalizationrule.md)

