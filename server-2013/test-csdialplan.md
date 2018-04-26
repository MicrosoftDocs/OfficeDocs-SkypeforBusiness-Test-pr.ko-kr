---
title: Test-CsDialPlan
TOCTitle: Test-CsDialPlan
ms:assetid: e6618394-82c5-4bc2-85cc-97ac4686a1aa
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399024(v=OCS.15)
ms:contentKeyID: 49305352
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsDialPlan

 

_**마지막으로 수정된 항목:** 2015-03-09_

다이얼 플랜(위치 프로필이라고도 함)에 대해 전화 번호를 테스트하고 해당 번호에 적용되는 정규화 규칙과 정규화 규칙이 적용된 후의 변환된 번호를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsDialPlan -DialedNumber <PhoneNumber> -Dialplan <LocationProfile>

## 예제

## 예제 1

이 예제에서는 ID가 site:Redmond인 다이얼 플랜에 대해 테스트를 실행합니다. 먼저 **Get-CsDialPlan** cmdlet을 실행하여 ID가 site:Redmond인 다이얼 플랜을 검색합니다. 그런 다음, 해당 다이얼 플랜 개체는 **Test-CsDialPlan** cmdlet에 파이프되고 다이얼 플랜은 전화 번호 14255559999에 대해 테스트됩니다. 일치하는 패턴을 가진 음성 정규화 규칙이 적용된 후 출력은 DialedNumber입니다. 일치하는 패턴을 가진 여러 개의 정규화 규칙이 사이트 내에 있는 경우 Priority 값이 가장 낮은 규칙이 적용됩니다. DialedNumber 값과 일치하는 패턴을 가진 규칙이 없는 경우(예를 들어, 정규화 규칙이 11자리 숫자 패턴과 일치하는데 7자리 숫자를 제공한 경우) 값이 반환되지 않습니다.

이 명령의 출력에는 전화 번호와 정규화 규칙이 포함됩니다. 정규화 규칙에는 수많은 속성이 있으며 기본적으로 이 출력은 줄임표(...)를 사용하여 잘립니다. 반환된 음성 정규화 규칙의 모든 속성과 값을 보기 위해 화면에 표시되기 전에 출력을 **Format-List** cmdlet에 파이프합니다. 이렇게 하면 전화 번호와 정규화 규칙이 별개의 줄에 나열되고 정규화 규칙 속성과 값이 화면에 맞게 줄 바꿈됩니다.

    Get-CsDialPlan -Identity site:Redmond | Test-CsDialPlan -DialedNumber 14255559999 | Format-List

## 예제 2

예제 2는 Get 작업의 결과가 **Test-CsDialPlan** cmdlet에 직접 파이프되는 대신에 먼저 $a 변수에 개체가 저장된 다음, DialPlan 매개 변수에 값으로 전달되어 테스트가 실행될 다이얼 플랜으로 사용된다는 점을 제외하고는 예제 1과 동일합니다.

예제 1과 마찬가지로 최종적으로 출력을 **Format-List** cmdlet에 파이프하므로 음성 정규화 규칙을 기본적으로 표시되는 형태보다 자세히 볼 수 있습니다.

    $a = Get-CsDialPlan -Identity site:Redmond
    Test-CsDialPlan -DialedNumber 14255559999 -Dialplan $a | Format-List

## 예제 3

이 예제에서는 Lync Server 배포 내에 정의된 모든 다이얼 플랜에 대해 다이얼 플랜 테스트를 실행합니다. 먼저 **Get-CsDialPlan** cmdlet을 매개 변수 없이 실행하여 모든 다이얼 플랜을 검색합니다. 그런 다음, 반환된 다이얼 플랜의 컬렉션이 **Test-CsDialPlan** cmdlet에 파이프되고 컬렉션의 각 다이얼 플랜은 전화 번호 2065559999에 대해 테스트됩니다. 컬렉션의 각 다이얼 플랜에 하나씩 적용된 음성 정규화 규칙과 함께 변환된 번호의 목록이 출력됩니다. 다이얼 플랜 내의 음성 정규화 규칙이 특정 다이얼 플랜의 DialedNumber 값에 적용되지 않은 경우(예: 정규화 규칙이 11자리 숫자 패턴과 일치하는데 7자리 숫자를 제공한 경우) 해당 다이얼 플랜에 대해 빈 줄이 목록에 나타납니다.

기본적으로 출력에서는 적용된 음성 정규화 규칙이 모두 표시되지 않고 잘립니다. 예제 1 및 2에서는 테스트 결과를 **Format-List** cmdlet에 파이프하여 전체 출력을 볼 수 있었습니다. 이 예제에서는 출력을 **Format-Table** cmdlet에 파이프하고 Wrap 매개 변수를 포함합니다. 이렇게 하면 각 항목이 테이블 형식(변환된 번호에 대한 열 하나와 적용된 음성 정규화 규칙에 대한 열 하나)으로 표시되지만 정규화 규칙이 열 안에 맞춰지도록 출력이 줄 바꿈됩니다.

    Get-CsDialPlan | Test-CsDialPlan -DialedNumber 2065559999 | Format-Table -Wrap

## 자세한 정보

이 cmdlet을 사용하면 다이얼 플랜을 지정된 전화 번호에 적용한 결과를 볼 수 있습니다. 다이얼 플랜은 정규화 규칙이 적용되는 방법을 비롯하여 Enterprise Voice 사용자가 전화를 거는 데 필요한 정보를 제공합니다. 전화 건 번호와 다이얼 플랜이 제공될 경우 이 cmdlet은 적용될 다이얼 플랜 내의 정규화 규칙과 변환된 번호가 무엇이 되는지 확인합니다.

이 cmdlet을 사용하여 번호 변환과 관련된 문제를 해결하거나 특정 번호에 대한 규칙 적용을 확인할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Test-CsDialPlan** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsDialPlan"}

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
<td><p>전화 번호</p></td>
<td><p>Dialplan 매개 변수에 지정된 다이얼 플랜을 테스트할 전화 번호입니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.Voice.PhoneNumber</p></td>
</tr>
<tr class="even">
<td><p><em>Dialplan</em></p></td>
<td><p>필수</p></td>
<td><p>위치 프로필</p></td>
<td><p>DialedNumber 매개 변수에 지정된 번호를 테스트할 다이얼 플랜에 대한 참조를 포함하는 개체입니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile 개체입니다. 다이얼 플랜 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

Microsoft.Rtc.Management.Voice.LocationProfileTestResult 유형의 개체를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsDialPlan](new-csdialplan.md)  
[Remove-CsDialPlan](remove-csdialplan.md)  
[Set-CsDialPlan](set-csdialplan.md)  
[Get-CsDialPlan](get-csdialplan.md)  
[Grant-CsDialPlan](grant-csdialplan.md)

