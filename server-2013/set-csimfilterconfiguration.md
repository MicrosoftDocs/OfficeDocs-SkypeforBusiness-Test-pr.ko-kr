---
title: Set-CsImFilterConfiguration
TOCTitle: Set-CsImFilterConfiguration
ms:assetid: c2b08cc0-8261-4b8b-b2e9-5efa902ceb40
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412960(v=OCS.15)
ms:contentKeyID: 49304939
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsImFilterConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 메신저 필터 구성을 수정합니다. 메신저 필터 설정은 사용자가 클릭 가능한 활성 하이퍼링크가 포함된 메시지를 보내지 못하도록 하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsImFilterConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsImFilterConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Action <Allow | Block | Warn>] [-AllowMessage <String>] [-BlockFileExtension <$true | $false>] [-Confirm [<SwitchParameter>]] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-IgnoreLocal <$true | $false>] [-Prefixes <PSListModifier>] [-WarnMessage <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에 표시된 명령은 ID가 site:Redmond인 메신저 필터 구성에 대해 URI 필터링을 사용하지 않도록 설정합니다. 이 작업을 수행하기 위해 Enabled 매개 변수 값을 $False로 설정하여 **Set-CsImFilterConfiguration** cmdlet을 호출합니다.

    Set-CsImFilterConfiguration -Identity site:Redmond -Enabled $False

## 예제 2

예제 2에서는 site:Redmond에 대한 메신저 필터 구성에서 차단하는 접두사 목록에 새 URI 접두사(urn:)를 추가합니다. 새 접두사를 추가하기 위해 **Get-CsImFilterConfiguration** cmdlet을 사용하여 site:Redmond에 대한 구성을 검색합니다. 해당 구성을 나타내는 반환된 개체는 $x라는 변수에 저장됩니다. 설정을 검색한 후에는 둘째 줄에서 Add() 메서드를 호출하여 Prefixes 속성에 저장된 접두사 집합에 urn:을 추가합니다. 이렇게 하면 개체 참조 $x의 값이 변경됩니다. 실제 구성 자체를 변경하기 위해 셋째 줄에서는 **Set-CsImFilterConfiguration** cmdlet을 호출하여 $x를 단일 매개 변수 값으로 전달합니다.

    $x = Get-CsImFilterConfiguration -Identity site:Redmond
    $x.Prefixes.Add("urn:")
    Set-CsImFilterConfiguration -Instance $x

## 예제 3

예제 3에서는 예제 2와 동일한 작업을 한 줄에서 실행합니다. 이 명령에서 **Set-CsImFilterConfiguration** cmdlet의 -Prefixes 매개 변수는 접두사 목록에 urn:을 추가하는 데 사용되고, add 목록 한정자는 이 값을 Prefixes 목록에 추가하는 데 사용됩니다.

    Set-CsImFilterConfiguration -Identity site:Redmond -Prefixes @{add="urn:"}

## 예제 4

이 예제에서는 site:Redmond에 대한 메신저 필터 구성에서 차단하는 접두사 목록에서 접두사 urn:을 제거합니다. 이 예제는 예제 3과 동일하지만 add 목록 한정자를 호출하여 목록에 접두사를 추가하는 것이 아니라 remove 한정자를 호출하여 접두사를 제거하는 점이 다릅니다.

    Set-CsImFilterConfiguration -Identity site:Redmond -Prefixes @{remove="urn:"}

## 자세한 정보

메시지를 보낼 때 사용자가 해당 메시지의 텍스트에 URI(Uniform Resource Identifier)를 포함하여 대화의 다른 참가자가 특정 웹 사이트 또는 공유를 참조하도록 할 수 있습니다. 특정 접두사가 포함된 하이퍼링크가 차단되거나 비활성화되도록 Lync Server를 구성할 수 있습니다. 즉, 참가자가 단순히 링크를 클릭하여 URI가 참조하는 사이트로 이동할 수 없고 수동으로 링크를 복사하여 브라우저에 붙여 넣어야 합니다.

**Set-CsImFilterConfiguration** cmdlet을 사용하면 필터링할 URI 접두사 목록을 수정할 수 있을 뿐 아니라 전역적으로 또는 특정 사이트 내에서 필터링을 사용하거나 사용하지 않도록 설정할 수 있습니다. 이 cmdlet을 사용하여 사용자에게 경고 메시지를 제공하는 다양한 메시지를 업데이트할 수도 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsImFilterConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsImFilterConfiguration"}

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
<td><p><em>Action</em></p></td>
<td><p>선택</p></td>
<td><p>URL 필터 작업</p></td>
<td><p>이 매개 변수 값은 메신저 대화에 하이퍼링크가 포함된 경우에 수행할 작업을 결정합니다.</p>
<p>Allow - 하이퍼링크 앞에 밑줄이 삽입되어 링크가 더 이상 활성화되지 않습니다. 또한 AllowMessage 속성에 메시지가 지정된 경우 하이퍼링크가 포함된 각 메신저 대화의 시작 부분에 알림 메시지가 삽입됩니다.</p>
<p>Block - 활성 하이퍼링크가 포함된 메시지의 배달이 차단되고 Lync Server에서 보낸 사람에게 오류 메시지를 보냅니다.</p>
<p>Warn - 수신 참가자에게 활성 하이퍼링크를 포함하는 메시지와 이러한 메시지의 시작 부분에 삽입되는 경고 메시지가 배달됩니다. 경고 메시지는 WarnMessage 속성을 사용하여 지정할 수 있습니다. Warn을 지정하고 WarnMessage를 입력하지 않으면 메신저 필터링이 해제되지만 BlockFileExtension 속성에 대한 설정은 계속 유효합니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>AllowMessage</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>이 매개 변수 값을 지정한 경우 Action 속성 값을 Allow로 설정하면 하이퍼링크가 포함된 각 메시지의 시작 부분에 해당 문자열이 삽입됩니다. 이 메시지를 사용하여 알 수 없는 링크를 클릭할 경우의 잠재적 위험 또는 조직의 관련 정책 및 요구 사항 등을 사용자에게 알릴 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>BlockFileExtension</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 매개 변수를 True로 설정하면 <strong>Get-CsFileTransferFilterConfiguration</strong> cmdlet을 호출하여 검색할 수 있는 Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.FileTransferFilterConfiguration 클래스에 정의된 Extensions 속성에서 지정하는 확장명을 가진 파일 경로가 포함된 하이퍼링크가 차단되고 보낸 사람에게 오류 메시지가 반환됩니다. 이 매개 변수를 False로 설정하면 파일 경로 및 확장명을 특별히 확인하지 않습니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 기능을 사용하거나 사용하지 않도록 설정합니다. 이 매개 변수를 True로 설정하면 메신저 대화의 하이퍼링크를 검사하고 이 구성의 규칙을 적용합니다. 이 매개 변수를 False로 설정하면 메시지의 하이퍼링크를 검사하지 않습니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Xds ID</p></td>
<td><p>수정할 메신저 필터 구성 설정의 고유 식별자입니다. 이 값은 global 또는 site:&lt;사이트 이름&gt;입니다. 여기서 &lt;사이트 이름&gt;은 구성을 적용할 사이트(예: site:Redmond)입니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>IgnoreLocal</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 매개 변수 값은 메신저 대화에 전달된 로컬 인트라넷 URI에 대해 필터링을 수행할지 여부를 제어합니다. 이 매개 변수를 True로 설정하면 로컬 컴퓨터의 인트라넷 영역에 정의된 모든 URI가 무시됩니다. 로컬 컴퓨터는 메신저 필터 응용 프로그램을 실행하는 프런트 엔드 서버입니다. 이 매개 변수를 False로 설정하면 지정된 필터링이 모든 하이퍼링크에 적용됩니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>메신저 필터 구성</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다. 이 cmdlet은 <strong>Get-CsImFilterConfiguration</strong> cmdlet을 호출하여 검색할 수 있는 Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration 유형의 개체를 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Prefixes</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>필터링할 URI 접두사 목록입니다. 메신저 대화에 이 목록의 접두사 중 하나와 일치하는 접두사가 있는 하이퍼링크가 포함된 경우 지정된 설정에 따라 필터링됩니다.</p>
<p>기본값: callto:, file:, ftp., ftp:, gopher:, href, http:, https:, ldap:, mailto:, news:, nntp:, sip:, sips:, tel:, telnet:, www*</p></td>
</tr>
<tr class="odd">
<td><p><em>WarnMessage</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>이 매개 변수는 Action 속성 값이 Warn으로 설정된 경우 하이퍼링크가 포함된 각 메신저 대화의 시작 부분에 삽입할 경고 메시지를 포함합니다. 일반적으로 이 메시지는 알 수 없는 링크를 클릭할 경우의 잠재적 위험을 알리거나 조직의 관련 정책 및 요구 사항을 참조하는 등에 사용됩니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration 개체입니다. 메신저 필터 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsImFilterConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[New-CsImFilterConfiguration](new-csimfilterconfiguration.md)  
[Remove-CsImFilterConfiguration](remove-csimfilterconfiguration.md)  
[Get-CsImFilterConfiguration](get-csimfilterconfiguration.md)

