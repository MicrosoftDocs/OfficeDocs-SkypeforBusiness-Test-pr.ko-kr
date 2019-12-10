﻿---
title: Lync Server 2013 풀 장애 조치(Failover) 및 풀 장애 복구(Failback)를 위한 복구 시간
TOCTitle: 풀 장애 조치(Failover) 및 풀 장애 복구(Failback)를 위한 복구 시간
ms:assetid: 902c658f-8442-4d0d-b3ad-bf795ecd550d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205079(v=OCS.15)
ms:contentKeyID: 49304375
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 풀 장애 조치(Failover) 및 풀 장애 복구(Failback)를 위한 복구 시간

 

_**마지막으로 수정된 항목:** 2012-09-10_

풀 장애 조치(failover) 및 풀 장애 복구(failback)의 경우 RTO(복구 시간 목표)에 대한 엔지니어링 목표는 30분입니다. 이는 관리자가 재해 발생을 파악하고 장애 조치 절차를 시작한 후에 장애 조치가 이루어지는 데 소요되는 시간입니다. 여기에는 관리자가 상황을 평가하고 의사 결정을 내리는 데 소요되는 시간이나 장애 조치 완료 후 사용자가 다시 로그인하기까지 소요되는 시간은 포함되지 않습니다.

풀 장애 조치(failover) 및 풀 장애 복구(failback)의 경우 RPO(복구 시점 목표)에 대한 엔지니어링 목표는 30분입니다. 이는 재해 및 백업 서비스의 복제 지연으로 인해 손실될 수 있는 데이터를 시간으로 측정한 것입니다. 예를 들어 오전 10시에 풀이 다운된 경우 RPO가 30분이므로 오전 9시 30분과 오전 10시 사이에 풀에 기록된 데이터는 백업 풀에 복제되지 않을 수 있으며, 그에 따라 손실될 수 있습니다.

이 문서의 모든 RTO 및 RPO 수치는 두 데이터 센터가 동일한 지역에 있으며 두 사이트 간에 대기 시간이 짧은 고속 전송을 사용하는 것으로 가정합니다. 이러한 수치는 동시 활성 사용자가 40,000명이고 데이터 복제 백로그가 없는 미리 정의된 사용자 모델에 따라 Lync를 사용하도록 설정된 사용자가 200,000명인 풀에 대해 측정된 값입니다. 이러한 수치는 성능 테스트와 유효성 검사에 따라 변경될 수 있습니다.
