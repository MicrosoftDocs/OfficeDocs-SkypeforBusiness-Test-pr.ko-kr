---
title: New-CsSipResponseCodeTranslationRule
TOCTitle: New-CsSipResponseCodeTranslationRule
ms:assetid: f7667ffd-3d11-40ec-87d4-7f9b1a861aae
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413041(v=OCS.15)
ms:contentKeyID: 49305560
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsSipResponseCodeTranslationRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 SIP 응답 코드 변환 규칙을 만듭니다. 이러한 규칙을 통해 관리자는 값이 400에서 699 사이인 SIP 응답 코드를 Lync Server에서 사용하는 값에 매핑할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsSipResponseCodeTranslationRule -Name <String> -Parent <String> <COMMON PARAMETERS>

    New-CsSipResponseCodeTranslationRule -Identity <XdsIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: -TranslatedResponseCode <Int32> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Priority <Int32>] [-ReceivedISUPCauseValue <Int32>] [-ReceivedResponseCode <Int32>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 PstnGateway:192.168.0.240/Rule404인 새 SIP 응답 코드 변환 규칙을 만듭니다. 이 규칙은 수신된 응답 코드 434를 표준 SIP 응답 코드 404(없음)로 변환합니다.

    New-CsSipResponseCodeTranslationRule -Identity "PstnGateway:192.168.0.240/Rule404" -ReceivedResponseCode 434 -TranslatedResponseCode 404

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령과 동일한 작업을 수행합니다. 예제 2에서는 그러나 Identity 매개 변수가 아닌 Parent 및 Name 매개 변수를 사용합니다. 이는 ID가 PstnGateway:192.168.0.240/Rule404인 새 SIP 응답 코드 변환 규칙을 만드는 또 다른 방법을 보여 줍니다.

    New-CsSipResponseCodeTranslationRule -Parent "PstnGateway:192.168.0.240" -Name "Rule404" -ReceivedResponseCode 434 -TranslatedResponseCode 404

## 자세한 정보

SIP 트렁크를 사용하면 PSTN(공중 전화망)을 통해 VoIP(Voice over Internet Protocol) 네트워크(예: Enterprise Voice)를 연결할 수 있습니다. Lync Server에서 중재 서버는 트렁크 피어를 사용하여 PSTN 네트워크와 상호 작용합니다. PSTN 네트워크에서 발신 전화에 실패하면 ISUP(ISDN User Part) 이유 코드가 자동으로 생성됩니다. 예를 들어 PSTN 게이트웨이에서 전화를 완료하는 데 사용 가능한 회로 또는 채널이 없음을 나타내는 이유 코드 34를 전송할 수 있습니다. 중재 서버 트렁크 피어는 ISUP 이유 코드를 받아 SIP 응답 코드로 변환한 후 중재 서버 자신에게 다시 전송합니다. 그러면 Lync Server에서 이러한 응답 코드를 사용하여 아웃바운드 경로 지정을 결정합니다. 예를 들어 제대로 작동하지 않는 게이트웨이에 "less-preferred" 상태가 자동으로 할당될 수 있습니다. 이를 통해 이 게이트웨이 사용 수를 최소화하고 통화가 성공적으로 완료될 가능성을 최대화할 수 있습니다.

그러나 일부 게이트웨이는 권장 ISUP 이유 코드와 Lync Server에서 사용하는 SIP 응답 코드 간의 매핑을 사용하지 않습니다. 이러한 게이트웨이의 경우 관리자는 **CsSipResponseCodeTranslationRule** cmdlet을 사용하여 게이트웨이 SIP 응답 코드(ISUP 이유 코드를 사용할 수 있는 경우 이 코드와 조합)를 Lync Server에서 사용하는 SIP 응답 코드에 매핑할 수 있습니다. 예를 들어 게이트웨이에서 ISUP 이유 코드 34("사용 가능한 회로/채널 없음")를 SIP 응답 코드 486 ("여기에서 사용 중")에 매핑할 수 있습니다. 이렇게 하면 응답 코드 486에 따라 Lync Server의 아웃바운드 경로 지정 논리가 통화를 완료하기 위해 새 게이트웨이를 찾으려고 시도하지 않습니다.

그러나 Lync Server의 경우에는 대신에 이러한 SIP 응답 코드 486이 SIP 응답 코드 503에 매핑되어야 합니다. 응답 코드 503은 Lync Server의 아웃바운드 경로 지정 논리에서 재시도 메커니즘을 트리거합니다. 즉, 시스템에서 통화를 완료하기 위해 다른 게이트웨이를 찾습니다. 이 상황을 처리하기 위해 ISUP 이유 코드 34와 SIP 응답 코드 486의 조합을 SIP 응답 코드 503에 매핑하는 변환 규칙을 만들 수 있습니다. 이러한 새 변환 규칙은 **New-CsSipResponseCodeTranslationRule** cmdlet을 사용하여 만듭니다. 변환 규칙은 전역 범위, 사이트 범위 또는 서비스 범위에 할당할 수 있습니다(PSTN 게이트웨이 서비스만 해당).

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsSipResponseCodeTranslationRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsSipResponseCodeTranslationRule"}

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
<td><p>만들 변환 규칙의 고유 식별자입니다. 변환 규칙 ID는 규칙을 할당할 범위와 규칙에 지정할 이름의 두 부분으로 구성됩니다. 예를 들어 전역 범위에서 만들어진 Rule404라는 변환 규칙의 ID는 global/Rule404와 유사할 수 있습니다.</p>
<p>Identity 매개 변수 대신 Parent 및 Name 매개 변수를 사용하여 새 변환 규칙을 만들 수도 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>한 변환 규칙을 식별하는 데 사용되는 이름입니다. 이름은 지정된 범위 내에서 고유해야 합니다. 예를 들어 Redmond 사이트는 Rule404라는 변환 규칙 하나만 가질 수 있습니다. 그러나 Redmond 사이트에 Rule404라는 변환 규칙을 가지고 Dublin 사이트에 Rule404라는 다른 규칙을 가질 수 있습니다.</p>
<p>Name 매개 변수는 항상 Parent 매개 변수와 함께 사용해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Parent</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 변환 규칙을 할당할 범위입니다. 전역 범위에 규칙을 할당하려면 -Parent global 구문을 사용합니다. 사이트 범위에 규칙을 할당하려면 -Parent site:Redmond와 유사한 구문을 사용합니다. 서비스 범위에 규칙을 할당하려면 -Parent PstnGateway:192.168.0.242와 유사한 구문을 사용합니다.</p>
<p>Parent 매개 변수는 항상 Name 매개 변수와 함께 사용해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TranslatedResponseCode</em></p></td>
<td><p>필수</p></td>
<td><p>System.Int32</p></td>
<td><p>ReceivedResponseCode 및/또는 ReceivedISUPCauseCode가 변환되어야 하는 Lync Server SIP 응답 코드의 값입니다. 변환된 응답 코드는 400에서 699(포함) 사이의 정수 값일 수 있습니다.</p></td>
</tr>
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
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Priority</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>변환 규칙의 상대적인 우선 순위입니다. 규칙은 할당된 우선 순위대로 처리됩니다. 맨 먼저 처리할 규칙의 우선 순위는 0이고 두 번째로 처리할 규칙의 우선 순위는 1입니다. 이 매개 변수를 지정하지 않으면 새 규칙에 해당 범위에서 가장 낮은 우선 순위가 부여됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ReceivedISUPCauseValue</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>게이트웨이에서 INVITE 메시지에 응답할 때 사용하는 SIP 응답 메시지에 나타나야 하는 ISUP(ISDN User Part) 코드 값입니다. 값 -1은 변환 규칙을 실행할 때 SIP 응답 코드만 사용되고 ISUP 이유 코드는 무시됨을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ReceivedResponseCode</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>게이트웨이에서 INVITE 메시지에 응답할 때 사용하는 SIP 응답 코드 값입니다. 응답 코드는 400에서 699(포함) 사이의 정수 값일 수 있습니다. 이 cmdlet은 400보다 작은 정수 값을 허용하지만 이러한 값은 최종 응답으로 인식되지 않습니다. 따라서 변환 규칙이 사용되지 않습니다. 값 0은 변환 규칙을 실행할 때 ISUP 이유 코드만 사용되고 SIP 응답 코드는 무시됨을 나타냅니다.</p></td>
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

없음. **New-CsSipResponseCodeTranslationRule** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsSipResponseCodeTranslationRule** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.SipResponseCodeTRanslationRule\#Decorated 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsSipResponseCodeTranslationRule](get-cssipresponsecodetranslationrule.md)  
[Remove-CsSipResponseCodeTranslationRule](remove-cssipresponsecodetranslationrule.md)  
[Set-CsSipResponseCodeTranslationRule](set-cssipresponsecodetranslationrule.md)

