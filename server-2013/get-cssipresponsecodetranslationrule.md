---
title: Get-CsSipResponseCodeTranslationRule
TOCTitle: Get-CsSipResponseCodeTranslationRule
ms:assetid: 075e9e85-8f85-402c-9256-4e73ec93f96b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398130(v=OCS.15)
ms:contentKeyID: 49302705
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsSipResponseCodeTranslationRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

SIP 응답 코드 변환 규칙에 대한 정보를 반환합니다. 이러한 규칙을 통해 관리자는 값이 400에서 699 사이인 SIP 응답 코드를 Lync Server에서 사용하는 값에 매핑할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsSipResponseCodeTranslationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsSipResponseCodeTranslationRule [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 응답 코드 변환 규칙 컬렉션을 반환합니다. 이 작업을 수행하기 위해 **Get-CsSipResponseCodeTranslationRule** cmdlet을 매개 변수 없이 호출합니다.

    Get-CsSipResponseCodeTranslationRule

## 예제 2

예제 2에서는 ID가 PstnGateway:192.168.0.240/Rule404인 단일 응답 코드 변환 규칙을 반환합니다.

    Get-CsSipResponseCodeTranslationRule -Identity "PstnGateway:192.168.0.240/Rule404"

## 예제 3

예제 3에서는 사이트 범위에서 구성된 모든 응답 코드 변환 규칙에 대한 데이터만 반환되도록 제한하기 위해 Filter 매개 변수가 사용됩니다. 필터 값 "site:\*"는 ID가 문자열 값 "site:"으로 시작하는 규칙에 대한 데이터만 반환되도록 제한합니다.

    Get-CsSipResponseCodeTranslationRule -Filter "site:*"

## 예제 4

예제 4에 표시된 명령은 ReceivedISUPCauseValue 속성 값이 구성되어 있지 않은 모든 응답 코드 변환 규칙 컬렉션을 반환합니다. 이를 위해 먼저 매개 변수 없이 **Get-CsSipResponseCodeTranslationRule** cmdlet을 호출하여 현재 사용 중인 모든 응답 코드 변환 규칙의 컬렉션을 반환합니다. 이 컬렉션은 ReceivedISUPCauseValue 속성이 -1과 같은 규칙만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsSipResponseCodeTranslationRule | Where-Object {$_.ReceivedISUPCauseValue -eq -1}

## 자세한 정보

SIP 트렁크를 사용하면 PSTN(공중 전화망)을 통해 VoIP(Voice over Internet Protocol) 네트워크(예: Enterprise Voice)를 연결할 수 있습니다. Lync Server에서 중재 서버는 트렁크 피어를 사용하여 PSTN 네트워크와 상호 작용합니다. PSTN 네트워크에서 발신 전화에 실패하면 ISUP(ISDN User Part) 이유 코드가 자동으로 생성됩니다. 예를 들어 PSTN 게이트웨이에서 전화를 완료하는 데 사용 가능한 회로 또는 채널이 없음을 나타내는 이유 코드 34를 전송할 수 있습니다. 중재 서버 트렁크 피어는 ISUP 이유 코드를 받아 SIP 응답 코드로 변환한 후 중재 서버 자신에게 다시 전송합니다. 그러면 Lync Server에서 이러한 응답 코드를 사용하여 아웃바운드 경로 지정을 결정합니다. 예를 들어 제대로 작동하지 않는 게이트웨이에 "less-preferred" 상태가 자동으로 할당될 수 있습니다. 이를 통해 이 게이트웨이 사용 수를 최소화하고 통화가 성공적으로 완료될 가능성을 최대화할 수 있습니다.

그러나 일부 게이트웨이는 권장 ISUP 이유 코드와 Lync Server에서 사용하는 SIP 응답 코드 간의 매핑을 사용하지 않습니다. 이러한 게이트웨이의 경우 관리자는 **CsSipResponseCodeTranslationRule** cmdlet을 사용하여 게이트웨이 SIP 응답 코드(ISUP 이유 코드를 사용할 수 있는 경우 이 코드와 조합)를 Lync Server에서 사용하는 SIP 응답 코드에 매핑할 수 있습니다. 예를 들어 게이트웨이에서 ISUP 이유 코드 34("사용 가능한 회로/채널 없음")를 SIP 응답 코드 486 ("여기에서 사용 중")에 매핑할 수 있습니다. 이렇게 하면 응답 코드 486에 따라 Lync Server의 아웃바운드 경로 지정 논리가 통화를 완료하기 위해 새 게이트웨이를 찾으려고 시도하지 않습니다.

그러나 Lync Server의 경우에는 대신에 이러한 SIP 응답 코드 486이 SIP 응답 코드 503에 매핑되어야 합니다. 응답 코드 503은 Lync Server의 아웃바운드 경로 지정 논리에서 재시도 메커니즘을 트리거합니다. 즉, 시스템에서 통화를 완료하기 위해 다른 게이트웨이를 찾습니다. 이 상황을 처리하기 위해 ISUP 이유 코드 34와 SIP 응답 코드 486의 조합을 SIP 응답 코드 503에 매핑하는 변환 규칙을 만들 수 있습니다.

**Get-CsSipResponseCodeTranslationRule** cmdlet을 사용하면 조직에서 사용하도록 구성된 모든 변환 규칙에 대한 정보를 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsSipResponseCodeTranslationRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsSipResponseCodeTranslationRule"}

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>반환할 변환 규칙을 지정할 때 와일드카드를 사용할 수 있습니다. 예를 들어 다음 구문은 Identity에 문자열 값 &quot;404&quot;가 포함된 모든 변환 규칙을 반환합니다.</p>
<p>-Filter &quot;*404*&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>변환 규칙의 고유 식별자입니다. 변환 규칙 ID는 규칙이 구성된 범위와 규칙을 만들 때 제공된 이름으로 구성됩니다. 예를 들어 전역 범위에서 만들어진 Rule404라는 변환 규칙의 ID는 global/Rule404와 유사할 수 있습니다.</p>
<p>전역 범위 외에 사이트 범위 또는 서비스 범위(PstnGateway 서비스에만 해당)에서 변환 규칙을 만들 수도 있습니다.</p>
<p>특정 사이트 또는 서비스에 대해 만들어진 모든 변환 규칙을 반환하려면 사이트 또는 서비스 ID를 지정하면 됩니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>이 매개 변수를 생략하면 <strong>Get-CsSipResponseCodeTranslationRule</strong> cmdlet은 모든 SIP 응답 코드 변환 규칙 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 SIP 응답 코드 변환 규칙 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsSipResponseCodeTranslationRule** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsSipResponseCodeTranslationRule** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.SipResponseCodeTRanslationRule\#Decorated 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsSipResponseCodeTranslationRule](new-cssipresponsecodetranslationrule.md)  
[Remove-CsSipResponseCodeTranslationRule](remove-cssipresponsecodetranslationrule.md)  
[Set-CsSipResponseCodeTranslationRule](set-cssipresponsecodetranslationrule.md)

