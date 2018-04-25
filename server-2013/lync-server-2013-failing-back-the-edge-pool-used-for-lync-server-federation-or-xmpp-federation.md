---
title: 'Lync Server 2013: Lync Server 페더레이션 또는 XMPP 페더레이션에 사용되는 에지 풀 장애 복구(failback)'
TOCTitle: Lync Server 페더레이션 또는 XMPP 페더레이션에 사용되는 에지 풀 장애 복구(failback)
ms:assetid: d40097a1-1bed-44dc-aeb6-0871927ab2b9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721897(v=OCS.15)
ms:contentKeyID: 49886004
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Lync Server 페더레이션 또는 XMPP 페더레이션에 사용되는 에지 풀 장애 복구(failback)

 

_**마지막으로 수정된 항목:** 2012-11-01_

페더레이션을 호스팅하는 데 사용되는 에지 풀에 오류가 발생했다가 다시 온라인 상태로 전환되면 다음 절차를 사용하여 복원된 이 에지 풀을 다시 사용하도록 Lync Server 페더레이션 경로 및/또는 XMPP 페더레이션 경로를 장애 복구(failback)해야 합니다.

## 복원된 에지 풀로 페더레이션 장애 복구

1.  다시 사용할 수 있는 상태가 된 에지 풀에서 에지 서비스를 시작합니다.

2.  복원된 에지 서버를 사용하도록 Lync Server 페더레이션 경로를 장애 복구하려면 다음을 수행합니다.
    
      - 프런트 엔드 서버에서 토폴로지 작성기를 엽니다. **에지 풀** 을 확장한 다음 페더레이션으로 현재 구성된 에지 서버 풀 또는 에지 서버를 마우스 오른쪽 단추로 클릭합니다. **속성 편집** 을 선택합니다.
    
      - **속성 편집** 의 **일반** 에서 **이 에지 풀에 페더레이션 사용(포트 5061)** 을 선택 취소합니다. **확인** 을 클릭합니다.
    
      - **에지 풀** 을 확장한 다음 페더레이션을 다시 사용하려는 원래 에지 서버 풀 또는 에지 서버를 마우스 오른쪽 단추로 클릭합니다. **속성 편집** 을 선택합니다.
    
      - **속성 편집** 의 **일반** 에서 **이 에지 풀에 페더레이션 사용(포트 5061)** 을 선택합니다. **확인** 을 클릭합니다.
    
      - **동작** 을 클릭하고 **토폴로지** 를 선택한 다음 **게시** 를 선택합니다. **토폴로지 게시** 에서 메시지가 나타나면 **다음** 을 클릭합니다. 게시를 마치면 **마침** 을 클릭합니다.
    
      - 에지 서버에서 Lync Server 배포 마법사를 엽니다. **Lync Server 시스템 설치 또는 업데이트** 를 클릭한 후 **Lync Server 구성 요소 설치 또는 제거** 를 클릭합니다. **다시 실행** 을 클릭합니다.
    
      - **Lync Server 구성 요소 설치** 에서 다음을 클릭합니다. 요약 화면에 실행한 작업이 표시됩니다. 배포를 마치면 **로그 보기** 를 클릭하여 사용할 수 있는 로그 파일을 봅니다. **마침** 을 클릭하여 배포를 완료합니다.

3.  복원된 에지 서버를 사용하도록 XMPP 페더레이션 경로를 장애 복구하려면 다음을 수행합니다.
    
      - 다음 cmdlet을 실행하여 이제 XMPP 페더레이션(예: EdgeServer1)을 호스팅할 에지 풀로 페더레이션 경로를 다시 가리킵니다.
        
            Set-CsSite Site1 -XmppExternalFederationRoute EdgeServer1.contoso.com
        
        이 예에서 사이트 1은 이제 XMPP 페더레이션을 호스팅할 에지 풀이 포함된 사이트이고, EdgeServer1.contoso.com은 해당 풀에 있는 에지 서버의 FQDN입니다.
    
      - 이제 XMPP 페더레이션을 호스팅할 에지 풀로 확인하는 XMPP 페더레이션에 대한 DNS SRV 레코드가 이미 있는 경우 다음 예에서와 같이 추가해야 합니다. 이 SRV 레코드의 포트 값은 5269여야 합니다.
        
            _xmpp-server._tcp.contoso.com
    
      - 외부 DNS 서버에서 EdgeServer2.contoso.com을 가리키도록 XMPP 페더레이션에 대한 DNS A 레코드를 변경합니다.
    
      - 이제 XMPP 페더레이션을 호스팅할 에지 풀의 포트 5269가 외부에 개방되었는지 확인합니다.

4.  오류가 발생했다가 복원된 에지 풀을 포함하는 사이트에 실행 중인 프런트 엔드 풀이 남아 있으면 이러한 프런트 엔드 풀의 웹 회의 서비스 및 A/V 회의 서비스를 업데이트하여 로컬 사이트의 에지 풀을 다시 사용하도록 해야 합니다. 자세한 내용은 [Lync Server 2013에서 프런트 엔드 풀과 연결된 에지 풀 변경](lync-server-2013-changing-the-edge-pool-associated-with-a-front-end-pool.md)을 참조하십시오.

5.  오류가 발생한 에지 풀과 동일한 사이트에서 프런트 엔드 풀에 오류가 발생하면 이제는 Invoke?CsPoolFailback을 사용하여 프런트 엔드 풀을 장애 복구할 수 있습니다.

## 참고 항목

#### 작업

[Lync Server 2013에서 Lync Server 페더레이션에 사용되는 에지 풀 장애 조치(failover)](lync-server-2013-failing-over-the-edge-pool-used-for-lync-server-federation.md)  
[Lync Server 2013에서 XMPP 페더레이션에 사용되는 에지 풀 장애 조치(failover)](lync-server-2013-failing-over-the-edge-pool-used-for-xmpp-federation.md)  

#### 개념

[Lync Server 2013의 에지 서버 재해 복구](lync-server-2013-edge-server-disaster-recovery.md)

