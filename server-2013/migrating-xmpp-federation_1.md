---
title: XMPP 페더레이션 마이그레이션
TOCTitle: XMPP 페더레이션 마이그레이션
ms:assetid: 7368ee8f-a201-4d3a-b4e8-68396b156d4d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688093(v=OCS.15)
ms:contentKeyID: 49885808
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# XMPP 페더레이션 마이그레이션

 

_**마지막으로 수정된 항목:** 2012-10-16_

이전 버전의 Office Communications Server에서는 XMPP 배포와의 페더레이션을 허용하기 위해 별도의 서버 역할로 배포할 수 있는 XMPP(Extensible Messaging and Presence Protocol) 게이트웨이를 제공했습니다. Lync Server 2013에서는 XMPP 기능을 하나의 기능으로 배포할 수 있습니다. XMPP 기능은 Lync Server 2013 에지 서버에서 실행되는 XMPP 프록시와 Lync Server 2013 프런트 엔드 서버에서 실행되는 XMPP 게이트웨이 두 부분으로 설치됩니다.

마이그레이션의 관점에서 Office Communications Server 2007 R2 사용자 계정은 Lync Server 2013 풀로 이동할 수 있으며, Office Communications Server 2007 R2 XMPP 게이트웨이를 계속 사용할 수 있습니다. 이러한 방식은 XMPP 페더레이션 파트너가 Lync Server 2013에 구성되어 있지 않은 경우에만 가능합니다.

요약하면 Office Communications Server이 Office Communications Server 2007 R2 XMPP 게이트웨이를 사용하여 배포되었고 레거시 Office Communications Server 2007 R2 사용자가 XMPP 페더레이션을 사용할 수 있도록 설정된 경우 XMPP 페더레이션을 Lync Server 2013으로 마이그레이션하려면 다음을 수행합니다.

1.  Lync Server 2013 풀을 배포합니다.

2.  Lync Server 2013 에지 서버를 배포합니다.

3.  모든 사용자를 Lync Server 2013 풀로 이동합니다.

4.  에지 서버에 대한 XMPP 액세스 정책 및 인증서를 만듭니다.

5.  Lync Server 2013에서 XMPP 페더레이션을 사용하도록 설정합니다.

6.  Lync Server 2013 XMPP 게이트웨이를 가리키도록 DNS 항목을 업데이트합니다.

