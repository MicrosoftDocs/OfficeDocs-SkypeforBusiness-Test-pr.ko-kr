---
title: Set-CsWebServiceConfiguration
TOCTitle: Set-CsWebServiceConfiguration
ms:assetid: 5aa0316d-afd8-4cc2-b606-0e720e6ab021
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398396(v=OCS.15)
ms:contentKeyID: 49303737
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsWebServiceConfiguration

 

_**마지막으로 수정된 항목:** 2014-06-05_

웹 서비스 구성 설정의 기존 컬렉션을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsWebServiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsWebServiceConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AllowAnonymousAccessToLWAConference <$true | $false>] [-AllowExternalAuthentication <$true | $false>] [-AutoLaunchLyncWebAccess <$true | $false>] [-CASigningKeyLength <UInt64>] [-Confirm [<SwitchParameter>]] [-CrossDomainAuthorizationList <PSListModifier>] [-DefaultValidityPeriodHours <UInt64>] [-EnableCertChainDownload <$true | $false>] [-EnableGroupExpansion <$true | $false>] [-Force <SwitchParameter>] [-InferCertChainFromSSL <$true | $false>] [-MACResolverUrl <String>] [-MaxCSRKeySize <UInt64>] [-MaxGroupSizeToExpand <UInt32>] [-MaxValidityPeriodHours <UInt64>] [-MinCSRKeySize <UInt64>] [-MinValidityPeriodHours <UInt64>] [-SecondaryLocationSourceUrl <String>] [-ShowAlternateJoinOptionsExpanded <$true | $false>] [-ShowDownloadCommunicatorAttendeeLink <$true | $false>] [-ShowJoinUsingLegacyClientLink <$true | $false>] [-TrustedCACerts <PSListModifier>] [-UseCertificateAuth <$true | $false>] [-UseDomainAuthInLWA <$true | $false>] [-UsePinAuth <$true | $false>] [-UseWindowsAuth <None | Negotiate | NTLM>] [-UseWsFedPassiveAuth <$true | $false>] [-WhatIf [<SwitchParameter>]] [-WsFedPassiveMetadataUri <String>]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트에 적용되는 웹 서비스 구성 설정의 그룹 확장을 활성화합니다(-Identity site:Redmond). 이 작업은 EnableGroupExpansion 속성을 포함하고 매개 변수 값을 True로 설정하여 수행됩니다.

    Set-CsWebServiceConfiguration -Identity site:Redmond -EnableGroupExpansion $True

## 예제 2

예제 2에서는 사이트 범위에서 적용된 모든 웹 서비스 구성 설정의 최대 유효 기간이 16시간으로 변경됩니다. 이 작업을 수행하기 위해 Filter 매개 변수와 함께 **Get-CsWebServiceConfiguration** cmdlet을 호출합니다. 필터 값 "site:\*"는 반환되는 데이터를 ID가 "site:" 문자로 시작하는 설정으로 제한합니다. 그런 다음 이 컬렉션은 컬렉션의 각 항목을 가져오고 MaxValidityPeriodHours 속성을 16으로 변경하는 **Set-CsWebServiceConfiguration** cmdlet에 파이프됩니다.

    Get-CsWebServiceConfiguration -Filter "site:*" | Set-CsWebServiceConfiguration -MaxValidityPeriodHours 16

## 예제 3

예제 3에서는 그룹 확장을 허용하는 웹 서비스 구성 설정의 각 컬렉션에 대해 그룹 확장 크기를 400으로 설정합니다. 이 작업을 수행하기 위해 매개 변수 없이 **Get-CsWebServiceConfiguration** cmdlet을 호출합니다. 그러면 조직에서 사용되는 모든 웹 서비스 구성 설정의 컬렉션이 반환됩니다. 이 컬렉션은 EnableGroupExpansion 속성이 True와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이 필터링된 컬렉션은 컬렉션의 각 항목을 가져와 MaxGroupSizeToExpand 속성 값을 400으로 설정하는 **Set-CsWebServiceConfiguration** cmdlet에 파이프됩니다.

    Get-CsWebServiceConfiguration | Where-Object {$_.EnableGroupExpansion -eq $True} | Set-CsWebServiceConfiguration -MaxGroupSizeToExpand 400

