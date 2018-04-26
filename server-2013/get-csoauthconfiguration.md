---
title: Get-CsOAuthConfiguration
TOCTitle: Get-CsOAuthConfiguration
ms:assetid: a3fda8bf-84e3-4d14-a1c5-093e6eb36ffe
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205155(v=OCS.15)
ms:contentKeyID: 49304605
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsOAuthConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용 중인 OAuth(Open Authorization) 구성 설정에 대한 정보를 반환합니다. OAuth는 서버 간 인증 및 권한 부여에 사용되는 표준 프로토콜입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsOAuthConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsOAuthConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>] [-Tenant <Guid>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용 중인 OAuth 구성 설정에 대한 정보를 반환합니다.

    Get-CsOAuthConfiguration

## 자세한 정보

Lync Server 2013에서는 Lync Server와 Microsoft Exchange Server 2013이 정보를 공유할 수 있도록 하는 인증과 같은 서버 간 인증이 OAuth 보안 프로토콜을 사용하여 수행됩니다. Lync Server 2013에서 OAuth는 항상 설정되어 있습니다. 이 프로토콜은 사용하거나 사용하지 않도록 설정할 필요가 없으며 이렇게 설정할 수 있는 방법도 없습니다. 그러나 Lync Server에서 Exchange 2013, Microsoft SharePoint 2013 등의 다른 서버 제품과 통신해야 하는 경우에는 OAuth 구성 설정을 수정해야 할 수 있습니다. 예를 들어 Office 365 버전 Exchange의 자동 검색 URL을 지정하고 영역 이름을 지정해야 할 수 있습니다. 이러한 설정은 **CsOAuthConfiguration** cmdlet을 통해서만 관리할 수 있으며 Lync Server 2013 제어판에서는 OAuth 설정 관리용 옵션이 제공되지 않습니다.

온-프레미스 버전 Lync Server 2013에서는 OAuth 설정의 전역 컬렉션을 하나만 사용할 수 있습니다. 즉, 추가 OAuth 설정 컬렉션을 만들거나 전역 컬렉션을 삭제할 수는 없습니다. 각 비즈니스용 Skype Online 테넌트 역시 OAuth 구성 설정 컬렉션을 하나만 사용할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsOAuthConfiguration"}

**Lync Server 제어판:** **Get-CsOAuthConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>OAuth 구성 설정의 컬렉션을 참조할 때 와일드카드 값을 사용할 수 있습니다. 이러한 설정에 대해서는 전역 인스턴스를 하나만 사용할 수 있으므로 Filter 매개 변수는 사용할 필요가 없습니다. 그러나 원하는 경우 다음 구문을 사용하여 전역 설정을 참조할 수 있습니다.</p>
<p>-Filter &quot;g*&quot;</p>
<p>이 구문은 ID가 &quot;g&quot; 문자로 시작되는 모든 OAuth 구성 설정을 가져옵니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>OAuth 구성 설정의 고유 ID입니다. 이러한 설정에 대해서는 전역 인스턴스를 하나만 사용할 수 있으므로 <strong>Get-CsOAuthConfiguration</strong> cmdlet을 호출할 때 ID를 지정할 필요가 없습니다. 그러나 원하는 경우에는 다음 구문을 사용하여 전역 설정을 참조할 수 있습니다.</p>
<p>-Identity global</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 OAuth 구성 데이터를 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>해당 OAuth 구성 설정을 검색할 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다.</p>
<p>예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsOAuthConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsOAuthConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.OAuthSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Set-CsOAuthConfiguration](set-csoauthconfiguration.md)

