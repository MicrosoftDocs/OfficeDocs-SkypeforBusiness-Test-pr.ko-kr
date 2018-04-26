---
title: 'Lync Server 2013: Lync Server 페더레이션에 사용되는 에지 풀 장애 조치(failover)'
TOCTitle: Lync Server 페더레이션에 사용되는 에지 풀 장애 조치(failover)
ms:assetid: 5c9da0f2-7429-40bb-bb3c-5cc4ecb5a13d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688071(v=OCS.15)
ms:contentKeyID: 49885784
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Lync Server 페더레이션에 사용되는 에지 풀 장애 조치(failover)

 

_**마지막으로 수정된 항목:** 2012-09-17_

Lync Server 페더레이션을 구성한 에지 풀이 다운될 경우 페더레이션이 작동하도록 하려면 다른 에지 풀을 사용하도록 페더레이션을 변경해야 합니다.

## Lync Server 페더레이션에 사용되는 에지 풀 장애 조치(failover)

1.  프런트 엔드 서버에서 토폴로지 작성기를 엽니다. **에지 풀** 을 확장한 다음 페더레이션으로 현재 구성된 에지 서버 풀 또는 에지 서버를 마우스 오른쪽 단추로 클릭합니다. **속성 편집** 을 선택합니다.

2.  **속성 편집** 의 **일반** 에서 **이 에지 풀에 페더레이션 사용(포트 5061)** 을 선택 취소합니다. **확인** 을 클릭합니다.

3.  **에지 풀** 을 확장한 후 현재 페더레이션에 대해 사용할 에지 서버 또는 에지 서버 풀을 마우스 오른쪽 단추로 클릭합니다. **에지 속성** 을 선택합니다.

4.  **속성 편집** 의 **일반** 에서 **이 에지 풀에 페더레이션 사용(포트 5061)** 을 선택합니다. **확인** 을 클릭합니다.

5.  **동작** 을 클릭하고 **토폴로지** 를 선택한 다음 **게시** 를 선택합니다. **토폴로지 게시** 에서 메시지가 나타나면 **다음** 을 클릭합니다. 게시를 마치면 **마침** 을 클릭합니다.

6.  에지 서버에서 Lync Server 배포 마법사를 엽니다. **Lync Server 시스템 설치 또는 업데이트** 를 클릭한 후 **Lync Server 구성 요소 설치 또는 제거** 를 클릭합니다. **다시 실행** 을 클릭합니다.

7.  **Lync Server 구성 요소 설치** 에서 다음을 클릭합니다. 요약 화면에 실행한 작업이 표시됩니다. 배포를 마치면 **로그 보기** 를 클릭하여 사용할 수 있는 로그 파일을 봅니다. **마침** 을 클릭하여 배포를 완료합니다.
    
    실패한 에지 풀을 포함하는 사이트에 아직 실행 중인 프런트 엔드 서버가 포함된 경우 아직 실행 중인 원격 사이트의 에지 풀을 사용하도록 해당 프런트 엔드 풀에서 웹 회의 서비스 및 A/V 회의 서비스를 업데이트해야 합니다. 자세한 내용은 [Lync Server 2013에서 프런트 엔드 풀과 연결된 에지 풀 변경](lync-server-2013-changing-the-edge-pool-associated-with-a-front-end-pool.md)을 참조하십시오.

## 참고 항목

#### 작업

[Lync Server 2013에서 XMPP 페더레이션에 사용되는 에지 풀 장애 조치(failover)](lync-server-2013-failing-over-the-edge-pool-used-for-xmpp-federation.md)  
[Lync Server 2013에서 Lync Server 페더레이션 또는 XMPP 페더레이션에 사용되는 에지 풀 장애 복구(failback)](lync-server-2013-failing-back-the-edge-pool-used-for-lync-server-federation-or-xmpp-federation.md)  

#### 개념

[Lync Server 2013의 에지 서버 재해 복구](lync-server-2013-edge-server-disaster-recovery.md)

