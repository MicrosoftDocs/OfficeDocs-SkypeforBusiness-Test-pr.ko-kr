---
title: Get-CsOAuthServer
TOCTitle: Get-CsOAuthServer
ms:assetid: c2a61eb0-cdff-4069-99e4-2bdf42812f47
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205238(v=OCS.15)
ms:contentKeyID: 49304937
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsOAuthServer

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 OAuth(Open Authorization) 서버에 대한 정보를 반환합니다. 보안 토큰 서버라고도 하는 OAuth 서버는 서버 간 인증 및 권한 부여에 사용되는 보안 토큰을 발급합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsOAuthServer [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsOAuthServer [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>] [-Tenant <Guid>]

## 예제

## 예제 1

예제 1에서는 조직에서 사용하도록 구성된 모든 OAuth 서버에 대한 정보를 반환합니다.

    Get-CsOAuthServer

## 예제 2

예제 2에서는 ID가 "Office 365"인 OAuth 서버에 대한 정보를 반환합니다.

    Get-CsOAuthServer -Identity "Office 365"

## 자세한 정보

Lync Server 2013에서는 Lync Server 2013과 Microsoft Exchange Server 2013이 정보를 공유할 수 있도록 하는 인증과 같은 서버 간 인증이 OAuth 보안 프로토콜을 사용하여 수행됩니다. 이러한 인증 유형에서는 보통 서로 통신해야 하는 서버 2대(서버 A와 B) 및 제3의 보안 토큰 서버 등 총 3대의 서버가 필요합니다. 서버 A와 B는 서로 통신해야 하는 경우 OAuth 서버라고도 하는 토큰 서버에 연결하여 두 서버가 신원을 증명하기 위해 교환할 수 있는 상호 트러스트된 보안 토큰을 가져옵니다.

온-프레미스 버전 Lync Server 2013을 사용 중인데 OAuth 프로토콜을 완벽하게 지원하는 다른 서버 제품(예: Exchange 2013 또는 Microsoft SharePoint 2013)과 통신해야 하는 경우에는 대개 토큰 서버를 사용할 필요가 없습니다. 이러한 서버 제품은 자체 보안 토큰을 직접 발급할 수 있기 때문입니다. 그러나 Office 365에서 제공되는 서버 제품을 비롯한 다른 서버 제품과 통신해야 하는 경우에는 토큰 서버를 사용해야 합니다. 이러한 토큰 서버는 **CsOAuthServer** cmdlet을 사용하여 관리할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsOAuthServer"}

**Lync Server 제어판:** **Get-CsOAuthServer** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>하나 이상의 OAuth 서버를 반환하기 위해 와일드카드 문자를 사용할 수 있습니다. 예를 들어 ID에 문자열 값 &quot;Microsoft&quot;가 포함된 모든 OAuth 서버를 반환하려면 다음 구문을 사용합니다.</p>
<p>-Filter &quot;*Microsoft*&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>반환할 OAuth 서버의 고유 식별자입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;Office 365&quot;</p>
<p>Identity 매개 변수와 Filter 매개 변수를 모두 명령에 포함하지 않으면 <strong>Get-CsOAuthServer</strong> cmdlet은 모든 OAuth 서버에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 OAuth 서비스 데이터를 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>해당 OAuth 서버 설정을 검색할 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다.</p>
<p>예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsOAuthServer** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsOAuthServer** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.OAuthServer\#Decorated 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsOAuthServer](new-csoauthserver.md)  
[Remove-CsOAuthServer](remove-csoauthserver.md)  
[Set-CsOAuthServer](set-csoauthserver.md)

