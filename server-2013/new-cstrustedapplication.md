---
title: New-CsTrustedApplication
TOCTitle: New-CsTrustedApplication
ms:assetid: 1c804a97-f9b5-4c3e-adc6-a120b26c1f51
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398259(v=OCS.15)
ms:contentKeyID: 49302983
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsTrustedApplication

 

_**마지막으로 수정된 항목:** 2015-03-09_

신뢰할 수 있는 응용 프로그램을 풀에 추가합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsTrustedApplication -ApplicationId <String> -TrustedApplicationPoolFqdn <String> <COMMON PARAMETERS>

    New-CsTrustedApplication [-Identity <ExternalApplicationIdentity>] <COMMON PARAMETERS>

    COMMON PARAMETERS: -Port <Int32> [-Confirm [<SwitchParameter>]] [-EnableTcp <SwitchParameter>] [-Force <SwitchParameter>] [-LegacyApplicationName <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 응용 프로그램 ID가 tapp1인 신뢰할 수 있는 응용 프로그램을 만듭니다. TrustedApplicationPoolFqdn 매개 변수를 사용하여 이 응용 프로그램이 상주할 신뢰할 수 있는 응용 프로그램 풀(이 경우 FQDN이 TrustPool.litwareinc.com인 풀)을 지정합니다. 또한 응용 프로그램에 대한 포트를 지정해야 합니다. 이 예제에서는 포트 6000을 사용했습니다. ApplicationId와 TrustedApplicationPoolFqdn을 지정하여 이 cmdlet을 실행하면 나중에 이 응용 프로그램을 검색, 수정 또는 제거하는 데 사용할 수 있는 Identity가 자동으로 생성됩니다.

    New-CsTrustedApplication -ApplicationId tapp1 -TrustedApplicationPoolFqdn TrustPool.litwareinc.com -Port 6000

## 예제 2

이 예제에서는 Port 6100에 Identity가 TrustPool.litwareinc.com/tapp2인 신뢰할 수 있는 응용 프로그램을 만듭니다. Identity의 형식을 확인합니다. 이 값은 \<신뢰할 수 있는 풀 FQDN\>/\<응용 프로그램 ID\> 형식이어야 합니다.

    New-CsTrustedApplication -Identity TrustPool.litwareinc.com/tapp2 -Port 6100

## 자세한 정보

신뢰할 수 있는 응용 프로그램은 Lync Server의 일부로 포함되어 기본 제공되지는 않지만 이 제품의 일부로 실행하도록 신뢰할 수 있는 상태가 지정된 타사에서 개발한 응용 프로그램입니다. 이 cmdlet은 신뢰할 수 있는 응용 프로그램 풀에 신뢰할 수 있는 응용 프로그램을 추가하고 해당 응용 프로그램을 실행하는 외부 서비스에 포트를 할당합니다.

신뢰할 수 있는 응용 프로그램을 GRUU(Globally Routable User Agent URI), 즉 서비스 GRUU와 컴퓨터 GRUU에 모두 연결해야 합니다. 이 cmdlet은 이 응용 프로그램이 이동된 풀에 연결된 컴퓨터 및 서비스를 기준으로 이러한 값을 자동으로 생성합니다.

이 cmdlet을 사용하여 신뢰할 수 있는 응용 프로그램을 만드는 경우 Identity 매개 변수나 ApplicationID 및 TrustedApplicationPoolFqdn 매개 변수에 값을 제공해야 합니다. Identity는 TrustedApplicationPoolFqdn 뒤에 슬래시(/)와 ApplicationID를 포함하여 구성됩니다. 예를 들어 TrustPool.litwareinc.com/tapp2에서 TrustPool.litwareinc.com은 TrustedApplicationPoolFqdn이고 tapp2는 ApplicationID입니다.

Identity 매개 변수의 일부로 또는 ApplicationID 매개 변수에 응용 프로그램 ID를 입력하는 경우 응용 프로그램 이름만 입력하면 됩니다. 그러나 전체 응용 프로그램 ID 앞에 urn:application:이 자동으로 추가됩니다. 예를 들어 ApplicationID에 값 tapp2를 입력하면 해당 ID가 urn:application:tapp2로 저장됩니다. 마찬가지로, Identity를 TrustPool.litwareinc.com/tapp2로 입력하면 Identity가 TrustPool.litwareinc.com/urn:application:tapp2로 시스템에 저장됩니다.

이 cmdlet에 Port 값을 지정하는 경우 cmdlet에서 포트를 열지 않습니다. 신뢰할 수 있는 응용 프로그램에서 방화벽 외부의 네트워크에 연결하려면 Windows 방화벽 및 기타 회사 방화벽에서 포트를 열어야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsTrustedApplication** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsTrustedApplication\\b"}

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
<td><p>응용 프로그램의 이름입니다. 이 이름은 TrustedApplicationPoolFqdn 매개 변수에 지정된 풀에서 고유한 문자열이어야 합니다. 문자열은 공백을 포함할 수 있습니다. ApplicationId 값을 제공하는 경우 TrustedApplicationPoolFqdn 매개 변수의 값도 제공해야 합니다. ApplicationId와 Identity를 모두 지정할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Port</em></p></td>
<td><p>필수</p></td>
<td><p>System.Int32</p></td>
<td><p>응용 프로그램이 실행될 포트 번호입니다. 포트는 지정된 풀에서 고유해야 합니다. 즉, 지정된 풀에서 동일한 포트를 사용하는 다른 응용 프로그램을 정의할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TrustedApplicationPoolFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>응용 프로그램이 있는 신뢰할 수 있는 응용 프로그램 풀의 FQDN입니다. TrustedApplicationPoolFqdn 값을 제공하는 경우 ApplicationId 값도 제공해야 하지만 Identity 매개 변수의 값은 제공할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableTcp</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>신뢰할 수 있는 응용 프로그램에서 TCP(Transmission Control Protocol)를 사용하도록 지정합니다. 신뢰할 수 있는 응용 프로그램이 Microsoft Unified Communications Managed API(UCMA) 응용 프로그램이 아닌 경우에만 이 매개 변수를 사용합니다. UCMA 응용 프로그램은 MTLS(Mutual Transport Layer Security) 프로토콜만 지원합니다. EnableTcp 매개 변수와 함께 Force 매개 변수를 지정하지 않으면 새 신뢰할 수 있는 응용 프로그램이 만들어지기 전에 확인 메시지가 표시됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.ExternalApplicationIdentity</p></td>
<td><p>풀에 있는 신뢰할 수 있는 응용 프로그램의 고유 식별자입니다. Identity 값은 &lt;풀 FQDN&gt;/&lt;응용 프로그램 ID&gt; 형식으로 입력해야 합니다. 여기서 풀 FQDN은 응용 프로그램이 있는 풀의 FQDN(정규화된 도메인 이름)이고, 응용 프로그램 ID는 응용 프로그램 이름입니다. 응용 프로그램 ID는 지정된 풀에서 고유해야 합니다.</p>
<p>Identity를 입력하는 경우 ApplicationId 또는 TrustedApplicationPoolFqdn 매개 변수의 값을 지정할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LegacyApplicationName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>응용 프로그램을 Microsoft Office Communications Server 2007 R2 배포에서 마이그레이션하는 경우에만 이 매개 변수를 사용합니다. 두 가지가 함께 작동하려면 이 값이 Office Communications Server 2007 R2 버전 응용 프로그램의 GRUU 형식과 같아야 합니다.</p>
<p>대부분의 경우 ApplicationId 매개 변수를 GRUU 형식과 동일하게 설정하면 응용 프로그램이 함께 작동할 수 있게 됩니다. 그러나 Office Communications Server 2007 R2 응용 프로그램의 GRUU 형식에 ApplicationId에서 유효하지 않은 문자가 포함된 경우에는 LegacyApplicationName 매개 변수에 이 값을 제공해야 합니다.</p>
<p>이 매개 변수의 값을 지정하지 않으면 응용 프로그램 ID 값이 urn:application: 접두사 없이 자동으로 삽입됩니다.</p></td>
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

없음.

## 반환 형식

Microsoft.Rtc.Management.Xds.DisplayTrustedApplication 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsTrustedApplication](remove-cstrustedapplication.md)  
[Set-CsTrustedApplication](set-cstrustedapplication.md)  
[Get-CsTrustedApplication](get-cstrustedapplication.md)

