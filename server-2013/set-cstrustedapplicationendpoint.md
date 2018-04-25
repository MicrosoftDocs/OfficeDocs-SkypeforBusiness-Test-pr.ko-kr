---
title: Set-CsTrustedApplicationEndpoint
TOCTitle: Set-CsTrustedApplicationEndpoint
ms:assetid: 6c2713f4-8e2c-48fc-9f27-07c1d6b87a18
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398509(v=OCS.15)
ms:contentKeyID: 49303941
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsTrustedApplicationEndpoint

 

_**마지막으로 수정된 항목:** 2015-03-09_

신뢰할 수 있는 응용 프로그램의 기존 끝점 연락처를 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsTrustedApplicationEndpoint -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DisplayName <String>] [-DisplayNumber <String>] [-Enabled <$true | $false>] [-EnabledForFederation <$true | $false>] [-EnterpriseVoiceEnabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-LineURI <String>] [-PassThru <SwitchParameter>] [-PrimaryLanguage <String>] [-SecondaryLanguages <MultiValuedProperty>] [-SipAddress <String>] [-Type <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 SIP 주소가 endpoint1@litwareinc.com인 응용 프로그램 끝점 연락처 개체를 수정합니다. ID 값은 문자열 sip:으로 시작하고 그 뒤에 SIP 주소가 오는 형식으로 입력해야 합니다. 다음 매개 변수인 DisplayName에 값 "Endpoint 1"이 제공되어 연락처의 표시 이름이 해당 값으로 변경됩니다.

    Set-CsTrustedApplicationEndpoint -Identity "sip:endpoint1@litwareinc.com" -DisplayName "Endpoint 1"

## 예제 2

이 예제에서는 표시 이름이 Endpoint 1인 끝점 응용 프로그램의 표시 번호를 수정합니다. 먼저 Endpoint 1 ID를 사용하여 **Get-CsTrustedApplicationEndpoint** cmdlet을 호출합니다. 그러면 해당 표시 이름을 가진 끝점 연락처 개체가 검색됩니다. 이 개체는 DisplayNumber를 해당 값(이 경우 (425)555-1212)으로 수정하는 **Set-CsTrustedApplicationEndpoint** cmdlet에 파이프됩니다.

    Get-CsTrustedApplicationEndpoint -Identity "Endpoint 1" | Set-CsTrustedApplicationEndpoint -DisplayNumber "(425)555-1212"

## 자세한 정보

신뢰할 수 있는 응용 프로그램 끝점은 신뢰할 수 있는 응용 프로그램으로 통화를 경로 지정할 수 있는 Active Directory 대화 상대 개체입니다. 이 cmdlet은 Active Directory 도메인 서비스의 기존 끝점 연락처 개체를 수정합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsTrustedApplicationEndpoint** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsTrustedApplicationEndpoint"}

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
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>수정할 응용 프로그램 끝점의 ID(고유 이름) 또는 SIP 주소입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>끝점 연락처 개체의 표시 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisplayNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>주소록에 표시되는 연락처의 전화 번호입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>연락처를 Lync Server에 대해 활성화할지 여부를 결정합니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="even">
<td><p><em>EnabledForFederation</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>페더레이션 사용자에게 이 연락처에 대한 액세스 권한을 부여할지 여부를 결정합니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="odd">
<td><p><em>EnterpriseVoiceEnabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>연락처를 Enterprise Voice에 대해 활성화할지 여부를 결정합니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="even">
<td><p><em>ExchangeArchivingPolicy</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.ExchangeArchivingPolicyOptionsEnum</p></td>
<td><p>연락처의 메신저 대화 세션이 보관되는 위치를 나타냅니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Uninitialized</p>
<p>* UseLyncArchivingPolicy</p>
<p>* ArchivingToExchange</p>
<p>* NoArchiving</p></td>
</tr>
<tr class="odd">
<td><p><em>LineURI</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>연락처의 전화 번호입니다. TEL:&lt;번호&gt; 형식이어야 합니다(예: TEL:+14255551212).</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 포함하면 cmdlet이 연락처 개체를 수정하고 출력으로 새 개체를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PrimaryLanguage</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>신뢰할 수 있는 응용 프로그램에 사용되는 기본 언어입니다. 언어는 유효한 언어 코드(예: en-US(영어(미국)), fr-FR(프랑스어) 등)를 사용하여 구성해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SecondaryLanguages</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.MultiValuedProperty</p></td>
<td><p>신뢰할 수 있는 응용 프로그램에 사용할 수 있는 언어 컬렉션입니다. 쉼표로 구분된 언어 코드 값 목록으로 값을 구성해야 합니다. 예를 들어 구문 -SecondaryLanguages &quot;fr-CA&quot;,&quot;fr-FR&quot;은 프랑스어(캐나다) 및 프랑스어(프랑스)를 보조 언어로 설정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>연락처의 SIP 주소를 수정할 수 없습니다. 이 SIP 주소는 응용 프로그램 끝점이 생성될 때 할당됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Type</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수는 이 cmdlet에 사용되지 않습니다.</p></td>
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

Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact 개체입니다. 신뢰할 수 있는 응용 프로그램 끝점 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact 유형의 개체를 수정합니다.

## 참고 항목

#### 기타 리소스

[New-CsTrustedApplicationEndpoint](new-cstrustedapplicationendpoint.md)  
[Remove-CsTrustedApplicationEndpoint](remove-cstrustedapplicationendpoint.md)  
[Get-CsTrustedApplicationEndpoint](get-cstrustedapplicationendpoint.md)

