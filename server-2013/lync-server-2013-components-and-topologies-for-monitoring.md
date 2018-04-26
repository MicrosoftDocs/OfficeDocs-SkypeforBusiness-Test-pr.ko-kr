---
title: 'Lync Server 2013: 모니터링의 구성 요소 및 토폴로지'
TOCTitle: 모니터링의 구성 요소 및 토폴로지
ms:assetid: c1bb36b0-1fb8-4d8e-9cc9-9bef740fe3c6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412952(v=OCS.15)
ms:contentKeyID: 49885965
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 모니터링의 구성 요소 및 토폴로지

 

_**마지막으로 수정된 항목:** 2012-09-05_

통합 데이터 수집 에이전트가 각 프런트 엔드 서버에 자동으로 설치되고 활성화되므로 모니터링 서버로 작동할 서버를 구성할 필요가 없습니다. 각 프런트 엔드 서버가 이미 모니터링 서버로 작동합니다. 그러나 모니터링 데이터를 위한 백 엔드 데이터 저장소로 작동할 데이터베이스를 설치하고 구성해야 합니다. Microsoft Lync Server 2013에서는 다음과 같은 데이터베이스를 모니터링용 백 엔드 저장소로 사용할 수 있습니다.

  - Microsoft SQL Server 2008 R2 Enterprise Edition

  - Microsoft SQL Server 2008 R2 Standard Edition

  - Microsoft SQL Server 2012 Enterprise Edition

  - Microsoft SQL Server 2012 Standard Edition

이러한 데이터베이스의 64비트 버전을 사용해야 합니다. 32비트 버전의 SQL Server는 모니터링용 백 엔드 저장소로 사용할 수 없습니다. 마찬가지로 Lync Server 2013에서는 SQL Server 2008 또는 SQL Server 2012의 Express Edition을 지원하지 않습니다. Lync Server 2013의 데이터베이스 요구 사항에 대한 자세한 내용은 Lync Server 2013 지원 가능성 가이드에서 [Lync Server 2013의 데이터베이스 소프트웨어 지원](lync-server-2013-database-software-support.md)을 참조하십시오.

모니터링을 배포하고 구성하기 전에 SQL Server를 설치하고 구성해야 합니다. 그러나 SQL Server 자체를 배포하기만 하면 되며 모니터링 데이터베이스를 미리 설치할 필요는 없습니다. 이러한 데이터베이스는 Lync Server 토폴로지를 게시할 때 자동으로 만들어집니다.

모니터링 데이터는 다른 유형의 데이터와 SQL Server 인스턴스를 공유할 수 있습니다. 일반적으로 통화 정보 기록 데이터베이스(LcsCdr) 및 체감 품질 데이터베이스(QoEMetrics)는 동일한 SQL 인스턴스를 공유합니다. 또한 이 두 가지 모니터링 데이터베이스는 보관 데이터베이스(LcSLog)와 동일한 SQL 인스턴스에 있는 경우가 많습니다. SQL Server 인스턴스에 대한 거의 유일한 실제적인 요구 사항은 하나의 SQL Server 인스턴스가 다음으로 제한된다는 점입니다.

  - 하나의 Lync Server 2013 백 엔드 데이터베이스 인스턴스. 일반적으로 모니터링 데이터베이스를 백 엔드 데이터베이스와 동일한 SQL 인스턴스 또는 동일한 컴퓨터에 배치하는 것은 좋지 않습니다. 기술적으로는 가능하지만 모니터링 데이터베이스가 백 엔드 데이터베이스에 필요한 디스크 공간을 모두 사용하게 될 위험이 있습니다.

  - 하나의 통화 정보 기록 데이터베이스 인스턴스

  - 하나의 체감 품질 데이터베이스 인스턴스

  - 하나의 보관 데이터베이스 인스턴스

다시 말해서 두 LcsCdr 데이터베이스 인스턴스를 동일한 SQL Server 인스턴스에 둘 수 없습니다. 여러 LcsCdr 데이터베이스 인스턴스가 필요한 경우 여러 SQL Server 인스턴스를 구성해야 합니다.

## 참고 항목

#### 기타 리소스

[Lync Server 2013의 모니터링 배포](lync-server-2013-deploying-monitoring.md)

