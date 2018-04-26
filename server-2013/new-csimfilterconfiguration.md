---
title: New-CsImFilterConfiguration
TOCTitle: New-CsImFilterConfiguration
ms:assetid: 1964cbf9-d7f1-4b4e-99d1-951ac42d82fe
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398244(v=OCS.15)
ms:contentKeyID: 49302950
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsImFilterConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 메신저 필터 구성을 만듭니다. 메신저 필터는 사용자가 활성 하이퍼링크를 포함하는 메신저 대화를 보낼 수 없도록 하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsImFilterConfiguration -Identity <XdsIdentity> [-Action <Allow | Block | Warn>] [-AllowMessage <String>] [-BlockFileExtension <$true | $false>] [-Confirm [<SwitchParameter>]] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-IgnoreLocal <$true | $false>] [-InMemory <SwitchParameter>] [-Prefixes <PSListModifier>] [-WarnMessage <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **New-CsImFilterConfiguration** cmdlet을 사용하여 ID가 site:Redmond인 새 메신저 필터 구성을 만듭니다. 추가 매개 변수가 지정되지 않았기 때문에 이러한 설정은 기본값을 사용하여 생성됩니다.

    New-CsImFilterConfiguration -Identity site:Redmond

## 예제 2

이 명령에서 **New-CsImFilterConfiguration** cmdlet은 ID가 site:Redmond인 새 메신저 필터 구성을 만드는 데 사용됩니다. Prefixes 매개 변수가 지정되었기 때문에 새 구성에는 필터링할 기본 접두사를 비롯한 모든 기본값과 rtsp: 및 urn:의 두 가지 추가 접두사가 포함됩니다. 이러한 접두사는 기본 목록에 이러한 접두사를 추가하는 add 목록 한정자를 사용하여 추가합니다.

    New-CsImFilterConfiguration -Identity site:Redmond -Prefixes @{add="rtsp:","urn:"}

## 예제 3

이 명령에서 **New-CsFileTransferFilterConfiguration** cmdlet은 ID가 site:Redmond인 새 메신저 필터 구성을 만드는 데 사용됩니다. 이 예제는 예제 2와 유사하지만 add 목록 한정자 대신 replace 목록 한정자를 사용하는 점이 다릅니다. 이는 모든 기본 URI 접두사가 이러한 두 접두사(rtsp: 및 urn:)로 바뀐다는 의미입니다. 따라서 앞에 rtsp: 또는 urn:이 오는 URI만 Redmond 사이트의 메신저 대화 내에서 필터링됩니다.

    New-CsImFilterConfiguration -Identity site:Redmond -Prefixes @{replace="rtsp:","urn:"}

## 자세한 정보

메신저 대화를 보낼 때 사용자가 해당 메시지의 텍스트에 URI(Uniform Resource Identifier)를 포함하여 대화의 다른 참가자가 특정 웹 사이트 또는 공유를 참조하도록 할 수 있습니다. 또한 특정 접두사가 포함된 하이퍼링크가 차단되거나 비활성화되도록 Lync Server를 구성할 수 있습니다. 즉, 참가자가 단순히 링크를 클릭하여 URI가 참조하는 사이트로 이동할 수 없고 수동으로 링크를 복사하여 브라우저에 붙여 넣어야 합니다.

**New-CsImFilterConfiguration** cmdlet을 사용하면 필터링할 URI 접두사 목록을 정의할 수 있을 뿐 아니라 특정 사이트 내에서 필터링을 사용하거나 사용하지 않도록 설정할 수 있습니다. Identity만 지정하여 **New-CsImFilterConfiguration** cmdlet을 호출하면 해당 ID로 새 구성이 만들어지고 해당 사이트의 Prefixes 목록이 필터링할 기본 접두사 집합으로 채워집니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsImFilterConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsImFilterConfiguration"}

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
<td><p>Xds ID</p></td>
<td><p>메신저 필터 구성 범위를 지정하는 고유한 식별자입니다. 전역 설정은 기본적으로 존재하므로 <strong>New-CsImFilterConfiguration</strong> cmdlet을 사용하여 다시 만들 수 없지만 site:&lt;사이트 이름&gt;의 Identity를 지정하여 사이트 수준 설정을 만들 수 있습니다. 여기서 &lt;사이트 이름&gt;은 설정을 적용할 사이트의 이름입니다(예: site:Redmond).</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
</tr>
<tr class="even">
<td><p><em>Action</em></p></td>
<td><p>선택</p></td>
<td><p>URL 필터 작업</p></td>
<td><p>이 매개 변수 값은 메신저 대화에 하이퍼링크가 포함된 경우에 수행할 작업을 결정합니다.</p>
<p>Allow - 하이퍼링크 앞에 밑줄이 붙어 링크 기능이 없어집니다. AllowMessage 속성에 메시지가 지정된 경우 하이퍼링크가 포함된 각 메신저 대화의 시작 부분에 메시지가 삽입됩니다.</p>
<p>Block - 활성 하이퍼링크가 포함된 메시지의 배달이 차단되고 Lync Server에서 보낸 사람에게 오류 메시지를 보냅니다.</p>
<p>Warn - 수신 참가자에게 활성 하이퍼링크를 포함하는 메시지와 이러한 메시지의 시작 부분에 삽입되는 경고 메시지가 배달됩니다. 경고 메시지는 WarnMessage 속성을 사용하여 지정할 수 있습니다. Warn을 지정하고 WarnMessage를 입력하지 않으면 메신저 필터링이 해제되지만 BlockFileExtension 속성에 대한 설정은 계속 유효합니다.</p>
<p>기본값: Allow. 메시지에 1,000개가 넘는 URL이 포함되는 경우 기본값은 Block입니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.UrlFilterAction</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowMessage</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>이 매개 변수에 값을 지정하면 Action 속성 값이 Allow로 설정된 경우 하이퍼링크를 포함하는 각 메시지의 시작 부분에 해당 문자열이 삽입됩니다. 이 메시지를 사용하여 알 수 없는 링크를 클릭할 경우의 잠재적 위험 또는 조직의 관련 정책 및 요구 사항 등을 사용자에게 알릴 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>BlockFileExtension</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 매개 변수를 True로 설정하면 <strong>Get-CsFileTransferFilterConfiguration</strong> cmdlet을 호출하여 검색할 수 있는 해당 파일 전송 필터 구성에 정의된 Extensions 속성에서 지정하는 확장명을 가진 파일 경로가 포함된 하이퍼링크가 차단되고 보낸 사람에게 오류 메시지가 반환됩니다. 이 매개 변수를 False로 설정하면 파일 확장명에 대한 특별 검사가 수행되지 않습니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 기능을 사용하거나 사용하지 않도록 설정합니다. 이 매개 변수를 True로 설정하면 메신저 대화의 하이퍼링크를 검사하고 이 구성의 규칙을 적용합니다. 이 매개 변수를 False로 설정하면 메시지의 하이퍼링크를 검사하지 않습니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>변경 작업을 수행하기 전에 표시되는 모든 확인 프롬프트를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>IgnoreLocal</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 매개 변수 값은 메신저 대화에 전달된 로컬 인트라넷 URI에 대해 필터링을 수행할지 여부를 제어합니다. 이 매개 변수를 True로 설정하면 로컬 컴퓨터의 인트라넷 영역에 정의된 모든 URI가 무시됩니다. 로컬 컴퓨터는 메신저 필터 응용 프로그램을 실행하는 프런트 엔드 서버입니다. 이 매개 변수를 False로 설정하면 지정된 필터링이 모든 하이퍼링크에 적용됩니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Prefixes</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>필터링할 URI 접두사 목록입니다. 메신저 대화에 이 목록의 접두사 중 하나와 일치하는 접두사가 있는 하이퍼링크가 포함된 경우 지정된 설정에 따라 필터링됩니다.</p>
<p>기본값: callto:, file:, ftp., ftp:, gopher:, href, http:, https:, ldap:, mailto:, news:, nntp:, sip:, sips:, tel:, telnet:, www*.</p></td>
</tr>
<tr class="odd">
<td><p><em>WarnMessage</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>이 매개 변수는 Action 속성 값이 Warn으로 설정된 경우 하이퍼링크가 포함된 각 메신저 대화의 시작 부분에 삽입되는 경고 메시지를 포함합니다. 일반적으로 이 메시지는 알 수 없는 링크를 클릭할 경우의 잠재적 위험을 알리거나 조직의 관련 정책 및 요구 사항을 참조하는 등에 사용됩니다.</p></td>
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

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsImFilterConfiguration](remove-csimfilterconfiguration.md)  
[Set-CsImFilterConfiguration](set-csimfilterconfiguration.md)  
[Get-CsImFilterConfiguration](get-csimfilterconfiguration.md)

