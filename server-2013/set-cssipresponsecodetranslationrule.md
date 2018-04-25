---
title: Set-CsSipResponseCodeTranslationRule
TOCTitle: Set-CsSipResponseCodeTranslationRule
ms:assetid: 3ce2fafe-9c79-4462-9f24-c2a30502e641
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425895(v=OCS.15)
ms:contentKeyID: 49303378
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsSipResponseCodeTranslationRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 SIP 응답 코드 변환 규칙을 수정합니다. 이러한 규칙을 통해 관리자는 값이 400에서 699 사이인 SIP 응답 코드를 Lync Server에서 사용하는 값에 매핑할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsSipResponseCodeTranslationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsSipResponseCodeTranslationRule [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Priority <Int32>] [-ReceivedISUPCauseValue <Int32>] [-ReceivedResponseCode <Int32>] [-TranslatedResponseCode <Int32>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 PstnGateway:192.168.0.240/Rule404인 변환 규칙의 ReceivedISUPCauseValue 속성을 수정합니다.

    Set-CsSipResponseCodeTranslationRule -Identity "PstnGateway:192.168.0.240/Rule404" -ReceivedISUPCauseValue 477

## 예제 2

예제 2에서는 ID가 PstnGateway:192.168.0.240/Rule404인 변환 규칙을 우선 순위가 가장 높은 규칙, 즉 맨 먼저 처리되는 규칙으로 표시합니다. 이를 위해 Priority를 0으로 설정합니다.

    Set-CsSipResponseCodeTranslationRule -Identity "PstnGateway:192.168.0.240/Rule404" -Priority 0

## 예제 3

예제 3에서는 조직에서 사용하도록 구성된 모든 변환 규칙의 ReceivedISUPCauseValue 속성을 -1로 설정하는 방법을 보여 줍니다. 이렇게 하면 규칙을 변환할 때 ISUP 이유 코드가 무시됩니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsSipResponseCodeTranslationRule** cmdlet을 호출하여 현재 사용 중인 모든 SIP 응답 코드 변환 규칙의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 항목에 대한 ReceivedISUPCauseValue 속성을 수정하는 **Set-CsSipResponseCodeTranslationRule** cmdlet에 파이프됩니다.

    Get-CsSipResponseCodeTranslationRule | Set-CsSipResponseCodeTranslationRule -ReceivedISUPCauseValue -1

## 자세한 정보

SIP 트렁크를 사용하면 PSTN(공중 전화망)을 통해 VoIP(Voice over Internet Protocol) 네트워크(예: Enterprise Voice)를 연결할 수 있습니다. Lync Server에서 중재 서버는 트렁크 피어를 사용하여 PSTN 네트워크와 상호 작용합니다. PSTN 네트워크에서 발신 전화에 실패하면 ISUP(ISDN User Part) 이유 코드가 자동으로 생성됩니다. 예를 들어 PSTN 게이트웨이에서 전화를 완료하는 데 사용 가능한 회로 또는 채널이 없음을 나타내는 이유 코드 34를 전송할 수 있습니다. 중재 서버 트렁크 피어는 ISUP 이유 코드를 받아 SIP 응답 코드로 변환한 후 중재 서버 자신에게 다시 전송합니다. 그러면 Lync Server에서 이러한 응답 코드를 사용하여 아웃바운드 경로 지정을 결정합니다. 예를 들어 제대로 작동하지 않는 게이트웨이에 "less-preferred" 상태가 자동으로 할당될 수 있습니다. 이를 통해 이 게이트웨이 사용 수를 최소화하고 통화가 성공적으로 완료될 가능성을 최대화할 수 있습니다.

그러나 일부 게이트웨이는 권장 ISUP 이유 코드와 Lync Server에서 사용하는 SIP 응답 코드 간의 매핑을 사용하지 않습니다. 이러한 게이트웨이의 경우 관리자는 **CsSipResponseCodeTranslationRule** cmdlet을 사용하여 게이트웨이 SIP 응답 코드(ISUP 이유 코드를 사용할 수 있는 경우 이 코드와 조합)를 Lync Server에서 사용하는 SIP 응답 코드에 매핑할 수 있습니다. 예를 들어 게이트웨이에서 ISUP 이유 코드 34("사용 가능한 회로/채널 없음")를 SIP 응답 코드 486 ("여기에서 사용 중")에 매핑할 수 있습니다. 이렇게 하면 응답 코드 486에 따라 Lync Server의 아웃바운드 경로 지정 논리가 통화를 완료하기 위해 새 게이트웨이를 찾으려고 시도하지 않습니다.

그러나 Lync Server의 경우에는 대신에 이러한 SIP 응답 코드 486이 SIP 응답 코드 503에 매핑되어야 합니다. 응답 코드 503은 Lync Server의 아웃바운드 경로 지정 논리에서 재시도 메커니즘을 트리거합니다. 즉, 시스템에서 통화를 완료하기 위해 다른 게이트웨이를 찾습니다. 이 상황을 처리하기 위해 ISUP 이유 코드 34와 SIP 응답 코드 486의 조합을 SIP 응답 코드 503에 매핑하는 변환 규칙을 만들 수 있습니다.

**Set-CsSipResponseCodeTranslationRule** cmdlet을 사용하면 조직에서 사용하도록 이전에 구성된 변환 규칙을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsSipResponseCodeTranslationRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsSipResponseCodeTranslationRule"}

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
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 변환 규칙의 고유 식별자입니다. 변환 규칙 ID는 규칙이 구성된 범위 및 규칙을 만들 때 지정된 이름의 두 부분으로 구성됩니다. 예를 들어 전역 범위에서 만들어진 Rule404라는 변환 규칙의 ID는 global/Rule404와 유사할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>정수</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Priority</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>변환 규칙의 상대적인 우선 순위입니다. 규칙은 할당된 우선 순위대로 처리됩니다. 맨 먼저 처리할 규칙의 우선 순위는 0이고 두 번째로 처리할 규칙의 우선 순위는 1입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ReceivedISUPCauseValue</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>게이트웨이에서 INVITE 메시지에 응답할 때 사용하는 SIP 응답 메시지에 나타나야 하는 ISUP(ISDN User Part) 코드 값입니다. 값 -1은 변환 규칙을 실행할 때 SIP 응답 코드만 사용되고 ISUP 이유 코드는 무시됨을 나타냅니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ReceivedResponseCode</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>게이트웨이에서 INVITE 메시지에 응답할 때 사용하는 SIP 응답 코드 값입니다. 응답 코드는 400에서 699(포함) 사이의 정수 값일 수 있습니다. 이 cmdlet은 400보다 작은 정수 값을 허용하지만 이러한 값은 최종 응답으로 인식되지 않습니다. 따라서 변환 규칙이 사용되지 않습니다. 값 0은 변환 규칙을 실행할 때 ISUP 이유 코드만 사용되고 SIP 응답 코드는 무시됨을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TranslatedResponseCode</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>ReceivedResponseCode 및/또는 ReceivedISUPCauseCode를 변환해야 하는 SIP 응답 코드 값입니다. 변환된 응답 코드는 400에서 699(포함) 사이의 정수 값일 수 있습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.SipResponseCodeTranslationRule\#Decorated 개체입니다. **Set-CsSipResponseCodeTranslationRule** cmdlet은 SIP 응답 코드 변환 규칙 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsSipResponseCodeTranslationRule** cmdlet은 개체나 값을 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.SipResponseCodeTranslationRule\#Decorated 개체의 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsSipResponseCodeTranslationRule](get-cssipresponsecodetranslationrule.md)  
[New-CsSipResponseCodeTranslationRule](new-cssipresponsecodetranslationrule.md)  
[Remove-CsSipResponseCodeTranslationRule](remove-cssipresponsecodetranslationrule.md)

