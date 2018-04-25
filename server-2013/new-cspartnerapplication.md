---
title: New-CsPartnerApplication
TOCTitle: New-CsPartnerApplication
ms:assetid: 0248acde-626d-42b4-a071-c96171364a18
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204628(v=OCS.15)
ms:contentKeyID: 49302622
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsPartnerApplication

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 파트너 응용 프로그램을 만듭니다. 파트너 응용 프로그램은 Lync Server 2013에서 타사 보안 토큰 서버를 거치지 않고 보안 토큰을 직접 교환할 수 있는 응용 프로그램입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsPartnerApplication -ApplicationIdentifier <String> -ApplicationTrustLevel <User | Application | Full> -CertificateRawData <String> -Realm <String> [-AcceptSecurityIdentifierInformation <$true | $false>] [-Enabled <$true | $false>] [-Identity <XdsGlobalRelativeIdentity>] [-Tenant <Guid>] <COMMON PARAMETERS>

    New-CsPartnerApplication -ApplicationIdentifier <String> -ApplicationTrustLevel <User | Application | Full> -CertificateFileData <String> -Realm <String> [-AcceptSecurityIdentifierInformation <$true | $false>] [-Enabled <$true | $false>] [-Identity <XdsGlobalRelativeIdentity>] [-Tenant <Guid>] <COMMON PARAMETERS>

    New-CsPartnerApplication -ApplicationIdentifier <String> -ApplicationTrustLevel <User | Application | Full> -UseOAuthServer <SwitchParameter> [-AcceptSecurityIdentifierInformation <$true | $false>] [-Enabled <$true | $false>] [-Identity <XdsGlobalRelativeIdentity>] [-Realm <String>] [-Tenant <Guid>] <COMMON PARAMETERS>

    New-CsPartnerApplication -ApplicationTrustLevel <User | Application | Full> -MetadataUrl <String> [-AcceptSecurityIdentifierInformation <$true | $false>] [-Enabled <$true | $false>] [-Identity <XdsGlobalRelativeIdentity>] [-Tenant <Guid>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 "MicrosoftExchange"인 새 파트너 응용 프로그램을 만듭니다. 이 예제에서 새 파트너 응용 프로그램은 메타데이터 URL https://autodiscover.litwareinc.com/metadata/json/1을 사용합니다.

    New-CsPartnerApplication -Identity "MicrosoftExchange" -ApplicationTrustLevel "Full" -MetadataUrl"https://autodiscover.litwareinc.com/metadata/json/1"

## 예제 2

예제 2에 표시된 명령도 ID가 "MicrosoftExchange"인 새 파트너 응용 프로그램을 만듭니다. 그러나 이 경우에는 새 파트너 응용 프로그램이 메타데이터 URL을 사용하지 않으며 대신 미리 정의된 OAuth 서버를 사용하도록 구성됩니다. 이를 위해 명령은 MetadataUrl 매개 변수 대신 UseOAuthServer 매개 변수를 사용합니다.

    New-CsPartnerApplication -Identity "MicrosoftExchange" -ApplicationIdentifier "microsoft.exchange" -ApplicationTrustLevel "Full" -UseOAuthServer

## 자세한 정보

Lync Server 2013에서는 Lync Server 2013과 Exchange 2013이 정보를 공유할 수 있도록 하는 인증과 같은 서버 간 인증이 OAuth 보안 프로토콜을 사용하여 수행됩니다. 이러한 인증 유형에서는 보통 서로 통신해야 하는 서버 2대(서버 A와 B) 및 제3의 보안 토큰 서버 등 총 서버 3대가 필요합니다. 서버 A와 B는 서로 통신해야 하는 경우 OAuth 서버라고도 하는 토큰 서버에 연결하여 두 서버가 신원을 증명하기 위해 교환할 수 있는 상호 신뢰된 보안 토큰을 가져옵니다.

온-프레미스 버전의 Lync Server 2013을 사용 중인데 OAuth 프로토콜을 완벽하게 지원하는 다른 서버 제품(예: Exchange 2013 또는 Microsoft SharePoint 2013)과 통신해야 하는 경우에는 대개 토큰 서버를 사용할 필요가 없습니다. 이러한 서버 제품은 자체 보안 토큰을 직접 발급할 수 있기 때문입니다. 그러나 Exchange 2013 등의 다른 서버 제품을 파트너 응용 프로그램으로 구성해야 하며 다른 서버 제품에 대해 Lync Server 2013를 파트너 응용 프로그램으로 구성해야 합니다. Lync Server 2013에서는 **CsPartnerApplication** cmdlet을 사용하여 파트너 응용 프로그램을 관리합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsPartnerApplication"}

**Lync Server 제어판:** **New-CsPartnerApplication** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>ApplicationIdentifier</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>파트너 응용 프로그램의 고유 식별자입니다. 서버 응용 프로그램에서 ApplicationIdentifier가 제공됩니다. 같은 명령에서 ApplicationIdentifier 매개 변수와 MetadataUrl 매개 변수를 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ApplicationTrustLevel</em></p></td>
<td><p>필수</p></td>
<td><p>응용 프로그램 신뢰 수준</p></td>
<td><p>Lync Server 2013 및 파트너 응용 프로그램 간의 신뢰 수준을 지정합니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Full -- 기본값으로, 파트너 응용 프로그램이 자기 자신을 표시하고 영역 내의 사용자를 가장하는 것으로 신뢰됩니다.</p>
<p>* Application -- 파트너 응용 프로그램이 영역 내에서 자기 자신을 표시하는 것으로 신뢰됩니다. 사용자를 가장하려면 보안 토큰 서버를 통한 동의를 얻어야 합니다.</p>
<p>* User -- 파트너 응용 프로그램은 사용자를 표시하려는 경우 보안 토큰 서버로부터 동의를 얻어야 하며 자기 자신을 표시할 수는 없습니다.</p>
<p>기본값은 Full입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>CertificateFileData</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>파트너 응용 프로그램에 할당할 수 있는 인증서 파일의 경로입니다. 예를 들면 다음과 같습니다.</p>
<p>-CertificateFileData &quot;C:\Certificates\PartnerApplication.cer&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>CertificateRawData</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>파트너 응용 프로그램에 할당할 수 있는 인증서(Base64 인코딩 형식)입니다. 인증서에서 원시 데이터를 읽은 다음 필요한 형식으로 변환하려면 다음과 같은 명령을 사용합니다.</p>
<p>$x = Get-Content &quot;C:\Certificates\PartnerApplication.cer&quot; -Encoding Byte</p>
<p>$y = [Convert]::ToBase64String($x)</p>
<p>그런 후에 다음 구문을 사용하여 $y 변수에 저장된 인증서 데이터를 할당할 수 있습니다.</p>
<p>-CertificateRawData $y</p></td>
</tr>
<tr class="odd">
<td><p><em>MetadataUrl</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>파트너 응용 프로그램에 대한 WS-FederationMetadata가 게시되는 URL입니다. 파트너 응용 프로그램은 메타데이터를 사용하여 교환할 토큰 유형 및 해당 토큰에 서명하는 데 사용할 키 유형에 합의합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UseOAuthServer</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>이 매개 변수가 있으면 파트너 응용 프로그램이 응용 프로그램 자체에서 기본 제공되는 보안 토큰 서버 대신 미리 권한이 부여된 OAuth 서버 중 하나를 사용함을 나타냅니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AcceptSecurityIdentifierInformation</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>True($True)로 설정하면 인증용으로 SID(보안 식별자)를 사용할 수 있습니다. 기본값은 False입니다.</p></td>
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
<td><p>True로 설정하면 파트너 응용 프로그램이 사용하도록 설정되며 즉시 사용 가능한 상태가 됩니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Xds 글로벌 상대 ID</p></td>
<td><p>새 파트너 응용 프로그램의 고유 식별자입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Realm</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>서버 간 보안 컨테이너입니다. 기본적으로 Lync Server 2013에서는 기본 SIP 도메인을 OAuth 영역으로 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>GUID</p></td>
<td><p>새 파트너 응용 프로그램을 만드는 대상 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>-Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsPartnerApplication** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsPartnerApplication** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.PartnerApplication\#Decorated 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsPartnerApplication](get-cspartnerapplication.md)  
[Remove-CsPartnerApplication](remove-cspartnerapplication.md)  
[Set-CsPartnerApplication](set-cspartnerapplication.md)

