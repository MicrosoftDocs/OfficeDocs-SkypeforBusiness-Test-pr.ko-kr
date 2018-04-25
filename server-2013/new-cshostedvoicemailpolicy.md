---
title: New-CsHostedVoicemailPolicy
TOCTitle: New-CsHostedVoicemailPolicy
ms:assetid: 81e1ec62-45c4-49ad-8e2b-3568c092b6c1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398653(v=OCS.15)
ms:contentKeyID: 49304211
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsHostedVoicemailPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

호스트된 음성 메일 정책을 새로 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsHostedVoicemailPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Description <String>] [-Destination <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Organization <String>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 명령은 ExRedmond라는 호스트된 음성 메일 정책을 새로 만듭니다. 범위가 지정되지 않았으므로 이 정책을 개별 사용자나 연락처에 할당할 수 있습니다. 이 정책에서는 정책의 Exchange UM 대상이 FQDN ExUM.fabrikam.com에 있도록 정의합니다. 또한 이 정책의 Lync Server 사용자는 litwareinc의 corp1 및 corp2 조직에 분산될 수 있습니다. Description 매개 변수 값인 "Redmond 사용자에 대한 호스트된 음성 메일 속성"으로 이 정책을 설명할 수 있습니다.

    New-CsHostedVoicemailPolicy -Identity ExRedmond -Destination ExUM.fabrikam.com -Description "Hosted voicemail policy for Redmond users." -Organization "corp1.litwareinc.com, corp2.litwareinc.com"

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령의 변형입니다. 그러나 이 경우에는 새로 호스트되는 음성 사서함 정책이 테넌트 ID ID 73d355dd-ce5d-4ab9-bf49-7b822c18dd98의 Lync Online 테넌트에 할당됩니다. Lync Online 테넌트에 대한 새 정책을 만들려면 InMemory 매개 변수를 포함하고 결과 정책을 변수에 저장해야 합니다. 이는 첫 번째 명령에서 수행되며 이름이 $x인 변수에 새 정책이 저장됩니다. 또한 ID를 전역으로 설정하고 Tenant 매개 변수를 적절한 테넌트 ID로 설정해야 합니다.

그러면 새 정책을 만들기 위해 두 번째 명령에서 Instance 및 Tenant 매개 변수와 함께 **Set-CsHostedVoiceMailPolicy** cmdlet을 호출합니다.

    $x = New-CsHostedVoiceMailPolicy -Identity global -Tenant "73d355dd-ce5d-4ab9-bf49-7b822c18dd98" -Destination ExUM.fabrikam.com -Description "Hosted voicemail policy for Redmond users." -Organization "corp1.litwareinc.com, corp2.litwareinc.com"
    Set-CsHostedVoiceMailPolicy -Instance $x -Tenant "73d355dd-ce5d-4ab9-bf49-7b822c18dd98"

## 자세한 정보

이 cmdlet은 Exchange 통합 메시징(UM) 호스트된 음성 메일 서비스를 사용하기 위해 Lync Server 또는 Office Communications Server를 사용하도록 설정된 사용자 계정을 구성하는 정책을 만듭니다. 이 정책은 사용자에 대한 응답하지 않은 통화를 호스트된 Exchange UM 서비스에 경로 지정하는 방법을 결정합니다.

이 정책을 적용하려면 사용자는 Exchange UM 호스트된 음성 메일에 대해 활성화되어야 합니다. **Get-CsUser** cmdlet을 호출하고 HostedVoiceMail 속성을 검사하여 사용자가 호스트된 음성 메일에 대해 활성화되었는지 여부를 확인할 수 있습니다. (True 값은 사용자가 활성화되었다는 것을 의미합니다.)

사이트 범위에서 만들어진 정책은 이 사이트에 속한 사용자에게 자동으로 할당됩니다. 사용자별 범위에서 만들어진 정책은 **Grant-CsHostedVoicemailPolicy** cmdlet을 사용하여 사용자 또는 연락처 개체에 할당해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsHostedVoicemailPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsHostedVoicemailPolicy"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>범위 및 사이트(site:Redmond와 같은 사이트 정책의 경우) 또는 정책 이름(RenoHostedVoicemail과 같은 사용자별 정책의 경우)을 포함하는 정책에 대한 고유 식별자입니다. 전역 정책은 항상 존재하고 제거할 수 없으므로 만들 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>정책에 대한 친숙한 설명입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Destination</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수에 할당된 값은 호스트된 Exchange UM 서비스의 FQDN(정규화된 도메인 이름)입니다. 선택한 대상은 라우팅용으로 신뢰할 수 있어야 합니다.</p>
<p>이 매개 변수는 선택 사항이지만 호스트된 음성 메일에 대해 사용자를 활성화하려는 경우 사용자의 할당된 정책에 Destination 값이 없으면 활성화가 실패합니다.</p>
<p>이 값은 255자 이내여야 하며 server.litwareinc.com과 같은 FQDN 형식이어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
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
<td><p>새 호스트된 음성 사서함 정책이 만들어지는 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identification)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대한 테넌트 ID를 반환할 수 있습니다.</p>
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

없음.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.HostedVoicemailPolicy 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsHostedVoicemailPolicy](remove-cshostedvoicemailpolicy.md)  
[Set-CsHostedVoicemailPolicy](set-cshostedvoicemailpolicy.md)  
[Get-CsHostedVoicemailPolicy](get-cshostedvoicemailpolicy.md)  
[Grant-CsHostedVoicemailPolicy](grant-cshostedvoicemailpolicy.md)

