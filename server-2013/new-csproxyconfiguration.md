---
title: New-CsProxyConfiguration
TOCTitle: New-CsProxyConfiguration
ms:assetid: 5133470e-1d77-4958-8844-a091336b2a3c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398335(v=OCS.15)
ms:contentKeyID: 49303630
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsProxyConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

프록시 구성 설정의 새 컬렉션을 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsProxyConfiguration -Identity <XdsIdentity> [-AcceptClientCompression <$true | $false>] [-AcceptServerCompression <$true | $false>] [-AllowPartnerPollingSubscribes <$true | $false>] [-Confirm [<SwitchParameter>]] [-DisableNtlmFor2010AndLaterClients <$true | $false>] [-DnsCacheRecordCount <UInt32>] [-EnableLoggingAllMessageBodies <$true | $false>] [-EnableWhiteSpaceKeepAlive <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-LoadBalanceEdgeServers <$true | $false>] [-LoadBalanceInternalServers <$true | $false>] [-MaxClientCompressionCount <UInt32>] [-MaxClientMessageBodySizeKb <UInt32>] [-MaxKeepAliveInterval <UInt32>] [-MaxServerCompressionCount <UInt32>] [-MaxServerMessageBodySizeKb <UInt32>] [-OutgoingTlsCount <UInt32>] [-Realm <IRealmChoice>] [-RequestServerCompression <$true | $false>] [-TreatAllClientsAsRemote <$true | $false>] [-UseCertificateForClientToProxyAuth <$true | $false>] [-UseKerberosForClientToProxyAuth <$true | $false>] [-UseNtlmForClientToProxyAuth <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 EdgeServer:atl-edge-001.litwareinc.com 서비스의 새 프록시 구성 설정 컬렉션을 만듭니다. 이러한 새 설정은 모든 기본 프록시 서버 속성 값을 사용합니다. 단, True로 설정된 RequestServerCompression 및 256으로 설정된 MaxClientMessageBodySizeKb는 예외입니다. EdgeServer:atl-edge-001.litwareinc.com 서비스에 대해 프록시 서버 설정이 이미 구성되어 있는 경우 이 명령이 실패합니다.

    New-CsProxyConfiguration -Identity "service:EdgeServer:atl-edge-001.litwareinc.com" -RequestServerCompression $True -MaxClientMessageBodySizeKb 256

## 예제 2

예제 2에 표시된 명령은 처음에 메모리에만 있는 프록시 서버 설정 컬렉션을 만드는 방법을 보여 줍니다. 이 작업을 수행하기 위해 첫 번째 명령은 두 매개 변수와 함께 **New-CsProxyConfiguration** cmdlet을 호출합니다. 하나는 설정의 ID를 지정하는 Identity 매개 변수이고 다른 하나는 새 설정을 메모리에만 만들도록 지정하는 InMemory 매개 변수입니다. 만들어진 개체는 변수 $x에 저장됩니다.

이러한 가상 설정이 만들어진 후에는 두 번째와 세 번째 명령을 사용하여 RequestServerCompression 속성 및 MaxClientMessageBodySizeKb 속성의 값을 각각 수정합니다. 마지막으로 네 번째 명령을 사용하여 가상 프록시 서버 구성 설정을 EdgeServer:atl-edge-001.litwareinc.com 서비스에 적용되는 실제 설정 컬렉션으로 변환합니다. 이 마지막 명령은 필수입니다. **Set-CsProxyConfiguration** cmdlet을 호출하지 않으면 EdgeServer:atl-edge-001.litwareinc.com에 아무런 설정이 적용되지 않으며 Windows PowerShell 세션을 종료하거나 변수 $x를 삭제하는 즉시 가상 설정이 사라집니다.

    $x = New-CsProxyConfiguration -Identity "service:EdgeServer:atl-edge-001.litwareinc.com" -InMemory
    $x.RequestServerCompression = $True 
    $x.MaxClientMessageBodySizeKb = 256
    Set-CsProxyConfiguration -Instance $x

## 자세한 정보

Lync Server를 사용하여 프록시 서버 구성 설정을 통해 프록시 서버를 관리할 수 있습니다. 전역 범위 및 서비스 범위( 에지 서버 및 등록자 서비스에만 해당)에서 적용할 수 있는 이러한 설정을 통해 클라이언트 끝점에서 사용할 수 있는 인증 프로토콜, 보내고 받는 프록시 서버 연결에 압축을 사용할지 여부 등을 제어할 수 있습니다. Lync Server를 설치하면 전역 프록시 서버 구성 설정 컬렉션이 자동으로 만들어집니다. 앞서 언급한 대로 서비스 범위에 추가 컬렉션을 만들 수도 있습니다. 이러한 새 컬렉션은 **New-CsProxyConfiguration** cmdlet을 사용하여 만듭니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsProxyConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsProxyConfiguration"}

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
<td><p>만들 프록시 서버 구성 설정의 고유한 식별자입니다. 프록시 서버 구성 설정은 서비스 범위에만 만들 수 있으며 에지 서버 및 등록자 서비스로 제한됩니다. 해당 서비스가 프록시 서버 설정의 컬렉션을 이미 호스트하는 경우 전역 범위에 설정을 만들 수 없으며, 마찬가지로 서비스 범위에도 설정을 만들 수 없습니다. 예를 들어 Registrar:atl-cs-001.litwareinc.com 서비스가 이미 프록시 서버 설정을 호스트하는 경우 해당 서비스의 새 설정을 만드는 모든 명령이 실패하게 됩니다.</p>
<p>새 프록시 서버 설정의 ID를 지정하려면 -Identity &quot;service:Registrar:atl-cs-001.litwareinc.com&quot;과 같은 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AcceptClientCompression</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정된 경우 프록시 서버가 클라이언트 끝점에서 오는 모든 압축 요청을 허용하게 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AcceptServerCompression</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정된 경우 프록시 서버가 다른 서버에서 오는 모든 압축 요청을 허용하게 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowPartnerPollingSubscribes</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 파트너 응용 프로그램이 정기적으로 서비스를 폴링하여 상태 변경 내용을 확인할 수 있습니다. 기본값은 False($False)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisableNtlmFor2010AndLaterClients</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정된 경우 Lync에서 로그온하는 사용자가 Kerberos 프로토콜을 사용하여 인증해야 합니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DnsCacheRecordCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>DNS 레코드 캐시에 유지할 수 있는 최대 레코드 수입니다. 기본값은 3000입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableLoggingAllMessageBodies</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Microsoft Lync Server에서 모든 메신저 대화의 실제 내용을 기록합니다. 개인 정보 보호를 위해 메시지 내용은 대개 삭제되며 통신 끝점에 대한 정보만 로그 파일에 포함됩니다.</p>
<p>기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableWhiteSpaceKeepAlive</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 프록시 서버에서 클라이언트가 연결이 활성 상태임을 표시하기 위해 정기적으로 &quot;공백&quot; 메시지(내용이 없는 빈 메시지)를 보낼 것으로 예상합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
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
<td><p>보안 자격 증명을 기본 프록시 서버 영역(SIP 통신 서비스) 또는 사용자 지정 영역 중 어디에서 처리할지 지정합니다. 사용자 지정 영역은 <strong>New-CsSipProxyCustom</strong> cmdlet을 사용하여 지정하고 만들어야 합니다.</p></td>
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
<td><p>True로 설정된 경우 모든 클라이언트 연결이 액세스 에지 서비스를 실행하는 에지 서버를 통과하는 외부 연결인 것처럼 프록시 서버가 작동합니다. 기본값은 False입니다.</p></td>
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
<td><p>True(기본값)로 설정된 경우 클라이언트 끝점에서 인증에 NTLM 프로토콜을 사용할 수 있습니다. NTLM은 Kerberos보다 덜 안전한 프로토콜이지만 클라이언트가 서버와 다른 도메인에 속하는 경우 NTLM을 사용할 수 있습니다. Kerberos 인증은 사용할 수 없습니다.</p></td>
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

없음. **New-CsProxyConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsProxyConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.ProxySettings 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsProxyConfiguration](get-csproxyconfiguration.md)  
[Remove-CsProxyConfiguration](remove-csproxyconfiguration.md)  
[Set-CsProxyConfiguration](set-csproxyconfiguration.md)

