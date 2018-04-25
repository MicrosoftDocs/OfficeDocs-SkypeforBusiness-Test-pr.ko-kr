---
title: Lync Online 고객에 대한 페더레이션 지원 구성
TOCTitle: Lync Online 고객에 대한 페더레이션 지원 구성
ms:assetid: e5f7f38d-ede5-4af3-88c2-026e8a78df12
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh202193(v=OCS.15)
ms:contentKeyID: 49305354
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Online 고객에 대한 페더레이션 지원 구성

 

_**마지막으로 수정된 항목:** 2012-11-01_

다음 방법을 통해 조직의 사용자에게 통신 서비스를 제공할 수 있습니다.

  - 조직에 Lync Server 2013을 배포하고(*온-프레미스 서비스*라고도 함) 조직에서 Lync 2013 사용자 계정을 설정합니다.

  - 호스팅 공급자를 통해 Microsoft Lync Online 2010 고객 계정을 설정하고 호스팅 공급자와 사용자 계정을 설정합니다(*온라인 서비스*라고도 함).

조직에 Lync 2013을 배포할 경우 하나 이상의 Microsoft Lync Online 2010 고객의 도메인과 페더레이션할 수 있습니다. 온-프레미스 Lync 2013 배포의 사용자와 Lync Online 2010 고객의 사용자 간에 페더레이션을 설정하려면 Lync Online 고객의 도메인 및 사용자에 대한 지원을 구성해야 합니다.


> [!NOTE]
> 이 설명서에서는 Lync Online 2010 고객과의 페더레이션을 지원하기 위해 조직을 구성하는 절차에 대해서만 설명합니다. 페더레이션 지원을 위해 Lync Online 2010 고객을 구성하는 절차에 대한 설명은 이 설명서에서 다루지 않습니다. Lync Online 서비스에 대한 자세한 내용은 Lync Online(<A class=uri href="http://go.microsoft.com/fwlink/?linkid=218941%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=218941&amp;clcid=0x412</A>)을 참조하십시오.



## 이 단원의 내용

  - [Lync Online 고객과의 페더레이션을 위한 필수 구성 요소](lync-server-2013-prerequisites-for-federating-with-a-lync-online-customer.md)

  - [Lync Online 도메인에 대한 페더레이션 지원 구성](lync-server-2013-configure-federation-support-for-a-lync-online-domain.md)

  - [Lync Online 고객과의 페더레이션을 위한 사용자 액세스 구성](lync-server-2013-configure-user-access-for-federation-with-a-lync-online-customer.md)

  - [Lync Online 고객과의 통신 확인](lync-server-2013-verify-communications-with-a-lync-online-customer.md)

