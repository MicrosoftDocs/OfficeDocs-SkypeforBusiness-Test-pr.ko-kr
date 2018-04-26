---
title: Remove-CsSipResponseCodeTranslationRule
TOCTitle: Remove-CsSipResponseCodeTranslationRule
ms:assetid: beb5f508-5f90-46ee-b5c5-7da8781420e0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412932(v=OCS.15)
ms:contentKeyID: 49304886
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsSipResponseCodeTranslationRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

SIP 응답 코드 변환 규칙을 제거합니다. 이러한 규칙을 통해 관리자는 값이 400에서 699 사이인 SIP 응답 코드를 Lync Server에서 사용하는 값에 매핑할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsSipResponseCodeTranslationRule -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 PstnGateway:192.168.0.240/Rule404인 단일 응답 코드 변환 규칙을 삭제합니다.

    Remove-CsSipResponseCodeTranslationRule -Identity "PstnGateway:192.168.0.240/Rule404"

## 예제 2

예제 2에서는 PSTN 게이트웨이 192.168.0.240에서 모든 응답 코드 변환 규칙을 제거합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsSipResponseCodeTranslationRule** cmdlet을 Filter 매개 변수와 함께 호출합니다. 필터 값 "service:PstnGateway:192.168.0.240/\*"는 반환되는 데이터를 문자열 값 "service:PstnGateway:192.168.0.240/"로 시작하는 ID를 가진 규칙으로 제한합니다. 필터링된 컬렉션은 컬렉션의 각 규칙을 삭제하는 **Remove-CsSipResponseTranslationCode** cmdlet에 파이프됩니다.

    Get-CsSipResponseCodeTranslationRule -Filter "service:PstnGateway:192.168.0.240/*" | Remove-CsSipResponseTranslationCode

## 예제 3

예제 3에서는 ReceivedISUPCauseValue 속성에 대해 구성된 값이 없는 모든 응답 코드 변환 규칙을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsSipResponseCodeTranslationRule** cmdlet을 매개 변수 없이 호출하여 현재 사용 중인 모든 응답 코드 변환 규칙의 컬렉션을 반환합니다. 이 컬렉션은 ReceivedISUPCauseValue 속성이 -1과 같은 규칙만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

여기에서 필터링된 컬렉션은 컬렉션의 각 규칙을 삭제하는 **Remove-CsSipResponseTranslationCode** cmdlet에 파이프됩니다.

    Get-CsSipResponseCodeTranslationRule | Where-Object {$_.ReceivedISUPCauseValue -eq -1} | Remove-CsSipResponseTranslationCode

## 자세한 정보

SIP 트렁크를 사용하면 PSTN(공중 전화망)을 통해 VoIP(Voice over Internet Protocol) 네트워크(예: Enterprise Voice)를 연결할 수 있습니다. Lync Server에서 중재 서버는 트렁크 피어를 사용하여 PSTN 네트워크와 상호 작용합니다. PSTN 네트워크에서 발신 전화에 실패하면 ISUP(ISDN User Part) 이유 코드가 자동으로 생성됩니다. 예를 들어 PSTN 게이트웨이에서 전화를 완료하는 데 사용 가능한 회로 또는 채널이 없음을 나타내는 이유 코드 34를 전송할 수 있습니다. 중재 서버 트렁크 피어는 ISUP 이유 코드를 받아 SIP 응답 코드로 변환한 후 중재 서버 자신에게 다시 전송합니다. 그러면 Lync Server에서 이러한 응답 코드를 사용하여 아웃바운드 경로 지정을 결정합니다. 예를 들어 제대로 작동하지 않는 게이트웨이에 "less-preferred" 상태가 자동으로 할당될 수 있습니다. 이를 통해 이 게이트웨이 사용 수를 최소화하고 통화가 성공적으로 완료될 가능성을 최대화할 수 있습니다.

그러나 일부 게이트웨이는 권장 ISUP 이유 코드와 Lync Server에서 사용하는 SIP 응답 코드 간의 매핑을 사용하지 않습니다. 이러한 게이트웨이의 경우 관리자는 **CsSipResponseCodeTranslationRule** cmdlet을 사용하여 게이트웨이 SIP 응답 코드(ISUP 이유 코드를 사용할 수 있는 경우 이 코드와 조합)를 Lync Server에서 사용하는 SIP 응답 코드에 매핑할 수 있습니다. 예를 들어 게이트웨이에서 ISUP 이유 코드 34("사용 가능한 회로/채널 없음")를 SIP 응답 코드 486 ("여기에서 사용 중")에 매핑할 수 있습니다. 이렇게 하면 응답 코드 486에 따라 Lync Server의 아웃바운드 경로 지정 논리가 통화를 완료하기 위해 새 게이트웨이를 찾으려고 시도하지 않습니다.

그러나 Lync Server의 경우에는 대신에 이러한 SIP 응답 코드 486이 SIP 응답 코드 503에 매핑되어야 합니다. 응답 코드 503은 Lync Server의 아웃바운드 경로 지정 논리에서 재시도 메커니즘을 트리거합니다. 즉, 시스템에서 통화를 완료하기 위해 다른 게이트웨이를 찾습니다. 이 상황을 처리하기 위해 ISUP 이유 코드 34와 SIP 응답 코드 486의 조합을 SIP 응답 코드 503에 매핑하는 변환 규칙을 만들 수 있습니다.

**Remove-CsSipResponseCodeTranslationRule** cmdlet을 사용하면 조직에서 이전에 사용하도록 구성된 모든 변환 규칙을 삭제할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsSipResponseCodeTranslationRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsSipResponseCodeTranslationRule"}

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
<td><p>제거할 변환 규칙의 고유 식별자입니다. 변환 규칙 ID는 규칙이 구성된 범위와 규칙을 만들 때 제공된 이름으로 구성됩니다. 예를 들어 전역 범위에서 만들어진 Rule404라는 변환 규칙의 ID는 global/Rule404와 유사할 수 있습니다.</p></td>
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
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.SipResponseCodeTranslationRule\#Decorated 개체입니다. **Remove-CsSipResponseCodeTranslationRule** cmdlet은 SIP 응답 코드 변환 규칙 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Remove-CsSipResponseCodeTranslationRule** cmdlet은 개체나 값을 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.SipResponseCodeTranslationRule\#Decorated 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsSipResponseCodeTranslationRule](get-cssipresponsecodetranslationrule.md)  
[New-CsSipResponseCodeTranslationRule](new-cssipresponsecodetranslationrule.md)  
[Set-CsSipResponseCodeTranslationRule](set-cssipresponsecodetranslationrule.md)

