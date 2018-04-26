---
title: Set-CsVoicePolicy
TOCTitle: Set-CsVoicePolicy
ms:assetid: e6035b74-d760-4c48-aa0b-d09d129e0830
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399021(v=OCS.15)
ms:contentKeyID: 49305349
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsVoicePolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 음성 정책을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsVoicePolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsVoicePolicy [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AllowCallForwarding <$true | $false>] [-AllowPSTNReRouting <$true | $false>] [-AllowSimulRing <$true | $false>] [-CallForwardingSimulRingUsageType <VoicePolicyUsage | InternalOnly | CustomUsage>] [-Confirm [<SwitchParameter>]] [-CustomCallForwardingSimulRingUsages <PSListModifier>] [-Description <String>] [-EnableBWPolicyOverride <$true | $false>] [-EnableCallPark <$true | $false>] [-EnableCallTransfer <$true | $false>] [-EnableDelegation <$true | $false>] [-EnableMaliciousCallTracing <$true | $false>] [-EnableTeamCall <$true | $false>] [-EnableVoicemailEscapeTimer <$true | $false>] [-Force <SwitchParameter>] [-Name <String>] [-PreventPSTNTollBypass <$true | $false>] [-PstnUsages <PSListModifier>] [-PSTNVoicemailEscapeTimer <Int64>] [-Tenant <Guid>] [-VoiceDeploymentMode <OnPrem | Online | OnlineBasic | OnPremOnlineHybrid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 UserVoicePolicy2라는 사용자별 정책에 대해 AllowSimulRing 속성을 False로 설정합니다. 따라서 이 정책에 할당된 모든 사용자는 사용자의 사무실 전화기에 전화가 왔을 때 다른 전화(예: 휴대폰)에도 벨이 울리는지 여부를 결정하는 동시 벨 울림 기능을 사용할 수 없습니다. 이 명령은 또한 이 정책에 대한 PSTN 사용법 목록에서 "Local"을 제거합니다. Identity 매개 변수가 명시적으로 지정되지 않았습니다. Identity 매개 변수는 위치 매개 변수이므로 매개 변수 목록에서 ID 값을 처음 포함한 경우 해당 값이 Identity라는 것을 명시적으로 지정할 필요가 없습니다.

    Set-CsVoicePolicy UserVoicePolicy2 -AllowSimulRing $false -PstnUsages @{remove="Local"}

## 예제 2

이 예제에서는 조직에 정의된 모든 PSTN 사용법이 이 정책에 적용되도록 Redmond 사이트에 대한 음성 정책을 수정합니다. 이 예제의 첫째 줄은 **Get-CsPstnUsage** cmdlet을 호출하여 조직에 대한 PSTN 사용법의 전역 집합을 검색하고 이를 $a 변수에 저장합니다. 둘째 줄은 **Set-CsVoicePolicy** cmdlet을 호출하여 Redmond 사이트에 대한 음성 정책을 수정합니다. 정책에 대한 현재 PSTN 사용법 목록을 전화 사용법의 전역 집합에 포함된 목록으로 대체하기 위해 PstnUsages 매개 변수에 값이 전달됩니다. 대체된 값의 구문은 $a.Usage입니다. 이 구문은 PSTN 사용법 목록을 포함하는 PSTN 사용법 설정의 Usage 속성을 나타냅니다.

    $a = Get-CsPstnUsage
    Set-CsVoicePolicy -Identity site:Redmond -PstnUsages @{replace=$a.Usage}

## 자세한 정보

이 cmdlet은 기존 음성 정책을 수정합니다. 음성 정책은 동시 벨 울림(누군가가 사무실 전화에 전화를 걸 때마다 또 다른 전화에서 벨이 울리는 기능) 및 착신 전환과 같은 Enterprise Voice 관련 기능을 관리하는 데 사용됩니다. 이 cmdlet을 사용하여 이러한 대부분의 기능을 활성화 및 비활성화하는 설정을 변경합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsVoicePolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoicePolicy"}

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
<td><p><em>AllowCallForwarding</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 매개 변수를 True로 설정하면 이 정책에 할당된 사용자가 착신 전환할 수 있습니다. 이 매개 변수가 False로 설정된 경우에는 통화를 착신 전환할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowPSTNReRouting</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 매개 변수를 True로 설정하면 풀이나 WAN을 사용할 수 없는 경우 지역 번호가 같은 다른 풀의 번호로 걸려 온 전화가 PSTN(공중 전화망)을 통해 경로 지정됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowSimulRing</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>동시 벨 울림은 한 번호로 전화를 걸었을 때 여러 개의 전화에서 벨이 울리는 기능입니다. 이 매개 변수를 True로 설정하면 동시 벨 울림이 활성화됩니다. 이 매개 변수가 False로 설정된 경우 이 정책에 대한 할당된 모든 사용자에 대해 동시 벨 울림을 구성할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CallForwardingSimulRingUsageType</em></p></td>
<td><p>선택</p></td>
<td><p>착신 전환 동시 전화 신호 울림 사용 유형</p></td>
<td><p>관리자가 착신 전환 및 동시 전화 신호 울림을 관리하는 방법을 제공합니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* VoicePolicyUsage - 기본 음성 정책 사용을 통해 모든 통화에 대한 착신 전환 및 동시 전화 신호 울림을 관리합니다. 기본값입니다.</p>
<p>* InternalOnly - Lync 사용자 간의 통화에 대해서만 착신 전환 및 동시 전화 신호 울림을 사용합니다.</p>
<p>* CustomUsage - 사용자 지정 PSTN 사용을 통해 착신 전환 및 동시 전화 신호 울림을 관리합니다. 이 사용은 CustomCallForwardingSimulRingUsages 매개 변수를 사용하여 지정해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CustomCallForwardingSimulRingUsages</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>착신 전환 및 동시 전화 신호 울림을 관리하는 데 사용되는 사용자 지정 PSTN 사용입니다. 음성 정책에 사용자 지정 사용을 추가하려면 다음과 같은 구문을 사용합니다.</p>
<p>-CustomCallForwardingSimulRingUsages @{Add=&quot;RedmondPstnUsage&quot;}</p>
<p>사용자 지정 사용을 제거하려면 다음 구문을 사용합니다.</p>
<p>-CustomCallForwardingSimulRingUsages @{Remove=&quot;RedmondPstnUsage&quot;}</p>
<p>이미 존재하는 사용만 CustomCallForwardingSimulRingUsages 매개 변수에서 사용할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>음성 정책에 대한 설명입니다.</p>
<p>최대 길이: 1040자</p></td>
</tr>
<tr class="even">
<td><p><em>EnableBWPolicyOverride</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>대역폭을 제한하고 네트워크 구성과 관련된 여러 개의 다른 속성을 지정하기 위해 정책을 설정할 수 있습니다. 이 매개 변수를 True로 설정하면 이러한 정책을 무시할 수 있습니다. 즉, 이 매개 변수를 True로 설정하면 CAC(통화 허용 제어) 설정에 관계없이 대역폭을 확인하지 않고 통화가 실행됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableCallPark</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>통화 대기 응용 프로그램을 사용하면 나중에 검색하기 위해 번호 범위 내의 특정 번호에서 통화를 보류하거나 대기시킬 수 있습니다. 이 매개 변수를 True로 설정하면 이 정책이 할당된 사용자에 대해 이 응용 프로그램을 사용하도록 설정할 수 있습니다. 이 매개 변수를 False로 설정하면 이 정책에 할당된 사용자가 자신의 전화 번호로 걸려 온 통화를 대기시킬 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableCallTransfer</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>통화를 다른 번호로 전송할 수 있는지 여부를 결정합니다. 이 매개 변수가 True로 설정된 경우 통화를 전송할 수 있고 이 매개 변수가 False로 설정된 경우 통화를 전송할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableDelegation</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>통화 위임을 통해 사용자는 다른 사용자 대신 통화에 응답하거나 전화를 걸 수 있습니다. 예를 들어, 운영자는 전화가 걸려오면 자신의 전화와 관리자의 전화 둘 다에서 벨이 울리도록 통화 위임을 설정할 수 있습니다. 이 매개 변수를 True로 설정하면 이 정책을 가진 사용자가 통화 위임을 설정할 수 있습니다. 이 매개 변수를 False로 설정하면 통화 위임이 비활성화됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableMaliciousCallTracing</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>악의적 통화 추적은 사용자가 악의적인 것으로 지정한 통화를 추적하는 표준입니다. 호출자 ID가 차단된 경우에도 이러한 통화를 추적할 수 있습니다. 추적은 사용자가 아니라 올바른 기관에만 사용할 수 있습니다. 이 속성을 True로 설정하면 악의적인 통화를 추적하는 기능이 활성화됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableTeamCall</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>팀 통화를 사용하면 사용자는 자신에게 전화가 걸려 왔을 때 다른 사용자의 전화가 울리도록 다른 사용자의 그룹을 지정할 수 있습니다. 예를 들어, 팀의 모든 구성원이 고객의 전화를 받을 수 있는 상황에서 이 기능이 유용합니다. 이 매개 변수를 True로 설정하면 이 기능이 활성화됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableVoicemailEscapeTimer</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>True로 설정하면 응답하지 않는 모바일 장치에 대한 전화가 모바일 장치 공급자의 음성 메일이 아닌 조직의 음성 메일로 라우팅됩니다. PSTNVoicemailEscapeTimer 속성에 대해 구성된 값에 해당하는 시간이 경과하기 전에 전화를 &quot;너무 빨리&quot; 받으면 해당 모바일 장치를 사용할 수 없는 것으로 간주하여 통화가 역시 조직의 음성 메일로 라우팅됩니다.</p>
<p>기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>변경 내용을 적용하기 전에 표시될 수 있는 확인 메시지를 숨깁니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Xds ID</p></td>
<td><p>정책의 범위나 경우에 따라서는 이름을 지정하는 고유한 식별자입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>음성 정책</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다. 이 개체의 유형은 VoicePolicy여야 하며, <strong>Get-CsVoicePolicy</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>이 정책을 설명하는 알기 쉬운 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PreventPSTNTollBypass</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>PSTN 유료 전화는 장거리 요금으로 더 잘 알려져 있습니다. 경우에 따라 조직에서는 지점 사무실이 네트워크 통화를 통해 연결할 수 있는 VoIP(Voice over Internet Protocol) 솔루션을 구현하여 이러한 유료 전화를 우회할 수 있습니다. 이 매개 변수를 True로 설정하면 네트워크를 통과하여 유료 전화를 우회하는 대신에 PSTN을 통해 통화가 전송되고 요금이 발생합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PstnUsages</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>이 정책에 사용할 수 있는 PSTN 사용법 목록입니다. PSTN 사용법은 음성 정책을 전화 경로에 연결합니다.</p>
<p>현재 PSTN 사용법의 전역 목록에 있는 문자열이면 모두 이 목록에 배치할 수 있습니다. 중복된 문자열은 허용되지 않으며 모든 문자열은 고유해야 합니다. <strong>Get-CsPstnUsage</strong> cmdlet을 호출하여 PSTN 사용법 목록을 검색할 수 있습니다.</p>
<p>이 매개 변수를 사용하여 모든 PSTN 사용법을 정책에서 제거하면 이 정책이 부여된 사용자가 아웃바운드 PSTN 전화를 걸 수 없게 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PSTNVoicemailEscapeTimer</em></p></td>
<td><p>선택</p></td>
<td><p>Int64</p></td>
<td><p>전화를 &quot;너무 빨리&quot; 받았는지를 결정하는 데 사용되는 시간(밀리초)입니다. 이 시간 간격 내에 응답이 수신되면 Lync Server는 모바일 장치를 사용할 수 없는 것으로 간주하여 전화를 조직의 음성 메일로 자동 전환합니다. 시간 간격에 도달하기 전에 응답이 수신되지 않은 경우에는 전화를 처리할 수 있습니다.</p>
<p>기본값은 1500밀리초입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>GUID</p></td>
<td><p>해당 음성 정책을 수정할 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
<tr class="odd">
<td><p><em>VoiceDeploymentMode</em></p></td>
<td><p>선택</p></td>
<td><p>음성 배포 모드</p></td>
<td><p>사용 가능한 값은 다음과 같습니다.</p>
<p>* OnPrem</p>
<p>* Online</p>
<p>* OnlineBasic</p>
<p>* OnPremOnlineHybrid</p>
<p>기본값은 OnPrem입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoicePolicy 개체입니다. 음성 정책 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값이나 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Voice.VoicePolicy 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoicePolicy](new-csvoicepolicy.md)  
[Remove-CsVoicePolicy](remove-csvoicepolicy.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)  
[Grant-CsVoicePolicy](grant-csvoicepolicy.md)  
[Test-CsVoicePolicy](test-csvoicepolicy.md)  
[Get-CsPstnUsage](get-cspstnusage.md)

