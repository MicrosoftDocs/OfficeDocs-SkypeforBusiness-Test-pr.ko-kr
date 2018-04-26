---
title: Remove-CsVoicePolicy
TOCTitle: Remove-CsVoicePolicy
ms:assetid: 4d3e67be-c094-415f-b1e6-0719dec6f3fc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398309(v=OCS.15)
ms:contentKeyID: 49303590
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsVoicePolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 음성 정책을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsVoicePolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 UserVoicePolicy1 사용자별 음성 정책 설정을 제거합니다.

    Remove-CsVoicePolicy -Identity UserVoicePolicy1

## 예제 2

이 예제에서는 특정 사용자에게 할당할 수 있는 모든 음성 정책 설정을 제거합니다. 먼저 **Get-CsVoicePolicy** cmdlet은 모든 사용자별 음성 정책을 검색하는 tag\* 필터와 함께 호출됩니다. 그런 다음, 해당 정책 컬렉션은 제거할 **Remove-CsVoicePolicy** cmdlet에 파이프됩니다.

    Get-CsVoicePolicy -Filter tag* | Remove-CsVoicePolicy

## 자세한 정보

이 cmdlet은 기존 음성 정책을 제거합니다. 음성 정책은 동시 벨 울림(누군가가 사무실 전화에 전화를 걸 때마다 또 다른 전화에서 벨이 울리는 기능) 및 착신 전환과 같은 Enterprise Voice 관련 기능을 관리하는 데 사용됩니다. 또한 이 cmdlet을 사용하여 전역 음성 정책을 제거할 수 있습니다. 그러나 이 경우 정책은 실제로 제거되지 않으며 단순히 정책 설정이 기본값으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsVoicePolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsVoicePolicy"}

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
<td><p>제거할 정책의 범위나 경우에 따라서는 이름을 지정하는 고유한 식별자입니다.</p></td>
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
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>삭제할 음성 정책에 대한 Office 365 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Windows PowerShell의 원격 세션을 사용 중이고 비즈니스용 Skype Online에만 연결되는 경우 Tenant 매개 변수를 포함하지 않아도 됩니다. 대신, 연결 정보에 따라 테넌트 ID가 자동으로 채워집니다. Tenant 매개 변수는 하이브리드 배포에서 주로 사용됩니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoicePolicy 개체입니다. 음성 정책 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoicePolicy 개체의 인스턴스를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoicePolicy](new-csvoicepolicy.md)  
[Set-CsVoicePolicy](set-csvoicepolicy.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)  
[Grant-CsVoicePolicy](grant-csvoicepolicy.md)  
[Test-CsVoicePolicy](test-csvoicepolicy.md)

