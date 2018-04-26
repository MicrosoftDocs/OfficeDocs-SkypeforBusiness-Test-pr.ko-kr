---
title: New-CsWebServiceConfiguration
TOCTitle: New-CsWebServiceConfiguration
ms:assetid: 6225cf8d-b669-464e-9848-a292953e3a3a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398440(v=OCS.15)
ms:contentKeyID: 49303825
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsWebServiceConfiguration

 

_**마지막으로 수정된 항목:** 2014-06-05_

웹 서비스 구성 설정의 새 컬렉션을 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsWebServiceConfiguration -Identity <XdsIdentity> [-AllowAnonymousAccessToLWAConference <$true | $false>] [-AllowExternalAuthentication <$true | $false>] [-AutoLaunchLyncWebAccess <$true | $false>] [-CASigningKeyLength <UInt64>] [-Confirm [<SwitchParameter>]] [-CrossDomainAuthorizationList <PSListModifier>] [-DefaultValidityPeriodHours <UInt64>] [-EnableCertChainDownload <$true | $false>] [-EnableGroupExpansion <$true | $false>] [-Force <SwitchParameter>] [-InferCertChainFromSSL <$true | $false>] [-InMemory <SwitchParameter>] [-MACResolverUrl <String>] [-MaxCSRKeySize <UInt64>] [-MaxGroupSizeToExpand <UInt32>] [-MaxValidityPeriodHours <UInt64>] [-MinCSRKeySize <UInt64>] [-MinValidityPeriodHours <UInt64>] [-SecondaryLocationSourceUrl <String>] [-ShowAlternateJoinOptionsExpanded <$true | $false>] [-ShowDownloadCommunicatorAttendeeLink <$true | $false>] [-ShowJoinUsingLegacyClientLink <$true | $false>] [-TrustedCACerts <PSListModifier>] [-UseCertificateAuth <$true | $false>] [-UseDomainAuthInLWA <$true | $false>] [-UsePinAuth <$true | $false>] [-UseWindowsAuth <None | Negotiate | NTLM>] [-UseWsFedPassiveAuth <$true | $false>] [-WhatIf [<SwitchParameter>]] [-WsFedPassiveMetadataUri <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트(-Identity site:Redmond)의 새로운 웹 서비스 구성 설정 컬렉션을 만듭니다. 이 예제에는 두 가지 선택적 매개 변수가 포함되어 있는데, 하나는 False($False)로 설정된 EnableGroupExpansion이고 다른 하나는 True($True)로 설정된 UseCertificateAuth입니다. 이러한 두 매개 변수는 각각 그룹 확장을 사용하지 않도록 설정하고 인증에 인증서를 사용하도록 설정하는 데 사용됩니다.

레드몬드 사이트에 대해 웹 서비스 구성 설정 컬렉션이 이미 생성되어 있는 경우 이 명령이 실패합니다. 사이트는 단일 웹 서비스 구성 설정 컬렉션으로 제한되기 때문입니다.

    New-CsWebServiceConfiguration -Identity site:Redmond -EnableGroupExpansion $False -UseCertificateAuth $True

## 예제 2

예제 2는 예제 1에 표시된 명령의 변형된 형태입니다. 그러나 여기에서는 웹 서비스 구성 설정의 새 컬렉션이 처음에 메모리에만 생성되고 나중에 Redmond 사이트에 적용됩니다. 이를 수행하기 위해 이 예제의 첫 번째 명령이 **New-CsWebServiceConfiguration** cmdlet을 사용하여 Redmond 사이트에 대한 설정 컬렉션을 만들고, 이 컬렉션이 메모리에만 생성되고 Redmond 사이트에 즉시 적용되지 않도록 InMemory 매개 변수가 포함됩니다. 설정은 메모리에만 존재하므로 변수에 저장해야 합니다. 이 경우에는 $x라는 변수입니다.

이 예제의 둘째 명령과 셋째 명령은 이러한 가상 구성 설정을 가져오고 EnableGroupExpansion 및 UseCertificateAuth 속성의 값을 수정합니다. 이러한 변경이 완료되면 마지막 명령이 **Set-CsWebServiceConfiguration** cmdlet을 사용하여 가상 설정을 가져와 Redmond 사이트에 적용합니다. **Set-CsWebServiceConfiguration** cmdlet을 호출하지 않으면 사이트에 새 설정이 할당되지 않습니다. 대신, Windows PowerShell 세션을 종료하거나 변수 $x를 삭제하는 즉시 가상 웹 서비스 구성 설정이 사라집니다.

    $x = New-CsWebServiceConfiguration -Identity site:Redmond -InMemory
    $x.EnableGroupExpansion = $False 
    $x.UseCertificateAuth = $True
    Set-CsWebServiceConfiguration -Instance $x

## 예제 3

예제 3에 나와 있는 명령은 Redmond 사이트에 대해 만드는 새로운 웹 서비스 구성 설정 모음용으로 권한이 부여된 도메인 목록에 http://fabrikam.com 도메인을 추가합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsWebOrigin** cmdlet을 사용하여 fabrikam.com에 대한 도메인 개체를 만듭니다. 그러면 생성되는 도메인 개체는 $x라는 변수에 저장됩니다.

예제의 두 번째 명령은 **New-CsWebServiceConfiguration** cmdlet을 사용하여 Redmond 사이트에 대해 웹 서비스 구성 설정을 만듭니다. ? CrossDomainAuthorizationList $x 구문은 도메인 간 스크립팅 권한이 부여된 도메인 모음에 http://fabrikam.com을 추가합니다.

    $x = New-CsWebOrigin -Url "http://fabrikam.com"
    New-CsWebServiceConfiguration -Identity "site:Redmond" - CrossDomainAuthorizationList $x

## 예제 4

예제 4에서는 권한이 부여된 여러 도메인을 새 웹 서비스 구성 설정 모음에 추가하는 방법을 보여 줍니다. 여러 도메인을 추가하려면 각 도메인을 별도의 변수에 저장하는 여러 도메인 개체를 만들어야 합니다. 예제 4에서 http://fabrikam.com에 대한 도메인 개체는 $x 변수에 저장되고 http://contoso.com에 대한 도메인 개체는 $y 변수에 저장됩니다.

모든 도메인 개체를 만든 후에는 각 변수 이름을 CrossDomainAuthorizationList 매개 변수의 매개 변수 값에 추가하기만 하면 됩니다. 예를 들면 다음과 같습니다.

–CrossDomainAuthorizationList $x, $y

    $x = New-CsWebOrigin -Url "http://fabrikam.com"
    $y = New-CsWebOrigin -Url "http://contoso.com"
    New-CsWebServiceConfiguration -Identity "site:Redmond" - CrossDomainAuthorizationList $x, $y

## 자세한 정보

여러 Lync Server 구성 요소는 웹 기반 구성 요소이며, 이러한 구성 요소에는 작업 수행을 위해 웹 서비스 또는 웹 페이지가 사용됩니다. 예를 들어, 사용자는 주소록에서 새 연락처를 검색하거나 그룹 확장을 사용하여 메일 그룹의 개별 멤버를 보는 경우 웹 서비스를 사용합니다. 마찬가지로 전화 접속 회의부터 Lync Server에 이르는 구성 요소는 Lync Server와 사용자 간의 인터페이스로 웹 페이지를 사용합니다.

**CsWebServiceConfiguration** cmdlet을 사용하면 관리자가 조직 전체의 웹 서비스 구성 설정을 관리할 수 있습니다. 여기에는 그룹 확장, 인증서 설정 및 허용되는 인증 방법 관리가 포함됩니다. 전역, 사이트 및 서비스(웹 서비스에만 해당) 범위에 여러 설정을 구성할 수 있으므로 다양한 사용자 및 위치에 대해 웹 서비스 기능을 사용자 지정할 수 있습니다.

새 웹 서비스 구성 설정은 **New-CsWebServiceConfiguration** cmdlet을 사용하여 만듭니다. 이러한 설정은 사이트 또는 서비스 범위(웹 서비스에만 해당)에서만 만들 수 있으며 전역 범위에 새 컬렉션을 만들려고 하면 명령이 실패하게 됩니다. 마찬가지로 레드몬드 사이트 등에 새 컬렉션을 만들려고 할 때 해당 사이트가 웹 서비스 설정 컬렉션을 이미 호스트하는 경우 명령이 실패하게 됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsWebServiceConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsWebServiceConfiguration"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>만들려는 웹 서비스 구성 설정의 고유 식별자입니다. 사이트 범위에 구성된 설정을 만들려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. 서비스 범위에 구성된 설정을 만들려면 -Identity &quot;service:WebServer:atl-cs-001.litwareinc.com&quot;과 유사한 구문을 사용합니다. 서비스 범위에 만든 모든 설정은 웹 서버 서비스에 할당해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowAnonymousAccessToLWAConference</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 익명 사용자가 Lync Web App 회의에 참가할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowExternalAuthentication</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 OAuth 인증을 사용하여 외부 사용자를 인증할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AutoLaunchLyncWebAccess</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 매개 변수는 온-프레미스 버전의 Lync Server 2013에서는 더 이상 사용되지 않습니다.</p>
<p>True로 설정하면 온라인 전화 회의에 참가하기 위한 기본 웹 팝업으로 Lync Web App을 자동으로 사용합니다. 단, Lync Web App 사용을 위한 필수 구성 요소(예: Silverlight가 설치되었으며 Internet Explorer에서 팝업 창을 차단하지 않음)가 충족되어야 합니다.</p>
<p>기본값은 True입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>CASigningKeyLength</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt64</p></td>
<td><p>CA(인증 기관)가 디지털 인증서에 서명하는 데 사용한 개인 키인 CA 서명 키의 크기를 설정합니다. 서명 키 길이는 2048-16384바이트 사이의 임의 정수 값으로 설정할 수 있으며 기본값은 2048입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>CrossDomainAuthorizationList</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>Lync Server 2013 배포로 도메인 간 스크립팅 요청을 보내는 웹 응용 프로그램을 호스트하도록 허용되는 도메인 모음입니다.</p>
<p>목록에 추가할 도메인은 New-CsWebOrigin cmdlet을 사용하여 만든 후에 새 웹 서비스 구성 설정 모음에 추가해야 합니다. 또한 도메인 이름에는 http: 또는 https: 접두사를 붙여야 합니다. 자세한 내용은 이 도움말 항목의 예제 3을 참조하십시오.</p>
<p>이 매개 변수는 Lync Server 2013의 2013년 2월 릴리스에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DefaultValidityPeriodHours</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt64</p></td>
<td><p>인증서 인증을 사용할 때 클라이언트는 인증서의 유효 기간(시간)을 요청할 수 있습니다. DefaultValidityPeriodHours는 클라이언트가 사용자 지정 유효 기간을 요청하지 않는 경우 인증서의 유효 시간을 나타냅니다.</p>
<p>DefaultValidityPeriodHours는 8-8760시간(365일) 사이의 임의 정수 값이 될 수 있습니다. 기본값은 4320(180일)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableCertChainDownload</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정되면 사용자가 인증 인증서를 제공한 서버가 해당 인증서의 인증서 체인을 다운로드하게 됩니다. 인증서 체인은 개별 인증서의 발급 CA를 추적합니다. 인증서의 CA를 신뢰할 수 있어야 인증서로 인증할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableGroupExpansion</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정된 경우 Lync Server에서 그룹 확장을 사용할 수 없게 됩니다. 그룹 확장을 사용하면 사용자가 메일 그룹을 연락처로 구성한 다음 해당 그룹을 &quot;확장&quot;할 수 있습니다. 그룹이 확장되면 사용자가 그룹의 모든 개별 구성원과 현재 상태 정보를 볼 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InferCertChainFromSSL</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정된 경우 서버가 SSL(Secure Sockets Layer) 프로토콜에 포함된 인증서 정보를 사용하여 발급 CA를 확인합니다. 인증서의 CA를 신뢰할 수 있어야 인증서로 인증할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
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
<td><p>CSR(인증서 서명 요청) 키의 최대 크기를 설정합니다. CSR은 신청자가 디지털 인증서를 신청하기 위해 CA에 보낸 메시지입니다. 최대 크기는 1024-16384바이트 사이의 임의 정수 값으로 설정할 수 있습니다. 기본값은 16384입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxGroupSizeToExpand</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>그룹을 확장할 때 표시되는 최대 구성원 수를 나타냅니다. 예를 들어 MaxGroupSizeToExpand가 75로 설정된 경우 그룹을 확장할 때마다 그룹의 처음 75명 구성원만 표시됩니다.</p>
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
<td><p>CSR 키의 최대 크기를 설정합니다. 최소 크기는 1024-16384바이트 사이의 임의 정수 값으로 설정할 수 있습니다. 기본값은 16384입니다.</p></td>
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
<td><p>위치 요청을 처리할 수 있는 웹 서비스의 URL입니다. 이 서비스는 일반적으로 위치 요청을 로컬에서 확인할 수 없는 경우에만 사용됩니다.</p></td>
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
<p>True(기본값)로 설정하면 Lync 이외의 클라이언트 응용 프로그램을 사용하여 온라인 모임에 참가하는 사용자에게 Lync Web App을 다운로드할 수 있는 링크가 표시됩니다.</p></td>
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
<td><p>True(기본값)로 설정할 경우 클라이언트가 인증서를 사용하여 인증될 수 있습니다. 인증서 인증을 사용하지 않도록 설정하려면 이 값을 False($False)로 설정합니다.</p></td>
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
<td><p>True(기본값)로 설정하면 클라이언트가 개인식별번호(PIN)을 사용하여 인증할 수 있습니다. PIN 인증을 사용하지 않도록 설정하려면 이 값을 False($False)로 설정합니다.</p></td>
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

없음. **New-CsWebServiceConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsWebServiceConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Web.WebServiceSettings 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsWebServiceConfiguration](get-cswebserviceconfiguration.md)  
[Remove-CsWebServiceConfiguration](remove-cswebserviceconfiguration.md)  
[Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)

