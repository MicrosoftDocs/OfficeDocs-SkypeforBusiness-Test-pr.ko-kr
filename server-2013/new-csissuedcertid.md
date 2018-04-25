---
title: New-CsIssuedCertId
TOCTitle: New-CsIssuedCertId
ms:assetid: 3158e26e-3fda-488b-a08d-5481e1abfc1d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425814(v=OCS.15)
ms:contentKeyID: 49303228
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsIssuedCertId

 

_**마지막으로 수정된 항목:** 2015-03-09_

SipProxy.TLS 개체에 기존 인증서를 할당하는 데 사용됩니다. 그런 다음 이 개체를 사용하여 TLS(Transport Layer Security)를 전송 프로토콜로 사용하는 고정 경로를 구성할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsIssuedCertId -Issuer <String> -SerialNumber <Byte[]>

## 예제

## 예제 1

예제 1에 표시된 명령은 새 인증서 ID 개체를 만든 다음 해당 인증서를 SipProxy.TLS 개체에 할당합니다. 그러면 해당 개체를 사용하여 TLS 전송 프로토콜을 사용하도록 고정 경로를 구성할 수 있습니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsIssuedCertId**를 사용하여 Fabrikam에서 발급하였고 일련 번호가 10143A1A인 인증서의 인증서 ID 개체를 만듭니다. 일련 번호는 2문자 문자열 배열로 지정됩니다. 결과 개체는 $cert 변수에 저장됩니다.

두 번째 명령에서는 New-CsSipProxyTLS를 사용하여 SIPProxy.TLS 개체를 만듭니다. 이 개체가 Fabrikam이 발행한 인증서를 인증에 사용하도록 변수 $cert를 –Certificate 매개 변수의 값으로 사용합니다.

    $cert = New-CsIssuedCertId -Issuer "Fabrikam" -SerialNumber 0x10,0x14,0x3A,0x1A
    
    $tls = New-CsSipProxyTLS -Certificate $cert -Fqdn atl-proxy-001.litwareinc.com

## 자세한 정보

SIP(Session Initiation Protocol) 메시지를 누군가에게 보내는 경우 이 메시지는 배달되기 전에 여러 서브넷과 네트워크를 통과해야 할 수 있습니다. 메시지가 거치는 이러한 길을 일반적으로 경로라고 합니다. 네트워킹에는 동적 경로와 고정 경로의 두 가지 유형의 경로가 있습니다. 동적 경로의 경우 서버가 알고리즘을 사용하여 메시지를 전달할 다음 위치(다음 홉)을 결정합니다. 고정 경로의 경우 시스템 관리자가 메시지 경로를 미리 정합니다. 메시지가 서버에 수신되면 서버는 메시지 주소를 확인한 다음 관리자가 미리 구성한 다음 홉 서버로 메시지를 전달합니다. 고정 경로를 올바르게 구성하면 시기적절하고 정확하게 서버에 대한 부하를 최소화하면서 메시지를 배달할 수 있습니다. 고정 경로의 단점은 네트워크 실패 시 메시지가 동적으로 다시 경로 지정되지 않는다는 것입니다.

Lync Server를 사용하면 고정 경로를 구성할 때 TCP(Transmission Control Protocol) 또는 TLS(전송 계층 보안)를 전송 프로토콜로 지정할 수 있습니다. 프로토콜로 TLS를 사용하기로 결정한 경우 먼저 인증에 사용할 인증서를 할당해야 합니다. 이 경우 Lync Server용으로 구성된 기본 인증서를 사용할 수 있습니다. 또는 **New-CsIssuedCertID**를 호출하여 인증서 개체를 만든 다음 해당 개체를 **New-CsSipProxyTLS** cmdlet을 사용하여 만든 SipProxy.TLS 개체에 할당하여 TLS 인증서를 할당할 수 있습니다.

**New-CsIssuedCertID**를 실행할 때는 cmdlet에 기존 인증서의 발급자 이름과 일련 번호를 제공해야 합니다. 이 정보는 다음 명령을 실행하여 얻을 수 있습니다.

Get-CsCertificate | Select-Object Issuer, SerialNumber

일련 번호는 바이트 배열로 전달해야 합니다. 즉, 2문자 값의 배열로 일련 번호를 전달해야 합니다. 또한 각 2문자 값은 0x로 시작해야 합니다. 예를 들어 일련 번호가 1E225D3ZF66인 인증서가 있는 경우 다음 구문을 사용하여 데이터를 전달해야 합니다.

\-SerialNumber 0x1E,0x22,0x5D,0x3F,0x66

**New-CsStaticRoute** cmdlet을 사용하여 고정 경로를 만드는 경우 **New-CsIssuedCertId** cmdlet을 사용할 필요가 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsIssuedCertId** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsIssuedCertId"}

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
<td><p><em>Issuer</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>고정 경로에서 사용할 인증서를 발급한 CA(인증 기관)의 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SerialNumber</em></p></td>
<td><p>필수</p></td>
<td><p>System.Byte[]</p></td>
<td><p>고정 경로에 사용할 인증서의 일련 번호입니다. 일련 번호는 바이트 배열로 전달해야 합니다. 즉, 2문자 값의 배열로 일련 번호를 전달해야 하며 이러한 각각의 2문자 값은 0x로 시작해야 합니다(예: -SerialNumber 0x01, 0x23, 0x45, 0x67, 0x89).</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsIssuedCertId**는 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsIssuedCertId**는 Microsoft.Rtc.Management.WritableConfig.BaseTypes.IssuedCertId 개체의 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsSipProxyTLS](new-cssipproxytls.md)

