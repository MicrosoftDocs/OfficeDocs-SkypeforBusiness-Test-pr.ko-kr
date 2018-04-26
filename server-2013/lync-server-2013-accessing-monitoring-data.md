---
title: Lync Server 2013에서 모니터링 데이터에 액세스
TOCTitle: Lync Server 2013에서 모니터링 데이터에 액세스
ms:assetid: 845385ca-5532-4fa2-91b9-51c6de6fec91
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688116(v=OCS.15)
ms:contentKeyID: 49885851
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 모니터링 데이터에 액세스

 

_**마지막으로 수정된 항목:** 2012-09-05_

모니터링 데이터는 SQL Server 데이터베이스 쌍에 저장됩니다. 이러한 데이터베이스 쌍은 통화 정보 기록 데이터를 위한 LcsCdr과 체감 품질 데이터를 위한 QoEMetrics입니다. 이러한 두 데이터베이스는 특별한 사항이 없습니다. 즉, 이러한 데이터베이스에 저장되는 데이터는 일반적으로 SQL Server 데이터를 액세스하고 분석하는 데 사용되는 도구를 통해 액세스할 수 있습니다.

모니터링 데이터를 액세스하고 분석하는 데 고려해야 하는 한 가지 도구는 Lync Server 모니터링 보고서입니다. 모니터링 보고서는 Microsoft SQL Server Reporting Services에서 게시되는 표준 보고서 집합입니다. 웹 브라우저를 통해 액세스할 수 있는 이러한 보고서는 모두 CDR 및 QoE 데이터베이스에 저장된 CDR(통화 정보 기록) 및 QoE(체감 품질) 레코드를 기반으로 사용, 통화 진단 정보 및 미디어 품질 정보를 제공합니다. 모니터링 보고서는 Lync Server 2013과 함께 제공되며 Lync Server을 설치하고 모니터링을 구성한 후 Lync Server 배포 마법사에서 설치할 수 있습니다.

위에서 설명한 것처럼 모니터링 보고서를 위해서는 SQL Server Reporting Services를 사용해야 합니다. SQL Server Reporting Services는 SQL Server를 설치할 때 동시에 설치하거나 SQL Server 자체를 설치한 후 언제라도 설치할 수 있습니다.

자세한 내용은 Lync Server 2013 배포 설명서에서 [Lync Server 2013 모니터링 보고서 설치](lync-server-2013-installing-lync-server-2013-monitoring-reports.md) 항목을 참조하십시오.

