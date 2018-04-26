---
title: New-CsTrustedApplicationEndpoint
TOCTitle: New-CsTrustedApplicationEndpoint
ms:assetid: 78b34ba4-4c31-4f68-9069-3c7e7c162fbf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398594(v=OCS.15)
ms:contentKeyID: 49304109
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsTrustedApplicationEndpoint

 

_**마지막으로 수정된 항목:** 2015-03-09_

신뢰할 수 있는 응용 프로그램에 대한 새 끝점 연락처를 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsTrustedApplicationEndpoint -ApplicationId <String> -TrustedApplicationPoolFqdn <Fqdn> [-Confirm [<SwitchParameter>]] [-DisplayName <String>] [-DisplayNumber <String>] [-LineURI <String>] [-PassThru <SwitchParameter>] [-PrimaryLanguage <String>] [-SecondaryLanguages <MultiValuedProperty>] [-SipAddress <String>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 TrustPool.litwareinc.com 풀에 위치한 응용 프로그램 ID가 tapp1인 응용 프로그램에 대한 신뢰할 수 있는 응용 프로그램 끝점을 만듭니다. 신뢰할 수 있는 응용 프로그램 끝점을 만들기 위해 필요한 매개 변수는 ApplicationID와 TrustedApplicationPoolFqdn 두 가지가 전부입니다. 이 두 매개 변수에만 값을 할당하면 연락처에 대한 SIP 주소가 생성됩니다. SIP 주소가 고유하도록 하기 위해 자동 생성된 주소는 GUID(Globally Unique Identifier)를 포함하며 다음과 같은 형태를 가집니다. sip:RtcApplication-fbf9e2d1-c6aa-45a3-a045-b92d4ef961b2@litwareinc.com. 조금 더 가독성이 좋은 SIP 주소를 원할 경우 예제 2를 참조하십시오.

    New-CsTrustedApplicationEndpoint -ApplicationId tapp1 -TrustedApplicationPoolFqdn TrustPool.litwareinc.com

## 예제 2

예제 2는 TrustPool.litwareinc.com 풀에 있는 응용 프로그램 ID가 tapp1인 응용 프로그램에 대한 신뢰할 수 있는 응용 프로그램 끝점을 만든다는 측면에서 예제 1과 동일합니다. 그러나 예제 1과 달리 끝점을 만들 때 매개 변수를 하나 더 포함합니다. 바로 SipAddress입니다. 시스템에서 SIP 주소를 생성하도록 하지 않고 endpoint1@litwareinc.com이라는 주소를 지정했습니다.

    New-CsTrustedApplicationEndpoint -ApplicationId tapp1 -TrustedApplicationPoolFqdn TrustPool.litwareinc.com -SipAddress sip:endpoint1@litwareinc.com

## 자세한 정보

신뢰할 수 있는 응용 프로그램 끝점은 신뢰할 수 있는 응용 프로그램으로 통화를 경로 지정할 수 있는 Active Directory 대화 상대 개체입니다. 이 cmdlet은 지정된 응용 프로그램에 대해 Active Directory 도메인 서비스에 새 끝점 연락처 개체를 만듭니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsTrustedApplicationEndpoint** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsTrustedApplicationEndpoint"}

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
<td><p><em>ApplicationId</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>끝점 연락처를 만드는 신뢰할 수 있는 응용 프로그램의 응용 프로그램 ID입니다. 이 ID를 가진 응용 프로그램이 이미 존재해야 합니다. 응용 프로그램 ID의 이름 부분만 포함할 수 있습니다. 즉, 접두사 정보는 포함하지 않아도 됩니다(포함할 수도 있음). 예를 들어 응용 프로그램 ID가 urn:application:TrustedApp1인 경우 TrustedApp1 문자열만 이 매개 변수에 전달하면 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TrustedApplicationPoolFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>응용 프로그램과 연결된 신뢰할 수 있는 응용 프로그램 풀의 FQDN(정규화된 도메인 이름)입니다. 끝점이 만들어지려면 응용 프로그램이 이미 이 풀과 연결되어 있어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisplayName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>끝점 연락처 개체의 표시 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>주소록에 표시되는 연락처의 전화 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LineURI</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>연락처의 전화 번호입니다. TEL:&lt;번호&gt; 형식이어야 합니다(예: TEL:+14255551212).</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 명령의 결과를 반환합니다. 이 cmdlet을 실행하면 새로 만든 개체가 표시됩니다. 단순히 이 매개 변수를 포함하면 해당 출력이 반복되므로 매개 변수를 중복하여 사용하는 것이 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PrimaryLanguage</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>신뢰할 수 있는 응용 프로그램에 사용되는 기본 언어입니다. 언어는 유효한 언어 코드(예: en-US(영어(미국)), fr-FR(프랑스어) 등)를 사용하여 구성해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SecondaryLanguages</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.MultiValuedProperty</p></td>
<td><p>신뢰할 수 있는 응용 프로그램에 사용할 수 있는 언어 컬렉션입니다. 쉼표로 구분된 언어 코드 값 목록으로 값을 구성해야 합니다. 예를 들어 구문 -SecondaryLanguages &quot;fr-CA&quot;,&quot;fr-FR&quot;은 프랑스어(캐나다) 및 프랑스어(프랑스)를 보조 언어로 설정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>새 연락처 개체에 대한 SIP 주소입니다. 이 매개 변수에 대한 값을 포함하지 않으면 SIP 주소는 sip:RtcApplication-&lt;GUID&gt;.&lt;도메인&gt; 형식으로 자동으로 생성됩니다(예: sip:RtcApplication-fbf9e2d1-c6aa-45a3-a045-b92d4ef961b2@litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>새 신뢰할 수 있는 응용 프로그램 풀 끝점을 만드는 대상 Office 365 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
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

없음.

## 반환 형식

Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsTrustedApplicationEndpoint](remove-cstrustedapplicationendpoint.md)  
[Set-CsTrustedApplicationEndpoint](set-cstrustedapplicationendpoint.md)  
[Get-CsTrustedApplicationEndpoint](get-cstrustedapplicationendpoint.md)

