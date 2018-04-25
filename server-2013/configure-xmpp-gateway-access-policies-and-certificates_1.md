---
title: XMPP 게이트웨이 액세스 정책 및 인증서 구성
TOCTitle: XMPP 게이트웨이 액세스 정책 및 인증서 구성
ms:assetid: cd91433e-6dfb-4553-8316-c1086b394221
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721885(v=OCS.15)
ms:contentKeyID: 49885989
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# XMPP 게이트웨이 액세스 정책 및 인증서 구성

 

_**마지막으로 수정된 항목:** 2012-10-15_

XMPP 페더레이션은 XMPP(eXtensible Messaging and Presence Protocol)에 따라 외부 배포를 정의합니다. XMPP 구성을 사용하면 Lync 사용자가 다음을 통해 MPP 도메인 사용자에 액세스할 수 있습니다.

  - IM 및 현재 상태 ? 개인 간에만

  - Lync 클라이언트에서 XMPP 페더레이션 연락처 만들기

XMPP(eXtensible Messaging and Presence Protocol) 페더레이션 파트너 지원을 위한 정책을 구성하는 경우 SIP(Session Initiation Protocol) 서비스 공급자(예: Windows Live)나 SIP 페더레이션된 도메인의 사용자가 아닌 XMPP 페더레이션된 도메인의 사용자에게 적용됩니다. 사용자가 연락처를 추가하고 통신하도록 허용할 각 XMPP 페더레이션된 도메인에 대해 XMPP 페더레이션 파트너를 구성할 수 있습니다. 정책을 만들었으면 XMPP 게이트웨이 인증서를 구성해야 합니다.


> [!NOTE]
> XMPP 게이트웨이 마이그레이션을 시작하려면 Lync Server 2013 XMPP 게이트웨이를 배포하고 사용자가 Lync Server 2013 XMPP 게이트웨이를 사용할 수 있도록 액세스 정책을 구성해야 합니다. 이러한 단계를 수행하기 전에 모든 사용자를 Lync Server 2013 배포로 이동해야 합니다. 자세한 내용은 <A href="configure-xmpp-gateway-on-lync-server-2013_1.md">Lync Server 2013에서 XMPP 게이트웨이 구성</A>을 참조하십시오.



## 사용자가 Lync Server 2013 XMPP 게이트웨이를 사용할 수 있도록 외부 액세스 정책 구성

1.  Lync Server 제어판을 엽니다.

2.  왼쪽 탐색 모음에서 **Federation and External Access(페더레이션 및 외부 액세스)** 를 클릭하고 **외부 액세스 정책** 을 클릭합니다.

3.  **새로 만들기** 를 클릭하고 **사용자 정책** 을 클릭합니다.

4.  외부 액세스 사용자 정책의 이름을 입력합니다.

5.  외부 액세스 사용자 정책에 대한 설명을 입력합니다.

6.  **페더레이션 사용자와의 통신 사용** 을 선택합니다.

7.  Select **Enable communications with XMPP federated users(XMPP 페더레이션 사용자와의 통신 사용)** 을 선택합니다.

8.  **커밋** 을 클릭하여 변경 내용을 사이트 또는 사용자 정책에 저장합니다.

