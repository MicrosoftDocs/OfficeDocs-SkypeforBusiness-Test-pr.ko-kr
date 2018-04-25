---
title: 모범 사례 분석기의 개요
TOCTitle: 모범 사례 분석기의 개요
ms:assetid: c5fcaa05-eb1c-4092-90ad-177b127e795b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg591349(v=OCS.15)
ms:contentKeyID: 49304984
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 모범 사례 분석기의 개요

 

_**마지막으로 수정된 항목:** 2012-09-19_

Lync Server 2013 모범 사례 분석기를 사용하여 Lync Server 2013 배포의 문제점을 식별하고 해결할 수 있습니다. Lync Server 2013 모범 사례 분석기는 Lync Server 2013 구성 요소에서 구성 정보를 수집합니다.

적합한 네트워크 액세스 권한을 보유한 모범 사례 분석기는 Active Directory 도메인 서비스, Exchange Server UM(통합 메시징) 및 Lync Server 2013을 실행하는 서버를 검사할 수 있습니다. 모범 사례 분석기를 사용하여 다음 작업을 수행할 수 있습니다.

  - 사전 예방적으로 검사를 수행하여 권장되는 모범 사례에 따라 구성이 설정되어 있는지 확인할 수 있습니다.

  - Lync Server 2013에 필요한 업데이트를 자동으로 검색할 수 있습니다.

  - 최적화되지 않은 구성 설정, 지원되지 않는 옵션, 누락된 업데이트 또는 권장되지 않는 사례 등 문제점 목록을 생성할 수 있습니다.

  - 특정 문제를 해결하고 수정할 수 있도록 지원합니다.

모범 사례 분석기의 특징은 다음과 같습니다.

  - 최소 설치 필수 구성 요소

  - 문제 해결, 팁 등을 포함하여 보고된 문제점을 설명하는 온라인 설명서

  - 나중에 검토할 수 있도록 저장 가능한 구성 정보

  - 최신 시스템 분석 기능

모범 사례 분석기에서는 일련의 XML 구성 파일을 사용하여 Lync Server 2013 환경에서 수집할 정보를 결정합니다. Active Directory 도메인 서비스를 검사할 뿐 아니라 WMI(Windows Management Instrumentation)에서 Windows Server 운영 체제 레지스트리 및 설정과 같은 원본도 검사합니다.

모범 사례 분석기는 Lync Server 2013 배포의 설정 및 구성과 관련된 데이터를 수집하여 미리 정의된 규칙 집합과 비교합니다.

수집된 데이터를 미리 정의된 규칙과 비교한 후 문제점을 보고합니다. 보고하는 각 문제점에 대해 검사한 Lync Server 2013 환경에서 발견된 내용 및 권장 구성에 대한 정보도 제공합니다. 모범 사례 분석기는 또한 특정 문제에 대해 자세한 정보를 제공하는 링크를 제공합니다.


> [!NOTE]
> Lync Server 2013 모범 사례 분석기는 Lync Server 2013 구성 요소에서만 구성 정보를 수집합니다. 이전 환경을 검사하려면 이전 버전의 도구를 사용할 수 있습니다. 자세한 내용은 <A href="lync-server-2013-requirements-for-running-best-practices-analyzer.md">모범 사례 분석기 실행을 위한 요구 사항</A>을 참조하십시오.