## 예제 4

예제 4에 표시된 명령은 Lync 이외의 클라이언트 응용 프로그램을 사용하여 모임에 참가하는 사용자에게 Lync Web App를 다운로드할 수 있는 사이트의 링크가 표시되도록 전역 웹 서비스 설정을 구성하는 방법을 보여 줍니다. 이 작업은 ShowDownloadCommunicatorAttendeeLink 매개 변수를 포함하고 매개 변수 값을 $True로 설정하여 수행됩니다.

    Set-CsWebServiceConfiguration -Identity global -ShowDownloadCommunicatorAttendeeLink $True 

## 예제 5

예제 5에 표시된 명령은 기존 웹 서비스 구성 설정 컬렉션에 http://fabrikam.com 도메인을 추가합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsWebOrigin** cmdlet을 사용하여 fabrikam.com에 대한 도메인 개체를 만듭니다. 만들어진 도메인 개체는 $x라는 변수에 저장됩니다.

예제의 두 번째 명령은 **Set-CsWebServiceConfiguration** cmdlet을 사용하여 Redmond 사이트에 적용된 웹 서비스 구성 설정에 http://fabrikam.com을 추가합니다. @{Add=$x} 구문은 도메인 간 스크립팅 권한이 부여된 도메인 컬렉션에 이미 포함되어 있는 도메인에 해당 도메인을 추가합니다. http://fabrikam.com만 포함하도록 기존 도메인을 바꾸려면 @{Replace=$x} 구문을 사용합니다.

    $x = New-CsWebOrigin -Url "http://fabrikam.com"
    Set-CsWebServiceConfiguration -Identity "site:Redmond" - CrossDomainAuthorizationList @{Add=$x}

## 예제 6

예제 6에서는 도메인 간 스크립팅 권한이 부여된 도메인 컬렉션의 첫 번째 도메인을 Redmond 사이트에 대한 웹 서비스 구성 설정에서 제거합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **Get-CsWebServiceConfiguration** cmdlet을 사용하여 Redmond 사이트의 현재 설정을 반환합니다. 이러한 값은 $x라는 변수에 저장됩니다.

두 번째 명령은 RemoveAt 메서드를 사용하여 첫 번째 도메인을 CrossDomainAuthorizationList 속성에서 제거합니다. 이 속성에는 도메인이 배열로 저장되므로 첫 번째 도메인의 인덱스 번호는 0이고 두 번째 도메인의 인덱스 번호는 1입니다. CrossDomainAuthorizationList 속성에서 두 번째 도메인을 제거하려면 다음 구문을 사용합니다.

$x.CrossDomainAuthorizationList.RemoveAt(1)

두 번째 명령은 사이트 자체에서가 아니라 변수 $x에 저장된 Redmond 사이트의 복사본에서 도메인을 제거합니다. Redmond 사이트에서 도메인을 실제로 제거하려면 **Set-CsWebServiceConfiguration** cmdlet 및 Instance 매개 변수를 사용하여 Redmond 사이트의 설정을 $x에 저장된 설정으로 덮어씁니다.

    $x = Get-CsWebServiceConfiguration -Identity "site:Redmond"
    $x.CrossDomainAuthorizationList.RemoveAt(0)
    Set-CsWebServiceConfguration -Instance $x

## 예제 7

예제 7에 표시된 명령은 도메인 간 스크립팅 권한이 있는 모든 도메인을 제거하여 Redmond 사이트의 웹 서비스 구성 설정을 수정합니다. 이 작업을 수행하려면 CrossDomainAuthorizationList 속성을 null 값($Null)으로 설정합니다.

    Set-CsWebServiceConfiguration -Identity "site:Redmond" - CrossDomainAuthorizationList $Null

## 자세한 정보

