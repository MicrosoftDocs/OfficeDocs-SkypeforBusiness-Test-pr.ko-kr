---
title: Lync Server 2013 IPv6에 대한 기술 요구 사항
TOCTitle: IPv6에 대한 기술 요구 사항
ms:assetid: caff0123-ce41-4a62-87a0-00b1d118b72b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205278(v=OCS.15)
ms:contentKeyID: 49305034
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 IPv6에 대한 기술 요구 사항

 

_**마지막으로 수정된 항목:** 2012-10-30_

IPv6로 Lync Server 2013을 구성하려면 다음 요구 사항을 유의해야 합니다.

  - Lync Server에 IPv6 주소를 구성하려면 IPv6 주소로 검색 및 확인되어야 할 레코드에 대해 DNS(Domain Name System) 레코드를 만듭니다. IPv6 DNS는 호스트 AAAA(4개의 A) 레코드를 사용합니다. 배포 환경에 IPv4 및 IPv6를 모두 사용하는 경우 IPv4에 대한 호스트 A 레코드 및 IPv6에 대한 호스트 AAAA 레코드를 모두 구성하고 유지 관리하는 것이 가장 좋습니다. 배포 환경을 IPv6로 완전히 전환하는 경우라도 IPv4를 계속 사용하는 외부 사용자를 위해 IPv4 DNS 호스트 레코드가 계속 필요할 수 있습니다.
    
    IPv6의 사용을 시작하기 전에 IPv6 DNS 호스트 레코드를 배포할 수 있습니다. 클라이언트 또는 서버가 IPv6를 사용하지 않는 경우 레코드는 참조되지 않습니다. 변환 기술 구성 및 정책에 기반하여 사용할 레코드가 변환 기술에 따라 결정됩니다.

  - 각 IPv6 주소에는 범위가 있습니다. IPv6 주소 지정에 사용하는 3개의 범위로는 IPv6 전체 주소(공용 IPv4 주소와 유사), IPv6 고유 로컬 주소(비공개 IPv4 주소 범위와 유사) 및 IPv6 링크 로컬 주소( Windows Server에서 사용되는 IPv4용 자동 비공개 IP 주소와 유사)가 있습니다. 풀 내의 모든 서버는 동일한 범위의 IPv6 주소를 보유해야 합니다.


> [!IMPORTANT]
> IPv6는 상당히 복잡한 주제이며 네트워크 팀 및 인터넥 공급자와 함께 주의하여 계획해야 합니다. 그래야 Windows Server 수준 및 Lync Server 2013 수준에서 할당한 주소가 예상대로 작동합니다. 이 문서의 마지막에 있는 링크를 참조하여 IPv6 주소 지정 및 계획에 대한 추가 리소스를 참조하십시오.



## 참고 항목

#### 기타 리소스

[IP 버전 6 주소 지정 구조](http://tools.ietf.org/html/rfc4291)  
[IPv6 전역 유니캐스트 주소 형식](http://tools.ietf.org/html/rfc3587)  
[고유 로컬 IPv6 유니캐스트 주소](http://tools.ietf.org/html/rfc4193)

