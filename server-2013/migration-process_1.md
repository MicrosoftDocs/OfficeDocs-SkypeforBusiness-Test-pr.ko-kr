---
title: 마이그레이션 프로세스
TOCTitle: 마이그레이션 프로세스
ms:assetid: b2bd9c76-2f4b-4d14-a5c4-157bbff75de0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205181(v=OCS.15)
ms:contentKeyID: 49304765
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 마이그레이션 프로세스

 

_**마지막으로 수정된 항목:** 2012-09-24_

Lync Server 2013에 대한 권장 및 지원되는 마이그레이션 절차는 병렬 마이그레이션 절차입니다. 이 항목에서는 병렬 마이그레이션을 사용해야 하는 이유와 동시 사용 관련 정보에 대해 설명합니다.

## 병렬 마이그레이션

거의 모든 마이그레이션에서는 병렬 마이그레이션 경로를 사용해야 합니다. 병렬 마이그레이션에서는 Lync Server 2013이 설치되어 있는 새 서버와 그에 대응하는 Office Communications Server 2007 R2 실행 서버를 함께 배포한 다음 새 서버로 작업을 전송합니다. 또한 Office Communications Server 2007 R2로 롤백해야 하는 경우에도 작업을 다시 원래 서버로 이동하기만 하면 됩니다. 이 경우 업그레이드된 클라이언트로 예약된 모든 새 모임이 작동하지 않으며 클라이언트도 다운그레이드해야 합니다.

## 동시 사용 테스트

Lync Server 2013과 함께 Office Communications Server 2007 R2를 배포한 후에는 토폴로지가 Lync Server 2013과 Office Communications Server 2007 R2의 동시 사용 테스트 상태를 나타냅니다. 이 상태에 있는 동안 서비스가 시작되는지, 각 사이트를 관리할 수 있는지, 클라이언트가 현재 및 레거시 사용자와 통신할 수 있는지를 테스트하여 확인해야 합니다. 모든 사용자를 마이그레이션하기 전에 각 배포의 상태를 이해하고 각 배포가 올바르게 기능 및 작동하는지 확인해야 합니다. 일반적으로 동시 사용 테스트 단계는 Lync Server 2013의 파일럿 테스트 전반에 걸쳐 수행됩니다. 레거시 사용자는 응용 프로그램 호환성 및 기능이 올바르게 작동하도록 보장하기 위해 일시적으로 Lync Server 2013으로 이동됩니다. 파일럿 테스트 후에는 사용자 및 응용 프로그램이 Lync Server 2013의 프로덕션 버전으로 이동되며 Office Communications Server 2007 R2의 레거시 풀 및 응용 프로그램이 폐기됩니다.