많은 Lync Server 구성 요소가 웹에 기반을 두고 있습니다. 이러한 구성 요소는 웹 서비스 또는 웹 페이지를 사용하여 작업을 수행합니다. 예를 들어 사용자는 주소록에서 새 연락처를 검색하거나 그룹 확장을 사용하여 메일 그룹의 개별 구성원을 볼 때 웹 서비스를 사용합니다. 마찬가지로 전화 접속 회의부터 Lync Server 제어판에 이르는 구성 요소는 Lync Server와 사용자 간의 인터페이스로 웹 페이지를 사용합니다.

**CsWebServiceConfiguration** cmdlet을 사용하면 관리자가 조직 전체의 웹 서비스 구성 설정을 관리할 수 있습니다. 여기에는 그룹 확장, 인증서 설정 및 허용되는 인증 방법 관리가 포함됩니다. 전역, 사이트 및 서비스(웹 서비스에만 해당) 범위에 여러 설정을 구성할 수 있으므로 다양한 사용자 및 위치에 대해 웹 서비스 기능을 사용자 지정할 수 있습니다. **CsWebServiceConfiguration** cmdlet을 사용하면 관리자가 조직 전체의 웹 서비스 구성 설정을 관리할 수 있습니다. 여기에는 그룹 확장, 인증서 설정 및 허용되는 인증 방법 관리가 포함됩니다. 전역, 사이트 및 서비스(웹 서비스에만 해당) 범위에 여러 설정을 구성할 수 있으므로 다양한 사용자 및 위치에 대해 웹 서비스 기능을 사용자 지정할 수 있습니다.

