---
title: New-CsStaticRoute
TOCTitle: New-CsStaticRoute
ms:assetid: 1df0c537-f24f-4a63-be6d-70d016f985a5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398265(v=OCS.15)
ms:contentKeyID: 49302995
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsStaticRoute

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 고정 전화 경로를 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsStaticRoute -Destination <String> -MatchUri <String> -Port <UInt16> -TLSRoute <SwitchParameter> [-Enabled <$true | $false>] [-MatchOnlyPhoneUri <$true | $false>] [-ReplaceHostInRequestUri <$true | $false>] [-TLSCertIssuer <String>] [-TLSCertSerialNumber <Byte[]>] [-UseDefaultCertificate <$true | $false>] <COMMON PARAMETERS>

    New-CsStaticRoute -Destination <String> -MatchUri <String> -Port <UInt16> -TCPRoute <SwitchParameter> [-Enabled <$true | $false>] [-MatchOnlyPhoneUri <$true | $false>] [-ReplaceHostInRequestUri <$true | $false>] <COMMON PARAMETERS>

    COMMON PARAMETERS:

## 예제

## 예제 1

예제 1에 표시된 명령은 새 고정 경로를 만든 다음 전역 고정 경로 지정 구성 컬렉션에 해당 경로를 추가합니다. 이 작업을 수행하기 위해 첫 번째 명령은 **New-CsStaticRoute** cmdlet을 사용하여 TCP를 전송 프로토콜로 사용하는 메모리 전용 경로를 만듭니다. 이 경로는 다음 홉 IP 주소인 192.168.0.100을 가리키고, 포트 8025를 사용하며, litwareinc.com 도메인의 모든 URI와 일치합니다. 결과 경로 개체는 변수 $x에 저장됩니다.

예제의 두 번째 명령은 전역 고정 경로 지정 구성 컬렉션에 새 경로를 추가합니다. 이 작업을 수행하기 위해 **Set-CsStaticRoutingConfiguration** cmdlet을 Route 매개 변수와 함께 호출합니다. 매개 변수 값 @{Add=$x}는 $x에 저장된 경로 개체가 이미 전역 컬렉션에 있는 기존 경로 집합에 추가합니다.

    $x = New-CsStaticRoute -TCPRoute -Destination "192.168.0.100" -Port 8025 -MatchUri "litwareinc.com" 
    
    Set-CsStaticRoutingConfiguration -Identity global -Route @{Add=$x}

## 예제 2

예제 2에서는 TLS를 전송 프로토콜로 사용하는 새 고정 경로를 만든 다음 전역 고정 경로 지정 구성 컬렉션에 해당 경로를 추가하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsStaticRoute** cmdlet을 사용하여 TLS를 전송 프로토콜로 사용하는 메모리 전용 경로를 만듭니다. 이 경로는 "atl-proxy-001.litwareinc.com"을 해당 대상으로 가리키고, 포트 8025를 사용하며, 도메인 접미사 "litwareinc.com"을 사용하는 URI를 일치시킵니다. 또한 변수 $x에 저장된 새 경로 개체는 기본 인증서를 인증에 사용합니다(-UseDefaultCertificate $True).

경로 개체가 만들어진 후 예제의 두 번째 명령은 전역 고정 경로 지정 구성 컬렉션에 새 경로를 추가합니다.

    $x = New-CsStaticRoute -TLSRoute -Destination "atl-proxy-001.litwareinc.com" -Port 8025 -MatchUri "*.litwareinc.com" -UseDefaultCertificate $True
    
    Set-CsStaticRoutingConfiguration -Identity global -Route @{Add=$x}

## 예제 3

예제 3에서는 TLS 및 특정 인증서를 사용하여 새 고정 경로를 만듭니다. 이 경로는 필수 TLS 매개 변수를 포함하는 것으로 표시됩니다.

경로 개체가 만들어진 후 예제의 두 번째 명령은 전역 고정 경로 지정 구성 컬렉션에 새 경로를 추가합니다.

    $x = New-CsStaticRoute -TLSRoute -Destination "atl-proxy.litwareinc.com" -Port 5061 -MatchUri "litwareinc.com" -UseDefaultCertificate $False -TLSCertIssuer "CN=CertificateAuthority, DC=litwareinc, DC=com" -TLSCertSerialNumber 0x8f,0x33,0x70,0x93,0x70,0x05,0x33,0x00,0x02,0x33
    
    Set-CsStaticRoutingConfiguration -Identity global -Route @{Add=$x}

## 자세한 정보

SIP 메시지를 누군가에게 보내는 경우 이 메시지는 배달되기 전에 여러 서브넷과 네트워크를 통과해야 할 수 있습니다. 메시지가 거치는 이러한 길을 일반적으로 경로라고 합니다. 네트워킹에는 동적 경로와 고정 경로의 두 가지 유형의 경로가 있습니다. 동적 경로는 서버가 알고리즘을 사용하여 메시지를 전달해야 할 다음 위치(다음 홉)를 결정합니다. 고정 경로의 경우 메시지 경로는 시스템 관리자에 의해 미리 결정됩니다. 메시지가 서버에 수신되면 서버는 메시지 주소를 확인한 다음 관리자가 미리 구성한 다음 홉 서버로 메시지를 전달합니다. 고정 경로를 제대로 구성한 경우에는 제시간에 정확하게 메시지를 전달하고 서버에 대한 오버헤드를 최소화할 수 있습니다. 고정 경로의 단점은 네트워크 실패 시 메시지가 동적으로 다시 경로 지정되지 않는다는 것입니다.

