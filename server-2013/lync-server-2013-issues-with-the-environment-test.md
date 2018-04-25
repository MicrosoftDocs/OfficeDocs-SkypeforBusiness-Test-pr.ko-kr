---
title: 환경 테스트 문제
TOCTitle: 환경 테스트 문제
ms:assetid: ff1fe0d3-35b2-41ef-87e7-6a61e9e1d2ca
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205421(v=OCS.15)
ms:contentKeyID: 49305641
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 환경 테스트 문제

 

_**마지막으로 수정된 항목:** 2012-09-21_

모범 사례 분석기는 Lync Server 2013 환경이 지원되는 구성인지 여부를 확인할 수 있는 방법을 제공합니다. 모범 사례 분석기는 Active Directory 도메인 서비스 검사의 일부로서 다음을 수행합니다.

  - Active Directory 도메인 서비스 포리스트 및 스키마 준비 상태를 확인합니다.

  - 배포에서 Active Directory 도메인 서비스 사이트 및 도메인 수를 식별합니다.

  - 포리스트 및 도메인 수준을 확인합니다.

  - 도메인 컨트롤러 버전을 확인합니다.

  - 도메인, 구성 및 스키마 명명 컨텍스트를 식별합니다.

  - 활성화된 사용자 수를 식별합니다.

  - 전역 Active Directory 도메인 서비스 설정이 저장된 위치를 확인합니다.

  - Lync Server의 SCP(서비스 연결 지점)를 확인합니다.

  - 데이터베이스 버전을 식별합니다.

## 환경 관련 문제 해결

환경 테스트 시 환경 관련 문제가 발견된 경우 대개 Active Directory 구성이나 특정 서버에서 실행 중인 소프트웨어 수준과 관련된 문제가 원인입니다. 예를 들어 모범 사례 분석기를 통해 환경에서 Windows Server 2000을 실행 중인 도메인 컨트롤러가 식별되는 경우 이로 인해 경고가 발생하며 이러한 도메인 컨트롤러를 지원되는 Windows Server로 업그레이드해야 합니다.

