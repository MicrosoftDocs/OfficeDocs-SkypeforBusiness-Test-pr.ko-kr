---
title: Test-CsVoiceUser
TOCTitle: Test-CsVoiceUser
ms:assetid: f29c3b43-d315-4964-ab5c-9fb14612db34
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413013(v=OCS.15)
ms:contentKeyID: 49305500
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsVoiceUser

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 사용자의 전화 통화가 음성 규칙, 경로 및 정책에 따라 연결에 사용하는 경로를 식별합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsVoiceUser -DialedNumber <PhoneNumber> -SipUri <UserIdParameter> [-Force <SwitchParameter>]

## 예제

## 예제 1

이 예제에서는 SIP 주소가 sip:kmyer@litwareinc.com인 사용자에 대해 음성 사용자 테스트를 실행합니다. 이 테스트는 DialedNumber 매개 변수에서 제공한 전화 번호("+14255559999")에 대해 수행됩니다. 일치하는 규칙이나 경로가 식별되지 않는 경우 이 cmdlet은 null 값을 반환합니다. 이 예제에서는 Verbose 매개 변수도 포함했습니다. Verbose는 테스트가 수행될 때 테스트에 대해 로드되는 다이얼 플랜 및 음성 정책과 같은 추가 정보를 표시하는 Windows PowerShell 일반 매개 변수입니다.

    Test-CsVoiceUser -DialedNumber "+14255559999" -SipUri "sip:kmyer@litwareinc.com" -Verbose

## 예제 2

이 예제에서는 Lync Server 또는 Office Communications Server를 사용할 수 있는 모든 사용자에 대해 음성 경로 지정 테스트를 수행합니다. 이 명령은 먼저 Lync Server 또는 Office Communications Server를 사용할 수 있는 모든 사용자의 컬렉션을 반환하는 **Get-CsUser** cmdlet을 호출합니다. 그런 다음 이 사용자 컬렉션을 **ForEach-Object** cmdlet에 파이프합니다. 이 cmdlet은 각 개별 사용자 개체를 보고 중괄호({})에 지정된 작업을 수행합니다.

첫 번째 작업은 현재 사용자의 표시 이름을 출력하는 것입니다. 현재 사용자는 $\_ 문자로 표현됩니다. 따라서 표시 이름은 $\_의 DisplayName 속성에 있습니다. 이제 테스트하려는 사용자 계정을 볼 수 있습니다. 다음으로, **Test-CsVoiceUser** cmdlet을 호출하고 현재 사용자의 DialedNumber("+14255559999") 및 SipUri를 전달합니다. 이 예제에서는 사용자의 SIP 주소($\_.SipAddress)를 사용합니다.

마지막으로 출력은 기본적으로 테이블 형식이고 화면 너비에 맞게 잘릴 수 있으므로 각 사용자의 표시 이름 다음 줄에 각 출력 필드가 표시되도록 **Format-List** cmdlet에 테스트 결과를 파이프합니다.

    Get-CsUser | ForEach-Object {$_.DisplayName; Test-CsVoiceUser -DialedNumber "+14255559999" -SipUri $_.SipAddress} | Format-List

## 자세한 정보

사용자가 전화를 걸면 통화가 대상에 연결하는 데 사용하는 경로는 해당 사용자에게 할당된 정책 및 다이얼 플랜에 따라 달라집니다. 사용자의 SIP 주소 및 전화 번호가 주어졌을 때 이 cmdlet은 사용자의 다이얼 플랜에 기초하여 E.164 형식으로 변환된 번호, 해당 변환을 제공한 정규화 규칙, 경로 우선 순위를 기준으로 한 첫 번째 경로와 전화 번호와 일치하는 숫자 패턴 및 해당 사용자의 음성 정책을 음성 경로에 연결하는 전화 사용을 반환합니다.

이 cmdlet은 특정 정화 번호가 사용자 설정에 따라 예상대로 경로 지정되고 변환될지 파악하는 데 사용할 수 있으며 개별 사용자에 의해 발생한 문제를 해결하는 데 도움이 될 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Test-CsVoiceUser** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsVoiceUser"}

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
<td><p>테스트할 전화 번호입니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.Voice.PhoneNumber</p></td>
</tr>
<tr class="even">
<td><p><em>SipUri</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>테스트를 수행할 대상 사용자의 SIP URI입니다. 이는 CsUser cmdlet에서 사용되는 사용자의 ID입니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. SamAccountName은 ID로 사용할 수 없습니다.</p></td>
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

없음.

## 반환 형식

Microsoft.Rtc.Management.Voice.OcsVoiceUserTestResult 개체 유형을 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUser](get-csuser.md)

