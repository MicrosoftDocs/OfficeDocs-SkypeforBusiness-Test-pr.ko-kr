---
title: 고정 라우팅 Cmdlet
TOCTitle: 고정 라우팅 Cmdlet
ms:assetid: 71d5e0cd-8412-4383-818a-95b851a4da4b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg416492(v=OCS.15)
ms:contentKeyID: 49304002
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 고정 라우팅 Cmdlet

 

_**마지막으로 수정된 항목:** 2012-06-20_

관리자는 고정 경로를 사용하여 SIP 메시지에 사용할 네트워크 경로를 미리 결정할 수 있습니다. 메시지가 서버에 수신되면 서버는 메시지 주소를 확인한 다음 관리자가 미리 구성한 다음 홉 서버로 메시지를 전달합니다. 고정 경로를 제대로 구성한 경우에는 제시간에 정확하게 메시지를 전달하고 서버에 대한 오버헤드를 최소화할 수 있습니다.

## 고정 라우팅 Cmdlet

Microsoft 지원 담당자가 별도로 지시하지 않는 한 Microsoft Lync Server 2013에 대해 구성된 고정 경로는 [New-CsStaticRoute](new-csstaticroute.md) cmdlet을 사용하여 만들어야 합니다. 경로를 만든 후 CsStaticRoutingConfiguration cmdlet을 사용하여 해당 경로를 고정 경로 컬렉션에 추가할 수 있습니다.

**고정 경로**

  -   
    [Get-CsSipResponseCodeTranslationRule](get-cssipresponsecodetranslationrule.md)

  -   
    [New-CsSipResponseCodeTranslationRule](new-cssipresponsecodetranslationrule.md)

  -   
    [Remove-CsSipResponseCodeTranslationRule](remove-cssipresponsecodetranslationrule.md)

  -   
    [Set-CsSipResponseCodeTranslationRule](set-cssipresponsecodetranslationrule.md)

  -   
    [New-CsStaticRoute](new-csstaticroute.md)

  -   
    [Get-CsStaticRoutingConfiguration](get-csstaticroutingconfiguration.md)

  -   
    [New-CsStaticRoutingConfiguration](new-csstaticroutingconfiguration.md)

  -   
    [Remove-CsStaticRoutingConfiguration](remove-csstaticroutingconfiguration.md)

  -   
    [Set-CsStaticRoutingConfiguration](set-csstaticroutingconfiguration.md)

  -   
    [New-CsSipProxyCustom](new-cssipproxycustom.md)

  -   
    [New-CsSipProxyRealm](new-cssipproxyrealm.md)

  -   
    [New-CsSipProxyTCP](new-cssipproxytcp.md)

  -   
    [New-CsSipProxyTLS](new-cssipproxytls.md)

  -   
    [New-CsSipProxyTransport](new-cssipproxytransport.md)

  -   
    [New-CsSipProxyUseDefault](new-cssipproxyusedefault.md)

  -   
    [New-CsSipProxyUseDefaultCert](new-cssipproxyusedefaultcert.md)

  -   
    [New-CsIssuedCertId](new-csissuedcertid.md)

## 참고 항목

#### 기타 리소스

[Lync Server PowerShell 블로그](http://go.microsoft.com/fwlink/?linkid=203150%26clcid=0x412)

