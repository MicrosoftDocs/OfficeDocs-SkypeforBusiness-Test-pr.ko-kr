---
title: Test-CsVoiceRoute
TOCTitle: Test-CsVoiceRoute
ms:assetid: 39d5012d-7beb-41c6-ac94-51011da04872
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425873(v=OCS.15)
ms:contentKeyID: 49303348
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsVoiceRoute

 

_**마지막으로 수정된 항목:** 2015-03-09_

음성 경로 번호 패턴을 기준으로 전화 번호를 테스트하고 제공된 번호가 경로의 번호 패턴과 일치하는지 여부를 나타내는 부울(true/false) 값을 반환합니다. 번호 패턴은 음성 경로에서 Enterprise Voice 사용자의 통화를 PSTN(공중 전화망) 또는 PBX(Private Branch Exchange)의 전화 번호로 경로 지정하는 방법을 Lync Server에 지시하는 데 사용하는 속성 중 하나일 뿐입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsVoiceRoute -Route <Route> -TargetNumber <PhoneNumber> [-Force <SwitchParameter>]

## 예제

## 예제 1

이 명령은 지정된 번호가 지정한 경로의 패턴과 일치하는지 여부를 확인합니다. 먼저 **Get-CsVoiceRoute** cmdlet을 사용하여 음성 경로 testroute를 검색합니다. 해당 경로는 **Test-CsVoiceRoute** cmdlet의 Route 매개 변수 값으로 사용됩니다. 또한 테스트할 번호를 TargetNumber 매개 변수에 포함합니다. 출력은 대상 번호가 해당 경로의 패턴과 일치하는지 여부를 나타내는 부울 값입니다.

    $vr = Get-CsVoiceRoute -Identity testroute
    Test-CsVoiceRoute -TargetNumber "+14255551212" -Route $vr

## 예제 2

예제 2에서는 예제 1과 동일한 작업을 수행하지만, 이 경우 작업이 단일 명령으로 수행됩니다. 먼저 **Get-CsVoiceRoute** cmdlet을 호출하여 ID가 testroute인 음성 경로를 검색합니다. 이 음성 경로를 **Test-CsVoiceRoute** cmdlet에 파이프하고 TargetNumber 매개 변수에 제공된 번호에 대해 경로를 테스트합니다. 경로가 cmdlet에 파이프되었으므로 Route 매개 변수를 지정할 필요가 없습니다.

    Get-CsVoiceRoute -Identity testroute | Test-CsVoiceRoute -TargetNumber "+14255551212"

## 예제 3

이 예제에서는 Lync Server 배포 내에서 정의된 모든 음성 경로 컬렉션을 검색하고 **Test-CsVoiceRoute** cmdlet 호출 시 제공된 TargetNumber에 대해 각 경로의 번호 패턴을 테스트합니다. 테스트되는 각 경로의 출력은 True 또는 False 값입니다.

    Get-CsVoiceRoute | Test-CsVoiceRoute -TargetNumber "+14255551212"

## 예제 4

이 예제는 여러 경로에 대한 음성 경로 테스트 결과를 검색한다는 점에서 예제 3과 유사합니다. 그러나 예제 3의 출력은 단순히 True/False 값의 목록으로, 테스트 결과가 적용되는 경로를 명확하게 표시하지 않습니다. 이 예제에서는 해당 문제를 해결합니다. 출력 표시를 향상시키기 위해 여러 작업을 수행할 수 있지만 이 짧은 예제에서도 최소한 해당 목적을 달성합니다.

먼저 **Get-CsVoiceRoute** cmdlet을 호출하여 모든 음성 경로를 검색하고 $z 변수에 할당합니다. 다음 줄에서 foreach 루프를 시작합니다. 이 루프는 한 번에 하나씩 컬렉션의 각 구성원을 가져오고 $x 변수에 할당합니다. 단일 음성 경로에 대한 참조가 포함된 $x에 대해 먼저 해당 경로의 ID를 표시합니다($x.Identity). 명령의 다음 부분에서는 **Test-CsVoiceRoute** cmdlet을 호출하여 대상 번호에 대해 $x 경로를 테스트합니다. 최종 출력은 단순한 서식의 음성 경로 ID 목록으로, 해당 ID를 가진 경로의 번호 패턴과 대상 번호가 일치하는지 여부를 나타내는 true/false가 뒤에 포함됩니다.

    $z = Get-CsVoiceRoute
    foreach ($x in $z){$x.Identity; Test-CsVoiceRoute -TargetNumber "+14255551212" -Route $x}

## 자세한 정보

음성 경로는 지정된 음성 경로를 통해 경로 지정되는 전화 번호를 식별하는 정규식을 포함합니다. 정규식과 일치하는 전화 번호가 이 경로를 통해 경로 지정됩니다. 이 cmdlet은 경로의 번호 패턴(NumberPattern 속성)을 기준으로 지정된 전화 번호가 지정한 음성 경로를 통해 경로 지정될지 여부를 확인합니다. 이 cmdlet을 통해 경로 지정 문제를 해결하거나 특정 경로에 대해 전화 번호를 시도하여 결과가 예상대로 표시되는지 확인할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Test-CsVoiceRoute** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsVoiceRoute"}

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
<td><p><em>Route</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route</p></td>
<td><p>TargetNumber 매개 변수에 지정된 번호를 테스트할 음성 경로에 대한 참조가 포함된 개체입니다. <strong>Get-CsVoiceRoute</strong> cmdlet을 호출하여 음성 경로 개체를 검색할 수 있습니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route</p></td>
</tr>
<tr class="even">
<td><p><em>TargetNumber</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Voice.PhoneNumber</p></td>
<td><p>Route 매개 변수에 지정된 음성 경로를 테스트할 전화 번호입니다. 이 번호는 E.164 형식(예: +14255551212)이어야 합니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.Voice.PhoneNumber</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>cmdlet을 실행할 때 나타날 수 있는 확인 프롬프트 또는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route 개체입니다. 음성 경로 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

Microsoft.Rtc.Management.Voice.VoiceRouteTestResult 유형의 개체를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoiceRoute](new-csvoiceroute.md)  
[Remove-CsVoiceRoute](remove-csvoiceroute.md)  
[Set-CsVoiceRoute](set-csvoiceroute.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)

