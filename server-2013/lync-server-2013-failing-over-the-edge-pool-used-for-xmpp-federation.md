---
title: 'Lync Server 2013: XMPP 페더레이션에 사용되는 에지 풀 장애 조치(failover)'
TOCTitle: XMPP 페더레이션에 사용되는 에지 풀 장애 조치(failover)
ms:assetid: 587e7829-a26b-46f8-8aad-b78a7b325b55
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688065(v=OCS.15)
ms:contentKeyID: 49885776
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 XMPP 페더레이션에 사용되는 에지 풀 장애 조치(failover)

 

_**마지막으로 수정된 항목:** 2012-10-19_

조직에는 XMPP 페더레이션에 사용할 풀로 하나의 에지 풀이 지정됩니다. 이 풀이 다운되면 XMPP 페더레이션이 다시 작동하기 전에 다른 에지 풀을 사용하도록 XMPP 페더레이션을 장애 조치(failover)해야 합니다.

에지 풀을 처음 설치하고 XMPP 페더레이션을 사용하도록 설정할 때는 XMPP 페더레이션용으로 모든 에지 풀에 대해 하나가 아니라 여러 개의 외부 DNS SRV 레코드를 설정하여 재해 복구 프로세스를 간소화할 수 있습니다. 이러한 각 SRV 레코드에는 우선 순위를 다르게 설정해야 합니다. 모든 XMPP 페더레이션 트래픽은 우선 순위가 가장 높은 SRV 레코드가 포함된 풀을 통과합니다. XMPP 페더레이션을 설정하고 사용하도록 설정하는 방법에 대한 자세한 내용은 [Lync Server 2013에서 XMPP 페더레이션 설정](lync-server-2013-setting-up-xmpp-federation.md)을 참조하십시오.

다음 절차에서 EdgePool1은 원래 XMPP 페더레이션을 호스팅한 풀이고 EdgePool2는 XMPP 페더레이션을 이제 호스팅할 풀입니다.

## XMPP 페더레이션에 사용되는 에지 풀 장애 조치(failover)

1.  아직 다른 에지 풀을 배포하지 않았으면(현재 다운된 에지 풀과 별도) 해당 풀을 배포합니다. 자세한 내용은 [Lync Server 2013에서 외부 사용자 액세스 배포](lync-server-2013-deploying-external-user-access.md)를 참조하십시오.

2.  이제 XMPP 페더레이션을 호스팅할 새로운 에지 풀(EdgePool2)의 각 에지 서버에서 다음 cmdlet을 실행합니다.
    
        Stop-CsWindowsService

3.  다음 cmdlet을 실행하여 XMPP 페더레이션 경로를 다시 EdgePool2로 지정합니다.
    
        Set-CsSite Site2 -XmppExternalFederationRoute EdgeServer2.contoso.com
    
    이 예에서 Site2는 XMPP 페더레이션 경로를 이제 호스팅할 에지 풀이 포함된 사이트입니다. EdgeServer2.contoso.com은 이 풀에 있는 에지 서버의 FQDN입니다.

4.  외부 DNS 서버에서 EdgeServer2.contoso.com을 가리키도록 XMPP 페더레이션에 대한 DNS A 레코드를 변경합니다.

5.  이제 XMPP 페더레이션을 호스팅할 에지 풀로 확인하는 XMPP 페더레이션에 대한 DNS SRV 레코드가 이미 있는 경우 다음 예에서와 같이 추가해야 합니다. 이 SRV 레코드의 포트 값은 5269여야 합니다.
    
        _xmpp-server._tcp.contoso.com

6.  이제 XMPP 페더레이션을 호스팅할 에지 풀의 포트 5269가 외부에 개방되었는지 확인합니다.

7.  이제 XMPP 페더레이션을 호스팅할 에지 풀의 모든 에지 서버에서 서비스를 시작합니다.
    
        Start-CsWindowsService

