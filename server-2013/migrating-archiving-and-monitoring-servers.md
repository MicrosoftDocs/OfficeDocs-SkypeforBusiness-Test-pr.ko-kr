---
title: 보관 및 모니터링 서버 마이그레이션
TOCTitle: 보관 및 모니터링 서버 마이그레이션
ms:assetid: 77831579-df45-4697-b8c5-207b74a07a40
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205015(v=OCS.15)
ms:contentKeyID: 49304087
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 보관 및 모니터링 서버 마이그레이션

 

_**마지막으로 수정된 항목:** 2012-10-02_

Lync Server 2010 환경에 보관 서버 및 모니터링 서버를 배포한 경우 프런트 엔드 풀을 마이그레이션한 후 해당 Lync Server 2013 환경에 이러한 서버를 배포할 수 있습니다. 보관 및 모니터링 기능이 조직에 중요한 경우라도 마이그레이션 프로세스 중 기능을 사용할 수 있도록 마이그레이션하기 전에 보관 서버 및 모니터링 서버를 Lync Server 2013 파일럿 풀에 추가해야 합니다.

마이그레이션 프로세스 중에 보관 및 모니터링 기능을 사용할 수 있으려면 다음과 같은 사항을 고려하십시오.

  - 보관 데이터 및 모니터링 데이터는 Lync Server 2013 배포로 이동되지 않습니다. 레거시 환경을 해제하기 전에 백업한 데이터는 Lync Server 2010 환경의 작업 내역이 됩니다.

  - Lync Server 2010 버전의 보관 서버 및 모니터링 서버는 Lync Server 2010 프런트 엔드 풀과만 연결할 수 있습니다. Lync Server 2013에서 보관 및 모니터링은 더 이상 서버 역할이 아니며, Lync Server 2013 프런트 엔드 풀에 통합된 서비스입니다.

  - 레거시 및 Lync Server 2013 배포를 동시에 사용하는 동안에는 Lync Server 2010 버전의 보관 서버 및 모니터링 서버가 Lync Server 2010 풀에 있는 사용자에 대한 데이터를 수집합니다. Lync Server 2013의 보관 및 모니터링이 Lync Server 2013 풀에 있는 사용자에 대한 데이터를 수집합니다.
    

    > [!NOTE]
    > 레거시 에지 서버와 새로운 Lync Server 2013 파일럿 풀을 계속 사용하는 마이그레이션 단계 중에는 Lync Server 2010 버전의 보관 서버가 Lync Server 2010 풀에 있는 사용자에 대한 데이터를 계속해서 수집하고 Lync Server 2013의 보관이 Lync Server 2013 풀에 있는 사용자에 대한 데이터를 수집합니다.



  - Lync Server 2013의 보관 및 모니터링과 함께 타사 보관 및 모니터링 솔루션을 사용하는 경우 타사 솔루션을 Lync Server 2013과 통합해야 하는 시기 및 방법에 대한 자세한 내용은 해당 공급업체에 문의하십시오.

