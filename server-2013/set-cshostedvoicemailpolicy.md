---
title: Set-CsHostedVoicemailPolicy
TOCTitle: Set-CsHostedVoicemailPolicy
ms:assetid: 9c47d2a5-356c-4bab-9cef-8346c4b5d99c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412722(v=OCS.15)
ms:contentKeyID: 49304517
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsHostedVoicemailPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

호스트된 음성 메일 정책을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsHostedVoicemailPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsHostedVoicemailPolicy [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Destination <String>] [-Force <SwitchParameter>] [-Organization <String>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 명령은 ExRedmond라는 호스트된 음성 메일 정책의 Destination 속성을 수정합니다. 이 명령은 이 정책의 Exchange UM 대상이 FQDN ExUM.contoso.com에 있도록 설정합니다.

    Set-CsHostedVoicemailPolicy -Identity ExRedmond -Destination ExUM.contoso.com

## 예제 2

이 명령은 정책 ExRedmond에 대한 보유자(조직)의 쉼표로 구분된 목록에 Exchange 보유자를 추가합니다. 첫 줄은 **Get-CsHostedVoicemailPolicy** cmdlet을 호출하여 ID가 ExRedmond인 정책을 검색합니다. 처음에 이 정책을 검색해야 하므로 이 cmdlet 호출은 괄호 안에 있습니다. 그런 다음, "점 표기법"을 사용하여 정책의 Organization 속성을 검색합니다. 반환된 문자열을 변수 $a에 저장합니다. 다음 줄에서는 += 연산자를 사용하여 할당된 문자열(,corp3.litwareinc.com)을 변수 $a에 저장된 문자열 끝에 추가합니다. 할당된 문자열에 쉼표가 있다는 것에 주의합니다. Organization은 쉼표로 구분된 목록이므로 목록에 이미 값이 있는 경우 모든 추가 값은 앞에 쉼표가 와야 합니다. 최종적으로 마지막 줄에서는 변수 $a를 매개 변수 Organization에 전달하여 **Set-CsHostedVoicemailPolicy** cmdlet을 호출하고 새 Organization 문자열을 할당합니다.

    $a = (Get-CsHostedVoicemailPolicy -Identity ExRedmond).Organization
    $a += ",corp3.litwareinc.com"
    Set-CsHostedVoicemailPolicy -Identity ExRedmond -Organization $a

## 예제 3

예제 3에 표시된 명령은 테넌트 ID 73d355dd-ce5d-4ab9-bf49-7b822c18dd98의 Lync Online 테넌트에 할당된 호스트된 음성 사서함 정책의 Destination 속성을 수정합니다.

    Set-CsHostedVoicemailPolicy -Tenant "73d355dd-ce5d-4ab9-bf49-7b822c18dd98" -Destination "ExUM.contoso.com"

## 자세한 정보

이 cmdlet은 Exchange 통합 메시징(UM) 호스트된 음성 메일 서비스를 사용하기 위해 Lync Server 또는 Microsoft Office Communications Server에 대해 활성화된 사용자 계정을 구성하는 정책을 수정합니다. 이 정책은 사용자에 대한 응답하지 않은 통화를 호스트된 Exchange UM 서비스에 경로 지정하는 방법을 결정합니다.

이 정책을 적용하려면 사용자는 Exchange UM 호스트된 음성 메일에 대해 활성화되어야 합니다. **Get-CsUser** cmdlet을 호출하고 HostedVoiceMail 속성을 검사하여 사용자가 호스트된 음성 메일에 대해 활성화되었는지 여부를 확인할 수 있습니다. (True 값은 사용자가 활성화되었다는 것을 의미합니다.)

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsHostedVoicemailPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsHostedVoicemailPolicy"}

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
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>정책에 대한 친숙한 설명입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Destination</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수에 할당된 값은 호스트된 Exchange UM 서비스의 FQDN(정규화된 도메인 이름)입니다. 선택한 대상은 라우팅용으로 신뢰할 수 있어야 합니다.</p>
<p>사용자의 할당된 정책에 Destination 값이 없는 경우 호스트된 음성 메일에 대해 사용자를 활성화하려고 하면 활성화가 실패합니다.</p>
<p>이 값은 255자 이하여야 하고 정규식 문자열 ^[a-zA-Z0-9\-_]+(\.[a-zA-Z0-9\-_]+){0,}$와 일치하는 형식이어야 합니다. 이는 단지 값이 server.litwareinc.com과 같은 FQDN 형식이야 한다는 것을 의미합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 호스트된 음성 메일 정책에 대한 고유한 식별자입니다. 이 식별자는 범위(전역의 경우), 범위 및 사이트(사이트 정책의 경우, 예: site:Redmond) 또는 정책 이름(사용자별 정책의 경우, 예: HVUserPolicy)을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>HostedVoicemailPolicy</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다. 개체는 HostedVoicemailPolicy 유형이어야 하고 <strong>Get-CsHostedVoicemailPolicy</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Organization</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수는 Lync Server 사용자를 포함하는 Exchange 보유자의 쉼표로 구분된 목록을 포함합니다. 각 보유자는 호스트된 Exchange 서비스에서 보유자의 FQDN으로 지정되어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>수정할 호스트된 음성 메일 정책에 대한 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.HostedVoicemailPolicy 개체입니다. 호스트된 음성 메일 정책 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.HostedVoicemailPolicy 유형의 개체를 수정합니다.

## 참고 항목

#### 기타 리소스

[New-CsHostedVoicemailPolicy](new-cshostedvoicemailpolicy.md)  
[Remove-CsHostedVoicemailPolicy](remove-cshostedvoicemailpolicy.md)  
[Get-CsHostedVoicemailPolicy](get-cshostedvoicemailpolicy.md)  
[Grant-CsHostedVoicemailPolicy](grant-cshostedvoicemailpolicy.md)

