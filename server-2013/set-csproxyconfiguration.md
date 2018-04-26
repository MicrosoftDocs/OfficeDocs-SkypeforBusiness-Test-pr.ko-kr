---
title: Set-CsProxyConfiguration
TOCTitle: Set-CsProxyConfiguration
ms:assetid: 2eb74d25-05b5-4901-aa92-eeda2f351e25
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425796(v=OCS.15)
ms:contentKeyID: 49303184
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsProxyConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 프록시 서버 구성 설정 컬렉션을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsProxyConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsProxyConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AcceptClientCompression <$true | $false>] [-AcceptServerCompression <$true | $false>] [-AllowPartnerPollingSubscribes <$true | $false>] [-Confirm [<SwitchParameter>]] [-DisableNtlmFor2010AndLaterClients <$true | $false>] [-DnsCacheRecordCount <UInt32>] [-EnableLoggingAllMessageBodies <$true | $false>] [-EnableWhiteSpaceKeepAlive <$true | $false>] [-Force <SwitchParameter>] [-LoadBalanceEdgeServers <$true | $false>] [-LoadBalanceInternalServers <$true | $false>] [-MaxClientCompressionCount <UInt32>] [-MaxClientMessageBodySizeKb <UInt32>] [-MaxKeepAliveInterval <UInt32>] [-MaxServerCompressionCount <UInt32>] [-MaxServerMessageBodySizeKb <UInt32>] [-OutgoingTlsCount <UInt32>] [-Realm <IRealmChoice>] [-RequestServerCompression <$true | $false>] [-TreatAllClientsAsRemote <$true | $false>] [-UseCertificateForClientToProxyAuth <$true | $false>] [-UseKerberosForClientToProxyAuth <$true | $false>] [-UseNtlmForClientToProxyAuth <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 service:EdgeServer:atl-edge-001.litwareinc.com인 모든 프록시 구성 설정을 서버 압축을 허용하도록 수정합니다. 이 작업을 수행하기 위해 **Set-CsProxyConfiguration** cmdlet 및 AcceptServerCompression 매개 변수를 호출하고 매개 변수 값을 True로 설정합니다.

    Set-CsProxyConfiguration -Identity service:EdgeServer:atl-edge-001.litwareinc.com -AcceptServerCompression $True

## 예제 2

예제 2에서는 서버 압축을 허용하는 모든 프록시 구성 설정을 찾은 다음 클라이언트 압축도 허용하도록 이러한 설정을 수정합니다. 먼저 조직에서 사용 중인 모든 프록시 설정 컬렉션을 반환하기 위해 **Get-CsProxyConfiguration** cmdlet이 매개 변수 없이 호출됩니다. 이 컬렉션은 AcceptServerCompression 속성이 True와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목에 대해 AcceptClientCompression 속성을 True로 설정하는 **Set-CsProxyConfiguration** cmdlet에 파이프됩니다.

    Get-CsProxyConfiguration | Where-Object {$_.AcceptServerCompression -eq $True} | Set-CsProxyConfiguration -AcceptClientCompression $True

## 예제 3

예제 3에서는 서비스 범위에서 구성된 모든 프록시 설정을 수정하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 이 명령은 먼저 Filter 매개 변수를 사용하여 **Get-CsProxyConfiguration** cmdlet을 호출합니다. 필터 값 "service:\*"는 Identity가 문자열 값 "service:"으로 시작하는 설정만 반환되도록 합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목에 대해 UseNtlmForClientToProxyAuth 속성을 False로 설정하는 **Set-CsProxyConfiguration** cmdlet에 파이프됩니다.

    Get-CsProxyConfiguration -Filter service:* | Set-CsProxyConfiguration -UseNtlmForClientToProxyAuth $False

## 자세한 정보

Lync Server에서는 프록시 서버 구성 설정을 통해 프록시 서버를 관리할 수 있습니다. 전역 범위 및 서비스 범위( 에지 서버 및 등록자 서비스에만 해당)에서 적용할 수 있는 이러한 설정을 통해 클라이언트 끝점에서 사용할 수 있는 인증 프로토콜, 보내고 받는 프록시 서버 연결에 압축을 사용할지 여부 등을 제어할 수 있습니다. Lync Server를 설치하면 전역 프록시 서버 구성 설정 컬렉션이 자동으로 만들어집니다. 앞서 언급했듯이 서비스 범위에 추가 컬렉션을 만들 수도 있습니다.

**Set-CsProxyConfiguration** cmdlet을 사용하면 기존 프록시 서버 구성 설정 컬렉션의 속성 값을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsProxyConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsProxyConfiguration"}

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
<td><p><em>AcceptClientCompression</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정된 경우 프록시 서버가 클라이언트 끝점에서 오는 모든 압축 요청을 허용하게 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AcceptServerCompression</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정된 경우 프록시 서버가 다른 서버에서 오는 모든 압축 요청을 허용하게 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowPartnerPollingSubscribes</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 파트너 응용 프로그램이 정기적으로 서비스를 폴링하여 상태 변경 내용을 확인할 수 있습니다. 기본값은 False($False)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisableNtlmFor2010AndLaterClients</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정된 경우 Lync에서 로그온하는 사용자가 Kerberos 프로토콜을 사용하여 인증해야 합니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DnsCacheRecordCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>DNS 레코드 캐시에 유지할 수 있는 최대 레코드 수입니다. 기본값은 3000입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableLoggingAllMessageBodies</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync Server에서 모든 메신저 대화의 실제 내용을 기록합니다. 개인 정보 보호를 위해 메시지 내용은 대개 삭제되며 통신 끝점에 대한 정보만 로그 파일에 포함됩니다.</p>
<p>기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableWhiteSpaceKeepAlive</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 프록시 서버에서 클라이언트가 연결이 활성 상태임을 표시하기 위해 주기적으로 &quot;공백 메시지&quot;(내용이 없는 빈 메시지)를 보낼 것으로 예상합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 프록시 서버 구성 설정의 고유 식별자입니다. 전역 설정을 수정하려면 -Identity global 구문을 사용합니다. 서비스 범위에서 구성된 설정을 수정하려면 -Identity &quot;service: EdgeServer:atl-edge-001.litwareinc.com&quot;과 유사한 구문을 사용합니다.</p>
<p>이 매개 변수를 포함하지 않으면 <strong>Set-CsProxyConfiguration</strong> cmdlet에서 자동으로 전역 설정을 수정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>ProxySettings 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LoadBalanceEdgeServers</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True인 경우 에지 서버에 대한 요청에 소프트웨어 부하 분산이 적용됩니다. 기본값은 True($True)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LoadBalanceInternalServers</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True인 경우 등록자 및 기타 내부 서버에 대한 요청에 소프트웨어 부하 분산이 적용됩니다. 기본값은 True($True)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxClientCompressionCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>지정된 시간에 압축할 수 있는 클라이언트-서버 연결의 최대 수를 나타냅니다. 이 제한을 초과하면 연결이 더 이상 압축되지 않습니다. 압축 수는 0-65535(포함) 사이의 임의 정수 값으로 설정할 수 있습니다. 기본값은 15000입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxClientMessageBodySizeKb</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>클라이언트 끝점에서 보내는 메시지 본문의 최대 허용 크기(킬로바이트)입니다. 기본값은 128입니다. 이는 본문 크기가 128KB보다 큰 메시지는 거부됨을 의미합니다. 클라이언트 메시지 본문 크기는 64-256(포함) 사이의 임의 정수 값으로 설정할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxKeepAliveInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>서버에서 클라이언트와의 연결이 아직 유효한지를 확인할 때까지 경과할 수 있는 시간을 분 단위로 지정합니다. 기본값은 20분입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxServerCompressionCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>지정된 시간에 압축할 수 있는 서버-서버 연결의 최대 수를 나타냅니다. 이 제한을 초과하면 연결이 더 이상 압축되지 않습니다. 서버 압축 수는 0-65535(포함) 사이의 임의 정수 값으로 설정할 수 있습니다. 기본값은 1024입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxServerMessageBodySizeKb</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>다른 서버에서 보내는 메시지 본문의 최대 허용 크기(킬로바이트)입니다. 기본값은 5000이며 이는 본문 크기가 5000KB보다 큰 메시지가 거부됨을 의미합니다. 서버 메시지 본문 크기는 1000-20000(포함) 사이의 임의 정수 값으로 설정할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>OutgoingTlsCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>각 내부 서버에 사용할 수 있는 최대 TLS(전송 계층 보안) 연결 수를 지정합니다. 최소 TLS 연결 수는 1이고 최대 수는 4입니다. 기본적으로 OutgoingTlsCount는 4로 설정됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Realm</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.IRealmChoice</p></td>
<td><p>보안 자격 증명이 기본 프록시 서버 영역(SIP 통신 서비스)에서 처리되는지, 아니면 사용자 지정 영역에서 처리되는지를 나타냅니다. <strong>New-CsSipProxyCustom</strong> cmdlet을 사용하여 사용자 지정 영역을 지정하고 만들어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RequestServerCompression</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정된 경우 프록시 서버에서 다른 서버로 나가는 모든 연결에 압축을 사용하도록 요청합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TreatAllClientsAsRemote</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정된 경우 모든 클라이언트 연결이 에지 서버를 통과하는 외부 연결인 것처럼 프록시 서버가 작동합니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UseCertificateForClientToProxyAuth</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정된 경우 클라이언트 끝점에서 인증에 인증서를 사용할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UseKerberosForClientToProxyAuth</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정된 경우 클라이언트 끝점에서 인증에 Kerberos 프로토콜을 사용할 수 있습니다. Kerberos는 NTLM보다 더 안전한 프로토콜이지만 클라이언트가 서버와 다른 영역에 속하는 경우에는 사용할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UseNtlmForClientToProxyAuth</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 클라이언트 끝점에서 인증을 위해 NTLM 프로토콜을 사용할 수 있습니다. NTLM은 Kerberos보다 안전하지 않은 프로토콜이지만 클라이언트가 서버와 서로 다른 도메인에 속해 있는 경우에 사용할 수 있습니다. 이는 Kerberos 인증에는 해당되지 않습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.ProxySettings 개체입니다. **Set-CsProxyConfiguration** cmdlet은 프록시 설정 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsProxyConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.ProxySettings 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsProxyConfiguration](get-csproxyconfiguration.md)  
[New-CsProxyConfiguration](new-csproxyconfiguration.md)  
[Remove-CsProxyConfiguration](remove-csproxyconfiguration.md)

