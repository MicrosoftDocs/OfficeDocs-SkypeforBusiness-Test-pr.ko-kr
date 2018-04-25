---
title: Remove-CsHostedVoicemailPolicy
TOCTitle: Remove-CsHostedVoicemailPolicy
ms:assetid: 13968bbe-1403-46de-b02a-ed61e712d1b3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398211(v=OCS.15)
ms:contentKeyID: 49302882
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsHostedVoicemailPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

호스트된 음성 메일 정책을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsHostedVoicemailPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 명령은 ExRedmond 사용자별 정책에 대한 호스트된 음성 메일 정책을 제거합니다.

    Remove-CsHostedVoicemailPolicy -Identity ExRedmond

## 예제 2

예제 2의 명령은 모든 사용자별 호스트된 음성 메일 정책을 제거합니다. 먼저 이 명령은 사용자별 정책으로 정의된 모든 정책을 검색하는 Filter인 tag\*와 함께 **Get-CsHostedVoicemailPolicy** cmdlet을 호출합니다. 그런 다음, 각 정책을 삭제하는 **Remove-CsHostedVoicemailPolicy** cmdlet에 정책 집합이 파이프됩니다.

    Get-CsHostedVoicemailPolicy -Filter tag* | Remove-CsHostedVoicemailPolicy

## 자세한 정보

이 cmdlet은 사용자에 대한 응답하지 않은 통화를 호스트된 Exchange 통합 메시징(UM) 서비스에 경로 지정하는 방법을 지정하는 정책을 제거합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsHostedVoicemailPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsHostedVoicemailPolicy"}

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
<td><p>제거할 호스트된 음성 메일 정책에 대한 고유한 식별자입니다. 이 식별자는 범위(전역의 경우), 범위 및 사이트(site:Redmond와 같은 사이트 정책의 경우) 또는 정책 이름(HVUserPolicy와 같은 사용자별 정책의 경우)을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경 작업을 수행하기 전에 표시되는 모든 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>삭제할 호스트된 음성 메일 정책에 대한 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
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

이 cmdlet은 개체를 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Policy.Voice.HostedVoicemailPolicy 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsHostedVoicemailPolicy](new-cshostedvoicemailpolicy.md)  
[Set-CsHostedVoicemailPolicy](set-cshostedvoicemailpolicy.md)  
[Get-CsHostedVoicemailPolicy](get-cshostedvoicemailpolicy.md)  
[Grant-CsHostedVoicemailPolicy](grant-cshostedvoicemailpolicy.md)

