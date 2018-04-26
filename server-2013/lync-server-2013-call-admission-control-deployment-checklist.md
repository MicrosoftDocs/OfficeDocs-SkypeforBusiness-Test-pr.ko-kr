---
title: Lync Server 2013의 통화 허용 제어 배포 검사 목록
TOCTitle: Lync Server 2013의 통화 허용 제어 배포 검사 목록
ms:assetid: d56a525f-3da5-4ac0-a311-0c5efd98c9df
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398928(v=OCS.15)
ms:contentKeyID: 49305160
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 통화 허용 제어 배포 검사 목록

 

_**마지막으로 수정된 항목:** 2012-10-22_

다음 검사 목록을 사용하여 CAC(통화 허용 제어)를 배포하기 위해 필요한 구성 작업이 모두 완료되었는지 확인합니다.

  - 하나 이상의 에지 서버가 배포된 경우 각 외부 인터페이스 IP 주소는 비트 마스크가 32인 네트워크 구성 설정의 서브넷 목록에 추가되어야 합니다. 또한 이 서브넷(IP 주소)을 A/V 에지 서비스가 배포된 지리적 위치의 네트워크 사이트 ID와 연결해야 합니다.
    

    > [!NOTE]
    > CAC를 구현하는 데 에지 서버는 필요하지 않습니다.



  - CAC가 Lync Server 제어판을 사용하거나 [Lync Server 2013에서 통화 허용 제어 사용](lync-server-2013-enable-call-admission-control.md)에서 지정된 대로 cmdlet를 실행하여 사용하도록 설정되었는지 확인합니다.

  - CAC가 모든 중앙 사이트에서 사용하도록 설정되었는지 확인합니다. 이 작업은 토폴로지 작성기를 통해 수행할 수 있습니다. 게시할 때 경고가 표시된 경우 경고를 무시하면 *안 됩니다*.

  - 엔터프라이즈 네트워크에서 관리된 모든 서브넷이 네트워크 구성 설정에서 구성되었는지 확인합니다. 이 확인 작업은 [Lync Server 2013 에서 네트워크 사이트에 서브넷 연결](lync-server-2013-associate-a-subnet-with-a-network-site.md)에서 설명한 대로 네트워크 사이트에 모든 서브넷을 연결할 때도 반드시 수행해야 합니다.

  - 모든 프런트 엔드 서버, SBA(Survivable Branch Appliance), 오디오/비디오 회의 서버(별도의 풀에 있는 경우), 중재 서버의 서브넷이나 IP 주소가 네트워크 구성 설정에서 구성되었는지 확인합니다.

