---
title: 'Lync Server 2013: 디렉터에 필요한 구성 요소'
TOCTitle: 디렉터에 필요한 구성 요소
ms:assetid: 15c7c8d4-b93f-4386-b2d1-d76dab8f801e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398228(v=OCS.15)
ms:contentKeyID: 49302912
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 디렉터에 필요한 구성 요소

 

_**마지막으로 수정된 항목:** 2012-09-08_

디렉터를 만들고 구성하는 데 필요한 구성 요소는 디렉터 서버 역할을 배포하는 것뿐입니다. 이 역할을 배포하려면 토폴로지 작성기를 사용하여 디렉터 풀 노드에서 단일 컴퓨터 풀 또는 다중 컴퓨터 풀을 정의합니다. 디렉터 또는 디렉터 풀을 정의한 후 디렉터로 사용할 컴퓨터에서 Lync Server 배포 마법사를 실행합니다. 디렉터 풀의 경우에는 풀 구성원으로 포함할 각 서버에서 Lync Server 배포 마법사를 실행합니다.

## 토폴로지

단일 디렉터 서버 또는 디렉터 풀을 구현할 수 있습니다. 디렉터는 항상 별도의 서버 또는 풀로, Lync Server 2013에서 다른 서버 역할과 함께 배치되지 않습니다.


> [!NOTE]
> 디렉터를 배포하지 않으면 프런트 엔드 서버 또는 프런트 엔드 풀에서 디렉터 역할을 수행합니다.



디렉터 풀은 부하 분산해야 합니다. 다음 중 하나를 수행할 수 있습니다.

  - 웹 서비스에는 하드웨어 부하 분산 장치를 사용하고 다른 트래픽 유형에는 DNS(Domain Name System) 부하 분산을 사용하는 토폴로지를 만듭니다.
    
    [Lync Server 2013의 조정된 디렉터 풀 - DNS 부하 분산 및 하드웨어 부하 분산 장치](lync-server-2013-scaled-director-pool-dns-load-balancing-and-hardware-load-balancer.md)

  - 디렉터 풀에 필요한 부하 분산을 위해 하드웨어 부하 분산 장치를 사용하는 토폴로지를 만듭니다.
    
    [Lync Server 2013의 조정된 디렉터 풀 - 하드웨어 부하 분산 장치](lync-server-2013-scaled-director-pool-hardware-load-balancer.md)

