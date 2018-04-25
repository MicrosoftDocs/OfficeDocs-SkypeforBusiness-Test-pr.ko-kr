---
title: 'Lync Server 2013: 위치 기반 라우팅을 위한 기술적 고려 사항'
TOCTitle: 위치 기반 라우팅을 위한 기술적 고려 사항
ms:assetid: 2e2a9199-7c6f-48d3-9adb-3873fc4f8c4e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994027(v=OCS.15)
ms:contentKeyID: 52056812
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 위치 기반 라우팅을 위한 기술적 고려 사항

 

_**마지막으로 수정된 항목:** 2013-03-09_

위치 기반 라우팅을 계획할 때 다음 시나리오에 미치는 영향을 고려해야 합니다.

## 재해 복구

기본 풀에서 백업 풀로 장애 조치(failover) 도중이나 정상 작동을 기본 풀로 복원할 때 위치 기반 라우팅은 재해 및 복구 절차 중에 항상 적용된 상태로 유지됩니다.

## SBA(Survivable Branch Appliance)

위치 기반 라우팅을 구성하면 SBA(Survivable Branch Appliance)와 연결된 게이트웨이를 배포하는 계획이 영향을 받습니다. SBA와 연결된 게이트웨이는 SBA(Survivable Branch Appliance)와 같은 네트워크 사이트에 있어야 합니다. 그렇지 않으면 위치 기반 라우팅이 구성된 경우 SBA(Survivable Branch Appliance)에 있는 사용자가 아웃바운드 호출을 할 수 없습니다. SBA(Survivable Branch Appliance)와 중앙 사이트 간의 WAN 연결이 다운되면 위치 기반 라우팅 제한이 적용된 상태로 유지됩니다.

## 참고 항목

#### 기타 리소스

[Lync Server 2013의 위치 기반 라우팅 계획](lync-server-2013-planning-for-location-based-routing.md)

