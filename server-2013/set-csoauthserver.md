---
title: Set-CsOAuthServer
TOCTitle: Set-CsOAuthServer
ms:assetid: 52825ca3-d287-4e09-9aec-b8b2d7bafc06
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204896(v=OCS.15)
ms:contentKeyID: 49303637
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsOAuthServer

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 OAuth(Open Authorization) 서버를 수정합니다. 보안 토큰 서버라고도 하는 OAuth 서버는 서버 간 인증 및 권한 부여에 사용되는 보안 토큰을 발급합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsOAuthServer <COMMON PARAMETERS>

    Set-CsOAuthServer [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-MetadataUrl <String>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 OAuth 서버 Office 365의 메타데이터 URL을 업데이트합니다.

    Set-CsOAuthServer -Identity "Office 365" -MetadataUrl "https://sts.office365.microsoft.com/metadata/json/1"

## 자세한 정보

Lync Server 2013에서는 Lync Server 2013과 Microsoft Exchange Server 2013이 정보를 공유할 수 있도록 하는 인증과 같은 서버 간 인증이 OAuth 보안 프로토콜을 사용하여 수행됩니다. 이러한 인증 유형에서는 보통 서로 통신해야 하는 서버 2대(서버 A와 B) 및 제3의 보안 토큰 서버 등 총 3대의 서버가 필요합니다. 서버 A와 B는 서로 통신해야 하는 경우 OAuth 서버라고도 하는 토큰 서버에 연결하여 두 서버가 신원을 증명하기 위해 교환할 수 있는 상호 트러스트된 보안 토큰을 가져옵니다.

온-프레미스 버전 Lync Server 2013를 사용 중인데 OAuth 프로토콜을 완벽하게 지원하는 다른 서버 제품(예: Exchange 2013 또는 Microsoft SharePoint 2013)과 통신해야 하는 경우에는 대개 토큰 서버를 사용할 필요가 없습니다. 이러한 서버 제품은 자체 보안 토큰을 직접 발급할 수 있기 때문입니다. 그러나 Office 365에서 제공되는 서버 제품을 비롯한 다른 서버 제품과 통신해야 하는 경우에는 토큰 서버를 사용해야 합니다. 이러한 토큰 서버는 CsOAuthServer cmdlet을 사용하여 관리할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsOAuthServer"}

**Lync Server 제어판:** **Set-CsOAuthServer** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>OAuth 서버를 식별하는 데 사용되는 고유한 이름입니다.</p></td>
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
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MetadataUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>서버에 대한 WS-FederationMetadata가 게시되는 URL입니다. 서버는 메타데이터를 사용하여 교환할 토큰 유형 및 해당 토큰에 서명하는 데 사용할 키 유형에 합의합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>수정할 OAuth 서버에 대한 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>-Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
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

**Set-CsOAuthServer** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.OAuthServer\#Decorated 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsOAuthServer** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.OAuthServer\#Decorated 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsOAuthServer](get-csoauthserver.md)  
[New-CsOAuthServer](new-csoauthserver.md)  
[Remove-CsOAuthServer](remove-csoauthserver.md)

