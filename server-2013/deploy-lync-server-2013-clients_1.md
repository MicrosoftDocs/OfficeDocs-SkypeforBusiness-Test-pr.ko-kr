---
title: Lync Server 2013 클라이언트 배포
TOCTitle: Lync Server 2013 클라이언트 배포
ms:assetid: 508e5dfa-588b-4289-81ce-2043c2d79e04
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204883(v=OCS.15)
ms:contentKeyID: 49303614
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 클라이언트 배포

 

_**마지막으로 수정된 항목:** 2012-10-19_

사용자를 Lync Server 2013으로 마이그레이션한 후 다음을 수행합니다.

1.  새 Lync Server 2013 서버에서 클라이언트 버전 필터를 사용하여 최신 업데이트가 설치된 클라이언트만 로그인하도록 허용합니다.

2.  필요에 따라 클라이언트 부트스트랩에 필요한 그룹 정책 설정을 구성합니다. 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 클라이언트 부트스트랩 정책 구성](lync-server-2013-configuring-client-bootstrapping-policies.md)를 참조하십시오. 이러한 설정에 대한 구성은 기존 클라이언트 부트스트랩 정책을 변경하려는 경우 또는 새로운 클라이언트 부트스트랩 정책을 설정하려는 경우에만 필요합니다. 클라이언트 부트스트랩 정책을 구성하지 않으려는 경우 또는 레거시 클라이언트 부트스트랩 정책을 그대로 유지하려는 경우에는 작업이 필요하지 않습니다.

3.  Lync Server 2013 제어판, Lync Server 2013 관리 셸 또는 둘 다를 사용하여 다른 사용자 및 특정 사용자 또는 사용자 그룹에 대한 클라이언트 정책을 구성합니다. 자세한 내용은 계획 설명서의 [Lync 2013의 새로운 기능과 변경된 기능](lync-server-2013-new-and-changed-settings-for-lync-2013.md)을 참조하십시오.

4.  최신 버전의 Lync Server 2013 클라이언트와 함께 최신 누적 업데이트를 배포합니다. 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 클라이언트 및 장치 배포](lync-server-2013-deploying-clients-and-devices.md)을 참조하십시오.

5.  (선택 사항) 조직에 Lync Server 2013 향상된 현재 상태 개인 정보 보호 모드가 필요한 경우, 마이그레이션이 완료된 후 이전 버전의 클라이언트가 로그인할 수 없도록 방지하는 클라이언트 버전 정책 규칙을 정의합니다. 그런 다음 향상된 현재 상태 개인 정보 보호 모드를 설정합니다.
    

    > [!IMPORTANT]
    > 지정된 서버 풀의 모든 사용자가 최신 클라이언트 버전을 설치할 때까지 Lync 2013 향상된 현재 상태 개인 정보 보호 모드를 설정하지 마십시오.


