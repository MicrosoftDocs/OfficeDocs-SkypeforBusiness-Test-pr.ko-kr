---
title: Test-CsVoicePolicy
TOCTitle: Test-CsVoicePolicy
ms:assetid: 4d631e36-3a9d-4ca2-913f-8c9f4e93183d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398310(v=OCS.15)
ms:contentKeyID: 49303576
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsVoicePolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

음성 정책에 대해 전화 번호를 테스트하고 해당 번호의 해당 정책에 대해 사용할 음성 경로를 결정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsVoicePolicy -TargetNumber <PhoneNumber> -VoicePolicy <VoicePolicy> [-Force <SwitchParameter>] [-RouteSettings <PstnRoutingSettings>]

## 예제

## 예제 1

이 예제에서는 Identity가 site:Redmond인 음성 정책에 대해 음성 정책 테스트를 실행합니다. 먼저 **Get-CsVoicePolicy** cmdlet을 실행하여 ID가 site:Redmond인 정책을 검색합니다. 이 정책 개체는 전화 번호 +14255559999에 대해 정책을 테스트하는 **Test-CsVoicePolicy** cmdlet에 파이프됩니다. 번호 패턴이 TargetNumber 값과 일치하고 전화 사용이 정책의 전화 사용과 일치하는 첫 번째 음성 경로(경로의 Priority 속성 기준)가 출력됩니다. 일치하는 경로를 찾을 수 없는 경우(예: 번호 패턴이 11자리 숫자 패턴과 일치하는데 7자리 숫자를 제공한 경우) null 값이 반환됩니다.

    Get-CsVoicePolicy -Identity site:Redmond | Test-CsVoicePolicy -TargetNumber "+14255559999"

## 예제 2

예제 2는 Get 작업의 결과가 **Test-CsVoicePolicy** cmdlet에 직접 파이프되는 대신 먼저 $a 변수에 개체가 저장된 다음, VoicePolicy 매개 변수의 값으로 전달되어 테스트를 실행할 정책으로 사용된다는 점을 제외하고 예제 1과 동일합니다.

    $a = Get-CsVoicePolicy -Identity site:Redmond
    Test-CsVoicePolicy -TargetNumber "+14255559999" -VoicePolicy $a

## 예제 3

이 예제에서는 Lync Server 배포 내에 정의된 모든 음성 정책에 대해 음성 정책 테스트를 실행합니다. 먼저 매개 변수 없이 **Get-CsVoicePolicy** cmdlet을 실행하여 모든 음성 정책을 검색합니다. 반환된 정책 컬렉션은 제공된 대상 전화 번호(+12065559999) 및 전화 사용을 기준으로 컬렉션의 각 정책에 대해 일치하는 경로를 확인하는 **Test-CsVoicePolicy**에 파이프됩니다. 일치하는 경로 목록과 일치된 전화 사용이 출력됩니다.

    Get-CsVoicePolicy | Test-CsVoicePolicy -TargetNumber "+12065559999"

## 자세한 정보

음성 정책은 PSTN(공중 전화망)을 사용하여 음성 경로와 연결됩니다. 특정 음성 정책이 할당된 사용자의 통화는 PSTN 사용이 정책의 사용과 일치하고 번호 패턴이 전화 건 번호와 일치하는 경로를 통해서만 전송할 수 있습니다. **Test-CsVoicePolicy** cmdlet을 호출하여 특정 음성 정책이 적용된 사용자의 통화를 라우팅하는 데 사용할 경로(있는 경우) 및 정책을 경로에 연결하는 전화 사용을 확인합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Test-CsVoicePolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsVoicePolicy"}

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
<td><p><em>TargetNumber</em></p></td>
<td><p>필수</p></td>
<td><p>전화 번호</p></td>
<td><p>테스트를 실행할 전화 번호입니다. 이 번호는 E.164 형식이어야 합니다(예: +14255551212).</p></td>
</tr>
<tr class="even">
<td><p><em>VoicePolicy</em></p></td>
<td><p>필수</p></td>
<td><p>음성 정책</p></td>
<td><p>테스트를 실행할 음성 정책 개체에 대한 참조입니다. <strong>Get-CsVoicePolicy</strong> cmdlet을 호출하여 음성 정책 개체를 검색할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>cmdlet을 실행할 때 나타날 수 있는 확인 프롬프트 또는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>RouteSettings</em></p></td>
<td><p>선택</p></td>
<td><p>PSTN 경로 지정 설정</p></td>
<td><p>테스트를 실행할 경로 설정입니다. 경로 설정은 <strong>Get-CsRoutingConfiguration</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoicePolicy 개체입니다. 음성 정책 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

Microsoft.Rtc.Management.Voice.VoicePolicyTestResult 유형의 개체를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoicePolicy](new-csvoicepolicy.md)  
[Remove-CsVoicePolicy](remove-csvoicepolicy.md)  
[Set-CsVoicePolicy](set-csvoicepolicy.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)  
[Grant-CsVoicePolicy](grant-csvoicepolicy.md)