사용자 지정 설정(예: 인증서에 대한 사용자 지정 유효성 기간)은 새 웹 서비스 구성 설정 컬렉션을 생성할 때 지정할 수 있습니다. 또는 **Set-CsWebServiceConfiguration** cmdlet을 사용하여 기존 컬렉션의 속성 값을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsWebServiceConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsWebServiceConfiguration"}

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
<td><p><em>AllowAnonymousAccessToLWAConference</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 익명 사용자가 Lync Web App 회의에 참가할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowExternalAuthentication</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 OAuth 인증을 사용하여 외부 사용자를 인증할 수 있습니다.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>AutoLaunchLyncWebAccess</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 매개 변수는 온-프레미스 버전의 Lync Server 2013에서는 더 이상 사용되지 않습니다.</p>
<p>True로 설정하면 온라인 전화 회의에 참가하기 위한 기본 웹 팝업으로 Lync Web App을 자동으로 사용합니다. 단, Lync Web App 사용을 위한 필수 구성 요소(예: Silverlight가 설치되었으며 Internet Explorer에서 팝업 창을 차단하지 않음)가 충족되어야 합니다.</p>
<p>기본값은 True입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CASigningKeyLength</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt64</p></td>
<td><p>CA(인증 기관)가 디지털 인증서에 서명하는 데 사용한 개인 키인 CA 서명 키의 크기를 설정합니다. 서명 키 길이는 2048-16384바이트 사이의 정수 값으로 설정할 수 있습니다. 기본값은 2048입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CrossDomainAuthorizationList</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>Lync Server 2013 배포로 도메인 간 스크립팅 요청을 보내는 웹 응용 프로그램을 호스트하도록 허용되는 도메인 모음입니다.</p>
<p>New-CsWebOrigin cmdlet을 사용하여 목록에 추가할 도메인을 만든 후 새 웹 서비스 구성 설정 컬렉션에 추가해야 합니다. 또한 도메인 이름 앞에 http: 또는 https: 접두사를 지정해야 합니다. 자세한 내용은 이 도움말 항목의 예제 5, 6, 7을 참조하십시오.</p>
<p>이 매개 변수는 Lync Server 2013의 2013년 2월 릴리스에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DefaultValidityPeriodHours</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt64</p></td>
<td><p>인증서 인증을 사용할 때 클라이언트는 인증서의 유효 기간(시간)을 요청할 수 있습니다. DefaultValidityPeriodHours는 클라이언트가 사용자 지정 유효 기간을 요청하지 않는 경우 인증서의 유효 시간을 나타냅니다.</p>
<p>DefaultValidityPeriodHours는 8-8760시간(365일) 사이의 임의 정수 값이 될 수 있습니다. 기본값은 4320(180일)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableCertChainDownload</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정되면 사용자가 인증 인증서를 제공한 서버가 해당 인증서의 인증서 체인을 다운로드하게 됩니다. 인증서 체인은 개별 인증서의 발급 CA를 추적합니다. 인증서의 CA를 신뢰할 수 있어야 인증서로 인증할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableGroupExpansion</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정된 경우 Lync에서 그룹 확장을 사용할 수 없게 됩니다. 그룹 확장을 통해 사용자는 메일 그룹을 연락처로 구성한 다음 해당 그룹을 &quot;확장&quot;할 수 있습니다. 그룹이 확장되면 사용자는 그룹의 개별 구성원과 구성원의 현재 상태 정보를 확인할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>cmdlet을 실행할 때 나타날 수 있는 확인 프롬프트 또는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 웹 서비스 구성 설정의 고유 식별자입니다. 사이트 범위에서 구성된 설정을 수정하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. 서비스 범위에서 구성된 설정을 수정하려면 -Identity &quot;service:WebServer:atl-cs-001.litwareinc.com&quot;과 유사한 구문을 사용합니다.</p>
<p>전역 범위에서 구성된 설정을 수정하려면 -identity global과 같은 구문을 사용할 수 있습니다.</p>
<p>Identity 매개 변수를 사용하지 않으면 <strong>Set-CsWebServiceConfiguration</strong> cmdlet이 전역 컬렉션을 자동으로 수정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InferCertChainFromSSL</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정된 경우 서버가 SSL(Secure Sockets Layer) 프로토콜에 포함된 인증서 정보를 사용하여 발급 CA를 확인합니다. 인증서의 CA를 신뢰할 수 있어야 인증서로 인증할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>WebServiceSettings 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MACResolverUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>MAC(미디어 액세스 제어) 확인을 수행할 수 있는 웹 서비스의 URL입니다. MAC 확인에서는 연결된 클라이언트의 MAC 주소를 가져온 다음 해당 클라이언트가 연결된 네트워크 스위치의 섀시 및 포트 ID를 반환합니다. MAC 확인은 Enhanced 9-1-1 서비스에서 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxCSRKeySize</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt64</p></td>
<td><p>CSR(인증서 서명 요청) 키의 최대 크기를 설정합니다. CSR은 디지털 인증서에 적용하기 위해 응용 프로그램에서 CA로 전송된 메시지입니다. CSR 키의 최대 크기는 1024-16384바이트의 정수 값으로 설정할 수 있습니다. 기본값은 16384입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxGroupSizeToExpand</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>그룹이 확장될 때 표시되는 최대 사용자 수를 나타냅니다. 예를 들어, MaxGroupSizeToExpand를 75로 설정하는 경우 그룹이 확장될 때 처음 75명의 그룹 구성원만 표시됩니다.</p>
<p>MaxGroupSizeToExpand는 1-1000(포함) 사이의 임의 정수 값으로 설정할 수 있습니다. 기본값은 100입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxValidityPeriodHours</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt64</p></td>
<td><p>인증서 인증을 사용할 때 클라이언트는 인증서의 유효 기간(시간)을 요청할 수 있습니다. MaxValidityPeriodHours는 클라이언트가 요청할 수 있는 최대 시간을 나타냅니다.</p>
<p>MaxValidityPeriodHours는 8-8760시간(365일) 사이의 임의 정수 값이 될 수 있습니다. 기본값은 8760입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MinCSRKeySize</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt64</p></td>
<td><p>CSR(인증서 서명 요청) 키의 최소 크기를 설정합니다. 최소 크기는 1024-16384바이트 사이의 정수 값으로 설정할 수 있습니다. 기본값은 16384입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MinValidityPeriodHours</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt64</p></td>
<td><p>인증서 인증을 사용할 때 클라이언트는 인증서의 유효 기간(시간)을 요청할 수 있습니다. MinValidityPeriodHours는 클라이언트가 요청할 수 있는 최소 시간을 나타냅니다.</p>
<p>MinValidityPeriodHours는 8-4320시간(180일) 사이의 임의 정수 값이 될 수 있습니다. 기본값은 8입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SecondaryLocationSourceUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>위치 요청을 처리할 수 있는 웹 서비스의 URL입니다. 이 서비스는 위치 요청을 로컬에서 확인할 수 없는 경우에만 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ShowAlternateJoinOptionsExpanded</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 매개 변수는 온-프레미스 버전의 Lync Server 2013에서는 더 이상 사용되지 않습니다.</p>
<p>True로 설정하면 Office Communicator 2007 R2 등 온라인 전화 회의 참가를 위한 대체 옵션이 자동으로 확장되어 사용자에게 표시됩니다. 기본값인 False로 설정하면 해당 옵션을 사용할 수는 있지만 사용자가 옵션 목록을 직접 표시해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ShowDownloadCommunicatorAttendeeLink</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 매개 변수는 온-프레미스 버전의 Lync Server 2013에서는 더 이상 사용되지 않습니다.</p>
<p>True(기본값)로 설정하면 Lync 이외의 클라이언트 응용 프로그램을 사용하여 모임에 참가하는 사용자에게 Lync Web App을 다운로드할 수 있는 링크가 표시됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ShowJoinUsingLegacyClientLink</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 매개 변수는 온-프레미스 버전의 Lync Server 2013에서는 더 이상 사용되지 않습니다.</p>
<p>True로 설정하면 Lync 이외의 클라이언트 응용 프로그램을 사용하여 모임에 참가하는 사용자에게 현재 클라이언트 응용 프로그램을 사용하여 모임에 참가할 수 있는 기회가 부여됩니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TrustedCACerts</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>웹 서버가 신뢰하는 인증서 체인을 나타내는 인증서 컬렉션입니다. 컬렉션에 추가할 새 인증서는 <strong>New-CsWebTrustedCACertificate</strong> cmdlet을 사용하여 만들어야 합니다.</p>
<p>InferCertChainFromSSL 속성이 True로 설정된 경우에는 이 컬렉션이 사용되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UseCertificateAuth</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정된 경우 인증서를 사용하여 클라이언트를 인증할 수 있습니다. 인증서 인증을 사용하지 않도록 설정하려면 이 값을 False로 설정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UseDomainAuthInLWA</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync Web App 사용자를 인증하는 방법으로 도메인 인증을 사용할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UsePinAuth</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 클라이언트가 개인식별번호(PIN)을 사용하여 인증할 수 있습니다. PIN 인증을 사용하지 않도록 설정하려면 이 값을 False로 설정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UseWindowsAuth</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Web.UseWindowsAuth</p></td>
<td><p>사용자가 Windows 인증을 사용하여 인증할지 여부와 그 방법을 지정합니다. Windows 인증은 Windows에 로그온할 때 사용한 것과 동일한 자격 증명을 사용합니다. 사용할 수 있는 값은 다음과 같습니다.</p>
<p>협상 - 클라이언트와 서버가 함께 적절한 인증 프로토콜(Kerberos 또는 NTLM)을 결정합니다.</p>
<p>NTLM - Windows 인증이 허용되지만 NTLM 프로토콜만 사용합니다.</p>
<p>없음 - Windows 인증이 허용되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UseWsFedPassiveAuth</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 수동 인증, 즉 URL 리디렉션 또는 스마트 링크를 통한 사용자 인증이 허용됩니다. 기본값은 False($False)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WsFedPassiveMetadataUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>WS-federation 웹 요청자 프로토콜에서 사용하는 URI입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Settings.Web.WebServiceSettings 개체입니다. **Set-CsWebServiceConfiguration** cmdlet은 웹 서비스 설정 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsWebServiceConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Web.WebServiceSettings 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsWebServiceConfiguration](get-cswebserviceconfiguration.md)  
[New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md)  
[Remove-CsWebServiceConfiguration](remove-cswebserviceconfiguration.md)

