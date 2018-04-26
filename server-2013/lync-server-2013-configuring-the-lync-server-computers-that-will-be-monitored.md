---
title: 모니터링할 Lync Server 컴퓨터 구성
TOCTitle: 모니터링할 Lync Server 컴퓨터 구성
ms:assetid: 9f1b2b91-d5af-42ad-a27d-b0815f762ad8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205118(v=OCS.15)
ms:contentKeyID: 49304549
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 모니터링할 Lync Server 컴퓨터 구성

 

_**마지막으로 수정된 항목:** 2012-10-20_

Lync Server 2013에서는 Microsoft Lync Server 2010에 사용된 중앙 복구 프로세스를 사용하지 않기 때문에 모니터링하려는 각 Lync Server 2013 컴퓨터가 자신의 존재를 관리 서버에 자동으로 보고할 수 있어야 합니다. 이를 위해서는 모니터링할 각 컴퓨터에 Operations Manager 에이전트 파일을 설치해야 합니다. 에이전트 파일을 설치한 후에는 컴퓨터가 System Center 프록시로 작동하도록 구성해야 합니다. 이러한 절차는 모니터링하려는 컴퓨터에 Lync Server를 설치 및 구성한 후에 수행해야 합니다.

