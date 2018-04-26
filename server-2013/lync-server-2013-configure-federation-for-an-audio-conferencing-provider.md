---
title: 'Lync Server 2013: 오디오 회의 공급자를 위한 페더레이션 구성'
TOCTitle: 오디오 회의 공급자를 위한 페더레이션 구성
ms:assetid: 08dedcce-0d3f-45da-8282-cf2634a41665
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn510996(v=OCS.15)
ms:contentKeyID: 59954254
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 오디오 회의 공급자를 위한 페더레이션 구성

 

_**마지막으로 수정된 항목:** 2014-07-24_

하이브리드 배포(Lync Online이 포함된 Lync Server 온-프레미스)에서 ACP(오디오 회의 공급자)를 사용하려는 경우 온-프레미스 Lync 배포와 ACP 파트너 사이의 페더레이션을 허용 파트너 서버로 구성해야 합니다. 페더레이션은 ACP 파트너 도메인 및 에지 서버(액세스 프록시라고도 함)를 온-프레미스 배포를 위한 페더레이션 도메인 목록에 추가해 구성할 수 있습니다. 그리고 나서 ACP 파트너가 온-프레미스 에지 서버 풀의 FQDN을 허용되는 페더레이션 도메인 목록에 추가해야 합니다. 추가 세부 정보는 ACP 공급자에게 문의하세요.

  - **ACP 도메인 및 에지 서버를 허용되는 페더레이션 도메인으로 추가**
    
    ACP 도메인을 허용 파트너 서버(허용되는 페더레이션 도메인)로 추가하려면 [Lync Server 2013에서 허용되는 외부 도메인 지원 구성](lync-server-2013-configure-support-for-allowed-external-domains.md)의 단계를 따르세요. 에지 서버의 경우 ACP 파트너 에지 서버의 FQDN을 추가합니다. 해당 에지 서버의 FQDN을 얻기 위해 ACP 파트너에게 연락해야 할 수도 있습니다. ACP에서 이를 액세스 프록시라고 하는 경우도 있습니다.

  - **ACP 파트너에 에지 서버 풀의 FQDN 제공**
    
    ACP 파트너는 에지 서버 풀의 FQDN을 허용되는 페더레이션 도메인으로 추가해 온-프레미스 도메인을 허용 파트너 서버로 추가하도록 페더레이션을 구성해야 합니다.

