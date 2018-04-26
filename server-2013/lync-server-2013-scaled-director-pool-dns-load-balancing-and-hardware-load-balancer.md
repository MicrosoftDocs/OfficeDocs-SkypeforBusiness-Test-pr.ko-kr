---
title: 'Lync Server 2013: 조정된 디렉터 풀 - DNS 부하 분산 및 하드웨어 부하 분산 장치'
TOCTitle: 조정된 디렉터 풀 - DNS 부하 분산 및 하드웨어 부하 분산 장치
ms:assetid: a1f6ffc0-9e6e-4217-a923-025c9679e154
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205142(v=OCS.15)
ms:contentKeyID: 49304579
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 조정된 디렉터 풀 - DNS 부하 분산 및 하드웨어 부하 분산 장치

 

_**마지막으로 수정된 항목:** 2012-10-22_

추가 용량을 처리하고 고가용성을 제공하기 위해 두 개 이상의 디렉터가 배포되어 있는 확장 디렉터 풀에는 클라이언트 및 서버 통신을 풀의 모든 구성원으로 분산시키기 위한 부하 분산이 필요합니다. 디렉터에서는 프런트 엔드 풀와 마찬가지로 웹 서비스를 호스팅합니다. 부하 분산을 제공하기 위해 하드웨어 분산이나 DNS(도메인 이름 시스템) 부하 분산 및 하드웨어 부하 분산을 사용할 수 있습니다. 하드웨어 부하 분산은 웹 서비스에 필요하며 DNS 부하 분산만으로는 웹 서비스에 필요한 기능이 제공되지 않습니다.

다음 항목에서는 하드웨어 부하 분산과 함께 DNS 부하 분산을 사용하여 디렉터 풀을 배포하기 위한 계획 고려 사항에 대해 설명합니다. 디렉터 풀에 하드웨어 부하 분산을 사용하지만 DNS 부하 분산은 사용하지 않으려는 경우 해당 토폴로지의 계획 요구 사항에 대해 설명하는 [Lync Server 2013의 조정된 디렉터 풀 - 하드웨어 부하 분산 장치](lync-server-2013-scaled-director-pool-hardware-load-balancer.md) 항목을 참조하십시오.

![확장된 디렉터 풀](images/JJ205142.35a78a7a-b781-4c8f-951e-168451ba6a65(OCS.15).jpg "확장된 디렉터 풀")

## 이 단원의 내용

  - [인증서 요약 - Lync Server 2013에서 DNS 및 HLB 부하 분산됨](lync-server-2013-certificate-summary-dns-and-hlb-load-balanced.md)

  - [Lync Server 2013의 포트 요약 - DNS 및 HLB 부하 분산됨](lync-server-2013-port-summary-dns-and-hlb-load-balanced.md)

  - [Lync Server 2013의 DNS 요약 - DNS 및 HLB 부하 분산됨](lync-server-2013-dns-summary-dns-and-hlb-load-balanced.md)

