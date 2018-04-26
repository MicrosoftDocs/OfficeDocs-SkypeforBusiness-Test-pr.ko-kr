---
title: New-CsVoiceRegex
TOCTitle: New-CsVoiceRegex
ms:assetid: a1a498b7-8353-40bd-9c02-424c95743ec3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412751(v=OCS.15)
ms:contentKeyID: 49304577
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsVoiceRegex

 

_**마지막으로 수정된 항목:** 2015-03-09_

전화 번호를 다른 형식으로 변환하기 위해 정규식 패턴 및 변환을 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsVoiceRegex -AtLeastLength <Int32> [-DigitsToPrepend <String>] [-DigitsToStrip <Int32>] [-StartsWith <String>] <COMMON PARAMETERS>

    New-CsVoiceRegex -ExactLength <Int32> [-DigitsToPrepend <String>] [-DigitsToStrip <Int32>] [-StartsWith <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS:

## 예제

## 예제 1

이 예제는 새 정규식 패턴 및 변환을 만듭니다. 이 식은 정확히 7자(-ExactLength 7)인 패턴을 포함하며 일치하는 번호의 처음 3자를 제거합니다(-DigitsToStrip 3). 이 정규식에서 만드는 Pattern은 ^\\d{3}(\\d{4})$이 되며 Translation은 $1이 됩니다. 예를 들어 5551212 번호가 이 패턴과 일치하고 결과 변환은 1212가 됩니다. 7자리 숫자에서 처음 3자리가 제거됩니다.

    $regex = New-CsVoiceRegex -ExactLength 7 -DigitsToStrip 3

## 예제 2

이 예제도 새 정규식 패턴 및 변환을 만들지만 이러한 값을 사용하여 새 음성 정규화 규칙을 만듭니다. 첫째 줄에서는 **New-CsVoiceRegEx** cmdlet을 호출하여 일치하는 번호가 7자 이상이고(-AtLeastLength 7) 1로 시작해야 하는(-StartsWith "1") 정규식을 만듭니다. 이 명령의 결과는 $regex 변수에 할당됩니다.

둘째 줄에서는 **New-CsVoiceNormalizationRule** cmdlet을 호출합니다. 새 규칙에 고유 이름을 지정합니다(이 경우 global/internal rule). 그런 다음 **New-CsVoiceRegex** cmdlet을 호출하여 만든 Pattern을 정규화 규칙에 Pattern으로 할당합니다(-Pattern $regex.Pattern). Translation도 마찬가지로 **New-CsVoiceRegex** cmdlet을 호출하여 Translation을 할당합니다(-Translation $regex.Translation).

참고: 이 예제에서 만든 Pattern은 ^(1\\d{5}\\d+)$입니다. 이는 1(1)로 시작하고 뒤에 5자리(\\d{5})가 오며 그 뒤에 임의 자릿수(\\d+)가 오는 번호로 해석할 수 있습니다. 이를 합산하면 정확히 우리가 원하는 1로 시작하는 7자 이상의 숫자(1 + 5 + 1 이상)임을 알 수 있습니다.

    $regex = New-CsVoiceRegex -AtLeastLength 7 -StartsWith "1"
    New-CsVoiceNormalizationRule "global/internal rule" -Pattern $regex.Pattern -Translation $regex.Translation

## 자세한 정보

정규식은 문자 패턴을 일치시키는 데 사용됩니다. Lync Server는 정규식을 사용하여 전화 건 번호, E.164 및 로컬 PBX(Private Branch Exchange) 및 PSTN(공중 전화망) 형식을 포함한 다양한 형식과 전화 번호 간을 변환합니다. 정규식의 사용 구문 및 형식 규칙을 잘 모를 경우 이러한 변환 규칙의 정의 과정이 어려울 수 있습니다. **New-CsVoiceRegex** cmdlet은 사용자에게 특정 기준을 지정할 수 있는 매개 변수를 제공한 다음 자동으로 정규식을 생성합니다.

이 cmdlet을 사용하여 정규화 규칙(**New-CsVoiceNormalizationRule** cmdlet) 및 아웃바운드 변환 규칙(**New-CsOutboundTranslationRule** cmdlet)의 Pattern, Translation 값 및 음성 경로(**New-CsVoiceRoute**cmdlet)의 NumberPattern 값으로 사용되는 정규식을 생성할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsVoiceRegex** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsVoiceRegex"}

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
<td><p><em>AtLeastLength</em></p></td>
<td><p>필수</p></td>
<td><p>System.Int32</p></td>
<td><p>식과 일치하는 문자열(전화 번호)에 필요한 최소 길이입니다. 예를 들어 7자리 또는 7자 이상의 숫자에만 영향을 주는 정규화 규칙을 정의하는 경우 이 매개 변수에 값 7을 지정합니다.</p>
<p>이 매개 변수 또는 ExactLength 매개 변수의 값을 입력해야 합니다. 둘 다의 값을 입력할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExactLength</em></p></td>
<td><p>필수</p></td>
<td><p>System.Int32</p></td>
<td><p>정규식과 일치하는 문자열(전화 번호)의 길이입니다. 예를 들어 10자리 숫자에만 영향을 주는 정규화 규칙이 필요한 경우 이 매개 변수에 값 10을 지정합니다.</p>
<p>이 매개 변수 또는 AtLeastLength 매개 변수의 값을 입력해야 합니다. 둘 다의 값을 입력할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DigitsToPrepend</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>전화 번호의 시작 부분에 추가할 문자 또는 숫자를 지정하는 문자열입니다. 이 매개 변수에 입력한 값은 정규식 Pattern과 일치하는 숫자 앞에 문자를 추가하는 Translation 값에 영향을 주게 됩니다. 예를 들어 패턴과 일치하는 번호가 5551212이고 DigitsToPrepend 값이 425인 경우 다른 변환은 적용되지 않았다고 가정하면 변환되는 번호는 4255551212입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DigitsToStrip</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>문자열(전화 번호)의 시작 부분에서 제거할 문자 수입니다. 예를 들어 2065551212 번호를 입력하고 DigitsToStrip이 3인 경우 번호는 5551212로 변환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>StartsWith</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>문자열(전화 번호)의 첫 번째 문자입니다. 문자열이 StartsWith 매개 변수에 지정된 문자열로 시작하지 않는 경우 정규식과 일치하지 않게 됩니다. 예를 들어 StartsWith에 지정된 값이 &quot;+1&quot;이면 +1로 시작하는 번호가 이 패턴과 일치하고 변환됩니다. StartsWith 문자열의 문자 수는 ExactLength 및 AtLeastLength 합계에 포함됩니다. 예를 들어 ExactLength에 10을 지정하고 StartsWith 문자열에 +1을 지정한 경우 일치하는 전화 번호는 길이가 8자이고 앞에 +1이 붙어 총 10자가 됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.Voice.OcsVoiceRegex 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)  
[New-CsOutboundTranslationRule](new-csoutboundtranslationrule.md)  
[New-CsVoiceRoute](new-csvoiceroute.md)

