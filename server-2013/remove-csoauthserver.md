---
title: Remove-CsOAuthServer
TOCTitle: Remove-CsOAuthServer
ms:assetid: fac7be48-06bb-4572-86a2-b872fe96d199
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205408(v=OCS.15)
ms:contentKeyID: 49305597
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsOAuthServer

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 OAuth(Open Authorization) 서버를 제거합니다. 보안 토큰 서버라고도 하는 OAuth 서버는 서버 간 인증 및 권한 부여에 사용되는 보안 토큰을 발급합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsOAuthServer -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 단일 OAuth 서버, 즉 ID가 "Office 365"인 서버를 삭제합니다.

    Remove-CsOAuthServer -Identity "Office365"

## 예제 2

예제 2에서는 조직에서 사용하도록 구성된 모든 OAuth 서버를 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsOAuthServer** cmdlet을 호출하여 모든 OAuth 서버를 반환합니다. 이러한 서버는 **Remove-CsOAuthServer** cmdlet에 파이프되며 해당 cmdlet에 의해 제거됩니다.

    Get-CsOAuthServer | Remove-CsOAuthServer

## 자세한 정보

Lync Server 2013에서는 Lync Server 2013와 Microsoft Exchange Server 2013이 정보를 공유할 수 있도록 하는 인증과 같은 서버 간 인증이 OAuth 보안 프로토콜을 사용하여 수행됩니다. 이러한 인증 유형에서는 보통 서로 통신해야 하는 서버 2대(서버 A와 B) 및 제3의 보안 토큰 서버 등 총 3대의 서버가 필요합니다. 서버 A와 B는 서로 통신해야 하는 경우 OAuth 서버라고도 하는 토큰 서버에 연결하여 두 서버가 신원을 증명하기 위해 교환할 수 있는 상호 트러스트된 보안 토큰을 가져옵니다.

온-프레미스 버전 Lync Server 2013을 사용 중인데 OAuth 프로토콜을 완벽하게 지원하는 다른 서버 제품(예: Exchange 2013 또는 Microsoft SharePoint 2013)과 통신해야 하는 경우에는 대개 토큰 서버를 사용할 필요가 없습니다. 이러한 서버 제품은 자체 보안 토큰을 직접 발급할 수 있기 때문입니다. 그러나 Office 365에서 제공되는 서버 제품을 비롯한 다른 서버 제품과 통신해야 하는 경우에는 토큰 서버를 사용해야 합니다. 이러한 토큰 서버는 **CsOAuthServer** cmdlet을 사용하여 관리할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsOAuthServer"}

**Lync Server 제어판:** **Remove-CsOAuthServer** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>삭제할 OAuth 서버의 고유 식별자입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;Office 365&quot;</p></td>
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
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>삭제할 OAuth 서버에 대한 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>실제로 명령을 수행하지는 않고 명령을 실행했을 때 발생할 결과에 대해 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Remove-CsOAuthServer** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.OAuthServer\#Decorated 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsOAuthServer** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.OAuthServer\#Decorated 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsOAuthServer](get-csoauthserver.md)  
[New-CsOAuthServer](new-csoauthserver.md)  
[Set-CsOAuthServer](set-csoauthserver.md)