새 고정 경로는 **New-CsStaticRoute** cmdlet을 사용하여 만듭니다. **New-CsStaticRoute** cmdlet을 사용하여 경로를 만든 후에는 **Set-CsStaticRoutingConfiguration** cmdlet을 사용하여 경로 지정 구성 설정 컬렉션에 경로를 추가해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsStaticRoute** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsStaticRoute"}

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
<td><p><em>Destination</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>경로에서 TLS(전송 계층 보안)를 전송 프로토콜로 사용하는 경우 Destination은 다음 홉 서버의 FQDN(정규화된 도메인 이름)입니다. 예: -Destination &quot;atl-proxy-001.litwareinc.com&quot;</p>
<p>경로에서 TCP(Transmission Control Protocol)를 전송 프로토콜로 사용하는 경우 Destination은 다음 홉 라우터의 IP 주소입니다. 예: -Destination &quot;192.168.0.240&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>MatchUri</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 경로에서 처리된 메시지를 사용자에게 보낼지 여부를 결정하는 데 사용되는 FQDN 또는 도메인 접미사입니다. 예를 들어 FQDN &quot;litwareinc.com&quot;을 사용할 수 있습니다. 이 패턴은 SIP 주소가 도메인 이름 &quot;litwareinc.com&quot;으로 끝나는 모든 사용자와 일치합니다.</p>
<p>도메인의 자식 도메인을 일치시키려면 &quot;*.litwareinc.com&quot;과 같이 와일드카드 값을 사용할 수 있습니다. 해당 값은 &quot;litwareinc.com&quot; 접미사로 끝나는 모든 도메인과 일치합니다. 예: northamerica.litwareinc.com, asia.litwareinc.com, europe.litwareinc.com 등</p></td>
</tr>
<tr class="odd">
<td><p><em>Port</em></p></td>
<td><p>필수</p></td>
<td><p>System.UInt16</p></td>
<td><p>SIP 경로 지정에 사용되는 포트 번호입니다. 예: -Port 7742.</p></td>
</tr>
<tr class="even">
<td><p><em>TCPRoute</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>TCP(Transmission Control Protocol)를 새 경로의 전송 프로토콜로 구성합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TLSRoute</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>TLS를 새 경로의 전송 프로토콜로 구성합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 경로가 활성화되고, MatchURI 패턴과 일치하는 모든 메시지가 다음 홉 서버로 경로 지정됩니다. False로 설정하면 경로가 비활성화되고 메시지 경로 지정에 사용되지 않습니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MatchOnlyPhoneUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 전화 URI(Uniform Resource identifier)로 보내는 메시지(예: sip:kenmmyer@litwareinc.com;user=phone)만 일치되고 경로 지정될 수 있습니다. False(기본값)로 설정하면 모든 메시지가 일치됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ReplaceHostInRequestUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True($True)로 설정하면 Request-URI의 호스트 부분이 다음 홉 서버의 주소로 바뀝니다. False(기본값)를 설정하면 Request-URI가 있는 그대로 사용됩니다. Request-URI는 요청(메시지)이 보내지는 사용자 또는 서비스의 URI를 나타냅니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TLSCertIssuer</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>고정 경로에서 사용할 인증서를 발급한 CA(인증 기관)의 이름입니다. TCP를 전송 프로토콜로 구성한 경우에는 이 매개 변수가 사용되지 않습니다.</p>
<p>TLSCertIssuer 매개 변수를 포함하는 경우 TLSCertSerialNumber 매개 변수도 사용해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TLSCertSerialNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.Byte[]</p></td>
<td><p>고정 경로에서 사용할 TLS 인증서의 일련 번호입니다. 일련 번호는 바이트 배열로 전달되어야 합니다. 즉, 두 문자로 이루어진 값의 배열로 일련 번호를 전달해야 합니다. 예: -TLSCertSerialNumber 0x01, 0xA4, 0xD5, 0x67, 0x89</p>
<p>TCP를 전송 프로토콜로 구성한 경우에는 이 매개 변수가 사용되지 않습니다.</p>
<p>TLSCertSerialNumber 매개 변수를 포함하는 경우 TLSCertIssuer 매개 변수도 사용해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UseDefaultCertificate</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>기본 Lync Server 인증서를 인증 인증서로 사용하도록 경로를 구성합니다. 기본 인증서를 사용하지 않으려면 TLSCertIssuer 및 TLSCertSerialNumber 매개 변수를 사용하여 다른 인증서를 지정해야 합니다.</p>
<p>기본 인증서를 보려면 다음 명령을 사용합니다.</p>
<p>Get-CsCertificate | Where-Object {$_.Use –eq &quot;urn:certref:Default&quot;}</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsStaticRoute** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsStaticRoute** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.Route 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsStaticRoutingConfiguration](new-csstaticroutingconfiguration.md)  
[Set-CsStaticRoutingConfiguration](set-csstaticroutingconfiguration.md)

